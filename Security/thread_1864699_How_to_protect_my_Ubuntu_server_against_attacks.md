---
title: "How to protect my Ubuntu server against attacks"
date: 2011-10-19
forum: Security
---

### Post by piet.couvreur on 2011-10-19
Hi,

I'm looking for a strong authentication solution to protect my Ubuntu server against attacks.

I want to protect SSH, PhpMyAdmin and my Drupal backend.

There are all protected using a password, and I'm not feeling safe about that.

I was looking for an hardware authentication and the only device I found is the Swekey authentication key.

Did anybody even tried this USB dongle ?

Regards,

Piet

---

### Post by Lars Noodén on 2011-10-19
For SSH, one of the best things for security would be to disable password-based authentication and only [key-based authentication](https://help.ubuntu.com/community/SSH/OpenSSH/Keys).

The weak link might be PhpMyAdmin.  Learn to use the shell and you can remove PhpMyAdmin from your machine.  Once you know how, the shell is faster and easier.  It's also scriptable.

---

### Post by e79 on 2011-10-19
+1 for what Lars Noodén said.

Also you might want to consider changing the default URL of your PHPmyadmin page if you want to stick with it; have a look [here]("http://www.thetechrepo.com/main-articles/488") to do so.

---

### Post by ubudog on 2011-10-20
> **Lars Noodén said:**
> For SSH, one of the best things for security would be to disable password-based authentication and only [key-based authentication](https://help.ubuntu.com/community/SSH/OpenSSH/Keys).

The weak link might be PhpMyAdmin.  Learn to use the shell and you can remove PhpMyAdmin from your machine.  Once you know how, the shell is faster and easier.  It's also scriptable.

+1
All the attacker will see is:
"Permission denied (publickey)."

A live demo:
```

ssh root@ubudog.net

```
:)

- No password prompt.

Also, you can install [fail2ban]("https://help.ubuntu.com/community/Fail2ban") for extra ssh security.

> **e79 said:**
> +1 for what Lars Noodén said.

Also you might want to consider changing the default URL of your PHPmyadmin page if you want to stick with it; have a look [here]("http://www.thetechrepo.com/main-articles/488") to do so.

Nice link!

---

### Post by Cyked on 2011-10-21
Change SSH listening port.

---

### Post by collisionystm on 2011-10-21
> **Lars Noodén said:**
> For SSH, one of the best things for security would be to disable password-based authentication and only [key-based authentication](https://help.ubuntu.com/community/SSH/OpenSSH/Keys).

The weak link might be PhpMyAdmin.  Learn to use the shell and you can remove PhpMyAdmin from your machine.  Once you know how, the shell is faster and easier.  It's also scriptable.

I +1 this as well.

Not sure what you have running on there, but you could also change the firewall to only accept outside requests from certain IP addresses.

---

### Post by Dangertux on 2011-10-21
For SSH I second what has already been said.

For phpmyadmin, change the default path, and preferably don't use it, like already stated.

For Drupal consider using mod-security (will also help phymyadmin) and hardening your database installation. Don't hack core, check your file permissions, protect your admin directory with htaccess.

For two factor authentication tokens swekey is nice, so are products by umikey and yubikey.

Hope this helps.

---

### Post by piet.couvreur on 2011-11-04
Thanks for your input.

I also purchased a Swekey.

To be honnest I'm amazed by the device.

I use it for ssh and to administrate a Drupal web site.

It is very simple to use, and when I unplug it I'm even logged out...

Thanks again,

Piet

---

### Post by Matt_Fussell on 2012-01-16
This works in Ubuntu Server 10.04 LTS.
First, you need to edit /etc/phpmyadmin/apache.conf and add make sure the top of the configuration looks like this (changes where appropriate):

"...

# phpMyAdmin default Apache configuration

Alias /[COLOR="navy"][YourSecretLocation][/COLOR] /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
        Options FollowSymLinks
        DirectoryIndex index.php
        AllowOverride All
        AuthType Basic
        AuthName "[COLOR="navy"][YourTitleHere][/COLOR]"
        AuthUserFile /usr/share/phpmyadmin/.htpasswd
        Require valid-user
        <IfModule mod_php5.c>
..."

Next: **cd /usr/share/phpmyadmin**
Then: **sudo htpasswd -c .htpasswd [COLOR="Navy"][YourSelectedUserName][/COLOR]**

Enter the passwords, and finally:
**sudo service apache2 restart**

This worked for me, hopefully it will for you as well.

---

### Post by hackertarget on 2012-01-18
Something I run on all my systems is [http://ossec.net](http://ossec.net), it is host based Intrusion software. Not difficult to install, minimal tuning required and its stable.

It will alert you if strange things start to happen, an important part of securing a system is system monitoring. 

Active Response can also be enabled with ossec, this will block access to the system from perceived attackers using IP Tables.

---

### Post by kindledwind on 2012-02-03
What I did:

- Moved SSH to a weird port.
- Edit /etc/apache2/apache2.conf & comment out the line that starts PHPmyadmin. When I want it, uncomment it & restart apache. When I'm done, comment it & restart apache again.

Don't use Drupal anymore, so I'm no help there.

todd

---

