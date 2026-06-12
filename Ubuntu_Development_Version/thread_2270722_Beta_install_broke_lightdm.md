---
title: "Beta install broke lightdm"
date: 2015-03-25
forum: Ubuntu Development Version
---

### Post by mnd999 on 2015-03-25
Hi all,

Question, I did the kubuntu beta upgrade last night and it seems to have broken something (probably) lightdm, which means the laptop doesn't work at all locally.

Startup gets as far as:

Started LSB: start Winbind daemon

and then just stops, (you can't Alt-F2, Alt-F3 to switch VTs). 

The only error is 

[FAILED] Failed to start light display maneger


â lightdm.service - Light Display Manager
   Loaded: loaded (/lib/systemd/system/lightdm.service; enabled; vendor preset: enabled)
   Active: failed (Result: start-limit) since Wed 2015-03-25 07:59:49 GMT; 6min ago
     Docs: man:lightdm(1)
  Process: 1594 ExecStart=/usr/sbin/lightdm (code=exited, status=1/FAILURE)
  Process: 1590 ExecStartPre=/bin/sh -c [ "$(basename $(cat /etc/X11/default-display-manager 2>/dev/null))" = "lightdm" ] (code=exited, status=0/SUCCESS)
 Main PID: 1594 (code=exited, status=1/FAILURE)

Mar 25 07:59:49 mark-ThinkPad-X1-Carbon systemd[1]: Failed to start Light Display Manager.
Mar 25 07:59:49 mark-ThinkPad-X1-Carbon systemd[1]: Unit lightdm.service entered failed state.
Mar 25 07:59:49 mark-ThinkPad-X1-Carbon systemd[1]: lightdm.service failed.
Mar 25 07:59:49 mark-ThinkPad-X1-Carbon systemd[1]: lightdm.service holdoff time over, scheduling restart.
Mar 25 07:59:49 mark-ThinkPad-X1-Carbon systemd[1]: start request repeated too quickly for lightdm.service
Mar 25 07:59:49 mark-ThinkPad-X1-Carbon systemd[1]: Failed to start Light Display Manager.
Mar 25 07:59:49 mark-ThinkPad-X1-Carbon systemd[1]: Unit lightdm.service entered failed state.
Mar 25 07:59:49 mark-ThinkPad-X1-Carbon systemd[1]: lightdm.service failed.

journalctl -xe shows the same thing.

/var/log/lightdm/lightdm.log is just debug, no errors

Any ideas where it might be hiding more useful information?

Mark

---

### Post by Elfy on 2015-03-25
*Thread moved to **Ubuntu Development Version**.*

Have you updated and upgraded it yet? 

The last released Beta is rather old.

---

### Post by Elfy on 2015-03-25
possibly you need sddm rather than lightdm now

in which case perhaps a bug

[http://irclogs.ubuntu.com/2015/03/25/%23ubuntu+1.html#t14:48](http://irclogs.ubuntu.com/2015/03/25/%23ubuntu+1.html#t14:48)

---

### Post by marco-parillo on 2015-03-25
I believe a fresh install from the latest ISO no longer has that problem.
You can always test the release candidate for Beta 2: [http://iso.qa.ubuntu.com/qatracker/milestones/336/builds](http://iso.qa.ubuntu.com/qatracker/milestones/336/builds)

---

### Post by mnd999 on 2015-03-26
Yes, that was this issue. It was still trying to use lightdm. Uninstalling lightdm and enabling sddm fixed it.

For the benefit of others:

sudo apt-get remove lightdm
sudo systemctl enable sddm

---

### Post by dino99 on 2015-03-26
> **mnd999 said:**
> Yes, that was this issue. It was still trying to use lightdm. Uninstalling lightdm and enabling sddm fixed it.

For the benefit of others:

sudo apt-get remove lightdm
sudo systemctl enable sddm

removing is not enough, to also remove the settings you need to purge :

sudo apt-get remove --purge lightdm

---

### Post by zika on 2015-03-26
To use SystemD and not to remove parts of the system:```
sudo systemctl disable lightdm.service
```with, if You want to be thorough```
sudo systemctl mask lightdm.service
```

---

### Post by mnd999 on 2015-03-26
Possibly it wouldn't be enough in all cases, but it worked for me.

---

### Post by leon-n-maurer on 2015-04-28
I installed the 4.3 beta late last week, ran into the same problem as mnd999, and I purged lightdm as dino99 instructed (and I've since upgraded to 4.3 now that it's out). Now, I can reach the graphical login screen, but it refuses to log in. I enter my password, it sits there for a bit, briefly dumps me back to the console, and then goes back to the login screen. I managed to snap a picture of the console (not easy because the console is only visible for a split second). I can post the photo, but I think the relevant part is the last two lines of text:

```
Starting Terminate Plymouth Boot Screen...
Starting Wait for Plymouth Boot Screen to Quit...
```

Any advice?

(Maybe I shouldn't post this on the thread, but my problem seems to be related to the earlier stuff in this thread.)

---

### Post by cariboo on 2015-04-28
Vivid was released last Thursday, please create a thread in [General Help]("http://ubuntuforums.org/forumdisplay.php?f=331"), as this thread is closed

---

