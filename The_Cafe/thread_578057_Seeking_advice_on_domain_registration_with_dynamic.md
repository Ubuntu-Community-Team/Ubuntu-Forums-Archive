---
title: "Seeking advice on domain registration with dynamic IP"
date: 2007-10-16
forum: The Cafe
---

### Post by satimis on 2007-10-16
Hi folks,

I'm currently subscribing Broadband static IP plan (fixed IP) with its agreement expired soon. My ISP can only supply ADSL connection even on static IP plan because of the network coverage in the area of my place of abode. Other ISPs are also unable to offer DSL connection.  In such a circumstance, I'm considering to renew a new plan for dynamic IP with my ISP. Because it is not worthwhile paying extra cost for static IP running on ADSL connection.

I have a domain registered with "godaddy" which is for personal use only. It also will expire soon.  Unfortunately "godaddy" does not support dynamic IP, therefore I have to transfer my domain to another registrar which can offer such a service.

Could you folks please shed me some suggestion other than;
[www.dyndns.com](www.dyndns.com)


TIA

B.R.
satimis

---

### Post by Sporkman on 2007-10-16
I use [www.no-ip.com](www.no-ip.com).

---

### Post by satimis on 2007-10-17
> **Sporkman said:**
> I use [www.no-ip.com](www.no-ip.com).
Thanks for your advice.

I believe the IP address only changes on reboot (dynamic-static IP).  OR the ISP server is down and refixed afterwards.

Are there free software available for monitoring  the change on IP address from ISP and updating the corresponding IP address on Registrar's site?

TIA


B.R.
satimis

---

### Post by southernman on 2007-10-17
The software doesn't change a thing as the regsitrar is concened. You point (at the registrar) to the name servers of the service you choose and then install the updating software on your server, to update your true IP (the one of your ISP's assignment) at the dns service your using. Make sense? :/

What's wrong with dyndns? Here is the link to the update software from their site - [http://www.dyndns.com/support/clients/](http://www.dyndns.com/support/clients/)

---

### Post by Sporkman on 2007-10-17
> **satimis said:**
> Are there free software available for monitoring  the change on IP address from ISP and updating the corresponding IP address on Registrar's site?


Yes - do a search for "no-ip" in the synaptic package manager...

---

### Post by satimis on 2007-10-29
Hi folks,


A further thought on dynamic-static IP. I recall previously when I ran dynamic IP, ISP blcoked "port 25". I can't send mail from my Mail Server. Finally I have to sending mails relayed via ISP's mail server.

They also blocked port 80. I used port 8080. But I have to inform my friends using this port on browsing my Web server.

Are there solutions? TIA


B.R.
satimis

---

### Post by Sporkman on 2007-10-29
> **satimis said:**
> Hi folks,


A further thought on dynamic-static IP. I recall previously when I ran dynamic IP, ISP blcoked "port 25". I can't send mail from my Mail Server. Finally I have to sending mails relayed via ISP's mail server.

They also blocked port 80. I used port 8080. But I have to inform my friends using this port on browsing my Web server.

Are there solutions? TIA


B.R.
satimis

No-ip.com does port redirects to get around those blockages...

---

