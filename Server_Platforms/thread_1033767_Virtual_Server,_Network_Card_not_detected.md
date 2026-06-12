---
title: "Virtual Server, Network Card not detected"
date: 2009-01-07
forum: Server Platforms
---

### Post by RickshawDriver on 2009-01-07
I am setting up a fresh virtual server in hyper-v running 8.04 server.  As I was setting it up I noticed it did not recognize the network card.  I did assign the card during the virtual server set up so I know it's available to the Linux server.  

I set a static IP address up by adding the iface eth0 inet static entry.  Upon "sudo /etc/init.d/networking restart" I get the error "eth0 : ERROR while getting interface flags".

I searched for the issue and see others that have had the problem, but never was able to find a solution.  Any help or shove in the right direction would be greatly appreciated.

Regards

---

### Post by whoop on 2009-01-07
Haven't tried this myself but you can try using Legacy Network Adapter.
Read the comments in this blog: [http://www.sriramkrishnan.com/blog/2008/03/running-ubuntu-on-windows-server-2008.html](http://www.sriramkrishnan.com/blog/2008/03/running-ubuntu-on-windows-server-2008.html)

---

### Post by dougpan on 2009-01-07
Seems like its a problem with the network not coming up in a Dom-U after the domain creation.

See if the following occurs when you execute the following:
/etc/init.d/networking restart

* Reconfiguring network interfaces…
eth0: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0.

If this is the case, it seems that udev is binding the domain’s NIC to the initial MAC address of the vswif and therefore the domain doesn't recognize the NIC

You can try editing the two files where the udev rules bind NICs to MAC addresses. 

Edit “/etc/udev/rules.d/70-persistent-net.rules” and comment out lines that look similar to this:
SUBSYSTEM==”net”, DRIVERS==”?*”, ATTRS{address}==”00:16:3e:2b:2f:6a”, NAME=”eth0&#8243;

Since the above file is automatically generated, you have to edit “/etc/udev/rules.d/75-persistent-net-generator.rules” and comment out lines that look similar to this:
SUBSYSTEMS==”xen”, ENV{COMMENT}=”Xen virtual device”

Commented out the following line too. You want to stop *any* generation.
ACTION==”add”, SUBSYSTEM==”net”, KERNEL==”eth*|ath*|wlan*|ra*|sta*” NAME!=”?*”, DRIVERS==”?*”, GOTO=”persistent_net_generator_do”

Restart the Dom-U,  and see if the network comes up.

Doug

---

### Post by RickshawDriver on 2009-01-08
Thank you for the replies.

When I open up 70-persistent-net.rules I only see the following:
```
This file maintains persistent names for network interfaces.
See udev(7) for syntax.

Entries are automatically added by the 75-persistent-net-generator.rules file; however you are also free to add your own entries.
```

Since I saw nothing there I thought I would continue commenting out the lines you suggested in the template file and let it regenerate the first file after the change.  I did not see your exact line, but these are the ones I commented out since they are the only ones that looked similar.
```
SUBSYSTEMS=="xen", GOTO="persistent_net_generator_end"
```

```
ACTION!="add", GOTO="persistent_net_generator_end"
SUBSYSTEM!="net", GOTO="persistent_net_generator_end"
```

I am unsure of how to "restart the Dom-U" so I assumed it was the networking restart command.  I did so and received the same messages as before.  eth0: ERROR while getting...

---

