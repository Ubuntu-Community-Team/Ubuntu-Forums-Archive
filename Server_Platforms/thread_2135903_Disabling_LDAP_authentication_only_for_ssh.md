---
title: "Disabling LDAP authentication only for ssh"
date: 2013-04-15
forum: Server Platforms
---

### Post by sdmike6 on 2013-04-15
I'm running ubuntu server 12.04 x64.

I have a server that is running Samba and this server authenticates users against Open LDAP.

I need to disable LDAP authentication for SSH but I'm not seeing a way to do this.

Does anyone know how to do this on Precise?

---

### Post by SeijiSensei on 2013-04-16
You can define service-specific authentication methods by [creating a file]("http://manpages.ubuntu.com/manpages/intrepid/man5/pam.conf.5.html") in /etc/pam.d/.  I've not done this on an Ubuntu server, but that man page and the existing files in pam.d/ might be enough to get you started.  Essentially you'd want to create a file called "ssh" (or perhaps "sshd" if plain "ssh" doesn't work) that tells PAM to use the password file rather than LDAP.

---

### Post by sdmike6 on 2013-04-25
This file was already in pam.d for sshd:

I'm still not quite sure what I need to do in order to turn LDAP authentication off for ssh access.

```
# PAM configuration for the Secure Shell service


# Read environment variables from /etc/environment and
# /etc/security/pam_env.conf.
auth       required     pam_env.so # [1]
# In Debian 4.0 (etch), locale-related environment variables were moved to
# /etc/default/locale, so read that as well.
auth       required     pam_env.so envfile=/etc/default/locale


# Standard Un*x authentication.
@include common-auth


# Disallow non-root logins when /etc/nologin exists.
account    required     pam_nologin.so


# Uncomment and edit /etc/security/access.conf if you need to set complex
# access limits that are hard to express in sshd_config.
# account  required     pam_access.so


# Standard Un*x authorization.
@include common-account


# Standard Un*x session setup and teardown.
@include common-session


# Print the message of the day upon successful login.
session    optional     pam_motd.so # [1]


# Print the status of the user's mailbox upon successful login.
session    optional     pam_mail.so standard noenv # [1]


# Set up user limits from /etc/security/limits.conf.
session    required     pam_limits.so


# Set up SELinux capabilities (need modified pam)
# session  required     pam_selinux.so multiple


# Standard Un*x password updating.
@include common-password
```

---

### Post by sdmike6 on 2013-05-02
I no longer have to do this because I was having an issue with a chef cookbook.

---

