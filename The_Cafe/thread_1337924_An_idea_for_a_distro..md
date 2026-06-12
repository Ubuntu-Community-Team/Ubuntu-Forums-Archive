---
title: "An idea for a distro."
date: 2009-11-25
forum: The Cafe
---

### Post by dragos240 on 2009-11-25
Hello,

I am creating a distro called 'wakarimashita'. It's aims are to provide an easily customizable Linux desktop. It has 2 package managers:

A source package manager (emerge)
And a binary package manager (pacman)

It takes the features of gentoo and archlinux, and rolls them into one. The main thing I'm working on is the install feature. I want to provide an easy to use gui installer. Having the installer walk the user through the basic setup, and allowing them to select what they want to install. I already have a simplistic dd image. It's not complete and has many bugs, I am going to push to get an alpha version released by christmas :)

I still need some ideas to incorporate.

Thanks!
Dragoz

---

### Post by the yawner on 2009-11-25
So... An operating system for those that don't understand?

---

### Post by Psumi on 2009-11-25
> **the yawner said:**
> So... An operating system for those that don't understand?

An OS for those who do not want to go through the hassle of installing Arch/Gentoo manually.

---

### Post by &#32 Greg on 2009-11-25
You do realize Arch has ABS/pacbuilder for installing from source, right?

---

### Post by chris200x9 on 2009-11-25
> **dragos240 said:**
> Hello,

I am creating a distro called 'wakarimashita'. It's aims are to provide an easily customizable Linux desktop. It has 2 package managers:

A source package manager (emerge)
And a binary package manager (pacman)

It takes the features of gentoo and archlinux, and rolls them into one. The main thing I'm working on is the install feature. I want to provide an easy to use gui installer. Having the installer walk the user through the basic setup, and allowing them to select what they want to install. I already have a simplistic dd image. It's not complete and has many bugs, I am going to push to get an alpha version released by christmas :)

I still need some ideas to incorporate.

Thanks!
Dragoz

sounds cool let me know if you need any testers/workers (I have hardly no time so I dunno about working) I have an idea though xfdesktop + compiz-fusion + tint2. I had it on my archbox for a while it had the full effects of compiz but more lightweight than a DE + compiz and it had a *box style menu which was a plus for me. :)

---

### Post by dragos240 on 2009-11-25
> **&#32 Greg said:**
> You do realize Arch has ABS/pacbuilder for installing from source, right?

Yeah, the AUR. I used to use yaourt. Yes I know.

---

### Post by &#32 Greg on 2009-11-25
> **dragos240 said:**
> Yeah, the AUR. I used to use yaourt. Yes I know.

Well, that's a little different (unless you're changing AUR pkgbuilds to include CFLAGS), but yeah...

And of course Sabayon has its package manager to be used with emerge. Just wanted to make sure that you knew that there were package management tools that do what you want done already.

---

### Post by the yawner on 2009-11-25
> **Psumi said:**
> An OS for those who do not want to go through the hassle of installing Arch/Gentoo manually.
I was just playing on the distro name. :p

---

### Post by Psumi on 2009-11-26
> **the yawner said:**
> I was just playing on the distro name. :p

It is japanese:

wakari = understanding; comprehension

mashita = right under; directly below

---

### Post by Xbehave on 2009-11-26
emerge supports ebuilds (binary distribution) and sabyon is gentoo based on ebuilds that with a gui installer so what sets your Yet-another-distro apart from sabyon?

---

### Post by Psumi on 2009-11-26
> **Xbehave said:**
> emerge supports ebuilds (binary distribution) and sabyon is gentoo based on ebuilds that with a gui installer so what sets your Yet-another-distro apart from sabyon?

That it can fit on a CD?

---

### Post by ~sHyLoCk~ on 2009-11-26
Why not name it "Gomenasai"? :P Jk..
I'd say pure ncurses installer with proper explanatory notes like slackware. ;)
As for GUI, openSUSE does it best.

---

### Post by crimesaucer on 2009-11-26
> **  Greg said:**
> Well, that's a little different (unless you're changing AUR pkgbuilds to include CFLAGS), but yeah...


