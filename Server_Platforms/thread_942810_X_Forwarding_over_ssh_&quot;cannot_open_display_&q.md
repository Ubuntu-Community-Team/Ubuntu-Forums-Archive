---
title: "X Forwarding over ssh &quot;cannot open display: &quot;"
date: 2008-10-09
forum: Server Platforms
---

### Post by promodus on 2008-10-09
If you get this error when using

```

rich@blackbox:~$ ssh -X 1.161
rich@1.161's password: 
Linux storage2 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
Last login: Thu Oct  9 12:47:00 2008 from 1.0.0.100
rich@storage2:~$ gedit
cannot open display: 
Run 'gedit --help' to see a full list of available command line options.
```


The fix being...
```
sudo apt-get install xauth
```

exit the ssh session, and reconnect. Problem gone.

---

