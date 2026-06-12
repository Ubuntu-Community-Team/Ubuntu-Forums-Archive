---
title: "Error Installing Firefox 3.5 In Intrepid"
date: 2009-09-05
forum: Ubuntuzilla
---

### Post by Viverrid on 2009-09-05
While running the script, I receive the following error:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
The following packages were automatically installed and are no longer required:
  libevolution3.0-cil linux-headers-2.6.27-7 python-json
  linux-headers-2.6.27-7-generic m4 libwnck2.20-cil libgnomedesktop2.20-cil
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

Backing up old Firefox preferences

cp: reading `/home/mike/.mozilla/firefox/fvh8gfnv.default/urlclassifier3.sqlite': Input/output error
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
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, http://ubuntuzilla.sourceforge.net
```/

Any help would be most appreciated :)

---

### Post by Viverrid on 2009-09-06
Deleting the file "urlclassifier3.sqlite," and then opening and closing Firefox seems to have fixed it.

---

### Post by nanotube on 2009-09-07
Hi
for the future: you probably could have just changed the ownership on all the files in the profile to your user. the permission denied errors are usually caused by having run firefox with sudo previously, which messes up the profile file ownership.

---

### Post by BigBaka on 2009-10-10
nanotube,

Can you please advise how to change the ownership on all the files in the profile to your user.

Thanks
BB

---

### Post by nanotube on 2009-10-12
hi
to change ownership of files in your profile to your user, run the following command:
```
sudo chown -R yourusername:yourusername ~/.mozilla
```

(where of course you replace "yourusername" with your actual username on your machine)

---

