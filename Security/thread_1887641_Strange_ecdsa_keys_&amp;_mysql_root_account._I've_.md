---
title: "Strange ecdsa keys &amp; mysql root account. I've probably been hacked."
date: 2011-11-27
forum: Security
---

### Post by Naranek on 2011-11-27
Today I noticed a strange user in my MySQL database. There was a root account with the hostname cardamom. I didn't recall making such an account and the host doesn't ring a bell.

So I grepped for cardamon and sure enough I found a **ecdsa-sha2-nistp256** public key for **root@cardamom** in the /etc/ssh folder. There was also a private key to go with that. When I checked the timestamps, they were created at the same time AND sshd_config was modified at the same time as well - probably to enable the ecdsa keys. The timestamp for the files was 2011-04-26 at about 3:15-3:30, four months **before **the system was installed.

After more digging I found a entry in my known_hosts file for the said key. The beginning of the row is: ```
|1|EqOUwm4eNXKDGTm9oDhjvwlw4T4=|lW4XLS7gV1nCC7sR48k+y6tesjo=
```

Does anyone have any idea if there's any way this could be normal, or has my computer simply been hacked? I've already switched it off and I'm planning on full wipe and reinstall, but before that I'd like to know what exactly has been compromised. 

Do you have any ideas about attacks using ecdsa keys? Is there some automated exploit package that fits the description, or has someone actually gone through the trouble of hacking my box? Any pointers what to do next?

---

### Post by OpSecShellshock on 2011-11-27
It's hard to say without knowing much about the nature of the server where the database resides. My best guess from the description is that a vulnerable web application was in use on the server and was available from the open web. If there was some sort of input validation flaw, then the web application could have been made to execute code with the necessary permissions to grab the attacker's configuration files (which were last modified prior to the installation of the server itself, but it doesn't matter except as a nice clue left behind for you!) and place them in the appropriate directories. After that the attacker's keys would be recognized and access would be persistent. Such attacks are largely automated. Mind you this is just a guess. Without knowing what the server is for, how it's set up, and what applications it's running or serving it would be hard to say for sure.

Nothing on it can probably be trusted at this point. Wiping and re-installing is the way to go.

---

### Post by Naranek on 2012-03-12
I just got a reply from ubuntu security. It seems to be a bug in the 11.04 iso. Cardamom and kapok are build servers. It would appear the 11.04 Mythbuntu .iso installs the livecd SSH host key by mistake when installing a system. Mysql root user is also used in the livecd.

Would have been nice to know this before I wiped my system though... :roll:

---

### Post by Ms. Daisy on 2012-03-12
> **Naranek said:**
> I just got a reply from ubuntu security. It seems to be a bug in the 11.04 iso. Cardamom and kapok are build servers. It would appear the 11.04 Mythbuntu .iso installs the livecd SSH host key by mistake when installing a system. Mysql root user is also used in the livecd. 
What?!? A bug? 
 
So when you reinstalled was the same thing present?

---

### Post by Naranek on 2012-03-13
> **Ms. Daisy said:**
> What?!? A bug? 
 
So when you reinstalled was the same thing present?

Indeed it was, though I noticed it a few months after installing. That's why I started to investigate this further. It was too scary to think that my freshly installed box would be hacked again so soon.

---