All you have to do is set your C[XX]FLAGS, LDFLAGS, and MAKEFLAGS globally in the /etc/makepkg.conf file, then it will build every package from both the ABS and the AUR using your flags. That is unless the PKGBUILD specifically uses code to unset them (and that means it's best to build without the flags unless you know you can use your own flags like with Firefox).



Then you can even change that part in the PKGBUILD (like with firefox) using export. Just change this part:

```

unset CFLAGS
unset CXXFLAGS

```

to this (these are my settings for Firefox-pgo-oss):

```

export CFLAGS="-march=athlon64-sse3 -O2 -pipe"
export CXXFLAGS="-march=athlon64-sse3 -O2 -pipe"
# The hash-style and as-needed flags are in Arch defaults anyways, and the others are safe.
export LDFLAGS="-Wl,-rpath,/usr/lib/firefox-$pkgver -Wl,-O1,--sort-common,--hash-style=gnu,--as-needed"

```


I've used pacbuilder-svn for over a year and maintained my Arch64 as almost completely source built and optimized. Occasionally I'll install a binary using pacman but that's the benefits of having a whole repo of binaries available if something doesn't build correctly.


As for yaourt I haven't installed it yet but I'll probably be switching to it pretty soon since pacbuilder hasn't had an update in ages. (and I already had to edit it a few times to keep it working properly with other upgrades).


The main advantage that Gentoo and Sabayon have with emerge/portage is that they have Use Flags that are supposed to really help things out.

---

### Post by KiwiNZ on 2009-11-26
> **dragos240 said:**
> Hello,

I am creating a distro called 'wakarimashita'. It's aims are to provide an easily customizable Linux desktop. It has 2 package managers:

A source package manager (emerge)
And a binary package manager (pacman)

It takes the features of gentoo and archlinux, and rolls them into one. The main thing I'm working on is the install feature. I want to provide an easy to use gui installer. Having the installer walk the user through the basic setup, and allowing them to select what they want to install. I already have a simplistic dd image. It's not complete and has many bugs, I am going to push to get an alpha version released by christmas :)

I still need some ideas to incorporate.

Thanks!
Dragoz

If you are serious about this you will not be past the initial project outine planing by Christmas. It  is only four weeks away.There is no way  you should even begin to think about having an Alpha edition out in that time frame.

You owe it to your potential users to plan well and implement well.It is their computers your project will be put on.

---

### Post by -grubby on 2009-11-26
> **dragos240 said:**
> wakarimashita

You should think up a new name.

---

### Post by Psumi on 2009-11-26
> **-grubby said:**
> You should think up a new name.

Why do you say that?

---

### Post by Grenage on 2009-11-26
Just name it Otaku and get it over with. ;)

---

### Post by RiceMonster on 2009-11-26
> **Grenage said:**
> Just name it Otaku and get it over with. ;)

lol

As for having 2 package managers, how are you going to have them play well together? pacman won't know what emerge has installed and vice versa. Plus, for the repos you'll have to maintain and package for both emerge and pacman. Sounds like a royal pain.

---

### Post by dragos240 on 2009-11-26
> **KiwiNZ said:**
> If you are serious about this you will not be past the initial project outine planing by Christmas. It  is only four weeks away.There is no way  you should even begin to think about having an Alpha edition out in that time frame.

You owe it to your potential users to plan well and implement well.It is their computers your project will be put on.

The menu plan will be implemented later. I will get a simple CLI installer setup in the meantime. If I can't do that (I probably can), then I'll provide a DD image.

---

### Post by dragos240 on 2009-11-26
> **RiceMonster said:**
> lol

As for having 2 package managers, how are you going to have them play well together? pacman won't know what emerge has installed and vice versa. Plus, for the repos you'll have to maintain and package for both emerge and pacman. Sounds like a royal pain.

I am working that out right now, but I think I'll get it. The pacman query command should export a list of packages installed to the database generated by emerge --sync, also, I will need to get that database exported to the pacman database. I should be able to do it.

---

### Post by ~sHyLoCk~ on 2009-11-26
Just use a single package manager/format. Do it like Arch does. Provide choices to either compile from source or install a binary version. I think if you add Arch's ABS feature by default then modify pacman accordingly to provide the user with option to choose his method of package installation, your work load will get reduced. Implementing use flags will be tricky since PKGBUILD doesn't provide that, see [srcpac]("http://aur.archlinux.org/packages.php?ID=29032").

---

### Post by dragos240 on 2009-11-26
> **~sHyLoCk~ said:**
> Just use a single package manager/format. Do it like Arch does. Provide choices to either compile from source or install a binary version. I think if you add Arch's ABS feature by default then modify pacman accordingly to provide the user with option to choose his method of package installation, your work load will get reduced. Implementing use flags will be tricky since PKGBUILD doesn't provide that, see [srcpac]("http://aur.archlinux.org/packages.php?ID=29032").

