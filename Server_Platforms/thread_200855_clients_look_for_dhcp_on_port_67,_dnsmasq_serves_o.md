---
title: "clients look for dhcp on port 67, dnsmasq serves on 53??"
date: 2006-06-20
forum: Server Platforms
---

### Post by tymanthius on 2006-06-20
Started this over here, [http://ubuntuforums.org/showthread.php?t=194075](http://ubuntuforums.org/showthread.php?t=194075) but needed a better title.

Essentially, I'm trying to set up a server, but dhcp isn't working.  I have dnsmask installed, and it appears to be working, but nothing on my network can find a dchp server.

My server says it's serving bootp on port 67, and dhcp on 53.  When my X/Ed/Unbuntu machines go searching for an IP, they search on port 67, but find nothing.  

Any ideas on why this would be?

---

### Post by Iowan on 2006-06-21
[http://www.windowsnetworking.com/articles_tutorials/Understanding-DHCP-Protocol-Part1.html]("http://www.windowsnetworking.com/articles_tutorials/Understanding-DHCP-Protocol-Part1.html") 
[http://www.dhcp-handbook.com/dhcp_faq.html#wppdd]("http://www.dhcp-handbook.com/dhcp_faq.html#wppdd")

From the brief research I've done, port 67/68 are used for **dhcp**, port 53 is for **dns**.

---

### Post by tymanthius on 2006-06-21
[QUOTE=Iowan][http://www.windowsnetworking.com/articles_tutorials/Understanding-DHCP-Protocol-Part1.html]("http://www.windowsnetworking.com/articles_tutorials/Understanding-DHCP-Protocol-Part1.html") 
[http://www.dhcp-handbook.com/dhcp_faq.html#wppdd]("http://www.dhcp-handbook.com/dhcp_faq.html#wppdd")

From the brief research I've done, port 67/68 are used for **dhcp**, port 53 is for **dns**.[/QUOTE]


Thanks, that makes sense.

But I still don't understand why I'm not getting dhcp to work. dnsmasq DOES provide that, right?

---

### Post by tymanthius on 2006-06-23
Ok, install Breezy on my server, put dnsmasq on, and POOF!  it works for dhcp.  Got ipmasq installed, and now my subnet can use the internet.

However, on my subnet, if I type in (from the server) 'ssh kidsputer'  It says no such hostname.  

I thought one of the things dnsmasq was supposed to do was make that work.

---

### Post by tymanthius on 2006-06-23
An interesting note:

when, from kidsputer, I 'ping kidsputer' it resolves to 127.0.0.1, as local host.  And when I do 'ping ftcent' (my server) from kids puter, it does the same thing.

---

### Post by tymanthius on 2006-06-26
I finally found the solution.  I snipped out all the back and forth, and went straight to the fix.  Thanks to Simon at dnsmasq for this:


It's likely that the DHCp client on your Ubuntu machine are simply not
sending the hostnames. There are different DHCP clients in use for
Linux, and configuration varies. If you are using dhclient, then
something like

send host-name kipdsputer

in /etc/dhclient.conf will work. An alternative is to move to using the
dhcpcd DHCP client. Assuming that Ubuntu has kept the Debian package
unaltered, that will Just Work for sending the hostname.

---

