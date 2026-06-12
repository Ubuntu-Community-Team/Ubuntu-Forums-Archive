---
title: "My system was hacked?!?"
date: 2009-11-18
forum: Security
---

### Post by rg_stephens on 2009-11-18
This morning I sent some emails before going to work. When I returned home, there were all kinds of files open, settings changed, like someone was playing around on my system. 

NO ONE has a key to my house, and Remote Desktop is set to "Do not allow connections." I am using Pidgin and Skype, would these be a problem? ClamAV tells me there are no viruses. What Happened???

---

### Post by doas777 on 2009-11-18
check your auth log, and whatnot. do you have ssh enabled?

---

### Post by rg_stephens on 2009-11-18
SSH is not installed. I opened the log file viewer, I'm not sure what to look for. Here is the auth.log for today until I got home:

```
ov 18 00:09:01 beto-laptop CRON[2825]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 00:09:01 beto-laptop CRON[2825]: pam_unix(cron:session): session closed for user root
Nov 18 00:17:01 beto-laptop CRON[2877]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 00:17:01 beto-laptop CRON[2877]: pam_unix(cron:session): session closed for user root
Nov 18 00:39:01 beto-laptop CRON[2907]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 00:39:01 beto-laptop CRON[2907]: pam_unix(cron:session): session closed for user root
Nov 18 01:09:01 beto-laptop CRON[2950]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 01:09:01 beto-laptop CRON[2950]: pam_unix(cron:session): session closed for user root
Nov 18 01:17:01 beto-laptop CRON[2963]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 01:17:01 beto-laptop CRON[2963]: pam_unix(cron:session): session closed for user root
Nov 18 01:39:01 beto-laptop CRON[2991]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 01:39:01 beto-laptop CRON[2991]: pam_unix(cron:session): session closed for user root
Nov 18 02:09:01 beto-laptop CRON[3030]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 02:09:01 beto-laptop CRON[3030]: pam_unix(cron:session): session closed for user root
Nov 18 02:17:01 beto-laptop CRON[3043]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 02:17:01 beto-laptop CRON[3043]: pam_unix(cron:session): session closed for user root
Nov 18 02:39:01 beto-laptop CRON[3071]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 02:39:01 beto-laptop CRON[3071]: pam_unix(cron:session): session closed for user root
Nov 18 03:09:01 beto-laptop CRON[3113]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 03:09:01 beto-laptop CRON[3113]: pam_unix(cron:session): session closed for user root
Nov 18 03:17:01 beto-laptop CRON[3126]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 03:17:01 beto-laptop CRON[3126]: pam_unix(cron:session): session closed for user root
Nov 18 03:39:01 beto-laptop CRON[3154]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 03:39:01 beto-laptop CRON[3154]: pam_unix(cron:session): session closed for user root
Nov 18 04:09:01 beto-laptop CRON[3192]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 04:09:01 beto-laptop CRON[3192]: pam_unix(cron:session): session closed for user root
Nov 18 04:17:01 beto-laptop CRON[3205]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 04:17:01 beto-laptop CRON[3205]: pam_unix(cron:session): session closed for user root
Nov 18 04:39:01 beto-laptop CRON[3236]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 04:39:01 beto-laptop CRON[3236]: pam_unix(cron:session): session closed for user root
Nov 18 05:09:01 beto-laptop CRON[3275]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 05:09:01 beto-laptop CRON[3275]: pam_unix(cron:session): session closed for user root
Nov 18 05:17:01 beto-laptop CRON[3288]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 05:17:01 beto-laptop CRON[3288]: pam_unix(cron:session): session closed for user root
Nov 18 05:39:01 beto-laptop CRON[3315]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 05:39:01 beto-laptop CRON[3315]: pam_unix(cron:session): session closed for user root
Nov 18 06:09:01 beto-laptop CRON[3355]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 06:09:01 beto-laptop CRON[3355]: pam_unix(cron:session): session closed for user root
Nov 18 06:17:01 beto-laptop CRON[3369]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 06:17:01 beto-laptop CRON[3369]: pam_unix(cron:session): session closed for user root
Nov 18 06:25:01 beto-laptop CRON[3380]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 06:25:01 beto-laptop CRON[3380]: pam_unix(cron:session): session closed for user root
Nov 18 06:39:01 beto-laptop CRON[3398]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 06:39:01 beto-laptop CRON[3398]: pam_unix(cron:session): session closed for user root
Nov 18 07:09:01 beto-laptop CRON[3461]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 07:09:01 beto-laptop CRON[3461]: pam_unix(cron:session): session closed for user root
Nov 18 07:17:01 beto-laptop CRON[3482]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 07:17:01 beto-laptop CRON[3482]: pam_unix(cron:session): session closed for user root
Nov 18 07:30:02 beto-laptop CRON[3514]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 07:30:02 beto-laptop CRON[3514]: pam_unix(cron:session): session closed for user root
Nov 18 07:35:05 beto-laptop sudo:     root : TTY=unknown ; PWD=/ ; USER=beto ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Nov 18 07:35:05 beto-laptop sudo:     root : TTY=unknown ; PWD=/ ; USER=beto ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Nov 18 07:35:05 beto-laptop sudo:     root : TTY=unknown ; PWD=/ ; USER=beto ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Nov 18 07:39:01 beto-laptop CRON[3594]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 07:39:01 beto-laptop CRON[3594]: pam_unix(cron:session): session closed for user root
Nov 18 08:07:59 beto-laptop sudo:     beto : TTY=unknown ; PWD=/home/beto ; USER=root ; COMMAND=/usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 96469031 -o Synaptic::closeZvt=true --progress-str Please wait, this can take some time. --finish-str Update is complete --set-selections-file /tmp/tmp2uSiF5
Nov 18 08:09:01 beto-laptop CRON[3909]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 08:09:01 beto-laptop CRON[3909]: pam_unix(cron:session): session closed for user root
Nov 18 08:17:01 beto-laptop CRON[9382]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 08:17:01 beto-laptop CRON[9382]: pam_unix(cron:session): session closed for user root
Nov 18 08:39:01 beto-laptop CRON[9501]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 08:39:01 beto-laptop CRON[9501]: pam_unix(cron:session): session closed for user root
Nov 18 09:09:01 beto-laptop CRON[9559]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 09:09:01 beto-laptop CRON[9559]: pam_unix(cron:session): session closed for user root
Nov 18 09:17:01 beto-laptop CRON[9572]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 09:17:01 beto-laptop CRON[9572]: pam_unix(cron:session): session closed for user root
Nov 18 09:39:01 beto-laptop CRON[9718]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 09:39:01 beto-laptop CRON[9718]: pam_unix(cron:session): session closed for user root
Nov 18 10:09:01 beto-laptop CRON[10134]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 10:09:01 beto-laptop CRON[10134]: pam_unix(cron:session): session closed for user root
Nov 18 10:17:01 beto-laptop CRON[10260]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 10:17:01 beto-laptop CRON[10260]: pam_unix(cron:session): session closed for user root
Nov 18 10:39:02 beto-laptop CRON[10815]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 10:39:02 beto-laptop CRON[10815]: pam_unix(cron:session): session closed for user root
Nov 18 11:09:01 beto-laptop CRON[10980]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 11:09:01 beto-laptop CRON[10980]: pam_unix(cron:session): session closed for user root
Nov 18 11:17:01 beto-laptop CRON[10993]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 11:17:01 beto-laptop CRON[10993]: pam_unix(cron:session): session closed for user root
Nov 18 11:39:01 beto-laptop CRON[11297]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 11:39:01 beto-laptop CRON[11297]: pam_unix(cron:session): session closed for user root
Nov 18 12:09:01 beto-laptop CRON[11884]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 12:09:01 beto-laptop CRON[11884]: pam_unix(cron:session): session closed for user root
Nov 18 12:17:01 beto-laptop CRON[12342]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 12:17:01 beto-laptop CRON[12342]: pam_unix(cron:session): session closed for user root
Nov 18 12:39:01 beto-laptop CRON[13951]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 12:39:01 beto-laptop CRON[13951]: pam_unix(cron:session): session closed for user root
Nov 18 13:09:01 beto-laptop CRON[15434]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 13:09:01 beto-laptop CRON[15434]: pam_unix(cron:session): session closed for user root
Nov 18 13:17:01 beto-laptop CRON[15863]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 13:17:01 beto-laptop CRON[15863]: pam_unix(cron:session): session closed for user root
Nov 18 13:39:01 beto-laptop CRON[17432]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 13:39:01 beto-laptop CRON[17432]: pam_unix(cron:session): session closed for user root
Nov 18 14:09:02 beto-laptop CRON[19593]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 14:09:02 beto-laptop CRON[19593]: pam_unix(cron:session): session closed for user root
Nov 18 14:17:01 beto-laptop CRON[20248]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 14:17:01 beto-laptop CRON[20248]: pam_unix(cron:session): session closed for user root
Nov 18 14:39:01 beto-laptop CRON[21674]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 14:39:01 beto-laptop CRON[21674]: pam_unix(cron:session): session closed for user root
Nov 18 15:09:01 beto-laptop CRON[23657]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 15:09:01 beto-laptop CRON[23657]: pam_unix(cron:session): session closed for user root
Nov 18 15:17:01 beto-laptop CRON[24162]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 15:17:02 beto-laptop CRON[24162]: pam_unix(cron:session): session closed for user root
Nov 18 15:39:01 beto-laptop CRON[25505]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 15:39:01 beto-laptop CRON[25505]: pam_unix(cron:session): session closed for user root
Nov 18 16:09:01 beto-laptop CRON[27398]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 16:09:01 beto-laptop CRON[27398]: pam_unix(cron:session): session closed for user root
Nov 18 16:17:01 beto-laptop CRON[27958]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 16:17:01 beto-laptop CRON[27958]: pam_unix(cron:session): session closed for user root
Nov 18 16:18:01 beto-laptop CRON[28021]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 16:18:03 beto-laptop CRON[28021]: pam_unix(cron:session): session closed for user root
Nov 18 16:39:01 beto-laptop CRON[29317]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 16:39:01 beto-laptop CRON[29317]: pam_unix(cron:session): session closed for user root
Nov 18 17:09:02 beto-laptop CRON[31229]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 17:09:02 beto-laptop CRON[31229]: pam_unix(cron:session): session closed for user root
Nov 18 17:17:01 beto-laptop CRON[31766]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 17:17:01 beto-laptop CRON[31766]: pam_unix(cron:session): session closed for user root
Nov 18 17:39:01 beto-laptop CRON[645]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 17:39:01 beto-laptop CRON[645]: pam_unix(cron:session): session closed for user root
Nov 18 18:09:01 beto-laptop CRON[2682]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 18:09:01 beto-laptop CRON[2682]: pam_unix(cron:session): session closed for user root
Nov 18 18:17:01 beto-laptop CRON[3180]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 18:17:01 beto-laptop CRON[3180]: pam_unix(cron:session): session closed for user root
Nov 18 18:39:01 beto-laptop CRON[4524]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 18:39:01 beto-laptop CRON[4524]: pam_unix(cron:session): session closed for user root
Nov 18 19:09:01 beto-laptop CRON[6362]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 19:09:01 beto-laptop CRON[6362]: pam_unix(cron:session): session closed for user root
Nov 18 19:17:01 beto-laptop CRON[6855]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 19:17:01 beto-laptop CRON[6855]: pam_unix(cron:session): session closed for user root
Nov 18 19:39:01 beto-laptop CRON[8196]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 19:39:01 beto-laptop CRON[8196]: pam_unix(cron:session): session closed for user root
Nov 18 20:09:01 beto-laptop CRON[10031]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 20:09:01 beto-laptop CRON[10031]: pam_unix(cron:session): session closed for user root
Nov 18 20:17:01 beto-laptop CRON[10527]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 20:17:01 beto-laptop CRON[10527]: pam_unix(cron:session): session closed for user root
Nov 18 20:39:01 beto-laptop CRON[11888]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 20:39:01 beto-laptop CRON[11888]: pam_unix(cron:session): session closed for user root
Nov 18 21:09:02 beto-laptop CRON[13732]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 21:09:02 beto-laptop CRON[13732]: pam_unix(cron:session): session closed for user root
Nov 18 21:17:01 beto-laptop CRON[14226]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 21:17:01 beto-laptop CRON[14226]: pam_unix(cron:session): session closed for user root
Nov 18 21:39:01 beto-laptop CRON[15581]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 21:39:01 beto-laptop CRON[15581]: pam_unix(cron:session): session closed for user root
Nov 18 22:09:01 beto-laptop CRON[17450]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 22:09:01 beto-laptop CRON[17450]: pam_unix(cron:session): session closed for user root
Nov 18 22:17:01 beto-laptop CRON[17942]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 22:17:01 beto-laptop CRON[17942]: pam_unix(cron:session): session closed for user root
Nov 18 22:39:01 beto-laptop CRON[19287]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 22:39:01 beto-laptop CRON[19287]: pam_unix(cron:session): session closed for user root
Nov 18 23:09:01 beto-laptop CRON[21119]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 23:09:01 beto-laptop CRON[21119]: pam_unix(cron:session): session closed for user root
Nov 18 23:17:01 beto-laptop CRON[21301]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 18 23:17:02 beto-laptop CRON[21301]: pam_unix(cron:session): session closed for user root
```

