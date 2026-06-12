---
title: "Bad eno1 address?"
date: 2018-11-10
forum: Server Platforms
---

### Post by Sheldon_Livingston on 2018-11-10
I just created a LAMP on my 10.1.1.x network.

ifconfig shows eno1 with a 192.168.0.109 address and the lo loopback adapter.

This LAMP has one NIC.

The LAMP can hit the Internet (Google, etc) but I cannot "see" the LAMP (as I am on a 10.1.1x scheme and it is on a 192.168.0.x scheme).

I am a nube... any thoughts on this issue?

---

### Post by SeijiSensei on 2018-11-10
You need to add a static route on your router that sends traffic for the 192.168 network to the machine running Apache. You'll need to read the docs for your router to learn how to set this up.

Is there a reason why you can't give that box an address in the 10 network?

---

### Post by slickymaster on 2018-11-10
Thread moved to **Server Platforms** fora a better fit

---

