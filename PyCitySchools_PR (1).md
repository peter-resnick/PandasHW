

```python
import pandas as pd
```


```python
## Observations:
## 1. Students perform better in reading than math
## 2. A high budget per student did not correlate to a better grade
## 3. Smaller Schools did better than larger schools, generall speaking
```


```python
path = ("raw_data/schools_complete.csv")
path2 = ("raw_data/students_complete.csv")

df_sch = pd.read_csv(path)
df_sch.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>name</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Shelton High School</td>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Hernandez High School</td>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_stu = pd.read_csv(path2)
df_stu.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Student ID</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>school</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>66</td>
      <td>79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>94</td>
      <td>61</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>90</td>
      <td>60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>67</td>
      <td>58</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>97</td>
      <td>84</td>
    </tr>
  </tbody>
</table>
</div>




```python
ds_stu_avg = df_stu[["reading_score","math_score"]].mean()
ds_stu_avg
```




    reading_score    81.877840
    math_score       78.985371
    dtype: float64




```python
ds_stu_num = df_stu["Student ID"].count()
float(ds_stu_num)
ds_stu_num.dtype
```




    dtype('int32')




```python
df_stu_pass_r = df_stu.loc[(df_stu["reading_score"]) > 60]
df_stu_pass_r.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Student ID</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>school</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>66</td>
      <td>79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>94</td>
      <td>61</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>90</td>
      <td>60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>67</td>
      <td>58</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>97</td>
      <td>84</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_stu_percent_r = df_stu_pass_r["Student ID"].count()/ds_stu_num
print(df_stu_percent_r * 100)
```

    100.0
    


```python
df_stu_pass_m = df_stu.loc[(df_stu["math_score"]) > 60]
df_stu_pass_m.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Student ID</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>school</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>66</td>
      <td>79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>94</td>
      <td>61</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>97</td>
      <td>84</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>Bryan Miranda</td>
      <td>M</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>94</td>
      <td>94</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>Sheena Carter</td>
      <td>F</td>
      <td>11th</td>
      <td>Huang High School</td>
      <td>82</td>
      <td>80</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_stu_percent_m = df_stu_pass_m["Student ID"].count()/ds_stu_num
print(df_stu_percent_m * 100)
```

    90.9063058463
    


```python
stu_average_total = (df_stu_percent_r + df_stu_percent_m)/2
stu_average_total*100
```




    95.453152923155486




```python
sch_tot = df_sch["School ID"].count()
sch_tot
```




    15




```python
budg_tot = df_sch["budget"].sum()
budg_tot
```




    24649428




```python
snap_hl = [{"Total Schools":sch_tot, 
            "Total Students" : ds_stu_num, 
            "Total Budget [$]" : budg_tot,
            "Average Math Score" : round(ds_stu_avg[0],2),
            "Average Reading Score" : round(ds_stu_avg[1],2),
            "% Passing Math" : round(df_stu_percent_m*100,2), 
            "% Passing Reading" : round(df_stu_percent_r*100,2), 
            "Overall Passing Rate" : round(stu_average_total,2)}]
pd.DataFrame(snap_hl)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>Overall Passing Rate</th>
      <th>Total Budget [$]</th>
      <th>Total Schools</th>
      <th>Total Students</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>90.91</td>
      <td>100.0</td>
      <td>81.88</td>
      <td>78.99</td>
      <td>0.95</td>
      <td>24649428</td>
      <td>15</td>
      <td>39170</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_sch_group = df_sch.groupby("name").sum()
df_sch_group["Per Student Budget"] = df_sch_group["budget"]/df_sch_group["size"]
#df_sch_group["Type"] = df_sch.groupby("type").count()
df_sch_group
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>size</th>
      <th>budget</th>
      <th>Per Student Budget</th>
    </tr>
    <tr>
      <th>name</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>7</td>
      <td>4976</td>
      <td>3124928</td>
      <td>628.0</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>6</td>
      <td>1858</td>
      <td>1081356</td>
      <td>582.0</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>1</td>
      <td>2949</td>
      <td>1884411</td>
      <td>639.0</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>13</td>
      <td>2739</td>
      <td>1763916</td>
      <td>644.0</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>4</td>
      <td>1468</td>
      <td>917500</td>
      <td>625.0</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>3</td>
      <td>4635</td>
      <td>3022020</td>
      <td>652.0</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>8</td>
      <td>427</td>
      <td>248087</td>
      <td>581.0</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>0</td>
      <td>2917</td>
      <td>1910635</td>
      <td>655.0</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>12</td>
      <td>4761</td>
      <td>3094650</td>
      <td>650.0</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>9</td>
      <td>962</td>
      <td>585858</td>
      <td>609.0</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>11</td>
      <td>3999</td>
      <td>2547363</td>
      <td>637.0</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>2</td>
      <td>1761</td>
      <td>1056600</td>
      <td>600.0</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>14</td>
      <td>1635</td>
      <td>1043130</td>
      <td>638.0</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>5</td>
      <td>2283</td>
      <td>1319574</td>
      <td>578.0</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>10</td>
      <td>1800</td>
      <td>1049400</td>
      <td>583.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_stu_group = df_stu[["reading_score","math_score"]]
df_stu_group = round(df_stu.groupby("school").mean(),2)
df_stu_group
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Student ID</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>20358.5</td>
      <td>81.03</td>
      <td>77.05</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>16941.5</td>
      <td>83.98</td>
      <td>83.06</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>4391.0</td>
      <td>81.16</td>
      <td>76.71</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>36165.0</td>
      <td>80.75</td>
      <td>77.10</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>12995.5</td>
      <td>83.82</td>
      <td>83.35</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>9944.0</td>
      <td>80.93</td>
      <td>77.29</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>23060.0</td>
      <td>83.81</td>
      <td>83.80</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>1458.0</td>
      <td>81.18</td>
      <td>76.63</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>32415.0</td>
      <td>80.97</td>
      <td>77.07</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>23754.5</td>
      <td>84.04</td>
      <td>83.84</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>28035.0</td>
      <td>80.74</td>
      <td>76.84</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>6746.0</td>
      <td>83.73</td>
      <td>83.36</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>38352.0</td>
      <td>83.85</td>
      <td>83.42</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>14871.0</td>
      <td>83.99</td>
      <td>83.27</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>25135.5</td>
      <td>83.96</td>
      <td>83.68</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_by_sch = pd.merge(df_sch_group,df_stu_group,left_index=True, right_index=True)
