---
title: "Wiped my partitions and am installing Xubuntu 15.10"
date: 2015-09-12
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2015-09-12
Yesterday I downloaded Xubuntu 15.10 daily ISO and tried to install it but after about an hour and a half I had to give up. It never successfully installed.

So, this morning I downloaded the Xubuntu 15.10 daily ISO for today but before it even brought up a GUI the ubuntu ubiquity installer crashed.
Still no bueno.

I installed Arch Linux using Xcfe exclusively so I figured I'd like Xubuntu. 

Tried to download the beta1 ISO but it hung and I had to unplug modem and router.

So, I am now downloading the ISO via Transmission which is normally quicker than downloading the ISO any way.

We shall see how it goes... My first Xubuntu install. :cool:

EDIT: Didn't intend to mark this as solved.

---

### Post by sudodus on 2015-09-12
When you download daily iso files with short intervals, we can say that you are ISO-testing, and you can use the QA-tracker and do incremental updating of the iso file from day to day or week to week with zsync :-) This saves a lot of bandwidth. See this link

[http://iso.qa.ubuntu.com](http://iso.qa.ubuntu.com)

and specifically for xubuntu (64-bit)

```
zsync http://cdimage.ubuntu.com/xubuntu/daily-live/current/wily-desktop-amd64.iso.zsync
```

---

### Post by flocculant on 2015-09-12
There's a bug with ubiquity 

[lpbug]1495017[/lpbug]

Ubuntu, Ubuntu Gnome and Lubuntu fail as well.

---

### Post by Cavsfan on 2015-09-12
> **sudodus said:**
> When you download daily iso files with short intervals, we can say that you are ISO-testing, and you can use the QA-tracker and do incremental updating of the iso file from day to day or week to week with zsync :-) This saves a lot of bandwidth. See this link

