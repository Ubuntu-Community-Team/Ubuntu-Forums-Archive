---
title: "Server Layout"
date: 2008-03-16
forum: Server Platforms
---

### Post by SuperMiguel on 2008-03-16
I have 1 server, 2 desktop (1 wired and 1 wireless), and 2 laptops in my house, whats best best way to set this up, is the way that the picture shows the best way??
[IMG]http://i37.photobucket.com/albums/e89/miguelv2002/ServerLayout.jpg[/IMG]
Also i dont know if the wireless computers should be connecting to the router directly?? please help :P first server set up... thanks =)

---

### Post by Koybe on 2008-03-16
Hello, I think it doesn't matter at all. But if it's your Router that give Wireless you get no choice.

I don't know exactly what's your question, everything seems fine. I would juste suggest to wire everything possible because i dislike wireless personaly ;)

---

### Post by SuperMiguel on 2008-03-16
well someone told me that i have to put two network cards on the server and then do something like this: router ---> server ---> computers... so the server will be the one managing my connection.. so i dont knot how i have to set up my wireless computers... ohhh also i have a ps3 in the network wireless...

---

### Post by Koybe on 2008-03-16
OK.

Then it depends on what your server is doing exactly. If iot's only a file server you do not need two network cards and routing.

This really depends on what you intend to do with your server.

---

### Post by SuperMiguel on 2008-03-16
well i really want to put make a lamp server, music server, file server, ventrilo server, printer server, firewall, so i though that for firewall i need to put the server between my router and computers.

---

### Post by Koybe on 2008-03-16
Yeah. For a personal use I thought that using a router as a firewall would be enough. Anyway, if you want to to this you'll need to join all your connexion  trough your server. So your schema isn't right.

And you'll need an Access Point in your 'LAN' i mean in the place before your server.

---

### Post by SuperMiguel on 2008-03-16
well i really dont know, whats better if just keep the set up how it is in the pic leaving the router as a firewall or puting an acess point?? the reason why i wanted to do it with all the security is to learn how to do it, so eventually if i have to do it for a company ill be able to do it.... since i have done it before... u know what im saying?

---

### Post by Koybe on 2008-03-16
If I were you I would do this :

- Put my router as a firewal
- Use only one network card and no firewall on my server
- I would forward any needed port from my router to my server
- I woudl join any pc in the LAN to the router for internet connexion and to the server for any service needed.

If you choose to route with your server, you'll need :
- Extra network card with routing configuration
- All machines in your network connected to the server
- Eventually an access point for the LAN card of your server if the one you owned is integrated to the router.
- Forward port to the server

I don't know if this can help you...

---

### Post by SuperMiguel on 2008-03-16
so if i choose option b will there be any benefits beside learning??? also u said i need and access point im assuming this is going to be a wireless access point correct?? (like [http://www.newegg.com/Product/Product.aspx?Item=N82E16833127139](http://www.newegg.com/Product/Product.aspx?Item=N82E16833127139))
then i have to set it up like this :


router --> access point --> server --> desktop 
....................|__wireless computers

---

### Post by Koybe on 2008-03-16
> **SuperMiguel said:**
> so if i choose option b will there be any benefits beside learning??? also u said i need and access point im assuming this is going to be a wireless access point correct?? (like [http://www.newegg.com/Product/Product.aspx?Item=N82E16833127139](http://www.newegg.com/Product/Product.aspx?Item=N82E16833127139))
Yes
> **SuperMiguel said:**
> then i have to set it up like this :
router --> access point --> server --> desktop 
....................|__wireless computers
No, it should be like this ->
router --> server --> access point -->  desktop 
.......................................|__wireless computers
And if you choose this option you'll get higer security.

---

### Post by SuperMiguel on 2008-03-16
to in this case i have to shut down the wireless signal of my router correct??

---

### Post by Koybe on 2008-03-16
Correct ;)

---

### Post by SuperMiguel on 2008-03-16
hehe is there a way to use my router as an access point?? since its a N router which im aussming im going to loose N, but it also have 3 antenas on it its a really nice d-link gaming router

---

### Post by Koybe on 2008-03-16
Then I think you should choose option 1. It would be a nice solution anyway. And cheaper.
So everything goes to your router, and your server is simply accessible from everyone with only one network card. No need to route trough it.

---

### Post by SuperMiguel on 2008-03-16
orrrr i can have two networks, one being managed by the router and one by the server so i wont shut down the wireless signal meaning that all my wireless signal willl go to the router and my main computer the one next to the server will have good protection just like my initial picture

---

### Post by Koybe on 2008-03-16
It could make sense, but it needs you manual changing. It's all up to you :)

---

### Post by SuperMiguel on 2008-03-16
i mean like this [IMG]http://i37.photobucket.com/albums/e89/miguelv2002/ServerLayout.jpg[/IMG]
so all my wireless connection will go though the router like a normal wireless network and then my server will have two network cards one incoming from the router and the other one to the computer (main computer)

---

### Post by Koybe on 2008-03-16
Yeah sure it's possible... but I would quote it as 'strange' ;)

---

### Post by SuperMiguel on 2008-03-16
hehe like i said before the only reason why i want the server to manage any connection is to learn how to set it up so i dont have to do it to all the network with one computer i will learn? make sence?

---

### Post by SuperMiguel on 2008-03-16
one last question will i loose internet speed on my main computer if it is managed by the server???

---

### Post by Koybe on 2008-03-16
No, it shouldn't make a difference.

---

### Post by SuperMiguel on 2008-03-16
Thanks for all your help =)

---

