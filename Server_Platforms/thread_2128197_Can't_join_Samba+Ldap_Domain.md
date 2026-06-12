---
title: "Can't join Samba+Ldap Domain"
date: 2013-03-22
forum: Server Platforms
---

### Post by Bathroth on 2013-03-22
Hey people,

im kind of new to Ubuntu and trying my best to get started fast. I am trying since 1 week to get my Ldap+Samba server to run as a domain. 
I finally figured it out how to configure both servers together with many diffrent tutorials.

Now im at a point where i can add easily the users and groups with smbldap-useradd for example. But i cant join the domain with my windows workstation!

My Samba shares work fine! i can see the shares on the LAN and with the samba/ldap credentials i can log me in for watch the files! 

But why i cant log onto my domain?
When i put on my windows client on the Domainfield the domain name and push okay, he ask for my Domain credentials. So he find my domain. But he wont join the domain for any reason i dont know ...

"Error on trying to join domain" (i translated it from español so im not sure how the real error sounds on english windows!)
"the specified domain dont exist or could not seet in contact with it"

My Server:
Ubuntu-server 12.04 LTS
samba 3.6.3
slapd 2.4.28-1

The main tutorials i used:
[https://help.ubuntu.com/12.10/serverguide/openldap-server.html](https://help.ubuntu.com/12.10/serverguide/openldap-server.html)
[https://help.ubuntu.com/12.04/serverguide/samba-ldap.html](https://help.ubuntu.com/12.04/serverguide/samba-ldap.html)
[https://help.ubuntu.com/11.10/serverguide/samba-dc.html](https://help.ubuntu.com/11.10/serverguide/samba-dc.html)

Anyone can help me please. If u need any Config file or something i can give it to you!

Thanks in advance,
Bathroth

---

### Post by ally_uk on 2013-03-22
Use Windows Server it's alot more easier :) lol

---

### Post by Bathroth on 2013-03-22
That doesn't help .....
you know a solution or not? and dont tell me to change to windows servers .... why ppl are doing linux huh? because its more difficult?

---

### Post by ally_uk on 2013-03-22
Well in the Windows World it's a case of clicking one button create a domain controller in the linux world it's a case of editing config files hacking bits and pieces together, tearing your hair out and praying to god that it works and when it goes wrong you either have to be a professor or a god damm genius :)

---

### Post by darkod on 2013-03-22
Is your samba server set as DNS on the client machine? Not sure if it has anything to do when using samba as DC, but even in windows it will have problems joining a domain if the DC is not a DNS server for the client machine.

Does it prompt you for administrator password to join a domain or it doesn't even get that far?

---

### Post by Bathroth on 2013-03-22
> **darkod said:**
> Is your samba server set as DNS on the client machine? Not sure if it has anything to do when using samba as DC, but even in windows it will have problems joining a domain if the DC is not a DNS server for the client machine.

Does it prompt you for administrator password to join a domain or it doesn't even get that far?

Yes it prompt me for the login details to join it.

Or is there anything wrong with the netBios? accepted already the option with wins support but still nothing.

Also told the client about who is the DNS and it isnt working.
The same error ...

At the moment i made all again on a virtual mashine. Working now with 1 win7 client and 1 ubuntu server on 'net intern' for better testing.

Have any more ideas?

---

### Post by darkod on 2013-03-22
In that case investigate a little if you have the administrative user set up correctly. Unfortunately I haven't worked with domains so I don't know what to check directly. You will have to google it until someone else jumps in. Usually it will not even prompt you for the admin user if it can't find the domain, so that part seems to work fine.

It looks like it's failing when the admin user needs to join the machine to the domain.

---

### Post by Bathroth on 2013-03-22
> **darkod said:**
> In that case investigate a little if you have the administrative user set up correctly. Unfortunately I haven't worked with domains so I don't know what to check directly. You will have to google it until someone else jumps in. Usually it will not even prompt you for the admin user if it can't find the domain, so that part seems to work fine.

It looks like it's failing when the admin user needs to join the machine to the domain.

First i want thank you for helping me out.

Just now i tried also one point to watch if the ldap is available with the Ldap URL:

ldap://hostname:port

It opened a window to find persons. It seems that the server is really available.
I guess you are right. Ill investigate and google some arround about that.

If someone else have any ideas. Im open for everything :)

Regards,
Bathroth

---

### Post by lingpanda on 2013-03-22
> **Bathroth said:**
> First i want thank you for helping me out.

Just now i tried also one point to watch if the ldap is available with the Ldap URL:

ldap://hostname:port

It opened a window to find persons. It seems that the server is really available.
I guess you are right. Ill investigate and google some arround about that.

If someone else have any ideas. Im open for everything :)

Regards,
Bathroth

So you can connect to the domain on your virtual machine but not on physical devices? Can you ping the domain? ie. ping example.domain.com?

---

### Post by ally_uk on 2013-03-23
Ignore the windows comments I was being a idiot :)

