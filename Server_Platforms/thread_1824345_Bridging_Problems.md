---
title: "Bridging Problems"
date: 2011-08-13
forum: Server Platforms
---

### Post by PierreRobiquet on 2011-08-13
Hello,

I'm currently trying to set up OpenVPN on my Ubuntu Server, however I'm having trouble setting up bridging. I am following the tutorial for bridging that is located on the Wiki here:

[https://help.ubuntu.com/11.04/serverguide/C/network-configuration.html#bridging](https://help.ubuntu.com/11.04/serverguide/C/network-configuration.html#bridging)

At the current time my /etc/network/interfaces looks like this (default from Ubuntu install):
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```However once I add the bridge, it seems that my eth0 is no longer able to get an IP address, I assume it's something to do with my configuration so here is the "broken" configuration:
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto br0
iface br0 inet static
        address 192.168.0.10
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.1.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

```If anyone could point out any errors that I've made I would very much appreciate it, I can create a CA fine and follow most of the rest of the tutorial however the bridging seems to be my main problem. Normally I would SSH into the server but obviously when I fry the network configuration I have to manually login, however I find that restoring the old interfaces file does not fix the problem along with doing /etc/init.d/networking restart and instead I have to restart the whole server whilst br0 still remains in ifconfig is there something else I need to restart?

Thanks,

---

### Post by YesWeCan on 2011-08-14
Well, you have to bridge two or more interfaces. You have added eth0 but nothing else. Presumably you want to add tun0 or tap0?

I did this differently. I followed this: [http://openvpn.net/index.php/open-source/documentation/miscellaneous/76-ethernet-bridging.html](http://openvpn.net/index.php/open-source/documentation/miscellaneous/76-ethernet-bridging.html)
And set up entries in /etc/network/interfaces to run bridgeStart and bridgeStop shell scripts:

```
# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
     address 192.168.1.123
     network 192.168.1.0
     netmask 255.255.255.0
     up /etc/openvpn/bridgeStart
     down /etc/openvpn/bridgeStop
```

---

### Post by PierreRobiquet on 2011-08-15
Thanks for the help, I used the guide you provided and it seemed to work rather well however I had to add ip route add default via 192.168.1.1 to the bottom of the bridge-start command or else I was unable to leave the subnet. However I'm now having a different problem, it seems that every time I attempt to restart the OpenVPN service to bring it up I instead receive the following error:

```
 * Starting virtual private network daemon(s)...
 *   Autostarting VPN 'server'
device tap0 is already a member of a bridge; can't enslave it to bridge br0.
   ...fail!

```

Both tp0 and br0 exist within ifconfig and as far as I know all of the other network configuration is correct however I cannot figure out what is causing this error message.

---

### Post by YesWeCan on 2011-08-15
Would you post your vpn server config file?

---

### Post by PierreRobiquet on 2011-08-15
Sure thing, thanks for all your help by the way, OpenVPN is the most confusing service I've set up out of SSH, Samba, Murmur and Apache so far. Here's my OpenVPN configuration file:

[http://pastebin.com/MZJQ56Ww](http://pastebin.com/MZJQ56Ww)

---

### Post by YesWeCan on 2011-08-15
You should try understanding mdadm...:-k :P

My server.conf is almost identical to yours except I don't have the up/down in lines 10 & 11. I think since you are already bringing up the bridge in /etc/network/interfaces these lines are not necessary. This may be why it complains that tap0 is already bridged.
I also have an 'mssfix 1200' directive because I found I was having big problems with nautilus file transfers: the transfers worked but Nautilus' progress bar lost the plot and I couldn't even shut Nautilus down without rebooting (there has been a bug report open about this for a couple of years now).

I should add that of all the linux software I have used, OpenVPN rates right up there in the top few in terms of reliability. It just seems to make bomb-proof tunnels in my experience.

---

### Post by PierreRobiquet on 2011-08-15
Thanks for your help, you finally got my VPN running, all I had to do was comment out the up and down scripts and everything seems to be running smoothly. I can connect from remote destinations. I even did a quick sniff with Wireshark and everything went smoothly. Does anyone recommend any good OpenVPN applications for Windows? I tried the offical client but it seems to have wanted a password and I couldn't locate a CLI application to use with my ovpn file.  At the moment I'm using OpenVPN portable, but I'm sure there are better alternatives.

---

### Post by YesWeCan on 2011-08-15
I'm using the official client on Windows 7. I find it much easier to use than the linux client because it is all taken care of in GUIs. The .ovpn file is edited from the GUI menu. You have to start the "OpenVPN GUI" as Administrator.
Can you elaborate on the problem you encountered?

---

### Post by PierreRobiquet on 2011-08-15
With OpenVPN portable I can connect perfectly to the network with my configuration file, however when I import it into the offical OpenVPN client it is stuck on "Connecting" after closing the box out it seems that it may have connected to the VPN (I haven't properly checked it doesn't seem to create logs either) however it reports very strange things:

[IMG]http://img684.imageshack.us/img684/1808/mainoptim.png[/IMG]

[IMG]http://img803.imageshack.us/img803/8200/statusoptim.png[/IMG]

EDIT: Here are the two separate log files from the applications, it seems the offical client can't perform the TLS handshake:

[http://pastebin.com/LDxjSq0a](http://pastebin.com/LDxjSq0a) Offical OpenVPN Client
[http://pastebin.com/RurrnXQY](http://pastebin.com/RurrnXQY) OpenVPN Portable

---

### Post by YesWeCan on 2011-08-15
"TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)" means that the client phoned the server and didn't get a response.

It's all Greek but two differences may be significant:

The server addresses are different:
UDPv4 link remote: 94.175.129.112:1194
UDPv4 link remote: 192.168.1.136:1194

The one that works logs that it is "using 'ta.key' as a OpenVPN static key file" but the one that fails records "tls-auth using INLINE static key file". It would be an issue if it can't find the ta.key file.

---

### Post by PierreRobiquet on 2011-08-15
The server addresses aren't that much of a concern, I have it set to point at my DynDNS address and I assume the portable client notices I'm still on my own network and as such just connects directly. However, I don't understand why it cannot locate the ta.key file, it is in the same folder as the configuration file and the one that OpenVPN portable uses unless there is somewhere special I'm supposed to place the key itself?

---

### Post by YesWeCan on 2011-08-15
I could be wrong about the ta.key file. It might just be reporting the thing with different wording. I'd change the two to use the same IP address just to eliminate that difference.

---

### Post by PierreRobiquet on 2011-08-15
Yep, now the official client is pointing towards my internal IP rather than the DynDNS domain however I'm still having issues. I'll try installing OpenVPN in a VM to see if it's a host issue. Within the VM the connection seems to fail too, I really don't see why it doesn't work they're using the exact same configuration files!

---

### Post by PierreRobiquet on 2011-08-16
I'll just use the open source solutions, I've tried about five different OpenVPN clients for Windows and all of them work apart from the official client.

---

