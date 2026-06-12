---
title: "FSCK every time I boot"
date: 2012-02-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by VinDSL on 2012-02-18
Ever since my last update (approx 24 hrs ago) whenever I boot/restart Ubu, the HD is checked for errors.

This used to happen (like) every 100 starts (never paid much attention to it). But, now it happens every time.

Anybody else experiencing this :confused:

Not causing a prob... just curious.

---

### Post by Baldrick_NZ on 2012-02-18
Nope, not happening here, Vin.

---

### Post by dcstar on 2012-02-18
> **VinDSL said:**
> Ever since my last update (approx 24 hrs ago) whenever I boot/restart Ubu, the HD is checked for errors.

This used to happen (like) every 100 starts (never paid much attention to it). But, now it happens every time.

Anybody else experiencing this :confused:

Not causing a prob... just curious.

It is a problem. It probably means that your filesystems are not unmounting properly before the system shuts down and are "dirty".

I had this happen to my system last year when VMware stuffed up the install of VMware Player/Workstation and corrupted the order of the /etc/rcx.d startup and shutdown scripts so that the system shut down before the unmounting was completed.

---

### Post by ArtLaForge on 2012-02-18
> **VinDSL said:**
> Ever since my last update (approx 24 hrs ago) whenever I boot/restart Ubu, the HD is checked for errors.

This used to happen (like) every 100 starts (never paid much attention to it). But, now it happens every time.

Anybody else experiencing this :confused:

Not causing a prob... just curious.


I reboot several times a day, and haven't had an issue with fsck, yet.

---

### Post by ventrical on 2012-02-18
Not here either Vin.

---

### Post by JasonR on 2012-02-18
This has been happening to me for a few weeks.  I'm on 11.10 Xubuntu.  I don't know how to fix the problem, so I've just been hitting "I" to ignore the results.  Can anyone point me in the direction of some tutorial or other to help me fix this?

Otherwise, my solution is a clean install of 12.04 in a few months.

---

### Post by kaldor on 2012-02-18
This happens every time I boot up my LAMP VM. I was wondering about it too. It begins an fsck and then cancels it automatically.

---

### Post by nm_geo on 2012-02-18
> **VinDSL said:**
> Ever since my last update (approx 24 hrs ago) whenever I boot/restart Ubu, the HD is checked for errors.

This used to happen (like) every 100 starts (never paid much attention to it). But, now it happens every time.

Anybody else experiencing this :confused:

Not causing a prob... just curious.

Not me either.. 

Interesting I do check the counts on all my partitions before Cloning with 
```
sudo dumpe2fs -h /dev/sda5 | grep -i 'mount count'
```I just increment the sda_5_ to sda_7_ through however many partitions I have at the time.

You can change the max counts to whatever you like with 

```
sudo tune2fs -c 30 /dev/sda5
```I believe if you set the number to -1 you will never get a fsck on boot.  Don't quote me on that one.:D

---

### Post by Ibidem on 2012-02-18
There are two limits--days and mounts since last check.
If you disable the per-n mounts check, it will just count a certain number of days (180, IIRC)--you'd need to disable that check as well.

---

### Post by dcstar on 2012-02-18
> **Ibidem said:**
> There are two limits--days and mounts since last check.
If you disable the per-n mounts check, it will just count a certain number of days (180, IIRC)--you'd need to disable that check as well.

Both are exceptionally stupid things to do.

The boot fsck is **always** done for a reason, either fix the underlying reason or risk data loss through a corrupt filesystem.

---

### Post by ranch hand on 2012-02-18
I would reset the number of mounts.  That file tends to get "fragile" in testing and get goofy.  I have had it change with every upgrade, I think in 9.10-testing.  Any time it changes it runs fsck.

So I would boot on day1 and it would say sda18 has been booted 21 times and run the bugger.  Do the next update and it would say sda18 has been booted 29 times and run fsck.

The command given in post 9 is correct and that is, or was, the default setting (30) here.  Debian likes 21.

One thing I would do is boot to recovery and see if there really is something going on.  If you can follow the scroll then there probably is a problem and you will be able to see it there.  If not run fsck from the prompt and see what it comes up with.

If nothing, just reset the file and forget it til next time.

---

### Post by zika on 2012-02-19
At every boot I get message line that shows that fsck was &#8222;touched&#8220;...
But only on selected mounts (I do have "-1" set so I decide when to check) I do get proper message that drive(s) are being checked...
What of the above is happening at OP...?

---

### Post by apoapo on 2012-03-23
Same here with a fresh Precise 32 bit install. 

Does OPalso use a SSD? Maybe a race condition?

---

