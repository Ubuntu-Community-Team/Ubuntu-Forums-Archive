---
title: "Asking for password before boot for decrypting device"
date: 2012-03-09
forum: Security
---

### Post by donut87 on 2012-03-09
Hello everybody,

is it possible to kind of pause the boot process to ask for a password which then decrypts a luks device? I want to set up a SQL-Server which contains highly (!!!) sensitiv data. I have to secure the server in a way that simply stealing it would not grant you access to this data BUT on the other hand (non IT) people have to use it. So my idea is to install a system and to have a second drive that is encrypted. This second drive must be mounted before the sql service (mysql, postgres - doesn't matter) is started. To mount this second drive the password is needed, so there must be a prompt to enter it. If the correct password was entered booting continues.

Is there any way I can have such a behaviour?


Thanks

Donut

---

### Post by baumanno on 2012-03-09
For one thing, you could set a BIOS password that will be prompted on each and every startup, and only a correct input will proceed to boot. But this will concern all partitions in the system, and is not really high-security, it'll only prohibit some basic mischief.

I'd recommend going through this article: [http://www.linuxjournal.com/article/7743]("http://www.linuxjournal.com/article/7743"), although it might be somewhat outdated, I suppose the concepts provided haven't changed much. But I'd **highly** recommend testing this on some non-production machine first, and test it thoroughly, i.e. do everything with it you would do on live. And more, if possible ;)
Fiddling with the boot-process and filesystems in general is, if not a sure way to data loss, then at least a well paved one...

Cheers

---

