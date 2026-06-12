---
title: "mount c drive sh help"
date: 2010-02-22
forum: Virtualisation
---

### Post by vickelly on 2010-02-22
windows 7 using VirtualBox 3.1.4 to host Ubuntu 9.10 with guest additions installed.

Well this will show me for the noob I am but I need help getting a command into the right place in ect. I currently have a text doc on my desktop with the command 

sudo mount -t vboxfs C_DRIVE /windows-share

every time I start vbox I click this and choose run in terminal give my password and am on my way. I'd really like this to just run at boot. 

so far I've tried to drag and drop the file into ect (I hope you're loling now) and tried to save it there which I am not able to do....

thank you in advance for your time (btw noob directions will be most helpful. please explain as though you are talking to a child :)

---

### Post by kiranmurari on 2010-02-23
Hi,
   In order to automount your C drive you can add the command your local boot
scripts say, /etc/rc.local file. So your /etc/rc.local file woould look like:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# Automount Windows C drive to /windows-share
mount -t vboxfs C_DRIVE /windows-share

exit 0
```Hope this helps.

---

### Post by vickelly on 2010-02-23
yepp that did it.

to make that happen I opened up a terminal and typed

sudo su

cd ..

cd /etc

gedit rc.local

I then added the command and the notes. 

was this the right way for me to get there?

---

### Post by bmuluu on 2010-02-23
Alternatively, you can edit /etc/fstab to add an entry for your windows or other partitions

[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

---

### Post by kiranmurari on 2010-02-23
@vickelly:
What you have done is correct. Now reboot the guest machine and you should see the C drive auto mounted on /windows-share.

@bmuluu:
You cannot add a mount entry for vboxsf file system type in /etc/fstab, because vboxsf is not initialized prior to fstab being processed. For more details see the following thread: [http://forums.virtualbox.org/viewtopic.php?p=7978](http://forums.virtualbox.org/viewtopic.php?p=7978)

So the best place to add would be /etc/rc.local.

---

### Post by vickelly on 2010-02-23
thanks again for the reply. it fires up perfectly. also thank you for taking the time to answer rather than just pointing to the link on the vbox forums. it seems like everyone there was trying to make this more complicated than it should have been.

---

