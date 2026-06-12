---
title: "Password keyring doesn't get unlocked upon login"
date: 2012-01-30
forum: Security
---

### Post by Compgeke on 2012-01-30
I was running Xubuntu\Ubuntu 11.04 (have Xfce AND Gnome installed, although I just installed Gnome to fix a problem with my USB headset), although ever since I upgraded to 11.10 I've been getting a message every time I open Chromium that my keyring wasn't unlocked upon login, something I never had before I ran the upgrade.

From what I have found, this is commonly associated with using an auto-login, however I have a password login, as I use this for school (Windows sucks, I wish it would just die already, kinda like IE6).

Thanks!

---

### Post by OpSecShellshock on 2012-01-30
Last time this happened for me was when I upgraded by way of doing a fresh install but just copied over my previous home folder. The reason it happened was because I used a different password on installation, but the keyring information in my home folder was still matched up to my previous password. I don't remember how I fixed that, but I remember it was pretty easy. If that seems similar to your situation perhaps someone who's had more coffee than I have can chime in.

---

### Post by LewisTM on 2012-01-30
Got to Menu/Settings/Passwords and Keys,
Right-click the default item and choose 'Change Password'.
Change it to match your login password.
If that fails, you can try to delete the default keyring. It will be recreated next time an application requests it and you can enter your login password at that time.

Cheers!

---

### Post by Compgeke on 2012-01-30
That seemed to have worked, I changed the password to the password, rebooted and went to my email without it asking for my keychain password.

Lets home that was the fix :D.

---

### Post by hungrybelly on 2012-03-10
The above solution sounds sensible, but I don't have "Passwords and Keys" under menu settings - not sure how to proceed.

Xubuntu 11.10 suddenly started asking for my keyring password after an update (not the update to 11.10, though). I also registered to leave comments on programs in the Software Center around the same time, so I'm not sure which (if either) caused it. It happens when Update manager runs, and at other seemingly random times - and after using Windows for years, out-of-the-blue password requests raise my malware hackles.

---

### Post by LewisTM on 2012-03-12
You need to install package seahorse which is not included by default in Xubuntu.

If you have configured your system for automatic login, the keyring will not be unlocked automatically. It's a security feature in case someone steals your computer or breaks in.

So a program like Update Manager will ask for the unlock password. Most browsers also encrypt sensitive infos using the keyring. If you enter a website that asks for a password, and you have asked Firefox (or Chrome, etc) to save it for you, the browser will prompt you to unlock the keyring.

The annoying part is that the dialog contains no info about which program is requesting and for what reason. Hopefully this will be fixed in the future.

If you don't care about this level of security, just set your keyring to have no password in seahorse. 

Cheers!

---

### Post by scottbomb on 2012-06-30
This is driving me INSANE. I installed seahorse and the $#%#-ed pop-up STILL comes up at random times. I'm playing OpenArena and it interrupts my game (and I get killed, of course). There MUST be a solution to this pest that doesn't compromise security.

---

### Post by dodo3773 on 2012-07-02
> **scottbomb said:**
> This is driving me INSANE. I installed seahorse and the $#%#-ed pop-up STILL comes up at random times. I'm playing OpenArena and it interrupts my game (and I get killed, of course). There MUST be a solution to this pest that doesn't compromise security.

Are you using gnome-keyring?

---

### Post by scottbomb on 2012-07-02
I don't know what it is. I use xfce with Xubuntu if that helps. Gnome desktop itself is not installed but there's something mysterious that makes that pop-up come up. It's usually after the machine has been on for about 15-20 min. It happens on 2 different machines. Every day.

---

### Post by dodo3773 on 2012-07-02
Well here is what I do with my .xinitrc:
```

#!/bin/sh
#
# ~/.xinitrc
#
# Executed by startx (run your window manager from here)

if [ -d /etc/X11/xinit/xinitrc.d ]; then
  for f in /etc/X11/xinit/xinitrc.d/*; do
    [ -x "$f" ] && . "$f"
  done
  unset f
fi


#export __GL_SYNC_DISPLAY_DEVICE=DFP-1
export BROWSER="chromium"
/usr/bin/gnome-keyring-daemon --start --components=gpg
/usr/bin/gnome-keyring-daemon --start --components=pkcs11
/usr/bin/gnome-keyring-daemon --start --components=secrets
/usr/bin/gnome-keyring-daemon --start --components=ssh

exec ck-launch-session dbus-launch openbox-session

```


You don't use openbox of course but maybe that should give you an idea. What I used to do is launch this script when my computer starts before my email (evolution):
```

#! /bin/bash
eval \`gnome-keyring-daemon\`
export GNOME_KEYRING_PID
export GNOME_KEYRING_SOCKET
exit

```

I also use "unsafe storage" though (a blank password in the keyring). I also use a different distro. So I am unsure if this will help you at all actually. It helped me in the past though when I was having a similar issue.

---

### Post by jcoles on 2012-10-14
I have exactly the same problem, scottbomb. A few minutes after logon, the unlock keyring password dialog pops up and steals whatever keystrokes I'm making at the time. 

I don't use auto logon. My keyring password is the same as my login password, and the keyring certainly does unlock. I can view the individual passwords inside it. My "Passwords: login" keyring is also the default one. That's another suggestion that's commonly made to people experiencing this problem.

dodo3773, does your suggestion completely fix the problem? Or, does it simply trigger the keyring password request early on in the login process so that you get it out of the way at the start of your session?

---

### Post by Compgeke on 2012-10-14
I've found that after updating I have the problem back again, but I'm not going to bother trying to solve it, as Wine is broken, Shutdown\Restart won't work and I can no longer print to any printers, but rather than taking the time to troubleshoot every individual problem I'm just going to do a clean OS install.

---

### Post by dodo3773 on 2012-10-14
> **jcoles said:**
> 

dodo3773, does your suggestion completely fix the problem? Or, does it simply trigger the keyring password request early on in the login process so that you get it out of the way at the start of your session?

Well, it does for me but your mileage may vary. I think the problem you're having though is the default password to initially unlock the keyring. Which may be a different issue. It's probably popping up because of wifi for network manager or something similar. I know this is old but it may be what you are looking for:

[http://ubuntuforums.org/showthread.php?t=1739932](http://ubuntuforums.org/showthread.php?t=1739932)

If you are getting the password to unlock default keyring at startup then you either have to enter password every time or use unsafe storage. My solution before is if it is asking you for the passwords and the keyring is not even working.

---

### Post by scottbomb on 2012-10-15
I was finally able to solve it by deleting the hidden keyring file in my home directory. I was asked for a password once after doing so and never since then.

---

