---
title: "Are any packages/apps available only via snap?"
date: 2020-06-09
forum: Ubuntu, Linux and OS Chat
---

### Post by kansasnoob on 2020-06-09
Just as the title says, are any packages available via snap only in Ubuntu? If so is there a list of what they are?

I've been asked by a few people to build them a "snap-free" Ubuntu, which seems easy enough, but wondered if some package or app they may want to install later might require snap. I'm actually thinking about building up from scratch using the mini iso (aka; net-install). Or maybe building "down" from a full install but the prior seems more sensible.

---

### Post by &amp;KyT$0P# on 2020-06-09
Does [FONT=Courier New]apt-cache rdepends snapd[/FONT] help?

---

### Post by crip720 on 2020-06-09
For a time Chromium was snap only.  I think they had to make a deb package also because of problems with snap chromium.  Think most other packages were installed as snaps, but had debs also, so you had choice.  In future might need to move to another linux to avoid snaps completely, but most snaps seem to do the basics okay, extra permissions were most trouble comes from.

---

### Post by deadflowr on 2020-06-09
Chromium has always had a deb for it.
It's just now for new releases of Ubuntu (currently for 19.10 and 20.04+) the deb just installs the snap parts instead.
So the deb is basically a transitional packaging utility.
(There was plans to at some point extend the snap version to older releases as the default/only version, but I haven't heard anything about that in some time, like over a year or so)

As far as snap only Ubuntu packages i can only think of two right now.
One is chromium, of course, and the other is lxd.
But there are probably others.

Ubuntu has shipped several packages with the snap version, that also have deb versions.
(In 20.04, Ubuntu Software is now snap-store, which is a snap.
But you can replace it with gnome-software, which is a deb)

They also, for a time (not sure it they still do) shipped a few default install packages with the snap versions,
like gnome-system-monitor, gnome-calculator, gnome-characters and gnome-logs and maybe something else.
All of those, though, could be removed and replaced with the deb versions if you wanted to.

And overall in the snap store there are probably dozens if not hundreds of snaps which have no deb equivalent.
But those are almost all from 3rd party developers, who, mind you, would probably never have packaged their app as a deb in the first place.

---

### Post by Shibblet on 2020-06-09
Caprine.  It's a Facebook messenger program for Linux.

---

### Post by kansasnoob on 2020-06-12
> **deadflowr said:**
> Chromium has always had a deb for it.
.................... They also, for a time (not sure it they still do) shipped a few default install packages with the snap versions,
like gnome-system-monitor, gnome-calculator, gnome-characters and gnome-logs and maybe something else.
All of those, though, could be removed and replaced with the deb versions if you wanted to.


I know the snap version of gnome-calculator was so incredibly slow in 18.04 I installed the .deb from the repos instead. I never followed up to see if it improved with bug fixes. I'm personally kind of agnostic when it comes to snap or flat-pack. If things work then it doesn't much matter to me how the devs got there. If things don't work a quick google search usually tells me that I'm not alone and workarounds abound aplenty. Regardless I still prefer Ubuntu as a base starting point whenever possible.

---

### Post by kansasnoob on 2020-06-17
I've been strongly considering QT based desktop environments - either Lubuntu or Kubuntu in this family - and I found one package that may be more appropriately installed via SNAP = Falkon. It's a continuation of QupZilla but now is loosely based on Chromium. I have not done a great deal of research however. I need to find time to play with both Lubuntu and Kubuntu 20.04.

---

### Post by deadflowr on 2020-06-18
I see that snapcraft is snap only for focal.
Older releases are still deb
(snapcraft is the package of utilities used to build snaps, ftr)

Does the same as lxd and chromium where it ships as deb but is really just a transitional package to install the snap.
So I guess you can add that to the list of snap only packages.

> I found one package that may be more appropriately installed via SNAP = Falkon.
Looks slow to updating the stable channel.
as it is almost a year old.
the edge channel looks more recent.
(currently updated last month)

The stable channel seems to put it in line with the falkon deb in focal's repository.

---

### Post by mc4man on 2020-06-22
> **kansasnoob said:**
> Just as the title says, are any packages available via snap only in Ubuntu? If so is there a list of what they are?

I've been asked by a few people to build them a "snap-free" Ubuntu, which seems easy enough, but wondered if some package or app they may want to install later might require snap. I'm actually thinking about building up from scratch using the mini iso (aka; net-install). Or maybe building "down" from a full install but the prior seems more sensible.

I would suspect there are  at least 100, probably many more snap only apps. 
As far as list, no way. One can't even get a full list of  cuurent available snaps anywhere. ( dumb but true...
If you look here I guarantee many shown  are snap only
[https://snapcraft.io/store](https://snapcraft.io/store)

---

### Post by monkeybrain20122 on 2020-06-23
sandboxing of snap is a pita in addition to loop mounting a bunch of stuffs on bootup. I personally prefer flatpak, like snap it has many software not available in the usual repo, but it is much easier to manage permission  and sandboxing with flatpak. It has a gui tool called flatseal that provides a common interface to manage all your flatpak apps. There is no such over arching tool for snap as far as I know. Also unlike snap flatpak doesn't require mounting a lot of stuffs on boot and so it doesn't increase boot time like snap (though snap is getting much better in terms of boot delay in 20.04 than 18.04)

You don't have to build "snap free" Ubuntu from scratch, it is easy to get rid of all the snap stuffs if you don't want them. e.g [https://www.kevin-custer.com/blog/disabling-snaps-in-ubuntu-20-04/](https://www.kevin-custer.com/blog/disabling-snaps-in-ubuntu-20-04/)

---

### Post by kansasnoob on 2020-06-23
> **monkeybrain20122 said:**
> sandboxing of snap is a pita in addition to loop mounting a bunch of stuffs on bootup. I personally prefer flatpak, like snap it has many software not available in the usual repo, but it is much easier to manage permission  and sandboxing with flatpak. It has a gui tool called flatseal that provides a common interface to manage all your flatpak apps. There is no such over arching tool for snap as far as I know. Also unlike snap flatpak doesn't require mounting a lot of stuffs on boot and so it doesn't increase boot time like snap (though snap is getting much better in terms of boot delay in 20.04 than 18.04)

You don't have to build "snap free" Ubuntu from scratch, it is easy to get rid of all the snap stuffs if you don't want them. e.g [https://www.kevin-custer.com/blog/disabling-snaps-in-ubuntu-20-04/](https://www.kevin-custer.com/blog/disabling-snaps-in-ubuntu-20-04/)

I assume that both Kubuntu and Lubuntu would be the same? I did check the iso package manifests so I know snapd exists in both, in fact all flavors I believe. I'm almost certainly going QT based with 20.04.

---

### Post by monkeybrain20122 on 2020-06-23
> **kansasnoob said:**
> I assume that both Kubuntu and Lubuntu would be the same? I did check the iso package manifests so I know snapd exists in both, in fact all flavors I believe. I'm almost certainly going QT based with 20.04.

Don't know about lubuntu. Kubuntu is the same,  I just removed all the snap stuffs from a kubuntu machine I set up for my friend. Nothing bad happened.

---

### Post by Shibblet on 2020-06-25
> **monkeybrain20122 said:**
> Don't know about lubuntu. Kubuntu is the same,  I just removed all the snap stuffs from a kubuntu machine I set up for my friend. Nothing bad happened.

I have one Snap on my system, Caprine (Facebook Messenger).  I know it's the worst messenger out there, but I use it only because friends and family use it.  Personally, I prefer Telegram.

Anyway, I have heard that Flatpaks are currently working very well, and a bit "tighter" and "faster" than Snaps.

This is really the first run of Ubuntu to really run with Snaps... have we given them enough time to get the bugs worked out yet?

---

### Post by monkeybrain20122 on 2020-06-26
> **Shibblet said:**
> I have one Snap on my system, Caprine (Facebook Messenger).  I know it's the worst messenger out there, but I use it only because friends and family use it.  Personally, I prefer Telegram.


I never heard of caprine before,  there is apparently a .deb for download. [https://github.com/sindresorhus/caprine](https://github.com/sindresorhus/caprine)

---

