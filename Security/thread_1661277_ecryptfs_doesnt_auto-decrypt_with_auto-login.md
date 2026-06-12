---
title: "ecryptfs doesnt auto-decrypt with auto-login"
date: 2011-01-06
forum: Security
---

### Post by reasonably_clever on 2011-01-06
I recently installed 32bit maverick and wanted to make it login automatically.

I tried enabling auto login from **Admin > Login** but that didnt work and I was still prompted for my password.

Then I went to **Users & Groups** and changed the password option to **Do Not ask for password at login**

now after I reboot, the user list is shown (only 1 user) and it doesnt ask for password after I click on my username.

However, then it gives a few errors (as i vaguely recall):

1. cannot load .ICE directory in my home directory
2. some error 256 about a gconf-sanity-2 file
3. nautilus cannot load my home directory etc

and then it gets stuck without loading anything (blank wallpaper).

i ve tried navigating to my home directory using Alt F2, gksudo nautilus and my home dir contents are encrypted by the ecryptfs (there is a readme.txt file and a shortcut). i have tried to decrypt but it doesnt work...
i ve also tried to start/stop gdm, and startx but nothing works. if i stop gdm, then the prompt doesnt recognize my password and keeps on rejecting the commands i enter...

I think this has something to do with the home dir not being decrypted due to the dont ask for paswd option...

any idea on how can i disable the dont ask for pwd without the gui (i can access my / by booting through an external usb).

Thanks.

---

### Post by bodhi.zazen on 2011-01-06
You can not use ecryptfs encryption of your home directory with the auto login in feature as you found. Although this might seem odd, it makes sense, why encrypt $HOME if you autologin ?

The other potential problem is when changing your password you need to use the graphical interface (well that is the easy way).

See :

[http://bodhizazen.net/Tutorials/Ecryptfs](http://bodhizazen.net/Tutorials/Ecryptfs)

---

### Post by cariboo on 2011-01-06
I thought encryption was for keeping others from viewing your personal data, using auto login defeats that purpose, all someone has to do is turn on the computer, wait for it to finishing booting, and then all your personal data is there for them to check out.

---

### Post by bvanaerde on 2011-05-25
I've got the same problem... any idea on how to go back to the previous state?

---

### Post by FuturePilot on 2011-05-25
Either disable auto login or remove ecryptfs [https://help.ubuntu.com/community/EncryptedPrivateDirectory#How%20to%20Remove%20an%20Encrypted%20Private%20Directory%20Setup]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#How%20to%20Remove%20an%20Encrypted%20Private%20Directory%20Setup")

---

### Post by jlahn on 2011-10-23
hi all,

i have a related question - that is, the same, but under slightly different circumstances:

i have a thinkpad x300 and got used to having a startup password which was the same as my login, which made for a combination where autologin made sense for me (and decreased boot time). 

now after moving to 11.10 i chose to encrypt my home, but of course as you said above this is not possible with auto-login. 

now i ask myself, is there a possibility of having login take over the power-on password from the thinkpad so i could save myself the step to have to enter it again for the login?

thanks for your help and knowledge! :D

---

