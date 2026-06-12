---
title: "state of remote desktop viewer in ubuntu compared with Windows"
date: 2009-08-02
forum: The Cafe
---

### Post by legolas_w on 2009-08-02
Hi
Today I was in a friend company where they have server 2003 installed as their corporate server. 

I was in ubuntu and he said I can connect to the server using "terminal server client" and when I trid that software it was amazing. Its performance was far better than when I try to view one ubuntu machine from another ubuntu machine using "remote desktop viewer" software.

are there some tricks available to improve the ubuntu -> ubuntu desktop viewing or I am doing something wrong? because when I connect from one ubuntu to another one, performance is really bad. mouse lag behind and it is very slow...

Thanks.

---

### Post by cdekter on 2009-08-02
The reason is that Remote Desktop Viewer uses VNC, while Terminal Server Client uses the proprietary RDP from Microsoft. RDP has far better performance than VNC, which is a sad state of affairs.

---

### Post by thisllub on 2009-08-02
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

