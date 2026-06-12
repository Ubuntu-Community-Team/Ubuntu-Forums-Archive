---
title: "Ports"
date: 2009-05-05
forum: Security
---

### Post by hashi856 on 2009-05-05
OK Stupid question time. This probably belongs in the beginner speak forum, but oh well.

What exactly is a port, also what are IPtables

---

### Post by cdenley on 2009-05-05
EDIT: I think I posted the wrong definition. The one below is probably the "port" you had in mind.

Iptables is basically a command-based firewall.
```

man iptables

```
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by lovinglinux on 2009-05-05
A [port](http://en.wikipedia.org/wiki/TCP_and_UDP_port) is like a door between the network and your system. Every communication must enter and exit your system through a port. Like on Hotel's doors, every port has a number. They range from 1 tom 65535. Some ports are used for specific types of communication/protocol. For example, port 80 is for web traffic, port 443 is for secure web traffic (https), 25 is for smtp mail, 21 is for ftp, 22 is for ssh, 6881 is for torrents and so on.

When you browse the web the port is usually not disclosed, but you can specify it on the address. For example try visiting these addresses:

[http://ubuntuforums.org:80](http://ubuntuforums.org:80)
[http://ubuntuforums.org:65535](http://ubuntuforums.org:65535)

The first one works because the Ubuntu forums site server is configured to use port 80 for http connections, as usual. But if you try the second address, it won't work, because you are trying to access the site by entering through the wrong door.

When you type those addresses on the browser, you are requesting a connection with the Ubuntu server. This request also must exit your computer through a port, but not port 80. Outgoing connection ports are selected by your system according too availability. The system will choose a port that is not currently being used. There are some exceptions. For example some programs like Deluge allows you to specify the outgoing ports too.

Despite that several services uses specific ports as standard, you can configure your own server to use a different port for incoming connections. But two services running at the same time cannot use the same port. For example, I cannot configure my web server to use port 6881 and at the same time use a torrent client that accepts connections on port 6881. So ports are used to separate different types of connections. You can have a web server running on your computer on port 80 and a torrent client on port 6881. Despite that both types of connection reaches you through the same IP number of your machine, they will be redirected to the correct service according to the port they are using. This way people can view a web site on your machine at the same time they can share files with torrent.

[IPtables](http://en.wikipedia.org/wiki/Iptables) is part of the Ubuntu firewall framework. Is commonly referred as the firewall. It is basically a tool that controls which doors (ports) are open for traffic and who (IP, protocol) can enter/exit. This is determined by rules that you create using iptables commands or a firewall manager like Firestarter and UFW.

---

