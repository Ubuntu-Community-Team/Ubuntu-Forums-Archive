---
title: "I want to contribute to linux"
date: 2008-09-05
forum: Ubuntu Dev Link Forum
---

### Post by revanb on 2008-09-05
I want to contribute to linux by doing development through programming. I have the necessary programming skills, but not the detail about the linux development scene. I have been using linux for a while and I am not new to linux, just to linux development.

I need a few questions answered, but for now this one will do:
1) I should probably try to fix a bug or two in existing projects to get the hang of the environment. Where can I get involved and chat with someone about this?



Anyway, I really like using linux. I have the following problem with linux though:
- There are so many people contributing to linux, but why is there so many different distros? My opinion is that the efforts are not working together to make linux better. Every distro seems working seperately trying to sort out the same problems...Isn't this why there still to this day does not seem to be real quality in graphics and sound support? Yes, its much better, but on my 4 year old notebook the x desktop makes the system freeze too often.

Choice is good, but to much choice means a lot of effort is scattered in a lot of half done projects. I think possible the reason is that if some developers dont like something they head off in their own direction trying to go it alone?

Anyway, I want to contribute and taking my own advice I would like to help important existing projects become better by fixing bugs at first and maybe additional development later.


If there is anyone with insight and experience in these matters please correct me if I'm wrong, but with the number of small yet signaficant problems that exist in (all distros of) linux you will do well to convince me that I am wrong!

---

### Post by tamoneya on 2008-09-05
Well the most common thing people do is bug testing.  Download alpha 5 which came out today. 

The other suggestion that I have for you since you seem to want to do more than just report the bugs is that you could get involved in MOTU.

[https://wiki.ubuntu.com/MOTU](https://wiki.ubuntu.com/MOTU)

MOTU manages all the packages and maintainers will manage certain packages.  It would then make sense to manage a package and work on solving bug reports related to that package.

---

### Post by jacksaff on 2008-09-05
Though there are many distros they all use most of the same software. As the software is all gpl'd or similarly licensed anyone can package up whatever stuff they like and release their own distro.

You need to think about what exactly you want to do and where in the development chain you want to be working.

For example, if you want to hack on the 'guts' of the system then look into kernel development (actual linux) or some low level system like the x-server. Work you do here will end up in EVERY distro that uses these systems. Most projects at this level seem to be written in C.

If there is a program you want to work with, go find their website and find out how to get involved. This work too will automatically flow to every distro as updates are pushed downstream. You could also get involved in very large projects here like gnome and kde. There is unix software in pretty much every language ever written so you should be able to find something that matches both your skills and interests.

If you are hooked on ubuntu then you can work on smoothing it out - testing, bug-fixing and the like. This is pretty much the only work that is distro specific, and even then if bugs are in upstream work they will get pushed up so the whole linux community benefits (and of course ubuntu gets the benefits of the work of other communities such as fedora and opensuse).

A few bits of software are developed by and specifically for ubuntu. Because of the licensing these too are free to be picked up and used by other distros if they also want to add that functionality. 

Overall there is some inefficiency and a little duplication of effort but much, much less than it appears at first. This is offset by the huge creative advantages the ecosystem offers. Noone is tied-in to doing things the 'right' way and there are no barriers to new ideas except for the need to code them and get them working.

---

### Post by revanb on 2008-09-10
Thank you very much for your replies.

This helps clear things up.

I think I'll try to contribute to the x-server in some way as I regard it as extremely important to linux. Think about it...The x-server influences a new users linux experience in a big way. 

The other possibility, though related, is graphics driver development. If 3D graphics are not up to scracth 3D games will not work properly and as I see it the lack of games being made available to linux is keeping many otherwise willing users away. Those same issues, users and 3D support, is probably what is keeping game companies from making native linux versions available. So in my opinion when the linux x-server and graphics support surpasses a certain threshold there is bound to be an explosion of new users and available software for existing users.

---