---

### Post by Bathroth on 2013-03-25
> **lingpanda said:**
> So you can connect to the domain on your virtual machine but not on physical devices? Can you ping the domain? ie. ping example.domain.com?

Maybe i didnt explained well. My english is a bit rusty since im living in south america ...

If i want join the domain on my physical server, it asks me in my windows client for the login credentials to join it.
So i put the Logindata of my ldap-samba admin and password inside and he say that the domain dont exists OR he cant contact the server.

So i tried 2 things: 
1. put any name inside -> other error that AD could not be found
2. in windows explorer the ldap address like written one post above -> and he wants to search people in my AD

-> so the domain is available but my windows client can not join the domain

Now Ping:
ping 192.168.10.104 --> fast ping tiempo <1m
ping domain.com --> slow ping tiempo=260-460m          [SIZE=5]//edit:[/SIZE] that was stupid -i pinged the webaddress of the company i work for so of course i got a good ping with slow ms ...](*,)](*,)

So domain also pingable over dns name.

tried again to connect - same error!

Ive got now one question. Its the first time im doing LDAP + SAMBA. 
Samba standalone in smb.conf : workgroup=domainname
samba + LDAP in smb.conf : workgroup=domainname.com ??? or just workgroup=domainname

Till now i just tried like usual on Samba workgroup=domainname
Just now i tried with domainname.com but also wont work.

But could it be an issue about the domainname dc=domain,dc=com and the workgroup in samba?

In my tutorials i used they dont talk about that part sadly.

Thanks in advance for your help guys.

> **ally_uk said:**
> Ignore the windows comments I was being a idiot :)

Its okay - you just read that im kind of new in Linux and thought that its a number too big for me.

But we need watch first. What is 'kind of new to Linux'?
Linux is so big that if u can do some ftp lamp samba servers - you are not even good in linux. Just a beginner trying to learn about Linux right?? :D ;)

Regards,
Bathroth

