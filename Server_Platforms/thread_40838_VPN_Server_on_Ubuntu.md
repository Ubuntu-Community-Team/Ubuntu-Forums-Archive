---
title: "VPN Server on Ubuntu"
date: 2005-06-10
forum: Server Platforms
---

### Post by echokilo on 2005-06-10
What VPN Server is easiest / best to install and configure with Ubuntu? I need Windows XP VPN Clients to be able to login.

I have heard of PopTop, but am open to all suggestions.

---

### Post by alastair on 2005-06-12
I'd highly recommend OpenVPN :

openvpn.net

---

### Post by echokilo on 2005-06-13
Alright, I installed OpenVPN and made the configuration files. However, I cannot seem to find:

1) Name & Location for config file on Windows Client machine.
2) The command to start Openvpn server on Linux.

Can you assist with that?

---

### Post by alastair on 2005-06-13
Ofcourse :-)

On windows, you can just drop a ".ovpn" config file into :

Program Files/OpenVPN/config/

right-click on it and "Start OpenVPN on this ..." to run it. A DOS shell opens up - look for :

"Peer connection initiated with ..."

Close DOS window to stop VPN.

On Linux, OpenVPN startup looks in :

/etc/openvpn

for .conf files. To start OpenVPN :

/etc/init.d/openvpn start

to stop :

/etc/init.d/openvpn stop

Check your system logs for the same "Peer connection initiated with ..." line.

---

### Post by echokilo on 2005-06-13
I think I'm getting close.

Where should the static.key be located on the windows machine and if I'm testing the tunnel locally on my 192.168.2.* network, what should I make the IP addresses in the config files?

This is so cool.

---

### Post by relix42 on 2005-06-13
IIRC the static key location is referred to in the .ovpn file on the Windows box.  Just make sure that they match.

On the IPs - all normal IP routing rules apply.  If you have some "interesting" routing needs, check the openvpn.net site - they have some very good examples of how to make just about any type of routing work corectly.

---

### Post by echokilo on 2005-06-14
I got it to work and I'm totally psyched! One last question....when I start the service on my Ubuntu server, it says "sequence completed" and doesn't give the command prompt back until I stop the service by using control-c.

Therefore, I have to open a new terminal to do other things - is that normal?

---

### Post by alastair on 2005-06-14
It is no problem to start the VPN in the foreground in a window - and carry on elsewhere. 

As a service though, it can run in the background until stopped i.e.

sudo /etc/init.d/openvpn start
sudo /etc/init.d/openvpn stop

Or started at boot (perhaps not what you want - I do not do this)

But no problem starting it manually, and leaving it running until CTRL-C or a window close. This is often how one does it on XP (close the DOS shell to shutdown). No problem.

---

### Post by psypher on 2005-09-18
for a bridge mode vpn go here: [http://openvpn.net/wiki/Bridged_Mode_OpenVPN_Server_on_Debian_HOWTO](http://openvpn.net/wiki/Bridged_Mode_OpenVPN_Server_on_Debian_HOWTO)

i followed this to a T and I got it working no problem.(except apt-get bridge-utils instead of bridgeutils) I needed bridge mode to play lan games that rely on broadcast traffic. I got it working tonight and have yet to test out BFME. But I am pretty positive it works as I could see my workgroup from a client vpn connection without any hassle. This will not work with traditional VPN's. 

As a windows client I used OpenVPN Gui for Windows [http://openvpn.se/](http://openvpn.se/) and that just worked. Instead of copying my client keys and config files into /etc/openvpn it went into c:\programfiles\openvpn\config. right clicked openvpn gui, connect and it connected, waited 3 minutes and could see my server side workgroup and could browse all the shares at quite a pleasant speed. connection was between 2 - 512 adsl's and got 40k d/l from server

the config isn't that much different with normal route mode. but route mode is all that most people need. like I said I needed bridge mode for games and workgroup browsing.  just create tun's instead of tap devices and skip out the bridge-utils sections. edit the openvpn init script to not load in bridge mode as well

have a quick look at the openvpn howto on the home page just to gget an idea of how it works.

---

### Post by jlist on 2005-09-19
poptop is a PPTP VPN server. Supposedly it works with Windows built-in VPN client. So, no client software is required. I said "supposedly" because I failed to make it work. Some other people did though. You can try it out and post back :)

---

### Post by lonetree on 2005-10-05
just a question. 

Can I view my LANs after connected to the VPN Server? 

Although I did not get sucessful in setting up OpenVPN, I gotit working with pptpconfig. But after loggin in, I couldn't view my LAN's PC, I can only see the server.  What should I do to be able to view all the LAN pc? I have seen someone mention that I should have 2 ethernet card, is this necessary?

Hope someone could enlighten me a bit.

Thanks

Regards,

---

### Post by Ubuntu Warrior on 2005-10-28
No problem viewing your LAN with OpenVPN. We r just struggling at the moment with some clients working and some not. The configs seem identical and this has us stumped! Maybe something to do with invalid certs/keys or OpenSSL updates? Have rebuilt another test OpenVPN server but still get the same problem.

---

