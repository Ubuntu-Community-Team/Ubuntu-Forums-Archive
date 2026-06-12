---
title: "Problems with eCryptfs after install Fingerprint GUI"
date: 2011-01-30
forum: Security
---

### Post by Gabriel Salinas on 2011-01-30
After buying an IBM/Lenovo USB fingerprint reader model FP06 and installing Fingerprint GUI, have problems to mount my home folder encrypted with eCyptfs. I was using it since the first time i install Ubuntu 10.10 64 bits.

After login from GDM, there are some ways to make it work:
1) open a terminal window and type ecryptfs-mount-private. This decrypt the home folder, but need to logout and login again to my personal preferences can be reached (bookmarks in nautilus, in firefox, etc). Each time the PC is rebooted, the same process is needed to made again.

2) before login in GDM, change to a tty1 terminal (ctrl-alt-F1) and login from here. The personal folder decrypt then without problems. Then change to GDM (ctrl-alt-F8), login an everything works fine. 
What could be the fault from GDM to not mount the encrypted folder?

Some logs are needed to check this, please tell me to put below. 

Thanks in advance.

---

### Post by FuturePilot on 2011-01-30
I'm guessing the problem here is that in order for ecryptfs to decrypt your home directory it needs to receive your login password. If you're using a different type of authentication, a fingerprint reader in this case, ecryptfs never receives your login password so it can't decrypt anything. This is the same reason why auto login doesn't work with ecryptfs. Unfortunately I really don't know a solution to this, but maybe someone else would.

---

### Post by Gabriel Salinas on 2011-01-30
Clarifying the problem...

I know that login with the fingerprint, the home folder wouldn't decrypted nor mounted.

This began after installing the fingerprint reader, but although login not using the fingerprint the home folder remains encrypted.

In a terminal, when type my username, give me the option to type the password in the classic way, or use the fingerprint; this last dont let the home folder to be decrypted as mentioned by FuturePilot. This is not the real problem in my case. 

Summarizing: if login from a tty terminal, the folder is decrypted.
if login from GDM, not decrypted.
Both typing the password.

---

### Post by Gabriel Salinas on 2011-02-05
Nobody?

---

### Post by saspekt on 2011-05-18
bump

---

### Post by chasetoys on 2011-06-25
bump and subscribed

---

### Post by trundlenut on 2011-06-25
I've noticed this, thought I don't have an encrypted home folder.  When you install fingerprint-gui it changes PAM Athentication module (or whatever the proper name is), it seems to be this which stops the password being passed to the keyring even if you type it rather than use your fingerprint.

---

### Post by Gabriel Salinas on 2011-07-18
Solved... formatting and reinstalling Ubuntu. 
 
Can´t be repaired, so the only way was to start again... 
 
Thanks all

---

### Post by chronos00 on 2011-08-06
Did any of you have problems while suspending your computer?

My laptop freezes when trying to suspend, and I suspect the combination of eCryptFS and fingerprint auth has something to do with this...

Freezes are VERY erratic, sometimes it justs freezes, sometimes it wil panic, and sometines it will just NOT suspend, and IOWait will top one of the processors... to make it even wierder, sometimes it WILL suspend.

I have checked every log file available, but none gives any useful information.

I have spent two weeks diagnosing this problem, reading countless forums and trying A LOT of different things, but none of them worked.

Any clues?

---