---

### Post by skillllllz on 2009-11-19
That auth log look suspicious. I would install rkhunter and do a scan for rootkits.

---

### Post by doas777 on 2009-11-19
the cron messages are normal. not sure about the others. they could be suspicious.

---

### Post by rg_stephens on 2009-11-19
Hmmm, there are some suspect files. Not sure what it means

This was with rkhunter

```
[00:34:40] /usr/sbin/unhide                                  [ Warning ]
[00:34:40] Warning: The file '/usr/sbin/unhide' exists on the system, but it is not present in the rkhunter.dat file.
[00:34:40] /usr/sbin/useradd                                 [ OK ]
[00:34:40] /usr/sbin/userdel                                 [ OK ]
[00:34:40] /usr/sbin/usermod                                 [ OK ]
[00:34:40] /usr/sbin/vipw                                    [ OK ]
[00:34:40] /usr/sbin/unhide-linux26                          [ Warning ]
[00:34:40] Warning: The file '/usr/sbin/unhide-linux26' exists on the system, but it is not present in the rkhunter.dat file.
[00:34:51]
[00:35:48]   Checking /dev for suspicious file types         [ Warning ]
[00:35:48] Warning: Suspicious file types found in /dev:
[00:35:48]          /dev/shm/pulse-shm-166145859: data
[00:35:48]          /dev/shm/pulse-shm-2166669791: data
[00:35:48]          /dev/shm/pulse-shm-4189239141: data
[00:35:48]          /dev/shm/pulse-shm-23335385: data
[00:35:48]          /dev/shm/pulse-shm-3225243383: data
[00:35:48]          /dev/shm/pulse-shm-2431161965: data
[00:35:49]   Checking for hidden files and directories       [ Warning ]
[00:35:49] Warning: Hidden directory found: /etc/.java
[00:35:49] Warning: Hidden directory found: /dev/.udev
[00:35:49] Warning: Hidden directory found: /dev/.initramfs
```

