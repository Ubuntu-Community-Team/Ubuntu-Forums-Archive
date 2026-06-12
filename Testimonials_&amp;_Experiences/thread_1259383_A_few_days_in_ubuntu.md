---
title: "A few days in ubuntu"
date: 2009-09-06
forum: Testimonials &amp; Experiences
---

### Post by FunkyRes on 2009-09-06
Despite my registration date, I only just installed Ubuntu (I was planning to back when I first registered but never did)

I am a long time Linux user, my first distribution was MKLinux DR3 on a brand spanking new 233MHz Beige G3 w/ 96MB of ram. I had to buy a 2GB scsi disk to do that install.

I have played with Debian before (Potato, Sarge) but not in a long time.

Currently I use CentOS 5.3 as my main OS.
-=-

I installed Ubuntu 9.04 desktop edition.

The good:
The torrent speed for getting the ISO was amazing. Thank you to the seeders.
I like a single CD that is installable. Much better than a DVD if you have the bandwidth to deal with fetching additional packages.

Booting is fast. Very fast. Fastest I've ever seen. Maybe that's partially because whenever I install Fedora or CentOS I install a bunch of server stuff that come with daemons, I have no desire to play with server software in Ubuntu, I'll stick with CentOS for that.

I really really REALLY like the fact that apt asks me about libraries it thinks I don't need after removing a package. That's nice.

Lot's of really nice repositories that so far seem to integrate very well at my fingertips. The reason I installed was twofold:

A) I was getting tired of maintaining my own multimedia RPM's - especially when changes to packages in EPEL repository kept breaking them causing me to need to rebuild what I was maintaining. I thought the point of enterprise linux was to NOT include updates that version shared libraries unless there really is no other choice, but it's happened several times. The EPEL stance is it is up to the maintainer.

With ubuntu, so far everything multimedia I've needed, and I mean everything, has been a repo I could easily find.

So now for my multimedia needs (right now mostly ffmpeg, kino, etc.) it looks like ubuntu is what I'll be using.

B) I wanted to play with bleeding edge browsers that use gtk webkit, as they supposedly have the ability to use gstreamer for html5 multimedia.

I found repos for those bleeding edge browsers, but it looks like they don't have any of the html 5 media stuff enabled, so I have to do more research, might be webkit build time option or a development branch patch that isn't quite ready for public consumption. Anyway, using GStreamer for html5 media I think is the right way to do it in Linux, especially with the fluendo plugins (which I have).

-=-

The bad:

The default theme - I worked at UPS for over a year, I don't want a default theme that looks like UPS. Brown is not good. Really. It's almost depressing. I know earth tones may be popular, but a light green would be nicer. Or blue. Even hot pink would be better than brown.

I'm not fond of how Debian packages are made, and while there is sufficient documentation for it, documentation is nowhere near as friendly as it is for RPM.

Also, are there any tools such as mock in Fedora land that one can use to build packages in a sane environment where a chroot is created and only declared build dependencies are pulled in? Because I can't seem to find such a build system.

Emacs is ugly. I'm going to have to see if borrowing the red hat default configuration makes it better. Emacs is so much nicer to use in CentOS / Fedora. I'm talking gui invocation, console invocation is the same.

Here's the really annoying thing though.
Much of the community provided documentation is "sudo this" and "sudo that" and includes instructions "cut and paste this in a terminal" and the line to cut and paste is sudo this or sudo that.

No. Don't tell people to cut and paste things with sudo in it.
Tell them to run it as root. Real potential for harm via social engineering or owned servers that run howtos or just plain typos when new users are conditioned to blindly cut and paste sudo commands.

Several howtos I saw had cut and past commands for using sudo to append stuff to the sources list. Very bad. A typo on your howto and you just royally screwed up some n00b who may not be able to recover.

When a file needs to be edited as root, instruct the user to use a text editor. Much safer.

Also, speaking of repos, a lot of instructions that say they are for jaunty involve modifying the main sources.list file.

