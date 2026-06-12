---
title: "Firejail - Thunderbird &quot;Unable to locate mail spool file&quot;- /var/mail access"
date: 2018-02-16
forum: Security
---

### Post by nerderello2 on 2018-02-16
Hi,
I want to use firejail with Thunderbird, and use Thunderbird to access my local mail as well as Internet based servers. 
If I use the "/etc/firejail/thunderbird.profile" it blacklists /var/mail, and I get the popup in Thunderbird "Unable to locate mail spool file".
If I create a "~/.config/firejail/thunderbird.profile", it works, but it ignores all of the goodies in "/etc/firejail/thunderbird.profile", and if I do an "include" of that profile, well, I'm back where I started.
If I put a "noblacklist /var/mail/userid" into the .config profile (where "userid" is my userid) and do the include as well, I get "TESTING warning: noblacklist /var/mail/ not matched by a proper blacklist command in disable*.inc".

Anybody got any ideas on how to get around this?

thanks
Nerderello

---

### Post by &amp;KyT$0P# on 2018-02-16
Does it work to use this as [FONT=Courier New]~/.config/firejail/thunderbird.profile[/FONT] ? -
```
noblacklist /var/mail
noblacklist /var/mail/userid
blacklist /var/mail/*
include /etc/firejail/thunderbird.profile

```

---

### Post by nerderello2 on 2018-02-16
Hi Halogen2,
many thanks for your reply. It didn;t work, but it did point me what I was doing wrong.

What it was complaining about was a not needed "/"!

I had added "noblacklist /var/mail/" , but when (after reading your post) I changed this to "noblacklist /var/mail" it worked!
I now have this in my ~/.config/firejail/thunderbird.profile  
 
> 
noblacklist /var/mail
whitelist /var/mail/userid
writable-var
include /etc/firejail/thunderbird.profile


Thanks again
Nerderello

---