---

### Post by doas777 on 2009-11-19
those are pretty standard messages. have you looked at the log? it usually tells you exactly what the warning is.

---

### Post by rg_stephens on 2009-11-19
This is the log, unless there's another one. 



> **doas777 said:**
> those are pretty standard messages. have you looked at the log? it usually tells you exactly what the warning is.

---

### Post by rg_stephens on 2009-11-19
A couple nights ago I heard the AutoPreview of icons on my desktop, like someone was moving the mouse around. There was no one here, but I didn't bother to check it out. Could there be a hole in Remote Desktop?

---

### Post by skillllllz on 2009-11-19
Are you on a network with other computers? Is your machine behind a hardware firewall? If you like I can perform a penetration test for you, just PM me for that.

Other than a remote attacker, it could be something stupid like a faulty keyboard or mouse. Also, do you have any animals in the house that may be touching the keyboard or something? I know the last question may seem obvious, but sometimes we overlook the simple explanations, so I must ask.

---

### Post by EJeanmaire on 2009-11-19
> **rg_stephens said:**
> A couple nights ago I heard the AutoPreview of icons on my desktop, like someone was moving the mouse around. There was no one here, but I didn't bother to check it out. Could there be a hole in Remote Desktop?

Do you visit questionable websites or websites from links you get in email?  How often do you update your system (via Update Manager or Synaptic)?

