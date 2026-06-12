---
title: "Disable Bluthooth without password"
date: 2010-08-03
forum: Security
---

### Post by iceman_ch on 2010-08-03
Well here is the issues that I'm running into.  I'm running into a pretty hard wall too.  I've learned how to write scripts and how to call those scripts with pamusb.  Right now if I pull the usb stick and walk away the computer locks. When I come near the computer unlocks before I put the stick in.  This is because of blueproximity. I want to make it so that when I pull the stick blue-tooth is disabled until I put the stick back in. This way blueproximity won't unlock the computer when ever I come near.  The idea is that if I pull the stick I want the computer locked.  If I don't pull the stick then it means it's not a big deal if it locks or not. 

So to accomplish this I wrote a script that has the command 

hciconfig hci0 down

This won't work because it doesn't have the correct permissions.  So I add sudo in front.  This still doesn't work since it is waiting for a password.  So I change the ownership to root and set the run as owner bit.  Still no go it wants my password.  Next I edit the sudoers file via 

sudo visudo

Still no go.  Still wants password.  Does anyone have any ideas as to what I can do to get this script to run without asking for the password?

---

### Post by iceman_ch on 2010-08-03
Well I figured it out.  I added the line to remove the password on sudo for the specific command at the end of the file and everything worked after that.

---

### Post by Agent ME on 2010-08-03
> **iceman_ch said:**
> This won't work because it doesn't have the correct permissions.  So I add sudo in front.  This still doesn't work since it is waiting for a password.  So I change the ownership to root and set the run as owner bit.  Still no go it wants my password.
If the script is set to run as root then you don't need to use sudo in the script.

---

### Post by chopinhauer on 2010-08-03
> **iceman_ch said:**
> 
This won't work because it doesn't have the correct permissions.  So I add sudo in front.  This still doesn't work since it is waiting for a password.  So I change the ownership to root and set the run as owner bit.  Still no go it wants my password.  Next I edit the sudoers file via 

sudo visudo


The **setuid** bit on scripts is ignored on Linux, however a NOPASSWD option in the sudoers file should probably work.

If I were you, I'd rather change the program used by Blue Proximity to unlock the screen and replace it with a script that checks for your USB key (via pamusb-check) and run 'gnome-screensaver-command -d' only if the key is present.

---

### Post by iceman_ch on 2010-08-03
> **chopinhauer said:**
> The **setuid** bit on scripts is ignored on Linux, however a NOPASSWD option in the sudoers file should probably work.

If I were you, I'd rather change the program used by Blue Proximity to unlock the screen and replace it with a script that checks for your USB key (via pamusb-check) and run 'gnome-screensaver-command -d' only if the key is present.

I like that idea.  I'll have to look and see if there is away for a script to call pamusb and check the status of the usb stick.  Right now I don't think it's possible.  I don't think that pamusb works that way.  What I could do is have the pamusb script move or change a file that blueproximity looks for.  However, it seems like it would be easily broken.   

I did finally get the pamusb script to stop asking for a password when using sudo to turn off bluetooth.  I wasn't adding the nopasswd line far enough in to the sudoers file.  

My problem now is the security of the scripts.

---

### Post by iceman_ch on 2010-08-03
> **Agent ME said:**
> If the script is set to run as root then you don't need to use sudo in the script.


Apparently the linux gods have seen fit to disable this.   You can no longer set scripts to run as owner.  You have to create an executable program that calls that script.  You can still set programs to run as owner and they can then call scripts as whatever they are.  


After all the research it seems like it is an old change that people are still just finding out about.


Edit

By the way the disabling bluetooth works really well.  So well that I can't get it running again.  Whenever I run *hciconfig hci0 up* it says that it timed out.  grrrrr

---

### Post by chopinhauer on 2010-08-03
> **iceman_ch said:**
> I like that idea.  I'll have to look and see if there is away for a script to call pamusb and check the status of the usb stick.  Right now I don't think it's possible.  I don't think that pamusb works that way.  What I could do is have the pamusb script move or change a file that blueproximity looks for.  However, it seems like it would be easily broken.   


Actually **pamusb-check** performs the same controls that the PAM module does, so a:
```

if [ ! pamusb-check --quiet "$USER" ]; then
gnome-screensaver-command -d;
fi

```
does exactly what you are trying to do.

---

### Post by iceman_ch on 2010-08-03
> **chopinhauer said:**
> Actually **pamusb-check** performs the same controls that the PAM module does, so a:
```

if [ ! pamusb-check --quiet "$USER" ]; then
gnome-screensaver-command -d;
fi

```
does exactly what you are trying to do.


Thats awesome.  I completely forgot about pamusb-check.  When I read your post I thought you were just referring to pamusb in general.  I used pamusb-check to test to make sure that pamusb was working I didn't think about using it to verify that the drive was in for other programs.  I guess with linux you really have to think less about what programs were meant for and more about what you can use them for.

---

### Post by chopinhauer on 2010-08-04
> **iceman_ch said:**
> 
I guess with linux you really have to think less about what programs were meant for and more about what you can use them for.


The 'man' manual pages system is extremely powerful and complete (you find most libc functions par exemple). The page for 'pamusb-check' says explicitly:
> 
pamusb-check  can  simulate  authentication through the pam_usb engine. It is useful for both testing purposes (to check the pam_usb configuration  without  having to try with a real program), but also for **scripting**. pamusb-check's exit code is 0 if the authentication  was  successful, 1 otherwise.


No other manual system (texinfo or yelp e.g.) has as much material.

---

