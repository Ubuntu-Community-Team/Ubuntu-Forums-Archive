---
title: "BIND/ Named Configuration"
date: 2011-02-09
forum: Server Platforms
---

### Post by Oxid3! on 2011-02-09
I got a brand new dedicated box, and well its a bit too bare for my liking and its forcing me to have to install a lot more then I first thought.

My current challenge is getting BIND/ Named set up correctly.

My datacenter provided me with 1 external ip address (92.48.118.10), and thats it

I have no clue how to set up nameservers  etc. so that I can use ns1.atomicoxide.co.uk etc. and have mail.atomicoxide.co.uk working correctly.

I have installed BIND through APT-GET and have played around with a few of the settings, but I am stuck to how the whole thing works.

If I set up BIND correctly, how will all of the root servers on the internet know that they exist, if nothing can point to it?

Hope you can help me with simple, clear examples - im a noob :)

---

### Post by elico on 2011-02-09
you better make some homework about DNS.
any domain registration is done by a registerer that can contact the root servers and update the zone in the root servers and also the DNS servers that are managing the domain.
it's better to use multiple dns server(at least two)
and what you can do is to get assited by your datacenter DNS to manage your zone.
let say that you will use one dns on the server with the ip that you own and the other one on the iip on the data center dns.
you can add A record (name to ip) for ns1.XX..XX and also another one on the same ip with your domain name.
for the mail .XXX.XXX you can use a CNAME (canonical name >A record).
the dns lookup goes in a tree hirarchy lookup as if the local dns dosnt know it asks the root zone server for direction 
then it goes to UK and the to the CO.UK and from there to the DNS\NS server that managing the domain.
look at this
[http://blog.ausweb.com.au/wp-content/uploads/2009/06/dns-lookups.png](http://blog.ausweb.com.au/wp-content/uploads/2009/06/dns-lookups.png)

---

### Post by Oxid3! on 2011-02-09
Thanks for your reply, so how would I go about informing the root servers about my presense? - My Datacenter gave me 3 DNS ips, but said they do not accept updates?

Is this related to it?

---

### Post by elico on 2011-02-10
yes it is related.
first you need to buy a domain from a domain registerter.
if you paid then you can specify in your registering info the dns servers that will manage your domain.
aht you should do now is to set 2 ips for dns of the datacenter and of course make sure wiht them that everythin is setup fine also you should add your server ip address as the a dns server in the domain registation.
if your data center has an CPANEL or any way to setup the domain enteries set it up there first.
if you will register you ip as a dns\ns server for your domain then you will be able to change domain enteries and after you will setup your server dns correctly you can change the order of the dns servers to your ip first.
it takes about 48-72 hours for a dns server entery update to get to the whole dns tree but in 18 hours most of the sites are working properly if you only change the prder of the dns servers.

---

