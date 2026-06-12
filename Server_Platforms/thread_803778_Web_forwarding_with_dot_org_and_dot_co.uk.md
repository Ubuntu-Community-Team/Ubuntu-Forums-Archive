---
title: "Web forwarding with dot org and dot co.uk"
date: 2008-05-22
forum: Server Platforms
---

### Post by Martyn Thompson on 2008-05-22
Hi guys and gals, 
Sorry if this is in the wrong section - I not entirely sure the best place to post this. 
However, here goes. I have bought the domain name ansuk.org through 123-reg.co.uk and attempted to set up web forwarding to my IP address.  
I have done this successfully before with .co.uk domain names but it appears not to work for .org domains. 
Any suggestions would be gratefully accepted. 
Just so you know, I am doing this for free for a professional association I am a member of, so I am not trying to blag some free advice for financial gain!
Thanks in advance,

Martyn.

---

### Post by windependence on 2008-05-22
Are you trying to forward the .co.uk domain to the .org domain? If so, the best way to do this would be in the DNS settings of your domain name registrar. You will need to point the A record at the IP address of your server, then no forwarding would be necessary.

You can have the .co.uk, .org, .com, and .net all point to the same IP address, and if you want you can mask the domain so they all show up as .com or whatever you want.

-Tim

---

### Post by Martyn Thompson on 2008-05-22
Tim,

Thanks for this. I am using the .co.uk for another (not for profit) virtual host - so bought the cheapest domain name I could that would be relevent. Hence, [www.ynng.co.uk](www.ynng.co.uk) and [www.ansuk.org](www.ansuk.org) should both point to the same IP address with different virtual hosts. I am doing this as a temporary measure to 'play' with the system until I am happy with it - then intend on presenting it to my colleagues and asking for funding to place it on a real (paid for) Ubuntu server. 

Thanks again Tim, I will look into the DNS route.


Martyn.

---

