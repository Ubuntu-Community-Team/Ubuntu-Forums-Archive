---
title: "*has just gotten his blackberry to sync with Ubuntu*"
date: 2008-08-04
forum: The Cafe
---

### Post by Lord Xeb on 2008-08-04
AWESOME!!!! >_> Took me about 2 hours to figure it all out, but once I did, worked like a charm.... it also charges. 

Also this guide (programs) will work the following devices: 
Molorola 
Windows CE devices
Nokia Mobile Devices
Opie
IrMC Mobile Devices
SyncML over HTTP
SyncML over OBEX Client
Palm Devices
And synchronization with handhelds using GPE
:p

> First off, you will have to download some software and have a little bit of fun trying to get it all to work:

I used this site to get them and get some help configuring the parts and pieces: [http://www.linux.com/feature/123251](http://www.linux.com/feature/123251)

Now then, the parts and pieces.

You will need to add in these source files into the repositories: 
```
echo 'deb [http://opensync.gforge.punktart.de/repo/opensync-0.21/](http://opensync.gforge.punktart.de/repo/opensync-0.21/) feisty main'  |  sudo tee -a /etc/apt/sources.list
echo 'deb-src [http://opensync.gforge.punktart.de/repo/opensync-0.21/](http://opensync.gforge.punktart.de/repo/opensync-0.21/) feisty main'  |  sudo tee -a /etc/apt/sources.list
```Upate: I forgot that you need keys: ```
 gpg --keyserver [hkp://subkeys.pgp.net/]("http://subkeys.pgp.net/") --recv-keys CB210090B029CB84
gpg --export CB210090B029CB84 | sudo apt-key add -
```Then do:

```
sudo apt-get update
```Now download the packages that are needed. I will just tell you how to do it with the synaptic. Just go and type in in 'opensync' and install all the packages that are '0.22-feisty'. I know, you are not supposed to mix the repos but this is the only way. Also, I recommend installing kitchensync since it is easier to use than the gui provided with msynctool.


Next, we need to make sure we have the libusb libraries:

```
sudo apt-get install libusb-0.1-4 libusb++-0.1-4c2 libusb-dev libusb++-dev
```Next, download and install the following (I will post the universal ones (the kind that can be used on most Ubuntu varients):

[http://downloads.sourceforge.net/barry/libbarry_0.13-1.2_i386.deb?modtime=1217433545&big_mirror=0](http://downloads.sourceforge.net/barry/libbarry_0.13-1.2_i386.deb?modtime=1217433545&big_mirror=0)

[http://downloads.sourceforge.net/barry/barrybackup-gui_0.13-1.2_i386.deb?modtime=1217433325&big_mirror=0](http://downloads.sourceforge.net/barry/barrybackup-gui_0.13-1.2_i386.deb?modtime=1217433325&big_mirror=0)

[http://downloads.sourceforge.net/barry/barry-util_0.13-1.2_i386.deb?modtime=1217433460&big_mirror=0](http://downloads.sourceforge.net/barry/barry-util_0.13-1.2_i386.deb?modtime=1217433460&big_mirror=0)

[http://downloads.sourceforge.net/barry/libbarry-dev_0.13-1.2_i386.deb?modtime=1217433629&big_mirror=0](http://downloads.sourceforge.net/barry/libbarry-dev_0.13-1.2_i386.deb?modtime=1217433629&big_mirror=0)

[http://downloads.sourceforge.net/barry/libopensync-plugin-barry_0.13-1.2_i386.deb?modtime=1217433710&big_mirror=0](http://downloads.sourceforge.net/barry/libopensync-plugin-barry_0.13-1.2_i386.deb?modtime=1217433710&big_mirror=0)

Or you could download the attached file on this post. Either way will work just fine.

You must install the first link before you can install any of the others.


Since that is all out of the way, we need to get down to business. First off, you must find out the PIN number of your  device. You can do that by simply going to terminal and typing after connecting your device: 

```
btool -d 'Browser Folders'
```It should give you a readout like this: 
```
nathan@nathan-laptop:~$ btool -d 'Browser Folders'
Blackberry devices found:
Device ID: 0x809ea00. PIN: 123ee774, Description: RIM 8100 Series Colour CDMA Handheld
Using device (PIN): 319ee762
Raw record dump for record: 8a17e602
    00000000: 06 00 26 00 40 02 44 01 01 00 02 e6 17 8a 00 14  ..&.@.D.........
    00000010: 00 00 81 d6 e2 b7 60 00 0d 57 41 50 20 42 6f 6f  ......`..WAP Boo
    00000020: 6b 6d 61 72 6b 73                                kmarks

Raw record dump for record: 2c692a88
    00000000: 06 00 2d 00 40 02 44 01 02 00 88 2a 69 2c 00 1b  ..-.@.D....*i,..
    00000010: 00 00 81 d6 e2 b7 60 00 14 42 6c 61 63 6b 42 65  ......`..BlackBe
    00000020: 72 72 79 20 42 6f 6f 6b 6d 61 72 6b 73           rry Bookmarks

```Where it says 'PIN; Then a series of numbers in HEX (ex: 123ee774). That is your PIN. Next, lets make a backup of your blackberry shall we? Go to terminal and type the following while your blackberry is plugged into your computer:

```
barrybackup
```You will get a window that looks like below:
[IMG]http://www.linux.com/var/uploads/Image/articles/123251-1.png[/IMG]


It should see your device and put the pin in automatically, if not, just enter in your PIN, and click 'backup'. You can put this just about anywhere you want. just got to configure it. I will let you figure it out since it is rather straight forward.

Next, lets setup msynctool. Just type in the following:

```
msynctool --addgroup Blackberry
msynctool --addmember Blackberry barry-sync
msynctool --addmember Blackberry file-sync
msynctool --showgroup Blackberry
```This will get that up and going but it still needs to be configured for it to sync.

Do the following to do that:

```
msynctool --configure Blackberry 1
```The 1 stands for the first 'member' that you added, which will be the barry-sync. You will get something like what is down in the attachments. The here you see '319ee762' that is where you put your PIN (again) and you are set (well, if you have a password, add that into by how it says, if not, remove it completely). Next, we want to set up the file-sync:


 ```
msynctool --configure Blackberry 2
```You should get something like this:

```
<config><path>Path_to_where_you_want_your_stuff_to_go</path><recursive>FALSE</recursive></co$

```There, now you are ready to go. Have fun and feel free to experiment. Also, feel free to give me feedback on anything I need to fix or add.  


I give thanks to Joe Barr who created that article.

---

### Post by kevin11951 on 2008-08-04
> **Lord Xeb said:**
> AWESOME!!!! >_> Took me about 2 hours to figure it all out, but once I did, worked like a charm.... it also charges. :p

please tell me how! there is a guy in a group of mine trying out linux, and he is having trouble with his computer and his blackberry.

---

### Post by Vishal Agarwal on 2008-08-04
I am also interested to know how ?

---

### Post by backupdevice on 2008-08-04
You are my hero !!!

---

### Post by tiachopvutru on 2008-08-04
Please tell, although I don't have a Blackberry, I'm interested in knowing since my sister has one.

---

### Post by Lord Xeb on 2008-08-04
First off, you will have to download some software and have a little bit of fun trying to get it all to work:

I used this site to get them and get some help configuring the parts and pieces: [http://www.linux.com/feature/123251](http://www.linux.com/feature/123251)

Now then, the parts and pieces.

You will need to add in these source files into the repositories: 
```
echo 'deb [http://opensync.gforge.punktart.de/repo/opensync-0.21/](http://opensync.gforge.punktart.de/repo/opensync-0.21/) feisty main'  |  sudo tee -a /etc/apt/sources.list
echo 'deb-src [http://opensync.gforge.punktart.de/repo/opensync-0.21/](http://opensync.gforge.punktart.de/repo/opensync-0.21/) feisty main'  |  sudo tee -a /etc/apt/sources.list
```Then do:

```
sudo apt-get update
```Now download the packages that are needed. I will just tell you how to do it with the synaptic. Just go and type in in 'opensync' and install all the packages that are '0.22-feisty'. I know, you are not supposed to mix the repos but this is the only way. Also, I recommend using kitchensync since it is much easier and nicer to use than the gui provided for msynctool.


Next, we need to make sure we have the libusb libraries:

```
sudo apt-get install libusb-0.1-4 libusb++-0.1-4c2 libusb-dev libusb++-dev
```Next, download and install the following (I will post the universal ones (the kind that can be used on most Ubuntu varients):

[http://downloads.sourceforge.net/barry/libbarry_0.13-1.2_i386.deb?modtime=1217433545&big_mirror=0](http://downloads.sourceforge.net/barry/libbarry_0.13-1.2_i386.deb?modtime=1217433545&big_mirror=0)

[http://downloads.sourceforge.net/barry/barrybackup-gui_0.13-1.2_i386.deb?modtime=1217433325&big_mirror=0](http://downloads.sourceforge.net/barry/barrybackup-gui_0.13-1.2_i386.deb?modtime=1217433325&big_mirror=0)

[http://downloads.sourceforge.net/barry/barry-util_0.13-1.2_i386.deb?modtime=1217433460&big_mirror=0](http://downloads.sourceforge.net/barry/barry-util_0.13-1.2_i386.deb?modtime=1217433460&big_mirror=0)

[http://downloads.sourceforge.net/barry/libbarry-dev_0.13-1.2_i386.deb?modtime=1217433629&big_mirror=0](http://downloads.sourceforge.net/barry/libbarry-dev_0.13-1.2_i386.deb?modtime=1217433629&big_mirror=0)

[http://downloads.sourceforge.net/barry/libopensync-plugin-barry_0.13-1.2_i386.deb?modtime=1217433710&big_mirror=0](http://downloads.sourceforge.net/barry/libopensync-plugin-barry_0.13-1.2_i386.deb?modtime=1217433710&big_mirror=0)

You must install the first link before you can install any of the others.


Since that is all out of the way, we need to get down to business. First off, you must find out the PIN number of your  device. You can do that by simply going to terminal and typing after connecting your device: 

```
btool -d 'Browser Folders'
```It should give you a readout like this: 
```
nathan@nathan-laptop:~$ btool -d 'Browser Folders'
Blackberry devices found:
Device ID: 0x809ea00. PIN: 123ee774, Description: RIM 8100 Series Colour CDMA Handheld
Using device (PIN): 319ee762
Raw record dump for record: 8a17e602
    00000000: 06 00 26 00 40 02 44 01 01 00 02 e6 17 8a 00 14  ..&.@.D.........
    00000010: 00 00 81 d6 e2 b7 60 00 0d 57 41 50 20 42 6f 6f  ......`..WAP Boo
    00000020: 6b 6d 61 72 6b 73                                kmarks

Raw record dump for record: 2c692a88
    00000000: 06 00 2d 00 40 02 44 01 02 00 88 2a 69 2c 00 1b  ..-.@.D....*i,..
    00000010: 00 00 81 d6 e2 b7 60 00 14 42 6c 61 63 6b 42 65  ......`..BlackBe
    00000020: 72 72 79 20 42 6f 6f 6b 6d 61 72 6b 73           rry Bookmarks

```Where it says 'PIN; Then a series of numbers in HEX (ex: 123ee774). That is your PIN. Next, lets make a backup of your blackberry shall we? Go to terminal and type the following while your blackberry is plugged into your computer:

```
barrybackup
```You will get a window that looks like below:
[IMG]http://www.linux.com/var/uploads/Image/articles/123251-1.png[/IMG]


It should see your device and put the pin in automatically, if not, just enter in your PIN, and click 'backup'. You can put this just about anywhere you want. just got to configure it. I will let you figure it out since it is rather straight forward.

Next, lets setup msynctool. Just type in the following:

```
msynctool --addgroup Blackberry
msynctool --addmember Blackberry barry-sync
msynctool --addmember Blackberry file-sync
msynctool --showgroup Blackberry
```This will get that up and going but it still needs to be configured for it to sync.

Do the following to do that:

```
msynctool --configure Blackberry 1
```The 1 stands for the first 'member' that you added, which will be the barry-sync. You will get something like what is down in the attachments. The here you see '319ee762' that is where you put your PIN (again) and you are set (well, if you have a password, add that into by how it says, if not, remove it completely). Next, we want to set up the file-sync:


```
msynctool --configure Blackberry 2
```You should get something like this:

```
<config><path>Path_to_where_you_want_your_stuff_to_go</path><recursive>FALSE</recursive></co$

```There, now you are ready to go. Have fun and feel free to experiment. Also, feel free to give me feedback on anything I need to fix or add.  


I give thanks to Joe Barr who created that article.

---

### Post by Polygon on 2008-08-04
i suggest you put this on the ubuntu wiki as well, google seems to like the wiki better for archiving then the forums =)

---

### Post by OutOfReach on 2008-08-04
Cool, I'll have to try this, I'll post back the results.

---

### Post by OutOfReach on 2008-08-04
Well, the computer and the blackberry seem to communicate with each other well (since backing up my blackberry worked). But my Blackberry Pearl reboots a couple of 10-20 seconds after the computer or a command probes it (for example, when I type 'btool -d 'Browser Folders'). Any suggestions?

---

### Post by Lord Xeb on 2008-08-04
Hmmm... I have a perl as well but it does not do that. Check the security on the phone in the options and see if there is anything funky.

---

### Post by OutOfReach on 2008-08-04
I just looked through the settings, nothing seems out of place. Ideas?

---

### Post by Lord Xeb on 2008-08-06
Post all settings and the commands used. There must be a feature turned on someplace. This may take a while for you to write down all of these but it is the best way too see wat is causing it.

---

### Post by OutOfReach on 2008-08-08
Sorry was kind of busy anyways I attached everything that was under the Security Options.

---

### Post by Lord Xeb on 2008-08-08
Hmmm....  I will look into it and get back too if I find anything since everything is EXACTLY the same on my phone. Post the config file of the barry sync in Multisync/KitchenSync and send your PIN in a private message since it could be used to track you/hack your phone.

---

### Post by S0VERE1GN on 2008-08-08
charles@charles-laptop:~$ msynctool --addmember Blackberry file-sync
Unable to instance plugin with name file-sync: Unable to find the plugin "file-sync"

how do i fix that?

---

### Post by itmanvn on 2008-08-11
> **S0VERE1GN said:**
> charles@charles-laptop:~$ msynctool --addmember Blackberry file-sync
Unable to instance plugin with name file-sync: Unable to find the plugin "file-sync"

how do i fix that?

You must download the plugin here: [http://www.opensync.org/wiki/download](http://www.opensync.org/wiki/download) (scroll to bottom of that page)

If you want to sync BB Evolution: [http://ubuntuforums.org/showpost.php?p=5565392&postcount=5](http://ubuntuforums.org/showpost.php?p=5565392&postcount=5) :popcorn:

---

### Post by TroyDowling on 2008-08-13
Huzzah! Got it all to sync beautifully. Ha, I think... I didn't really notice any changes really, but judging by the console output, I gained about thirty entries of something... :P Thanks for all the help and support, this is a great guide. Anyone know how I can utilize this for installing applications? Right now I have to boot a Windows VM to use the Desktop Software...

---

### Post by OutOfReach on 2008-08-13
Gah, almost forgot to say that my Blackberry actually works now, it doesn't reboot anymore O.o, which seems weird, but hey it works so thanks for the help Lord Xeb. :D

---

### Post by Lord Xeb on 2008-08-14
Alright, glade to hear it. I do not know why yours was acting up and mine didn't...

---

### Post by DoctorMO on 2008-08-14
Three cheers for Chris Frey!

It'll be nice when the hardware hal stuff is in place for all syncable phones and such. So you know... plug and play type thing. But for now that only works with my computer under hackishness.

There is a long road to travel for sync support; I'm having trouble finding something to sync my blackberry _to_ since none of the linux based contact or calendars are very good. either tied to gui, tied to an app or tied to a kde/gnome all using non standard formats and fields. Meh.

---

### Post by blazercist on 2008-08-14
Does this work with Verizon curve, I see you are using barry and I read somewhere they havent added the pci id for the verizon version of the curve.

---

### Post by Lord Xeb on 2008-08-14
> **blazercist said:**
> Does this work with Verizon curve, I see you are using barry and I read somewhere they havent added the pci id for the verizon version of the curve.
It works with my Verizon perl, I do not see why it wouldn't work with a curve. There is just only one way to see and that is to try it. Just remember to enter in the PIN correctly >_>

---

### Post by Greydog on 2008-08-14
I'm not sure where I went wrong but, I get a bash: btool: command not found error.
I tried to cd /usr/share/barry and tried again but, it still gave the same error.
Got any ideas?
Thanks for the post though. I just got my Curve last week and I really don't want to use the LW's Windows machine. 
Thanks for any help,
Greydog

---

### Post by Greydog on 2008-08-15
*Bump*

---

### Post by Lord Xeb on 2008-08-16
Go through and redo everything all over and that usually will fix things. If not, let me know.

Also, post what you put into the terminal (just copy and post)

---

### Post by TroyDowling on 2008-08-17
Sorry for this post. I made a bonehead mistake... ignore or delete please!

---

### Post by Greydog on 2008-08-19
Hi Xeb..er Lord,
Sorry I haven't gotten back to you. Out of town.
I'll try as you suggested after work and get back to you.
Greydog

---

### Post by Greydog on 2008-08-19
Lord Xeb
I redid everything as you sugested and volia'!
I think I misses the "key" step before.
Thanks for the help and thanks for your work.
Greydog

---

### Post by Lord Xeb on 2008-08-19
You are very welcome. Anytime :D Have fun.

---

### Post by danish77 on 2008-09-14
has anyone been able to use the file-sync plugin to sync files in the device memory (/Device Memory/home/user/blah)?
i have every other plugin that i want working (Curve 8330 w/ v4.3.0.127) and file-sync seems to work but i'm not sure what files it's looking at by default or how to aim it at the device memory
tia,
danish

---

### Post by Lord Xeb on 2008-09-14
No. I have not. Instead i just got a microSD card for like 12 bucks :D 2GB and used that

---

### Post by jack frost on 2008-09-23
What model perl do you have?

---

### Post by Lord Xeb on 2008-09-24
I think it is an 8330.... but I do not remember

---

### Post by zippypickle on 2008-09-25
I have an 8100 series Pearl, and this is the third install that didn't work.  I can get BarryBackup to work fine, and the evolution synchronization initiates, but my Blackberry restarts itself after 30 seconds of being connected.  It is fine just charging off of the computer, but something about accessing the BB through the msynctool triggers a restart.

I know this has affected many others, as this seems like a common theme voiced in many forums.  But I'm still frustrated by this!   I just want to synchronize my evolution calendar with my BlackBerry!  What a pain!

Anyone who has overcome this problem (other than reinstalling everything) please post what you did.  Pretty pretty please with a cherry on top!

Thanks-
Zipp.

---

### Post by Lord Xeb on 2008-09-25
Actually... I have an 8130. I do not have any problems. I just did what I did above thats it. Try updating the OS on your berry.

---

