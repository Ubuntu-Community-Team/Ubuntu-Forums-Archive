---
title: "Maxed CPU Usage"
date: 2010-03-05
forum: Server Platforms
---

### Post by markvanwyk on 2010-03-05
Hi

I have the below server running Ubuntu 9.10 64bit

2 x Quad Core 2.66Ghz CPU's
18GB DDR

I have installed Apache2 , php5, mysql, freetds pear and pear Spreadsheet Excel Viewer. The problem I have is on my php website I extract data from MSSQL and present it in the Excel Viewer on the website but as soon as I do this the CPU's jump to max (check on top) It only happens when I need to extract and view the data - i am not sure where to start looking at as there are many different web answers for this

Please can you assist
Regards
Mark

---

### Post by dragos2 on 2010-03-05
> **markvanwyk said:**
> Hi

I have the below server running Ubuntu 9.10 64bit

2 x Quad Core 2.66Ghz CPU's
18GB DDR

I have installed Apache2 , php5, mysql, freetds pear and pear Spreadsheet Excel Viewer. The problem I have is on my php website I extract data from MSSQL and present it in the Excel Viewer on the website but as soon as I do this the CPU's jump to max (check on top) It only happens when I need to extract and view the data - i am not sure where to start looking at as there are many different web answers for this

Please can you assist
Regards
Mark

You can start the process with a lower priority, like 15.

Also how big is the data to be extracted ?

Another thing that you can do is to set processor affinity for that activity and it won't
impact the whole system.

---

### Post by markvanwyk on 2010-03-08
Hi

Thank for the details - There is no need to change the systems priority as this is all the system does, The excel file size ranges between a few KB to 1 meg of data (excel lines around 50 or more dependent on date selection) and takes around 25 min to complete

Do you know of any other way I can speed this up

Kind Regards 

Mark

---

### Post by markvanwyk on 2010-03-09
Problem Solved - I have replaced the Pear OLE with an older version(0.5) as well as the Pear Spreadsheet Excel Writer with an older version (0.9.1) - all works great 9MB Excel file data extracts in 16 sec  

:P

---

