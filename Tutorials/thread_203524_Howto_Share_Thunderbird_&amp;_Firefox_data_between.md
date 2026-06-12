---
title: "Howto: Share Thunderbird &amp; Firefox data between Ubuntu &amp; Windows"
date: 2006-06-25
forum: Tutorials
---

### Post by Matchless on 2006-06-25
Hi,
   Here it is finally.
[U][B]Howto Thunderbird/Firefox profile share XP & Dapper
[/B][/U]
If you are running a dual boot PC, it would be nice to be able to manage the same emails, addresses and bookmarks from either the Windows or Ubuntu OS. It would even be nice to do this from separate PC's regardless whether they are running Ubuntu or Windows.

Basically what has to be done. You should have a separate FAT32 partition that can be accessed by any other PC or OS and shared for read and write (always mounted and maybe NFS and Samba installed, with sharing activated). You cannot use the Windows NTFS as there are some issues with linux writing to an NTFS partition. If on a dual boot PC, either of the OS's should be able to read this partition. On separate PC's, the PC with the partition must be running and could even be your gateway/server PC.
Each installation of Thunderbird and Firefox stores all its data, such as all the mail and mailboxes, account settings, addressbook, extensions, bookmarks etc. in a profile folder. If you could share the same profile it means that adding or deleting something will show on any installation.
What has to be done is to move the profile to a FAT32 partition and ensure that all the PC's and OS's can see this partition and profile and can read and write to it. Then you have to create a new profile on each installation, which in actual fact only means a new name and pointing it to the shared new location of the profile. Then test each installation to make sure it works.
A problem to keep in mind is that if you already have two different profiles in use you will have to sacrifice one as you cannot combine two. It is also a good idea to save you present profiles somewhere as a backup in case something goes wrong and you need to fall back.

To access the profile manager:

Windows  -  run  thunderbird.exe -profilemanager
or                         firefox.exe -profilemanager

Linux        -  run ./mozilla-thunderbird -profilemanager
or                        ./firefox -profilemanager

The profiles can be found in:

C: / Documents and Settings/user/Application Data/Thunderbird/Profiles/xxxxxxxx.default
C: / Documents and Settings/user/Application Data/Mozilla/Firefox/Profiles/xxxxxxxx.default
 
for Windows or for Ubuntu

/home/<username>/.mozilla-thunderbird/Profiles/xxxxxxxx.default 
/home/<username>/.mozilla/firefox/xxxxxxxx.default

The steps:
1.Boot in Windows and create a FAT32 partition by using any good partion tool (i.e. Acronis etc) to a size you think is sufficient for the data you will store there i.e. 10G.
2.Now create a folder called Mozilla_Profiles and inside this folder, two folders called Thunderbird and Firefox
3.No reboot to Ubuntu. Go to the System menu icon in the kicker panel, Remote Places or Storage Media should show you your FAT32 partition. Ensure that the partion is mounted and that you can share it with NFS and Samba. Test from all your installations.
4.If you have decided to use your old Windows profile for sharing, reboot to Windows and locate you profile as shown above and only copy the Profiles folder in the Thunderbird folder, leave the config file there as this is the one that finally points to the new location, over to you new FAT32 folder Mozilla_Profiles/Thunderbird.
5.If you are using the Ubuntu profile, boot to Ubuntu and do the same.
6.Now you need to point Windows to its old profile in the new location Run the profile manager (see above) and select Create new profile, Begin creating, use the default name such as Default User (or a name you want) and with Choose Folder find the profile you have moved at its new position and select and Finish. Go into the profile manager again and ensure that your new profile is the default or delete the old profile, but do not select the delete files option (in case you need to fall back and can then just repoint back to old folder)
7.Now start Thunderbird and go to Account Settings, select the Server Settings and change the Local Directory to the mail account name found in your new profile location inside the profile folder (see what it was called before changing)
8.Restart Thunderbird and see if you can see all your mails, addresses, extensions, send and receive mail
9.If this is OK then all you need to do is point all your other Thunderbird installations to this same file in the same way regardless of it being an XP or Ubuntu PC
10.For Firefox the same procedure is followed, but after pointing to the new profile location with profilemanager the change is complete and you will be sharing bookmarks, extensions etc.

