---
title: "Would it be possible to create a DRM spoof for Netflix?"
date: 2013-07-07
forum: Ubuntu, Linux and OS Chat
---

### Post by JamesTheAwesomeDude on 2013-07-07
I've read about the issue of Netflix not supporting Linux (first, they said "there's no Silverlight." Moonlight was pointed out, they said "there's no DRM." The Linux community offered support, and was turned down wholeheartedly.)

I think we've given Netflix every opportunity to reach out to the Linux community, and allow people to use a service they paid for on a computer they own. It's time to take action ourselves.

Moonlight has the power to play Netflix, there are Firefox add-ons to spoof the necessary HTTP headers, now all we need is a modification to Moonlight that would spoof whatever Netflix is looking for to send the video to the computers.

Now, some of you may say "wait: isn't this illegal?"
Think about this: Watching DVD's that you legally own [is, in fact, illegal]("http://www.howtogeek.com/138969/why-watching-dvds-on-linux-is-illegal-in-the-usa/") if your machine is running Linux, but [Jon Lech Johansen]("https://en.wikipedia.org/wiki/Jon_Lech_Johansen") found a way to do it, and to this very day, [we can watch our bought-and-paid-for DVD's on Linux]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs"), and the DVD CCA hasn't shut down Canonical yet. Ubuntu's still alive and thriving.

Why can't we use our Netflix streaming services that we paid for, just because we've got our computers booted into a certain OS?

Moonlight is open-source, so the proposed modifications, while difficult, may not be impossible.
Is this being planned? Has it already been considered? Is it available, just not openly?

From a proud Netflix subscriber.

P.S., *please* do not talk about the Netflix Ubuntu PPA here. I know that my computer (from the Windows XP generation) is far too weak to run it, and with XP being abadoned by MS next year, there will be more computers that have to go linux-only (instead of a dual-boot.) For now, the issue is a mere inconvenience (you have to wait 2 minutes for a reboot whenever you want to watch Netflix,) but I don't want to have to put my computer at risk every time I need to use the computer to play Netflix.

---

### Post by Gnawnsense on 2013-07-07
> **JamesTheAwesomeDude said:**
> P.S., *please* do not talk about the Netflix Ubuntu PPA here. I know that my computer (from the Windows XP generation) is far too weak to run it, and with XP being abadoned by MS next year, there will be more computers that have to go linux-only (instead of a dual-boot.) For now, the issue is a mere inconvenience (you have to wait 2 minutes for a reboot whenever you want to watch Netflix,) but I don't want to have to put my computer at risk every time I need to use the computer to play Netflix.

I'm confused. You don't have to wait for a reboot to use the software in the PPA. You simply install, it uses Wine for the Silverlight plugin, and you watch Netflix from your Linux install. The requirements aren't outrageous. If you can watch Netflix on the machine, you can definitely use this solution, as well.

I wouldn't assume your computer won't run it without giving it a try. It's as easy to remove as it is to install. But your solution has already been created, it's up to you to use it or not.

