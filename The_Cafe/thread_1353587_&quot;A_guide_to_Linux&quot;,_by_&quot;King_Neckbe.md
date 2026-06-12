---
title: "&quot;A /g/uide to Linux&quot;, by &quot;King Neckbeard&quot; of 4chan"
date: 2009-12-12
forum: The Cafe
---

### Post by earthpigg on 2009-12-12
even a broken clock is right from time to time. as a matter of fact, it may even be right ***twice*** a day.

likewise, even [4chan]("http://en.wikipedia.org/wiki/4chan") is capable of good stuff. 

Thus, i submit "A /g/uide to Linux" by a 4chan persona that goes by "King Neckbeard".

(I doubt the primary author, "Neckbeard" is a member of our happy little forum community, by the way. He is not a Canonical fan, but he does speak of Ubuntu in a positive light in this document.)

it is, essentially:

1) an introduction to Linux and FOSS
2) an introduction to common Linux concepts unfamiliar to many - package management, distributions, and different release models
3) different distributions
4) Community.
5) The Terminal
6) Basic Troubleshooting - "You mean i can use google to solve problems??! and there are discussion forums?! and CLUBS that provide free tech support (LUGs)?!"


aaaand, its 8 pages long, plain english, and does not evangelize. not bad.

---

### Post by FuturePilot on 2009-12-12
Wow, that's pretty good. It's not preachy or anything and lets the person reading it make their own decision. I think I'll keep it around. Never would have guessed someone from 4chan wrote it.

---

### Post by earthpigg on 2009-12-13
> **FuturePilot said:**
> Wow, that's pretty good. It's not preachy or anything and lets the person reading it make their own decision. I think I'll keep it around. Never would have guessed someone from 4chan wrote it.

never would have guessed, except for the typos? :D

i like his distro list. you could argue till the end of the world ***any*** of the categories he lists.... they aren't perfect.

but they certainly aren't bad, either.

---

### Post by Gizenshya on 2009-12-13
be careful, you gonna get raped!

---

### Post by Rainstride on 2009-12-13
> **earthpigg said:**
> never would have guessed, except for the typos? :D

i like his distro list. you could argue till the end of the world ***any*** of the categories he lists.... they aren't perfect.

but they certainly aren't bad, either.

from what I have seen king neckbeard is probably one of the least trollish on /g/ but I'm still kind of surprised that anything good would come from there. I stopped going to /g/ for the most part because its nothing but trolling/nvidia vs. ati these days. Ill give it a read.

---

### Post by jordanmthomas on 2009-12-13
Install Gentoo.

---

### Post by earthpigg on 2009-12-13
> **jordanmthomas said:**
> Install Gentoo.

gentoo....?

what do?

---

### Post by NoaHall on 2009-12-13
You think I'm going to download/open anything from that site? No thanks.

---

### Post by CharlesA on 2009-12-13
> **NoaHall said:**
> You think I'm going to download/open anything from that site? No thanks.

Same here. Heh.

---

### Post by earthpigg on 2009-12-13
> **NoaHall said:**
> You think I'm going to download/open anything from that site? No thanks.

if the .pdf was NSFW, this thread would have been jailed by now.

---

### Post by NoaHall on 2009-12-13
> **earthpigg said:**
> if the .pdf was NSFW, this thread would have been jailed by now.

I'm thinking more along the lines of not safe for my computer.

---

### Post by earthpigg on 2009-12-13
well, here: 

(not formatted as nicely and not as easy to read as the pdf...)

