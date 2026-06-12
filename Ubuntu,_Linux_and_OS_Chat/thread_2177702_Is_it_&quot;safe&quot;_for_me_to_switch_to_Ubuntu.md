---
title: "Is it &quot;safe&quot; for me to switch to Ubuntu?"
date: 2013-09-29
forum: Ubuntu, Linux and OS Chat
---

### Post by 7nXwYdh on 2013-09-29
Hello!

The title might seem odd to some of you, so let me explain a bit. :) When I say "is it 'safe'" to switch to Ubuntu, I ask because of the current situation with Mir. I myself have no opposition to the fact that Canonical has decided to use Mir as the default display server in Ubuntu 13.10, but the only thing I'm concerned about is proprietary driver support. I play some games on Steam, so proprietary drivers are a must for me. I know that I can fall back to X and use the current drivers in 13.10, but what about when 14.04 LTS comes along? Is it likely that AMD/Nvidia will put out Mir-compatible drivers when the time comes? I know there is no definite answer, but what's *your* opinion?

Also, I saw somewhere that if AMD/Nvidia were to put out a driver that uses EGL (not 100% sure what that is, but that's beside the point), that the driver would be compatible with both Mir and Wayland. Is that true? I don't have much knowledge when it comes to driver coding, so that could be completely wrong. :P

Thanks! :D

---

### Post by deadflowr on 2013-09-30
I have 13.10 installed, with absolutely no sign of mir.
Using nvidia's drivers.
Take it as you will
Here's some comments on the latest beta
[http://ubuntuforums.org/showthread.php?t=2177095](http://ubuntuforums.org/showthread.php?t=2177095)

---

### Post by cariboo on 2013-09-30
If you have a high enough friend count, you can take part in the SteamOS Beta

---

### Post by ssam on 2013-09-30
I don't think there is much risk of Ubuntu taking away the option of using the closed graphics drivers.

---

### Post by kostkon on 2013-09-30
> **7nXwYdh said:**
> I know that I can fall back to X and use the current drivers in 13.10, but what about when 14.04 LTS comes along? Is it likely that AMD/Nvidia will put out Mir-compatible drivers when the time comes? I know there is no definite answer, but what's *your* opinion?
13.04 will automatically fallback to X if you are using the proprietary drivers from Nvidia or AMD, so don't worry. 
> **7nXwYdh said:**
> Also, I saw somewhere that if AMD/Nvidia were to put out a driver that uses EGL (not 100% sure what that is, but that's beside the point), that the driver would be compatible with both Mir and Wayland. Is that true?
It is, yes. Nvidia and AMD are currently working on the EGL drivers. Check on [Phoronix]("http://www.phoronix.com/") for some articles related to that.

Hope that helps.

---

### Post by grahammechanical on 2013-09-30
Xmir is part of Mir but not all there is to it. Xmir replaces the Xserver and the intention is to have it do this by default in the 13.10 release. Therefore it will also be default in 14.04. But, although 13.10 final beta is out Xmir is still not in 13.10 by default. At the moment the Xmir module will only load if we are running on Nouveau and if we are using Lightdm. For Lightdm manages the Xserver as well as the login screen and it has been patched to also manage Xmir. GDM has not been patched in this way so Xmir will not load on Ubuntu Gnome.

We are told that discussions are under way with the developers of proprietary video drivers for them to modify their drivers to run Mir. There is no rush for this to happen because it is not planned for Mir to be in 14.04 but in 14.10. By the way, Mir replaces not only the Xserver but also Lightdm and Compiz.

Think of it this way. If we are worried about Mir becoming the display server by 14.10 then we should also be worried about any Wayland compositor becoming the display server during the next 12 - 18 months. We will be in the same situation with a Wayland display server as we will be with the MIr display server and that is uncharted territory.

The one thing that I think is certain is that X is going to be replaced sometime during the next two years whether it be by a Wayland display server or by the MIr display server. So, I say expect a rocky ride and if you don't like ups and downs on the journey then stick to an LTS.

Regards.

---

### Post by Bucky Ball on 2013-09-30
Start with 12.04 LTS if you want safe. Perhaps try the newer releases as you get your feet wet and things get sorted with Mir, etc.

You are installing an unreleased version if you install 13.10 anyhow, regardless of Mir or anything else. ;)

---

### Post by buzzingrobot on 2013-09-30
What Bucky said.

I can't imagine Canonical releasing an Ubuntu that can't use Nvidia/AMD drivers.  They might slip a release date, change Mir's schedule, or make X the default with Mir optional, but not deliberately do a broken release.

The current LTS release is 12.04.03.  Get it at releases.ubuntu.com. Supported until 2017.

---

### Post by deadflowr on 2013-09-30
> **buzzingrobot said:**
> What Bucky said.

I can't imagine Canonical releasing an Ubuntu that can't use Nvidia/AMD drivers.  They might slip a release date, change Mir's schedule, or make X the default with Mir optional, but not deliberately do a broken release.

The current LTS release is 12.04.03.  Get it at releases.ubuntu.com. Supported until 2017.

12.04.3 is what is currently available here
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

I think if you go to releases.ubuntu.com or old-releases.ubuntu.com you can get the older point releases of 12.04.
The older point releases have the older kernel versions and older X stacks.

---

### Post by 7nXwYdh on 2013-09-30
Thanks everyone for the replies! I have actually been using Ubuntu for a while now (since 9.04) so I'm fairly experienced with it, just trying to get other people's opinions. :)

> **grahammechanical said:**
> There is no rush for this to happen because it is not planned for Mir to be in 14.04 but in 14.10.

Thanks grahammechanical for the response, but isn't Mir supposed to become the default in 13.10 with an X fallback, and then that fallback will be removed in 14.04? I read that **[here]("http://www.omgubuntu.co.uk/2013/06/mir-display-server-to-ship-default-in-ubuntu-13-10")**(OMGUbuntu) and **[here]("http://news.softpedia.com/news/The-Mir-Display-Server-Will-Be-Default-in-Ubuntu-13-10-X-Used-as-Fallback-363953.shtml") **(Softpedia), but perhaps I missed some more recent news? :confused: Please correct me if I'm wrong! :)

