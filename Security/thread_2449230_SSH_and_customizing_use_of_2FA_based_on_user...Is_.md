---
title: "SSH and customizing use of 2FA based on user...Is this possible?"
date: 2020-08-22
forum: Security
---

### Post by kevdog on 2020-08-22
Based on the recently exploits of ssh as discussed on ArsTechnica [https://arstechnica.com/information-technology/2020/08/new-p2p-botnet-infects-ssh-servers-all-over-the-world/](https://arstechnica.com/information-technology/2020/08/new-p2p-botnet-infects-ssh-servers-all-over-the-world/), I went ahead on a few test machines and install ssh keybased logins coupled with a mandatory 2FA via use of Duo (Google Authenticator could have also been chosen).  This 2FA mechanism works in conjuction with PAM authentication to authenticate the user based on username, ssh key and 2FA mechanism.  I don't know a ton about PAM and authentication however was wondering if there was a way to setup 2FA/PAM for selected users/groups rather than just globally as I currently have now.

---

### Post by EuclideanCoffee on 2020-08-22
That's a great question.

Did you see this answer? [https://serverfault.com/questions/222637/sshd-how-to-enable-pam-authentication-for-specific-users-under](https://serverfault.com/questions/222637/sshd-how-to-enable-pam-authentication-for-specific-users-under)

There are three really good answers I recommend testing. Report back your findings.

---

