---
title: "Web support site"
date: 2008-10-06
forum: Server Platforms
---

### Post by bonesjones256 on 2008-10-06
This may not be the right place to post this but ubuntu is where i would want this feature. 

You see these sites all the time. Say i work for a company called DFD. And my name is john doe. Well our client sally has problems with her pc so she goes to dfd.com/remote or something and i give her a session id. then she runs a download and i can control her machine and chat with her and such. I am currently looking for a way to do this for my own company that i work for. I've seen paid versions but they are like 30 bucks a month. Does anyone know of a way to accomplish this?

---

### Post by cariboo on 2008-10-06
You can easily do what you want using one of the vnc derivatives like tightvnc. Tightvnc is available in the repositories and for Windows is a free download. So you could set it up for your customer to download tightvncserver and then you can connect to their computer from your computer using tightvncviewer. The only problem you might run into, is if they have a router they will have to forward port 5900 form the computer to the router.

I'll leave the implimentation up to you.

Jim

---

### Post by bonesjones256 on 2008-10-06
> **cariboo907 said:**
> You can easily do what you want using one of the vnc derivatives like tightvnc. Tightvnc is available in the repositories and for Windows is a free download. So you could set it up for your customer to download tightvncserver and then you can connect to their computer from your computer using tightvncviewer. The only problem you might run into, is if they have a router they will have to forward port 5900 form the computer to the router.

I'll leave the implimentation up to you.

Jim
You actually just gave me a good idea. Vnc servers have a thing called listening mode. So i could make a script that would run the service and connect to the listening server. genius. :)

---

