---
title: "systemd forum?"
date: 2020-04-13
forum: Ubuntu, Linux and OS Chat
---

### Post by Quarkrad on 2020-04-13
Is there such a thing as the definitive systemd forum where up to date accurate expert advice is given?  I'm trying to run a script at shutdown and it is proving extremely difficult as there is so much conflicting advice on the webnet.  Specifically I have to write a service file in the form:

```
[Unit]
Description=local-backup at shutdown
Before=shutdown.target reboot.target halt.target
[Service]
ExecStart=/bin/true
ExecStop=/path/to/backup/script/local-backup.sh
RemainAfterExit=yes
[Install]
WantedBy=multi-user.target
```

this file is saved in  /lib/systemd/system/backup.service (make file executable and owned by user)

execute these two commands:
Code:
sudo systemctl start backup
Code:
sudo systemctl enable backup

The above code does not work (I've got many others that also do not work) and one spends hours and hours reading about variants/additions/omissions to this code going round and round in circles.   E.g. I've spent hours reading and learning about the structure of this service code and then read on another site something like  '...from ubuntu xxx the line ExecStart= has to be written as ExecStart=/bin/true.....' .  As per this forum where one can get up to date advice on what to do re ubuntu, that works, is there a place for systemd?

---

### Post by vitalio on 2020-04-13
While not a specialist but on my 19.04 I have /usr/lib/systemd/system-shutdown folder. Maybe putting your script there will help? In mine I have some ufwd script. Just plain sh script. But probably all filesysymes will be unmounted already??? Or readonly???

There also a manpage man systemd-shutdown.
Hope this helps


Nope did not work :( couldn't make it work neither

---

### Post by TheFu on 2020-04-13
No.  Systemd is still under active development and the team seems to write "*aspirational documentation*" for what they hope will happen at some point in the future.  There are new releases of systemd all the time, so what is on your system probably doesn't map to the version on my system.  Still, the local manpages SHOULD be accurate for the version on your box.  That should be where we each start or quest for knowledge with any command on any Unix system.

I wouldn't know how to run a script at shutdown, but I do run some backups, then force standby mode on one of my systems every night.  That works easily, using the root crontab.  Perhaps if you consider that, it would work better?

Vitalio - 19.0-4 support ended a few months ago.  You need to move to a supported release ASAP. There are remote attacks known for 19.04 which have NOT been patched.

---

