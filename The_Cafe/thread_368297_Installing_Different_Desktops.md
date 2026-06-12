---
title: "Installing Different Desktops"
date: 2007-02-23
forum: The Cafe
---

### Post by steven8 on 2007-02-23
1) How does one go about installing, say xfce in place of the default gnome?

2) Is it possible to install it such that you could choose the different environments using the options at login?

---

### Post by yabbadabbadont on 2007-02-23
sudo apt-get install xfce4

That will get you the basic xfce4 desktop.  After it is installed, if you restart GDM, there should be an xfce4 session you can choose from the Sessions menu.

---

### Post by steven8 on 2007-02-23
> **yabbadabbadont said:**
> sudo apt-get install xfce4

That will get you the basic xfce4 desktop.  After it is installed, if you restart GDM, there should be an xfce4 session you can choose from the Sessions menu.

That's cool.  And simple.  Will gnome still be there to use as well then?

---

### Post by rfs1970 on 2007-02-23
Hi there,

If you want to install the very new version of Xfce 4.4.0 (its quite cool), follow the instructions at the [Tolero's Blog]("http://tech.tolero.org/blog/en/linux/xfce-440-packages-for-ubuntu-edgy").

I strongly recommend!

r.

---

### Post by bigken on 2007-02-23
yes your gnome  will still be there 


I would use sudo aptitude install xfce4

---

### Post by steven8 on 2007-02-23
Hmm.  A bit more to chew on.  What exactly is the difference between apt-get and aptitude?

---

### Post by agiamba on 2007-02-23
also if you want kde apt-get install kubuntu-desktop, same thing as xfce, you can choose what session in the login menu.

the difference between aptitude and apt-get?
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by steven8 on 2007-02-23
> **agiamba said:**
> also if you want kde apt-get install kubuntu-desktop, same thing as xfce, you can choose what session in the login menu.

the difference between aptitude and apt-get?
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

Okay.  Thanks for the link.  I am using Dapper, so aptitude is definitely the way I want to go!  Thanks everyone!  This should go very smoothly, I'd say.

---

### Post by Rui Pais on 2007-02-23
> **steven8 said:**
> Hmm.  A bit more to chew on.  What exactly is the difference between apt-get and aptitude?

aptitude deals better with dependencies. 
Since you want a meta packages with a lot of depencencies, aptitude is definitely better :)

You may also prefer to do:
```
sudo aptitude install xubuntu-desktop
```
instead.

---

### Post by steven8 on 2007-02-23
Whoa.  Each response takes us ever further into this thing.  Now, why is it better to install the xubuntu desktop better for me than just installing xfce4?

---

### Post by yabbadabbadont on 2007-02-23
Just be aware, that if you install the ?ubuntu-desktop packages, the last one installed will replace your usplash theme with it's own.

---

### Post by Rui Pais on 2007-02-23
> **steven8 said:**
> Whoa.  Each response takes us ever further into this thing.  Now, why is it better to install the xubuntu desktop better for me than just installing xfce4?

You **may prefer**, not necessarily **should do** or **better then** ;)

xubuntu-desktop it's a meta package design to deal specifically with dependencies... Seems to makes easier and safer dist-upgrades, among other things. 
The other side, it will install more stuff, and eventually replace some things, like yabbadabbadont mentioned.

---

### Post by steven8 on 2007-02-23
Now, let me try to get this straight.  If I install the xubuntu desktop, it'll give me the cute little mouse running on an ubuntu-wheel when I boot, but my programs will still be there, yet in an xfce DE.  If I install just xfce, I'll get the standard Ubuntu bootup, can select xfce, and have my programs there, yet in an xfce DE.

All the while. . .being able to choose gnome with options at login.

Also. . .can I get fries with that? :)

---

### Post by yabbadabbadont on 2007-02-23
> **steven8 said:**
> Now, let me try to get this straight.  If I install the xubuntu desktop, it'll give me the cute little mouse running on an ubuntu-wheel when I boot, but my programs will still be there, yet in an xfce DE.  If I install just xfce, I'll get the standard Ubuntu bootup, can select xfce, and have my programs there, yet in an xfce DE.

All the while. . .being able to choose gnome with options at login.

Also. . .can I get fries with that? :)

Yes.  Yes.  Maybe.  (I'm sure there is some sort of "fries" software in Linux somewhere.  ;))

---

### Post by steven8 on 2007-02-23
sudo aptitude eat fries

:)

---