I intend to keep gentoo features separate from pacman and PKG packages. ALL compiling will be done with portage. All binary installations will be done with pacman.

---

### Post by RiceMonster on 2009-11-26
> **dragos240 said:**
> I am working that out right now, but I think I'll get it. The pacman query command should export a list of packages installed to the database generated by emerge --sync, also, I will need to get that database exported to the pacman database. I should be able to do it.

Sounds scary.

---

### Post by JBAlaska on 2009-11-26
Arch/Gentoo hybrid..Called 'wakarimashita' Priceless!

---

### Post by ~sHyLoCk~ on 2009-11-26
> **dragos240 said:**
> I intend to keep gentoo features separate from pacman and PKG packages. ALL compiling will be done with portage. All binary installations will be done with pacman.

Well good luck.

Ganbare. :popcorn:

---

### Post by kk0sse54 on 2009-11-26
> **dragos240 said:**
> I intend to keep gentoo features separate from pacman and PKG packages. ALL compiling will be done with portage. All binary installations will be done with pacman.

What's the point of this? Both Gentoo and Arch have distros (or distrolets) that aim to provide an easier method for installation. Furthermore Sabayon already has a binary/source based hybrid for package management using Entropy for binary packages and portage for compiling. As for Arch, there's Chakra which  being a distrolet you can easily install ABS on it and ABS is *not* the same as the aur.

---

### Post by schauerlich on 2009-11-26
> **C!oud said:**
> What's the point of this? Both Gentoo and Arch have distros (or distrolets) that aim to provide an easier method for installation. Furthermore Sabayon already has a binary/source based hybrid for package management using Entropy for binary packages and portage for compiling. As for Arch, there's Chakra which  being a distrolet you can easily install ABS on it and ABS is *not* the same as the aur.

Now now, don't ruin the illusion with "reality"...

---

### Post by KiwiNZ on 2009-11-26
> **dragos240 said:**
> The menu plan will be implemented later. I will get a simple CLI installer setup in the meantime. If I can't do that (I probably can), then I'll provide a DD image.

You completely missed my point.

---

### Post by renkinjutsu on 2009-11-26
> **-grubby said:**
> You should think up a new name.

I suggest:
nanikore?

---

### Post by Skripka on 2009-11-26
> **KiwiNZ said:**
> You completely missed my point.

Dragos240 went off to Argentina...while the point stayed in South Carolina...

---

### Post by dragos240 on 2009-11-26
> **renkinjutsu said:**
> I suggest:
nanikore?

"What's that?" Why would I name it that?

---

### Post by dragos240 on 2009-11-26
> **KiwiNZ said:**
> You completely missed my point.

I think I got your point. That I couldn't do this in four weeks. I had announced this yesterday, while the actual project has been going on for about 2 months now. I wanted to have a brainstorm topic. The main barebones of the distro WILL be available the day after Christmas.

---

### Post by renkinjutsu on 2009-11-26
> **dragos240 said:**
> "What's that?" Why would I name it that?

no, "what's that" would be naniare

.. and it invokes curiosity, right? It's how i feel when i'm using Linux distributions... every corner, i'm wondering "What's this?" .. "What does THIS do?" .. etc

---

### Post by Kdar on 2009-11-26
> **Psumi said:**
> It is japanese:

wakari = understanding; comprehension

mashita = right under; directly below

Actually "wakarimashita" (I understood, I got it) is just past tense of "wakaru" - to understand

---

### Post by dragos240 on 2009-11-26
> **renkinjutsu said:**
> no, "what's that" would be naniare

.. and it invokes curiosity, right? It's how i feel when i'm using Linux distributions... every corner, i'm wondering "What's this?" .. "What does THIS do?" .. etc

Oh yeah, kore is this. Sorry, still learning. But doesn't are mean that over there? So wouldn't it be nanisore?

---

### Post by Xbehave on 2009-11-26
> **C!oud said:**
> What's the point of this? Both Gentoo and Arch have distros (or distrolets) that aim to provide an easier method for installation. Furthermore Sabayon already has a binary/source based hybrid for package management using Entropy for binary packages and portage for compiling. As for Arch, there's Chakra which  being a distrolet you can easily install ABS on it and ABS is *not* the same as the aur.
+1 Why create yet another distro when Sabayon already seams to offer the features your looking for?

---

### Post by Psumi on 2009-11-26
> **Xbehave said:**
> +1 Why create yet another distro when Sabayon already seams to offer the features your looking for?

