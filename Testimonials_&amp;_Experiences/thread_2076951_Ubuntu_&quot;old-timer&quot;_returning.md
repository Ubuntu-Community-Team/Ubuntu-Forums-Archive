---
title: "Ubuntu &quot;old-timer&quot; returning"
date: 2012-10-27
forum: Testimonials &amp; Experiences
---

### Post by j00ed on 2012-10-27
Here's a long personal story about Linux and Ubuntu for you if you've got a few minutes to spare.

I discovered Linux in my early teens and was amazed by the eye candy it could offer (Compiz and company) compared to XP. Ubuntu was my first Linux distribution. I think it was one of the 2007 or 2008 releases. In any case, I was quite the Microsoft fanboy back then, and didn't really get into Ubuntu even after installing it, but a major OS crash left my XP installation dead, and it was (un)fortunately combined with a sudden internet access loss. Due to this, I had to use a vanilla installation of Ubuntu exclusively for 15 days or so... When I "finally" returned to XP with much relief and gazed upon the driver horror that awaited me, I went "nope" and didn't bother much with it anymore. I knew I was hooked.

After that came long adventures of distrohopping between stuff like Fedora, openSUSE, Gentoo (which, to this day, fails to emerge world without compilation errors), but I spent most of my time on Debian and Arch, and have even installed those last two distributions on some of my family's computers.

To be honest, I was pretty sure I had found my favourite distribution in Arch Linux, but eventually I grew tired of having to pay attention to tiny details lest updates break my system. One day Qt decided to break compatibility with KDE, the other day filesystem decided to change permissions in this or that system folder, nowadays there's the whole init-to-systemd transition that likes to break configuration files... Honestly, Arch was turning into just the kind of system I disliked in Gentoo, i.e. something that's snappy and innovative but too high maintenance for its own good. I couldn't claim I could install once, pacman -Syu forever any longer, and that was a huge appeal.

But of course, people like my mother on Debian stable could do just that without blinking, and that had become kind of appealing, to be honest. Specifically, I have lots of important files on my computers, and I really don't like the thought of a developer messing something up that ends up causing major file system damage, backups be damned. So, long story short, I went on the lookout for more stable, fixed release-circle-based distributions.

Good old Debian was a possibility, but it tends to be a bit too conservative with its packaging (good luck making Python 3 and PyQt cooperate on stable). On the other hand, Ubuntu has been getting quite a lot of flak around the websites I follow, but I had installed Lubuntu 12.04 for a tutorial I wrote, and it didn't seem all that bad. "It's slow! It crashes all the time! It's not customisable!" That kind of stuff. Back in the day, I had left Ubuntu due to stability issues, but I was also a newbie without much Linux knowledge back then. I decided to go find out for myself.

Now, I knew I wanted to try out GNOME 3 on Ubuntu, and there's no official flavour around that, and besides, I don't really fancy distributions that pre-install a ton of stuff, because more often than not I don't need it. So I grabbed the "mini.iso" for a "network install", which is mainly targeted at more "advanced" users.

To be honest, the ncurses-based installer was probably one of the easiest things I've done in a while. In my opinion it's actually better than the default Ubuntu installer, and definitely miles ahead of the likes of openSUSE. It felt like the Debian installer (and probably is based on it), and I highly suggest it to anyone feeling a bit more adventurous with Ubuntu. You should partition your hard drive with on a LiveCD before doing that, however, since the included partitioner isn't as good as GParted (nothing is).

After that was done, I ended up with a bunch of ttys, and ran sudo apt-get install xserver-xorg gnome-shell gdm gnome-terminal firefox synaptic, which wrapped things up for me. Zero configuration file editing required. ;)

So far, I really like Ubuntu 12.04. I don't know what people are rambling on about regarding responsiveness, stability, or customisability. I've found the experience on par with Arch Linux (when it's feeling happy), without the issues of update breakage and so on, and we all know Arch is hailed as super-customisable and super-responsive, second only to Gentoo maybe.

While I'm no big fan of Unity, I think a lot of self-proclaimed Linux "experts" have missed the memo that Ubuntu is more than a single user interface, and I think my experience makes it clear just how easy it is for a user to customise their desktop if they spend their time on synaptic instead of angry comment threads and news stories.

So, after a very, very long time, I'm back to Ubuntu, and I like it quite a lot so far. I'm not sure yet whether I want to stick to the LTS releases happening every couple of years, or just the April ones. I think that will depend on whether a radical new feature appears in GNOME that I really want.

Oh, lastly... The 12.10 mini.iso doesn't include wireless_tools or network drivers at all during a minimal installation, resulting in a system that can only see the loopback network and can't be fixed without chrooting or reinstallation! That doesn't look very sensible, since you can't install additional packages without at least ethernet support. That might be a bug; should I report it?

PS: I'm attaching a screenshot of my desktop to show off! :D

---

### Post by nothingspecial on 2012-10-27
Welcome to the forums :)


> **j00ed said:**
> That might be a bug; should I report it?



Yes you should.

---

### Post by j00ed on 2012-10-27
Thanks! I've reported the problem in Ubuntu's Launchpad.

---

### Post by nothingspecial on 2012-10-27
So I see :D

[https://bugs.launchpad.net/ubuntu/+bug/1072081](https://bugs.launchpad.net/ubuntu/+bug/1072081)

---

