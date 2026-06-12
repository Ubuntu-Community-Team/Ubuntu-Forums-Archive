---
title: "My experience with Ubuntu"
date: 2008-05-22
forum: Testimonials &amp; Experiences
---

### Post by jesrani on 2008-05-22
I have an office network having 98/XP computers. My laptop is XP Home. Some months back, I decided to try Linux Ubuntu, having read all good things about it. I am not a Microsoft fan at all, they overcharge for the product and one requires all kinds of security. But the software (98 or XP) is easy to use no doubt.

I installed 7.10 on an old computer. I am not really a techie and it took me a number of days to understand Ubuntu and put it to correct use. I use it to backup all the 98/XP network shares. Without the use of this forum and extensive searching on the net I just could not have done this. But it takes a lot of time.

Recently we replaced some old Win98 computers with new ones having XP, no choice but to spend some good money. I configured Admin and user accounts, installed all the software and put security rights. It's not difficult. I did have to search the net now and then but not too much.

Now I upgraded my Linux box to 8.04, I can't do a fresh install without losing my programs and settings. But again I am having to spend lot of time to configure things like resolution, network and now samba is not working for 98 shares. Yes, I am getting help from the forum and without this forum I cannot even imagine using Ubuntu. I dont understand all the commands but sometimes just do as suggested and it works.

Don't get me wrong, Ubuntu is very good. In fact, I am thinking of setting up a PCLinuxOS as internet browsing station, just to get the feel of it. But for average users, I just don't think they can handle Ubuntu. We have about 10 people using Windows here and I can;t see any of them handle Linux. Maybe we are not very able people, but then this is where Windows is easier.

No, I will **NOT give up on Ubuntu**. I will keep trying to use it. I really like the fact that once setup, it is not difficult to maintain. But it is difficult to remember how it has been set up. So many commands and so many installs and configurations. But it is safe, fast and reliable, no doubt. I hope one day, it will have more GUI and lesser tweakings required for the average user.

I just want to give an example of how set minds work, I may be wrong. When I used Openoffice 1.1, it was difficult. Being used to MS office, the commands were different and it was awakard. But I persisted and stopped using MS Office. However I could not pass this to my colleagues as it was beyond them. But recently, I have installed Openoffice 2.4 on all computers and everyone is using it. The interface is more or less like MS office and everyones comfortable, no need for MS office anymore.

I hope the post wasn;t too big. These are just my thoughts which I wanted to post.

---

### Post by dmizer on 2008-05-22
actually, i had some serious issues with file sharing between windows and ubuntu myself a while back.  the samba server howto (linked in my sig) was instrumental in saving my sanity, and the cifs howto is the result of about two months of painstaking research and trial and error.

but, i also clearly remember (because it was not so long ago) the very first time i ever set up my own file sharing network between windows computers, and the experience was _no_ less painfull.

you're also talking about sharing files with a platform that is officially unsupported even by microsoft.  it's a wonder they're functional at all.

what's more, you're trying to share files to windows from linux with samba.  since samba is not native to linux, it can't be expected to work as well with linux as it does with windows.  you'll run into flaky windows <-> OSX filesharing for the same reason.

finally, you're talking about:
> I configured Admin and user accounts, installed all the software and put security rights. It's not difficult. I did have to search the net now and then but not too much.
and
> I installed 7.10 on an old computer. I am not really a techie and it took me a number of days to understand Ubuntu and put it to correct use. I use it to backup all the 98/XP network shares.
which are items i would put well beyond the reach of your "average user" in windows or otherwise.  these are administrative tasks, not "user" tasks.  and they are made easier simply by the fact that you're familiar with windows.  if you grew up with linux instead of windows, the opposite would be true. and i think it says a lot about the "average" usability of ubuntu that you were even able to install and configure ubuntu (something most "average" users would never dream of doing even in windows)

seriously, i sympathize with your frustration, as i have indeed been through the same painful transition.  but if you keep an open mind, and try to stay away from invoking that "average user" stereotype, you'll have a lot better experience with linux.

---

### Post by jesrani on 2008-05-22
> **dmizer said:**
> seriously, i sympathize with your frustration, as i have indeed been through the same painful transition.  but if you keep an open mind, and try to stay away from invoking that "average user" stereotype, you'll have a lot better experience with linux.

As I said, I am not giving up and will keep trying. But as I also said, Linux is not for average users, I feel.

---

### Post by dmizer on 2008-05-22
actually, i still beg to differ.  once ubuntu is set up (just as windows is set up when your "average user" gets ahold of it), anyone can use it very easily.

the huge difference here is that you do not get ubuntu pre-configured for your computer.  you have to start from scratch (which average users never have to do with windows).  if an average user finds themselves in a position where they must reinstall windows from scratch (as is the case with ubuntu), they will take it in to a shop, not do it themselves.

again, i think the subjects you touch on as being difficult in ubuntu are not "average user" tasks to begin with.

---

### Post by jesrani on 2008-05-22
> **dmizer said:**
> actually, i had some serious issues with file sharing between windows and ubuntu myself a while back.  the samba server howto (linked in my sig) was instrumental in saving my sanity, and the cifs howto is the result of about two months of painstaking research and trial and error.

I tried this for accessing a password protected share on Windows 98 but I got error 2 = no such file or directory. Tried smbfs option and got error 112 = host is down

---

### Post by dmizer on 2008-05-22
if you had posted in the howto that you were having this trouble, i would have been happy to help you, just as i've been happy to help everyone else who has posted :)

