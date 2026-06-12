---
title: "Postfix &amp; MySQL"
date: 2007-03-23
forum: Server Platforms
---

### Post by sparty2809 on 2007-03-23
I have postfix configured with mysql  What I want to do is take all of the users in the mysql database and forward it to the email that they specify in the mysql database.  Any ideas how I can do that?

---

### Post by conjur3r on 2007-03-24
You can accomplish that using a server side script (php, perl, etc...).  

1. Query the database for a list of users (using SQL).
2. Query the database for the email recipient
3. Format #1 to some readible text and send to email #2
4. Cleanup!

---

