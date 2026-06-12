---
title: "Update Problem"
date: 2006-08-30
forum: Server Platforms
---

### Post by DtJee on 2006-08-30
Just a short question.
I am running a few Ubuntu 6.06 Server here for testing. I want to place them in the productive line, but there´s one question. What about updates.
Do I have to run from computer to computer and update Ubuntu Packages (Security/Updates what ever) or is there something like a centralized update function.
It would be cool if had a "CONTROL"-Server which downloads the necessery updates and deliveres them to every single server. 
So we could save some bandwith and not every machine must download a new kernel if its released. Further it would be real cool if I had some kind of overview, which server is in which state...

Perhaps somehting like this already exists.. Perhaps not... 

Any ideas???

---

### Post by Jussi Kukkonen on 2006-08-30
Take a look at apt-proxy. It only downloads whatever clients ask for (so you don't have to mirror the whole repository), but the file is downloaded only once.

---

### Post by DtJee on 2006-08-31
Sounds interessting.. I'll take a look. Can I enable something like autoupdate for dapper. I've seen that something like this should be included in Edgy. 
Perhaps a cronjob.. or something like this.

---

### Post by Jussi Kukkonen on 2006-08-31
look at cron-apt for the clients -- but remember to think about testing. Autoupdating servers without testing the updates might not be the smartest move...

---

### Post by DtJee on 2006-08-31
Yes you´re right. But it would be cool if, important security updates would be immidiatly be mentioned on a central server.. or via mail to admin etc.  would be a nice feature for ubuntu server...

thanks for your help

---

### Post by chrisfay on 2006-08-31
You could cron a simple apt-get update updgrade bash script that would pipe the output into an email. Unless you add the -y flag you will be prompted before the updates actually install allowing you to check the emails output and deciding later what to actually install. 

Rudimentary I know, but works for me.

---

### Post by DtJee on 2006-09-12
Sounds interessting... I will give this one a try... but a real "Managment Console" would be real cool...

---

