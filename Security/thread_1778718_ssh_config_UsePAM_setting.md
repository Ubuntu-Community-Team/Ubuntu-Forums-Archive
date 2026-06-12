---
title: "ssh_config UsePAM setting"
date: 2011-06-09
forum: Security
---

### Post by krumpy on 2011-06-09
I use keyed authetication for ssh.  It seems to work fine.  For example if I try to login as a random user I get the message "Permission denied (publickey)"  But I was looking through an article on secure passwordless ssh and they recommended setting UsePam to No (Currently I have it set to yes, which I believe was the default).  The ssh_config file is kind of confusing on the issue as this is note above UsePam:

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.

To me it seems like even if UsePAM is set to yes as long as PasswordAuthentication and ChallengeResponseAuthentication are set to no users must have a key to login?  Could someone please clarify as I don't want to leave any sort of password login active and only allow keyed authentication.

---

