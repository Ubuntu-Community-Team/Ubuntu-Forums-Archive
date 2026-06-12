---
title: "Software Stores"
date: 2018-06-28
forum: Ubuntu, Linux and OS Chat
---

### Post by monkeybrain20122 on 2018-06-28
I always think the software centre in Ubuntu is kind of useless whether it is ubuntu software centre or now gnome-software. Slow performance, buggy and lack of features aside, it only has a small subset of software comparing to what you can find in synaptic. I think that may be off putting to new users who don't know about other ways to install software and think that the 'app store" is all there is.

Looking outside of the Debian/Ubuntu/Mint ecology there are other possibilities

The best Linux "app store" IMO is pamac in Arch and Arch based distros. It is easy to use and feature rich, like combining the best of synaptic and the software centre. Of course nothing beats the AUR where you get all kind of cool stuffs.

What is your favourite?

---

### Post by bodhin2 on 2018-06-28
in my new usage of ubuntu and the software store i have found it quite buggy at times.  search items come up blank though they are there and loading seems to be an issue.  many attempts have to be made with closing and opening the store.  i or 2 items i need are not there and in synaptic.  i use synaptic more than the store.  though i am set for what i need at present.  there were some things i did not know that i also need in ubuntu that are in the store that i probably would not have found without the help of some mods here.

---

### Post by ajgreeny on 2018-06-28
As a GUI application for package management I believe synaptic is unbeatable; it shows every package separately, including all the thousands of lib files etc, etc, and other dependency packages that the software store does not show as far as I'm aware, though I never use anything other than command line or synaptic so may be wrong about that.

---

### Post by poorguy on 2018-06-28
I'll skim through the ***software centre ***and search for software and I read the reviews sometimes although when it's time to download and install it's off to ***synaptic package manager ***as I agree with ***ajgreeny*** it does show all needed packages.

---

### Post by lostmoonofsaturn on 2018-07-01
Visibility into individual components and dependencies provided by apt and front-ends like Synaptic is very useful when you know what you are doing. It's obviously easy to go astray if you don't know what you are doing.

A "software center" hides the complexity of dependencies and components. Arguably, ordinary users should not need to do package management. They should be able to install an "application" and remove an "application" with confidence that whatever needs to be done that is not visible to them will be done.

---

### Post by monkeybrain20122 on 2018-07-01
> **lostmoonofsaturn said:**
> Visibility into individual components and dependencies provided by apt and front-ends like Synaptic is very useful when you know what you are doing. It's obviously easy to go astray if you don't know what you are doing.


Just because the individual components are visible it doesn't follow you have to install it. I started as a complete noob (not only Linux, but computers in general)  around Ubuntu 10.04, there was no "software store" and synaptic was the  default, took me no time to learn how to use it and have never "gone astray". In fact except for people messing with their sources.list and break apt in general I have never seen any thread where people have a problem using synaptic. But there are plenty about broken software centre.

> A "software center" hides the complexity of dependencies and components. Arguably, ordinary users should not need to do package management. They should be able to install an "application" and remove an "application" with confidence that whatever needs to be done that is not visible to them will be done.



The idea sounds good, but the implementation is underwhelming.  The software centre only has a small fraction of software available, if you want it to be a complete solution for new users at least try to have a reasonably complete listing (no I am not even talking about lib and -dev pakckages, just end user applications)

Also it is buggy and now tries to push snap packages some of which are not even fully functional (e.g vlc) so what is supposed to be "easy" for new users end up being actually a frustrating experience.

As I said, I really find pamac to be the best gui package manager, it has all the information you can get from synaptic but it is tugged away so the causal user would see something like the software store with nice icons and unlike the gnome/ubuntu software store it lists all software available in the official channels (excluding AUR which you have to search but it is not official and somewhat chaotic) 

Deepin Linux has the prettiest, most polished sofware store and  is much more complete in its listing than gnome's/Ubuntu's. For an app store (not a package manager as such) it absolutely blows away the crappy offering from gnome.  But deepin's upgrade model is a bit problematic (still with Firefox 58 in the deepin test install and some software seems to be very outdated, but those issues have nothing to do with the function of the  gui frontend)

---

### Post by bodhin2 on 2018-07-01
so i i installed vlc and some other stuff via the store should i uninstall?  via the store or use synaptic and then reinstall using synaptic?


or


just let it go until issues appear?

---

### Post by monkeybrain20122 on 2018-07-01
> **bodhin2 said:**
> so i i installed vlc and some other stuff via the store should i uninstall?  via the store or use synaptic and then reinstall using synaptic?


or


just let it go until issues appear?

