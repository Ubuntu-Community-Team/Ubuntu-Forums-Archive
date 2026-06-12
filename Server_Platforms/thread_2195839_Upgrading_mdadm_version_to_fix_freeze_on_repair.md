---
title: "Upgrading mdadm version to fix freeze on repair"
date: 2013-12-26
forum: Server Platforms
---

### Post by gGtUSehIeS on 2013-12-26
I am running 12.4.  I have a problem where when I try to run a repair on my mdadm array my machine locks up (so hard the reset button doesn't even react for 10-15 seconds).  I found this post on the linux-raid mailing list earlier in 2013.  

> [FONT=arial][COLOR=#500050]> Hi,
>
> When I run [COLOR=#222222]repair[/COLOR] on an MD-RAID1 sync_action, the speed slows down and it
> stays like this (below) for hours.
>
> The system is then completely unresponsive to user input. 

[/COLOR]
[/FONT]
[FONT=arial]Hi Justin,[/FONT]
[FONT=arial] this is a known bug.  Fix has been accepted into mainline for 3.11-rc2.[/FONT]
[FONT=arial] Hopefully it will get into 3.10.3 (too late for 3.10.2).

Neil Brown[/FONT]

Then

> [COLOR=#500050][FONT=arial]> Did the fix by chance make it into 3.10.3?[/FONT][/COLOR][COLOR=#500050][FONT=arial]
No, it looks like it missed again.  I gather there was a large inflow of
patches for -stable in the 3.11-rc1 merge window and Greg has been
processing
them in batches.  Hopefully in 3.10.4.

The relevant patch is commit 30bc9b53878a9921b02e3 in mainline.

NeilBrown

[/FONT][/COLOR]
[FONT=arial]--[/FONT]

[FONT=arial]Method to get patch via git and patch kernel:[/FONT]

[FONT=arial]$ git clone[/FONT]
[FONT=arial]git://[/FONT][git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git]("http://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git")
[FONT=arial]$ git log |grep 30bc9b53878a9921b02e3[/FONT]
[FONT=arial]commit 30bc9b53878a9921b02e3b5bc4283a[/FONT][FONT=arial]c1c6de102a[/FONT]
[FONT=arial]$ git show 30bc9b53878a9921b02e3b5bc4283a[/FONT][FONT=arial]c1c6de102a > /tmp/a[/FONT]
[FONT=arial]# patch -p1 < /tmp/a[/FONT]
[FONT=arial]patching file drivers/md/raid1.c[/FONT]
[FONT=arial]Hunk #1 succeeded at 1848 (offset -1 lines).[/FONT]
[FONT=arial]Hunk #2 succeeded at 1886 (offset -1 lines).[/FONT]
[FONT=arial]Hunk #3 succeeded at 1915 (offset -1 lines).[/FONT]

[FONT=arial]Reboot- tested, success, thanks..![/FONT]

Although I stay up with dist-upgrade on 12.04, my mdadm version is 3.2.6 so I obviously am far from having this fix.  I am a windows developer by profession so I know how to use git, but nothing about patching the linux kernel, or the community workflow around development.  
So my question is what is the best way to get this fix on my server so I can do a check/repair on my array without locking it up?  [The mdadm webpage]("https://www.kernel.org/pub/linux/utils/raid/mdadm/") only shows releases to version 3.3, so I'm assuming I will have to check out a branch in git like above.  I am not sure if the above example was used with ubuntu or if it even matters but I don't want to go out of my element mucking with the kernel without some advice.

Also, with whatever method is "best" how will it affect me doing dist-upgrades?  (Should I not do them?  Will they not work?  Do I need to redo the patch afterwards?)  Thanks

---

### Post by rubylaser on 2013-12-26
Hello, James. Welcome to the UbuntuForums!

These issues are not in directly related to mdadm, but to the combination of mdadm and the kernel version.  What kernel version are you running?
```

uname -r

```

In regards to upgrading mdadm, you can grab or compile almost any version. mdadm has almost no dependencies, so it's very easy to run an upgraded version.  Also, if you didn't want to patch, the kernel, you could just grab the latest 3.12.6 stable kernel and compile it yourself or just grab the latest [.deb package]("http://ubuntuhandbook.org/index.php/2013/11/linux-kernel-3-12-released-install-ubuntu-or-linux-mint/") (if you want to use the latest kernel with these patches integrated already, this deb package is really the easiest way to go).

---

