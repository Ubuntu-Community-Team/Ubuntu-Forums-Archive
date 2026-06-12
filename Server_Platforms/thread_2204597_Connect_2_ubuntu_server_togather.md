---
title: "Connect 2 ubuntu server togather"
date: 2014-02-09
forum: Server Platforms
---

### Post by rifaadh_saif on 2014-02-09
I got a question. I tried google search and found nothing on this subjet.


I wanted to know if it is possible to connect to ubuntu server together that are in 2 different location. 


This is the way i would like to set it up:
 i have my main office and it has all the DHCP, LDAP account,etc and i have a 2nd office and there is a server also but it pretty much does nothing and he is connected to the main office via VPN. So when a user logs into the computer, he will get an IP from the main office and the gateway will be via that server.


Is it possible to do that? if yes can some one give me instructions?


Thanks

---

### Post by CharlesA on 2014-02-09
I believe you can do that with OpenVPN, but as I've never used it or set it up, I don't know of any tutorials.

This might help tho:
[https://help.ubuntu.com/12.04/serverguide/openvpn.html](https://help.ubuntu.com/12.04/serverguide/openvpn.html)
[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

---

### Post by rifaadh_saif on 2014-02-09
Hey,

Thanks for your replay. I read the links you posted but it does not show me anything ways to do it. But i think that if i have a VPN server at 1 location and connect another server has a client it should work. but i will need to try it. I am going to install ubuntu and try this, mostly in the coming weeks. But if i get a solution i will paste it into this forum.

If anybody has any other idea please post i will appreciate it 

Thanks,

---

### Post by CharlesA on 2014-02-09
Yeah, you'd set up the main office with an OpenVPN server and connect the remote office to it with the OpenVPN client.

---

