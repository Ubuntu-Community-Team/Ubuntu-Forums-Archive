---
title: "removing programs to increase speed?"
date: 2008-11-05
forum: The Cafe
---

### Post by Lowcountry on 2008-11-05
I've been using Linux for about a year, and everytime I upgrade or switch distros, I immediately erase all the apps. I don't use.  I'm still "hopping" to find my perfect distro.  
Will erasing apps. that you don't use make your computer any faster?  For example, I have a computer running Ubuntu in my garage that I only use Rhythmbox & Firefox on.  I will never use openoffice on it.  Will deleting openoffice make my computer any faster, or is it merely taking up disk space(which isn't a problem for me)?
Thanks

---

### Post by aysiu on 2008-11-05
It will increase speed only if the app has a service that runs in the background. Removing an app like Rhythmbox won't really give you any difference in performance, as it basically doesn't run... unless you run it.

Frankly, though, unless you are removing a lot of running services, I don't think you'll even notice a difference. If you have 128 MB or 256 MB of RAM, everything will always feel a little slow unless you're using extremely lightweight applications like Sylpheed-Claws, Rox-Filer, and Dillo. And if you're using those, it won't matter if you have one or two services running in the background. And if you have 512 MB or up to 4 GB of RAM, everything will always feel fast unless you are running some extremely intense graphics or video editing programs while playing some 3D game. And again, if you're doing all that, one or two services running in the background won't really be noticeable.

Bottom line, unless you're hard-up for hard drive space (i.e., you have a 4 GB or 8 GB SSD), there's not really a lot you gain from removing the default apps.

---

### Post by snowpine on 2008-11-05
Deleting a regular application you don't use will just save hard disk space.

Disabling daemons (applications that run in the background) may give you a performance boost though. For example I disable bluetooth (System->Preferences->Sessions) because my computer doesn't have bluetooth. :)

---

### Post by kellemes on 2008-11-05
> **Lowcountry said:**
> I've been using Linux for about a year, and everytime I upgrade or switch distros, I immediately erase all the apps. I don't use.  I'm still "hopping" to find my perfect distro.  
Will erasing apps. that you don't use make your computer any faster?  For example, I have a computer running Ubuntu in my garage that I only use Rhythmbox & Firefox on.  I will never use openoffice on it.  Will deleting openoffice make my computer any faster, or is it merely taking up disk space(which isn't a problem for me)?
Thanks

Only diskspace..
It's all about the **running** apps and daemons.
So if Rhythmbox and Firefox is all you need, I would personally not use Gnome (and all it's bloat) at all, instead I'd use some likeweight wm like Icewm or Fluxbox to run these applications.
That will make your system a lot faster.

---

### Post by LaRoza on 2008-11-05
> **Lowcountry said:**
> I've been using Linux for about a year, and everytime I upgrade or switch distros, I immediately erase all the apps. I don't use.  I'm still "hopping" to find my perfect distro.  
Will erasing apps. that you don't use make your computer any faster?  For example, I have a computer running Ubuntu in my garage that I only use Rhythmbox & Firefox on.  I will never use openoffice on it.  Will deleting openoffice make my computer any faster, or is it merely taking up disk space(which isn't a problem for me)?
Thanks
No, but if you want a distro that is fast, but familiar (if you are familiar with Ubuntu) try Debian.

---

### Post by chucky chuckaluck on 2008-11-05
after a couple of years of installing ubuntu and stripping it, i finally just switched to arch. arch is a distro you build up from nothing. it's an "if you didn't install it, it isn't there (except for dependencies)" type of distro, rather than an "in case you need it and you're new" type of distro which i think, in a large part, ubuntu is. even so, i've tried running gnome in arch and it's slow. running a light wm, with access to your apps, is going to be quicker. running simple terminal apps instead of giant blobs of gui is going to be faster, for the most part. having fast equipment is probably the number one concern, though.

---

### Post by LaRoza on 2008-11-05
> **chucky chuckaluck said:**
> after a couple of years of installing ubuntu and stripping it, i finally just switched to arch. arch is a distro you build up from nothing. it's an "if you didn't install it, it isn't there (except for dependencies)" type of distro, rather than an "in case you need it and you're new" type of distro which i think, in a large part, ubuntu is. even so, i've tried running gnome in arch and it's slow. running a light wm, with access to your apps, is going to be quicker. running simple terminal apps instead of giant blobs of gui is going to be faster, for the most part. having fast equipment is probably the number one concern, though.

