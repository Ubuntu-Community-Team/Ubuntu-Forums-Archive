---
title: "no pgp-keys"
date: 2009-02-18
forum: Ubuntuzilla
---

### Post by gerard on 2009-02-18
I  tried ubuntuzilla on unbuntu 8.10 I got error messages saying that the pgp-keys could not be optained (from various sites).

What does this mean and what can I do about it.

Gerard

---

### Post by nanotube on 2009-02-24
Hi
please post full output of your ubuntuzilla session.

---

### Post by swatsbiz on 2009-04-05
I have a similar problem, the installer won't let me access my profile:

> Backing up old Firefox preferences

Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1146, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 209, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 236, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 601, in install
    self.backupProfile()
  File "/usr/local/bin/ubuntuzilla.py", line 757, in backupProfile
    self.checkDiskSpaceForBackup("~/.mozilla")
  File "/usr/local/bin/ubuntuzilla.py", line 384, in checkDiskSpaceForBackup
    requiredForBackup = int(self.util.getSystemOutput(executionstring="du -sk "+target+" |awk '{print $1}'"))
ValueError: invalid literal for int() with base 10: "du: cannot read directory `/home/david/.mozilla/firefox/ls0awjxq.David': Permission denied"


so I use sudo for the install and then I get this:

> gpg: WARNING: unsafe ownership on configuration file `/home/david/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg --keyserver keymaster.veridis.com --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from keymaster.veridis.com . Trying again...
Failed to retrieve Mozilla Software Releases Public key from any of the listed keyservers. Please check your network connection, and try again later.


what's the way round this?

David

---

### Post by swatsbiz on 2009-04-05
However I have noticed that thunderbird installs without the sudo command without problems.

---

### Post by swatsbiz on 2009-04-05
here's how I solved this problem:

There was a locked profile folder in my ~/.mozilla/firefox/

So I deleted it using:

> sudo rm -r

this got me passed the pgp ownership problem (the locked profile is not the one I use).

All sorted now :KS

---

### Post by nanotube on 2009-04-05
Hi

the problem seems to have been some root-owned directory in your firefox profile. deleting your profile certainly solved the problem. 

in the future, avoid running firefox with sudo, so that there are no files created in your profile that are owned by root.

glad you figured it out. :)

---

### Post by virusiidx on 2009-07-07
Sorry to bump the thread again, but I'm having a similar issue, except only this part...

```
Unable to retrieve Mozilla Software Releases Public key from wwwkeys.pgp.net . Trying again...
gpg: WARNING: unsafe permissions on configuration file `/home/alf/.gnupg/gpg.conf'
gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/alf/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg --keyserver keymaster.veridis.com --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from keymaster.veridis.com . Trying again...
Failed to retrieve Mozilla Software Releases Public key from any of the listed keyservers. Please check your network connection, and try again later.


```

I tried the methods above, but still doesn't work. Any way to fix? Thanks in advance.

---

### Post by nanotube on 2009-07-07
Hi

make sure that your .gnupg directory and the files contained therein are owned by you. further, make sure the directory is chmodded to 700, and all the files inside are chmodded to 600. 

in command-form, run the following commands:
```

sudo chown -R alf:alf ~/.gnupg
chmod 700 ~/.gnupg
chmod 600 ~/.gnupg/*

```

---

### Post by virusiidx on 2009-07-08
That did it! Thank you very much. :)

---

### Post by fencer on 2010-01-04
you are the man it worked perfectly for me as well

---

