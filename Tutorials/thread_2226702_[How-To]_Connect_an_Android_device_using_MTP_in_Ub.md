---
title: "[How-To] Connect an Android device using MTP in Ubuntu 14.04 LTS"
date: 2014-05-28
forum: Tutorials
---

### Post by jdarby1983 on 2014-05-28
Hi,

After much looking around I was never able to find a how-to guide(or should I say the ones that did never worked)on how to connect my android tablet/phone to Ubuntu for file transfers, sure there's other means of doing it wireless via your LAN, but truth be told MTP and Ubuntu don't exactly see eye to eye and as such I hope the following guide I put together saves someone a lot of time and effort. This was performed on Ubuntu 14.04 LTS

**[COLOR=#000000]STEP 1[/COLOR]**
Firstly we're going to need to install some of the common MTP apps that will be needed. Open up a terminal and type the following two lines one after the other.

```
sudo apt-get install libmtp-common mtp-tools libmtp-dev libmtp-runtime libmtp9
```
```
sudo apt-get dist-upgrade
```

**[COLOR=#000000]STEP 2[/COLOR]**
Then we're going to amend the fuse.conf file. FUSE is an application that aims to provide a secure method for non privileged users to create and mount their own file system implementations. This option overrides  the  security  measure  restricting  file access  to  the  user  mounting  the  file system.  So all users (including root) can access the files. This option is by default only allowed to root, but this restriction can be removed with a change to the aforementioned fuse.conf file as follows:

At the terminal type

```
sudo nano /etc/fuse.conf
```

We want to remove the # from the below line of code for user_allow_other, like so...

```
#/etc/fuse.conf - Configuration file for Filesystem in Userspace (FUSE)

#Set the maximum number of FUSE mounts allowed to non-root users.
#The default is 1000.
#mount_max = 1000

# Allow non-root users to specify the allow_other or allow_root mount options.
user_allow_other
```


Now save the file by pressing Ctrl+x, press Y and then Enter.

**[COLOR=#000000]STEP 3[/COLOR]**

We now need to set up some rules for our device that we plan on connecting, but before we do that we need to find out both the vendor and product id

Connect your device via an available usb port and from terminal enter

```
lsusb
```
This should bring up an output similar to the following

```
Bus 002 Device 003: ID 0fce:01b1 Sony Ericsson Mobile Communications AB 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 0461:4d65 Primax Electronics, Ltd 
Bus 001 Device 005: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]

```

You need to look for your device, in this instance my Sony Tablet is at the top of the list, the vendor id is 0fce and product id is 01b1

**STEP 4**
We're then going to amend the mtp udev rules as follows, from a terminal type

```
sudo nano /lib/udev/rules.d/69-mtp.rules
```

Then add the below line of code

```
# [COLOR=#FF0000]Sony Xperia Z2 Tablet[/COLOR]
ATTR{idVendor}=="[COLOR=#FF0000]0fce[/COLOR]", ATTR{idProduct}=="[COLOR=#FF0000]01b1[/COLOR]", SYMLINK+="libmtp-%k", ENV{ID_MTP_DEVICE}="1", ENV{ID_MEDIA_PLAYER}="1"
```

Remember what you're changing here is the device name next to the #, this can be whatever you want, the # comments out the code, but for clarity and reference later I would choose the name of your tablet/phone and also the vendor id and product id, they should match what was seen when you issued the lsusb command earlier. 

Once done, save the file.

**STEP 5**
The next step would also be to add a line of code to the 51 android rules file, again from a terminal type

```
sudo nano /etc/udev/rules.d/51-android.rules
```

Then add the following line of code

```
ATTR{idVendor}=="[COLOR=#FF0000]0fce[/COLOR]", ATTR{idProduct}=="[COLOR=#FF0000]01b1[/COLOR]", MODE=&#8221;0666"
```

Remember what I have highlighted in red needs to be changed to your device product id and vendor id.

Once that is done and the file is saved, remove any usb device currently connected and  issue the following commands

[COLOR=#000000]**STEP 6**[/COLOR]

```
sudo service udev restart
```

Then save any other remaining work you may have open and reboot the system.

**[COLOR=#000000]STEP 7[/COLOR]**
```
sudo reboot
```

Once rebooted you should now be able to plug your Android device in(making sure the screen is unlocked) and VIOLA!!(or at least I hope) You will now be able to transfer data to/from your Android device via the much quicker and much more reliable MTP

All feedback gladly welcome, would like to know if this has worked for this others too.

---

### Post by livewirebt2 on 2014-06-04
> **jdarby1983 said:**
> [...]After much looking around I was never able to find a how-to guide(or should I say the ones that did never worked)[...]

Okay, you looked around and didn't find a good and crisp answer that works for you or your device. That's okay, I can understand that, because I've seen the MTP-confusion on AU and you must have spend some amount of time getting it to work for you. But do you think posting another device specific how-to is going to improve the situation? Also, there are some bits in your how-to that don't seem to make much sense. On the other side it would be beneficial to all users, to find out what issue you actually had, because MTP should work out of the box with the GVFS MTP backend since 13.04 or your device is just [not supported by the libmtp version]("http://askubuntu.com/a/417324/40581") that is shipped with the particular release.

> **jdarby1983 said:**
> 
**[COLOR=#000000]STEP 2[/COLOR]**
Then we're going to amend the fuse.conf file. FUSE is an application [...]


... FUSE shouldn't be involved in the out of the box solution as far as I know.

> **jdarby1983 said:**
> 
**STEP3 + STEP 4**
```
sudo nano /lib/udev/rules.d/69-mtp.rules
```
```
# [COLOR=#FF0000]Sony Xperia Z2 Tablet[/COLOR]
ATTR{idVendor}=="[COLOR=#FF0000]0fce[/COLOR]", ATTR{idProduct}=="[COLOR=#FF0000]01b1[/COLOR]", SYMLINK+="libmtp-%k", ENV{ID_MTP_DEVICE}="1", ENV{ID_MEDIA_PLAYER}="1"
```


**This looks interesting.** I searched for [FONT=courier new]01b1[/FONT] ony my machine in [FONT=courier new]/lib/udev/rules.d/69-libmtp.rules[/FONT] but couldn't find it. **[COLOR=#ff0000]You should file a bug[/COLOR]** to have the following lines included there.

```
# SONY Xperia Z2 MTP
ATTR{idVendor}=="0fce", ATTR{idProduct}=="01b1", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio", ENV{ID_MTP_DEVICE}="1", ENV{ID_MEDIA_PLAYER}="1"
```

> **jdarby1983 said:**
> 
**STEP 5**
```
sudo nano /etc/udev/rules.d/51-android.rules
```


This file is supposed to contain udev rules for ADB and fastboot. None of them have anything to with MTP.

> **jdarby1983 said:**
> 
[COLOR=#000000]**STEP 6**[/COLOR]** + [COLOR=#000000]STEP 7[/COLOR]**
```
sudo service udev restart
```
[...]
```
sudo reboot
```


Why restart udev when you reboot the machine shortly after?

---

### Post by peter.hewett on 2014-06-21
If this (above) isn't the correct way to connect an Android phone to a Linux box via USB, what is?
Is there a howto on this?  (I couldn't find one that looks current.)

The system here is Kubuntu 14.04 and we have two different Android phones (Samsung Galaxy Nexus and S3).

TIA

Peter

---

### Post by coffeecat on 2014-06-21
@jdarby1983, a reminder of the [Tutorials Sub-forum &#8211; Guidelines]("http://ubuntuforums.org/showthread.php?t=2143602") sticky:

> **Tutorials should be supported.**

You are expected to offer support for your tutorial, within practical limits. If you fail to respond to requests for help or clarification within a reasonable time, or fail to update your tutorial, the thread will be closed or removed.

Please respond to the above two posts.

---

### Post by bill-bouterse on 2014-06-23
Trusty 14.04 on old Dell Latitude 630 

All I can say is connecting my Lenova S6000 tablet to the Dell initially showed nothing.
After following the instructions of                                                                                      [**[COLOR=#000000]jdarby1983[/COLOR]**]("http://ubuntuforums.org/member.php?u=1883481")  and plugging in the Lenova device ID as suggested it now is recognized and is accessible.

I am not knowledgable enough to know if there are other or simpler methods. I am just happy it worked for me!

Someday it would be nice if the Android kernel would have Ext recognition for external devices compiled into it by default, but that is another story.
Not understanding the guts of MTP I was disappointed that my ext4 partition on the external sd card was not seen while the 
original Fat32 portion was. 

Ah well.

Anyway thanks to all for their efforts....

---

### Post by Elena_cm on 2014-07-16
Thanks @jdarby1983!! :smile:
Great step-by-step procedure and thank you so much for sharing it! Clear enough even for newbies like me. My Teclast P89 Mini tablet is now mounted in a blink of an eye on Ubuntu 14.04.
Keep up the good work!

---

### Post by Satyanath_Bhat on 2014-07-23
Of all the posts this works, please dont remove it.

---

### Post by coffeecat on 2014-07-23
> **coffeecat said:**
> 
Please respond to the above two posts.

One month later - no response.

@jdarby1983, if you change your mind and decide to support those posting to this thread, please request its re-opening by using the report button. Until then...

Thread closed.

**Edit**: Re-opened.

---

### Post by jdarby1983 on 2014-07-24
I think some confusion here has arisen due to the title of this topic being "how to connect an android device using mtp in Ubuntu 14.04" when clearly my guide goes a little bit further than just MTP. So a point worth noting is perhaps the title needs changing. I do agree my Xperia Z2 tablet was not included I n the latest mtp release, my Samsung note 3 was and did work without and additional config

Not sure why you say I need to file a bug for having "01b1" this was highlighted in red and also referenced this is specific to the device you are trying to connect and will change from device to device.

Restarting udev and then rebooting the system was two steps I included as simply rebooting sometimes did not work, why? I don't know and can't explain further.

> **peter.hewett said:**
> If this (above) isn't the correct way to connect an Android phone to a Linux box via USB, what is?
Is there a howto on this?  (I couldn't find one that looks current.)

The system here is Kubuntu 14.04 and we have two different Android phones (Samsung Galaxy Nexus and S3).

TIA

Peter

Have you tried to follow my guide? If yes, how did you get on? I have not tested this way on kubuntu but would be interested to know if this works or not. Also there is no official how to on this, this guide was out together after much trial and error but from other posts its noted that it does work

Also great to here of the other devices users have managed to successfully mount following the guide

---

### Post by ewr2san on 2014-07-29
Kubuntu 14.04 people who had MTP working on a previous release may find that all they need to do is edit /etc/fuse.conf and uncomment #user_allow_other
to 
user_allow_other

Aparently upgrading replaces /etc/fuse.conf...

---

### Post by Matt_Stevenson on 2014-08-01
> **jdarby1983 said:**
> Also great to here of the other devices users have managed to successfully mount following the guide

Thank you for the guide, @jdarby1983. Confirming that this worked for a Sony Z1 Compact [D5503]. The device id is reported as 01a7.

The device's internal memory and SD card contents are accessible through Nemo on my system as an attached device, in addition to gMTP and Banshee.

---

### Post by SeijiSensei on 2014-08-01
> **ewr2san said:**
> Kubuntu 14.04 people who had MTP working on a previous release may find that all they need to do is edit /etc/fuse.conf and uncomment #user_allow_other

Thanks!  That seems to have fixed my problems.

---

### Post by nah2 on 2014-08-05
Works great for me.

I'm a new ubuntu user, and this was so helpful.

Test on ubuntu 14.04 LTS
Smartphone: Motorola Razr D1

Thank you !

---

### Post by Peivand_Perez on 2014-08-05
Thanks for the tutorial, but i cant connect my Samsung Galaxy S4 phone to Ubuntu 14.04 LTE. I have followed your instructions and changed the id of the device and then rebooted from terminal.

  # Samsung Galaxy S4ATTR{idVendor}=="04e8", ATTR{idProduct}=="6860", SYMLINK+="libmtp-%k", ENV{ID_MTP_DEVICE}="1", ENV{ID_MEDIA_PLAYER}="1"


But still cant connect

Thanks in Advance,


Peivand

---

### Post by serra19 on 2014-08-13
I've tried to configure my android phone, and it has worked momentarily, but then, I've activated the debug mode and mtp has stopped working.
I've executed lsusb, and I've saw that the idProduct has changed (but not the idVendor). Then, I've tried to reconfigure my android phone with the new idProduct, but it hasn't worked...
Any idea?

PD: Sorry for my bad english... :? (I'm spanish...)

---

### Post by ykkhern on 2014-08-15
I had installed Ubuntu 14.04.1 LTS, by doing only Step 3, 4 & 6 is already good enough to hook up my Xperia Z1 Compact, I can access both internal storage as well as SDCard of the phone.

For Step 3, I think you need to do 2 times.  1 time with ***[COLOR=#ff0000]USB Debugging Off[/COLOR]*** and 1 time with ***[COLOR=#0000cd]USB Debugging ON[/COLOR]*** in order to get the 2 different Product ID, then you need to add these 2 ID in Step 4 as 2 seperate lines

For Step 5, I think this is not related to MTP.  Unless you want to use "**adb**" and "**fastboot**" with the phone, you may skip this step.

> **serra19 said:**
> I've tried to configure my android phone, and it has worked momentarily, but then, I've activated the debug mode and mtp has stopped working.
I've executed lsusb, and I've saw that the idProduct has changed (but not the idVendor). Then, I've tried to reconfigure my android phone with the new idProduct, but it hasn't worked...
Any idea?

PD: Sorry for my bad english... :? (I'm spanish...)

For Step 3, I think you need to do 2 times.  1 time with ***[COLOR=#ff0000]USB Debugging Off[/COLOR]*** and 1 time with ***[COLOR=#0000cd]USB Debugging ON[/COLOR]*** in order to get the 2 different Product ID, then you need to add these 2 ID in Step 4 as 2 seperate lines (one Product ID per line).

---

### Post by serra19 on 2014-08-15
I've tried that, but it doesn't work with USB debugging on... :cry:

---

### Post by Fred_Pauling on 2014-08-22
This works for my Samsung Galaxy S2. Strangely, there was already an MTP rule for my vendor : product ID, but it has never worked properly - it showed up as an MTP device after plugging in, but I always got an error dialog. This tutorial fixed it. It is late August now, and there were two things that were different for me from this tutorial: 1. I have a 69-libmtp.rules file instead of 69-mtp.rules, and 2. I needed to create the android rules file since it did not exist already. Apart from that it worked like a boss! Kudos.

---

### Post by Jim March on 2014-08-27
First, the OP's instructions worked flawlessly for me on the following phone:

Samsung SGH-T599
Android: 4.1.2
TMobile

So thank you extremely on that basis.

BUT!!!!

My phone is protected with encryption on the SD card and this technique totally and completely defeats the phone's encryption!  Not kidding at all - spanks it cold.  I assume law enforcement already knows about this trick :(.

---

### Post by peddanet on 2014-08-31
@jdarby1983: Thank you that tutorial helped me connecting to my SONY Xperia Z2 Mobile Phone!!!

**Funnily I had to switch off the "USB Debugging" option to show up.** Because it was formerly recommended to do so, maybe you can add it to your post?

I followed your instructions but before I had not gone through the whole thread, I only saw the device D6503 without any content.

I came lately from an distribution upgrade and had different issues before in 12.04 (now upgraded to 14.04, which was not bug-free) and found the following beginning of the /lib/udev/rules.d/69-libmtp.rules:

```
Unable to open ~/.mtpz-data for reading, MTPZ disabled.# UDEV-style hotplug map for libmtp
# Put this file in /etc/udev/rules.d

ACTION!="add", GOTO="libmtp_rules_end" ENV{MAJOR}!="?*", GOTO="libmtp_rules_end" SUBSYSTEM=="usb", GOTO="libmtp_usb_rules" GOTO="libmtp_rules_end"  
LABEL="libmtp_usb_rules"  

[...]

```

I copied the file - after the changes in your tutorial, commented out the first line - according to line 2 to directory /etc/udev/rules.d/ (did not exist before)
Maybe then the 51-android.rules file isn't necessary any more? As far as  I understood these scripts in rules.d they are processed in the order of the number they are prefixed.

---

### Post by Arunkumar_Manimara on 2014-09-07
[COLOR=#DD4814][COLOR=#000000][jdarby1983]("http://ubuntuforums.org/member.php?u=1883481"), 
i tried your steps in Ubuntu 14.04 for connecting [/COLOR][/COLOR][**Xperia**™ **Z2** ]("http://www.sonymobile.com/XperiaDetails")[SIZE=4][COLOR=#000000]It worked like a charm. Thanks again for sharing steps for the noobs ^_^ [/COLOR][/SIZE][COLOR=#000000]Bang!!![/COLOR]

---

### Post by aline_fernandes_de on 2014-09-28
it worked perfectly in my motorola moto e xt1022 (the dual chip without dtv)
thank you so much! :p

---

### Post by letsjump on 2014-10-22
Thanks @jdarby1983
It works well on Kubuntu 14.04.
I had to write just /lib/udev/rules.d/*69-libmtp.rules* with both product ID and Mode.

> # OnePlus One
ATTR{idVendor}=="05c6", ATTR{idProduct}=="6765", SYMLINK+="libmtp-%k", MODE="666", GROUP="audio", ENV{ID_MTP_DEVICE}="1", ENV{ID_MEDIA_PLAYER}="1"

After sudo service udev restart my smartphone OPO started to work!

Thanks a lot

---

### Post by Jarno_Suni on 2014-10-22
Unfortunately, this tutorial did not help me to gain proper access to files in Samsung S5 Mini: [http://ubuntuforums.org/showthread.php?t=2249442](http://ubuntuforums.org/showthread.php?t=2249442)

Why do you want to install libmtp-dev?

---

### Post by jeancar on 2014-10-27
Thank you! Your tutorial is working for me. Now I can see the thumbnails of pictures directly in nemo!!
But, i get the same error when I try to open them: "libmtp error: unknown error"

---

### Post by ahmed22 on 2014-10-30
Works like a charm for Asus Fonepad 7 FE170CG

Thank you so much!

---

### Post by claracc on 2014-10-31
I have a sony xperia m smartphone and I would like to connect it to my hp compaq 6720s ubuntu 12.04 fully updated system. Is it possible to follow this step by step guide in ubuntu 12.04 in order the smartphone be recognized or is there other method?.

Thanks in advanced.

---

### Post by Mark_du_Preez on 2014-11-02
After entering "lsusb", I don't see my device. What else can I try?

---

### Post by Banshee-2007 on 2014-11-02
Hello


I have tried this for Galaxy S III, and did not work, as it did not work for a member who commented in Page.2 about Galaxy S IV (S4). I tested this method on Samsung Galaxy S II (S2), Galaxy S III (S3), Galaxy S IV (S4), Galaxy S4 Active, Galaxy Ace 2, Galaxy Note 3.0 & HTC M8.


It worked for the Galaxy S II (S2) and the HTC M8 with the following IDs:
```
 ID [COLOR=#ff0000]04e8:685e[/COLOR] Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II] 
```


&


```
 ID [COLOR=#ff0000]0bb4:0f25[/COLOR] HTC (High Tech Computer Corp.)  
```


This method did not work for the Galaxy S3, Galaxy S4, Galaxy S4 Active, Galaxy Ace 2 & Galaxy Note 3.0, all with the following ID.
```
 ID [COLOR=#ff0000]04e8:6860[/COLOR] Samsung Electronics Co., Ltd 
```


It turned out that the problem in the devices I checked was in the Samsung mobile phones issued in the generation of Galaxy S III and later. Those phones carrying the ID shown above, and later phones from Samsung just won't work with the method explained in this topic. Galaxy S II did not need this method to connect through MTP to the computer with no problems, and when I applied this way explained in the tutorial, nothing changed, and the mobile was still connecting correctly. In smaller scale did the HTC. However, in the HTC M8 case, the media (audio, video and images) worked fine through MTP when I connected the phone to the computer, but there was some limitation in other things, such as browsing documents which did not work.

 
When I implemented the method explained things worked fine as they do in Windows (at least for me during my quick test). Note that I noticed that when I connected the phone without changing the permissions of the phone in the rules files I created earlier, as explained on topic, the documents did not work, while the media did work and the icons of the photos and videos had avatars (if it is correct to say that) showing the content of the photo/video file. However, when I applied the changes in the rule files, everything went well, except that the icons of the photo/video files showed nothing related to the content, but just standard avatars in green for the photos and blue for the videos (this in LinuxMint, I don't know how that would look in Ubuntu). 


Note that for the mentioned Samsung Galaxy phones (with an exception for Galaxy Ace 2), the connection with the PC in LinuxMint (it should apply to Ubuntu and Zorin OS also) works using the PTP USB Computer Connection setting (which you can access from the notification bar when you connect you mobile to the computer). Galaxy Ace 2 as I noticed does not support PTP with its Android 2.3.6, but does originally support Mass Storage Connection (in contrast with the other new Samsung phones I mentioned). Using Mass Storage Connection, you can access your files from a LinuxMint (or Ubuntu and Ubuntu-based systems). For explanation about connecting you data using Mass Storage Connection, you can pay a visit to the following link with an explanation. The explanation for Android 4.0 applies to Android 2.3.6 (as in the case of Galaxy Ace 2).
[http://www.device-recovery.com/how-to-connect-android-devices-to-pc-with-usb-mass-storage-mode](http://www.device-recovery.com/how-to-connect-android-devices-to-pc-with-usb-mass-storage-mode)


To sum up, this method is not required for Galaxy S II, required to obtain full connection functionality for HTC M8 (without this method you can browse only the media files but not documents), and it does not work for Samsung Galaxy mobile phones that have the ID [COLOR=#ff0000]04e8:6860[/COLOR] (such as Galaxy S3, S4 and Note 3.0). The connection of the mentioned Samsung Galaxy mobile phones works with no need for this method on the PTP connection setting.

---

### Post by spino-spinelli on 2014-11-08
@jdarby1983, **thank you very much for your effort.**

Using your tutorial I managed to connect my Wiko Highway Signs (which is an Android phone) to my Trusty Ubuntu 14.04.1 LTS

*For completeness of information*, I must say that some of the steps you suggest were not necessary for me. I just added the lines 

```

# WIKO Highway Signs
ATTR{idVendor}=="0bb4", ATTR{idProduct}=="2008", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio", ENV{ID_MTP_DEVICE}="1", ENV{ID_MEDIA_PLAYER}="1"

```

to file
 ```
 /lib/udev/rules.d/69-libmtp.rules
```

mtp-tools were already up to date.

I just executed

```
sudo service udev restart
```

(no reboot).

So, as a personal remark, I would suggest to people with the same problem, first of all to try the minimal solution (add rule to 69-libmtp.rules and restart udev). If the problem persists, go ahead with the full solution.  Moreover, I am not an expert of libmtp, but reading file /lib/udev/rules.d/README, there is the danger that updates to libmtp will overwrite my changes, so be warned! 


I also submitted a bug report to

```
http://sourceforge.net/p/libmtp/bugs/
```

and I hope in future versions the issue will be solved. I think that everybody exxperiencing the same problem with another phone or device should contribute to the community.

---

### Post by pwabrahams on 2014-11-08
I'm trying to connect my Android phone to Kubuntu.  At one point I had the connection working just fine -- and then it stopped working.  The relevant lsusb entry is:
[B]Bus 003 Device 007: ID 1004:631c LG Electronics, Inc. 
[/B]
My entry in **/etc/udev/rules.d/99-android.rules** is:
**SUBSYSTEM=="usb", ATTR{idVendor}=="1004", ATTR{idProduct}=="*",MODE="0666", OWNER="pwa", GROUP="plugdev"    # MTP mode with USB debug on**
But I get:
```
pwa@lentinus:~$ adb devices
List of devices attached 

pwa@lentinus:~$ 

```
I suspect that something I've done has messed up the Android filesystem, but I have no idea how to check that out.  It might be related to disconnecting the Android from the USB port improperly.

---

### Post by maryclaire on 2014-11-09
Followed this to connect my Lenovo S860 with good results-- previously, upon connected with USB, mounting with MTP just gave me a disc image to be run on PC with some .exe files. Following this guide, upon reboot, Lenovo S860 comes up as an internal storage disc with full access to files therein. Was able to drag and drop my music from Ubuntu onto the phone via USB just as desired. Thanks.:KS

---

### Post by robindebonnecoeur on 2014-11-10
I've been following this whole thing with great interest. Oddly enough, this is a recent issue: I was able to browse my Samsung SIII (S3) a few months ago, with debugging set off on the phone, by just plugging it into a USB port. Yes, that action would initially generate an error, but then, Nemo (I use Linux Mint) would come up and I could browse the phone just like a shared network drive.
All this ended recently. 

Now, from what I've read in the thread so far, it appears the OP's strategy worked for some Android (even later flavours, it seemed) phones and devices, but notoriously, Samsungs appeared to be resistant to the technique.
Just curious: before I embark on this exercise... has any Samsung S3/S4 user been able to successfully access the phone via this method?

---

### Post by jumbo3 on 2014-11-20
Jdarby you've saved my bacon. Excellent. Now I no longer get the 'Unable to mount MTP device' message. Many thanks.
(FYI: my device is a HUDL and I'm running Ubuntu 14.10)

---

### Post by jdneate on 2014-11-22
Followed jdarby's post slavishly for Ubuntu 14.04 LTS and Samsung Fame phone; phone not recognised when mounted.
Prior to following jdarby the phone was at least recognised as usb device - if not accessible.
I notice Banshee's recent post about changing to PTP .... cannot see how to do ...... any help welcome !  Thanks in advance

Played around a bit more; realised that reference to changing to PTP by Banshee is on phone notification. Tried this and can now communicate in PTP to phone. Connection  seems a bit " delicate" ..... but at least I can now access phone.( Thanks Banshee-2007). Any further info on how to make it communicate as MTP device welcome.

---

### Post by esther3 on 2014-12-02
Hi:

Thanks you very much for the tutorial, but unfortunatly, doen't rule for me and my Samsung ACE II. My problem is at the 3th step, the mobile never apperars. I use the key: 04e8:6860 indicated in a previous comment, but it is not the solution.

Bye

---

### Post by Marcel Bergeret on 2014-12-07
Thanks a lot jdarby1983!

Your how-to fixed the file transfer with my HP Slate 7! 

This device, for whatever reason, was automatically managed by gvfs-gphoto2, that has apparently issues in handling huge files. In my Ubuntu I did not have the files /lib/udev/rules.d/69-mtp.rules and /etc/udev/rules.d/51-android.rules, so I created them following the example lines you posted, and now my HP Slate 7 is managed by gvfs-mtp, that works much better in file transfers!

---

### Post by arfi-firdaus on 2014-12-11
Great !!, works for my Xiaomi Redmi 1s...

---

### Post by TedinOz on 2014-12-12
Hi. I basically understand all the steps but could someone please help this novice through Step 2. I am unused to Terminal usage and can't seem to find a way to "[COLOR=#000000] to remove the # from the below line of code for user_allow_other, like so..." What keyboard usage is necessary to make a change to the file within the terminal please? I can't seem to do any editing? Once I know how to do this I am sure I can proceed through the tutorial.

Thank you.[/COLOR]

> **TedinOz said:**
> Hi. I basically understand all the steps but could someone please help this novice through Step 2. I am unused to Terminal usage and can't seem to find a way to "[COLOR=#000000] to remove the # from the below line of code for user_allow_other, like so..." What keyboard usage is necessary to make a change to the file within the terminal please? I can't seem to do any editing? Once I know how to do this I am sure I can proceed through the tutorial.

Thank you.[/COLOR]

Right...solved my own problem here thanks to [http://askubuntu.com/questions/54221/how-to-edit-files-in-a-terminal-with-nano](http://askubuntu.com/questions/54221/how-to-edit-files-in-a-terminal-with-nano). Ubuntu remains a marvel to me with all the support available!
Thanks for the thread and the tutorial. Finally connected my Asus Zenfone 5 and all is working beautifully!  :)

---

### Post by vinnie2 on 2014-12-14
absolutely worked like a charm for me....explained it so well that am totally amateur to both android and linux, yet i got it right the first time....

---

### Post by wavesound on 2014-12-14
Hi Just like to say thanks for this it worked on my HTC
I have two phones that all worked, no problem
one is an old Huawei
and also  HTC max 1.
They both used to work in older OS's, is there a reason for this being broken under 14.1 lts
Seems a bit odd considering we all have smart phones and often need to access the phone from the PC.
Cheers Bob

---

### Post by Mustapha_Ajam on 2014-12-18
Hi there

Thank you for your post. I followed your instructions and I can connect to my Htc wildfire device in disk mode and see all folders etc, when I click on Android fone in the explorer window I get the following error.
Unable to access “Android Phone”
No Mtp devices found.

Do you perhaps have a solution or did I make an error somewhere.
Thank you.

---

### Post by enrico-volpe on 2015-01-01
Worked with my Xiaomi Mi4 W and Ubuntu 14.04
Thaks a lot, it's really useful.

---

### Post by ajgreeny on 2015-01-02
This also worked faultlessly for my Acer Iconia A210 using Xubuntu 14.04.1 on my desktop machine.

I had managed to get it working in a similar way for a while on my Xubuntu 12.04, though it needed an added line in /etc/fstab to mount it, but then it simply stopped, and I never did figure out what happened to stop it.

---

### Post by toontoon on 2015-01-03
My device: Oneplus One
Distro: Lubuntu 14.04.1 LTS
This tutorial did not help but this post did [https://forums.oneplus.net/threads/linux-mount-problem-all-linux-distro.87271/#post-4667149](https://forums.oneplus.net/threads/linux-mount-problem-all-linux-distro.87271/#post-4667149)

---

### Post by muadzmohamad13 on 2015-01-04
thanks :) 
the best guide for mtp I've ever read. thank you very much :)

---

### Post by kripalu on 2015-01-11
Great Help -followed your instructions precisely-- Am using Ubuntu 14.04 for the Redmi Note 4G. Worked like a charm.  THANK YOU VERY VERY MUCH

---

### Post by PaulWhipp on 2015-01-14
I'm using Ubuntu 14.04 and was unable to connect my nice new Galaxy Note 4. Following this guide with a pinch of salt, I installed the mtp applications. Then I found that the /lib/udev/rules.d/69-mtp.rules file had my device in it but it had bad text on the first line. I deleted the first line and rebooted. Sorted. It now connects automatically and I can copy files to and from the device.

Googling found [this bug]("https://bugs.launchpad.net/ubuntu/+source/libmtp/+bug/1261075"). Those are the only two things I did.

---

### Post by lunareth on 2015-01-14
Thank you for this thread, I have mounted my LG G Pad 8.0 without any problems.

---

### Post by jdarby1983 on 2015-01-18
Thanks for finding this out Banshee-2007. I too have a Samsung Galaxy Note 3, even after following the steps in my own guide I can get the device to show up in Ubuntu, however, the performance when transferring files between the OS and SD Card is very intermittent and almost always drops connectivity.

---

### Post by Achmed_Islamic_Her on 2015-01-21
works perfectly. thank you... :guitar:

---

### Post by vjgeddes on 2015-01-24
Thank you so much!

---

### Post by Banshee-2007 on 2015-01-28
Go back to my reply please. It is in this page above.

---

### Post by RISHIKESHGAWADE on 2015-01-30
This worked really well for my Asus Zenfone 5 on Ubbuntu 14.04. Thanks for the great detailed guide.

---

### Post by akylasa09 on 2015-02-04
Thanks for this post! Worked perfectly to get my Shield Tablet recognized on Ubuntu 14.10.

---

### Post by stafio on 2015-02-08
Thanks, this worked for me using Kubuntu 14.04 and a Oneplus One phone. 

There is no sudo 51-android.rules file as mentioned in step 5 though, so I just skipped that step.

---

### Post by decrepit on 2015-02-12
On my 14.04 PC followed your guide, and my Galaxy Ace mounts OK but nautilus says it's empty.
Where as on my 14.04 laptop it worked out of the box.
Any suggestions would be welcome.

---

### Post by Tattorack on 2015-02-13
Kudos Write_mem!
This was very helpful and now I can connect my Samsung phone and Lenovo tab ^^

---

### Post by glamont-frontiernet on 2015-02-15
Don't care what the whiney babies said, worked like a champ for me

---

### Post by drsreehari98vet on 2015-02-16
my samsung gti8242 contents where visible in nautillus.. still this error was coming ! unable to mount.. did all the things said in the post.. problems persist :( device keeps showing connected disconnected again and again..

---

### Post by drsreehari98vet on 2015-02-16
holy.. now i am not able to view the android files at all.. !!!!!but the unable to mount message coming and repeating every second has stopped LOL

---

### Post by granny4linux2 on 2015-02-16
Thank you so much for taking the time to document this. Your instructions worked like a charm on my Asus Memo Pad 8 K011; Android 4.4.2 on Ubuntu 14.04.1 LTS . I did not do this added step until last.  In Asus go to settings>storage and click on the icon in upper right hand corner, then check the  box "Media Device MTP". I don't know if I had done this in the Asus first if it would have mounted without following your steps as well. Happy Granny

---

### Post by kto456dog on 2015-02-24
Thank you for this excellent tutorial.

---

### Post by Chip88 on 2015-03-05
Hi there!

I tried to connect my Xperia Z2 for a really long time with my Kubuntu (Ubuntu 14.04.2 LTS).

[B]All the steps and advices given by &#65532;write_mem in his first post worked great for me!!!


[/B]Thank you for your instructions, write_mem!!!

Regards,
Chipy

---

### Post by alexforsale on 2015-03-05
thanks for this, now I can connect to my Redmi 1s!

my 69-mtp.rules:

```
# Xiaomi Redmi1S WCDMA - MTP Mode
ATTR{idVendor}=="2717", ATTR{idProduct}=="1260", SYMLINK+="libmtp-%k", ENV{ID_MTP_DEVICE}="1", ENV{ID_MEDIA_PLAYER}="1"
# Xiaomi Redmi1S WCDMA - MTP Mode with USB Debug
ATTR{idVendor}=="2717", ATTR{idProduct}=="1268", SYMLINK+="libmtp-%k", ENV{ID_MTP_DEVICE}="1", ENV{ID_MEDIA_PLAYER}="1"


# Xiaomi Redmi1S WCDMA - PTP Mode
ATTR{idVendor}=="2717", ATTR{idProduct}=="1210", SYMLINK+="libmtp-%k", ENV{ID_MTP_DEVICE}="1", ENV{ID_MEDIA_PLAYER}="1"
# Xiaomi Redmi1S WCDMA - PTP Mode with USB Debug
ATTR{idVendor}=="2717", ATTR{idProduct}=="1218", SYMLINK+="libmtp-%k", ENV{ID_MTP_DEVICE}="1", ENV{ID_MEDIA_PLAYER}="1"
# Xiaomi Redmi1S WCDMA - USB Mode == Built-in CD-ROM Mode!
ATTR{idVendor}=="2717", ATTR{idProduct}=="1220", SYMLINK+="libmtp-%k", ENV{ID_MTP_DEVICE}="1", ENV{ID_MEDIA_PLAYER}="1"
# Xiaomi Redmi1S WCDMA - USB Mode with USB Debug
ATTR{idVendor}=="2717", ATTR{idProduct}=="1228", SYMLINK+="libmtp-%k", ENV{ID_MTP_DEVICE}="1", ENV{ID_MEDIA_PLAYER}="1"



```

---

### Post by gunnar207 on 2015-03-10
Thank you!.  Worked for me and my Sony Xperia Z2.

---

### Post by Berry Greene on 2015-03-12
First of all thank you for this. 
Second  - my Version is 12.04 LTS
Third - when I did this procedure on Tuesday it worked just fine!
Fourth - the following day ? (keep up!) it didn't. So I went through the procedure again. Noticed a slight change. My Tablet ID which was 1f3a :1000 now 1f3a : 1006
Fifth -  went back over - still no go. Noticed Limit set to 1000 so increased to 1006 on spec. Didn't work! Put it back.
Sixth -Tried my Android on Windows XP- which worked OK!  -  
Seventh - came back to UBUNTU -tried again - the address 1f3a ; 1006 is reported when attached, moves around for different ports and disappears when not attached.
Eighth - At a loss

So please, if you can, give me a clue as to what to do now. I am so fatigued with this it's not true! Be yer friend forever!  [IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG]

Rgds and thanks whatever.....
Berry

---

### Post by maisam2 on 2015-03-27
> **write_mem said:**
> Hi,

After much looking around I was never able to find a how-to guide(or should I say the ones that did never worked)on how to connect my android tablet/phone to Ubuntu for file transfers, sure there's other means of doing it wireless via your LAN, but truth be told MTP and Ubuntu don't exactly see eye to eye and as such I hope the following guide I put together saves someone a lot of time and effort. This was performed on Ubuntu 14.04 LTS

**[COLOR=#000000]STEP 1[/COLOR]**
Firstly we're going to need to install some of the common MTP apps that will be needed. Open up a terminal and type the following two lines one after the other.

```
sudo apt-get install libmtp-common mtp-tools libmtp-dev libmtp-runtime libmtp9
```
```
sudo apt-get dist-upgrade
```

**[COLOR=#000000]STEP 2[/COLOR]**
Then we're going to amend the fuse.conf file. FUSE is an application that aims to provide a secure method for non privileged users to create and mount their own file system implementations. This option overrides  the  security  measure  restricting  file access  to  the  user  mounting  the  file system.  So all users (including root) can access the files. This option is by default only allowed to root, but this restriction can be removed with a change to the aforementioned fuse.conf file as follows:

At the terminal type

```
sudo nano /etc/fuse.conf
```

We want to remove the # from the below line of code for user_allow_other, like so...

```
#/etc/fuse.conf - Configuration file for Filesystem in Userspace (FUSE)

#Set the maximum number of FUSE mounts allowed to non-root users.
#The default is 1000.
#mount_max = 1000

# Allow non-root users to specify the allow_other or allow_root mount options.
user_allow_other
```


Now save the file by pressing Ctrl+x, press Y and then Enter.

**[COLOR=#000000]STEP 3[/COLOR]**

We now need to set up some rules for our device that we plan on connecting, but before we do that we need to find out both the vendor and product id

Connect your device via an available usb port and from terminal enter

```
lsusb
```
This should bring up an output similar to the following

```
Bus 002 Device 003: ID 0fce:01b1 Sony Ericsson Mobile Communications AB 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 0461:4d65 Primax Electronics, Ltd 
Bus 001 Device 005: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]

```

You need to look for your device, in this instance my Sony Tablet is at the top of the list, the vendor id is 0fce and product id is 01b1

**STEP 4**
We're then going to amend the mtp udev rules as follows, from a terminal type

```
sudo nano /lib/udev/rules.d/69-mtp.rules
```

Then add the below line of code

```
# [COLOR=#FF0000]Sony Xperia Z2 Tablet[/COLOR]
ATTR{idVendor}=="[COLOR=#FF0000]0fce[/COLOR]", ATTR{idProduct}=="[COLOR=#FF0000]01b1[/COLOR]", SYMLINK+="libmtp-%k", ENV{ID_MTP_DEVICE}="1", ENV{ID_MEDIA_PLAYER}="1"
```

Remember what you're changing here is the device name next to the #, this can be whatever you want, the # comments out the code, but for clarity and reference later I would choose the name of your tablet/phone and also the vendor id and product id, they should match what was seen when you issued the lsusb command earlier. 

Once done, save the file.

**STEP 5**
The next step would also be to add a line of code to the 51 android rules file, again from a terminal type

```
sudo nano /etc/udev/rules.d/51-android.rules
```

Then add the following line of code

```
ATTR{idVendor}=="[COLOR=#FF0000]0fce[/COLOR]", ATTR{idProduct}=="[COLOR=#FF0000]01b1[/COLOR]", MODE=”0666"
```

Remember what I have highlighted in red needs to be changed to your device product id and vendor id.

Once that is done and the file is saved, remove any usb device currently connected and  issue the following commands

[COLOR=#000000]**STEP 6**[/COLOR]

```
sudo service udev restart
```

Then save any other remaining work you may have open and reboot the system.

**[COLOR=#000000]STEP 7[/COLOR]**
```
sudo reboot
```

Once rebooted you should now be able to plug your Android device in(making sure the screen is unlocked) and VIOLA!!(or at least I hope) You will now be able to transfer data to/from your Android device via the much quicker and much more reliable MTP

All feedback gladly welcome, would like to know if this has worked for this others too.




i was in so tention brother, searched whole internet didnt find a solution but ur guide helped me and it worked, im using Huawei Honor 3c Lite !! :*

---

### Post by daniel122 on 2015-03-28
Works also great for the new bq Aquaris Ubuntu Edition. No need to add the android-rules though. Thank you very much.

---

### Post by david-mann on 2015-04-03
Worked perfectly well for my Tesco Hudl tablet, (made by Pegatron)

---

### Post by mortalcs on 2015-04-05
Hey man, thanks for the write up, it worked perfectly for my XperiaZ3.

---

### Post by zhuceforum on 2015-04-29
Thank you write_mem, I just followed your instruction, and it works well to connect my brand new ASUS Zenfone 2 to my Ubuntu 14.04

Best Regards,
Zhuce

---

### Post by badrx1011 on 2015-05-05
Almost worked for me.  I can see both Internal SD and External SD in the file manager and media app like Clementine but in Clementine I cannot play my music.  seems pointless.  I will have to do some permissions configurations but not sure how to go about it.  Thanks for the tutorial anyway.  appreciate it.

EDIT

Device: HTC Desire 510 (Sprint)
OS: Ubuntu Vivid 15.04

---

### Post by clstal on 2015-05-12
This did NOT work for me - trying to connect a galaxy note 3, have my device and product IDs and have edited as directed. My device shows up in files for half a second before disappearing, no matter what I select on the phone (MTP: connect as storage or connect as camera) and USB 3.0 is greyed out despite using a compatible cable to connect the phone. 
Running 14.04.

Any suggestions? This has been the most useful-looking tutorial out there!

---

### Post by crf112 on 2015-05-13
I was able to successfully use the instructions in Post #73 above on my 15.04 system with the ONE EXCEPTION.  

The correct name of the file in Step 4 (on my 15.04 system) is** /lib/udev/rules.d/69-libmtp.rules.**

---

### Post by Haris_Mu on 2015-05-15
Thanks bro... !!!

It really helped..

=d>=d>=d>=d>

---

### Post by nathatanu0 on 2015-05-19
> **write_mem said:**
> Hi,

After much looking around I was never able to find a how-to guide(or should I say the ones that did never worked)on how to connect my android tablet/phone to Ubuntu for file transfers, sure there's other means of doing it wireless via your LAN, but truth be told MTP and Ubuntu don't exactly see eye to eye and as such I hope the following guide I put together saves someone a lot of time and effort. This was performed on Ubuntu 14.04 LTS

**[COLOR=#000000]STEP 1[/COLOR]**
Firstly we're going to need to install some of the common MTP apps that will be needed. Open up a terminal and type the following two lines one after the other.

```
sudo apt-get install libmtp-common mtp-tools libmtp-dev libmtp-runtime libmtp9
```
```
sudo apt-get dist-upgrade
```

**[COLOR=#000000]STEP 2[/COLOR]**
Then we're going to amend the fuse.conf file. FUSE is an application that aims to provide a secure method for non privileged users to create and mount their own file system implementations. This option overrides  the  security  measure  restricting  file access  to  the  user  mounting  the  file system.  So all users (including root) can access the files. This option is by default only allowed to root, but this restriction can be removed with a change to the aforementioned fuse.conf file as follows:

At the terminal type

```
sudo nano /etc/fuse.conf
```

We want to remove the # from the below line of code for user_allow_other, like so...

```
#/etc/fuse.conf - Configuration file for Filesystem in Userspace (FUSE)

#Set the maximum number of FUSE mounts allowed to non-root users.
#The default is 1000.
#mount_max = 1000

# Allow non-root users to specify the allow_other or allow_root mount options.
user_allow_other
```


Now save the file by pressing Ctrl+x, press Y and then Enter.

**[COLOR=#000000]STEP 3[/COLOR]**

and 

**STEP 4**
and 

**STEP 5**

and

[COLOR=#000000]**STEP 6**[/COLOR]

and

**[COLOR=#000000]STEP 7[/COLOR]**

And

.
 

Rebooted... and nothing happened ! My Samsung Galaxy SIII Neo doesn't connect ! Same old error message, "Unable to mount..... Error initializing camera: -60: Could not lock the device" and "....Error initializing camera: -1: Unspecified error"  !

It seems that this is an unsolvable problem and whoever can invent a device independent "how-to" solution may apply for a fields medal or something !

---

### Post by enekoalfer on 2015-05-24
Awesome! It fixed my problem with my Android phone (BQ Aquaris E5 HD). I was unable to connect it to my Elementary OS Freya, and now it is working perfectly! 10 out of 10 for you ;)

---

### Post by andrii-popovych on 2015-06-16
Work on UMI ZERO 3.10 Android 4.4.2. Thanks!

---

### Post by ahsan_sajjad on 2015-07-14
Works! Thanks Man you rock!

---

### Post by gscratch2 on 2015-07-20
Thanks very much to the original poster.  However, I have the same symptoms as nathatanu0.  Followed all the steps, but when I connect my phone after reboot, the condition is exactly the same as before the steps, namely "Could not lock the device" and all folders show zero files.   When I connect the phone to a Windows machine, I can see all the files in all the folders.

Samsung Galaxy S II and Ubuntu 12.04LTS

---

### Post by janwouter on 2015-07-24
Worked on the first try like a charm. Thanks for this explanation. I use a cheap unknown Chinese phone, InFocus M310, android 4.2.2, but that made no difference.

---

### Post by mazhar330gb on 2015-07-31
Many thanks. Instructions worked for the tesco hudl2 tablet (once I worked out saving stuff with nano) with my fujitsu laptop running ubuntu 14.04 but exactly the same instructions and kit doesn't work with my unbranded desk top also running ubuntu 14.04. weird. However I can get the hudl2 connected to the desk top using gMTP.

---

### Post by MackaDocious_Prime on 2015-08-01
You guys mind if I ask a specific question on this thread?  It's about ADB. I get an error when I try
 ```
sudo apt-get install android-tools-adb android-tools-fastboot
```

[IMG]http://s13.postimg.org/7ygjozflj/adberror.png[/IMG]

---

### Post by henrique10 on 2015-08-02
Nice how-to.

I spent hours trying to connect my Redmi 2 to my notebook running  with Ubuntu 14.04 LTS and with a couple minutes with this post my problem desapeared.

Thanks!

---

### Post by howefield on 2015-08-02
> **MackaDocious_Prime said:**
> You guys mind if I ask a specific question on this thread?  It's about ADB. I get an error when I try
 ```
sudo apt-get install android-tools-adb android-tools-fastboot
```

[IMG]http://s13.postimg.org/7ygjozflj/adberror.png[/IMG]

Try 

```
sudo apt-get -f install
```

---

### Post by MackaDocious_Prime on 2015-08-04
It helped.  I did ```
sudo apt-get -f install
``` then,

```
sudo apt-get install android-tools-adb
```.  I see my device now thanks!  Except I probably should have also done 'fastboot'

---

### Post by wilnd on 2015-08-16
Worked perfectly for my One Plus 1 Android phone under Ubuntu Trusty, thank you!!!!

---

### Post by Trogladyte on 2015-08-20
This didn't work for my HTC One XL. I tried it on a different USB port and got "Unable to open MTP device '[usb:001,007]'"

Grateful for any advice. I'm sure this shouldn't be so hard...

---

### Post by smc2 on 2015-08-22
I have not found a forum central to Android, but this appears the best for Android/Ubuntu interoperability. Is there one out there?  I need exchange not dependent upon the internet between Ubuntu and Android!  Please let me know if this is not it!  It is referenced by others:

[http://ubuntuforums.org/showthread.php?t=2260400](http://ubuntuforums.org/showthread.php?t=2260400)

I've been struggling with this topic for days.  Tried quickly on 14.04 and 15.04 without luck on a stick install of each(maybe that's the problem).  My preference would be to plug a USB into the phone, but it is not OTG compliant and that's another headache, so the USB charging cable is what I've been working with.  

I would love to have normal file exchange at the file system level and bash, but run into a mix of experience permission/security errors.  I believe a correctly installed mtp-server is the route?  Honestly, running through this thread in entirety I start to get a little lost.

Help, where do I start, are the above still correct for 14.04, 15.04?

---

### Post by ulrich-morgenthaler on 2015-08-24
> **Mark_du_Preez said:**
> After entering "lsusb", I don't see my device. What else can I try?

Hi, after I changed the connecting cable between my laptop (Asus X54C) and my device (Samsung Galaxy Note 2) it suddenly showed.

---

### Post by Dawn_Cherian on 2015-08-27
Install mtpfs from your terminal
[LIST]
[*]sudo apt-get install mtp-tools mtpfs
[/LIST]

Get idVendor and idProduct of your mobile phone
[LIST]
[*]mtp-detect | grep idVendor
[*]mtp-detect | grep idProduct
[/LIST]

Insert the follwing text to your 69-libmtp.rules file located at /lib/udev/rules.d replacing idVendor_got_above and idProduct_got_above
[LIST]
[*]ATTR{idVendor}=="idVendor_got_above", ATTR{idProduct}=="idProduct_got_above", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio", ENV{ID_MTP_DEVICE}="1", ENV{ID_MEDIA_PLAYER}="1", TAG+="uaccess"
[/LIST]

---

### Post by jdarby1983 on 2015-08-27
Hi,

There is an incompatibility after Samsung Galaxy S2, I'm afraid you've hit that. I did document this in an earlier post.

I myself own a Samsung Galaxy Note 3 and have different results every time connect. Sometimes works, sometimes doesn't

---

### Post by Kenneth_C._Brown on 2015-09-08
Thanks for sharing this with othermembers, some of whom might be going through the same kind ofproblem. But we need to try this out to find out whether this helpsus find the right solution.

---

### Post by pinaart on 2015-09-17
Is there a new thread specifically for v15.04 & Samsung III?
Mine used to work fine then failed last week and I thought I only installed some "Configuration" thing to allow me to test my 5 TB USB 3.0 drives and some failing 3 TB drives.
I got to this tutorial after extensive Googling, but it failed for me. My Windows 10 machine has no problem talking MTP with my S3. Ubuntu 14.04 - 15.05 didn't either until last week.
I am getting the,
 Unable to open ~/.*mtpz*-data for reading, *MTPZ* disabled.
message along with the,
 Unable to to handle MTP. (or something like that
I can navigate the droid, but get "Permission Denied" if I try to open any file.
I popped an xterm and attempted to read the files as root, but was still denied permission, so it's a systems issue. I.e., I thought the droid didn't want to be read. I never had to unlock the screen before and even I make sure it's unlocked, it still doesn't work.

I tried my Samsung Note 10.1 and get exactly the failure mode - Permission Denied at the file level, but directory traversal is no problem. PTP works fine in both.

Thx - Art

---

### Post by Fiksdal on 2015-09-18
Negative for Samsung I9305

---

### Post by fwrun2011 on 2015-09-19
It worked for me. I was not able to open, let alone write to the SD card in my Moto e Android 4.4 KitKat phone until I followed the procedure.
Thanks much!

---

### Post by decrepit on 2015-09-29
That's 3 phones (Samsung Ace3, Sony Xperia E, and Alcatel Pixie 3), successfully connected thanks for this tuit.

---

### Post by vladutz on 2015-10-05
The only thing on internet that actually worked. Great job! My Chuwi Hi8 with KitKat was dead under Ubuntu (though working fine in Fedora 20 and Windows 7), now it works.
It's quite remarkable how, more than a year after the bug was reported, this continues to remain unsolved.

---

### Post by cjsmall on 2015-10-07
These instructions worked with my last Samsung phone, but I cannot get it to work on a Ubuntu 15.04 system with the LG G4 running Android 5.1.  The phone thinks it is connected to the system, by attempts to access the device in the Nemo file viewer result in the message:

```
Could not display "mtp://[usb:007,009]".
Error: Location is already mounted
Please select another viewer and try again
```

**mount**(8) does not show the phone's internal and/or external cards being mounted.  Any idea why it reports "already mounted"?

Has anyone else been able to get an LG G4 to mount?

---

### Post by Asmodel on 2015-10-10
I'm on Ubuntu 14.04, trying to connect my samsung galaxy S5. Previously I could connect it using PTP, but wished to connect it MTP for various reasons. After following your directions, I now cannot connect it even using PTP.

I received the following error message:

“mtp:host=%5Busb%3A001%2C019%5D” could not be found. Perhaps it has recently been deleted.

How should I fix this?

---

### Post by jaapscheper on 2015-10-13
Thanks! I'm using Ubuntu 14.04 and I could see files on my LG L-90 phone, but was not able to download them to my computer. By following your tutorial, I'm able to copy files from my phone to my pc and back.

---

### Post by anonymous15 on 2015-10-19
Nope, didn't work for LG Optimus. MTP sucks.

---

### Post by Jean_MYTAZ on 2015-10-19
Unable to connect ubuntu 14.04 with a cheap tablet Klipad D71 despite this good tuto !!!
(I would like to root this tablet because the internal storage is too small for installing a little more apps...)
Is there other people with the same problem ? - work no more with windoze...

---

### Post by dwsdad on 2015-10-27
Man, I'm glad I stumbled across this thread.  I've gotten further following this tutorial than I have with anything else I've found, but I'm still having and issue.

I have an LG V410 that is soft bricked - it gets stuck in a boot loop, but I can get it into download mode, which I have it in now.  Thanks to this tutorial I have at least now gotten to:

 lsusb:
Bus 001 Device 004: ID 1004:633e LG Electronics, Inc. G2 Android Phone [MTP mode]


 mtp-detect:
libmtp version: 1.1.9

Listing raw device(s)
Device 0 (VID=1004 and PID=633e) is a LG Electronics Inc. LG G Flex 2.
   Found 1 device(s):
   LG Electronics Inc.: LG G Flex 2 (1004:633e) @ bus 1, dev 4
Attempting to connect device(s)
PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device
LIBMTP PANIC: failed to open session on second attempt
Unable to open raw device 0
OK.

So, at least now mtp is seeing the device.  Any thoughts as to why it cannot open the device?

---

### Post by ssreddy555 on 2015-11-07
My Samsung Note 3 Neo is connecting to Ubuntu 15.04 as MTP directly without making any changes described in this tutorial. The device and the card are displayed separately and all the files on the device can be browsed and transferable both ways.

---

### Post by groundlifter on 2015-11-26
> **write_mem said:**
> Hi,

After much looking around I was never able to find a how-to guide(or should I say the ones that did never worked)on how to connect my android tablet/phone to Ubuntu for file transfers, sure there's other means of doing it wireless via your LAN, but truth be told MTP and Ubuntu don't exactly see eye to eye and as such I hope the following guide I put together saves someone a lot of time and effort. This was performed on Ubuntu 14.04 LTS

**[COLOR=#000000]STEP 1[/COLOR]**

):P As you wanted to know if this worked, it did. Every step went perfectly and now i can access my Xperia Z5 with os Linux Mint. Appreciated alot! ):P

---

### Post by cjsmall on 2015-12-09
Now on Xubuntu 15.10.  I have followed all the instructions noted above and still cannot connect the LG G4 phone.  Has anyone with a G4 been able to connect?

---

### Post by dollseye on 2015-12-13
[QUOTE=write_mem
All feedback gladly welcome, would like to know if this has worked for this others too.[

Following your advice got my Samsung Core Prime recognized for the first time on 14.04 LTS

I very much appreciate your help, as I always do *all* of the Ubuntu support.

---

### Post by Aviendha09 on 2015-12-13
Yesterday, I could move files to and fro my android phone and my youngest daughter's mp3 player. Then, my eldest's Sony walkman arrived by mail and I transferred files to it. The transfer rate was excruciatingly slow, but worked. 

Today, even after multiple reboots, none of our devices are recognized, not even LSUSB or dmesg. USB flash drive is fine. I tried a few things here and there, mostly old(er) resources. Could Sony's "windows only" support have caused my usb mtp devices to be blacklisted ?
How do I go about fixing this issue ?

---

### Post by mozgren on 2016-01-02
Thanks!  
I had to make ***/etc/udev/rules.d/51-android.rules*** but my Kindle Fire is recognised now.
:D

---

### Post by kurja on 2016-02-02
worked here. I got confused by the screen lock at first.... :D

---

### Post by oscar43 on 2016-02-04
This tutorial is solid gold for anyone having this issue,  which are probably most people with Ubuntu and an Android.  It worked splendidly for my Ubuntu 14.04 lts distro and brand new blu energyx Android. After,  I might add,  many hours of trying to find any other effective workaround.

---

### Post by sammiev on 2016-02-04
I really must be one of the lucky ones, my Android just works when set for MTP.

Transfer files all the time between my device and the computer.

---

### Post by simon127 on 2016-02-05
I just installed Kubuntu 14.04 and have worked through these steps to connect my Samsung Galaxy SIII. It worked perfectly. Thank you for sharing!

---

### Post by 5-ubuntx-o on 2016-02-10
Possibly off topic, but if all you are looking to do is access files remember there are many workarounds. Most people are doing this for photos and vids, right ?

1. card readers, unmount your storage and remove.
2. bluetooth.
3. wifi (eg. SaMBa client) to a server.
4. email in and out.
5. mms in and out.
6. http upload/download to webserver/cloud.
7. ftp, ssh etc.

Yes, things should just work, but redundancy is good for us all.

---

### Post by dave157 on 2016-02-21
For ubuntu 14.04 and a Samsung note how does this change if any? Or just install the one on the package or add a PPA?

---

### Post by r-salas01 on 2016-02-22
[h=1][Connect an Android device using MTP in Ubuntu 14.04 LTS]("http://ubuntuforums.org/showthread.php?t=2226702") - SOLVED WORKED[/h]
THANK YOU!

---

### Post by Trogladyte on 2016-03-27
This isn't working for me. I am trying to connect HTC One XL to 14.04. I am getting "Unable to open MTP device '[usb:001,008]'" I can see "Android Phone" in launcher, and can see the folders in internal storage, but there's no MTP access.

Any ideas?

---

### Post by him610 on 2016-03-31
Followed the steps in your procedure substituting the vendor id and device id of my own android tablet. 
Worked like a charm; however, I then connected my android phone and it too was recognized without any additional modification of the files. 
Thanks.

---

### Post by massimiliano-polito on 2016-08-18
I successfully followed the tutorial up to step 2 then I got stuck at  step 3: when I make "lsusb" I don't get anything about my phone.  Actually, the output is the same whether the phone is connected or not:

```
max@max-HP-Stream-Notebook-PC-13:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:b001 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 002: ID 05c8:036e Cheng Uei Precision Industry Co., Ltd (Foxlink) Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
max@max-HP-Stream-Notebook-PC-13:~$
```

My phone is a Huawei G Play Mini (model number: CHC-U01, Android 4.4.2).

I'm using Ubuntu Studio 14.04.

```
max@max-HP-Stream-Notebook-PC-13:~$ uname -a
Linux max-HP-Stream-Notebook-PC-13 3.19.0-66-lowlatency #74~14.04.1-Ubuntu SMP PREEMPT Tue Jul 19 22:04:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```

Any help would be greatly appreciated.

Regards,
Max

---

### Post by ajgreeny on 2016-08-18
Try a different cable; are you using the USB cable that came with the phone?

I have a Huawei phone and the connection works fine after following this thread.

---

### Post by massimiliano-polito on 2016-09-04
> **ajgreeny said:**
> Try a different cable; are you using the USB cable that came with the phone?

I have a Huawei phone and the connection works fine after following this thread.

Sorry for the delay. I was not notified about your answer.

Honestly, I can't remember which is the original cable, I've got some cables and they look to me all the same. I tried with a couple of them always with the dame (bad) result.

I'm now trying to upgrade to the latest Ubuntu version to see if this can help.

Thanks.

Bye,
Max

---

### Post by gde061-www on 2016-09-21
I tried following the tutorial to connect my Kindle Fire Gen2 to my system running 14.04.  In "normal" mode, it will connect via MTP *after I swipe the Kindle and enter the screen unlock code*.  This is same behavior when I try to hook up any other Android / Apple device.  The problem is I want to connect in Fastboot mode, but in fastboot the Kindle has no "unlock" screen.

The error I get is {  >  gde061@TP-E530-laptop:~$ mtpfs
Unable to open ~/.mtpz-data for reading, MTPZ disabled.Listing raw device(s)
Device 0 (VID=1949 and PID=0007) is a Amazon Kindle Fire (ID1).
   Found 1 device(s):
   Amazon: Kindle Fire (ID1) (1949:0007) @ bus 1, dev 3
Attempting to connect device
LIBMTP PANIC: Unable to find interface & endpoints of device
Unable to open raw device 0


I have installed android-tools-fastboot from the SW center (as well as android-tools-adb)...  and adb seems to work fine in "normal" mode.  

How do I get this device to mount in fastboot mode so I can use fastboot commands?

---

### Post by massimiliano-polito on 2016-09-21
I solved the problem upgrading to 16.04, nothing else worked.

---

### Post by tantric3 on 2016-10-29
the quality and length of the cable you use to connect are of *critical* importance

---

### Post by av10191 on 2017-01-07
What a wonderful tutorial! everything is explained in perfect detail and with admirable clarity.
THANK YOU EVER SO MUCH.
Everything worked.

---

### Post by pepper3 on 2017-02-26
> **av10191 said:**
> What a wonderful tutorial! everything is explained in perfect detail and with admirable clarity.
THANK YOU EVER SO MUCH.
Everything worked.

I did this for Motorola G4 Play (Unlocked GSM) and after following all the tutorial it did not work.  Using Ubuntu-Gnome 16 LTS

Then I went into developer options and changed the "Select USB Configuration" to PTP Picture Transfer Protocol.  After I did that I was able to see the DCIM and pictures folder.  THen I went in and changed the same setting back to MTP and voila!  It is working now.  
[B]
[SIZE=3]BEFORE YOU BEGIN THE STEPS IN THIS TUTORIAL[/SIZE][/B][SIZE=3]:[/SIZE]  Recommend to people running the recent version of Linux to just try going into Developer Options (inside android) and toggling the setting from MTP to PTP and then back to MTP.  Maybe that is all you actually need to do (Maybe, give it a shot)

Tags:  Motorola G4 Play Linux USB connect connection

---

### Post by aturnwald on 2017-11-30
Hello Genius / Einstein,
YOU ARE GREAT !!!!! I searched for ages for a functioning routine for my old stupid Android HTC-Sense mobile. And I
found nothing at all, also nothing worked. Til, today, totally depressed I saw your text and I tried it. AND ???? 
Great, it worked on the 1st try. Have many many " Thank You ", you are famous.
cheers Toni
PS: I use Ubuntu 16.04

---

### Post by peddie on 2018-02-12
After struggling for days with MTP and then using FTP over WiFi (FileZilla), I came across this thread today.  Copying about 2600 MP3's to my laptop used to take more than 12 hours over MTP. After following these instructions it took ... drum roll and trumpet fanfare please... 10 minutes!
My eternal heartfelt thanks to write_mem.
BTW I'm new to Linux and run Mint 18.3 Cinnamon kernel 4.10.0-38 on a Lenovo Ideapad 110. Very very satisfied!

---

