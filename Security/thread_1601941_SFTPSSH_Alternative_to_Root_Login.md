---
title: "SFTP/SSH Alternative to Root Login"
date: 2010-10-20
forum: Security
---

### Post by kingbilly on 2010-10-20
Hello All,

On my Ubuntu 8.04.4 LTS webserver I desperately want to disable the Root account.  But at the moment I am unable because I prefer to use Nautilus/Dolphin on my home laptop for SFTP.  The graphical interface also helps when comparing multiple config files at once, something that being limited to NANO or PICO would make extremely painful. 

The problem is that if I don't use ROOT I can't perform any SSH or SFTP actions with a graphical interface, because I can't use SUDO without the terminal.  

Does anyone else leave root enabled?  I have a non-standard port, disabled password authentication in favor of ssh keys, and I have a tarpit configured.

Is there a solution?  Chroot?

And I searched the forums but could not find this specific topic.

---

### Post by WinstonChurchill on 2010-10-20
> **kingbilly said:**
> 
Does anyone else leave root enabled?  I have a non-standard port, disabled password authentication in favor of ssh keys, and I have a tarpit configured.

I allow root logins in SSH (I know, blasphemy...) - it just makes some things easier. I have multiple daemons that move files around on my server with their own  user-credentials, plus a few dozen people that download and store files on it; I find it much easier to use a graphical SFTP as  root to organize all the files, mostly because typing long file names at the terminal  can get quite tedious. Plus, I use SSH tunX interfaces a lot, and logging in as root makes that easier to configure. I only allow public key authentication, and I cannot honestly see how letting root login to SSH with public keys is any detriment to security: the SSH Daemon runs as root regardless of whether or not root can log in, so if there were some exploitable security vulnerability in the SSH daemon, the attacker would very likely end up with root privileges anyway. 

However, I don't log in as root very often - I almost always use my non-privileged username with sudo; partially because, after so many years of using Ubuntu, logging in as root makes me feel guilty... (Also, I always picture _[COLOR=DeepSkyBlue][this happening]("http://imgs.xkcd.com/comics/goto.png")[/COLOR]_). The root account still has no password set (in /etc/shadow, a "*" - if you use "!" you can't log in...), and I use a different key to log in as root than as my normal user.

In your case though, it's not really necessary - if you need to compare config files, just open up multiple gnome-terminal sessions and SSH to your server on all of them. Also, I find VIM to be vastly superior to nano and pico, but that may be a matter of taste.

If you want to continue SSH-ing as root, be sure you've included the following in your sshd_config: (Some of these are the defaults - I just list them all in my config anyway)
```

PublicKeyAuthentication yes
PermitRootLogin without-password
ChallengeResponseAuthentication no
GSSAPIAuthentication no
GSSAPIKeyExchange no
HostbasedAuthentication no
KerberosAuthentication no
KerberosOrLocalPasswd no
PasswordAuthentication no
RhostsRSAAuthentication no
RSAAuthentication no
UseLogin no
UsePAM no
```UsePAM does not allow password logins if all the other options are set to no (contrary to what the man-page seems to imply...) - it changes the way the session behaves in a few ways that can be nice (for instance, with UsePAM the MOTD is dynamically regenerated every time you log in), but if you don't care, it's probably strictly safer to disable it.

---

### Post by kingbilly on 2010-10-20
Thanks for your feedback.

I am going to work on my sshd_config and changing the AllowRootLogin to the one you recommended.

---

