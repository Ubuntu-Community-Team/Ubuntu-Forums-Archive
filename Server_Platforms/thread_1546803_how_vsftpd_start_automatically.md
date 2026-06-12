---
title: "how vsftpd start automatically??"
date: 2010-08-05
forum: Server Platforms
---

### Post by ansary on 2010-08-05
guys can u give me some steps on how to start automatically vsftpd in my server after reboot?

---

### Post by Bachstelze on 2010-08-06
It should start automatically.  What makes you think it doesn't?

---

### Post by pipemartinm on 2010-08-06
If you installed it via aptitude it should start automatically. You can check that it's starts automatically by installing rcconf
```

sudo apt-get install rcconf
sudo rcconf

```

---

### Post by cdenley on 2010-08-06
> **pipemartinm said:**
> If you installed it via aptitude it should start automatically. You can check that it's starts automatically by installing rcconf
```

sudo apt-get install rcconf
sudo rcconf

```

I don't think that will work with the upstart configuration. Is vsftpd configured to bind to an external interface (if so, which), or does it listen for connections on all interfaces?
```

sudo service vsftpd start
sudo netstat -tlnp
ifconfig

```

---

### Post by mikedep333 on 2010-08-07
> **cdenley said:**
> I don't think that will work with the upstart configuration. Is vsftpd configured to bind to an external interface (if so, which), or does it listen for connections on all interfaces?
```

sudo service vsftpd start
sudo netstat -tlnp
ifconfig

```

rcconf works for me.

---

### Post by cdenley on 2010-08-07
> **mikedep333 said:**
> rcconf works for me.

Well I'm pretty sure rcconf manages your startup configuration by adding/removing symlinks in /etc/rc?.d. However, in ubuntu 10.04, there are no such symlinks for vsftpd. Most services have been configured with the upstart configuration files instead. The /etc/init.d script is just a symlink for a generic upstart wrapper there for backwards compatibility.

---

