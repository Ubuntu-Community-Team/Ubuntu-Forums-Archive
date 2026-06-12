---
title: "Squid, VPN or something else?"
date: 2008-08-13
forum: Server Platforms
---

### Post by dmitrijledkov on 2008-08-13
I travel a bit. And I would like to set up secure connection via my home computer, so that any sites and resources I access would come from my home ip address and then forwarded to my laptop. As I understand it I need proxy server at home.

Googled up squid, but so far I have only found username&password authentication method. This won't be good enough because someone could brute force it and abuse my proxy. Access control by ip won't work, cause I will never know what ip I will have to allow.

After browsing a bit more I found VPN, ssl tunnel, IPSec and 802.1x if I understand right, after I will be authenticated through these I will be able to access eg proxy server@home as if I was on my home wifi. And in addition connection between me and home server would be encrypted.

Could you please point me in the right direction on what I need to use to setup secure encrypted connection and proxy which only I will be able to access.

---

### Post by erwall on 2008-08-13
How about nph-proxy?  All you do is drop the cgi file in your cgi-bin and that's it.

[http://jmarshall.com/tools/cgiproxy/](http://jmarshall.com/tools/cgiproxy/)

Could .htaccess the cgi-bin directory I guess also?

---

### Post by moonpup on 2008-08-13
This is what I do at home and it works great. It's a bit overkill as I do use squid as a proxy, but you could also use the -D flag with ssh to create a socks proxy to hide your browsing.

First off this is a multi step process...I'll give you a brief overview but you'll need to learn about configuring squid if you don't know how. Here's a good link to follow and includes how to setup squid to use a username and password before it allows you access to it. It's written based on rpm (redhat) commands. You'll need to know the ubuntu equivalents. You can most likely stop at the point where it tells you about forcing users to use the proxy section.

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid)

1) The remote server must be running a proxy server... in this case most likely squid. Squid should be setup to only accept connections from the local network only. Do not open this up to the outside world. Also, using the default port 3128 is fine.

2) Follow the above how-to which will give you a basic, but good enough install to make this work. Again, you can most likely stop at the point where it tells you about forcing users to use the proxy section.

3) You won't (and don't) open a port on the firewall for squid as you'll be connecting through ssh

4) On your workstation, set firefox to use localhost on port 3128 for proxy settings.

5) Make your ssh connection to the server with ssh -L 3128:localhost:3128 username@server

Remember to change port #'s if necessary. If you remote server accepts ssh connection on a different port from 22, then add a -p port# to the above ssh command. As long as you are not blocked by a firewall, you should be good to go. Just open the ssh connection first and then firefox.

Hope this helps!

---

### Post by windependence on 2008-08-14
OpenVPN would work for you also and would probably be easier to set up than some other solutions.

This one is for Dapper but it should be very close:

[http://www.techimo.com/forum/linux-unix/176687-howto-openvpn-ubuntu-dapper.html](http://www.techimo.com/forum/linux-unix/176687-howto-openvpn-ubuntu-dapper.html)

-Tim

---

### Post by MJN on 2008-08-14
I recommend reading [this]("http://ubuntuforums.org/showthread.php?t=879400") recent thread which covered some of the options available to you (at the very least it will stop everyone having to cover old ground again!).
 
I personally would recommend SOCKS proxying over SSH as being perfect for your requirements - it is secure (key-based authentication) and is easy to set up (indeed it doesn't need setting up as your server already supports it if you've got SSHD installed).
 
Mathew

---

