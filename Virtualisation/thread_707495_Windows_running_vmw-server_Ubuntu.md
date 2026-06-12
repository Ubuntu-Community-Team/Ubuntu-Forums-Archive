---
title: "Windows running vmw-server Ubuntu"
date: 2008-02-25
forum: Virtualisation
---

### Post by mgan on 2008-02-25
I have a question about running Ubuntu via vmware server on my windows desktop.  I saw an article detailing how to do the installation so no questions there.  

But my question is on some functionality aspects that I'd like to achieve.  I'd like my virtualized version of ubuntu to act as a LAMP server for me to develop php / python applications.  Will I be able to foward http requests to my virtualized ubuntu lamp stack?  That way I could view/test my web application from another computer.  Provided I setup some DNS and what not?  I'm a programmer with some unix/linux system admin knowledge, but not that up-to-speed on networking and tcp/ip stuff.

I'd prefer not to dualboot. because i need to have access to my pc apps while I develop.

---

### Post by fjgaude on 2008-02-25
I am sure it can be done, but I'm not up to it. You start by using Bridged connection in your guest, Ubuntu, getting its local IP address that the router has supplied. You have essentially a private link directly to the guest. Your host has its own IP address.

Now the router has to be setup to permit your guest IP to come through.

It's doable, that's for sure.

I'm sure the vmware.com site has much to say about such.

---

### Post by mgan on 2008-02-25
Thankx for the reply.  I'm  willing to give it a try :)  Just wanted to get some feedback or some thoughts on it before I spend several hours tinkering with it.  If anyone else has some tips / hints for things to keep in mind as I try to set everything up the more help the better.

---

### Post by HermanAB on 2008-02-25
Use bridging, then for all practical purposes it is like you bought another PC, which is independent from the host.

---

### Post by mgan on 2008-02-26
Thankx, reading up on bridging and all that fun stuff.   thanks for the help.

---