### Post by Rui Pais on 2007-02-23
> **steven8 said:**
> Now, let me try to get this straight.  If I install the xubuntu desktop, it'll give me the cute little mouse running on an ubuntu-wheel when I boot, but my programs will still be there, yet in an xfce DE.  If I install just xfce, I'll get the standard Ubuntu bootup, can select xfce, and have my programs there, yet in an xfce DE.

All the while. . .being able to choose gnome with options at login.

Also. . .can I get fries with that? :)

for that you need to go with Gentoo and set the USE flags +fries -popcorns :lol: 
just joking

Yes, gdm will have an entry for xfce (and a xfce theme) where you can choose (or set default) which do you prefer to start. 
You can do the same for fluxbox, enlightenment, windowmaker, e17 and a lot of others.

With kde if you go for kubuntu-desktop it will also change gdm for kdm i think.

Linux is nice isn't it :)

---

### Post by steven8 on 2007-02-23
> **Rui Pais said:**
> for that you need to go with Gentoo and set the USE flags +fries -popcorns :lol: 
just joking

Yes, gdm will have an entry for xfce (and a xfce theme) where you can choose (or set default) which do you prefer to start. 
You can do the same for fluxbox, enlightenment, windowmaker, e17 and a lot of others.

With kde if you go for kubuntu-desktop it will also change gdm for kdm i think.

Linux is nice isn't it :)

I've always heard good stuff about Gentoo!! :)

Yes Linux is nice.  It's the best moved I've ever made on my computer.  Thanks!!

---

### Post by yabbadabbadont on 2007-02-23
> +fries -popcorns
That isn't valid USE flag syntax I'm afraid...  it should be:

USE="fries -popcorns" emerge -uDN world

But the preferred method would be to add them to /etc/portage/package.use for the individual packages that would be affected.


