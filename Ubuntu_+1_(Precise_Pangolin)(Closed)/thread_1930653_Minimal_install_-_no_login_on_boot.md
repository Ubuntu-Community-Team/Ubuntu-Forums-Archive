---
title: "Minimal install - no login on boot"
date: 2012-02-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by A_T on 2012-02-24
Hi. Having done a minimal Precise install upon reboot I was presented with nothing but a flashing cursor rather than the prompt/command line I was expecting to enable me to login. Is there a way to login from this position? I was hoping to install my software at this point with apt-get (I simply cannot get on with aptitude TUI that was offered before the reboot).

---

### Post by paul_in_london on 2012-02-24
> **A_T said:**
> Hi. Having done a minimal Precise install upon reboot I was presented with nothing but a flashing cursor rather than the prompt/command line I was expecting to enable me to login. Is there a way to login from this position? I was hoping to install my software at this point with apt-get (I simply cannot get on with aptitude TUI that was offered before the reboot).

Reboot into recovery mode.

Choose **[COLOR="Red"]network[/COLOR]** from the menu.

Upon return to the menu, choose **[COLOR="Red"]root[/COLOR]**.

Run these commands from the root prompt:

```
aptitude update
aptitude full-upgrade
aptitude install --without-recommends xorg
```

or use apt-get instead of aptitude if you prefer.

At this stage, you could just reboot and see if you're able to log in, but if you want a graphical login etc. do the following as well before you reboot:

```
aptitude install --without-recommends lightdm lightdm-gtk-greeter
```

Do you know if you want to use gnome or lxde for example?

To get a minimal gnome set-up:

```
aptitude install --without-recommends gnome-session gnome-panel gnome-terminal gnome-themes \
gnome-themes-selected gnome-themes-ubuntu ubuntu-artwork light-themes
```

To get a minimal lxde (lubuntu) set-up:

```
aptitude install --without-recommends python-software-properties lubuntu-core
```

After that you should be ok and it's just a matter of deciding would else you want/need to install.

---

### Post by A_T on 2012-02-24
Thanks. After some messing around I was also able to get a command prompt at the flashing cursor by pressing Ctl-Alt-F6.

I tried lightdm but this didn't give me a login screen. In the end I used lxdm which worked.

Do we know if the "alternate" cds allow an install without a desktop environment?

---

### Post by cariboo on 2012-02-24
> **A_T said:**
> Thanks. After some messing around I was also able to get a command prompt at the flashing cursor by pressing Ctl-Alt-F6.

I tried lightdm but this didn't give me a login screen. In the end I used lxdm which worked.

Do we know if the "alternate" cds allow an install without a desktop environment?

Yes just type **cli** at the Main menu screen, and the alternate install iso will install a command line only system.

---

### Post by Irihapeti on 2012-02-24
There are problems with LightDM and a minimal install. There's a bug filed at [https://bugs.launchpad.net/lightdm/+bug/935591](https://bugs.launchpad.net/lightdm/+bug/935591). If you haven't done so already, you could indicate that it affects you too.

---

### Post by paul_in_london on 2012-02-28
> **A_T said:**
> Thanks. After some messing around I was also able to get a command prompt at the flashing cursor by pressing Ctl-Alt-F6.

I tried lightdm but this didn't give me a login screen. In the end I used lxdm which worked.

Do we know if the "alternate" cds allow an install without a desktop environment?

Hmm. Not sure why **[COLOR="Red"]lightdm[/COLOR]** didn't give you a login screen. If you're still using your original install and want a text-only login this would be one way to disable **[COLOR="Red"]lxdm[/COLOR]** (taking your example) completely and prevent it from running:

```
sudo mv /etc/init/lxdm.conf ~/lxdm.conf
```

(To restore **[COLOR="Red"]lxdm[/COLOR]** put the file back in /etc/init).

If you have **[COLOR="Red"]lightdm[/COLOR]** and/or **[COLOR="Red"]gdm[/COLOR]** installed, run the equivalent commands for those as well.

---

