---
title: "own isp"
date: 2008-11-28
forum: The Cafe
---

### Post by proguy on 2008-11-28
Just wondering, I have a headoffice with a dsl uncaped account and 3 banches with 2gb accounts, now was wondering is there an easy way for my braches to use the head office as there isp?

If not

Is it possible for the branches to rather be on local accounts only, and have them route there international traffic from the headoffice via an vpn. 

My problem is the users in the branches are only really getting email and remote desktoping to the headoffice(which is local only) but might need to browse an international site from time to time. Any other suhggestions welcome.

---

### Post by steveneddy on 2008-11-28
I think you should try posting this in the networking forums area. You would probably get more responses there as opposed to the community cafe.

---

### Post by madverb on 2008-11-28
1. No.
2. Don't really understand what the problem is with the current setup

Maybe you could be a bit more precise with what you want to achieve

---

### Post by mips on 2008-11-28
> **proguy said:**
> Just wondering, I have a headoffice with a dsl uncaped account and 3 banches with 2gb accounts, now was wondering is there an easy way for my braches to use the head office as there isp?

In a way you could but it would be pretty pointless, whether you use the ISP as a gateway or your HO as a gateway the same amount of traffic is still going to traverse the 2gb adsl  branch links. This would require a VPN setup anyway. Also keep in mind that you will need sufficient bandwidth(speed) at the HO to now cater for all 4 combined sites.

> **proguy said:**
> 
If not

Is it possible for the branches to rather be on local accounts only, and have them route there international traffic from the headoffice via an vpn. 

By local accounts I assume you are referring to an ISP account that only provides for local traffic which is usually cheaper? This would be an option. Ideally you would route ALL traffic via the HO and at that point setup access lists & policies etc for outside access. This also provides a central point for firewalling. Also keep in mind that you will need sufficient bandwidth(speed) at the HO to now cater for all 4 combined sites.

> **proguy said:**
> 
My problem is the users in the branches are only really getting email and remote desktoping to the headoffice(which is local only) but might need to browse an international site from time to time. Any other suhggestions welcome.

We do not really know enough about your network to give you good advice. Depending on various things like quantity of users, amount of traffic, current infrastructure, cost etc there could be various options avaialable to you. One would be routers and dedicated links to your branches or using VPN services on private networks (not the internet) etc.

---

### Post by proguy on 2008-11-28
Hello mips.

Well im also in SA, so basically this comes to cost saving.  My head office is in cape town and  has an uncapped internet connection with static ip's. There is an excange sever 07 receving all the mail and running a terminal server so our branches can access our accounting system.

Now we have 2 branches 1 in JHB and DBN. Both of them currently have 5 users. they both have a 2gb cap conncection. Now all they really do is mail and accounting, and then maybe the odd person might need to browse a websithe not hosted locally. R19 per a gig is alot cheaper than R99 per a gig but then i cant browse international sites. so was wondering if via a vpn i could get my international gatway. if so how?

---

### Post by mips on 2008-11-29
> **proguy said:**
> 
Now we have 2 branches 1 in JHB and DBN. Both of them currently have 5 users. they both have a 2gb cap conncection. Now all they really do is mail and accounting, and then maybe the odd person might need to browse a websithe not hosted locally. R19 per a gig is alot cheaper than R99 per a gig but then i cant browse international sites. so was wondering if via a vpn i could get my international gatway. if so how?

VPN will work for you. With a VPN your remote/branch users will basically become part of your HO LAN and their traffic will be routed just like that of the local pc's.

Do you have ADSL routers that support VPN services? You could buy some or alternatively you could setup pc's to do this.

I have never setup VPNs outside of using Cisco gear but it should not be to hard.

BTW, Who is your ISP?

---

