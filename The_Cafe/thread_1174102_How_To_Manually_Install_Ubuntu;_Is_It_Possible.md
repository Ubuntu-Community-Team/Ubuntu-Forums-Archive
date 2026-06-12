---
title: "How To Manually Install Ubuntu; Is It Possible?"
date: 2009-05-30
forum: The Cafe
---

### Post by b@sh_n3rd on 2009-05-30
I got this crazy Idea a moment ago. Is it possible (and I'm quite sure it *is*) to build and compile an Ubuntu installation from scratch? If possible, using the LiveCD (I'll be using Jaunty). This is supposedly possible with nUbuntu, I'm doing some research on that though. How would I get about it? I'd have to use the console right? How would I exit to the console from the LiveCD if I have to? (the opposite of "**startx**"?) Thanks :D...

(I'm just trying to get some info on this. Not sure if I'll try it right away as I'm experimenting with nUbuntu)

---

### Post by dragos240 on 2009-05-30
Like gentoo?

---

### Post by CJ Master on 2009-05-30
Nubuntu is used for security, not compiling a whole installation. If you want to do that, use Gentoo.

---

### Post by MikeTheC on 2009-05-30
How about just sticking the Ubuntu Live CD in and clicking on the buttons yourself? Surely that's gotta be *some* kind of "manual"...

Other than that, I'd agree with the above posters. Go with Gentoo.

Me, I'll stick with the stuff that's finished, tested and known to work, thank you very much.

---

### Post by b@sh_n3rd on 2009-05-30
> **CJ Master said:**
> Nubuntu is used for security, not compiling a whole installation. If you want to do that, use Gentoo.

yeah...I know that..and I've compiled Gentoo too (In other words, the CD's on my right :D)...What I'm wanting is to know if a manual installation/compilation is possible on ***Ubuntu***? [*not* Gentoo] (There's a way of manually installing nUbuntu...I think I used the wrong expression on my first post for that. For nUbuntu, I mean manual *installation* not *compilation*). Thanks for your replies though...

---

### Post by b@sh_n3rd on 2009-05-30
> **MikeTheC said:**
> How about just sticking the Ubuntu Live CD in and clicking on the buttons yourself? Surely that's gotta be *some* kind of "manual"...

Other than that, I'd agree with the above posters. Go with Gentoo.

Me, I'll stick with the stuff that's finished, tested and known to work, thank you very much.

hehe, so ma idea's gone to the ground...spitty...It's kinda difficult to learn portage when I'm so used to apt and Ubuntu's similar functions in the console...Just a wild idea about ubuntu anyways...hey, anyone heard of Gobuntu? That's supposed to be manual...but it's an older release...anyways, I think I'll just do some digging on that...so no "manual" installation, let alone compilation for Ubuntu anyhow? :D

---

### Post by kk0sse54 on 2009-05-30
What exactly is your idea of a manual install? And use the command 'exit' to logout of a console session or "shutdown -h now" (man shutdown for more info) to shut off your computer.

---

### Post by schauerlich on 2009-05-30
You can install the [Ubuntu Minimal CD](https://help.ubuntu.com/community/Installation/MinimalCD) and then compile the rest yourself.

---

### Post by HappyFeet on 2009-05-30
> **EDavidBurg said:**
> You can install the [Ubuntu Minimal CD](https://help.ubuntu.com/community/Installation/MinimalCD) and then compile the rest yourself.

I've done that, and it's not compiling the rest, but rather just installing what you want. But yes, it's a great way to get an ubuntu install just the way you want.

---

### Post by Rainstride on 2009-05-30
> **b@sh_n3rd said:**
> yeah...I know that..and I've compiled Gentoo too (In other words, the CD's on my right :D)...What I'm wanting is to know if a manual installation/compilation is possible on ***Ubuntu***? [*not* Gentoo] (There's a way of manually installing nUbuntu...I think I used the wrong expression on my first post for that. For nUbuntu, I mean manual *installation* not *compilation*). Thanks for your replies though...

i don't think a single person in here gets what you are asking. maybe you should start again at the top....(or use google;).)

---

### Post by schauerlich on 2009-05-30
> **HappyFeet said:**
> I've done that, and it's not compiling the rest, but rather just installing what you want. But yes, it's a great way to get an ubuntu install just the way you want.

Well, you could just do the very minimal install, abort the installation, and start wget'ing tar.gz's.

---

### Post by MikeTheC on 2009-05-30
Ubuntu is provided as more of a "solution" than purely an OS. It is not intended to be handled in the way the OP is suggesting.

At a guess, you could probably obtain the entire source code for an Ubuntu install from Canonical, but the question is why? If you're trying to get everything to be more native or optimized for your hardware, all you're going to do is break what Canonical is distributing. It isn't designed to be used like that. Gentoo is.

---