Sabayon is a DVD ISO, I would rather have a CD ISO. Though dragos has not said what medium it would be.

---

### Post by RiceMonster on 2009-11-26
> **Psumi said:**
> Sabayon is a DVD ISO, I would rather have a CD ISO. Though dragos has not said what medium it would be.

So, create a whole new distro so you can install from a CD rather than a DVD?

---

### Post by dragos240 on 2009-11-26
> **Xbehave said:**
> +1 Why create yet another distro when Sabayon already seams to offer the features your looking for?

Well. I use Sabayon. it's fine and all, but I don't want things installed by default. I want to pick and choose *exactly* what I want. I don't like how sabayon is set up. It uses equo by default, and installs binary packages. My distro will let you choose what package manager you want. And a few other things. Gotta go. Thanksgiving time!

---

### Post by KiwiNZ on 2009-11-26
I have to ask .... Why?

One of the major issue for Linux uptake is confusion brought about by the number of distributions out there.

Potential users look at the say Distrowatch and say I will use that one .... no that one...hang on that one....Oh stuff it  I will stay with what I know.

CIO's look at it and say hell no , its too fragmented.

We need less distributions , a lot less and we need better quality. Quality over quantity will win through in the end , the current trend of each week of yet another dozen or two here today gone tomorrow Distros will kill Linux.

---

### Post by Pogeymanz on 2009-11-26
Are you building a LFS distro, or are you starting with Arch or Gentoo?

I agree that you should probably just choose a package manager and stick with it, especially because the rest of the stuff will be hard enough.


Good luck. I would be glad to test in Virtualbox.

I've always wanted to make a distro that would boot off of a USB stick and only have Emacs and Firefox on it. No DE or anything. Just switch TTY's between fullscreen Emacs and Fullscreen Firefox. (Since Emacs has a built-in filemanager, terminal emulator, games, and can even use a text-browser, like w3m, inside it.)

---

### Post by MasterNetra on 2009-11-26
> **KiwiNZ said:**
> I have to ask .... Why?

One of the major issue for Linux uptake is confusion brought about by the number of distributions out there.

Potential users look at the say Distrowatch and say I will use that one .... no that one...hang on that one....Oh stuff it  I will stay with what I know.

CIO's look at it and say hell no , its too fragmented.

We need less distributions , a lot less and we need better quality. Quality over quantity will win through in the end , the current trend of each week of yet another dozen or two here today gone tomorrow Distros will kill Linux.

Prehaps, but its the more popular/major distros such as Ubuntu, Fedora/Redhat, and Open Suse that generally get the attention anyway. So whats one more distro that will most likely remain in the shadows? Besides diversity, competition and cooperation tends to breed innovation and ingenuity. I assure you Linux's diversity will not kill it. I mean its been this way for what about 15 or so years and it still is going and is getting more popular.

---

### Post by chris200x9 on 2009-11-26
> **KiwiNZ said:**
> I have to ask .... Why?

One of the major issue for Linux uptake is confusion brought about by the number of distributions out there.

Potential users look at the say Distrowatch and say I will use that one .... no that one...hang on that one....Oh stuff it  I will stay with what I know.

CIO's look at it and say hell no , its too fragmented.

We need less distributions , a lot less and we need better quality. Quality over quantity will win through in the end , the current trend of each week of yet another dozen or two here today gone tomorrow Distros will kill Linux.

Potential users don't look at distrowatch, they get an *buntu cd from a friend...if anyone here seriously got into linux by looking at distrowatch I'll eat my head.

Fragmentation will not scare off companies as you allude to; why? Any company seriously considering the switch to linux has enough knowledge not to say "omg 500 distros which one????"

your argument is bogus let drago do what he wants

---

### Post by KiwiNZ on 2009-11-26
> **chris200x9 said:**
> 

Fragmentation will not scare off companies as you allude to; why? Any company seriously considering the switch to linux has enough knowledge not to say "omg 500 distros which one????"



I talk to CIO's weekly trust me I know

---

### Post by chris200x9 on 2009-11-26
> **KiwiNZ said:**
> I talk to CIO's weekly trust me I know

ok, seems I over estemated people. lol

---

### Post by Xbehave on 2009-11-26
> **dragos240 said:**
> Well. I use Sabayon. it's fine and all, but I don't want things installed by default. I want to pick and choose *exactly* what I want. I don't like how sabayon is set up. It uses equo by default, and installs binary packages. My distro will let you choose what package manager you want. And a few other things. Gotta go. Thanksgiving time!
What advantage is your distro going to have over a different installer CD for sabyon? I mean your sacrificing having a lot of packages provided for you (unless you pull of compatibility with both arch and gentoo).

