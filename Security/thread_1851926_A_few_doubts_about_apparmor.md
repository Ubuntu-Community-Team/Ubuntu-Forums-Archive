---
title: "A few doubts about apparmor"
date: 2011-09-29
forum: Security
---

### Post by arroy_0209 on 2011-09-29
1. I am yet to understand how to recognize apparmor-generated warnings from message log-file. e.g., is the following in anyway related to apparmor?
> xyz-desktop kernel: [....] __ratelimit: 99 callbacks suppressed
or should I only rely on result of sudo aa-logprof? So far I have not got any relevant result out of that. The only result had been:
> 
Reading log entries from /var/log/messages.
Updating AppArmor profiles in /etc/apparmor.d.
2. When does one realize that one should change apparmor from complain mode to enforce mode?

---

### Post by Porcini M. on 2011-09-29
1. Search for "audit" in the message log file

2. When you are no longer getting any apparmor errors after regular use of the application.

3. That's a logged packet.

---

### Post by arroy_0209 on 2011-09-29
I notice that if I keep apparmor in complain mode (for firefox profile), it works for that session only. If I restart the machine, and check for apparmor_status, apparmor(firefox) is found no longer to be in complain mode. I have to repeat the commands again to set apparmor(firefox) in complain mode. Is it expected or am I doing something wrong?

---

### Post by Porcini M. on 2011-09-29
> **arroy_0209 said:**
> I notice that if I keep apparmor in complain mode (for firefox profile), it works for that session only. If I restart the machine, and check for apparmor_status, apparmor(firefox) is found no longer to be in complain mode. I have to repeat the commands again to set apparmor(firefox) in complain mode. Is it expected or am I doing something wrong?

How do you set it to complain mode? I write it directly in the profile, like:

```

/usr/share/subsonic/subsonic.sh flags=(complain) {
# /usr/share/subsonic/subsonic.sh {

```

...then, when I'm ready to switch it to enforce mode, I just comment out the top & uncomment the bottom, save, then reload profiles.

---

### Post by arroy_0209 on 2011-09-29
Thanks for your reply. I use these commands (as given at many places):
```

sudo apparmor_status
sudo aa-copmplain /etc/apparmor.d/usr.bin.firefox
sudo apparmor_parser -r /etc/apparmor.d/usr.bin.firefox 
sudo apparmor_status /etc/apparmor.d/usr.bin.firefox 
sudo aa-logprof /etc/apparmor.d/usr.bin.firefox 

```is this method not enough to keep firefox profile in complain mode foreever (or until I change myself)?

---

### Post by Porcini M. on 2011-09-29
I don't know, I've never used aa-complain...

---

