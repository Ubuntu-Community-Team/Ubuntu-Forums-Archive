---
title: "LTSP Setup"
date: 2007-05-15
forum: Server Platforms
---

### Post by ghosting0 on 2007-05-15
I wonder if someone could assist me. I have attempted to setup LTSP on my Ubuntu 7.04 server but have been unsuccessful. I closely followed the steps detailed in [https://help.ubuntu.com/community/ThinClientHowto]("https://help.ubuntu.com/community/ThinClientHowto"). Upon booting the client I recieve the following error: PXE-E32: TFTP open timeout

I am brand new to Ubuntu and server setup in general so any assistance would be greatly appreciated. I have searched for related material but so far have had no luck. Thanks in advance.

---

### Post by lossie on 2007-06-05
I'm having the same PXE problem. But it worked yesterday and now it doens't anymore. I tried installing vmware and in doing so i must have unwillingly tampered with the LTSP setting. Is there ANYway of getting the settings back to there defaults? I can't find any referencesof tftp in inetd.conf or xinetd.conf. Something must start this baby up.

---

### Post by lossie on 2007-06-05
I kinda fixed the problem, but it is not the way to do it. It may however help you in finding the real sollution.
Try runnin tftpd-hpa as a daemon.
```
vi /etc/default/tftpd-hpa

change ==> RUN_DAEMON="yes"

/etc/init.d/tftpd-hpa start
```

Now it works, but there must be a reason why inetd or xinetd isn't configured to do this. I'll let you know if i find somthing of use.

---

