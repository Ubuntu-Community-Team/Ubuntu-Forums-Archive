---
title: "Advise on migrating Windows 2000 Server to Linux Server"
date: 2010-05-04
forum: Server Platforms
---

### Post by Jester2109 on 2010-05-04
Good Morning All,

I am looking for some advise on what the benefits would be if I were to migrate my home Windows 2000 server to an Ubuntu (or other Linux flavour) Server.

**Background:**
I am actually an IT Professional, but one who has always worked with Microsoft products. Through the years, I have 'toyed' with Linux/Unix (both professionally and at home), but never really looked at it seriously. Now I want to learn the Linux/Unix world to help expand my IT knowledge.

To that end, I am currently playing with Linux on my home environment. I have been using Ubuntu Desktop on an old Dell PC happily for the last few weeks, now I am considering going the next step and installing a Linux Server.

At home (being a bit of a geek), I currently have a Windows 2000 Server installed with a shared network printer hanging off it and several shares.

The only reason for having a Windows Server has always been to be able to share my printer easily with everyone in the household (it is not a printer with an inbuilt network card) and also to share the mp3's I have with other members of the household (i.e. my kids) that enables them to easily put music on their iPods. The kids also use the shares for sharing and exchanging various things between each other (such as homework and art - all of them like to draw art onto their PC's through use of Graphic Tablets).

In total, there are currently 13 PC's (including 4 laptops) on my home network. The majority of the PC's and laptops are running either Windows XP, Windows Vista or Windows 7. Obviously, I also have the Windows 2000 server, an Ubuntu Desktop (as described above) and an AppleMac.

I am seriously considering migrating the Windows 2000 Server to a Linux server (maybe Ubuntu Server if it is a viable option). The Windows Server (running on an ageing AMD 2800 processor with just 1Gb of RAM) is configured with just a small internal hard disk drive handling the O/S and configuration, but also has an external 1Tb hard disk drive upon which all the shares are currently held. The external hard disk drive is configured as an NTFS volume.

I do also run some games servers on this Windows Server for my son and his friends to play games such as Quake, Unreal Tournament etc etc against each other in the household, though this is only ever enabled as a local network and is never exposed to the internet.



**My Question:**
Now, my question is how easy it would be to migrate this Windows 2000 Server to a Linux server, what benefits I would see from doing so, what the pitfalls to watch out for, what are best flavours of Linux to use for this, is it worth the pain, and finally, are there any guides that would help me do this.

Bear in mind that I do have an extensive technical background on Microsoft and Novell products (have installed these for many years), so am not a novice in technical terms, but that I have little experience with actually setting up and configuring Linux/Unix servers.

So I would appreciate any Linux guru's out there who might be prepared to impart a little advice on whether what I am considering doing above is worth the exercise, based on their own experiences of doing such a thing.

Thanks

---

### Post by HermanAB on 2010-05-04
Howdy,

For someone coming freshly from the Windows world, a Mandriva Linux Small Business Server is best, since it has wizards for everything, same as Windows.  For someone familiar with Linux, it doesn't matter what distribution you use, since experienced users don't care about the wizards.

A Linux server can do anything you want, but it won't run Windows games properly.

---

