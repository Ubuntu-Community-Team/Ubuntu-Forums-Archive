---
title: "ubuntu destop raid to server"
date: 2015-04-07
forum: Server Platforms
---

### Post by amerinde on 2015-04-07
i think this might be a tricky question, but.. i set a computer up with ubuntu desktop and made a raid5 with mdadm... if i delete the desktop and install server, will the raid still exist?

---

### Post by darkod on 2015-04-07
In general yes, but it depends on the setup you have and what you want to do during the server os installation.
For example where is your root partition? In the raid or outside?

---

### Post by amerinde on 2015-04-07
i boot off a 120G. ssd (sdf1) , my raid5 (md0) consists of (sd[abcd]1) the system and root (everyhting is on sdf*) The raid is for back up and file storage, right now mainly music and movies. I want to open it up so i and friends can access online(anywhere).

---

### Post by darkod on 2015-04-07
In that case you can keep the raid and the data. If I'm not mistaken the install process will detect the raid and ask you if you want to activate it. Say yes. Continue with the install and make sure to select sdf as destination. Of course you will have to format sdf to make clean install. If you want to keep any data or config files from it make a copy first.
That's about it. The process is more or less the same regardless if you have existing raid.

---

### Post by amerinde on 2015-04-07
wow.. u are fast.and thank you... your opinion, should i switch from desktop to server or not... i have read up, only difference i c, i desktop gives the gui.. are there actual advantages to switch to server.. i use webmin to access my ??server/desktop?? so i dont need gui.

---

### Post by tgalati4 on 2015-04-08
You can leave the desktop installation and simply install the web server and any other services that you need.  With an i7, there is very little performance difference between the desktop and server.  When you log in, you can select "terminal session" and not even activate the desktop--this is known as single-user mode and will save some CPU cycles.  I would only install the server if the machine is truely a headless or rack-mounted server, where you don't need the desktop.  But for a desktop machine, you may want the gui so you can try out new software, games, and easier management, etc.

---

### Post by MAFoElffen on 2015-04-08
+1...

Darkod answered your question by what and how you had asked... But tgalati4 answered it to what you might only really need, would be less work for you to implement and what you are already might be more familiar with.

I was thinking the same as I was reading your posts. There is no need for you to get rid of something that is already working, just to add services to it. What you are talking about is not much overhead on "your" hardware and is serving a limited user-base. The server edition and desktop edition is on the same base-core system. You only need to install the additional services you need to add... what you want to offer. Without the GUI would be more secure, but with the limited access you want to offer... not as much a concern.

---

### Post by amerinde on 2015-04-09
darkrod, u were half right, half wrong... during setup, it saw the raid. so i kept it... but after boot, i still had to edit fastab(??) for the system to recognise the raid. but the files were no longer there... good thing for backups... atleast i didnt have to do the wait for it to configure the raid.

---

### Post by amerinde on 2015-04-09
and to tgalati4 n MAFoElffen, wish u would have said so earlier.. cause now i got a problem with getting access from my windows 7 pc.. On the server, i have read write access, but in windows, i can only access the files. smb.conf has me as write... but it doesnt work.. i keep getting access denied..should i close here and open new thread?

---

### Post by darkod on 2015-04-09
> **amerinde said:**
> darkrod, u were half right, half wrong... during setup, it saw the raid. so i kept it... but after boot, i still had to edit fastab(??) for the system to recognise the raid. but the files were no longer there... good thing for backups... atleast i didnt have to do the wait for it to configure the raid.

If you needed to adjust fstab to automount the array at boot, that's one thing. But for the data to be deleted, that should not happen. Is it possible that you formatted the array while keeping it? Not that it makes a difference now, because you already retrieved your backup.

As for samba, I am not expert on it, but does the windows user match the samba and/or linux user on the server? It needs to match. Also, a samba user is considered different from the linux user, so you might need to create both.

---

### Post by tgalati4 on 2015-04-10
Often when trying to achieve one objective in Linux, you destroy everything else.  I call this the Burn-Down Principle.  Yes, backups are important.  Understand that when you have something working in Linux and you want to make a change, there is a risk of destroying everything.  In these forums you will frequently see the phrase:  "When you break Linux, at least you get to keep the pieces."

In theory, if you have a working data RAID5 and you perform an update or change the OS, you should be able to reconnect to that data RAID5.  In practice, depending on what you did, that may not work.  Was there an ability to physically disconnect the RAID5 pool before installation?  

As far as "I wish I knew earlier", many help requests are after-the-fact.  That is the nature of a help forum.  

Going forward, measure your changes to your system in "Agony Units".  If I make this change to my system, what are the Agony Units involved to get back to where I am now?  If the Agony Units are greater than your tolerance, spend more time on the forums trying to figure out a better way.  Either increase your Agony Units tolerance (having a good backup, for example) or lower the Agony Units (get a second machine to bang on).  After a while you will be able to answer the question:  "Are the Agony Units involved in making this change worth possibly trashing my only working Linux system?"

---

### Post by MAFoElffen on 2015-04-12
I guess this goes back to my post and on providing services... What is your basic goal? Once you determine that, determine what services you need/want to provide, and how to best provide them? If all you needed was to provided file sharing... I try to make a plan and see how to best attack that. I guess that is the IT Consultant in me, squeaking out.

But you have already jumped ahead a few steps... No use in jumpimg backwards, eh? So now you have Samba Installed? And you are saying you have permissions problems? If you can paste your smb.conf to a pastebin ( or here ) maybe we can help you debug that problem...

I'm still a little confused. Didn't you start out saying your wanted to provide file access to remote users? But what you last described was intranet access permissions right?

---

### Post by amerinde on 2015-04-13
MAFoElffen... yes, i was setting Ubuntu desktop up(to try it), had internet permission to access the share.. Now, with the server, it wont let me give myself intranet access. I have to be on the machine to do anything.

BTW, i thought i closed this post.. i close it now.. thanks all for your help. i opened a new thread..

---

### Post by cariboo on 2015-04-13
> **amerinde said:**
> BTW, i thought i closed this post.. i close it now.. thanks all for your help. i opened a new thread..

If you want to close this thread, please report the last post, and request it be closed.

---