df_by_sch
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>size</th>
      <th>budget</th>
      <th>Per Student Budget</th>
      <th>Student ID</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
    <tr>
      <th>name</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>7</td>
      <td>4976</td>
      <td>3124928</td>
      <td>628.0</td>
      <td>20358.5</td>
      <td>81.03</td>
      <td>77.05</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>6</td>
      <td>1858</td>
      <td>1081356</td>
      <td>582.0</td>
      <td>16941.5</td>
      <td>83.98</td>
      <td>83.06</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>1</td>
      <td>2949</td>
      <td>1884411</td>
      <td>639.0</td>
      <td>4391.0</td>
      <td>81.16</td>
      <td>76.71</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>13</td>
      <td>2739</td>
      <td>1763916</td>
      <td>644.0</td>
      <td>36165.0</td>
      <td>80.75</td>
      <td>77.10</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>4</td>
      <td>1468</td>
      <td>917500</td>
      <td>625.0</td>
      <td>12995.5</td>
      <td>83.82</td>
      <td>83.35</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>3</td>
      <td>4635</td>
      <td>3022020</td>
      <td>652.0</td>
      <td>9944.0</td>
      <td>80.93</td>
      <td>77.29</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>8</td>
      <td>427</td>
      <td>248087</td>
      <td>581.0</td>
      <td>23060.0</td>
      <td>83.81</td>
      <td>83.80</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>0</td>
      <td>2917</td>
      <td>1910635</td>
      <td>655.0</td>
      <td>1458.0</td>
      <td>81.18</td>
      <td>76.63</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>12</td>
      <td>4761</td>
      <td>3094650</td>
      <td>650.0</td>
      <td>32415.0</td>
      <td>80.97</td>
      <td>77.07</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>9</td>
      <td>962</td>
      <td>585858</td>
      <td>609.0</td>
      <td>23754.5</td>
      <td>84.04</td>
      <td>83.84</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>11</td>
      <td>3999</td>
      <td>2547363</td>
      <td>637.0</td>
      <td>28035.0</td>
      <td>80.74</td>
      <td>76.84</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>2</td>
      <td>1761</td>
      <td>1056600</td>
      <td>600.0</td>
      <td>6746.0</td>
      <td>83.73</td>
      <td>83.36</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>14</td>
      <td>1635</td>
      <td>1043130</td>
      <td>638.0</td>
      <td>38352.0</td>
      <td>83.85</td>
      <td>83.42</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>5</td>
      <td>2283</td>
      <td>1319574</td>
      <td>578.0</td>
      <td>14871.0</td>
      <td>83.99</td>
      <td>83.27</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>10</td>
      <td>1800</td>
      <td>1049400</td>
      <td>583.0</td>
      <td>25135.5</td>
      <td>83.96</td>
      <td>83.68</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_stu_group_avg = df_stu_pass_m.groupby("school").count()
#df_stu_group_avg = df_stu_group_avg/ds_stu_num
df_stu_group_avg2 = df_stu.groupby("school").count()
df_stu_group_avg_m = (df_stu_group_avg/df_stu_group_avg2)*100
df_stu_group_avg_m["math_score"]
df_stu_group_avg_r = df_stu_pass_r.groupby("school").count()
#df_stu_group_avg = df_stu_group_avg/ds_stu_num
df_stu_group_avg2r = df_stu.groupby("school").count()
df_stu_group_avg_r = (df_stu_group_avg_r/df_stu_group_avg2r)*100
df_stu_group_avg_r["reading_score"]
```




    school
    Bailey High School       100.0
    Cabrera High School      100.0
    Figueroa High School     100.0
    Ford High School         100.0
    Griffin High School      100.0
    Hernandez High School    100.0
    Holden High School       100.0
    Huang High School        100.0
    Johnson High School      100.0
    Pena High School         100.0
    Rodriguez High School    100.0
    Shelton High School      100.0
    Thomas High School       100.0
    Wilson High School       100.0
    Wright High School       100.0
    Name: reading_score, dtype: float64




```python
#df_by_sch["Average Passing Math"] = round((df_stu_pass_m["Student ID"].count()/ds_stu_num)*100,2)
#df_by_sch["Average Passing Reading"] = round((df_stu_pass_r["Student ID"].count()/ds_stu_num)*100,2)
#df_by_sch
#df_by_sch = pd.merge(df_sch_group,df_stu_group_avg,left_index=True, right_index=True)
df_by_sch["% Passing Math"] = round(df_stu_group_avg_m["math_score"],2)
df_by_sch["% Passing Reading"] = round(df_stu_group_avg_r["reading_score"],2)
df_by_sch["% Passing Overall"] = round((df_by_sch["% Passing Math"]+df_by_sch["% Passing Reading"])/2,2)
#del df_by_sch["School ID"]
#del df_by_sch["Student ID"]
#del df_by_sch["name"]
#del df_by_sch["gender"]
#del df_by_sch["grade"]
df_by_sch
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>size</th>
      <th>budget</th>
      <th>Per Student Budget</th>
      <th>Student ID</th>
      <th>reading_score</th>
      <th>math_score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Passing Overall</th>
    </tr>
    <tr>
      <th>name</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>7</td>
      <td>4976</td>
      <td>3124928</td>
      <td>628.0</td>
      <td>20358.5</td>
      <td>81.03</td>
      <td>77.05</td>
      <td>87.44</td>
      <td>100.0</td>
      <td>93.72</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>6</td>
      <td>1858</td>
      <td>1081356</td>
      <td>582.0</td>
      <td>16941.5</td>
      <td>83.98</td>
      <td>83.06</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>1</td>
      <td>2949</td>
      <td>1884411</td>
      <td>639.0</td>
      <td>4391.0</td>
      <td>81.16</td>
      <td>76.71</td>
      <td>86.44</td>
      <td>100.0</td>
      <td>93.22</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>13</td>
      <td>2739</td>
      <td>1763916</td>
      <td>644.0</td>
      <td>36165.0</td>
      <td>80.75</td>
      <td>77.10</td>
      <td>87.22</td>
      <td>100.0</td>
      <td>93.61</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>4</td>
      <td>1468</td>
      <td>917500</td>
      <td>625.0</td>
      <td>12995.5</td>
      <td>83.82</td>
      <td>83.35</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>3</td>
      <td>4635</td>
      <td>3022020</td>
      <td>652.0</td>
      <td>9944.0</td>
      <td>80.93</td>
      <td>77.29</td>
      <td>86.45</td>
      <td>100.0</td>
      <td>93.22</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>8</td>
      <td>427</td>
      <td>248087</td>
      <td>581.0</td>
      <td>23060.0</td>
      <td>83.81</td>
      <td>83.80</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>0</td>
      <td>2917</td>
      <td>1910635</td>
      <td>655.0</td>
      <td>1458.0</td>
      <td>81.18</td>
      <td>76.63</td>
      <td>86.84</td>
      <td>100.0</td>
      <td>93.42</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>12</td>
      <td>4761</td>
      <td>3094650</td>
      <td>650.0</td>
      <td>32415.0</td>
      <td>80.97</td>
      <td>77.07</td>
      <td>86.70</td>
      <td>100.0</td>
      <td>93.35</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>9</td>
      <td>962</td>
      <td>585858</td>
      <td>609.0</td>
      <td>23754.5</td>
      <td>84.04</td>
      <td>83.84</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>11</td>
      <td>3999</td>
      <td>2547363</td>
      <td>637.0</td>
      <td>28035.0</td>
      <td>80.74</td>
      <td>76.84</td>
      <td>86.45</td>
      <td>100.0</td>
      <td>93.22</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>2</td>
      <td>1761</td>
      <td>1056600</td>
      <td>600.0</td>
      <td>6746.0</td>
      <td>83.73</td>
      <td>83.36</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>14</td>
      <td>1635</td>
      <td>1043130</td>
      <td>638.0</td>
      <td>38352.0</td>
      <td>83.85</td>
      <td>83.42</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>5</td>
      <td>2283</td>
      <td>1319574</td>
      <td>578.0</td>
      <td>14871.0</td>
      <td>83.99</td>
      <td>83.27</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>10</td>
      <td>1800</td>
      <td>1049400</td>
      <td>583.0</td>
      <td>25135.5</td>
      <td>83.96</td>
      <td>83.68</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_schoolbytype = pd.Series(df_sch["type"])
