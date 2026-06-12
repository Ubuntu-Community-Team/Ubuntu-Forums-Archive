---
title: "Need a howto Virtual hosting"
date: 2008-12-19
forum: Server Platforms
---

### Post by rwslippey on 2008-12-19
I've been looking for a very long time for a solution to this issue...

If someone could help...

I have a ubuntu server running apache and 3 different completly seperate websites.. all served on the same port (non standard due to ISP port 80 Blockage)

All three servers work fine and are accessible from their respective domain name ... ie     example.hopto.org   ....
    that is outside my network...

I need to be able to access all of the sites from inside my network... 
however when entering the server IP address it will only load one site.... 

is their a way I can load these sites within my LAN if so.. how?

also it may be important (not sure)  I am using another computer to access the sites.. not the same computer that is hosting the files...

Thanks for the help   

Rob

---

### Post by MJN on 2008-12-19
The success of your virtual hosting relies on Apache being able to tell which site is being requested - it cannot do this when you just type the server's IP address into your browser. Hence you need to be using the site URLs when using the internal machines.

Presumably you have already tried this and failed (most likely due to the inability of your router to allow internal clients to access internal machines via the external WAN address) and so you best bet, assuming a limited number of internal machines, would be to add static entries to each client's hosts file (/etc/hosts on Ubuntu) to map your site URLs to the internal IP address of the server.

For example,

```
#Format: <address> <name> <name 2> ... <name x>
192.168.0.2 example.hopto.org www.site2.com site2.com www.site3.com site3.com
```

Any help?

Mathew

---

### Post by rwslippey on 2008-12-19
okay...

That makes perfect sense.. and I knew that Apache would need the URL to understand witch site is being requested it was just how to make it work internaly... So yes this is very helpful  

How I understand it now is to add the code you provided to the /etc/hosts file to each client that will visit the site... correct.


Thanks

---

### Post by MJN on 2008-12-19
Spot on. You'll already have at least one entry in there (mapping localhost to 127.0.0.1) so just add your entries to a new line.

Mathew

---

### Post by rwslippey on 2008-12-19
Well....


you are my hero!  

It works out great... now I have 4 more computers to add this to....


Thanks...

I've been looking for a solution for a while now and this worked...

I really appriciate your response...

Rob

---

