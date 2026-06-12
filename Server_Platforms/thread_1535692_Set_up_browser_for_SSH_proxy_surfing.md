---
title: "Set up browser for SSH proxy surfing"
date: 2010-07-21
forum: Server Platforms
---

### Post by yc2 on 2010-07-21
Hello,

A few Chinese friends of mine surf the free Internet through my Ubuntu SSH server. It works for Firefox. They usually use Putty for setting up the connection (Tunnel: Dynamic, local port=8080)

To set up the Firefox client socks must be set as 127.0.0.1:8080. You cannot enter anything else for Firefox proxy settings. (http and others must be left blank)

My friends have problems using other browsers. Today I brought FF, Opera and Chrome portable on a USB-stick to the library to try against my SSH-server. FF worked perfectly. (only socks should be entered)

I tried different settings for Opera and Chrome but none worked. I naturally tried setting http: to 127.0.0.1:8080 but it didn't work. With Opera I just get a white page, it seems like it has connected to "something", I do _not_ get "page not found".

I would also like to know how to set up IE, but it was not possible to try for me today, since the library disallow setting proxies in their systems browsers.

I even got an error "system admin has disallowed this setting" when I tried to set proxy for Chrome. I was susprised by this since my Chrome was brought on a USB-stick. (It was OK to change proxy-settings for portable FF and Opera.)

**EDIT**: I found this link that says that Opera does not support socks proxy
[http://www.opera.com/support/kb/view/194/](http://www.opera.com/support/kb/view/194/)
I am not sure this is still correct?
Is Firefox the only browser able to connect to a SSH server?
Is there any other way to connect than by "socks"??

---

### Post by cdenley on 2010-07-21
Chrome works fine for me, but it seems to use the system's proxy settings, so it could be different when running it on windows. SSH simply acts as a SOCKS server supporting SOCKS4 and SOCKS5. All you need to do is configure the browser to use the SOCKS server. Nothing special. SSH doesn't support any other method of dynamic port forwarding as far as I know. You can setup a VPN server, but that would be much more difficult.

---

### Post by yc2 on 2010-07-21
Thanks cdenley

I am gradually trying to understand this subject. I first set up the ssh tunneling for my friends and it worked instantly, but I more and more realize I haven't really understood the basics.

When I now try Chrome at home I see that proxy-settings opens the system connection panel, like you say. They would never let you do that in an Internetcafé.

Before, I didn't realize the difference between socks and http proxies. Like you say, ssh provides encrypted socks tunnelling, but not http server capabilities.

Since Opera cannot connect to socks-server, I will probably have to set up http-server for this. I am just looking around and it seems the server to install in Ubuntu is called Squid. (Or maybe there are modules that can be added to my Apache?)

Any further information about the basics of this subject much appreciated :D

---

### Post by cdenley on 2010-07-21
Apache can also act as an HTTP proxy server. I'm not sure which is easier to configure, as I've never used squid.

---

### Post by yc2 on 2010-07-21
You suggested VPN.

I assume "every problem" would be solved with VPN? If my friends start a VPN client they can then surf with any browser or do anything they like (like ftp, pop3 etc)??

Right now, with SSH, just for precaution, I have to give my friends the "iron bar shell". It is not an obvious thing to restrict SSH users. But I assume with VPN they cannot access my computer, as they can with SSH?

I have read that there are two VPN servers?
Poptop or openVPN

I do not know which one to try? I give priority to stability and simplicity in installation ;)

---

### Post by cdenley on 2010-07-21
I've never used poptop. OpenVPN isn't easy to configure, especially if you want to route traffic to the internet. It would also require you install an OpenVPN client with a tun/tap driver on the client system. You don't need to give users a valid shell in order to allow dynamic port forwaring with SSH. You can set their shell to /bin/false then have them connect without executing a shell (ssh -N user@server), or you can set their shell to a script that does nothing but wait for a line of input.

---

### Post by yc2 on 2010-07-21
Thanks cdenley, I learn useful things today.

I didn't know (think of that) you could just write your own script and give to SSH-users. (I guess it would be something like "if $1 != exit do nothing, else exit"  ? )

So i will have to do some reading up on the OpenVPN then, I guess these are good starting points?
[http://openvpn.net/index.php/access-server/quick-start-guide.html](http://openvpn.net/index.php/access-server/quick-start-guide.html)
[http://openvpn.net/index.php/open-source/downloads.html](http://openvpn.net/index.php/open-source/downloads.html)
[http://ubuntuguide.org/wiki/Ubuntu:Lucid#VPN_servers](http://ubuntuguide.org/wiki/Ubuntu:Lucid#VPN_servers)

---