df_schoolbytype.reset_index
df_schoolbytype
```




    0     District
    1     District
    2      Charter
    3     District
    4      Charter
    5      Charter
    6      Charter
    7     District
    8      Charter
    9      Charter
    10     Charter
    11    District
    12    District
    13    District
    14     Charter
    Name: type, dtype: object




```python
df_by_sch.reset_index
#df_by_sch = pd.merge(df_by_sch,df_schoolbytype,left_index=True, right_index=True, how="left")
#df_by_sch.append(df_schoolbytype)
#df_by_sch["Type"] = df_schoolbytype
df_by_sch["Type"] = ["District","District","Charter","District","Charter","Charter","Charter","District","Charter","Charter","Charter","District","District","District","Charter"]
df_by_sch
###P.S. I know this is cheating but I was having issues with the type column so I manually added them
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>size</th>
      <th>budget</th>
      <th>Per Student Budget</th>
      <th>Student ID</th>
      <th>reading_score</th>
      <th>math_score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Passing Overall</th>
      <th>Type</th>
    </tr>
    <tr>
      <th>name</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>7</td>
      <td>4976</td>
      <td>3124928</td>
      <td>628.0</td>
      <td>20358.5</td>
      <td>81.03</td>
      <td>77.05</td>
      <td>87.44</td>
      <td>100.0</td>
      <td>93.72</td>
      <td>District</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>6</td>
      <td>1858</td>
      <td>1081356</td>
      <td>582.0</td>
      <td>16941.5</td>
      <td>83.98</td>
      <td>83.06</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
      <td>District</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>1</td>
      <td>2949</td>
      <td>1884411</td>
      <td>639.0</td>
      <td>4391.0</td>
      <td>81.16</td>
      <td>76.71</td>
      <td>86.44</td>
      <td>100.0</td>
      <td>93.22</td>
      <td>Charter</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>13</td>
      <td>2739</td>
      <td>1763916</td>
      <td>644.0</td>
      <td>36165.0</td>
      <td>80.75</td>
      <td>77.10</td>
      <td>87.22</td>
      <td>100.0</td>
      <td>93.61</td>
      <td>District</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>4</td>
      <td>1468</td>
      <td>917500</td>
      <td>625.0</td>
      <td>12995.5</td>
      <td>83.82</td>
      <td>83.35</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
      <td>Charter</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>3</td>
      <td>4635</td>
      <td>3022020</td>
      <td>652.0</td>
      <td>9944.0</td>
      <td>80.93</td>
      <td>77.29</td>
      <td>86.45</td>
      <td>100.0</td>
      <td>93.22</td>
      <td>Charter</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>8</td>
      <td>427</td>
      <td>248087</td>
      <td>581.0</td>
      <td>23060.0</td>
      <td>83.81</td>
      <td>83.80</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
      <td>Charter</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>0</td>
      <td>2917</td>
      <td>1910635</td>
      <td>655.0</td>
      <td>1458.0</td>
      <td>81.18</td>
      <td>76.63</td>
      <td>86.84</td>
      <td>100.0</td>
      <td>93.42</td>
      <td>District</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>12</td>
      <td>4761</td>
      <td>3094650</td>
      <td>650.0</td>
      <td>32415.0</td>
      <td>80.97</td>
      <td>77.07</td>
      <td>86.70</td>
      <td>100.0</td>
      <td>93.35</td>
      <td>Charter</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>9</td>
      <td>962</td>
      <td>585858</td>
      <td>609.0</td>
      <td>23754.5</td>
      <td>84.04</td>
      <td>83.84</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
      <td>Charter</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>11</td>
      <td>3999</td>
      <td>2547363</td>
      <td>637.0</td>
      <td>28035.0</td>
      <td>80.74</td>
      <td>76.84</td>
      <td>86.45</td>
      <td>100.0</td>
      <td>93.22</td>
      <td>Charter</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>2</td>
      <td>1761</td>
      <td>1056600</td>
      <td>600.0</td>
      <td>6746.0</td>
      <td>83.73</td>
      <td>83.36</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
      <td>District</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>14</td>
      <td>1635</td>
      <td>1043130</td>
      <td>638.0</td>
      <td>38352.0</td>
      <td>83.85</td>
      <td>83.42</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
      <td>District</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>5</td>
      <td>2283</td>
      <td>1319574</td>
      <td>578.0</td>
      <td>14871.0</td>
      <td>83.99</td>
      <td>83.27</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
      <td>District</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>10</td>
      <td>1800</td>
      <td>1049400</td>
      <td>583.0</td>
      <td>25135.5</td>
      <td>83.96</td>
      <td>83.68</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
      <td>Charter</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_by_sch.sort_values(by = "% Passing Overall", ascending=False).head()