### Post by b@sh_n3rd on 2009-05-30
> **C!oud said:**
> What exactly is your idea of a manual install? And use the command 'exit' to logout of a console session or "shutdown -h now" (man shutdown for more info) to shut off your computer.
Hmm...good question...manual as in...no GUI...but copying, partitioning, etc. all from a console manually? eg: [http://wiki.nubuntu.org/index.php/Installing_nUbuntu_to_a_hard_drive#Manual_install](http://wiki.nubuntu.org/index.php/Installing_nUbuntu_to_a_hard_drive#Manual_install) about the exit thingy, that's not what I meant...what I meant was, the reverse of loading X with the command "startx"?? (i.e: exitx ; This didn't work when I tried it...but it wasn't really ubuntu I tried it on :D)
> **EDavidBurg said:**
> You can install the [Ubuntu Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") and then compile the rest yourself.
cool, I might try that.. (why I mentioned "LiveCD" was specifically to avoid wasting a CD...and they are scarce for me :D...gotta get a new batch)
> **RainStride said:**
> i don't think a single person in here gets what you are asking. maybe you should start again at the top....(or use google:wink:.)
I think so too...:lolflag:
> **MikeTheC said:**
> Ubuntu is provided as more of a "solution" than purely an OS. It is not intended to be handled in the way the OP is suggesting.

At a guess, you could probably obtain the entire source code for an Ubuntu install from Canonical, but the question is why? If you're trying to get everything to be more native or optimized for your hardware, all you're going to do is break what Canonical is distributing. It isn't designed to be used like that. Gentoo is.
You make me feel I'm insulting my favourite linux distribution :( :(

---

### Post by HappyFeet on 2009-05-30
> **EDavidBurg said:**
> Well, you could just do the very minimal install, abort the installation, and start wget'ing tar.gz's.

At that point you may as well use Slackware.

---

### Post by schauerlich on 2009-05-30
> **HappyFeet said:**
> At that point you may as well use Slackware.

True, but he was asking for Ubuntu solutions. What I suggested is probably his [best, only] bet.

---

### Post by b@sh_n3rd on 2009-05-30
hehe, this thread is going like my warmed up moped :D...didn't think the topic was so hot :D...thanks anyways, I think I'll mess around with Gobuntu. I did check on it before, but somehow I didn't feel like getting it, extra disk and all (it's 7.04; Gutsy Gibbon!) but, nvm, anyways, It's what I want too Thanks guys :D

[http://www.ubuntu.com/products/whatisubuntu/gobuntu](http://www.ubuntu.com/products/whatisubuntu/gobuntu)

**EDIT:** According to this article, [http://en.wikipedia.org/wiki/Gobuntu](http://en.wikipedia.org/wiki/Gobuntu) it's nil...No newer versions...

---

### Post by MikeTheC on 2009-05-30
[My brain hurts!](http://www.youtube.com/watch?v=IIlKiRPSNGA)

---

### Post by sisco311 on 2009-05-30
How about Linux from scratch:
[http://www.linuxfromscratch.org/]("http://www.linuxfromscratch.org/")

Or a minimal chroot environment: 
[http://linux.about.com/od/ubupck_doc/a/ubupg26t01.htm]("http://linux.about.com/od/ubupck_doc/a/ubupg26t01.htm")

---

### Post by durand on 2009-05-30
The sole purpose of debian based systems is to fix this sort of "problem". I think you can use apt sources to manually compile the packages somehow but there would be no real point as it would be automated and you wouldn't learn anything and you would get exactly the same packages as if you used the binary ones since apt would compile exactly as it does on the build servers.

---

### Post by The Toxic Mite on 2009-05-30
Correct me if I am wrong, but I think you can boot from the Live CD, mount the hard drive, format it then install the things you want on there using the Terminal

---

### Post by b@sh_n3rd on 2009-06-02
So you guys thought it would be great to recommend Gentoo to "this nerd" huh?? well guess what? I had to emerge packages on my PC with an uptime of about 18 hrs and 40 mins..the guide I followed said that it wouldn't take more than 2 or 3 hours but it didn't even come in 12!!! I'm sick of Gentoo...in the "unwanted disk tin" it goes!!!:lolflag:

PS: If I sounded annoyed there, it was just an "act" of humor :D..I woudn't get angry with Ubuntu buddies, no way!! :D ;) (I'm trying arch btw :D)

---

### Post by CrazyArcher on 2009-06-02
Probably a nub question but I was thinking about it for a while and this thread reminded me...
Is it possible to recompile all the packages after having Ubuntu (or any other distro) installed? Well, surely it's possible, but would it yield any benefits? Can something get wrong as a result?

---

### Post by stwschool on 2009-06-02
I'm a relative noob and I've compiled stuff on Ubuntu, it's cool, it's a learning experience, sometimes stuff breaks, but that's what regular backups are for, and usually if it's little apps, it's not system-breaking. As you're compiling to your specific system you'll get a performance boost. I hear people mention compiling their own kernels, that's probably much more high-risk but it seems the performance gains there are quite large. Put it this way, I'm not brave enough for that yet outside of a virtual PC!

---

### Post by b@sh_n3rd on 2009-06-02
I really like compiling software manually from tarball sources. My next milestone would be to experiment with a custom kernel as **stwschool** mentioned, since what I'm asking in the thread title is not possible...

---

### Post by durand on 2009-06-02
> **b@sh_n3rd said:**
> So you guys thought it would be great to recommend Gentoo to "this nerd" huh?? well guess what? I had to emerge packages on my PC with an uptime of about 18 hrs and 40 mins..the guide I followed said that it wouldn't take more than 2 or 3 hours but it didn't even come in 12!!! I'm sick of Gentoo...in the "unwanted disk tin" it goes!!!:lolflag:

PS: If I sounded annoyed there, it was just an "act" of humor :D..I woudn't get angry with Ubuntu buddies, no way!! :D ;) (I'm trying arch btw :D)

There's a program in the gentoo repos that estimates how long your merges will take.
```
sudo emerge genlop
```


Then you can either pipe a prentend merge to it:
```
emerge --pretend [packages] | genlop -qp
```

or query how long the current program will take to compile:
```
genlop -qc
```

or query how long any program will take:
```
genlop -qt
```

The q tells genlop to look at online databases if it can't find any time estimates on the local machine.

---

### Post by jsmidt on 2009-06-02
[apt-build]("http://polishlinux.org/linux/debian/apt-build-optimize-debian/") may be similar to what you are looking for.

---

