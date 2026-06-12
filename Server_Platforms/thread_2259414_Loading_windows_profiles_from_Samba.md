---
title: "Loading windows profiles from Samba"
date: 2015-01-04
forum: Server Platforms
---

### Post by dirk14 on 2015-01-04
Hello, 

First i have just created an account here on Ubuntuforums and if i have posted in the wrong thread. Sorry!

I like to work with Windows and Linux Servers. There is so much to learn.

i am following my own project at home with the help of Virtual Box.

Lets say we have a company called timing.

They have 1 Windows 2008 R2 PDC server and 1 Windows 2008 R2 Addtional Server for replication and 1 Ubuntu 14.0.4.1 server.

They have als have client machine that runs Windows 7 and is connected to the windows domain

What i want to do is that the Windows Active directory user picks his profile from the ubuntu server that is running samba.

I have done the following:

I always used Likewise-open to join the ubuntu server to the windows domain. Now that the repository is gone in version 14.x.x. I want to use powerbroker identity service to join the domain. I still have to do that (or does have somebody a better idea)

Now comes the point that i must create User and Home folders in the ubuntu server.

I have searched the internet and one says you must make your ubuntu server a pdc or you must configure somethinh in your smb.cond etc..

There are a lot of tutorials, but i dont know if it works for me and i dont know which tutorial is the best. So thats why i have come to this forum to seek knowledge from you guys.

I am sorry if there are topics which have the same problem as me.

thanx!

---

### Post by dirk14 on 2015-01-04
Really

105 views and no one has an answer?

---

### Post by MAFoElffen on 2015-01-04
I just read this for the 1st time (my out). So what you want to do (in MS Server verbage) is implement roaming profiles for your Windows clients, but keep them stored in a separate SMB share. Do-able, but...

Having just updated my MOAC certs from Server 2008R2 and Workstation 7 to Server 2012R2 and Workstation 8.1... somethings have changed, so 7 and 8.x profiles are not interchangeable. There is a work-around to separate out per-version roaming profiles.

So just an SMB share (on Ubuntu). Well from M$'es own doc's on that:
> 
Step 3: Create a file share for roaming user profiles


If you do not already have a separate file share for roaming user profiles (independent from any shares for redirected folders to prevent inadvertent caching of the roaming profile folder), use the following procedure to create a file share on a server running Windows Server 2012.


---