(Can you tell that I'm the #42 top poster to the Gentoo forums?  :lol:)

---

### Post by steven8 on 2007-02-23
> **yabbadabbadont said:**
> That isn't valid USE flag syntax I'm afraid...  it should be:

USE="fries -popcorns" emerge -uDN world

But the preferred method would be to add them to /etc/portage/package.use for the individual packages that would be affected.


(Can you tell that I'm the #42 top poster to the Gentoo forums?  :lol:)

I never would have noticed. =D>   How long have you been using Gentoo?

---

### Post by yabbadabbadont on 2007-02-23
> **steven8 said:**
> I never would have noticed. =D>   How long have you been using Gentoo?

Joined the forums in March 2003, but started with Gentoo around September 2002.  I'm running Dapper now though.  While I enjoyed the control over the system that Gentoo allows, I reached a point where I just wanted a stable system with regular security updates.  Dapper fits the bill.  (ummm, no pun intended)

---

### Post by steven8 on 2007-02-23
> **yabbadabbadont said:**
> Joined the forums in March 2003, but started with Gentoo around September 2002.  I'm running Dapper now though.  While I enjoyed the control over the system that Gentoo allows, I reached a point where I just wanted a stable system with regular security updates.  Dapper fits the bill.  (ummm, no pun intended)

Good pun though.  :popcorn:   To me, Dapper is the best thing since sliced bread!  I love it.

---

### Post by Rui Pais on 2007-02-23
> **yabbadabbadont said:**
> That isn't valid USE flag syntax I'm afraid...  it should be:

USE="fries -popcorns" emerge -uDN world

But the preferred method would be to add them to /etc/portage/package.use for the individual packages that would be affected.


(Can you tell that I'm the #42 top poster to the Gentoo forums?  :lol:)

damn it you are right, of course :)

(i don't use Gentoo for almost an year... )

We are joking, but once i saw some distro screenshots -don't remember the name- that while install it instead of the usual timer bars offers a window where the user could play tetris game while the installer was working. 
Thats the close of fries or popcorns i can think about :lol:

edit: btw, i come back to ubuntu, when dapper released, for the same reasons.

---

### Post by steven8 on 2007-02-23
> We are joking, but once i saw some distro screenshots -don't remember the name- that while install it instead of the usual timer bars offers a window where the user could play tetris game while the installer was working. 
Thats the close of fries or popcorns i can think about 

I'd take Tetris in place of fries.  Anyday.

---

### Post by rfs1970 on 2007-02-23
Well... depend...

Do you have space in your hard disk?
To install the full xubuntu-desktop and all its feature you will need at least 135mbytes available
i dont know for sure, how much space you will need to installl just the xfce

Btw, I just installed the entire xubuntu-desktop and I am very impressed with it.

r.

---

### Post by steven8 on 2007-02-23
I've got about 75 gbs available.  I'm okay. :)  I've used the xubuntu liveCD, and I liked it very much.  I really like the basic Ubuntu Dapper install, I'd just like to try it with the xfce.

Can the xfce be customized more than the gnome?  I mean, as far as moving arount the toolbars and such?

---

### Post by steven8 on 2007-02-23
Okay, I used sudo aptitude install xfce4.  It went smooth as pie.  Yet, even though I only got xfce, xubuntu took over!  I was just wanting to try it out sometime on my own.  I just got my wife to venture into Ubuntu and don't want to throw her off.  

So . . .I got it set back up to the default human theme.  I'll spring that on her later, once she's more comfortable with it. :)

Thanks for all the help, guys.  I really do like the xfce system.  I'll use it on the weekend after everyone's down for the night!

---

### Post by steven8 on 2007-02-24
My wife is now totally convinced!  So I have another question.  If I delete my windows partition and expand my Ubuntu partition, what step must I take for boot-up?

---

### Post by bigken on 2007-02-24
you can use gparted liveCD to delete and resizes your partitions

but do more research on this as your grub might be on the same partition as windows ?

---

### Post by steven8 on 2007-02-24
I know I can do that, but will the system just boot okay and the windows option will be missing from GRUB, or do I have to alter files before rebooting.

---

### Post by user1397 on 2007-02-24
by the way, a good guide on installing the different desktop environments can be found in my signature

---

### Post by kevinlyfellow on 2007-02-24
installing the xubuntu-desktop will give you the desktop as if you installed it using a cd, so there may be extra apps that don't necessarily come with xfce4.

---

### Post by steven8 on 2007-02-24
> **kevinlyfellow said:**
> installing the xubuntu-desktop will give you the desktop as if you installed it using a cd, so there may be extra apps that don't necessarily come with xfce4.

I just installed the xfce4.  It made my system default to the xubuntu desktop anyway, but that's okay, I swapped it back.  My wife really liked the cute little xubuntu mouse, and she seemed to like the desktop.  It's great to have the choices!!

---

### Post by fuscia on 2007-02-24
being more of a minimalist user, i'd be more likely to install kde-core vs. kubuntu-desktop and xfce4 vs. xubuntu-desktop. and speaking of minimal, try some of the window managers, too: openbox, icewm, fluxbox...even qvwm.

---

### Post by steven8 on 2007-02-24
> **fuscia said:**
> being more of a minimalist user, i'd be more likely to install kde-core vs. kubuntu-desktop and xfce4 vs. xubuntu-desktop. and speaking of minimal, try some of the window managers, too: openbox, icewm, fluxbox...even qvwm.

See!  Choices.  Sweet!!

---

### Post by floke on 2007-02-24
Also, just for fun, have a look at Looking Glass, and check out the Matisse DE for Mandriva.
they're both developmental though; you can't install the latter (and it's not Ubuntu anyway) and the former doesn't yet work properly (and is pants anyway IMHO) - but just to see the choices makes you appreciate the Penguin.

---

### Post by fuscia on 2007-02-24
> **steven8 said:**
> See!  Choices.  Sweet!!

yup. i had to use openbox on my old desktop, or it wouldn't move, but even though my laptop runs gnome and kde perfectly well, i still prefer the openbox way of doing things. a warning though: the first time i logged into openbox, i got a blank screen and thought it was broken. i didn't realize that that was it - just a blank screen and a right-click menu (which i discovered by shear accident).

---

### Post by steven8 on 2007-02-24
> **Steve.K said:**
> Also, just for fun, have a look at Looking Glass, and check out the Matisse DE for Mandriva.
they're both developmental though; you can't install the latter (and it's not Ubuntu anyway) and the former doesn't yet work properly (and is pants anyway IMHO) - but just to see the choices makes you appreciate the Penguin.

I'm always open to new stuff.  Thanks!!

---

### Post by floke on 2007-02-24
Edit to my previous post: apparently you can install Metisse on ubuntu, but its a bit of a devil to compile. Am currently trying to suss it out, but alas with no joy.

---

### Post by steven8 on 2007-02-25
> **Steve.K said:**
> Edit to my previous post: apparently you can install Metisse on ubuntu, but its a bit of a devil to compile. Am currently trying to suss it out, but alas with no joy.

Did it work out for you?

---

### Post by floke on 2007-02-25
Not yet. Keep getting an error message about being unable to init fonts. If anyone has any clues as to how to solve this then give us a shout. There's a good thread on metisse in the forums on which someone has posted links to a couple of deb packages so you haven't got to go through the compiling hassle. I've heard that people have managed to do it, so it is possible. Am just waiting for wiser minds than mine to point the way to the metisse moon.

(Incidentally, I've had a play with the Mandriva Meitsse LiveCD - though it doesn't work on my main PC - and its not as good as Beryl by a long way, but still an interesting piece of kit to have knocking around if you can get it working).

---

### Post by SuSUntu on 2007-02-25
> **steven8 said:**
> My wife is now totally convinced!  So I have another question.  If I delete my windows partition and expand my Ubuntu partition, what step must I take for boot-up?

I've noticed you've been posting here with exuberance and using a lot of exclamations when describing your new experiences with Ubuntu / Linux (Sweet!; Choices!; My wife is now totally convinced!; To me, Dapper is the best thing since sliced bread! I love it.; etc.)

However, jumping the gun and removing Windows, despite the fact that you say you have plenty of hard disk space, may be a mistake.

Your computer is a tool. Ubuntu is a tool. Windows is a tool. The various (different) applications that each OS runs are tools. So, why throw out one set of tools just because they may not be the most often used (or liked) as of now?

I mostly use metric-sized wrenches and sockets, but I don't throw out my American Standard-sized tools, especially out of spite or giddyness over my favored metrics. 

I don't mean to dampen your enthusiasm as it's a good thing, just a friendly thought to slow down a bit. :)

---

### Post by floke on 2007-02-25
Good point. It's easy to get excited about the fact that you don't have to use Bill Gates' piece of crap anymore, but there's no need to delete it straightaway, unless you really need the disc space. When I started I told myself that I would only delete XP if my ubuntu partition ran out of space, or when six months had expired without me needing to use it - whichever came the soonest. This was at the end of October 2006. A few days ago I deleted my XP partition (and exceedingly good it feels), so I got to four months. 

Give it some time. Learn to find your way around Ubuntu a bit so that you can always dig yourself out of any accidental holes. What will you do if Ubuntu breaks and you need to get to the forum. Without XP, do you have a means to do it? For me, the whole thing has also taught me that I don't think I'll ever have just one OS on my PC, it's always nice to have a backup (of course a pile of LiveCD's also helps!) just in case.

You have nothing really to gain by deleting XP just yet but could potentially incur a great deal of hassle by so doing. Wait until the balance is in your favour. 

And then destroy ever sodding last line of the miserable thing from your life forever.

BTW: If you choose to ignore the advice from the above posts, the answer to your question is that it 'should' still boot fine (at least mine did); you'll just have to edit your grub file (sudo nano /boot/grub/menu.lst) to delete the reference to windows once it has gone.

---

### Post by steven8 on 2007-02-26
Your advice(s) : - ) are well taken.  I didn't just discover it this week, though.

