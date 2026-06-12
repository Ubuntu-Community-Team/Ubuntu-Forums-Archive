---
title: "HOWTO: Install LDOCE5 on Ubuntu 64-bit"
date: 2010-01-22
forum: Tutorials
---

### Post by eltama on 2010-01-22
After spending some time I managed to install the Longman Dictionary of Contemporary English 5th edition (LDOCE5) on Ubuntu 9.10 (Karmic Koala) 64-bit and I want to share my experience.

On the cd there is a file LINUX_README.txt which says that if you want to launch the installer in graphical mode you have to install libgtk1.2. libgtk1.2 is not available in Karmic (see [https://bugs.launchpad.net/ubuntu/+source/gtk+1.2/+bug/478219](https://bugs.launchpad.net/ubuntu/+source/gtk+1.2/+bug/478219)) and although there are ways to install it (e.g. [http://www.rabbnix.com/vb/showthread.php?t=979](http://www.rabbnix.com/vb/showthread.php?t=979)), it is easier to install it from the console.

According to [http://pearsonsupport.helpserve.com/index.php?_m=knowledgebase&_a=viewarticle&kbarticleid=115](http://pearsonsupport.helpserve.com/index.php?_m=knowledgebase&_a=viewarticle&kbarticleid=115), LDOCE5 should work on Ubuntu 9.04+ on both architectures. However, when I tried to run linux/setup.sh, I got following error:
> The setup program seems to have failed on amd64/glibc-2.1

Fatal error, no tech support email configured in this setup
After investigating the script setup.sh I noticed that it determines the architecture (amd64 or x86), and it uses that value to construct a path to the actual installer, e.g. linux/setup.data/bin/Linux/x86/setup. However, there is no linux/setup.data/bin/Linux/amd64/ directory.

**UPDATE**: I found an easier way to make the installer work than the one described on the next paragraph. Just run from the linux directory ```
linux32 ./setup.sh
```

Since I had nothing to lose, I though about executing the installer for the x86 version. So I copied the whole cd to the hard disk, and renamed ldoce5/linux/setup.data/bin/Linux/x86/ to ldoce5/linux/setup.data/bin/Linux/amd64/. Then I ran ldoce5/linux/setup.sh (after adding execute permission to setup.sh). A terminal-based installer launched with the message "You are running an x86 machine with glibc-2.1", I pressed OK, then I agreed with the licence and chose the instalation directory. Then the installer did it's work.

I went to the directory where it installed the dictionary and with my fingers crossed I run ldoce5. To my surprise it worked!

Most things work fine: sounds, links, nice fonts. The only problem I found is that on the "Teacher Resouces" section, the links to the pdfs do not work, however, they can be directly accessed in ldoce5/chrome/ldoce5/pdfs.

**UPDATE 2**:
.It also works on Ubuntu 10.04 and 10.10.

.You need the Adobe Flash Plugin, otherwise sound will not work. It's also recommended to have Pulse Audio.

.If you want to back it up, besides the installation directory backup the .font directory (optional), and the file ~/.macromedia/Flash_Player/#Security/FlashPlayerTrust/ldoce5.cfg, which only contains the path to the ldoce5 installation, for instance, /usr/share/ldoce5/. If you don't have this file you will be able to open the program but when you click on the main menu nothing will happen. You can create it yourself if you don't have it.

.This made me realize that to if you want to execute through wine a version that has been installed in Windows, all you need to do is add the executable to the allowed applications on wine's flash. The result is not the same, it flickers more, but you can save 2.5 GB of space.

**UPDATE 3**:
The Copy button at the top does not work, neither does Ctrl-c. To copy some text, select it and press Ctrl-Insert.

---

### Post by pietro-23 on 2010-02-21
Hi, thank you for sharing your experience,  I ve been looking for solutions to install LDOCE on ubuntu 9.10, now it seems i have found it.
Can you please explain in an easier way how to make it run? 
thank you

---

### Post by ngohaibac on 2010-03-10
Hi eltama,

Thank you very much for your sharing. I think it is very easy to understand pietro-23. Just try to open setup.sh and see

```
vi ./linux/setup.sh
```

Best regards,

---

### Post by liedan on 2010-04-08
Hi Eltama,

thanks you very much, your post was extremely helpful for me. I also have Ubuntu Karmic 64bit. However, I have LDOCE4_2 , so I had to modify your solution a little. 
I posted detailed description here : [http://ubuntuforums.org/showthread.php?p=9094386#post9094386](http://ubuntuforums.org/showthread.php?p=9094386#post9094386)

Cheers

---

### Post by eltama on 2010-05-17
I'm happy to see that it's been helpful. Sorry for not replying, I forgot to subscribe to this thread, but I've done it now.

---

### Post by susiriss on 2010-06-06
This is a really cool hack. I used it for Oxford ALD and it works. ;-)
Was thinking of installing gtk1.2 and stuff, and then found this thread.

thanks eltama  !!!

---

### Post by eltama on 2010-06-06
> **susiriss said:**
> This is a really cool hack. I used it for Oxford ALD and it works. ;-)
Was thinking of installing gtk1.2 and stuff, and then found this thread.

thanks eltama  !!!

My pleasure!

---

### Post by IronLeo on 2010-06-08
I have Ubuntu 10.04 X86 64-bit and I managed to install LDOCE5 but the sounds do not work! Any idea? :-(

---

### Post by eltama on 2010-06-08
> **IronLeo said:**
> I have Ubuntu 10.04 X86 64-bit and I managed to install LDOCE5 but the sounds do not work! Any idea? :-(

Are you sure everything was installed correctly? A full installation is about 2.4 GB.
Does the sound work fine on all other applications?
LDOCE uses flash, do you have the Adobe Flash Plugin for 64 bit?

---

### Post by IronLeo on 2010-06-09
> **eltama said:**
> Are you sure everything was installed correctly? A full installation is about 2.4 GB.
Does the sound work fine on all other applications?
LDOCE uses flash, do you have the Adobe Flash Plugin for 64 bit?

I did not have the Flash Plugin!! Now it works!! Great! Thanks!! ;-)

---

### Post by eltama on 2010-06-09
> **IronLeo said:**
> I did not have the Flash Plugin!! Now it works!! Great! Thanks!! ;-)

Great!

---

### Post by Tung on 2010-11-10
Thanks for the tutorial, I managed to install the dictionary successfully and sound worked. But on the second day, sound didn't work anymore. I have adobe flash installed. Do you have any clue ?

Thanks !

---

### Post by eltama on 2010-11-14
> **Tung said:**
> Thanks for the tutorial, I managed to install the dictionary successfully and sound worked. But on the second day, sound didn't work anymore. I have adobe flash installed. Do you have any clue ?

Thanks !

No sorry, I don't know what the problem could be.
The only problem with sound I heard about was related to flash.

Let me know if you find the problem.

---

### Post by Tung on 2010-11-14
Do you know where does LDOCE5 look for the flash library. I have downloaded the lastest flash 64 bit from [Adobe]("http://labs.adobe.com/downloads/flashplayer10.html") and replaced it with the default one used by firefox and chrome. Afterwards, sound worked again in LDOCE5, but just few hours later, it didn't work anymore, I have not even restarted the machine.

It's really weird to me ... So I think I need a way to tell LDOCE5 explicitly where I should look for the flash library ....

---

### Post by Tung on 2010-11-14
Hi, 

I FOUND the solution. It was Google Chrome that somehow make the flash in LDOCE5 malfunctions. As soon as I start Google Chrome, sound doesn't work in LDOCE5 anymore, but before that it worked fine ! 

So I removed Google Chrome, and installed Chromium instead, sound works now perfectly !

---

### Post by eltama on 2010-11-14
Thanks for your tip!
I have both chrome and chromium but I've never experienced any problem with sound.

---

### Post by Tung on 2010-11-14
I have to correct the statement. It was actually because of the flashblock extension I used in Chrome and not Chrome itself :)

---

### Post by eltama on 2010-11-15
> **Tung said:**
> I have to correct the statement. It was actually because of the flashblock extension I used in Chrome and not Chrome itself :)

That makes more sense. Thanks again!

---

### Post by ngadung on 2010-12-10
I'm the newbe, i've just install ubuntu 10.10 a few days ago, I try to install Longman dictionary LEOCD 5 ( I copied the disk in to the computer) but i can't not install, could please show me in detail how to install it. Thanks alot

---

### Post by Tung on 2010-12-11
What kind of error message do you have ? Try read the tutorial by eltama thoroughly, everything is written there, and you also don't need to copy the disk into your hard drive.

---

### Post by eltama on 2010-12-12
> **ngadung said:**
> I'm the newbe, i've just install ubuntu 10.10 a few days ago, I try to install Longman dictionary LEOCD 5 ( I copied the disk in to the computer) but i can't not install, could please show me in detail how to install it. Thanks alot

I will try to be more detailed, let me know if you get stuck at some point.

1. Open a terminal (Applications -> Accessory -> Terminal)

2. On the terminal change the directory to the place where you have copied the CD. For instance if you copied it in your home directory and it's called LDOCE5 the you have to do
```
cd LDOCE5
```

3. Go to the linux subdirectory
```
cd linux
```

4. Then execute the installer
```
linux32 ./setup.sh
```

---

### Post by ngadung on 2010-12-30
I have LDOCE5 in iso file. I mounted this file.

In the When i click on : Places/ Computer

I see the disk LDOCE5,  I tried with the command  cd LDOCE5 and cd /Computer/LDOCE5
I got the notice: " no such file or directory"
Please tell me what is my problem. Thanks a lot

---

### Post by eltama on 2010-12-31
> **ngadung said:**
> I have LDOCE5 in iso file. I mounted this file.

In the When i click on : Places/ Computer

I see the disk LDOCE5,  I tried with the command  cd LDOCE5 and cd /Computer/LDOCE5
I got the notice: " no such file or directory"
Please tell me what is my problem. Thanks a lot

How did you mount the iso?
Can you see it on Nautilus (the file manager)?
You just have to navigate to the linux directory of the CD and execute setup.sh, but if you have a 64bit OS you have to do it from the command line with linux32 ./setup.sh

I also have it on an iso. This is what I do.

1. Open a terminal: Applications -> Accessories -> Terminal (on Ubuntu since 10.04 the shortcut is ctrl-alt-T).

2. Mount the iso
a. Create the directory where you will mount it if you didn't before. In the terminal execute:
```
cd /media
sudo mkdir iso
```
b. Mount the LDOCE iso
```
sudo mount -t iso9660 -o loop <path_to_LDOCE.iso> /media/iso
```
You have to replace <path_to_LDOCE.iso> with the actual path to where you have the LDOCE iso.

3. Navigate to the linux directory of the iso:
```
 cd /media/iso/linux
```

4. 4. Then execute the installer
```
linux32 ./setup.sh
```

Note: Unlike in Windows, it will not check that you have original CD. That's great because I don't need to have the CD around. It's also easier to install illegal copies, but let's not get there :)

5. Once you have installed it, you can unmount the CD:
a. First get out of the iso directory
```
cd /media
```
b. Then unmount it
```
sudo umount iso
```

If the command line is still difficult to you, try this:

1. Install the package nautilus-open-terminal. You can use the Ubuntu Software Center, Synaptic or even simpler, the terminal :)
```
sudo apt-get install nautilus-open-terminal
```

2. Mount it like you did before or as I just explained.
On Nautilus there is an option "Open with Archive Mounter", but for me it doesn't work.

3. Using Nautilus navigate to the contents of the iso. If you mounted as I told you, you will see a new entry called iso under Devices on the left panel. Click on it.

4. Enter the linux directory. Once there right click (but not over a file) to show the context menu and choose Open in Terminal.

5. Then execute ```
linux32 ./setup.sh
```

I hope this time you succeed, good luck!

---

### Post by ngadung on 2010-12-31
Great, it worked. I'm so happy about this. Thank you so much.
Happy new year:guitar::guitar::p

---

### Post by eltama on 2010-12-31
> **ngadung said:**
> Great, it worked. I'm so happy about this. Thank you so much.
Happy new year:guitar::guitar::p

Great! Happy new year :popcorn:

---

### Post by terrywang on 2011-02-22
Thank you for the post.

Recently I got a new Dell Latitude E6410 and installed Ubuntu 10.10 x86_64. After data migration (easy shot using tar & netcat & untar ^^), I found the LDOCE5 setup script doesn't work on 64-bit Linux due to the same error.

Your tip really helped to work around the issue;-)

I just copied the linux and ldoce5.data folder to the HDD and renamed the ldoce5/linux/setup.data/bin/x86 to amd64 and it worked.

I've been stuck with uninstalling ldoce5 on one of my arch linux installation with error "Could not find a usable uninstall program. Aborting." I did something similar, looked into the uninstall scripts in the installation folder and was able to manually uninstall completely.

