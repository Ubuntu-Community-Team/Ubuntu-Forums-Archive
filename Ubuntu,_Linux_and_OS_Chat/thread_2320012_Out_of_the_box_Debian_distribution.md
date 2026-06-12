---
title: "Out of the box Debian distribution"
date: 2016-04-09
forum: Ubuntu, Linux and OS Chat
---

### Post by marouane87 on 2016-04-09
Hello :)

There are hundreds of Linux Distributions out there that are derived from Debian (including Ubuntu). But Debian is not really a user friendly when it comes to the first setups and configurations.
So, I'm wondering why isn't there a derivative that is based on Debian (testing or stable) and that works "out of the box" pretty much like Korora for Fedora, Ubuntu after checking the extras when installing etc... ?

---

### Post by grahammechanical on 2016-04-09
I do believe that the Debian way is not to use proprietary software of any kind. And that I think is the reason why Debian does not necessarily work "out of the box" as you put it. It is why we have a distribution called Ubuntu. But even so, Ubuntu developers give the responsibility of using proprietary software to the user. And so sometimes Ubuntu does not work "out of the box." There are distributions that go further still away from the model of all Free and Open Source Software and include proprietary software without even asking. I think that Linux Mint is that kind of distribution.

The more a distribution goes toward working out of the box, the less Debian it becomes.

Regards

---

### Post by KBD47 on 2016-04-09
Debian has become much easier to install and use in the last two stable releases. On older hardware it pretty much works out of the box, you will need to enable 'contrib non-free' in sources to get codecs and such, but that is about it. On newer hardware Debian Stable may not be a good choice because of using an older kernel lacking drivers for new hardware.

---

### Post by montag dp on 2016-04-09
Um, there is one. It's called Ubuntu. :)

That said, Debian isn't hard to get working out of the box. Yes, you may have to read a thing or two and it doesn't attempt to do everything for you (like Ubuntu), especially when it comes to proprietary drivers, but that's by design.

To KDB47: about the kernel, you can get 4.4 on Debian stable by using the backports repository.

---

### Post by Bucky Ball on 2016-04-09
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by grahammechanical on 2016-04-10
> Only software that complies with the DFSG is allowed in the main distribution of Debian.

