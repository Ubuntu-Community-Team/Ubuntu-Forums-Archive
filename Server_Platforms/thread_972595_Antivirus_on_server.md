---
title: "Antivirus on server"
date: 2008-11-05
forum: Server Platforms
---

### Post by petersenmde on 2008-11-05
I am in the setup/testing phase of a Ubuntu Hardy Heron 8.04 server which will be replacing a windows 2000 server. We have about 20 XP workstations with our ISP hosting our company email - each XP workstation uses an email client to retrieve mail from the ISPs mail server. We have been using Symantec Corporate Antivirus which uses a management console on the server to pass updates to each workstation.

Symantec does have a linux version but it does not have the same management functions as the Windows version and amounts to option 1 below.

I am not sure what to do about antivirus for the XP workstations.

1 I can convert the workstation installs to unmanaged and allow each  workstation to update across the internet to Symantec - which will mean a lot of network traffic

2 Another way I can go is to run Windows XP in a virtual machine on the server, and then install Symantec on the virtual machine. - I may have problems getting the virtual machine to run as a service.

3 Or install Symantec on an older pc/workstation to act as the antivirus server. - Another machine to maintain.

4 Or does anybody have a better idea?

Thanks for any assistance.

Mark

---

### Post by mike010 on 2008-11-05
petersenmde 


no don't put windows on there look at avast for linux if it is for a company they still have it for linux and windows but you need to buy it there are free
company antivirus out there just google it.As for the server linux does not get virus like windows so all you would have to worry about is internet access
and email for the windows what i would do is get a virus scanner for email
server set it to auto update then use wine to run Symantec management console
and update all the xp computers from there.Link to wine

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

or look at this 

