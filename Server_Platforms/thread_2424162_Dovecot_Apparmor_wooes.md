---
title: "Dovecot Apparmor wooes"
date: 2019-08-04
forum: Server Platforms
---

### Post by beowulf222 on 2019-08-04
Hello,

Running dovecot 2.2.33.2 on Ubuntu 18.04.2 LTS and am stuck on a few error messages popping up in the kernel.log. Dovecot works, so nothing is broken, but I'd like to understand what the problem is.

```
Aug  4 17:06:07 ubutuserver kernel: [3833607.754343] audit: type=1400 audit(1564909567.789:3883552): apparmor="ALLOWED" operation="file_perm" profile="/usr/lib/dovecot/anvil" name="/run/dovecot/anvil-auth-penalty" pid=240241 comm="anvil" requested_mask="w" denied_mask="w" fsuid=112 ouid=0
Aug  4 17:06:07 ubutuserver kernel: [3833607.754349] audit: type=1400 audit(1564909567.789:3883553): apparmor="ALLOWED" operation="file_perm" profile="/usr/lib/dovecot/anvil" name="/run/dovecot/anvil-auth-penalty" pid=240241 comm="anvil" requested_mask="w" denied_mask="w" fsuid=112 ouid=0
Aug  4 17:06:12 ubutuserver kernel: [3833612.495335] audit: type=1400 audit(1564909572.533:3883554): apparmor="ALLOWED" operation="open" profile="/usr/lib/dovecot/imap" name="/home/USER/.imap/.imap/INBOX/dovecot.index.log" pid=180593 comm="imap" requested_mask="ra" denied_mask="ra" fsuid=1001 ouid=1001
Aug  4 17:06:12 ubutuserver kernel: [3833612.495815] audit: type=1400 audit(1564909572.533:3883555): apparmor="ALLOWED" operation="open" profile="/usr/lib/dovecot/imap" name="/home/USER/.imap/.imap/INBOX/dovecot.index" pid=180593 comm="imap" requested_mask="wr" denied_mask="wr" fsuid=1001 ouid=1001
Aug  4 17:06:12 ubutuserver kernel: [3833612.497388] audit: type=1400 audit(1564909572.533:3883556): apparmor="ALLOWED" operation="file_lock" profile="/usr/lib/dovecot/imap" name="/home/USER/.imap/.imap/INBOX/dovecot.index.log" pid=180593 comm="imap" requested_mask="wk" denied_mask="wk" fsuid=1001 ouid=1001
Aug  4 17:08:08 ubutuserver kernel: [3833728.431542] audit: type=1400 audit(1564909688.470:3883557): apparmor="ALLOWED" operation="open" profile="/usr/lib/dovecot/imap" name="/home/USER/.imap/.imap/Junk-E-Mail/dovecot.index.log" pid=180591 comm="imap" requested_mask="ra" denied_mask="ra" fsuid=1001 ouid=1001
Aug  4 17:08:08 ubutuserver kernel: [3833728.433133] audit: type=1400 audit(1564909688.470:3883558): apparmor="ALLOWED" operation="file_lock" profile="/usr/lib/dovecot/imap" name="/home/USER/.imap/.imap/Junk-E-Mail/dovecot.index.log" pid=180591 comm="imap" requested_mask="wk" denied_mask="wk" fsuid=1001 ouid=1001
Aug  4 17:08:33 ubutuserver kernel: [3833753.791800] audit: type=1400 audit(1564909713.830:3883559): apparmor="ALLOWED" operation="open" profile="/usr/lib/dovecot/imap" name="/home/USER/.imap/.imap/Drafts/dovecot.index.log" pid=180602 comm="imap" requested_mask="ra" denied_mask="ra" fsuid=1001 ouid=1001
Aug  4 17:08:33 ubutuserver kernel: [3833753.793021] audit: type=1400 audit(1564909713.830:3883560): apparmor="ALLOWED" operation="open" profile="/usr/lib/dovecot/imap" name="/home/USER/.imap/.imap/Drafts/dovecot.index" pid=180602 comm="imap" requested_mask="wr" denied_mask="wr" fsuid=1001 ouid=1001
Aug  4 17:08:33 ubutuserver kernel: [3833753.793881] audit: type=1400 audit(1564909713.830:3883561): apparmor="ALLOWED" operation="file_lock" profile="/usr/lib/dovecot/imap" name="/home/USER/.imap/.imap/Drafts/dovecot.index.log" pid=180602 comm="imap" requested_mask="wk" denied_mask="wk" fsuid=1001 ouid=1001
Aug  4 17:08:35 ubutuserver kernel: [3833755.644217] audit: type=1400 audit(1564909715.682:3883562): apparmor="ALLOWED" operation="open" profile="/usr/lib/dovecot/imap" name="/home/USER/.imap/.imap/Junk-E-Mail/dovecot.index.log" pid=180604 comm="imap" requested_mask="ra" denied_mask="ra" fsuid=1001 ouid=1001
Aug  4 17:08:35 ubutuserver kernel: [3833755.644966] audit: type=1400 audit(1564909715.682:3883563): apparmor="ALLOWED" operation="file_lock" profile="/usr/lib/dovecot/imap" name="/home/USER/.imap/.imap/Junk-E-Mail/dovecot.index.log" pid=180604 comm="imap" requested_mask="wk" denied_mask="wk" fsuid=1001 ouid=100
```

I suspected it being related to apparmor and tweaked the usr.lib.dovecot.imap profile under /etc/apparmor.d/local to include some of the items

```
/usr/sbin/dovecot flags=(complain,attach_disconnected) {

/home/USER/.imap/.imap/INBOX/dovecot.index rw,
/home/USER/.imap/.imap/Drafts/dovecot.index ra,
/home/USER/.imap/.imap/Drafts/dovecot.index.log ra,
/home/USER/.imap/.imap/Junk-E-Mail/dovecot.index ra,
/home/USER/.imap/.imap/Junk-E-Mail/dovecot.index.log ra,

/home/USER/.imap/.subscriptions r,
}
```

Well, that worked partly. I then got messages of the below sort flooding the kernel.log

```
 1 Time(s): audit: type=1400 audit(1564156802.229:3664150): apparmor="ALLOWED" operation="setsockopt" profile="/usr/sbin/dovecot//null-/usr/lib/dovecot/imap-login" pid=18604 comm="imap-login" laddr=192.168.1.1 lport=993 faddr=ADDRESS fport=61269 family="inet" sock_type="stream" protocol=6 requested_mask="setopt" denied_mask="setopt"
```

Does anyone have any pointers on the cause of the issue and how to fix it?

-- nick

---

