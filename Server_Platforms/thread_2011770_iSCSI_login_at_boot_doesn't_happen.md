---
title: "iSCSI login at boot doesn't happen"
date: 2012-06-27
forum: Server Platforms
---

### Post by jpmfresno on 2012-06-27
Hi..Im new to the forums and I don't have extensive Linux knowledge yet..I'm a Windows Server Admin.
 
_Issue:_
 
Trying to do something seemingly simple, adding an iSCSI lun to my new Ubuntu 12.04 LTS server.
 
I've successfully configured and mounted the volume but on a reboot the initiator doesn't automatically log on to the target and there for the mounts don't happen. I have to run this command to manually logon:
 
iscsiadm -m node --targetname "iqn.2001-05.com.equallogic:0-8a0906-9c06f9d0a-2e6814005f04fea4-test01" --portal "192.168.1.50:3260" --login
 
This connects successfully and I can then mount the volumes.
 
I should also mention I have ***node.startup = automatic*** in /etc/iscsi/iscsid.conf
 
Not sure why this isn't working.
 
Thanks in advance.
Joe

---

### Post by SeijiSensei on 2012-06-28
The tried-and-true hackish way to fix problems like these is to dump the command into the file called /etc/rc.local.  It's the last script run during boot.

/etc/rc.local is is owned and executed by root, so you'll need to use sudo to edit it.  Add the "iscsiadm..." command you gave above into that file.  That command will now be run with root privileges at each boot.  Reboot to see if that fixes the problem.

---

### Post by solarix on 2012-06-30
> **jpmfresno said:**
> Hi..Im new to the forums and I don't have extensive Linux knowledge yet..I'm a Windows Server Admin.
 
_Issue:_
 
Trying to do something seemingly simple, adding an iSCSI lun to my new Ubuntu 12.04 LTS server.
 
I've successfully configured and mounted the volume but on a reboot the initiator doesn't automatically log on to the target and there for the mounts don't happen. I have to run this command to manually logon:
 
iscsiadm -m node --targetname "iqn.2001-05.com.equallogic:0-8a0906-9c06f9d0a-2e6814005f04fea4-test01" --portal "192.168.1.50:3260" --login
 
This connects successfully and I can then mount the volumes.
 
I should also mention I have ***node.startup = automatic*** in /etc/iscsi/iscsid.conf
 
Not sure why this isn't working.
 
Thanks in advance.
Joe

The Startup Script seems to be utterly broken.


As i had to face the same issue few weeks ago,  i wondered that my working ISCSI LUn Config,
from SuSE, Debian and RedHat Systems
never started up on Ubuntu precise  so  i took the DEBIAN Squeeze startup Script from the open-iscsi Package and it worked immediately.


Take the attached Script copy it somewhere on the box
 ```
 
cp open-iscsci.sh /etc/init.d/open-iscsi
cd /etc/init.d

 :/etc/init.d#
chmod +x open-iscsi

```

```
update-rc.d open-iscsi enable
 update-rc.d open-iscsi start 20 2 3 4 5 . stop 20 0 1 6 .

```

At least verify if  update-rcd  has done the job.

```
ls -l /etc/rc*.d/S* |grep open-iscsi

```
you  should recive a comparable output 

```
rwxrwxrwx 1 root root 20 Jun  2 09:44 /etc/rc0.d/S41open-iscsi -> ../init.d/open-iscsi
lrwxrwxrwx 1 root root 20 Jun  2 09:44 /etc/rc1.d/S41open-iscsi -> ../init.d/open-iscsi
lrwxrwxrwx 1 root root 20 Jun  2 09:44 /etc/rc6.d/S41open-iscsi -> ../init.d/open-iscsi
```

If your ISCSI Config is valid all the LUN should be mounted automatically at the next Reboot

---

### Post by chernobil on 2012-08-07
Huge thanks mate!

I was having the same issue and I was in a hurry to deliver the server.

After swapping the daemon script with yours it's working like a charm ;)

Kind regards,

Ivan

---

### Post by cyberfarer on 2012-12-05
Thank you for the posting and resolution. I don't understand why open-iscsi is always such a challenge on Ubuntu Server.

---

### Post by tvbowman on 2013-02-13
Thank you, solarix, worked great!

---

### Post by jimbeck81 on 2013-02-15
Life-saver.

Thank you!

---

