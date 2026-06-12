---
title: "forgot passphrase, computer is on."
date: 2012-07-25
forum: Security
---

### Post by colsinc on 2012-07-25
Sorry if this is covered elsewhere, I'm sure I'm not the only one to have had this problem, but I couldn't find any information.

I installed 12.04 on a computer about 2 months ago, and used full disk encryption.  It has been running ever since, but now I want to install updates, and it will probably want to restart afterward.. problem is I am not sure what passphrase I used for the encryption.  Is there a way to find out what it is before I shut down?

---

### Post by cariboo on 2012-07-25
This may help, I haven't tried it myself:

[http://blog.dustinkirkland.com/search?updated-max=2012-05-29T13:36:00-05:00&max-results=7](http://blog.dustinkirkland.com/search?updated-max=2012-05-29T13:36:00-05:00&max-results=7)

Dustin is the maintainer of ecryptfs-utils.

---

### Post by Cheesemill on 2012-07-26
If it's full disk encryption then you're out of luck, there is no way to recover the passphrase.

If you don't know what it is then copy all your data off the encrypted drive now while you still have access. Once you reboot if you can't remember the passphrase then your only option is a new clean installation.

---

### Post by colsinc on 2012-08-29
Thanks for the responses.  

I couldn't find a way to get the passphrase out in cleartext, but it is possible to test some guesses without restarting. Assuming you have some idea what it is.

Go to disk utility, select your disk, select the encrypted partition.  A button will appear to 'Change Passphrase'.  You can then enter your guess for the current phrase (and you must enter a new one too - don't forget it!).  Then enter sudo password.  If your guess is wrong, you will return to the change passphrase dialogue.

Hope this helps anyone else with the same problem.

Luckily for me I got it after several tries :) and restarted successfully.

---