Well if it is working for you, you can keep it. You can always uninstall and get the .deb from synaptic if you need some missing features. My understanding is that you get more updated version for vlc in snap but some of the functions don't work like accessing external drive and maybe  hardware accelerated decoding (??, not sure) Also I heard that snap packages are slow to startup the first time you use it after boot. I found that they almost double my boot time because the system have to mount all these snap containers at boot (my understanding) as 18.04 installs a few snap packages by default (gnome stuffs) I am always getting the latest and greatest  for some selected apps either with ppa and compiling from source anyway so snap has no appeal to me.

---

### Post by bodhin2 on 2018-07-01
thanks monkeybrain....  i guess i will see what happens.  not that i want ot reinstall.  and i may be dead by 2023 for the new LTS but - maybe i will not use apps in store that i can install via synaptic.   this is a learning experience moving to ubuntu.  but also want a sleek speedy working system for my many needs here on the homestead.

---

### Post by monkeybrain20122 on 2018-07-01
> **bodhin2 said:**
> thanks monkeybrain....  i guess i will see what happens.  not that i want ot reinstall.  and i may be dead by 2023 for the new LTS but - maybe i will not use apps in store that i can install via synaptic.   this is a learning experience moving to ubuntu.  but also want a sleek speedy working system for my many needs here on the homestead.

Well only some applications in the stores are snap and to be fair, there is a huge improvement in 18.04 comparing to 16.04. The listings are much more complete now so if you are not looking for something relatively obscure you probably can find it in the store, but in 16.04 there are only a few entries and even some very basic things are missing so I have no idea how they could tell new users for years to use the software store (not to mention the bugs)

---

### Post by bodhin2 on 2018-07-01
Thanks again.

---

### Post by nik.charles on 2018-08-26
I use Debian distributions more than Ubuntu because of synaptic being dropped.

Not sure if it is different on Debian, but I recently found how to dig deeper into installed packages; check dependencies and installed files and force-install an older version of a package

But i prefer pamac too

---

### Post by pauljw on 2018-08-27
> **nik.charles said:**
> I use Debian distributions more than Ubuntu because of synaptic being dropped.

Not sure if it is different on Debian, but I recently found how to dig deeper into installed packages; check dependencies and installed files and force-install an older version of a package

But i prefer pamac too

synaptic hasn't been dropped, it's just not pre-installed.  I just now installed it in Ubuntu Budgie 18.04.  

'sudo apt install synaptic'

---

### Post by PaulW2U on 2018-08-27
> **pauljw said:**
> synaptic hasn't been dropped, it's just not pre-installed.
Technically synaptic has been dropped as it is no longer supported by Canonical and is now supported by the "community". That's why it's in the universe repository and not the main repository. It could never have survived as Ubuntu's "software centre" as it doesn't support the installation of snaps which Ubuntu Software does.

---

### Post by pauljw on 2018-08-27
> **PaulW2U said:**
> Technically synaptic has been dropped as it is no longer supported by Canonical and is now supported by the "community". That's why it's in the universe repository and not the main repository. It could never have survived as Ubuntu's "software centre" as it doesn't support the installation of snaps which Ubuntu Software does.

Thanks, wasn't aware of that.

---

### Post by monkeybrain20122 on 2018-08-27
> **PaulW2U said:**
> Technically synaptic has been dropped as it is no longer supported by Canonical and is now supported by the "community". That's why it's in the universe repository and not the main repository. It could never have survived as Ubuntu's "software centre" as it doesn't support the installation of snaps which Ubuntu Software does.

Not sure why it needs to be supported by Canonical anyway, many non Ubuntu distros also use it, synaptic has never been a Ubuntu developed app as far as I know. Synaptic is always the first thing I install when I install Ubuntu, I don't really care for snap or the paid apps in  Ubuntu Software. To say that it is "dropped" gives the wrong impression that  it is no longer available for Ubuntu, normal users don't really care whether it is in universe or main, they are all parts of the default software pool.

---

### Post by PaulW2U on 2018-08-27
> **monkeybrain20122 said:**
> Not sure why it needs to be supported by Canonical anyway,
I'm just repeating what I've been told by a Canonical employee regarding a bug that I reported recently. I quote:
> Marking as low considering that synaptic is not officially supported.
I too install synaptic and have done so on every Ubuntu installation that I've used since 2010. I'm not going to argue over wording but to clarify - as far as I am concerned synaptic was **dropped by Canonical** as their **preferred** application for package management in favour of the Software Center and later on by Ubuntu Software also known as GNOME Software.

---

### Post by Geoffrey_Arndt on 2018-08-28
Any thoughts about "App Grid" as a replacement for Gnome Software??

Seems faster and more complete, but I just installed it today so I'll have to give it a couple weeks to see if it's really a better choice.

---

