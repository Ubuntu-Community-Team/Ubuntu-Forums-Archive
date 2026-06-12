---
title: "How Do I Change U1 Account To Which Computer is Assigned?"
date: 2010-11-05
forum: Ubuntu One (CLOSED)
---

### Post by step12dude on 2010-11-05
I am running Ubuntu 10.10.  I would like to change the Ubuntu One account to which my computer is assigned - but I can't seem to find a way to do it.  If I select "Ubuntu One" from the "Preference" menu, I can access my current settings, but I can't see how to change the Ubuntu One account.  My guess is that this isn't hard to do, but I've not  yet found a way to do it.  Help!

---

### Post by duanedesign on 2010-11-06
You will need to remove your computer from the current account. You can do that by:
**1.** open the Ubuntu One Preferences and clicking 'Remove' under the 'Devices' Tab. 
**2.** close the Ubuntu One Preferences. 
**3.** visit [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/) and check the box next to your computer and click 'Remove Selected Computer'.
**4.** open Ubuntu One Preferences and you should be prompted to add your computer. Their is a link at the bottom of the page if you already have an account.
**5. **Enter the Name and Password for the account you wish to use.

If when you open the Preferences the 'Add Computer' process does not start please try the following.
-------**Maverick**---------------
**1.** Open System->Preferences->Passwords and Encryption Keys
**2.** Under "Passwords", right-click on Ubuntu One and select Delete
**3.** Open Applications->Accessories->Terminal and run: 
```
killall ubuntu-sso-login u1sdtool -q; u1sdtool -c 
```

--------**Lucid**---------------
**1.** Close the Ubuntu One Preferences application window (if it's already open)
**2.** Open your Terminal (located in Applications >> Accessories) and type the following: 
```
u1sdtool -q; killall ubuntuone-login; u1sdtool -c
```

thank you,
duanedesign

---