Like Debian disks and [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Not saying they are the same as Arch, but one can do a similiar thing with Debian and Ubuntu.

---

### Post by paul101 on 2008-11-05
> **LaRoza said:**
> No, but if you want a distro that is fast, but familiar (if you are familiar with Ubuntu) try Debian.


i second that


if you're really picky you could use damn small linux. ive got it running on my core 2 duo  3.16 ghz desktop. with 3gb ram! :D

---

### Post by oldsoundguy on 2008-11-05
installing a program in Ubuntu (other than ones that have a daemon such as the bluetooth previously mentioned) will not have an effect on the speed of the program as it only makes the program available for USE without having to install it every time.

Unlike Windows, there are very very few Linux programs that "load with the system"  (no need for something like msconfig to disable their start up to speed things up.)

BUT, there are programs that load WITH programs .. IE: the plug ins you have with Firefox .. speed can be gained there with fewer programs installed (those that have to be launched from the toolbar do not load.)

(BTW, I found Linux Mint to be relatively fast .. not tried some of the others suggested.)

---

### Post by Lowcountry on 2008-11-05
Thanks for ALL the help everyone!

I have thought about messing with Arch, but I'm more of a user than a builder.  Also, I like how the stuff I use works "out of the box" with Ubuntu.
Is a regular install of Debian faster than a regular install of Ubuntu?
I've tried starting with a minimal install, but I end up doing a "apt-get install ubuntu-desktop" and that puts me at a regular install.
Also, I've tried xfce & flux, but I really like Gnome and that's what I want to stick with.

I guess my best bet is to use Debian(which I have no problem with) and limit the services running.

Also, I have used Mint, and like it, but this computer is 256mb.

---

### Post by AndyCooll on 2008-11-05
With 256mb the biggest speed boost you are likely to gain would by by switching your DE to something like XFCE or Fluxbox.

Debian is slightly quicker but it still uses GNOME (or KDE) and hence is still quite memory intensive.

:cool:

---

### Post by oldsoundguy on 2008-11-05
really, why fight it?  IF your motherboard supports it, memory is dirt cheap on eBay.

---

### Post by Lowcountry on 2008-11-05
> **oldsoundguy said:**
> really, why fight it?  IF your motherboard supports it, memory is dirt cheap on eBay.

It's a 1999 Dell Optiplex GX1.  I bought it on ebay for $40--shipped...it's mere principle that I'm trying to make it work as is.  Besides, my wife won't let me spend anymore money on it.;-)

...Right now, I'm trying the ubuntu barebones install from psychocats...

---

### Post by bodhi.zazen on 2008-11-05
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by K.Mandla on 2008-11-05
I've seen minor speed increases when yanking out core software in Ubuntu.

This is a two-second improvement in boot times on a 1Ghz command-line 8.04 system. Before, and after; clean installations both times.

Of course, speed while the system is running is going to depend on the workload you give the machine, and how much in the way of resources you have to do it.

---

### Post by oldsoundguy on 2008-11-05
think (if I remember right)  I paid well under 20 bucks including shipping from eBay for some PC66 ram to add to a board with a 466 celeron on it .. brought it up to the board max of 512 .. right now Linux Mint on it and it flies for something that old and slow!

Cut out a couple of lattes in a couple of weeks and it is paid for!

---

### Post by handy on 2008-11-05
> **Lowcountry said:**
> Thanks for ALL the help everyone!

I have thought about messing with Arch, but I'm more of a user than a builder.  Also, I like how the stuff I use works "out of the box" with Ubuntu.
Is a regular install of Debian faster than a regular install of Ubuntu?
I've tried starting with a minimal install, but I end up doing a "apt-get install ubuntu-desktop" and that puts me at a regular install.
Also, I've tried xfce & flux, but I really like Gnome and that's what I want to stick with.

I guess my best bet is to use Debian(which I have no problem with) and limit the services running.

Also, I have used Mint, and like it, but this computer is 256mb.

Installing Arch by following the [***_Beginners Guide_***]("http://wiki.archlinux.org/index.php/Beginners_Guide") is not hard, it is very educational & many of us consider it to be fun as well.

There are very few distro's out there that run faster than Arch, due to Arch using only the system resources that it needs to suit your particular custom setup.

The Arch Wiki has excellent information available, & the Arch Forum naturally is very helpful with a kind attitude, all of which (& more) are available in the tabs on [***_this page_***]("http://www.archlinux.org/"). The Ubuntu Arch sub-forum responds very quickly to people with Arch problems, as there are quite a few in the Ubuntu community that have moved from Ubuntu, or also use Ubuntu & Arch.

---

### Post by Lowcountry on 2008-11-05
> **handy said:**
> Installing Arch by following the [***_Beginners Guide_***]("http://wiki.archlinux.org/index.php/Beginners_Guide") is not hard, it is very educational & many of us consider it to be fun as well.

There are very few distro's out there that run faster than Arch, due to Arch using only the system resources that it needs to suit your particular custom setup.

The Arch Wiki has excellent information available, & the Arch Forum naturally is very helpful with a kind attitude, all of which (& more) are available in the tabs on [***_this page_***]("http://www.archlinux.org/"). The Ubuntu Arch sub-forum responds very quickly to people with Arch problems, as there are quite a few in the Ubuntu community that have moved from Ubuntu, or also use Ubuntu & Arch.

I WOULD like to try Arch, especially on my main Linux computer.  My problem general problem with linux has been screen resolution.  Our comupter is in our den and the monitor is a 32" lcd flatscreen...resolution has always been a problem.  I could never get the proper resoultion.  Then, when 8.04(and Lenny) came out, the resolution worked perfectly, "out of the box"...That's what is really keeping me with ubuntu.  If I knew resolution would be just as easy, I would definitely try Arch.

---

### Post by handy on 2008-11-05
> **Lowcountry said:**
> I WOULD like to try Arch, especially on my main Linux computer.  My problem general problem with linux has been screen resolution.  Our comupter is in our den and the monitor is a 32" lcd flatscreen...resolution has always been a problem.  I could never get the proper resoultion.  Then, when 8.04(and Lenny) came out, the resolution worked perfectly, "out of the box"...That's what is really keeping me with ubuntu.  If I knew resolution would be just as easy, I would definitely try Arch.

Arch works fine on my 24" monitor, though that is not an unusually large size these days.

I tend to think that updates to X & also to GPU drivers are what has allowed your large screen to be working these days.  If that is the case then Arch should work also as being around the cutting edge is part of the Arch make-up.

You could post a question in the Arch forums, perhaps someone their will have experience on the matter.  Though you will very likely wait a little longer for an answer than you would on the Ubuntu forums due to the relative number of users.

---

