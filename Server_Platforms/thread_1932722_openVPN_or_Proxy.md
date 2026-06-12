---
title: "openVPN or Proxy?"
date: 2012-02-28
forum: Server Platforms
---

### Post by crazyfruitbat on 2012-02-28
Hi guys,

I live over in Japan and I'm wanting to view some TV from home like the BBC iplayer etc in the UK which is IP blocked.

I have a Linode box running a standard LAMP web server on Ubuntu Lucid and I run a couple of small websites off it but I'd like to be able to use the IP address of the system there to allow me to fake my IP here in Japan (and thus let me watch the blasted rugby!).

I followed a Openvpn tutorial over at linode but it failed pretty badly, it connected but gave me no traffic. 

Is this the best way of doing this or would a Proxy be a better solution? 

cheers
C

---

### Post by zeljkojagust on 2012-02-28
Did you try to solve your problem by contacting your provider in Japan? You can try Tor project, but I don't promise it will work.

---

### Post by SeijiSensei on 2012-02-28
You could install the Squid proxy on the Linode box, then configure your browser to use the proxy over the OpenVPN tunnel.  If the Linode end of the tunnel has IP address 10.1.1.1, you'd just configure the browser to use 10.1.1.1:3128 as the proxy.  You'll need to adjust squid.conf to enable traffic over the tunnel to use the proxy.

---

### Post by kevdog on 2012-02-28
I used the instructions in this thread to create a bridged VPN using OpenVPN: [http://ubuntuforums.org/showthread.php?t=1762152&highlight=openvpn](http://ubuntuforums.org/showthread.php?t=1762152&highlight=openvpn)

I can confirm it works on 11.10.  My only issue is that it was rather slow than when accessing the VPN remotely -- likely do to my comcast basic network speeds.

One thing you might consider -- and this is what I ended up doing to improve the speed -- was using a combination of ssh/X11 forwarding.  If all you need to do is tunnel your browser -- you can easily do this over ssh using a socks proxy which is built into ssh.  If you need additional ports, it can also be done to accomodate other services.  

Basic X11 forwarding to get a graphical interface works OK -- if its not too resource intensive.  I've been able to run an xcfe-panel that gives me a very basic gui to the remote ubuntu box from where I can use gedit and other gnome programs.  I can run a browser remotely over X11 -- but the performance is very poor.

---

### Post by kgatan on 2012-02-29
If you are the only user of the VPN and you want easy deployment and management id recommend OpenVPN Access Server.

Its a configuration that includes 2 concurent users so if you need more it costs money.
Easy to install on ubuntu and all later configuration is done via web gui.

I use it on my trips to China and it works like a charm.

Im not sure if its in the reposatory but you can download a deb package from [www.openvpn.org](www.openvpn.org).

---

### Post by enjoijesus94 on 2012-02-29
You Can Try Tor Like Stated Above.

thats What I Use.

---

### Post by SlugSlug on 2012-02-29
I use this for a few things, works great

[http://embraceubuntu.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/](http://embraceubuntu.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/)

& with putty

[http://thinkhole.org/wp/2006/05/10/howto-secure-firefox-and-im-with-putty/](http://thinkhole.org/wp/2006/05/10/howto-secure-firefox-and-im-with-putty/)

---