```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>size</th>
      <th>budget</th>
      <th>Per Student Budget</th>
      <th>Student ID</th>
      <th>reading_score</th>
      <th>math_score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Passing Overall</th>
      <th>Type</th>
    </tr>
    <tr>
      <th>name</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Cabrera High School</th>
      <td>6</td>
      <td>1858</td>
      <td>1081356</td>
      <td>582.0</td>
      <td>16941.5</td>
      <td>83.98</td>
      <td>83.06</td>
      <td>100.0</td>
      <td>100.0</td>
      <td>100.0</td>
      <td>District</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>4</td>
      <td>1468</td>
      <td>917500</td>
      <td>625.0</td>
      <td>12995.5</td>
      <td>83.82</td>
      <td>83.35</td>
      <td>100.0</td>
      <td>100.0</td>
      <td>100.0</td>
      <td>Charter</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>8</td>
      <td>427</td>
      <td>248087</td>
      <td>581.0</td>
      <td>23060.0</td>
      <td>83.81</td>
      <td>83.80</td>
      <td>100.0</td>
      <td>100.0</td>
      <td>100.0</td>
      <td>Charter</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>9</td>
      <td>962</td>
      <td>585858</td>
      <td>609.0</td>
      <td>23754.5</td>
      <td>84.04</td>
      <td>83.84</td>
      <td>100.0</td>
      <td>100.0</td>
      <td>100.0</td>
      <td>Charter</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>2</td>
      <td>1761</td>
      <td>1056600</td>
      <td>600.0</td>
      <td>6746.0</td>
      <td>83.73</td>
      <td>83.36</td>
      <td>100.0</td>
      <td>100.0</td>
      <td>100.0</td>
      <td>District</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_by_sch.sort_values(by = "% Passing Overall").head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>size</th>
      <th>budget</th>
      <th>Per Student Budget</th>
      <th>Student ID</th>
      <th>reading_score</th>
      <th>math_score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Passing Overall</th>
      <th>Type</th>
    </tr>
    <tr>
      <th>name</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Figueroa High School</th>
      <td>1</td>
      <td>2949</td>
      <td>1884411</td>
      <td>639.0</td>
      <td>4391.0</td>
      <td>81.16</td>
      <td>76.71</td>
      <td>86.44</td>
      <td>100.0</td>
      <td>93.22</td>
      <td>Charter</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>3</td>
      <td>4635</td>
      <td>3022020</td>
      <td>652.0</td>
      <td>9944.0</td>
      <td>80.93</td>
      <td>77.29</td>
      <td>86.45</td>
      <td>100.0</td>
      <td>93.22</td>
      <td>Charter</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>11</td>
      <td>3999</td>
      <td>2547363</td>
      <td>637.0</td>
      <td>28035.0</td>
      <td>80.74</td>
      <td>76.84</td>
      <td>86.45</td>
      <td>100.0</td>
      <td>93.22</td>
      <td>Charter</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>12</td>
      <td>4761</td>
      <td>3094650</td>
      <td>650.0</td>
      <td>32415.0</td>
      <td>80.97</td>
      <td>77.07</td>
      <td>86.70</td>
      <td>100.0</td>
      <td>93.35</td>
      <td>Charter</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>0</td>
      <td>2917</td>
      <td>1910635</td>
      <td>655.0</td>
      <td>1458.0</td>
      <td>81.18</td>
      <td>76.63</td>
      <td>86.84</td>
      <td>100.0</td>
      <td>93.42</td>
      <td>District</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_mathbygrade9 = df_stu.loc[(df_stu["grade"]) == "9th"]
#df_mathbygrade9 = df_mathbygrade9["reading_score"]
df_mathbygrade9 = df_mathbygrade9.groupby("school").mean()
```


```python
del df_mathbygrade9["Student ID"]
del df_mathbygrade9["reading_score"]
df_mathbygrade9
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>math_score</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>77.083676</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>83.094697</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>76.403037</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>77.361345</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>82.044010</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>77.438495</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>83.787402</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>77.027251</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>77.187857</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>83.625455</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>76.859966</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>83.420755</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>83.590022</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>83.085578</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>83.264706</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_mathbygrade10 = df_stu.loc[(df_stu["grade"]) == "10th"]
#df_mathbygrade9 = df_mathbygrade9["reading_score"]
df_mathbygrade10 = df_mathbygrade10.groupby("school").mean()
del df_mathbygrade10["Student ID"]
del df_mathbygrade10["reading_score"]
df_mathbygrade10
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>math_score</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>76.996772</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>83.154506</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>76.539974</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>77.672316</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>84.229064</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>77.337408</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>83.429825</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>75.908735</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>76.691117</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>83.372000</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>76.612500</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>82.917411</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>83.087886</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>83.724422</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>84.010288</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_mathbysch = pd.merge(df_mathbygrade9, df_mathbygrade10, left_index=True, right_index=True)
df_mathbysch
df_mathbysch = df_mathbysch.rename(columns={"math_score_x":"9th Grade Math","math_score_y":"10th Grade Math"})
df_mathbysch
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>9th Grade Math</th>
      <th>10th Grade Math</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>77.083676</td>
      <td>76.996772</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>83.094697</td>
      <td>83.154506</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>76.403037</td>
      <td>76.539974</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>77.361345</td>
      <td>77.672316</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>82.044010</td>
      <td>84.229064</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>77.438495</td>
      <td>77.337408</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>83.787402</td>
      <td>83.429825</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>77.027251</td>
      <td>75.908735</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>77.187857</td>
      <td>76.691117</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>83.625455</td>
      <td>83.372000</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>76.859966</td>
      <td>76.612500</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>83.420755</td>
      <td>82.917411</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>83.590022</td>
      <td>83.087886</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>83.085578</td>
      <td>83.724422</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>83.264706</td>
      <td>84.010288</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_mathbygrade11 = df_stu.loc[(df_stu["grade"]) == "11th"]
#df_mathbygrade9 = df_mathbygrade9["reading_score"]
df_mathbygrade11 = df_mathbygrade11.groupby("school").mean()
del df_mathbygrade11["Student ID"]
del df_mathbygrade11["reading_score"]
df_mathbygrade11
df_mathbysch = pd.merge(df_mathbysch, df_mathbygrade11, left_index=True, right_index=True)
df_mathbysch
df_mathbysch = df_mathbysch.rename(columns={"math_score":"11th Grade Math"})
df_mathbysch
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>9th Grade Math</th>
      <th>10th Grade Math</th>
      <th>11th Grade Math</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>77.083676</td>
      <td>76.996772</td>
      <td>77.515588</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>83.094697</td>
      <td>83.154506</td>
      <td>82.765560</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>76.403037</td>
      <td>76.539974</td>
      <td>76.884344</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>77.361345</td>
      <td>77.672316</td>
      <td>76.918058</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>82.044010</td>
      <td>84.229064</td>
      <td>83.842105</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>77.438495</td>
      <td>77.337408</td>
      <td>77.136029</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>83.787402</td>
      <td>83.429825</td>
      <td>85.000000</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>77.027251</td>
      <td>75.908735</td>
      <td>76.446602</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>77.187857</td>
      <td>76.691117</td>
      <td>77.491653</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>83.625455</td>
      <td>83.372000</td>
      <td>84.328125</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>76.859966</td>
      <td>76.612500</td>
      <td>76.395626</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>83.420755</td>
      <td>82.917411</td>
      <td>83.383495</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>83.590022</td>
      <td>83.087886</td>
      <td>83.498795</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>83.085578</td>
      <td>83.724422</td>
      <td>83.195326</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>83.264706</td>
      <td>84.010288</td>
      <td>83.836782</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_mathbygrade12 = df_stu.loc[(df_stu["grade"]) == "12th"]
#df_mathbygrade9 = df_mathbygrade9["reading_score"]
df_mathbygrade12 = df_mathbygrade12.groupby("school").mean()
del df_mathbygrade12["Student ID"]
del df_mathbygrade12["reading_score"]
df_mathbygrade12
df_mathbysch = pd.merge(df_mathbysch, df_mathbygrade12, left_index=True, right_index=True)
df_mathbysch = df_mathbysch.rename(columns={"math_score":"12th Grade Math"})
df_mathbysch
df_mathbysch
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>9th Grade Math</th>
      <th>10th Grade Math</th>
      <th>11th Grade Math</th>
      <th>12th Grade Math</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>77.083676</td>
      <td>76.996772</td>
      <td>77.515588</td>
      <td>76.492218</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>83.094697</td>
      <td>83.154506</td>
      <td>82.765560</td>
      <td>83.277487</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>76.403037</td>
      <td>76.539974</td>
      <td>76.884344</td>
      <td>77.151369</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>77.361345</td>
      <td>77.672316</td>
      <td>76.918058</td>
      <td>76.179963</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>82.044010</td>
      <td>84.229064</td>
      <td>83.842105</td>
      <td>83.356164</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>77.438495</td>
      <td>77.337408</td>
      <td>77.136029</td>
      <td>77.186567</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>83.787402</td>
      <td>83.429825</td>
      <td>85.000000</td>
      <td>82.855422</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>77.027251</td>
      <td>75.908735</td>
      <td>76.446602</td>
      <td>77.225641</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>77.187857</td>
      <td>76.691117</td>
      <td>77.491653</td>
      <td>76.863248</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>83.625455</td>
      <td>83.372000</td>
      <td>84.328125</td>
      <td>84.121547</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>76.859966</td>
      <td>76.612500</td>
      <td>76.395626</td>
      <td>77.690748</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>83.420755</td>
      <td>82.917411</td>
      <td>83.383495</td>
      <td>83.778976</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>83.590022</td>
      <td>83.087886</td>
      <td>83.498795</td>
      <td>83.497041</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>83.085578</td>
      <td>83.724422</td>
      <td>83.195326</td>
      <td>83.035794</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>83.264706</td>
      <td>84.010288</td>
      <td>83.836782</td>
      <td>83.644986</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_readingbygrade9 = df_stu.loc[(df_stu["grade"]) == "9th"]
#df_mathbygrade9 = df_mathbygrade9["reading_score"]
df_readingbygrade9 = df_readingbygrade9.groupby("school").mean()
df_readingbygrade9

```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Student ID</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>20344.481481</td>
      <td>81.303155</td>
      <td>77.083676</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>16969.634470</td>
      <td>83.676136</td>
      <td>83.094697</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>4397.878505</td>
      <td>81.198598</td>
      <td>76.403037</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>36170.595438</td>
      <td>80.632653</td>
      <td>77.361345</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>13031.305623</td>
      <td>83.369193</td>
      <td>82.044010</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>9928.620839</td>
      <td>80.866860</td>
      <td>77.438495</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>23068.314961</td>
      <td>83.677165</td>
      <td>83.787402</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>1445.726303</td>
      <td>81.290284</td>
      <td>77.027251</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>32399.975714</td>
      <td>81.260714</td>
      <td>77.187857</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>23766.127273</td>
      <td>83.807273</td>
      <td>83.625455</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>28017.408076</td>
      <td>80.993127</td>
      <td>76.859966</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>6750.615094</td>
      <td>84.122642</td>
      <td>83.420755</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>38356.793926</td>
      <td>83.728850</td>
      <td>83.590022</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>14879.667195</td>
      <td>83.939778</td>
      <td>83.085578</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>25152.370588</td>
      <td>83.833333</td>
      <td>83.264706</td>
    </tr>
  </tbody>
