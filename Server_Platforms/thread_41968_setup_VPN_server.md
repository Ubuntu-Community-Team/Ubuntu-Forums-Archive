---
title: "setup VPN server"
date: 2005-06-15
forum: Server Platforms
---

### Post by lartan on 2005-06-15
Hi,

I like to setup a VPN server on my Ubuntu server. I cannot find a lot of information on a simple way to do this.

I used apt-get install openvpn, can someone help me with information on how to proceed.

My ultimate goal is that I am able to reach my documents on the server if I am connected to the internet on a remote location with my iBook (mac OS X) in the same way as I can use these documents in my home network.

Thanx in advance!
Arne

---

### Post by alastair on 2005-06-15
OpenVPN is pretty easy to configure.

I recommend you take a look at the documentation on the OpenVPN website i.e.

openvpn.net

See the simple examples and have a read.

---

### Post by lartan on 2005-06-17
[QUOTE=alastair]OpenVPN is pretty easy to configure.

I recommend you take a look at the documentation on the OpenVPN website i.e.

openvpn.net

See the simple examples and have a read.[/QUOTE]
 I have tried to follow the simple(st) example on openvpn.net but when I try to start the openvpn server I recieve the error "Starting openvpn: Failed->server."

I dit the following:
1) apt-get install openvpn
2) under root created /etc/openvpn/sercer.conf file with the following content:

dev tun
ifconfig 10.0.0.200 10.0.0.201
secret static.key

3) create the secret key via:
openvpn --genkey --secret static.key (under root)

So when I now try to start the openvpn server with the following line "/etc/init.d/openvpn start" I recieve the following error: "Starting openvpn: Failed->server."

I have no idea what is wrong, can someone help me out??

thanx,
Arne

---

### Post by alastair on 2005-06-18
Why not add a "log", or "log-append" line and look at the OpenVPN log output e.g.

log-append /var/log/openvpn

Then, on any problem, have a look at the log file.

---

### Post by psypher on 2005-09-18
for a bridge mode vpn go here: [http://openvpn.net/wiki/Bridged_Mode_OpenVPN_Server_on_Debian_HOWTO](http://openvpn.net/wiki/Bridged_Mode_OpenVPN_Server_on_Debian_HOWTO)

i followed this to a T and I got it working no problem.(except apt-get bridge-utils instead of bridgeutils) I needed bridge mode to play lan games that rely on broadcast traffic. I got it working tonight and have yet to test out BFME. But I am pretty positive it works as I could see my workgroup from a client vpn connection without any hassle. This will not work with traditional VPN's. 

As a windows client I used OpenVPN Gui for Windows [http://openvpn.se/](http://openvpn.se/) and that just worked. Instead of copying my client keys and config files into /etc/openvpn it went into c:\programfiles\openvpn\config. right clicked openvpn gui, connect and it connected, waited 3 minutes and could see my server side workgroup and could browse all the shares at quite a pleasant speed. connection was between 2 - 512 adsl's and got 40k d/l from server

the config isn't that much different with normal route mode. but route mode is all that most people need. like I said I needed bridge mode for games and workgroup browsing.  just create tun's instead of tap devices and skip out the bridge-utils sections. edit the openvpn init script to not load in bridge mode as well

have a quick look at the openvpn howto on the home page just to gget an idea of how it works.

---