also, i tracked down a very good post reagarding the "average user" by aysiu that you may enjoy reading: [http://ubuntuforums.org/showthread.php?t=212847](http://ubuntuforums.org/showthread.php?t=212847)

and, a blog post:
[http://ubuntukids.org/blog/?p=12](http://ubuntukids.org/blog/?p=12)

edit:
actually, after a bit of investigation it seems that windows 98 cannot handle cifs, so you'll need to use smbfs.

---

### Post by jesrani on 2008-05-22
> **dmizer said:**
> if you had posted in the howto that you were having this trouble, i would have been happy to help you, just as i've been happy to help everyone else who has posted :)


Thanks for the links, I will check them out. I have posted my problem here :
[http://ubuntuforums.org/showthread.php?t=803025](http://ubuntuforums.org/showthread.php?t=803025)
I would really appreciate your help on this one.

---

### Post by hyper_ch on 2008-05-22
I'd just like to ask: What average user can handle a total new install of windows (and hunting down according drivers)?

---

### Post by SunnyRabbiera on 2008-05-22
> **hyper_ch said:**
> I'd just like to ask: What average user can handle a total new install of windows (and hunting down according drivers)?

Right, windows is honestly no better off in a fresh install.

---

### Post by jesrani on 2008-05-22
> **hyper_ch said:**
> I'd just like to ask: What average user can handle a total new install of windows (and hunting down according drivers)?

That's quite right actually. I manage the machines on my network and other users can't really do anything other than use windows. I mean they are not able to, they neither have the knowledge nor the interest.
But I, as a "Network administrator", am no expert either. Windows has a GUI for almost everything and that makes things easier, if not better. Linux may definitely be better but it needs to be easier. Again, this is just my opinion which may not be held by everyone. It's all about how much the subject interests you and how much time one is willing to spend, and above all that if one has the capability and common sense (which in any case is very uncommon)

---

### Post by NightwishFan on 2008-05-22
Windows gui is worse than kde gui. Everything is hidden and not obvious. Any fresh user on Windows would be exactly as confused or more. Anyone that uses Ubuntu that I have seen gets to desktop and clicks firefox, and off they go. They want to message they click pidgin. They want to change the desktop, they see System -> Preferences -> Appearance. To do similar in Windows you have to right click, go to properties, click in the themes, set to Windows Classic, and go to customize, and then guess what all those options mean. (As far as I remember, its been a LONG time)

Many find kde control center even more simple as it says "Appearance" or "Network". It will not lie to you. People know Windows because it is what is common, sadly.

---

### Post by jesrani on 2008-05-22
> **NightwishFan said:**
> People know Windows because it is what is common, sadly.

Very true.

---

### Post by Fenris_rising on 2008-05-22
my tuppence on this. 8.04 is very stable for me and yes ive trawled the forums to find answers to problems i had initially with setup and then answers to things i wanted to do (setup a network between PC, Laptop, Xbox1)
and anything else i want to do as i find i need it. my other weapon is copy and paste! i have several tutorials made up from this site copied and pasted into an office document. they are all specific to things i had to do to tweak and fix bits and bobs to get my OS running exactly as i need it. they are saved in several places on and off the PC. trust me its a winner and with this ready to hand info you should have little trouble sorting things out and not have to struggle to remember what you did to fix/tweak the last time.

---

### Post by jesrani on 2008-05-22
> **Fenris_rising said:**
> my other weapon is copy and paste! i have several tutorials made up from this site copied and pasted into an office document. they are all specific to things i had to do to tweak and fix bits and bobs to get my OS running exactly as i need it. they are saved in several places on and off the PC. trust me its a winner and with this ready to hand info you should have little trouble sorting things out and not have to struggle to remember what you did to fix/tweak the last time.

This is really important. I have thinking about something like this for some time but when things go ok, I tend to ignore it and then forget. I will take this hint and start so that I don't have trouble in future.

---

### Post by VeryGoodYear on 2008-05-22
I've been using Ubuntu for about 3-4 months now. I began like most people as a Vista user, and dual booted it with 7.10. I found it fantastic to have a new OS, it did everything I wanted it to do, (the web, email, word processing) and it is very pretty to look at with Compiz installed.

However, I'm a pretty savvy user, not so much knowledge of Linux, but more Google! I ran into some problems, nothing that couldn't be fixed with some looking 'round. I found the experience of something going wrong and having to fix it very useful, because with every problem, I learn something new. Such as what 'sudo' does in the Terminal or how to install programs with apt-get.

So now as I have removed Vista, running only Hardy Heron, my girlfriend has started to use my laptop. She was a bit unsure at first, 'where's the start menu!?'. But as she got used to it, she was very easily installing games, (Penguin Racer lol!) from Add/Remove and changing themes. Not advanced, but the sort of thing 'normal' users want to do. So the point of all this? That Linux, and Ubuntu do work for the normal user, but I do understand the poster's comments about it being a little hard to start off with. Now this is not anybody's fault, the amount of hardware out there, and having to ensure the OS is compatible with all that hardware is no easy task. But like any computer system, it's never going to be perfect.

I do think that we can all agree on one thing though - it can only get better from here! :)

---

### Post by jesrani on 2008-05-23
Since the last 2 days I have been struggling to get Mr.Hardy to access protected windows shares ([http://ubuntuforums.org/showthread.php?t=803025](http://ubuntuforums.org/showthread.php?t=803025)).
It's completely frustrating and I don;t know what to do now. Will keep on trying.

---

