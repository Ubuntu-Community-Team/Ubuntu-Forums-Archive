---
title: "Burg?"
date: 2012-01-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ranch hand on 2012-01-17
I have not looked at Burg since 10.04-testing.  Seemed interesting even if it didn't really blow my skirt up.

Nice work.

Doesn't seem to be any development past Mangy Moose (10.10).

Figured that it would be the default boot loader for this LTS release.   Seems to be a Launchpad site for exactly that but again nothing moving for a long time.

Anyone able to fill me in on this?

---

### Post by xyzzyman on 2012-01-17
You answered your own question. The developer hasn't made any updates since 2010. It also doesn't work with WUBI. Even if you ignore the WUBI issue, it's probably not worth dumping a working solution for one that's not actively maintained just for eye candy.

---

### Post by cariboo on 2012-01-17
It looks like it Burg is no longer being developed, or maintianed. The last update was in May of 2010. The forum is also no longer available.

---

### Post by ranch hand on 2012-01-17
> **xyzzyman said:**
> You answered your own question. The developer hasn't made any updates since 2010. It also doesn't work with WUBI. Even if you ignore the WUBI issue, it's probably not worth dumping a working solution for one that's not actively maintained just for eye candy.
I agree with you completely.

Was just wondering what the real deal here is.

I did actually get it to work in my Xubuntu 12.04-testing, themes and all.  The default theme (Burg) did not work but a couple others worked fine.  By that I mean that the theme came up but the boot loader didn't work with it.

This is not a problem as all you have to do is run "sudo grub-install /dev/sdx where x is the drive with the MBR.

Burg is installed on its own, grub is not removed.

I tested Burg in both 9.10 and 10.04 testing cycles just because the guy wanted it tested.  I don't like icons on any menu and particularly not on my boot menu but it was testing after all.

Very nice piece of work, if not particularly my style.  Thought I would take a look at it and found the situation as it is and just wondered WTF?

---

### Post by ronacc on 2012-01-18
> **xyzzyman said:**
> You answered your own question. The developer hasn't made any updates since 2010. It also doesn't work with WUBI. Even if you ignore the WUBI issue, it's probably not worth dumping a working solution for one that's not actively maintained just for eye candy.

 They dumped the whole DE for eyecandy , have patience they'll get around to screwing up the bootloader .

---

### Post by xyzzyman on 2012-01-18
> **ronacc said:**
> They dumped the whole DE for eyecandy , have patience they'll get around to screwing up the bootloader .

Gnome 2.5 went the way of the dodo burg **rimshot**... Unity was more of a reaction to Gnome 3's devel's going towards eye candy and Canonical not agreeing. I'd be using Arch if it wasn't for preferring Unity over Gnome 3. I never thought I would wind up preferring global menu's, but now it's second nature.

A modern looking bootloader would be nice if anything just to break stigmas of Linux only being meant for server & 'computer nerd' use, but even Microsoft doesn't deal with it past text-mode.

---

### Post by ranch hand on 2012-01-18
> **ronacc said:**
> They dumped the whole DE for eyecandy , have patience they'll get around to screwing up the bootloader .
Seems like.

You remember how excited some folks were when Burg came out.  Surely someone knows more of the story.

Bean didn't strike me like a guy that would quit that quick.  Could have been wrong about that obviously.

Had a lot of folks willing to help with themes and such.  Went quite a ways toward not needing a lot of hard effort to keep it going.  That of coarse could have been a problem, the fun of making it work done and then just keeping it up with grub may have been a let down.

