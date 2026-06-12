---
title: "Trouble with static IP configuration"
date: 2005-05-04
forum: Server Platforms
---

### Post by keldrum on 2005-05-04
I have just set my machine (Hoary, "server" install) to use a static IP but after rebooting I am unable to access my LAN until I bring eth0 down and then up again. Eth0 appears to be up after rebooting and I can ping it's IP but none of the addresses of any other machine on my network.

To be clear, after rebooting I've checked the route entries (using "route" command) and both the lan and default gateway entry are present but I cannot  ping any machine on the lan or on the web. Then, after restarting the NIC (sudo ifdown eth0 and sudo ifup eth0), without making a single change to the configuration, everything works fine.

One possible error is that I was uncertain if /etc/network/interfaces was the correct location to define the default gateway which should be included on boot. 


Content of /etc/network/interfaces
--------------------------------------------
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
#iface eth0 inet dhcp
iface eth0 inet static
address 192.168.22.3
netmask 255.255.255.0
broadcast 192.168.22.255
gateway 192.168.22.254

Any help would be greatly appreciated!

Thanks

---

### Post by chrisf on 2005-05-04
try adding the line:
   auto eth0

---

### Post by keldrum on 2005-05-04
I added "auto eth0" and that does the trick!

I assume that "auto eth0" tells the OS to bring up the NIC automatically on boot instead of waiting for the manual command. I notice the "lo" interface has that line also so I guess it just makes sense.

Thanks for the info.

p.s. I have included my revised /etc/network/interfaces below in case I'm not the only one.

Content of /etc/network/interfaces
--------------------------------------------
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
#iface eth0 inet dhcp
auto eth0
iface eth0 inet static
address 192.168.22.3
netmask 255.255.255.0
broadcast 192.168.22.255
gateway 192.168.22.254

---

### Post by SychoSly on 2005-05-16
[QUOTE=keldrum]I added "auto eth0" and that does the trick!

I assume that "auto eth0" tells the OS to bring up the NIC automatically on boot instead of waiting for the manual command. I notice the "lo" interface has that line also so I guess it just makes sense.
[/QUOTE]

I do not have the "auto eth0" line in my file. Is it necessary, or is it just to bring up the interface if it doesn't do it automatically. 

This thread was helpful. 

I have my ubuntu running an ftp and http server and it gets annoying playing with the DHCP addresses. 

I configured static and it seems to work. Thanks.

---

### Post by keldrum on 2005-05-17
"auto eth0" seems to be necessary but only if you are using a static IP. I'm guessing that otherwise some portion of the DHCP client script will bring the interface up.

Since having changed this line I have rebooted a couple times and the interface always seems to come up without any trouble.

I should mention that while setting a static IP seems to have corrected your problem my guess is that the problem was simply that with DHCP, the address of your server would change and then you could no longer reach it by name. Two possible ways of dealing with this would be to either set up dynamic dns which would reregister the server's address automatically each time it changed or, what would be much simpler, would be to continue using DHCP but create an address reservation in DHCP for the server based on it's MAC address.

I should also mention that FTP is, by deafult, quite an insecure service. You can use SSH/SFTP instead for file transferring without any fear of password snooping. If necessary, there are even free GUI SFTP clients for Windoze (if you must) which greatly simplify moving of files and do so in a much more secure manner than FTP.  

Good luck!

---

### Post by swiftworm on 2005-06-15
I am having a similar problem. I just moved to a place with static IP internet connection. i have done all the configuration ( IP, gateway, netmask, DNS) but i still do not have access to the internet. pinging any address outside the LAN does not work.
when i  >> sudo ifdown eth0
i get       >>ifdown: interface eth0 not configured

i can not access any computer on the network with their names except for their IPs.
I have gone thru the whole forum, tried many things to no avail.

any help will be appreciated.

---

### Post by relix42 on 2005-06-17
[QUOTE=swiftworm]I am having a similar problem. I just moved to a place with static IP internet connection. i have done all the configuration ( IP, gateway, netmask, DNS) but i still do not have access to the internet. pinging any address outside the LAN does not work.
when i  >> sudo ifdown eth0
i get       >>ifdown: interface eth0 not configured
[/QUOTE]

Do you get anything from 'ifconfig eth0'?  If not, it may be a driver/module issue.  If you do, you may want to post the results from 'route -n' and 'ifconfig eth0'.

> 
i can not access any computer on the network with their names except for their IPs.  I have gone thru the whole forum, tried many things to no avail.


Name->IP resolution is handled differently depending on what you are trying to do.  If these are other *nix boxes, you will need either /etc/hosts entries for them or DNS entries for them.  If you are trying to access Windows boxes, you'll need to get Samba running in order to resolve their names to IP addresses.

HTH

---

### Post by LordHunter317 on 2005-06-17
[QUOTE=relix42]Do you get anything from 'ifconfig eth0'?  If not, it may be a driver/module issue.  If you do, you may want to post the results from 'route -n' and 'ifconfig eth0'.[/quote]No, it means that ifdown already thought the interface was down, so it didn't do anything.  He needs to run: 'ifup interface'

> If you are trying to access Windows boxes, you'll need to get Samba running in order to resolve their names to IP addresses.This isn't necessarily true at all.

---

### Post by msgyrd on 2005-06-17
Are you using a router?  I have a linksys router and have to assign static ip's outside it's DHCP address range for the router to let it work.  I didn't see anything about how your network is running, but if a "hardware" router is in there, it might be the cause of your problems.

---

### Post by kiddo on 2005-07-06
Hello folks!
I currently am in a corporate network with my ubuntu laptop. Since I'm the only one who used DHCP, it was mostly okay but today I conflicted with someone else's IP. The reason why I wasn't already static is that it was not working as it should. Meaning I could not ping anything, not even the gateway.

Thanks to this thread, adding "auto eth0" solved it. I'm very happy. But I wanted to know, **has any of you submitted this as a bug?** This is very important; that means the gnome network config tool *forgot* to put that line!.. unless I'm mistaken. Besides, [according to this]("http://www.google.com/search?hl=en&q=site%3Abugzilla.ubuntu.com+%22auto+eth0%22&btnG=Google+Search"), no one did submit this.

---

### Post by RedFever on 2006-01-08
I've had the same problem but thanks to the 'auto eth0' line i also fix the problem.
I thank chrisf may times for that :D \\:D/

---

