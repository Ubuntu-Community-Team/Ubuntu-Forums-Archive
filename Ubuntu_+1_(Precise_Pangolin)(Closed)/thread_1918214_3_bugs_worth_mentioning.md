---
title: "3 bugs worth mentioning"
date: 2012-01-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by EgoGratis on 2012-01-31
1.) 

Using ppa-purge sometimes "ain" is left behind in the source file and i get errors updating sources list. I have to manually remove "ain" from the sources file and i think i am not the only one.

2.) 

Using gksu nautilus /file always opens one additional empty tab in gedit. It's annoying.

3.) 

"Bluetooth stack" works fine for some things but it has much problems with other things. For example browsing files on device does cause problems for a lot of users. Solving bug like this would make many users happy.

[https://bugs.launchpad.net/ubuntu/+source/obexd/+bug/872044](https://bugs.launchpad.net/ubuntu/+source/obexd/+bug/872044)

If timings are the problems:

[https://bugs.launchpad.net/ubuntu/+source/obexd/+bug/872044/comments/25](https://bugs.launchpad.net/ubuntu/+source/obexd/+bug/872044/comments/25)

Then this should be noted and fixed. Saying user has "crappy phone" (by author of patch) does not solve anything. :D

---

### Post by jbicha on 2012-02-01
The "ain" is short for "main" and it sounds to me like a serious bug.  I've gotten it too but not recently and not with ppa-purge but with  Software Sources (perhaps it's an aptdaemon bug then?).

---

### Post by EgoGratis on 2012-02-15
Looks like "one down"!

[https://bugs.launchpad.net/ubuntu/+source/obexd/+bug/872044](https://bugs.launchpad.net/ubuntu/+source/obexd/+bug/872044)

Or at least now it's clear where the problem exist and workaround exist too. I can't browse files on device just jet but sending/receiving files works with workaround and i hope will work without workaround soon. This is huge improvement and Precise just got some more precision! Now if only Dodge...

I do see to improvements that could be made:

 1.) It's a bit problematic gnome-user-share has to be installed and  to be set up to enable sending files from device to PC over bluetooth. Could this be  improved and integrated in bluetooth control panel?

2.) When user clicks Browse files on device Nautilus could be opened?

I found "Gedit bug":

[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/796076](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/796076)

---

### Post by arpanaut on 2012-02-15
>  Using gksu nautilus /file always opens one additional empty tab in gedit. It's annoying.

I've always thought that this was a not so subtle hint that one should make a backup of system files before editing.

Seriously though, Yes it is annoying.

---

### Post by mc4man on 2012-02-15
> **EgoGratis said:**
> 

I found "Gedit bug":

[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/796076](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/796076)

I don't see that being resolved anytime soon. 
Myself just use sudo gedit or as mentioned sudo -H gedit

That would resolve opening from a term., & there are workarounds for actions or extensions that would allow either sudo or sudo -H to be used without failing (no password.
I just use an entry in /etc/sudoers.d/<a_file> to take care of & a nautilus action to initiate

---

### Post by mdhollis on 2012-02-15
I filed a bug about "invalid text ain" in the oneiric developmental stage but it was marked invalid because I couldn't reproduce it.

It wasn't related to ppa-purge for me but the bug is exactly as you describe it and removing the ain resolves the issue.

---

### Post by EgoGratis on 2012-02-16
About "ain bug". Yes this happens on rare occasions and it is mentioned occasionally for some time now and i thought i mentioned it here too. Who knows it might be fixed already but the real objective for mentioning this bug here was to pay attention if somebody "catches one" and would be able to reproduce it. That would probably share some light on it!

About "Gedit bug" i tried to use sudo instead of gksu(do) but then i realized i was telling everybody else don't use sudo with GUI applications. I guess i will just have to be patient until it's resolved. It was introduced in Ubuntu 11.10 if i am correct so probably it has something to do with Gnome 3. Wild guess.

About the "bluetooth bug". For all the users that would like to use bluetooth devices (mobile phones) with Ubuntu 11.10 and 12.04 and can't because at the moment it does not work i decided to share some light on this (workarounds until mentioned bugs are solved).

1.) Send files to device ...

