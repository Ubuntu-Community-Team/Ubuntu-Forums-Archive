---
title: "My return to Xubuntu"
date: 2008-07-15
forum: Testimonials &amp; Experiences
---

### Post by cardinals_fan on 2008-07-15
I started my Linux journey with Ubuntu Dapper about two years ago.  By the time Feisty rolled around, I had become unhappy with Ubuntu and moved on to other distros.  After trying many distros (Linux, BSD, and Solaris), I had almost settled on Vector Linux.  It had the same simplicity that I learned to love with Slackware, but was lighter. Before settling in with Vector, I decided to give Xubuntu 8.04.1 a chance.  There were three things that had me interested in Xubuntu:

1) Ample repositories.  The Ubuntu repos are vast in comparison to Vector's, and being able to "aptitude install" almost any program is a big plus.

2) Xubuntu lightness.  Past Xubuntu releases (especially Gutsy) were horrendously bloated, but I heard that the Xubuntu team was trying to lighten the distro.  I wanted to see whether they succeeded.

3) LTS.  I've done the whole "screw around with the bleeding edge" thing with Fedora, Zenwalk Snapshot, and Arch, and I'm ready to just sit down and use my computer.  With an LTS release, I can receive security updates for three years - in other words, until I leave for college.

So, did Xubuntu Hardy live up to my expectations?  Here are my thoughts, divided into pros and cons.

_**PROS**_
* Ease of installation.  I'm usually a fan of text-based installers, but Ubiquity works great.
* App selection.  I'm mostly impressed with the apps included in Xubuntu.  Xfce, Abiword/Gnumeric, GNOME-Games, and a few other key apps.  Enough for a functional system, but not too much bloat.  I wasn't happy with the presence of file-roller; Xarchiver is a better choice for a light Xfce system.
* Package management.  Big repos make life easy.
* Speed.  Xubuntu is actually very fast with this release.  It boots up FAST, and is pretty snappy overall.
* Hardware support.  My wireless adapter worked out of the box, and the NVIDIA drivers installed fine.
* New artwork.  I firmly believe that a distro's default look is its least important feature, because appearance is easy to customize.  However, the Xubuntu defaults are very pleasant and clean.

_**CONS**_
* Graphical bootsplash.  I despise these things.  When I boot up my computer, let me see what's going on!
* Sudo.  I'm used to running as a normal user and su'ing to root for system administration.  Using sudo feels weird, and I really don't like the default 15-minute timeout.  It feels very insecure.
* The Add/Remove apps thing is just stupid.  I use the command line for most package installation, but Synaptic handles GUI package management beautifully.  Why is Add/Remove included?

Overall, I'm very pleased with Xubuntu Hardy and it's now my main OS.

---

### Post by atomkarinca on 2008-07-15
> **cardinals_fan said:**
> 
* The Add/Remove apps thing is just stupid.  I use the command line for most package installation, but Synaptic handles GUI package management beautifully.  Why is Add/Remove included?

I guess because it looks nicer and has a brief description of the application. I think it's nice to have choices.

---

### Post by aysiu on 2008-07-15
Well, the good news, then, is that all your **Cons** can be remedied.

