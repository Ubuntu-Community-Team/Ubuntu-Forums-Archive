---
title: "Fail2Ban for Securing SSH"
date: 2014-03-10
forum: Server Platforms
---

### Post by thufirhawat2 on 2014-03-10
I have a 12.04 home server that is basically used to safely store pictures, music and documents for easy access and is RAIDed for redundancy. I also made a personal site and use owncloud and vsftpd (SFTP) to share some pictures with family and friends. There is no personal data stored on the server itself like tax records or anything, so securing the data is not really a concern, but I did want to take some basic practical steps to secure the server from being taken over remotely or having anything malicious installed. Yes, I know I should use certs and turn off password based logins, but I really like the ability to access my server easily from anywhere.

I read an article about SSH brute force attacks, and found a program called fail2ban which uses iptables and reads your logs for failed SSH login attempts. It then matches those attempts to the IP they came from, and bans any IP that fails to login after a preconfigured number of failures. I tested it locally and it works great. However when I tested it publicly, it does not ban the public IP of the device that was trying to log in, it bans my router's local IP address, thus preventing access from any public source, myself included. I am basically just forwarding a random port number I arbitrarily picked on the WAN side to port 22 of my server's local static IP on the LAN side. I did not want to just forward port 22 directly as it seemed like that would make what I was doing obvious to anyone with a port scanner. I am wondering if it is the port forwarding causing this, or if it is the fact that I am translating a different port number instead of forwarding 22 straight through. 

In a way I kind of like how it works now, as anyone who is dedicated enough would probably spoof their IP to keep trying to gain access. Even if they were that dedicated, this would still prevent them, but in a way, they could basically use my own security measures to DoS me. I have the timeout for restricting access set to 10  minutes, so it would take a whole lot of dedication on their part if they wanted to do that though, and the program would only be blocking my SSH and SFTP connections, which I really don't use that often anyway. My website and owncloud still work fine during the lockdown, so I am kind of torn. I would like to know for future reference though how I could configure this to work as it is intended and only block the public IP of the machine that is trying and failing to log in properly. Thanks!

---

### Post by nerdtron on 2014-03-10
> I would like to know for future reference though how I could configure  this to work as it is intended and only block the public IP of the  machine that is trying and failing to log in properly.

I know fail2ban can whitelist certain IPs, for example, your local trusted LAN can fail to login as many times as they like while all other IPs will be banned after a few failed attempts.

---

### Post by Habitual on 2014-03-10
[http://www.fail2ban.org/wiki/index.php/Whitelist](http://www.fail2ban.org/wiki/index.php/Whitelist)

---

### Post by raja.genupula on 2014-03-10
[http://www.thegeekstuff.com/2010/07/fail2ban-howto/](http://www.thegeekstuff.com/2010/07/fail2ban-howto/)

---

### Post by thufirhawat2 on 2014-03-10
I figured it out.

I was aware of the whitelisting capability, but ANY public IP I connected from was causing my router's local IP to be blocked, so whitelisting my router's local IP would be essentially the same as disabling fail2ban. In testing, I was using my iphone on 3g with an SSH app, and then I used a laptop that was tethered to my iphone for internet access (or so I thought), and received the same results each time, when pegging my server with false logins, my router's local IP was being blocked. When I whitelisted my router, nothing ever got blocked no matter how many times I spammed my server with fake creds. 

I just realized that my iphone's wifi was already on when I turned on tethering, so it was connected to the same LAN as the server, so it and anything tethered to it was being routed through my router, so my traffic was not actually leaving the LAN, it was just being locally forwarded right to the server, thus straight from my router's local IP. Once I figured this out, I made sure I was on 3G, and re-tested, then re-tested from my office, and now the proper public IP from where I am is being blocked. Thanks for the replies, sorry for the noob moment, maybe my work will let me change from IOS to droid one day... This thread can be closed.

---

### Post by Habitual on 2014-03-11
> **thufirhawat2 said:**
> sorry for the noob momentNo worries. Glad it worked out!

By the way, you can whitelist using IP, CIDR and MAC hardware address.

---

