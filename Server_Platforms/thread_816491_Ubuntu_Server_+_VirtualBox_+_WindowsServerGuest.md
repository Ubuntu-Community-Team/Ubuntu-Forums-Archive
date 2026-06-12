---
title: "Ubuntu Server + VirtualBox + WindowsServerGuest"
date: 2008-06-02
forum: Server Platforms
---

### Post by renesilva on 2008-06-02
I configured a Ubuntu server with Bind9 and  Apache using virtual hosts. It runs and everything but lately one of my bosses wanted to implement a Windows Server because there's a divisition that uses Microsoft technology. So they were going to buy a new server but I screwed it up and said that virtualization was the solution, actually it is. So I implemented a Windows 2003 Server as a guest on the Ubuntu server with virtualBox. But I don't have any idea how to redirect a request for a domain into this Windows Server, I could redirect ports with VirtualBox but they ask me to redirect a domain, for example, I have some domains like [www.asdf123123.com](www.asdf123123.com) hosted on Apache on same server (thanks to virtualhosts) but they want a www.micro$oft123asdf.com hosted on the same server thanks to virtualization.
One solutions could be buying a new network card and redirect from there to the Windows Guest. Is there a solution that doesn't implies buying a new card??

---

### Post by quelx on 2008-06-02
Peep [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox) specifically the **Networking** section.

---

### Post by beniwtv on 2008-06-03
This is actually quite simple to accomplish.

I have the same set-up in my environment from home.

Basically what you need to do is to bridge your ethernet interface. This way, you can give your Windows server an IP as if it was on the same network switch as the actual machine.

It's sort of an emulation of a network card, with all it's ports et all.

I have a handy script that auto starts my VM's on Ubuntu boot-up, which sets bridging up also. Unfortunately, I'm not currently at my laptop to give it to you.

If you need this (there are plenty of examples on the web), drop me a response and I will send it to you this evening when I get home.

Cheers,

---

### Post by renesilva on 2008-06-04
Thanks quelx and beniwtv, I bought that new NIC and could configure it without any problems, it works like charm :)

---

