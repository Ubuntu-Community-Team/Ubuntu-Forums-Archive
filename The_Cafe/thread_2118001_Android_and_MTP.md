---
title: "Android and MTP?"
date: 2013-02-20
forum: The Cafe
---

### Post by mamamia88 on 2013-02-20
What the heck are they doing?  It seems like they have completely removed mass storage support in all newer phones?  Is there a reason they would remove such a useful feature that allows it to work on any operating system period?  Seems like they are just turning into another apple taking away features just because they think they know better than the consumer.

---

### Post by 3rdalbum on 2013-02-20
> **mamamia88 said:**
> What the heck are they doing?  It seems like they have completely removed mass storage support in all newer phones?  Is there a reason they would remove such a useful feature that allows it to work on any operating system period?  Seems like they are just turning into another apple taking away features just because they think they know better than the consumer.

Why, do you think you know better than Google's engineers?

Android originally was limited to a small amount of storage for the system partition, and needed an SD card to get more storage. Still, the SD card could only be used as storage for files, not for programs (partly fixed in Android 2.1).

The limitation was removed in Android 3, but it had to be done by using SD cards as part of system storage. You can't unmount them while the phone is running, so you can't have them behave as USB mass storage.

Hence the need for MTP.

MTP is an open protocol. Linux supports it, but not very well. MTP has been around for a long time and it is plain embarrassing that our MTP support is so terrible.

In short, don't blame Google. Blame LIBMTP.

---

### Post by mamamia88 on 2013-02-20
> **3rdalbum said:**
> Why, do you think you know better than Google's engineers?

Android originally was limited to a small amount of storage for the system partition, and needed an SD card to get more storage. Still, the SD card could only be used as storage for files, not for programs (partly fixed in Android 2.1).

The limitation was removed in Android 3, but it had to be done by using SD cards as part of system storage. You can't unmount them while the phone is running, so you can't have them behave as USB mass storage.

Hence the need for MTP.

MTP is an open protocol. Linux supports it, but not very well. MTP has been around for a long time and it is plain embarrassing that our MTP support is so terrible.

In short, don't blame Google. Blame LIBMTP. Again i'm gonna call bs.  I can mount my phone in mass storage mode right now with no problems and it's been upgraded to 4.2.2 via unofficial roms. I'm sure there is a technical reason like you say.  Sure maybe I can't use the phone and apps while it's mounted but at least it works. Oh and mtp is a joke on linux what's up with that?

---

### Post by Nburnes on 2013-02-20
> MTP is a big improvement over USB mass storage &#8212; for devices with lots of internal memory, a manufacturer no longer needs to come up with some hard partition between the USB mass storage and internal storage. Instead, they are all in one partition, with MTP providing access to the directory of media files that would normally be available through USB mass storage.This means there is no longer a need for apps on SD card for such devices, because what used to be the &#8220;internal SD card&#8221; is in the same partition as where applications are stored. The storage on your device can be used for either applications or media, depending on what you want to put on it. You aren&#8217;t stuck with how much space the manufacturer decided to leave for the two areas.

Oh also this means that the media storage doesn&#8217;t need to be unmounted from Android when it is being access through the PC.

