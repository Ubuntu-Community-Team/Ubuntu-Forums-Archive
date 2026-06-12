---
title: "Host name on LAN"
date: 2012-04-04
forum: Server Platforms
---

### Post by LordFlick on 2012-04-04
For a school project I have set up a LAMP server on VMware.

I installed another vm running win7 just to see if I can access the web page outside of the server.

 I bridged the connections and set them on the same network 10.1.1.0/24. I can access the page by putting the server ip in 10.1.1.6 but when I put in the host name jdbank.ca I have no luck what so ever.

](*,)

---

### Post by Cheesemill on 2012-04-04
You have 2 options:

1 - Set up an internal DNS server. Difficult to set up but minimal configuration needed on the system you are using to access the web server.

2 - Edit your hosts file. Easy to set up but needs doing on each machine you want to access the website from.

For your purposes I would go with option 2. Edit the hosts file on your Windows 7 VM (you can find it at %systemroot%\system32\drivers\etc\hosts) and add the following line:
```
10.1.1.6     jdbank.ca
```

---

