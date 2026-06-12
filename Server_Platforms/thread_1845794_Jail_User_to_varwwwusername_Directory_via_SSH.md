---
title: "Jail User to /var/www/username Directory via SSH"
date: 2011-09-17
forum: Server Platforms
---

### Post by tts5 on 2011-09-17
I have multiple folders in /var/www for different websites -- Apache uses name-based Virtual Hosts (Ubuntu Server). Suppose I want to allow someone to access their /var/www/user directory, but not cd out of it and be able to traverse the system.

I found information about an OpenSSH Jail here: [http://antitese.org/sshjail/](http://antitese.org/sshjail/)

Has anyone used/implemented something like this? Is there a better way aside from basic permissions to control this?

---

### Post by Lars Noodén on 2011-09-18
There's a better way to do it with SFTP already built into OpenSSH server.  Just use the "[ChrootDirectory](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#Chrooted_SFTP-Only_Accounts)" directive.  

```

Subsystem sftp internal-sftp

Match Group webmasters
        ChrootDirectory /var/www/%u
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp

```

If you want shell access, too, then you'll have to populate the jail with the necessary programs and devices.  Myself, I'd recommend just SFTP only.

---

