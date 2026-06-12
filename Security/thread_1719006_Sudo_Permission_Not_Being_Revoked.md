---
title: "Sudo Permission Not Being Revoked"
date: 2011-04-01
forum: Security
---

### Post by Astrals on 2011-04-01
I am using Ubuntu 10.04-alternate-amd64 for full disk encryption.

After getting my updates which i get as soon as they are released.
I am getting the **issue temp root (sudo)  password is not being revoked.**
After using any app that requires the use of sudo the permission for it does not get removed like it normally does.
I have tried logging out then back in, which usually removes the permission, this no longer works, also tried waiting and even after 1 hour permission still there.
The only work around I have found is to use the terminal to execute the required programs then after closing terminal the temp permission is now removed like it should be.
This issue has effected all of my systems and a friend of mine as well, (friend uses same distro).

To replicate issue:
1) Boot system.
2) Login.
3) Check for updates or any other app that uses root permission.
4) Logout
5) Login
6) Repeat step 3
7) App will not ask for permission it will use root permission automatically.

I hope this is enough information as I have not had to post many issues.
I hope this is the right section to post this, if not sorry.

Any help with this will be greatly appreciated, thank you in advance.

---

### Post by bodhi.zazen on 2011-04-01
Did you edit /etc/sudoers ?

visudo ?

Post the content of /etc/sudoers ;)

---

### Post by Astrals on 2011-04-01
I filed a bug report on this security issue.

Adding this fixed my issue.
This is from a reply from my launchpad account:

[https://help.ubuntu.com/community/RootSudo#Usage](https://help.ubuntu.com/community/RootSudo#Usage) If there isn't a line already for timestamp in sudoers, one could add a line at the end, example:
# Set timeout to zero. Default is 15.
Defaults timestamp_timeout = 0
 ## Note: the last line of sudoers always must remain empty.
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)
[U]
[/U]
_Hope this helps_.

---

### Post by tgm4883 on 2011-04-02
> **Astrals said:**
> I filed a bug report on this security issue.

Adding this fixed my issue.
This is from a reply from my launchpad account:

[https://help.ubuntu.com/community/RootSudo#Usage](https://help.ubuntu.com/community/RootSudo#Usage) If there isn't a line already for timestamp in sudoers, one could add a line at the end, example:
# Set timeout to zero. Default is 15.
Defaults timestamp_timeout = 0
 ## Note: the last line of sudoers always must remain empty.
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)
[U]
[/U]
_Hope this helps_.

Link to bug?

That would be a workaround not a fix. The default timeout is set to 15 minutes. You are just turning off the timeout. 

The bug though it would seem is that you would expect sudo to be revoked on a logout.

---

