---
title: "How to figure out used pam security"
date: 2011-11-12
forum: Server Platforms
---

### Post by boetzie on 2011-11-12
Hi guys, 
A collegua of mine configured a ubuntu 10.10 webserver for me. I'm kind of new to linux but my knowledge is getting there. 

WHen i login throught ssh everything is ok and i have acces to the ssh of the server. I created a new user to to server, assigned him a ssh private key and everything should work. 
Now when i try to login on the server with the new user he isn't acces. So i'm checking the security in my sshd_config and i see that UsePam=Yes, i've been doing a lot of reading and checking the pam config files but i can't see to find where the extra security is to allow or disallow users form login in. 

Anyone any tips on pointing me in the right direction? Thnx

---

### Post by Dangertux on 2011-11-12
> **boetzie said:**
> Hi guys, 
A collegua of mine configured a ubuntu 10.10 webserver for me. I'm kind of new to linux but my knowledge is getting there. 

WHen i login throught ssh everything is ok and i have acces to the ssh of the server. I created a new user to to server, assigned him a ssh private key and everything should work. 
Now when i try to login on the server with the new user he isn't acces. So i'm checking the security in my sshd_config and i see that UsePam=Yes, i've been doing a lot of reading and checking the pam config files but i can't see to find where the extra security is to allow or disallow users form login in. 

Anyone any tips on pointing me in the right direction? Thnx

If you look in /etc/pam.d/sshd 

there is probably a line that looks something like this

```

auth required pam_listfile.so item=user sense=allow file=/etc/sshd/sshd.allow onerr=fail

```

you see where it says file=/etc/sshd/sshd.allow. That is the allowed list of usernames. Check the file to make sure its in the same location if it is not use the location actually referred to in your /etc/pam.d/sshd file, add the user you wish to be able to login to the file listed above and restart ssh server

```

sudo /etc/init.d/ssh restart

```

your new user should be able to log in.

---

### Post by boetzie on 2011-11-12
Thanx for the reply, 
I find that command as well but when i check the sshd file i can't find anything in there wich pointed to the pam_listfile.

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

Could it be that there is some other way to block the user? Thnx for your help

---

### Post by boetzie on 2011-11-12
Ok i figured it out, the problem was not the pam restriction but there went something wrong with the .ssh settings .. the user couldn't acces his own public key. solved that problem.

I'm going to limit the the sshd acces by pam anyway because it was not enabled thnx the help !

---

### Post by Dangertux on 2011-11-12
Sorry I didn't get back to you sooner, I was away from my computer, I was going to suggest check your public keys. 

I'm glad it all worked out for you.

---

### Post by boetzie on 2011-11-12
No worries i think your replies are preTty damn quick  thnx a lot !!

---

