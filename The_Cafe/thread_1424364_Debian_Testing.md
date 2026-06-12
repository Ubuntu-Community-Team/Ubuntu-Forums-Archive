---
title: "Debian Testing"
date: 2010-03-07
forum: The Cafe
---

### Post by linux4life88 on 2010-03-07
I was looking at giving Debian testing a try simple because of the fact it is a rolling release, and it is Debian therefore uses Debian package management which is my favorite. My question is, from what I understand Debian Testing will become the next release which is 6. Therefore will testing ever go into a freeze state? Will it ever be transitioned into 6, or when 6 comes out will it automatically stay testing and be testing for release 7? I'm just not sure how testing works, except that it is a rolling release with newer packages yet still has security updates and still pretty stable.

---

### Post by blueshiftoverwatch on 2010-03-07
Good questions, I too am consitering a switch to Debian. I'm just not sure whether I want to use Stable or Testing.

---

### Post by linux4life88 on 2010-03-07
> **blueshiftoverwatch said:**
> Good questions, I too am consitering a switch to Debian. I'm just not sure whether I want to use Stable or Testing.

I have heard that Ubuntu is usually based on either testing or unstable. If I understand correctly Karmic was based on unstable and Lucid will be based on testing. I thought this is what I read. I was just wanting a little more of updated software than stable provides. Also, if the above is true then testing should be just as stable if not more stable than Ubuntu. Hopefully someone can either back this up or correct it if I'm mistaken.

---

### Post by kerry_s on 2010-03-07
to keep it a rolling release you need to change "squeeze" to "testing" in the sources.list & you will never move out of testing even when it moves to stable.

the last time i tried the installer was boned when it got to grub, let me know how it go's.

