---
title: "Is someone hacking into my music?"
date: 2009-08-10
forum: Security
---

### Post by Dark Aspect on 2009-08-10
Hello,

When I open rhythmbox I have some unknown shared by the name of Mary's itunes? I have not a single clue who that might be, is it possible that someone has hacking into my music?

[IMG]http://img146.imageshack.us/img146/2865/screenshoti.png[/IMG]

eth0 shows no network activity going up or down when I am idle and when I right click on "Mary's itunes" and click on disconnect it doesn't do anything.

What does this shared network drive mean? and how can I get rid of it?

---

### Post by Riaku on 2009-08-10
Are you on a strange network( college or other network) or your home network?

---

### Post by Dark Aspect on 2009-08-10
> **Riaku said:**
> Are you on a strange network( college or other network) or your home network?

Hm, Home network right now. There are two other computers on the network my Dad's computer and my brother's computers. None of which should have a shared folder named Mary to my knowledge.

I should add that the other computers have Ubuntu 8.04 and Windows XP on them, I have Ubuntu 9.04.

---

### Post by bekind2thenoob on 2009-08-10
Is you home network encrypted?

Could mary be stealing your bandwith?

---

### Post by wojox on 2009-08-10
You can share music on a Lan with rythmbox. Do you have a wireless router?
Is it secure?

---

### Post by Riaku on 2009-08-10
well my best guess would be someone is bumming your network connection. I show those a lot around my school, no ones hacking your music. Just some idiot using Limewire. Frostwire is better IMO

---

### Post by Dark Aspect on 2009-08-10
> **bekind2thenoob said:**
> Is you home network encrypted?

Could mary be stealing your bandwith?

Don't know, my dad handles most of the network. I see if I can't get him to disconnect and change the wireless password and connect back up.

> **wojox said:**
> You can share music on a Lan with rythmbox. Do you have a wireless router?
Is it secure?

Yep, it wireless. Has wep though but I guess it could still be insecure. Can rythmbox go over the Internet or only a lan?

> **Riaku said:**
> well my best guess would be someone is bumming your network connection. I show those a lot around my school, no ones hacking your music. Just some idiot using Limewire. Frostwire is better IMO

Hm.........

I am not happy sharing my music collection with anyone, hopefully I can fix this.

---

### Post by bekind2thenoob on 2009-08-10
> **Dark Aspect said:**
> 
Hm.........

I am not happy sharing my music collection with anyone, hopefully I can fix this.

In rhythmbox go to edit>plugins and uncheck DAAP Music sharing.

---

### Post by wojox on 2009-08-10
Yes it connects over the internet but it shares really easy locally. Have you Dad change to WPA2. Google wep hacking and see how  many hits it gets. It's a deprecated algorithm. It could be your brother messing with you too.

---

### Post by headshotaof on 2009-08-10
yea switch to a WPA2. go to START->RUN->CMD type in ipconfig /all
get your default gateway number. Open your web browser. type in the number. Go to your security settings and change it. Also you can go to i think it is DHCP client list which is also there. and find out who is all connected to your network and find their ip address.:popcorn:

---

### Post by Dark Aspect on 2009-08-10
solved

My dad fixed the problem by setting up the network differently, I think we're using WPA2 now. Connection was still there but after I reset my computer it was gone.

thxs

---

### Post by pdtpatrick on 2009-08-11
Ubuntu uses avahi daemon which would discover anything you have on your network especially multimedia related. So if you don't know who that person is then its possible you have an open wireless connection that someone else has become part of. 

You can scan your network to see the computer that is on. 

sudo nmap -sT -T4 -O ipaddress

But locking down your network as you just did will fix the issue as well :)

---

### Post by theZoid on 2009-08-11
> **pdtpatrick said:**
> Ubuntu uses avahi daemon which would discover anything you have on your network especially multimedia related. So if you don't know who that person is then its possible you have an open wireless connection that someone else has become part of. 

You can scan your network to see the computer that is on. 

sudo nmap -sT -T4 -O ipaddress

But locking down your network as you just did will fix the issue as well :)

"nmap" command not found?  is that a typo?  thanks  Jaunty 64

---

### Post by cariboo on 2009-08-11
Nmap isn't installed by default either use, Synaptic, Add/Remove, install it manually, or click the link.

[apt://nmap](apt://nmap)

---

### Post by ixpl on 2009-08-12
Yeah you may have a visitor on your LAN : ) I would take a look at scanning around with nmap or watch a little wireshark to find out who. Also your routers dhcp client table could point you in the direction. Type in the routers IP in a browser address bar and check the logs, also switch the encryption to WPA2. --Good Luck!    edit---D@mn didn't see all the replies sorry to over post : )

---

### Post by Dark Aspect on 2009-08-12
> **cariboo907 said:**
> Nmap isn't installed by default either use, Synaptic, Add/Remove, install it manually, or click the link.

[apt://nmap](apt://nmap)

Thanks, obviously fixed now but still very useful for when I start my own network.

Only shows two peers now :)

---

