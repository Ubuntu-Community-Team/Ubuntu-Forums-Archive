---
title: "Installing mail server for 14.04, hit snag with Dovecot"
date: 2014-12-30
forum: Server Platforms
---

### Post by vanusk2 on 2014-12-30
Alright so I'm trying to install a mail server on Ubuntu 14.04 and I was following the guides for doing so when I got to this section: 
```
Make Dovecot listen for authentication requests[/h]In /etc/dovecot/dovecot.conf edit the auth section to:
auth default {
  mechanisms = plain cram-md5
  passdb passwd-file {
    args = /etc/dovecot/passwd
  }
  userdb passwd-file {
    args = /etc/dovecot/users
  }
  user = root
  socket listen {
    client {
      # The client socket is generally safe to export to everyone. Typical use
      # is to export it to your SMTP server so it can do SMTP AUTH lookups
      # using it.
      path = /var/spool/postfix/private/auth-client
      mode = 0660
      user = postfix
      group = postfix
    }
  }
}
Note: Code above needs an update for versions 12.04 and after. Dovecot packed with those systems does'nt work with these settings anymore.
```

So, yeah. Anyone have any advice on how to proceed?

---

### Post by MAFoElffen on 2014-12-30
Welcome to Ubuntu Forums!

I'm sure a Moderator will be along soon to move this thread to the Server section. Once moved there, this can get some exposure in that section, where someone could help you with this.

I have experience with Server Edition and with sSMTP, but not specifically with Dovecot.

---

### Post by lisati on 2014-12-31
*Thread moved to **Server Platforms**.*

---

### Post by vanusk2 on 2014-12-31
Sorry about posting in the wrong section - My bad.

---

### Post by nerdtron on 2015-01-01
Just passing by.. If you would like to quickly have a working mail server iredmail is certainly an option.
[http://iredmail.org/](http://iredmail.org/)
Install on a fresh vm of ubuntu for testing: [http://iredmail.org/docs/install.iredmail.on.debian.ubuntu.html](http://iredmail.org/docs/install.iredmail.on.debian.ubuntu.html)

It a complete suite, but If you want to study and install your own from scratch, then you can look at the config files used by iredmail and see how they work together.

---

### Post by vanusk2 on 2015-01-02
I might look into this as an alternative - Is it capable of having web a portal for multiple accounts/ checking the mailboxes and sending mail?

---

### Post by nerdtron on 2015-01-02
Yup it has a webmail (Roundcube), with another web panel for administering mail domains and email accounts (iRedadmin). Installation also comes with a spamassassin, clamAV anti virus and fail2ban for security. And I found their developer quite active answering questions on the forums.

---

### Post by vanusk2 on 2015-01-03
Since I'm not exactly an expert on Ubuntu systems yet, how would I undo the setup of the dovecot/ Postfix? When I installed dovecot, it uninstalled the pop3/ imap packages I'd installed for a previous step in the guide and replaced them with its own. Does iredmail do something similar?

---

### Post by nerdtron on 2015-01-03
Hmm not sure about the uninstallation of the current software since you did not list all the packages you installed.

iredmail should be installed on a fresh ubuntu server with no packages installed. All required software including dovecot, postfix, mysql, apache etc. will be installed automatically when you run the iredmail installer. It assumes that these packages will be installed for the first time. You will be asked to provide any credentials and info regarding the email and domain name, mysql password etc.

So the recommendation here is to install it on a fresh server (or virtual machine if you have).
Browse the installation section link that I gave and you'll see how automated it is.

---

### Post by vanusk2 on 2015-01-03
I installed Postfix, then Courier, then Dovecot. Dovecot killed Courier, so it's redundant - But I'm mentioning it anyway.

Unfortunately, with the setup I'm currently using - I can't really go about installing iredmail on a fresh installation of Ubuntu. I'm running this mail server on my gaming community's VPS, it's to be for in-house staff purposes and for our message board's mail system. To wipe the system would mean hours of backing up and then reuploading many gigabytes of data, something I'd like to avoid if possible. Is there any way to avoid having to do a completely fresh install? (For reference, Apache and mysql are already installed)

---

