---
title: "Dynamic IP updateing script for Bind"
date: 2006-08-19
forum: Server Platforms
---

### Post by chrisfay on 2006-08-19
Does anyone know of any scripts that would auto update bind with my WAN IP when it changes? I know there are plenty out there for use with zoneedit or noip but, what about for your own DNS server? 

I run Bind on my Dynamic IP which doesn't really change unless I hard reset my router though when it does, I have to manually edit all my zone records and my registrar. I was hoping for something that would auto populate all the ip inputs in bind with the new IP. Then all I would have to do is change my IP at my registrar....

Any ideas?

---

### Post by jrjr on 2006-08-19
.

---

### Post by chrisfay on 2006-08-19
I have used zoneedit before with great success. That's the service I was using prior to configuring Bind9 on my own server but, am now looking for a way to auto update my zones similar to a client that updates zoneedit zones only specifically for Bind.  

I have domains at both Godaddy and Bluehost and both of them have updated NS changes within seconds. I have never had a delay in routing after an NS change from either registrar. 

I go to dnsstuff.com and run their dns test to make sure they have the new name servers listed at the parent servers and everytime its been almost instant. 

I was doing some more searching and found a couple, albeit outdated peices of software that could have potential. 

1. b9ddns- this was project died I think about a year ago. Anyone know of something similar?

2. Bind dynamic update - Not sure how this works yet but curious as to anyone's exerience. 

It seems to be an extensive and confusing path to configure auto updateing manually so I was hoping for a software client package that could do it.

---

