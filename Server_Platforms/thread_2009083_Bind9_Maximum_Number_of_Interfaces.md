---
title: "Bind9 Maximum Number of Interfaces"
date: 2012-06-23
forum: Server Platforms
---

### Post by dashpilot79 on 2012-06-23
Hello,
  I had a working Bind9 Configuration that listened on a 4 Interfaces (Local, Eth1, Eth2, and Tun0).  I didn't want to have listen to all by default because Eth0 is untrusted and I don't want it to answer Responses on that Interface.  Everything was working fine until I did a recent update, didn't remember seeing and Bind Updates in it, but now it doesn't like having 4 interfaces in there and I had to put place any in the configuration file.  Has anyone else had a similar problem?

Thank You,

---

### Post by SeijiSensei on 2012-06-25
Are you saying the update overwrote named.conf?  That's the only place I know of where you control the interfaces bind9 uses with the "listen-on" directive that's part of the global options in named.conf.

---

### Post by dashpilot79 on 2012-06-27
Nope it didn't overwrite named.conf  thats intact.  Its odd I have the 4 interfaces and the first three are working just fine, but it doesn't appear to be listening on the 4th, which is also the last one listed.  The config hasn't changed from when it used to work under that setup.

---

### Post by SeijiSensei on 2012-06-28
Is it the tunnel interface that doesn't work?  It didn't happen to change IP addresses or not come up for some reason, right?  Just trying to eliminate the obvious.  

I'll bet the order of events at boot is the problem.  Did you reboot the system after the updates?  I see that openvpn starts after bind9 in /etc/rc2.d/.  The same is true on my CentOS 6 public DNS server.  That's a problem for those of us with bind9 bound to a tunnel IP.

I just ran an experiment where I shut down both bind9 and openvpn, then started bind9 followed by openvpn.  When bind9 started, it had no tun0 interface to bind to, and it did not detect the later creation of the tunnel by openvpn.   So there was no listener on tun0 and DNS queries to that interface returned "no servers could be reached."  Once I restarted bind9, it detected and bound to the tun0 interface and queries to the tunnel IP resolved immediately.

The short-term fix is to restart bind9 after the tunnel starts.  If you run a script with the "up" directive in openvpn.conf, you could add a "service bind9 restart" to the commands.  An alternative long-term fix is to reorder the startup services so openvpn runs ahead of bind9, but see the caveats below.

You can do this with update-rc.d.  Currently at startup bind9 has priority 15 and openvpn 16.  I'd like to assign openvpn priority 14 so it will start before bind9.  You can do this as follows:

```

sudo update-rc.d -f openvpn remove
sudo update-rc.d -f openvpn defaults 14 86

```

I also changed the shutdown priority from 80 to 86 so openvpn shuts down after bind9 not before.  On RedHat flavors like CentOS, you change the "chkconfig" values at the top of the service script in /etc/init.d/.

[**Edit**]  Since writing this, I've realized the drawback to this approach.  You won't be able to write OpenVPN configuration files that use symbolic hostnames, only IP addresses.  For instance, if you have a client tunnel that uses the "remote" directive, you'll need to use the remote server's IP address rather than its hostname, or have an entry for the server in /etc/hosts.  

**The more robust solution is thus to restart the name server using an "up" script** as I described above.  If you don't mind using IP addresses instead of hostnames, or you are diligent about keeping an entry in /etc/hosts for any machines referenced by OpenVPN, you can reverse the order of startup.

---

### Post by dashpilot79 on 2012-06-30
Before your message, I was begining to suspect there was a timing issue since the Tun device seems to come and go, I need to play with it when I get home. Thank You for the help.  If it solves it I'll mark the thread as such. 

Thank You,

---

### Post by dashpilot79 on 2012-07-21
Sure enough it was a issue with the Exisitance of one of the interfaces.

---

