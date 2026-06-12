---
title: "[SOLVED] Frequency out of range issue..."
date: 2008-07-31
forum: Server Platforms
---

### Post by themadhacker on 2008-07-31
First I would like to say that I have found several posts on this site related to this issue.  However none of them, so far, have been the answer to my particular problem.

I have 6.06 server installed(not 64 ver) and working perfectly as a VMWare host.  I do not have xserver installed as I do not need a GUI on this box.  As I said...its just a VMWare host box.

When I set this box up and installed 6.06 everything went fine.  VMware is fine...and the host OS running on VMWare is fine and have been for quite some time.

My issue is that when I moved this rack chasis to my server rack it gives me the frequency out of range error.  It worked fine with the monitor on my test bench(which at the time was I think an Acer 19" LCD).  It only gives this error when plugged into my console pull out keyboard/monitor KVM controller.

I am assuming that there has to be somewhere outside of x-server config(since I dont even have x-server installed) that has settings for the refresh rates?

I have just been using putty to telnet into the box remotely for administration purposes as the OS still works fine...just cant do anything from the console.  With it out of the rack, I tried an old 17" CRT monitor and it boots fine on this older monitor as well.  Just not on the pull out key/monitor console in my rack.

Anyone else encounter this?  And if so...how did you overcome?

---

### Post by prshah on 2008-07-31
> **themadhacker said:**
> 
I am assuming that there has to be somewhere outside of x-server config(since I dont even have x-server installed) that has settings for the refresh rates?


You can try changing the resolution in /etc/usplash.conf to a more standard level; eg. 1024 x 768. Or you can pass a suitable video module using the "vga" kernel directive; ie, to the end of the current kernel line that you use to boot, add the phrase ```
vga=771
``` or whatever suitable mode you think works/will work. You may need to experiment with a number of parameters. If you don't know a suitable code, you can change the above phrase to ```
vga=ask
``` whereby on startup it will ask you for a suitable mode.

To find out which mode represents what, look for a file svga.txt in your installation's documentation.

---

### Post by themadhacker on 2008-07-31
> **prshah said:**
> You can try changing the resolution in /etc/usplash.conf to a more standard level; eg. 1024 x 768. Or you can pass a suitable video module using the "vga" kernel directive; ie, to the end of the current kernel line that you use to boot, add the phrase ```
vga=771
``` or whatever suitable mode you think works/will work. You may need to experiment with a number of parameters. If you don't know a suitable code, you can change the above phrase to ```
vga=ask
``` whereby on startup it will ask you for a suitable mode.

To find out which mode represents what, look for a file svga.txt in your installation's documentation.

I am still relatively new to linux.  But still there is not usplash.conf in my /etc dir

Im running ubuntu 6.06.1 LTS

Im assuming that your additions to the file are the same file that I am missing?

Thanks for any and all comments in advance. :)

---

### Post by prshah on 2008-07-31
> **themadhacker said:**
>  But still there is not usplash.conf in my /etc dir

Well my usplash.conf reads```

Fri Aug 01 00:28:21 ~:$ cat /etc/usplash.conf 
# Usplash configuration file
xres=1280
yres=1024

```

but I guess you can ignore this. Try the other option: adding the "vga=ask" kernel parameter.

---

### Post by themadhacker on 2008-07-31
> **prshah said:**
> Well my usplash.conf reads```

Fri Aug 01 00:28:21 ~:$ cat /etc/usplash.conf 
# Usplash configuration file
xres=1280
yres=1024

```

but I guess you can ignore this. Try the other option: adding the "vga=ask" kernel parameter.

Thats what I was unclear of...adding the vga attribute to where?

Again...still learning linux at the command line.  GUI's are easier for me...its just I did not want to waste the resources installing X on a server.

---

### Post by prshah on 2008-07-31
> **themadhacker said:**
> Thats what I was unclear of...adding the vga attribute to where?


To do it temporarily (recommended): Press esc to enter the GRUB menu (during bootup); scroll to the usual booting option, but press "e" instead of enter. Scroll down to the second (?) line (the one that starts with "kernel") then press "e" again to edit it. At the end of the line, add a space and add any **one** of the following phrases
```

vga=771
``` == OR == ```

vga=ask
``` 

then press enter; then "b" to boot.

If you find that it solves your problem, post back for advice on how to make it permanent.

---

### Post by themadhacker on 2008-07-31
> **prshah said:**
> To do it temporarily (recommended): Press esc to enter the GRUB menu (during bootup); scroll to the usual booting option, but press "e" instead of enter. Scroll down to the second (?) line (the one that starts with "kernel") then press "e" again to edit it. At the end of the line, add a space and add any **one** of the following phrases
```

vga=771
``` == OR == ```

vga=ask
``` 

then press enter; then "b" to boot.

If you find that it solves your problem, post back for advice on how to make it permanent.


That done the trick.  So making it perm would be killer.

Thanks so much!

---

### Post by prshah on 2008-08-01
> **themadhacker said:**
> That done the trick.  So making it perm would be killer.


From the terminal, give the command ```
sudo nano /boot/grub/menu.lst
``` in the editor screen that opens up, locate the entry for your kernel (as in one of the previous posts), then zoom to the end of it and add the phrase that worked for you (from the previous post)

Then press Ctrl+X, save when prompted, then give the command ```
sudo update-grub
```

From now on the change should be permanent, and take effect every bootup.

Post back with relevant outputs if you run into problems.

---

### Post by themadhacker on 2008-08-05
> **prshah said:**
> From the terminal, give the command ```
sudo nano /boot/grub/menu.lst
``` in the editor screen that opens up, locate the entry for your kernel (as in one of the previous posts), then zoom to the end of it and add the phrase that worked for you (from the previous post)

Then press Ctrl+X, save when prompted, then give the command ```
sudo update-grub
```

From now on the change should be permanent, and take effect every bootup.

Post back with relevant outputs if you run into problems.

Tried making edits as you instructed but they would not stick.

Tried a second time and made sure that the edits had taken effect by closing and then reopening menu.lst and they indeed were made.

However after running the command update-grub, and reloading the file...changes were not there.

Any suggestions?

Thanks

---

### Post by themadhacker on 2008-08-05
Here is what my file looks like

```

## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-26-server
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-server root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-server
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-server (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-server root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-26-server
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

The only thing I did differently was to edit the file from a telnet session rather than directly on the server console.  I did not think that it would matter, and still dont think it does.

But if it does...I can get it back from your earlier suggestion(server is back in rack now) and make the changes again.

Thanks

---

### Post by prshah on 2008-08-05
> **themadhacker said:**
> Here is what my file looks like
```

kernel          /boot/vmlinuz-2.6.15-26-server root=/dev/hda1 ro quiet splash

```

 edit the file from a telnet session rather than directly on the server console.  

Change the above quoted line to read (scroll all the way to the right to see the changes)```
kernel          /boot/vmlinuz-2.6.15-26-server root=/dev/hda1 ro quiet splash [color=red]vga=771[/color]
```

And, I hope you also ran sudo update-grub from the telnet session on the server, rather than quit the telnet session, in which case update-grub would have run on the local machine.

---

### Post by themadhacker on 2008-08-05
> **prshah said:**
> Change the above quoted line to read (scroll all the way to the right to see the changes)```
kernel          /boot/vmlinuz-2.6.15-26-server root=/dev/hda1 ro quiet splash [color=red]vga=771[/color]
```

Thats what I did...exactly.

[QUOTE=prshah]
And, I hope you also ran sudo update-grub from the telnet session on the server, rather than quit the telnet session, in which case update-grub would have run on the local machine.[/QUOTE]

And yes...I did that as well.  My desktop box is Windows XP...so there is no way I could run that command on anything other than the server via telnet.

---

### Post by themadhacker on 2008-08-05
I did not really pay attention, but after performing the tasks again I noticed this when running update-grub

```

root@VMS-3:/boot/grub# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.15-26-server
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

Perhaps it not being able to find the splash image...is the reason its reverting my changes???

Thanks

---

### Post by prshah on 2008-08-06
> **themadhacker said:**
> 
```

root@VMS-3:/boot/grub# update-grub
..
Searching for splash image ... none found, skipping ...
..

```


Nope this is a normal message and doesn't count, unless you have defined a special splash image (you haven't.)

Are you sure you're making the changes in the "correct" server?

---

### Post by themadhacker on 2008-08-06
Yes...Im sure its the correct server as I only have 2 VMware hosts running on linux(this one which is of course Ubuntu and the other is on Fedora Core 6)

I will retry again in a short while directly from the console and report back.  

Thank you very much for sticking with me on this though.

---

### Post by themadhacker on 2008-08-06
Ok...update.

The only way I could get the edit to "stick" was to not run the "update-grub" command.

Using the nano editor I edited the file again from the console and ran the update-grub command it it performed exactly as it did from the term session.  Meaning it removed my edits of vga=771 to the EOL.

Just for S&Giggles, I decided to not run the update command after editing the file and rebooted the box.  Low and behold the console booted up fine this time.

As I already stated, I am still kinda new to Linux and so I cant really even speculate as to why the command made my changes go bye-bye on that file.?.?.?

Thanks so much for helping me though...as your advice did lead to the fix I was needing.

---

### Post by prshah on 2008-08-06
> **themadhacker said:**
> 
The only way I could get the edit to "stick" was to not run the "update-grub" command.

I have an ongoing argument in some other thread regarding this; a poster said update-grub will revert the file to default; I disagreed; now I'm beginning to think server platforms handle update-grub differently. Something to check, something learned.

In any case, you should now mark this thread "solved"; click on "Thread Tools" near the upper right hand side of the page, then click "Mark as Solved".

---

### Post by themadhacker on 2008-08-07
Alright....will do.

And thanks again for your insights. :)

---

