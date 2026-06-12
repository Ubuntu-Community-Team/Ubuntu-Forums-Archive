---
title: "Thunderbird wont start"
date: 2010-09-12
forum: Ubuntuzilla
---

### Post by kelmark2180 on 2010-09-12
I'm using 10.04 Lucid and updated using thunderbird-mozilla-build, but TB will not start. I tried starting in a terminal/usr/bin/thunderbird -safe-mode and the only thing that happens is I get cmd accepted and a new line. No errors. I tried just thunderbird in terminal with same results.

Any help is appreciated. I really don't know where to go from here.

---

### Post by nanotube on 2010-09-14
> **kelmark2180 said:**
> I'm using 10.04 Lucid and updated using thunderbird-mozilla-build, but TB will not start. I tried starting in a terminal/usr/bin/thunderbird -safe-mode and the only thing that happens is I get cmd accepted and a new line. No errors. I tried just thunderbird in terminal with same results.

Any help is appreciated. I really don't know where to go from here.

hmm strange - works fine for me on lucid. ...

do you have an existing thunderbird profile? if you do, can you post the output of ```
ls -ald ~/.thunder*
```

what was your setup prior to installing the -mozilla-build package?

---

### Post by kelmark2180 on 2010-09-14
> **nanotube said:**
> hmm strange - works fine for me on lucid. ...

do you have an existing thunderbird profile? if you do, can you post the output of ```
ls -ald ~/.thunder*
```

what was your setup prior to installing the -mozilla-build package?

This didn't seem like much output, however:

donald@donald-toughbook:~$ ls -ald ~/.thunder*
drwx------ 4 donald donald 4096 2009-12-09 10:39 /home/donald/.thunderbird
lrwxrwxrwx 1 donald donald   33 2009-12-09 10:36 /home/donald/.thunderbird.upstream -> /home/donald/.mozilla-thunderbird
donald@donald-toughbook:~$ 

Thunderbird was working, and I think I installed it w/ubuntuzilla.py
It was the upgrade that went South.
Thanks; Don

---

### Post by nanotube on 2010-09-14
a couple of things to try:

first, in case you have any stuff left over from ubuntuzilla.py's install, run ubuntuzilla.py remove process, have it delete everything it needs to, then reinstall the thunderbird-mozilla-build package from the repository.