---

### Post by doas777 on 2009-11-19
> **rg_stephens said:**
> This is the log, unless there's another one.

your right. I took it for the output (it's been a while since I've used rkhunter).
the pulse shims, and unhide are common warnings, and shouldn't be a problem. the hidden dirs look legit, but you may wanna look closer.
you may also want to run scans with chkrootkit and tiger. you may want to install the harden-enviroment package as that contains a preconfigured IDS that gives you some extra logging.

---

### Post by rg_stephens on 2009-11-19
Hmmm, didn't think of that. The HP Tablet has several different pointing devices, but they seem to work normal. I wonder if static electricity could affect the touchpad? Or the pen? You'd have to click on things to make files open.

I don't have a router, but I just installed Firestarter. If it's insecure, I'd like to know

Thanks!

> **skillllllz said:**
> Are you on a network with other computers? Is your machine behind a hardware firewall? If you like I can perform a penetration test for you, just PM me for that.

Other than a remote attacker, it could be something stupid like a faulty keyboard or mouse. Also, do you have any animals in the house that may be touching the keyboard or something? I know the last question may seem obvious, but sometimes we overlook the simple explanations, so I must ask.

---

### Post by Sarmacid on 2009-11-19
> **rg_stephens said:**
> Hmmm, didn't think of that. The HP Tablet has several different pointing devices, but they seem to work normal. I wonder if static electricity could affect the touchpad? Or the pen? You'd have to click on things to make files open.

