---
title: "Ubuntu OS hardening (version 14.0.4.3)"
date: 2017-02-08
forum: Security
---

### Post by makauser on 2017-02-08
Dear Concern,

We want to implement following OS hardening feature in below version in Ubuntu. Request to share us necessary plan.

amirislam@blnidapp03:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:        14.04
Codename:       trusty


 1. Account lock for 30 minutes for 5 failure attempts.
 2. Password complexity (Min Length=8, upper-case=1, lower-case=1, digit=1, non-alphanumeric=1).
 3. Password history (remember last 5 passwords).
 4. Password expiration day settings change (PASS_MAX_DAYS 90, PASS_MIN_DAYS 0, PASS_MIN_LEN 8, PASS_WARN_AGE 7).
 5. Session timeout after 5 minutes.
 6. Disable unnecessary services.
 7. Enable Individual Administrator user’s Login & SUDO Privilege.
 8. Enable the terminal security file to restrict root logins to system console.
 9. Disable "root" login for SSH.
 10. List of redundant and orphaned files/directories from Systems & Remove them.
 11. Enable UMASK value to 0022 or 0002 in global profile file.

With Best Regards,
Md. Abdullah-Al Kauser

---

### Post by deadflowr on 2017-02-08
*Thread moved to **Security**.*

---

### Post by QIII on 2017-02-08
Hello!

You have given a long list of requests.  This sort of post is very difficult and confusing to answer, both for you and for those who would like to help.

First, I suggest you read the material [here]("https://help.ubuntu.com/community/Security").

Then, if you have questions, please start one new thread for each subject you would like help with.  One subject/One thread is far easier. Please feel free to start new threads.  This one will likely be closed if it becomes too tangled.

And welcome to the forums!

---

### Post by ajgreeny on 2017-02-09
Your **Ubuntu 14.04.3 LTS** output seems to suggest you may be using a point release that has not been updated to the full extent; have you made sure that your hardware enablement software stack is fully  up to date, for example what kernel are you currently using?

If that is not done security could be compromised by the fact that you are still using unsupported software package versions.

See [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) for full info on this.

---

### Post by TheFu on 2017-02-09
Actually, **14.04.3 support has ended already**.
[https://www.ubuntu.com/info/release-end-of-life](https://www.ubuntu.com/info/release-end-of-life) - scroll to the bottom to see.
Only these three versions get support through to 2019.
14.04.0
14.04.1
14.04.5

At this point, I'd migrate to 14.04.5 as the first step.
Most of the answers to these questions are part of beginning-level Linux administration training.  Some of the non-standard password controls will require additional packages to achieve.  npasswd is one option. There are commercials tools for this too, but I've never set those up. 8 characters is nowhere near enough for a secure password these days, BTW.  16+ is really the new standard.  I've seen professional password teams brute force every possible password that is 13 characters and less in 26 hrs. That was a few years ago.  I use 20 characters as my minimum and normally use 45-90 characters for all everything that allows it where a password manager is possible.   

The sudo stuff is pretty basic for any qualified admin.

---

