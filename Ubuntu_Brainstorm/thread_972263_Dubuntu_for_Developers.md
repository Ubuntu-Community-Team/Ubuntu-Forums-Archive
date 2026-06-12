---
title: "Dubuntu for Developers"
date: 2008-11-05
forum: Ubuntu Brainstorm
---

### Post by wistle on 2008-11-05
I've recently switched from *****(name of other distribution) to Ubuntu... and I love it (after having tried some other main stream distros as well.

The only thing the got to me was the lack of "out of the box" support for development when I had to set up 2 customer machines and 3 development PC's for my project.  It took several days and several gigabytes of downloads.

So without further delay, here's my goal: I want to create a new flavour following the path of Edubuntu of an Add-on disk containing various tools needed for development.

Looking at forums I seen that this is a common discussion point with roughly the same end result each time:
- most people think its a good idea
- nobody agrees on what should be done
- nothing actually gets done

I think the key to success here would be to avoid the wars and setting some ground rules:
- Make it easy for beginners
- Freedom of choice
- Simplicity

Knowing the subject, the tools and the people... this is more difficult than it appears. But here's what I have in mind:

Create (or modify an existing) installer that would give you a few selections with the option to drill down where necessary.  For example:

Select one or more  Programming Platform:
- C++
- Python
- Perl
- Java
- etc

For each one you select you can drill down and get more options, e.g.:

Choose IDE: 
- KDevelop
- Ajunta
- etc
- all (Suggested for beginners)

Choose Additional Tools:
- GDB 
- Cachegrind (Valgrind)
- CVS
- etc

There may be more or less options (and plenty more disagreements) to follow, but the intention is to rather install to many things than to confuse with too much detail... thinking especially about beginners here.

We can also stick to (or at least initially) supported packages from the Ubuntu and Kubuntu communities.  This way the focus will be on:
a. building a user-friendly GUI installer
b. selecting the packages to put on the CD (so you don't need a Terabyte internet cap when setting up several PC's)

From experience I know what I need to do my work and it includes a list of about 25 different packages, most of which I realize is not installed when I try to use it or try to compile.  Surely this would be an "easier" way even if it is not the most efficient.

It should be noted that there are plenty of useful resources that can guide you, but when you are a newbie (or switching to Ubuntu like me) it is quite a daunting and time consuming process.

I believe that by doing this we can make Ubuntu the preferred distro for Linux development, same as Edubuntu did for Education.  Just one more way of promoting this great distro.

On the Ubuntu Brainstorm forum Canonical clearly stated that this should be a community project and that they will not proceed with this themselves.

Anybody willing to help me start such a community project?

---

### Post by smartboyathome on 2008-11-05
Its been suggested before, and what it comes down to is someone having to do it themselves.

---

### Post by wistle on 2008-11-06
I agree.  What I'm saying is: "I'm doing it! Who's with me?"

I'll start the project, the forum, the wiki, anything it takes! But I need community members to give there input and commitment as no single person knows all the languages, tools, IDE's etc.

---

### Post by j3frea on 2008-11-06
Well, my vote goes in for Eclipse (perhaps also the web side stuff... I haven't tried that largely because of its size). [I use Eclipse for Java stuff]

And SciTE - the best syntax highlighting non-cli-based text editor ever! :D [SciTE is awesome for basically anything (it's not an IDE though - nor is it meant to be one)]

Also, this will probably need to be developed but how about a gui installer of Apache (or <insert alternative popular server here>), PHP (or, <insert other server side language here>) and MySQL (or <whatever database you like>) so basically a LAMP setup thing with options for what mix you want.

Maybe some sort of Internet Explorer test suite using IES4Linux or something (although certain stuff still doesn't work there - I use a virtual machine)

I don't do much low level stuff so I can't comment on the best utility for it.

---

### Post by wistle on 2008-11-06
Thanks for the comments.  

I've created a Launchpad team specifically for this.  There are also links to an existing Wiki and Project Blueprints.  If you want to help, or just issue some comments, please join:

:arrow: [http://launchpad.net/~dubuntu-team](http://launchpad.net/~dubuntu-team)

I'm busy contacting anyone that I can find that has worked on this before and inviting them to join again.  Joining the team will keep you up to date and give you the opportunity to make a contribution.

---

### Post by damoxc on 2008-11-06
What about Devbuntu instead?

---

### Post by danf_1979 on 2008-11-06
> **damoxc said:**
> what about devbuntu instead?

+1

---

### Post by MadsRH on 2008-11-07
> **damoxc said:**
> What about Devbuntu instead?

+1
Makes more sense :-)

---

### Post by wistle on 2008-11-10
Join fist... name later...

Join us at: [http://launchpad.net/~dubuntu-team](http://launchpad.net/~dubuntu-team)
Read more: [http://wiki.ubuntu.com/Ubuntu-Developer](http://wiki.ubuntu.com/Ubuntu-Developer)

---

### Post by davidpeace on 2008-11-26
I just started using ubuntu about a month after Hardy came out. I love it. I was looking for an alternative to windoze and discovered a world of possibilities. I am learning Python as my first programming language and have been exploring different IDEs. Something like this for beginners, like me, would be great, especially when the enthusiasm ramps up and they, like me, would eventually like to develop for Linux in general, and Ubuntu in specific. The only problem I see is that some people, again, like me, don't really have gobs of room and abilities to keep expanding and expanding. So many choices are rather daunting for beginners. Do try this? What if it doesn't work for the language I choose to learn? What if I don't like it now, but what possibilities are there that it can grow on me?... For the absolute beginner, keep it very simple: minimum choice-making and lots of tutorials. But at the same time there needs to be some ability for exploration. For example, it may turn out that Python isn't suited to what I want to do or the style I eventually decide to develop. I'm still up in the air as to what direction I want to go with the whole thing and how to go about it. Other than being a complete novice in the programming aspect, and still fairly new to Linux, I am learning at a rapid rate. Others may find themselves on steeper learning curves. These ideas should be addressed as well.

That all being said, and given what I've said about myself above, how else can I help?:popcorn:

---

### Post by davidpeace on 2008-11-30
Did a check and the name Dubuntu is also the name for another derivation:

#
#
dubuntu-6.06-livecd-i386.iso
Dubuntu [http://www.dubuntu.com/](http://www.dubuntu.com/) Dubuntu is a Chinese GNU/Linux operating system based on Ubuntu. The goal of this new distribution is to provide a Linux ...
[www.metalinker.org/samples/dubuntu-6.06-livecd-i386.iso.metalink](www.metalinker.org/samples/dubuntu-6.06-livecd-i386.iso.metalink) - 2k - 

Anyway, here's my suggestion for a logo/default desktop:

---

### Post by mhh91 on 2008-11-30
Devbuntu is a better name in my opinion :)

i also think programs like dh_make ,build-essential and debhelper should be added to the distro,for packaging purposes,as they don't come already installed with ubuntu,you have to get them from the repo's

thanks for such great idea,guys :)

---

