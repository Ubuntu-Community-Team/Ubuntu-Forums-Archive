---
title: "Plan 9 (from Bell Labs) virtualisation"
date: 2008-04-28
forum: Virtualisation
---

### Post by JGT on 2008-04-28
Hi I'm a novice Linux user but I would really like to play with Plan 9 in a virtual enviroment.

The current UK edition of Linux Format gives instructions on how to do this under qemu, but I couldn't get it to work. (qemu launches then this is followed with an error like "no bootable CD in drive" (from memory, sorry, I'm at work).

If there is an idiot-proof way of running Plan 9 under Ubuntu 8.04, I'd be grateful if you could kindly provide instructions.

Thanks

John

---

### Post by JGT on 2008-04-28
More details:

I've burnt plan9.iso to a CD with Brasero. That created a CD with a lot of files on it - none of them called plan9.iso, if that's relevant

I've also got a copy sitting on my desktop.

At the terminal

[PHP]qemu-img create -f qcow Plan9.qcow.img 2G[/PHP]

That went okay.

Then I tried 

[PHP]qemu -hda Plan9.qcow.img -cdrom plan9.iso -boot d[/PHP]

Which gave me an output of:

qemu: could not open disk image plan9.iso

Sorry if I'm not tagging this correctly. 

Anyway, I tried (a pure guess):

[PHP]qemu -hda Plan9.qcow.img /home/john/Desktop/plan9.iso -boot d[/PHP]

That's probably garbled rubbish. It did launch qemu

but with a message

Booting from CD-Rom
CDROM boot failure code: 0003
Boot from CD-Rom failed: could not read the boot disk
FATAL: No bootable device.

Trying  [PHP]qemu -cdrom Plan9.qcow.img /home/john/Desktop/plan9.iso[/PHP]

gives me a 0005 failure code.

Reading the man pages are somewhat beyond my expertise, as I'm sure you can tell.

I feel I'm close - can anyone help?

---

### Post by go_beep_yourself on 2008-05-08
> **JGT said:**
> More details:

I've burnt plan9.iso to a CD with Brasero. That created a CD with a lot of files on it - none of them called plan9.iso, if that's relevant

I've also got a copy sitting on my desktop.

You should have provided a link with the instructions you are following. I don't believe the instructions say to burn the image. I think you would only burn the image if you were going to install it on your machine, not run it with virtualization. I don't suggest you try to install it that way because of limited hardware support. You shouldn't be using Linux unless you are trying to understand it. Just copying and pasting commands won't teach you anything. I don't have qemu anymore, but I found the man page from searching google. You can use the burned cd, but then you must do this command.

```
qemu -hda Plan9.qcow.img -cdrom /dev/cdrom -boot d
```

instead of:

```
qemu -hda Plan9.qcow.img -cdrom plan9.iso -boot d
```

> At the terminal

[PHP]qemu-img create -f qcow Plan9.qcow.img 2G[/PHP]

That went okay.

Then I tried 

[PHP]qemu -hda Plan9.qcow.img -cdrom plan9.iso -boot d[/PHP]

Which gave me an output of:

qemu: could not open disk image plan9.iso

Sorry if I'm not tagging this correctly. 

Anyway, I tried (a pure guess):

[PHP]qemu -hda Plan9.qcow.img /home/john/Desktop/plan9.iso -boot d[/PHP]

but with a message

Booting from CD-Rom
CDROM boot failure code: 0003
Boot from CD-Rom failed: could not read the boot disk
FATAL: No bootable device.

That's probably garbled rubbish. It did launch qemu


You were close to right, but first you should have looked at the man page to see what that -cdrom option does. Don't guess!! If you don't understand why something did not work, then you are less likely to be able to fix it. You received the errors because qemu could not find the plan9.iso file. When you don't give the full path to the file, then qemu is going to look for the file in your working directory. The "pwd" command shows your working directory. I think what happened is that qemu looked for plan9.iso in your home directory and did not find it there. You said you had the plan9.iso file on your desktop. You must tell it where it is with -cdrom option, so this would be correct.

```
qemu -hda Plan9.qcow.img -cdrom /home/john/Desktop/plan9.iso -boot d
```

> Trying  [PHP]qemu -cdrom Plan9.qcow.img /home/john/Desktop/plan9.iso[/PHP]

gives me a 0005 failure code.

Reading the man pages are somewhat beyond my expertise, as I'm sure you can tell.

I feel I'm close - can anyone help?

If you can't understand man pages, then you probably need to learn some basic things about Linux first such as these commands.

pwd
cd
ls
mount
learn about file permissions and ownerships:
chown
chmod
and others

An easy to understand Linux book is probably what you need. You could go to a book store, look at some of the books, find one you like that covers alot of topics in Linux or Ubuntu, not specific to one thing about Linux, and then purchase it.

If you burned the iso as an image and have it in your drive, this should work.

```
qemu -hda Plan9.qcow.img -cdrom /dev/cdrom -boot d
```

---

### Post by JGT on 2008-05-08
Thanks very much for your clear instructions. Plan 9 is working now! 

I do need to start learning Linux properly rather than paste commands from forums into the terminal all the time. 

Kind regards

John

---