It's the same path construction problem.

```
if which loki-uninstall 2> /dev/null > /dev/null || type -p loki-uninstall 2> /dev/null > /dev/null; then
UNINSTALL=loki-uninstall
else
UNINSTALL="$HOME/.loki/installed/bin/`DetectOS`/`DetectARCH`/uninstall"
if test ! -x "$UNINSTALL" ; then
echo Could not find a usable uninstall program. Aborting.
exit 1
fi
fi
"$UNINSTALL" -L ldoce5 "/usr/local/ldoce5/.manifest/ldoce5.xml" "$1"
```

This /usr/local/ldoce5/.manifest/scripts/preun.sh can be used as reference to manually uninstall ldoce5.

I have to say LDOCE5 rocks, works perfectly on all OS (Mac, Linux and Windows), unified UI (thanks to Mozilla framework). But some minor issues with their scripts LOL

---

### Post by eltama on 2011-02-22
> **terrywang said:**
> Thank you for the post.

Recently I got a new Dell Latitude E6410 and installed Ubuntu 10.10 x86_64. After data migration (easy shot using tar & netcat & untar ^^), I found the LDOCE5 setup script doesn't work on 64-bit Linux due to the same error.

Your tip really helped to work around the issue;-)

I just copied the linux and ldoce5.data folder to the HDD and renamed the ldoce5/linux/setup.data/bin/x86 to amd64 and it worked.

I've been stuck with uninstalling ldoce5 on one of my arch linux installation with error "Could not find a usable uninstall program. Aborting." I did something similar, looked into the uninstall scripts in the installation folder and was able to manually uninstall completely.

It's the same path construction problem.

```
if which loki-uninstall 2> /dev/null > /dev/null || type -p loki-uninstall 2> /dev/null > /dev/null; then
UNINSTALL=loki-uninstall
else
UNINSTALL="$HOME/.loki/installed/bin/`DetectOS`/`DetectARCH`/uninstall"
if test ! -x "$UNINSTALL" ; then
echo Could not find a usable uninstall program. Aborting.
exit 1
fi
fi
"$UNINSTALL" -L ldoce5 "/usr/local/ldoce5/.manifest/ldoce5.xml" "$1"
```

This /usr/local/ldoce5/.manifest/scripts/preun.sh can be used as reference to manually uninstall ldoce5.

I have to say LDOCE5 rocks, works perfectly on all OS (Mac, Linux and Windows), unified UI (thanks to Mozilla framework). But some minor issues with their scripts LOL

Thanks for your tip!

---

### Post by terrywang on 2011-02-22
BTW: I have to manually mount the LDOCE5 DVD, it won't mount automatically like other CD/DVDs, not sure why.

```
mount -t iso9660 /dev/dvd /media/cdrom
```

Anyway manual labor works. In case other Ubuntu dudes run into the same problem.

---

### Post by emanamini on 2011-03-19
HI
I use Archlinux 64 Bit
I want to execute it but I receive an Error like this

```
[eman@eMan-PC linux]$ linux32 ./setup.sh
./setup.sh: line 201: /home/eman/.setup15066: No such file or directory
./setup.sh: line 201: /home/eman/.setup15066: No such file or directory
The setup program seems to have failed on x86/glibc-2.1

Fatal error, no tech support email configured in this setup

```
what can I do ?

---

### Post by eltama on 2011-03-19
> **emanamini said:**
> HI
I use Archlinux 64 Bit
I want to execute it but I receive an Error like this

```
[eman@eMan-PC linux]$ linux32 ./setup.sh
./setup.sh: line 201: /home/eman/.setup15066: No such file or directory
./setup.sh: line 201: /home/eman/.setup15066: No such file or directory
The setup program seems to have failed on x86/glibc-2.1

Fatal error, no tech support email configured in this setup

```
what can I do ?

Try the other solution:
Copy the whole cd to the hard disk, and rename ldoce5/linux/setup.data/bin/Linux/x86/ to ldoce5/linux/setup.data/bin/Linux/amd64/. Then run ldoce5/linux/setup.sh (after adding execute permission to setup.sh)

---

### Post by emanamini on 2011-03-19
Thanks for respond
But this solution didn't work
I do many things to fix it but ...
you can see the out put of these comands

```
[root@eMan-PC linux]# ./setup.sh 
./setup.sh: line 201: /root/.setup2920: No such file or directory
./setup.sh: line 201: /root/.setup2920: No such file or directory
The setup program seems to have failed on amd64/glibc-2.1

Fatal error, no tech support email configured in this setup
[root@eMan-PC linux]# sudo sh setup.sh 
setup.sh: line 201: /root/.setup2951: No such file or directory
setup.sh: line 201: /root/.setup2951: No such file or directory
The setup program seems to have failed on amd64/glibc-2.1

Fatal error, no tech support email configured in this setup
[root@eMan-PC linux]# su - eman
[eman@eMan-PC ~]$ cd /home/eman/Desktop/New/linux/setup.data/bin/Linux/
[eman@eMan-PC Linux]$ sh setup.sh
sh: setup.sh: No such file or directory
[eman@eMan-PC Linux]$ ls
amd64
[eman@eMan-PC Linux]$ cd ..
[eman@eMan-PC bin]$ cd ..
[eman@eMan-PC setup.data]$ cd ..
[eman@eMan-PC linux]$ sh setup.sh 
setup.sh: line 201: /home/eman/.setup2982: No such file or directory
setup.sh: line 201: /home/eman/.setup2982: No such file or directory
The setup program seems to have failed on amd64/glibc-2.1

Fatal error, no tech support email configured in this setup
[eman@eMan-PC linux]$ ./setup.sh 
./setup.sh: line 201: /home/eman/.setup3007: No such file or directory
./setup.sh: line 201: /home/eman/.setup3007: No such file or directory
The setup program seems to have failed on amd64/glibc-2.1

Fatal error, no tech support email configured in this setup
[eman@eMan-PC linux]$ linux32 ./setup.sh 
The setup program seems to have failed on x86/glibc-2.1

Fatal error, no tech support email configured in this setup
[eman@eMan-PC linux]$
```

Many thanks my good friend

---

### Post by eltama on 2011-03-19
Try this, copy the linux/setup.data/bin/Linux/x64/setup (if you have renamed it, /x86 otherwise) to linux/ (where setup.sh is) and execute setup (not sure if as root) from there (with linux32 if you have x86).

Unfortunately, I don't have Archlinux installed so I cannot test it.

---

### Post by emanamini on 2011-03-20
Many thanks my good friend
I finally install it with adding a respo and instal a lib
but when I want to execue it I recieve this error
```
[eman@eMan-PC ldoce5]$ ./run-ldoce5.sh
./ldoce5-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
[eman@eMan-PC ldoce5]$ sudo pacman -Ss libgtk-x11
Password: 
Sorry, try again.
Password: 
[eman@eMan-PC ldoce5]$ sudo pacman -Ss libgtk
extra/libgtkhtml 2.11.1-2
    An HTML library for GTK
community/libgtksourceviewmm2 2.10.1-1
    A C++ API for gtksourceview2
[eman@eMan-PC ldoce5]$ 
```

I think there is a extra lib that I need to install but there isn't any thing that I can realiz

---

### Post by eltama on 2011-03-20
I'm happy to hear that you could install it. Indeed it seems that you need to install libgtk-x11-2.0. In Ubuntu I have
```
/usr/lib/libgtk-x11-2.0.a
/usr/lib/libgtk-x11-2.0.la
/usr/lib/libgtk-x11-2.0.so
/usr/lib/libgtk-x11-2.0.so.0
/usr/lib/libgtk-x11-2.0.so.0.2200.0
/usr/lib32/libgtk-x11-2.0.so
/usr/lib32/libgtk-x11-2.0.so.0
/usr/lib32/libgtk-x11-2.0.so.0.2200.0
```

I know nothing about Archlinux, so I cannot help you much there.

---

### Post by emanamini on 2011-03-21
Anyway thank you my good friend for your patient 
I will install Arch32 bit system early 
 thank you again

---

### Post by primejava on 2011-03-25
My computer using Ubuntu 10.10 32-bit, when I installed LDOCE5 finish, it was cannot play sound of Words and cannot download PDF in Teacher Resources. I cannot run LDOCE5 icon on the Desktop, I must type "sudo <path>/ldoce5" on Terminal it was run. I had already installed Flash Plug. I installed LDOCE5 on Terminal and completed size is 2.4G. I tried this post suggested methods, and problem still appearance. Have anyone meets this question? How to resolve it? Thanks!

---

### Post by emanamini on 2011-03-26
for sound I install pulse and manage sounds with it

---

### Post by Sef on 2011-03-26
Moved to T & T due to this thread is a HowTo.

---

### Post by eltama on 2011-03-26
> **primejava said:**
> My computer using Ubuntu 10.10 32-bit, when I installed LDOCE5 finish, it was cannot play sound of Words and cannot download PDF in Teacher Resources. I cannot run LDOCE5 icon on the Desktop, I must type "sudo <path>/ldoce5" on Terminal it was run. I had already installed Flash Plug. I installed LDOCE5 on Terminal and completed size is 2.4G. I tried this post suggested methods, and problem still appearance. Have anyone meets this question? How to resolve it? Thanks!

Good to know that sound is working.

About the PDFs, as I note in the first post, they can be directly accessed in ldoce5/chrome/ldoce5/pdfs.

Regarding the icon on the desktop, I don't know how you installed it. Check that you have the necessary rights to execute it. What is the command you have in the launcher?

---

### Post by primejava on 2011-03-26
> **eltama said:**
> Good to know that sound is working.

About the PDFs, as I note in the first post, they can be directly accessed in ldoce5/chrome/ldoce5/pdfs.

Regarding the icon on the desktop, I don't know how you installed it. Check that you have the necessary rights to execute it. What is the command you have in the launcher?
Thanks for your pay attention my question. I had run "chmod 777 -R ldoce5-directory" and "chmod 777 ldoce5.desktop" to get all rights.

---

