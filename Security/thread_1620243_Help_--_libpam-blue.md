---
title: "Help -- libpam-blue"
date: 2010-11-12
forum: Security
---

### Post by mathgeek2000 on 2010-11-12
I need some help getting PAM bluetooth working. I'm trying to set it up with my Cell Phone, but it's not working. -- My /etc/security/bluescan.conf file first:

```

general {
    timeout = 3;
}

demo = {
 name = SCH;
 bluemac = 44:F4:59:03:E1:A9;
 timeout = 60;
}

```

Demo is an account I created, without an encrypted home. -- As my own account has an encrypted home. I'm testing with just the /etc/pam.d/login and trying to login via bluetooth authentication:

```

# Standard Un*x authentication.
auth sufficient pam_blue.so 
@include common-auth

```

If the line: 'auth sufficient pam_blue.so' is placed where it is, (above common-auth in the original file) the user is immediately prompted for the password. If the word sufficient is changed to required, the user can't log in.

Any ideas, an RFCOMM channel setting, or another location to put the pam_blue.so line?

---

