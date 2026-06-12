---
title: "Unity 8 desktop"
date: 2016-01-07
forum: Ubuntu Development Version
---

### Post by krishnan t s on 2016-01-07
I have Ubuntu 16.04 installed on one of my systems.
I have recently downloaded the unity8-desktop-session-Mir package from the repositories and have booted into the unity 8 desktop. However, I'm not able to install any application from the Ubuntu store. I know this is a known issue where I can't install click packages from the store on the desktop. But I am eager to get a basic unity 8 experience namely music video and the document viewer compatible with libre office on the desktop.
Is there any way to install these applications and access them from the unity 8 shell?
Also, unity 8 via lxc did not work in my case. Apparently it's a systemd issue. However the workaround in launchpad does not work in my case. I'm on the phone now and can't attach the launchpad link. Will update once I get it to the desktop. Should I open a new bug report or is it enough if I subscribe to the same?

---

### Post by grahammechanical on 2016-01-07
Do not get me started on Unity 8 session.

I get GPU lock up on Nouveau and never get to a desktop. And on Nvidia I get login screen bounce. That I expect but not the result on Nouveau.

In the past I have installed Ubuntu Desktop Next ISO image & personal_x86.img. Both will load on Mir and to a desktop on this machine. So, I am a little disappointed that the Unity 8 desktop session is broken.

The Unity 8 user interface has little worthwhile functionality for a desktop user. Some apps are written for the Arm architecture and not X86. So, they won't load. There is talk of making it possible to run Click apps on Unity 7. I see click related packages being downloaded in Xenial but I see multiple lines of development as new opportunities are revealed. As far as I am concerned, we can forget about this Unity 8 session for 16.04. It is never going to be more than it already is. Development is already moving in other directions.

For the record. With Personal Mir was working fine and the workplace switcher was excellent. But the app store only pretended to load apps and Browser would freeze the desktop. Even on Unity 7 Browser crashes. 

Regards.

---

### Post by krishnan t s on 2016-01-07
Is there anyway I can install the music app media player app and the document viewer in unity 7 then? The ppa for Ubuntu touch core apps does not work in xenial yet.

---

### Post by ventrical on 2016-01-08
> **krishnan t s said:**
> Is there anyway I can install the music app media player app and the document viewer in unity 7 then? The ppa for Ubuntu touch core apps does not work in xenial yet.

There is a large amount of resources currently focused on  snappy core, canonical-pc and canonical-linux-pc (also for x86 based machines -amd64) and currently even the base apps for (x86) do not work. Updating the previous 15.04 and 15.10 snappy core issuances (x86) will not update. 

There is more of a shift towards stablizing snappy core for BeagleBone Black and RasperryPi form factors. Certainly not an ISO image or release of any sort for a snappy personal pc desktop.

  In good faith I can say that I have been informed that work is  ongoing for a viable working snappy-personal-pc desktop but I cannot answer when that will be. More and more it seems that this project is getting shuffled to 'wish-list' status.

Regards..

---

### Post by krishnan t s on 2016-01-09
So am I to understand that there "could not be" an unofficial snappy personal image for the desktop either during or after 16.04 release in April?
I am waiting for snappy core ubuntu. And boy do i have some amazing news. I updated the lxc container with unity8 just sometime back and now i'm able to boot into the unity8 session from the login screen. The browser app that crashed for me too till date started working almost flawlessly after an update today in both the unity 8 and unity 7 desktop.
If only they made the ppa available for 16.04 soon. That'd be the icing on the cake :)

---

### Post by ventrical on 2016-01-09
> **krishnan t s said:**
> So am I to understand that there "could not be" an unofficial snappy personal image for the desktop either during or after 16.04 release in April?
I am waiting for snappy core ubuntu. And boy do i have some amazing news. I updated the lxc container with unity8 just sometime back and now i'm able to boot into the unity8 session from the login screen. The browser app that crashed for me too till date started working almost flawlessly after an update today in both the unity 8 and unity 7 desktop.
If only they made the ppa available for 16.04 soon. That'd be the icing on the cake :)

A larger part of the resources are going into development of LXD .. the next generation of lxc. I have done some experiments and it is promising - so .. the conventional theory is that we will be able to install .ISOs and desktops using containers in snappy walled garden. In fact, if tweaked correctly (as I have experimented) you can use conventional apt-get repos for  desktops that will be isolated from the possible proposed OTA snappy updates. snappy-core (possible snappy personal also) is being completey refitted for 16.04. 

