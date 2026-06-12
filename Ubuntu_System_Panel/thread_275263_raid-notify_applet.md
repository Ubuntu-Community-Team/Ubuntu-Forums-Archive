---
title: "raid-notify applet"
date: 2006-10-11
forum: Ubuntu System Panel
---

### Post by gny on 2006-10-11
Hello,

I hope this is the right category for this stuff. 

I have started a project which i call raid-notify.
It's a gnome applet which gives you the status of your raid/raids. Right now it only shows if it's up/down/syncing, but I'm working on a menu for simple raid configuration. I'm not aware of any similar projects, so if you know any send me a post.

Any input is appreciated, this is my first gnome project. :)

Screenshots coming up in a while.

---

### Post by TheMono on 2006-10-12
Probably not the right category, but since it sounds like a good applet, I think we'll forgive you lol.

Good luck with it!

---

### Post by chanders on 2006-10-13
> **gny said:**
> Hello,

I hope this is the right category for this stuff. 

I have started a project which i call raid-notify.
It's a gnome applet which gives you the status of your raid/raids. Right now it only shows if it's up/down/syncing, but I'm working on a menu for simple raid configuration. I'm not aware of any similar projects, so if you know any send me a post.

Any input is appreciated, this is my first gnome project. :)

Screenshots coming up in a while.


Well good luck in your first project! What is it written in? C? Python? 

Is it GTK based? Post some scrennies ;-)

---

### Post by gny on 2006-10-13
It's written in python and pygtk. Depending of how it grows i might implement it in c.
What I understand python is the preferred language in Ubuntu, is this also true for the gnome project?
I have mostly been developing in Ruby, but i figured this could be a nice way to learn a new language.

I'm a living evidence that developers probably shouldn't try to make graphics, so I'm trying to brush up the icons a bit. ;)

I'll post some screenies this weekend.

---

### Post by buellman on 2006-10-27
Hi,

A wonderful idea!
Today I looked at dmesg to find that one Disk of my Raid1 was kicked after a powerfailure. I was suprised since this is my first raid and I didn't exspect something like that :-/ So a notification would be pretty cool if something is wrong with the raid. Hope to see your applet in the future :-)

Greets. Buellman

---

### Post by gny on 2006-11-18
Hello,

I have no idea of how to move this thread and where a more appropriate place would be.

I'm making some progress. It's no longer an applet, I didn't like that approach because it always uses my precious panel space. It's new home is in the systray, where it is visible on start-up and when something is wrong.

No nice pictures yet ;)

---

### Post by cybergalvez on 2007-10-29
Hey does anyone know if this applet ever got finished? if so is it available? I'd love to add this my desktop setup
Jose

---

### Post by gny on 2007-10-30
Well, i sort of did, I guess I have to finish it now when some one is interested ;)

---

### Post by gny on 2007-11-01
Well, I actually found the code :O
Brushing it up, learnt a lot since i started this project. Hopfully I have something to show soon.

---

### Post by buellman on 2007-11-01
That would be great!

Greets. Buellman

---

### Post by Lem on 2007-11-09
Actually this may be a good place for this.. how about integrating it into USP?

---

### Post by gny on 2007-11-10
Yea, that would be cool.

---

### Post by buellman on 2008-02-05
> **gobindbuilders said:**
> which gives you the status of your raid/raids. Right now it only shows if it's up/down/syncing, but I'm working on a menu for simple raid configuration. I'm not aware of any similar projects, so if you know any send me a pos
Do you have some debs to test?

---

### Post by Quikee on 2008-02-05
Ignore gobindbuilders.. it is some kind of automatic spammer. It posted a snipped of something gny said int the first post. 


> **gny said:**
> Hello,

I hope this is the right category for this stuff. 

I have started a project which i call raid-notify.
It's a gnome applet **which gives you the status of your raid/raids. Right now it only shows if it's up/down/syncing, but I'm working on a menu for simple raid configuration. I'm not aware of any similar projects, so if you know any send me a pos**t.

Any input is appreciated, this is my first gnome project. :)

Screenshots coming up in a while.

---

### Post by buellman on 2008-02-05
> **Quikee said:**
> Ignore gobindbuilders.. it is some kind of automatic spammer. It posted a snipped of something gny said int the first post.
Lol... I thought of something like that :-) but... you never know. At least I now know why the text looks like something I had read before :-)

Greets. Buellman

---

### Post by Quikee on 2008-02-05
> **buellman said:**
> Lol... I thought of something like that :-) but... you never know. At least I now know why the text looks like something I had read before :-)

Greets. Buellman

To not let you go empty handed I will release that I made some time ago when my md raid5 array constantly needed to be resynchronized.

Just unpack and start with "python mdRaidStatus.py" and an Icon should be added to the notification area. 

The program is generally untested (I don't even know what happens If no arrays are available), but it detects my raid0, raid1 and raid5 arrays. I might add more info and do proper .deb packaging in the future. 

It would be cool if gny would also present what raid applet had he done or is doing. 

Have fun.

---

### Post by dlrm on 2008-03-31
Hi

I just tested your fine applet and it's great but let me ask for some improvements.

change the icon based on the status: 
a green check sign for all ok
some circle symbol for resync 
a red exclamation mark if some md device is in error.

you could also change the toolbox according to the status:
"all ok" , "md2 resyncing 54%" , "md1 error!"

just my 2 cent



cheers and keep up the good work 
-dlrm

---

### Post by Shadowfire on 2008-04-21
I am working on setting up a server, and was hoping to find something like this.

I haven't tried it yet, but I am hoping to use it soon, let you know what I think.

This is something that should come with a GUI sever version of Ubuntu, if there was such a thing ;)

Thanks
Shadowfire

---

### Post by Quikee on 2008-04-21
> **Shadowfire said:**
> I am working on setting up a server, and was hoping to find something like this.

I haven't tried it yet, but I am hoping to use it soon, let you know what I think.

This is something that should come with a GUI sever version of Ubuntu, if there was such a thing ;)

Thanks
Shadowfire

Don't expect too much. I haven't put much work in the applet as I have a lot of other work. 

However if the demand is high I will put the project into launchpad and PPA to make it easier to install. I will also implement requested things when I have time. However it would be preferred if someone else would pick things up and do further development and maintaining once this is done.

---

### Post by elektriks on 2008-04-26
good luck with your proyect

---

### Post by stuffa on 2008-09-11
Quikee:  I just grabbed your app.  Lovely - just what I was hoping to find.

Would defiantly be worth packaging

---