### Post by jbrown96 on 2010-05-04
Basically, your setup is going to involve Samba and that's it. There's really very little that you will learn from setting that up. It doesn't make any difference what version of Linux you use: Ubuntu ```
sudo apt-get install samba
```, Fedora ```
sudo yum install samba
```, etc. From a home server perspective, there's nothing really to gain. If you just want to replace Win 2000 with Linux, then it's a lot of mental masturbation, with no gain. 
On the other hand, if you want to learn something about Linux, then you are going to need to do something beyond just replacing your Win 2000 setup. If you are looking for professional development, then you need to go with a Red Hat distro either Fedora or RHEL. Red Hat 6 beta came out a few weeks ago. It's free and what you would use professionally. Ubuntu is easy to set up, but it's peanuts. You could replace your Win 2000 setup in 45 minutes total, but won't learn more than how to read a 2 page howto guide. 
Learning Linux is not quick, especially if you take a casual path on it. There's nothing wrong with that. I've used Ubuntu for 4 years, and I've learned a ton. Just don't expect to learn it really quickly. There's a lot of hand-holding, which makes it easy and encouring to get started, but you won't progress that quickly. 
It all depends on where you want to go. If you just want to give Linux a try to replace your current setup, then Ubuntu is your easiest path. If you want professional development, then Ubuntu is not a bad path, but I think it's a slower road, especially since most business is Red Hat-based (either RHEL or other rpm-based distro).

---

### Post by spynappels on 2010-05-04
The file and Print sharing can be achieved quite easily using Samba, do you have another older machine you could set up a small test system on?

I'd also recommend looking at 2 books by Sander van Vugt on Apress, Beginning Ubuntu LTS Administration and Pro Ubuntu Server Administration. I found them very helpful when I was starting out.

The biggest difference you will find is using the CLI rather than a GUI as in Windows, but with a little practise, you will understand what is happening a lot better and it will become clear to you.

---

### Post by Jester2109 on 2010-05-04
Interesting answers so far, and thankyou for them.

I suppose this should be considered my first ambling steps into the Linux/Unix world. I do have some knowledge of Unix as I have installed several products onto such an environment in the past (Sun IdM, Novell Access manager, Novell Identity Manager, Tivoli Access Manager, Tivoli Identity Manager etc etc).

It's just that I don't feel I know enough about the Linux World and feel that by installing different flavours of Linux in my home environment is the easiest way to go (as I rarely get the time to sit down and have the time to learn such things at work).

At this point, my main aim is to start getting into the Linux technical environment. I am not duly concerned with how long it takes me to learn it all, as I tend to be a quick learner anyway.

Initially, my thoughts are to go with the simpler (easier to use) Linux products and develop my knowledge from there. Gradually moving on to the more technically demanding tasks and knowledge. For the most part, in my professional world I would usually have a Unix expert to work with anyway. I just feel it is a worthwhile exercise to learn more about the product myself at home, in an envirnment where I can afford to make mistakes.

However, migrating the Windows Server to a Linux Server is undoubtedly ambitious a project even for myself to have a go at. Especially since I would not like to lose the data stored on the shares (so I will be ensuring a good back up of that data first).

One of the issues I can think of first hand would be that of migrating the NTFS external drive into Linux as I am unsure that Linux would support NTFS directly in such a way so would expect to have to change the external drive format.

BTW, as regards the machine acting a games server, most such server code will quite happily run on a Linux server as they do little more than command prompts. There is not really any graphics required on the server itself, the connected PC's are the ones that need the Graphics abilities as they are the ones actually running the software for real. The games server merely acts as the 'go-between'. I happen to know that many of the games I mentioned above (Quake, Unreal Tournament, Far Cry) are freely available as actual Linux downloads. The only thing that needs a license are the PC's actually running the game ... and they are always Windows desktops !!

Thanks for the great advice so far  :)

---

### Post by Jester2109 on 2010-05-04
> **spynappels said:**
> The file and Print sharing can be achieved quite easily using Samba, do you have another older machine you could set up a small test system on?

I'd also recommend looking at 2 books by Sander van Vugt on Apress, Beginning Ubuntu LTS Administration and Pro Ubuntu Server Administration. I found them very helpful when I was starting out.

The biggest difference you will find is using the CLI rather than a GUI as in Windows, but with a little practise, you will understand what is happening a lot better and it will become clear to you.

I don't have a new PC to play with at the moment (other than the old Dell that currently have Ubuntu Desktop installed on and which I am using to write this very message).

However, what I do have is a lot of spare IDE drives of varying sizes that I can swap in and out of the Windows 2000 Server box so that I can experiment without putting my current Windows Server configuration at risk. What I don't currently have is a spare external 1Gb hard drive with which to back up my current external hard drive (with all the shares on). But as external hard drives of that size and above are so cheap these days then that won't be an issue.

---

### Post by jbrown96 on 2010-05-04
> **Jester2109 said:**
> Interesting answers so far, and thankyou for them.

I suppose this should be considered my first ambling steps into the Linux/Unix world. I do have some knowledge of Unix as I have installed several products onto such an environment in the past (Sun IdM, Novell Access manager, Novell Identity Manager, Tivoli Access Manager, Tivoli Identity Manager etc etc).

It's just that I don't feel I know enough about the Linux World and feel that by installing different flavours of Linux in my home environment is the easiest way to go (as I rarely get the time to sit down and have the time to learn such things at work).

At this point, my main aim is to start getting into the Linux technical environment. I am not duly concerned with how long it takes me to learn it all, as I tend to be a quick learner anyway.

Initially, my thoughts are to go with the simpler (easier to use) Linux products and develop my knowledge from there. Gradually moving on to the more technically demanding tasks and knowledge. For the most part, in my professional world I would usually have a Unix expert to work with anyway. I just feel it is a worthwhile exercise to learn more about the product myself at home, in an envirnment where I can afford to make mistakes.

However, migrating the Windows Server to a Linux Server is undoubtedly ambitious a project even for myself to have a go at. Especially since I would not like to lose the data stored on the shares (so I will be ensuring a good back up of that data first).

One of the issues I can think of first hand would be that of migrating the NTFS external drive into Linux as I am unsure that Linux would support NTFS directly in such a way so would expect to have to change the external drive format.

BTW, as regards the machine acting a games server, most such server code will quite happily run on a Linux server as they do little more than command prompts. There is not really any graphics required on the server itself, the connected PC's are the ones that need the Graphics abilities as they are the ones actually running the software for real. The games server merely acts as the 'go-between'. I happen to know that many of the games I mentioned above (Quake, Unreal Tournament, Far Cry) are freely available as actual Linux downloads. The only thing that needs a license are the PC's actually running the game ... and they are always Windows desktops !!

Thanks for the great advice so far  :)

If you want to get into Linux administration, then I don't think sticking with NTFS is a good decision. Part of Linux is the unique file systems, and you should really learn to use them. NTFS is no problem for compatibility, but you won't learn much. It's certainly understandable if you don't have enough disk space to migrate your data, but I think that setting up a software raid and lvm setup is a great intro into learning linux. Partitioning is one of the fundamental parts of a Linux setup and skipping that undermines Linux knowledge. 
If you have any interest in getting into Linux professionally, then I would highly encourage the RHEL 6 beta. It's top-notch and has surprisingly current software for a RHEL release. Not to bad-mouth Ubuntu because it's great as well. I just think that RHEL distros will teach you more.

---

### Post by v1ad on 2010-05-04
i would do it just for the learning experience, it all will work, and one fun thing is that you can always ssh, scp or sshfs files back and forth anytime. i use linux to host my files. its not as easy but once you learn your set.

---

### Post by Jester2109 on 2010-05-04
Guys,

This is brilliant information and advice. Thanks very much for the speedy replies.

Just for the record, I am NOT looking to become a professional Unix/Linux administrator. I'm an IT Security Architect by trade with 10 years experience behind me, and quite happy with that role professionally. It's just that having been a Tecchie for around 20 years before that, I have a natural curiosity in how things work - the nuts and bolts so to speak.

I have a natural 'geeky' side in me in knowing how things work (e.g. I built a Hackintosh on a Toshiba laptop last year just to prove that I could do it and to see how it is done) and doing stuff like that for fun in my spare time.

At home, I can often be found building different PC's and servers and messing about with the latest security and technical products. Linux/Unix is just one of those things that I want to know more about and feel it would help me in my current role as a Security Architect to understand the Unix/Linux world better.

Cheers

---

### Post by itisachilles on 2010-05-04
personally i think that that dell laptop you mentioned earlier is the perfect starting point get into it and have some fun the "nuts and bolts" will come like osmosis i currently am running a three moniter alienware PC that runs ubuntu like they were made for each other altough my start was ruff i tried to earn some money on mechanical turks and got hit with some many Trojans and god only knows what else that a could barley start her up with out a crash (vista ... nuff said) but once you learn what you want and what your system can be compatible with then you'll know exactly witch distro to switch to

---

### Post by Jester2109 on 2010-05-04
> **itisachilles said:**
> personally i think that that dell laptop you mentioned earlier is the perfect starting point get into it and have some fun the "nuts and bolts" will come like osmosis i currently am running a three moniter alienware PC that runs ubuntu like they were made for each other altough my start was ruff i tried to earn some money on mechanical turks and got hit with some many Trojans and god only knows what else that a could barley start her up with out a crash (vista ... nuff said) but once you learn what you want and what your system can be compatible with then you'll know exactly witch distro to switch to


Actually I was referring to a Dell Desktop, but now you mention it I do also have a Dell Laptop and a Toshiba laptop that I could use for the very purpose in learning a bit more about setting up a Linux server using several of the different distros mentioned and see how easy it is to go.

Good suggestion. 

Thanks

---

### Post by Jester2109 on 2010-05-04
Thought I would start with Ubuntu Server to get familiar with what needs to be done, then move on to other distros and see which I like best (as well as getting more familiar).

It's installing on the Dell Laptop as I type !!

---

### Post by itisachilles on 2010-05-05
thats great i love to hear people moving to mostly linux after years of microsoft computing and love it even more when they turn out really happy with the switch. .

---

### Post by drdos2006 on 2010-05-05
I found this very useful.

Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab.

Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood

This how-to assumes your looking to setup a Linux server, not a Linux Desktop. For use without a keyboard, mouse, or GUI interface. After
setup completes you will be remotely managing it, and will not have a need for the monitor and keyboard once you finish the initial setup.
This how-to also assumes you are connected to the internet, and have at least (2) computers on the same network. It also assumes you will
have at least (2) hard-drives in the server, one for the O.S. and one for the data.

regards

---

### Post by itisachilles on 2010-05-05
> **drdos2006 said:**
> I found this very useful.

Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab.

Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood

This how-to assumes your looking to setup a Linux server, not a Linux Desktop. For use without a keyboard, mouse, or GUI interface. After
setup completes you will be remotely managing it, and will not have a need for the monitor and keyboard once you finish the initial setup.
This how-to also assumes you are connected to the internet, and have at least (2) computers on the same network. It also assumes you will
have at least (2) hard-drives in the server, one for the O.S. and one for the data.

regards
hes trying to convert a server not set one up and he all ready said he was connected to the internet and had multiple drives. next time actually read the thread before posting

---

### Post by kevinthecomputerguy on 2010-05-10
The article Dr. DOS suggested would be a great read for this users post.

---

