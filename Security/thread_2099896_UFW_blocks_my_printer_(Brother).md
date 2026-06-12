---
title: "UFW blocks my printer (Brother)"
date: 2012-12-31
forum: Security
---

### Post by Askel on 2012-12-31
Hi

I reinstalled my system and activated UFW using the guide here on the forum. When I tried to install my printer, a Brother MFC-J6910DW, it can't get connected. If I disable the firewall I can print, but not with it enabled. What port should be open to be able to use the priner. Should it only be open out or also in? I'm also using the Brscan-skey. I guess some port has to allow trafic in to be able to get the scanned file?

/askel

---

### Post by crispy_420 on 2012-12-31
Owners manual states:

Network scanning = UDP 54925
PC/Fax receiving = UDP 54926

And it looks like UDP 137 is involved too.

[http://welcome.solutions.brother.com/BSC/public/us/us/en/faq/faq/000000/002500/000097/faq002597_000.html?reg=us&c=us&lang=en&prod=mfc7345n_us](http://welcome.solutions.brother.com/BSC/public/us/us/en/faq/faq/000000/002500/000097/faq002597_000.html?reg=us&c=us&lang=en&prod=mfc7345n_us)

---

### Post by Askel on 2012-12-31
I've opened the ports but I still don't get any contact with the printer.

---

### Post by crispy_420 on 2012-12-31
In firewall are ports allowed for incoming?

---

### Post by Askel on 2012-12-31
Yes, I've tried that to, but it doesn't make a difference

Edit:
I tried the GUI for UFW and could enable the specific IP-adress for the printer for incoming and outgoing trafic. So it works fine now. (Printing at least. I've got to fix the Brscan-skey-connection)

---

### Post by Ms. Daisy on 2012-12-31
Look at the ufw logs when you attempt to use the Brscan-skey-connection.  They will tell you what ports are being blocked.

---

### Post by Askel on 2013-01-03
WHat's more secure? To ha a specific port open or to give access to the specific ip of the printer?

---

### Post by Ms. Daisy on 2013-01-03
> **Askel said:**
> WHat's more secure? To ha a specific port open or to give access to the specific ip of the printer? If its a network printer and you have assigned/ reserved an IP address for it then you could allow traffic to/from that IP. But if the printer is local or uses DHCP then it would be hard to allow by IP.

---

