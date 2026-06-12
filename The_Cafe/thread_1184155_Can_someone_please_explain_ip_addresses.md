---
title: "Can someone please explain ip addresses?"
date: 2009-06-10
forum: The Cafe
---

### Post by ninja_numbnuts on 2009-06-10
I don't really understand it!

---

### Post by dragos240 on 2009-06-10
> **ninja_numbnuts said:**
> I don't really understand it!

It's basically a code that explains where your connection is coming from. It just says where you are, every website has one, although I'm terrible at explaining :(


See below for a more accurate explanation.
[http://en.wikipedia.org/wiki/IP_address](http://en.wikipedia.org/wiki/IP_address)

---

### Post by ninja_numbnuts on 2009-06-10
> **dragos240 said:**
> It's basically a code that explains where your connection is coming from. It just says where you are, every website has one, although I'm terrible at explaining :(


See below for a more accurate explanation.
[http://en.wikipedia.org/wiki/IP_address](http://en.wikipedia.org/wiki/IP_address)

I looked at the wiki page but it's too technical for me! Please explain for dummies :P

---

### Post by dragos240 on 2009-06-10
> **ninja_numbnuts said:**
> I looked at the wiki page but it's too technical for me! Please explain for dummies :P

The wikipedia entry here is very down to earth, just read it again. I found it very easy to read through, consider this:
I'm 14.

---

### Post by ninja_numbnuts on 2009-06-10
> **dragos240 said:**
> The wikipedia entry here is very down to earth, just read it again. I found it very easy to read through, consider this:
I'm 14.

I'm 13 :(

---

### Post by Tipped OuT on 2009-06-10
Basically, (and I mean basically) it's just your internet address.

---

### Post by zekopeko on 2009-06-10
> **ninja_numbnuts said:**
> I looked at the wiki page but it's too technical for me! Please explain for dummies :P

it's like a real world address. it goes from 0.0.0.0 to 255.255.255.255. most websites get a permanent one. simple users like you and me get a random one from our ISP's IP address pool everytime your router connects to your ISP.
now how do website address such as ubuntu.com resolve to number?
well you have what's called Domain Name Server (DNS) all round the world that have tables with one column having a name of the website while the other column has an associated IP address number. so when you type [www.ubuntu.com](www.ubuntu.com) your router ask your ISP DNS server what address is [www.ubuntu.com](www.ubuntu.com). and the server say: well it's 91.189.94.8 and then a route is created for your connection to the ubuntu webpage.

easy as that.

here is a simple wiki article(less technical then the one already posted): [http://simple.wikipedia.org/wiki/IP_address](http://simple.wikipedia.org/wiki/IP_address)

---

### Post by ninja_numbnuts on 2009-06-10
> **Tipped OuT said:**
> Basically, (and I mean basically) it's just your internet address.

Lol, I know that! Can please explain what dynamic ip, static ip and DCHP mean?

---

### Post by zekopeko on 2009-06-10
read my post. it's in the first paragraph.

---

### Post by ninja_numbnuts on 2009-06-10
> **zekopeko said:**
> read my post. it's in the first paragraph.

Thank you! Can you please explain DCHP?

---

### Post by CharmyBee on 2009-06-10
It's a way to make automatic configuration of IP addresses easier, depending on your router. It's not required, but it helps for those that use portable OS or Live CDs.

---

### Post by Redache on 2009-06-10
DHCP (Dynamic Host Configuration Protocol) is a way of distributing Dynamic IP Addresses to Network Devices. For Example a Router will use DHCP to give your Laptop an IP Address dynamically as soon as it connects. Static IP's can be used so that every time you connect your Laptop to That Network, It takes on the same IP Address every time.

[http://en.wikipedia.org/wiki/DHCP](http://en.wikipedia.org/wiki/DHCP) is a good place to read more about it.

But normally all you'd need to be aware of is that usually with an Internet Connection you'll have a Dynamic IP from your ISP (Although there are some ISP's who allocate Dynamically but try to give you the same IP address continuously for 6 months and then changing it.) unless you are specifically paying for a Static IP address (Usually unecessary unless you want to run a server/VPN.

---

### Post by lisati on 2009-06-10
> **ninja_numbnuts said:**
> Thank you! Can you please explain DCHP?

An IP address is a bit like a phone number: in the same way a phone number can be used to identify a particular phone line and sometimes even which area the phone is in, an IP address can be used to identify a particular computer and sometimes the general area where the computer is.

Normally a phone number relates to just one phone (or group of phones). To a point, the same thing can be said of IP addresses. But what happens when there are more possible connections than available IP addresses? DHCP goes some way to helping: on the assumption that not everyone is going to be connected at the same time, it allows the networking gadgets select an IP address as and when required.

---

### Post by schauerlich on 2009-06-10
> **ninja_numbnuts said:**
> I looked at the wiki page but it's too technical for me! Please explain for dummies :P

> **ninja_numbnuts said:**
> Lol, I know that! Can please explain what dynamic ip, static ip and DCHP mean?

> **ninja_numbnuts said:**
> Thank you! Can you please explain DCHP?

Can you google?

---

### Post by nmccrina on 2009-06-11
> **EDavidBurg said:**
> Can you google?

Hey, I too have some of these questions, and found that most internet resources (google, wikipedia) invariably inundated my brain with an annoying amount of jargon. I found some of the replies in this thread helpful! :p

Though I sort of agree, it might be presumptuous to expect a collaborative networking manual, written in real time by denizens of ubuntuforums! ;)

---

### Post by Delever on 2009-06-11
Internet address is address of some computer on the Internet. If you know someone's address you can communicate (same as sending mail). In this point of view address is like mailbox.

It is usual for computer to have dynamic address, especially when connected over DSL line. Think of it as mailbox which could be assigned to users only when they are using Internet. As soon as they stop using, this address can be given to some other user.

Your computer could also be in internal network. In such case you would not have public address, butonly address just for this local network. However, all computers could still access Internet. Think of this as bunch of people using the same mailbox. They can send messages out, but mailbox is where incoming message stops. Actually, you can *connect* to outside, and once you are *connected*, you *can* receive. Internal network is managed by router, and it can be configured to forward connections to appropriate users. This mechanism is called NAT (network address translation).

DHCP helps computer to get new unused address on the network, when it is not static.

---

