---
title: "help on ubuntu server for home network"
date: 2008-11-03
forum: Server Platforms
---

### Post by egeneral27 on 2008-11-03
hello!

currently, my home network is connected through a wireless router. i have 1 desktop computer running winxp, a laptop on vista, another laptop running ubuntu 8.04 hardy desktop and the computer that i am using right now is running ubuntu 8.04 hardy server. i installed a gui because i dont need to reserve that much of my resources anyway. both of my desktops are connected via cable. what im planning to do is to make a dedicated server for file sharing, and internet connection sharing. 

My ideal setup would be:

1. an ubuntu dedicated server running file sharing and internet connection sharing and an access point connected through a hub/switch to my server. 
2. All my computers can see each other on the network by just typing the computer name not just ip address when pinging.
3. Printer sharing.

I have three concerns:

1. i have tried sharing my internet connection through firestarter, but my winxp can't connect properly (its on and off) and im not sure if setting up an access point connected through a hub/switch to my server would work.

2. from my winxp desktop, i tried to ping my ubuntu server. it worked fine but when i ping using the computer name it is unreachable.

3. when it comes to interet sharing, are firestarter and iptables the same? which one would you recommend?


Any advice? Thanks in advance!!!

-EJ

---

### Post by doogy2004 on 2008-11-03
Sounds like you are going to need Samba, DNS, CUPS, and possibly FTP.

I'm very familiar with getting these setup, however, I'm not sure how it would work using your server for internet connection sharing.

Personally, I would recommend using the wireless router so serve up your internet connection.

---

### Post by egeneral27 on 2008-11-04
thanks! i'll look into those services right away... ):P

---

### Post by hrod beraht on 2008-11-04
> **egeneral27 said:**
> 2. from my winxp desktop, i tried to ping my ubuntu server. it worked fine but when i ping using the computer name it is unreachable.

Windows XP has a hosts file just like a Linux machine does. So you need to make sure your server's name is defined in there, as in:
**ipaddress hostname**

The linux location is /etc/hosts, and the Windows XP location should be c:\windows\system32\drivers\etc\hosts

Bob

---

### Post by egeneral27 on 2008-11-04
thanks bob! thats a big help... ):P

---

