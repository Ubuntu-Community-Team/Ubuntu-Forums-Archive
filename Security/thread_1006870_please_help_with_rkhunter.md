---
title: "please help with rkhunter"
date: 2008-12-09
forum: Security
---

### Post by drascus on 2008-12-09
could someone please look at my logfile and let me know if my system has been compromised. I got several warnings while running RKhunter. It doesn't look bad to me but I am not sure. 

```
[20:48:37] /usr/sbin/unhide                                  [ Warning ]
[20:48:37] Warning: The file '/usr/sbin/unhide' exists on the system, but it is not present in the rkhunter.dat file.
[20:48:37] /usr/sbin/useradd                                 [ OK ]
[20:48:37] /usr/sbin/userdel                                 [ OK ]
[20:48:37] /usr/sbin/usermod                                 [ OK ]
[20:48:38] /usr/sbin/vipw                                    [ OK ]
[20:48:38] /usr/sbin/unhide-linux26                          [ Warning ]
[20:48:38] Warning: The file '/usr/sbin/unhide-linux26' exists on the system, but it is not present in the rkhunter.dat file.
```

```
[20:51:24] Performing filesystem checks
[20:51:24] Info: Starting test name 'filesystem'
[20:51:24] Info: SCAN_MODE_DEV set to 'THOROUGH'
[20:51:27]   Checking /dev for suspicious file types         [ Warning ]
[20:51:27] Warning: Suspicious file types found in /dev:
[20:51:27]          /dev/shm/pulse-shm-2035059263: data
[20:51:28]   Checking for hidden files and directories       [ None found ]
```

sorry if this is a stupid question it is my first time using Rkhunter so I don't know what to expect. thanks for the help.

---

### Post by drascus on 2008-12-10
So just to be safe I did a fresh install. I used Dariks boot and nuke just to be safe. after the fresh install I installed rkhunter and ran another scan. I came up with the same warning results. So I am assuming that these are false positives. I am just looking for a second opinion on that.

---

### Post by bodhi.zazen on 2008-12-10
They are likely false positives.

If in doubt, google is your friend. If it is a known exploit, or a know false positive, google should give you some information. If not, I suggest you report it as a false positive to the depelopers.

---

### Post by OrangeCrate on 2008-12-10
When you installed rkhunter, unhide was installed as a "recommend", and is used by rkhunter. I would doubt that it's anything more than a false positive.

[https://launchpad.net/ubuntu/intrepid/+package/unhide](https://launchpad.net/ubuntu/intrepid/+package/unhide)

---

### Post by wyth on 2009-02-17
Run 
```
sudo rkhunter --propupd
```

---

### Post by drascus on 2009-02-18
hey the --propupd was a real help the warnings disappeared after that. except the suspicious file type warning in /dev but I don't think that is a concern thanks!!

---

