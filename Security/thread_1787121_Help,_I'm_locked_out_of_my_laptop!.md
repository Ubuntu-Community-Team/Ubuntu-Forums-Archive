---
title: "Help, I'm locked out of my laptop!"
date: 2011-06-20
forum: Security
---

### Post by ladasky on 2011-06-20
Hello, I have an older (vintage 2006) IBM ThinkPad laptop that runs Ubuntu 9.04.  I encrypted the hard disk back when I installed the OS.  Yesterday, I thought it was a good time to change the password on that system, as I hadn't done so before.  I thought that I did this correctly, but now I'm no longer sure.

In the first place, when I rebooted the machine today, it's the old password that gets me past the login, not the new.  Next, I get a dialog box with this disturbing message:

"Could not update ICEauthority file /home/john/.ICEauthority"

And after clicking past that box, I get this one:

"There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)"

After passing that dialog, I get this one:

"Nautilus could not create the following required folders: /home/john/Desktop, /home/john/.nautilus.  Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them."

I don't have to close that dialog to get a fourth message, a lengthier dialog box asking me whether I want to generate a custom encryption passphrase.  I've tried to re-enter my original passphrase, thinking that doing so might reconnect me to my files.  It doesn't help.  After clicking through these last two dialog boxes, I'm left with a blank, Ubuntu orange desktop screen, with no menu bars.

The machine has not crashed completely.  If I push and hold the power button, I can bring up the shutdown/hibernate/restart/suspend window.

All right, so what happened here?  And now that I'm on the road, can I repair it without an Ubuntu installation CD?

Many thanks for your advice!

---

### Post by kmsalex on 2011-06-20
Why 9.04 in the fist plase, just re-install something that's actually still supported, I'd go with 10.04 for the LTS at the end of its name, but you could do 11.04 if you can live with unity (and it can live with your laptop). If not maby give lubuntu a shot on that old think pad sure it will run fast with what ever it has. Maby login into the terminal at boot up and trying root to reset everything, sorry i cant be of more help with your actual problem, but is it relay worth fixing?

---

### Post by ladasky on 2011-06-20
> **kmsalex said:**
> Why 9.04 in the fist plase, just re-install something that's actually still supported, I'd go with 10.04 for the LTS at the end of its name, but you could do 11.04 if you can live with unity (and it can live with your laptop). If not maby give lubuntu a shot on that old think pad sure it will run fast with what ever it has. Maby login into the terminal at boot up and trying root to reset everything, sorry i cant be of more help with your actual problem, but is it relay worth fixing?

Well, while I'm out on the road, it's not practical for me to install ANYTHING.  I'm using another person's (Windows :frown:) laptop to post these messages.  I have some files I'd like to access on my own laptop.

Perhaps I can scare up a blank CD, burn an Ubuntu Live CD/install disk, and boot?  Since my hard drive is encrypted, I wonder whether I can even read it from a live boot...

---

### Post by Dry Lips on 2011-06-21
Perhaps an older thread of mine could help you out:
[http://ubuntuforums.org/showthread.php?t=1703551](http://ubuntuforums.org/showthread.php?t=1703551)

---

