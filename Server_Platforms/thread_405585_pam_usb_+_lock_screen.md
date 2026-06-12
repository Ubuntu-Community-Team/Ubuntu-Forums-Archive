---
title: "pam_usb + lock screen"
date: 2007-04-09
forum: Server Platforms
---

### Post by SgtPepperKSU on 2007-04-09
I have pam_usb set up to auto authenticate my credentials for login, sudo, etc whenever I have my usb key inserted, but I can't seem to get it to work with gnome-screensaver-command --lock.  This is the same as going to panel->power button->lock screen and, more importantly in my case, this happens when you go to panel->power button->switch user (when you log back in to that user your screen is locked for obvious security reasons).

Does anybody know how to get pam_usb to work with the gnome screensaver lock feature?

---

### Post by SgtPepperKSU on 2007-04-10
After looking into people using other pam modules with gnome-screensaver, I've added a /etc/pam.d/gnome-screensaver file that consists of just "@include common-auth" (where my pam_usb.so line is).  But, it still isn't working; I still just get a password prompt when unlocking the screen.

Does anybody have any ideas on how to either
a) Get pam_usb to work with gnome-screensaver, or
b) Get the main log in screen to unlock the session when you log in (rather than making you log in twice every time).

Either way would be great.

---

### Post by SgtPepperKSU on 2007-04-10
Looks like I'm not alone on this (as far as my "b)" above goes):
[Consistent and Easy to Use Login Screen and Unlock Screensaver](https://blueprints.launchpad.net/ubuntu/+spec/consistent-login-screen)

It says it was accepted for feisty, but I'll just have to hope it makes it into Feisty+1.

Still, does anybody know how to get PAM to work with gnome-screensaver?

---

### Post by xfile087 on 2007-04-18
I don't suppose anyone can tell me how or tell me where to look to install pam_usb in feisty? I tried to follow the instructions but i'm useless...

---

### Post by aamukahvi on 2007-04-18
> **xfile087 said:**
> I don't suppose anyone can tell me how or tell me where to look to install pam_usb in feisty? I tried to follow the instructions but i'm useless...
I made a checkinstall .deb. Attached, use at your own peril. It should draw in all the deps but I'm not sure. After install refer to /usr/share/doc/pamusb.

Again it works for me (Feisty) but could bork your system.

---

### Post by xfile087 on 2007-04-18
> **aamukahvi said:**
> I made a checkinstall .deb. Attached, use at your own peril. It should draw in all the deps but I'm not sure. After install refer to /usr/share/doc/pamusb.

Again it works for me (Feisty) but could bork your system.


Thanks for the quick reply! I just tried to install but I get the following:

"dpkg-deb: `pam-usb_0.4.0-1_i386.deb' is not a debian format archive"

---

### Post by aamukahvi on 2007-04-18
> **xfile087 said:**
> Thanks for the quick reply! I just tried to install but I get the following:

"dpkg-deb: `pam-usb_0.4.0-1_i386.deb' is not a debian format archive"
Ok... Let me check.... Should be better now? (50kB vs 10kB) Reinstall via gdebi works for me.

---

### Post by aamukahvi on 2007-04-18
> **SgtPepperKSU said:**
> After looking into people using other pam modules with gnome-screensaver, I've added a /etc/pam.d/gnome-screensaver file that consists of just "@include common-auth" (where my pam_usb.so line is).  But, it still isn't working; I still just get a password prompt when unlocking the screen.

Does anybody have any ideas on how to either
a) Get pam_usb to work with gnome-screensaver, or
b) Get the main log in screen to unlock the session when you log in (rather than making you log in twice every time).

Either way would be great.
Got it working... sorta! :mrgreen:
Make sure you have double dashes in your pamusb.conf as follows:
--lock
--deactivate
```
	<users>
			<user id="toni">
				<device>CruzerMini</device>
				<option name="quiet">true</option>
				<agent event="lock">gnome-screensaver-command --lock</agent>
				<agent event="unlock">gnome-screensaver-command --deactivate</agent>
			</user>

```

Have pamusb-agent running when you remove/insert your USB key and it should work. However I haven't yet determined a way to keep it running. I added it to my session but no dice.

---

### Post by xfile087 on 2007-04-18
> **aamukahvi said:**
> Ok... Let me check.... Should be better now? (50kB vs 10kB) Reinstall via gdebi works for me.

Well it installed  and everything seems to be working perfectly! The deb was much appreaciated!

---

### Post by aamukahvi on 2007-04-18
> **xfile087 said:**
> Well it installed  and everything seems to be working perfectly! The deb was much appreaciated!
Great! :)

---

### Post by xfile087 on 2007-04-18
Sorry for keep bothering but you seem to know what you're doing. I just wondered if you knew how to make it so I still have to type in my password for sudo? I'm not to keen on it not asking me for it.

---

### Post by SgtPepperKSU on 2007-04-19
Have you made sure none of the files included by /etc/pam.d/sudo don't refer to pam_usb?

---

### Post by xfile087 on 2007-04-19
> **SgtPepperKSU said:**
> Have you made sure none of the files included by /etc/pam.d/sudo don't refer to pam_usb?

Thanks, I think it's sorted now :)

---

### Post by aamukahvi on 2007-04-19
> **xfile087 said:**
> Thanks, I think it's sorted now :)
Hi can you tell me what you guys did to make sudo not use pam_usb? I'm a little wary about removing common-auth from there.

pam.d/sudo:
```
#%PAM-1.0

@include common-auth
@include common-account
```

---

### Post by xfile087 on 2007-04-19
> **aamukahvi said:**
> Hi can you tell me what you guys did to make sudo not use pam_usb? I'm a little wary about removing common-auth from there.

pam.d/sudo:
```
#%PAM-1.0

@include common-auth
@include common-account
```

I didn't remove anything from it because I wasn't sure what to remove so I simply added the following to my pamusb.conf and all seems to be working perfectly.

>   <service id="sudo">
    <option name="enable">false</option>
  </service>

---

### Post by aamukahvi on 2007-04-19
> **xfile087 said:**
> I didn't remove anything from it because I wasn't sure what to remove so I simply added the following to my pamusb.conf and all seems to be working perfectly.
Thanks for the advice. I had done that but no go. This is so weird. Now it works consistently with the screensaver but not with gdm. I will reinstall soon so it doesn't matter :) Maybe I'll get it working then.

---

### Post by xfile087 on 2007-04-19
> **aamukahvi said:**
> Thanks for the advice. This is so weird. Now it works consistently with the screensaver but not with gdm. I will reinstall soon so it doesn't matter :) Maybe I'll get it working then.

Good luck - don't forget to let us know if it works after the reinstall!

I've just noticed something actually. After I rebooted it didn't ask me for a password for sudo again. THEN I ran pamusb-agent and tried sudo again and only then does it ask for the password to use sudo... If only we could get pamusb-agent to work on boot...

---

