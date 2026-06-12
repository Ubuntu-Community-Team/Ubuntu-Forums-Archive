---
title: "Hosting phpBB3 from Apache"
date: 2009-12-13
forum: Server Platforms
---

### Post by Azubah on 2009-12-13
I've read or tried to read most of the tutorials and they only speak of phpBB2 I've got apache and everything but I wanted to have Apache just point towards PHPbb3.

I even have Mysql installed and phpbb3 from synaptic installed with all the parts required, I just don't understand why it's not wanting to work right.

and I'm pretty sure I posted in the wrong place without realizing could someone move this to the appropriate place?

---

### Post by Queue29 on 2009-12-13
> **Azubah said:**
> I've read or tried to read most of the tutorials and they only speak of phpBB2 I've got apache and everything but I wanted to have Apache just point towards PHPbb3.

I even have Mysql installed and phpbb3 from synaptic installed with all the parts required, I just don't understand why it's not wanting to work right.

and I'm pretty sure I posted in the wrong place without realizing could someone move this to the appropriate place?

After installing phpbb through apt-get,
ex: ```
sudo apt-get install phpbb3
```
 you need to place the following line at the bottom of your /etc/apache2/apache2.conf file:

```
 Include /etc/phpbb3/apache.conf

```

Then your phpbb3 installation will be available at [http://yoursite/phpbb/](http://yoursite/phpbb/)

If you want it at [http://yoursite/](http://yoursite/) you could just put an index file that instantly forwards to /phpbb or you can screw around with your apache config


The **BEST** solution however would be to use turnkey's phpBB appliance. It's ubuntu server with phpbb, webmin, postfix, SSL, etc. all preconfigured: 
[http://www.turnkeylinux.org/phpbb](http://www.turnkeylinux.org/phpbb)

---

