---
title: "Linux Distro Question"
date: 2007-03-26
forum: The Cafe
---

### Post by Supergoo on 2007-03-26
Hi Guys , 
    Got a few questions here I been playing with a few different Distros Ubuntu 6.10, Opensuse,and Fedora Core 6. I do not care for OpenSuse and trying to understand the each version of Linux, can somebody more knowledgeable help me with the diffences in Fedora Core and Ubuntu ? 
Thanks

---

### Post by MattSMiddleton on 2007-03-26
The main difference you are going to find is package management, Ubuntu is Debian based and therefore uses tools like apt-get and aptitude which make installing software a heck of a lot easier.  Fedora Core is RPM based, and even though their package management has come a long way in the past few years, in my experience it still lacks when compared to Ubuntu.  Other than that tools you can get for Fedora you can get for Ubuntu and visa-versa.  Another difference is that, again from my experience Ubuntu has a far superior community backing it.  That's my two cents.

---

### Post by SunnyRabbiera on 2007-03-27
I feel that ubuntu surpases fedora in many ways:
1: Ubuntu is non intrusive to me, you can use its live CD without even installing anything on your hard drive. Fedora Core has no real live CD installer, it doesnt allow you take a look at the system before you install it, now sure yes a live CD is under works but i feel its lacking compared to ubuntu's
2: Ubuntu's package management is wonderful, it has great programs like synaptic and a vast assortment of programs in its repo's. Fedora core is terrible for installing new packages, even with knowing all its tips and tricks I find Fedora a real pain to work with when concerning getting new apps.
3: the community, Ubuntu's community is one of the best, now fedora's community is alright too but to me some of them seem stuck up and unwilling to help a newb in need.
4: commitmant, Ubuntu's commitmant to be adaptive and flexible while retaining a gate for open source fans. I feel fedora has commitmant too, but it seems like they dont have as good of a drive that ubuntu has
5: focus, Ubuntu has a great focus to become a very good distro that the average joe can use, now fedore has focus too but I feel its develpment on the desktop leaves a lot to be desired.

---

### Post by Henry Rayker on 2007-03-27
> **SunnyRabbiera said:**
> I feel that ubuntu surpases fedora in many ways:
1: Ubuntu is non intrusive to me, you can use its live CD without even installing anything on your hard drive. Fedora Core has no real live CD installer, it doesnt allow you take a look at the system before you install it, now sure yes a live CD is under works but i feel its lacking compared to ubuntu's

They have a live CD with installer now (in F7 test, at least)

> 2: Ubuntu's package management is wonderful, it has great programs like synaptic and a vast assortment of programs in its repo's. Fedora core is terrible for installing new packages, even with knowing all its tips and tricks I find Fedora a real pain to work with when concerning getting new apps.

In terms of command line tools, (which is all I can speak for) I find Yum to be much faster and concise than apt-get. The GUI may or may not be very good...I find synaptic to be too slow and never messed with pup.

> 3: the community, Ubuntu's community is one of the best, now fedora's community is alright too but to me some of them seem stuck up and unwilling to help a newb in need.

Fedora's community isn't nearly the same size as Ubuntu's. This causes some issues, I feel. Fedora's main problem is lack of focus. There are so many old documents still floating around for FC2...I do really like the Ubuntu community, though...very responsive.

> 4: commitmant, Ubuntu's commitmant to be adaptive and flexible while retaining a gate for open source fans. I feel fedora has commitmant too, but it seems like they dont have as good of a drive that ubuntu has

I'm not sure what you mean here...so I'll just leave it alone.

> 5: focus, Ubuntu has a great focus to become a very good distro that the average joe can use, now fedore has focus too but I feel its develpment on the desktop leaves a lot to be desired.

Well, Fedora is more of a testbed for their RedHat enterprise version, so their focus is on a different idea. However, their network tools are MUCH nicer than Ubuntus...it automatically found my networked printer and configured my network card. For one reason or another, while the Ubuntu Network-Manager applet just wouldn't work with my wireless card, the same version number in Fedora works without a problem. Also, overall speed in Fedora is notably faster (at least on my machine). Running XFCE DE in Ubuntu is slower than GNOME in Fedora.

One GREAT thing about Fedora is that its laptop support (especially wide screen) is leagues ahead of Ubuntu. Wireless is great, my wide screen was configured automatically. The only place where Fedora loses to Ubuntu is that, with Ubuntu, my suspend to RAM actually worked.

---

### Post by SunnyRabbiera on 2007-03-27
> **Henry Rayker said:**
> They have a live CD with installer now (in F7 test, at least)
Thats good, as I perfer live CD's to traditional installer CD's nowadays, now mind you yes a classic installer CD would be better for older machines but I like live CD's as they allow you to tour before you install.