[http://iso.qa.ubuntu.com](http://iso.qa.ubuntu.com)

and specifically for xubuntu (64-bit)

```
zsync http://cdimage.ubuntu.com/xubuntu/daily-live/current/wily-desktop-amd64.iso.zsync
```

I could not get the beta to install either. After an hour or so it hadn't gotten past where it said at the bottom creating the partition.
I doubt building on a bad ISO is a good idea is it?

I do see your point though. But, I did pull this down with a torrent and Transmission. I wish all flavors used torrents. I've used it with Mate and now Xubuntu, however unproductive.

> **flocculant said:**
> There's a bug with ubiquity 

[lpbug]1495017[/lpbug]

Ubuntu, Ubuntu Gnome and Lubuntu fail as well.

The beta didn't get the same error, but since I got it on the daily I added my name to the bug. 
Thanks for pointing that out. 

I guess I'll give it a few days. I am not giving up on Xubuntu.

---

### Post by sudodus on 2015-09-13
> **Cavsfan said:**
> I could not get the beta to install either. After an hour or so it hadn't gotten past where it said at the bottom creating the partition.
I doubt building on a bad ISO is a good idea is it?

I do see your point though. But, I did pull this down with a torrent and Transmission. I wish all flavors used torrents. I've used it with Mate and now Xubuntu, however unproductive.

zsync uses a method similar to the torrent clients. It replaces chunks of the file that are different, checks each of them and merges them. The final result is always checked (that the md5sum is correct). So, zsync 'can build a good version from a bad version'.
> 

The beta didn't get the same error, but since I got it on the daily I added my name to the bug. 
Thanks for pointing that out. 

I guess I'll give it a few days. I am not giving up on Xubuntu.

That's right. We must expect, that some time during a development cycle, the daily iso files are severely corrupted. Next day or next week they will work again.

---

### Post by Cavsfan on 2015-09-13
> **sudodus said:**
> zsync uses a method similar to the torrent clients. It replaces chunks of the file that are different, checks each of them and merges them. The final result is always checked (that the md5sum is correct). So, zsync 'can build a good version from a bad version'.


That's right. We must expect, that some time during a development cycle, the daily iso files are severely corrupted. Next day or next week they will work again.

Thanks for the information. Bandwidth has never been a problem for me. I pay for 10 down and 1 up and it when tested it gets 17 down and almost 2 up.

I cannot understand how a beta would be released that doesn't install. I thought that surely could not be so. So I got another copy and tried it again from the Xubuntu beta.

After an hour and a half I again gave up. I've already wasted more time than I intended to on this so I'll give it a week or so.

---

### Post by flocculant on 2015-09-13
Then I would suggest there's an issue there - it was obviously tested. If it was uninstallable then it wouldn't have been released.

---

### Post by sudodus on 2015-09-13
I agree with flocculant. The beta iso file would not have been released, if it did not work at all. So I think it works in many computers. But it is different with the daily iso file. Right now the daily Lubuntu iso file boots, but the installer (ubiquity) does not work.

On the other hand, there is no big meaning with the beta iso file. A daily iso file is almost 'on the same level', only less tested. And it is newer and should be closer to the final released system.

---

### Post by Cavsfan on 2015-09-14
> **flocculant said:**
> Then I would suggest there's an issue there - it was obviously tested. If it was uninstallable then it wouldn't have been released.

> **sudodus said:**
> I agree with flocculant. The beta iso file would not have been released, if it did not work at all. So I think it works in many computers. But it is different with the daily iso file. Right now the daily Lubuntu iso file boots, but the installer (ubiquity) does not work.

On the other hand, there is no big meaning with the beta iso file. A daily iso file is almost 'on the same level', only less tested. And it is newer and should be closer to the final released system.

Yes, I got to thinking about that and pretty much knew the beta iso had to be good. I just don't know why it would not go past a certain point. I've installed many 'buntus over the years and knew some thing was not right.

I gave up waiting a week though and was trying to install to a 30 GB (4th physical partition). I tried installing Vivid Xubuntu and it did the same thing as the beta did. So, for some odd reason I decided to delete the 4th partition and make it an extended partition.
I allocated 20GB to sda5 and left 10GB on sda6, just in case I need that. So, Then Vivid Xubuntu finally installed to the sda5 partition. 

Then before I applied any updates I switched it to Wily Xubuntu with **sudo sed -i s'/vivid/wily/g' /etc/apt/sources.list** and dist-upgraded. I got all of the updates and there were many.

So now I'm in with Xubuntu 15.10.
```
cavsfan@cavsfan-le-beast:~$ uname -r
4.2.0-7-generic

```

```
cavsfan@cavsfan-le-beast:~$ cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=15.10
DISTRIB_CODENAME=wily
DISTRIB_DESCRIPTION="Ubuntu Wily Werewolf (development branch)"
NAME="Ubuntu"
VERSION="15.10 (Wily Werewolf)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu Wily Werewolf (development branch)"
VERSION_ID="15.10"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
```

Now just to figure out some quirks as I'm not used to working with Xubuntu, just Xcfe in Arch, which is close I guess.

I installed compiz, it's plugins along with CCSM and the typical **compiz --replace** doesn't seem to work in startup up commands. But it does start it when run from a terminal oddly enough.

I'll get that figured out hopefully.

---

### Post by Cavsfan on 2015-09-14
I've got one problem that I cannot for the life of me remember how to fix: when I open Firefox or a terminal or anything, it opens under the top panel.

I can then pull it down and once it's below the panel it will not go back up.

I think I got the cure for compiz starting up in composite manager of Cairo Dock. Not positive yet though.

---

### Post by QDR06VV9 on 2015-09-14
It used to be Click Start > Preferences > Xfce 4 Settings Manager. Click on the Application Autostart tab. Click the Add button. Enter Compiz for the name, Compiz Startup, for the description, and the same command you entered above, minus the "&" (compiz --replace ccp) in the Command section.
If that don't work Try the below
[http://www.webupd8.org/2012/11/how-to-set-up-compiz-in-xubuntu-1210-or.html](http://www.webupd8.org/2012/11/how-to-set-up-compiz-in-xubuntu-1210-or.html)

---

### Post by flocculant on 2015-09-14
>  I've got one problem that I cannot for the life of me remember how to fix: when I open Firefox or a terminal or anything, it opens under the top panel.

Set panel to not reserve borders.

Right click on panel somewhere - then panel preferences

[IMG]http://i.imgur.com/eNV51Aj.png[/IMG]

---

### Post by Cavsfan on 2015-09-14
> **runrickus said:**
> It used to be Click Start > Preferences > Xfce 4 Settings Manager. Click on the Application Autostart tab. Click the Add button. Enter Compiz for the name, Compiz Startup, for the description, and the same command you entered above, minus the "&" (compiz --replace ccp) in the Command section.
If that don't work Try the below
[http://www.webupd8.org/2012/11/how-to-set-up-compiz-in-xubuntu-1210-or.html](http://www.webupd8.org/2012/11/how-to-set-up-compiz-in-xubuntu-1210-or.html)

I feel like a moron! D'oh! #-oI didn't notice you put the command at the bottom. I am used to the command being in the middle.

[ATTACH=CONFIG]264421[/ATTACH]

Problem solved! 
Thanks!

> **flocculant said:**
> Set panel to not reserve borders.

Right click on panel somewhere - then panel preferences

[IMG]http://i.imgur.com/eNV51Aj.png[/IMG]

I do not have that checkbox checked but the windows still go behind the top panel when opened but if pulled down with Alt+button 1 it will not go back up but it will go down past the bottom panel (which I added).
When I hover the mouse over that checkbox, it does appear that that would cause it but, it's never had a checkmark.

I was thinking maybe something in Windows management in CCSM might be causing it but can't find it any where. I've had this problem before but cannot remember what fixed it.
Thanks!

---

### Post by QDR06VV9 on 2015-09-14
> [COLOR=#000000]I was thinking maybe something in Windows management in CCSM might be causing it but can't find it any where. I've had this problem before but cannot remember what fixed it.[/COLOR]
[COLOR=#000000]Thanks![/COLOR]
In Compiz setting Manager> Window Management> and tick Place Windows.
Kind Regards

---

### Post by Cavsfan on 2015-09-15
> [COLOR=#000000]I was thinking maybe something in Windows  management in CCSM might be causing it but can't find it any where. I've  had this problem before but cannot remember what fixed it.[/COLOR]
[COLOR=#000000]Thanks![/COLOR]

> **runrickus said:**
> In Compiz setting Manager> Window Management> and tick Place Windows.
Kind Regards

Yes, by jove, I do believe that got it! Thanks dude!

Sooo much stuff to remember! *sheesh*!!! :p

Now I believe I'm cooking with gas! I've got the conkys all looking good! Luckily I didn't have to tweak the positioning and font size on Xubuntu.

Like I had to do with Arch, Mate and I don't remember what else. I was able to just use the one I had on Wily with Unity, but of course I used FB with Compiz instead of Unity.

Arch and Mate were like a day and a half's worth of work and that was not programming any of it; just positioning, resizing and tweaking. :lolflag:

---

### Post by QDR06VV9 on 2015-09-15
Nice! That's Great.:-D
No need to thank me Because as bashing-om would say "All for One and One for All".
I think I got that right.:-k Right?:-\"
Seriously Glad I could help.
Cheers

---

### Post by Cavsfan on 2015-09-16
> **runrickus said:**
> Nice! That's Great.:-D
No need to thank me Because as bashing-om would say "All for One and One for All".
I think I got that right.:-k Right?:-\"
Seriously Glad I could help.
Cheers

Right! :D

I have to login a couple of times for everything to get right but that's expected I think.

Cheers

---

### Post by Cavsfan on 2015-09-20
As I mentioned I had the startup for my 4 conkys set to start with no delay.
That is what caused the bootup issues. One must not just start a conky with no delay. :p
Fixed that and it boots pretty smooth.

---

### Post by Cavsfan on 2015-10-16
Messed the system up and did a clean install from the RC yesterday. Actually it took me 2 installs because I got something bad put back in the system that caused the first problem.

So, this time I was more careful. I couldn't get compiz window decorator to work properly so I got Emerald installed via 2 deb files and Ubuntu Software Center and it's looking pretty decent.

It's not *quite* there yet but close.

[[IMG]http://en.zimagez.com/miniature/screenshot2015-10-1613-48-20.png[/IMG]]("http://en.zimagez.com/zimage/screenshot2015-10-1613-48-20.php")

---

### Post by ventrical on 2015-10-16
Nice. 

I have always used xubuntu as a more or less forensic type DE. It can get some major computering done in a reliable fashion.  I have always had problems getting ccsm up in running there.

Regards..

---

### Post by grahammechanical on 2015-10-16
@ Cavsfan

When I first saw your thread title I thought you were referring to the bug where if we did a version upgrade using a live session DVD/USB & it actually did an Erase disk and install Ubuntu.

I was curious because there is a new post where the OP wants to upgrade from Kubuntu 15.04 to Xubuntu 15.10 without doing a fresh install. It might be possible if it was not for the risk of the upgrade doing an erase disk install. 

[http://ubuntuforums.org/showthread.php?t=2299206](http://ubuntuforums.org/showthread.php?t=2299206)

Regards.

---

### Post by QDR06VV9 on 2015-10-16
> **ventrical said:**
> Nice. 

 I have always had problems getting ccsm up in running there.

Regards..
Only If you want to try compiz on xfce this is the method that I had used with Vivid, worked well.
[http://www.webupd8.org/2012/11/how-to-set-up-compiz-in-xubuntu-1210-or.html](http://www.webupd8.org/2012/11/how-to-set-up-compiz-in-xubuntu-1210-or.html)
I have not tried that on Wily yet. But it should work.
Regards

---

### Post by Cavsfan on 2015-10-16
> **ventrical said:**
> Nice. 

I have always used xubuntu as a more or less forensic type DE. It can get some major computering done in a reliable fashion.  I have always had problems getting ccsm up in running there.

Regards..

Thanks.

I was about to give up on CCSM and compiz but I like my eye candy. I finally found a couple of utopic deb files that gave me Emerald and everything has been smooth since.
I have two commands setup in CCSM Commands for Cntl+Shift+F12 and Cntl+Shift+F11 so I know when compiz is not running when those keys don't work.

But, I think I finally found the magical mixture of packages and it seems a lot better than before and pretty solid. At least at this time.

This is my first go around with Xubuntu but I found out it is much like my Xcfe DE running on Arch. I think I really like it.

Regards.

> **grahammechanical said:**
> @ Cavsfan

When I first saw your thread title I thought you were referring to the  bug where if we did a version upgrade using a live session DVD/USB &  it actually did an Erase disk and install Ubuntu.

I was curious because there is a new post where the OP wants to upgrade  from Kubuntu 15.04 to Xubuntu 15.10 without doing a fresh install. It  might be possible if it was not for the risk of the upgrade doing an  erase disk install. 

[http://ubuntuforums.org/showthread.php?t=2299206](http://ubuntuforums.org/showthread.php?t=2299206)

Regards.

Thanks. Yes that title of the thread is a little misleading. I had like 4 Ubuntu installs, Mint 17.2, Arch Linux and Windows 10 and just got tired of all the updating etc.

So, I'm down to just Arch, Xubuntu 15.10 and Windows 10. Much simpler and I like it like this. It's always nice to have a 2nd Linux install in case something goes awry in one of them.

I seen that thread and the OP was trying to do something that shouldn't really be attempted - mixing DEs up. I'd opt for a clean install any day.

I believe ian-weisser made that clear that they would not mix well.

I hope I do not ever encounter an install that erases the disk and installs Ubuntu on the entire disk. I may drop out of the development cycle for a while maybe at least until the beta comes out the next cycle.
But I will be interested since it's an LTS I believe.

Regards.

---

### Post by Cavsfan on 2015-10-17
This recent install went particularly strange. I at first just booted with the DVD and tried to install on the same partition where it was (of course choosing "other" at the bottom). 
But after getting to the point of selecting the partition and formatting it to ext4 at /, checking the format box and clicking continue it stayed at that place forever.

I went and took a shower and did some other stuff. When I came back it was still stuck at that same spot so I killed it. I booted into Arch and in gparted formatted the partition to ext4 and that worked.
Then I went back to the installation DVD and tried again. This time I did not put a check in format the partition. It gave me a bunch of warnings about what might happen but, I continued anyway.

Which I believe turned out to be a mistake because by the time 4-5 hours went by it would no longer boot and gave me the same message in tty "entering emergency mode".
I could login and enter **systemctl reboot**, **systemctl default** (to continue to try a normal boot) and a command to look at the log errors. But it did not accept my login and password.

So I got back in Arch and formatted the partition in gparted again. Then tried the install DVD again and did everything the same but checked the format box.

This time it actually took off and installed. Not sure why it did that like it did when I first opened this thread.

But, finally it's installed and looking pretty good. I'd say much better than before.

---

### Post by sudodus on 2015-10-17
Could it be that there are some 'almost bad' sectors, that sometimes fail to be read from or written to, in the drive space, where you have the ext4 partition?

What is the S.M.A.R.T. status of the drive?

You can try to check and if necessary mark bad sectors with

```
sudo e2fsck -cf /dev/sdxy
```

where x is the drive letter and y is the partition number.

---

### Post by ventrical on 2015-10-17
> **sudodus said:**
> Could it be that there are some 'almost bad' sectors, that sometimes fail to be read from or written to, in the drive space, where you have the ext4 partition?

What is the S.M.A.R.T. status of the drive?

You can try to check and if necessary mark bad sectors with

```
sudo e2fsck -cf /dev/sdxy
```

where x is the drive letter and y is the partition number.

Sudodus,

This is a good point.  I some times take it for granted because Ubuntu distributions have resurrected so many 'supposedly' bad hard drives which may or may not have been infected with Microsoft Malware on Windows. linux/ubuntu is a superb system all around but it does not have the ability to correct solid state wear in materials and parts.

Regards..

---

### Post by Cavsfan on 2015-10-17
> **sudodus said:**
> Could it be that there are some 'almost bad' sectors, that sometimes fail to be read from or written to, in the drive space, where you have the ext4 partition?

What is the S.M.A.R.T. status of the drive?

You can try to check and if necessary mark bad sectors with

```
sudo e2fsck -cf /dev/sdxy
```

where x is the drive letter and y is the partition number.

Good point. I tried running it in Wily but it has to unmounted and so I booted into Arch and ran it.
What does this tell you?

```
[cavsfan@arch-install ~]$ sudo e2fsck -cf /dev/sda5
[sudo] password for cavsfan: 
e2fsck 1.42.13 (17-May-2015)
Superblock last mount time is in the future.
    (by less than a day, probably due to the hardware clock being incorrectly set)
Checking for bad blocks (read-only test): done                                                 
Wily-Xubuntu: Updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

Wily-Xubuntu: ***** FILE SYSTEM WAS MODIFIED *****
Wily-Xubuntu: 200009/1218224 files (0.1% non-contiguous), 1834349/4864502 blocks

```

My daughter got this drive for me for Christmas 2 years ago as my other one was giving warnings that it was going bad.

---

### Post by sudodus on 2015-10-17
I think it looks good concerning e2fsck. I think it tells you if there are bad blocks. The modification might be only about 'Superblock last mount time is in the future'.

Have you checked the S.M.A.R.T. status?

---

### Post by Cavsfan on 2015-10-17
> **sudodus said:**
> I think it looks good concerning e2fsck. I think it tells you if there are bad blocks. The modification might be only about 'Superblock last mount time is in the future'.

Have you checked the S.M.A.R.T. status?

Thanks! I only know how to check the S.M.A.R.T. status in Windows and it would likely only check that partition.

How do I check it in Linux?

---

### Post by sudodus on 2015-10-17
You can do it with ***gnome-disks*** alias 'Disks' in the menu. It is probably enough to check it like that.

*Edit:* Wily: Click the button near the top right corner (with 3 horisontal bars above each other), and select 'SMART data ...'

-o-

You can do it in a more advanced way with ***smartctl***, that you install with smartmontools

```
sudo apt-get install smartmontools
```

See ```
man smartctl
``` for more details.

---

### Post by cariboo on 2015-10-17
> **Cavsfan said:**
> Thanks! I only know how to check the S.M.A.R.T. status in Windows and it would likely only check that partition.

How do I check it in Linux?

You can have a look at S.M.A.R.T. either by opening Disks, or install smartmon tools, then in a terminal type:

```
sudo smartctl -a /dev/sda
```

Oops ninja'd by sudodus

---

### Post by Cavsfan on 2015-10-18
Thanks!

It appears all is well with the disk drive.

Although VinDSL's conky which displays fan speeds shows my CPU fan is going bad. It's spinning about 1700RPM now but shows zero most of the time.
I got the fan after the factory fan went out very shortly after getting the PC. I wasn't sure I could replace it now but when I initially did I had to remove the mobo to put 4 screws and a mount on the other side. 
But, this time it'll just take removing 4 screws and replacing the lube for the heatsink. I think I can handle that.

I got this one in July 2009 so I guess I can't complain too much lol.

I've got another one just like it on order with the lube and it will be here within the week all for under $22.
It's a good thing NewEgg and TigerDirect keep a record of previous purchases so I knew when it was installed.

Thanks again. I made some notes on checking S.M.A.R.T. drives.

---

