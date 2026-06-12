---
title: "[SOLVED] changed user password, keyring uses old password?"
date: 2008-12-05
forum: Security
---

### Post by mireson on 2008-12-05
Hi,
I'm running intrepid on an old compaq evo n610c.
I recently changed my user password for security reasons. I did this via System -> Administration -> About Me
I now log on with this password, and use it for sudo or gksudo operations.
Mine is the only user account on the machine.

However, since changing the password, at the start of each session I am asked to enter a password to unlock the default keyring, so I can access the wireless network. AND it requires my OLD password.

I've scoured the forums for hints, but most of them seem to be about removing the prompts, not old passwords.

I'd really appreciate any help at all. Even a better way of changing passwords if that will help down the track.

---

### Post by lovinglinux on 2008-12-06
That happened to me also, but I just realized it after a lot of hair pulling :)

Open System >> Preferences >> Passwords & Keys or something similar (I changed the menu title for this in my machine), select the keyring in question and click "Change Unlock Password"

---

### Post by mireson on 2008-12-08
I took your hints, and this is my solution:

**Changing the Default Keyring Password in Ubuntu Intrepid Ibex (8.10)**

Applications -> Accessories -> Passwords and Encryption Keys

Edit -> Preferences

Under "Passwords Keyrings" select 'login'

Click on "Change Unlock Password"

Follow the prompts to set your new password

And that solved my issue!

---

### Post by welling on 2009-02-05
This solution doesn't seem to work under Jaunty- the 'preferences' dialog doesn't offer these options.  Am I missing something?  What's the Jaunty equivalent?

---

### Post by mireson on 2009-02-06
Yeah, this solution worked for Intrepid. I haven't looked at Jaunty yet. You may like to start a new thread specifying Jaunty in the title?

---

### Post by Raumkraut on 2009-04-21
Just came across the same problem with Jaunty. Finally discovered how to go about it:

**Changing the Default Keyring Password in Ubuntu Jaunty Jackalope (9.04)**

Applications -> Accessories -> Passwords and Encryption Keys

Passwords tab

Right-click "Passwords: login"

Select "Change Password"

Follow the prompts to set your new password

---

### Post by rusyear04 on 2009-04-27
thank you to raumkraut for the Jaunty Jackalope (ubuntu 9.04) hint on solving the issue!

---

