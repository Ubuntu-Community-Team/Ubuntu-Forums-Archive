---
title: "CUPS with 2 NICs"
date: 2008-07-30
forum: Server Platforms
---

### Post by bindatype on 2008-07-30
I am trying to set up a CUPS print server using Hardy. The PC has two NICS, eth0 faces a network with address 172.16.0.* and eth1 faces a local network 192.168.12.*. The PC hosts a DHCP server on eth1 and the only client is an OKI c5300 printer.

[PC]--(eth0)---------other machines on the 172.16.0.* block
| 172.16.0.1
|
(eth1)
|
|
Printer (192.168.12.100)

Ideally, the other machines on 172.16.0.* will be able to access the printer on eth1 thru CUPS.

Presently I can print to the printer from the PC but none of the other machines can see or connect to the printer. The two NICS aren't bridged but I don't think that is necessary. I can see the CUPS server via [http://172.16.0.1:631](http://172.16.0.1:631) on the eth0 side and CUPS can print to the printer on the eth1 side.

Any thoughts?


Here is a snippet of the cupsd.conf file:

# Show troubleshooting information in error_log.
LogLevel debug
SystemGroup lpadmin
# Allow remote access
Listen 631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL
DefaultAuthType Basic
DefaultEncryption IfRequested
<Location />
Allow localhost
Allow 172.16.0.1
# Allow shared printing and remote administration...
Order allow,deny
Allow all
</Location>
<Location /admin>
Allow localhost
Allow 172.16.0.1
# Allow remote administration...
Order allow,deny
Allow localhost
Allow @LOCAL
Allow all
</Location>
<Location /admin/conf>
AuthType Default
Require user @SYSTEM
Allow localhost
Allow 172.16.0.1
# Allow remote access to the configuration files...
Order allow,deny
Allow all
</Location>

---

### Post by BobMUK on 2008-07-31
Let's make sure I understand what you're trying to achieve:
CUPS is installed on the PC and it can see/use the printer on eth1 perfectly.  You are trying to configure things such that machines on the 172.16.0.0 subnet can use the "main" PC as a CUPS server - yes?
I.E. you're not trying to configure the client machines to talk directly to the printer via ethernet?

If it's the latter, then you will indeed need to bridge your subnets (and indeed won't need CUPS).

If it's the former, then what OS are the client machines running?  If it's windows you'll need to configure Samba on the "main" PC in order to share the printer with them.

---

### Post by windependence on 2008-07-31
I agree with Bob here, what you are trying to do is actually routing unless you bridge the networks.

-Tim

---

### Post by bindatype on 2008-07-31
Yes, I am trying to set up things so that the other machines use the PC as a CUPS server and do not print directly to the printer. The OSes are linux and OSX. I have read that such a configuration is possible without setting up samba shares but I've been unsuccessful finding documentation for this.

In your opinion is it simpler to use samba to achieve this goal?

Many thanks...




> **BobMUK said:**
> Let's make sure I understand what you're trying to achieve:
CUPS is installed on the PC and it can see/use the printer on eth1 perfectly.  You are trying to configure things such that machines on the 172.16.0.0 subnet can use the "main" PC as a CUPS server - yes?
I.E. you're not trying to configure the client machines to talk directly to the printer via ethernet?

If it's the latter, then you will indeed need to bridge your subnets (and indeed won't need CUPS).

If it's the former, then what OS are the client machines running?  If it's windows you'll need to configure Samba on the "main" PC in order to share the printer with them.

---

### Post by BobMUK on 2008-07-31
Yup, Samba makes it simpler, but it is possible to print with CUPS without it.  

Take a look at [http://gentoo-wiki.com/HOWTO_Linux_Cups_printserver_Windows_clients_without_samba]("http://gentoo-wiki.com/HOWTO_Linux_Cups_printserver_Windows_clients_without_samba")

---

### Post by bindatype on 2008-07-31
Thanks for the link...



> **BobMUK said:**
> Yup, Samba makes it simpler, but it is possible to print with CUPS without it.  

Take a look at [http://gentoo-wiki.com/HOWTO_Linux_Cups_printserver_Windows_clients_without_samba]("http://gentoo-wiki.com/HOWTO_Linux_Cups_printserver_Windows_clients_without_samba")

---