I have been using Ubuntu and other various distros off of livecds as well as installs on test drives for the last several months.  Right now it is my wife who needs to do most of the learning.  I had already decided to leave windows on for awhile yet to make sure she is totally happy with everything she can do in Ubuntu.  Last night we went through the printing process and how to set up draft printing, and using PDF files in Evince.  She was not entirely happy with how we had to set up draft printing, but said she would be able to adapt.  She was used to being able to access this from the print dialog in windows.  You have to go into system>admin>printing to do it here.  An extra step, but not that big of a deal.

I have one more little question about editing the grub file.  In my mind, that should be done after reboot, or while still in the livecd, by mounting my drive?

Oh yes, I am not afraid of having to just wipe and redo the drive with a fresh install of anything.  Actually, I like doing it!  :)

---

### Post by steven8 on 2007-02-26
> **Steve.K said:**
> Not yet. Keep getting an error message about being unable to init fonts. If anyone has any clues as to how to solve this then give us a shout. There's a good thread on metisse in the forums on which someone has posted links to a couple of deb packages so you haven't got to go through the compiling hassle. I've heard that people have managed to do it, so it is possible. Am just waiting for wiser minds than mine to point the way to the metisse moon.

(Incidentally, I've had a play with the Mandriva Meitsse LiveCD - though it doesn't work on my main PC - and its not as good as Beryl by a long way, but still an interesting piece of kit to have knocking around if you can get it working).

I have xfce and gnome for now.  I think Those will be enough to keep us going for awhile.  :)

---

### Post by Asham on 2008-12-30
I can't seem to find where I can remove this post.

---

