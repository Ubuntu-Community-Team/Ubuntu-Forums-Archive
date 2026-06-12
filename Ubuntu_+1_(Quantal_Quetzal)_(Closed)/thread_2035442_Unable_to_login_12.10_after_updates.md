---
title: "Unable to login 12.10 after updates"
date: 2012-07-30
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Rallg on 2012-07-30
After recent updates, I am unable to login to 12.10. I cannot login either as my user name, or as guest.

Ubuntu boots, and I get the login screen as usual. I use my password, but soon I am returned to login as if my password is incorrect. I am sure that my password is correct. So, as an alternative I try a guest session. I cannot get into guest session but instead I am returned to the login screen.

I am sure it is not a video driver problem. Everthing appears OK. There are no broken packages. I am not using Ubuntu One.

I can boot to diagnostic session. Fail-safe does not help. I can boot to system root prompt, enable newtowrking, and do various things as root. But I still cannot login to unity or to anything else.

Any suggestions?

If there is a way (using root prompt in recovery session) to re-define my username and password, I'll try it. This is a "development" vrsion, so I'm not worried about losing data.

My system has many enhancements beyond "off the shelf" Ubuntu, so this problem may not be seen by others. I'll deal with that if I can ever get to log in.

---

### Post by effenberg0x0 on 2012-07-30
A test:
1) Start the PC normally (no recovery mode, etc).
2) On lightdm, do not login as you or Guest just yet. Instead, switch to any VT by pressing Ctrl+Alt+(F1 to F6)
3) Login to that tty using your User/Password.
4) Stop lightdm and move/backup $HOME/.Xauthority:
```

sudo service lightdm stop
sudo mv  $HOME/.Xauthority $HOME/.Xauthority.backup

```5) Restart lightdm:
```

sudo service lightdm start

```6) You should be back at lightdm. Try to login with your standard user. If it still fails, you can use Ctrl+Alt+Fx(1 &#8804;      x &#8804; 6) to go back to the VT you were just before (already logged in there). Have a look at the logs. See if there a relevant error, warning by the end of the output (like the last 10 or so lines). Or run the following to just catch most errors, warnings, etc to a mylog.txt file in your $HOME directory.
```

sudo grep 'warning\|oops\|segfault\|error' -iHnr /var/log/dmesg /var/log/syslog /var/log/kern.log /var/log/Xorg.0.log $HOME/.xsession-errors > $HOME/mylog.txt && nano $HOME/mylog.txt

```OBS: At Step 3, when you login to a working console, make sure your system is up to date with sudo apt-get update && sudo apt-get upgrade. 

Regards,
Effenberg

---

### Post by Rallg on 2012-07-30
Thanks. I will try that, and report back. My report won't be for another day.

---

### Post by Rallg on 2012-07-30
SOLVED! Thanks.

The problem was found by doing the sudo grep command, as you suggested. This produced some 477 lines of code, which I read in plain text from another partition (rather than using nano).

Most of it I did not understand, but I noticed that there seemed to be a problem with ubuntu-2d and gnome-session files. I use 2d (rather than 3d) and also have various parts of gnome-session installed.

So I enabled networking. Then I ran:

sudo apt-get install ubuntu-2d*

and then:

sudo apt-get install gnome-session*

so that the wild cards would find various packages. I noticed that both ubuntu-2d and gnome-session had essential packages missing. Presumably, when I updated recently, the "non-Ubuntu" updates threw out some essential parts of Ubuntu.

After install, success.
:KS

---

### Post by effenberg0x0 on 2012-07-30
> **Rallg said:**
> SOLVED! Thanks.

The problem was found by doing the sudo grep command, as you suggested. This produced some 477 lines of code, which I read in plain text from another partition (rather than using nano).

Most of it I did not understand, but I noticed that there seemed to be a problem with ubuntu-2d and gnome-session files. I use 2d (rather than 3d) and also have various parts of gnome-session installed.

So I enabled networking. Then I ran:

sudo apt-get install ubuntu-2d*

and then:

sudo apt-get install gnome-session*

so that the wild cards would find various packages. I noticed that both ubuntu-2d and gnome-session had essential packages missing. Presumably, when I updated recently, the "non-Ubuntu" updates threw out some essential parts of Ubuntu.

After install, success.
:KS

Cool :) I generally use that command because it allows me to read logs a little better than simply using "cat", "tail" or something like it. Glad it helped you find the problem. I'd say maybe you were in those situations of incomplete update (in which something like sudo apt-get -f install could also have helped). 