There's a directory where you can put individual files without risking screwing up the main file. It's /etc/apt/sources.list.d/

I think it's a new feature, not sure it is new with 9.04 but I don't remember it in classic Debian. But new or not, if you are writing pages for jaunty telling n00bs how to do things and there is a very safe way that does not risk messing up a critical source list file, that's what you should instruct them to do. I was amazed at how many jaunty specific tutorials didn't even mention that directory where individual source list files can go. Most n00bs won't understand that a directory named like a config file but with a .d is for that kind of thing. Tell them.

Also - the way repositories are added in Red Hat world is simply better.
They are typically added by a package. You install foorepo-noarch.rpm and it puts the config file where it needs to go. First invocation of yum that wants to install a package from it, and it asks you if it can import the gpg key for package signatures.

Much more user friendly than what ubuntu does.

That is probably difficult to solve w/o changing how apt works, but it is a difficulty for nOObs. Probably not a real big deal though.

Another nitpick - after installing the nvidia driver, the gui was even slower. I'm on a 2.6GHz X2 processor with 2GB of RAM and a GeForce 6800 XT with 256MB of vram. No - it's not a brand new computer, but it's not old, and it is more powerful than what most non geeks have unless they *just* bought one.

The problem of course was with the nVidia driver, the eye candy effects were enabled. Don't do that. Yes, they are neat, but they really slow things down. Let those who want the eye candy but otherwise useless effects specifically enable them, don't make the rest of the world specifically disable them. Unless you have a very modern system it makes the OS feel slow.

-=-=-

Overall - the good massively outweighs my nitpicks.
I'm probably going to stick with CentOS for most things, but I must say, I'm extremely impressed and I will definitely recommend Ubuntu as a desktop OS - because it rocks in that department.

---

### Post by armandh on 2009-09-06
most of your cons are over my head [call me n00b]

but I don't see how pasting a sudo command in terminal is any worse than habitual root access.
at least you are asked for your password as a sanity check
[for the session or time out which ever comes first]

as for editing a config

I found opening sudo gedit in terminal and using the find function a noob easy GUI. 
and it backs up the original!  same time same place. easy to find

a lot is what one is use to I guess

---

### Post by binbash on 2009-09-06
If you do not tell sudo blabla, you have to write a page to teach what he is doing. Also there are a LOT better boot times on other distros like gentoo or arch. I agree with the other parts especially artwork part.

---

### Post by Megaptera on 2009-09-06
I use blubuntu to avoid the brown. In the repos.

---

### Post by HappyFeet on 2009-09-06
I noticed how you kept saying "it should be like redhat/rpm". No, it should not. You are just not used to it. It did not become the world's most popular distro because they don't know what they're doing. Secondly, if you were hoping to influence the developers, you are in the wrong place. Anyway, have fun with ubuntu.

---

### Post by FunkyRes on 2009-09-06
> **HappyFeet said:**
> I noticed how you kept saying "it should be like redhat/rpm". No, it should not. You are just not used to it. It did not become the world's most popular distro because they don't know what they're doing. Secondly, if you were hoping to influence the developers, you are in the wrong place. Anyway, have fun with ubuntu.

I did not keep saying "it should be like redhat rpm"

Secondly, this forum is titled testimonials and experiences.
That's exactly what I posted. So smurf off.

---

### Post by FunkyRes on 2009-09-06
> **binbash said:**
> If you do not tell sudo blabla, you have to write a page to teach what he is doing. Also there are a LOT better boot times on other distros like gentoo or arch. I agree with the other parts especially artwork part.

You only have to tell a user once how to run something as root.

After that, you tell them to run it as root.
As far as boot times, it very well may be the fact that I'm doing absolutely nothing with servers etc. and thus do not have many services.

Some faster boot times that I have seen actually cheat, starting gdm before system is finished booting which gets you to a login screen faster but you still have to wait.

---

