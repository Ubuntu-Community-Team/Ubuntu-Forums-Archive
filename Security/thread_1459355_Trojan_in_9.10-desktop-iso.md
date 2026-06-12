---
title: "Trojan in 9.10-desktop-iso?"
date: 2010-04-21
forum: Security
---

### Post by cloud9mike on 2010-04-21
Installed a fresh iso of ubuntu-9.10-desktop-i386.iso with matching md5 checksums... As soon as it came on-the-air snort spit out the following:
 
EVENT_ID 20887991:
[**] [1:1328636:0] 28636 VID23953 Momibot Trojan Phoning Home [**]
[Classification: None] [Priority: 5]
04/20/2010-19:32:30.025713 *.*.*.89:59408 -> 69.163.151.181:80
tcp TTL:64 TOS:0x0 ID:61786 IpLen:20 DgmLen:152 DF
***AP*** Seq: 0x3264D505 Ack: 0x67860299 Win: 0x6C TcpLen: 32
TCP Options (3) => NOP NOP TS: 9159 19030882 

POST /vino/vino.php HTTP/1.1..Host: [www.bani.com.br..Content-Typ](www.bani.com.br..Content-Typ)
e: text/xml..Content-Length: 220....

---

### Post by uRock on 2010-04-21
A google search just shows that as a Window32 deal.

---

### Post by CharlesA on 2010-04-21
vino is the VNC server included with Ubuntu desktop, it probably doesn't like it.

---

### Post by cloud9mike on 2010-04-21
This traffic is exhibiting the same behavior with a post to 69.163.151.181:80 as the "w32" versions... Don't you think it is naive to dismiss this because a google search reveals that it is a "W32" issue?  I realize this could be a false positive, but I'm not ready to let it go based on googling it.

---

### Post by cloud9mike on 2010-04-21
Charles... Thanks for the info.. That brings it all together for me... I enabled the "remote desktop" feature and then disabled it..  Still curious why that package would exhibit that behavior though...

---

### Post by cdenley on 2010-04-21
That is vino, or "remote desktop", checking to see if it is accessible from the internet. It sends an HTTP POST to a PHP script on a web server maintained by vino's author, and the PHP script's output allows vino to determine if the web server was able to make a connection to your vino server.
```

cdenley@ubuntu:~$ cat vino-2.28.1/capplet/webservices
# This file lists all webservices URLs that can be used by vino to provide
# a connectivity test.

# The webservice must be a XMLRPC service, which provides a method 'vino.check':
# vino.check (
#   IN int port, -> port to be tested against. Default is 5900.
#   IN int timeout, -> timeout, in seconds to cancel the testing. Default is 10.
#   OUT string IP, -> The public IP of the machine (variable 'REMOTE_ADDR').
#   OUT bool status, -> True if can connect to the host at specified port.
#   OUT string version -> Version of the method signature, currently is "0.1".
# )
# 
# Basically what the service does is: Try to open a connection into the
# incoming host (REMOTE_ADDR) at the specified port. It returns the IP and
# if the connection was established successfully.

# Check a PHP implementation of that service in the file org.gnome.vino.Service.php,
# shipped in vino source code, in 'capplet' folder.

# Put one address per line. Blank lines and started with a '#' are ignored.



# Jorge Pereira
http://blog.jorgepereira.com.br/jorge/org.gnome.vino.Service.php

# Jonh Wendell
**http://www.bani.com.br/vino/vino.php**
cdenley@ubuntu:~$ host www.bani.com.br
www.bani.com.br has address 69.163.151.181

```

---

### Post by CharlesA on 2010-04-21
> **cloud9mike said:**
> Charles... Thanks for the info.. That brings it all together for me... I enabled the "remote desktop" feature and then disabled it..  Still curious why that package would exhibit that behavior though...

See the post above this one. :)

---

### Post by OpSecShellshock on 2010-04-21
You can always look at the Snort signature itself and see what it's looking for, as well as any reference link that might be included. It would at least show you the connection between the traffic and why the signature was firing (in this case you'll know it's a false positive from the explanation offered in the posts above mine, but it might help you tune your IDS, which is always good).

---

### Post by The Cog on 2010-04-21
Ooh-Er!

I didn't know that vino phones home. That means that the authors get to hear about every machine that ever runs vino, and (if they felt so inclined) they have the opportunity to ty to take control of it.

Although opening vino to the internet is a Rally Bad Idea in the first place, I really don't like the fact that it also phones home and tells the authors that it's there and listening on port xxxx. I just tried it on my system, and it phoned home to two different places. One of the two places told me my public IP address in its reply.

---

### Post by cdenley on 2010-04-21
> **The Cog said:**
> Ooh-Er!

I didn't know that vino phones home. That means that the authors get to hear about every machine that ever runs vino, and (if they felt so inclined) they have the opportunity to ty to take control of it.

Although opening vino to the internet is a Rally Bad Idea in the first place, I really don't like the fact that it also phones home and tells the authors that it's there and listening on port xxxx. I just tried it on my system, and it phoned home to two different places.

How else would it determine that it is open to the internet?

---

### Post by rookcifer on 2010-04-22
Do away with SNORT.  Unless you are running an enterprise with a bunch of Windows boxes, it is superfluous and a headache.  It depends on signatures, just like AV software, and we all know the awesome record AV software has at keeping Windows boxen clean. :)

Anything that relies on signatures is doomed to fail.  There's just too large and quickly changing threat landscape for that.

---

### Post by DawieS on 2010-04-22
I have noticed that the Nvidia proprierty graphics driver also attempts dialing home after activation.

---

