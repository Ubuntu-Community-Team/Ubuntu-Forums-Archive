---
title: "Changing Password Problems Seem to be Potential Security Hazard"
date: 2010-08-03
forum: Security
---

### Post by carrickfergus on 2010-08-03
Okay, this is going to be a bit complicated. I already posted a topic similar to this concerning the Desktop OS version, but this deals with the Netbook because unlike the Desktop, the Netbook is less cooperative. Allow me to elaborate:

Today (or rather yesterday since it's not after midnight where I am), I changed my password because I was hopelessly confounded about how to get my Wireless Network card up and running after it had been installed and I was allowing my dad to use it. This issue has since been resolved, however...

When I chose my password during the original installation, there was no mention of it being "too simple." This is where the Desktop OS and the Netbook OS differ. The desktop will let me change it in the terminal without any errors. The Netbook will not. When I've attempted to revert it back to the original, it will not let me do so in the User Profile or in the Terminal. The Passwords and Encryption Keys application also does not appear to help.

So now even after I've changed it to a different "complicated" password I am still prompted to insert two different passwords since I changed my user password but I am unable to change the password I input during the installation. A bit screwy methinks... :-s

This is extremely important. I'd like to know how to change the original installation password.

If I can't change the main password on my laptop then this is a serious potential security breach just waiting to happen (*especially* since it's on a laptop and I will be hauling it around with me) and I will most likely install a different OS if this isn't resolved --- It would be very unfortunate since I spent the whole day fixing it and I really enjoy the interface. Luckily I can live with this on my Desktop since I'm not going to be hauling it around with me everywhere when the school year starts.

So please understand when I say that any input in this would be very valuable to me. Thanks for your time and good night/morning/afternoon/evening! :D

---

### Post by jarviser on 2010-08-03
This has been answered in your other posting.

In essence don't use sudo commands to change passwords. use either system/preferences/about me or system/administration/users and groups, then reboot to reset keyring etc.

If you have really messed it up try a re-install but this is NOT a security breach - you can change your password safely at any time, but steer clear of sudo commands unless you know what you are doing.

---

### Post by stlsaint on 2010-08-03
> This is extremely important. I'd like to know how to change the original installation password.

Are you referring to your root password or your user profile password?

---

### Post by FuturePilot on 2010-08-03
> **jarviser said:**
> or system/administration/users and groups,

That would be the same as using sudo passwd and it will break things since doing it that way is still forcibly changing the password.

---

### Post by jarviser on 2010-08-03
> **FuturePilot said:**
> 
 Originally Posted by jarviser  View Post
or system/administration/users and groups,

That would be the same as using sudo passwd and it will break things since doing it that way is still forcibly changing the password.

Please explain.

---

### Post by snowpine on 2010-08-03
> **carrickfergus said:**
> This is extremely important. I'd like to know how to change the original installation password.


You should be able to bypass "password too simple" with:

```
sudo passwd carrickfergus
```

---

### Post by carrickfergus on 2010-08-03
> **snowpine said:**
> You should be able to bypass "password too simple" with:

```
sudo passwd carrickfergus
```
This does not appear to bypass with the netbook version but it does on my desktop.

---

### Post by carrickfergus on 2010-08-03
> **FuturePilot said:**
> That would be the same as using sudo passwd and it will break things since doing it that way is still forcibly changing the password.
Your other post seems to have solved it.

For future users searching for the solution to this problem, I did the following:

1. Accessed the Home Folder
2. Home>"Your Username"
3. "ctrl" + "h"
4. Home>.gnome2
5. Delete the folder "keyrings"
6. Log out
7. Log back on

Thanks, FP. However, in order to bypass the "password too simple" error on my desktop, I had to use that. Oddly, that command has not appeared to bypass the error on my netbook.

---

### Post by FuturePilot on 2010-08-03
> **jarviser said:**
> Please explain.

When you change a password though the Users and Groups tool you are doing so with administrative privileges meaning you are forcing a password change which does not update the keyring's password. It is the exact same thing as doing sudo passwd. Using the Users and Groups tool is not the recommended way to change your own password. Not only does it break the keyring but if you use ecryptfs for an encrypted home it breaks that as well.

---

