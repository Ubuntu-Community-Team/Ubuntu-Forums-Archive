---
title: "X Server help"
date: 2014-04-01
forum: Server Platforms
---

### Post by DanHorniblow on 2014-04-01
Hi

I am trying to setup a special tor server. I currently have got tor and vidalia installed and they are working fine. I have also configured firefox to use tor's SOCKS proxy, this is also working fine.

I connect to my Tor server via my PC over the network like this:

"ssh -X user@server firefox" 

I do this because I am often examining malware and other things which sometimes include web pages, these web pages can contain things I really don't want to be accessing / running on my PC,

This works fine, the problem occurs when another person on the network wants to use the server at the same time as me, Firefox won't open for them as it says ```
Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system
```

After days of googleing I think this is something to do with the $DISPLAY variable but im not sure. I want to be able to run as many instances of this as I want, any suggestions?


Thanks in advance

Dan

---

### Post by TheFu on 2014-04-01
They need to use a different userid on the remote system. Using **ssh -X** automatically sets the DISPLAY for you. Of course, X-Forwarding must be allowed in the /etc/ssh/sshd_config X11Forwarding yes is the setting.

The other PC must also have a running X/Server.

---

### Post by DanHorniblow on 2014-04-02
Hi

I will look into this and do some more research about userid later and report back.

Yes all of the PC's are running Cygwin's X / Win, it seems to work really well, and yes I have tried do this with all Linux PCs and I get the same error, so I don't think that Windows is my problem here (for once!!) I have also allowed the X11Forwarding in the servers config.

Thanks

---