```
                                   A /g/uide to Linux
                                                Version 0.8.5
    1.   What is Linux?
    2.   Is Linux Right For You?
    3.   Which Distribution Should I Choose?
    4.   Getting Started
    5.   The Package Manager
    6.   The Terminal
    7.   Giving Back
    8.   Troubleshooting/miscellaneous
1. What is Linux?
         The term 'Linux' is used in several different ways. Linux is sometimes used as the name of a
kernel initially written and still maintained by Linus Torvalds. It's also used as a general term for
operating systems that use the Linux kernel and the GNU userspace, although there are operating
systems that use GNU without Linux and Linux without GNU. For the purposes of the guide, the
second meaning will be used.
         Enough about the name, what is Linux? Linux is a Unix-like operating system that consists
primarily or completely of Free and Open Source Software(also known as FOSS). Unix-like means
that it follows the same design principles as the UNIX operating system that was developed by Bell
Labs. To grossly oversimplify it, the main idea is that everything is a file. Other operating systems
following this design include FreeBSD, Solaris, Mac OS X, HP-UX, and AIX.
         Free and Open Source Software means two things: It is free to be distributed, and the source
code is available for any developers to modify and redistribute. This allows for easier cooperation
between different projects, prevents vendor lock-in, and allows developers with differing viewpoints to
fork without losing compatibility with each other.
         Finally, there is a very important point to note for Windows users. Linux is NOT Windows.
Many things function in a different way because Linux is not designed to be a Windows substitute.
Projects of that nature exist in the form of FreeDOS and ReactOS
2. Is Linux Right for You?
While Linux is a great solution for many people, some can't make the transition at this time and that is
fine. Jumping into Linux when it's not the right fit for you can leave you hostile towards Linux, so
only make the switch if you are willing. If you fall somewhere in between, Wubi or a virtual machine
might be an option(for more details, see the Installation/miscellaneous section).
Reasons why you may have a problem transitioning to Linux:
    &#8226; You play high-end PC games on a regular basis
    &#8226; You need to use specific program(s) for work, school, or personal usage that do not have a
         viable Linux alternative
    &#8226; You don't have the time to learn or troubleshoot a new system
    &#8226; Your primary computer is shared or used for critical work
    &#8226; Your hardware is currently unsupported or requires too much configuration for your time or
         level of experience
Reasons to choose Linux:
    &#8226; Most Linux distributions have native package managers, which make installation, removal, and
         upgrading of software easy and secure
    &#8226; A wide collection of desktop environments and window managers are available to choose from
    &#8226; Linux is easy to customize to fit your individual needs
    &#8226; You want an operating system that consists of free software
    &#8226; You like to learn new things
    &#8226; You have an interest in programming and like the availability of source code in the tools you
         use daily
3. Which Distribution Should I Choose?
The open nature of Linux has led to a myriad of different variations to choose from. However, the
variety of choices can be quite daunting for new users. This guide will provide a brief overview of the
most popular distributions(also called 'distros' by many linux users). You can find more information at
their respective websites, [www.distrowatch.org](www.distrowatch.org) , or use an interactive chooser at
[http://www.zegeniestudios.net/ldc/](http://www.zegeniestudios.net/ldc/) or [http://polishlinux.org/choose/quiz/](http://polishlinux.org/choose/quiz/).
Notes on terms:
-Rolling release: software in the repositories is upgraded to newer versions on a regular basis, meaning
there are no explicitly defined versions of the distribution. This keeps the user up to date, but there is a
larger risk of breaking the system.
-Point release: software in the repositories is only upgraded for bug fixes and security patches, with
some newer software being available through backporting. This has an advantage of further testing for
stability, but leaves the software dated.
-LiveCD/LiveDVD/LiveUSB: An operating system that can be booted directly from a CD, DVD, or
USB. This requires no configuration or installation, and is very helpful for system recovery or testing
your hardware. These discs typically allow for installation to a hard drive as well.
Name: Ubuntu                                       Name: Zenwalk
Difficulty: Beginner                               Difficulty: Intermediate
LiveCD: Yes                                        LiveCD: Yes
Release Model: Point; every 6 months, extended Release Model: Point; about every 6 months
support release every 2 years                      Description: A Slackware-based distribution that
Description: A Debian-based distribution developedintends to make improvements to package
and supported by Canonical which aims to provide management while maintaining compatibility
a simple, easy to use, operating system.           Related Distros: Slackware, SLAX
Related Distros: Debian, Mint, Knoppix
Name: Mint                                         Name: Debian
Difficulty: Beginner                               Difficulty: Intermediate
LiveCD: Yes                                        LiveCD: Yes
Release Model: Point ; correlated with Ubuntu      Release Model: Point release about every 2 years;
releases                                           Rolling release of unstable branch
Description: An Ubuntu-based distribution aimed at Description: A community driven distribution that
making codecs more easily available and providing provides a stable experience of supports for many
the user with eye candy.                           different architectures. Also renowned for it's
Related Distros: Ubuntu, Debian, Knoppix           dedication to free software.
                                                   Related Distros: Ubuntu, Mint, Knoppix
Name: Mandriva
Difficulty: Beginner                               Name: Slackware
LiveCD: Yes                                        Difficulty: Advanced
Release Model: Point; about every 6 months         LiveCD: No
Description: A distribution backed by the French Release Model: Point; One to two releases per year
Mandriva company that aims to be easy to use.      Description: One of the earliest distributions, aims
Related Distros:                                   to be simple in design and Unix-like
                                                   Related Distros: Zenwalk, SLAX
Name: OpenSUSE
Difficulty: Beginner                               Name: Arch
LiveCD: Yes                                        Difficulty: Advanced
Release Model: Point; One to two releases per year LiveCD: No
Description: A distrubution by Novell that aims to Release Model: Rolling
provide the user with an easy install and the      Description: A user-centric distribution that aims to
centralized graphical setup tools of YaST.         give users up-to-date software and easily control
Related Distros: SUSE Linux                        their system.
                                                   Related Distros:
Name: Fedora
Difficulty: Intermediate                           Name: Gentoo
LiveCD: Yes                                        Difficulty: Expert
Release Model: Point; about every 6 months         LiveCD: Yes
Description: A community driven distribution       Release Model: Rolling
based on Red Hat that aims to be on the leading    Description: A distribution aimed at giving the user
edge.                                              convenient tools to have complete control of their
Related Distros: RHEL, CentOS                      system to optimize it as they see fit.
                                                   Related Distros: Sabayon
4. Getting Started
         If you've already decided that you want to try Linux and have decided which distribution is the
best fit for you, the next step is installation. Mainstream distros have installation discs that can be
bought or downloaded for free. You will typically have a choice of a direct download from the distros
or a bittorrent download. There will often be a range of installation media to choose from, varying
from a very small image for a network based install to a robust set of repositories spanning several
DVDs. Make sure you select the proper disc for download. If you are running Windows on the
computer you will install Linux on and intend to keep it(which is advised for new Linux users), it's a
good idea to defragment your hard drive to make partitioning easier. There are also LiveCDs that may
be a better choice for users who want a casual introduction to Linux without serious risks.
If you encounter any problems, see the troubleshooting section or your distro's documentation
    &#8226; Download the disc image
    &#8226; Burn the image to a physical disc
    &#8226; Place disc in tray and reboot
    &#8226; Follow installation instructions and consult your distro's documentation (for advanced help with
         partitioning, see troubleshooting)
    &#8226; Reboot your computer when installation is complete
    &#8226; Choose Linux in the bootloader
5. The Package Manager
One major difference with Linux distributions is that they almost all have a centralized package
manager. Many package managers handle dependencies to ensure you have everything you need to run
a program. Most of the time, if a program is available in the package manager, it will be the simplest
solution, although you can do it yourself if you have advanced needs. Depending on your needs, many
distros have both graphical and command line prompts, so choose the best option for you.
6. The Terminal
One thing that often discourages new Linux users is being instructed to type a command. It is for many
a realm of the unknown, which can be discomforting. While they are a useful tool, The purpose of
this section is to give the user a basic understanding of how terminal commands work. Lets say there's
a command called 'foo'. The first thing you will likely want to do is enter one of the three following
commands:
foo --help
foo -h
man foo
These will bring up a brief description of the syntax and options. Commands will typically consist of
three things, the program name, flags, and files. Here's an example with the copy command, cp.
cp -u folder/files/file1 folder/backups/backup1
In this example, 'cp' is the command, '-u' is a flag, and 'folder/files/file1' is the source file, and
'folder/backup/backup1' is the target file. The source file will be copied to the location of the target
file. '-u' is a flag for update and will only replace the target file if the source file is newer. The key to
effective usage of the terminal is not in memorization of all the commands and flags, but rather in
seeing the patterns and grasping the underlying concepts.
Another important thing to note is the commands needed to perform administrative tasks. They are su
and sudo. su will ask you for your password and give your root privileges(root is another word for the
administrator) for subsequent commands. sudo will give you root privileges for a single command and
prompt you to enter your password. It is advised that you use root privileges only when needed, as you
can harm your computer through irresponsible use of root.
7. Giving Back
         If you've found that you've enjoy Linux and free software, there are several ways to give back to
help improve Linux. You can donate to or buy support from one of your favorite projects, you can
report bugs, try out beta versions of software, and offer suggestions. You can give technical support
and guidance to others, seed torrents of free software, and share free software with our friends. If you
have the necessary skills, you can contribute code or help in translation to other languages.
8. Troubleshooting/Miscellaneous
Installation
If your computer starts as normal after inserting the installation disc, your BIOS may not be set to boot
from a CD/DVD. Press F2(the key or key combination may be slightly different for your computer, so
if the specific key doesn't appear onscreen during startup, check for further details of your
manufacturer and model) at startup to access the BIOS. Navigate through the menus and set your
CD/DVD drive in a higher priority than your hard drive.
Wubi
Wubi allows you to install Ubuntu within a Windows partition. It makes installation somewhat safer to
your Windows partition, but has a set of peculiarities, the most noticeable being that performance
degrades if the Windows install is fragmented or full. Additionally, if your Windows partition fails,
your Ubuntu is lost as well.
Virtual Machines
This is a viable option for those who are interested but can't risk compromising a critical system. It has
the drawbacks of reduced performance and additional strain on system resources, although the
installation process is generally simpler since there are limited amounts of hardware being emulated.
VirtualBox and VMware are both well supported VMs.
Unetbootin/LiveCDs
LiveCDs allow you to boot Linux without installing anything. Knoppix is one of the most popular and
robust LiveCDs, although many installation discs also function as LiveCDs. There are also LiveCDs
for specific tasks such as music (dyne:bolic) and science (Quantian). A program called Unetbootin
allows users to make LiveUSBs from many popular distros.
Macs
The installation process is somewhat different on Macs. You can use Boot Camp on an Intel Mac, and
there is documentation of the specifics on the internet. If you have a PPC Mac, you will need to use
different installation media. Debian, Yellow Dog Linux, and Fedora all have support for PPC.
Windows Solutions
Many Linux users may find themselves still in need of Windows-only software. There are various
solutions with different strengths and weaknesses.
Dual Booting
Leaving a Windows install on the same hard drive is a common solution and fairly easy to set up. The
biggest advantage is that all of your Windows applications will still run, but you will need to reboot to
use them. You can also install Windows on a computer with Linux already installed, but this tends to
cause complications with the bootloader(Windows installation will overwrite the Master Boot Record).
During the installation process, options for partitioning will come up. Shrink the Windows partition,
and create partition(s) for Linux is the freed space(If you don't know what you need, two partitions, one
for the root directory and a smaller on for swap space would be a safe bet). Most distributions should
either load GRUB or LILO automatically after installation is completed. Most distros have NTFS-3G
installed by default, but if it isn't you should be able to get it through your package manager or build
from source For Windows to access your Linux files, you will need to download Ext2IFS. If this
solutions sounds difficult for you but you would still like to dual boot, the above Wubi solution may be
a good option for you.
WINE/CrossOver/Cedega
WINE is an ongoing project to allow Windows programs to run on Linux via a compatibility layer.
This lets you run apps without restarting and minimal overhead. Because this project involves reverse
engineering, applications work to varying degrees(some work with comparable performance to
Windows, some work significantly worse, and some don't functional completely or at all). Two
commercial variants exist, one specifically for gaming, called Cedega, and another called CrossOver
has a stable version targeted at office users and a more experimental build aimed at gaming. Crossover
contributes their code back towards WINE while Cedega does not and does not use code since WINE
changed to the LGPL. You can check an applications compatibility at the WINE AppDB
Virtual Machines
Allows you to run an operating system inside a window. It's more reliable than WINE and doesn't
require rebooting, but it does take additional resources and hardware acceleration is not fully supported
Additionally, installation media is required. Popular virtualization software includes VirtualBox (freely
available in most repositories) and various products by VMware.
64-bit vs. 32-bit
Many distros offer the choice of an install based on the x86_64 architecture in addition to the x86
architecture. If you are using an x86_64 processor(Anything currently offered by AMD and Intel that
isn't on netbooks should be x86_64), then running a 64-bit release. x86_64 offers support for more
RAM, some architectural improvements, and increased performance in some applications. Because of
the free and open nature of Linux, most of the software has been ported to x86_64 and many other
architectures, and 32-bit software can run with the appropriate libraries, although there may be certain
obstacles. Proprietary software, such as Java, Flash, and certain hardware drivers were once a serious
obstacle to x86_64 adoption, but Java has been ported, and a FOSS version exists. An alpha release of
Adobe Flash 10 for x86_64 exists and is available here. Regarding hardware drivers, testing with a
LiveCD is generally a good idea for finding out if your hardware is supported.
Problem Solving
If you need help for a specific problem, you should do the following steps in order
    1. RTFM
         Many problems have solutions easily available to you through man pages or in the release notes
         of the distro or application's release notes or FAQ/Help section. If the help here is over your
         head, you should seek help elsewhere.
    2. Google it.
         Using a search engine will often return a relevant answer. Good terms to include in your search
         are &#8220;Linux&#8221;, your distros name, and the application or hardware that is giving you trouble.
    3. Go to the forums
         Try going to your distro's or program's forums for help. These forums are designed for help,
         and if you can show that you've made an earnest effort on your own, they will typically be
         helpful. Asking smart questions will prove generally prove more fruitful in getting a helpful
         reply, so reading (or at least skimming Eric S. Raymond's How To Ask Questions The Smart
         Way is highly advised.
    4. Ask a friend
         If you have friends that use Linux or friends that are generally computer literate, they are a good
         resource for assistance. They will have patience with you, and can help you in a more direct
         way.
    5. Linux User Groups
         These are groups of Linux users that gather on some kind of regular basis. They can be helpful
         to new users, but they meet on their time instead of yours and the nearest LUG may be too far
         away. You can find a LUG here.
Last modified May 29, 2009 Maintained by King Neckbeard. Send revisions, suggestion, questions,
and complaints to [email]neckbeard.king@gmail.com[/email] along with how you would like to be accredited.
Additional contributers:
sirobvious !CfagJg.fuc
Install !GENToOO59.
Various anonymous members of /g/
This work is licensed under the Creative Commons Attribution-Share Alike 3.0 Unported License. To
view a copy of this license, visit [http://creativecommons.org/licenses/by-sa/3.0/](http://creativecommons.org/licenses/by-sa/3.0/) or send a letter to
Creative Commons, 171 Second Street, Suite 300, San Francisco, California, 94105, USA.

```

---

### Post by DonPachi on 2009-12-15
>implying king neckbeard isn't a troll

laughing_elf_man.jpg

---

### Post by DeadSuperHero on 2009-12-15
Overall, a highly enjoyable read. I like it!

---

### Post by earthpigg on 2009-12-15
> **DonPachi said:**
> >implying king neckbeard isn't a troll

laughing_elf_man.jpg

[COLOR="YellowGreen"]>implying you yourself are not a troll.[/COLOR]

rms-toecheeze.jpg

---

### Post by AllRadioisDead on 2009-12-15
> **NoaHall said:**
> I'm thinking more along the lines of not safe for my computer.
It seems to be safe for the rest of us, so maybe you should stop being such a paronoid sourpus.
The way I see it, Linux needs all the help it can get.

---