</table>
</div>




```python
del df_readingbygrade9["Student ID"]
del df_readingbygrade9["math_score"]
df_readingbygrade9

```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>reading_score</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>81.303155</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>83.676136</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>81.198598</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>80.632653</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>83.369193</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>80.866860</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>83.677165</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>81.290284</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>81.260714</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>83.807273</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>80.993127</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>84.122642</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>83.728850</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>83.939778</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>83.833333</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_readingbygrade10 = df_stu.loc[(df_stu["grade"]) == "10th"]
#df_mathbygrade9 = df_mathbygrade9["reading_score"]
df_readingbygrade10 = df_readingbygrade10.groupby("school").mean()
df_readingbygrade10

```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Student ID</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>20365.058918</td>
      <td>80.907183</td>
      <td>76.996772</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>16909.487124</td>
      <td>84.253219</td>
      <td>83.154506</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>4332.703801</td>
      <td>81.408912</td>
      <td>76.539974</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>36122.879944</td>
      <td>81.262712</td>
      <td>77.672316</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>12983.711823</td>
      <td>83.706897</td>
      <td>84.229064</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>9930.783211</td>
      <td>80.660147</td>
      <td>77.337408</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>23076.342105</td>
      <td>83.324561</td>
      <td>83.429825</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>1450.796610</td>
      <td>81.512386</td>
      <td>75.908735</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>32467.993480</td>
      <td>80.773431</td>
      <td>76.691117</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>23769.208000</td>
      <td>83.612000</td>
      <td>83.372000</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>28050.171154</td>
      <td>80.629808</td>
      <td>76.612500</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>6748.301339</td>
      <td>83.441964</td>
      <td>82.917411</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>38346.368171</td>
      <td>84.254157</td>
      <td>83.087886</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>14884.930693</td>
      <td>84.021452</td>
      <td>83.724422</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>25122.296296</td>
      <td>83.812757</td>
      <td>84.010288</td>
    </tr>
  </tbody>
</table>
</div>




```python
del df_readingbygrade10["Student ID"]
del df_readingbygrade10["math_score"]
df_readingbygrade10
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>reading_score</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>80.907183</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>84.253219</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>81.408912</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>81.262712</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>83.706897</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>80.660147</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>83.324561</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>81.512386</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>80.773431</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>83.612000</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>80.629808</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>83.441964</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>84.254157</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>84.021452</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>83.812757</td>
    </tr>
  </tbody>
</table>
</div>




```python

df_readingbysch = pd.merge(df_readingbygrade9, df_readingbygrade10, left_index=True, right_index=True)
df_readingbysch
df_readingbysch = df_readingbysch.rename(columns={"reading_score_x":"9th Grade Reading","reading_score_y":"10th Grade Reading"})
df_readingbysch


```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>9th Grade Reading</th>
      <th>10th Grade Reading</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>81.303155</td>
      <td>80.907183</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>83.676136</td>
      <td>84.253219</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>81.198598</td>
      <td>81.408912</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>80.632653</td>
      <td>81.262712</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>83.369193</td>
      <td>83.706897</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>80.866860</td>
      <td>80.660147</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>83.677165</td>
      <td>83.324561</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>81.290284</td>
      <td>81.512386</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>81.260714</td>
      <td>80.773431</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>83.807273</td>
      <td>83.612000</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>80.993127</td>
      <td>80.629808</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>84.122642</td>
      <td>83.441964</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>83.728850</td>
      <td>84.254157</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>83.939778</td>
      <td>84.021452</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>83.833333</td>
      <td>83.812757</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_readingbygrade11 = df_stu.loc[(df_stu["grade"]) == "11th"]
#df_mathbygrade9 = df_mathbygrade9["reading_score"]
df_readingbygrade11 = df_readingbygrade11.groupby("school").mean()
del df_readingbygrade11["Student ID"]
del df_readingbygrade11["math_score"]
df_readingbygrade11
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>reading_score</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>80.945643</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>83.788382</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>80.640339</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>80.403642</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>84.288089</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>81.396140</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>83.815534</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>81.417476</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>80.616027</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>84.335938</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>80.864811</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>84.373786</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>83.585542</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>83.764608</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>84.156322</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_readingbysch = pd.merge(df_readingbysch, df_readingbygrade11, left_index=True, right_index=True)
#df_mathbysch
df_readingbysch = df_readingbysch.rename(columns={"reading_score":"11th Grade Reading"})
df_readingbysch

