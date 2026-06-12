---
title: "Moving on from n00b status"
date: 2006-03-27
forum: The Cafe
---

### Post by Basu on 2006-03-27
I've been using Ubuntu for over 6 months now. I've learnt a lot of things and I think I'm between newbie and intermediate now. I'm now trying to get beyond that stange ot intermediate-advanced. Problem is, I don't know how. I'd like to eventually to be able to do to things like install and patch kernels without hassle and regularly compile, install and maybe fix new (unstable) stuff. You guys have any ideas on how I should proceed?

---

### Post by Jason_25 on 2006-03-27
Do you have a spare pc(s)?  That way you can jump right into whatever dangerous thing you want to try.

---

### Post by Basu on 2006-03-27
unfortunately, no. Not at the moment at least. But I was wondering, what sort of "dangerous thing" would be a good learning experience

---

### Post by ssam on 2006-03-27
learning to program is a good way to learn about computers.

i recomend either bash scripting or python to start with. you can find more information in the programming forum.

---

### Post by Basu on 2006-03-27
Please [visit my blog]("http://basu715.weblogs.us") for a more detailed version of what I want to do, as well as a partial battle plan. And thanks for being a great community!

---

### Post by Kvark on 2006-03-27
I'm in the same position. The problem is that Ubuntu doesn't break to require you to learn how to fix it and it doesn't require you to learn how to compile stuff either.

The best solution seems to be to dual boot with Ubuntu plus a source based distro like Gentoo or Arch. Then you will have to get used to compiling, tweaking, breaking and fixing stuff real quick.

Another solution would be to help beta test Ubuntu's unstable development release. That should force you to learn how to find and fix problems plus trace and report bugs. But it sounds like Dapper is already too stable to be a challenge.

Personally I tried installing Linux From Scratch to dual boot with Ubuntu. It has great documentation and is a very good learning experience. But I had to give up pretty fast because I am too impatient to wait for things to compile "argh, it's been 10 mins now whats is taking so much time??? ... grr now it's been going for 15 mins wtf is it doing??? *jumps around madly*".

---

### Post by Basu on 2006-03-27
Can anyone tell me how to install Arch or maybe Gentoo, but get them to use Ubuntu's menu.lst & GRUB? that way, if I do mess anything up, I can atleast be ceratin that the comp will boot safely into stable Ubuntu.

---

### Post by bonzodog on 2006-03-27
I have been using linux as a sole OS for 9 years now, and I would still only class myself as intermediate. 
Get yourself into something like Slackware or Zenwalk, or BSD. They have a steep learning curve, and not all of the community is friendly, but there will be people willing to help you learn. There you will learn things like the intracacies of the Xorg file (you have to set it up yourself on first boot of Slackware), and learning about building programs and providing bug-fixes. You will learn just how powerful the command line will be, and not to be afraid to run a machine entirely from it. You will learn about directory structures, and if you build software yourself, learn all about dependencies and how they work and link in to the root tree. Get your self a good book or two from someone like O'reilly, and sit down and read it away from the computer, it will teach you an awful lot.

---

### Post by kanem on 2006-03-27
[QUOTE=Basu]Can anyone tell me how to install Arch or maybe Gentoo, but get them to use Ubuntu's menu.lst & GRUB? that way, if I do mess anything up, I can atleast be ceratin that the comp will boot safely into stable Ubuntu.[/QUOTE]
For Gentoo you can just not install Grub during the installation, and it should leave your current Grub configuration intact in the MBR. But to boot into Gentoo you will have to add a Gentoo entry into your current menu.lst

---

### Post by endersshadow on 2006-03-27
So nobody has to go to his blog, here's his mission statement:

>    I&#8217;ve been using GNU/Linux for over six months and by now I consider myself in between newbie and intermediate. But us usual I&#8217;m not satisfied and I want more. In this case, I want to know more about what Linux can do and what I can do with it. By this I mean that I want to try out unconventional, probably dangerous stuff. Problem is, I really don&#8217;t know how to go about making the transition from post-newbie to Linux hacker. I know some things that i could do: Namely trying to upgrade to the relatively unstable Dapper and maybe installing a customized kernel.  However neither of these look likely to happen as firstly I don&#8217;t have the time and secondly I don&#8217;t have a spare PC to fall back if I mess it up (which I invariably will, the first time at least). So I&#8217;m pretty much stuck with a mission critical system on which to try out all my weird and wonderful experiments. Not the best of situations.
    What to do? Well, I&#8217;m starting to make a plan to hack away at my existing GNU/Linux system from the top down. That means I&#8217;ll start to strip down my system by gradually removing software, services and daemons, keeping only what I need. By doing that I&#8217;ll gradually dig down to a minimum-frills core system, which I can then start improving by replacing components with custom-compiled, more efficient alternatives. I&#8217;ll do this in small, reversible steps, so that if anything goes wrong, I can fix it back. I have about two months to Dapper, in which time, I should have a pretty good idea of what I need and what I want. Once I fresh install Dapper, I can do all that again, but this time with more confidence, and in a more aggressive way. I&#8217;ve started a thread at the Ubuntu forums to get some feedback. Let&#8217;s see how it all goes.

As per my recommendations, learn your way around CLI and around the file structure.  Figure out where stuff is and what it does.  Compiling programs won't teach you too much about Linux...it's just ./configure && make && make install most of the time, so nothing too special.  Writing those programs tells you a lot more about it.

Also, compiling your own kernel is actually a fairly straightfoward process, it just takes forever.  Also, when you say that you want to be a "Linux hacker," are you saying that you want to hack on the kernel, or you want to hack on the other programs surrounding it.  From a developer's perspective, it takes a while to actually grok what's going on with a program once you have the source (it took Mozilla about two years to fully understand Netscape).

I would say that the best way to go about things is not to remove stuff from your system and recompile it (it's actually rather time consuming...and it doesn't boost efficiency all that much, if at all), but rather, start poking around, customizing your system, and finding programs that do what you want to do, and if they don't exist...make it.  And when you ask for help, don't be afraid to ask, "Okay, I did X and it worked, but what did it do?"  That's the best way you can learn anything about it.

And if you want to be a kernel hacker, you'd best be served buying a book...

---

### Post by IYY on 2006-03-27
Learn vim. ;)

---

### Post by briancurtin on 2006-03-27
[QUOTE=Basu]Can anyone tell me how to install Arch or maybe Gentoo, but get them to use Ubuntu's menu.lst & GRUB? that way, if I do mess anything up, I can atleast be ceratin that the comp will boot safely into stable Ubuntu.[/QUOTE]
check out the arch installation documentation, it is very good. if you wanted, you could keep your current partition scheme and not reformat some of the drives (like your /home) if you wanted to and just keep all of your stuff but have a new OS to add to the list. i used ubuntu before and took a few files over to arch and it worked great. take a copy of your xorg.conf if you make the switch, it will come in handy.

---

### Post by Basu on 2006-03-27
is there a way to find out what kernel modules that my system is actually using? I did a modprobe -l and got dozens of things like wifi and wireless lan which i never use. And what is LVM? Is there a place where I can learn about what startup scripts/ programs Linux uses at boot?

---