### Post by jarviser on 2010-08-03
> **FuturePilot said:**
> When you change a password though the Users and Groups tool you are doing so with administrative privileges meaning you are forcing a password change which does not update the keyring's password. It is the exact same thing as doing sudo passwd. Using the Users and Groups tool is not the recommended way to change your own password. Not only does it break the keyring but if you use ecryptfs for an encrypted home it breaks that as well.


Yes, I agree that it uses root privileges, but how else would you change the administration password except with admin privilege?  I am the only user as installed and with admin privileges. There are no "Desktop users" set up as they will not run some apps.  I have no wish to change my login password and leave the root password as-was when I installed. That would indeed be a security risk as the OP suggested.

And more importantly why would the developers include a routine in the menu system that will "break" the system? If there is a menu route then I would always suggest it before any sudo commands for that very reason - tested by the developers as a user tool.

I have done it that way many times before and never had any problem with keyring.

 Anyway, warnings duly noted - thanks.

---

### Post by OpSecShellshock on 2010-08-03
> **jarviser said:**
> Yes, I agree that it uses root privileges, but how else would you change the administration password except with admin privilege?  I am the only user as installed and with admin privileges. There are no "Desktop users" set up as they will not run some apps.  I have no wish to change my login password and leave the root password as-was when I installed. That would indeed be a security risk as the OP suggested.

And more importantly why would the developers include a routine in the menu system that will "break" the system? If there is a menu route then I would always suggest it before any sudo commands for that very reason - tested by the developers as a user tool.

I have done it that way many times before and never had any problem with keyring.

 Anyway, warnings duly noted - thanks.

The default user is only an administrator in the context of administrative actions (which is the purpose for using sudo). At all other times it's just a regular user account. When you go into Users and Groups, you need to elevate privileges in order to make changes because those are administrative actions. However, making changes to the keyring is a regular user action since all users have their own. In that sense, it's important to make sure that password changes are done with regular user privileges, as can be done in About Me under Preferences.

---

### Post by jarviser on 2010-08-04
> **OpSecShellshock said:**
> The default user is only an administrator in the context of administrative actions (which is the purpose for using sudo). At all other times it's just a regular user account. When you go into Users and Groups, you need to elevate privileges in order to make changes because those are administrative actions. However, making changes to the keyring is a regular user action since all users have their own. In that sense, it's important to make sure that password changes are done with regular user privileges, as can be done in About Me under Preferences.

Agreed 100% for user password of a "desktop" user or even another "admin" level user. But I think the OP wants to change the Admin/root password. So how to do that safely other than by a method using Admin privilege?  Would you recommend never changing root password?  

EDIT: only asking, not criticising.

---

### Post by OpSecShellshock on 2010-08-04
> **jarviser said:**
> Agreed 100% for user password of a "desktop" user or even another "admin" level user. But I think the OP wants to change the Admin/root password. So how to do that safely other than by a method using Admin privilege?  Would you recommend never changing root password?  

EDIT: only asking, not criticising.

By default, Ubuntu doesn't have a root password set, and the account isn't enabled. System owners are able to change that if they'd like, of course. However, there's no reason for root to have a keyring since it's not meant to be used for applications or for interactive graphical desktop sessions. In that sense, once the account has been enabled there's no reason why the session vs. keyring conflict should ever come up.

For most daily computer usage, I see no need to log in as root directly, so there would be no reason for setting a password for that account in the first place.

---

### Post by jarviser on 2010-08-05
> **OpSecShellshock said:**
> ...

For most daily computer usage, I see no need to log in as root directly, so there would be no reason for setting a password for that account in the first place.

My bad - I should not have used the term "Root" - I have used several distros on and off and, as you know, some do and some don't have Root!

I meant to say the Admin password - i.e. the one asked by sudo and Synaptic for that user. So if Preferences/"About Me" will do the same job of changing that Admin password then I will try it next time. 

I am disappointed that ANY option in the System/Administration menu system might have damaging content - that would surely be a bug. Obviously the menu command contains  Sudo commands embedded in it - surely the whole distro is merely a GUI front end for Linux terminal commands. 
Messing up a manual terminal sudo command - well that's my fault. but using any distro menu command should be "safe". That was the point of my original intervention on the thread.

---