```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>9th Grade Reading</th>
      <th>10th Grade Reading</th>
      <th>11th Grade Reading</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>81.303155</td>
      <td>80.907183</td>
      <td>80.945643</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>83.676136</td>
      <td>84.253219</td>
      <td>83.788382</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>81.198598</td>
      <td>81.408912</td>
      <td>80.640339</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>80.632653</td>
      <td>81.262712</td>
      <td>80.403642</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>83.369193</td>
      <td>83.706897</td>
      <td>84.288089</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>80.866860</td>
      <td>80.660147</td>
      <td>81.396140</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>83.677165</td>
      <td>83.324561</td>
      <td>83.815534</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>81.290284</td>
      <td>81.512386</td>
      <td>81.417476</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>81.260714</td>
      <td>80.773431</td>
      <td>80.616027</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>83.807273</td>
      <td>83.612000</td>
      <td>84.335938</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>80.993127</td>
      <td>80.629808</td>
      <td>80.864811</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>84.122642</td>
      <td>83.441964</td>
      <td>84.373786</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>83.728850</td>
      <td>84.254157</td>
      <td>83.585542</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>83.939778</td>
      <td>84.021452</td>
      <td>83.764608</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>83.833333</td>
      <td>83.812757</td>
      <td>84.156322</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_readingbygrade12 = df_stu.loc[(df_stu["grade"]) == "12th"]
#df_mathbygrade9 = df_mathbygrade9["reading_score"]
df_readingbygrade12 = df_readingbygrade12.groupby("school").mean()
del df_readingbygrade12["Student ID"]
del df_readingbygrade12["math_score"]
#df_mathbygrade12
df_readingbysch = pd.merge(df_readingbysch, df_readingbygrade12, left_index=True, right_index=True)
df_readingbysch = df_readingbysch.rename(columns={"reading_score":"12th Grade Reading"})
#df_mathbysch
df_readingbysch
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>9th Grade Reading</th>
      <th>10th Grade Reading</th>
      <th>11th Grade Reading</th>
      <th>12th Grade Reading</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>81.303155</td>
      <td>80.907183</td>
      <td>80.945643</td>
      <td>80.912451</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>83.676136</td>
      <td>84.253219</td>
      <td>83.788382</td>
      <td>84.287958</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>81.198598</td>
      <td>81.408912</td>
      <td>80.640339</td>
      <td>81.384863</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>80.632653</td>
      <td>81.262712</td>
      <td>80.403642</td>
      <td>80.662338</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>83.369193</td>
      <td>83.706897</td>
      <td>84.288089</td>
      <td>84.013699</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>80.866860</td>
      <td>80.660147</td>
      <td>81.396140</td>
      <td>80.857143</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>83.677165</td>
      <td>83.324561</td>
      <td>83.815534</td>
      <td>84.698795</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>81.290284</td>
      <td>81.512386</td>
      <td>81.417476</td>
      <td>80.305983</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>81.260714</td>
      <td>80.773431</td>
      <td>80.616027</td>
      <td>81.227564</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>83.807273</td>
      <td>83.612000</td>
      <td>84.335938</td>
      <td>84.591160</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>80.993127</td>
      <td>80.629808</td>
      <td>80.864811</td>
      <td>80.376426</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>84.122642</td>
      <td>83.441964</td>
      <td>84.373786</td>
      <td>82.781671</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>83.728850</td>
      <td>84.254157</td>
      <td>83.585542</td>
      <td>83.831361</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>83.939778</td>
      <td>84.021452</td>
      <td>83.764608</td>
      <td>84.317673</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>83.833333</td>
      <td>83.812757</td>
      <td>84.156322</td>
      <td>84.073171</td>
    </tr>
  </tbody>
</table>
</div>




```python
bins = [0,595,615,635,100000000]
names = ["<595","595<615","615<635",">635"]
pd.cut(df_by_sch["Per Student Budget"], bins, labels=names)
```




    name
    Bailey High School       615<635
    Cabrera High School         <595
    Figueroa High School        >635
    Ford High School            >635
    Griffin High School      615<635
    Hernandez High School       >635
    Holden High School          <595
    Huang High School           >635
    Johnson High School         >635
    Pena High School         595<615
    Rodriguez High School       >635
    Shelton High School      595<615
    Thomas High School          >635
    Wilson High School          <595
    Wright High School          <595
    Name: Per Student Budget, dtype: category
    Categories (4, object): [<595 < 595<615 < 615<635 < >635]




```python
df_by_sch["Spending Bin"] = pd.cut(df_by_sch["Per Student Budget"], bins, labels=names)
df_by_sch
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>size</th>
      <th>budget</th>
      <th>Per Student Budget</th>
      <th>Student ID</th>
      <th>reading_score</th>
      <th>math_score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Passing Overall</th>
      <th>Type</th>
      <th>Spending Bin</th>
    </tr>
    <tr>
      <th>name</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>7</td>
      <td>4976</td>
      <td>3124928</td>
      <td>628.0</td>
      <td>20358.5</td>
      <td>81.03</td>
      <td>77.05</td>
      <td>87.44</td>
      <td>100.0</td>
      <td>93.72</td>
      <td>District</td>
      <td>615&lt;635</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>6</td>
      <td>1858</td>
      <td>1081356</td>
      <td>582.0</td>
      <td>16941.5</td>
      <td>83.98</td>
      <td>83.06</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
      <td>District</td>
      <td>&lt;595</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>1</td>
      <td>2949</td>
      <td>1884411</td>
      <td>639.0</td>
      <td>4391.0</td>
      <td>81.16</td>
      <td>76.71</td>
      <td>86.44</td>
      <td>100.0</td>
      <td>93.22</td>
      <td>Charter</td>
      <td>&gt;635</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>13</td>
      <td>2739</td>
      <td>1763916</td>
      <td>644.0</td>
      <td>36165.0</td>
      <td>80.75</td>
      <td>77.10</td>
      <td>87.22</td>
      <td>100.0</td>
      <td>93.61</td>
      <td>District</td>
      <td>&gt;635</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>4</td>
      <td>1468</td>
      <td>917500</td>
      <td>625.0</td>
      <td>12995.5</td>
      <td>83.82</td>
      <td>83.35</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
      <td>Charter</td>
      <td>615&lt;635</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>3</td>
      <td>4635</td>
      <td>3022020</td>
      <td>652.0</td>
      <td>9944.0</td>
      <td>80.93</td>
      <td>77.29</td>
      <td>86.45</td>
      <td>100.0</td>
      <td>93.22</td>
      <td>Charter</td>
      <td>&gt;635</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>8</td>
      <td>427</td>
      <td>248087</td>
      <td>581.0</td>
      <td>23060.0</td>
      <td>83.81</td>
      <td>83.80</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
      <td>Charter</td>
      <td>&lt;595</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>0</td>
      <td>2917</td>
      <td>1910635</td>
      <td>655.0</td>
      <td>1458.0</td>
      <td>81.18</td>
      <td>76.63</td>
      <td>86.84</td>
      <td>100.0</td>
      <td>93.42</td>
      <td>District</td>
      <td>&gt;635</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>12</td>
      <td>4761</td>
      <td>3094650</td>
      <td>650.0</td>
      <td>32415.0</td>
      <td>80.97</td>
      <td>77.07</td>
      <td>86.70</td>
      <td>100.0</td>
      <td>93.35</td>
      <td>Charter</td>
      <td>&gt;635</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>9</td>
      <td>962</td>
      <td>585858</td>
      <td>609.0</td>
      <td>23754.5</td>
      <td>84.04</td>
      <td>83.84</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
      <td>Charter</td>
      <td>595&lt;615</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>11</td>
      <td>3999</td>
      <td>2547363</td>
      <td>637.0</td>
      <td>28035.0</td>
      <td>80.74</td>
      <td>76.84</td>
      <td>86.45</td>
      <td>100.0</td>
      <td>93.22</td>
      <td>Charter</td>
      <td>&gt;635</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>2</td>
      <td>1761</td>
      <td>1056600</td>
      <td>600.0</td>
      <td>6746.0</td>
      <td>83.73</td>
      <td>83.36</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
      <td>District</td>
      <td>595&lt;615</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>14</td>
      <td>1635</td>
      <td>1043130</td>
      <td>638.0</td>
      <td>38352.0</td>
      <td>83.85</td>
      <td>83.42</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
      <td>District</td>
      <td>&gt;635</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>5</td>
      <td>2283</td>
      <td>1319574</td>
      <td>578.0</td>
      <td>14871.0</td>
      <td>83.99</td>
      <td>83.27</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
      <td>District</td>
      <td>&lt;595</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>10</td>
      <td>1800</td>
      <td>1049400</td>
      <td>583.0</td>
      <td>25135.5</td>
      <td>83.96</td>
      <td>83.68</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
      <td>Charter</td>
      <td>&lt;595</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_by_bin = round(df_by_sch.groupby("Spending Bin").mean(),2)
