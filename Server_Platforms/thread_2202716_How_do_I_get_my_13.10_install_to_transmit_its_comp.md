---
title: "How do I get my 13.10 install to transmit its computer name back to my router?"
date: 2014-01-30
forum: Server Platforms
---

### Post by Chris of Arabia on 2014-01-30
At the moment, the computer names of the windows devices (and HP OfficeJet & QNAP) quite happily transmit their computer names back to my NetGear WNR2000. My Ubuntu 13.10 server install (and iOS devices for that matter) don't. So when I go into the router's 'Attached Devices' page, all those that are currently attached show up along with their MAC addresses, but the Ubuntu box and iOS stuff don't have a 'listed 'Device Name'. Is there a way of getting Ubuntu to pass its computer name back to the router?

---

### Post by Iowan on 2014-01-30
IF you're using DHCP for a server IP address, you can modify */etc/dhcp/dhclient.conf*.
This line is *supposed* to send the hostname:
```
send host-name "<hostname>";
```
but I've had better luck hard-coding the name between the quotes:
```
send host-name "myserver";
```

---

### Post by papibe on 2014-01-30
> **Iowan said:**
> IF you're using DHCP for a server IP address...
and if you are not using DHCP because you set up an static LAN IP on the server itself (common source of that problem), I'd recommend going back the default DHCP settings on the server, and setting a DHCP **reservation** on your router.

It will work just as an static IP, but since the router hands the address, the router will know the server's name, MAC, and of course its IP.

Just a thought,
Regards.

Note: the reservation has to be outside the dynamic DHCP range.

---

### Post by Chris of Arabia on 2014-02-01
The server was set up with a static IP, but I've since reverted it to DHCP. There is a reserved address for the server in my Netgear WNR2000 anyway. For a number of reasons, the router has had its power recycled more than once over the last couple of days, but the server still doesn't show up with its name included. I've taken a look at the file mentioned and it shows as follows:

```
#send host-name "andare.fugue.com";
send host-name = gethostname();
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;



```

i'm looking at that second line there, and it's constructed somewhat differently to the example above. I need to check the file again, but I'm wondering where gethostname() is getting its value from. I'll go look...

---

### Post by Chris of Arabia on 2014-02-01
There's a 'Request' in there that refers to 'host-name', but that's about it. No clues as to where it's picking it from though.

---

### Post by SeijiSensei on 2014-02-03
The function get_hostname() works in C, but I doubt it will work in dhcpd.conf.  Just put the machine's actual host name in there.  You should not include its domain; just the host part.

---

### Post by Chris of Arabia on 2014-02-07
OK, I've now amended /etc/dhcp/dhclient.conf to read

```
send host-name "PIGLET2";
#send host-name = gethostname();
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
```

and all seems well. My router now recognises it when it's connected. Case closed and thanks all. :)

---

