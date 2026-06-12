---
title: "Setting up LTSP"
date: 2015-02-23
forum: Ubuntu/Debian BASED
---

### Post by stevecook on 2015-02-23
I  have recently set up and have got reliably running an ltsp server and client on Ubuntu Mate 14.04. Though, I have had considerable difficulty getting it up and running. I initially followed this instructional ([https://www.thefanclub.co.za/how-to/how-create-ubuntu-1104-x64-ltsp-server-32bit-thin-clients](https://www.thefanclub.co.za/how-to/how-create-ubuntu-1104-x64-ltsp-server-32bit-thin-clients)). It works, but I have had to do some extra stuff to get it going.

 Firstly, I had to remove the network manager and then reinstall network-manager-gnome. I also had to leave network management to "false" in the network manager config file. No idea why, just trial and error showed this to be the case. It I didn't reinstall the gnome manager, then the ltsp dhcpd server would not start no matter what. Similarly, if I did not set network management to false.

 Secondly, I had to copy the ltsp dhcp.conf file's contents over to the etc/dhcpd/dhcp.conf file. Unless those contents are in there as well, it will not work. Also, I need to have a non-ltsp full fat client machine physically linked to eth0 in order for my dhcpd and tftp servers to start. I start them with a startup script on the server (though it has to have a prefixed sleep command of around 30 seconds other wise the servers will still fail to start properly). Obviously, I have to start the full-fat client eth0-connected machine first, so the server has got an active connection from bootup, otherwise the dhcpd server will fail to start.

 Having once started the dhcpd and tftp servers in the way described, I then fire up a virtualbox VM ltsp client on the server and it boots successfully. Once it is booted, I can disconnect the bare metal full fat client from eth0, I mentioned earlier. From this point, any physical ltsp client connected to eth0 on the server will now boot. If I tried to start the vm ltsp client before an active connection was established with the full fat bare metal client, as described above, it would fail for the reasons already given. However once booted, and then kept open, the ltsp vm client keeps the dhcpd server connection alive for any other real world ltsp clients. It's a bit messy, but it works. This means I can then shut down the full-fat client that was initially connected to eth0.

 Given all of the above, what I am wanting is a way to establish some kind of fake eth0 connection at bootup so that I can start the dhcpd and tftp servers without a real world machine being connected to eth0 and so they wont fail because they will "think" that the connection is active and so will start. At which point, the VM ltsp client should boot. Indeed, it may even mean I don't need the VM ltsp client as a "seed" client to keep the dhcpd connection alive for all other real world ltsp clients.
 
I should add, for completeness, when I say, that without the full-fat client machine being connected at boot-up on eth0, the dhcpd server "fails", what I mean is that is does not "appear" to fail. That is to say, it gives the "OK" in a terminal as if it has started. However, the ltsp vm client (or a real world ltsp client) will not boot as a consequence of not receiving an address. Only when I boot the server machine with an ordinary full-fat client machine attached to eth0, and then start the dhcpd and tftp servers, will the ltsp vm client subsequently boot.
 
One final weirdness:

 as for updating the ltsp image with new software, I obviously do this by chrooting to the image. However, I am unable to download any software from the internet/repositories etc, whilst inside ltsp chroot, unless the dhcpd server is properly up and running on the server. However, that can only happen if there is an active connection on eth0. Obviously I don't want an ltsp client running while I am updating the image. So, in order to do any updating, I have to close all ltsp clients and reconnect my ordinary full-fat client machine to eth0.

 That's it, Any advice folks?

 Edit to add:

 I should say, this was NEVER an issue up until Ubuntu 13 (and it's even recently become an issue on the latest downloadable ISO's of 12.04). So what on earth did Canonical do differently from that point?

My guess is it's the bleeding network manager.......

---