Regards,
Effenberg

---

### Post by philinux on 2012-07-31
Sounds like the OP fell foul of a partial upgrade.

---

### Post by Rallg on 2012-07-31
It's possible that there was a partial upgrade problem, but I don't recall a partial upgrade in the session when the problem was created.

But I had made changes to some graphics packages that are not part of the regular distribution (not even in Quantal). Perhaps I got a message such as:

"To install new-graphics-package-0.4.5 you must also install some-other-package-0.3.2 and remove your-operating-system-12.10"

but didn't read the whole message. :rolleyes:

At any rate, all good now.

---

### Post by t0@d on 2012-09-22
I had the problem after the upgrade from Percise to Quantal Beta1.    It did not happen during the upgrade from Percise to any of the Quantal Alpha versions.  

For me the GUEST account login was successful, but useless because I was unable to elevate privileges using sudo ("unable to change to sudoers gid: Operation not permitted") - so I could not troubleshoot the problem.

My work around was to create a second administrator account called 'toad2' right after the upgrade but before the required reboot.  I was then able to log in using the new toad2 user account but not the original toad account created using Precise. 

Oddly - when I am attempting to login - I can click on the various user accounts displayed in the Unity Greeter (lightdm) and I see the appropriate wallpapers displayed as I switch back and forth between users.  

That seems like a good sign, but I still get bounced back to the Unity Greater after using the original Precise created user account.

---

### Post by t0@d on 2012-09-22
LAUNCHPAD contains a related bug that indicates it is related to  [**_ /tmp not being writable_**]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/999526")

I did notice a warning about something related to /TMP being 'missing' or 'not found' or something during the initial UBUNTU boot-up. I thought it was part of that typical 'checking disk status' routing we see from time to time. It just went away by itself.

---

### Post by DougieFresh4U on 2012-09-28
> **effenberg0x0 said:**
> A test:
1) Start the PC normally (no recovery mode, etc).
2) On lightdm, do not login as you or Guest just yet. Instead, switch to any VT by pressing Ctrl+Alt+(F1 to F6)
3) Login to that tty using your User/Password.
4) Stop lightdm and move/backup $HOME/.Xauthority:
```

sudo service lightdm stop
sudo mv  $HOME/.Xauthority $HOME/.Xauthority.backup

```5) Restart lightdm:
```

sudo service lightdm start

```6) You should be back at lightdm. Try to login with your standard user. If it still fails, you can use Ctrl+Alt+Fx(1 &#8804;      x &#8804; 6) to go back to the VT you were just before (already logged in there). Have a look at the logs. See if there a relevant error, warning by the end of the output (like the last 10 or so lines). Or run the following to just catch most errors, warnings, etc to a mylog.txt file in your $HOME directory.
```

sudo grep 'warning\|oops\|segfault\|error' -iHnr /var/log/dmesg /var/log/syslog /var/log/kern.log /var/log/Xorg.0.log $HOME/.xsession-errors > $HOME/mylog.txt && nano $HOME/mylog.txt

```OBS: At Step 3, when you login to a working console, make sure your system is up to date with sudo apt-get update && sudo apt-get upgrade. 

Regards,
Effenberg

Thanks, helped me to login again. If I could only get grub to find my Win7 install now.:evil:

---

### Post by fluteflute on 2012-09-28
> **DougieFresh4U said:**
> Thanks, helped me to login again. If I could only get grub to find my Win7 install now.:evil:Do you get a GRUB prompt? At that, type 'c' for command line, and then enter "exit". For me that takes me to Windows 7.

---

