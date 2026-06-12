---
title: "Todays 19.10 update causes loop on login"
date: 2019-08-27
forum: Ubuntu Development Version
---

### Post by makitso on 2019-08-27
Running 19.10 Ubuntu Budgie in VirtualBox.  After today's update and a reboot, login loops.  Any other *ubuntu distros having same problem?

---

### Post by PaulW2U on 2019-08-27
I tried to partly update Ubuntu 19.10 by avoiding updates to gnome-shell, ubuntu-session, mutter, a few extensions and one or two other packages that I knew might be risky to install without hearing from anyone else. As the kernel was updated I rebooted and was greeted by a blank log in screen apart from the mouse pointer just sat there in its usual place.

So I installed the remaining packages and apart from the usual broken extensions that require their usual six monthly updates all seems to work as it should.

---

### Post by PaulW2U on 2019-08-27
Just seen this on IRC:
> 16:20:36 <fossfreedom> Quick heads up ... getting reports that the gtk 3.34 uplift today has resulted in a login loop to budgie desktop. Will need to investigate.   If there are any bug reports please ping me. TIA


---

### Post by amano on 2019-08-27
PaulW2U, you did upgrade on baremetal?

Is it somewhat stable or the kind of crashy, crashy stable?

---

### Post by makitso on 2019-08-27
I upgraded on bare metal and can't login.

[FONT=Helvetica]Here is what journalctl -ae --full displayed on Thinkpad:

[/FONT]
[FONT=Helvetica]eoan lightdm[14344] PAM unable to dlopen(pam_kwallet.so); /lib/security/pam_kwallet.so: cannot open shared object file: no such file or directory
eoan lightdm[14344] PAM adding faulty module: pam_kwallet.so
eoan lightdm[14344] PAM unable to dlopen(pam_kwallet5.so); /lib/security/pam_kwallet5.so: cannot open shared object file: no such file or directory
eoan lightdm[14344] PAM adding faulty module: pam_kwallet5.so
eoan lightdm[14344] pam_succeed_if(lightdm:auth): requirement &#8220;user ingroup nopasswdlogin&#8221; not met by user &#8220;rob&#8221;[/FONT]

---

### Post by PaulW2U on 2019-08-27
> **amano said:**
> PaulW2U, you did upgrade on baremetal?

Is it somewhat stable or the kind of crashy, crashy stable?
Bearing in mind that this thread is about potential log in problems which don't seem to affect Ubuntu all I'll add to my post above is that the installation that I've been using for some months now on a medium spec laptop is still very usable apart from the GNOME Shell extensions that broke today.

---

### Post by Frogs Hair on 2019-08-27
Same here, this was previously caused by mutter updates in the Budgie development PPA but, this doesn't apply to my current installation. Have to drop into Budgie Discourse and see if it has been reported there.


> [COLOR=#919191]Ubuntu Budgie Team Member[/COLOR]
[43m]("https://discourse.ubuntubudgie.org/t/testing-19-10-only-for-the-most-adventurous/2061/70?u=frogshair")
[COLOR=#66CCFF]
[/COLOR]ok - found the issue.
GNOME have been cleaning up gnome-settings-daemon - they removed two components this time around. Budgie Desktop was expecting those to be there. oops.
I&#8217;ve uploaded a fix upstream - and have uploaded the package for building. In the next few hours the new budgie-desktop package should be released.



Edit: Logged into tty with crtl + alt+ F1 and ran the following commands. ```
sudo apt update
``` ```
sudo apt upgrade
``````
 sudo reboot
```  Was able to login normally.:)

---