[http://www.onino.co.uk/computer_software/computer_associates_etrust_antivirus_v7_1_etrave7125bpmx_for_pc_unix_mac_linux.html](http://www.onino.co.uk/computer_software/computer_associates_etrust_antivirus_v7_1_etrave7125bpmx_for_pc_unix_mac_linux.html) 

Linux free
[http://www.avast.com/eng/download-avast-for-linux-edition.html](http://www.avast.com/eng/download-avast-for-linux-edition.html)

They also have a free windows version here

windows free
[http://www.avast.com/eng/download-avast-home.html](http://www.avast.com/eng/download-avast-home.html)


friends don't let friends use windows.

---

### Post by petersenmde on 2008-11-07
Thanks for the reply Mike010.

I looked at the software you suggested, however I don't see any that fit my needs. As this is a business, I cannot use any of the free/home versions, and I did not see any that could manage the clients through the server.

I have 3 months of support left with Symantec so here is what I am going to do now. As the end of my support contract gets closer, I'll re-evaluate.

Symantec has what they call Live Update Administrator (LUA) which can download updates for any Symantec product and make it available to local client machines. LUA can generate a host config file to point the clients to the updates. I have installed it on a workstation that is already on 24/7. On the Ubuntu server I am going to run Clam and scan the Samba folders.

What gets me is Symantec's LUA which will only run on a Windows NT PC is built on Apache Tomcat and Postgresql - both open source software applications.

My main concern was the amount internet traffic there would be with all of the clients individually downloading updates, and Symantec's LUA should take care of that.

Mark

---

### Post by mike010 on 2008-11-08
does all your internet connections on windows workstations connect to the internet threw the server and are you running a email server?

if so install a antivirus on the server to scan email and internet connections from the server i am not a big clam antivirus fan there are better ones out there.

or the way i would handle it

install a software called wine it will let you install and run windows software on your linux system and you can still run your norton and have all the pc update from there.wine is great i use it to run autocad 2008 and it does a great job it is also open source so you can just download and go and it will solve a few more problems in the years to come if you was to get a new antivirus software or maybe some software that does not come with a linux version and you don't have to run Windows XP in a virtual machine on the server to do this
link to wine
[http://www.winehq.org/site/about](http://www.winehq.org/site/about)



I do not thank there is a cross platform software out for linux
linux does not get virus like windows

friends dont let friends use windows

---

### Post by windependence on 2008-11-08
AVG has a great corporate product:

[http://www.avg.com/business-security-comparison](http://www.avg.com/business-security-comparison)

Trend Micro is another good choice. I am not a fan of Symantec or McAfee.

If you need help when you are ready to do it, I am an AVG reseller. I can give you a volume quote if you need it, and they also have a version to install on a gateway box if you need it.

-Tim

---

### Post by mike010 on 2008-11-08
> **windependence said:**
> AVG has a great corporate product:

[http://www.avg.com/business-security-comparison](http://www.avg.com/business-security-comparison)

Trend Micro is another good choice. I am not a fan of Symantec or McAfee.

If you need help when you are ready to do it, I am an AVG reseller. I can give you a volume quote if you need it, and they also have a version to install on a gateway box if you need it.

-Tim

hello
what i think he is trying to do is update all of the pcs from one place like Symantec corporate it has software to that from the server but not for linux server only windows.Does avg have a cross platform software?

---

### Post by windependence on 2008-11-08
I know they have a version for each platform but I do think they are separate products. 

They do have the central update and management feature though. Here is more info on that:

[http://www.avg.com/product-avg-admin](http://www.avg.com/product-avg-admin)

-Tim

---

### Post by mike010 on 2008-11-08
oh learn something new every day that is cool so you can update antivirus on windows from linux thanks i thank that is what he is looking for and i have learned something to

---

### Post by petersenmde on 2008-11-09
I checked out AVG Admin. - It only runs on Windows. - Checkout the system requirements.

It seems that at this time there is no antivirus management software that runs on a Linux server.

How are bigger companies managing antivirus on their workstations? or is everybody running Windows servers?

Thanks

Mark

---

### Post by mike010 on 2008-11-09
not all run windows servers in fact most run linux or unix servers.I am no fan of avg anyway when i used it avg would not pick up some viruses.I did not ever know of something like that
what my work place did was on there linux server install a antivirus then use a software called wine and use the management console to update norton i use wine for running autocad
on my home pc and it does great.

---

### Post by windependence on 2008-11-11
Running Norton on Wine isn't what I would call production ready. It may be working for them but it can't be stable. 

I was going to suggest ClamAV as I have had good success with it, but some folks didn't seem to be so hot on it. It is good IF you keep it current, and of course it runs on Linux among other platforms.

I guess everybody has their opinions when it comes to AV. ;)

-Tim

---

### Post by Philio on 2008-11-11
Is it such a big deal just to have the clients updating indervidually over the internet? :)

Virus definition updates are not massive! It won't require much network usage at all.

This doesn't exactly solve your problem but it would be a quick and simple solution.

If your worried about internet traffic volumes then consider using an internal mail server as already suggested as this could potentially be using tonnes of bandwidth (depending on email content).

---

### Post by mike010 on 2008-11-11
> **windependence said:**
> Running Norton on Wine isn't what I would call production ready. It may be working for them but it can't be stable. 

I was going to suggest ClamAV as I have had good success with it, but some folks didn't seem to be so hot on it. It is good IF you keep it current, and of course it runs on Linux among other platforms.

I guess everybody has their opinions when it comes to AV. ;)

-Tim

there not running norton on wine just the management console for
updating windows clients. Wine runs real good if it is set up right like i said before i run autocad 2008 on wine and have not had anything go wrong so far.There should be a cross platform
software out there the problem is finding it but wine opens up a door to find easy ways of doing this kind of stuff.Autocad is the most used program for drafting out there is not a software out for linux that will do everything it will wine opens up that so people can get the best of both worlds and if it is set up right it is very stable.

as far as letting norton update on each computer well in a perfect world that would be fine but if you have a lot of money on the line and a virus shuts you down because one forgets to update one day or one pc does not update for some reason then that is a big problem i can see why if you can update all pc's form one place that it would be better but it is not a perfect world and i guess it's what works for you.

---

