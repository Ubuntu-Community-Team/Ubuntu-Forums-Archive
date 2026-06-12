---
title: "wireshark"
date: 2008-11-18
forum: Server Platforms
---

### Post by daboroe on 2008-11-18
i know wireshark has a gui but ubuntu server does not. I would like to use wireshark on my ubuntu server any suggestions. i know the command to get it installed is sudo apt-get intall wireshark but how do I start it, configure, etc.

thanks for any help in advance.

daboroe

---

### Post by pdwerryhouse on 2008-11-18
Use tcpdump instead, get it to write the captured data to a file, and then copy that file to a desktop where you have wireshark installed and examine it there.

Eg:

```
tcpdump -i eth0 -s 0 -n -w packetdump.cap
```

Then use wireshark to read the packetdump.cap file.

---

### Post by daboroe on 2008-11-18
okay thakn you. so just ftp it or an openssh server on the server to transfer it from there to my windows box then?

---

### Post by pdwerryhouse on 2008-11-18
Yep, transfer it using whatever method is most convenient for you.

---

### Post by daboroe on 2008-11-19
I need to run that every time I start my server right?

**Edit at 09:09HRS EST**
this is on a vmware image at the moment. I get a tcpdump: socket:  Operation not permitted. I am going to try to run it as sudo.

**Edit at 09:26hrs EST**
I have to run it as sudo.

---

