---
title: "[SOLVED] Problem with shared folder in Gutsy + XP on Virtual Box"
date: 2008-02-07
forum: Virtualisation
---

### Post by geo909 on 2008-02-07
Hello everybody.

I have a folder (it's actually a HD mounted in /media/sdb1) which I want to share with XP which I have installed in Virtual Box..

 Well, it seemed to be simple enough but I can't manage to "see" my shared folder. 

 Look what I have done:
[CENTER][[IMG]http://www.imageshack.gr/files/gmnbx4wjmpaeh6tfp8du.png[/IMG]](http://www.imageshack.gr/view.php?file=gmnbx4wjmpaeh6tfp8du.png)[/CENTER]
[IMG][[IMG]http://www.imageshack.gr/files/12m5i3u9ga99xbkhyaze.png[/IMG]](http://www.imageshack.gr/view.php?file=12m5i3u9ga99xbkhyaze.png)

Could you please indicate what I have done wrong?

Thank you in advance!

---

### Post by fjgaude on 2008-02-07
For one thing there shouldn't be any spaces between the backslashs.

Another, do you have your vboxsvr's IP address in the hosts file of Ubuntu?

---

### Post by geo909 on 2008-02-07
Firstly, thanks for your answer..

> For one thing there shouldn't be any spaces between the backslashs.

You mean, I should type:
```
net use e: \\vboxsvr\160_GB_Storage
```

Right?

```
Another, do you have your vboxsvr's IP address in the hosts file of Ubuntu?
```

Hmm... ...well.. 
I don't really have an idea what that means...:oops:
Well... I declare myself noob! Could you explain what that means and what I should do?

---

### Post by fjgaude on 2008-02-07
> **geo909 said:**
> Firstly, thanks for your answer..

You mean, I should type:
```
net use e: \\vboxsvr\160_GB_Storage
```

Right?

Drop the e: and only have the host name and the shares. But rihgt now I don't understand why you are using the Windows command line, net use?

```
Another, do you have your vboxsvr's IP address in the hosts file of Ubuntu?
```

Hmm... ...well.. 
I don't really have an idea what that means...:oops:
Well... I declare myself noob! Could you explain what that means and what I should do?

I haven't used VBox in a year and have forgotten how to access the shares in Ubuntu. There are a number of ways but I don't think I have the language to explain them to you. Using Windows Exploxer going to Network Places is one. Using the File Manager, Nautilus, in Ubuntu and Samba. But in VBox you have listed your shares and then it should work right off.

Maybe someone else here can help more than I.

---

### Post by geo909 on 2008-02-07
Well...
I don't have the slightest idea what I should do next..

Any advice will be very welcomed...

---

### Post by fjgaude on 2008-02-07
Have you studied this post:

[http://ubuntuforums.org/showthread.php?t=340113](http://ubuntuforums.org/showthread.php?t=340113)

There has been lots of posts on VBox and sharing folders. Do a search on something like that.

---

### Post by p_quarles on 2008-02-07
If I remember right, it's as simple as opening the Control Panel, going to "network places" and finding the shared folder. It's been a couple months since I set this up, but I believe that's all I had to do.

---

### Post by geo909 on 2008-02-08
SOLVED!

Well, for a strange reason, when I set my root folder as a shared one it worked. That was not the case with my /media/sdb1 folder.

 Maybe because it's a folder that a disk is mounted. Maybe it has to do with permissions. I don't have the slightest idea.

 I just set my "/" folder as shared and named it "ROOT"
Then opened XP in VB, Start Menu -> Accessories-> Command Prompt and typed  
```
net use e: \\vboxsvr\ROOT
```

A message appeared and confirmed everything went all right. Then in "My Computer" appeared my ROOT folder.

 From there I can even access USB sticks mounted in Ubuntu (by just going to /media/USB_mount_point).

 The only problem (not a big one though) is that I cannot handle files from my shared folders.
For example, If I want to run an .exe, I have to drag&Drop it in my XP Desktop and execute it. The same with my MP3s, to make them playable...

 But, you can't have it all, anyway... I'm pretty fine with the situation right now.

HOWEVER, if someone's have a solution for this, please PM me.

 Thanks everybody for taking the time to answer my questions.

---

