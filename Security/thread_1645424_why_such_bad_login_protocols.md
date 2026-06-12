---
title: "why such bad login protocols?"
date: 2010-12-14
forum: Security
---

### Post by Paradoxfox93 on 2010-12-14
I'm seeing really bad user login format under a standard installation and am wondering why ubuntu does this as default.

Specifically, I have noticed that the graphical login for gnome sizes itself to accommodate a user's exact password length.  This indicates to me that somewhere on the unencrypted part of a standard installation with user encryption contains at least some indication of the content of the password length which seems a security flaw even if not a complete hole, it majorly reduces the number of attempts a cracker would have to cycle through.

And that's assuming that *only* the length is contained.

Furthermore it seems that it would be MUCH better to simply display the number of characters entered into the pw field and allowing the gui to expand itself from an fixed size as the field is filled out so the the user still receives visual feedback for entering characters.

Either a simple character count display should be entered into the field or a 10 dot to new line so that one can visually quickly count the number enter by multiplying from a 10base graphical observation.

Thoughts?  Yeah, I know it's paranoid but isn't that the point of encryption?

---

### Post by tgm4883 on 2010-12-14
> **Paradoxfox93 said:**
> I'm seeing really bad user login format under a standard installation and am wondering why ubuntu does this as default.

Specifically, I have noticed that the graphical login for gnome sizes itself to accommodate a user's exact password length.  This indicates to me that somewhere on the unencrypted part of a standard installation with user encryption contains at least some indication of the content of the password length which seems a security flaw even if not a complete hole, it majorly reduces the number of attempts a cracker would have to cycle through.

And that's assuming that *only* the length is contained.

Furthermore it seems that it would be MUCH better to simply display the number of characters entered into the pw field and allowing the gui to expand itself from an fixed size as the field is filled out so the the user still receives visual feedback for entering characters.

Either a simple character count display should be entered into the field or a 10 dot to new line so that one can visually quickly count the number enter by multiplying from a 10base graphical observation.

Thoughts?  Yeah, I know it's paranoid but isn't that the point of encryption?

I hadn't noticed that but i'll test it now. Are you sure it isn't just set to a width of a specific number or to the width of the username?

---

### Post by cipherboy_loc on 2010-12-14
Change the password to a different length. Does the size of the password box change? Now you have me looking into this... ;)



Cipherboy

---

### Post by tgm4883 on 2010-12-14
I just tested it in a 32-bit 10.10 virtual machine, freshly installed yesterday for another purpose. The password field when logging in graphically is 31-32 characters long. Not anywhere near my password length.

Is there somewhere else you want me to check?

---

### Post by FuturePilot on 2010-12-14
I don't see this issue with the login password field either.

---

### Post by Paradoxfox93 on 2010-12-14
I've reinstalled LL64 three times since it's release and thought it was coincidence until this most recent install (once is a accident, twice a coincidence, thrice a conspiracy).

I'm not sure it's *exactly* spaced to the width of the characters but my password is significantly longer than 30 characters and the gui reflects within 1 character's worth of pixels the length of my password each time I have reinstalled 10.04-64


I cannot speak for maverick because after trying to upgrade my first installation it broke PA so bad I had to scrap everything and reinstall.  The recent re-installation I did was due to some bad firewall settings and a really bad encryption password choice.

Thanks for looking into this.  Maybe it's nothing and I can only speak for a fresh install of Lucid64 from the liveCD with encrypted user account.

Incidentally I didn't think you can change the password for an encrypted user as it is used to hash the decryption.

---

### Post by cipherboy_loc on 2010-12-14
I tested it with both the login screen (GDM) and GKSUDO. Both had a length of the field longer (by a good amount) than what I set my password to (10 digits long). 



Cipherboy

---

### Post by Paradoxfox93 on 2010-12-14
Maybe it's been fixed in maverick.   I only *just* noticed this consitantly enough to post about it so now that you are failing to observe the same I will be back in a day or two with more specific and repeatable tests after I grab mavericks and lucid32 and run a few dozen virtual installations to more specifically isolate trends.  TIA for your time and consideration.

---

### Post by FuturePilot on 2010-12-14
> **Paradoxfox93 said:**
> 

Incidentally I didn't think you can change the password for an encrypted user as it is used to hash the decryption.

You can. Use System > Preferences > About Me

---

### Post by movieman on 2010-12-14
Considering that the OS -- as I understand it -- doesn't even store the length of the password but just a cryptographic hash, this would be a bit tricky.

---

