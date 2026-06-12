---
title: "DHCP Troubleshooting?"
date: 2011-06-30
forum: Server Platforms
---

### Post by kevin11951 on 2011-06-30
I am setting several settings on a DHCP server (PXE, WINS, etc...), and I can't tell if they are being applied.  

Is there a tool that I can use to call a DHCP request as if I was a client, but read the reply from the DHCP server?

---

### Post by kevin11951 on 2011-06-30
For anyone else asking this question in the future:

Apparently Wireshark can be used for this, it displays all the options and their values in easy to read plain text...

edit: Specifically read "DHCP Offer"

[http://wiki.wireshark.org/DHCP](http://wiki.wireshark.org/DHCP)

[IMG]http://wiki.wireshark.org/DHCP?action=AttachFile&do=get&target=dhcp-ws.png[/IMG]

---

### Post by kevin11951 on 2011-07-01
In case anyone is wondering, I am still looking for other programs for seeing the reply from a DHCP server...

Wireshark is too heavy for my uses...  But good for now.

---

### Post by arrrghhh on 2011-07-01
> **kevin11951 said:**
> In case anyone is wondering, I am still looking for other programs for seeing the reply from a DHCP server...

Wireshark is too heavy for my uses...  But good for now.

Wireshark seems just what you want.

Have you seen the cli version tcpdump?  Perhaps that's what you're looking for...?  

Either way, filters are your friend when doing any packet tracing/capturing ;).

---

### Post by BkkBonanza on 2011-07-01
tcpdump is good for seeing the packets. It's a bit short on decoding and presenting the data in useful form. 

You might check out [bootpdc]("http://www.net.princeton.edu/software/bootpdc/bootpdc.1.html") - it says it's designed to decode packets from tcpdump for DHCP and BootP protocols. Just needs Perl which is usually available.

---

