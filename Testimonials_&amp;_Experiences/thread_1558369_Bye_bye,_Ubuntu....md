---
title: "Bye bye, Ubuntu..."
date: 2010-08-22
forum: Testimonials &amp; Experiences
---

### Post by asbesto on 2010-08-22
Hi,

finally I gave up on Ubuntu.

It was a funny trip. I'm thankful to everyone.

Many time ago it was very nice, because Ubuntu saved me a lot of time in configuring things, to have a running system without pain. As a 25+ years experienced UNIX sysadmin/user, i was tired to do every time the same things to do what I have to do (eg. configuring the same thing by hand over and over, mounting medias by hand over and over, and so on).

But about 2 years ago I strongly feel Ubuntu took a totally different direction. 

And Ubuntu team started filling the entire system with paranoid security crap (the same password asked again and again and again for configuring things in MY OWN desktop, or the PolicyKit CRAP, the PAM settings, millions of daemons running for nothing etc.)

Also, they started adding crap over crap - stupid daemons doing unrequested stupid stuff, keeping the system running on things and using memory and cpu. And this is going worse in every version. 

And, wanna talk about device support? Old version with hardware running perfectly out of the box, and new versions with bugged or removed support for them? 

And, what about old (and working!) versions of software REMOVED by repositories when a new (and bugged!) version is added? :(

So in this time I started measuring and comparing the time I used to install and configure a Debian GNU/Linux system for my needs, against the time I have to THROW AWAY removing all the crap from Ubuntu, configuring it for a normal and not stupid user need (ex. the 60 sec. shutdown delay, or the "Are you sure" when closing an XTerm, or stupid things like that)

And it's a LOT of TIME. Really a LOT of PAINFUL time, to fix STUPID things. :mad:

And last but not least I had to deal with those stupid forum policies about "security" (thru obscurity), when proposing solutions to all this password madness, obtaining infraction warnings and having my topic closed or censored by administrators.

I also wrote an interesting page on our wiki about how to purify Ubuntu from all this CRAP (you can search "UbuntuPurification" on [http://lab.dyne.org](http://lab.dyne.org) - I can't add the url here because someone will surely censore and warn me :lolflag:)

Days ago I finally noticed that the time for configuring UBUNTU as a normal GNU/Linux system (and not like a windows Vista CRAP system) has overpassed the time used to configure a Debian GNU/Linux system to the normal needs of a normal (not impaired :) ) user. 

So, for now this is a goodbye, Ubuntu. I pass. I want UNIX, not WINDOWS.

I pass with the hope for a change of direction of you all: getting back to the UNIX roots, to GNU/Linux, where you can log in as root on YOUR console (tty1), where you can "su -" without pain, where you can configure the network on your own computer without writing the same damn password every time, where you don' have tons of daemons conflicting and fighting against themselves, where software is solid tested and not in alpha or beta version (remember Firefox some time ago?), where support for working hardware is not DESTROYED from a version to another (HDSPA, network cards, etc), a direction in which working stuff is keep working in the right way, etc. etc...

I will continue to spread Ubuntu to newcomers, but just as a first try to a real GNU/Linux OS, before installing something real useful. 

Really I hope for a change of directions!

):P

Ah, I forgot: my DEBIAN GNU/Linux is FAST LIKE HELL! ;)

---

### Post by Elfy on 2010-08-22
moved to testimonials

---

### Post by fatality_uk on 2010-08-22
Bye then!

---

### Post by DrMelon on 2010-08-22
Well, it's open source. You don't like it, you *do* have the ability to change it yourself. Especially since you're such an experienced UNIX user, editing the source shouldn't faze you at all.

---

### Post by the8thstar on 2010-08-22
I like the password as a security feature to prevent inexperienced people from damaging system files and configurations. My family members use this computer and they have no experience whatsoever with Linux. So it DOES serve a purpose.

