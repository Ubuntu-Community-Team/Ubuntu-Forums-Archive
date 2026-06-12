---
title: "pam_tally2 excessive logins"
date: 2016-07-27
forum: Server Platforms
---

### Post by sorted78 on 2016-07-27
hi, i am using pam pam_tally.so to limit excessive logins and I noticed that Ubuntu doesn't have the fail_interval available like RHEL does. 

my configuration is pretty standard but was wondering if there is debian/ubuntu solution via pam to specify a time frame for excessive logins? i.e "lock account is login more than 10 logins fail during a 10 minute window" 

auth        required      pam_tally2.so  file=/var/log/tallylog deny=10 even_deny_root 
auth    [success=1 default=ignore]      pam_unix.so nullok_secure

---

### Post by rounder8 on 2016-07-27
I have been trying to figure out how to get pam_tally2 (or even the first version) working on Ubuntu. It seems that you have got it working already but without the specified time window for login attempts. That's not too bad, even if it's not perfect. Can you be a bit more detailed about what you have done so far? In which file / files did you add those lines? In which position? I've read something (about pam_tally, first version actually) that the order of the commands matter so it would be nice if you could specify exact location in file where you put those lines in.

Edit: Nevermind, i figured it out. Just add on top of /etc/pam.d/common-auth the line:

auth required pam_tally2.so file=/var/log/tallylog deny=10 even_deny_root 

Now i need to figure out how to make this work with GUI login manager as well...

[COLOR=#000000]

[/COLOR]

---

