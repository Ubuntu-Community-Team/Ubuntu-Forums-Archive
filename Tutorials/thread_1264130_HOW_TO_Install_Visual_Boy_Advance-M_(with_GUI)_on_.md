---
title: "HOW TO: Install Visual Boy Advance-M (with GUI) on i386 and 64-bit versions of Ubuntu"
date: 2009-09-11
forum: Tutorials
---

### Post by Mike_IronFist on 2009-09-11
*Notice: This howto makes use of the awesome app getlibs, which is bundled in the download provided for this post. For more info, go here:**[[[http://ubuntuforums.org/showthread.php?t=474790]("http://ubuntuforums.org/showthread.php?t=474790")]]***
**_Introduction_**
Visual Boy Advance (A gameboy advance emulator) in the Ubuntu repos, even when installing the GUI versions from Synaptic Package managers, is old and leaves a lot to be desired. Needless to say, if you enjoyed VBA on Windows and want the same experience on Ubuntu, like several Windows-to-Linux ports (and vice versa) it sometimes requires an annoying bit of know-how. Well no longer!

This tutorial will show you how to get the best possible VBA setup on Ubuntu, regardless of whether or not you use the i386 (32-bit) or Intel/AMD64 (64-bit) version.

**_Getting the stuff you need_**
The version of Visual Boy Advance supplied with this howto is called VBA-M. The "M" stands for "merger", as in VBA-M is a merger of most forks from the original Open Source VBA project.

In addition, a simple (but mighty) app is included in the package, known as getlibs. What getlibs does, is it installs 32-bit libraries for any program that depends on them. On a 32-bit system, this is good if the installer is missing that info (It is, in this case). On a 64-bit system, you're not gonna be able to install a 32-bit .deb file and make use of the program most of the time unless you install the 32-bit libraries, and getlibs can handle this easily as well.

So, where to get all this good stuff?
[COLOR="Navy"]**[[[CLICK HERE TO DOWNLOAD MIKE_IRONFIST'S VBA-M ALL PLATFORM INSTALLATION PACKAGE!]("http://cid-0a1b309241732506.skydrive.live.com/self.aspx/.Public/visualboyadvance-m%5E_1.8.0.877-1%5E_x86-64.tar.gz")]]**[/COLOR]

And now, onto the show!

_**32-bit (Most) Users**_
Unless you consciously chose to download and install the 64-bit version of Ubuntu, you're a 32-bit user, so follow these instructions.

1. Copy both .deb files to the desktop.

2. Double-click the getlibs deb file to install it. Follow the onscreen instructions and let it install. When it's done, close the window.

3. Double-click the Visual Boy Advance deb file to install it. Once again, follow the instructions, let it install, and when it's done, close the window.

4. Open a terminal, and in the terminal, type:
```
getlibs /usr/local/bin/gvbam
```

The terminal will list the library files that the program needs, and then ask you if you want to proceed with installing them. Of course you do, so enter in "y" (without quotes) and press enter.

Once the libraries are done installing, clicking on VBA-M (located under the "Games" section of your applications menu) should launch the application with no problems! Enjoy!

_**64-bit Users**_
If you installed the 64-bit version of Ubuntu, you might be in a bit of a pickle with installing 32-bit applications. However, if you follow these instructions, and you're not afraid to copy-paste some commands into the terminal, you'll be on your way to using VBA-M in no time.

1. Copy both .deb files to the desktop.

2. Double-click the getlibs deb file to install it. Follow the onscreen instructions and let it install. When it's done, close the window.

3. Open a terminal and type in the following command:

```
cd ~/Desktop
```

4. Next, type (or paste) this into the terminal, carefully:

```
sudo dpkg --force-architecture -i visualboyadvance-m_1.8.0.877-1_i386.deb
```

You will be prompted for your password. Remember that the terminal doesn't show your password as you type - just enter in the password correctly and press enter.

5. Lastly, type this into the terminal:

```
getlibs /usr/local/bin/gvbam
```

The terminal will list the library files that the program needs, and then ask you if you want to proceed with installing them. Of course you do, so enter in "y" (without quotes) and press enter.

Once the libraries are done installing, clicking on VBA-M (located under the "Games" section of your applications menu) should launch the application with no problems! Enjoy!

**_Enjoy VBA-M!_**
I hope you found this installation process very easy. The main purpose of this FAQ was to help users get the most up-to-date version of VBA (while also allowing 64-bit users to make use of it). I made this FAQ in hopes that it is absolutely fool-proof, but if I made a mistake that doesn't quite make things clear, let me know and I'll be glad to clear it up for you.

---

### Post by miniyak on 2009-10-14
im using vba-m with mednafen as the frontend, is this the same set up?

---

### Post by Nevon on 2009-10-15
The .tar.gz file linked to doesn't seem to work. When I download it, it only says: "This does not look like a tar file. Skipping header." and then nothing happens.

---

### Post by Mike_IronFist on 2009-10-15
> **miniyak said:**
> im using vba-m with mednafen as the frontend, is this the same set up?

Nope, the frontend for this version of VBA-M is roughly identical to the Windows GUI.

---

### Post by Mike_IronFist on 2009-10-15
> **Nevon said:**
> The .tar.gz file linked to doesn't seem to work. When I download it, it only says: "This does not look like a tar file. Skipping header." and then nothing happens.

How are you downloading it? What browser, etc?

---

### Post by miniyak on 2009-10-20
I'd love to try it out. It seems the website thats linked to doesn't like how the file was posted. Here is what im seeing


```
XML Parsing Error: not well-formed
Location: http://cid-0a1b309241732506.skydrive.live.com/self.aspx/.Public/visualboyadvance-m%5E_1.8.0.877-1%5E_x86-64.tar.gz
Line Number 120, Column 20:for (var i = 0; i < selfPageData.items.length; i++)
-------------------^
```

---

### Post by miniyak on 2009-10-20
sorry, just my browser. Firefox must be allergic to windows live.
Chrome found it just fine

vba-m in this incarnation works great. Ive got a game working at 350% vs. 220% on the old vba with express front-end. Thanks!

I only have one issue. I can't find the option for RTC(real time clock). Is there a way to turn this on?

---

### Post by miniyak on 2009-11-26
It works at about %700 on a fresh start, but decreases to about 300 when i resume from suspend or close vba-m then restart within the same session.

An idea why?

oh, and thanks again, VBA-M works awesome beside the whole absence of RTC deally

---

### Post by Mike_IronFist on 2009-11-29
> **miniyak said:**
> It works at about %700 on a fresh start, but decreases to about 300 when i resume from suspend or close vba-m then restart within the same session.

An idea why?

oh, and thanks again, VBA-M works awesome beside the whole absence of RTC deally

Hi. Sorry for my super-late response, I really neglected maintaining this thread, huh?
I don't know why it's lacking RTC. This particular one was snagged straight from the developer's site, so it might be leaving that out for now.

---

### Post by TheFloridiot on 2010-03-17
I just installed VBA M, using your instructions here (Which, I might add, were very simple and well done!). It all installed seemingly correctly, however whenever I try to load a ROM, it just freezes. I know it's not the ROM itself, since they worked when I used VBA Express. Any idea?

---

### Post by miniyak on 2010-03-17
i know this sound windowsish... but restart, i had the same issue

if that fails reinstall vba-m (i might have.. idr)

i have this working fine in 64bit karmic except for occasional freezes

---

### Post by texantrumpeter on 2010-03-19
Could someone tell me if it is possible to install VBA on a flash drive for portable use? If so, how do I do it?

---

### Post by miniyak on 2010-03-20
never tried but, i can play stepmania from external media so i sure its possible. 

stepmania ships as a binary thats why its so easy just to drop the folder onto an external drive then run the executable file to start it (by creating a launcher)

maybe copying the folder from it location in the file system will work? (you'll need to access as root)

---

### Post by firebreather on 2010-08-03
> **miniyak said:**
> 
I only have one issue. I can't find the option for RTC(real time clock). Is there a way to turn this on?

I have the same issue. Does anyone know how to have this option, or perhaps have something separate that could act similarly?

---

### Post by maybeway36 on 2010-09-27
Regular "vbam" has a --rtc option. Maybe gvbam does too, but I haven't tried it.

---

### Post by krytorii on 2010-10-28
Sorry for replying to an old thread, but in 10.10 vba doesnt show up in the games menu, or anywhere I look. It worked in 10.4, and was the best way I found to get vba working on ubuntu.

---

### Post by Omnomnom on 2010-10-29
Great tut, :)

---

### Post by miniyak on 2010-12-08
yeah i couldn't get it to work in mavrik or lucid

and it seemed to stop working reliably in karmic

so i haven't used it in a couple of months 

any reports on the health of the project?

---

### Post by watajublá on 2011-01-20
hey, i'm kinda new here and i dont know where else to post this, so here it is. i've got one problem: ive allready installed VBA-M and i'm using  Ubuntu 10.04 LTS. When i try to open VBA-M it just doesn't open, what can i do? or what i have to do to make this work ok?? i wanna play jazz jackrabbit 1 and i've installed Wine. So i don't know what else to do... please help. Thanks!;)

---

### Post by sshh on 2011-01-22
Hi!
I know probably no one will reply, but I keep getting:

> libcairomm-1.0-1 was not found in your repositories
Make sure you have all repositories enabled and updated
libglibmm-2.4-1c2a was not found in your repositories
Make sure you have all repositories enabled and updated
libgtkmm-2.4-1c2a was not found in your repositories
Make sure you have all repositories enabled and updated
libpangomm-1.4-1 was not found in your repositories
Make sure you have all repositories enabled and updated


And VBA-M does not appear at Games. 
Any ideas?

---

### Post by mesilliac on 2011-02-15
Hi,

There seems to be a good ppa for installing VBA-M from here:

[https://launchpad.net/~hunter-kaller/+archive/ppa](https://launchpad.net/~hunter-kaller/+archive/ppa)

You should be able to install VBA-M easily by adding this ppa and installing the vbam package (it seems to be working fine for me on amd64, Ubuntu 10.10).

Running the following commands in a terminal should work
```

sudo apt-add-repository ppa:hunter-kaller/ppa
sudo apt-get update
sudo apt-get install vbam

```
The latest builds have an option to turn on the realtime clock for those who need it. It can be found under "Options > Game Boy Advance" in VBA-M.

---

### Post by sshh on 2011-02-16
Thank you! It works!

---

### Post by Erenith on 2012-02-23
I was able to install VBA-M as suggested by mesilliac.  I am also able to open the emulator itself, however when I tried to load a game in, it did not load.  Instead, whenever I tried to select the game I wanted to run, it would not get selected and it would stay on the screen to select a game to run.  I am still able to leave that screen by pressing esc, however neither the open nor cancel button seems to respond.  I tried to figure out why that might be the case however I was not able to find anyone who had a similar problem as to mine own.  I will still look around and see what I might have not done or done incorrectly though.  Any help from here would be greatly appreciated!

I am relatively new to Ubuntu and the whole Linux community so I'm pretty sure I might have botched something up.  I'm running Ubuntu 11.10 and using the Gnome Shell

EDIT:
Upon running gvbam in the terminal, it loaded fine.  However when I try to load a ROM I get this error after pressing escape from the load file screen:

```
(gvbam:4517): glibmm-CRITICAL **: 
unhandled exception (type Glib::Error) in signal handler:
domain: g-key-file-error-quark
code  : 5
what  : Key file contains key 'flashSize' in group 'AGSE' which has value that cannot be interpreted.
```

I know that there probably won't be an answer, but does anyone know what can be done?

---

### Post by ceil210 on 2012-02-28
[http://cid-0a1b309241732506.skydrive.live.com/self.aspx/.Public/visualboyadvance-m%5E_1.8.0.877-1%5E_x86-64.tar.gz]("http://cid-0a1b309241732506.skydrive.live.com/self.aspx/.Public/visualboyadvance-m%5E_1.8.0.877-1%5E_x86-64.tar.gz")

I have tried to load this in both Firefox and Chrome--neither load :(


```
agardner@ubuntu:~$ sudo apt-get install vbam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package vbam
```

---

### Post by Erenith on 2012-02-28
> **mesilliac said:**
> Hi,

There seems to be a good ppa for installing VBA-M from here:

[https://launchpad.net/~hunter-kaller/+archive/ppa]("https://launchpad.net/%7Ehunter-kaller/+archive/ppa")

You should be able to install VBA-M easily by adding this ppa and installing the vbam package (it seems to be working fine for me on amd64, Ubuntu 10.10).

Running the following commands in a terminal should work
```

sudo apt-add-repository ppa:hunter-kaller/ppa
sudo apt-get update
sudo apt-get install vbam

```The latest builds have an option to turn on the realtime clock for those who need it. It can be found under "Options > Game Boy Advance" in VBA-M.

Try doing that ceil210.  The link you posted has not been working for sometime.  What I quoted seemed to work well enough for me and most of the ROMs that I run work.

---

### Post by Erenith on 2012-03-08
> **Erenith said:**
> I was able to install VBA-M as suggested by mesilliac.  I am also able to open the emulator itself, however when I tried to load a game in, it did not load.  Instead, whenever I tried to select the game I wanted to run, it would not get selected and it would stay on the screen to select a game to run.  I am still able to leave that screen by pressing esc, however neither the open nor cancel button seems to respond.  I tried to figure out why that might be the case however I was not able to find anyone who had a similar problem as to mine own.  I will still look around and see what I might have not done or done incorrectly though.  Any help from here would be greatly appreciated!

I am relatively new to Ubuntu and the whole Linux community so I'm pretty sure I might have botched something up.  I'm running Ubuntu 11.10 and using the Gnome Shell

EDIT:
Upon running gvbam in the terminal, it loaded fine.  However when I try to load a ROM I get this error after pressing escape from the load file screen:

```
(gvbam:4517): glibmm-CRITICAL **: 
unhandled exception (type Glib::Error) in signal handler:
domain: g-key-file-error-quark
code  : 5
what  : Key file contains key 'flashSize' in group 'AGSE' which has value that cannot be interpreted.
```I know that there probably won't be an answer, but does anyone know what can be done?

 I figured out the problem as to that error that I had earlier.  If there are others that had a similar error, then consult this page: [http://sourceforge.net/tracker/?func=detail&aid=3201910&group_id=212795&atid=1023154](http://sourceforge.net/tracker/?func=detail&aid=3201910&group_id=212795&atid=1023154)  However, I now have a different problem: I had to reinstall ubuntu due to hard drive failure and when i reinstalled VBA-M using the PPA above, I was given this error when I ran it from terminal:  ```
terminate called after throwing an instance of 'Glib::FileError' Aborted 
```  Does anyone what could be done?  I have looked around and didn't really understand too well the source of the error since I am still new to all of this.  Thank you to anyone who answers ------------------------------------- Edit ------------------------------------- I just ended up not using that ppa and instead I downloaded the latest .deb for the VBAM.  I surfed around the forums and found a link where you could download the latest .deb for VBAM.  I'll post the link here for people who would like to use that if they are not able to get the PPA to work for them: [http://sourceforge.net/projects/vbam/files/](http://sourceforge.net/projects/vbam/files/) Enjoy!

---

### Post by SilverSword612 on 2012-08-09
Could someone possibly re-upload this package somewhere else? I don't have a skydrive account and I don't feel like making one, especially after just having created this account. Also this is another reason why I stopped using most microsoft products and services.

---

