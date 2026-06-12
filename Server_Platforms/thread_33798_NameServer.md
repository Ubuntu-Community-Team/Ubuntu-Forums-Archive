---
title: "NameServer"
date: 2005-05-12
forum: Server Platforms
---

### Post by dave9191 on 2005-05-12
Ok, I have a slight annoyance with my setup. Let me explain it quickly. 

LAN - Router - WAN

On the LAN if i type the Router LAN or WAN ip i get the configuration pages up. You cant access those from the WAN. 

I set up a webserver at 192.168.03. That works fine if i type the IP on the LAN. I configured the router to direct to the server machine if someone types my IP on the WAN. I have a subdomain on the WAN to redirect to my WAN IP. 

When I open the WAN IP or subdomain on the wan it loads up the server properly. But if I am on the LAN and type any of those, then I get the router config pages up and I am forced to use LAN IP for the server. 

That leads to probs with my bookmarks, I need to have ones that will work on the LAN for the server and ones that will work on the WAN. Plus when copying and pasting links to people, i have to edit the IP each time. 

I was thinking that I could setup a nameserver for when Im on the LAN that would take the subdomain and redirect me to the server. Is that possible. And did this post make sense ?

---

### Post by qstone on 2005-05-12
'Not sure a nameserver is mandatory to solve this...
You have certainly set un a rule on your router that redirects all traffic (or only http requests on port 80?) from wan to your server. But you don't have any special rule for traffic from your lan. If you set up a rule, similar to what you did for wan traffic, but this time for your lan, it should be ok.

BTW, does your router config pages really show up on port 80 ? Is it the only way you can get access to it ? If so, be warned that adding a rule like I said above may prevent you from accessing your router config...

---

### Post by dave9191 on 2005-05-12
Well the way that I set up WAN -> server is using the port forwarding section in the router config. That only seems to work for WAN. There doesnt seem to be a way to setup a LAN port forwarding. There is something called static route, but Im not quite sure what thats for. And I can telnet into the router as well.

---