[http://www.markshuttleworth.com/archives/1479](http://www.markshuttleworth.com/archives/1479)

It is just my broader assumption atm that we might not see a bonifide snappy personal ISO but we will definitely get a working desktop that will fit on LXD.

Regards..

---

### Post by rrnbtter on 2016-01-10
Greetings,
My crystal ball needs an oil change at the moment so I don't know much as to what is going into the final release. However, many of the common applications seem to be taking on tablet like characteristics and much of the infrastructure has been appearing in the downstream for the past year.  I quit testing Next during wily due to excessive resources being invested into too little results. Plus I don't have a touch laptop. What I'm expecting sometime in the future is a seamless experience between phone, tablet, and desktop, much like Android now has between the phone and tablet. If that becomes the case, I'm all for it.  In any case Canonical will release whatever they have stable at the end of the cycle and all will be good a couple of weeks after the final release when all of the software catches up. I've been running the dev version since 2009 and haven't been disappointed yet.

---

### Post by grahammechanical on 2016-01-10
Mark Shuttleworth

> Ubuntu Core is the all-snappy minimal server, and Ubuntu Personal will be the all-snappy phone / tablet / pc.

Snappy Ubuntu core is here now. But from what I have heard, I do not expect Ubuntu Personal to start making an appearance until the 16.10 development cycle. There are next to no traditional desktop apps (X apps) packaged as snap apps. They will have to run on Xmir and in LXC containers both to get them running on Mir & to comply with the security model for Ubuntu personal. I have seen experiments of this working in Unity 8.

I keep in mind that code is re-usable. If the code works, is polished & is beautiful, then it can be used at any time. Code that is not used is not necessarily wasted effort. I hope we are seeing different code experiments that will be fitted together to make a whole. I have heard Canonical employees say that Unity was release before it was ready and that was a mistake. Perhaps they do not want to make the same mistake with Ubuntu Personal.

Regards.

---

### Post by DogMatix on 2016-01-11
> **grahammechanical said:**
> 
... I have heard Canonical employees say that Unity was release before it was ready and that was a mistake. Perhaps they do not want to make the same mistake with Ubuntu Personal.


Flashbacks to 10.10 Netbook remix! and my first experience of Unity DE. I can certainly wait for Ubuntu Personal to mature. I have kind of become to rely on Ubuntu LTS being reliable.

---

### Post by fjgaude on 2016-01-11
Ubuntu Unity has been for me the best thing since sliced bread. For those who have a complex workflow it is a god-send. Please don't let its features go away.

---

### Post by mc4man on 2016-01-12
> **fjgaude said:**
> Ubuntu Unity has been for me the best thing since sliced bread. For those who have a complex workflow it is a god-send. Please don't let its features go away.
That's one really good thing about Canonical's penchant for overestimating, 16.04 will be unity7/compiz with some decent bug fixing preceding release, they'll have to bury them later...

---

### Post by fjgaude on 2016-01-14
> **mc4man said:**
> That's one really good thing about Canonical's penchant for overestimating, 16.04 will be unity7/compiz with some decent bug fixing preceding release, they'll have to bury them later...

Such will keep me going until 2021... that could be enough! <smile>

---

### Post by ventrical on 2016-01-15
> **fjgaude said:**
> Such will keep me going until 2021... that could be enough! <smile>

I still have a frozen install of 10.10. Never needs  updates (or flash). It just keeps on ticking :) I think unity will be around for a while. There will be a backstep to desktops because slates and tablets are , well, pretty well useless, if you want to get any real work done.

Regards..

---

### Post by fjgaude on 2016-01-15
> **ventrical said:**
> I still have a frozen install of 10.10. Never needs  updates (or flash). It just keeps on ticking :) I think unity will be around for a while. There will be a backstep to desktops because slates and tablets are , well, pretty well useless, if you want to get any real work done.

Regards..

Well, being a retired graphic designer and still doing hobby design I sure fine Unity just right for me and the workflow I established because of it. I've always used four workspaces, desktops since long ago, at least 15 years for this kind of work.

---

### Post by nikolay-kuzmin on 2016-04-04
New nvidia 364.* branch contains support for Wayland/Mir. Have someone managed to launch Unity 8 session with it?

---

### Post by grahammechanical on 2016-04-04
> New nvidia 364.* branch contains support for Wayland/Mir. Have someone managed to launch Unity 8 session with it?

My Nvidia adapter is obsolete by Nvidia standards. So, I cannot use the very latest Nvidia drivers. But I have not had unity8-desktop-session-mir working even on Nouveau since I tried with Trusty. I wish people would stop pushing that unity8 session as a viable option.

On the other hand I have had Ubuntu Personal running on this machine. It had Mir, Unity 8, Snappy core but of course all on Nouveau. If Nvidia is not going to backport that Wayland & Mir code to older drivers then a lot of people are going to have to stop using Nvidia if they want to run on a Wayland compositor or on the Mir compositor.

Regards.

---

### Post by rrnbtter on 2016-04-04
Greetings,
There are so many Unity 8/Mir updates in the Xenial downstream that if they had a Unity 8 breath-a-lizer Xenial would be blowing a 5.8. In spite of this I agree, Canonical has it on the "see you later" list for desktop.

---

### Post by rrnbtter on 2016-04-06
Greetings,
I have had no problem with my Unity integrated menu since I used the two fixes in this thread. If the OP is and the rest are ok I suggest it be marked as solved.

---

