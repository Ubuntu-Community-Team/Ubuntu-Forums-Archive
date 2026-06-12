---
title: "Problems installing Firefox 3.5 on ubuntuzilla"
date: 2009-08-26
forum: Ubuntuzilla
---

### Post by darms on 2009-08-26
Dear all,

I'm just a newbie towards ubuntu linux, after looking through the web for update procedure of Firefox, I've manage to found this ubuntuzilla helps to update firefox.  But according to the forum, I have to install a whole new firefox 3.5, I couldn't upgrade from my existing 3.0 to 3.5.  

I'll list down the error that I've encountered while I'm doing my installation.

Errors:

Making sure that the repositories version of Firefox is installed...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

Backing up old Firefox preferences

cp: cannot open `/home/<myname>/.mozilla/firefox/Crash Reports/InstallTime20090729211829' for reading: Permission denied
cp: cannot open `/home/<myname>/.mozilla/firefox/vsx4sm17.default/flashgot.log.bak' for reading: Permission denied
cp -R ~/.mozilla ~/.mozilla_backup_$(date -Iseconds)
Failed to back up profile.
Process returned code 1
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1294, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 300, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 343, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 744, in install
    self.backupProfile()
  File "/usr/local/bin/ubuntuzilla.py", line 906, in backupProfile
    self.util.execSystemCommand(executionstring="cp -R ~/.mozilla ~/.mozilla_backup_$(date -Iseconds)", errormessage="Failed to back up profile.")
  File "/usr/local/bin/ubuntuzilla.py", line 143, in execSystemCommand
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)
________________________________________________________________________

Hopefully someone can help me out here.  Thank you for your patient!

---

### Post by nanotube on 2009-08-26
Hi
it appears that the permissions on your firefox profile got messed up. probably because you ran firefox as root (with sudo) at some point before.

So, run the following commands to get stuff back in order:
```
sudo chown -R yourusername:yourusername ~/.mozilla
sudo chmod -R u+r ~/.mozilla
```

replace 'yourusername' with your actual username, of course.

then run ubuntuzilla again.

---

### Post by darms on 2009-08-26
Hey nanotube,

Thank you for your assistant.  I really appreciate it and it works like a charm!  I hope this will be an assistant towards those people who has manually upgraded their FireFox to 3.5.:lolflag:

By the way, I've noticed a couple changes has been made on 3.5, but i realized that the surfing is a lot slower when it comes to ads.  Especially when i login my yahoo mail (new interface), it will cost my firefox to hang.

I was just curious if anyone have the same problem that I'm facing?  Thank you and hope to hear from any of you soon!

p/s: anyway, love ubuntu due to the support community!:KS

---

### Post by nanotube on 2009-08-26
glad to see that it worked :)

as far as ads are concerned, I highly recommend the adblock plus extension, along with the easylist blocklist subscription:

[http://adblockplus.org/](http://adblockplus.org/)

[http://adblockplus.org/en/subscriptions](http://adblockplus.org/en/subscriptions)

hope that helps. :)

---

