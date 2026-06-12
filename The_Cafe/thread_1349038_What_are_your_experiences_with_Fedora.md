---
title: "What are your experiences with Fedora?"
date: 2009-12-07
forum: The Cafe
---

### Post by PacSci on 2009-12-07
I've been looking at different distros recently, and one that stood out at me was Fedora. Based on what I've seen, it's about as runnable off of the disc as Ubuntu, and it's more geared to power users. Another thing I've read is that it gets the latest software faster than Ubuntu, which would be a big plus for me.

Does anyone have experience with Fedora (especially the Xfce spin, though general info is nice too) and could tell me if I'm right about these, and what they think about it compared to Ubuntu?

---

### Post by RiceMonster on 2009-12-07
My experiences are good. Haven't had any crashes. You're basically using a distro that a large number of the upstream developers are involved in. There's good security by default, and if you're familiar with apt, yum should be easy for you to learn, as it's syntax is very similar.

---

### Post by murderslastcrow on 2009-12-07
Yeah, Fedora's pretty evenly matched with Ubuntu. I think I heard that the latest release had some really questionable changes in security.

I like how the software center handles security- you can leave it authorized for several consecutive installations, then click the key icon to disable it if you don't want to wait for it to time out. A bit better than making you enter your password for each one, but still, if you install more than one at a time I wish you could use the checkboxes again. :\ But eh, it'll get better in time, I'm sure.

I liked Fedora last time I used it. I typically use lightweight DEs with it, though, so maybe I'm biased.

---

### Post by kevCast on 2009-12-07
It's very good, but can be a tad unstable at times. Your mileage may vary.

---

### Post by dragos240 on 2009-12-07
I had headaches. We have it on my mom's laptop. I guess I did something wrong.

---

### Post by SmittyJensen on 2009-12-07
Never used it for an extended period of time, 64-bit is a pain to get up and running (if you need a few 32 bit libs) and always discouraged me.
 
i wish all distros would have something like ia32-libs, so much easier. :<

---

### Post by RiceMonster on 2009-12-07
> **murderslastcrow said:**
> Yeah, Fedora's pretty evenly matched with Ubuntu. I think I heard that the latest release had some really questionable changes in security.

Yes, it did. Normal users could install signed packages from trusted repos without authenticating as root. Those were fixed shortly after the release in an update, though. There was a lot of drama about it.

---

### Post by slumbergod on 2009-12-07
Last time I tried it I had a few stability issues though I think they were more hardware related. They have a policy of only using open source stuff don't they?

If you give it a try please post your thoughts cos I am thinking of a change from Karmic.

---

### Post by doorknob60 on 2009-12-07
I haven't given it a good fair shot, but I'm not a huge fan of the package manager (or the size of their repos), and it's just not the distro for me really. I like more customizablity and building my system from the base up, but also want a good binary package manager (with big repositories), like apt-get, or even better, pacman. Not a bad distro at all, but I prefer Debian-based distros, and of course I like Arch too :)

---

### Post by gashcr on 2009-12-07
been using the fedora 12 XFCE spin for a couple weeks now, and its been a good time :D. Only thing I'm missing is Docky... jejeje. Actually, these guys made a great job putting together this distro, everything feels snappy and responsive, pretty solid actually. Highly recommended :)

---

### Post by Crunchy the Headcrab on 2009-12-07
I highly recommend the DVD install.  It allows you to choose which programs are installed, which makes for a nice setup.  Fedora also has a dude that does webcam fixes for laptops, so if you have an annoying upside down camera (like my asus), then chances are it will work right out of the box.  It worked for me.  I generally prefer ubuntu, but fedora is pretty stable, and is fun because it's slightly more cutting edge.

---

### Post by snowpine on 2009-12-09
Typing this from Fedora now; it is a great distro, very similar to Ubuntu. (more similarities than differences)

---

### Post by PacSci on 2009-12-13
I went ahead and installed Fedora (Xfce spin). It's a pretty nice system, and seems to respond a bit faster than Xubuntu on my laptop. I may end up using Fedora permanently on my laptop and desktop (but I'll still hang around here for the community). There are only two real issues I am having with it:

