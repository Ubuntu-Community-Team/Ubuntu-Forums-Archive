---
title: "would it be a false positive in rkhunter?"
date: 2016-09-23
forum: Security
---

### Post by hunter555 on 2016-09-23
My rkhunter on ubuntu 14.04.5 LTs desktop detected 3 warnings and 1 skipped see:

```
Checking system commands...

/usr/bin/unhide.rb                                       [ Warning ] 
```
```
Checking the local host...

 Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]  
```
Skipped:

```
Checking the network...
Checking for hidden ports                                [ Skipped ] 
```

final log:
```

Warning: The command '/usr/bin/unhide.rb' has been replaced by a script: /usr/bin/unhide.rb: Ruby script, ASCII text
Warning: Suspicious file types found in /dev:
         /dev/.udev/rules.d/root.rules: ASCII text
Warning: Hidden directory found: /dev/.udev: directory 
Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'

```
Can you help me?
Thank you

---

### Post by Habitual on 2016-09-24
[What to do with "common" warnings]("https://help.ubuntu.com/community/RKhunter")

---

### Post by hunter555 on 2016-09-25
> **Habitual said:**
> [What to do with "common" warnings]("https://help.ubuntu.com/community/RKhunter")
thank you

---

### Post by Habitual on 2016-09-26
You are welcome!

---