### Post by VMC on 2012-03-23
Shut down Precise then reboot using either another Linux os or the livecd. Then fsck the partition in question and see if it finds it "dirty" or clean. If clean then you have another issue.

---

### Post by squilookle on 2012-03-23
Not sure if this has been solved, but I installed KDE 4.8 on my Ubuntu 11.10 install and had this problem for the next couple of hours, I rebooted several times as KDE 4.8 was slow to the point it was unusable, and I had some other issues as well. 

I (sort of) solved both issues in one go by nuking my installation and doing a clean install of Kubuntu 12.04 - not that I'm saying that's the solution for you. I'm posting more to say that mine started acting up after I made changes to my system.

---

### Post by Gregory Lee on 2012-03-23
How can I make the system messages during boot visible for Ubuntu?  (Since I can't tell whether I'm getting fsck's or not.)

---

### Post by cariboo on 2012-03-23
> **Gregory Lee said:**
> How can I make the system messages during boot visible for Ubuntu?  (Since I can't tell whether I'm getting fsck's or not.)

If Plymouth is working properly, you should see that fsck is running on screen. To boot with all the text messages, press **e** at the grub menu, and remove quiet+splash from the kernel line, then follow the on screen instructions to boot.

---

### Post by dentaku65 on 2012-03-23
Maybe there is a forcefsck somewhere...

Try:
```
sudo updatedb
locate forcefsck
```
If exist you can safely delete forcefsck

Or can be only a need of shutdown not reboot of the system

---

### Post by Gregory Lee on 2012-03-23
> **cariboo907 said:**
> If Plymouth is working properly, you should see that fsck is running on screen. To boot with all the text messages, press **e** at the grub menu, and remove quiet+splash from the kernel line, then follow the on screen instructions to boot.
"Plymouth"?  I see that I have a /bin/plymouth, but man/help/info plymouth give no result.   I don't see any grub menu during boot.  Is there a config file somewhere that I can edit to remove "quiet+splash" so that I don't have to do it every time I boot?

I hope there is some online documentation for things like this in Ubuntu that I may yet discover.  My recollection is that Gnome used to have a very good documentation system, but if that is present in Ubuntu, I haven't found it yet.

I don't quite understand why anyone should be having to run fsck.  I thought fsck was not ordinarily needed any more, since Linux got journaling file systems.  In my previous Linux system, I don't recall running fsck in years and years.

---

### Post by cariboo on 2012-03-23
> **Gregory Lee said:**
> "Plymouth"?  I see that I have a /bin/plymouth, but man/help/info plymouth give no result.   I don't see any grub menu during boot.  Is there a config file somewhere that I can edit to remove "quiet+splash" so that I don't have to do it every time I boot?

I hope there is some online documentation for things like this in Ubuntu that I may yet discover.  My recollection is that Gnome used to have a very good documentation system, but if that is present in Ubuntu, I haven't found it yet.

I don't quite understand why anyone should be having to run fsck.  I thought fsck was not ordinarily needed any more, since Linux got journaling file systems.  In my previous Linux system, I don't recall running fsck in years and years.

Plymouth is the Ubuntu logo you should see while booting, between grub and the login screen. If you aren't seeing the grub menu hold down the space bar just after you've turned on your system, or rebooted. Grub doesn't show if you only have a single boot system.

---

### Post by effenberg0x0 on 2012-03-23
I get FSCK at every boot. In my case it is because I also have mountall failing (because of Plymouth). I can't be 100% sure, but I would say that a lot of people that somehow attempted to customize or disable Plymouth, directly or indirectly (like using tools such as BUC) is likely to see this FSCK behavior.

At one point I thought it had to do with prelink/preload, but I was wrong (I think).

```
sudo grep -i "fsck" -A 10 -B 10 /var/log/boot.log
```> Begin: Loading essential drivers ... done.
Begin: Running /scripts/init-premount ... done.
Begin: Mounting root file system ... Begin: Running /scripts/local-top ... done.
Begin: Running /scripts/local-premount ... done.
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... done.
[B]mountall: Event failed
fsck from util-linux 2.20.1[/B]
fsck from util-linux 2.20.1
udevd[665]: missing file parameter for attr
/dev/sda1: clean, 472121/6283264 files, 3435335/25111595 blocks
/dev/sdb1: clean, 72276/61054976 files, 49517050/244190185 blocks
 * Stopping Read required files in advance (for other mountpoints)                                        [ OK ]
 * Stopping OpenSSH server                                                                            [ OK ]
 * Starting OpenSSH server                                                                              [ OK ] Starting Mount network filesystems                                                                    [ OK ]

Regards,
Effenberg

---