[https://www.debian.org/intro/free](https://www.debian.org/intro/free)

The Debian Free Software Guidelines

[https://www.debian.org/social_contract#guidelines](https://www.debian.org/social_contract#guidelines)

People who build distributions on other distributions usually have a greater vision than simply adding a facility to automatically install proprietary drivers. We see this in Ubuntu, built on Debian & Linux Mint, built on Ubuntu.

It is one thing to give credit to Debian as the original source of the distribution. The Debian developers would like that. It is something else to call it a Debian distribution if it does not comply with the Debian Free Software Guidelines. I do not think that the Debian developers would like anybody doing that. No. Not at all.

 Regards

---

### Post by montag dp on 2016-04-10
> **grahammechanical said:**
> [https://www.debian.org/intro/free](https://www.debian.org/intro/free)

The Debian Free Software Guidelines

[https://www.debian.org/social_contract#guidelines](https://www.debian.org/social_contract#guidelines)

People who build distributions on other distributions usually have a greater vision than simply adding a facility to automatically install proprietary drivers. We see this in Ubuntu, built on Debian & Linux Mint, built on Ubuntu.

It is one thing to give credit to Debian as the original source of the distribution. The Debian developers would like that. It is something else to call it a Debian distribution if it does not comply with the Debian Free Software Guidelines. I do not think that the Debian developers would like anybody doing that. No. Not at all.

 Regards I'm not sure if you were replying to me or anyone in particular, but I don't think anyone is referring to Ubuntu and the other derivatives as "Debian distributions." But they are the following:

> **marouane87 said:**
> ... a derivative that is based on Debian (testing or stable) and that works "out of the box" ...  Although, I think I read that Ubuntu is actually based on Debian unstable frozen at a certain point in time, so that's a slight difference compared to what he's looking for. But then again, Debian testing and stable are based on unstable.

---

### Post by marouane87 on 2016-04-10
I understand about the open and free philosophy of Debian. 
Meanwhile, I don't see a distribution that is based on "Vanilla Debian" that offers everything out of the box, which in my humble opinion, will have an impact on how users see Debian: "Server oriented" or "Difficult to set up".

---

### Post by Rocky_Bennett on 2016-04-10
I am a Linux newbie and I have Debian installed on my computer. It worked for me perfectly out of the box, but I went ahead and changed the sources list anyway.

---

### Post by deadflowr on 2016-04-10
What would constitute Vanilla Debian?

---

### Post by marouane87 on 2016-04-10
Just Debian :)
To make myself clear, I will use the example of Arch:

- There is Arch (The "normal" one)
- There are Architecte/Bridge: These are distributions that are based on Arch which are there for the ease of installation of Arch and simple install of graphical interface.
- There are Antergos/Manjaro: These are derivatives that made changes to Arch Additions that are not only limited to the ease of installation and use (Modified theme, repository for some etc...)

---

### Post by Habitual on 2016-04-10
> **deadflowr said:**
> What would constitute Vanilla Debian?

Anything labeled "default".

---

### Post by montag dp on 2016-04-10
Default according to whom? Debian already applies plenty of its own patches. If you want vanilla, you probably need to go for something like Arch or Slackware. 

I suspect what he wants is Debian with non-free and contrib repos enabled by default, and maybe a fancier installer. I don't think there is such a thing.

I suppose this is because if someone wants to go through the trouble of making a distro, they also want to make it their own, with their own personalization, vision, and goals baked in.

---

### Post by marouane87 on 2016-04-11
Yes sure and that´s what I´m looking for (I even got answer from [6975]("http://ubuntuforums.org/member.php?u=2024607") whom I deeply thank) contqining non free frirmware.

About the Vision, that´s what makes each Distribution unique, the Vision of ist creature wheras it´s a from scratch Distribution or a derivative. I was asking why so much derivative "out of the box" of ubuntu and Arch but not Debian :)

---

### Post by mastablasta on 2016-04-11
> **deadflowr said:**
> What would constitute Vanilla Debian?


the netinstall image :P

---

### Post by deadflowr on 2016-04-11
Have you looked at [bunsenlabs]("https://www.bunsenlabs.org/") yet?

---

### Post by marouane87 on 2016-04-11
Thank you! This is kind of the projects I'm talking about  :)
But I don't think I will go for it because I would like to have a gnome experience :)

---

### Post by vasa1 on 2016-04-11
> **deadflowr said:**
> Have you looked at [bunsenlabs]("https://www.bunsenlabs.org/") yet?
And the devs of the project are present in the forums. Quite approachable.

I don't distro-hop but this is one I'd like to try sometime.

---

### Post by kansasnoob on 2016-04-12
> **marouane87 said:**
> Thank you! This is kind of the projects I'm talking about  :)
But I don't think I will go for it because I would like to have a gnome experience :)

By "gnome experience" do you mean GNOME Shell? Or do you mean the old style GNOME 2 experience?

Linux Mint has Debian Editions with both the Cinnamon and Mate DE's:

[https://www.linuxmint.com/download_lmde.php](https://www.linuxmint.com/download_lmde.php)

I personally prefer Ubuntu GNOME, although it seems like GNOME Shell just keeps getting more and more resource hungry recently (or maybe I'm just expecting Xenial to be more stable at this point).

---

### Post by marouane87 on 2016-04-12
I´m talking about Gnome Shell. I had enough experience with Gnome 2 like Interface through Cinnamon for the last 3 years :) 
It seems that LMDE is not really a priority for the Mint Team and as I said, it´s time for me to move from Cinnamon and Mate.

---

### Post by mastablasta on 2016-04-12
> **deadflowr said:**
> Have you looked at [bunsenlabs]("https://www.bunsenlabs.org/") yet?

awesome if they can make it as #!. it was one of the best Linux desktop distributions. easy to setup, minimalistic and I liked the questions in the start (the scripts) so you can easily enable or not enable certain function/feature on install.

---

### Post by CharlesA on 2016-04-12
> **montag dp said:**
> Um, there is one. It's called Ubuntu. :)

That said, Debian isn't hard to get working out of the box. Yes, you may have to read a thing or two and it doesn't attempt to do everything for you (like Ubuntu), especially when it comes to proprietary drivers, but that's by design.

To KDB47: about the kernel, you can get 4.4 on Debian stable by using the backports repository.

Oh yes... I remember having to fudge with nonfree firmware for network cards when doing installs with Debian.. so much fun. :p

---