I don't have a router, but I just installed Firestarter. My IP is. Feel free to try whatever. If it's insecure, I'd like to know

Thanks!

You should edit your post and remove your IP address from there, you're giving away too much information of your system to possible attackers. Use the pm feature to give your ip to someone you trust to perform those tests.

---

### Post by cdenley on 2009-11-19
My first guess would be that you're using VNC without a password, but you said remote desktop is disabled. Did you install another vnc server? Do you have any servers running?
```

sudo netstat -tulnp

```
If you don't have any but avahi and dhcp, then a firewall isn't going to do much good. Also, it would be impossible for an attacker to take over your computer unless there is already something malicious running which initiates the connection.
```

sudo netstat -tunp

```

That auth.log looks perfectly normal by the way. What kind of settings were changed, anyway?

---

### Post by rg_stephens on 2009-11-19
Well last night I changed my password and installed firestarter

chrootkit didn't give any errors. tiger gave a lot of Warnings, not sure what they mean. The log file is too big to attach

I don't visit questionable sites, but I do use the internet a lot. At one time I tried to set up a lamp server, but I didn't know how to configure it, so I ended up using a hosting company. It only reports Skype as an active connection.


```
sudo netstat -tulnp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1432/mysqld     
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      2326/perl       
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      2056/cupsd      
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1753/master     
tcp        0      0 0.0.0.0:17114           0.0.0.0:*               LISTEN      2483/skype      
tcp6       0      0 :::1024                 :::*                    LISTEN      2188/apache2    
tcp6       0      0 :::139                  :::*                    LISTEN      2018/smbd       
tcp6       0      0 ::1:631                 :::*                    LISTEN      2056/cupsd      
tcp6       0      0 :::445                  :::*                    LISTEN      2018/smbd       
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1435/dhclient   
udp        0      0 0.0.0.0:17114           0.0.0.0:*                           2483/skype      
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           1123/avahi-daemon: 
udp        0      0 0.0.0.0:34563           0.0.0.0:*                           1123/avahi-daemon: 
udp        0      0 68.49.176.35:137        0.0.0.0:*                           1775/nmbd       
udp        0      0 0.0.0.0:137             0.0.0.0:*                           1775/nmbd       
udp        0      0 68.49.176.35:138        0.0.0.0:*                           1775/nmbd       
udp        0      0 0.0.0.0:138             0.0.0.0:*                           1775/nmbd       
udp        0      0 127.0.0.1:50959         0.0.0.0:*                           2483/skype      
udp        0      0 0.0.0.0:10000           0.0.0.0:*                           2326/perl       

```

