---
title: "Networking Instance Unknown"
date: 2013-01-29
forum: Server Platforms
---

### Post by chrisguk on 2013-01-29
I keep receiving this message when I issue the command:

```
sudo service networking restart
```

Output:

```


stop: Unknown instance: 
networking stop/waiting


```

I search Google etc and tried some suggested debugging like the following:

```


sudo service network-interface restart INTERFACE=eth0

and

sudo service network-interface restart INTERFACE=eth1


```

They both stop and start with no errors

This is my setup:

[http://ubuntuforums.org/showthread.php?t=2109373]("http://ubuntuforums.org/showthread.php?t=2109373")

I have checked the logs in /var/log/syslog and no errors are visible in there either so I am kind of lost on this one.  Any ideas?

---

