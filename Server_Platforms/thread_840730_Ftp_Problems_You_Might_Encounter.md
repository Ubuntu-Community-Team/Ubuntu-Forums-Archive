---
title: "Ftp Problems You Might Encounter"
date: 2008-06-25
forum: Server Platforms
---

### Post by speedster239 on 2008-06-25
Having troubles with vsftp login, error 530?

Alright, I was having much trouble with vsftpd for a few days now until I finally figured out what was going wrong. Just in case you care I'm running a vps with ubuntu 8.04.

1. To install vsftdp simple run:
```

sudo apt-get install vsftpd

```

2. Once you have vsftpd installed change into the configuration file:
```

sudo vi /etc/vsftpd.conf

```
Hit 'i' to enter editor mode.

You will now see the default configuration, not much needs to be changed here...

```

#anonymous_enable=YES

to..

anonymouns_enable=NO

```

```

#local_enable=YES

to..

local_enable=YES

```

```

#write_enable=YES

to..

write_enable=YES

```

```

#local_unmask=022

to..

local_unmask=022

```

Close this file by typing <esc> :wq

**And lastly the problem that was causing it all for me!**

3.Change into /etc/ftpusers with:
```

sudo vi /etc/ftpusers

```
and BE SURE that the username you're trying to log into ftp with is not on the list, if it is remove it.

4.Lastly you must restart vsftpd for the changes to apply:
```

sudo /etc/init.d/vsftpd restart

```
Hope This Helps,
Speedster239

---