[http://cdimage.debian.org/cdimage/squeeze_di_alpha1/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/squeeze_di_alpha1/i386/iso-cd/debian-testing-i386-businesscard.iso)

---

### Post by kerry_s on 2010-03-07
> **linux4life88 said:**
> I have heard that Ubuntu is usually based on either testing or unstable. If I understand correctly Karmic was based on unstable and Lucid will be based on testing. I thought this is what I read. I was just wanting a little more of updated software than stable provides. Also, if the above is true then testing should be just as stable if not more stable than Ubuntu. Hopefully someone can either back this up or correct it if I'm mistaken.

ubuntu is always based on unstable sid, that's why the stuff is the newest at release. it does not matter what ubuntu version, they all start from unstable.

---

### Post by Uncle Spellbinder on 2010-03-07
From [http://www.ubuntu.com/testing/lucid/alpha3](http://www.ubuntu.com/testing/lucid/alpha3)


As with every new release, packages--applications and software of all kinds--are being updated at a rapid pace. Many of these packages come from an *automatic sync from Debian's Testing branch*.

---

### Post by Post Monkeh on 2010-03-07
> **linux4life88 said:**
> I have heard that Ubuntu is usually based on either testing or unstable. If I understand correctly Karmic was based on unstable and Lucid will be based on testing. I thought this is what I read. I was just wanting a little more of updated software than stable provides. Also, if the above is true then testing should be just as stable if not more stable than Ubuntu. Hopefully someone can either back this up or correct it if I'm mistaken.

i think the way it works with ubuntu is that when one release is made, debian unstable (or testing in this case) is "frozen" and made as steady as possible for the next 6 months, then released, then a new snapshot of debian unstable is taken.

so lucid is actually debian testing from 6 months ago, worked on to make it stable.

---

### Post by tjwoosta on 2010-03-07
> **linux4life88 said:**
>  Also, if the above is true then testing should be just as stable if not more stable than Ubuntu. 

Not nescessarily. While ubuntu is based off debian unstable, its not the same thing. That said, in my experience debian testing is just as stable as ubuntu. Then again ubuntu has never exactly been stable for me.

---

### Post by NightwishFan on 2010-03-08
I just switched to Debian a few days ago and I am loving it. I am not against Ubuntu though, it was what got me started.

I use Unstable on my laptop and I have found it to be rock solid. Any issues are solved in no time. Testing might be better, and I may reinstall to that. It can be a rolling release like Unstable as was said above.

Note that "Unstable" means for the most part changes a lot, and not buggy. It may be broken now and then, but just do not update a package if you are unsure. I have found performance in general to be around equal in throughput to Ubuntu, but much more responsive and lighter. I am using a full gnome desktop.

Ubuntu can be configured as such with a minimal install of course. I have no issue with that as well. I just like all the options Debian gives me.

---

### Post by trekrem on 2010-03-08
> **kerry_s said:**
> ubuntu is always based on unstable sid, that's why the stuff is the newest at release. it does not matter what ubuntu version, they all start from unstable.

10.04 is based on Debian Testing.

---

### Post by lemuriaX on 2010-03-08
Some good info on the different versions of Debian here:

[http://www.debian.org/doc/manuals/debian-faq/ch-choosing.en.html](http://www.debian.org/doc/manuals/debian-faq/ch-choosing.en.html)

---

### Post by gradinaruvasile on 2010-03-08
I already moved to debian testing. Its about the same thing as Ubuntu, but it takes a bit longer to set up. Most of the applications from Ubuntu are found in the repos (you have to add only 1 repo, the multimedia, not tons of PPAs ).
Also, the Grub 2 loader is optional, i use the old one.

Also, the devs seem to have more common sense than Ubuntu's - they kept Ekiga, Pidgin as default applications (Empathy is installed also), there is Remmina installed (great remote desktop app, the default one cant match it), no PulseAudio integration.

Anyway, a bit of experience is required as it doesnt have helper apps like "Hardware drivers", automatical finding of packages that contain x executable (this was really useful, anyone know how it is called?).

It is lighter and faster than Ubuntu, has no unnecessary stuff (ok, it has less than Ubuntu) - no default Compiz, no default PulseAudio, no graphical boot loader.
PulseAudio can be installed and the sound keeps working after that in all applications. It isnt integrated as in Ubuntu meaning that apps that use ALSA use ALSA without being routed through the PA server. I use it on my laptop with bluetooth handsfree and works.

---

### Post by Nerd King on 2010-03-08
I'm just testing it out on a vm at the moment and I'm actually pretty impressed. Having older grub and gdm is positive, I need to upgrade gnome to 2.28 as 2.22 is horrible, but my internet's slow and I'm doing this off a lenny cd which probably doesn't help much!
Overall, like ubuntu with more CLI-emphasis (which I like) and rolling? Seems like a nice place between ubuntu and arch to me.

---

### Post by gradinaruvasile on 2010-03-08
If you plan to upgrade gdm, upgarde everything. Lenny is stable as advertised if you are using its own app versions. Gdm upgrade brings x server upgrade and so forth. You will have a mishmash system. Anyway if you want to install newer versions of applications you will have to install them from the testing or unstable repos.

Bottom line: if you want newer gdm and everything just install testing (squeeze) - its at least as stable as Ubuntu (its best versions, not 9.10 and the like) and its up to date + has rolling updates...

---

### Post by Nerd King on 2010-03-08
Yeah that's what I was trying to do but I've only got a lenny cd lying around and crappy slow internet (this is Thailand). Btw some people might want to look at Sidux. Debian Sid tamed.

---

### Post by XubuRoxMySox on 2010-03-08
I'm loving my Debian Testing / Xfce mixture. It's *rolling release* because I use the Testing repositories instead of "Squeeze," which will be the new version of Debian Stable soon (currently the latest Stable is called "Lenny"). Set up once and update whenever, but no new installs every 6 months or whatever... always current.

It's a lean, mean, fast, up-to-date Linux, but not as cutting-edge as Debian Unstable. A nice "in between" safe zone.

To my knowledge, Lucid is the first time ever that an Ubuntu release is being built on Debian Testing rather than Debian Unstable. I think it is a wise decision, as Lucid is to be a LTS release.

-Robin

---

### Post by Post Monkeh on 2010-03-08
> **dixiedancer said:**
> 

To my knowledge, Lucid is the first time ever that an Ubuntu release is being built on Debian Testing rather than Debian Unstable. I think it is a wise decision, as Lucid is to be a LTS release.

-Robin

i'd say that was their thinking and i'd agree. the last couple of releases have had some problems. maybe only one or two, but they've been annoying for the people who've suffered them. the devs really need to nail this release, being LTS, and the best way is by going for stability.

---

### Post by snowpine on 2010-03-08
On my one rolling release computer, I personally use Arch instead of Debian Testing, because Debian Testing is the last of the 3 branches to receive security updates (they trickle down from Unstable):

> Please note that security updates for "testing" distribution are not yet managed by the security team. Hence, "testing" does not get security updates in a timely manner. For more information please see the announcement of the Testing Security Team. You are encouraged to switch your sources.list entries from testing to lenny for the time being if you need security support. See also the entry in the Security Team's FAQ for the "testing" distribution.

([source]("http://www.debian.org/releases/testing/"))

In my opinion, Debian Testing is designed for testing the next Stable release (like Ubuntu 10.04 at this point in time), not as an everyday operating system. If security is a concern, you should use Debian Stable or Unstable. ([Sidux]("http://sidux.com/PNphpBB2-viewtopic-t-20148.html") is a great way to get a Debian Unstable system up and running quickly.) For casual home users who do not deal with sensitive information (banking etc.), Testing is probably OK.

Another way of phrasing it is that the whole "flow" of the Debian project is to produce the next Stable release, whereas a distro like Arch is designed as "pure" rolling release.

---

### Post by blueshiftoverwatch on 2010-03-08
> **lemuriaX said:**
> Some good info on the different versions of Debian here:[http://www.debian.org/doc/manuals/debian-faq/ch-choosing.en.html](http://www.debian.org/doc/manuals/debian-faq/ch-choosing.en.html)
According to that page, unstable/sid is preferrible to testing because a bug in unstable will probably be fixed quickly while a bug in testing might be there for up a month or two. But on the other hand, bugs are less likely to make their way into testing in the first place.
> **dixiedancer said:**
> I'm loving my Debian Testing / Xfce mixture. It's *rolling release*
Wouldn't testing and unstable both be rolling releases? Testing is just a slower rolling release because unstable updates even more frequently.

---

### Post by snowpine on 2010-03-08
> **blueshiftoverwatch said:**
> Wouldn't testing and unstable both be rolling releases? Testing is just a slower rolling release because unstable updates even more frequently.

Testing rolls in "waves." It gets frozen for a while in preparation for a Stable release, then after the release date, there are a lot of changes. Currently I believe it is fairly stable (since Squeeze is probably coming out sometime this year).

---

### Post by blueshiftoverwatch on 2010-03-09
> **snowpine said:**
> Testing rolls in "waves." It gets frozen for a while in preparation for a Stable release, then after the release date, there are a lot of changes. Currently I believe it is fairly stable (since Squeeze is probably coming out sometime this year).
I think I'm going to go with a Debian Testing netinstall.

---

