---
title: "Why aren't ip addresses portable like phone numbers?"
date: 2007-11-13
forum: The Cafe
---

### Post by hkgonra on 2007-11-13
I just went through an expensive mess when my isp merged with another at my business. I had to re-buy some server software ( no linux alternative exists ) that was tied to my ip address and go through and notify , and re-notify , and re-notify , and re-notify my over 100 users about the change in the address. 
Considering my phone number is mine , why can't my ip address be mine ?


EDIT , I meant to say portable in the subject line.

---

### Post by aks44 on 2007-11-13
> **hkgonra said:**
> I just went through an expensive mess when my isp merged with another at my business. I had to re-buy some server software ( no linux alternative exists ) that was tied to my ip address and go through and notify , and re-notify , and re-notify , and re-notify my over 100 users about the change in the address. 
Considering my phone number is mine , why can't my ip address be mine ?

That's why domain names exist... :)

---

### Post by DoctorMO on 2007-11-13
1) you should endever to use DNS name spaces to make ip-addresses a technicality
2) You really should try to find open source packages for running your servers.
3) Neither your phone number or your ip-address is "yours" since it's an agreement between the society that runs the network and you and thus can't be owned, it's the same reason why you don't own your address but you do own the door step the address points to (and you tend not to be able to move a house around).

---

### Post by megamania on 2007-11-13
> **DoctorMO said:**
> 3) Neither your phone number or your ip-address is "yours" since it's an agreement between the society that runs the network and you and thus can't be owned, it's the same reason why you don't own your address but you do own the door step the address points to
Yes, but still I can change phone company and keep my phone number (both with landline and mobile phones).

---

### Post by saulgoode on 2007-11-13
The real question is why do phone numbers still exist? Surely there is enough technology inherent in the telephone system to contact people using names.

---

### Post by sailor2001 on 2007-11-13
suggest you read up on ipv6

---

### Post by hkgonra on 2007-11-13
> **aks44 said:**
> That's why domain names exist... :)


That would have helped on my users but not on my licenses that had to be purchased to work only with a specific  ip address.

---

### Post by hkgonra on 2007-11-13
> **sailor2001 said:**
> suggest you read up on ipv6

Could you please expand on that ?

---

### Post by BWF89 on 2007-11-13
> **hkgonra said:**
> Considering my phone number is mine , why can't my ip address be mine ?
Unless you own the phone company it's not actually yours. Their just letting you use it.

---

### Post by BDNiner on 2007-11-13
That is a very good point. With our static IP addresses from our DSL company we can move them to another location. When we moved offices we were able to keep the same static IP addresses. You have to pay more for the static IPs.

using people's names would be next to impossible to implement without phone numbers. I could see a DNS system for phone numbers where your name would point to your phone number. but i don't think it is practical.

I don't think ipv6 would apply here. it is just an expansion on the current ipv4 system. only to allow more ip addresses since we are close to running out of the current ipv4 addresses. plus it is backwards compatible. so accessesing ipv4 address would still work the same way.

What software required you to link it to your ip address. there was no way to change the ipaddress on their system. From what you have said it seems like your IP was hard coded into their software and they should not charge you to change that section of the code. that is a tough situation to be put in by a vendor.

---

### Post by boast on 2007-11-13
don't ISPs buy large ranges of IPs? So selling one IP to another ISP for customers to switch would be messy.

---

### Post by hkgonra on 2007-11-13
> **BWF89 said:**
> Unless you own the phone company it's not actually yours. Their just letting you use it.

They are required by law to let me keep it when I change vendors , why couldn't ip's be the same ?

---

### Post by hkgonra on 2007-11-13
> **boast said:**
> don't ISPs buy large ranges of IPs? So selling one IP to another ISP for customers to switch would be messy.

That is the same argument the cell and landline phone companies used but it works just fine.

---

### Post by hkgonra on 2007-11-13
> **BDNiner said:**
> 

What software required you to link it to your ip address. there was no way to change the ipaddress on their system. From what you have said it seems like your IP was hard coded into their software and they should not charge you to change that section of the code. that is a tough situation to be put in by a vendor.


