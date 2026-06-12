---
title: "[SOLVED] Virtualbox accessing ubuntu localhost"
date: 2008-01-30
forum: Virtualisation
---

### Post by Okar on 2008-01-30
hi,
I got Ubuntu 7.10 and WinXP with Virtualbox.
Is there a way to access the localhost of Ubuntu in the WinXP, without beeing in an network?
My Problem is:
I want to do some webstuff. So I installed apache on my Ubunutu. There I can access my stuff by using: localhost/~okar/stuff.. Can I somehow access these things on my WinXP.

Thanks in advance;)

---

### Post by p_quarles on 2008-01-30
Yes, you can, but not using localhost. You'll need to get the IP address that your Ubuntu Apache server is listening on, and then enter that to connect from XP. You can get the correct address by running this:
```
ifconfig -a
```
The "inet address" will be the number you want to enter into your browser in XP.

---

### Post by Okar on 2008-01-30
ok thanks.
but this only works if I'm connected to a network. Is there a possibility to achieve the same without being in a network?

---

### Post by mannheim on 2008-01-31
From memory, if you have set up VirtualBox with NAT networking, I think you can access services running on the host from the guest OS. From the guest (WinXP), the host appears as 10.0.2.2. So if you point your WinXP web browser to that address, it should connect to your Ubuntu Apache server. (To the host, this appears to be a connection from localhost, I believe.)

---

### Post by Okar on 2008-01-31
hey nice, that was what I was looking for.
thank you very very much :D

---

### Post by kokaku on 2008-07-19
I'm not having any luck with the ideas offered here. I have a WinXP guest running in VBox 1.5.6 in Ubuntu 8.04. There is a network adapater using NAT (the default, I believe). I network fine withing WinXP but cannot access the Apache2 server running in Ubuntu.

I tried:
* the IP address offered by ifconfig -a
* 10.0.0.2
* the tips offered at [http://herbee.fr/?q=VirtualBox-NAT](http://herbee.fr/?q=VirtualBox-NAT) (see my comments at the bottom)

It would be very cool if I could get this working so I would only have to maintain 1 version of Apache2 for Windows browser testing (instead of installing/maintaining a duplicate setup within Windows).

Any ideas?

thx
a

---

### Post by Okar on 2008-08-29
did you try 10.0.0.2 or 10.0.2.2?   because the latter is the right one.

---

### Post by matiz on 2008-08-30
Wow, this is really nice work !

---

### Post by gpasci on 2009-03-22
10.0.2.2
this is what I was looking for :D

---

### Post by emyller on 2009-07-13
Perfect. Much better than run ifconfig everytime I get a new IP address. thank you!

---

### Post by Ebon Lupus on 2010-06-06
I'm using an XP guest in an Ubuntu 9.10 installation of VirtualBox. The [http://10.0.2.2/](http://10.0.2.2/) thing seems to work okay, except IE is not saving cookies. Does anyone know why?

EDIT: Never mind. I figured it out. Silly-stupid me. My bad.

---

### Post by tirengarfio on 2011-04-29
Hi,

I want to check my localhost from the browser of Windows 7 installed in VirtualBox. (I have as main OS Ubuntu).

When I write 10.0.2.2 in W7/IE, I go to the 127.0.0.1 in Ubuntu. But..

what should I do to go to another IP for example 127.0.0.2 ???????

Regards

Javi

---

