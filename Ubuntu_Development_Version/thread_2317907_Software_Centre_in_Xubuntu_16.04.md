---
title: "Software Centre in Xubuntu 16.04"
date: 2016-03-21
forum: Ubuntu Development Version
---

### Post by Crimple on 2016-03-21
Hi.
I know that Ubuntu is going to use Gnome Software but will that be the case with other DEs ?
Ubuntu Mate is going its own way with the Welcome/Software Boutique tool, But what about Xubuntu? At the moment I'm installing through good ol' Software Centre; will it be replaced with Gnome from here to final release?

Thanks.

---

### Post by slickymaster on 2016-03-21
> **zemartins said:**
> Hi.
I know that Ubuntu is going to use Gnome Software but will that be the case with other DEs ?
Ubuntu Mate is going its own way with the Welcome/Software Boutique tool, But what about Xubuntu? At the moment I'm installing through good ol' Software Centre; will it be replaced with Gnome from here to final release?

Thanks.
Yes, it will. See [http://ubottu.com/meetingology/logs/xubuntu-devel/2016/xubuntu-devel.2016-02-17-22.00.log.html](http://ubottu.com/meetingology/logs/xubuntu-devel/2016/xubuntu-devel.2016-02-17-22.00.log.html) and [http://ubottu.com/meetingology/logs/xubuntu-devel/2016/xubuntu-devel.2016-03-18-18.01.log.html](http://ubottu.com/meetingology/logs/xubuntu-devel/2016/xubuntu-devel.2016-03-18-18.01.log.html)

---

### Post by Crimple on 2016-03-21
Many thanks.

---

### Post by Cavsfan on 2016-03-21
I figured I'd put this here as it seems to pertain to the topic.
I have Xubuntu 16.04 installed and looked on the new daily ISO manifest and did not see Ubuntu Software Centre.
```
cavsfan@cavsfan-le-beast:~$ apt-cache policy software-center
software-center:
  Installed: 16.01+16.04.20160217
  Candidate: 16.01+16.04.20160217
  Version table:
 *** 16.01+16.04.20160217 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe i386 Packages
        100 /var/lib/dpkg/status
```

So I purged it and installed Gnome Software:
```
cavsfan@cavsfan-le-beast:~$ sudo apt-get install gnome-software
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  appstream gnome-desktop3-data gnome-software-common hwdata libappstream-glib8 libappstream3 libgcab-1.0-0 libgnome-desktop-3-12
  libgtkspell3-3-0
The following NEW packages will be installed:
  appstream gnome-desktop3-data gnome-software gnome-software-common hwdata libappstream-glib8 libappstream3 libgcab-1.0-0
  libgnome-desktop-3-12 libgtkspell3-3-0
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,909 kB of archives.
After this operation, 5,799 kB of additional disk space will be used.
Do you want to continue? [Y/n]
```

Then it wanted a couple extra packages related to my language. And viola I have it.
I'm going to reboot and see how it works.

---

### Post by slickymaster on 2016-03-21
> **Cavsfan said:**
> I figured I'd put this here as it seems to pertain to the topic.
I have Xubuntu 16.04 installed and looked on the new daily ISO manifest and did not see Ubuntu Software Centre.
```
cavsfan@cavsfan-le-beast:~$ apt-cache policy software-center
software-center:
  Installed: 16.01+16.04.20160217
  Candidate: 16.01+16.04.20160217
  Version table:
 *** 16.01+16.04.20160217 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe i386 Packages
        100 /var/lib/dpkg/status
```

So I purged it and installed Gnome Software:
```
cavsfan@cavsfan-le-beast:~$ sudo apt-get install gnome-software
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  appstream gnome-desktop3-data gnome-software-common hwdata libappstream-glib8 libappstream3 libgcab-1.0-0 libgnome-desktop-3-12
  libgtkspell3-3-0
The following NEW packages will be installed:
  appstream gnome-desktop3-data gnome-software gnome-software-common hwdata libappstream-glib8 libappstream3 libgcab-1.0-0
  libgnome-desktop-3-12 libgtkspell3-3-0
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,909 kB of archives.
After this operation, 5,799 kB of additional disk space will be used.
Do you want to continue? [Y/n]
```

Then it wanted a couple extra packages related to my language. And viola I have it.
I'm going to reboot and see how it works.
The fact that you needed to install GS is extremely odd, because it has been being shipped since the beginning of March.
This is from [today's ISO]("http://cdimage.ubuntu.com/xubuntu/daily-live/20160321/xenial-desktop-amd64.manifest")```
gnome-software	3.19.93~git20160318.55deb24-0ubuntu1
gnome-software-common	3.19.93~git20160318.55deb24-0ubuntu1
```

---

### Post by Cavsfan on 2016-03-21
> **slickymaster said:**
> The fact that you needed to install GS is extremely odd, because it has been being shipped since the beginning of March.
This is from [today's ISO]("http://cdimage.ubuntu.com/xubuntu/daily-live/20160321/xenial-desktop-amd64.manifest")```
gnome-software    3.19.93~git20160318.55deb24-0ubuntu1
gnome-software-common    3.19.93~git20160318.55deb24-0ubuntu1
```

I haven't done a clean install, this is formerly 15.10 Xubuntu.
I seen that in the manifest and that's why I thought I would go for it.
I had to enable proposed to get the rest of it. But, I did not install the 4.4.0-15-generic kernel though.

However it does not appear in any of my menus probably Settings is where it should be.
I see it in the Menu Editor at the very bottom but cannot figure out how to get it up to Settings.

---

### Post by slickymaster on 2016-03-21
> **Cavsfan said:**
> I haven't done a clean install, this is formerly 15.10 Xubuntu.
I seen that in the manifest and that's why I thought I would go for it.
I had to enable proposed to get the rest of it. But, I did not install the 4.4.0-15-generic though.

However it does not appear in any of my menus probably Settings is where it should be.
I see it in the Menu Editor at the very bottom but cannot figure out how to get it up to Settings.

In a vanilla install it will just be listed in the whiskermenu main menu browser. If you want it to also be displayed in the Settings category you'll have to edit its entry and add a new category for it.

---

### Post by Cavsfan on 2016-03-21
After another reboot I was however able to add it to Cairo Dock but the icon was just a blue circle with a question mark.
So I pointed it to /usr/share/icons/buuf3.10/miscellaneous/128x128/apps/softwarecenter.png and it looks like the old Ubuntu Software Center icon but it was created on 3/1/16.

I guess that'll work until it updates more perhaps...

---

### Post by Cavsfan on 2016-03-21
> **slickymaster said:**
> In a vanilla install it will just be listed in the whiskermenu main menu browser. If you want it to also be displayed in the Settings category you'll have to edit its entry and add a new category for it.

Thanks, I'll work on that. :)

---

### Post by Cavsfan on 2016-03-21
I was able to get it into the Settings section just with the arrow at the bottom in Menu Editor:

[ATTACH=CONFIG]267918[/ATTACH]

For the Cairo Dock icon I noticed the name of it was **org.gnome.Software** so I found it here **/usr/share/icons/hicolor/256x256/apps/org.gnome.Software.png**.

[[IMG]http://en.zimagez.com/miniature/screenshot2016-03-2115-10-43.png[/IMG]]("http://en.zimagez.com/zimage/screenshot2016-03-2115-10-43.php")

Mission accomplished. :popcorn:

---

### Post by slickymaster on 2016-03-21
> **Cavsfan said:**
> I was able to get it into the Settings section just with the arrow at the bottom in Menu Editor:

[ATTACH=CONFIG]267918[/ATTACH]<---snip--->
Mission accomplished. :popcorn:

Yeah, that's another way of doing it. :P

Glad you got it fixed.

---

### Post by Cavsfan on 2016-03-22
> **slickymaster said:**
> Yeah, that's another way of doing it. :P

Glad you got it fixed.

Thank you!
I love a good challenge anymore. :P

With the exception of keeping the terminal open and removing the folders that were not empty when the software-center was purged, it went pretty well.
I did find and delete /usr/share/software-center and I doubt the other couple were of any size or relevance. It just got to me when I closed that terminal without first cleaning up.
C'est la vie.

---

### Post by brashley46 on 2016-04-21
Just updated to xubuntu 16.04 today from xubuntu 15.10; still ubuntu software centre, no gnome. What happened, and when will it upgrade?

---

### Post by brashley46 on 2016-04-21
Actually, it is installed; it was hard to fine in the whisker menu. Sorry.

---

### Post by brashley46 on 2016-06-05
And as it turns out the old ubuntu software centre, even unsupported, is still faster in my Xubuntu install than Gnome-software. Shrug.

---

### Post by coffeecat on 2016-06-05
16.04 no longer in development - thread closed.

---

