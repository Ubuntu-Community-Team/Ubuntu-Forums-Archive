---
title: "Why should I switch to Ubuntu?"
date: 2006-08-12
forum: The Cafe
---

### Post by MaJoR42 on 2006-08-12
I used to be a Linux sysadmin but due to life, the universe and everything, am now only using Linux for my personal interests. I've always used Redhat and then Fedora, but I'm getting tired of the rate at which I need to upgrade if I want to stay current. Also, Fedora has gone in the direction of SELinux, which tends to interfere with everything I want to do.

I'd appreciate it if someone could give me some good reasons why I should switch to Ubuntu. In other words, why is Ubuntu a better system than Fedora?

I posted this here because I'm looking for answers that are more in depth than just "because everyone likes Ubuntu better".

Regards,
MaJoR42

---

### Post by maniacmusician on 2006-08-12
in regard to what you're looking for, the answer comes quick. you should switch because Ubuntu suits the needs of the average normal user. that's what it was built for. Even though it can be customized into something you would need as a sysadmin (I know you dont anymore; i'm just saying), It starts out as a system for the average user that want's to use linux only for their personal interests. and while there is some hard work required on some systems regarding customization of the way it looks, the way it plays certain things, I think that comes with every good system. To sum it up, Ubuntu would be good for you because you don't need to worry about keeping up to date all the time, and it's well suited for "personal interests." Unless you set Ubuntu up to do complex things, you usually don't get too many complex problems.

edit: also, be aware of the different flavors of Ubuntu. The main three: Ubuntu (Gnome), Kubuntu (KDE), and Xubuntu (XFCE; which has gotten a lot better recently).

edit again: another good reason to switch is you can get a *reasonable* view of the stuff that is in K/X/Ubuntu from the live CD that you download, if you have a decent system. Of course some things like wireless are harder to set up and best done with a HD installation, but live CDs are just for a glimpse anyways, and they work reasonably well.

---

### Post by ardchoille on 2006-08-12
I switched to Ubuntu from Fedora 4 for the following reasons:

1. I was tired of having to update everyday. Fedora is used as a test bed for cutting edge apps to see if said apps can be included into Red Hat distributions at a later date. Ubuntu doesn't use such cutting edge apps and I have found that updates in Ubuntu aren't nearly as frequent as they were in Fedora 4.

2. I always used yum in Fedora for package installation and updates. When I switched to Ubuntu, I found that apt-get, compared to yum, was blazingly fast.

3. I often found that, in Fedora, I was forced to compile apps because the apps I wanted weren't in the repos. Now that I am on Ubuntu, I can't remember having to compile anything. The Ubuntu repos are huge compared to Fedora.

4. I installed Fedora 5 over Fedora 4 and found that botting into Fedora 5 caused the system to hang everytime. I traced this problem to the Fedora 5 kernel - someone removed support for my NIC. When I brought this to the attention of the Fedora developers, they said, in so many words, "you're on your own".. and I had no idea of how to compile my own kernel. Ubuntu, however, installed and booted up quickly.

5. I have found the Ubuntu community much more open and willing to help than the Fedora community was. When you think about it, the community of a given distro is extremely important.

6. I always had to "work" at getting things to work in Fedora, probably because I had to compile so many apps that I wanted and had to chase down deps. In Ubuntu, the biggest problem I had was changing the icon in the main menu applet - a problem which was quickly solved after a few minutes in these wonderful forums.

I have found Ubuntu to be more stable and better "stocked" than Fedora. I love Ubuntu now, and it will be quite hard to get me to switch to anything else, having been through 17 distros :)

---

### Post by fragos on 2006-08-13
Ubuntu now has LTS, Long term Support, which means that at a minimum, security update support will continue even after new releases are made.  If the last version release is a good example, new versions don't mean new system builds.  Version upgrades work well with Ubuntu.

---

### Post by cogsprocket on 2006-08-13
> **ardchoille said:**
> 
2. I always used yum in Fedora for package installation and updates. When I switched to Ubuntu, I found that apt-get, compared to yum, was blazingly fast.

3. I often found that, in Fedora, I was forced to compile apps because the apps I wanted weren't in the repos. Now that I am on Ubuntu, I can't remember having to compile anything. The Ubuntu repos are huge compared to Fedora.

5. I have found the Ubuntu community much more open and willing to help than the Fedora community was. When you think about it, the community of a given distro is extremely important.


Well said, these are the reasons why I've almost completely stopped using RedHat flavors when I need a Linux solution for something.  I think at this point I'm using FC4 to allow SFTP to a samba share on one of our Windows server and that's only there because it's the only purpose it serves and there's no need to change it at the moment.

I never really liked RPM or Yum, myself because, like you point out in your third point I wound up having to just compile everything because what I really needed wasn't there.

Ubuntu thrives on it's community.  While it's not perfect, the community is one of the best of any distro I've seen.  I think a lot can be said for the fact that Ubuntu had brought in a newer crowd.  It seems a much easier transition from other distros because the community seems ready to get new users up to speed.  A major plus in my book.

---

### Post by fragos on 2006-08-13
Ubuntu uses technology but isn't focused on it.  The focus is the user.  Despite being a design engineer since 1964 I like the user focus -- Ubuntu is my distro of choice.  If the user focus doesn't jive with your purist *nix heart -- there's always Debian.

---

### Post by Iandefor on 2006-08-13
If you're a sysadmin used to the way Linux works, might I suggest you give Debian a whirl? They're planning on releasing a new stable by December, so it should be pretty up-to-date.

Personally, I feel less like I'm using Linux when I use Ubuntu, so, if you use Linux for fun, it's possible using Ubuntu won't be so satisfying as Debian.

Just a couple of thoughts :).

---

### Post by atrus123 on 2006-08-13
Hmm...  I really dig Ubuntu, but FC5 is pretty sweet as well.

If I had a really nice FC5 setup, I don't know if I'd switch.  However, one reason why I'm not using it now is that Debian based repositories are easier to deal with (though if I used FC regularly, I'm sure I'd have little problem figuring out the ins-and-outs of yum).

I also find that the average Ubuntu install tends to be just a bit better at hardware detection than FC5, but that's a small thing.

From what I understand, Ubuntu handles XGL better than Fedora (in which you're more limited to using the less-mature Aiglx).

Ultimately, I say just use whatever you're used to using, but if you do decide to switch, you will find Ubuntu a clean, smooth distro, which is both easy to use and maintains an active userbase.

---

### Post by Bragador on 2006-08-13
You should switch because you tried Ubuntu and liked it.

Seriously, just try the live cd and check it by yourself.

---

### Post by slakkie on 2006-08-13
> **Bragador said:**
> You should switch because you tried Ubuntu and liked it.

Seriously, just try the live cd and check it by yourself.

I agree with this remark. 

Reasons why you could switch are:
1) Ease of use ; The packaging system, which takes care of dependencies. I like the BSD ports system a lot. There are plenty of differences between the ports and apt, but they both take care of dependencies. 
The default installation provides you a system which works from the get go. No need to install a browser, mail client, office applications, and the works. Its already present.

2) For me this is a Unix/Linux flavor that is really focussed on the desktop; It supports all PC's I'm currently using, other distro's often gave problems with my graphics card.

3) This is valid for me, and not for you; its a perfect replacement for Windows. It's even better.

4) I've tried it, and I simply fell in love with it. I think you should give it a shot and see for yourself. If it fits your needs and whishes - go for it, otherwise, go back to your previous distro.

---

### Post by Derek Djons on 2006-08-13
And you can of course try Ubuntu for the reasons you mentioned yourself about other Linux distro's.

---