### Post by mihalybaci on 2012-02-28
I'm having a similar problem (no command line, just a cursor), except I'd like to to a minimal command line install of 11.10 in Virtual Box (trying to follow [this]("https://help.ubuntu.com/community/Installation/LowMemorySystems") prescription). When I boot the VM into rescue mode, there is a 'network' option, so I followed it, but it seems like its just trying to reinstall certain packages, and when its finished there is no "root" option. I can open an ash "terminal", but the sudo and apt-get (aptitude) commands aren't recognized. Am I missing something?

---

### Post by paul_in_london on 2012-02-28
> **mihalybaci said:**
> I'm having a similar problem (no command line, just a cursor), except I'd like to to a minimal command line install of 11.10 in Virtual Box (trying to follow [this]("https://help.ubuntu.com/community/Installation/LowMemorySystems") prescription). When I boot the VM into rescue mode, there is a 'network' option, so I followed it, but it seems like its just trying to reinstall certain packages, and when its finished there is no "root" option. I can open an ash "terminal", but the sudo and apt-get (aptitude) commands aren't recognized. Am I missing something?

Are you using a MinimalCD (mini.so) image? That's what I usually use. For 11.10 go to this page:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Once you boot up the installed system (in recovery mode) you should be able to start networking (via the recovery menu option) and then choose the root option from the menu so that you can run aptitude or apt-get in a fully functional shell to apply updates. Then it's a question of whether you want to install xorg etc.

Have a look at this page too:

[https://forums.virtualbox.org/viewtopic.php?f=3&t=44979](https://forums.virtualbox.org/viewtopic.php?f=3&t=44979)

EDIT: You could also try the daily mini.iso for precise from here:

[http://archive.ubuntu.com/ubuntu/ubuntu/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/ubuntu/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/) (64 bit)

or here:

[http://archive.ubuntu.com/ubuntu/ubuntu/ubuntu/dists/precise/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/ubuntu/ubuntu/dists/precise/main/installer-i386/current/images/netboot/) (32 bit)

---

### Post by mihalybaci on 2012-02-28
It was the 11.10 mini.iso. I got it working, somehow I got the grub menu to show up (it wasn't before) and booted into recovery mode. I didn't see any network options, so I went straight to root and luckily networking was already enabled. I skipped the update/upgrade steps, and proceeded to install xorg, openbox, etc., according to the 'Low Memory Systems' link from my earlier post. All seems well, I booted up the VM logged in to my minibuntu system and saw a nice solid beige screen. 

Thanks for the help.

---

### Post by paul_in_london on 2012-02-29
> **mihalybaci said:**
> It was the 11.10 mini.iso. I got it working, somehow I got the grub menu to show up (it wasn't before) and booted into recovery mode. I didn't see any network options, so I went straight to root and luckily networking was already enabled. I skipped the update/upgrade steps, and proceeded to install xorg, openbox, etc., according to the 'Low Memory Systems' link from my earlier post. All seems well, I booted up the VM logged in to my minibuntu system and saw a nice solid beige screen. 

Thanks for the help.

Sorry if I confused you.

In 11.10 (oneiric), selecting the **[COLOR="Red"]recovery mode[/COLOR]** entry in GRUB now stops in a read-only mode with the following "stage 1" recovery menu:

Recovery Menu (limited read-only menu)
 * resume   Resume normal boot
 * fsck     Check all file systems (will exit read-only mode)
 * remount  Remount / read/write and mount all other file systems
 * root     Drop to root shell prompt

Selecting **[COLOR="Red"]remount[/COLOR]** (and pressing Enter after a successful remount) will get you to the "stage 2" recovery menu:

Recovery Menu
 * resume   Resume normal boot
 * clean    Try to make free space
 * dpkg     Repair broken packages
 * grub     Update grub bootloader
 * netroot  Drop to root shell prompt with networking
 * root     Drop to root shell prompt

You can also reach this "stage 2" recovery menu by selecting **[COLOR="Red"]fsck[/COLOR]** or **[COLOR="Red"]root[/COLOR]** at "stage 1".

In 12.04 (precise), it's similar (but not not exactly the same - for example there's no separate **[COLOR="Red"]netroot[/COLOR]** option).

I don't quite know what the rationale for all this is though.

---