[LIST]
[*]The preference for "su"-style authentication over "sudo"-style, like Ubuntu. On the command line, sudo is still installed by default, and for installing packages I just had to add myself to the desktop_admin_r group, but for programs that use consolehelper like system-config-date and system-config-users I'm not sure how to get it to accept my user password instead of root (if I can get those to accept it*, I'll lock down root and just administrate as myself). This is compounded by the fact that gksudo isn't even in the package repositories.
[*]The command for describing a package being "yum info package" rather than "yum show package". I think I might write a Yum plugin to alias show to info.
[/LIST]

On the other hand, there are few "little things" I like:

[LIST]
[*]It seems to boot faster.
[*]I didn't have to enable a third-party repository to get the latest version of Mercurial.
[*]I don't have to shut off wireless whenever I boot to make it not use my crappy Broadcom card (the card is built into the laptop, so I can't remove it).
[/LIST]

I suppose that the second one kind of implies the overall responsiveness of Fedora updates compared to Ubuntu (which is still on Mercurial 1.3.1 in Karmic and was on 1.1.2 in Jaunty), which I like since I prefer to use the latest software.

Installing wasn't very hard (though it might be considerably harder than Ubuntu for those that are newer to Linux) and didn't take much longer than Ubuntu, but I forgot to set up the bootloader the first time through so I had to reinstall before I even booted the system. The next thing I will do is create a Live CD to carry around with me for emergencies (like being stuck at school in a room full of Windows computers). Right now, the process looks easier than Ubuntu Live CDs.

This may be due to Ubuntu's heritage, but one thing I noticed about Xubuntu vs. Fedora Xfce Spin is that Fedora puts more of Xfce's applications on the disc, while Ubuntu puts more of GNOME's.

In general, I think that Fedora strikes a good balance between the stability-first it-just-worksitude of Ubuntu and the freshness-first do-it-yourselfitude of Arch Linux, which are the other two distros I have major experience with.

*On that note, does anyone here with Fedora/RHEL experience know how to do this?

---

### Post by jrusso2 on 2009-12-13
Before Ubuntu I ran Fedora up until Fedora 5.  I found it to be too buggy compared to Ubuntu which I thought was more stable at least until recently.

---

### Post by clanky on 2009-12-13
I like Fedora, the only thing I would say is that if you are looking around because you fancy a change from ubuntu then you might want to try something a bit more different.

---

### Post by Techsnap on 2009-12-13
I've used Fedora on and off since Fedora Core 2, I think it's a brilliant system though it does get updated a heck of a lot, so it's quite cutting edge.

What I usually do is install the previous version (So at the moment I'm running 11 not 12). Then when the next version comes out I upgrade to the next version from what I'm using so it's always 1 behind the current release. 

This way RPMFusion has a working FGLRX and I still have a stable system with the latest release of KDE and this is how I've always done it with Fedora. Also I've never had Fedora break with an upgrade.

---

### Post by Crunchy the Headcrab on 2009-12-13
> **PacSci said:**
> 

[LIST]
[*]The preference for "su"-style authentication over "sudo"-style, like Ubuntu. On the command line, sudo is still installed by default, and for installing packages I just had to add myself to the desktop_admin_r group, but for programs that use consolehelper like system-config-date and system-config-users I'm not sure how to get it to accept my user password instead of root (if I can get those to accept it*, I'll lock down root and just administrate as myself). This is compounded by the fact that gksudo isn't even in the package repositories.
[/LIST]
In sudoers file (/etc/sudoers) insert (su visudo or su nano /etc/sudoers):

> loginname ALL=(ALL) ALL under > root ALL=(ALL) ALLthen you can add a default timeout on your password for that user:
> Defaults:loginname timestamp_timeout=2where 2 is a variable that can be any number for the time in minutes you want to expire before you are asked for your sudo password again.  In both cases replace loginname with your username (case sensitive).

---

### Post by Raffles10 on 2009-12-13
Fedora is test bed for RHEL. The idea seems to be that you use the dist', file bug reports and contribute to the next Red Hat release, all without a prize ! If it was like file 100 bug reports and win a holiday in Rio I could understand it. Why people want to beta test for Red Hat without any incentive beats me. :twisted:

Whatever floats your Linux boat I guess.

(SELinux in a desktop..... really !) :o

---

