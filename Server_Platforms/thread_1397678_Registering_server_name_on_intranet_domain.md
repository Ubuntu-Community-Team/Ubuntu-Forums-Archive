---
title: "Registering server name on intranet domain"
date: 2010-02-03
forum: Server Platforms
---

### Post by jahservant on 2010-02-03
I apologize for the noobish question, but I'm new to setting up servers (too used to desktops).

I have an Ubuntu Server on a local network controlled by a Windows Server.  The Windows server is controlling the domain "mycompany.local", and registers all the Windows computers on the network as "computer.mycompany.local".

What I want to do is register the Ubuntu Server as such so that when a user types "myubuntu" or "myubuntu.mycompany.local" into a web-browser they will get to the intranet website running on the Ubuntu Server.

I've seen people do this using Samba and Winbind, but I'd prefer to stay away from things like that.  I don't want to have to log onto the server with a Windows Domain/Username, and I don't really care if the two servers ever talk much, outside of the name resolution.

Please note that I'm not trying to do anything with the intErnet (ie changes to DNS servers), just the intrAnet (local company access).

Is there a simple way to do this in the hosts or interfaces file? Or do I *have *to have something like Winbind?

---

### Post by cdenley on 2010-02-03
You don't need samba to authenticate in your AD in order to broadcast a netbios name. However, your clients will need to be able to resolve netbios names. Windows would out-of-the-box (I think even AD clients), but other OS's (ubuntu) would require configuration.

You can use avahi-daemon to broadcast your name using zeroconf. You would have to install bonjour on windows clients, though. Ubuntu desktop has the avahi client installed by default, but not all linux distros may.

You can configure an internal DNS server for your intranet (if you don't already have one) and add a new record for your server.

A much more tedious solution would be to add an entry in the hosts file for every system which may need to resolve a hostname to the server's IP address. (windows has a hosts file as well)

---

### Post by pirateghost on 2010-02-03
> **jahservant said:**
> I apologize for the noobish question, but I'm new to setting up servers (too used to desktops).

I have an Ubuntu Server on a local network controlled by a Windows Server.  The Windows server is controlling the domain "mycompany.local", and registers all the Windows computers on the network as "computer.mycompany.local".

What I want to do is register the Ubuntu Server as such so that when a user types "myubuntu" or "myubuntu.mycompany.local" into a web-browser they will get to the intranet website running on the Ubuntu Server.

I've seen people do this using Samba and Winbind, but I'd prefer to stay away from things like that.  I don't want to have to log onto the server with a Windows Domain/Username, and I don't really care if the two servers ever talk much, outside of the name resolution.

Please note that I'm not trying to do anything with the intErnet (ie changes to DNS servers), just the intrAnet (local company access).

Is there a simple way to do this in the hosts or interfaces file? Or do I *have *to have something like Winbind?

if your pcs all authenticate with the windows domain controller, then the windows domain controller is handling DNS.  add an A record into the Active Directory DNS for the server and you are done.

---

### Post by R.Bucky on 2010-02-03
I operate SBS 03 and SBS 08 at my employer and use Ubuntu 8.04 as a LAMP intranet host. I have about 8 different intranet sub-domains on the network. Just use your MS for DNS. Most CMS's that I tried require a full domain path, rather than showing relative URL's. You are better off choosing a sub.domain.com than a hostname. That is just poor practice.

---

### Post by jahservant on 2010-02-05
> **pirateghost said:**
> if your pcs all authenticate with the windows domain controller, then the windows domain controller is handling DNS.  add an A record into the Active Directory DNS for the server and you are done.

This worked perfectly.

Although I do still wish Ubuntu was controlling the DNS.  Too bad management won't bounce for it...

Thanks!

---

### Post by pirateghost on 2010-02-05
> **jahservant said:**
> This worked perfectly.

Although I do still wish Ubuntu was controlling the DNS.  Too bad management won't bounce for it...

Thanks!
with an active directory it is best practice to allow the domain controller to handle DHCP and DNS.

---

### Post by BobVila on 2010-02-05
> **pirateghost said:**
> with an active directory it is best practice to allow the domain controller to handle DHCP and DNS.

What he said  ;)

Jesus, does it get hairy when people try to shoehorn a Linux bind server into the mix...

MS might not do very much right, but they've got vendor lock-in down to a science!

---

