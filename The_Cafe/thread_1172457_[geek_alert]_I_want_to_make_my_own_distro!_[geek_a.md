---
title: "[geek alert] I want to make my own distro! [/geek alert]"
date: 2009-05-28
forum: The Cafe
---

### Post by The Toxic Mite on 2009-05-28
Hello guys!

I am taking Linux a lot more seriously than I did earlier. I want to make my own distribution.

I have a virtual machine set up on my laptop, and I am using that to create the operating system.

My intention is that it's supposed to be as light as possible, but I want it to work "out-of-the-box" as well. I know that there are some distros that fulfill my intentions, but I want to create one myself.

-----

I am downloading the Ubuntu 9.04 Alternate CD just now.

Any suggestions are welcome, I would also like some artwork if I manage to make a fully-working distribution.

P.S. I plan to call this LightningOS, so think about that ;D

P.P.S Do bear in mind that it is just an experiment

---

### Post by mcduck on 2009-05-28
You might want to start by trying to get something like Linux From Scratch running. [http://www.linuxfromscratch.org/]("http://www.linuxfromscratch.org/")

If you manage to get a working result you may even have luck at creating a distro. :)

---

### Post by monsterstack on 2009-05-28
You might want to try [Linux From Scratch]("http://www.linuxfromscratch.org/") if you're deadly serious about making your own awesome distro. But be warned, it's an incredibly involved process and really complicated.

But if you want a gentler introduction to distro-hacking then your current approach will probably be best. Get a bare-bones distro and add applications and hack it to your needs. You can create a LiveCD of your custom distro with tools such as [Remastersys]("http://en.wikipedia.org/wiki/Remastersys") [wikipedia.org]. There's a tutorial you can look at [here]("http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys") [howtoforge.com].

Good luck :D

---

### Post by The Toxic Mite on 2009-05-28
If you are wondering why I am downloading the Alternate CD, I want to start by installing from the CLI

Speaking of the CLI...

[question] Would the VM be connected to the internet even if it is on the CLI? [/question]

---

### Post by monsterstack on 2009-05-28
> **The Toxic Mite said:**
> If you are wondering why I am downloading the Alternate CD, I want to start by installing from the CLI

Speaking of the CLI...

[question] Would the VM be connected to the internet even if it is on the CLI? [/question]

So long as dhcp is working correctly, you should be able to connect from the terminal command-line. I don't know how the use of a VM changes that, though.

---

### Post by b@sh_n3rd on 2009-05-28
I tried Gentoo for this same reason...wanted my own cool OS...but it's kinda complicated and I'm kind of an impatient person and want it to *work*...so, I haven't really completed a Gentoo system and I hear it's quite complicated and that Arch Linux is better in comparison?

PS: I recognise you by your avatar...I watched your video on your laptop...it's cool, great demo, but have you ever thought of removing the bottom panel and moving the top panel to the bottom? It looks cooler with the "Dust" theme and a higher resolution. I'm loving it :D look [*here*]("http://www.facebook.com/photo.php?pid=30382037&l=eae946fb0b&id=1421833186") for a screenshot (got the idea from openSUSE's GNOME implementation and KDE (though KDE's bar is too broad..like the winblows' taskbar)

---

### Post by mcduck on 2009-05-28
> **The Toxic Mite said:**
> If you are wondering why I am downloading the Alternate CD, I want to start by installing from the CLI

Speaking of the CLI...

[question] Would the VM be connected to the internet even if it is on the CLI? [/question]

Not wishing to spoil your fun, but Alternate CD isn't even close to being a command-line install. It's pretty much a graphical installer, although using character graphics. Pretty much like the installer for Win2000 and older, if you've ever installed those.

---

### Post by -grubby on 2009-05-28
Why not contribute to an already existing distribution?

---

### Post by binbash on 2009-05-28
> **b@sh_n3rd said:**
> I tried Gentoo for this same reason...wanted my own cool OS...but it's kinda complicated and I'm kind of an impatient person and want it to *work*...so, I haven't really completed a Gentoo system and I hear it's quite complicated and that Arch Linux is better in comparison?

PS: I recognise you by your avatar...I watched your video on your laptop...it's cool, great demo, but have you ever thought of removing the bottom panel and moving the top panel to the bottom? It looks cooler with the "Dust" theme and a higher resolution. I'm loving it :D look [*here*]("http://www.facebook.com/photo.php?pid=30382037&l=eae946fb0b&id=1421833186") for a screenshot (got the idea from openSUSE's GNOME implementation and KDE (though KDE's bar is too broad..like the winblows' taskbar)

If you are an impatient person then arch is not for you also.Gentoo is easier but its installation is complicated.

---

### Post by XubuRoxMySox on 2009-05-28
> **grubby- said:**
> Why not contribute to an already existing distribution?

I got one in mind, too. A bunch of us are working on [the Lubuntu project]("https://wiki.ubuntu.com/Lubuntu") which is aiming at the same goals. Ultra-lightweight Ubuntu. Hopefully to become an officially endorsed-by-Canonical *buntu release.

-Robin

---

### Post by calrogman on 2009-05-28
> **The Toxic Mite said:**
> If you are wondering why I am downloading the Alternate CD, I want to start by installing from the CLI

Speaking of the CLI...

[question] Would the VM be connected to the internet even if it is on the CLI? [/question]

```
dhclient eth0
```

---

### Post by b@sh_n3rd on 2009-05-28
> **binbash said:**
> If you are an impatient person then arch is not for you also.Gentoo is easier but its installation is complicated.

for some reason I *thought* someone might say that Gentoo is easier...well yeah, the installation is tricky but then at the time I tried compiling Gentoo, I didn't have the linux knowledge I have now. Well, not really "impatient", I *tend to get impatient* coz I'm used to doing alot of research in a day...so I seem to get bored at times, like, when I don't seem to be able to get the thing working :D How *is* arch anyway? coz I thought of trying it some time ago, and you seem to make me hesitate...:D It *looks* cool enough...

---

### Post by k2t0f12d on 2009-05-29
> **The Toxic Mite said:**
> Hello guys!

I am taking Linux a lot more seriously than I did earlier. I want to make my own distribution.

I have a virtual machine set up on my laptop, and I am using that to create the operating system.

My intention is that it's supposed to be as light as possible, but I want it to work "out-of-the-box" as well. I know that there are some distros that fulfill my intentions, but I want to create one myself.

-----

I am downloading the Ubuntu 9.04 Alternate CD just now.

Any suggestions are welcome, I would also like some artwork if I manage to make a fully-working distribution.

P.S. I plan to call this LightningOS, so think about that ;D

P.P.S Do bear in mind that it is just an experimentI don't think you know how much work a distribution actually is. You might be able to pick some low hanging fruit by remixing Ubuntu, but in the end that's all it will be. Yet Another Ubuntu Remix.

I roll my own GNU+Linux from source code. Here is the short list of prerequistes you'll need to make your own distro;[list][*]know how to build from source code
[*]know how to chroot to build/install from source code (as well as why you'd want to)
[*]know what the GNU build system is and how it works
[*]know how to read, write, and debug bash shell scripts
[*]ability to confidently edit, move, or resize disk partitions
[*]select and implement a package manager (or write your own)
[*]select and implement a boot script system (or write your own)
[*]understand the order in which basesystem packages need to be built, which packages need to be built more then once, and why
[*]must have created a bootable minimal basesystem *a la* Linux from Scratch/DIY Liunx[/list]

After covering those you *might* be ready to plan a GNU+Linux distribution. However, if you spend too much, or not enough, time walking in the footsteps of others, you are much less likely to create something original or that even works. I recommend looking at the features, nuts and bolts of the major distributions (Debian, Fedora, openSUSE, etc) to understand why they do it the way they do it, then add your improvements. First make it boot then make it beautiful. ;)

---

### Post by gn2 on 2009-05-29
> **mcduck said:**
> Not wishing to spoil your fun, but Alternate CD isn't even close to being a command-line install.

It is if you press F4 and select "Install a command-line system"

---

### Post by The Toxic Mite on 2009-05-29
> **k2t0f12d said:**
> I don't think you know how much work a distribution actually is. You might be able to pick some low hanging fruit by remixing Ubuntu, but in the end that's all it will be. [highlight]Yet Another Ubuntu Remix.[/highlight]

I roll my own GNU+Linux from source code. Here is the short list of prerequistes you'll need to make your own distro;
[LIST]
[*]know how to build from source code
[*]know how to chroot to build/install from source code (as well as why you'd want to)
[*]know what the GNU build system is and how it works
[*]know how to read, write, and debug bash shell scripts
[*]ability to confidently edit, move, or resize disk partitions
[*]select and implement a package manager (or write your own)
[*]select and implement a boot script system (or write your own)
[*]understand the order in which basesystem packages need to be built, which packages need to be built more then once, and why
[*]must have created a bootable minimal basesystem *a la* Linux from Scratch/DIY Liunx
[/LIST]

After covering those you *might* be ready to plan a GNU+Linux distribution. However, if you spend too much, or not enough, time walking in the footsteps of others, you are much less likely to create something original or that even works. I recommend looking at the features, nuts and bolts of the major distributions (Debian, Fedora, openSUSE, etc) to understand why they do it the way they do it, then add your improvements. First make it boot then make it beautiful. ;)

Do you have anything against my distro going to be Ubuntu-based?

---

### Post by Script Warlock on 2009-05-29
modify the existing one?

---

### Post by CJ Master on 2009-05-30
I try not to be on of those annoying users that push Arch at every opertunity, but I think it fits here. When you install arch, you configure everything during the install to get a base, fast system, then install whatever you want without all the crud. Once you do that, you just need to find something like remastersys for it. I think there's one call archiso or something, search for it in shaman.

---

### Post by mcduck on 2009-05-30
> **gn2 said:**
> It is if you press F4 and select "Install a command-line system"
I suppose this is just a question of how you define "command-line install" (I would define it as command-line based installer). :)

---

### Post by gn2 on 2009-05-30
Ah yes, I see what you were getting at now! 

Thank heavens it's not a CLI installer.....

---

### Post by ehazlett on 2009-08-24
Try Reconstructor -- i think it will do what you are asking...  [http://www.reconstructor.org](http://www.reconstructor.org)

---

