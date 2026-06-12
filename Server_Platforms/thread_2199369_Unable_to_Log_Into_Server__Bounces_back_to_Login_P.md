---
title: "Unable to Log Into Server / Bounces back to Login Prompt"
date: 2014-01-13
forum: Server Platforms
---

### Post by lingpanda on 2014-01-13
So I reboot the server using SSH via Putty. Attempt to log back in using putty and am greeted with an error "Server unexpectedly closed network connection". So I go to the server room and attempt login. However upon entering the user name and hitting enter I'm immediately brought back to the user name field with a brief screen flash. Any ideas? Using Ubuntu 12.04.4. Thanks.

---

### Post by steeldriver on 2014-01-13
... something nasty in your .bashrc or .profile? have you tried connecting via putty with remote command /bin/bash --norc --noprofile?

---

### Post by lingpanda on 2014-01-13
> **steeldriver said:**
> ... something nasty in your .bashrc or .profile? have you tried connecting via putty with remote command /bin/bash --norc --noprofile?

I'm away from the machine at the moment but I believe an incorrect library was installed on this server which caused this issue. If memory servers me the package libpam-krb was installed and should not have. I booted to the recovery console and looked at the last commands run. I tried to purge it but it complained of access. Don't recall the correct verbiage at the moment.

---

### Post by lingpanda on 2014-01-14
So I solved my issue by booting to recovery mode and choosing the fsck option. This allowed read write mode. I then removed the last package installed and was able to log in.

---