[SIZE=5]//edit
[SIZE=2]Changed now in my smb.conf workgroup= domain.com
As i tried it before i had all WITH CAPSLOCK and now ive written it normally like in my ldap configuration and it asks me also for my Logincredentials - Still dont want to join my domain :([/SIZE]
[/SIZE]

---

### Post by darkod on 2013-03-25
Do you have the ldap related options in smb.conf? Not sure if something like this can help:
[https://help.ubuntu.com/10.04/serverguide/samba-ldap.html](https://help.ubuntu.com/10.04/serverguide/samba-ldap.html)

You have more documentation for 12.04 LTS here:
[https://help.ubuntu.com/12.04/serverguide/network-authentication.html](https://help.ubuntu.com/12.04/serverguide/network-authentication.html)

---

### Post by Bathroth on 2013-03-25
> **darkod said:**
> Do you have the ldap related options in smb.conf? Not sure if something like this can help:
[https://help.ubuntu.com/10.04/serverguide/samba-ldap.html](https://help.ubuntu.com/10.04/serverguide/samba-ldap.html)

You have more documentation for 12.04 LTS here:
[https://help.ubuntu.com/12.04/serverguide/network-authentication.html](https://help.ubuntu.com/12.04/serverguide/network-authentication.html)

Thanks again,

But this 2 tutorials i used for installation and did all the same.

The only thing what i didnt had was:

ldap ssl = start tls
I had no ssl! Ill check my other configurations about tls and ssl for be sure its not fault of this ...

[SIZE=5]//edit:[/SIZE]
[https://help.ubuntu.com/12.10/serverguide/openldap-server.html](https://help.ubuntu.com/12.10/serverguide/openldap-server.html)
On this tutorial in the section of TLS - this is neccesary for get it working? 

I was thinking of doing without ssl/tls - but if its needed ill go for it to try ...

---

### Post by darkod on 2013-03-26
One thing I noticed in the tutorials is that it says you first have to create an entry for the XP machine in LDAP. Have you done that? It says you need to do that before you try joining it to the domain. The entry has to have the same computer name as the XP machine.

Also, is your XP VM networking option NAT or Bridged? If you are using NAT I'm not sure if that can interfere since the traffic gets NATed. Try in Bridge mode so that the XP VM has an IP in the same subnet where your LDAP server is. Most VMs use NAT by default but i always change it to Bridge to have the machine in my LAN.

---

### Post by Bathroth on 2013-03-26
Hey Darkod,

ill check that if i have the Machine in my LDAP. 

And bout the VMs. I remade the server as VM and made an Windows maschine for checking. Both running as VM as IntNet - so internal LAN.

So there should not be a problem about that or no?

Regards

//edit:
Now added the maschine account to samba+ldap over smbldap ... Or i have to install ldapscritps and make it only over ldap?

The point is that i want to have all automatically. Like a samba PDC - joining the domain, autimatically over root preexec creating the userfolders and automatically adding the maschine to the server. I dont want to do it manually. 

any ideas? :S

---

### Post by darkod on 2013-03-26
I don't have detailed experience of this, but I think you are looking at it the wrong way. You want to use samba for controller but in reality the OpenLDAP is the controller. Samba can use the users in LDAP to authenticate who can do what, but it's the LDAP holding the users and the groups, etc.

About the VMs. I'm not sure what IntNet is, In Virtual Box it's called NAT mode vs Bridged mode for example. The IP of the virtual host has to be in the same subnet as the IPs of the virtual guests (the LDAP server and the client machine). Testing in virtual machines is very good but you have to be careful not to get yourself into trouble if you leave them as stand-alone NATed devices. When you look at the IP of any machine in your home, the server IP has to be in the same subnet.

I assume you set a static IP on the server. In that case you should know if the IP is in the same subnet as your home network.

This could be the issue because of which it's not working as you expect it all the way.

---

### Post by Bathroth on 2013-03-26
Thanks for the reply,

I guess you are right about the way i look at LDAP - just my boss wants that i use ldap for any reason noone knows. He doesnt know about linux. For our use a Samba would be enough. For that im trying to get the LDAP to run. Ill watch agian about the administrative user. But it seems that i created him without any problems.

About the Virual Maschines. In my virtualBox i got an option which is called 'Internal Network' ([http://www.dedoimedo.com/computers/virtualbox-network-sharing.html](http://www.dedoimedo.com/computers/virtualbox-network-sharing.html))
So its a Lan inside of VirtualBox and the IPs are all in the same subnet (192.168.1.xxx 255.255.255.0)

Thanks so far for your help. Because im working as support and making servers i have not enough time for investigate all the time. So ill write again if i found something/changed anything. Getting on my nerves stopping my investigation all the time for doing support ... !

Regards,
Bathroth

---

### Post by darkod on 2013-03-26
I would still give a shot to the Bridged Adapter option in place of Internal Network. That will also allow you to try reaching the server from your physical machines, unless you don't want this. Maybe you want to prevent the server to be on your LAN but if no one knows about it I doubt people will find it and try to access it. And for you it can help with the dilemma whether you have something wrong with the server settings, or simply the network settings.
I guess pinging between the VMs works just fine? Can you try a SSH session from the VM client to the VM server? That could show you if networking is fine because sometimes ping works but a specific service like ssh or ftp will not be routed correctly between them.

If you are only after a few different users to share samba, installing ldap is really not necessary. In that case yes, you could run and control everything with the samba users administration.

In case od ldap i see it similar to AD. It hold the configuration of all the domain, it runs the show, and any administration is done with the ldap scripts or maybe a GUI tool like LDAP Admin, etc. Samba can only use existing users instead of creating the same users two times. But samba doesn't run the domain and user administration. That's how i understand it.

---

### Post by Bathroth on 2013-03-26
> **darkod said:**
> I would still give a shot to the Bridged Adapter option in place of Internal Network. That will also allow you to try reaching the server from your physical machines, unless you don't want this. Maybe you want to prevent the server to be on your LAN but if no one knows about it I doubt people will find it and try to access it. And for you it can help with the dilemma whether you have something wrong with the server settings, or simply the network settings.
I guess pinging between the VMs works just fine? Can you try a SSH session from the VM client to the VM server? That could show you if networking is fine because sometimes ping works but a specific service like ssh or ftp will not be routed correctly between them.

If you are only after a few different users to share samba, installing ldap is really not necessary. In that case yes, you could run and control everything with the samba users administration.

In case od ldap i see it similar to AD. It hold the configuration of all the domain, it runs the show, and any administration is done with the ldap scripts or maybe a GUI tool like LDAP Admin, etc. Samba can only use existing users instead of creating the same users two times. But samba doesn't run the domain and user administration. That's how i understand it.

It seems that you have good experience - could i ask you a other question?

The company im supporting day in and out has arround 30 - 40 diffrent users. Groups would be arround 5-10. 

For this kind of company would it be an advantage to use LDAP?

The other company im making the Server at the moment are arround 15 diffrent users and 5 Groups maximum.

Really enough with Samba or am i wrong? Because a PDC in samba i made arround 8 times and is easy to use.

Would be nice if you could answer me that.

Regards

---

### Post by darkod on 2013-03-26
I have no extensive experience with domains on linux, but for 15 users it really looks like there is no point of configuraing ldap. Even for 40 users it might be too much work.

However, we are looking only at the user count. What happens on the desktop clients? Making an analogy to AD, if you have no ldap (and ldap users), can employees change workstations? The local user with their username would have to exist so they could use the machine. If my analogy with AD is correct, you can install a workstation, join it to the domain, and any user that exists in ldap can log in, right? From that point of view, it does serve a purpose even for a small number of users.

Not to mention having their folder available in the network so they can access their data on any machine. But the home folder can be done in samba too.

I don't know the requirements of the companies, and also i don't know in depth the ldap benefits. But it does sound benefitial even for small number of users.

---

