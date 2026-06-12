---
title: "Linux &quot;all-in-one&quot; Server for small NGO"
date: 2010-11-15
forum: Server Platforms
---

### Post by Meissel on 2010-11-15
Hey, this is my first Post here, after reading lots and learning even more =)

This time, i have a task, demanding more skills than ever before:

This is the Situation:
in a small NGO I'll have to upgrade the IT infrastructure. From a poorly organized P2P Network, we want to step up to a Domain we can work (together) in.

Tech. infrastructure:
Modem
| Server (Ubuntu)
| | Switch
| | | Clients (Win, Mac, Linux)
| Wireless AP
| | Clients (Win, Mac, Linux)

To do this, I'll first need a DHCP (DHCP3-server) and DNS Server (Bind9) running. This will be the Gateway. There i also plan to install a Firewall (Firestarter or ufw) and Anti Virus for security reasons.

The thing is, i want to control who and when they use the Internet. and i want to have these permissions administrated centrally. to do that, I'll want to work with a Samba Server who acts as a PDC, with some group-shares and a individual home share for each user (H:\ Drive).

Additionally, i also want to add a wireless network card (in master mode) to the server and let it act as a wireless access point. But to get access to the Internet, you should need to login (with individual login information) to get the right credentials (i.e. The Staff have unlimited access, the students have blocked access during school time). But some students just login with a ipad or iphone, so this should work too. Do I have to realize this with a Radius server, or can this work only with Samba?

I've read about LDAP and Radius. Do I need this for my setup?

Furthermore, I'll just add CUPS and install a shared Printer. (Did this before)

And to complete this setup, i want to realize all this in a single machine. For sure with double NIC, Raid1 and Backup. My guess is, that a Computer with a i5 CPU and 4-8gb ram should handle all this, with a max numbers of users not exceeding 20.

or is it easier to just use zentyal, instead of ubuntu?

I've got enough time to learn and to test, so the more elegant a solution is, the better. But the thing is, Linux Server is such a huge place to start, so I primarily want to know if this is possible (with the chosen Software, All in one Machine), and if someone can give me a hint or something to take care when I start, I'm always thankful!

---

### Post by DasEi on 2010-11-15
He, nice questions, so I I'll give some answers.

With your hardware, i5 and 4 gig ram or more you can realize it.
For not gettting overhelmed and for easy backup I consider you tu use virtualmachines. They can easy be restored and backed up.
So you would startup by setting up up a softraid with 2 similar Hardrives for redundancy first...
You could also use older proc, aka c2d or opteron (cheaper), cache and ram are more important in this scene.
Just keep on asking or get me on irc (#ubuntu), which communication is more responsive , nick DasEi, currently logged in

---

### Post by wongo888 on 2010-11-15
Some other good questions:

[LIST=1]
[*]What operating system is running on the clients?
[*]What applications are most often used by the users (on client machines and on servers)?
[*]What is the IT budget of the organization and what expertise do they have in house (or is support going to be outsourced)? Is it currently outsourced?
[*]Are internal users prepared to learn another OS + apps if they are switching?
[/LIST]

---

### Post by Meissel on 2010-11-16
thx for the replys!

i already had a disscussion with dasEi on IRC, thanks to him i already know what hardware im going to use.

the clients have different os:
mostly win, but also mac and some linux clients
the budged isnt fixed, so i have so options open. but of course, the cheaper, the better =)

applications used are very different. mostly its just internet and officesoftware, but also some other stuff like cubase or photoshop.

the users should be able to stick to their known os, we're not here to train them. but of course, some learning will be required to use the new stuff.

i also know, that i will do all on one server, but with some virtual machines to make management easier.

---

### Post by i.r.id10t on 2010-11-16
You need 2 server boxes - one to work and one as a hot spare.  Use rsync between them to synch over data on a regular basis.  Load a real light distro (bare bones base debian install), load vmware or virtual box, and use several virtual machines (as mentioned).

---

### Post by haplo_dk on 2010-11-19
Hi Meissel and others

I'm more or less in the exact same situation as you: I'm in an NGO with approx. 20 people, different client OS'es (though it will be mostly ubuntu).
What hardware have you decided on?
Also I'm not very experienced - I have all the theoretical background necesary, but not so much practical experience. Do you ( or others listening in :) ) know of any good books, usefull guides, etc.?
I'm setting everything up from scratch and I have 2 months to do it. And everything really does mean everything - from all hardware including switches, servers, IP-phone system, router, wireless access points, wires - to all software: fileserver, access control (radius), backup, VPN, phoneserver (freepbx), webserver (we will have a seperate machine acting as webserver)... well as I said, everything :)
My budget is as yours: not fixed.
Also we will probably invest in new desktop machines for everyone in the office, and I plan on investing in laptops (with dockingstations or simply just sreen, mouse and keybords to plugin to when at the desk). Does any of you have any experience with this?

All advice apreciated :)

Best regards
/Anders:)

---

### Post by Meissel on 2010-11-19
hey!

good to know im not alone having such a task before me =)

i'll go with a i5, 8gb, 2x1Tb HD as rough specs.. but before i buy, i need to clarify some more things:

- The Users should only need one username/pw for all the services (Domain Login and access to the shares (Samba), Auth for the Wireless Access Point

anyone know where i can find some information/tutorials about this? what programs do i need to accomplish this task?

- Im reading about Samba beeing a NT Directory, not Active Directory. What are the major disadvantages? is there anything i cant do for my needs?

- to access the domain and the shares, the windows home editions won't work. but internet access should be possible only with authenification (specific username/pw for each user) on every machine (even Iphone?) attached to the network

One major thing is, the later administration of the Users (add, del, set access times for internet, enable access to shares) should be done by two "non-professionals". of course i'll instruct them, but it should be as easy as possible.

again, thx a lot for all the information and help provided here!!!

---

