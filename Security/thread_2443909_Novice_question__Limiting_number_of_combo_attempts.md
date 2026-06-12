---
title: "Novice question:  Limiting number of combo attempts with Fail2ban and 128 bits of ent"
date: 2020-05-21
forum: Security
---

### Post by Drone4four on 2020-05-21
Apps such as Fail2ban and DenyHosts enable unix administrators to limit username/password combo attempts to typically 3 attempts. But why 3? Some admins enable more, like 6 or 8 giving honest users a little more slack when making different attempts at a password they may not recall exactly. But why not 18? Or even 30? 

If a sophisticated cracker wanted to brute force a combo with a scheme involving 128 bits of entropy, s/he would need to make trillions of attempts a second. So if an admin limited the total number of attempts to 100 using Fail2ban, wouldn’t the authentication system still be secure and robust, as long as the admin sets up their username/password scheme to require 128 bits of entropy?

---

### Post by TheFu on 2020-05-21
Fail2ban monitors logs and can be setup to block remote access.  I don't think it would work for local access.

As for securing remote access, if you are still using passwords without something else too, you've failed Security 101.  For remote ssh connections, use ssh-keys.  They are vastly more secure AND 1000x more convenient.  Takes 2 commands to setup ssh keys, I've never understood why they aren't used by everyone.
```
   $ ssh-keygen -t ed25519
   $ ssh-copy-id -i ~/.ssh/id_ed25519.pub username@remote

```Done.  Only need to do the first step once. Do the 2nd to push the public key to any remote system you want access.  Then we can block any password attempts that aren't from our LAN in the server's sshd_config. Put something like this at the bottom of the file and comment out any *PasswordAuthentication* lines above that:
```
PasswordAuthentication no
Match Address 192.168.22.0/24,172.21.22.0/24,10.12.44.0/24
      PasswordAuthentication yes
```
Just change the subnets for your needs, then restart the sshd service.  Normal Ubuntu installs block remote root, but some IaaS providers only allow root initially over ssh with keys.  Remote root should be disabled and the login accounts used on any system should all be odd.  No "admin" - make it "admin39455".  It isn't like we need to type that in ... ever.  With the client-side ssh config file, ~/.ssh/config, we can setup aliases so we don't need to know any IPs, no usernames, no non-standard ports again.
```
host pihole
  user ubuntu59034
  hostname 172.22.22.80
  port 62022

host pihole-tf
  user thefu
  hostname 172.22.22.80
  port 62022
```
Bam.  just **ssh pihole** becomes *ssh -p 62022 ubuntu59034@172.22.22.80* automatically for every ssh-based too.

As to how many attempts should be allowed, often that isn't determined by the admin, but by company policy. Often, that policy is set to follow whatever the defaults in MSFT domains are.  The one place I worked that was really very excellent for a 60K employee company set their standards regardless of what the MSFT defaults were.

BTW, fail2ban can be configured for any number of allowed attempts.  There are botnets commonly attacking a single server from 100K different IPs in the world, so allowing 50 attempts for each would allow a huge number of attempts.  Don't use passwords. Just keys.

Password crackers seldom use the front door, but they will try the most common 100K passwords just to see if it is easy to get in.  After that, if it is allowed, they may continue just to keep the logs full.  I was seeing 10K attempts daily on my little server, then I moved the ssh service to a non-standard port and the attempts dropped to zero.  Finding the port wouldn't be hard, but the automatic hacking tools don't bother.  That was over a decade ago.  Can't remember the last attempt that wasn't a 1-time thing.

---

