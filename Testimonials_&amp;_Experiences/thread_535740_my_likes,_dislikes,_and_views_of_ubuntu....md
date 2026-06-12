---
title: "my likes, dislikes, and views of ubuntu..."
date: 2007-08-26
forum: Testimonials &amp; Experiences
---

### Post by spiroth10 on 2007-08-26
first off, I'd like to say I've been a linux user for a very long time. I started off learning about the system with mulinux, and eventually got a copy of redhat 7 on disk, I had dial-up at the time, and was only able to screw with floppy distros... funny story is, pogolinux offered free (full version) redhat disks at the time to any linux usergroup -- I lied and said I had one, a few months later I actually got a disk lol...

since then, I have setup networks, gotten several winmodems to work, actually dialed through to aol (while I still had dial-up), explored various programming languages, and pretty much made myself as much of a seasoned system admin (of my own network at home at least) as one could expect to become strictly by immersing them self in the OS.

My views on ubuntu are mixed -- It is a great OS, and is bringing tons of users to the linux community, and proving that you no longer have to be a masochistic geek to run the operating system anymore.

I love the way that things "just work" because they do. My Nvidia graphics card, my sound, hell, even a simple apt-get or synaptic install of Timidity++ gets you the full synthesizer setup (something that was an issue in slackware)

My mother has used it with no instruction from me, and if it supported tax programs, I'd wipe off windows completely (turbotax saves $$ and time lol) I really think ubuntu is the future of linux -- it's what so many linux distros in the past could've been, had it not been for hardcore linux nerds in their little heaven of complexity that they called their distro...

I firmly believe that while a lot of linux users want to spread linux, there were a lot of users in previous years who were nothing but elitests who said stuff like "U SUCK U Us3 WiNDoWZZzz", and trying to make sure it stayed as cryptic as possible -- I know I was there, now you have distros like this, welcoming new people and embracing new ideas to the scene. 

now for what I don't like...

but a lot of traditional linux/unix ideas have been abandoned by ubuntu. The first thing I will bring up is the lack of software development tools that come off the CD. No matter how easy you try to make it, there will always be stuff you can't provide via binary.

also, what if the computer in question can't connect to the internet? Why can't I just burn tarred sources to a CD or DVD to get the software I want? An uncommon, but very possible scenario for this day and age. Compiling software is still something I use a lot in ubuntu -- there are packages I just can't find in your repository I want.
Its an essential part of the open source movement, and I feel at least a c/c++ compiler and make are in order to put on a disk, you could certainly fit them on the cd...

Also, the whole sudo thing -- I understand the point of it was to keep people from messing up their filesystems, but what if I want a separate, traditional root account and I know what I'm doing? Typing in sudo and a password a thousand times can get annoying as hell, no matter how used to it you are...

hell, back before when I had dial-up, since there was no hacker threat, I simply used the root account all the time. so long as I didnt do anything dumb, there was no problem. It was convenient because I never stop tweaking my system (a habit from slackware 9 and 10...)

The main problem I see in ubuntu, is that even after you sudo apt-get install build-essential, you still miss out on a lot of libraries, and when you go to compile a program, you have to go seek out the package. 

I think there should be a script that simply downloads all the most typical libraries and development utilities needed in ubuntu...

The last problem I will comment on is the shell -- I find the standard shell lacks in functionality compared to other distros. I realise that ubuntu is supposed to be a graphical OS, but what if you severely screw something up with the graphics settings and cant login after that? You gotta do a full reinstall instead of just ctrl-F2 and open a new terminal, login killall x, and fix the problem.

what if you have an old machine without supported graphics? sure, you still have a limitedly functional terminal, but compared to the shells in other distros, its not the best IMHO...

again, the shell is an essential part of unix, there should be more function enabled in the default one in case of emergencies.

other than that, I really like it. I think its reaching out to new users in a way linux never has before. With Vista trying to force business to upgrade their hardware, ubuntu gives a good push in for linux -- showing that it CAN be easy to everyone, something linux has overlooked for a long time.

If I have anything to say, its that distros like Gentoo and Slackware are nice if you have special needs, but I think usability is far more important for a mainstream OS. Distros that are immensely complicated, I think, will begin die out, and only remain for a few die hard enthusiasts while more distros like ubuntu arise. Hell, I switched from slackware to ubuntu, and I think other people will too in time.

---

### Post by freebeer on 2007-08-26
You can enable a root account in Ubuntu...

---

### Post by steveneddy on 2007-08-26
Well, how 'bout that.

---

### Post by starcannon on 2007-08-26
You can also type "sudo bash" in terminal and keep root open that way, I use that if I've got alot to do in a terminal as root, gets rid of the need to sudo all the time.

About the only package that I've run into thats needed and not "just there" is build-essentials.

sudo apt-get install build-essential 

should do the trick, I am a very typical user though, so I haven't had any real issues with lost packages.

---

### Post by DarkOx on 2007-08-26
Build-essentials is on the CD, just not installed. If you add the CD to synaptic, it can be installed even without internet -- except of course, there's no real way to know that.

Typing "sudo -i" at the terminal will get you root access in the same way as "su" on other systems. Once again, the problem is more that there's no way to know that offhand than that Ubuntu's lacking the feature.

---

### Post by mostwanted on 2007-08-27
Just for the record: the package is called *build-essential* (no s in it!).

The reason build-essential and the root account are not installed per default is because both are security risks (malicious code can be compiled using gcc, danger of the user using root as the default account).

As has been said before, it is not impossible or hard to create the root account and compiler tools are included, just not installed for regular users. Power users can still use both, it's just joe regulars that are shielded from them.

---

