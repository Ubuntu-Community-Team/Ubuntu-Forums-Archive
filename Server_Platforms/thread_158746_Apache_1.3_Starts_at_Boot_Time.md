---
title: "Apache 1.3 Starts at Boot Time"
date: 2006-04-11
forum: Server Platforms
---

### Post by AnhD on 2006-04-11
Hi All,
     I did a lot of search and read a lot but still have not figured out howto start apache 1.3 at start time.  I compiled apache and can start with /usr/local/apache/bin/apachectl startssl.  How do instruct the server to start this at boot time?

Ubuntu OS: Server 5.10 (no GUI)
Apache Version: 1.3


Thanks in advance

---

### Post by afonic on 2006-04-11
It should start at boot by default. Have you used the package to install through apt-get?
Try sudo dpkg-reconfigure apache.

Is "apache" present in /etc/init.d/ ?

Also see:
[http://linuxhelp.blogspot.com/2006/04/enabling-and-disabling-services-during_01.html](http://linuxhelp.blogspot.com/2006/04/enabling-and-disabling-services-during_01.html)

---

### Post by fdoving on 2006-04-14
I would strongly recommend installing apache from the apt-get archives.
It's very easy, and it will help you keep track of security updates and fixes.
 
If you are interested, take a look at:
[https://wiki.ubuntu.com/AptGetHowto](https://wiki.ubuntu.com/AptGetHowto)


If not,
This is a evil hack, not recommended at all. Use at own risk. This is not the Ubuntu-way, Debian-way or even my-way of starting services at boot time. It's just a evil hack to 'just do it'.


This will put the command '/usr/local/apache/bin/apachectrl startssl' into the  new file /etc/init.d/rc.local, and make it executable.
```

echo "/usr/local/apache/bin/apachectl startssl" > /etc/init.d/rc.local
chmod +x /etc/init.d/rc.local

```


This will tell ubuntu to run rc.local at boot.
```

update-rc.d rc.local defaults

```

Now your selfcompiled apache 1.3 should be starting at boottime.

To make it not start at boot do the following:
```

update-rc.d -f rc.local remove

```

If you decide that you never want to use this evil hack anymore you can now safely delete /etc/init.d/rc.local
```

rm /etc/init.d/rc.local

```

That's all.

Hope this evil hack helps you somehow. Remeber, doing it the Ubuntu-way is waaaay better and more elegant. It's really the best solution.
- Frode

---

