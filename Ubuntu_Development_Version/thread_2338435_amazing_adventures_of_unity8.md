---
title: "amazing adventures of unity8"
date: 2016-09-28
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-09-28
Now on my boxes with ppa installed I have lost libertine-scope and apps-scope and all the apps I installed in containers are in with regular apps so I can run firefox, gedit and nautilus. It is a really amazing journey here :)

Regards..

---

### Post by ventrical on 2016-10-15
:)

 Now that LIbertine + container are working zestily and zippity I can run two session of firefox and load two separate  e-mail accounts concurrently from individual containers without having to switch, log out or whatever else we had to do.!

Looks like there are a lot of goodies in Santa's stockings this year :)

Regards..

---

### Post by bearlake on 2016-10-15
> **ventrical said:**
> :)

 Now that LIbertine + container are working zestily and zippity I can run two session of firefox and load two separate  e-mail accounts concurrently from individual containers without having to switch, log out or whatever else we had to do.!

Looks like there are a lot of goodies in Santa's stockings this year :)

Regards..

Interesting

Thanks

---

### Post by rrnbtter on 2016-10-15
Greetings,
Still using my rolled over (not new install) yakkety with Unity 8 PPA.  Container apps are working. Container GUI working. CLI installed apps working. It is all clunky but working.  For now my snap is down. Haven't had time to mess with that. Right now it is purged. I think I will download the deb off of Launchpad when I get a chance and try a reinstall. Let you know what happens when I get the time.  Anyway we are definitely off on a new adventure.

---

### Post by terry_gardener on 2016-10-15
> **ventrical said:**
> Now on my boxes with ppa installed I have lost libertine-scope and apps-scope and all the apps I installed in containers are in with regular apps so I can run firefox, gedit and nautilus. It is a really amazing journey here :)

Regards..

so to get updates on unity 8 do you need the PPA installed, if so is it the ppa from [https://unity.ubuntu.com/getinvolved/development/unity8/]("https://unity.ubuntu.com/getinvolved/development/unity8/")

---

### Post by cariboo on 2016-10-15
> **terry_gardener said:**
> so to get updates on unity 8 do you need the PPA installed, if so is it the ppa from [https://unity.ubuntu.com/getinvolved/development/unity8/]("https://unity.ubuntu.com/getinvolved/development/unity8/")

I'm not using the PPA, just a fresh install using the ISO dated Oct 12 2016.

---

### Post by ventrical on 2016-10-15
> **terry_gardener said:**
> so to get updates on unity 8 do you need the PPA installed, if so is it the ppa from [https://unity.ubuntu.com/getinvolved/development/unity8/](https://unity.ubuntu.com/getinvolved/development/unity8/)

As cariboo pointed out .. we no longer need the ppa. However, if you have had a unity8 system installed as an early adopter I think there are still updates but it doesn't really fix a system if it is broken. It is better to start with fresh install of yakkety, I have one unity8/ ppa system where I can run 3d games like extreme-tux-racer but on others, I can't.

Regards..

---

### Post by terry_gardener on 2016-10-16
sorry i meant future updates to unity 8.
so how will future updates be released, only in the next development release of ubuntu (17.04), backported to 16.10, or via ppa.

---

### Post by amano on 2016-10-18
I trink that it is still not clear if we are supposed to test Unity8 on Xenial, Yakkety or during the upcoming zesty development run.

---

### Post by cariboo on 2016-10-19
Seeing as this sub-forum will shortly be concerned with testing Zesty, I'd suggest testing Unity 8 on the current development release. You still can and should report bugs, if you are running Yakkety. 

I'll have to discuss with the other admins if we will be supporting Unity 8 on Yakkety, or if we will only support it on Zesty here.

---

### Post by ventrical on 2016-10-19
> **cariboo said:**
> Seeing as this sub-forum will shortly be concerned with testing Zesty, I'd suggest testing Unity 8 on the current development release. You still can and should report bugs, if you are running Yakkety. 

I'll have to discuss with the other admins if we will be supporting Unity 8 on Yakkety, or if we will only support it on Zesty here.

Yes.. please do.  IMO I think that unity8 topics related to yakkety can still offer important insight  to unity8 bugs - so - basically saying that all unity8 related topics could perhaps be considered as development version because it is deemed a technical preview.
And yes .. I can see perhaps where unity8 threads may predominate the echo. It has been marked to become a default desktop in the near future last I heard.



Regards..

---

### Post by PaulW2U on 2016-10-19
> **cariboo said:**
> I'll have to discuss with the other admins if we will be supporting Unity 8 on Yakkety, or if we will only support it on Zesty here.
> **ventrical said:**
> IMO I think that unity8 topics related to yakkety can still offer important insight  to unity8 bugs - so - basically saying that all unity8 related topics could perhaps be considered as development version because it is deemed a technical preview.
Just adding an opinion but I think that the discussion of Unity8 on any **currently** supported release should be allowed here until Unity8 becomes the default Ubuntu desktop.

I'm not sure I'll be adding much to the discussions though. I'm not liking what I'm currently seeing. :(

---

### Post by ventrical on 2016-10-19
> **PaulW2U said:**
> Just adding an opinion but I think that the discussion of Unity8 on any **currently** supported release should be allowed here until Unity8 becomes the default Ubuntu desktop.

I'm not sure I'll be adding much to the discussions though. I'm not liking what I'm currently seeing. :(

@PaulW2u

Thanks Paul. Thats the whole point  I think. 

Personally I more or less adopted the unity7 stack of things and I like the ease of use and a lot of reliability factors of that stack. I have been  using unity-desktop since it's inception and I have  had a riot testing it but it wasn't always an effervescent experience. Some  of the early breakage was just awful. This may be the case with unity8 . There may be some awful breakage ahead but at least we have a reasonable facsimile  of unity8 on yakkety to fall back with. 

Another big disappointment was that there was no snappy_personal.img. The whole project just seemed to drop off the edge of the edge... but I am thinking that the 'snap' core program will allow for a lot of diversity, not only in the cloud  but on the desktop. It is the pathway to convergence and I think there is no turning back for Canonical in this regard. (just my two cents worth from the crystal ball). 

 For me, as a hacker, (white hatted of course), unity8  is just what the doctor ordered. Last cycle a large amount of resource was committed to snapcraft, other projects and etc.. I think that those hatches have been buttoned down and  so there will be more development resource for mir and unity8 this cycle. 

From a testers point of view (and  the fact that I have several form-factors that support virtualization and a large supply of Intel processors of the same bent) the lxc hypervisor working through libertine is just awesome. People like the idea of being in the turtle's shell but lxc is much more than that, so, having this ability to work with mir and xapps concurrently in separately created containers  is quite a feat, especially with the GUI to create reliable containers. Back several years ago many commercial based software end_users were advised to create a user account with no permissions and there would be less chance of having some form of malware infest your system. (MSXP). In some cases it worked for a while but the cat always came back the very next day! :)   It was a concept that was short lived but lxc is the real deal .  The other alternative is to not test libertine containers and never really know the full potential of the engine under the hood. Come hell or highwater  I am in for the long ride into the core of the unity8 maelstrom.

Regards..

---

