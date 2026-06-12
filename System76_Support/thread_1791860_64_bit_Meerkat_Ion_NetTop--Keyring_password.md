---
title: "64 bit Meerkat Ion NetTop--Keyring password"
date: 2011-06-27
forum: System76 Support
---

### Post by oldpath on 2011-06-27
Keyring password on Meerkat Ion NetTop Ubuntu 10.10 no longer works.  I originally wrote down the login password in my log book. After I moved to Denver from Omaha I found the login would no longer work.  Using Psychocats method I used recovery mode to establish a new login password.  But, with the new login the keyring will no longer recognise the new password.  To change the keyring password I need the 'old' password to make a new password in the SeaHorse Keyring.  I wish I knew what that 'Old Password' was.  
  Has anyone figured out how to get a Keyring Password installed without the old password?

---

### Post by isantop on 2011-06-27
You can open up the "Passwords and Encryption Keys" utility, then delete the old keyring. Nest time you need to access it, it will ask you to create a new keyring password; simply set it to your new log in password.

---

### Post by oldpath on 2011-06-27
I did delete the old keyring password.  Rebooted and no keyring password was asked for.  The computer runs as if Keyring password is OK.  Do I still need to enter a new password?  Am I possibly running the computer with no keyring password?  How do I check this out?

Many thanks

Oldpath

---

### Post by isantop on 2011-06-28
In the Passwords and Encryption Keys window, you can see the current keyrings. 

Running without a keyring password isn't actually all that dangerous, since usually the only information stored in the keyring are things like wireless passwords. If you've set up your email in Evolution, then you'd want to set a password on your keyring.

---

### Post by oldpath on 2011-06-28
Keyrings.  Funny that you mention email Evolution.  It works just fine, but Evolution is linked to my gmail acct and once an a while gmail will prompt me for a log-in password.  So, I do not know for sure if I have a working keyring or not.  I am mystified by the keyring box.  I guess I can play with without doing lasting damage.  I will work at establishing a password in the Keyring box.

Thx,

Oldpath

---

### Post by oldpath on 2011-06-28
I figured that I could find out if I had a working Keyring login by using the change keyring password facility and by entering my current password as the old password and then entering the same password as the new password and punching the change button.  Indeed it worked.  That means that by deleting the keyring password and rebooting this Meerkat computer with Maverick Meerkat 10.10 Ubuntu edition it loaded the Keyring with the new password automatically.  The computer did not prompt me to edit the Keyring password after boot up.  

Problem solved.

Many thanks for your assistance.

Oldpath


Time to close this topic.

---

