---
title: "CUPS servers 403 error"
date: 2009-07-19
forum: Server Platforms
---

### Post by kpictjl on 2009-07-19
I did a fresh install of Ubuntu server 9.04 trying to setup a print server at home.  I cannot connect to the CUPS admin web page from another machine on my local network.  I keep getting a 403 "Forbidden" error.  I've tried from both a linux machine and from a Vista machine.

Then I followed the instructions on the Ubuntu documentation site. 
[https://help.ubuntu.com/9.04/serverguide/C/cups.html]("https://help.ubuntu.com/9.04/serverguide/C/cups.html")

The CUPS error logs in debug mode give me this...

```
D [19/Jul/2009:16:12:10 -0400] cupsdAcceptClient: 8 from 192.168.1.6:631 (IPv4)
D [19/Jul/2009:16:12:10 -0400] cupsdReadClient: 8 GET / HTTP/1.1
D [19/Jul/2009:16:12:10 -0400] cupsdAuthorize: No authentication data provided.
D [19/Jul/2009:16:12:10 -0400] cupsdSendError: 8 code=403 (Forbidden)
D [19/Jul/2009:16:12:10 -0400] cupsdCloseClient: 8
D [19/Jul/2009:16:12:10 -0400] cupsdAcceptClient: 8 from 192.168.1.6:631 (IPv4)
D [19/Jul/2009:16:12:10 -0400] cupsdReadClient: 8 GET /cups.css HTTP/1.1
D [19/Jul/2009:16:12:10 -0400] cupsdAuthorize: No authentication data provided.
D [19/Jul/2009:16:12:10 -0400] cupsdSendError: 8 code=403 (Forbidden)
D [19/Jul/2009:16:12:10 -0400] cupsdCloseClient: 8

```

Any help is appreciated, thank you.

---

### Post by kpictjl on 2009-07-19
Getting closer.  Now I can access the main cups page but no the admin pages. 

I had to add "Allow @LOCAL" to the Location section of cupsd.conf.

```
# Restrict access to the server...
<Location />
  Order allow,deny
  Allow @LOCAL #new
</Location>
```

Now I can't access the Administration section of the web page.  But I think I'm on the right track.

---

### Post by kpictjl on 2009-07-19
I added the Allow @LOCAL to the admin and the admin/conf sections also.  I think I'm good to go.  Sorry for posting and then answering my own post within minutes...


```
# Restrict access to the admin pages...
<Location /admin>
  Encryption Required
  Order allow,deny
  Allow @LOCAL #new
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
  Allow @LOCAL #new
</Location>
```


Thanks to the linuxforums for setting me straight.
[http://www.linuxforums.org/forum/servers/120309-cups-403-forbidden-error.html]("http://www.linuxforums.org/forum/servers/120309-cups-403-forbidden-error.html")

---

### Post by cariboo on 2009-07-19
By design, you cannot connect remotely to the cups server. If your network isn't outward facing, and you have the firewall on your router set to block everything, you can allow remote connections to the cups server by enabling it on the internal cups web page. See the screenshot.

---

### Post by sinaen on 2009-07-28
This helped me too.. its a good answer.. :) deeply apprecciate it.. :)

---

### Post by stlu on 2012-01-02
> **kpictjl said:**
> 
...
Sorry for posting and then answering my own post within minutes...


You better be sorry! Next time we expect you to just whine about the problem and sit there waiting for somebody else to do the work :)

Actually, I was pretty impressed that he/she was working on the problem himself.  Good initiative! (a little late on the compliment though)

---

