---
title: "Ban connections based on username"
date: 2009-07-15
forum: Security
---

### Post by SINZAR on 2009-07-15
Hi all,

I'm using ubuntu hardy as a media center with ftp access to easily transmit the files over.

Due to the fact that I have an ftp server at all, bots routinely attack the server trying to gain access. They will never be successful because they're trying to hack the administrator account, which doesn't exist.

I routinely check the logs and add any attacking ip's to the host.deny list but I'm wondering if there's any way to automatically ban a connection if they specifically try to use the administrator account?

I know fail2ban will check logs and ban ip's, but it happens after the fact.

Any tips would be appreciated.

---

### Post by cdenley on 2009-07-15
> **SINZAR said:**
> 
I know fail2ban will check logs and ban ip's, but it happens after the fact.

You need a solution which bans them before the authentication attempt based on the username they will use during authentication? As far as I know, neither proftpd or vsftpd can be configured to ban IP addresses, so the only way this would be possible is with a program that monitors logs (such as denyhosts or fail2ban). What is the harm in banning an IP after a failed authentication attempt? You can't ban based on an event which hasn't happened yet.

---

### Post by SINZAR on 2009-07-15
> **cdenley said:**
> What is the harm in banning an IP after a failed authentication attempt? You can't ban based on an event which hasn't happened yet.

The harm is that the attacks flood the server and cause huge log files. 

The idea isn't to ban them before it happens, but that once a failed attempt at administrator has been made, the ban is put in to place.

---

### Post by cdenley on 2009-07-15
> **SINZAR said:**
> The harm is that the attacks flood the server and cause huge log files. 

The idea isn't to ban them before it happens, but that once a failed attempt at administrator has been made, the ban is put in to place.

Isn't that how denyhosts and fail2ban work? You can specify how many failed attempts will result in a ban.

---

### Post by lykwydchykyn on 2009-07-15
Check out:
[http://www.hexten.net/wiki/index.php/Pam_abl](http://www.hexten.net/wiki/index.php/Pam_abl)
I don't think it's in the repos, but it looks like it might put you in the right direction.

---

### Post by bodhi.zazen on 2009-07-15
You can do this with iptables or denyhosts.

denyhosts has a blacklist available you can use , read the config file.

To be honest, why not use scp over a non-default port ? changing to a non-default post stops 99.9999 % of the script kiddies.

---

### Post by cdenley on 2009-07-15
> **bodhi.zazen said:**
> You can do this with iptables or denyhosts.

I know you can use fail2ban to ban IP's using any regex expression for matching based on events like authentication attempts for a specific user. Does denyhosts have this flexibility as well? I never realized that.

---

### Post by bodhi.zazen on 2009-07-15
denyhosts is not as flexible so as to do a regex search in the logs. It will ban an IP and should keep your logs from filling up.

---

### Post by cdenley on 2009-07-15
> **bodhi.zazen said:**
> denyhosts is not as flexible so as to do a regex search in the logs. It will ban an IP and should keep your logs from filling up.

Oh, I see. The original post indicated he wanted to ban specifically after authentication attempts as "administrator", but the default configuration of banning after a few failed authentication attempts would probably be more appropriate, and it would still satisfy his requirements since any attempt to authenticate as "administrator" will fail anyway.

---

### Post by bodhi.zazen on 2009-07-15
I think either ignore (ie do not log) these attempts or, depending how public the ftp server is, restrict access via iptables would be best.

Is it possible to use a simple white list in /etc/hosts.allow (ie tcpwraper) (depends on how public the ftp server is really).

---

### Post by SINZAR on 2009-07-16
Thanks for the info everybody. I went ahead and changed the default ftp port since that's the easiest and quickest way to prevent the attacks in the first place.

The only hard part now will be remembering that it's not the default port anymore :)

---

### Post by bodhi.zazen on 2009-07-16
> **SINZAR said:**
>  The only hard part now will be remembering that it's not the default port anymore :)

And that is the down-side of changing the default port, lol.

---

### Post by SlugSlug on 2009-07-17
I highly recommend denyhosts and fail2ban, I use both. denyhosts will sync to its servers and add baddies to you hosts.deny

---

