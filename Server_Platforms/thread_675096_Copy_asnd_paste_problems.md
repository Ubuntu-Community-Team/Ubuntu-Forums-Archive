---
title: "Copy asnd paste problems"
date: 2008-01-22
forum: Server Platforms
---

### Post by hooligan36 on 2008-01-22
I have worked on a new web page to replace the index.html file. I have tried to move it from my gutsy desktop install on my ;aptop to my gutsy server. Everytime I try to copy it from my desktop and paste it into the server file, I get an error saying that I do not have permission for that function. I only have one user setup on the laptop and one use on the server but both are different names. 

I have also tried to copy a file from the laptop and paste it on an XP machine and got the same error.

I figure it maybe a noob question, but I have searched and browsed and have not found an answer.

Thanks for any help.

---

### Post by smileypaul on 2008-01-22
Its a permissions error... be weary of this answer .. 

but 

sudo chmod o+w /pathtofile/index.html

that will allow "others" to write to that file... be aware, that others include all others, not just you.

---

