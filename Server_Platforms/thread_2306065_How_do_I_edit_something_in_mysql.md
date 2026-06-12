---
title: "How do I edit something in mysql?"
date: 2015-12-11
forum: Server Platforms
---

### Post by Higgins909 on 2015-12-11
I made a premade schemas through mysql workbench.  I can kinda find the value I want to edit, but I can't.
Lets see, its something like schema/account/columns/money (this is for a game)
I can select rows 1000 of "money" but I don't get how I would find my money if there were other users.
Since I'm the only user it only shows 1 value and that matches to to my in game money.
But I can't edit this value, it says read only?  How would I find this value if there were other users?
It don't really seem to say it's linked to my account.

Thanks,
Higgins909

---

### Post by cariboo on 2015-12-12
you should have set up a root account when you installed mysql, use that user to make changes to your database.

---

### Post by Higgins909 on 2015-12-13
Turns out I'm just really bad at using MySQL Workbench... or MySQL in general.
Was able to do it... Just clicking on a sub table instead of a table? 
schema>tables>table>subtable
exile>tables>accounts>money
right clicked accounts...  Probably not supposed to be asking such questions here... but idk where I would ask then.
-Solved-

---

