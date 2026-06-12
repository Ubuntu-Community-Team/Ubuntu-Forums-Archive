---
title: "Making something load on Bootup?"
date: 2010-12-22
forum: Server Platforms
---

### Post by thefix0r on 2010-12-22
Ok how the heck to make this machine load my unreal server on bootup??

 /home/user/Unreal3.2/./unreal start

---

### Post by SeijiSensei on 2010-12-22
Put the command in /etc/rc.local which is the last script run at boot.  You'll need to edit it with sudo.

---

### Post by thefix0r on 2010-12-22
I tried the following and it doesnt work


#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
su -c /home/fixjack/Unreal3.2/./unreal start



exit 0

---

### Post by HugoSerrano on 2010-12-23
what he means is that you need to edit the file with sudo.
$sudo nano /etc/rc.local
remove the "su -c" from the line you added.

---

### Post by thefix0r on 2010-12-23
bah its ok, I used crontab instead, and that works

---

