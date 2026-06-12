---
title: "Small Office Network OPENLDAP or other solutions"
date: 2010-07-16
forum: Server Platforms
---

### Post by david.garceau on 2010-07-16
Hey guys, heres my situation...

Small office... 20-30 computers all windows based. xp/vista/windows 7
3 Servers running ubuntu 10.04... 1 domain controller, and two file servers with samba
We want to be able to login once in the morning, and then not have to worry about users/passwords at all throughout the day.
So i was thinking that i could setup a PDC and then make the two filservers both BDC's and use ldap to authenticate everything... Would this even work out? and is there a better way to do it?

---

### Post by david.garceau on 2010-07-17
is this in the right forum? :(

---

### Post by naelq on 2010-07-17
yes it is possible, & yes you are in the right forum section :)
one thing to consider though, before going the "manual-way", what about managing the system afterwards? for some it is an easy task, for others it is not, i don't know about you, but i would consider one of the following or the like.. :)
* eBox, ubuntu based, yet you can install it on your current system (back config 1st..)
* ClearOS, CentOS based
* SME Server


i hope this helps ;)

nael

---

### Post by david.garceau on 2010-07-17
honestly, the problem that im having is getting the fileservers to be authed from ldap. The only thing i cannot do is change my fileservers to something different than ubuntu 10.04, over 8tb of data on each of them, and i really do not feel like trying to format them and change os's or anything major to them. The domain controller is brand new so im not worried about what i do to it. I have tried ebox, i can get the pdc working, but again i cannot figure out how to get my fileservers to auth.

---

### Post by kevinthecomputerguy on 2010-07-17
Give this a read
Page 3 atleast (html)
[http://woodel.com](http://woodel.com)
It might help you with the auth part, pass-thru authentication. Atleast for the shares.
-Kev

---

### Post by david.garceau on 2010-07-19
kevin i gave it a quick read, but i couldnt really find anything that suited me.

Just to sum it up again since i dont feel like i asked the question correctly...

i have 3 servers. 

One is a currently working pdc samba/ldap server
Two are samba fileservers.

I need to find out how to make the two fileservers use the ldap server to authenticate users that logged in during the morning hours

Goal... I want the users to be able to login in the morning, and not have to worry about logging into the fileservers.

---

### Post by david.garceau on 2010-07-19
looking around i am seeing a lot of information on using kerberos to do what i want, should i do it this way or is there another way using just samba?

---

### Post by mcarrara on 2010-07-19
Why do you think you need 2 BDC, LDAP for 20-30 users?  I have about 300 users and I am using Samba with a TBD backend.  Much simpler than what you are proposing.  If the computers are located in three different offices with a WAN connection maybe BDC's are needed but I don't see where you need them unless I am missing something.

Mark

---

### Post by david.garceau on 2010-07-19
Well i am not sure what i need, which is why i asked for other solutions. The end goal is to have my PDC and my two other file servers all using same users/passwords. So that when someone logs on in the morning, they do not have to enter the passwords for the fileservers. I want it so that i can go to my pdc, and create a new user and password, which will then carry over to the two file servers also.

---

### Post by mcarrara on 2010-07-19
I am using Samba with 1 PDC running the TBD backend.  I several other Ubuntu servers running Samba and Winbind pointing to the PDC.  Staff and students only have to log in one to the PDC and they are good to go.  We have both file and print servers all working with a single sign on.  My clients are all Windows XP pro.  You will need the pro version of Windows because the Home version will not be able to connect to a domain.

Mark

---

### Post by david.garceau on 2010-07-19
I see, just to clarify.

Your staff and students log on in the morning to the pdc. Once they do that, then they have access to the file servers. Also are there folders that the staff have that the students dont have access to. 

The way my current network was setup was that i had to create the account on the pdc, then i would have to map the fileservers and login using a root account, then it would remember that root user and password, and it would work like that. I want to avoid having to manually login to the fileservers using a root account, so that the account is all set once i create it. If this is all true, could you point me in the right direction of how to begin to set it up that way?

---

### Post by mcarrara on 2010-07-20
As long as they stay on the same computer they do not have to long in a second time.  Yes there are files that teachers can access RW and students are R only.  There are some that students can't even see.

I have been using Samba for three years and playing with it for another two and I am still learning.  The basics are easy, once you get your head around the concepts, including how Windows runs a network.  I have found the documentation on the Samba site to be voluminous and dense, but not 100% complete.  I continue to post here when I run into issues.

On the Samba site is a good book for your situation, Samba by Example.  It can be downloaded as a PDF and takes you through the life of a company from a small start up to a multi location 2000 user gaint.  All using Samba.

Mark

---