[http://www.androidpolice.com/2011/11/18/impromptu-qa-session-with-android-engineer-dan-morrill-brings-to-light-reasons-behind-galaxy-nexus-lack-of-usb-mass-storage/](http://www.androidpolice.com/2011/11/18/impromptu-qa-session-with-android-engineer-dan-morrill-brings-to-light-reasons-behind-galaxy-nexus-lack-of-usb-mass-storage/)

Also, MTP mounts automagically and works great in 13.04. 

[http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html](http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html)

---

### Post by mamamia88 on 2013-02-20
> **Nburnes said:**
> Also, MTP mounts **automagically** and works great in 13.04. 

[http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html](http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html)

great word. maybe i'll try 13.04 when it releases.  i'm just grumpy.  one of the main reasons i bought android stuff instead of apple stuff.   sure i can use adb which works fine or i can use go-mtpfs but i prefer to have the device integrated into the os and work like other devices i plug in like my external harddrive.  i'm sure there are benefits to mtp it's just i don't see them and i don't see why they they can't at least have it as an option like before.   also automagically is my new favorite word

---

### Post by kevdog on 2013-02-20
The new gvfs release really helped me.  The phone automounts now and th
the phone automatically mounts.  It's actually great.  I'd recommend you try out the new gvfs version.

---

### Post by mamamia88 on 2013-02-20
> **kevdog said:**
> The new gvfs release really helped me.  The phone automounts now and th
the phone automatically mounts.  It's actually great.  I'd recommend you try out the new gvfs version.

That would probably be more effort than it's worth to me.  My phone still works msc.  And I bought my nexus 7 thinking i'd watch a lot of videos on it but honestly haven't watched one in the few months i've owned it.  I don't put music or anything on it since who wants to listen to music on anything that big?  It doesn't have a rear facing camera so i don't take pictures with it either.  And if i really needed to copy a file over to it i would just use ```
adb push path/to/file /sdcard/
``` which really isn't that difficult.  I just needed to rant.

---

### Post by 3rdalbum on 2013-02-20
> **mamamia88 said:**
> That would probably be more effort than it's worth to me.  My phone still works msc.  And I bought my nexus 7 thinking i'd watch a lot of videos on it but honestly haven't watched one in the few months i've owned it.  I don't put music or anything on it since who wants to listen to music on anything that big?  It doesn't have a rear facing camera so i don't take pictures with it either.  And if i really needed to copy a file over to it i would just use ```
adb push path/to/file /sdcard/
``` which really isn't that difficult.  I just needed to rant.

My father has a Nexus 7. I tried to get libMTP to work with it on 12.10, followed the instructions, didn't work. Adb is too clunky a solution for Dad.

In the end I assigned the Nexus a static IP address and installed a wifi FTP server on it. Then I bookmarked the FTP server on the computer. The whole process is nearly as easy as USB Mass Storage. I fully recommend doing it this way, especially for new users, until 13.04 or when MTP support breaks again in 13.10. Trust me, MTP support on Linux will break again sooner or later.

---

### Post by kevdog on 2013-02-20
Good solution with the ntp client

I prefer actually an ssh client over a ftp client, however its a similar solution -- just with a little bit more security and encryption in the process.  

Yes -- MTP is a pain.  No doubt. The new gvfs version with builtin mtp is the slickest I've seen, however no doubt it will probably break a few times in the process.

---

### Post by The Cog on 2013-02-20
> **kevdog said:**
> The new gvfs version with builtin mtp is the slickest I've seen, 
What new version is this? Are you referring to *buntu 13.04, or is there something else around?

---

### Post by kevdog on 2013-02-20
I actually compiled gvfs from git, however yes --- there is a ppa around that is meant for the 13.04 release.  It's actually quite amazing how well the interface works.  I'm using a Cinnamon desktop, so it integrated with nemo really well.  I know there it also works with thunar, however I'm uncertain the compatibility with other file managers in case your not into the entire gtk libraries.

---

### Post by donniezazen on 2013-02-20
> **mamamia88 said:**
> What the heck are they doing?  It seems like they have completely removed mass storage support in all newer phones?  Is there a reason they would remove such a useful feature that allows it to work on any operating system period?  Seems like they are just turning into another apple taking away features just because they think they know better than the consumer.

Mounting internal storage using mass storage protocol would make it inaccessible to the Android OS making all apps that rely on it unusable. On the other hand MTP make the storage available for both Android OS and you on your system. libMTP is a work in progress.

```
sudo add-apt-repository ppa:langdalepl/gvfs-mtp
sudo apt-get update
```

Source:-[Webupd8](http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html)

---

### Post by The Cog on 2013-02-20
> **kevdog said:**
> I actually compiled gvfs from git, however yes --- there is a ppa around that is meant for the 13.04 release.  It's actually quite amazing how well the interface works.  I'm using a Cinnamon desktop, so it integrated with nemo really well.  I know there it also works with thunar, however I'm uncertain the compatibility with other file managers in case your not into the entire gtk libraries.

Ah, thanks. It's thunar that would interest me. I think I'll take the lazy route and wait for 13.04, then try it out.

---

### Post by Dafydd on 2013-04-18
Just trying out the new 13.04 ubuntu and plugged in my Samsung to recharge. Very surprised to see Nautilus open it up automatically allowing me to exchange files. This is so much easier than the various solutions I've tried out over the past year since MTP came around. Great.

---

