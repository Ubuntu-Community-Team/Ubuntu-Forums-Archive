---
title: "gcr security problem?"
date: 2012-12-07
forum: Security
---

### Post by millerthegorilla on 2012-12-07
Hi - I am running ubuntu studio 12.10 and recently a gcr prompt has been turning up that states - you weren't logged in to your keyring at log in time - or words to that effect.

The prompt requests the login passphrase, all of this in both user accounts and the admin account.

I was doing some less than secure work involving dropping the firewall briefly just before it happened, and I have seen a keystroke logging equivalent of this on Windows machines about 7 years ago.  Is there a way to find out if this is an exploit?

Thanks

---

### Post by nothingspecial on 2012-12-08
*Thread moved to **Security Discussions**.*

---

### Post by Hungry Man on 2012-12-08
Try reading here maybe.

[https://wiki.ubuntu.com/BasicSecurity#Did_I_Just_Get_Owned.3F](https://wiki.ubuntu.com/BasicSecurity#Did_I_Just_Get_Owned.3F)

---

### Post by millerthegorilla on 2012-12-09
Thanks for the link, I am working through that now.  I think that I may have found the error.  
In auth.log I have the following : 

```
Dec  8 19:37:49 xxxxx-R720 polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.19 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_GB.UTF-8)
Dec  8 19:38:45 xxxxx-R720 gnome-keyring-daemon[2315]: couldn't set environment variable in session: The name org.gnome.SessionManager was not provided by any .service files
Dec  8 19:38:45 xxxxx-R720 gnome-keyring-daemon[2315]: keyring alias directory: /home/xxxxx/.local/share/keyrings
```When I check the environment variables I get :

```
GNOME_KEYRING_CONTROL=/run/user/xxxxx/keyring-oOGlqL
GNOME_KEYRING_PID=2453

```When I list the actual process id :
```
2739 ?        00:00:00 gnome-keyring-d

``` and 2453 is not listed

and the keyring file is ```
keyring-Wk2OwE
```So it seems that my environment variables are not being updated.  I will read about this now but if anyone can contribute before I get back then I'd be grateful.

Thanks.

---

