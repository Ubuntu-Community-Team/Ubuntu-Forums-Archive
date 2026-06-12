---
title: "Best backup system..."
date: 2008-12-21
forum: Server Platforms
---

### Post by hockey97 on 2008-12-21
HI, I want to know what would be the best backup system for me.

Ok, I am currently hosting 2 websites. using apache2. 

what I want is that I can recover my system without needing to reinstall anything.

It happened to me before where I lost everything and it took me a month to get back to where I was.
I had to remake the websites and all the code which was a pain.

I bought a external hard drive so I can backup the system.

I was told to use part image  or use a bash script.

I wounder which one is best for me.

I already have partimage installed and used it. I was able to make a copy of the main partition of linux  however I can't copy my extended space which is on the hd with os windows but it's  a seperate partition which is a extended partition which is in a file system of Linux. 

Partimage would give me a error saying the drive is locked or something for forbids partimage from accessing it.

which is the best route?  I do have 2 computers and want to some day down the road to use my new computer as the server. So I should be able to transfer the files easily.

---

### Post by namdung on 2008-12-21
[http://www.zmanda.com/](http://www.zmanda.com/)

---

### Post by 2hot6ft2 on 2008-12-21
From another thread.
> Clonezilla, fastest ever cloning i have ever done is using CLONEZILLA(indeed it is top notch app).

i have cloned several HDD and networked machines with it, locally and on network with no problem what so ever. Great app for one off complete system state clone/backup

Last week I cloned my laptop's HDD 120GB locally within 35 mins.

[http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

---

### Post by hictio on 2008-12-21
I use [Rsnapshot](http://www.rsnapshot.org/) on every single Linux/ *BSD box I put my hands on.
Free, easy to install, easy to configure.

I setup local snapshots of whatever I need, every 6 hours, with a backlog of 7 days; and also, I make a daily [rsync over SSH to a central box of the last snapshot once a day](http://oesediez.blogspot.com/2008/07/remote-backups-made-easy.html).

---

### Post by windependence on 2008-12-21
I agree with hictio on this. rsnapshot is da bomb.

The absolute easiest way to come back from a disaster is to run your boxes as VMs and then keep a copy of your VM as backup. If something fails we boot from the saved VM in less than 5 minutes.

-Tim

---

### Post by indispus on 2008-12-21
> **hockey97 said:**
> [...]It happened to me before where I lost everything and it took me a month to get back to where I was.
I had to remake the websites and all the code which was a pain.[...]

To avoid this kind of mistake in the future, I recommend you keep your websites on some [SVN server]("http://www.howtogeek.com/howto/ubuntu/install-subversion-with-web-access-on-ubuntu/"). Doing this, you will be able to restore anytime your websites and even get back to some older version if needed. You can keep your database data there too.

Cheers :popcorn:!

---

### Post by R.Bucky on 2008-12-21
Finding an easy backup solution has been challenging for me. I utilize Webmin to perform daily backups of my web server and also my primary file folders such as pictures, music, and others. the folders are backed up in .tgz format, so it makes it easy. 

one thing to point out - i created a backup of my entire user directory (~100GB). unfortunately, i had to use it one day and used archive manager to decompress it. my harddrive is only 200GB. the file backup was too large to fit on my drive. it took some fine work to retrieve the files. So, I now backup by folder, somewhere in the neighborhood of around 10GB each. LESSON LEARNED the hard way...

---

### Post by hictio on 2008-12-21
> **R.Bucky said:**
> Finding an easy backup solution has been challenging for me. I utilize Webmin to perform daily backups of my web server and also my primary file folders such as pictures, music, and others. the folders are backed up in .tgz format, so it makes it easy. 

one thing to point out - i created a backup of my entire user directory (~100GB). unfortunately, i had to use it one day and used archive manager to decompress it. my harddrive is only 200GB. the file backup was too large to fit on my drive. it took some fine work to retrieve the files. So, I now backup by folder, somewhere in the neighborhood of around 10GB each. LESSON LEARNED the hard way...


I used to use Webmin's backup feature, but, to me, it makes no sense on creating huge tgz files daily, when actually what have changed are actually a few MBs of files here and there.

---

### Post by hockey97 on 2008-12-22
Thanks for the reply's. 

I currently am making 2 websites one is a company website and the other is a social network site.

I been scratching my head on how to setup my system.

I got 2 computers.   When I installed and setup web servers and all that it was on my old computer.

I then got a new computer from highschool. I was taking a career prep center course in electronics . So we got computer kits and put the computer together. I have a AM2 socket cpu and a athlon 64. 

currently that computer I don't use as much. I can upgrade the system to use 4 gigs of ram and more hd. 

My problem I am facing right now is that I have 2 computers and one I need to use for personal stuff like games or school work etc.

Then on computer would be the server.
 
I really want to currently just do manual backups nothing on  a time schedule. 

I am confused on how I can make backups and yet have it transferable to other pcs. I mean I might buy another computer to be a backup system for the main server. 

I already put in about 3 years of work on my server and websites  and currently haven't finished the websites.

Since like 2 times  I have a dual boot system with linux and windows.

and when I log on windows I installed some software to be able to have windows see linux particians. Which I can access linux particians. What happened was my windows os gives me a prompt saying that 2 hd are not formatted properly so it formated my particians of linux OS. So I tried to boot into linux and couldn't.

I then finally accepted that I lost everything and then installed a fresh new installation which too me months to get back where I was.

So in summer of 08 I decided to buy a external hd to make backups to.

Ever since I bought it I been trying to figure out how I should backup my system.


So I am ussing I should stick with copying the partician image.

I just want to know if I take the partician image will I have trouble installing it  on my new computer?

I am asking that because I have different hardware compared to my old computer.

So I woundered if I will have issues with the hardware.

Thanks for the replies. I will check out clonezilla I have heard some stuff about it.

I don't have any cd's spare so I need a program that would make backups from the computer.

I later on might go out and buy some blank cds to have clonezilla to be on the cd.

Thanks for your time.

---

