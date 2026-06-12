---
title: "SQL Problem Driving me Crazy"
date: 2008-01-05
forum: Server Platforms
---

### Post by Black Mage on 2008-01-05
I'm having this problem with MS Access where I want to get values in between two dates, but it never gets the values in between the dates and when I use the NOT BETWEEN, it gets every value, including he ones in between the dates. No errors are thrown. My code, which is Java, looks like this:

```

java.sql.Date date1 =java.sql.Date.valueOf("2008-01-01");
				java.sql.Date date2 =java.sql.Date.valueOf("2008-01-31");
				//s.execute("SELECT Hours FROM Clock WHERE Clocked_date >= "+date1+" and Clocked_date  < "+date2+" and User_ID="+218+"");
				s.execute("SELECT Hours FROM Clock WHERE User_ID="+id+" and Clocked_date NOT BETWEEN "+date1+" AND "+date2+"");


```

Anyone have any suggestions?

---

### Post by GWoitena on 2008-01-05
Your SQL looks good with the exception that the second "and" reads date < whatever so the data will not include the end date.

I'm thinking there is an issue with the data types in the table.  Be sure you have all the fields using the correct data type for what you want to do.

Hope this helps.

---

### Post by koenn on 2008-01-06
try "#date1#" i.s.o. "+date1+"

---

### Post by Black Mage on 2008-01-10
yea, that work, thanks.

---

