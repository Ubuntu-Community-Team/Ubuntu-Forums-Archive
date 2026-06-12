---
title: "User Name and Password"
date: 2009-04-03
forum: Testimonials &amp; Experiences
---

### Post by YancyD on 2009-04-03
Well, so far I have had Ubuntu loaded for  about 10 minutes and don't like it already.  Cannot log on as it indicates I do not have correct Username or password.  So how uninstall Ubuntu and go back to XP??:(

---

### Post by billgoldberg on 2009-04-03
Pop in your XP cd, and install it over the Ubuntu installation.

During the XP install, you can format the drive.

---

### Post by philinux on 2009-04-03
> **YancyD said:**
> Well, so far I have had Ubuntu loaded for  about 10 minutes and don't like it already.  Cannot log on as it indicates I do not have correct Username or password.  So how uninstall Ubuntu and go back to XP??:(

Seems a shame to get this far then quit.

It's case sensitive so be careful. And it's possible to reset them if you choose. Requires a bit of command line stuff.

[https://answers.launchpad.net/ubuntu/+question/3039](https://answers.launchpad.net/ubuntu/+question/3039)

---

### Post by billgoldberg on 2009-04-03
> **philinux said:**
> Seems a shame to get this far then quit.


Exactly, since it takes the whole 1 minute to reset them.

---

### Post by philinux on 2009-04-03
Hi Bill,

It will also take an hour or so to reinstall windows, then god knows how long doing updates and reinstalling programs etc etc.

---

### Post by billgoldberg on 2009-04-03
> **philinux said:**
> It will take an hour to reinstall windows then god knows how long doing updates and reinstalling programs etc etc.

Don't forget the drivers.

:p 

--

To OP:

There are alternatives if you want to run Ubuntu but still have access to XP.

You can dualboot, meaning when you start up your pc you can either start Windows or Ubuntu.

You can virtualize an operating system while you are running another, take a look at Virtualbox.

Or you can use Wubi to install Ubuntu in Windows.

---

### Post by t.rei on 2009-04-03
> **philinux said:**
> Hi Bill,

It will also take an hour or so to reinstall windows, then god knows how long doing updates and reinstalling programs etc etc.

Depending on the Version installed, Internet Connection ans MS-Server performance its about 1-2 hours of patching. About 30 Minutes to install the basic System.
another ¨30 minutes of Patching office if installed.

I know, because I have to do it about once a week. Not mine. Work. 

thank god for that heise.de update-dvd-creation tool. Got the windows-server out of the equasion. :)

Honestly - change your password. If you don't like to USE it use something else. But not being able to remember the username and password for the 10 minutes of configuration won't safe you from forgetting those on windows, too. :shock:

---

### Post by billgoldberg on 2009-04-03
> **t.rei said:**
> Depending on the Version installed, Internet Connection ans MS-Server performance its about 1-2 hours of patching. About 30 Minutes to install the basic System.
another ¨30 minutes of Patching office if installed.

I know, because I have to do it about once a week. Not mine. Work. 

thank god for that heise.de update-dvd-creation tool. Got the windows-server out of the equasion. :)

Honestly - change your password. If you don't like to USE it use something else. But not being able to remember the username and password for the 10 minutes of configuration won't safe you from forgetting those on windows, too. :shock:

To be honest, most people don't need to enter a username and password in XP. 

Don't get me wrong, I'm not saying that is a good thing.

You can also do that in Ubuntu, there is an option for it during install, stuffed away in a corner somewhere.

---

### Post by YancyD on 2009-04-03
So Now I have a recover Menu with the following:
Resume  Resume Normal Boot
clean   Try to make free space
fsck    File system check
root    Drop to root shell prompt
xfix    Try to fix x server

Went into drop to root prompt and added:  Is/home but message says "No such file  or directory"

---

### Post by mkvnmtr on 2009-04-03
Welcom to the Ubuntu forum. Hope you have enjoyed your time here. From your post it seems that reinstalling xp will be the best thing for you.