### Post by Crunchy the Headcrab on 2009-12-13
> **Raffles10 said:**
> Fedora is test bed for RHEL. The idea seems to be that you use the dist', file bug reports and contribute to the next Red Hat release, all without a prize ! If it was like file 100 bug reports and win a holiday in Rio I could understand it. Why people want to beta test for Red Hat without any incentive beats me. :twisted:

Whatever floats your Linux boat I guess.

(SELinux in a desktop..... really !) :oBecause Red Hat is successful at what Ubuntu dreams it could be?

---

### Post by Isengrin on 2009-12-13
I just tried it one, and it was a graphic-card-chaos.
Since in that time I didn't had much knowledge, just leaved for good. XD

---

### Post by Xbehave on 2009-12-13
Not a bad distro but
[LIST=1]
[*]Installing prop stuff, can be tricky (ms fonts were a PITA and when i complained i got fedora wasn't a distro for noobs)
[*]I found yum to be slow (some people claim it's faster than apt, but that was not what i saw, especially when searching)
[*]limited number of 3rd party repos (although the backports do stay very current), unlike ubuntu or opensuse.
[*]it uses SElinux, i ran into a couple of problems that you don't get with apparmor
[/LIST]

---

### Post by Raffles10 on 2009-12-13
> **Crunchy the Headcrab said:**
> Because Red Hat is successful at what Ubuntu dreams it could be?

You never know. One day there may be a Ubuntu Enterprise Edition that costs megabucks. ;)

---

### Post by mmix on 2009-12-14
it is stable

---

### Post by gnomeuser on 2009-12-14
Having been a Fedora user for years as well as part of the development team these are my observations:

1) The community is large and very technically capable, any solution anyone comes up with there is likely to have been vetted for several use cases by experts in the field.

2) I like that applications are kept up to date, I will never have to file a bug and be told to try the latest (except for projects like mplayer which seem to insist that you use CVS when filing bugs).

3) Given the rapid update cycle during a release, you often find yourself downloading a lot.

4) rapid updates also seem to require many reboots or x restarts to take advantage of fully, stability can suffer (but does more rarely than you'd expect).

5) They are rapidly anti Mono and have taken to disabling features in Mono using applications without debate or evidence, they will willingly insult and degrade their Mono maintainers (in the interest of disclosure I was one of the Mono maintainers and left due to this treatment).

6) Fedora is a high quality product, their QA processes are well defined and the dedicated bug triaging teams do excellent work. The developers are highly competent and when you file a bug you are nearly always sure that it will be taken care off. The results they bring are often a bit flawed though but the processes and people are in place, they will improve over time provided 7 is solved.

7) They lack instrumentation, Ubuntu's greatest weapon in making bug to fix loops short is Apport. With many releases on it's back now it's a polished product that works well. Fedora only just got such tools and their solution requires you to download all the debug symbols to get a backtrace.. uncool to the point of being not just useless but counterproductive.

8) The desktop lacks polish but certain areas are excellent. E.g. their GTK+ is very well maintained, they have a superior kernel team and their audio stack is kept in shape with rigor.

---

### Post by RiceMonster on 2009-12-14
> **Raffles10 said:**
> Fedora is test bed for RHEL. The idea seems to be that you use the dist', file bug reports and contribute to the next Red Hat release, all without a prize ! If it was like file 100 bug reports and win a holiday in Rio I could understand it. Why people want to beta test for Red Hat without any incentive beats me. :twisted:

Whatever floats your Linux boat I guess.

(SELinux in a desktop..... really !) :o

Because Red Hat is a company that's extremely important to the Linux world, and does a huge amount of work improving it. That's not just the kernel, either. So basically, you get to use a lot of new technologies as they come out. Whether that appeals to you or not is a different story.

Complain all you want about Red Hat charging big bucks for RHEL, but Ubuntu relies on a number of the stuff they develop, whether you like it or not.

---

### Post by kevCast on 2009-12-14
> **Raffles10 said:**
> Fedora is test bed for RHEL. The idea seems to be that you use the dist', file bug reports and contribute to the next Red Hat release, all without a prize ! If it was like file 100 bug reports and win a holiday in Rio I could understand it. Why people want to beta test for Red Hat without any incentive beats me. :twisted:

Whatever floats your Linux boat I guess.

(SELinux in a desktop..... really !) :o

We get it, Fedora isn't as good as Arch.

---

