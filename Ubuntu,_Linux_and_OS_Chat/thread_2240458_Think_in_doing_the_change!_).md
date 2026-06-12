---
title: "Think in doing the change! :)"
date: 2014-08-20
forum: Ubuntu, Linux and OS Chat
---

### Post by jviure on 2014-08-20
Hi to everyone, first of all, sorry for my english, I know it's not perfect, I will try! 

I'm Jordi, from Spain, I'm web developer, since now, I've been working mainly in Windows, but I've always a secundary partition with linux because I like it so much but there are missing features/programs I want to know if they exists there:

- I like a lot to work with Winscp in Windows, could edit files in the "cloud"  only saving (without prompts as Filezilla do...) the file.
- I need a database manager, in Windows I use Navicat and it's perfect for me! mysql, postgres, mssql, sqlite..
- Well, photoshop for me is better than gimp but I can give it another try
- I remember before I could save the session when I close the computer, this exists nowadays? It was a very good feature! in gnome 2 I remember.

I like native programs, I don't like so much wine. What alternatives can I use???

With these two/three alternatives I think I can work with the calm in Linux.

Now I've installed Linux Mint but today I've had an error and now I cannot open it (only in recovery mode...puaj!), so... I think I'll try to install another debian version (ubuntu, debian, elementary os.. ) what do you recommend me?

Thanks a lot!!
Jordi

---

### Post by Lars Noodén on 2014-08-20
> **jviure said:**
> 
- I like a lot to work with Winscp in Windows, could edit files in the "cloud"  only saving (without prompts as Filezilla do...) the file.

One option would be to use [sshfs](http://manpages.ubuntu.com/manpages/trusty/en/man1/sshfs.1.html) to connect to the remote server then you could just save your files as if they were local even though they are the remote machine.  First you need an empty directory for the mount point, say /home/jviure/cloud, then use sshfs to mount it.

```

sshfs jviure@www.example.com:/Users/jviure/ /home/jviure/cloud/

```

Then anything saved in the ~/cloud directory on the local machine is really saved to /Users/jiuvre on the remote machine.

Edit: mastablasta's suggestion below of using the file manager is easier.  SFTP support is built into most, if not all, of them.

---

### Post by mastablasta on 2014-08-20
I don't know about Ubuntu but Kubuntu by default saves the session. this can be disabled ofcourse.

what do you do in photoshop? I find that for basic editing and such Gimp is more than enough. once you know how to use it... and for websites large photos are not good anyway (unless they are presenting the product). Though quite a few PS version work in Wine. GIMP and Inkscape are also good for me since I am not English speaker and it's easier for me to recognise faster what certain function does.

winscp - from what I see can be run in wine (Platinum-[https://appdb.winehq.org/objectManager.php?sClass=version&iId=29631](https://appdb.winehq.org/objectManager.php?sClass=version&iId=29631) )- otherwise there is a number of similar tools. including various file browsers (crusader, midnight commander). not sure what is possible with latest filezilla. I need to check. prompts are the least of concern I am sure they can be turned off. WinSCP is windows implementation of Linux SCP protocol so yeah there is a way to do it in Linux. it was before windows implementation.
[http://chi3x10.wordpress.com/2008/02/24/krusader-linux-ftpsftpscp-gui/](http://chi3x10.wordpress.com/2008/02/24/krusader-linux-ftpsftpscp-gui/)
or just mount in your filebrowser:
[TABLE]
[TR]
[TD="class: votecell"] 
[/TD]
[TD="class: answercell"]**Ubuntu:**

Open Nautilus and type (in the link bar): sftp://user@server/
**Kubuntu:**

Open Konqueror and type (in the link bar): fish://user@server/
**Xubuntu:**

Open Thunar and type (in the link bar): sftp://user@server/

[/TD]
[/TR]
[/TABLE]
Though Kubutnu nowadays uses Dolphin. 

Navicat runs on Linux as you can see on their website. as well as Win and Mac. otherwise there are a number of free GUI database managers in Linux (or cross system). maybe you could use one of those?

recommend - try and see which one works best for what you need to do. if none of them works well just stick with windows. or you will lose too much time getting OS to work with windows hardware. I don't have time for that. so I try to trouboleshoot and if it's an easy fix I do it else I just use Windows.

---

### Post by grahammechanical on 2014-08-20
You have answered your own question.

"I like to work a lot with." "It is perfect for me." "for me is better than." 

You are not ready to become a satisfied Ubuntu user. You are already giving reasons not to change. You are already finding faults with Linux.

Dual boot and experiment with different applications. You will find that it is easier to import documents made by Windows applications into Linux applications. Than to import document created in Linux into Windows applications.

If you are not willing to learn different ways of working then you should stay with what you are used to using.

Regards.

---

### Post by buzzingrobot on 2014-08-20
If  you earn your living -- or hope to -- as a web designer, I think you should use the tools that you know best. Photoshop, in particular, has an entire ecology of third-party tools, plugins, and support associated with it. Gimp and other Linux tools may or may not provide equivalent functionality, but when they do it will be implemented differently, forcing you to deal with  a learning curve, decrease productivity, perhaps miss deadlines, etc.

If you don't want to risk setting up a dual booting situation, burn an Ubuntu install image to a USB stick and boot it in Live "Try It" Mode.  It won't touch your existing drives, but it will run reasonably fast off the USB and give you a chance to explore a bit.

---

### Post by jviure on 2014-08-20
uau! thanks for all the quick answers! well, Photoshop it's not vital, but programs as Explorer or similar to test my webs... sometimes is embarrasing have to boot a virtual machine or similar. 

With navicat, I tried before the linux version, yes! but I only found mysql support, not all the others I commented. A pitty!

I want to change to linux because all the programs go faster than in Windows. Sometimes I've to work with Java applications or Android and.. what a difference! and because I like "play" with the SO, and with linux this is more possible xD.

Well, I suppose I will install kubuntu. I've an ssd hd partitioned, so ... i will try! thanks again! :)

---

### Post by mastablasta on 2014-08-21
why would it be embarrassing to boot a virtual machine?

I have virtual server setup for tests of plugins and such for the website. if you need it only for explorer test...

strange this navicat that they advertise as crossplatform and then have limitations. either you are cross platform or you are not. anyway is there no similar program? surely not only windows people need database managers...

---