---

### Post by cdenley on 2009-11-19
There are two things that would concern me? You have a samba server running. This is not the most secure file server, and shouldn't be accessible to the internet. How are you using it?

What concerns me more, though, is the perl script listening on port 10000.
```

sudo lsof -p 2326

```

Webmin perhaps? If so, it shouldn't be listening for any remote connections.

---

### Post by rg_stephens on 2009-11-19
I sometimes use samba if I'm on a LAN and I want to share files between a windows computer. Should I set up a password for it?

I know that perl is a programming language, but I'm not a programmer.

```
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/beto/.gvfs
      Output information may be incomplete.
COMMAND    PID USER   FD   TYPE     DEVICE SIZE/OFF    NODE NAME
miniserv. 2326 root  cwd    DIR        8,1    12288   29088 /usr/share/webmin
miniserv. 2326 root  rtd    DIR        8,1     4096       2 /
miniserv. 2326 root  txt    REG        8,1  1306332     315 /usr/bin/perl
miniserv. 2326 root  mem    REG        8,1  1319364 1180500 /lib/tls/i686/cmov/libc-2.10.1.so
miniserv. 2326 root  mem    REG        8,1  1454876 3147066 /lib/i686/cmov/libcrypto.so.0.9.8
miniserv. 2326 root  mem    REG        8,1    83608 1060446 /lib/libz.so.1.2.3.3
miniserv. 2326 root  mem    REG        8,1    22024 3150286 /usr/lib/perl/5.10.0/auto/Sys/Syslog/Syslog.so
miniserv. 2326 root  mem    REG        8,1    38344   19026 /usr/lib/perl5/auto/Authen/PAM/PAM.so
miniserv. 2326 root  mem    REG        8,1    79676 1180506 /lib/tls/i686/cmov/libnsl-2.10.1.so
miniserv. 2326 root  mem    REG        8,1    17924    2677 /usr/lib/perl/5.10.0/auto/IO/IO.so
miniserv. 2326 root  mem    REG        8,1    42444   77953 /usr/lib/perl5/auto/IO/Tty/Tty.so
miniserv. 2326 root  mem    REG        8,1     9736 1180503 /lib/tls/i686/cmov/libdl-2.10.1.so
miniserv. 2326 root  mem    REG        8,1    38504 1180511 /lib/tls/i686/cmov/libnss_nis-2.10.1.so
miniserv. 2326 root  mem    REG        8,1   362912  108118 /usr/lib/perl5/auto/Net/SSLeay/SSLeay.so
miniserv. 2326 root  mem    REG        8,1    42572 1180509 /lib/tls/i686/cmov/libnss_files-2.10.1.so
miniserv. 2326 root  mem    REG        8,1     9748 1180519 /lib/tls/i686/cmov/libutil-2.10.1.so
miniserv. 2326 root  mem    REG        8,1   113320 3015891 /lib/ld-2.10.1.so
miniserv. 2326 root  mem    REG        8,1   149392 1180504 /lib/tls/i686/cmov/libm-2.10.1.so
miniserv. 2326 root  mem    REG        8,1    22056    2706 /usr/lib/perl/5.10.0/auto/Socket/Socket.so
miniserv. 2326 root  mem    REG        8,1    30684 1180516 /lib/tls/i686/cmov/librt-2.10.1.so
miniserv. 2326 root  mem    REG        8,1    26400 1180507 /lib/tls/i686/cmov/libnss_compat-2.10.1.so
miniserv. 2326 root  mem    REG        8,1    46736 3148750 /lib/libpam.so.0.82.1
miniserv. 2326 root  mem    REG        8,1    17840 1180921 /usr/lib/perl/5.10.0/auto/Digest/MD5/MD5.so
miniserv. 2326 root  mem    REG        8,1   298548 3147067 /lib/i686/cmov/libssl.so.0.9.8
miniserv. 2326 root  mem    REG        8,1    13796    2665 /usr/lib/perl/5.10.0/auto/Fcntl/Fcntl.so
miniserv. 2326 root  mem    REG        8,1   108596    2697 /usr/lib/perl/5.10.0/auto/POSIX/POSIX.so
miniserv. 2326 root  mem    REG        8,1   116920 1180514 /lib/tls/i686/cmov/libpthread-2.10.1.so
miniserv. 2326 root  mem    REG        8,1    38360 1180502 /lib/tls/i686/cmov/libcrypt-2.10.1.so
miniserv. 2326 root  mem    REG        8,1    34420 3150256 /usr/lib/perl/5.10.0/auto/SDBM_File/SDBM_File.so
miniserv. 2326 root    0r   CHR        1,3      0t0    1198 /dev/null
miniserv. 2326 root    1w   CHR        1,3      0t0    1198 /dev/null
miniserv. 2326 root    2w   REG        8,1    10080  545877 /var/webmin/miniserv.error
miniserv. 2326 root    3u  unix 0xf3c4f400      0t0    8056 socket
miniserv. 2326 root    4w   CHR        1,3      0t0    1198 /dev/null
miniserv. 2326 root    5u  IPv4       8102      0t0     TCP *:webmin (LISTEN)
miniserv. 2326 root    6u  IPv4       8103      0t0     UDP *:10000 
miniserv. 2326 root    7u   REG        8,1     1024  545881 /var/webmin/sessiondb.pag
miniserv. 2326 root    8u   REG        8,1        0  545882 /var/webmin/sessiondb.dir

```

