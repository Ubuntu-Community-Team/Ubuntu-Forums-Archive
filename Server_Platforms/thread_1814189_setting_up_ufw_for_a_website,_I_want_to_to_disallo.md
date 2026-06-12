---
title: "setting up ufw for a website, I want to to disallow everything except ssh, e-mail, an"
date: 2011-07-29
forum: Server Platforms
---

### Post by batfink3312 on 2011-07-29
I have read the basic instructions here:

[https://help.ubuntu.com/community/UFW]("https://help.ubuntu.com/community/UFW")

I want to ```
sudo ufw default deny
``` and then

```
sudo ufw allow ssh
sudo ufw allow smtp
sudo ufw allow www
sudo ufw allow https
sudo ufw allow imaps
```

to allow the services I need, am I missing anything ? I assume allowing *ssh* will also allow *scp* ? (heck I will allow *sftp* as well anyway).

However my problem is I am connecting remotely, so the only way I can do what I want is to actually do a ```
sudo ufw default allow
``` then use a list of the services provided by ```
less /etc/services
``` and deny each service individually? This seems a pain as if I turn on the firewall with default deny it will boot me out of my ssh connection?

---

### Post by Lars Noodén on 2011-07-29
> **batfink3312 said:**
> However my problem is I am connecting remotely... if I turn on the firewall with default deny it will boot me out of my ssh connection?

It's risky but you can use [at](http://manpages.ubuntu.com/manpages/natty/en/man1/at.1.html) to let yourself back in after a mistake.

```

echo "sudo ufw default allow" | at now +3 minutes

```

That means messing with /etc/sudoers to allow ufw to no need passwords, but is good to ensure that you don't accidentally lock yourself out.

That gives 3 minutes to test new rules.

---

