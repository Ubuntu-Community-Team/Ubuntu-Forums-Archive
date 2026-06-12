---
title: "[SOLVED] Proxy error in Virtual box"
date: 2007-10-19
forum: Virtualisation
---

### Post by ~~Tito~~ on 2007-10-19
I keep getting that when connecting usb devices. . . I have done the thing where you put something in the file and I have added my self to the vbox group thing. So what is up? I need this fixed.

---

### Post by ~~Tito~~ on 2007-10-19
There was this link I found but it never works for me. . .
[http://doc.gwos.org/index.php/VirtualBox#Enable_USB_devices](http://doc.gwos.org/index.php/VirtualBox#Enable_USB_devices)

---

### Post by ~~Tito~~ on 2007-10-19
Also usb works but it wont let me connect sometimes. I connected my iPhone when I first got it but then it stopped connecting 5 sec after the usb found thing popped up in windows. . .

---

### Post by ~~Tito~~ on 2007-10-19
Also, I dont know where to put what these people said:
[http://ubuntuforums.org/showthread.php?t=551469&highlight=proxy+in+virtual+box](http://ubuntuforums.org/showthread.php?t=551469&highlight=proxy+in+virtual+box)

where? In what txt file? And where could I find the usbusers group? I checked and I don't see anything that is usb.

Please help?

---

### Post by ~~Tito~~ on 2007-10-19
Please people? I need to fix my iphone and have everything error less. . .

---

### Post by ~~Tito~~ on 2007-10-19
Anyone? I need this fixed like ASAP!

---

### Post by ~~Tito~~ on 2007-10-19
Can anyone tell me?

---

### Post by ~~Tito~~ on 2007-10-19
Some one help me please!

---

### Post by ice60 on 2007-10-19
you can try running sudo tail -f /var/log/messages while you plug in the usb device to see what happens.

if you are talking about a virtual machine you could try looking on their forums for usb support :) maybe try updating it ??

---

### Post by ~~Tito~~ on 2007-10-19
Their forums have under 10000 people and no one ever answers and if they do its days later. I need this answered now.

---

### Post by ice60 on 2007-10-19
lol i just read the thread, i've no idea if this is right, but as no one else is helping try this - you put that stuff in the fstab
gksudo gedit /etc/fstab
and add this -
usbfs    /proc/bus/usb    usbfs    devgid=<something>,devmode=664,nodev,nosuid,noexec    0    0

the something bit is found in /etc/group so you can do 
grep usbusers /etc/group
and add the number it gives i think.

---

### Post by chamberlain2006 on 2007-10-19
That is likely the problem.  Your iPhone may also try to mount on the Linux side.  When you attach it, look at your desktop and see if an icon appears for it.  If it does, right click and choose "unmount".  Also, please give us a break.  A lot of people need help right now with the new release.  Also, VirtualBox is a difficult thing sometimes that people may not be able to help with.

---

### Post by ~~Tito~~ on 2007-10-19
Yea, when my iphone mounts it mounts as a camera and not as a Drive. Ok, I will try that and I will post asap! I need to unbirck my iphone. . . .

---

### Post by ~~Tito~~ on 2007-10-19
i put in that command in the terminal and It doest work (The 2nd one not the 1st one. I cant find the groups folder in ect. Is it my ect or the main ect?

---

### Post by ~~Tito~~ on 2007-10-19
Ok, I figured it out but I don't see any usb user group in the txt file of group. . . How would I ad it?

---

### Post by ice60 on 2007-10-19
one reason i don't normally help much is i have really bad concentration! i just read this thread again, and if things don't work you can run this instead -
sudo VBOX=$(grep vboxusers /etc/group | sed 's/vboxusers:x:\(.*\):.*/\1/')
sudo mount -t usbfs -o devgid=$VBOX,devmode=664,nodev,noexec,nosuid none /proc/bus/usb

and take the stuff you put in fstab out again -
gksudo /etc/fstab

---

### Post by ~~Tito~~ on 2007-10-19
Same here. So that will add the usb user group?

---

### Post by ~~Tito~~ on 2007-10-19
Hey neither command did anything. The 1st one made an error that VBOX=1001 isn't a command and the other one just skipped and went back to normal.

---

### Post by ice60 on 2007-10-19
actually maybe run this instead -
sudo VBOX=$(grep vboxusers /etc/group | sed 's/vboxusers:x:\(.*\):.*/\1/') && mount -t usbfs -o devgid=$VBOX,devmode=664,nodev,noexec,nosuid none /proc/bus/usb

yeap, that will mount it and get it working, i think it just needed to know where to find it, it was looking in the wrong place.

---

### Post by ice60 on 2007-10-19
i suppose you need to have your virtaul box running and the usb device plugged in before you run that command

---

### Post by ~~Tito~~ on 2007-10-19
LOL, ok. let me try now.

---

### Post by ~~Tito~~ on 2007-10-19
Nope still the same error
```
tito@TITOS-LAPTOP:~$ sudo VBOX=$(grep vboxusers /etc/group | sed 's/vboxusers:x:\(.*\):.*/\1/') && mount -t usbfs -o devgid=$VBOX,devmode=664,nodev,noexec,nosuid none /proc/bus/usb
sudo: VBOX=1001: command not found
tito@TITOS-LAPTOP:~$ 

```

VBOX is running so?

---

### Post by ice60 on 2007-10-19
OK you can try manually. open /etc/group and look for vboxusers and post back what it says

---

### Post by ~~Tito~~ on 2007-10-19
Wait? I thought you said usb? I have it. I thoght you said usbusers?? Ok, so now I will do what you said the first time.

Ok, so when I gonna put it in the fstab file where do i put it? Just put it and the last line? or push enter then put it?

---

### Post by ice60 on 2007-10-19
it's a bit like the blind leading the blind here, but if it doesn't work try this when you have the number -

the next bit looks like it's saying substitute the first occurance of the output with the output, but i'm sure that's not right, so just try putting the number you get for vboxusers here -
sudo mount -t usbfs -o devgid=[color=red]right here[/color],devmode=664,nodev,noexec,nosuid none /proc/bus/usb

---

### Post by ~~Tito~~ on 2007-10-19
WOOT!! No more error. Now My iphone wont connect. . .

If you would have said vboxusers then I would have got it. It works now. But I need to get that iphone to connect now. It charges for a sec and then it stops and It doesn't go under windows either.

---

### Post by ice60 on 2007-10-19
> **~~Tito~~ said:**
> Wait? I thought you said usb? I have it. I thoght you said usbusers?? Ok, so now I will do what you said the first time.

Ok, so when I gonna put it in the fstab file where do i put it? Just put it and the last line? or push enter then put it?
i did say usbusers, maybe it was wrong, sorry, try putting that number in there right at the bottom of the fstab (i mean last line), like this -
usbfs /proc/bus/usb usbfs devgid=<something>,devmode=664,nodev,nosuid,noexec 0 0

put the number where it says <something>, i've pretty much lost track of what's being said so i hope that works!

---

### Post by ~~Tito~~ on 2007-10-19
```
tito@TITOS-LAPTOP:~$ sudo tail -f /var/log/messages
Oct 19 15:32:48 TITOS-LAPTOP kernel: [ 4917.055236] usb 5-1: USB disconnect, address 5
Oct 19 15:32:49 TITOS-LAPTOP kernel: [ 4918.805665] usb 5-1: new high speed USB device using ehci_hcd and address 7
Oct 19 15:32:49 TITOS-LAPTOP kernel: [ 4918.940872] usb 5-1: configuration #1 chosen from 3 choices
Oct 19 15:34:50 TITOS-LAPTOP kernel: [ 5039.425420] usb 5-1: USB disconnect, address 7
Oct 19 15:34:53 TITOS-LAPTOP kernel: [ 5042.602561] usb 5-2: new high speed USB device using ehci_hcd and address 8
Oct 19 15:34:53 TITOS-LAPTOP kernel: [ 5042.737882] usb 5-2: configuration #1 chosen from 3 choices
Oct 19 15:35:04 TITOS-LAPTOP kernel: [ 5053.352917] usb 5-2: USB disconnect, address 8
Oct 19 15:35:07 TITOS-LAPTOP kernel: [ 5056.078461] usb 5-2: new high speed USB device using ehci_hcd and address 9
Oct 19 15:35:07 TITOS-LAPTOP kernel: [ 5056.226204] usb 5-2: configuration #1 chosen from 3 choices
Oct 19 15:36:17 TITOS-LAPTOP kernel: [ 5125.939771] usb 5-2: USB disconnect, address 9
Oct 19 15:36:19 TITOS-LAPTOP kernel: [ 5128.005910] usb 5-2: new high speed USB device using ehci_hcd and address 10
Oct 19 15:36:19 TITOS-LAPTOP kernel: [ 5128.149582] usb 5-2: configuration #1 chosen from 3 choices

```

Why does it do that? It connects then disconnects? Some of them are other USB devices but some are the iphone so what is going to happen?

---

### Post by ice60 on 2007-10-19
> **~~Tito~~ said:**
> WOOT!! No more error. Now My iphone wont connect. . .

If you would have said vboxusers then I would have got it. It works now. But I need to get that iphone to connect now. It charges for a sec and then it stops and It doesn't go under windows either.

lol, i can't believe it worked, by the end i had no idea what was going on :lolflag:

did you see someone else posted? do what he said, right-click unmount, then right-click mount, i think it was.

you didn't unlock the iphone, then install the new firmware? that breaks it i think.

---

### Post by ~~Tito~~ on 2007-10-19
When I bought it from this guy thats what i think happened. . . It doesn't mount as a Drive it mounts as a camera and I disabled it where it auto syncs to get the pics, after I did that it doesn't do anything.

---

### Post by ice60 on 2007-10-19
> **~~Tito~~ said:**
> When I bought it from this guy thats what i think happened. . . It doesn't mount as a Drive it mounts as a camera and I disabled it where it auto syncs to get the pics, after I did that it doesn't do anything.
does the phone work at all? if you're saying the firmware broke it, i heard there are fixes on the net and also there's a chance if you take it to apple they'll fix it too.

---

### Post by ~~Tito~~ on 2007-10-19
Everything works except the phone and my sim card allways says invalid sim. Plus I dont have the original sim card for it. . . The modem FW is the 1.1.1 one and I need to downgrade it and the baseband and then unlock it so I can use the iphone with my sim or just go to an at&t store and get the sim for it.

---

### Post by ice60 on 2007-10-19
OK, the best thing to do is find out which hack was used to unlock the phone, there's more then one, then when you know which hack was used just google that iphone hack with unbrick. if you can't find out which hack did it then just go with the hack that's free, and was easiest to use, some cost money and some used the CLI.

i've never used an iphone so i don't know much about them!

---

### Post by ~~Tito~~ on 2007-10-19
anySIM, and I just need the iphone to work in the usb so I can downgrade it. I know how to do it and I am not going to pay unless IPSF makes a complete virginizer and makes everything work again.

---

### Post by ice60 on 2007-10-19
OK, good luck. i'm going to watch a movie :popcorn:

---

### Post by ~~Tito~~ on 2007-10-19
Hmm, what do I do then people?

---