Remove the *usplash* and *gnome-app-install* packages, [change the *sudo* timeout to 0 seconds](http://ubuntuforums.org/showthread.php?p=116697#post116697), and then use ```
sudo -i
``` every time you want a root terminal.

---

### Post by Neobuntu on 2008-07-15
You had me at your #1.

Your pros were excellent.

I totally disagreed with every one of your cons. Go figure.

Anyway, your first points echo the real majors needed. Your cons underscore that people are different.

How much faster/leaner is Xubuntu 8.04 over it's previous? I may need to upgrade an install. That system now has 256MB RAM and it did seem the 256MB went farther in the past. I used to run Kubuntu on it fine. They like to use my (some what more limited) installed and tweaked Icewm for speed. It uses a bit less base RAM.

Lighter, is definitely the right direction for Xubuntu.

---

### Post by cardinals_fan on 2008-07-15
> **atomkarinca said:**
> I guess because it looks nicer and has a brief description of the application. I think it's nice to have choices.
Choices are always good.  I just don't see any difference, because Synaptic also has descriptions.
> **aysiu said:**
> Well, the good news, then, is that all your **Cons** can be remedied.

Remove the *usplash* and *gnome-app-install* packages, [change the *sudo* timeout to 0 seconds](http://ubuntuforums.org/showthread.php?p=116697#post116697), and then use ```
sudo -i
``` every time you want a root terminal.
Very good.  I already changed the timeout, so I'll tackle the bootsplash now.  I remember a way to have both the pretty little status bar AND the text info, so I'll try to set that up.

EDIT: I added an alias in my .bashrc for "su", so it now equals "sudo -i".  Perfect :)
> **Neobuntu said:**
> You had me at your #1.

Your pros were excellent.

I totally disagreed with every one of your cons. Go figure.

Anyway, your first points echo the real majors needed. Your cons underscore that people are different.

How much faster/leaner is Xubuntu 8.04 over it's previous? I may need to upgrade an install. That system now has 256MB RAM and it did seem the 256MB went farther in the past. I used to run Kubuntu on it fine. They like to use my (some what more limited) installed and tweaked Icewm for speed. It uses a bit less base RAM.

Lighter, is definitely the right direction for Xubuntu.
I find Xubuntu Hardy much faster than any release since Edgy.

---

### Post by hyper_ch on 2008-07-16
I see the point of Add/Remove for new people that do not know what different packages are called. With Add/Remove you get a listing according to the category so they can just browse that.

---

### Post by azolotko on 2008-07-16
Add/Remove feature is just perfect for newbies.

---

### Post by Canis familiaris on 2008-07-16
> **azolotko said:**
> add/remove Feature Is Just Perfect For Newbies.

+1

---

### Post by cardinals_fan on 2008-07-16
> **hyper_ch said:**
> I see the point of Add/Remove for new people that do not know what different packages are called. With Add/Remove you get a listing according to the category so they can just browse that.
> **azolotko said:**
> Add/Remove feature is just perfect for newbies.
Synaptic has package categories too...

[[img]http://xs329.xs.to/xs329/08293/2008-07-16-121652_1280x1024_scrot115.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs329&d=08293&f=2008-07-16-121652_1280x1024_scrot115.png)

Anyway, that's a minor quibble.  It doesn't take up much space.

---

### Post by mivo on 2008-07-16
I use Xubuntu on my laptop, and I actually like it quite a bit. I considered using it on my regular machine as well. It's just significantly faster, though on my desktop it would probably not matter (it's more on the high end of things, unlike my laptop). I disagree on the importance of a pleasing default theme. That is what users seen first, and first impressions are important, especially if someone is checking out the distro or, even more critical, if it's someone who considers switching from Windows. Yes, the theme is easy to change, but it's an extra step that's needed. If I were to design a distro, I would give the default theme a much higher priority than the Ubuntu devs seem to.

What I like about Xubuntu is that it comes with software I actually use, as oppised to a lot of Ubuntu default apps that I don't need. That's also very easy to change, but it's another convenience aspect like the default theme. 

I like graphical splash screens. :) In Gutsy I had none, because my video card was too new at the time (8800GTS) and while it wasn't a huge problem, a proper splash screen looks more professional.

---

### Post by cardinals_fan on 2008-07-16
> **mivo said:**
> I use Xubuntu on my laptop, and I actually like it quite a bit. I considered using it on my regular machine as well. It's just significantly faster, though on my desktop it would probably not matter (it's more on the high end of things, unlike my laptop). I disagree on the importance of a pleasing default theme. That is what users seen first, and first impressions are important, especially if someone is checking out the distro or, even more critical, if it's someone who considers switching from Windows. Yes, the theme is easy to change, but it's an extra step that's needed. If I were to design a distro, I would give the default theme a much higher priority than the Ubuntu devs seem to.

What I like about Xubuntu is that it comes with software I actually use, as oppised to a lot of Ubuntu default apps that I don't need. That's also very easy to change, but it's another convenience aspect like the default theme. 

I like graphical splash screens. :) In Gutsy I had none, because my video card was too new at the time (8800GTS) and while it wasn't a huge problem, a proper splash screen looks more professional.
I don't **personally** care about default themes.  I realize that it makes a huge difference in terms of publicity.  BTW, I love that gray theme in Xubuntu.  Gray is my favorite color :)

Xubuntu has most of the apps I need and only a few that I don't.

---

### Post by mivo on 2008-07-16
Isn't it baby blue? ;)

---

### Post by cardinals_fan on 2008-07-16
> **mivo said:**
> Isn't it baby blue? ;)
Not anymore.  The theme is a pleasant gray and the wallpaper is multicolored but tasteful.

BTW, I forgot a pro.  Xubuntu doesn't include any legally dubious (in the US) codecs.

---

### Post by bmac on 2008-07-17
[cardinals_fan]("http://ubuntuforums.org/member.php?u=360925")

I agree. I've often wondered why we needed two apps that perform identical tasks.

As you indicated it's no big deal as it doesn't use any real resources. Just makes you wonder...

---

### Post by Frak on 2008-07-18
> **azolotko said:**
> Add/Remove feature is just perfect for newbies.
+1 to whatever the last plus was to this post.

---

### Post by cardinals_fan on 2008-07-20
I'm a bit confused by those who say that Add/Remove apps is good for newbies.  I would say that it causes them considerable confusion.  Let's say that a new user reads about an app online and decides to install it.  They're used to Add/Remove, so they use that.  But if the app is one of the many that is not in Add/Remove, they might assume that it isn't in the repos and try to compile it from source rather than just searching Synaptic.  Then they run into dependency issues and don't get their program installed.

---

### Post by mivo on 2008-07-20
Hmm, actually, I sort of like the Add/Remove component for "newbies". It includes neat little descriptions and I believe some screenshots, too. I never really used it myself, but if I look at someone like my mother (in her 60s and using her computer for browsing and email, with Lotus Notes her only actual practical experience at the office), she'd probably get a lot more out of this than she'd get from Synaptic, mostly because Add/Remove allows you to "browse". People may find software they were not really looking for, or that they didn't know exists, but that looks useful or fun. If you use Synpatic, you usually know what you're looking for.

(But in either case you usually do not get the latest version, which is a real issue with fast moving projects like Pidgin or Battle of Wesnoth.)

---

### Post by Joeb454 on 2008-07-20
I've just done a minimal install of Ubuntu from the alternate CD, and then read this...I've just decided to ```
sudo apt-get install xubuntu-desktop
``` :D

---

### Post by cardinals_fan on 2008-07-20
> **Joeb454 said:**
> I've just done a minimal install of Ubuntu from the alternate CD, and then read this...I've just decided to ```
sudo apt-get install xubuntu-desktop
``` :D
Give it a shot.  I like the app selection (aside from file-roller) a lot.

---

### Post by Canis familiaris on 2008-07-21
> **cardinals_fan said:**
> I'm a bit confused by those who say that Add/Remove apps is good for newbies.  I would say that it causes them considerable confusion.  Let's say that a new user reads about an app online and decides to install it.  They're used to Add/Remove, so they use that.  But if the app is one of the many that is not in Add/Remove, they might assume that it isn't in the repos and try to compile it from source rather than just searching Synaptic.  Then they run into dependency issues and don't get their program installed.

I see the need of an advanced button in Add/Remove which will run Synaptic

---

### Post by Joeb454 on 2008-07-21
That's not actually a bad idea

---

