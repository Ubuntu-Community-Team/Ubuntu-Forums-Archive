---
title: "see history of user logon's"
date: 2010-08-06
forum: Security
---

### Post by benj.545 on 2010-08-06
I think someone hacked my server and I'm wondering if it's possible to view the possible the past user logons? any help?

---

### Post by kvtb on 2010-08-06
you can use the 'last' command in a terminal window

---

### Post by benj.545 on 2010-08-06
wow, thanks!:p

---

### Post by benj.545 on 2010-08-06
how far back will that show me?

---

### Post by amite on 2010-08-06
try
 $man last
u will get ur answer

for ur purpose do this:
$last -n 10 
10 or any number

---

### Post by benj.545 on 2010-08-06
thanks, i think this problem is solved

---

### Post by bodhi.zazen on 2010-08-06
You may also wish to look at the log files, depending on what services you are running of course.

---

