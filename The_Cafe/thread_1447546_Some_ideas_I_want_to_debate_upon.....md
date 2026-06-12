---
title: "Some ideas I want to debate upon...."
date: 2010-04-05
forum: The Cafe
---

### Post by rahilm on 2010-04-05
hii..
Ubuntu lucid is the first beta i am testing. since my hard drive is out of space, i installed it on one of my external usb hard drive. So far, it has been impressive.
Since now people are really serious about changing ubuntu rather than defend what it already has and glorifying its features, I thought I would bring up some ideas to some problems that i have faced. I don't know if many of you have faced these problems,  neither do i know if any of these ideas are feasible. But i thought about mentioning some of them here since people are more polite in these parts of the forums. There are also problems which i have no solution.

1)The dependancy issue..
I debated with myself for a long time on this. I have been a windows user for a long time till i switched to ubuntu completely. There is one feature of windows which i find really useful. Double-click install. Talk about installing vlc on both windows and in ubuntu. There is an executable you download and then install it directly. In ubuntu you fire up USC and install with a single click which sounds great. There are actually more than a dozen files which are downloaded into a mysterious "/var/cache/apt/archives" directory.
What do you do if a computer does not have internet access. Or let's say, It doesn't have the drivers required to access the internet. What to do? In windows no problem, but in ubuntu it is. You even need the corresponding repositories to be activated if you want to install through '.deb's. Else there is brute force install.

I am not saying it is that bad. But how about making the gdebi scan the current directory to see if there are any dependencies that it requires. It makes installing a bit easier.

2) How about installing while downloading...
While beta testing, one thing i noticed is that there are almost 200mb updates every day. It takes over 1+1/2 hrs to download them so I don't do that everyday. But i used to use synaptic. A good thing about USC is that it installs different programs as different tasks. I realised it just now which makes this point a little outdated.

3) Too many kernels....
Although I do know how to remove them, the average user doesn't. How about making only two kernels to remain at the same time. While installing, the installer could check if there are more than two kernels installed and then remove the needful until only two remain. Even if that sounds crazy, how about asking to remove them for you. Loads of entries on bootup don't look nice.

[Computer Janitor is crazy... and unintelligent]

4) Running apt-get autoremove automatically after something is removed. Rather than expecting the user to fire up the computer janitor (which he won't.. it is very confusing) or opening the terminal and running it (he may even not know such command exists), how about doing it automatically. like after something is un-installed, a pop up asking permission to remove certain packages that are useless.

5) A problem that has been bugging me since i installed the beta on my externel drive is that whenever i update grub (as in.. the program) , the idiot installs grub to the mbr of the internal hard disk, which leads to an "error device not found" when i start my computer without the hard disk plugged in. I am considering replacing grub with burg.. but i wonder what will happen when I install a new kernel.

6)OK now this point is actually worthless.. its only a rant. about the new indicator icons. Some really wise men decided that they shall integrate the 'envelope', the 'volume' and 'rhythmbox' and ubuntu would look more efficient.... it doesn't.

7)This is actually more of a question i have been having. What's with the "Lock Screen".. what is the logic anyway. I read... It is there to prevent somebody else from using your session. and it really succeeds in it. But doesn't sleep mode work that way too? As i mentioned above that it takes 1.5 hrs to download an update. Since i have nothing to do, I take a stroll outside. Before that,  i lock my screen so that my younger brother doesn't mess around with the updates. But he figured out a way to do that. Click Switch User. Click the power icon on bottom right. Click Shutdown, and boom.. the computer shuts down without a warning that other users are logged in.

SO much so far... will be back with more.

---

### Post by cariboo on 2010-04-05
Except for #7 this isn't a support question. Moved to the Cafe.

---

### Post by doas777 on 2010-04-05
1) yeah, depends can be a pain. I like your solution, but at the same time, i've never really had the issue you describe either. I had serious problems of that type in SUSE (curse you yast!), but the repos in ubuntu have done me fine for everything except compiling PCsx2 on 64bit. 

2) I'm kinda meh on that one. then apt has to do a lot of coorelation between dependencies to make sure that all are present at the time any given package is installed, including the ones that are being installed right this second. sounds like a recipe for database corruption.