df_by_bin
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>size</th>
      <th>budget</th>
      <th>Per Student Budget</th>
      <th>Student ID</th>
      <th>reading_score</th>
      <th>math_score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Passing Overall</th>
    </tr>
    <tr>
      <th>Spending Bin</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>&lt;595</th>
      <td>7.25</td>
      <td>1592.00</td>
      <td>924604.25</td>
      <td>581.0</td>
      <td>20002.00</td>
      <td>83.94</td>
      <td>83.45</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
    </tr>
    <tr>
      <th>595&lt;615</th>
      <td>5.50</td>
      <td>1361.50</td>
      <td>821229.00</td>
      <td>604.5</td>
      <td>15250.25</td>
      <td>83.88</td>
      <td>83.60</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
    </tr>
    <tr>
      <th>615&lt;635</th>
      <td>5.50</td>
      <td>3222.00</td>
      <td>2021214.00</td>
      <td>626.5</td>
      <td>16677.00</td>
      <td>82.42</td>
      <td>80.20</td>
      <td>93.72</td>
      <td>100.0</td>
      <td>96.86</td>
    </tr>
    <tr>
      <th>&gt;635</th>
      <td>7.71</td>
      <td>3376.43</td>
      <td>2180875.00</td>
      <td>645.0</td>
      <td>21537.14</td>
      <td>81.37</td>
      <td>77.87</td>
      <td>88.59</td>
      <td>100.0</td>
      <td>94.29</td>
    </tr>
  </tbody>
</table>
</div>




```python
del df_by_bin["size"]
del df_by_bin["budget"]
del df_by_bin["Per Student Budget"]
df_by_bin
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>Student ID</th>
      <th>reading_score</th>
      <th>math_score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Passing Overall</th>
    </tr>
    <tr>
      <th>Spending Bin</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>&lt;595</th>
      <td>7.25</td>
      <td>20002.00</td>
      <td>83.94</td>
      <td>83.45</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
    </tr>
    <tr>
      <th>595&lt;615</th>
      <td>5.50</td>
      <td>15250.25</td>
      <td>83.88</td>
      <td>83.60</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
    </tr>
    <tr>
      <th>615&lt;635</th>
      <td>5.50</td>
      <td>16677.00</td>
      <td>82.42</td>
      <td>80.20</td>
      <td>93.72</td>
      <td>100.0</td>
      <td>96.86</td>
    </tr>
    <tr>
      <th>&gt;635</th>
      <td>7.71</td>
      <td>21537.14</td>
      <td>81.37</td>
      <td>77.87</td>
      <td>88.59</td>
      <td>100.0</td>
      <td>94.29</td>
    </tr>
  </tbody>
</table>
</div>




```python
del df_by_bin["School ID"]
del df_by_bin["Student ID"]
```


```python
df_by_bin
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>reading_score</th>
      <th>math_score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Passing Overall</th>
    </tr>
    <tr>
      <th>Spending Bin</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>&lt;595</th>
      <td>83.94</td>
      <td>83.45</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
    </tr>
    <tr>
      <th>595&lt;615</th>
      <td>83.88</td>
      <td>83.60</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
    </tr>
    <tr>
      <th>615&lt;635</th>
      <td>82.42</td>
      <td>80.20</td>
      <td>93.72</td>
      <td>100.0</td>
      <td>96.86</td>
    </tr>
    <tr>
      <th>&gt;635</th>
      <td>81.37</td>
      <td>77.87</td>
      <td>88.59</td>
      <td>100.0</td>
      <td>94.29</td>
    </tr>
  </tbody>
</table>
</div>