About the software regressions, I have found that my webcam was sometimes not supported anymore from one version to the next. I don't know why that is. And yes it is annoying when it happens to you because you have to boot into Windows just to be able to use Skype.

---

### Post by MarcusW on 2010-08-22
I've switched from Ubuntu to Debian, and I don't get what you mean about the password thing. As long as I log in using my regular user, I have to use sudo a bit more in Debian than I had to in Ubuntu, to get the same things done. Also, for "su" without actually having a root account just do "sudo -s".

---

### Post by gradinaruvasile on 2010-08-22
Well i too switched to Debian without the drama.. :) Ubuntu was really useful in learning Linux as i had very limited experience before.

BTW the sudo settings can be simply set to the defaults Debian uses - no tty_tickets and/or longer password expiration time or something, there are tons of settings.
I on the other hand configured Debian to work with sudo as Ubuntu does. Then i left a terminal with root logged in and do the root stuff from there.

---

### Post by ral0r3us on 2010-08-22
So the point of the QQ is?

---

### Post by kaldor on 2010-08-22
> **ral0r3us said:**
> So the point of the QQ is?

Not a QQ.

I agree with the OP; I haven't been able to use Ubuntu for a long while now apart from on the server/one work machine. I use Mint (fixes a lot of Ubuntu's problems), OpenSUSE, Fedora/CentOS and sometimes dabble with random other distros. 

Ubuntu is definately not what it used to be. It looks great, though. I use the Ambiance theme even on other distros.

---

### Post by Noz3001 on 2010-08-22
If one wants Ubuntu to be like it used to be, download an old release. Doesn't this seem the obvious solution?

---

### Post by kaldor on 2010-08-22
> **Noz3001 said:**
> If one wants Ubuntu to be like it used to be, download an old release. Doesn't this seem the obvious solution?

Not a matter of readjusting, it's a matter of quality. 

What's the point in downloading an old, outdated release?

---

### Post by Noz3001 on 2010-08-22
> **kaldor said:**
> Not a matter of readjusting, it's a matter of quality. 

What's the point in downloading an old, outdated release?

In OP's post, he says that about 2 years ago Ubuntu started the change into something he didn't like.

---

### Post by Xbehave on 2010-08-22
Wow in 25+ years of unix experience you never heard of a netinstall and the choice to uninstall features you don't want.

millions of deamons :O here i have 29 processes running as root (maybe a couple more as haldaemon) lets break them down
init (can you even have a unix system without init)
cron (same again)
getty, X, kdm, cupsd (pretty much inevitable)
irqbalance, acpid (hardware changes these deamons are needed now)
hald & udevd (while not perfect hardware compatibility seams to have skyrocketed since these became widespread)
Networkmanager (easyenough to remove)
wpasupplicant and dhcpd (pretty much needed if i want networking working)
plymouth and upstart-udev-bridge (unneeded)
policykit (nice tool to get stuff working securly but i don't know much about it)

so if by millions you mean 2, then yeah there are 2 unneeded daemons running using up nearly 0 cpu, hell even i you dont want your hardware to work and forsake hal, udevd, networkmanager, irqbalance, acpid, dhcpd and wpasupplicant that's still less than a dozen and they mostly sit there not using CPU when they are not needed (check powertop if you don't believe me)

---

### Post by d3v1150m471c on 2010-08-22
couldn't you just login as root? btw what OS doesn't have some apps you don't like?

---

### Post by Sporkman on 2010-08-22
Re su, I just have this in my login aliases:

```
alias su='sudo bash'

```
...and in my .bashrc:

> if [ "`whoami`" = "root" ]; then
   PS1='${HOSTNAME}: ${debian_chroot:+($debian_chroot)}$PWD# '
else
   PS1='${HOSTNAME}: ${debian_chroot:+($debian_chroot)}$PWD> '
fi


---

### Post by iponeverything on 2010-08-22
The drama!

Adiós amigo. Enjoy Debian, it is clean, stable and still Linux. 