It was an activation key that went with the ip address of the machine in order for the software to work. 
Had to buy new software to get a new key. 
Just in case somebody brings this up , I tried getting one for an internal ip address ( 10.x.x.x)  and then would have routing setup in my firewall so it wouldn't matter if my ip address changed again , but they wouldn't do it. Has to be an externally routed ip address that is setup as the static address on that machine.

---

### Post by amadeus266 on 2007-11-13
I'd be looking for a new software company. They should not have been able to make you repurchase the software and licenses just because of an IP change. Sounds too much like Microsoft to me.

---

### Post by Frak on 2007-11-13
Just like phone numbers, IP addresses are bought, but since they are non-important, changes are made often. From there, the canonical servers are notified of the change (considering your DNS addresses changed also) and you have a new name. Phone #'s though, would be hard to keep up with.

---

### Post by phrostbyte on 2007-11-13
IP addresses are licensed in groups. There is no real way to do what you want unless the government intervenes, and if the government intervenes we should switch to IPv6 anyways. IPv6 will give you an ridiculously large  amount of IP addresses (like a billion trillion) per user, and thus remove the need for NAT and dynamic IPs many people use today because of the IP shortage.

---

### Post by hkgonra on 2007-11-13
I just want to say if I sounded snippy to anyone I am sorry. 
It is just frustrating. 
Phone numbers were bought in blocks as well ( at least cell numbers were ) but they can do it so I am still looking for a reason that IP addresses couldn't be the same.

---

### Post by popch on 2007-11-14
> **hkgonra said:**
> I just want to say if I sounded snippy to anyone I am sorry. 
It is just frustrating. 
Phone numbers were bought in blocks as well ( at least cell numbers were ) but they can do it so I am still looking for a reason that IP addresses couldn't be the same.

It's because the IP address 'describes' the route from your provider's servers to your gateway or PC. It is not just an identifying number.

You won't keep your street address, either, when you move to another town.

---

### Post by Sporkman on 2007-11-14
> **popch said:**
> It's because the IP address 'describes' the route from your provider's servers to your gateway or PC. It is not just an identifying number.


That's not a very good setup - fast I'd think, but not good, as it's not very flexible or "data-driven", so to speak.

---

### Post by popch on 2007-11-14
> **Sporkman said:**
> That's not a very good setup - fast I'd think, but not good, as it's not very flexible or "data-driven", so to speak.

True. However, that's how the internet (rather the IP) works. As someone already has suggested, look up the IP RFC.

---

### Post by koenn on 2007-11-14
> **hkgonra said:**
>  were )  so I am still looking for a reason that IP addresses couldn't be the same.
You can't see it on first sight, but your IP address consists of a network number and a host (computer) number.
the network number attaches you to the network of your ISP, and makes your computer routable, i.e. you can communicate with other computers (on the internet) because they know what network you belong to and how to reach it. 
That's whay change of ISP --> change of IP address, 

And because of that, using DNS names in stead of IP addresses is always a good idea. That's what they're for, to make abstraction of the underlying network infrastructure. That answers your question about 'not very flexible": you have to see the complete TCP/IP protocol stack, not just the IP component. 

although in this case ( a take over) they could probably have made an effort to keep the IP addresses, I think, and DNS apparently wouldn't help you with that dirty trick of license depending on an IP address

---

### Post by Bruce M. on 2007-11-14
> **megamania said:**
> Yes, but still I can change phone company and keep my phone number (both with landline and mobile phones).

Depends on where you are.  Phone numbers here are not portable.

---

### Post by LaRoza on 2007-11-14
I immediately thought of IPv6 (and [this]("http://www.youtube.com/watch?v=_y36fG2Oba0")) when I saw the thread title.

---

### Post by Frak on 2007-11-14
> **LaRoza said:**
> I immediately thought of IPv6 (and [this]("http://www.youtube.com/watch?v=_y36fG2Oba0")) when I saw the thread title.
great song :)

---

### Post by inversekinetix on 2007-11-15
Outside of this country I don't think there are many IPv6 capable networks yet are there?  We're set to run out of IPv4 assignments in the near future but not many places seem to be rushing to get ready for the change.  It could be a disaster.

We also buy our phone numbers here (from what I can make out)  you buy the number and then rent a line, the number is yours wherever you go forever.

---

