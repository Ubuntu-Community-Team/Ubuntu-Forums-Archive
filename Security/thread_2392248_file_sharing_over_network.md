---
title: "file sharing over network"
date: 2018-05-18
forum: Security
---

### Post by idkwhatimdoing1.0 on 2018-05-18
On a network I am on my friend says he can see my laptop connected on the serve and it says file sharing. I have zero idea however what in the world I am sharing and when he clicks on it it says t enter a password... Is there a way he could get around that password? I am more concerned about what someone could do with my files

---

### Post by TheFu on 2018-05-18
Well, only you can determine which services/daemons are running to figure out which file sharing method might be enabled.  I would use **netstat** and **lsof** and perhaps the **service** command to see what is running.  If you are on a trusted LAN, things are a little less bad, but if you are at a University or other untrusted LAN, you should disable services you don't specifically need and have a restrictive firewall towards all other systems on the same LAN.

Passwords should not be used as a security measure unless there is no other solution.  Almost always, there are better authentication methods than using passwords.

---

### Post by idkwhatimdoing1.0 on 2018-05-19
ok that is perfect, sadly yes its a school LAN so there should ne some concerns...I am disabelling everything right now. Thanks!

---

### Post by HermanAB on 2018-05-20
Why poke around in the dark?  Run tcpdump and netstat and see what your machine is doing.

---

