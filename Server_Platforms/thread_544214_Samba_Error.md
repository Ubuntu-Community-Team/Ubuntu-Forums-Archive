---
title: "Samba Error"
date: 2007-09-06
forum: Server Platforms
---

### Post by mzar on 2007-09-06
Hi,

I just finish setup my samba server. All configuration in /etc/samba/smb.conf looks fine. My samba running and no error come out. When I want to open from windows, i got those error. Any idea how to fix it? :confused:

[[IMG]http://img126.imageshack.us/img126/2060/errorun1.th.jpg[/IMG]](http://img126.imageshack.us/my.php?image=errorun1.jpg)

---

### Post by HermanAB on 2007-09-06
Well, that is a new one.

Test Samba on Linux itself and make sure it works before trying it from Windows:
telnet serveripaddress 445
smbclient -L \\serveripaddress -N
smbclient \\serveripaddress\sharename -U username%password

Only if those three work, is Samba working properly, only then try a telnet test from Windows.

If the above doesn't work using the ip address, but does work using localhost, then the Linux firewall is at fault.

Cheers,

H.

---

### Post by mzar on 2007-09-06
This is my result

1.

```
[squid@monitor2 ~]$ telnet 10.10.10.62 445
Trying 10.10.10.62...
Connected to idham.intra.abamon.com (10.10.10.62).
Escape character is '^]'.
```

2.

```
[squid@monitor2 ~]$ smbclient -L \\10.10.10.62 -N
tree connect failed: Call returned zero bytes (EOF)
```

---

### Post by Techno.Scavenger on 2007-09-06
This is not the best solution but I had similar issue before and it went away after reboot. :)

Maybe you can try.

---

### Post by HermanAB on 2007-09-06
1. OK, something is listening on the Samba port and the firewall is OK, since it lets the connection through.
2. Samba is listening, but it is screwed up.

I suggest restarting smbd and nmbd with something like 'service smb restart'.
(I'm not running Ubuntu now, so I cannot verify that command)

'Hope that helps!

H.

---