Came across this running a search, thought it was interesting, particularly the Launchpad link.  The forum for burg is the only link there that is dead.
[http://code.google.com/p/burg/](http://code.google.com/p/burg/)

Just kind of shocked.  There was, by a lot of folks in the testing forum anyway, a lot of support for it.  Would have thought some one would have taken it over if Bean were to quit.  Never lit a fire under me but there were several little threads and that one big one in 10.04-testing and now it is like it never happened?  Weird.

---

### Post by ronacc on 2012-01-18
a fancy bootloader doesn't really excite me , I use it for about 2 seconds to select which install I want to load  .

---

### Post by cecilpierce on 2012-01-18
Bean was realy Gung-Ho there for awhile, it was strange he just disappeared.
I still use it and its been working fine with the custom file, I guess theres not much more you could do to make it better.
I would like to see someone make grub a little more fancy.

---

### Post by ronacc on 2012-01-18
A few years ago one of the many distros I have installed had a really fancy bootloader , I think it was some generation of puppy but don't hold me to that , anyway it had a graphical background and animated penguins walking around . I worked ok at least for me but it was only used for that one release and I never saw it again so I guess it had problems .

---

### Post by philinux on 2012-01-18
> **ronacc said:**
> a fancy bootloader doesn't really excite me , I use it for about 2 seconds to select which install I want to load  .

+1. I themed the login screen way back. I just cant see the point now.

---

### Post by ranch hand on 2012-01-18
> **ronacc said:**
> a fancy bootloader doesn't really excite me , I use it for about 2 seconds to select which install I want to load  .
Yes.  I have a custom background for grub on all my installs  that matches the wallpaper on that install.  Makes it easy for me to know where grub is coming from when I boot.

If not for that the white text on a black background is fine for me.

It is just something that I kind of expected to be in the repo by now and possibly be default on the LTS.  Seems to go with the direction Ubuntu wants to go.  Was a well built piece of work.  I go looking for it and find this situation.

Figured this was the place to ask about it as so many people were so excited about it at the time.

Bean seemed to have been working on it while we were still trying to figure out how to boot installs that were on 2 partitions (first week after 9.10A1 was released).  Just kind of shocked that someone that would do that much, that early would just up and disappear.

---

### Post by ronacc on 2012-01-18
maybe he'll jump back in in awhile , lots of things can eat up your time , I recall you disappeared for awhile when you were getting that ranch set up where there was no net access .

---

### Post by cariboo on 2012-01-18
There was a similar question on the ubuntu-devel mailing list this morning, this is the answer from Colin Watson:

> On Wed, Jan 18, 2012 at 08:32:35AM +0000, Paul Sladen wrote:
> I think it's an excellent idea to streamline the Grub menu.  Could you
> perhaps try to mock up before/after "screenshots", so that it's clear
> each change that you'd like to make?
As the Ubuntu GRUB maintainer I'd prefer text.  Since we aren't going to
be making large changes to the visual layout at least in this cycle,
text should be quite sufficient, and much less work for bug reporters
too.

I think there are bugs about most of this already.  The main source of
tedium is that we don't have reliable data for all of this.  Finding the
Windows boot loader at all in a consistent way is more of a pain than
you might think, and even with Ubuntu you have the question of how to
deal with kernels that originated with old Ubuntu releases but that are
associated with more recent userspace.

> If you're not sure where to file these;  you're welcome to file them
> against "Ubuntu branding" for the moment:
>
>   [http://launchpad.net/ubuntu-branding/+filebug?field.title=Grub:+streamline+boot+entries](http://launchpad.net/ubuntu-branding/+filebug?field.title=Grub:+streamline+boot+entries)
No need for a layer of indirection; the correct package is grub2 in
Ubuntu.

-- Colin Watson 

---

### Post by ronacc on 2012-01-18
I guess I've been lucky , as I commented elsewhere grub2 has been rock solid for me for the last couple of cycles , finds all my multiple installs every time including windows and some distros still on grub (1) .

---

### Post by xyzzyman on 2012-01-18
> **ronacc said:**
> I guess I've been lucky , as I commented elsewhere grub2 has been rock solid for me for the last couple of cycles , finds all my multiple installs every time including windows and some distros still on grub (1) .

It's not really luck, it sounds more like that's why they are sticking with grub2 and not screwing with it.

---

### Post by kansasnoob on 2012-01-18
> **cariboo907 said:**
> There was a similar question on the ubuntu-devel mailing list this morning, this is the answer from Colin Watson:

Thanks for that :)

I agree with Colin. We need to focus on stability!

---

### Post by VMC on 2012-01-19
> **philinux said:**
> +1. I themed the login screen way back. I just cant see the point now.

That make me +2. I think it takes me just 1 second. My grub menu has been set in concrete for a year or two. I know the position I want to boot what OS I want. 

I made it real splashy with blue on white?

---

### Post by Ibidem on 2012-01-19
Well...Grub2 seems nice when it works right, but I managed to screw it up--install it from a chroot on an upgrade, and you just might see the same problems.  It got so fouled up, I had to manually correct the partition information.
Even reconfiguring after booting Ubuntu didn't work. 
When I went to edit the files, I couldn't figure out anything, so I just switched back to Grub1.  That took maybe 15 seconds to fix.

---

### Post by cariboo on 2012-01-19
> **Ibidem said:**
> Well...Grub2 seems nice when it works right, but I managed to screw it up--install it from a chroot on an upgrade, and you just might see the same problems.  It got so fouled up, I had to manually correct the partition information.
Even reconfiguring after booting Ubuntu didn't work. 
When I went to edit the files, I couldn't figure out anything, so I just switched back to Grub1.  That took maybe 15 seconds to fix.

What does this have to do with the topic of this thread? I'm going to leave it here, but it would be better in Testimonials & Experiences. instead of Precise Testing & Discussion..

---

### Post by ronacc on 2012-01-19
possibly what screwed up grub2 was that different installs don't always report the drive numbers the same , what is HD0 to one install may be HD2 to another install so it may have picked up the drive #'s of the install you chrooted from .

---

### Post by VMC on 2012-01-20
> **Ibidem said:**
> Well...Grub2 seems nice when it works right, but I managed to screw it up--install it from a chroot on an upgrade, and you just might see the same problems.  It got so fouled up, I had to manually correct the partition information.
Even reconfiguring after booting Ubuntu didn't work. 
When I went to edit the files, I couldn't figure out anything, so I just switched back to Grub1.  That took maybe 15 seconds to fix.

Run boot_info_script(see my blue link). You might have found the solution there. Apparently it's to late to diagnose your problem.

---

### Post by ranch hand on 2012-01-20
I use chroot all  the time to change grub around my several installs.  Never had a problem.

Have nothing at all against grub-legacy and if you want to use an unsupported boot loader that is cool with me.

If you want one that is supported I suggest reading the documentation.

---

### Post by cariboo on 2012-01-20
+1 for using chroot to fix/edit a grub2 problem.

---

