---
title: "Welcome to Grub!"
date: 2013-08-16
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-08-16
After a fresh install and upgrade of all files I get this displayed on my screen:

Grub is Loading ..
Welcome to Grub!

Anyone else?

  I know it's not much but maybe there is still more fireworks to come :)LOL

---

### Post by cecilpierce on 2013-08-16
Why can't Grub be more like Burg? I don't like Grub... :(

---

### Post by grahammechanical on 2013-08-17
I noticed both the update to Grub and the welcome messages. The message would be completely different with the addition of "you are"at the front of the message.

Still, on a more serious note, I am curious as to any more important changes/improvements than code to put a Grub loading notice. I suppose it is useful for those users who only have one OS and a Linux one at that. Some think that they do not have Grub because they do not see a menu a menu.

Regards.

---

### Post by ventrical on 2013-08-17
I am assuming then that GRuB  is trying to identify itself as a separate entity from Ubuntu as a whole. I'd like to see some action on GRuB with btrfs but that's a whole different topic.

  On a more positive note GRuB is a rather unique menuing tool for startups. I don't hear much about lilo  anymore.

regards..

---

### Post by fooman on 2013-08-18
i thought that something was different after starting my computer this morning....even restarted a few times to see just what the message was that flashed for a second just before the grub menu displayed.

actually thought i had mistakenly installed something that produced it.  glad to hear its not just me, lol

---

### Post by Sworddragon on 2013-08-19
As I could figure out from google this message exists for a few years so maybe there is a way to disable it somehow.

---

### Post by bregma2 on 2013-08-19
I just started getting this after the recent Grub update.  It annoys me because I previously had a flicker-free text-free boot sequence with a custom Grub theme, and now I have this ghastly 1990s-era text displayed at boot.

I'm going to assume this cruft is going to disappear before 13.10 final release.

---

### Post by grahammechanical on 2013-08-19
> I'm going to assume this cruft is going to disappear before 13.10 final release.

I would not assume that. I do not think it is coming from Ubuntu developers. I cannot see anything like that message in grub.cfg. This seems to be appearing before grub.cfg is read. If it is a part of Grub that is in the MBR. It will not be going any time soon, if at all.

Regards.

---

### Post by Cavsfan on 2013-08-19
I got the update the other day and was unaffected by it. 
I keep mine custom and so there is never a problem. All I see is this:
```
cavsfan@cavsfan-MS-7529:~$ grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl --starting-line-number=0
     0    menuentry "Precise Pangolin 12.04" {
     1    menuentry "Precise Pangolin 12.04 (Recovery Mode)" {
     2    menuentry "Quantal Quetzal 12.10" {
     3    menuentry "Quantal Quetzal 12.10 (Recovery Mode)" {
     4    menuentry "Raring Ringtail 13.04" {
     5    menuentry "Raring Ringtail 13.04 (Recovery Mode)" {
     6    menuentry "Saucy Salamander 13.10" {
     7    menuentry "Saucy Salamander 13.10 (Recovery Mode)" {
     8    menuentry "Linux Mint 13 Nadia" {
     9    menuentry "Linux Mint 13 Nadia (Recovery Mode)" {
    10    menuentry "Linux Mint 15 Olivia" {
    11    menuentry "Linux Mint 15 Olivia (Recovery Mode)" {
    12    menuentry "Windows 7" {

```

Or this: [ATTACH=CONFIG]245479[/ATTACH]

I did receive notification that **/etc/grub.d/05_debian_theme** and **/etc/default/grub** had changed and I took the newer versions of the files. I just made sure I edited them both before I rebooted.
The one thing that changed as far as this method of customization is that the font colors had to be moved to after line 117. As mentioned in this [[COLOR=blue]_post_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2076205&page=19&p=12758694#post12758694").

The action of installing the updates installed grub on my Saucy install which is why I fixed it. I generally keep grub installed on another install besides the development version but have never had an issue when it was on that install.
Without customizing grub like when I initially install from an ISO the other installs are messed up even though I only have one swap file.

I generally just boot into Lucid, my main install which is usually in 640x480 instead of the normal 1900x1200 so I install grub there (**sudo grub-install /dev/sda**) and then reboot and put grub on which ever install I want it on.
Although it is fine to leave it on Saucy to avoid having to move grub around.

---

### Post by ventrical on 2013-08-19
> **grahammechanical said:**
> I would not assume that. I do not think it is coming from Ubuntu developers. I cannot see anything like that message in grub.cfg. This seems to be appearing before grub.cfg is read. If it is a part of Grub that is in the MBR. It will not be going any time soon, if at all.

Regards.

  I am reminded now that the "Welcome to GRuB" message is a percursor to a fail and entering in of <grub rescue prompt. So I have no  idea what is going on with   the exception that the boot is not failing.

regards..

---

### Post by grahammechanical on 2013-08-21
I am also noticing a Loading 'Ubuntu' message while the Grub background image is still on screen. It appears before the sparse file error message (which we get when using btrfs). I take this Loading Ubuntu message as an indication that Grub has located its grub.cfg file and has read it. I think that the loading Grub message would stay on screen longer if Grub could not locate grub.cfg. I wonder what message we would get if Grub could not find the partition the kernel was on or the kernel. I am not about to deliberately break a working install to find out. Perhaps this is all to do with Grub being more informative when things go wrong other than a Grub Rescue message.

Regards.

---

### Post by tad1073 on 2013-08-21
> **ventrical said:**
> After a fresh install and upgrade of all files I get this displayed on my screen:

Grub is Loading ..
Welcome to Grub!

Anyone else?

  I know it's not much but maybe there is still more fireworks to come :)LOL

That's normal behavior, back when 7.04, 8.04 were released it did the same thing so it's nothing to worry about.

---

### Post by tad1073 on 2013-08-21
> **grahammechanical said:**
> I am also noticing a Loading 'Ubuntu' message while the Grub background image is still on screen. It appears before the sparse file error message (which we get when using btrfs). I take this Loading Ubuntu message as an indication that Grub has located its grub.cfg file and has read it. I think that the loading Grub message would stay on screen longer if Grub could not locate grub.cfg. I wonder what message we would get if Grub could not find the partition the kernel was on or the kernel. I am not about to deliberately break a working install to find out. Perhaps this is all to do with Grub being more informative when things go wrong other than a Grub Rescue message.

Regards.

It will drop you to the grub terminal.

---

### Post by ventrical on 2013-08-22
> **grahammechanical said:**
> I am also noticing a Loading 'Ubuntu' message while the Grub background image is still on screen. It appears before the sparse file error message (which we get when using btrfs). I take this Loading Ubuntu message as an indication that Grub has located its grub.cfg file and has read it. I think that the loading Grub message would stay on screen longer if Grub could not locate grub.cfg. I wonder what message we would get if Grub could not find the partition the kernel was on or the kernel. I am not about to deliberately break a working install to find out. Perhaps this is all to do with Grub being more informative when things go wrong other than a Grub Rescue message.

Regards.

I had two installs where I had to use the grub rescue disk so far. I am not sure if it is due to the new Grub updates and those were on installs of ext4 + btrfs partitions, of course, btrfs getting bumped.

---