> In terms of command line tools, (which is all I can speak for) I find Yum to be much faster and concise than apt-get. The GUI may or may not be very good...I find synaptic to be too slow and never messed with pup.
I really dont like yum, especially it and dependancy hell. I feel apt is better in my opinion, apt is very clean compared to yum in my expereince as it does help resolve dependancies better.
apt for fedora is looking promising, but I think the debian native systems are better.
As for gui, well not everyone can do command line, thats why I personally favor synaptic.
pup is fair but I feel synaptic is more versitile, sure it is a slow runner but I think its great for the beginner who doesnt know that much about command line apps.
also i feel that getting new upstream apps is easier in ubuntu, fedora is great for pro users but it is not for the beginner.

> Fedora's community isn't nearly the same size as Ubuntu's. This causes some issues, I feel. Fedora's main problem is lack of focus. There are so many old documents still floating around for FC2...I do really like the Ubuntu community, though...very responsive.
Uh huh, but those in the fedora community are rather rude to me.
Ubuntu's community is very vast and good in my opinion while fedora is small and arrogant.

> I'm not sure what you mean here...so I'll just leave it alone.
I dunno about fedora sometime to be honest with you, they dont seem to have a well planned released cycle like ubuntu. I feel its organization that stands out the most for ubuntu, while fedora core seems mixed up in its goals ubuntu is very streightforward

> Well, Fedora is more of a testbed for their RedHat enterprise version, so their focus is on a different idea. However, their network tools are MUCH nicer than Ubuntus...it automatically found my networked printer and configured my network card. For one reason or another, while the Ubuntu Network-Manager applet just wouldn't work with my wireless card, the same version number in Fedora works without a problem. Also, overall speed in Fedora is notably faster (at least on my machine). Running XFCE DE in Ubuntu is slower than GNOME in Fedora.
One GREAT thing about Fedora is that its laptop support (especially wide screen) is leagues ahead of Ubuntu. Wireless is great, my wide screen was configured automatically. The only place where Fedora loses to Ubuntu is that, with Ubuntu, my suspend to RAM actually worked.

well it is bound to happen that another distro works different and sometimes better in some feild or another.
Take Mepis for example, I find it better then ubuntu when concerning hardware as its modded kernel allows it to read stuff ubuntu cant, but ubuntu is getting better in its hardware detection, warty was terrible for me as it didnt detect squat, but dapper and edgy are at the top of the game and I feel things are only going to go up for ubuntu.
as for speed, yes an issue with ubuntu, as it seems something holds it down somewhere, but I think its ease of use makes up for it.

Its ease of use that makes me lean toward ubuntu, fedora has never been something that the average joe could use thus why it gave linux a reputation for not being easy to operate and upgrade.
But ubuntu and its varients are proving that linux can be good for the average joe, Ubuntu's ease of use runs circles around anything fedora can offer in my mind as I do value ease of use a lot.
After all not everyone knows command line, and you know the average windows user wont have a clue what it is, they are very used to a point and click atmosphere and to show them command line scares them.
This is why ubuntu's good, it is very point and click in nature, getting new apps is a snap of the fingers.
Fedora to me is more of a server distro for linux folks with more advanced skills, but ubuntu and its varients are more tuned to the average windows user.

---

### Post by Dragonbite on 2007-03-27
It looks lke the biggest differences are :
[LIST=1]
[*]_Package Manager (APT-GET vs YUM). _
The RPMs of Fedora may be more commonly available to download from individual projects' web sites than DEBs, which focus more on repositories. So if you want the latest-and-greatest, then Fedora may (or may not, you have to look into each individual program) be better but only by a little.
[*]_Community_
The two distro's seem to attract a different crowd. 
**Ubuntu **is more user-friendly and consumer level users but also attracts a number of power users and developers.  People are more supportive of some of the more basic questions and a greater emphasis is placed on making the Wiki's and documentation available and up-to-date.
**Fedora**, it seems, attracts developers and power-users but not so much the consumer-level. There is nothing wrong with this except it makes for a steeper learning curve and for putting chips on some (but not all) of the forum-goers' shoulders.
[/LIST]
Otherwise, each distro can point to something that makes them 'better" or "different" from the others. I think of it as they leave you at a landing spot (a running OS) and depending on what you want to do that distro may be closer to your goal, or not.

---

### Post by celsofaf on 2007-03-27
The main difference is that Fedora is **crap**.

---

### Post by Quillz on 2007-03-27
> **Supergoo said:**
> Hi Guys , 
    Got a few questions here I been playing with a few different Distros Ubuntu 6.10, Opensuse,and Fedora Core 6. I do not care for OpenSuse and trying to understand the each version of Linux, can somebody more knowledgeable help me with the diffences in Fedora Core and Ubuntu ? 
Thanks
Fedora Core uses RPM and Ubuntu uses DEB in their respective package managers. They will ultimately do the same things, just differently. You'll probably want to try both out extensively and see what works better for you.

---

