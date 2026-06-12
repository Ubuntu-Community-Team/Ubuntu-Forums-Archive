---
title: "ubuntu one sync takes forever"
date: 2011-03-03
forum: Ubuntu One (CLOSED)
---

### Post by selectstar on 2011-03-03
[B]I have recently decided to ditch Dropbox and to start using Ubuntu One to sync files between my computer at work and my laptop at home. I really like the features and price plan is great. Although one thing that I feel is lacking is an indicator in the tray bar.

However I am experiencing very long delays in the syncronization process.
For example today I have shared on my office desktop computer a folder of about 5 MB, it took several time before the syncronization process ended (probably around 30 - 60 minutes). Once I came back home I have switched on my laptop, around 1 hour has passed and still no files have been downloaded (apart from the folders structure).
Should I file a bug report?


[/B]

---

### Post by selectstar on 2011-03-08
16 minutes to upload a folder containing 23 MB and around 300 files
I don't think this is acceptable.
My connection is average with tested speeds of 5 MB download and 4 MB in upload.

---

### Post by selectstar on 2011-03-08
I forgot to mention that although all files are successfully uploaded (proof of this logging in the web interface where the new folders and files are reported) the message "syncronization in progress" is still displayed in the Ubuntu One preferences window.

---

### Post by duanedesign on 2011-03-14
The older versions of Ubuntu One definetly did not upload metadata as fast as we all would have liked. The problem is the number of files, not necessarily the size. So lots of small files would take longer than one file of the same size. They have been working on this and each release sees improvements. The version in Natty has made a big improvement. You can install this version on older releases by adding the Ubuntu One nightlies repository.
```

sudo add-apt repository ppa:ubuntuone/nightlies

sudo apt-get update

sudo apt-get upgrade; sudo apt-get install ubuntuone-control-panel ubuntuone-control-panel-gtk
```

There is [a sticky]("http://ubuntuforums.org/showthread.php?t=1594301") about how to get more information about how many files have synced and how many are left. For example this command will tell you the number of files in each queue (there is a metadata and content queue).

```
u1sdtool --waiting-metadata | wc -l

u1sdtool --waiting-content | wc -l
```

---

### Post by selectstar on 2011-03-14
Thanks for the reply, I tried upgrading the client version hoping it would solve the problem.
Unfortunately now the client has completely stopped to work.

After the upgrade the client wasn't opening (either from the System > Preferences > Ubuntuone or directly from the Me menu)

I have therefore tried to uninstall the whole thing and reinstall it according to instructions in this FAQ
[https://wiki.ubuntu.com/UbuntuOne/FAQ/HowDoICompletelyRemoveAndReinstallUbuntuOne](https://wiki.ubuntu.com/UbuntuOne/FAQ/HowDoICompletelyRemoveAndReinstallUbuntuOne)

At the moment Ubuntu One does not appear in Me menu nor in the System > Preferences menu and I am unable to sync

---

### Post by duanedesign on 2011-03-14
ok. There were some new packages added. Must need to add them. Apparently they are not getting pulled in with just an update/upgrade.

```
sudo apt-get install ubuntuone-control-panel
```

Also what release are you running?

---

### Post by selectstar on 2011-03-14
I have to rectify my last post. Ubuntu One seems to be running perhaps with some issues?.
Actually I must say that it looks awesome! I really like the new menu when right clicking on a folder and the "add computer / login" screen.

Right clicking on a folder is the only feedback that I get that let's me see that the client is installed. I don't get the button in Me menu nor in System > Preferences 


My system is 10.04 LTS 64 bit

---

### Post by selectstar on 2011-03-14
I am getting this error:
E: Couldn't find package ubuntuone-control-panel

---

### Post by duanedesign on 2011-03-14
I did not realize this earlier, but not all the packages have been built yet for Lucid. So the preferences panel package is probably not yet available. You can control Ubuntu One from the command line.

to connect
```
u1sdtool -c
```

to quit
```
u1sdtool -q
```

number of items items in the metadata/content queue
```
u1sdtool --waiting | wc -l
```

you can find more options with
```
man u1sdtool
```

To get a GUI you can try Magicicada. It is a project by one of the Ubuntu One developers.

```
sudo add-apt-repository ppa:chicharreros/ppa

sudo apt-get update; sudo apt-get install magicicada 
```

---

### Post by selectstar on 2011-03-14
I think I will just wait for Ubuntu 11
thanks

---

