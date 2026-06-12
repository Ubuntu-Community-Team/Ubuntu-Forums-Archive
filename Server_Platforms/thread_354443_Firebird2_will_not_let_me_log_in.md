---
title: "Firebird2 will not let me log in"
date: 2007-02-06
forum: Server Platforms
---

### Post by rphelps on 2007-02-06
I recently installed Firebird2 on Dapper.  I now am trying to use the 'gsec' utility to change the sysdba password. However whenever I try to use gsec as in 

gsec -user sysdba -password <the password> 

I get the following response.

"Your user name and password are not defined. Ask your database administrator to set up a Firebird login."

I get the same response when I try to connect to the example  emplyee.fdb database.

I know the username and password are valid as I see them in the "SYSDBA.password" file. 

Any suggestions.

---

### Post by rphelps on 2007-02-11
I fixed my problem by simply reinstalling Firebird,  

For those of you who are planning on installing it. When the Synaptic package manager starts the install make sure you click the little triangle to open the terminal window because you will be asked to enter a  sysdba password which you will use to admin, create, test your installation.

---