[COLOR=Blue] Since posting this some contributors have suggested an easier practice that eliminates a seperate fat32 partition and will allow you to leave the partition on one, usually your main installation i.e. ubuntu and share with your windows profile see this:[/COLOR] [http://ubuntuforums.org/showthread.php?t=469666](http://ubuntuforums.org/showthread.php?t=469666)

---

### Post by Matchless on 2006-06-30
Has been updated

---

### Post by crystal on 2006-07-06
The above howto is concerned with profiles in a FAT32 shared partition. I have been successful in applying it to an Ext3 shared partition using the [Ext2 Installable File System For Windows](http://fs-driver.org) on my NTFS Windows partition. With this setup it seems that the "share it with NFS and Samba" part is no longer required, since the shared partition is native to Linux and the Ext2 filesystem driver does the work on Windows.

---

### Post by Matchless on 2006-07-07
I like this very much! And will try it out. This is what we need, howto's to make Windows work with Linux instead of adapting linux to work with Windows!
Thanks

---

### Post by crystal on 2006-07-13
This is my take on the howto, using the Ext2 installable filesystem driver for Windows.

I shall assume that Firefox and Thunderbird have been installed on both Linux and Windows, and that the shared data partition, /home  is 'E:' on Windows.

You now have two sets of profiles. One for Linux, one for Windows. What will happen is that the Windows installation of Firefox and Thunderbird will use the Linux set of profiles.

Boot into Windows. Find the profiles for Firefox and Thunderbird as per Matchless's instructions. You can also type %AppData% into the run program dialog box.

In the Mozilla/Firefox folder you will find profiles.ini
This is a simple settings file. You will only need to change IsRelative and Path.
Path should point to the profile folder on the Linux installation of Firefox.
```
IsRelative=0
Path=E:\<linux-username>\.mozilla\firefox\xxxxxxxx.default
```

Do the same for the Thunderbird profiles.ini in the Thunderbird folder, except that now Path should point to the profile folder on the Linux installation of Thunderbird.
```
IsRelative=0
Path=E:\<linux-username>\.mozilla-thunderbird\xxxxxxxx.default
```

Consequently, if you already have settings (e.g. mail) that you want to import, you should copy them over to the Linux profile folders. Of course, the plugins for each version of Firefox and Thunderbird have to be installed separately (they cannot be shared).

---

### Post by domino on 2006-07-18
I dont want to share the entire firefox folder. Rather I only want to sync/share bookmarks.html, cookies.txt, and signons.txt. Reason is because I use different extentions and themes for firefox in xp/vista/dapper/osx. they all will share using a FAT32 parition.

As for Tb, you can always map the user mail direstories to a common r/w volume. It would not effect what ever extentions and/or themes you use for what ever OS platform.

---

### Post by xmastree on 2006-07-26
I'm having trouble with this.

Firstly, it's just thunderbird I need to share, and it's Windows 98 so it's already FAT32. The drive is shared and working fine.

I created a directory c:\thundershare and copied the contents of
c:\windows\application data\thunderbird\profiles\xxxxxxxx.default
into it.
Namely four directories: chrome, extensions, mail, us and a few files.

When I created the profile in ubuntu, and told it to use that directory, it created a whole bunch of new ones, all ending in .sbd

The mail one is mail.sbd and appears to contain the same stuff as mail from the windows installation, but without the actual content. Just blank.

What am I doing wrong? ](*,)

---

### Post by Oppi on 2006-08-01
Hi,

I tried this out and came to the point where I should edit profiles in Firefox Profile Manager. But there is no Profile Manager for Firefox here. Where do I find it ? I searched in the Add/Remove Prog., in 'Alacarte Menu Editor' ... I only found the profile Manager for Thunderbird.

---

### Post by Metroid48 on 2006-08-02
you have to type (in Linux):

mozilla-firefox -profilemanager

or (in Windows), create a shortcut and add to the path (after the quote):

 -profilemanager

Anyway, I've got the problem that I can't see the folders I created in Windows when I log back into Linux.

---

### Post by Metroid48 on 2006-08-02
you have to type (in Linux):

mozilla-firefox -profilemanager

or (in Windows), create a shortcut and add to the path (after the quote):

 -profilemanager

Anyway, this works great! I did however have to remount the partition for Linux to recognize the folders that I made in Windows. No big.

---

### Post by Epperly on 2006-08-02
Ah thank you! I never thought of doin it this way.

---

### Post by xmastree on 2006-08-03
I got it working eventually. The directory structure had me puzzled for a while though. Go in at the wrong level and it duplicates everything.

Since it's a Windows 98 installation, the disk is already FAT32 so I pointed linux thunderbird right to it.

---

### Post by TiredBird on 2006-08-03
I started sharing the profile of Firefox a year and half ago when they released 1.0. At the time I had two networked computers, one Linux and one Win2K, but with Samba I was able to share the profile. My setup now is one Linux (Ubuntu 6.06), one WinXP, and one dual booting 6.06 and WinXP. It has gotten a bit more complicated also by my use of Thunderbird as a mail client.

Solution: I put Portable Thunderbird and Portable Firefox, (both are Windows only), on a Thumbdrive. I have non-portable Thunderbird and Firefox installed on each of my OS's, (2 each of 6.06 and 2 each of WinXP), with their startup files all pointed at the folder on the thumbdrive. (Yes, that means I have 5 installs of 1.5.0.5 for each program - messy but it works.)

Firefox and Thunderbird cannot find their respective profile folders unless the thumbdrive is plugged into the machine I'm running on but it also means that no matter where I run either of the them I have the latest changes I've made to either without synchronization. It also means that because I have the portable versions on the thumdrive linked to the same profiles I can take Firefox and Thunderbird with me and run them on any Windoze machine I find.

---

### Post by tuxcantfly on 2006-08-03
You can bypass the mozilla profilemanager entirely by making an ntfs junction (create it using winbolic link in windows [http://www.pearlmagik.com/winbolic/](http://www.pearlmagik.com/winbolic/)) for the profile in windows to the profile in the ext3 drive. This also useful for sharing only parts of the profile, not the entire thing; just junction that part only. You can do this the other way around by making a symbolic link to the windows profile in linux, and mount the windows drive as read-write, using ntfs3g.

---

### Post by rodri83 on 2006-08-03
> **tuxcantfly said:**
> You can bypass the mozilla profilemanager entirely by making an ntfs junction (create it using winbolic link in windows [http://www.pearlmagik.com/winbolic/](http://www.pearlmagik.com/winbolic/)) for the profile in windows to the profile in the ext3 drive. This also useful for sharing only parts of the profile, not the entire thing; just junction that part only. You can do this the other way around by making a symbolic link to the windows profile in linux, and mount the windows drive as read-write, using ntfs3g.

Hi,

I'm trying to sync Firefox's bookmars for Windows and Ubuntu. I've follow the steps of the tutorial and select the profile folders for Firefox. When I execute Firefox and, for example, I create a new bookmark, it is created and it showed in the bookmarks list. But when I restart Firefox, the bookmark dissapears. I suppose that Firefox can't write on the profile folder. This is in a ntfs drive (I have read/write support with ntfs-3g and I can write with other app.). What I'm doing wrong?. Sorry for my english :(

---

### Post by bparham on 2006-08-04
A little late in coming, but FireFox has a bookmark sync tool called Foxmarks that uploades copies of bookmarks to the Internet to be pulled down by other computers. I use it at work/home, so when I add a bookmark at work, it's added at home & vice versa.

---

### Post by Nevermore on 2006-08-04
hello
i was trying to follow your tutorial but i found some problems:
first of all i have a fat32 windows installation for ease of share with linux, so i dont have to make a new partition..
however when i try to import windows profiles into ubuntu i get the following message:
the profiles are already in use, please select another profile or close thunderbird process.
and the second time i try to start thunderbird or swiftfox:
thunderbird is alreadt running but not responding, to open a new window u nmust first close the existing thunderbird process or restart ur system..
and i am locked there..
no way i could make it work..
any idea?
thanks

---

### Post by rodri83 on 2006-08-05
> **rodri83 said:**
> Hi,

I'm trying to sync Firefox's bookmars for Windows and Ubuntu. I've follow the steps of the tutorial and select the profile folders for Firefox. When I execute Firefox and, for example, I create a new bookmark, it is created and it showed in the bookmarks list. But when I restart Firefox, the bookmark dissapears. I suppose that Firefox can't write on the profile folder. This is in a ntfs drive (I have read/write support with ntfs-3g and I can write with other app.). What I'm doing wrong?. Sorry for my english :(

Ok. I've solve my problems putting the profiles in a fat32 partition. Now, all works ok. However, has anyone shared firefox and thunderbird profiles with a ntfs partition?

---

### Post by flyvholm on 2006-08-11
Same problem as Nevermore. Made a new FAT32 partition for WinXP/Dapper to share, and migrating to the new folders went smooth in XP. But after creating the new profiles in Dapper I can't start either FF or TB, but get an error message that I need to close the existing, non-responding process (which doesn't exist).

One complicating factor I can think of is that I'm running 64-bit on Dapper, but I'm not sure if that is relevant to this particular issue.

---

### Post by mclaren101 on 2006-08-12
When following the instructions to the letter, this setup works fine the first time, launching the profile manager from terminal, updating and then launching FF or TB, everything is there. But, once I shut it down and attempt to load it up, the settings are no longer there. Little help please?

---

### Post by Matchless on 2006-08-12
Hi,
   Just recheck your profile manager as per point 6 to ensure that that your new profile is the default or delete the old profile, but do not select the delete files option (in case you need to fall back and can then just repoint back to old folder). This is especially important if there are more than 1 profile.
Hope this helps

---

### Post by mclaren101 on 2006-08-12
I have done so, and is has changed the problem. Now it thinks firefox is still running but not responding and must be closed before opening a new window. Not too sure what else to do now.

---

### Post by Matchless on 2006-08-13
Does this happen from both Windows and Ubuntu that are sharing the same profile now or only from one of them?

---

### Post by flyvholm on 2006-08-14
Happens only in Ubuntu (Dapper) in my case. It's working fine in WinXP.

---

### Post by moontan on 2006-08-14
Hi

How to kill persistent processes

I also had problems with firefox and thunderbird processes not terminating. I kept getting errors similar too:
[LIST=1]
[*]thunderbird is already running but not responding, to open a new window you must first close the existing thunderbird process or restart your system.
[*]still running but not responding and must be closed before opening a new window.
[/LIST]
I tried rebooting ubuntu but still had the same error.

This is how I fixed it:
[LIST=1]
[*]Open a terminal and enter the following commands
[*]**ps -A**     
lists all the currently running processes. The listing is in the form
 PID TTY          TIME CMD
The PID column has a list of numbers (process Identifiers) and the CMD column has a list of process commands. The other columns I did not use.
[*]locate the firefox-bin command in the list and note the PID on the same line 
[*] enter **kill <PID>**  (replace PID with number found in step 3) in the console and the firefox process should be terminated.
[*] enter **ps -A** in the terminal to confirm this --> firefox-bin should not be in the CMD list 
[*] Repeat above steps for Thunderbird (CMD is  mozilla-thunder)
[/LIST]

Hope this helps others. Please let me know if this is incorrect. It worked for me and I have been able to consistently repeat it with the same outcome.

This is my first post here so be nice.

Cheers
moontan

---

### Post by stanna on 2006-08-14
this was very handy. thanks alot mate.

---

### Post by flyvholm on 2006-08-15
Neither TB or FF shows up in the list of processes in my case. So there's a different issue triggering these error messages.

---

### Post by moontan on 2006-08-15
The command used needs to be **ps -A** not** ps** or **ps -a**.

That is one possible way you would not see all processes. But if they do not exist then obviously these commands will not do anything. 

It seems like some flag or trigger is not resetting properly. Is there any sort of lock file associated with the process that might not reset when the process dies. Sorry I can no longer help but I am a Linux noob and ubuntu is the most I have gotten into it.

I look forward to seeing how it is solved.

---

### Post by flyvholm on 2006-08-17
Here's a link to some info about what can cause this issue:

[http://kb.mozillazine.org/Profile_in_use](http://kb.mozillazine.org/Profile_in_use)

In my case it appeared to be a permission problem due to the way my FAT32 partition was mounted. In /etc/fstab I was using default mount options:

/dev/hda4    /shared	vfat    defaults    0    0
(FF and TB won't launch)

I changed the mount options to the following:

/dev/hda4    /shared	vfat    rw,user,users,auto,umask=0000	0    0

Rebooted and now FF and TB starts fine using the shared profile. :D

---

### Post by pcolamar on 2006-08-21
Done. Smooth as silk

This is part of my migration from WinXP --> Linux. 
I will play with this configuration for a while and eventually migrate the profiles under ext3 and let Windows (as long as I do not kill it!!)  points to the ext3.

Thanks Matchless

---

### Post by benkong2 on 2006-09-05
My question is this are there extensions that work differently in windows and linux.

This tutorial worked great however it seems that some extensions get clobbered by each other. Also When I choose a download directory on my fat32 partition it is unset when I boot in win or back into dapper. Any thoughts?

---

### Post by moontan on 2006-09-07
> **benkong2 said:**
> My question is this are there extensions that work differently in windows and linux.

If the extension uses a windows dll file it will not work in ubuntu. This occured with the minimise to system tray and view in ie extensions. It does seem possible to get IE to work in Ubuntu but I do not know how and am not really interested.

> This tutorial worked great however it seems that some extensions get clobbered by each other. Also When I choose a download directory on my fat32 partition it is unset when I boot in win or back into dapper. Any thoughts?

My thunderbird folders seem to be a little unstable. Nothing is lost but sometimes they are rebuilt, emails are redownloaded and the order is changed from ascending to descending.

Firefox is fine.

Hope this helps

---

### Post by james99 on 2006-09-08
Thank you bparham, as a newby this was the easiest way to transfer my bookmarks. Worked a treat.
Once again thank you, James

---

### Post by Average Joe on 2006-09-08
I just made symbolic links to my (fat) Windows partition for my Firefox bookmarks and my Thunderbird profile. Works for me.

So, assuming that the Windows partition is mounted under /windows, do:

For Firefox

```
cd ~/.mozilla/firefox/user.default
cp bookmarks.html bookmarks.backup
ln -s /windows/Documents and Settings/Username/Application Data/Mozilla/Firefox/Profiles/user.default/bookmarks.html bookmarks.html
```

For Thunderbird

```
cd ~/.mozilla-thunderbird
cp user.default user.backup
ln -s /windows/Documents and Settings/Username/Application Data/Thunderbird/Profiles/user.default user.default
```

Done.

---

### Post by Average Joe on 2006-09-09
If anybody is still interested in this stuff, I am using another solution now.

1) For Firefox I only want to share the bookmarks between Windows XP and Ubuntu.
2) For Thunderbird I only want to share the mail content.

To do so I:

1) Made a user.js file in my .mozilla directory containing:
```
// Specify which bookmarks file to use:
user_pref("browser.bookmarks.file", "C:\\Path To Firefox Profile\\bookmarks.html");
```
This solves the bookmarks issue for Firefox.

2) Copy the prefs.js file from the partition you want to share to the Thunderbird profile directory. (Make backup of the existing one first!) This contains all your e-mail account settings (apart from the passwords), so you don't have to create them again for your other operating system.

3) Open Thunderbird and under Account Settings >> Server Settings point the Local directory to the mail directory you want to share. You can find this directory in your Profiles >> Mail directory. Do this for every mail account.

Done. Now you still can customize Firefox and Thunderbird with different extensions, themes, etc. for different operating systems. Only your bookmarks and mail content is shared.

P.S. I run Windows on a fat partition, so maybe this does't work too well for ntfs.

---

### Post by Ted_Smith on 2006-09-19
In case anyone has trouble executing the Firefox ProfileManager from the linux command line (as I did) which has already been stated as : 

```

mozilla-firefox -profilemanager


```

,fear not. All you have to do is open the profiles.ini file found in the default profile folder (home/username/.mozilla/firefox), and edit it to look at your shared profile on your FAT partition as follows (the path is given as an example - chnage accordinly): 
```

IsRelative=**0**
Path=**/home/yourmountfolder/vfat/MozillaProfiles/mozillaFF/firefox/p3qqf1aq.default**



```

Save the file, restart Firefox. When it starts, it will look at the profiles.ini file in the default folder, and then be diverted to your shared profile elsewhere on your system. Cunning, eh? 

You must change the 'IsRelative' value from 1 to 0 - 0 means 'use a custom value', 1 means 'use a relative value in the default path'. If you only change the path, but not the IsRelative, you'll get the 'Profile Locked' error. 

I've only added this because I was not able to launch the Profile Manager myself in any way, shape, or forum, and have spent the last two hours trying to do so scouring the Internet. I kept getting errors relating to it not being able to execute mozilla.firefox-bin etc etc. Someone on IRC said it was due to me installing FF 1.5 from the non conventional source? Who knows. Anyway, I hope this easy and quick little tweak might help someone else. It's worked for me. And now I can access my mails and browser settings from my Linux tower and my Windows XP Laptop downstairs. Bravo! Great HOWTO. 

Ted

Cheers

Ted

---

### Post by stanna on 2006-09-19
i think i have something wrong in my setup. i followed the howto exactly and its shared perfectly fine on my fat32 partition, all emails work in both windows & linux. but... about 50% of the time when im sending an email it will keep asking me for my email password in both linux and windows, and all i have to do is keep typing it in until it eventualy works and sends the email. it must have something to do with the profile sharing but i dont know what it is. anyone have any ideas?

---

### Post by ashrack on 2006-11-13
my problem with sharing is when I boot to WIndows and lunch FF and then boot back to LINUX again the AUTOSCROOL FEATURE gets disabled!

---

### Post by ashrack on 2006-11-28
> **ashrack said:**
> my problem with sharing is when I boot to WIndows and lunch FF and then boot back to LINUX again the AUTOSCROOL FEATURE gets disabled!

anyonr

---

### Post by enrybkram on 2006-12-01
Great howto - I've just combined this with the ntfs-3g howto and just pointed Thunderbird in kubuntu to the Windows install on NTFS. Working well.

---

### Post by ramnarayan on 2006-12-04
Hi

I was partly successful in setting up firefox and thunderbird to be shared between Windows and Linux. The thunderbird data was drawn from my linux bakup. Due to technical difficulties - after changing jobs I have not been able to access thunderbird through windows - so am now trying to set it up. As said earlier its partially succesful

Firefox works well. I have managed to set thunderbird up - almost - can see all the folders, read all the existing mails.

BUT I cannot get Thunderbrid to update because it gives me a malformed user name / pass word error. 
I deleted the old password so that it would ask me the new one but Cannot seem to get around and still get the same message.

Any ideas and tips

thanks
ram

---

### Post by radinator on 2006-12-13
I have been using this successfully, except for one problem.

I have the shared profiles on a fat32 partition which is mounted with rw permissions.  Everything is great.  I also use that same partition (not the same directory of course) to hold my thunderbird mail files so those are shared as well.

By the way, I'm on an AMD64 system, and used the new 64-bit HowTo to install 32-bit firefox2 (with working Flash and mplayer and such) on the system.  So firefox2 is using the shared profile.

Things are great, until firefox 2 starts up.  Firefox starts successfully, but from that moment on the whole shared partition is read-only.  If I try to  get new thunderbird mail it tells me that it cannot write to message folders.  If I try to 'touch testFile' on the shared partition, i get a 'read-only' error message.

Also, if I stop and restart firefox, the new firefox process will generate an error message about a security problem (which is rooted in not being able to write data in the shared partition containing the profile).

Ideas?  Somehow, firefox2 is making the whole partition read-only.

Thanks.

---

### Post by zedfrugnug on 2007-01-07
Has anyone tried this, with the data on a USB-stick?

I'd like to be able to take my mail with me from my home computer, to the one at my parents house. The firefox profile would be less important.

Also, does anyone have any idea wether it be would be necessary to have a stick that supports running software (U3 technology)?

---

### Post by ashrack on 2007-01-15
> **ashrack said:**
> my problem with sharing is when I boot to WIndows and lunch FF and then boot back to LINUX again the AUTOSCROOL FEATURE gets disabled!
I will reply to my own problem:\
I finally got the sollution over at BUGZILLA firefox. I am posting the solution so others with similar problem will find the answer:
> --- Comment #1 from Ria Klaassen <ria.klaassen@gmail.com>  2007-01-14 12:51:57 PST ---
Sounds like your Linux has a different default for general. autoScroll.
You could make a user.js with the line user_pref("general.autoScroll", true);
in it.
[http://kb.mozillazine.org/User.js](http://kb.mozillazine.org/User.js)


---

### Post by mooter on 2007-02-05
All I wanted to do was to be able for thunderbird to share the same folders between XP and Edgy so I just pointed Edgy TB to the same 2 folders that XP has, one being the profiles Local Folders (in the XP profiles Local Folders dir) and the Server Settings local directory is the xp dir of the name of the ftp server where I get my mail.

Works fine, it's an NTFS drive so, are you guys talking about more in depth profile settings or have there been some updates lately?

---

### Post by hansning on 2007-02-18
anyway to do this with ubuntu 6.10?

linux newb, can't seem to get ubuntu to see the FAT32 drive.  I'm not really sure how to proceed, as i'm not familiar with the system at all...

---

### Post by Matchless on 2007-02-19
hansning,
            Have a look here, part of this may be what you want.
[http://ubuntuforums.org/showthread.php?t=363886](http://ubuntuforums.org/showthread.php?t=363886)

---

### Post by Danny Boy on 2007-02-22
Excellent write up, went off without a hitch. Thank you. :)

---

### Post by NJC on 2007-03-14
I have Win 98 / Ubuntu 6.06 dual boot running Tbird 1.5.0.10 in both OS'es.

Only problem I have is that Ubuntu Tbird recreates summary files in each folder every time I start. I understand this is/was a bug:
[https://bugzilla.mozilla.org/show_bug.cgi?id=266837](https://bugzilla.mozilla.org/show_bug.cgi?id=266837)

Adding mail.db_timestamp_leeway with a value of 4000 in the Ubuntu Tbird config editor solved the problem. See this:

[http://kb.mozillazine.org/Mail.db_timestamp_leeway](http://kb.mozillazine.org/Mail.db_timestamp_leeway)

-----------------------
UPDATE: Using mail.db ... actually did NOT fix this problem. My problem was that the system clock and Ubuntu were hours apart. See here for more info: [http://kb.mozillazine.org/Daylight_savings_time](http://kb.mozillazine.org/Daylight_savings_time)
I understand this will be fixed in Tbird 2.0

---

### Post by rusyear04 on 2007-03-20
does this HOWTO also work for **winXP** and *edgy*??

if yes, this would really save me quite some disk-space ;)

---

### Post by essex on 2007-03-21
Using the fat-32 partition on the Windows side works fine for both Firefox & Thunderbird, I have not tried to setup Thunderbird on Linux computer yet, I want to get Firefox setup before I try Thunderbird. I cannot see my fat-32 partition on the Windows computer that I am trying to use as the server. When I open profile manager under Linux and try to create a new profile I cannot see or navigate to the fat-32 folder on the Windows machine. I have Samba setup and working as I can browse-R/W these folders & drives with any file browser. Why can't the profile wizard navigate to these folders. I have also tried to do this by modifying the profile.ini.

[General]
StartWithLastProfile=1

[Profile0]
Name=Dell-Host_Fat-32
IsRelative=0
Path=smb://dell-host/Host-Data_3/Mozilla.org/Firefox Profile/Profiles/b3s40k6a.default
Default=1

This profile.ini just caused a new profile to be created.
Is there a way to mount this Windows Fat-32 partition with the fstab file.
Has anyone set this up similarly. :confused:

---

### Post by NJC on 2007-03-21
essex;

I spent WAAAY too long trying to configure Thunderbird mail between Win98/Ubuntu 6.06 when it was a simple task. 

Question: If profile info for Tbird and Firefox is kept in Windows and accessible by Linux, is Samba needed? I don't know the answer but I initially downloaded Samba only to find I didn't use for Tbird. I can tell you what I did to configure mail between both OS'es

First, auto mount Win drive in fstab as per this:

[https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/partitions-booting.html](https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/partitions-booting.html) 

Second, point the Linux thunderbird profile to your Win Tbird profile. Mine looks like this:

[Profile1]
Name=Win
IsRelative=0
Path=/media/windows/windows/profiles/<username>/Application Data/Thunderbird/Profiles/xxxxxxxx.default
Default=1

---

### Post by essex on 2007-03-22
Thanks NJC, this would work if I had a dual boot system. I have two separate computers (Windows XP & Ubuntu Dapper). At this point I have Windows setup to to do my backups and thought that it would be easier to keep the profiles on it. The Linux box does have a fat-32 partition that I can access from Windows, I will probably move the profiles over to it and access them across my network.

---

### Post by JoxBG on 2007-03-22
> **essex said:**
> Thanks NJC, this would work if I had a dual boot system. I have two separate computers (Windows XP & Ubuntu Dapper). At this point I have Windows setup to to do my backups and thought that it would be easier to keep the profiles on it. The Linux box does have a fat-32 partition that I can access from Windows, I will probably move the profiles over to it and access them across my network.

You need samba client tools to mount Windows network share into your local Linux file system:

Checklist: 
  - smbmnt, smbfs, smbclient:  verify if you have them, ie. sudo aptitude show <module name>, if 
    not there install them first. Ubuntu installs smbclient by default (unless server mode), except 
    smbfs
  - set smbmnt to suid so you can use sudo command for mounting devices:
    code:   sudo chmod u+s /usr/bin/smbmnt

Mount manually (permanent mounting discussed later if this works). Use windows share name in yourusername, ditto password:
   code:    smbmount //machine/sharename ~/somedir/subdir -o username=yourusername,password=userpassword

Username and password are only needed if the windows share need permission to access.

Test that it works:
   code : ls -l ~/somedir/subdir
This should list the top level entries in your windows share. You can also traverse that directory like a normal file system (it will show up in profile manager search).

If you plan on manually mounting the share each time the machine reboots, I suggest you create a script. If you need to supply username/password, make that script only readable by you and root. Also make it executable.
     code:   chmod 600 <scriptname>
     code:   chmod +x  <scriptname>

if everything works fine above and you want to do permanent mount, you need to edit /etc/fstab.

   code: sudo gedit /etc/fstab

Add the lines:

//machine/share    ~/somedir/subdir  smbfs  credentials=full_path/to/credentialsfile,uid=idnumber,gid=gidnumber 0 0

You need to use credentials file because fstab is system readable, so any user can see your user/password combination. Now you have to create the credentials file, which I suggest you put in home directory. You can name it anything, for this example i will use .winpasswd (yes start with . so it's hidden).

   code:   echo  username=yourusername >  .winpasswd
   code:   echo  password=userpassword  >> .winpasswd

Make file readable only by you and root;
  code:    chmod 600 .winpasswd

With that your fstab line should look like:

//machine/share   ~/essex/subdir smbfs  credentials=/home/essex/.winpasswd,uid=uidnumber,gid=gidnumber 0 0

To get uidnumber and gidnumber:
   code:   id

Note: make sure the machine can be seen, ie. ping machine name, unless you use the actual ip address. If not available and you don't use Wins server, edit /etc/hosts file and add your machine ip:
          ip address           machine name

Once you reboot, it will be mounted automatically. Now, you can continue mapping your TBird and FF profiles.

If you want to test without rebooting, unmount the share first:

code:  sudo umount  ~/somedir/subdir

mount fstab again:

code: sudo mount -a

test:

code: df -k

Output should show all mounted devices including windows shares


HTH,

Jox

---

### Post by essex on 2007-04-01
> **JoxBG said:**
> You need samba client tools to mount Windows network share into your local Linux file system:

Checklist: 
  - smbmnt, smbfs, smbclient:  verify if you have them, ie. sudo aptitude show <module name>, if 
    not there install them first. Ubuntu installs smbclient by default (unless server mode), except 
    smbfs
  - set smbmnt to suid so you can use sudo command for mounting devices:
    code:   sudo chmod u+s /usr/bin/smbmnt

Mount manually (permanent mounting discussed later if this works). Use windows share name in yourusername, ditto password:
   code:    smbmount //machine/sharename ~/somedir/subdir -o username=yourusername,password=userpassword


I have checked that smbmnt and smbclient are in the /usr/bin/ directory yet this is the error I get. Similar results with smbfs, smbclient. :confused:  Synaptic shows smbfs is installed.

root@Linux-Box:~# sudo aptitude show smbmnt
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable      )
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process       using it?
E: Unable to locate package smbmnt

Using this 
code: smbmount //dell-host/Host-Data_3/Firefox Profile/Profiles/b3s40k6a.default

results in 
Could not resolve mount point Profile/Profiles/b3s40k6a.default
I can browse these shares across the network so I think Samba must be set up properly.  Any suggestions would be appreciated.

---

### Post by hamamelis on 2007-04-11
ntfs-3g: How to share Thunderbird and My Documents between Linux & Windows using ntfs-3g

In Ubuntu Linux Thunderbird I have under Account Settings>Local Folders, Local directory
/media/WinXP/Documents and Settings/Ian/Application Data/Thunderbird/Profiles/default.2qp/Mail/LocalFolders 
This is the same directory that is used by Thunderbird when I log on to WinXP as ian namely:
C:/Documents and Settings/Ian/Application Data/Thunderbird/Profiles/default.2qp/Mail/LocalFolders

I could link Thunderbird to a directory in My Documents if I wanted. This would be more convenient because all I need to do to back up all my data files would then be to back up My Documents.

I've been running ntfs-3g to acces windows NTFS partitions for about a year now and had no trouble at all. There is one advantage for me. I can read and write MyDocuments (on Linux) without any permissions problems since ntfs doesn't really do this much. I suppose this might be a security issue, but it makes life easier.  NB I use Ubuntu and ntfs-3g can be installed from Synaptic.
My fstab entries look like this: 
#/dev/hda4       /media/WinData  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda4 	/media/WinData ntfs-3g defaults,locale=en_GB.utf8 0 0
#/dev/hda2       /media/WinXP    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda2 	/media/WinXP	ntfs-3g defaults,locale=en_GB.utf8 0 0
The commented out lines are the old read only enties. The two partitions are automatically mounted on boot.

Accessing WinXP "My Documents" on Linux or WinXP
On my linux /home/ian there is a "MyDocuments" [note no space]  symbolic link pointing to the WinXP (on ntfs) folder:
/media/WinXP/Documents and Settings/Ian/My Documents. This on a WinXP NTFS partition.
The use of "MyDocuments" as a symbolic link in /home/ian allows Win4LinPro v4.0 to see this and allow WinXP progames to access it as if they were running WinXP natively.

Anytime I click on MyDocuments in the Linux system the Ian/My Documents Windows directory opens for read/write access.

I periodically run chckdsk on WinXP, or on PartPE to ensure that the ntfs partitions are fine. For the last year, I cannot remember getting an error. I believe that ntfs-3g does not work on encrypted volumes which I never use.

I also run Photoshop 7 and Dreamweaver 8 natively using Crossover (or wine) using the same symbolic link to My Documents without any problems at all.

Hope this adds to the fund.
Best wishes,
Ian.

---

### Post by chipbennett on 2007-04-22
Anyone have any experience with Ubuntu 7.04 and Thunderbird 2.0? I have it *almost* working, but not quite.

First, the relevant background:

HDD partitions:

hda2: WinXP (C:), NFTS
hda3: Linux Ubuntu 7.04, Ext3
hda6: Documents (D:), FAT32

(hda1 is an unused FAT partition, used to be the recovery partition; hda4 is the extended partition that holds hda5/6, hda5 is the Linux Swap partition)

Dual-boot, XP/Ubuntu. Documents (hda6) is my shared-data partition.

Mozilla Profiles:

Prior to installing Ubuntu, I had moved my mozilla partitions to the D: drive under Windows, as follows:

D:\Application Data\Mozilla\<application>\Profiles\<profilename>

Currently, these profiles are for Firefox 2.0 and Thunderbird 2.0.

Ubuntu installation:

I installed Ubuntu (originally, Edgy), and pointed Firefox successfully to the profile in hda6.
I upgraded Ubuntu to Feisty, and Firefox still maintained its profile.

I waited to use Thunderbird, as over on the Windows side, I was waiting to upgrade to 2.0, and to upgrade my extensions (especially Lightning, and Enigma).

I installed Thunderbird 2.0 under Ubuntu, and pointed it to the profile in hda6.

Now, I can see my email and contacts, and receive new messages; however, **Thunderbird appears not to recognize any of my installed extensions or themes**.

Any ideas?

Thanks in advance!

---

### Post by NJC on 2007-04-23
I have Tbird 2 downloaded as *.tz but I don't know how to install it properly. I wonder how long until Synaptic picks it up ... and I don't know how to add it yet either. Erg. I've been waiting what seems like a LONG TIME for Tbird 2.0.

---

### Post by mistergq on 2007-04-29
> **NJC said:**
> I have Tbird 2 downloaded as *.tz but I don't know how to install it properly. I wonder how long until Synaptic picks it up ... and I don't know how to add it yet either. Erg. I've been waiting what seems like a LONG TIME for Tbird 2.0.

Go to this web page: [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla)
download the script on that page to the desktop
then run the terminal command line on that page and it will automatically install Thunderbird 2.0

---

### Post by mistergq on 2007-04-29
I want to thank you for putting this How To up.  I created a /home as ext2.  I am only using this plugin with Thunderbird.  Although I see reasons to do it with Firefox, I look at websites with Linux that I wouldn't with windows because of spyware.  Also, I am not sure how I feel about the cache going back and forth between the two.  I am probably over thinking this, so I will probably end up doing it tomorrow.

---

### Post by takin on 2007-05-08
I have used this method for the last couple of years, including a number of reinstalls, but for a few months now, it's been failing on the Ubuntu side.

Thunderbird won't start up until you create an account, so I tried creating dummy data.  I just wanted to get to create a profile so that I could point it to the existing profile, expecting that it would read the configuration there.  But when I did that, it overwrote all the existing data and loaded all sorts of junk folders (anything it could find in the directory structure).

In the end, yesterday, I created a new folder, pointed the profile there, manually reconfigured it for all my email accounts and moved all the folder files back in.  It took many hours, but it works and Windows recognised the configuration straight away.

I now realise it would probably have been easier to just manually create a profile.ini file and a link to the shared mail folder.  It should then find the configuration and use that rather than trying to create a new one.  Something like the following should work.

```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=mymail.default
```

---

### Post by scaltro on 2007-05-12
Anyone have any experience with Ubuntu 7.04 and Thunderbird 2.0? I have it *almost* working, but not quite.

First, the relevant background:

HDD partitions:

hda1: WinXP (C, NFTS
hda2: Linux Ubuntu 7.04, Ext3
hda6: Documents (D, FAT32

Dual-boot, XP/Ubuntu. Documents (hda6) is my shared-data partition.

Mozilla Profiles:

Prior to installing Ubuntu, I had moved my mozilla partitions to the F: drive under Windows, as follows:

F:\\Mozilla\<application>\Profiles\<profilename>

Currently, these profiles are for Firefox 2.0 and Thunderbird 2.0.

I installed Thunderbird 2.0 under Ubuntu, and pointed it to the profile in hda6.

Now, I can see my email and contacts, and receive new messages; however, every time i got a new mail it download it, and re-downlaod the same new mail every time it do the check for new mail on server. And so If  i delete the new mail it re-download it another time for ever....

Any ideas?

Thanks in advance!

---

### Post by lumiawaily on 2007-05-31
I have had problem sharing profile between ubuntu feisty & windows xp.  

I had chosen to share the ubuntu profile (on ext3 partition) and use it in windows xp through ext2ifs.  I had soon discovered that after shutting down windows and booting into ubuntu, it had found problem with the partition and had to spend a long process reparing the drive to recover all the files :S  

scary thing... 

wondering if anyone of u had experienced something like that... i had since turned off the profile sharing and avoiding that at this point.. 

just wanted to share

---

### Post by talkout on 2007-06-07
In case of Windows Vista the profiles are in
> C:\Users\<USER>\AppData\Roaming\Mozilla\Firefox\Profiles

---

### Post by Krydahl on 2007-07-27
OK, I've followed the instructions and it all worked fine, except that thunderbird on ubuntu (Feisty 64 bit) won't automatically check for mail. The windows version does this ok. 

Any ideas?

---

### Post by aaronfay on 2007-08-02
Thanks so much for the tip on Ext2 IFS crystal, the biggest thing keeping me from booting back into my XP install was I didn't want to get my mail messed up (I use TBird on both installs), and I was using webmail (which doesn't keep my 'sent' messages).

Now I think I'll try the shared partition for 'working' files, so I can work on either OS...

Cheers,
Aaron

---

### Post by fistikuffs on 2007-08-16
Hi i'm a new linux user and this took me a while but boy was it worth it:guitar: Thanks for the guide it's given me another reason to stick with ubuntu!

---

### Post by drummer101 on 2007-08-23
I'm pretty new here so I guess I'll just jump right in. I've been trying to get Amarok to play my music on my network share for the past hour and a half.

The problem that I'm in this thread for is as follows...

I've read through the thread a couple times, and followed the guide to the letter, and when I go to mount my share...

```
sudo smbmount //192.168.1.10/music/##### /home/#####/music -o username=######,password=########
```

```
cli_negprot: SMB signing is mandatory and we have disabled it.
6943: protocol negotiation failed
SMB connection failed

```

samba, smbfs and smbclient are all installed... :confused:

---

### Post by metalcoat on 2007-09-18
Please post the contents of your smb.conf.

Also are you trying to mount a samba share from across the network?

Easiest way is to share /home/user/.mozilla-thunderbird/ directory and have only you have permissions to it. (Have ubuntu host)

After that run thunderbird or firefox -profilemanager and create new user and set the shared folder whatever the subdirectory is as the location

---

### Post by rpn on 2007-09-20
A different problem but related.

I have my mail folder hosted on a W2000 server on my home network. Using Thunderbird on XP with that is easy. Just change the server and Local Folder settings to the appropriate directory on the server. However both my main machines are now Ubuntu 7.04 with Thunderbird 1.5 and on both I have an identical problem. 

Both installed and ran fine. Both Ubuntu boxes have no trouble browsing the Windows shares on the server (and other XP machines on the network, and I have installed ntfs-config). For some obscure reason if I browse to change location the shortcut on the desktop does not appear though it does with other browser dialogues. If I type smb://servers name/ then the deeper parts of the share do list so selecting the right folder is fine. Trouble is it will not register in Thunderbird. Nor will it let me type them in directly as I can on an XP box. In short for some reason both location boxes will not allow a change of location on the Ubuntu boxes. Any ideas why? How I can get round this?

Richard.

---

### Post by Paqman on 2007-09-27
> **bparham said:**
> A little late in coming, but FireFox has a bookmark sync tool called Foxmarks that uploades copies of bookmarks to the Internet to be pulled down by other computers. I use it at work/home, so when I add a bookmark at work, it's added at home & vice versa.

I use this as well. Besides synching between Win and Linux it's also handy if you ever run Portable Firefox off a flash drive. Really useful extension.

---

### Post by Spare Tire on 2007-10-26
Hi, here's my case.
I know how to share the firefox profile folder using the -profilemanager switch and pointing it to the right place. But the problem comes after that.
I've configured firefox to download to a specific parition, in my case it's F: But of course linux doesn't understand what F: is so every time i switch from windows to linux or vice versa i have to tell them where to put the downloads. I know that this is a string in the file "prefs.js" inside the firefox profile folder.

user_pref("browser.download.lastDir", "F:");

How must i edit this thing for firefox to understand where to place the downloads in both windows and linux?

---

### Post by nickpaton on 2008-01-25
Great Howto

To clarify setting up the profile in Ubuntu, open a command line using Alt-F2 keys and run

```
thunderbird -profilemanager
```

Nick

---

### Post by NJC on 2008-01-27
FWIW, 
```
Thunderbird -P
```also open up Profile Manager.

---

### Post by gtr33m on 2008-02-04
I have this working on Vista 32bit and 7.10 x64 with the data residing on the windows ntfs partition.

It mostly works fine, except for the lightning extension.  The lightning extension is platform specific so it will work in one os and not in the other.

Anyone else come across this and find a fix?

---

### Post by sublimation on 2008-02-05
I've got the same situation. I'm using Feisty Fawn and Windows XP. The main client does appear to work fine, but as you mention Lightning does seem to be an issue.
Currently, I've been keeping the xpi's on the respective desktops and re-installing Lightning to whichever copy of lightning is open. Unfortunatly it does require me to start up Thunderbird twice every time I switch platforms. 

While only a stop-gap measure, I hope it helps you at least keep working. It's a bit shorter than rebooting just to look at what meeting is coming up.

---

### Post by Brian96 on 2008-02-06
> **sublimation said:**
> I've got the same situation. I'm using Feisty Fawn and Windows XP. The main client does appear to work fine, but as you mention Lightning does seem to be an issue.
Currently, I've been keeping the xpi's on the respective desktops and re-installing Lightning to whichever copy of lightning is open. Unfortunatly it does require me to start up Thunderbird twice every time I switch platforms. 

While only a stop-gap measure, I hope it helps you at least keep working. It's a bit shorter than rebooting just to look at what meeting is coming up.

I was hoping to find a work-around by synching with Google calendar, but that hasn't really panned out either. My primary solution these days is to avoid booting into Windows. :)

---

### Post by noravanq on 2008-06-01
Hi,

My setup is a WinXP and Kubuntu Hardy dual boot. I tried to get the Kubuntu version of firefox to use XP's profile, but I ran into problems, that I think were caused by the add-on Tab Mix Plus. In ubuntu in the list of extensions I could see Tab Mix Plus, but it was completely unresponsive. I tried to uninstall it, so as usual it required a restart of Firefox, but after the restart nothing changed. It actually only got uninstalled when I booted XP.

So if I understand correctly, the same installation of Tab Mix Plus cannot work for both OS's. Is that so? But at the same time, I can't install that add-on twice - once in XP and once in ubuntu, right?

Does this mean it's impossible to share the profile while having a working copy of Tab Mix Plus in both?

Thanks for the help.

I should mention that I am a complete newbie to linux. I have a total of 5 days of linux under my belt.

p.s. I use Tab Mix Plus to have the tabs open in a column on the right as in the picture.

---

### Post by Brian96 on 2008-06-01
> **noravanq said:**
> Hi,

My setup is a WinXP and Kubuntu Hardy dual boot. I tried to get the Kubuntu version of firefox to use XP's profile, but I ran into problems, that I think were caused by the add-on Tab Mix Plus. In ubuntu in the list of extensions I could see Tab Mix Plus, but it was completely unresponsive. I tried to uninstall it, so as usual it required a restart of Firefox, but after the restart nothing changed. It actually only got uninstalled when I booted XP.

So if I understand correctly, the same installation of Tab Mix Plus cannot work for both OS's. Is that so? But at the same time, I can't install that add-on twice - once in XP and once in ubuntu, right?

Does this mean it's impossible to share the profile while having a working copy of Tab Mix Plus in both?

Thanks for the help.

I should mention that I am a complete newbie to linux. I have a total of 5 days of linux under my belt.

p.s. I use Tab Mix Plus to have the tabs open in a column on the right as in the picture.

I think I am having similar problems, but apparently with all (or at least most) of my add-ons. I am thinking this is a Ff 3 problem, not an OS problem (but I could be wrong).

I am running a Hardy/Vista dual boot on a new machine. I copied my shared profiles from my old machine (which was successfully sharing across XP and Gutsy). However, virtually none of my add-ons worked right on the new machine. I tried updating and upgrading, but that failed. So I went into my profile folder and deleted all the files related to my installed add-ons. Then I went back and re-installed them from the Ff add-ons site.

After all this, the add-ons appeared to be working fine in Hardy. However, they are not working well in Vista. (On the other hand, I am having no problems with my add-ons for T-bird.)

---

### Post by noravanq on 2008-06-03
Hi,

I got this to work for thunderbird, but have the following problem.
In WinXP I had named some of the mailbox folders using armenian unicode characters. In Kubuntu those folders showed up with weird names using regular ascii characters. When I changed the folder names back to their original names in armenian in Kubuntu, in WinXP they showed up as question markes, and one of them didn't show up at all.

Is there a way to fix this?

Right now I changed the names to english, but would really like to have the armenian names back.

Thanks

---

### Post by vyom on 2008-06-03
how to work in vi Editor in Ubuntu.

---

### Post by pcolamar on 2008-06-08
> **Brian96 said:**
> I think I am having similar problems, but apparently with all (or at least most) of my add-ons. I am thinking this is a Ff 3 problem, not an OS problem (but I could be wrong).

I am running a Hardy/Vista dual boot on a new machine. I copied my shared profiles from my old machine (which was successfully sharing across XP and Gutsy). However, virtually none of my add-ons worked right on the new machine. I tried updating and upgrading, but that failed. So I went into my profile folder and deleted all the files related to my installed add-ons. Then I went back and re-installed them from the Ff add-ons site.

After all this, the add-ons appeared to be working fine in Hardy. However, they are not working well in Vista. (On the other hand, I am having no problems with my add-ons for T-bird.)
Brian96, same problem here.
I upgraded from gutsy to hardy and the profile sharing was gone.
In my case I deinstalled-reinstalled all the add-on in linux , I rebooted and started working in  WinXP (all fine) but when I went back to linux .... back in trouble.  FF linux does not see all the add-on again.

I will try to move the shared profile from the NTFS partition to an Ext3 one.

Regards

Palmer

---

### Post by vijaym on 2008-06-12
lightning extension stuff

Look for unified lightning. There is a site which shows how to combine the windows and linux versions of the extension.
see [http://wiki.mozilla.org/User:Ssitter/UnifiedLightning](http://wiki.mozilla.org/User:Ssitter/UnifiedLightning) for info on how to build your own version or just use the version from the site.

---

### Post by Brian96 on 2008-06-12
> **pcolamar said:**
> Brian96, same problem here.
I upgraded from gutsy to hardy and the profile sharing was gone.
In my case I deinstalled-reinstalled all the add-on in linux , I rebooted and started working in  WinXP (all fine) but when I went back to linux .... back in trouble.  FF linux does not see all the add-on again.

I will try to move the shared profile from the NTFS partition to an Ext3 one.

Regards

Palmer

Any luck yet?

My issue is that once I get things working in Ubuntu, my add-ons don't work in Windows. In Vista I get the "restart firefox" message in the add-ons window, but it doesn't go away and nothing changes when I let it restart.

This seems to be a problem with Ff3.

---

### Post by pcolamar on 2008-06-13
Not yet Brian,
  the problem with my idea is that the WinXP driver freely available to read/write Ext partitions does not cope very well with ext3 kind of disks. Particularly with the journaling of ext3.
They are designed for ext2 .
When I have a minute I will reformat the temp ext3 partition in ext2 and see if this does any good.

Cheers

Palmer

---

### Post by katalyst23 on 2008-06-28
Just fyi, for anyone using firefox 3 and trying to just share bookmarks by setting the browser.bookmarks.file preference, it no longer works in Firefox 3.  

[http://kb.mozillazine.org/Browser.bookmarks.file](http://kb.mozillazine.org/Browser.bookmarks.file)

> Starting in Firefox 3, bookmarks are stored in the places.sqlite file in the Firefox profile folder and this preference does not allow you to change that location (bug 385077). [1] [2] 

From looking at the bug report, it looks like developers probably won't add it back in for Firefox 3.  

[https://bugzilla.mozilla.org/show_bug.cgi?id=385077](https://bugzilla.mozilla.org/show_bug.cgi?id=385077)

Just thought I'd post this in here for anyone trying that approach, I just upgraded to Hardy Heron and spent an hour or two trying to figure out why my old bookmark sharing setup wasn't working.  I guess I'll try sharing the whole profile and see if that works.

---

### Post by h0bbe on 2008-08-05
Is there a way to do this kind of sharing in Evolution between Ubuntu and Windows?

(Evolution for Windows: [http://www.softpedia.com/get/Internet/E-mail/E-mail-Clients/Evolution-for-Windows.shtml](http://www.softpedia.com/get/Internet/E-mail/E-mail-Clients/Evolution-for-Windows.shtml))

---

### Post by h0bbe on 2008-08-05
> **katalyst23 said:**
> I guess I'll try sharing the whole profile and see if that works. Did it?

---

### Post by MartinSz on 2008-10-16
Not sure if this has been posted yet, so feel free to ignore this if it has. 
I tried the standard method of editing the profile.ini in Linux to make it use the folder in Windows. I got Vista and an NTFS partition and did not want to bother to create another one. 
When I did this, Thunderbird gave me a wierd error message saying that there is a version of it running but not responding (which it wasnt), so I just mounted the directory in windows to the one in Linux after I mount the NTFS partition under Linux. 
Here's how I changed /etc/fstab:
/dev/sda5 /mount/Windows ntfs-3g rw,uid=1000 0 0
/mount/Windows/Users/--Username--/AppData/Roaming/Profiles/Thunderbird/profilename.default /home/--username--/.mozilla-thunderbird/linux_profilename.default none bind

The first line is to mount the NTFS partition, the second one to remount the folder. So far, it seems to work perfectly. 
I know this is really trivial for the more seasoned linux users, but I was quite happy when I discovered this. 

Hope this is helpful.

---

### Post by reg4c on 2008-10-16
Dont mean to burst your bubbles but this is highly unrecommended since sharing profiles means sharing extensions and scripts too. Since Winblowz and Ubuntu don't have the same executables it means that some extensions will act completely weird. In addition, some extensions are available just for Ubuntu or just for Windows meaning that they wont work properly in the other.

I am not reproducing something I read somewhere, I am telling you from experience:
I lost both installations of FFox and when I reinstalled the profile folder was unusable.

Cheers

---

### Post by zachbb on 2008-11-02
reg4c,

Your comments seem directed at Firefox..

What about sharing Thunderbird profiles across vista and ubuntu? Without any addons?

---

### Post by zachbb on 2008-11-02
reg4c,

Your comments seem directed at Firefox..

What about sharing Thunderbird profiles across vista and ubuntu? Without any addons?

---

### Post by hzFVOW00pw on 2009-02-19
This is my synchronisation recipe for Thunderbird. The advantage is that you can take your USB stick anywhere and plug it into any computer with Windows, or Linux with Wine installed and receive and send email. With this method you will always have a backup of your email folders and configuration as well. You can extend this method to other programs as you can see in the configuration file of the synchronisation script.

You need:

- USB-Stick (or card reader with flashcard, or usb-disk), formatted as FAT32.
- ThunderBird-Portable [http://portableapps.com/apps/internet/thunderbird_portable](http://portableapps.com/apps/internet/thunderbird_portable)
- Rsync on Linux
- Thunderbird on Linux

Boot into Windows and connect the USB-Stick.

### OPTIONAL ###

Follow these instructions to fix the drive letter for your USB-Stick:

- Start -> Run...
- Type mmc and click OK. This launches a window with the title Console 1
- Select File -> Add/Remove Snap-in... A window with the title Add/Remove Snap-in will appear.
- Click the Add button at the bottom of the window (on the Standalone tab)
- Select Computer Management from the list then click the Add button
- The Local Computer radio button should be selected. Click the Finish button
- Click the Close button to return to Add/Remove Snap-in window, then click OK to return to Console 1
- Expand the item Computer Management (Local) on the left (under Console Root)
- Expand the item Storage then click on the Disk Management item
- When the window fills on the right side of the console, locate your USB drive in the listing on the lower right scrollable box.
- Right-click on the drives box and select Change Drive Letter and Paths...from the pop-up menu
- Here is where you either assign it an unused drive letter or edit the currently assigned drive letter.
- From the Window that appears, you can choose the drive letter to use. Click OK once you've added/changed the drive letter.
- Select File -> Exit from the main menu, and save the settings when prompted (or not, it doesn't matter)

You can test the changes by removing the USB device and checking in Explorer to be sure it is no longer available, then plug it back in and the newly assigned drive letter should now be present (F5 to refresh display).

### END OPTIONAL ###

Now,

Install TB Portable on the USB-stick in, lets say, Z:\ThunderbirdPortable

Reboot to Linux

Find your TB profile folder, it wil be named something like /home/teddybear/.mozilla-thunderbird/c0mpl3t3b0ll0cks.profile

rename "c0mpl3t3b0ll0cks.profile" to "profile"

```
cd ~ && mv -f "c0mpl3t3b0ll0cks.profile" "profile"

```

Now you need to edit every file that contains "c0mpl3t3b0ll0cks.profile" and change this string to "profile"

We start with the "/home/teddybear/.mozilla-thunderbird/profiles.ini" file

Gnome users:

```
gedit "/home/teddybear/.mozilla-thunderbird/profiles.ini"

```
KDE users

```
kate "/home/teddybear/.mozilla-thunderbird/profiles.ini"

```

Edit the file.

For convenience I have written a script to recurively search for text files and replace text strings within the files. There may be a graphical utility for that purpose, but I'm not aware of it.

```

#!/bin/bash

if [ "$#" != "3" ]; then

    echo -e "Usage: $0 \"/path/directory\" \"original string\" \"replace string\""

    sleep 2

    exit 1

fi

for FILE in $(find $1 -name '*[!~]' -type f) ; do

    unset YESNO

    # Skip this script

    if [ "${FILE}" != "$0" ]; then

	# Skip files other than text

	TEXT="$(file "${FILE}" | cut -d ":" -f 2 | grep "text")"

	if [ -n "${TEXT}" ]; then

	    # Search for original string and ask if it should be replaced

	    if grep --color -e "$2" "${FILE}" ; then

		echo -e "\nFound string \"$2\" in file: ${FILE}"

		echo -en "Replace string \"$2\" with \"$3\" ? [y/n]: "

		read YESNO

		if [ "${YESNO}" = "y" ]; then

		    sed -i "s|$2|$3|g" "${FILE}" 

		fi

		echo

	    fi

	fi

    fi

done

echo -e "\nDone..."

read

exit 0

```

Copy this code by selecting it with the mouse (or trackball ;) ), press CTRL+C and start gedit (or kate) as root:

```

sudo gedit /usr/local/bin/search-replace-text

```

To paste the selected code in gedit, press CTRL-V in the gedit window. Save the file.

Now start a Terminal (i.e. gnome-terminal) and run these commands:

```

sudo chmod +x /usr/local/bin/search-replace-text

cd ~/.mozilla-thunderbird/profile

search-replace-text . "c0mpl3t3b0ll0cks.profile" "profile"

```

You need to explicitly confirm every question with a "y". Pressing enter will just skip replacing the text.

In the next section I'm assuming the mountpoint of the USB-Stick is "/media/usb-stick"

Now you can copy the profile folder to your USB-Stick in /media/usb-stick/ThunderbirdPortable/Data/profile

Command line from a terminal:

```

cp -f ~/.mozilla-thunderbird/profile /media/usb-stick/ThunderbirdPortable/Data

```

Or just use any GUI file manager.

Actually, you can now just copy your profile folder to the stick if you are planning to boot into Windows, process your email from within Windows and then reboot to Linux and copy back the stuff from the stick to your Linux profile folder. That way you'll always have your latest emails.

But I prefer to do this by means of synchronisation with an rsync script I've written for that purpose:

```

#!/bin/bash

# 081124

# Script written by Maxim Heijndijk

#set -x

echo -e "\033[1;33mSTATUS\033[0m: $0 is started...\n"

function usage {

    echo -e "\nOptions: -m --mountpoint /folder/folder (Mountpoint of flashcard or USB-stick. Required option)\n"
    echo -e "        -l --label disklabel (Disklabel of flashcard or USB-stick. Required option)\n"
    echo -e "        -h --help (this help screen)\n"
    echo -e "Example: \"$0 -m /media/usb-stick -l usb-stick\n"

    sleep 5

    exit 1

}

[ -z "$4" ] && usage

while [ ! -z "$1" ]; do

    case "$1" in

	-m|--mountpoint)
	
	    shift
	    MOUNTPOINTS="$1"
	    ;;

	-l|--label)

	    shift
	    DISKLABEL="$1"
	    ;;

	-h|--help)

	    usage
	    sleep 5
	    exit 0
	    ;;

	*)

	    echo -e "Wrong option \"$1\""
	    usage
	    sleep 5
	    exit 1
	    ;;

    esac

    shift

done

# Een entry als "IPADDR FQDN ALIAS" in /etc/hosts voor deze host is,
# belangrijk, anders kan het script de juiste hostnaam niet vinden.

# An entry like "IPADDR FQDN ALIAS" in /etc/hosts for this host is
# important. or else the script will not be able to find the configuration.

for CONF in "/etc/scriptconfig/sync-flashdevice-`hostname -f`.conf" ; do

    if [ -f "${CONF}" ]; then

	. "${CONF}"

    else

	echo -e "\n\033[1;31mEROR\033[0m: $0: Configuration file \"${CONF}\" not found! Script will be aborted..."
	sleep 2
	exit

    fi

done

function unmount_disks {

    cd /

    for MPOINT in ${MOUNTPOINTS} \
		      ; do

	if [ -d "${MPOINT}" ] ; then

	    if grep -q "${MPOINT}" "/etc/mtab" ; then

		umount "${MPOINT}" && echo -e "\033[1;32mOK\033[0m: \"${MPOINT}\" is unmounted..."

	    fi

	fi

    done

    echo

}


function sync_dirs {

    [ "${SYNCTOFAT32}" = "yes" ] && OPTS="rtL" || OPTS="a"

    TARGET_FOLDER="/media/${DISKLABEL}"

    if ! grep -q "${MOUNTPOINT}" "/etc/mtab" ; then

	if [ -d "${MOUNTPOINT}" ] ; then

	    mount "${MOUNTPOINT}" && echo -e "\n\033[1;32mOK\033[0m: \"${MOUNTPOINT}\" is mounted...\n"

	else

	    echo -e "\033[1;31mEROR\033[0m: Folder \"${MOUNTPOINT}\" does not exist..."

	fi

    fi

    if grep -q "${TARGET_FOLDER}" "/etc/mtab" ; then

	cd "${TARGET_FOLDER}"

    else

	if [ -d "${TARGET_FOLDER}" ] ; then

	    if [ -n "${DEVICENODE}" ]; then

		if [ -e "${DEVICENODE}" ]; then

		    echo -e "\n\033[1;33mSTATUS\033[0m: Started filesystem check on \033[1;36m\"${DEVICENODE}\"\033[0m\n"

		    sleep 2

		    if [ ${SYNCTOFAT32} = "no" ]; then

			if /sbin/fsck -pC "${DEVICENODE}"; then

			    mount "${DEVICENODE}" "${TARGET_FOLDER}" && echo -e "\n\033[1;32mOK\033[0m: \"${DEVICENODE}\" is mounted on \"${TARGET_FOLDER}\"\n"

			    cd "${TARGET_FOLDER}"

			    unset DEVICENODE

			fi

		    elif [ ${SYNCTOFAT32} = "yes" ]; then

			if /sbin/dosfsck -y "${DEVICENODE}"; then

			    mount -t vfat "${DEVICENODE}" "${TARGET_FOLDER}" && echo -e "\n\033[1;32mOK\033[0m: \"${DEVICENODE}\" is mounted on \"${TARGET_FOLDER}\"\n"

			    cd "${TARGET_FOLDER}"

			    unset DEVICENODE

			fi

		    fi

		else

		    echo -e "\033[1;31mEROR\033[0m: The file \"${DEVICENODE}\" does not exist! Is the USB device not connected ?"
		    echo -e "\nHit Enter to exit this script..."

		    read

		    exit

		fi

	    else

		mount "${TARGET_FOLDER}" && echo -e "\033[1;32mOK\033[0m: \"${TARGET_FOLDER}\" is mounted.\n"

		cd "${TARGET_FOLDER}"

	    fi

	else

	    echo -e "\033[1;31mEROR\033[0m: The folder \"${TARGET_FOLDER}\" does not exist! Is the USB device not connected or not mounted ?\n"

	    unmount_disks

	    echo -e "Hit Enter to exit this script..."

	    read

	    exit

	fi

    fi

    # The external devices must have a file in their root, which
    # has the same name as the disklabel, whic you can find in
    # /dev/disk/by-label. This is to make sure the rigt device
    # is mounted on the right mountpoint. The disklabel filename
    # is not case-sensiteve.

    # De externe schijven moeten een bestand bevatten in de root,
    # dat dezelfde naam heeft als het schijflabel zoals te vinden
    # in /dev/disk/by-label. Dit  om ervoor te zorgen dat de juiste
    # schijf op het juiste koppelpunt is aangekoppeld. Hoofdletters
    # of kleine letters maakt niet uit

    find ${TARGET_FOLDER} -maxdepth 1 -iname "${DISKLABEL}" | while read DISKLABEL_MIXED; do

	if [ ! -d "${DISKLABEL_MIXED}" -a -e "${DISKLABEL_MIXED}" ]; then

	    [ -d "${TARGET_FOLDER}/${SUBFOLDER}" ] || mkdir -p "${TARGET_FOLDER}/${SUBFOLDER}"

	    # A trailing slash on the source dir means:
	    # Copy directory content only . So, "rsync /dir1/dir2/ /dir3" will copy only the contents of /dir1/dir2 into /dir3.

	    # A Source dir without trailing slash means:
	    # Copy dirs including path. So, "rsync /dir1/dir2 /dir3" wil copy /dir1/dir2 into /dir3.

	    for BRON in ${SOURCE_FOLDERS}; do

		# First copy to flashdevice

		echo -e "\033[1;33mSTATUS\033[0m: Synchronising from \033[1;36m\"${BRON}\"\033[0m to \033[1;36m\"${TARGET_FOLDER}/${SUBFOLDER}\"\033[0m\n"

		nice -20 \
		rsync -uz${OPTS} --modify-window=1 \
	              ${RELATIVE} \
	              --delete \
    	    	      --progress \
		      --exclude-from="${FILTER}" \
	              "${BRON}/" "${TARGET_FOLDER}/${SUBFOLDER}"
		      #-i --list-only \

		echo -e "\n\033[1;33mSTATUS\033[0m: Synchronisation done...\n"

	    done

	    for BRON in ${SOURCE_FOLDERS}; do

		# Get newer files from flashdevice

		echo -e "\033[1;33mSTATUS\033[0m: Synchronisation from \033[1;36m\"${TARGET_FOLDER}/${SUBFOLDER}\"\033[0m to \033[1;36m\"${BRON}\"\033[0m\n"

		nice -20 \
		rsync -uzo${OPTS} --modify-window=1 \
	              ${RELATIVE} \
    	    	      --progress \
		      --exclude-from="${FILTER}" \
	              "${TARGET_FOLDER}/${SUBFOLDER}/" "${BRON}"
		      #-i --list-only \

		echo -e "\n\033[1;33mSTATUS\033[0m: Synchronisation done...\n"

	    done

	fi

    done

}


function do_pass {

    case "$1" in

	01) MOUNTPOINT="${MOUNTPOINT_01}"
	    SOURCE_FOLDERS="${SOURCE_FOLDERS_01}"
	    DEVICENODE="${DEVICENODE_01}"
	    SYNCTOFAT32="${SYNCTOFAT32_01}"
	    RELATIVE="${RELATIVE_01}"
	    SUBFOLDER="${SUBFOLDER_01}"
	    FILTER="${FILTER_01}"
	    ;;

	02) MOUNTPOINT="${MOUNTPOINT_02}"
	    SOURCE_FOLDERS="${SOURCE_FOLDERS_02}"
	    DEVICENODE="${DEVICENODE_02}"
	    SYNCTOFAT32="${SYNCTOFAT32_02}"
	    RELATIVE="${RELATIVE_02}"
	    SUBFOLDER="${SUBFOLDER_02}"
	    FILTER="${FILTER_02}"
	    ;;

	03) MOUNTPOINT="${MOUNTPOINT_03}"
	    SOURCE_FOLDERS="${SOURCE_FOLDERS_03}"
	    DEVICENODE="${DEVICENODE_03}"
	    SYNCTOFAT32="${SYNCTOFAT32_03}"
	    RELATIVE="${RELATIVE_03}"
	    SUBFOLDER="${SUBFOLDER_03}"
	    FILTER="${FILTER_03}"
	    ;;

	04) MOUNTPOINT="${MOUNTPOINT_04}"
	    SOURCE_FOLDERS="${SOURCE_FOLDERS_04}"
	    DEVICENODE="${DEVICENODE_04}"
	    SYNCTOFAT32="${SYNCTOFAT32_04}"
	    RELATIVE="${RELATIVE_04}"
	    SUBFOLDER="${SUBFOLDER_04}"
	    FILTER="${FILTER_04}"
	    ;;

	05) MOUNTPOINT="${MOUNTPOINT_05}"
	    SOURCE_FOLDERS="${SOURCE_FOLDERS_05}"
	    DEVICENODE="${DEVICENODE_05}"
	    SYNCTOFAT32="${SYNCTOFAT32_05}"
	    RELATIVE="${RELATIVE_05}"
	    SUBFOLDER="${SUBFOLDER_05}"
	    FILTER="${FILTER_05}"
	    ;;

	06) MOUNTPOINT="${MOUNTPOINT_06}"
	    SOURCE_FOLDERS="${SOURCE_FOLDERS_06}"
	    DEVICENODE="${DEVICENODE_06}"
	    SYNCTOFAT32="${SYNCTOFAT32_06}"
	    RELATIVE="${RELATIVE_06}"
	    SUBFOLDER="${SUBFOLDER_06}"
	    FILTER="${FILTER_06}"
	    ;;

	07) MOUNTPOINT="${MOUNTPOINT_07}"
	    SOURCE_FOLDERS="${SOURCE_FOLDERS_07}"
	    DEVICENODE="${DEVICENODE_07}"
	    SYNCTOFAT32="${SYNCTOFAT32_07}"
	    RELATIVE="${RELATIVE_07}"
	    SUBFOLDER="${SUBFOLDER_07}"
	    FILTER="${FILTER_07}"
	    ;;

	08) MOUNTPOINT="${MOUNTPOINT_08}"
	    SOURCE_FOLDERS="${SOURCE_FOLDERS_08}"
	    DEVICENODE="${DEVICENODE_08}"
	    SYNCTOFAT32="${SYNCTOFAT32_08}"
	    RELATIVE="${RELATIVE_08}"
	    SUBFOLDER="${SUBFOLDER_08}"
	    FILTER="${FILTER_08}"
	    ;;

	09) MOUNTPOINT="${MOUNTPOINT_09}"
	    SOURCE_FOLDERS="${SOURCE_FOLDERS_09}"
	    DEVICENODE="${DEVICENODE_09}"
	    SYNCTOFAT32="${SYNCTOFAT32_09}"
	    RELATIVE="${RELATIVE_09}"
	    SUBFOLDER="${SUBFOLDER_09}"
	    FILTER="${FILTER_09}"
	    ;;

	10) MOUNTPOINT="${MOUNTPOINT_10}"
	    SOURCE_FOLDERS="${SOURCE_FOLDERS_10}"
	    DEVICENODE="${DEVICENODE_10}"
	    SYNCTOFAT32="${SYNCTOFAT32_10}"
	    RELATIVE="${RELATIVE_10}"
	    SUBFOLDER="${SUBFOLDER_10}"
	    FILTER="${FILTER_10}"
	    ;;

    esac

    [ ! -z "${SOURCE_FOLDERS}" ] && sync_dirs

}

do_pass 01
do_pass 02
do_pass 03
do_pass 04
do_pass 05
do_pass 06
do_pass 07
do_pass 08
do_pass 09
do_pass 10

unmount_disks

echo -e "\033[1;33mSTATUS\033[0m: Done...Hit Enter to exit this script..."

read

exit 0

```

And this is its configuration file:

```

#!/bin/bash

# Windows filter
echo -e "
- [Hh][Ii][Bb][Ee][Rr][Ff][Ii][Ll][.][Ss][Yy][Ss]
- [Nn][Tt][Uu][Ss][Ee][Rr][.][Dd][Aa][Tt]
- [Pp][Aa][Gg][Ee][Ff][Ii][Ll][Ee][.][Ss][Yy][Ss]
- [Ww][Ii][Nn]386[.][Ss][Ww][Pp]
- [Cc][Aa][Cc][Hh][Ee]/***
- [Cc][Oo][Oo][Kk][Ii][Ee][Ss]/***
- [Ll][Oo][Gg][Ss]/***
- [Pp][Rr][Ee][Ff][Ee][Tt][Cc][Hh]/***
- [Ss][Yy][Ss][Tt][Ee][Mm]?[Vv][Oo][Ll][Uu][Mm][Ee]?[Ii][Nn][Ff][Oo][Rr][Mm][Aa][Tt][Ii][Oo][Nn]/***
- [Tt][Hh][Uu][Mm][Bb][Ss]/***
- [Tt][Mm][Pp]/***
- [Tt][Ee][Mm][Pp]/***
- [Tt][Ee][Mm][Pp][Oo][Rr][Aa][Rr][Yy]/***
- _[Rr][Ee][Ss][Tt][Oo][Rr][Ee]/***
" > "/tmp/winfilter"

# Linux filter
echo -e "
- [Cc]ache/***
- thumbs/***
- thumbnails/***
- temp/***
- tmp/***
- junklog.html
- urlclassifier[0-9].sqlite
- [Xx][Pp][Cc].mfasl
- [Xx][Uu][Ll].mfasl
- [Xx][Uu][Ll].mfl
" > "/tmp/linfilter"

# Thunderbird profiles

# This is the location of the partition on which
# the Thunderbird profile resides. The script
# will check if it is mounted.
MOUNTPOINT_01="/home"

# This is the source folder.
# You can specify multiple folders,
# however the will all be copied to
# the same target folder.
SOURCE_FOLDERS_01="/home/ubuntu/.mozilla-thunderbird/profile"

# This is the devicenode. It is used to see if
# there are errors on the filesystem, and if so,
# the script will do a filesystem check. Hence
# it will only need to be specified once in this
# configuration file.
DEVICENODE_01="/dev/disk/by-label/${SCHIJFLABEL}"

# ALWAYS specify "yes" if you are syncing to a
# FAT32 filesystem. FAT32 is slow on updating
# timestamps and this is a workaround.
SYNCTOFAT32_01="yes"

# Specify RELATIVE_01="--relative" if multiple
# source folders are synced to a single target
# subfolder, and it will strip the parent folders
# from the path.
RELATIVE_01=""

# This is the folder to sync the source folder
# to. It il be created if it doe not exist.
SUBFOLDER_01="ThunderbirdPortable/Data/profile"

# This is to filter out unneeded files.
# It calls the filter at the top of the script.
FILTER_01="/tmp/linfilter"

# Firefox profiles
MOUNTPOINT_02="/home"
SOURCE_FOLDERS_02="/home/ubuntu/.mozilla/firefox/profile"
#DEVICENODE_02="/dev/disk/by-label/${SCHIJFLABEL}"
SYNCTOFAT32_02="yes"
RELATIVE_02=""
SUBFOLDER_02="FirefoxPortable/Data/profile"
FILTER_02="/tmp/linfilter"

# Keepass
MOUNTPOINT_03="/home"
SOURCE_FOLDERS_03="/home/ubuntu/.keepassx"
#DEVICENODE_03="/dev/disk/by-label/${SCHIJFLABEL}"
SYNCTOFAT32_03="yes"
RELATIVE_03=""
SUBFOLDER_03="KeePassPortable/Data/db"
FILTER_03="/tmp/linfilter"

```

The script first parses its configuration file which resides in /etc/scriptconfig. Then it wil check if a device is mounted and, if not, it wil exit with an error message. If the device is mounted, the script will first synchronise your Linux TB profile to the USB stick, and copy anything that is newer to the stick. Then it will check if there are newer files on the stick and copy them back to your Linux TB profile. Finally the stick will be unmounted.

If yo'd like to try this as well, then follow these steps:

Copy this code by selecting it with the mouse, press CTRL+C and start gedit (or kate) as root:

```

sudo gedit /usr/local/bin/sync-flashdevice

```

To paste the selected code in gedit, press CTRL-V in the gedit window. Save the file and then make it executable.

```

sudo chmod +x /usr/local/bin/sync-flashdevice

```

Do something similar for the config file, but save it in /etc/scriptconfig in the format sync-flashdevice-hostname.conf:

```

hostname
sudo mkdir -p /etc/scriptconfig
sudo gedit /etc/scriptconfig/sync-flashdevice-yourhostname.conf

```

(You can find out what your hostname is by typing 'hostname').

Edit the configuration to your likings.

You're almost done. One thing that still needs to be done is to create an empty text file in the root of the USB-Stick which is named exactly like the disklabel and mountpoint of your stick. So, if the disklabel is "usb-stick" the file must also be named "usb-stick". This is to verify the right device is mounted on the right mountpoint, if there are multiple devices attached to the computer. You can find out the disklabel with:

```

ls /dev/disk/by-label

```

Then create the file:

```

sudo touch /media/usb-stick/usb-stick

```

...or, again, create an empty file with any file manager.

Now you have to mount the stick, and if all's well the script can be started. Start it from a terminal with:

```

/usr/local/bin/sync-flashdevice -m /media/usb-stick -l usb-stick

```

-m is the mountpoint
-l is the disklabel

You can of course also put an icon on your desktop to make things easier:

```

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Sync USB Stick
Categories=System;
Exec=/usr/local/bin/sync-flashdevice -m /media/usb-stick -l usb-stick
Icon=konsole
MimeType=;
Name=Sync USB Stick
StartupNotify=false
Terminal=true
Type=Application

```

Copy and paste it in a textfile and save it on your desktop.

Now you can always keep your email synced by following this procedure:

- Get your email from within Linux
- Start the synchronisation
- Reboot to Windows
- DO NOT TRY TO GET YOUR EMAIL IF YOU SKIPPED THE FIRST STEP (Synchronising)
- Start ThunderbirdPortable
- Email away
- Reboot to Linux
- DO NOT GET TRY TO GET YOUR EMAIL FROM LINUX YET!
- Start Synchronisation
- Email away

Always follow this scheme strictly, or you will lose email.

---

### Post by Brian96 on 2009-02-21
I, for one, grew tired of the complications and switched to an IMAP e-mail account and Google calendar to keep my e-mail synchronized, and Foxmarks for Firefox. It's not perfect, but it keeps the important (to me) features all synced up.

---

### Post by Rebelli0us on 2009-05-10
It was simple for me. I have Thunderbird 2.0 installed in both Windows and Ubuntu on different disks. I'm sharing my Windows Thunderbird 2.0 profile on an NTFS volume.

In Ubuntu command window I typed "thunderbird -profilemanager". In profile manager I created a new profile "shared profile" and pointed to the Windows profile directory. The "profiles.ini" file in \root\.mozilla-thunderbird\ got updated as folows:

[Profile1]
Name=Shared Profile
IsRelative=0
Path=/media/<Volume Label>/Documents and Settings/<User Name>/Application Data/Thunderbird/Profiles/<random name>.default
Default=1

Thunderbird now works in Ubuntu with all my account settings, existing mail, preferences, etc. Frankly, Thunderbird is not as good as Outlook Express, but it's free as in FREEDOM. Firefox, on the other hand, kicks IE butt.

---

### Post by hey_there on 2009-11-21
Is there any way to also make filters work in both Linux and Windows? I guess it's a problem of the / and \ usage in Win and Linux...

When I set the filters up in Win, Thunderbird will disenable them under Linux as soon as there comes a mail that uses it and vice versa... :(

---

### Post by hzFVOW00pw on 2009-11-21
> **hey_there said:**
> Is there any way to also make filters work in both Linux and Windows? I guess it's a problem of the / and \ usage in Win and Linux...

When I set the filters up in Win, Thunderbird will disenable them under Linux as soon as there comes a mail that uses it and vice versa... :(

Filters work with my setup under Win and Linux. But I set the filters up under Linux. I don't think it's a problem with (back)slashes because the msgFilterRules.dat files contains mailbox:// url-type strings.

---

### Post by hey_there on 2009-11-22
Right, now that I know which file to check, I found why it is not working: When a folder is written in caps, linux uses only lower case. But then again, Win does not find it. Both show it correcty in Thunderbird, i.e. in caps. Example:

Win uses

actionValue="mailbox://.../Inbox/AMG"

But linux wants

actionValue="mailbox://.../Inbox/amg"

Any way to fix that?

---

### Post by hzFVOW00pw on 2009-11-23
> **hey_there said:**
> Right, now that I know which file to check, I found why it is not working: When a folder is written in caps, linux uses only lower case. But then again, Win does not find it. Both show it correcty in Thunderbird, i.e. in caps. Example:

Win uses

actionValue="mailbox://.../Inbox/AMG"

But linux wants

actionValue="mailbox://.../Inbox/amg"

Any way to fix that?

Win can read either AMG or amg, but Linux reads the dirnames as they really are.

So maybe you could hand-edit the file. Change the directory names like they show up in Linux, because Win doesn't make distinction between caps and lowercase. Or just set up your filters in Linux.

Also, when your folders are on a FAT32 partition you should mount this partition from Linux with an extra option shortname=mixed to get mixed uppercase and lowercase characters. Otherwise Linux will squeeze all filenames to lowercase. So, something like:

```
mount -t vfat -o shortname=mixed /dev/sda1 /mnt/windows
```

or put hardcoded options in /etc/fstab like this:

```
/dev/sdb1 /mnt/windows vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 0 0
```

---

### Post by hey_there on 2009-11-23
Thanks, I put that code in my fstab. I had already installed a script to copy the msgFilterRules.dat on start/stop so that for linux I had a working lower case and for win the upper case file.

Thanks a lot! :)

---

### Post by spoxox on 2010-02-18
I confess, I haven't read all 10 pages of posts here. It would take longer than the solution I tried this morning.

Having just installed Ubuntu (9.10) via Wubi on my Vista machine, I, too, wanted the email solution. I have been using Thunderbird with many accounts (news & email, POP and IMAP) on Vista, imported from XP, imported from some other Windows, since at least 2006 I think.

After installing Thunderbird on Ubuntu, I:
1) rm ~/.mozilla-thunderbird (hope this is the right name; I'm on Vista now!)
2) ln -s /host/Users/me/AppData/Roaming/Thunderbird .mozilla-thunderbird

and it works. Moving back to Vista, when launching I get migration messages (version 2 on Ubuntu, 3.x on Vista). Undiscovered problems may remain, and I haven't checked many features (e.g. filters), but so far, so good.
---
After 2 weeks, all is well. Updated to v3 on Ubuntu. (Had to re-add IMAP account.)

---

### Post by yorkie2 on 2010-04-21
Hi, joining v late to this I suspect, but I have similar needs/problem which I cannot solve despite having read all this thread, and others.

I would like to share mail folders (mail and local) between different installations of Thunderbird.
Currently I have all mail folders, but no profile, on a Freenas samba share. Windows can get to these without problems, just a couple of changes in the profile.ini file and away I go, three different windows machines see the same mail and local folders.

I now have Thunderbird on karmic 9.10, woks fine 'locally', but I'd like to use it more and so would like to connect to the mail folders on the Freenas samba share.

But, I can't find a way of putting the correct folder/share names into any of the various configuration areas of Thunderbird.

If I go into file browser, the mail files location is "smb://freenas/freenas1/Documents/****/Thunderbird%20profile", but I can't browse to that location when go into Thunderbird profile manager. Nor does it seem to work when I edit that string directly into profile.ini (with associated - isrelative=0 change). Thunderbird just refuses to start.
I've tried various options of removing the smb: and //freenas parts of the text string, but no different behaviour.

Does anyone have any insight into what I must have done wrong, or what other avenue I haven't followed ?

TIA

Yk2

---

### Post by smmankad on 2010-10-06
Thanks a lot for all this :) It works!

---

### Post by rcbinwi on 2010-11-06
My Firefox doesn't seem to be able to read the XP partition since I upgraded to Koala.  I run profile manager, and when I pick the XP profile, it says Firefox is already running, which, of course, isn't.

Any suggestions?

---

### Post by suspectDevice12 on 2011-04-06
Hi,

Like Spoxox.  I did not read through all the previous posts.  Just wanted to share what worked for me.  As it seems on the ubuntu side the directory name has changed.

First I am using windows 7 with a wubi install of maverick.

After installing Thunderbird on Ubuntu, I:
1) rm ~/.thunderbird 
2) ln -s /host/Users/me/AppData/Roaming/Thunderbird ~/.thunderbird

I think thunderbird only creates the .thunderbird directory after you have set up a profile.  If you do not see the folder that might be the reason.  If you are using the gui and looking for the folder you may need to try pressing ctrl-h.

---

### Post by WernerB on 2011-04-11
Another option.

- run TB once on Ubuntu and create a profile
- stop TB
- change the "Path" entry in ~./thunderbird/profiles.ini


e.g.
Path= /media/1A32C7D832C7B6D3/Users/username/Application Data/Thunderbird/Profiles/qxn1pkxp.default

and change IsRelative=1 to IsRelative=0

restart TB

To cleanup you might want to remove the profile folder created at the beginning.

Werner

---

### Post by gajanan.khandake on 2011-11-06
> **Matchless said:**
> Hi,
   Here it is finally.
[U][B]Howto Thunderbird/Firefox profile share XP & Dapper
[/B][/U]
If you are running a dual boot PC, it would be nice to be able to manage the same emails, addresses and bookmarks from either the Windows or Ubuntu OS. It would even be nice to do this from separate PC's regardless whether they are running Ubuntu or Windows.

Basically what has to be done. You should have a separate FAT32 partition that can be accessed by any other PC or OS and shared for read and write (always mounted and maybe NFS and Samba installed, with sharing activated). You cannot use the Windows NTFS as there are some issues with linux writing to an NTFS partition. If on a dual boot PC, either of the OS's should be able to read this partition. On separate PC's, the PC with the partition must be running and could even be your gateway/server PC.
Each installation of Thunderbird and Firefox stores all its data, such as all the mail and mailboxes, account settings, addressbook, extensions, bookmarks etc. in a profile folder. If you could share the same profile it means that adding or deleting something will show on any installation.
What has to be done is to move the profile to a FAT32 partition and ensure that all the PC's and OS's can see this partition and profile and can read and write to it. Then you have to create a new profile on each installation, which in actual fact only means a new name and pointing it to the shared new location of the profile. Then test each installation to make sure it works.
A problem to keep in mind is that if you already have two different profiles in use you will have to sacrifice one as you cannot combine two. It is also a good idea to save you present profiles somewhere as a backup in case something goes wrong and you need to fall back.

To access the profile manager:

Windows  -  run  thunderbird.exe -profilemanager
or                         firefox.exe -profilemanager

Linux        -  run ./mozilla-thunderbird -profilemanager
or                        ./firefox -profilemanager

The profiles can be found in:

C: / Documents and Settings/user/Application Data/Thunderbird/Profiles/xxxxxxxx.default
C: / Documents and Settings/user/Application Data/Mozilla/Firefox/Profiles/xxxxxxxx.default
 
for Windows or for Ubuntu

/home/<username>/.mozilla-thunderbird/Profiles/xxxxxxxx.default 
/home/<username>/.mozilla/firefox/xxxxxxxx.default

The steps:
1.Boot in Windows and create a FAT32 partition by using any good partion tool (i.e. Acronis etc) to a size you think is sufficient for the data you will store there i.e. 10G.
2.Now create a folder called Mozilla_Profiles and inside this folder, two folders called Thunderbird and Firefox
3.No reboot to Ubuntu. Go to the System menu icon in the kicker panel, Remote Places or Storage Media should show you your FAT32 partition. Ensure that the partion is mounted and that you can share it with NFS and Samba. Test from all your installations.
4.If you have decided to use your old Windows profile for sharing, reboot to Windows and locate you profile as shown above and only copy the Profiles folder in the Thunderbird folder, leave the config file there as this is the one that finally points to the new location, over to you new FAT32 folder Mozilla_Profiles/Thunderbird.
5.If you are using the Ubuntu profile, boot to Ubuntu and do the same.
6.Now you need to point Windows to its old profile in the new location Run the profile manager (see above) and select Create new profile, Begin creating, use the default name such as Default User (or a name you want) and with Choose Folder find the profile you have moved at its new position and select and Finish. Go into the profile manager again and ensure that your new profile is the default or delete the old profile, but do not select the delete files option (in case you need to fall back and can then just repoint back to old folder)
7.Now start Thunderbird and go to Account Settings, select the Server Settings and change the Local Directory to the mail account name found in your new profile location inside the profile folder (see what it was called before changing)
8.Restart Thunderbird and see if you can see all your mails, addresses, extensions, send and receive mail
9.If this is OK then all you need to do is point all your other Thunderbird installations to this same file in the same way regardless of it being an XP or Ubuntu PC
10.For Firefox the same procedure is followed, but after pointing to the new profile location with profilemanager the change is complete and you will be sharing bookmarks, extensions etc.

[COLOR=Blue] Since posting this some contributors have suggested an easier practice that eliminates a seperate fat32 partition and will allow you to leave the partition on one, usually your main installation i.e. ubuntu and share with your windows profile see this:[/COLOR] [http://ubuntuforums.org/showthread.php?t=469666](http://ubuntuforums.org/showthread.php?t=469666)
Hi Matchless,

Thank You!

It workd for me too with a little change for ubuntu 10.04 LTS and Windows Vista over ntfs partition. I am facing problem with lightning I am gussing that is due to different version of Thunderbird. Is it that, we must have same version of Thunderbird on Ubuntu as well as on Linux for all featurs to work correctly?

---

### Post by jsavga on 2012-02-06
_[This]("http://askubuntu.com/questions/92053/can-i-use-the-same-thunderbird-profile-under-windows-and-ubuntu/100664#100664")_ is how I shared my existing XP thunderbird profile with a new Ubuntu installation on a dual boot set up. I never created a profile in the Ubuntu Thunderbird, opting to edit the profile.ini file first to point to my XP thunderbird profile. 

I have Ubuntu set to _[automount]("http://askubuntu.com/questions/46588/how-to-automount-ntfs-partitions")_ my XP drives. If you don't, you need to make sure to mount the drive before launching Thunderbird or else you'll get an error.

---