Delete the device if you have already paired it then enter this command into the terminal:

sudo hciconfig hci0 sspmode 0

Then pair the device and send files to device should work.

[https://bugs.launchpad.net/ubuntu/+source/obexd/+bug/872044](https://bugs.launchpad.net/ubuntu/+source/obexd/+bug/872044)

2.) Browse files on device ...

You have to do step one to make this work. But then you should not use GUI options (button) that mounts the device in Nautilus but you should manually mount the device with obexfs command. When it is mounted you can browse the device with Nautilus.

obexfs -b B8:XX:XX:XX:XX:XX /mounting point (folder)

Replace XX:XX:XX:XX:XX with the one from device. You can find the correct value in GUI Settings or with command hcitool scan!

To unmount the device:

fusermount -u /mounting point (folder)

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/899858](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/899858)

3.) Send files from the device to Ubuntu.

This one has another problem gnome-user-share has to be installed and properly configured. There is no mention of this anywhere so i guess majority of user just assume it does not work? Do what i described here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/933533](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/933533)

It's said this is not a bug so be it, then! If anybody finds this useful try it out!

---

### Post by prusswan on 2012-02-16
I noted some unexpected behavior in gedit3, though it is hard to tell if is a problem with the plugins (which are actually more important to me) or the app itself

---

### Post by EgoGratis on 2012-03-16
Pairing bluetooth device and sending or receive file(s) should works now with latest kernel:

[https://bugs.launchpad.net/ubuntu/+source/obexd/+bug/872044](https://bugs.launchpad.net/ubuntu/+source/obexd/+bug/872044)

I am confident browsing the device with Nautilus will work soon too:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/899858](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/899858)

Fantastic work. I still believe this is a bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/933533](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/933533)

It's a shame because it does work but there is no visual indicator that pressing on the button in default Ubuntu software will not work because needed package is not installed and  configured correctly.

---

### Post by cariboo on 2012-03-16
That bug was marked invalid, because that isn't the way Ubuntu does things, when installing a package, which ever method you use, should inform you what packages are going to be installed, if a package is missing, that's the bug. In the case of your invalid bug, you should have reported that gnome-user-share should be a dependency of the package you installed.

Ubuntu's aim is to be easy to use, opening an window saying you need to install an extra package before what you want to do will work, is just to complicated for many users.

---

### Post by EgoGratis on 2012-03-17
That information alone would save me a day or two of work. For average Ubuntu user that comes down to he/she will never send files from bluetooth device to Ubuntu.

There is a button for send files (to phone) and browse the device and this will probably work in Ubuntu 12.04.

There is no indication:

-User needs to install gnome-user-share package (Personal File Sharing). 
-Enable setting Receive files in Downloads folder over Bluetooth.

If gnome-user-share would be installed by default there would still be no indication it's has to be configured first.

Basically two thing could fix this. Information or the setting should be there in default tool for bluetooth when user click on paired device. I don't think the setting will be there soon? 

> Ubuntu's aim is to be easy to useThen information should be added how to send file from device to Ubuntu over bluetooth until better option (then information) is implemented. Like enabling folder sharing for example.

---

### Post by cariboo on 2012-03-17
If you feel the bluetooth problem is important enough, why not update the wiki page here:

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by EgoGratis on 2012-03-17
The first thing would probably be deleting the content of the Wiki page because it's outdated and too complex. And yes i feel the bluetooth problem is important enough and too bad i can't edit "default tool" in Ubuntu to put this valuable information for the user in it!

:wink:

---

### Post by cariboo on 2012-03-17
If you have a launchpad account, there is nothing stopping you from either editing the present page, or creating a new one.

---

### Post by EgoGratis on 2012-03-22
Browsing the device over bluetooth with Nautilus works now!

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/899858](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/899858)

---

