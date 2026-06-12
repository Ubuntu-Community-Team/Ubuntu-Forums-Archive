---
title: "Home Server - Name access but no http acsess"
date: 2008-10-25
forum: Server Platforms
---

### Post by ernst on 2008-10-25
Finally succeeded in accessing my home web server having a static IP address.  Succeeds only when using the DNS name assigned to my IP address.  I am not able to access that IP address directly, i.e. http;//nnn.nnn.nnn.nnn/.  Since my DNS name is assigned to that http..., why shouldn't I be able to access my home web page using only that address?

---

### Post by baudday on 2008-10-25
Are you trying to access it from inside or outside your network. Also, are you using your local or global ip? If you're using a local ip outside the network, it won't work.

---

### Post by ernst on 2008-10-25
Re: Access local or global:  Both.  Have Ubuntu on my machine and wife's Win2000 on her using a D-Link router.  After accessing my names web site on both our machines, I had her university computer, a friends computer on a different ISP as well as my using my laptop at a hotspot.  All succeeded on accessing my web page using my DNS name.  But, still couldn't access the http address shich the DNS name points to.

Regards, Rob

---

### Post by baudday on 2008-10-25
Are you sure all the correct ports are open in your firewall.

---

### Post by tuskenraider on 2008-10-25
yeah thats what i would say.... make sure your port 80 is forwarded to the correct computer... also .. some isp's block port 80 so you may have to run your http server on another port 81 or 8080 something like that...  also you ever thought about nixing the static ip addy and getting a service like dyndns? i have a cable modem that changes ip addys more than i change my socks... and i have my router set to update dyndns's servers evertime there is an ip address change.  idk.. that works for me.. may not be what you need...  but i would def check 1 ports and 2. that your isp isnt blocking port 80(standard http port)

tusken

p.s
hope this helps...  also try portforward.com for assistance and im sure there are applications floating around that will tell you if a port is blocked or not....  idk any in linux.. my server is a windoze media center machine.  hey hey hey.. i know i know.. i should switch to ubuntu... but you know when it aint borked dont fix it...:lolflag:  so i dont. LOL  hope this helped.

p.s i agree with dude above me about the firewall... when i was setting up my server that was a stumbling block for me... darn firewalls...  lol anyway router and wirewall ports...  have fun and good luck!!!!

---

