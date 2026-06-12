---
title: "apc for php in ubuntu 8.10"
date: 2009-01-18
forum: Server Platforms
---

### Post by q.dinar on 2009-01-18
hello.
i have installed "apc" accelerator of php from synaptic.
[http://ru.php.net/manual/en/apc.configuration.php](http://ru.php.net/manual/en/apc.configuration.php) :
> Once you have a running server, you should copy the apc.php script that comes with the extension to somewhere in your docroot and load it up in your browser. It provides you with a detailed look at what is happening in your cache.
i have not found that file.

where should i write that settings to enable apc? append to php.ini ?
i have not found any configurations for apc except a line in apc.ini.

---

### Post by q.dinar on 2009-01-23
now i have written "apc.enabled=1" (as remember) line at the end of php.ini yesterday. as i know i should not restart apache when php is through fcgid. now today i look in administration page of a forum on the server and it shows that no cache is installed. when i used xcache on last installation it also did not show though, but i was said that it shows other caches.

---

### Post by q.dinar on 2009-01-28
it works. that forum script does not show it. phpinfo function displays it. also i tested with ab command.

---

