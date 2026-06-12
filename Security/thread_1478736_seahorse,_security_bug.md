---
title: "seahorse, security bug"
date: 2010-05-10
forum: Security
---

### Post by zeldos on 2010-05-10
in seahorse (apps -> acces -> passwords ens encryption keys)

there are visible passwords... if I choose to lock Passwords: login on  tab Passwords, on next login its unlock again

anyway I dont wont auto logins on accounts in evolution. I wont to write  passwords. How can I choose this option? I did not find any option for  that.

---

### Post by schwascore on 2010-05-12
Let's separate this into two issues

1 - Seahorse
There is no bug in Seahorse that I can find. Opening seahorse only gives a user access to the passwords stored for that user, which is protected by the initial login. Also, Seahorse does not show the passwords in plaintext unless the user selects that option, which requires the following steps:
 - Double-click on the name of the stored password
 - Click on the plus sign at the bottom of the window
 - Check the "show password" box

There is no problem here that I can find.

2 - Evolution
When you created the email account(s) in question, you were prompted to enter a password. Evolution will only remember passwords if you checked the "remember password" box, so at some point you made the choice to have Evolution remember your password(s).

Here's how to turn off this feature:
- Go to Edit --> Preferences
- Select the account you wish to edit and click on the "Edit" button.
- Select the "Receiving Email" tab and un-check the "remember password" box.
- Select the "Sending Email" tab and un-check the "remember password" box.
- Click the "OK" button.

---

### Post by Karl1982 on 2010-05-15
The issue that's bugging me about seahorse right now is simply the fact that if I turn my back on my laptop while it's logged in, my cleartext passwords are a mere 7 clicks away.  At the same time, locking my laptop every time I turn my back can put people off.  I trust my coworkers, but I still don't want my passwords, network passphrases, and keys to be so... available.

What I want from this is pretty simple: I want the seahorse gui to require you to re-unlock keyrings every time you open it.  Is that possible?

---

### Post by FuturePilot on 2010-05-15
[not this again]("http://ubuntuforums.org/showthread.php?t=1302342"). ](*,)

---

### Post by Karl1982 on 2010-05-16
That again indeed, seeing as it has yet to be addressed.  But thanks, your cynicism has pointed me in the right direction to suggest something be done about it.

---

### Post by Jive Turkey on 2010-05-17
I agree with Karl, I think it should be locked.  However, since it isn't you shouldn't be all that concerned, Karl, what your coworkers think about you locking your screen if you can't trust them not to go snooping through your stored passwords. You might get some relief from setting a short delay on the screensaver and set it to lock the screen when activated.

---

