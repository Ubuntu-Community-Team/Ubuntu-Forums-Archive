---
title: "New virtualbox usb problem"
date: 2007-06-16
forum: Virtualisation
---

### Post by penguinchrissy on 2007-06-16
I'm trying to get my ipod to work under virtualbox. 

This is the message I'm getting when I connect my ipod


Failed to create a proxy device for the USB device. (Error: VERR_NOT_SUPPORTED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}



also when my ipod is recognized it always says its in recovery mode but the other problem is my main one.

I have tried a couple of different sites 
[http://doc.gwos.org/index.php/](http://doc.gwos.org/index.php/)
being my main one and a couple of different forums

my problem in not with the usbfs permission I have tried those fixes.

---

### Post by josereyes0 on 2007-07-07
Same exact problem here, if anybody can help, it would be great.

I've also tried all the permission fixes, but that has not made it change.

One thing to note. there are times at which even though the error goes through, Windows XP (virtually) will boot up and begin recognizing the device, starts going through the install device process but then the entire window randomly crashes and I often find myself looking instead at an Ubuntu device prompt, such as "transfer photos", etc.

Help here would be greatly appreciated.

Thanks

---

### Post by punkybouy on 2007-11-17
I get the same error when trying to connect my Timex Data Link watch to a Windows XP guest running on Feisty host.  It appears to be a bug in Virtualbox that has yet to be fixed.

---

### Post by Ylang on 2007-11-17
Same problem here. Has anyone fixed it yet?

---

### Post by firestrife2382 on 2007-11-19
EDIT: Wrong Post sorry about that

---

### Post by punkybouy on 2007-11-20
This fixed my usb issue.  from a terminal type "cat /etc/group" to see your group ID's.  You need to modify the /etc/fstab file.  This is the suggested entry from the Vbox manual:

# 85 is the USB group
none     /proc/bus/usb    usbfs     devgid=85,devmode=664       0 0

Replace 85 with the group ID that matches your system (search /etc/group for &#8220;usb&#8221;
or similar). Alternatively, if you don&#8217;t mind the security hole, give all users access to
USB by changing &#8220;664&#8221; to &#8220;666&#8221;.

---

### Post by firestrife2382 on 2007-11-20
do you mean group id number for users, or vboxuser, or sys ? i dont see entry for usb while i do "cat /etc/group"

---

### Post by punkybouy on 2007-11-24
I used the group ID from my vbox users group.  What group is not important as long as you use it for acess to the usbfs file system and you put the right users (meaning your id) in the group.

---

### Post by phillywize on 2007-11-24
Having the same problem.  An interesting take here:

[http://michael-prokop.at/blog/2007/07/11/virtualbox-usb/](http://michael-prokop.at/blog/2007/07/11/virtualbox-usb/)

The commands he had on that blog worked for me up to the point of having windows recognize and install the ipod.  iTunes, however, detects the ipod as being in recovery mode (someone had this issue above), and I cannot, for love or money, get it to detect properly.  Any thoughts?

Thanks in advance...

---

### Post by hyperair on 2007-12-31
I reckon it's the same problem that doesn't allow Sony Ericsson and Nokia PC Suites to work.

---

### Post by schumifer on 2008-05-21
Since it was mentioned, any available update on connecting a Sony Ericcson phone to virtualbox?

---

### Post by hyperair on 2008-05-21
> **schumifer said:**
> Since it was mentioned, any available update on connecting a Sony Ericcson phone to virtualbox?

Nope, no update. But wammu does everything I need for phone management anyway, so I don't need Virtualbox for this. Besides, Sony Ericsson's PC Suite really irritates me.

---

