---
title: "Easy to use OpenVPN tutorial needed"
date: 2014-06-02
forum: Server Platforms
---

### Post by nandor2 on 2014-06-02
Hi there,

I need to install OpenVPN to an Ubuntu 14.04 server.
I found many-many tutorial about how to install OpenVPN server, but none of them was workable for me.
If you know a good and easy to use tutorial the please share it with me.

Thanks,
Nandor

---

### Post by m-dw on 2014-06-02
Hi

I followed these instructions...  [https://help.ubuntu.com/14.04/serverguide/openvpn.html](https://help.ubuntu.com/14.04/serverguide/openvpn.html)

I have a tendency to skip ahead and miss things which made it quite difficult, but when I followed them exactly it went OK.  I've not done anything clever with bridged or routed connectivity yet, but I can connect up to my server no problems.

---

### Post by nandor2 on 2014-06-02
Thanks for the answer. 
What do you think? Can it work on VPS as well?

---

### Post by SeijiSensei on 2014-06-03
I maintain [static-key tunnels]("http://openvpn.net/static.html") between a server in my office and my remote servers at Linode.  It's a simple, effective solution.  I added a rule on my router that forwards traffic intended for the remotes over to the OpenVPN machine.  Every machine in my office can see both my remote servers this way.

---

### Post by nandor2 on 2014-06-04
Thank you SeijiSensei, this solution seems to be very good.

---

