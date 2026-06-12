---
title: "wireless server challenge"
date: 2008-10-29
forum: Server Platforms
---

### Post by adept_king on 2008-10-29
how does an isp know the ip address of computers beneath a wireless network?

especially when such an ip address is as generic as 192.0.0.1 or something like that.

does the isp use the ip it assigns the router PLUS some kind of identifier or machine address to find the wifi surfer's real identity?

the question comes from the fact that im trying to get my ubuntu server to serve a page through the university's wireless.

of course, dyndns.or (which i just set up) cant find my machine, only the router's ip.  

how does big brother draw a bead on me?  i need to make it easier if only to serve up the "it works" page courtesy of apache2.

---

### Post by heimo on 2008-10-29
If I understand what you're trying to achieve... You should setup a port forwarding from your router to internal (192.x) address (port 80 probably) and then use routers public ip to access Apache.

---

### Post by adept_king on 2008-10-29
i am using someone elses wireless.  i just want to test my setup.  just to see if it works, but it seems like the dyndns.org is pointing people to the wireless router instead of to me.  because, i dont have an ip address. i am way down the food chain.  i cant configure someone elses router.  if its possible to chat online or use torrent files, it must also be possible for the internet to find my computer.  

how can i make my computer found by the internet?

---

### Post by cariboo on 2008-10-29
The easy way to solve your problem, is to pay for your own internet access.

Jim

---

### Post by alienprdkt on 2008-10-29
you can test via [http://localhost:80](http://localhost:80)
other then that you need access to the router

---

### Post by mbeach on 2008-10-29
I don't believe you'll be sucessfull serving http over tcp without access to the router setup (port forwarding).  With those other applications you are connecting to a server somewhere (so you make the initial connection).

---

### Post by adept_king on 2008-10-30
if i give my laptops root password, and im sitting in a cafe using wireless, would it be possible for a super-hacker to go ahead and browse my love letters?

if i am completely safe from harm, then all i have to do is surf with wireless and i can go ahead and commit war crimes on line and the worst case is the cafe goes under interrogation right?

what im driving at is that there MUST be a way for my computer itself to be seen by entities beyond the wireless router.

if that is the case, it must then be possible to serve a webpage from wherever there is a connection to the internet, and if that connection changes, my computer could still be uniquely identified and therefore resolveable as a server.

why again should i not post my root password in my signature?  im totally safe right?  Im using other peoples wireless.  I am virus free and behind a wireless router, invincible.  right?

---

### Post by Zeosa on 2008-10-31
You've already been given your answer...there's simply no way for someone on the WAN side of the router to establish the tcp connection that you require without that packet being forwarded to your computer by the router. 

When that router receives a packet that wasn't requested by a device on the LAN side and for which no 'rule' exists to handle said packet it quietly drops drops or ignores it.


I realize that it's not the answer you WANT ...but it's the only correct one.

---

### Post by adept_king on 2008-10-31
how is it that you can chat right inside gmail?  info is coming back and forth.  thats all a server needs.  dont be so quick to say something is impossible.  new technology is not impossible, it keeps happening every day.  when ipv6 is the new standard, the new impossibilities i mention might be old history.

until then, i will enjoy my complete cloak of anonymity (invincibility) as i surf via a different wireless network every day fighting for the impossible!  and world peace.

---

### Post by Zeosa on 2008-11-01
> **adept_king said:**
> how is it that you can chat right inside gmail?  info is coming back and forth. 


It's coming back and forth because it's traffic which has been requested from the client side, therefore the router knows what to do with the packets...

> 
dont be so quick to say something is impossible.


Ok ...I'll give you this. It's not possible with any current technology. Maybe aliens will visit someday and bring us the knowledge of how to create a hardware based firewall which can read our minds and know exactly where to send packets for which it has no knowledge of...:)

> 
  when ipv6 is the new standard, the new impossibilities i mention might be old history.


See above

> 
until then, i will enjoy my complete cloak of anonymity (invincibility) as i surf via a different wireless network every day fighting for the impossible!  and world peace.
[/quote]

Hey, enjoy! ....(though I'm not quite sure what one has to do with the other)

---

