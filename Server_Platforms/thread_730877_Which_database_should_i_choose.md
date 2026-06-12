---
title: "Which database should i choose?"
date: 2008-03-21
forum: Server Platforms
---

### Post by Guradian on 2008-03-21
Hi, i'm new to linux, and i have a project to import some data to database, and i have no idea about which one should i choose in ubuntu,
now i'm use xubuntu 710 and we have almost 100,000,000 per month
thanks for any suggestions

---

### Post by keratos on 2008-03-21
OpenOffice BASE

no brainer

---

### Post by rickyjones on 2008-03-21
> **Guradian said:**
> Hi, i'm new to linux, and i have a project to import some data to database, and i have no idea about which one should i choose in ubuntu,
now i'm use xubuntu 710 and we have almost 100,000,000 per month
thanks for any suggestions

You are going to have to provide a lot more information here.

What kind of data?
How much data?
Where is the data from?
Is the data being accessed by other applications?
Is the data being accessed by, say, a website?
How do you wish to interact with the data?
What is the "100,000,000" number in regards to?

For example, if you wish to host a database that will store financial information from an e-commerce website then I highly recommend using MySQL. I've had great experiences with it in the past.

Please provide more information and the database experts might be able to help you out.

Thanks,

-Richard

---

### Post by Guradian on 2008-03-22
> **rickyjones said:**
> You are going to have to provide a lot more information here.

What kind of data?
How much data?
Where is the data from?
Is the data being accessed by other applications?
Is the data being accessed by, say, a website?
How do you wish to interact with the data?
What is the "100,000,000" number in regards to?

For example, if you wish to host a database that will store financial information from an e-commerce website then I highly recommend using MySQL. I've had great experiences with it in the past.

Please provide more information and the database experts might be able to help you out.

Thanks,

-Richard

it will store some dhcp records, which is imported by a program written by python. also will access it by python program.  and the records nearly 100,000,000 per month
sorry for my poor english

---

### Post by Mithrilhall on 2008-03-22
I'll second MySQL.

---

### Post by Oldsoldier2003 on 2008-03-22
MYSQL is definitely the best option in my opinion.

---

### Post by keratos on 2008-03-22
Oh, well for that MySQL definitely.

BASE for things like personal CD collections, record keeping etc. For "stuff" like this though, MySQL as suggested above.

[http://mysql-python.sourceforge.net/](http://mysql-python.sourceforge.net/)

---

### Post by anantshri on 2008-03-22
any one working on postgresql,

heard that its a lot better then mysql.

---

### Post by Guradian on 2008-03-22
thanks for replies, i'll have a test on mysql and postgresql.
and we want to store the records at least 2 years, that means there could be 24 billion record. how the performance of mysql in this situation.

---

### Post by keratos on 2008-03-22
i think the performance of 24 billion records would test ANY system.

I mean 24 BILLION.

R u serious !?

:lolflag:

---

### Post by anantshri on 2008-03-27
> **Guradian said:**
> thanks for replies, i'll have a test on mysql and postgresql.
and we want to store the records at least 2 years, that means there could be 24 billion record. how the performance of mysql in this situation.

in that case i would suggest postgresql or oracle.

one more option is to go for mysql enterprise version.

---

### Post by keratos on 2008-03-27
> **anantshri said:**
> in that case i would suggest postgresql or oracle.

one more option is to go for mysql enterprise version.

yep

Oracle 8 is out and this has excellent capabilities...

but its a REAL beast...

if you can Master the Oracle suite then mega bucks await you.

good luck.

---

### Post by Poleh on 2008-03-29
I think that should be 2.4 Billion, but that's still a lot :D

---

### Post by keratos on 2008-03-29
> **Poleh said:**
> I think that should be 2.4 Billion, but that's still a lot :D

:lolflag: yep, still amazing amount of data. I mean that's more data than the entire UK populations National Health & Social Security records combined. 

(nice avatar btw)

---

### Post by Poleh on 2008-03-31
> **keratos said:**
> :lolflag: yep, still amazing amount of data. I mean that's more data than the entire UK populations National Health & Social Security records combined. 

(nice avatar btw)

Well, perhaps more records, not necessarily more data :)

Thanks RE the avatar, I take it you recognise it then?

---

