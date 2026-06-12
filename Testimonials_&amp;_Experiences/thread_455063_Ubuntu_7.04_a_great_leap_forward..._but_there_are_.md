---
title: "Ubuntu 7.04 a great leap forward... but there are still some issues to be solved"
date: 2007-05-26
forum: Testimonials &amp; Experiences
---

### Post by Prisma on 2007-05-26
Ubuntu 7.04 is a great improvement over previous releases. Features like that you can just click to install restrictive drivers or that you just have to open a movie to download the relevant codecs, and also that your wireless and wired connection just works out of the box have solved i would said MOST of the main Linux issues. However, there are still some issues that on my opinion as an end user keep bothering people on this forums and scare people away to switch.

It is a great feature that when you download a .deb package you can just double click it and it install itself like in windows. This is essential for people who don't have a degree in computer science and for example want to do something as simple as install the latest version of Frostwire, Google's Picasa or Google's Earth in their computers running Linux or try out the new version of Nero Linux 3 which is pretty cool. So my thanks to Debian, Ubuntu and the great efforts of the whole Linux community for that great leap forward. :p

However....

In windows, when you download a .zip file you can just double click to search for the .exe file inside and install it. In Linux you can also double click a compressed file and decompress it but you still need to install .bin files via console. So i think, it is URGENT to find a solution to this problem. 

People should be able for example to download Realplayer 10 from the web and just double click the file to install it like you do with a .deb package.

Also, often there are not .deb packages available for download on websites. Only .rpm packages, so it would be great if you can just install any type of Linux packages automatically. If I understand correctly there is something called Alien that convert packages, why you cant have something like that that can automatically install rpm packages without using the console?

The chess game that comes with Ubuntu ask you to find some files in order to enable the 3D feature. Why Ubuntu not just get those dependency files when a program really need them to run properly? why not Ubuntu download automatically the dependency files when you want to use the help feature in Amarok, Kopete or any other KDE application?

scripts like easy Ubuntu are interesting for computer enthusiasts, but they don't make any sense for the average end user who is not interested in computer science. The operating system should let you download those programs with just a click from the web. And in the unlikely scenario that people brake their PCs doing that, Ubuntu should restart in a safe mode and keeping track of installed items in a list and recommend to unistall the pieces of software that are causing issues.  If I remember correctly Apple have something similar. i think is called time machine?

Other than those issues I don't think there is any other thing that could turn down a windows user to switch.

---

### Post by Roger Gundberg on 2007-05-26
I would have to concur with your opinions. The subject matter is productivity not convience. If I may digress, let's say we have an individual that is setting fires. I s it preferable to send the fire department out to fight these fires or apprehend the perpertrator? The phrase "Be at cause, rather than effect" may be apt. While I am in deepest appreciation and awe of the Ubuntu staff and their tireless efforts to create a product and I might add volunteerizm is exceptional. The issue of productivity and 'packages' are of some concern. When one recieves a package one expects a complete 'ready to use out of the box'. The present state suggests that that programmers in Linux (generic) would be comfortable with the terms 'kind of dead' or 'kind of pregnant'. You either are or you are not. Perhaps the privisio SAR (Some Assembly Required) should be considered.
Where is the spell checker?

---

### Post by Prisma on 2007-05-27
I forgot there is another minor issue that can turn down windows switchers, the main gnome music player rythmbox do not support MTP decives like Zen micro out of the box. Lets hope that with Ubuntu going mainstream with the Dell deal MTP devices will be supported out of the box. The good thing is that Amarok do support MTP so we can use it for the moment.

---

### Post by 3rdalbum on 2007-05-28
1. MTP support - assuming it's not patented technology (this is Microsoft), you are correct in saying that it should be supported OOTB. It's not a "Windows switcher showstopper" because most MP3 players are either Mass Storage or iPods.

2. Binary installers don't necessarily have to be run through the terminal. Some are terminal-based, so it's better to start a terminal and run the program through there - but it's not a pre-requisite for ones with GUIs. This isn't an Ubuntu problem, it's a 3rd party developer problem.

Also, for more on "Everyday Joe Won't Use The Terminal", see [http://bigbolshevik.blogs.friendster.com/a_man_and_his_penguin/2007/05/reason_2_it_has.html]("http://bigbolshevik.blogs.friendster.com/a_man_and_his_penguin/2007/05/reason_2_it_has.html")

3. The chess game was a bit of a balls-up; a silly little bug that somehow made it to release. It's not a Windows-Switcher-Showstopper - it's just a chess game.

4. Realplayer sucks; it doesn't contain the older codecs anymore, so legacy files will not play. MPlayer doesn't have any trouble with those. Besides, it's up to Helix/Real to make a GUI-based binary installer. Ubuntu can't do anything about it, as it's closed-source software.

5. I'm undecided about an inbuilt graphical Alien for installing RPM packages. On one hand, it would be useful. On the other, some RPMs can cause problems with Apt, and dependencies cannot be automatically resolved due to the differences in package names.

What is needed is an easy source installer that can link into Dpkg, RPM and all other package managers; where there is some way to list the required files and translate that into whatever packages are available on the particular distribution. I am very very slowly working on this.

6. Apple does not have what you describe.

7. Scripts like Easy Ubuntu and Automatix are designed for green users - I think you're getting confused with something else. Nothing necessary in Ubuntu has been designed for "computer scientists".

Downloading and installing programs from the web is all down to the program developers. If they're willing to license under the GPL, BSD license, MIT license, or any other open-source license, then Ubuntu can legally package it. If they don't, then their license should allow redistribution so it can be easily installed through Synaptic and 3rd party repos. If they don't allow redistribution, then it's up to THEM to provide a graphical binary installer.

8. Breaking your system means that it can't start up, so therefore it can't provide you with a list of things you broke. I hate to sound like an elitist, but it's difficult to break something unless you don't know what you're doing and you're fiddling with things you shouldn't fiddle with. If you open up the back of your TV and start soldering new connections, you wouldn't expect the manufacturer to give you instructions about how to replace the components.

---

### Post by ntetreau on 2007-05-29
I just wanted to add that MTP devices work pretty much out of the box in Feisty, using gnomad2 and Amarok.  Also, there is a plugin being developped for rhythmbox that works very, very well for me (you can search the forum for Rhythmbox MTP SVN) but it still needs to be compiled by hand.  

Nic

---

### Post by Prisma on 2007-05-31
> **3rdalbum said:**
> 

6. Apple does not have what you describe.




I suppose they don't...


[http://www.apple.com/macosx/leopard/timemachine.html]("http://www.apple.com/macosx/leopard/timemachine.html")

---

### Post by Prisma on 2007-05-31
> **ntetreau said:**
> I just wanted to add that MTP devices work pretty much out of the box in Feisty, using gnomad2 and Amarok.  Also, there is a plugin being developped for rhythmbox that works very, very well for me (you can search the forum for Rhythmbox MTP SVN) but it still needs to be compiled by hand.  

Nic


I agree but that "out of the box" is relative complex for the average user. It requires configuration and to dig inside Amarok. What in my humble opinion is needed is a feature in Linux (like a configuration wizard) that will auto detect your MTP device, offer you to link it to your preferred application (Amarok or Rythmbox) and automatically install it in your music player. Also, this program should be able to remember your MTP device so it will not fire up every time you connect it.

---

### Post by swoll1980 on 2007-06-02
my cpu did this automaticly

---