> **cdenley said:**
> There are two things that would concern me? You have a samba server running. This is not the most secure file server, and shouldn't be accessible to the internet. How are you using it?

What concerns me more, though, is the perl script listening on port 10000.
```

sudo lsof -p 2326

```

Webmin perhaps? If so, it shouldn't be listening for any remote connections.

---

### Post by Simian Man on 2009-11-19
Do you have a cat?

---

### Post by whoop on 2009-11-19
> **Simian Man said:**
> Do you have a cat?

:lolflag: that made me laugh. But it's actually a good question...

---

### Post by cdenley on 2009-11-19
> **rg_stephens said:**
> 
```

COMMAND    PID USER   FD   TYPE     DEVICE SIZE/OFF    NODE NAME
miniserv. 2326 root  cwd    DIR        8,1    12288   29088 /usr/share/webmin

```

That perl script is definitely webmin, as I had suspected. I'm not very familiar with webmin or what password you need in order to use it. However, since it is listening for any connections, and you previously weren't using any firewall, someone could have very well guessed your password, then used webmin to control your system. Or maybe webmin rejects connections from internet IP's, I'm not sure.

I think samba may reject internet connections by default, so that may not be a concern.

---

### Post by rg_stephens on 2009-11-19
I don't think so, but maybe I should get a dog just to be safe. 

I'm going to re-install my system when I have the time, but I would like to know what's up.

