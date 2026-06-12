---
title: "Automated file transfer"
date: 2008-01-17
forum: Server Platforms
---

### Post by sydneymoon on 2008-01-17
I want to automate the file transfer from a remote site to my pc over a WAN. Can anyone please suggest an industry standard secure file transfer tool for a windows environment?

I am looking for an industry accepted, more secure than traditional FTP.
Thanks!

---

### Post by andol on 2008-01-17
Windows <--> Windows or Windows <--> Linux/Unix

---

### Post by HermanAB on 2008-01-17
Cygwin with rsync over ssh.  Secure and rock solid stable.

Cheers,

Herman

---

### Post by donadelo on 2008-01-18
Yeah! There are lots of secure file transfer tools are available on the net that can solve your problems. I know one among of them called [ JSCAPE Secure FTP Server.](http://www.jscape.com/secureftpserver/) 
It provides reliable and secure file transfers between internal and remote users, business partners and customers across corporate networks and the Internet. Secure file transfer is paramount in protecting critical, confidential enterprise data from would-be intruders as the data is transmitted over the Internet.
Hope this will help you!
All the best!

---

### Post by MJN on 2008-01-18
I'd recommend using [PSCP]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/"), a Windows command-line SCP client from the widely-used Putty suite of tools. Easy to use/script and secure given it uses SSH. It doesn't require anything server-side other than a working SSH server.

An example usage from the [docs]("http://the.earth.li/%7Esgtatham/putty/0.60/htmldoc/Chapter5.html#pscp"):

```
pscp c:\documents\foo.txt fred@example.com:/tmp/foo/
```

Mathew

---

