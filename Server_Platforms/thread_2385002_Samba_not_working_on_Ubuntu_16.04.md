---
title: "Samba not working on Ubuntu 16.04"
date: 2018-02-15
forum: Server Platforms
---

### Post by 5circles on 2018-02-15
I have two Ubuntu boxes on my LAN and several Windows machines.  

The older Ubuntu box is running 14.04, and its Samba is running fine (sort of).  Within Nautilus, it can see itself, a NAS server, a Windows machine, and the other Ubuntu box.  Shares on itself are visible, with a couple of peculiarities. I don't know whether these existed before - I'm more concerned about getting the newer (hardware and OS) Ubuntu box working, but perhaps these notes help.  The NAS is visible, but the shares aren't.  I don't know if that is due to changes on the NAS.  The shares on the windows machine aren't visible.  The shares on the other Ubuntu box aren't visible.  And one of the shares that I can see from Windows (a user's home directory) isn't visible.

The newer Ubuntu box is running 16.04.  Nautilus shows a slightly different set of high level links - presumable that's related to 16.04 vs 14.04.  The Windows Network has LAN and WORKGROUP (whereas the older box has just LAN - which is what I use for all machines).  I think that WORKGROUP relates to a media server on a recently acquired router whose name I can't change,  but it's odd that the other box doesn't show this.  I can't go any lower than the workgroups.

From Windows, I can see the additional share for the user, and I've just noticed that the content for [homes] is the same as for [user].  This is true on the old Ubuntu box too.

Both Ubuntu machines are running Samba 2:4.3.11 and both have the same smb.conf.

The old box was originally named Edradour, and was renamed Edradour-old when the new box was installed and named Edradour.

I'm at a loss what to try next.

Thanks!

---

### Post by wildmanne39 on 2018-02-15
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by darkod on 2018-02-15
To be honest, I didn't understand anything...

Ubuntu Server is command line only, and you are obviously running either an added GUI or Ubuntu Desktop. At the end of the day, I wouldn't be worried how Nautilus shows things, you are interested for clients to see the shares, right?

Is Samba on the 16.04 providing the shares? Because you also mention a NAS. What has the NAS to do with it?

---

### Post by 5circles on 2018-02-15
The thread was moved to Server Platforms by a moderator -  "more appropriate forum".  Perhaps that's true, but it might prevent people who can help seeing it.

@darkod: Ubuntu server isn't necessarily command line only.  You can add GUI features to a LAMP server, or add LAMP to a desktop.  For me, that's helpful because I use Ubuntu for development and I'm not active on the machine every day.   

What do you mean by "I don't understand anything"? You don't understand my descriptions or what?  The NAS is relevant (or not) because it's a different machine (running Linux actually).  At the moment I'm trying to move files between the Ubuntu machines, but I'm also trying to move between Windows and NAS, and shortly to run Netbeans on Windows integrated with Ubuntu as I've done before.  This current issue just seems to be about Samba.

Thanks

---

### Post by darkod on 2018-02-15
I won't go into the part about adding GUI to linux servers. I know you can add whatever you want on ubuntu server but if you add the gui use ubuntu desktop instead. That was my point...

Correct, I didn't understand your descriptions (what the problem exactly is).

When you say moving files between the ubuntu machines, you mean one acts as samba server and the other as client that wants to copy files from the server, right?

Did you try mounting the share in terminal (command line), or only by Nautilus?

In Nautilus did you try to use Connect to Server and use the IP of the server?

And FYI, moving files between linux is always better with nfs shares, not samba/cifs. If windows needs to access the same data, it's more complex because windows does need the samba. But you can share the same path on the server with both samba and nfs, so depending on the client OS you can access it in a better way...

PS. On the machine acting as client you do have the smbclient package installed, right?

---

### Post by Morbius1 on 2018-02-15
Based on the lack of information in the original post I know I'm going to regret this but let's see if we can't get the two Linux machines to work together first. Samba between 2 Linux machines is easier than between Linux and Windows.

From the Ubuntu 16.04 machine run these commands and post the output:
```
testparm -s
```
```
net usershare info --long
```
```
hostname
```

---

### Post by Chaim_Eliyah on 2018-05-01
Thanks, that helped get enough information to solve the problem. Yes I realize I'm a necromancer.

---