For me, the "I am leaving Ubuntu" sounds the same as "I am selling my car" or "I am changing the way I drive to work"

---

### Post by jward3010 on 2010-08-22
I'm with you on a lot of your points. I recently put Euro800 into a new machine with high performance hardware and found I couldn't even install Ubuntu. I had little problems with most all Ubuntu versions and my older PC. 

I find the Gnome Desktop eventually gets on my nerves. It's a little sluggish and behind and it's overall top and bottom taskbar design is the greatest space hog on the planet. It's a very "fat" desktop system. I find Windows 7 quicker in general - just more alert, more ready. I don't mind the security aspect that much, it's highly secure straight out of the box and that's where other virus ridden systems (ahem...) failed abysmally. Now, true it could be refined to something slightly less strict, but only slightly.

The hardware support is an annoying area - On Jaunty everything would work exceptionally, On Lucid it would be all a mess again - and you wouldn't being trying it on an old machine(Like you say, it would probably work on an old machine). Another issue here is hardware manufacturers and there lack of interest in creating and open sourcing drivers which means a lot of the drivers your hardware is currently utilising are "guessware", unfinished and slightly buggy. Linux developers can only go so far.

Overall, if you're looking for a system that just works and lets you get work done - you'll still have to stick with commercial OS's like Windows and Mac OS. You can be lucky and get a 100% compatible machine or you spend some configuration time getting a sloppy machine more refined but ultimately Ubuntu isn't ready for everyday use - for me anyway.

---

### Post by Mustard on 2010-08-22
I think the OP should really try Arch linux.  I would think it would fit his needs perfectly.

---

### Post by rjbl on 2010-08-22
[I]
[B]@jward3010

[/B]I[/I]*'m with you on a lot of your points. I recently put Euro800 into a new  machine with high performance hardware and found I couldn't even install  Ubuntu. I had little problems with most all Ubuntu versions and my  older PC. *

Sorry, after my 25+ years of installing all flavours of MS DOS and Windows and so many GNU/Linux distros (since c1994) I have to say I simply do not believe you. In your turn, you can disbelieve any claims that I might make that there is a thriving colony of leprechauns dwelling at the bottom of my garden. Meanwhile, please don't troll, it is a very boring waste of everyones' bandwith.

rjbl

---

### Post by rjbl on 2010-08-22
**@asbesto**

Ah ....... they don't make the past like they used to, do they? 

Whenever I get really pissed-orf with the 21st Century I dig out my trusty config file and make my current Ubuntu look just like my good ol' Sun Workstation did in 1989. 

.....And on a really good day I can keep my XP SP3 (fully WUSsed) box running for longer than 8 hours without FSX freezing-up (useful if you are 'flying' from here to Benson, Arizona); or the whole box BSODing on all my hopes and dreams. 

Have ze nice day, y'all
rjbl

---

### Post by afroman10496 on 2010-08-22
Well, if you want UNIX, there's [Solaris]("http://www.oracle.com/us/products/servers-storage/solaris/index.html") you spoiled lump.

---

### Post by xircon on 2010-08-22
```
alias su='sudo bash'

```
Useful tip (I am a Mandriva refugee).  I am finding the whole sudo thing a royal pain, so I turned it off (and got a gentle telling off from some fellow forumers :))

I am also a Unix sysadmin (Scosysv), I was also finding the Ubuntu experience was equating to Vista, but with tips like the above, my experience is getting better.

---

### Post by afroman10496 on 2010-08-22
> **Sporkman said:**
> Re su, I just have this in my login aliases:

```
alias su='sudo bash'

```
...and in my .bashrc:

Well, you can always ```
gksudo gnome-terminal
``` from a normal terminal session.

---

