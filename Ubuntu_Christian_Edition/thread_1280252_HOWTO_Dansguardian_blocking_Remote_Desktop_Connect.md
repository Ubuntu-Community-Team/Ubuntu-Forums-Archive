---
title: "HOWTO: Dansguardian blocking Remote Desktop Connection"
date: 2009-10-01
forum: Ubuntu Christian Edition
---

### Post by johntippett on 2009-10-01
Hi.  I just intsalled UbuntuCE so that I could have the Dansguardian installed with the gui.
Works well, but I find it is preventing my remote desktop connection from working.

In the RDP viewer, I type in  myRDPurl:10  and hit 'connect'
Then the RDP viewer changes the address to myRDPurl:**5910**

I figure this has something to do with proxies or port forwarding, but I hardly know what that means.  

I would be so grateful for any advice as to how I can get it connecting to the correct port correctly.

Thanks in advance !

John

---

### Post by david_kt on 2009-10-01
[QUOTE=johntippett;8038091]Hi.  I just intsalled UbuntuCE so that I could have the Dansguardian installed with the gui.
Works well, but I find it is preventing my remote desktop connection from working.

In the RDP viewer, I type in  myRDPurl:10  and hit 'connect'
Then the RDP viewer changes the address to myRDPurl:**5910**

/QUOTE]

The one blocking remote desktop is firewall. Stop firewall on ubuntu ce so as other people could access via remote desktop:

```
sudo /etc/init.d/ubuntu_ce_firewall stop
```

But by stopping firewall, you must set the proxy on firefox to use localhost port 8080.

If you want to enable remote desktop without disabling firewall, you should open port 5900 (default) or 5910 (if you specify 10 as your case)

DK

---

