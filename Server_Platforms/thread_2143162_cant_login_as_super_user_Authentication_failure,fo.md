---
title: "cant login as super user Authentication failure,for a previously accessed password"
date: 2013-05-08
forum: Server Platforms
---

### Post by sajithmohan on 2013-05-08
i cant login as super user using su command ,previously it was successful and i am sure that password is correct,previosly there was an issue by changing file permission of www folder and i follow this link to correct it[http://sysadminnotebook.blogspot.in/...ssions-to.html]("http://sysadminnotebook.blogspot.in/2012/06/how-to-reset-folder-permissions-to.html") after that i cant login as su

---

### Post by lisati on 2013-05-08
Do you have any success with *[sudo -i]("https://help.ubuntu.com/community/RootSudo")*  ?

---

### Post by sajithmohan on 2013-05-08
NO i can access root as driect login

---

### Post by Elfy on 2013-05-08
Logging into a terminal or into your GUI?

You need to give a lot more information for people to help you.

---

### Post by chrisguk on 2013-05-08
If you are able to log into your normal user, are you able to issue the following command?

sudo passwd root

---

