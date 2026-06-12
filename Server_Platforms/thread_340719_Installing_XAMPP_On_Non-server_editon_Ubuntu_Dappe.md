---
title: "Installing XAMPP On Non-server editon Ubuntu Dapper"
date: 2007-01-17
forum: Server Platforms
---

### Post by Phalangees on 2007-01-17
I've installed everything that is needed for XAMPP (LAMPP) to run but I can only access my page through [http://localhost](http://localhost). I figured that there are some file's that need settings changed to allow my server to be accessed from anywhere by typing in my IP. I already set up all the security stuff and I already configure my router to allow a virtual server but now I need to configure Ubuntu. Any help would be greatly appreciated and I'm somewhat new with linux alltogether so it would be nice if you used dumb people terms. Thanks for all and any help you can give.

---

### Post by kebes on 2007-01-17
Go to this howto:
[http://www.ubuntuforums.org/showthread.php?t=268985](http://www.ubuntuforums.org/showthread.php?t=268985)

And go to "Step 2: Make sure you can access your webserver." Follow the instructions. Essentially go through steps and see where the problem occurs. Basically try, in order:

1. Access page locally (you said this works, right?):
[http://127.0.0.1/](http://127.0.0.1/)
[http://localhost/](http://localhost/)

2. Access page inside network:
[http://192.168.0.100/](http://192.168.0.100/)
Instead of "192.168.0.100", use your internal-network IP address, which you can obtain from by running "ifconfig" on a commandline. So open a terminal:
Applications > Accessories > Terminal
type:
ifconfig
hit enter, and you should see something like:
```

eth0      Link encap:Ethernet  HWaddr 00:22:4C:4C:4C:00
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:89805 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:37610856 (35.8 MiB)  TX bytes:21190178 (20.2 MiB)
          Interrupt:66 Base address:0x4000

```
The "inet addr:" is your internal IP address.

3. Now check using your external IP address. Go to some place like:
[http://www.ipaddressworld.com/](http://www.ipaddressworld.com/)
Which tells you your external IP, and they try going to it:
[http://xxx.xxx.xxx.xxx/](http://xxx.xxx.xxx.xxx/)

4. Lastly, check (if applicable) using your domain name or whatever DNS redirect you might be using:
[http://www.mydomain.org/](http://www.mydomain.org/)



Based on which steps fail and succeed, we will be able to tell what the problem is. For instance if 1 and 2 work, but 3 and 4 fail, then the problem is with your router (check settings again!)... whereas if 1 works but everything else fails, then the problem may be with your Linux firewall (you can install the package "firestarter" which gives you a nice GUI for modifying your firewall rules).

Also, you can then try (see the guide I mentioned at beginning of post) to use a non-standard port, and see if that helps. It's possible that your ISP is blocking port 80.

Hope that helps.

---

### Post by Phalangees on 2007-01-17
Wow thanks. I'll try this all out and let you know how it goes. Thanks again!

---

### Post by Phalangees on 2007-01-17
Ah, Thank's so much. You have no idea how much this means to me. I had 1 number wrong in my router configuration. Thanks!

---

