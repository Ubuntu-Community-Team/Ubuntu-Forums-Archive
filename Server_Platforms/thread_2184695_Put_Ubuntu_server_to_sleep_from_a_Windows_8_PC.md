---
title: "Put Ubuntu server to sleep from a Windows 8 PC"
date: 2013-10-30
forum: Server Platforms
---

### Post by applewood1 on 2013-10-30
I have been using Windows PC’s for years and have finally seen the light.

I have built myself a server using Ubuntu 12.04 LTS and it is performing well.
I have installed ethtool to wake the server from sleep using a Windows 8 PC and this works fine.
I have the power button set to make my server sleep and this works OK as well.
What I now need is to be able to send the server to sleep from my Windows 8 PC.
I have googled it and I can find lots about waking a computer but not putting it to sleep.

I would like to use a windows batch file to send the appropriate command to my server if possible but I don’t know what commands to put on the server or where to put them.

As I say I am new to Linux and any help would really be appreciated

---

### Post by josgeluk on 2013-10-30
You could cobble something together like this:
From the Windows PC, send an empty file to the server, let's say /path-to-file/switch.
On the server, write a script like this: 

if [ -f /path-to-file/switch ]
then
rm /path-to-file/switch
pm-suspend               # or whatever your suspend command looks like
fi

and have cron execute this script every minute.

---

### Post by coffeecat on 2013-10-30
Not a Forum Feedback & Help Thread.

*Thread moved to **Server Platforms**.*

@applewood1, I've edited your thread title to replace PC with server. Good luck with getting the solution you need, and welcome to the forum.

---

### Post by applewood1 on 2013-10-31
Thanks for your quick reply but Linux is totally alien to me.
I haven't any idea how to do what you suggest.

---

### Post by josgeluk on 2013-11-01
No problem. PM me and I'll tell you how to set up things on the Linux side.

---