### Post by donescamillo on 2010-08-22
When I took up Ubuntu about 1.5 years ago I was very happy that after the installation all peripherals worked.
But...
On one notebook I have 9.10 and it runs OK. I tried to install 10.04 and it would not install, some problems with the video support, it garbles the picture. I guess that can be fixed (by going to root and do obscure things) but I dont have the time and the desire. And its no good telling people if you dont like something go and fix and recompile kernel.
On another notebook there was a bug in GRUB (probably it is not Ubunu's fault) that caused the CDROM to disappear even when I boot in Win. It is documented, described and not fixed at least two versions later.
I know I can go to Debian (but there my Wifi does not work and I needed to recompile a video driver) or Windows (as someone might suggest) but how can this attract more users

donescamillo

---

### Post by MarcusW on 2010-08-22
For the love of god, hope can people dislike sudo over su? "sudo -s" or simply "sudo su". It's only one line to actually activate the root account as well, it's not that hard...

---

### Post by Spice Weasel on 2010-08-22
> **MarcusW said:**
> For the love of god, hope can people dislike sudo over su? "sudo -s" or simply "sudo su". It's only one line to actually activate the root account as well, it's not that hard...

sudo passwd to set the root password, then you don't even need "sudo su", just "su".

---

### Post by Sporkman on 2010-08-22
> **Spice Weasel said:**
> sudo passwd to set the root password, then you don't even need "sudo su", just "su".

...but then you've enabled the root account. Security risk. Plus, does su keep your aliases & home directory location?

---

### Post by MarcusW on 2010-08-23
> **Sporkman said:**
> ...but then you've enabled the root account. Security risk. Plus, does su keep your aliases & home directory location?

Don't know, but I'm pretty sure "sudo -s" does.

---

### Post by asbesto on 2010-08-23
Thank you for every answer :)

Is not a matter of myself changing distro to something similar to a '80 VAX/VMS :D

It's a matter of quality. Quality in building software, in mantaining his usability and looking for the compatibility with the past hardware. 

):P

---

### Post by Spice Weasel on 2010-08-23
> **Sporkman said:**
> ...but then you've enabled the root account. Security risk. Plus, does su keep your aliases & home directory location?

And being able to use a non-root user's password to gain root privileges isn't a security risk? Having the root account enabled makes no difference to security unless you have disabled sudo entirely.

---

### Post by Sporkman on 2010-08-23
> **Spice Weasel said:**
> And being able to use a non-root user's password to gain root privileges isn't a security risk? Having the root account enabled makes no difference to security unless you have disabled sudo entirely.

No, the sudo scheme is more secure (at least from the outside of the system) in that the root user's login name is not the universally-known "root", rather it's the more secure user-chosen name.

---

### Post by Spice Weasel on 2010-08-24
> **Sporkman said:**
> No, the sudo scheme is more secure (at least from the outside of the system) in that the root user's login name is not the universally-known "root", rather it's the more secure user-chosen name.

I agree that using sudo to configure the system would be more secure in a corporate environment where you are administering a system with lots of different users with different permissions, but if it's a home system or home server they'd only have to look through a few usernames and anyone with the patience to crack into a Linux system wouldn't have any trouble browsing through the names of users. Just look for the one that isn't standard.

---

### Post by v0idloser on 2010-08-24
> **DrMelon said:**
> Well, it's open source. You don't like it, you *do* have the ability to change it yourself. Especially since you're such an experienced UNIX user, editing the source shouldn't faze you at all.
Sure, because he wants to waste his time editing so many programs to fit his needs, when all he has to do is move to another distro which doesn't do all the things he dislikes in the first place.

The main concern for him is the fact that time is seriously wasted, that's what he said.

---

### Post by julianb on 2010-08-26
> Well, it's open source. You don't like it, you do have the ability to change it yourself.

Ubuntu is 700MB of compressed files, representing far, far more than 700MB of source code.

Don't be surprised when the vast majority of users aren't poking around to figure out where in that labyrinth of files is the code responsible for (insert-issue-here). Maybe it makes sense that most of the documentation is about fixing problems without fiddling with source code, BUT, that creates a situation where most users don't know where to start with altering existing programs' source code.

---