### Post by vxthanh on 2011-04-05
Hi folks.
I use Ubuntu 10.10 32 -bit and have sound problem with Ldoce5. I have installed ldoce5 follow [http://thanhsiang.org/faqing/node/105](http://thanhsiang.org/faqing/node/105) . Namely, first I "install libgtk1.2 libxp6 alsa-oss", later I install ldoce5 into /usr/local (code: "cd ~/Documents/linux" and  "sudo sh setup.sh"). Installation is successful and I can run ldoce5 by running /usr/local/ldoce5/ldoce5. However, I can't play audio in ldoce5, both words and examples. My com has already Adobe Flash Plugin (I install flashplugin-installer 10.2.153.1 in Synaptic) and Pulseaudio.
Beside, during installation, I get the following errors: 
- Immediately after typing "sudo sh setup.sh" I see the following message on terminal:

Gtk-CRITICAL **: file gtkwidget.c: line 3310 (gtk_widget_set_sensitive): assertion `widget != NULL' failed.

Gtk-CRITICAL **: file gtkwidget.c: line 1510 (gtk_widget_hide): assertion `widget != NULL' failed.

Gtk-CRITICAL **: file gtkwidget.c: line 1510 (gtk_widget_hide): assertion `widget != NULL' failed.

Gtk-CRITICAL **: file gtkwidget.c: line 1510 (gtk_widget_hide): assertion `widget != NULL' failed.

But I still agree License Agreement to continue the installation process. 

- While Ldoce5 being installed, I see the following message on terminal: "cp: cannot stat `setup.data/AWLPhonetics3U.TTF': No such file or directory"

-Later, the installation process complement successful. I can run Ldoce5 and use all tools except can't play audio (important part of dictionary).

I expect your help.

---

### Post by eltama on 2011-04-06
@vxthanh
I don't know how you installed it following those instruction because libgtk1.2 has not been available in the repositories since 9.10 I think. The whole point of this howto is workaround that dependency.

You also installed alsa so that may have changed the audiosink.
If you want to use alsa run
```
sudo modprobe snd-pcm-oss
```

If you want to use pulseaudio try running this to set the default values for gstreamer (i.e. pulseaudio):
```
gconftool-2 --type string --set /system/gstreamer/0.10/default/audiosink "autoaudiosink"
gconftool-2 --type string --set /system/gstreamer/0.10/default/musicaudiosink "autoaudiosink"
```

---

### Post by vxthanh on 2011-04-06
Thank you **eltama**.
I have removed Ldoce5 to my com and reinstalled after run 
```
gconftool-2 --type string --set /system/gstreamer/0.10/default/audiosink "autoaudiosink"
gconftool-2 --type string --set /system/gstreamer/0.10/default/musicaudiosink "autoaudiosink"
```
by this way, I can play audio. However, "Grammar" and "Teacher Resources" do not work. With "Teacher Resources", as you say, I can access in ldoce5/chrome/ldoce5/pdfs directly. But unfortunately can not use "Grammar".
Otherwise, I can not run 
```
sudo modprobe snd-pcm-oss
```
there is a message on terminal: "FATAL: Module snd_pcm_oss not found.". Ago, I also have tried this many times but have the same problem.
Now, I am using Oald8 by I need only look up and practice pronunciation. However, if we can solve this problem completely, it will help to many people.

---

### Post by eltama on 2011-04-06
Forget the modprobe, I took it from [http://thanhsiang.org/faqing/node/105#comment-799]("http://thanhsiang.org/faqing/node/105#comment-799"), but it doesn't seem to work. Anyway it's good to know that you have audio.

It's really weird that you can access all but the grammar (and the pdfs links that do not work, but that's OK). What happens when you click on Grammar. If you run it on the console, do you get any error message?

I can only recommend you to make sure that it is properly installed, that is that there were no errors when it was installed and check that you have the directory ldoce5.data/gram.skn, which is about 58.6KB.

Also check that you have the file ~/.macromedia/Flash_Player/#Security/FlashPlayerTrust/ldoce5.cfg,whose content is the path to the ldoce5 executable.

---

### Post by vxthanh on 2011-04-08
OK, I have could use "Grammar" and "Teacher Resource" without any other manipulation. This happened after I had restarted my com. I really have files: "gram.skn" and "~/.macromedia/Flash_Player/#Security/FlashPlayerTrust/ldoce5.cfg".Thus, We can install Ldoce5 in the way of [http://thanhsiang.org/faqing/node/105]("http://thanhsiang.org/faqing/node/105"). To install "libgtk1.2", we can add suitable repositories into "/etc/apt/sources.list", see [http://www.pvv.ntnu.no/~knuta/xmms/]("http://www.pvv.ntnu.no/~knuta/xmms/").

P/S: I'm very happy. I have could use Ldoce5. Thank you very much.

---

### Post by eltama on 2011-04-08
Good to know!

---

### Post by mehrdad_v on 2012-06-21
Hey guys,

I have followed the instruction and it has installed without any problem, but I get the below error when I want to run it:

```
mehrdad@mehrdad-XPS:~/ldoce5$ ./ldoce5-bin 
./ldoce5-bin: error while loading shared libraries: libxpcom.so: cannot open shared object file: No such file or directory
mehrdad@mehrdad-XPS:~/ldoce5$ chmod +x ldoce5
mehrdad@mehrdad-XPS:~/ldoce5$ chmod +x ldoce5-
ldoce5-bin     ldoce5-config  
mehrdad@mehrdad-XPS:~/ldoce5$ chmod +x ldoce5-bin 
mehrdad@mehrdad-XPS:~/ldoce5$ ./ldoce5
*** glibc detected *** ./ldoce5-bin: free(): invalid pointer: 0x087e0098 ***
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(+0x73e42)[0xf6ab3e42]
/usr/lib/i386-linux-gnu/libstdc++.so.6(_ZdlPv+0x1f)[0xf52a451f]
/usr/lib/i386-linux-gnu/libstdc++.so.6(_ZNSs4_Rep10_M_destroyERKSaIcE+0x1b)[0xf528b99b]
/usr/lib/i386-linux-gnu/libstdc++.so.6(+0x909dc)[0xf528b9dc]
/usr/lib/i386-linux-gnu/libstdc++.so.6(_ZNSsD1Ev+0x2e)[0xf528ba4e]
/usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/liboxygen-gtk.so(_ZN6Oxygen3Gtk2RC4initEv+0x141)[0xf5387071]
/usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/liboxygen-gtk.so(_ZN6Oxygen10QtSettingsC2Ev+0x408)[0xf53812b8]
/usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/liboxygen-gtk.so(_ZN6Oxygen5Style8instanceEv+0x77)[0xf53a5d37]
/usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/liboxygen-gtk.so(theme_init+0x2f)[0xf53efa5f]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(+0x2136b6)[0xf72cf6b6]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_type_module_use+0x99)[0xf6f4e7e9]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(gtk_theme_engine_get+0x42)[0xf72cf7f2]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(+0x18dafd)[0xf7249afd]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(+0x18e673)[0xf724a673]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(+0x18e7e1)[0xf724a7e1]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(+0x18e11d)[0xf724a11d]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(+0x18e673)[0xf724a673]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(+0x18e7e1)[0xf724a7e1]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(gtk_rc_reparse_all_for_settings+0xee)[0xf724ad2e]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(gtk_settings_get_for_screen+0xe4)[0xf726b7b4]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(gtk_settings_get_default+0x24)[0xf726b824]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(+0x1c7f0a)[0xf7283f0a]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_type_create_instance+0x11b)[0xf6f4b71b]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(+0x12508)[0xf6f2e508]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_object_newv+0x811)[0xf6f30231]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_object_new+0xa8)[0xf6f307c8]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(gtk_style_new+0x24)[0xf7284354]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(gtk_widget_get_default_style+0x25)[0xf7330065]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(+0x274118)[0xf7330118]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_type_create_instance+0xce)[0xf6f4b6ce]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(+0x12508)[0xf6f2e508]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(+0x121cb6)[0xf71ddcb6]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_object_newv+0x811)[0xf6f30231]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_object_new+0xa8)[0xf6f307c8]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(gtk_invisible_new+0x24)[0xf71de1d4]
/home/mehrdad/ldoce5/components/libwidget_gtk2.so(+0x143e7)[0xf579a3e7]
/home/mehrdad/ldoce5/components/libwidget_gtk2.so(+0x12b43)[0xf5798b43]
./libxpcom_core.so(+0x3f9c1)[0xf767f9c1]
./libxpcom_core.so(+0x7afb5)[0xf76bafb5]
./libxpcom_core.so(+0x7b301)[0xf76bb301]
./libxpcom_core.so(_Z14CallGetServiceRK4nsIDS1_PPv+0x42)[0xf767d122]
./libxpcom_core.so(_ZNK17nsGetServiceByCIDclERK4nsIDPPv+0x2b)[0xf767d493]
./libxpcom_core.so(_ZN13nsCOMPtr_base18assign_from_gs_cidE17nsGetServiceByCIDRK4nsID+0x2b)[0xf767cf5d]
./ldoce5-bin[0x804c251]
./ldoce5-bin[0x804ce1f]
./ldoce5-bin[0x804db2b]
/lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xf3)[0xf6a594d3]
======= Memory map: ========
08048000-08073000 r-xp 00000000 08:15 12326187                           /home/mehrdad/ldoce5/ldoce5-bin
08073000-08074000 rw-p 0002b000 08:15 12326187                           /home/mehrdad/ldoce5/ldoce5-bin
086d3000-087fd000 rw-p 00000000 00:00 0                                  [heap]
f51fb000-f52d3000 r-xp 00000000 08:11 1450541                            /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
f52d3000-f52d4000 ---p 000d8000 08:11 1450541                            /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
f52d4000-f52d8000 r--p 000d8000 08:11 1450541                            /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
f52d8000-f52d9000 rw-p 000dc000 08:11 1450541                            /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
f52d9000-f52e0000 rw-p 00000000 00:00 0 
f52e0000-f5424000 r-xp 00000000 08:11 139409                             /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/liboxygen-gtk.so
f5424000-f5425000 ---p 00144000 08:11 139409                             /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/liboxygen-gtk.so
f5425000-f5428000 r--p 00144000 08:11 139409                             /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/liboxygen-gtk.so
f5428000-f542a000 rw-p 00147000 08:11 139409                             /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/liboxygen-gtk.so
f542a000-f5434000 r-xp 00000000 08:11 1711393                            /lib/i386-linux-gnu/libnss_nis-2.15.so
f5434000-f5435000 r--p 00009000 08:11 1711393                            /lib/i386-linux-gnu/libnss_nis-2.15.so
f5435000-f5436000 rw-p 0000a000 08:11 1711393                            /lib/i386-linux-gnu/libnss_nis-2.15.so
f5436000-f544c000 r-xp 00000000 08:11 1711388                            /lib/i386-linux-gnu/libnsl-2.15.so
f544c000-f544d000 r--p 00015000 08:11 1711388                            /lib/i386-linux-gnu/libnsl-2.15.so
f544d000-f544e000 rw-p 00016000 08:11 1711388                            /lib/i386-linux-gnu/libnsl-2.15.so
f544e000-f5450000 rw-p 00000000 00:00 0 
f5450000-f5457000 r-xp 00000000 08:11 1711389                            /lib/i386-linux-gnu/libnss_compat-2.15.so
f5457000-f5458000 r--p 00006000 08:11 1711389                            /lib/i386-linux-gnu/libnss_compat-2.15.so
f5458000-f5459000 rw-p 00007000 08:11 1711389                            /lib/i386-linux-gnu/libnss_compat-2.15.so
f5478000-f5488000 r-xp 00000000 08:15 12326053                           /home/mehrdad/ldoce5/components/libnsprefm.so
f5488000-f5489000 rw-p 0000f000 08:15 12326053                           /home/mehrdad/ldoce5/components/libnsprefm.so
f5489000-f54cf000 r-xp 00000000 08:15 12326025                           /home/mehrdad/ldoce5/components/libdocshell.so
f54cf000-f54d2000 rw-p 00046000 08:15 12326025                           /home/mehrdad/ldoce5/components/libdocshell.so
f54d2000-f5522000 r-xp 00000000 08:15 12325985                           /home/mehrdad/ldoce5/components/libhtmlpars.so
f5522000-f5529000 rw-p 00050000 08:15 12325985                           /home/mehrdad/ldoce5/components/libhtmlpars.so
f5529000-f55e2000 r-xp 00000000 08:15 12325950                           /home/mehrdad/ldoce5/components/libuconv.so
f55e2000-f55e8000 rw-p 000b9000 08:15 12325950                           /home/mehrdad/ldoce5/components/libuconv.so
f55e8000-f55f2000 rw-p 00000000 00:00 0 
f55f2000-f5639000 r-xp 00000000 08:11 1714906                            /lib/i386-linux-gnu/libdbus-1.so.3.5.8
f5639000-f563a000 r--p 00046000 08:11 1714906                            /lib/i386-linux-gnu/libdbus-1.so.3.5.8
f563a000-f563b000 rw-p 00047000 08:11 1714906                            /lib/i386-linux-gnu/libdbus-1.so.3.5.8
f563b000-f565f000 r-xp 00000000 08:11 1461060                            /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.2
f565f000-f5660000 r--p 00023000 08:11 1461060                            /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.2
f5660000-f5661000 rw-p 00024000 08:11 1461060                            /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.2
f5661000-f568d000 r-xp 00000000 08:11 1461478                            /usr/lib/i386-linux-gnu/libgconf-2.so.4.1.5
f568d000-f568e000 r--p 0002b000 08:11 1461478                            /usr/lib/i386-linux-gnu/libgconf-2.so.4.1.5
f568e000-f568f000 rw-p 0002c000 08:11 1461478                            /usr/lib/i386-linux-gnu/libgconf-2.so.4.1.5
f568f000-f569a000 r-xp 00000000 08:11 1711391                            /lib/i386-linux-gnu/libnss_files-2.15.so
f569a000-f569b000 r--p 0000a000 08:11 1711391                            /lib/i386-linux-gnu/libnss_files-2.15.so
f569b000-f569c000 rw-p 0000b000 08:11 1711391                            /lib/i386-linux-gnu/libnss_files-2.15.so
f56a4000-f56ba000 r-xp 00000000 08:15 12326049                           /home/mehrdad/ldoce5/components/libchrome.so
f56ba000-f56bb000 rw-p 00015000 08:15 12326049                           /home/mehrdad/ldoce5/components/libchrome.so
f56bb000-f56be000 r-xp 00000000 08:11 1450288                            /usr/lib/i386-linux-gnu/gconv/UTF-16.so
f56be000-f56bf000 r--p 00002000 08:11 1450288                            /usr/lib/i386-linux-gnu/gconv/UTF-16.so
f56bf000-f56c0000 rw-p 00003000 08:11 1450288                            /usr/lib/i386-linux-gnu/gconv/UTF-16.so
f56c0000-f56c7000 r--s 00000000 08:11 1443804                            /usr/lib/i386-linux-gnu/gconv/gconv-modules.cache
f56c7000-f56e1000 r-xp 00000000 08:15 12326216                           /home/mehrdad/ldoce5/libxpcom_compat.so
f56e1000-f56e2000 rw-p 0001a000 08:15 12326216                           /home/mehrdad/ldoce5/libxpcom_compat.so
f56e2000-f56e6000 r-xp 00000000 08:11 1714926                            /lib/i386-linux-gnu/libuuid.so.1.3.0
f56e6000-f56e7000 r--p 00003000 08:11 1714926                            /lib/i386-linux-gnu/libuuid.so.1.3.0
f56e7000-f56e8000 rw-p 00004000 08:11 1714926                            /lib/i386-linux-gnu/libuuid.so.1.3.0
f56e8000-f56fe000 r-xp 00000000 08:11 1461350                            /usr/lib/i386-linux-gnu/libICE.so.6.3.0
f56fe000-f56ff000 r--p 00015000 08:11 1461350                            /usr/lib/i386-linux-gnu/libICE.so.6.3.0
f56ff000-f5700000 rw-p 00016000 08:11 1461350                            /usr/lib/i386-linux-gnu/libICE.so.6.3.0
f5700000-f5702000 rw-p 00000000 00:00 0 
f5702000-f5709000 r-xp 00000000 08:11 1461352                            /usr/lib/i386-linux-gnu/libSM.so.6.0.1
f5709000-f570a000 r--p 00006000 08:11 1461352                            /usr/lib/i386-linux-gnu/libSM.so.6.0.1
f570a000-f570b000 rw-p 00007000 08:11 1461352                            /usr/lib/i386-linux-gnu/libSM.so.6.0.1
f570b000-f5763000 r-xp 00000000 08:11 1461354                            /usr/lib/i386-linux-gnu/libXt.so.6.0.0
f5763000-f5764000 r--p 00057000 08:11 1461354                            /usr/lib/i386-linux-gnu/libXt.so.6.0.0
f5764000-f5767000 rw-p 00058000 08:11 1461354                            /usr/lib/i386-linux-gnu/libXt.so.6.0.0
f576d000-f5772000 r-xp 00000000 08:15 12325944                           /home/mehrdad/ldoce5/components/libxpcom_compat_c.so
f5772000-f5773000 rw-p 00004000 08:15 12325944                           /home/mehrdad/ldoce5/components/libxpcom_compat_c.so
f5773000-f5785000 r-xp 00000000 08:15 12326051                           /home/mehrdad/ldoce5/components/libprofile.so
f5785000-f5786000 rw-p 00012000 08:15 12326051                           /home/mehrdad/ldoce5/components/libprofile.so
f5786000-f57ad000 r-xp 00000000 08:15 12326009                           /home/mehrdad/ldoce5/components/libwidget_gtk2.so
f57ad000-f57b1000 rw-p 00026000 08:15 12326009                           /home/mehrdad/ldoce5/components/libwidget_gtk2.so
f57b1000-f57fd000 r-xp 00000000 08:15 12326076                           /home/mehrdad/ldoce5/components/libappcomps.so
f57fd000-f5800000 rw-p 0004b000 08:15 12326076                           /home/mehrdad/ldoce5/components/libappcomps.so
f5800000-f5821000 rw-p 00000000 00:00 0 
f5821000-f5900000 ---p 00000000 00:00 0 
f5900000-f5904000 r-xp 00000000 08:15 12326194                           /home/mehrdad/ldoce5/libgtkxtbin.so
f5904000-f5905000 rw-p 00003000 08:15 12326194                           /home/mehrdad/ldoce5/libgtkxtbin.so
f5905000-f5919000 r-xp 00000000 08:15 12326047                           /home/mehrdad/ldoce5/components/libnsappshell.so
f5919000-f591a000 rw-p 00014000 08:15 12326047                           /home/mehrdad/ldoce5/components/libnsappshell.so
f591a000-f5940000 r-xp 00000000 08:15 12325983                           /home/mehrdad/ldoce5/components/librdf.so
f5940000-f5942000 rw-p 00025000 08:15 12325983                           /home/mehrdad/ldoce5/components/librdf.so
f5942000-f5977000 r-xp 00000000 08:15 12325955                           /home/mehrdad/ldoce5/components/libi18n.so
f5977000-f597a000 rw-p 00034000 08:15 12325955                           /home/mehrdad/ldoce5/components/libi18n.so
f597a000-f597b000 ---p 00000000 00:00 0 
f597b000-f617b000 rwxp 00000000 00:00 0 
f617b000-f622c000 r-xp 00000000 08:15 12325971                           /home/mehrdad/ldoce5/components/libnecko.so
f622c000-f6233000 rw-p 000b0000 08:15 12325971                           /home/mehrdad/ldoce5/components/libnecko.so
f6233000-f6241000 r-xp 00000000 08:15 12325979                           /home/mehrdad/ldoce5/components/libpref.so
f6241000-f6242000 rw-p 0000d000 08:15 12325979                           /home/mehrdad/ldoce5/components/libpref.so
f6242000-f628a000 r-xp 00000000 08:15 12325947                           /home/mehrdad/ldoce5/components/libxpconnect.so
f628a000-f628e000 rw-p 00047000 08:15 12325947                           /home/mehrdad/ldoce5/components/libxpconnect.so
f628e000-f629e000 r-xp 00000000 08:15 12326196                           /home/mehrdad/ldoce5/libmozz.so
f629e000-f629f000 rw-p 0000f000 08:15 12326196                           /home/mehrdad/ldoce5/libmozz.so
f629f000-f62bc000 r-xp 00000000 08:15 12326192                           /home/mehrdad/ldoce5/libgkgfx.so
f62bc000-f62bd000 rw-p 0001d000 08:15 12326192                           /home/mehrdad/ldoce5/libgkgfx.so
f62bd000-f62e5000 r-xp 00000000 08:15 12326036                           /home/mehrdad/ldoce5/components/libembedcomponents.so
f62e5000-f62e7000 rw-p 00027000 08:15 12326036                           /home/mehrdad/ldoce5/components/libembedcomponents.so
f62e7000-f64e7000 r--p 00000000 08:11 1448146                            /usr/lib/locale/locale-archive
f64e7000-f64ea000 rw-p 00000000 00:00 0 
f64ea000-f64ef000 r-xp 00000000 08:11 1460930                            /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
f64ef000-f64f0000 r--p 00004000 08:11 1460930                            /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
f64f0000-f64f1000 rw-p 00005000 08:11 1460930                            /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
f64f1000-f64f3000 r-xp 00000000 08:11 1460928                            /usr/lib/i386-linux-gnu/libXau.so.6.0.0
f64f3000-f64f4000 r--p 00001000 08:11 1460928                            /usr/lib/i386-linux-gnu/libXau.so.6.0.0
f64f4000-f64f5000 rw-p 00002000 08:11 1460928                            /usr/lib/i386-linux-gnu/libXau.so.6.0.0
f64f5000-f64f6000 rw-p 00000000 00:00 0 
f64f6000-f651c000 r-xp 00000000 08:11 1714841                            /lib/i386-linux-gnu/libexpat.so.1.5.2
f651c000-f651d000 ---p 00026000 08:11 1714841                            /lib/i386-linux-gnu/libexpat.so.1.5.2
f651d000-f651f000 r--p 00026000 08:11 1714841                            /lib/i386-linux-gnu/libexpat.so.1.5.2
f651f000-f6520000 rw-p 00028000 08:11 1714841                            /lib/i386-linux-gnu/libexpat.so.1.5.2
f6520000-f6533000 r-xp 00000000 08:11 1714815                            /lib/i386-linux-gnu/libresolv-2.15.so
f6533000-f6534000 ---p 00013000 08:11 1714815                            /lib/i386-linux-gnu/libresolv-2.15.so
f6534000-f6535000 r--p 00013000 08:11 1714815                            /lib/i386-linux-gnu/libresolv-2.15.so
f6535000-f6536000 rw-p 00014000 08:11 1714815                            /lib/i386-linux-gnu/libresolv-2.15.so
f6536000-f6538000 rw-p 00000000 00:00 0 
f6538000-f6555000 r-xp 00000000 08:11 1714910                            /lib/i386-linux-gnu/libselinux.so.1
f6555000-f6556000 r--p 0001c000 08:11 1714910                            /lib/i386-linux-gnu/libselinux.so.1
f6556000-f6557000 rw-p 0001d000 08:11 1714910                            /lib/i386-linux-gnu/libselinux.so.1
f6557000-f656b000 r-xp 00000000 08:11 1714843                            /lib/i386-linux-gnu/libz.so.1.2.3.4
f656b000-f656c000 r--p 00013000 08:11 1714843                            /lib/i386-linux-gnu/libz.so.1.2.3.4
f656c000-f656d000 rw-p 00014000 08:11 1714843                            /lib/i386-linux-gnu/libz.so.1.2.3.4
f656d000-f656e000 rw-p 00000000 00:00 0 
f656e000-f6576000 r-xp 00000000 08:11 1461167                            /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
f6576000-f6577000 r--p 00008000 08:11 1461167                            /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
f6577000-f6578000 rw-p 00009000 08:11 1461167                            /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
f6578000-f657a000 r-xp 00000000 08:11 1461169                            /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
f657a000-f657b000 r--p 00001000 08:11 1461169                            /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
f657b000-f657c000 rw-p 00002000 08:11 1461169                            /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
f657c000-f65a4000 r-xp 00000000 08:11 1714920                            /lib/i386-linux-gnu/libpng12.so.0.46.0
f65a4000-f65a5000 r--p 00027000 08:11 1714920                            /lib/i386-linux-gnu/libpng12.so.0.46.0Aborted (core dumped)
```

Would you please help me to figure out what wrong with it?

FYI, I use Kubuntu 12.04 64bit.

---

### Post by mehrdad_v on 2012-07-04
Hello guys,

Any idea?!

---

### Post by johnnybegood on 2012-08-07
I managed to fix it in this way (Ubuntu 12.04 Precise 64 bits):

1- Install alsa-oss 32 bits library
sudo apt-get install alsa-oss:i386

2- Modify aoss bin file (sudo gedit /usr/bin/aoss) linking to the new location: /usr/lib/i386-linux-gnu/libaoss.so

You just have to modify the location, you don't need all this code, but the lines would be:

if [ -d /proc/asound ]; then
  prefix=/usr
  libdir=${prefix}/lib/i386-linux-gnu
  LD_PRELOAD=${libdir}/libaoss.so${LD_PRELOAD:+:$LD_PRELOAD} exec "$@"
else
  echo "Warning: /proc/asound not found. Running without ALSA wrapper."
  exec "$@"
fi
exit 1

3- Preload this library simply using:
aoss /'your home directory'/ldoce5/ldoce5

or

LD_PRELOAD=/usr/lib/i386-linux-gnu/libaoss.so /'your home directory'/ldoce5/ldoce5

I hope it works, I got the idea from [this website]("http://askubuntu.com/questions/90951/no-sound-in-longman-dictionaryldoce5") but I modified it a bit.

GOOD LUCK!!!:)

---

### Post by rh1363 on 2012-09-09
I installed LDOCE5 completely.
but after I running, I'll see warning message. That is:
please insert the LDOCE DVD-ROM to access this feature
I don't want use DVD always.
How can I use this dictionary without mounting it's DVD?

---

### Post by rh1363 on 2012-09-11
> **rh1363 said:**
> I installed LDOCE5 completely.
but after I running, I'll see warning message. That is:
please insert the LDOCE DVD-ROM to access this feature
I don't want use DVD always.
How can I use this dictionary without mounting it's DVD?

[SIZE=4][COLOR=Red][B]Any answer?!!!

Please Help Men ........

:KS


[/B][/COLOR][/SIZE]

---

### Post by dom1n1cus on 2012-12-25
Hello folks,

I got a brand new Longman dictionary for Christmas, but I am unable to install the electronic version on my system. I followed the instructions, but there seem to be some trouble with permissions. When I go for it **without sudo**, the result is like this:

```
dominik@dominik-Satellite-L650D:~/Longman/linux$ linux32 ./setup.sh
----====== LDOCE5 installation program ======----

You are running a x86 machine with libc5
Hit Control-C anytime to cancel this installation program.

Single User Licence Agreement: Longman Dictionary of Contemporary English

IMPORTANT: READ CAREFULLY

This is a legally binding agreement between You (the user or purchaser) and Pearson Education Limited.  By retaining this license, any so
ftware media, or accompanying written materials or carrying out any of the permitted activities You agree to be bound by the terms of the
 license agreement below.

If You do not agree to these terms then promptly return the entire publication (this license and all software, written materials, packagi
ng and any other components received with it) with Your sales receipt to Your supplier for a full refund.

ONE COPY ONLY

This license is for a single user copy of the software


YOU ARE PERMITTED TO:

Use (load into temporary memory or permanent storage) a single copy of the software on only one computer at a time. If this computer is l
inked to a network then the software may only be installed in a manner such that it is not accessible to other machines on the network. I
f You want to use the software on a network or across a whole site, please contact Pearson Education Limited at the address given at the 
end of this license.

Use the software with a class provided it is only installed on one computer

Transfer the software from one computer to another provided that you only use it one computer at a time

Print out individual screen extracts from the disk for (a) private study or (b) to include in Your essays or classwork with students

Photocopy individual screen extracts for your schoolwork or classwork with students


YOU MAY NOT 

Rent, lease, or sell the software or any part of the publication

Copy any part of the documentation, except where specifically indicated otherwise

Make copies of the software, even for backup purposes

Reverse engineer, decompile, or disassemble the software or create a derivative product from the contents of the databases or any softwar
e included in them

Use the software on more than one computer at a time

Install the software on any networked computer or server in a way that could allow access to it from more than one machine in a network

Include any special material or software from the disk in any other product or software materials, except as allowed under "You are permi
tted to"

Use the software in any way not specified above without the prior written consent of Pearson Education Limited

Print out more than one page at a time

Print, download, or save any pictures  


PEARSON EDUCATION LIMITED RESERVES THE RIGHT TO TERMINATE THIS LICENSE BY WRITTEN NOTICE AND TO TAKE ACTION TO RECOVER ANY DAMAGES SUFFER
ED BY PEARSON EDUCATION LIMITED IF YOU BREACH ANY PROVISION OF THIS AGREEMENT.

Pearson Education Limited owns the software. You only own the disk on which the software is supplied.

LIMITED WARRANTY

Pearson Education Limited warrants that the disk or CD-ROM on which the software is supplied is free from defects in materials and workma
nship under normal use for ninety (90) days from the date You receive it. This warranty is limited to You and is not transferable. Pearso
n Education Limited does not warrant that the functions of the software meet Your requirements or that the media is compatible with any c
omputer system on which it is used or that the operation of the software will be unlimited or error-free.

You assume responsibility for selecting the software to achieve Your intended results and for the installation of, the use of, and the re
sults obtained from the software. The entire liability of Pearson Education Limited and your only remedy shall be replacement free of cha
rge of the components that do not meet this warranty.

This limited warranty is void if any damage has resulted from accident, abuse, misapplication, service, or modification by someone other 
than Pearson Education Limited. In no event shall Pearson Education Limited be liable for any damages whatsoever arising out of installat
ion of the software, even if advised of the possibility of such damages. Pearson Education Limited will not be liable for any loss or dam
age of any nature suffered by any party as a result of reliance upon or reproduction of or any errors in the content of the publication.

Pearson Education Limited does not limit its liability for death or personal injury caused by its negligence. 

This license agreement shall be governed by and interpreted and construed in accordance with English law. 

Technical support: only registered users are entitled to free technical help and advice. As a registered user, You may receive technical 
help by writing to elt-support@pearson.com or your local agent.

New releases and updates: as a registered user You may be able to get new releases and updates, or upgrade to a network version of the so
ftware at reduced prices.

Registration: to register as a user, please write to us at the address shown below or email us at elt-support@pearson.com

Longman Dictionaries Division
Pearson Education Limited
Edinburgh Gate
Harlow
Essex
CM20 2JE
England
Do you agree with the license? [Y/n] y
Please enter the installation path [/home/dominik/ldoce5] 
'Application and data files' option will be installed.
'Minimal data files and application' option will be installed.
'Medium data files' option will be installed.
'Recommended data files' option will be installed.
'Full data files' option will be installed.
'Permission handling' option will be installed.
'Install fonts' option will be installed.
'Install desktop shortcut' option will be installed.
Installing to /home/dominik/ldoce5/
39643 MB available, 2415 MB will be installed.

Continue install? [Y/n] y
Installing Application and data files ...
 100% - /home/dominik/ldoce5//LICENSE.txt
 100% - /home/dominik/ldoce5//chrome/comm.jarinInspectorMain16.xpmmm
 100% - /home/dominik/ldoce5//chrome/en-US.jar.txt
 100% - /home/dominik/ldoce5//chrome/toolkit.jar
 100% - /home/dominik/ldoce5//chrome/modern.jar
 100% - /home/dominik/ldoce5//chrome/inspector.jar
 100% - /home/dominik/ldoce5//chrome/plugs.jarst
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/tour.swfml
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/xml/words_int.xmlsandseas.xmll
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/xml/sentences.xmlx1.xmlmllxmll
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/xml/words_adv.xmllise1.xml.xml
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/audio/IELTS_listening_exercise1_1.mp3
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/audio/IELTS_listening_exercise7_2.mp3
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/audio/cae1_list2.mp3
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/audio/cae1_list3.mp3
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/audio/TOEIC_listening_exercise1.mp3
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/audio/TOEIC_listening_exercise2.mp3
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/audio/TOEIC_listening_exercise6_1.mp3
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/audio/TOEIC_listening_exercise6_2.mp3
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/audio/TOEIC_listening_exercise6_3.mp3
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/audio/IELTS_listening_exercise7_1.mp3
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/audio/cae2_list_part2.mp3
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/audio/cae2_list_part3.mp3
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/audio/fce1_listening2.mp3
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/audio/fce1_listening4.mp3
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/audio/fce2_listening2.mp3
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/audio/fce2_listening4.mp3
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/images/Thumbs.db
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/images/carbackfinal.jpg
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/images/carfrontfinal.jpg
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/images/carinsidefinal.jpg
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/images/containersfinal.jpg
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/images/crockery_excfinal.jpg
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/images/desk_itemsfinal.jpg
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/images/dried_fruitfinal.jpg
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/images/fruit1final.jpg
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/images/fruit2final.jpg
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/images/garden_toolsfinal.jpg
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/images/patiofinal.jpg
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/images/receptionfinal.jpg
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/images/skeleton_excfinal.jpg
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/images/suitsfinal.jpg
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/images/trayfinal.jpg
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/images/vegetables1final.jpg
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/images/vegetables2final.jpg
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/images/ielts_writing5.jpgg
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/1_Homepage.flvion.jpg
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/2_WordDay.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/5_DictionarySearch.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/6_DictionarySpellCheck.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/7_DictionaryInflectedF.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/8_Dict - Phrase search.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/10.Dictionary - Search.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/12_SeeExamples.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/17_Collocations.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/18.Thesaurus.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/19.Phrase Bank.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/20.Pronunciations.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/21_WordFamily.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/23_VerbForms.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/24.User notes.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/25_ActivatorOpeningAct.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/27_ActUsingFullIndSear.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/28.Grammar.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/29.Exam Practice.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/29.Exercise Bank.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/30.Select a list.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/31.Learn words.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/34_ReviseWords.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/35_Teacher Resources.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/36.Pop up dict - words.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/36.Pop up dictionary.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/13.See over 1500 pictu.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/33.Check Progress.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/37.Writing assistant.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/3.Academic word list11.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/9.Dicti Pron.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/4.Communication 3000.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/22.Menu111111.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/16.Personalize setting.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/26.Activator Keyword s.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/15.Explore word origin.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/11.Dict - Under dict e.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/assets/14.Search dict ent.flv
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/ldoce_exercises.swf
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/scores.swfpicturecd.xmlde.xml
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/skins/skins1.swf
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/skins/Copy of skins1.swf
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/swf/crossword.swf
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/swf/matching.swf
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/swf/preview.swf
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/swf/listening.swf
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/flash/homepage/swf/scramble.swf
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/help/images/image002.jpggiff
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/help/images/image003.jpg
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/help/images/image007.jpg
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/help/images/image008.jpg
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/help/images/image009.jpg
 100% - /home/dominik/ldoce5//chrome/ldoce5/content/help/images/image010.jpg
 /home/dominik/ldoce5//chrome/ldoce5/skin/activator.csss.csscssrs.csshov.giff.giffngionManager.css
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Homework1.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Homework10.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Homework2.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Homework3.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Homework4.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Homework5.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Homework6.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Homework7.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Homework8.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Homework9.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/LDOCE5_Worksheets21.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/LDOCE5_Worksheets22.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/LDOCE5_Worksheets23.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/LDOCE5_Worksheets24.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/LDOCE5_Worksheets25.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/LDOCE_AWL.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Quiz1.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Quiz10.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Quiz2.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Quiz3.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Quiz4.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Quiz5.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Quiz6.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Quiz7.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Quiz8.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Quiz9.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Worksheet1.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Worksheet10.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Worksheet11.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Worksheet12.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Worksheet13.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Worksheet14.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Worksheet15.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Worksheet16.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Worksheet17.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Worksheet18.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Worksheet19.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Worksheet2.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Worksheet20.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Worksheet3.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Worksheet4.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Worksheet5.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Worksheet6.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Worksheet7.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Worksheet8.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/Worksheet9.pdf
 100% - /home/dominik/ldoce5//chrome/ldoce5/pdfs/comm3000.pdf
 100% - /home/dominik/ldoce5//components/libxpconnect.so
 100% - /home/dominik/ldoce5//components/libuconv.so
 100% - /home/dominik/ldoce5//components/libi18n.so
 100% - /home/dominik/ldoce5//components/libnecko.sopt
 100% - /home/dominik/ldoce5//components/libhtmlpars.so
 100% - /home/dominik/ldoce5//components/libgfxps.so
 100% - /home/dominik/ldoce5//components/libgfx_gtk.so
 100% - /home/dominik/ldoce5//components/libimglib2.so
 100% - /home/dominik/ldoce5//components/libwidget_gtk2.so
 100% - /home/dominik/ldoce5//components/libgklayout.so
 100% - /home/dominik/ldoce5//components/libdocshell.so
 100% - /home/dominik/ldoce5//components/libeditor.soso
 100% - /home/dominik/ldoce5//components/libmork.so
 100% - /home/dominik/ldoce5//components/libappcomps.sotener.js
 100% - /home/dominik/ldoce5//components/libxpinstall.so
 100% - /home/dominik/ldoce5//components/libpipnss.so
 100% - /home/dominik/ldoce5//components/libtransformiix.so
 100% - /home/dominik/ldoce5//libSDL-1.2.so.0s.jss.jsssffome-example.csss
 100% - /home/dominik/ldoce5//libaspell.so.15
 100% - /home/dominik/ldoce5//libmozjs.so
 100% - /home/dominik/ldoce5//libnspr4.so
 100% - /home/dominik/ldoce5//libnss3.so
 100% - /home/dominik/ldoce5//libnssckbi.so
 100% - /home/dominik/ldoce5//libsmime3.so.so
 100% - /home/dominik/ldoce5//libsmpeg-0.4.so.0
 100% - /home/dominik/ldoce5//libsoftokn3.so
 100% - /home/dominik/ldoce5//libssl3.so
 100% - /home/dominik/ldoce5//libstdc++.so.5
 100% - /home/dominik/ldoce5//libxpcom_core.so
 100% - /home/dominik/ldoce5//plugins/libflashplayer.so
 Running scriptldoce5//xpcshellents/libskfindbenative.so.soffiesrties
rm: nelze odstranit „/home/dominik/.macromedia/Flash_Player/#Security/FlashPlayerTrust/ldoce5.cfg“: Operace zamítnuta
setup.data/set_flash_security_file.sh: &#345;ádek 9: /home/dominik/.macromedia/Flash_Player/#Security/FlashPlayerTrust/ldoce5.cfg: Operace zamítnuta
loki_setup: Script seems to have failed with error code 1.
Installing Minimal data files and application ...
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/idx_index.skn/wordlist/tok.skn/OCC.skn/POSITION.skn/POSITION.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/idx_index.skn/wordlist/tok.skn/OCC.skn/OCC.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/idx_index.skn/wordlist/tok.skn/tok.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/idx_index.skn/wordlist/tok.skn/TOKEN.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/idx_index.skn/wordlist/simtok.skn/TOKENS.skn/TOKENS.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/idx_index.skn/wordlist/simtok.skn/simtok.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/idx_index.skn/wordlist/simtok.skn/TOKEN.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/idx_index.skn/wordlist/revsimtok.skn/revsimtok.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/idx_index.skn/wordlist/revsimtok.skn/TOKEN.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/idx_index.skn/wordlist/revtok.skn/revtok.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/idx_index.skn/wordlist/revtok.skn/TOKEN.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/index.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/dict/en.rws
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-3.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-2.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-11.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-10.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-13.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-13.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-2.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-3.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-7.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-8.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-9.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-16.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-6.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-15.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-4.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-4.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-14.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-16.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-5.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-11.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-15.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-1.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-5.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-1.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-14.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-9.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-10.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-6.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-7.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/spell/data/iso-8859-8.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/arl_sound.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/display.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/ac_label.skn/rs_ids.skn/label.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl_sound.skn/ac_label.skn/rs_ids.skn/rs_ids.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/idx_index.skn/wordlist/tok.skn/OCC.skn/POSITION.skn/POSITION.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/idx_index.skn/wordlist/tok.skn/OCC.skn/OCC.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/idx_index.skn/wordlist/tok.skn/tok.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/idx_index.skn/wordlist/tok.skn/tok.lc
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/idx_index.skn/wordlist/tok.skn/TOKEN.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/idx_index.skn/wordlist/simtok.skn/TOKENS.skn/TOKENS.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/idx_index.skn/wordlist/simtok.skn/simtok.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/idx_index.skn/wordlist/simtok.skn/simtok.lc
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/idx_index.skn/wordlist/simtok.skn/TOKEN.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/idx_index.skn/wordlist/revsimtok.skn/revsimtok.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/idx_index.skn/wordlist/revsimtok.skn/TOKEN.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/idx_index.skn/wordlist/revsimtok.skn/revsimtok.lc
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/idx_index.skn/wordlist/revtok.skn/revtok.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/idx_index.skn/wordlist/revtok.skn/revtok.lc
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/idx_index.skn/wordlist/revtok.skn/TOKEN.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/index.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/dict/en.rws
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-3.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-2.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-11.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-10.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-13.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-13.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-2.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-3.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-7.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-8.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-9.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-16.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-6.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-15.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-4.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-4.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-14.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-16.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-5.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-11.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-15.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-1.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-5.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-1.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-14.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-9.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-10.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-6.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-7.cset
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/spell/data/iso-8859-8.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/context.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/display.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/arl.skn/arl.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/culture_alpha_index.skn/CONTEXT.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/culture_alpha_index.skn/SRCH.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/culture_alpha_index.skn/TOOLTIP.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/culture_alpha_index.skn/LABEL.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/culture_alpha_index.skn/lc_SRCH.skn/a_ids.skn/a_ids.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/culture_alpha_index.skn/lc_SRCH.skn/lc_SRCH.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/culture_alpha_index.skn/lc_SRCH.skn/SRCH.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/culture_alpha_index.skn/ARL.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/culture_alpha_index.skn/culture_alpha_index.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/files.skn/CONTENT.tda.tdz
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/files.skn/files.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/files.skn/TITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/files.skn/NAME.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/files.skn/TEXTTITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/files.skn/CONTENT.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/mapping.skn/lc_publisher_id.skn/publisher_id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/mapping.skn/lc_publisher_id.skn/lc_publisher_id.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/mapping.skn/lc_publisher_id.skn/lc_publisher_id.lc
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/mapping.skn/publisher_id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/mapping.skn/mapping.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/dirs.skn/FILES.skn/FILES.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/alpha_index.skn/CONTEXT.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/alpha_index.skn/SRCH.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/alpha_index.skn/TOOLTIP.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/alpha_index.skn/LABEL.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/alpha_index.skn/alpha_index.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/alpha_index.skn/lc_SRCH.skn/a_ids.skn/a_ids.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/alpha_index.skn/lc_SRCH.skn/lc_SRCH.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/alpha_index.skn/lc_SRCH.skn/SRCH.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/alpha_index.skn/ARL.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/bookmark.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/phrasal_search.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/phrase.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/context.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/display.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/flex.skn/flex.lc
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/flex.skn/flex.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/flex.skn/r_stem.skn/stem.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/flex.skn/r_stem.skn/r_stem.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/flex.skn/r_flex.skn/flex.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/flex.skn/r_flex.skn/r_flex.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/flex.skn/word.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/words.skn/words.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/words.skn/r_phword.skn/r_phword.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/words.skn/r_phword.skn/targetid.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/words.skn/lookup.tda
  40% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/words.skn/lc_SRCH.skn/wordlist/tok.skn/OCC.skn/POSITION.skn/POSITION.  81% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/words.skn/lc_SRCH.skn/wordlist/tok.skn/OCC.skn/POSITION.skn/POSITION. 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/words.skn/lc_SRCH.skn/wordlist/tok.skn/OCC.skn/POSITION.skn/POSITION.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/words.skn/lc_SRCH.skn/wordlist/tok.skn/OCC.skn/OCC.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/words.skn/lc_SRCH.skn/wordlist/tok.skn/tok.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/words.skn/lc_SRCH.skn/wordlist/tok.skn/TOKEN.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/words.skn/lc_SRCH.skn/wordlist/simtok.skn/TOKENS.skn/TOKENS.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/words.skn/lc_SRCH.skn/wordlist/simtok.skn/simtok.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/words.skn/lc_SRCH.skn/wordlist/simtok.skn/TOKEN.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/words.skn/lc_SRCH.skn/wordlist/revsimtok.skn/revsimtok.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/words.skn/lc_SRCH.skn/wordlist/revsimtok.skn/TOKEN.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/words.skn/lc_SRCH.skn/wordlist/revtok.skn/revtok.dat
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/words.skn/lc_SRCH.skn/wordlist/revtok.skn/TOKEN.tda
 100% - /home/dominik/ldoce5//ldoce5.data/fs.skn/phrasal_search.skn/entry_id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/vt/q_idx.skn/QA_IDS.tda
 100% - /home/dominik/ldoce5//ldoce5.data/vt/q_idx.skn/HID.tda
 100% - /home/dominik/ldoce5//ldoce5.data/vt/q_idx.skn/QB_IDS.tda
 100% - /home/dominik/ldoce5//ldoce5.data/vt/q_idx.skn/q_idx.dat
 100% - /home/dominik/ldoce5//ldoce5.data/vt/q_idx.skn/QC_IDS.tda
 100% - /home/dominik/ldoce5//ldoce5.data/vt/fs.skn/files.skn/files.dat
 100% - /home/dominik/ldoce5//ldoce5.data/vt/fs.skn/files.skn/TITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/vt/fs.skn/files.skn/NAME.tda
 100% - /home/dominik/ldoce5//ldoce5.data/vt/fs.skn/files.skn/TEXTTITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/vt/fs.skn/files.skn/CONTENT.tda
 100% - /home/dominik/ldoce5//ldoce5.data/vt/fs.skn/dirs.skn/dirs.dat
 100% - /home/dominik/ldoce5//ldoce5.data/vt/fs.skn/dirs.skn/NAME.tda
 100% - /home/dominik/ldoce5//ldoce5.data/vt/fs.skn/dirs.skn/FILES.skn/FILES.dat
Installing Medium data files ...
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/concept_highlight_id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/idx_index.skn/wordlist/tok.skn/OCC.skn/POSITION.skn/POSITION.dat
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/idx_index.skn/wordlist/tok.skn/OCC.skn/OCC.dat
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/idx_index.skn/wordlist/tok.skn/tok.dat
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/idx_index.skn/wordlist/tok.skn/TOKEN.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/idx_index.skn/wordlist/simtok.skn/TOKENS.skn/TOKENS.dat
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/idx_index.skn/wordlist/simtok.skn/simtok.dat
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/idx_index.skn/wordlist/simtok.skn/TOKEN.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/idx_index.skn/wordlist/revsimtok.skn/revsimtok.dat
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/idx_index.skn/wordlist/revsimtok.skn/TOKEN.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/idx_index.skn/wordlist/revtok.skn/revtok.dat
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/idx_index.skn/wordlist/revtok.skn/TOKEN.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/index.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/dict/en.rws
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-3.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-2.cset
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-11.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-10.cset
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-13.cset
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-13.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-2.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-3.cset
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-7.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-8.cset
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-9.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-16.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-6.cset
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-15.cset
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-4.cset
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-4.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-14.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-16.cset
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-5.cset
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-11.cset
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-15.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-1.cset
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-5.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-1.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-14.cset
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-9.cset
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-10.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-6.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-7.cset
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/spell/data/iso-8859-8.cmap
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/concept_id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/section_highlight_id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/display.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/concept_scroll_id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/section_id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/section_scroll_id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/arl.skn/arl.dat
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/files.skn/files.dat
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/files.skn/TITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/files.skn/NAME.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/files.skn/TEXTTITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/files.skn/CONTENT.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/activator_section.skn/files.skn/files.dat
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/activator_section.skn/files.skn/NAME.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/activator_section.skn/files.skn/CONTENT.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/activator_section.skn/mapping.skn/lc_publisher_id.skn/publisher_id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/activator_section.skn/mapping.skn/lc_publisher_id.skn/lc_publisher_id.dat
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/activator_section.skn/mapping.skn/publisher_id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/activator_section.skn/mapping.skn/mapping.dat
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/activator_section.skn/dirs.skn/FILES.skn/FILES.dat
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/alpha_index_key.skn/alpha_index_key.dat
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/alpha_index_key.skn/TOOLTIP.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/alpha_index_key.skn/LABEL.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/alpha_index_key.skn/ARL.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/dirs.skn/FILES.skn/FILES.dat
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/alpha_index.skn/CONTEXT.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/alpha_index.skn/SRCH.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/alpha_index.skn/TOOLTIP.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/alpha_index.skn/LABEL.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/alpha_index.skn/alpha_index.dat
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/alpha_index.skn/lc_SRCH.skn/a_ids.skn/a_ids.dat
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/alpha_index.skn/lc_SRCH.skn/lc_SRCH.dat
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/alpha_index.skn/lc_SRCH.skn/SRCH.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/alpha_index.skn/ARL.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/activator_concept.skn/files.skn/files.dat
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/activator_concept.skn/files.skn/TITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/activator_concept.skn/files.skn/NAME.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/activator_concept.skn/files.skn/CONTENT.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/activator_concept.skn/mapping.skn/lc_publisher_id.skn/publisher_id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/activator.skn/activator_concept.skn/mapping.skn/publisher_id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/collocations.skn/files.skn/CONTENT.tda.tdz
 100% - /home/dominik/ldoce5//ldoce5.data/collocations.skn/files.skn/files.dat
 100% - /home/dominik/ldoce5//ldoce5.data/collocations.skn/files.skn/TITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/collocations.skn/files.skn/NAME.tda
 100% - /home/dominik/ldoce5//ldoce5.data/collocations.skn/files.skn/TEXTTITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/collocations.skn/files.skn/CONTENT.tda
 100% - /home/dominik/ldoce5//ldoce5.data/collocations.skn/mapping.skn/lc_publisher_id.skn/publisher_id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/collocations.skn/mapping.skn/lc_publisher_id.skn/lc_publisher_id.dat
 100% - /home/dominik/ldoce5//ldoce5.data/collocations.skn/mapping.skn/publisher_id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/collocations.skn/mapping.skn/mapping.dat
 100% - /home/dominik/ldoce5//ldoce5.data/collocations.skn/dirs.skn/FILES.skn/FILES.dat
 100% - /home/dominik/ldoce5//ldoce5.data/common_errors.skn/files.skn/files.dat
 100% - /home/dominik/ldoce5//ldoce5.data/common_errors.skn/files.skn/TITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/common_errors.skn/files.skn/NAME.tda
 100% - /home/dominik/ldoce5//ldoce5.data/common_errors.skn/files.skn/TEXTTITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/common_errors.skn/files.skn/CONTENT.tda
 100% - /home/dominik/ldoce5//ldoce5.data/common_errors.skn/mapping.skn/mapping.dat
 100% - /home/dominik/ldoce5//ldoce5.data/etymologies.skn/files.skn/files.dat
 100% - /home/dominik/ldoce5//ldoce5.data/etymologies.skn/files.skn/TITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/etymologies.skn/files.skn/NAME.tda
 100% - /home/dominik/ldoce5//ldoce5.data/etymologies.skn/files.skn/TEXTTITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/etymologies.skn/files.skn/CONTENT.tda
 100% - /home/dominik/ldoce5//ldoce5.data/etymologies.skn/mapping.skn/lc_publisher_id.skn/publisher_id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/etymologies.skn/mapping.skn/lc_publisher_id.skn/lc_publisher_id.dat
 100% - /home/dominik/ldoce5//ldoce5.data/etymologies.skn/mapping.skn/publisher_id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/etymologies.skn/mapping.skn/mapping.dat
 100% - /home/dominik/ldoce5//ldoce5.data/etymologies.skn/dirs.skn/FILES.skn/FILES.dat
 100% - /home/dominik/ldoce5//ldoce5.data/examples.skn/files.skn/files.dat
 100% - /home/dominik/ldoce5//ldoce5.data/examples.skn/files.skn/TITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/examples.skn/files.skn/NAME.tda
 100% - /home/dominik/ldoce5//ldoce5.data/examples.skn/files.skn/TEXTTITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/examples.skn/files.skn/CONTENT.tda
 100% - /home/dominik/ldoce5//ldoce5.data/examples.skn/mapping.skn/lc_publisher_id.skn/publisher_id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/examples.skn/mapping.skn/lc_publisher_id.skn/lc_publisher_id.dat
 100% - /home/dominik/ldoce5//ldoce5.data/examples.skn/mapping.skn/publisher_id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/examples.skn/mapping.skn/mapping.dat
 100% - /home/dominik/ldoce5//ldoce5.data/examples.skn/dirs.skn/FILES.skn/FILES.dat
 100% - /home/dominik/ldoce5//ldoce5.data/gram.skn/files.skn/CONTENT.tda
 100% - /home/dominik/ldoce5//ldoce5.data/menus.skn/files.skn/files.dat
 100% - /home/dominik/ldoce5//ldoce5.data/menus.skn/files.skn/TITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/menus.skn/files.skn/NAME.tda
 100% - /home/dominik/ldoce5//ldoce5.data/menus.skn/files.skn/TEXTTITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/menus.skn/files.skn/CONTENT.tda
 100% - /home/dominik/ldoce5//ldoce5.data/menus.skn/mapping.skn/mapping.dat
 100% - /home/dominik/ldoce5//ldoce5.data/phrases.skn/files.skn/files.dat
 100% - /home/dominik/ldoce5//ldoce5.data/phrases.skn/files.skn/TITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/phrases.skn/files.skn/NAME.tda
 100% - /home/dominik/ldoce5//ldoce5.data/phrases.skn/files.skn/TEXTTITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/phrases.skn/files.skn/CONTENT.tda
 100% - /home/dominik/ldoce5//ldoce5.data/phrases.skn/mapping.skn/lc_publisher_id.skn/publisher_id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/phrases.skn/mapping.skn/lc_publisher_id.skn/lc_publisher_id.dat
 100% - /home/dominik/ldoce5//ldoce5.data/phrases.skn/mapping.skn/publisher_id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/phrases.skn/mapping.skn/mapping.dat
 100% - /home/dominik/ldoce5//ldoce5.data/phrases.skn/dirs.skn/FILES.skn/FILES.dat
 100% - /home/dominik/ldoce5//ldoce5.data/picture.skn/files.skn/files.dat
 100% - /home/dominik/ldoce5//ldoce5.data/picture.skn/files.skn/NAME.tda
 100% - /home/dominik/ldoce5//ldoce5.data/picture.skn/files.skn/CONTENT.tda
 100% - /home/dominik/ldoce5//ldoce5.data/picture.skn/dirs.skn/dirs.dat
 100% - /home/dominik/ldoce5//ldoce5.data/picture.skn/dirs.skn/NAME.tda
 100% - /home/dominik/ldoce5//ldoce5.data/pronpractice.skn/files.skn/files.dat
 100% - /home/dominik/ldoce5//ldoce5.data/pronpractice.skn/files.skn/TITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/pronpractice.skn/files.skn/NAME.tda
 100% - /home/dominik/ldoce5//ldoce5.data/pronpractice.skn/files.skn/TEXTTITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/pronpractice.skn/files.skn/CONTENT.tda
 100% - /home/dominik/ldoce5//ldoce5.data/pronpractice.skn/mapping.skn/lc_publisher_id.skn/publisher_id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/pronpractice.skn/mapping.skn/lc_publisher_id.skn/lc_publisher_id.dat
 100% - /home/dominik/ldoce5//ldoce5.data/pronpractice.skn/mapping.skn/lc_publisher_id.skn/lc_publisher_id.lc
 100% - /home/dominik/ldoce5//ldoce5.data/pronpractice.skn/mapping.skn/publisher_id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/pronpractice.skn/mapping.skn/mapping.dat
 100% - /home/dominik/ldoce5//ldoce5.data/pronpractice.skn/dirs.skn/FILES.skn/FILES.dat
 100% - /home/dominik/ldoce5//ldoce5.data/sound.skn/files.skn/files.dat
 100% - /home/dominik/ldoce5//ldoce5.data/sound.skn/files.skn/NAME.tda
 100% - /home/dominik/ldoce5//ldoce5.data/sound.skn/files.skn/CONTENT.tda
 100% - /home/dominik/ldoce5//ldoce5.data/sfx.skn/files.skn/CONTENT.tda
 100% - /home/dominik/ldoce5//ldoce5.data/teacher.skn/pdf.skn/files.skn/CONTENT.tda
 100% - /home/dominik/ldoce5//ldoce5.data/thesaurus.skn/files.skn/files.dat
 100% - /home/dominik/ldoce5//ldoce5.data/thesaurus.skn/files.skn/NAME.tda
 100% - /home/dominik/ldoce5//ldoce5.data/thesaurus.skn/files.skn/CONTENT.tda
 100% - /home/dominik/ldoce5//ldoce5.data/thesaurus.skn/mapping.skn/lc_publisher_id.skn/publisher_id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/thesaurus.skn/mapping.skn/lc_publisher_id.skn/lc_publisher_id.dat
 100% - /home/dominik/ldoce5//ldoce5.data/thesaurus.skn/mapping.skn/publisher_id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/thesaurus.skn/mapping.skn/mapping.dat
 100% - /home/dominik/ldoce5//ldoce5.data/thesaurus.skn/dirs.skn/FILES.skn/FILES.dat
 100% - /home/dominik/ldoce5//ldoce5.data/verb_forms.skn/files.skn/files.dat
 100% - /home/dominik/ldoce5//ldoce5.data/verb_forms.skn/files.skn/TITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/verb_forms.skn/files.skn/NAME.tda
 100% - /home/dominik/ldoce5//ldoce5.data/verb_forms.skn/files.skn/TEXTTITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/verb_forms.skn/files.skn/CONTENT.tda
 100% - /home/dominik/ldoce5//ldoce5.data/verb_forms.skn/mapping.skn/lc_publisher_id.skn/publisher_id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/verb_forms.skn/mapping.skn/lc_publisher_id.skn/lc_publisher_id.dat
 100% - /home/dominik/ldoce5//ldoce5.data/verb_forms.skn/mapping.skn/publisher_id.tda
 100% - /home/dominik/ldoce5//ldoce5.data/verb_forms.skn/mapping.skn/mapping.dat
 100% - /home/dominik/ldoce5//ldoce5.data/verb_forms.skn/dirs.skn/FILES.skn/FILES.dat
 100% - /home/dominik/ldoce5//ldoce5.data/word_lists.skn/files.skn/CONTENT.tda
 100% - /home/dominik/ldoce5//ldoce5.data/word_families.skn/files.skn/files.dat
 100% - /home/dominik/ldoce5//ldoce5.data/word_families.skn/files.skn/TITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/word_families.skn/files.skn/NAME.tda
 100% - /home/dominik/ldoce5//ldoce5.data/word_families.skn/files.skn/CONTENT.tda
 100% - /home/dominik/ldoce5//ldoce5.data/word_sets.skn/files.skn/TITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/word_sets.skn/files.skn/CONTENT.tda
Installing Recommended data files ...
 100% - /home/dominik/ldoce5//ldoce5.data/gb_hwd_pron.skn/files.skn/CONTENT.tda.tdz
 100% - /home/dominik/ldoce5//ldoce5.data/gb_hwd_pron.skn/files.skn/files.dat
 100% - /home/dominik/ldoce5//ldoce5.data/gb_hwd_pron.skn/files.skn/TITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/gb_hwd_pron.skn/files.skn/NAME.tda
 100% - /home/dominik/ldoce5//ldoce5.data/gb_hwd_pron.skn/files.skn/TEXTTITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/gb_hwd_pron.skn/files.skn/CONTENT.tda
 100% - /home/dominik/ldoce5//ldoce5.data/gb_hwd_pron.skn/dirs.skn/DIRS.skn/DIRS.dat
 100% - /home/dominik/ldoce5//ldoce5.data/gb_hwd_pron.skn/dirs.skn/dirs.dat
 100% - /home/dominik/ldoce5//ldoce5.data/gb_hwd_pron.skn/dirs.skn/NAME.tda
 100% - /home/dominik/ldoce5//ldoce5.data/gb_hwd_pron.skn/dirs.skn/FILES.skn/FILES.dat
 100% - /home/dominik/ldoce5//ldoce5.data/us_hwd_pron.skn/files.skn/CONTENT.tda.tdz
 100% - /home/dominik/ldoce5//ldoce5.data/us_hwd_pron.skn/files.skn/files.dat
 100% - /home/dominik/ldoce5//ldoce5.data/us_hwd_pron.skn/files.skn/TITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/us_hwd_pron.skn/files.skn/NAME.tda
 100% - /home/dominik/ldoce5//ldoce5.data/us_hwd_pron.skn/files.skn/TEXTTITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/us_hwd_pron.skn/files.skn/CONTENT.tda
 100% - /home/dominik/ldoce5//ldoce5.data/us_hwd_pron.skn/dirs.skn/DIRS.skn/DIRS.dat
 100% - /home/dominik/ldoce5//ldoce5.data/us_hwd_pron.skn/dirs.skn/dirs.dat
 100% - /home/dominik/ldoce5//ldoce5.data/us_hwd_pron.skn/dirs.skn/NAME.tda
 100% - /home/dominik/ldoce5//ldoce5.data/us_hwd_pron.skn/dirs.skn/FILES.skn/FILES.dat
Installing Full data files ...
 100% - /home/dominik/ldoce5//ldoce5.data/exa_pron.skn/files.skn/CONTENT.tda.tdz
 100% - /home/dominik/ldoce5//ldoce5.data/exa_pron.skn/files.skn/files.dat
 100% - /home/dominik/ldoce5//ldoce5.data/exa_pron.skn/files.skn/TITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/exa_pron.skn/files.skn/NAME.tda
 100% - /home/dominik/ldoce5//ldoce5.data/exa_pron.skn/files.skn/TEXTTITLE.tda
 100% - /home/dominik/ldoce5//ldoce5.data/exa_pron.skn/files.skn/CONTENT.tda
 100% - /home/dominik/ldoce5//ldoce5.data/exa_pron.skn/dirs.skn/FILES.skn/FILES.dat
 Fixing data
 Install fonts
cp: nelze vytvo&#345;it oby&#269;ejný soubor „/home/dominik/.fonts/AWLPhonetics3U.TTF“: Operace zamítnuta
./fonts.scale: fopen(w): Permission denied
./fonts.dir: fopen(w): Permission denied
 Install desktop shortcut
rm: nelze odstranit „/home/dominik/Desktop/ldoce5.desktop“: Operace zamítnuta
setup.data/desktop_icon.sh: &#345;ádek 6: /home/dominik/Desktop/ldoce5.desktop: Operace zamítnuta
setup.data/desktop_icon.sh: &#345;ádek 7: /home/dominik/Desktop/ldoce5.desktop: Operace zamítnuta
setup.data/desktop_icon.sh: &#345;ádek 8: /home/dominik/Desktop/ldoce5.desktop: Operace zamítnuta
setup.data/desktop_icon.sh: &#345;ádek 9: /home/dominik/Desktop/ldoce5.desktop: Operace zamítnuta
setup.data/desktop_icon.sh: &#345;ádek 10: /home/dominik/Desktop/ldoce5.desktop: Operace zamítnuta
setup.data/desktop_icon.sh: &#345;ádek 11: /home/dominik/Desktop/ldoce5.desktop: Operace zamítnuta
setup.data/desktop_icon.sh: &#345;ádek 12: /home/dominik/Desktop/ldoce5.desktop: Operace zamítnuta
setup.data/desktop_icon.sh: &#345;ádek 13: /home/dominik/Desktop/ldoce5.desktop: Operace zamítnuta
setup.data/desktop_icon.sh: &#345;ádek 14: /home/dominik/Desktop/ldoce5.desktop: Operace zamítnuta
setup.data/desktop_icon.sh: &#345;ádek 15: /home/dominik/Desktop/ldoce5.desktop: Operace zamítnuta
loki_setup: Script seems to have failed with error code 1.

Installation complete.

```

There is a bunch of "Operation denied" ( ="Operace zamítnuta") in the last paragraph. And "unable to create a simple file" (="nelze vytvo&#345;it oby&#269;ejný soubor"):confused:

I can run the ldoce5.sh, it shows the menu but then it doesn't respond to anything. The terminal log goes like this:

```
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"

(ldoce5-bin:5989): Gtk-WARNING **: Nelze nalézt systém motiv&#367; v module_path: "murrine",

(ldoce5-bin:5989): Gtk-WARNING **: Nelze nalézt systém motiv&#367; v module_path: "murrine",

(ldoce5-bin:5989): Gtk-WARNING **: Nelze nalézt systém motiv&#367; v module_path: "pixmap",

(ldoce5-bin:5989): Gtk-WARNING **: Nelze nalézt systém motiv&#367; v module_path: "pixmap",

(ldoce5-bin:5989): Gtk-WARNING **: Nelze nalézt systém motiv&#367; v module_path: "murrine",

(ldoce5-bin:5989): Gtk-WARNING **: Nelze nalézt systém motiv&#367; v module_path: "murrine",

(ldoce5-bin:5989): Gtk-WARNING **: Nelze nalézt systém motiv&#367; v module_path: "pixmap",

(ldoce5-bin:5989): Gtk-WARNING **: Nelze nalézt systém motiv&#367; v module_path: "murrine",

(ldoce5-bin:5989): Gtk-WARNING **: Nelze nalézt systém motiv&#367; v module_path: "murrine",

(ldoce5-bin:5989): Gtk-WARNING **: Nelze nalézt systém motiv&#367; v module_path: "murrine",

(ldoce5-bin:5989): Gtk-WARNING **: Nelze nalézt systém motiv&#367; v module_path: "murrine",

(ldoce5-bin:5989): Gtk-WARNING **: Nelze nalézt systém motiv&#367; v module_path: "murrine",

(ldoce5-bin:5989): Gtk-WARNING **: Nelze nalézt systém motiv&#367; v module_path: "murrine",

(ldoce5-bin:5989): Gtk-WARNING **: Nelze nalézt systém motiv&#367; v module_path: "murrine",

(ldoce5-bin:5989): Gtk-WARNING **: Nelze nalézt systém motiv&#367; v module_path: "murrine",

(ldoce5-bin:5989): Gtk-WARNING **: Nelze nalézt systém motiv&#367; v module_path: "murrine",

(ldoce5-bin:5989): Gtk-WARNING **: Nelze nalézt systém motiv&#367; v module_path: "murrine",

(ldoce5-bin:5989): Gtk-WARNING **: Nelze nalézt systém motiv&#367; v module_path: "murrine",

(ldoce5-bin:5989): Gtk-WARNING **: Nelze nalézt systém motiv&#367; v module_path: "murrine",

(ldoce5-bin:5989): Gtk-WARNING **: Nelze nalézt systém motiv&#367; v module_path: "murrine",

(ldoce5-bin:5989): Gtk-WARNING **: Nelze nalézt systém motiv&#367; v module_path: "murrine",

(ldoce5-bin:5989): Gtk-WARNING **: Nelze nalézt systém motiv&#367; v module_path: "murrine",

(ldoce5-bin:5989): Gtk-WARNING **: Nelze nalézt systém motiv&#367; v module_path: "murrine",

(ldoce5-bin:5989): Gtk-WARNING **: Nelze nalézt systém motiv&#367; v module_path: "murrine",

(ldoce5-bin:5989): Gtk-WARNING **: Nelze nalézt systém motiv&#367; v module_path: "murrine",

(ldoce5-bin:5989): Gtk-WARNING **: Nelze nalézt systém motiv&#367; v module_path: "pixmap",
Gtk-Message: Failed to load module "canberra-gtk-module"
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: chybná t&#345;ída ELF:&#8239;ELFCLASS64

(ldoce5-bin:5989): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: chybná t&#345;ída ELF:&#8239;ELFCLASS64

(ldoce5-bin:5989): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

```

When I run the installation **with sudo**, I am not allowed to choose the folder to install to. Ldoce is installed into /root and I can't access the program at all.

Do you have any ideas, what might be wrong? Thank you.

---

### Post by tinyram on 2013-01-14
> **rh1363 said:**
> I installed LDOCE5 completely.
but after I running, I'll see warning message. That is:
please insert the LDOCE DVD-ROM to access this feature
I don't want use DVD always.
How can I use this dictionary without mounting it's DVD?

Hello,
1. Create iso from your DVD named **ldoce5.iso**.
**If uder KDE**
[http://vivapinkfloyd.blogspot.com/2008/07/how-to-create-cddvd-iso-images-with-k3b.html](http://vivapinkfloyd.blogspot.com/2008/07/how-to-create-cddvd-iso-images-with-k3b.html)

2. Put that ldoce5.iso into /home/**YOUR-USER-NAME**/ldoce5

3. create **LDOCE5** folder if needed under **/media**, ie **/media/LDOCE5**
not shure is that crucial under Ubuntu: 
if your media sounds like tmpfs, see /etc/mtab for string like **tmpfs /media ....**, you may try to skip this step

4. revise your **/etc/fstab** file adding the following lines

# LDOCE5 only here to mount (any comment)
/home/**YOUR-USER-NAME**/ldoce5/ldoce5.iso  /media/LDOCE5 iso9660 ro,loop,user,noauto,uid=1000 0 0

5. reboot, try and let us know how it goes

6. Greetings from OpenSuse! ;)

---

### Post by tinyram on 2013-01-14
> **dom1n1cus said:**
> Hello folks,

I got a brand new Longman dictionary for Christmas, but I am unable to install the electronic version on my system. I followed the instructions, but there seem to be some trouble with permissions. When I go for it **without sudo**, the result is like this:

Do you have any ideas, what might be wrong? Thank you.

Hello Dominik,

1. You are correct, no need in **sudo**
2.> Install fonts cp: nelze vytvo&#345;it oby&#269;ejný soubor „/home/dominik/.fonts/AWLPhonetics3U.TTF“: Operace zamítnuta ./fonts.scale: fopen(w): Permission denied ./fonts.dir: fopen(w): Permission denied  Install desktop shortcutSeems like you already have that font installed in .fonts dir
If all goes OK there must be 3 files
file:///home/**YOUR-USER-NAME**/.fonts/AWLPhonetics3U.TTF
file:///home/**YOUR-USER-NAME**/.fonts/fonts.dir
file:///home/**YOUR-USER-NAME**/.fonts/fonts.scale

3. > rm: nelze odstranit  „/home/dominik/.macromedia/Flash_Player/#Security/FlashPlayerTrust/ldoce5.cfg“:  Operace zamítnuta setup.data/set_flash_security_file.sh: &#345;ádek 9:  /home/dominik/.macromedia/Flash_Player/#Security/FlashPlayerTrust/ldoce5.cfg:  Operace zamítnuta loki_setup: Script seems to have failed with error  code 1.> the menu but then it doesn't respond to anything.To make menu operational 
4.1 check for **canberra-gtk**-module installation 
4.2 create 
file:///home/**YOUR-USER-NAME**/.macromedia/Flash_Player/#Security/FlashPlayerTrust/**ldoce5.cfg** with one string ```
/home/**YOUR-USER-NAME**/ldoce5
```5.
> rm: nelze odstranit „/home/dominik/Desktop/ldoce5.desktop“: Operace zamítnutaCreate the "**link to application**" manually, put in command fileld
```
aoss '/home/**YOUR-USER-NAME**/ldoce5//ldoce5'
```5. Let us know how it goes.

---

### Post by kmajaa on 2013-07-15
> **eltama said:**
> After spending some time I managed to install the Longman Dictionary of Contemporary English 5th edition (LDOCE5) on Ubuntu 9.10 (Karmic Koala) 64-bit and I want to share my experience.

On the cd there is a file LINUX_README.txt which says that if you want to launch the installer in graphical mode you have to install libgtk1.2. libgtk1.2 is not available in Karmic (see [https://bugs.launchpad.net/ubuntu/+source/gtk+1.2/+bug/478219](https://bugs.launchpad.net/ubuntu/+source/gtk+1.2/+bug/478219)) and although there are ways to install it (e.g. [http://www.rabbnix.com/vb/showthread.php?t=979](http://www.rabbnix.com/vb/showthread.php?t=979)), it is easier to install it from the console.

According to [http://pearsonsupport.helpserve.com/index.php?_m=knowledgebase&_a=viewarticle&kbarticleid=115](http://pearsonsupport.helpserve.com/index.php?_m=knowledgebase&_a=viewarticle&kbarticleid=115), LDOCE5 should work on Ubuntu 9.04+ on both architectures. However, when I tried to run linux/setup.sh, I got following error:
After investigating the script setup.sh I noticed that it determines the architecture (amd64 or x86), and it uses that value to construct a path to the actual installer, e.g. linux/setup.data/bin/Linux/x86/setup. However, there is no linux/setup.data/bin/Linux/amd64/ directory.

**UPDATE**: I found an easier way to make the installer work than the one described on the next paragraph. Just run from the linux directory ```
linux32 ./setup.sh
```

Since I had nothing to lose, I though about executing the installer for the x86 version. So I copied the whole cd to the hard disk, and renamed ldoce5/linux/setup.data/bin/Linux/x86/ to ldoce5/linux/setup.data/bin/Linux/amd64/. Then I ran ldoce5/linux/setup.sh (after adding execute permission to setup.sh). A terminal-based installer launched with the message "You are running an x86 machine with glibc-2.1", I pressed OK, then I agreed with the licence and chose the instalation directory. Then the installer did it's work.

I went to the directory where it installed the dictionary and with my fingers crossed I run ldoce5. To my surprise it worked!

Most things work fine: sounds, links, nice fonts. The only problem I found is that on the "Teacher Resouces" section, the links to the pdfs do not work, however, they can be directly accessed in ldoce5/chrome/ldoce5/pdfs.

**UPDATE 2**:
.It also works on Ubuntu 10.04 and 10.10.

.You need the Adobe Flash Plugin, otherwise sound will not work. It's also recommended to have Pulse Audio.

.If you want to back it up, besides the installation directory backup the .font directory (optional), and the file ~/.macromedia/Flash_Player/#Security/FlashPlayerTrust/ldoce5.cfg, which only contains the path to the ldoce5 installation, for instance, /usr/share/ldoce5/. If you don't have this file you will be able to open the program but when you click on the main menu nothing will happen. You can create it yourself if you don't have it.

.This made me realize that to if you want to execute through wine a version that has been installed in Windows, all you need to do is add the executable to the allowed applications on wine's flash. The result is not the same, it flickers more, but you can save 2.5 GB of space.

**UPDATE 3**:
The Copy button at the top does not work, neither does Ctrl-c. To copy some text, select it and press Ctrl-Insert.

I use Ubuntu 13.04 64-bit.

I managed to install it more or less the same way you described. I copied the folders "linux" and "setup.data" to my HDD into /tmp/ldoce5. The difference was that when I changed the name of "x86" to "amd64" and tried to install it, there was some problem during installation referring to x86, so I made a copy of this folder and now had two folders with the exact same content - one named "x86" and the other "amd64". I ran the installation again with the command: ```
sudo linux ./setup.sh
```. And it worked, only the sound is not working (yes, I've got Flash installed...), but I've got used to it as I tried to fix it on my previous laptop with Ubuntu 12.04  trying many different methods (alsa, reinstalling flash among others) and to no avail, so I rest my case.

---

### Post by afshin3 on 2014-03-30
Can I ask you how can I set permission on Setup.sh ?? I'm new to ubuntu and using terminal is very confusing for me. thanks in advance ;)

---

### Post by afshin3 on 2014-03-30
[COLOR=#000000]Can I ask you how can I set permission on Setup.sh ?? I'm new to ubuntu and using terminal is very confusing for me. thanks in advance [/COLOR]:wink:

---

### Post by zinebl-90 on 2014-09-27
Hi 

in my case i have this msg:
[HTML]The setup program seems to have failed on amd64/unknown 
Fatal error, no tech support email configured in this setup[/HTML]

so there is no glibc-2.1 in my system , in order to install it just go to the synaptic and search for libc6 
1- install theadequat packages, 
2- than search for glibc-2.1 and install the both packages found in synaptic
3- go to the terminal and paste :
root@!!!!!:/media/!!!!!!/sda7/STP/LDCE5/L/linux# sudo sh setup.sh

thanks

---

### Post by toopho on 2015-06-27
I am using Debian 8.0 which went freeze in early Nov 2015 so I guess I am using a distro very similar to the official Ubuntu 14.10 release.

I have followed the instructions here and after creating a copy of the x86 folder called amd64 in the same directory the error became:

```
./setup.sh: 201: ./setup.sh: /home/un/.setup5401: not found
The setup program seems to have failed on amd64/unknown

Fatal error, no tech support email configured in this setup
```

Then, I installed the package “libc6-i386”. But I couldn't find anything similar to “glibc-2.1”.

After that, I launched setup.sh again and the installation begun, I accepted the licence, and it seemed to go well through all the installation process until the last few lines:

```
 100% - /home/un/ldoce5//ldoce5.data/exa_pron.skn/dirs.skn/FILES.skn/FILES.dat
 Fixing data
 Install fonts
cp: cannot stat ‘setup.data/AWLPhonetics3U.TTF’: No such file or directory
 Install desktop shortcut

Installation complete.
```

When I tried to start the dictionary the following error message prompts:

```
./ldoce5/ldoce5-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
```

I am wondering if I can still find those old libraries in the newer versions of Ubuntu and Debian. Thanks for reading my post.

---

### Post by arapaho on 2015-11-13
I have the same problem on 14.04
```
sh run-ldoce5.sh
./ldoce5-bin: error while loading shared libraries: **libgtk-x11-2.0.so.0:** cannot open shared object file: No such file or directory
```
Anyone succeeded?

---