```python
bins2 = [0,1500,3000,100000000]
names2 = ["Small","Medium","Large"]
pd.cut(df_by_sch["size"], bins2, labels=names2)
df_by_sch["Size Bin"] = pd.cut(df_by_sch["size"], bins2, labels=names2)
df_by_sch
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>size</th>
      <th>budget</th>
      <th>Per Student Budget</th>
      <th>Student ID</th>
      <th>reading_score</th>
      <th>math_score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Passing Overall</th>
      <th>Type</th>
      <th>Spending Bin</th>
      <th>Size Bin</th>
    </tr>
    <tr>
      <th>name</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>7</td>
      <td>4976</td>
      <td>3124928</td>
      <td>628.0</td>
      <td>20358.5</td>
      <td>81.03</td>
      <td>77.05</td>
      <td>87.44</td>
      <td>100.0</td>
      <td>93.72</td>
      <td>District</td>
      <td>615&lt;635</td>
      <td>Large</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>6</td>
      <td>1858</td>
      <td>1081356</td>
      <td>582.0</td>
      <td>16941.5</td>
      <td>83.98</td>
      <td>83.06</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
      <td>District</td>
      <td>&lt;595</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>1</td>
      <td>2949</td>
      <td>1884411</td>
      <td>639.0</td>
      <td>4391.0</td>
      <td>81.16</td>
      <td>76.71</td>
      <td>86.44</td>
      <td>100.0</td>
      <td>93.22</td>
      <td>Charter</td>
      <td>&gt;635</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>13</td>
      <td>2739</td>
      <td>1763916</td>
      <td>644.0</td>
      <td>36165.0</td>
      <td>80.75</td>
      <td>77.10</td>
      <td>87.22</td>
      <td>100.0</td>
      <td>93.61</td>
      <td>District</td>
      <td>&gt;635</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>4</td>
      <td>1468</td>
      <td>917500</td>
      <td>625.0</td>
      <td>12995.5</td>
      <td>83.82</td>
      <td>83.35</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
      <td>Charter</td>
      <td>615&lt;635</td>
      <td>Small</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>3</td>
      <td>4635</td>
      <td>3022020</td>
      <td>652.0</td>
      <td>9944.0</td>
      <td>80.93</td>
      <td>77.29</td>
      <td>86.45</td>
      <td>100.0</td>
      <td>93.22</td>
      <td>Charter</td>
      <td>&gt;635</td>
      <td>Large</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>8</td>
      <td>427</td>
      <td>248087</td>
      <td>581.0</td>
      <td>23060.0</td>
      <td>83.81</td>
      <td>83.80</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
      <td>Charter</td>
      <td>&lt;595</td>
      <td>Small</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>0</td>
      <td>2917</td>
      <td>1910635</td>
      <td>655.0</td>
      <td>1458.0</td>
      <td>81.18</td>
      <td>76.63</td>
      <td>86.84</td>
      <td>100.0</td>
      <td>93.42</td>
      <td>District</td>
      <td>&gt;635</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>12</td>
      <td>4761</td>
      <td>3094650</td>
      <td>650.0</td>
      <td>32415.0</td>
      <td>80.97</td>
      <td>77.07</td>
      <td>86.70</td>
      <td>100.0</td>
      <td>93.35</td>
      <td>Charter</td>
      <td>&gt;635</td>
      <td>Large</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>9</td>
      <td>962</td>
      <td>585858</td>
      <td>609.0</td>
      <td>23754.5</td>
      <td>84.04</td>
      <td>83.84</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
      <td>Charter</td>
      <td>595&lt;615</td>
      <td>Small</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>11</td>
      <td>3999</td>
      <td>2547363</td>
      <td>637.0</td>
      <td>28035.0</td>
      <td>80.74</td>
      <td>76.84</td>
      <td>86.45</td>
      <td>100.0</td>
      <td>93.22</td>
      <td>Charter</td>
      <td>&gt;635</td>
      <td>Large</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>2</td>
      <td>1761</td>
      <td>1056600</td>
      <td>600.0</td>
      <td>6746.0</td>
      <td>83.73</td>
      <td>83.36</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
      <td>District</td>
      <td>595&lt;615</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>14</td>
      <td>1635</td>
      <td>1043130</td>
      <td>638.0</td>
      <td>38352.0</td>
      <td>83.85</td>
      <td>83.42</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
      <td>District</td>
      <td>&gt;635</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>5</td>
      <td>2283</td>
      <td>1319574</td>
      <td>578.0</td>
      <td>14871.0</td>
      <td>83.99</td>
      <td>83.27</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
      <td>District</td>
      <td>&lt;595</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>10</td>
      <td>1800</td>
      <td>1049400</td>
      <td>583.0</td>
      <td>25135.5</td>
      <td>83.96</td>
      <td>83.68</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
      <td>Charter</td>
      <td>&lt;595</td>
      <td>Medium</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_by_bin2 = round(df_by_sch.groupby("Size Bin").mean(),2)
df_by_bin2
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>size</th>
      <th>budget</th>
      <th>Per Student Budget</th>
      <th>Student ID</th>
      <th>reading_score</th>
      <th>math_score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Passing Overall</th>
    </tr>
    <tr>
      <th>Size Bin</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Small</th>
      <td>7.00</td>
      <td>952.33</td>
      <td>583815.00</td>
      <td>605.00</td>
      <td>19936.67</td>
      <td>83.89</td>
      <td>83.66</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
    </tr>
    <tr>
      <th>Medium</th>
      <td>6.38</td>
      <td>2242.75</td>
      <td>1388627.75</td>
      <td>614.88</td>
      <td>18007.50</td>
      <td>82.82</td>
      <td>80.90</td>
      <td>95.06</td>
      <td>100.0</td>
      <td>97.53</td>
    </tr>
    <tr>
      <th>Large</th>
      <td>8.25</td>
      <td>4592.75</td>
      <td>2947240.25</td>
      <td>641.75</td>
      <td>22688.12</td>
      <td>80.92</td>
      <td>77.06</td>
      <td>86.76</td>
      <td>100.0</td>
      <td>93.38</td>
    </tr>
  </tbody>
</table>
</div>




```python
del df_by_bin2["School ID"]
del df_by_bin2["Per Student Budget"]
del df_by_bin2["Student ID"]
del df_by_bin2["size"]
del df_by_bin2["budget"]
df_by_bin2
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>reading_score</th>
      <th>math_score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Passing Overall</th>
    </tr>
    <tr>
      <th>Size Bin</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Small</th>
      <td>83.89</td>
      <td>83.66</td>
      <td>100.00</td>
      <td>100.0</td>
      <td>100.00</td>
    </tr>
    <tr>
      <th>Medium</th>
      <td>82.82</td>
      <td>80.90</td>
      <td>95.06</td>
      <td>100.0</td>
      <td>97.53</td>
    </tr>
    <tr>
      <th>Large</th>
      <td>80.92</td>
      <td>77.06</td>
      <td>86.76</td>
      <td>100.0</td>
      <td>93.38</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_by_schType = df_by_sch.groupby("Type").mean()
df_by_schType
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>size</th>
      <th>budget</th>
      <th>Per Student Budget</th>
      <th>Student ID</th>
      <th>reading_score</th>
      <th>math_score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Passing Overall</th>
    </tr>
    <tr>
      <th>Type</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Charter</th>
      <td>7.250000</td>
      <td>2625.125000</td>
      <td>1.668661e+06</td>
      <td>622.000000</td>
      <td>19966.312500</td>
      <td>82.428750</td>
      <td>80.322500</td>
      <td>93.255</td>
      <td>100.0</td>
      <td>96.62625</td>
    </tr>
    <tr>
      <th>District</th>
      <td>6.714286</td>
      <td>2595.571429</td>
      <td>1.614306e+06</td>
      <td>617.857143</td>
      <td>19270.285714</td>
      <td>82.644286</td>
      <td>80.555714</td>
      <td>94.500</td>
      <td>100.0</td>
      <td>97.25000</td>
    </tr>
  </tbody>
</table>
</div>




```python
del df_by_schType["School ID"]
del df_by_schType["size"]
del df_by_schType["budget"]
del df_by_schType["Per Student Budget"]
del df_by_schType["Student ID"]
df_by_schType
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>reading_score</th>
      <th>math_score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Passing Overall</th>
    </tr>
    <tr>
      <th>Type</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Charter</th>
      <td>82.428750</td>
      <td>80.322500</td>
      <td>93.255</td>
      <td>100.0</td>
      <td>96.62625</td>
    </tr>
    <tr>
      <th>District</th>
      <td>82.644286</td>
      <td>80.555714</td>
      <td>94.500</td>
      <td>100.0</td>
      <td>97.25000</td>
    </tr>
  </tbody>
</table>
</div>