[http://linuxg.net/how-to-use-netflix-on-ubuntu-13-04/](http://linuxg.net/how-to-use-netflix-on-ubuntu-13-04/)

But, in regards to your concerns. There are plenty of Netflix alternatives out there to use. You aren't being victimized by Netflix not offering native Linux support. You know every month you pay your subscription that due to the technology they use (Silverlight, which is Microsoft proprietary software), there is no native Linux support. They aren't wronging you by not offering it, just like an Ubuntu user who bought Adobe Creative Suite isn't being wronged by the software being Windows only. You know that going into it.

The best solution would be to speak with your wallet, or utilize the options we have available. You can't force a company to support your system. You can either adapt, wait for the company to come around, or move on.

The thing with DVDs is, you purchase the content. With Netflix, you didn't purchase any physical goods. You purchased subscription-based access to the Netflix collection. Trying to spoof Netflix DRM is completely different morally than getting your physically owned DVDs to play. All you purchase from Netflix is access to their collection, not the collection itself.

---

### Post by monkeybrain2012 on 2013-07-07
BTW Netflix is going to dump silverlight anyway.
[http://www.theinquirer.net/inquirer/news/2261684/netflix-drops-silverlight-moves-to-html5](http://www.theinquirer.net/inquirer/news/2261684/netflix-drops-silverlight-moves-to-html5)

But the downside is that the new DRM implementation probably won't work on Linux either. Personally I don't use Netflix so either way I don't care much, but it is good for Linux to go mainstream if people can watch Netflix on their Linux boxes.

---

### Post by coldraven on 2013-07-08
If I land on any site that requires Silverlight I just go elsewhere, maybe they will get the hint.
Try installing the Ghostery add-on in Firefox and just see how many trackers etc. some sites use. It's quite frightening how much data they are sucking out of us.

---

### Post by JamesTheAwesomeDude on 2013-07-08
> **Gnawnsense said:**
> I'm confused. You don't have to wait for a reboot to use the software in the PPA. You simply install, it uses Wine for the Silverlight plugin, and you watch Netflix from your Linux install. The requirements aren't outrageous. If you can watch Netflix on the machine, you can definitely use this solution, as well.

I wouldn't assume your computer won't run it without giving it a try. It's as easy to remove as it is to install. But your solution has already been created, it's up to you to use it or not.

[http://linuxg.net/how-to-use-netflix-on-ubuntu-13-04/](http://linuxg.net/how-to-use-netflix-on-ubuntu-13-04/)I didn't assume it wouldn't wok without trying it. In fact, I went into it with the concept of it not working hardly on my mind at all. But, nonetheless, all it did was eat up my CPU cycles for 10 minutes, freeze the window, and it needed to be killed in the end.

> **Gnawnsense said:**
> But, in regards to your concerns. There are plenty of Netflix alternatives out there to use. You aren't being victimized by Netflix not offering native Linux support. You know every month you pay your subscription that due to the technology they use (Silverlight, which is Microsoft proprietary software), there is no native Linux support. They aren't wronging you by not offering it, just like an Ubuntu user who bought Adobe Creative Suite isn't being wronged by the software being Windows only. You know that going into it.

The best solution would be to speak with your wallet, or utilize the options we have available. You can't force a company to support your system.I'm actually just a kid, not in charge of the finances of our house. But even if I were, I would still keep Netflix. Their decicsion to snub Linux users, while irritating, is understandable from a business perspective.

> **Gnawnsense said:**
> You can either adapt, wait for the company to come around, or move on.

The thing with DVDs is, you purchase the content. With Netflix, you didn't purchase any physical goods. You purchased subscription-based access to the Netflix collection. Trying to spoof Netflix DRM is completely different morally than getting your physically owned DVDs to play. All you purchase from Netflix is access to their collection, not the collection itself.What I'm proposing is "option 1", so to speak - Adapt.

Spoofing and hacking our way through Netflix's restrictions may be morally grey and legally questionable, *but that's half the point*. It is nice to be able to watch Netflix on older computers, but it's pretty cool knowing that you're doing it against the company's will, *and that they brought it on themselves*.

So my request is partly uilitarian (let us watch Netflix on computers older than Win 7,) and partly idealistic (Netflix won't let us stream video, so WE let us stream video.)

---

### Post by JamesTheAwesomeDude on 2013-07-08
@coldraven

Yeah, Netflix is actually the only site I've ever seen that uses Silverlight, and it's really the only reason I ever installed Silverlight (bet you dollars to donuts that Netflix accounts for 90% of Silverlight installs ;))

If (when) Netflix drops Silverlight, it'll be uninstalled within the hour.

---

### Post by JamesTheAwesomeDude on 2013-07-08
> **monkeybrain2012 said:**
> BTW Netflix is going to dump silverlight anyway.
[http://www.theinquirer.net/inquirer/news/2261684/netflix-drops-silverlight-moves-to-html5](http://www.theinquirer.net/inquirer/news/2261684/netflix-drops-silverlight-moves-to-html5)

But the downside is that the new DRM implementation probably won't work on Linux either. Personally I don't use Netflix so either way I don't care much, but it is good for Linux to go mainstream if people can watch Netflix on their Linux boxes.
Hopefully Ubuntu will offer it in the Restricted or Multiverse repositories, somewhat in the vein of the paid Software Center apps, or the closed-source codecs (e.g., [FONT=courier new]libmp3lame[/FONT], [FONT=courier new]libgstreamer-plugins-bad[/FONT], etc.)

---

### Post by snowpine on 2013-07-08
Netflix runs great in Ubuntu using the PPA. It sounds like you are hoping your family will buy you a new computer to replace your old piece-of-junk XP machine, but you are instead misdirecting your frustration against Netflix Corp. :)

---

### Post by JamesTheAwesomeDude on 2013-07-08
@snowpine

Nah, I've been ticked off about Netflix's not supporting Linux for a while, but it wasn't really a pressing matter until I discovered Win XP's EOL next year.

We have a family of 7, so oftentimes, the "Big People" will watch something like The Walking Dead on the PS3, and the "Little People" will go and watch Netflix on my computer. But with Windows XP about to be filled with more security holes than Internet Explorer, that's not going to be safe anymore. :(

Also, keep in mind, this isn't all about Netflix being the bad guy; their decision was completely understandable.
This is both an ideasistic *and* a utilitarian proposal. It's not just a jab at Netflix, but also an attempt to keep our older computers useful for streaming movies from Netflix.

---

### Post by snowpine on 2013-07-08
Microsoft is dropping support for your hardware next year, so why should Ubuntu continue to support it? Ubuntu didn't even exist yet back in 2001 when Windows XP was released. Nothing wrong with XP (it's been very popular!) but Ubuntu has never marketed itself as "the new Windows XP." ;)

If you have aging hardware that struggles to play multimedia, then perhaps experiement with a "lightweight" desktop environment such as Xfce/Xubuntu or LXDE/Lubuntu?

---

### Post by JamesTheAwesomeDude on 2013-07-08
Ya, that's probably what I'll do.

But a patched version of Moonlight would be DE-independent, I should think...

---

### Post by MadmanRB on 2013-07-08
With any luck we may get the ability to watch netflix in chrome.

---

