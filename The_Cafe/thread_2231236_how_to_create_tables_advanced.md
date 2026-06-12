---
title: "how to create tables advanced"
date: 2014-06-24
forum: The Cafe
---

### Post by shad2 on 2014-06-24
how can i create another two rows for each of the 1.1.1 and 1.1.2 rows in the following example
I have tried and it is not coming out 
<!DOCTYPE html>
<html>
<head>
<title></title>
<style>
table { width:auto; height:1px; table-layout:auto; border-collapse:collapse;
margin-left:20px; border:1px solid black; }
td, th { width:50px; height:1px; overflow:hidden; visibility:visible;
border:1px solid black; padding:5px; background:gold;
text-align:center; vertical-align:middle; text-indent:5px; }
</style>
</head>
<body class="noscroll">

<table>
<tr> <td rowspan="2">1.1</td> <td>1.1.1</td></tr><tr><td>1.1.2</td></tr> 
 
</table>

</body>
</html>

---

### Post by waffen on 2014-06-24
and?? whats the Ubuntu related question???

---

### Post by yancek on 2014-06-24
I'm not really sure what you are trying to do but, if you want "1.1, 1.1.1 and 1.1.2" as separate rows change your entry to:

```
<table>
<tr> <td>1.1</td></tr><tr> <td>1.1.1</td></tr><tr><td>1.1.2</td></tr>

</table>
```

If that's now what you want, post more information.  You could probably get some good beginner information on html at w3schools as well as a number of other sites.

---

### Post by oldos2er on 2014-06-24
Not an Ubuntu support question; moved to Cafe.

---

### Post by Old_Grey_Wolf on 2014-06-25
I am also not sure what you are trying to do. If you want a line break within a table use <br>.
```
<table>
<tr> <td>1.1<br>whatever you what</td></tr><tr> <td>1.1.1<br>whatever you what</td></tr><tr><td>1.1.2<br>whatever you what</td></tr>

</table>
```

---

