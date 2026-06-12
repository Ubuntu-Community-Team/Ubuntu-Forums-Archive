---
title: "Lock Network Settings Only"
date: 2012-08-20
forum: Security
---

### Post by doulos05 on 2012-08-20
Ok, I have a Ubuntu 12.04 system that has a single user. I need to lock the Network settings, specifically the dns settings, from being changed by user while still allowing them all other root permissions. I'm setting up OpenDNS on this for the content blocking and don't want to be able to change the dns settings once they're set. I want to set it on the computer rather than the router because it is a laptop and don't want to be able to just carry it off in search of wifi to bypass the filtering. Is this possible?

I realize I'll need to create a separate administrator account with full root access that they don't have the password to, that's fine. It looks like the sudoers file is what I need to change but I'm not sure exactly what what settings to use and man sudo is written in an arcane form of geek I'm not quite familiar with. My initial google searches revealed a single web page that hinted that it could be done, but didn't really tell me how to do it, but my google-fu could be weak. Any suggestions?

---

### Post by Ms. Daisy on 2012-08-20
If the user has all other root privileges, what's stopping him from becoming root and doing whatever he wants? You would have to restrict what root could do (which would be ridiculous and probably impossible).

```
limiteduser@ubuntu:~$ sudo su
Password:
root@ubuntu:# 
```Now he can do whatever he wants to the dns settings.

---

### Post by CharlesA on 2012-08-20
What Ms. Daisy said.

Physical access = root access and if they *really* wanted to bypass OpenDNS, they would boot a livecd and mess with the DNS settings that way.

---

### Post by doulos05 on 2012-08-20
I know that this isn't going to be a fool-proof barrier. I'm just trying to add as much extra work between 'filtered' and 'unfiltered' as possible. Can it be done or not?

---

### Post by CharlesA on 2012-08-20
Not with giving someone sudo rights.

Just give them limited rights.

---