Thanks again everyone for the replies!

---

### Post by monkeybrain20122 on 2013-09-30
> **7nXwYdh said:**
> Thanks everyone for the replies! I have actually been using Ubuntu for a while now (since 9.04) so I'm fairly experienced with it, just trying to get other people's opinions. :)



Thanks grahammechanical for the response, but isn't Mir supposed to become the default in 13.10 with an X fallback, and then that fallback will be removed in 14.04? I read that **[here]("http://www.omgubuntu.co.uk/2013/06/mir-display-server-to-ship-default-in-ubuntu-13-10")**(OMGUbuntu) and **[here]("http://news.softpedia.com/news/The-Mir-Display-Server-Will-Be-Default-in-Ubuntu-13-10-X-Used-as-Fallback-363953.shtml") **(Softpedia), but perhaps I missed some more recent news? :confused: Please correct me if I'm wrong! :)

Thanks again everyone for the replies!

My understanding is that the roadmap of removing x fallback assumes that there will be proprietary graphic driver support by 14.04. If not I suppose x fallback will stay so I am not worrying about that. The worst case scenario is that there IS some last minute proprietary driver support for 14.04  but it is buggy (as these things usually takes time to smooth out) and they remove x fallback, so IMO if proprietary driver doesn't come early in the 14.04 developmental cycle it may as well not come at all until 14.10. 

I would also like to have the option of using the up to date open source drivers even if I have an Nvidia or AMD card (there seems to be a lot of exciting development in the open source 3d drivers lately) I have no idea how nouveau works with xmir as most of the data appear to be Intel and if you use Nvidia everyone assumes that you would use the blob, but nouveau is actually smoother than the blob for most "normal" use not involving gaming in 13.04 and 12.04.The latest nouveau developmental driver appears to have some support for power management and vdpau, it is closing the gap. It would be very bad if Ubuntu cuts itself off from these developments because of Mir.

---

### Post by 3rdalbum on 2013-10-01
X will not be removed from Ubuntu before 15.04. It might not be in the default install, but it will be in the repositories. I'm sure of it. Even if it is removed from the repos, someone will put it in a PPA or you can compile it yourself.

So, no need for panic.

---

### Post by 7nXwYdh on 2013-10-01
UPDATE: Looks like Canonical has decided to push back Mir again. Source: [http://www.omgubuntu.co.uk/2013/10/xmir-longer-default-supported-cards-13-10](http://www.omgubuntu.co.uk/2013/10/xmir-longer-default-supported-cards-13-10)

---