3) I used to use startup-manager to limit the number of bootable kernels to 2, but I'm told that it does not work fully with grub2 yet. for now I'm just uninstalling the oldest. would be nice to get some config on that.

4)sounds like a great idea.

5)I've had a simillar issue with grub1. my fstab was in uuid format, but grub uses that hd(0,1) format, that fixates on the bus position to find the mbr disk. most annoying. haven't found a good fix. presumably making the external appear to be the last disk on the bus rather than the first, would remove any likelyhood of it recurring, but i don't know what other effects it would have.

6) ...there is no rule 6...

7) if you take away your brothers admin rights he shouldn't be able to shut down. 
most systems that supply a "switch users" feature suffer from the same issue. that is much of why MS choose to have most of the installation of updates happen after the logout event. that way all users had no choice butto see the "please do not turn off your PC until updating completes" thing.

---

### Post by J_Stanton on 2010-04-05
you should take your ideas to ubuntu brainstorm. talking about those things here is just a waste of time.

---

### Post by rahilm on 2010-04-05
> **doas777 said:**
> 
2) I'm kinda meh on that one. then apt has to do a lot of coorelation between dependencies to make sure that all are present at the time any given package is installed, including the ones that are being installed right this second. sounds like a recipe for database corruption.

What i meant was, to start installing a particular program when all of its dependencies have finished downloading. From waht i understand, synaptic first scans the database, finds out the files required to download, then downloads them, and then installs them. The idea is based on the apparent fact that synaptic is mostly idle when downloading packages. Consider a situation that you have to install two programs A and B. An intelligent synaptic would download all dependencies of A and then B which ever is smaller will get downloaded first.. While the larger is being downloaded, synaptic could install the downloaded ones and I can use them right away while others are busy being downloaded.

I must say i have no idea how the installation on a linux system works. So it may lead to problems.

> **doas777 said:**
> 
7) if you take away your brothers admin rights he shouldn't be able to shut down. 
most systems that supply a "switch users" feature suffer from the same issue. that is much of why MS choose to have most of the installation of updates happen after the logout event. that way all users had no choice butto see the "please do not turn off your PC until updating completes" thing.

I am the only user on the beta OS. He can still do that. that's the problem.

---

### Post by rahilm on 2010-04-05
> **J_Stanton said:**
> you should take your ideas to ubuntu brainstorm. talking about those things here is just a waste of time.
I'll try that. I must add that i find lauchpad sites very confusing. That is one of the reasons i don't report a lot of bugs. ONly through apport do they get reported by me. Atleast, that's what the program tells me.

---

### Post by NightwishFan on 2010-04-05
This should help you out. ;)
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by doas777 on 2010-04-05
> **rahilm said:**
> What i meant was, to start installing a particular program when all of its dependencies have finished downloading. From waht i understand, synaptic first scans the database, finds out the files required to download, then downloads them, and then installs them. The idea is based on the apparent fact that synaptic is mostly idle when downloading packages. Consider a situation that you have to install two programs A and B. An intelligent synaptic would download all dependencies of A and then B which ever is smaller will get downloaded first.. While the larger is being downloaded, synaptic could install the downloaded ones and I can use them right away while others are busy being downloaded.


ok, i'm followin.
as I understand it, that possibility is preempted by design. apt uses a very complex database of installed/installable apps, and as a result, can be destroyed by corruption. in order to keep everything working smoothly, the devs choose to make the database "lock" whenever an app requests the ability to access it. synch locking the database ensures that only one app can access it at a time. that means that the app starts it's operation, and no other app can touch it until the operation is finished. as a result, you can't be in the middle of updating the status of an app being downloaded while at the same time updating the status of the app that is installing.

imagine you have two synaptic windows open. in one you are installing a packageX that requires library libZ, which was already on your system because it is an depend for packageY.  while in the middle of installing X, you start purging Y. 

so instead of spending years writting concurrency tracking code and all kinds of fallback conditions and whatnot, and debugging and testing all the additional code, they choose to make it safe by keeping it simple.

as for shutdown, folks have been able to remove teh shutdown button from login screen at least in past versions. never tried it myself: [http://www.cyberciti.biz/faq/linux-unix-remove-gui-shutdown-reboot-option/](http://www.cyberciti.biz/faq/linux-unix-remove-gui-shutdown-reboot-option/)

---