---

### Post by ajgreeny on 2009-04-03
It is ```
ls /home
``` that you need, ie a lower case L, not upper case i, and don't miss out the space or nothing will happen.  The output from that command will be your username and you can change password easily.
Once you're in recovery mode, you reset the password like so: ```
passwd username
```It will prompt you type the new password twice, and you're done. You can now boot into normal mode and log in to your account.

---

### Post by kansasnoob on 2009-04-03
My dumb question is:

How can you install and not remember or write down your user name and password?

Every time I see something like this I wonder who's trying to hack who's box?

There's a reason they ask for the repetition of password! And when someone says they can't remember what user-name they used I get suspicious!

Sorry to be a turd in the punch bowl, but I don't buy someone not remembering either their user name or password!

---

### Post by YancyD on 2009-04-03
Thanks to everyone for the help.  Finally waded thru and was able to change password.  Now,  Maybe will learn how to use ubuntu.

---

### Post by philinux on 2009-04-03
> **YancyD said:**
> Thanks to everyone for the help.  Finally waded thru and was able to change password.  Now,  Maybe will learn how to use ubuntu.

Marvelous. Dont forget to post here with any problems before trying stuff out. Some guides on the net are out of date. Best to ask here first before using the command line.

---

### Post by stchman on 2009-04-03
> **YancyD said:**
> Well, so far I have had Ubuntu loaded for  about 10 minutes and don't like it already.  Cannot log on as it indicates I do not have correct Username or password.  So how uninstall Ubuntu and go back to XP??:(

1.  You typed in a username and password during installation.  If you forgot it then you will need to reset it.  Booting into recovery mode will allow you to do it.

2.  I think it takes more than 10 minutes to get used to Linux.

Oh well.

---

### Post by stchman on 2009-04-03
> **philinux said:**
> Hi Bill,

It will also take an hour or so to reinstall windows, then god knows how long doing updates and reinstalling programs etc etc.

My rear end, last time I installed XP it took me about 3+ hrs with drivers and updates.

---

### Post by bodhi.zazen on 2009-04-03
Moved to T&eE :

I would like to remind people of two things :

1. Ubuntu is NOT a drop in replacement for Windows. It takes most new users a few months to become comfortabel with a new OS.

2. Please assume the posts as in the OP of this thread are an expression of frustration and a call for assistance, so please let's not flame those who are frustrated.

---

### Post by wolfen69 on 2009-04-04
> **stchman said:**
> My rear end, last time I installed XP it took me about 3+ hrs with drivers and updates.

i have to call you on this one. it should take less time, but i, or anyone else wasn't there. i just feel  i can do windows in my sleep, but linux is my passion.

---

### Post by Tamlynmac on 2009-04-04
> kansasnoob
Every time I see something like this I wonder who's trying to hack who's box?

There's a reason they ask for the repetition of password! And when someone says they can't remember what user-name they used I get suspicious!

I must admit that was also my first thought. Of course some may believe we're both paranoid. ;)

---

### Post by YancyD on 2009-04-04
So, I am back with head hanging low.  I added Ubuntu to a second drive, now that drive does not show up in the My Computer Windows.  So How do I erase the disk in Ubuntu to get rid of it since I can't see it?   I am a stupid newbee that should have never gotten into this.

---

### Post by 3rdalbum on 2009-04-04
Windows cannot read Linux disks unless you install an "ext2" filesystem driver for Windows. I don't use Windows so I can't recommend a particular one - does anyone else want to help out and suggest one?

Don't be discouraged. You've been using Linux for what, two hours? Of course you're a newbie! We were all newbies once, and if we didn't persist with learning Linux then we wouldn't be where we are today. My grandmother is in her 80s, and when she was in her 20s she tried to learn to drive a car. After a few hours she got discouraged and never tried again. She tried to learn to ride a bike; but she went down a hill and was too scared to put on the brake, so she rode straight into a prickle bush. She never tried riding a bike again.

So, please don't give up. Linux isn't any harder than driving a car, riding a bike or using Windows; it's just different.

---

### Post by armandh on 2009-04-04
if your fix via command line fails.... it is quicker to reinstall Ubuntu than windows, and when you get to the install screen where you put in the log on and pass word there is a box to check to skip it at start up. but write it down anyway, you will need it later.

---

### Post by jbysmith on 2009-04-04
> **3rdalbum said:**
> Windows cannot read Linux disks unless you install an "ext2" filesystem driver for Windows. I don't use Windows so I can't recommend a particular one - does anyone else want to help out and suggest one?

I've not used it myself, but [this](http://www.fs-driver.org/) looks like a possibility.  I'm kind of leery about the whole idea myself though; the EXT file system is more sophisticated than NTFS; I'd be worried about losing two operating systems with one BSOD.

---

### Post by cariboo on 2009-04-04
@t.rei

Could you provide a link to the heise.de update dvd creation tool?

Jim

---

### Post by Dylanby on 2009-04-05
> **cariboo907 said:**
> @t.rei

Could you provide a link to the heise.de update dvd creation tool?

Jim

A quick Google gives me [this article]("http://www.vulnerabilityassessment.co.uk/ctupdate.htm")

&

[this app]("http://www.heise.de/ct/projekte/offlineupdate/download_uk.shtml")

---

### Post by cariboo on 2009-04-05
@Dylanby

Thanks, I guess I didn't search enough. :)

Jim

---

### Post by bobmatino17 on 2009-04-05
well just type in "format E:" or whatever drive it is in the windows command line.

---

### Post by night_fox on 2009-04-05
That command deletes everything on a drive. make sure you know exactly what your doing. Actually, that command might not help because if windows can't read ext* it might not assign it a drive letter.

YancyD, I hope you see how evil Microsoft are being here. Ext* is far more sophisticated than any windows file system, and Microsoft choose not to be able to read it. It's possible to install Ubuntu on NTFS (with a performance hit) and it's also possible, using one of the links above, to make windows see your linux file system.

Be careful when doing this because when using windows, windows viruses will be able to do nasty things to your linux partition

Be careful when using the command line especially the root option in recovery mode, and prefixing commands with sudo. You can destroy everything with a 7 character command. If you find it very easy to give up on ubuntu, the last thing we you want to do is to accidentally type in some destructive command. With linux you have COMPLETE control.

Sorry I havent told you how to delete linux, because I dont know.

---

### Post by jbysmith on 2009-04-05
> **night_fox said:**
> That command deletes everything on a drive. make sure you know exactly what your doing. Actually, that command might not help because if windows can't read ext* it might not assign it a drive letter.

Right, if you're wanting to just blast it you'll need to delete the partition and re-create it via Computer Management.  Might also need to boot into a recovery console and run fixmbr if you put a Linux boot loader onto a primary Windows boot drive. You'll know if you need to when you try to boot into Windows and its it's unable to boot. (Yes, you need to get into a console to fix some stuff in Windows too.. that argument against Linux is inane and just plain uninformed.)

Obviously if you're wanting to preserve data, this isn't exactly the best option as it'll complete destroy whatever is on the partition in question.

---

### Post by stchman on 2009-04-06
> **wolfen69 said:**
> i have to call you on this one. it should take less time, but i, or anyone else wasn't there. i just feel  i can do windows in my sleep, but linux is my passion.

I have done MANY XP installs.

From disc in to disc out yes that is an hour.  By the time you install all the drivers, do all the updates, etc. it is more like 3.5 hours.  Lets not forget all the apps that XP needs to become useful.

My Ubuntu installs take about 1/2 that time.  Now mind you you can have a usable Ubuntu install as soon as you reboot.  I am talking after all the updates and I install the apps I love that are not part of the default install.

---

