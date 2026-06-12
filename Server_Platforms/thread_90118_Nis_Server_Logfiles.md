---
title: "Nis Server Logfiles"
date: 2005-11-14
forum: Server Platforms
---

### Post by khaledagha on 2005-11-14
Hello All
I use NIS server with UBUNTU 5.04 and I need to get a report of users hows entered to may domain ,actually I need to now the time of login and logout for every user .
Thanks

---

### Post by Nixed0 on 2005-11-14
Quick easy listing `ypcat passwd` 

You could create some scripts to parse the data in /var/log/wtmp, using the output from the "last" command. To collect login / logout times.

Also take a look at the "acct" package, available in apt. The command "ac -dp" will total all the users that have logged into that system.

---

### Post by khaledagha on 2005-11-15
Thank you Nixed0 
The command ac –dh is very interesting , , the problem I need to now , when I have the user server it must serve me to get all information from it , I don’t need to go from one client to anthers to gather information that I needed , 
[COLOR="Blue"]is there any way to make log file for nis server [/COLOR]

---

