---
title: "Clamav engine"
date: 2010-10-31
forum: Security
---

### Post by Jesusguy44 on 2010-10-31
My name is Todd, I am new here.  I just had a question, My clamav says that the engine is out of date.  How can I upgrade the engine.  Thank you :P

---

### Post by llamakc on 2010-10-31
```

sudo freshclam

```

Will update the signatures. As to the engine, you should specify which version of Ubuntu you are using and which version of clamav is currently installed.

---

### Post by uRock on 2010-10-31
Hi and Welcome,

If the engine is out of date it will still upgrade definitions and run properly, but the newer engine has to be manually installed via the [ClamTK]("http://sourceforge.net/projects/clamtk/") website.

Regards,
uRock



Moved to Security Discussions.

---

### Post by Jesusguy44 on 2010-10-31
Sorry about that, I am using Ubuntu 10.10 and the clamav engine is 96.3.  The clamav website says that the engine was been updated to 96.4.  Thanks

---

### Post by 73ckn797 on 2010-10-31
Go to System/Administration/Synaptic Package Manager and install "clam-freshclam" which will keep things updated. You can also enter in Applications/Accessories/Terminal: ```
sudo apt-get install clam-freshclam
``` and accomplish the same thing.

---

### Post by Jesusguy44 on 2010-10-31
How would you install the new engine.  I installed clamav from the Ubuntu Software center.

---

### Post by uRock on 2010-10-31
Download the new version on the link I posted, then right click and open with Ubuntu Software Center, then click to install it.

---

### Post by Jesusguy44 on 2010-10-31
Thanks for the help.

---

### Post by uRock on 2010-10-31
You're welcome.

Please mark this thread as solved by clicling the red Thread Tools dropdown near the top of the screen.

---

### Post by 73ckn797 on 2010-10-31
The "clam-freshclam" package states:
[HTML]This package contains the freshclam program and scripts to automate virus
database updating. It relies on an Internet connection, but can be
run in a variety of ways to compensate for intermittent connections.[/HTML]

---

### Post by uRock on 2010-10-31
Freshclam only updates the signatures. It doesn't update the GUI, which is what the OP wanted to upgrade.

---