---

### Post by thegreenblob on 2009-11-26
> **chris200x9 said:**
> Potential users don't look at distrowatch, they get an *buntu cd from a friend...if anyone here seriously got into linux by looking at distrowatch I'll eat my head.

Start eating... :-\"

---

### Post by chris200x9 on 2009-11-26
> **thegreenblob said:**
> Start eating... :-\"

are you honestly saying you had no clue about linux or that every distro is the *same* before you started looking at distrowatch?

---

### Post by thegreenblob on 2009-11-26
> **chris200x9 said:**
> are you honestly saying you had no clue about linux or that every distro is the *same* before you started looking at distrowatch?

I heard about plain "linux" as an alternative os, I had no idea what a distro was, so I googled "download linux" or something along those lines, and eventually found distro watch, and when I did I downloaded a ton of distros and burned them to cds and tried them out, mostly live cds, opensuse was the first one I installed.

---

### Post by Ylon on 2009-11-26
TinyWM with Compiz, Cairo and other eyecandy stuff.


Even in VESA! :KS

---

### Post by chousho on 2009-11-26
> **Psumi said:**
> It is japanese:

wakari = understanding; comprehension

mashita = right under; directly below

wakaru = u-verb, so you move it to the infinitive form "wakari" and add "masu" to place it in the polite form. Since it's past-polite form, you will use the past tense of masu, mashita.

So it only means "understood" in a polite way, basically. I would prefer it be named &#12431;&#12363;&#12425;&#12408;&#12435;, but I'm biased.

---

### Post by ~sHyLoCk~ on 2009-11-26
> **Psumi said:**
> Sabayon is a DVD ISO, I would rather have a CD ISO. Though dragos has not said what medium it would be.

Sabayon also has a minimal install CD.

@chousho

I love your dp. Chiyo-chan <3 I think I'm gonna rewatch Azumanga :D

---

### Post by Psumi on 2009-11-26
> **~sHyLoCk~ said:**
> Sabayon also has a minimal install CD.

Isn't it only for version 3.4 though?

---

### Post by ~sHyLoCk~ on 2009-11-26
> **Psumi said:**
> Isn't it only for version 3.4 though?

Nope. I haven't used sabayon since 4.1. Went to their irc and confirmed. Sabayon 5.1 core CD is currently in beta. Actually their mirrors are not that updated. I couldn't even find sabayon 5 in some of the listed mirrors. :\

---

### Post by crimesaucer on 2009-11-26
> **Psumi said:**
> Isn't it only for version 3.4 though?

There was version 4.2: [http://wiki.sabayonlinux.org/index.php?title=Visual_Tour:_CoreCD](http://wiki.sabayonlinux.org/index.php?title=Visual_Tour:_CoreCD)


I thought about installing the 4.2 Core CD and was going to build a minimal install of xfce4 using emerge (I also thought about Slackware64 with slackbuilds, and the new Gentoo install CD). Maybe next year. Or possibly FreeBSD.


I also checked out a 64bit CLFS that looked really interesting: [http://cross-lfs.org/view/svn/x86_64-64/index.html](http://cross-lfs.org/view/svn/x86_64-64/index.html)

---

### Post by chousho on 2009-11-27
> **~sHyLoCk~ said:**
> Sabayon also has a minimal install CD.

@chousho

I love your dp. Chiyo-chan <3 I think I'm gonna rewatch Azumanga :D
Haha, thanks. But it isn't from Azumanga, it's from Yotubato! (Yotsuba&! is the translated title). It's by the same author, but is more slice of life than situational comedy. Both series are great, though :) I'm not sure if you picked up that Osaka is my favorite Azumanga character, which is why I said the distro should be named "&#12431;&#12363;&#12425;&#12408;&#12435;" (the Kansai equivalent of the suggested name, only in negative form).

---

### Post by ~sHyLoCk~ on 2009-11-27
Ooops Im sorry i thought it's Chiyo. I also read Yatsubato :D It's funny.

---

### Post by Psumi on 2009-11-27
> **~sHyLoCk~ said:**
> Nope. I haven't used sabayon since 4.1. Went to their irc and confirmed. Sabayon 5.1 core CD is currently in beta. Actually their mirrors are not that updated. I couldn't even find sabayon 5 in some of the listed mirrors. :\

Yeah, I would rather not get a beta of an ISO.

---