second (if first doesn't do it), try starting with a fresh profile and see if that helps.
so... move .thunderbird out of the way (rename it to like, .thunderbird.bak), and see if thunderbird starts then. if yes, then the problem is somewhere in your profile.

---

### Post by KenDiPietro on 2010-09-15
I have the same problem here. 

After the last round of upgrades Thunderbird 3.(?) will not start. I click either on the icon, or try to launch from the menu and I get the Start Thunderbird block on my program panel and then nothing. Even starting from the command line gives me a few seconds of disk activity and then nothing.

Top does not show the program as running.

I renames the .thunderbird directory as instructed and still nothing, no change. However, Thunderbird did create a new .thunderbird profile - so I do have that going for me.

There's a problem out there.

---

### Post by KenDiPietro on 2010-09-15
Okay, this is what I did to get Thunderbird to work.

First up - Locate the thunderbird directory 

Second, View > Show Hidden Files.

Now locate the .thunderbird folder. At this point, it might be a good idea to make a copy (backup) of the .thunderbid folder somewhere safe.

Carefully delete the thunderbird folder (and make sure you are deleting the correct thunderbird folder - **NOT THE _._thunderbird folder**) 

To be safe, I renamed the .thunderbird folder .thunderbird.old - and I would advise you to do the same - even though you made a backup copy, right?

Download the latest version of Thunderbird from Mozilla's site and put it in your home folder (whatever that is called)

Double click on the compressed file to extract it and allow it to extract into the home folder.

At this point, you can now start Thunderbird as you usually do - *But wait, there's more.*

You will be prompted to create a new account and I think you need to complete this. To be honest with you, I didn't try canceling the process, you might be able to, I'm not sure. If someone else tries this please post your results here for the benefit of everyone else.

What I did, at this point was to now locate both the .thunderbird folder that was recently created by Thunderbird when you just started it up and the old .thunderbird folder.

Open both folders up on your desktop so that you can see both of them. Open up the cryptically named profile folders and you should see the your Mail folder. Now open up the Mail folder in both windows.

Copy the entire contents of the mail folder from your old profile Mail folder into your new profile Mail folder. WARNING - DO NOT MAKE THE MISTAKE OF COPYING THE NEW MAIL FOLDER INTO YOUR OLD MAIL FOLDER - but if you do, you made a backup, right.

Once the operation is complete you can restart Thunderbird and enjoy all the sweet functionality that a correctly operating Email/RSS/Calendar brings you, assuming you use Thunderbird for all of those things.

---

### Post by kelmark2180 on 2010-09-15
> **nanotube said:**
> a couple of things to try:

first, in case you have any stuff left over from ubuntuzilla.py's install, run ubuntuzilla.py remove process, have it delete everything it needs to, then reinstall the thunderbird-mozilla-build package from the repository.

second (if first doesn't do it), try starting with a fresh profile and see if that helps.
so... move .thunderbird out of the way (rename it to like, .thunderbird.bak), and see if thunderbird starts then. if yes, then the problem is somewhere in your profile.

I tried-dis and dat as follows:
The ubuntuzilla.py is gone to the bitbucket evidently long before the thunderbird-mozilla-build package.

I renamed my ???.default and tried TB. It crashed. You may grin, but that's the most generated output from TB in awhile.

Looked in SW Center and saw Thunderbird, (Uninstalled it)
sudo apt-get remove thunderbird-mozilla-build (Restarted Ubuntu)
Renamed .thunderbird thunderbird.old
sudo apt-get install thunderbird-mozilla-build (No big install file downloaded?, I guess it's in somewhere local files)
The build completed with no errors, I launched TB and I'm back at my original post results. Tried thunderbird in Terminal and results in nice nothing new cmd line.
BTW, I have the same setup +OS on a desktop and it works fine. I'm ready to just quit stepping on my pvt-parts and say uncle since TB isn't the only email client.
Thanks for your time; Don

---

### Post by nanotube on 2010-09-15
> **kelmark2180 said:**
> I tried-dis and dat as follows:
The ubuntuzilla.py is gone to the bitbucket evidently long before the thunderbird-mozilla-build package.

I renamed my ???.default and tried TB. It crashed. You may grin, but that's the most generated output from TB in awhile.

Looked in SW Center and saw Thunderbird, (Uninstalled it)
sudo apt-get remove thunderbird-mozilla-build (Restarted Ubuntu)
Renamed .thunderbird thunderbird.old
sudo apt-get install thunderbird-mozilla-build (No big install file downloaded?, I guess it's in somewhere local files)
The build completed with no errors, I launched TB and I'm back at my original post results. Tried thunderbird in Terminal and results in nice nothing new cmd line.
BTW, I have the same setup +OS on a desktop and it works fine. I'm ready to just quit stepping on my pvt-parts and say uncle since TB isn't the only email client.
Thanks for your time; Don

if you uninstall thunderbird-mozilla-build package, can you look and see if anything remains in /opt/thunderbird?

---

### Post by kelmark2180 on 2010-09-15
> **nanotube said:**
> if you uninstall thunderbird-mozilla-build package, can you look and see if anything remains in /opt/thunderbird?

There are allot of files there: 
donald@donald-toughbook:~$ locate /opt/thunderbird
/opt/thunderbird (#24 -/opt/thunderbird/README.txt to #72 /opt/thunderbird/updates
#73 /opt/thunderbird/components/FeedProcessor.js to #281 /opt/thunderbird/components/zipwriter.xpt
#284 /opt/thunderbird/modules/DownloadLastDir.jsm to #313 /opt/thunderbird/modules/virtualFolderWrapper.js
#314 /opt/thunderbird/res/EditorOverride.css to #335 /opt/thunderbird/res/svg.css

Can I just delete some directory and clean all of TB and try a reinstall? I really don't care about recovery of mail.

---

### Post by kelmark2180 on 2010-09-15
Sorry, I did do the remove
donald@donald-toughbook:~$ sudo apt-get remove thunderbird-mozilla-build
[sudo] password for donald: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  thunderbird-mozilla-build
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 261882 files and directories currently installed.)
Removing thunderbird-mozilla-build ...
Removing `diversion of /usr/bin/thunderbird
to /usr/bin/thunderbird.ubuntu by thunderbird-mozilla-build'
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
donald@donald-toughbook:~$ locate /opt/thunderbird
/opt/thunderbird
/opt/thunderbird/README.txt

---

### Post by nanotube on 2010-09-16
Hm first, try looking at what is actually being executed when you run 'thunderbird'. use command 'which thunderbird' to see the full path. ls -al on that, and see if it's a symlink to somewhere, if so, ls -al the target of the symlink, etc, until you come to the final target. (just to see if maybe you're trying to execute some random tbird install rather than the mozilla-build package one)

Further... if you don't care about recovery of mail, try 1. uninstalling the thunderbird-mozilla-build package, 2. deleting /opt/thunderbird 3. deleting (or backing up) any directories in your home dir that look like .thunderbird or .mozilla-thunderbird. 4. try installing thunderbird-mozilla-build again.

if that doesn't do it, i don't know what will.

---

### Post by kelmark2180 on 2010-09-16
> **nanotube said:**
> Hm first, try looking at what is actually being executed when you run 'thunderbird'. use command 'which thunderbird' to see the full path. ls -al on that, and see if it's a symlink to somewhere, if so, ls -al the target of the symlink, etc, until you come to the final target. (just to see if maybe you're trying to execute some random tbird install rather than the mozilla-build package one)

Further... if you don't care about recovery of mail, try 1. uninstalling the thunderbird-mozilla-build package, 2. deleting /opt/thunderbird 3. deleting (or backing up) any directories in your home dir that look like .thunderbird or .mozilla-thunderbird. 4. try installing thunderbird-mozilla-build again.

if that doesn't do it, i don't know what will.

I did the build uninstall, removed the /opt/thunderbird and home TB directories reinstalled the build and everything works great!
I did not find an symlink, but I did find some old thunderbird dir's which I removed before the mozilla build again. Maybe that was my problem? I did learn something about which cmd and others.

I certainly do appreciate your time and effort to get be back to running TB again. It's support like you have given me that makes Ubuntu great! I award you 15 atta-boys. The old mail folder in your prior instructions is still there. I suppose I could try a magic finger trick to recover, but it is of no consequence. My magic fingers went South long ago, anyway.
Thanks again;
Don

---

### Post by nanotube on 2010-09-16
> **kelmark2180 said:**
> I did the build uninstall, removed the /opt/thunderbird and home TB directories reinstalled the build and everything works great!
I did not find an symlink, but I did find some old thunderbird dir's which I removed before the mozilla build again. Maybe that was my problem? I did learn something about which cmd and others.


Excellent news! ;)

> 
I certainly do appreciate your time and effort to get be back to running TB again. It's support like you have given me that makes Ubuntu great! I award you 15 atta-boys.


thank you very much :)

> 
 The old mail folder in your prior instructions is still there. I suppose I could try a magic finger trick to recover, but it is of no consequence. My magic fingers went South long ago, anyway.
Thanks again;
Don

well, just for kicks, you could try to quit tb, copy the 'Mail' directory out of your backup to your fresh profile, and restart tb, and see if your mail magically reappears. (worst thing that can happen is that it won't work and tb will stop starting again, and you can just delete the profile once more). but it's up to you if you want to try it. if you're fine as is, then don't worry about it. :)

---