> **Simian Man said:**
> Do you have a cat?

Cdenly, I thought that Firestarter was only to view your firewall, not to install it.

---

### Post by EJeanmaire on 2009-11-19
> **cdenley said:**
> That perl script is definitely webmin, as I had suspected. I'm not very familiar with webmin or what password you need in order to use it. However, since it is listening for any connections, and you previously weren't using any firewall, someone could have very well guessed your password, then used webmin to control your system. Or maybe webmin rejects connections from internet IP's, I'm not sure.

I think samba may reject internet connections by default, so that may not be a concern.


Webmin has quite a few known exploits in older versions.  Another issue I see is that you have msqld, and apache2 running, which you stated you aren't even using... Dangerous, especially with your potential lack of firewall restrictions.  There are a plethora of attacks on LAMP; it needs to be hardened and well updated.  Smbd also a risk if you don't have the ports blocked on your firewall... which leads me to wonder, if you aren't using a router, this seems like your only PC/Computer?  Then why are you running smbd (file sharing)? By the way, can you post your firewall rules for us?

---

### Post by EJeanmaire on 2009-11-19
> **rg_stephens said:**
> 


```

tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      2326/perl       

```

Thats webmin running right there on port 10000, you are right cdenley.

---

### Post by rg_stephens on 2009-11-19
At my old college dorm I would have suspected the cockroaches were playing Solatire.

I loaned my router to my parents, and I never bothered doing anything to the firewall. #-o Next month I'm getting married, so I'll have to buy a router for her computer. Money and time is tight...

I definately want file and print sharing. I used apache2 because it was an easy way to share files.  Can I uninstall mysql? Php? I'll be more careful with the firewall. 


> **EJeanmaire said:**
> Webmin has quite a few known exploits in older versions.  Another issue I see is that you have msqld, and apache2 running, which you stated you aren't even using... Dangerous, especially with your potential lack of firewall restrictions.  There are a plethora of attacks on LAMP; it needs to be hardened and well updated.  Smbd also a risk if you don't have the ports blocked on your firewall... which leads me to wonder, if you aren't using a router, this seems like your only PC/Computer?  Then why are you running smbd (file sharing)? By the way, can you post your firewall rules for us?

---

### Post by cdenley on 2009-11-19
Mysql isn't a concern because it is only listening on 127.0.0.1. Nobody can connect remotely. I missed apache2, but I doubt that is related to your current issue, and should be safe unless you're hosting an easily exploitable script. If you don't use it, or are unsure it is configured properly, I would remove it.

Firestarter both configures your firewall (iptables) and logs rejected packets. It is a dead project, and I wouldn't recommend using it.

---

### Post by doas777 on 2009-11-19
gufw is the new "kewl tool" for iptables managment, though it is clumbsy, cumbersome, inefficient, generally annoying, and does not present any of the monitoring or logging features that firestarter does.

still, everyone will recommend you use it.

---

### Post by rg_stephens on 2009-11-19
I haven't set up any firewall rules. In firestarter, this option is greyed-out.

I set up webmin for some reason, but I couldn't figure it out. I guess I should not install things I don't understand. For now I'll just keep my internet connection locked when not in use.

> **doas777 said:**
> gufw is the new "kewl tool" for iptables managment, though it is clumbsy, cumbersome, inefficient, generally annoying, and does not present any of the monitoring or logging features that firestarter does.

still, everyone will recommend you use it.

---

### Post by skillllllz on 2009-11-19
I've scanned the IP you PM'd me using several different methods. It appears to be offline, either that or all ports are in stealth mode and the host is not responding to echo requests.

---

### Post by doas777 on 2009-11-19
> **rg_stephens said:**
> I haven't set up any firewall rules. In firestarter, this option is greyed-out.

I set up webmin for some reason, but I couldn't figure it out. I guess I should not install things I don't understand. For now I'll just keep my internet connection locked when not in use.

are you running it with gksu? iptables alteration requires root, so firestarter is useless if run as a normal user.

---

