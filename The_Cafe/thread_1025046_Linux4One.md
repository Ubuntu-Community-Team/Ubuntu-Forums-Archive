---
title: "Linux4One"
date: 2008-12-29
forum: The Cafe
---

### Post by Warpnow on 2008-12-29
Apparently, an Italian team has released a version of Ubuntu Netbook Remix customized for the Acer Aspire One- only one catch- it, its site, and the entirety of its installation is in Italian, without the option to switch to linux at the boot screen...

Does anyone know anything about this distribution?

---

### Post by gettinoriginal on 2008-12-29
Found this:

[http://eeepc.itrunsonlinux.com/the-news/1-latest-news/242-linux4one-ubuntu-for-the-acer-aspire-one-](http://eeepc.itrunsonlinux.com/the-news/1-latest-news/242-linux4one-ubuntu-for-the-acer-aspire-one-)

---

### Post by dinda on 2009-01-02
I downloaded the iso and tried it but I keep getting a "Fatal error.  Battery module not found" and then the machine boots in the the vanilla UNR version I first installed.

Using the vanilla UNR doesn't give much functionality as the repositories are incorrect and no new apps can be installed due to the lpia architecture.  Very disappointing so far.  I'll try a few more things then will revert back to the version of XP that shipped with the machine.
:(

---

### Post by bradthewanderer on 2009-01-02
I don't understand why people aren't just putting the full version on?

---

### Post by Prefix100 on 2009-01-02
> **bradthewanderer said:**
> I don't understand why people aren't just putting the full version on?

Custom kernel means faster boots etc

---

### Post by pjalegria on 2009-01-02
When multilanguage version???

---

### Post by dinda on 2009-01-02
Plus UNR has a customized interface and is better adapted for the smaller displays.

---

### Post by bradthewanderer on 2009-01-02
Ok thanks.

---

### Post by Rotaj on 2009-01-03
I just read that an english version should be out Tuesday.

[http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=8884&p=58887&hilit=linux4one#p58887]("http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=8884&p=58887&hilit=linux4one#p58887")

---

### Post by blazemore on 2009-01-11
I'd quite like an update on this, as I'm torn between an Aspire One and an eeePC for my girlfriend's birthday...
Ubuntu support is a must.

---

### Post by dinda on 2009-01-11
I've still had no luck getting this update on the acer aspire one.  Ever since I've installed the UNR, the machine will no longer boot from the USB drive or CD images.  Anyone have a way to completely remove UNR or force boot to USB so that I can try this update?

The problem with UNR is that all the repositories are wrong so no updates can be installed.  Even when I manually added in the correct ones, including the binary-lpia one, there is a very limited set of apps that can be added.  Most apps say they are not compatible with the lpia or the maker of the app does not have support for lpia.  Most notable is java 7 and many other java components.

I'm afraid it's back to XP on this machine.  :(

---

### Post by SpicyMcHaggis on 2009-01-11
I just finished the install on my new Acer One. And other than getting adjusted to the netbook remix interface, it seems to run rather well. I figured that I'd use the stock setup for a while before I change anything, just to see if i like it.

---

### Post by lydmrtnyng on 2009-01-18
i've tried Linux4One i think one down side of it comparing to linpus lite it that it can only run the unit for 2hrs only... while linpus could max a 3 cell battery up to three hours...

---

### Post by crazyjj on 2009-03-19
Hi;

I have just installed Unix4one on my new (!) Acer Aspire one.  

It all seems to work very well but I cannot get my wireless connection up.  The card is working as it can 'see' the network but it cannot connect.  There seems to be two independent wireless network configs; on in 'network' within preferences 9which has a 'roaming' tick box, and one on the top menu bar.  They seem to work in different ways; ie one will take the pass phrase then other only take the hex key?

Is this a general ubuntu thing or just in this distro?

Anybody got an ideas or config guidance?

Cheers

J

---

### Post by t0p on 2009-03-19
> **crazyjj said:**
> Anybody got an ideas?

Yeah... learn Italian then ask for help at the Linux4One website!

:p

---

### Post by crazyjj on 2009-03-19
Hmmm, yes.  

I was sort of hoping that there may be a faster solution perhaps. 

J

---

### Post by imagia on 2009-04-24
> **t0p said:**
> Yeah... learn Italian then ask for help at the Linux4One website!

:p

The website has all the necessary info in English if you care to scroll down. And there's a full installation guide in English over here:

[http://www.linux4one.it/forum/index.php?topic=144.0](http://www.linux4one.it/forum/index.php?topic=144.0)

If you don't want to spend hours tweaking a distro, it's well worth installing this one. My AAO has worked out of the box every time.

---

### Post by Sokraates on 2009-05-28
> **imagia said:**
> My AAO has worked out of the box every time.

Which implies that you have done some reinstalls. Care to share the reason why?

At the moment I have UNR Jaunty installed on my A110L and I'm very satisfied, which means a lot, considering that I usually use Kubuntu.

I was considering switching to Linux4One due to the WLAN-LED support and (hopefully) a better startup time. Does anyone have any experience with Linux4One and UNR on an A110?

What also makes me wonder: Linux4One claims that they have fixed the SD-card issue (not recognized unless the system is booted with a card in the slot), however they say that the card is recognized as a regular SD-card instead of a storage expansion. What's the difference? In my places menu, I see the card in the storage expansion slot like ay nrmal SD-card.

---

### Post by Warpnow on 2009-05-28
> **Sokraates said:**
> Which implies that you have done some reinstalls. Care to share the reason why?

At the moment I have UNR Jaunty installed on my A110L and I'm very satisfied, which means a lot, considering that I usually use Kubuntu.

I was considering switching to Linux4One due to the WLAN-LED support and (hopefully) a better startup time. Does anyone have any experience with Linux4One and UNR on an A110?

What also makes me wonder: Linux4One claims that they have fixed the SD-card issue (not recognized unless the system is booted with a card in the slot), however they say that the card is recognized as a regular SD-card instead of a storage expansion. What's the difference? In my places menu, I see the card in the storage expansion slot like ay nrmal SD-card.

They mean that they don't have the feature linpus does where inserting an SD card into the left SD slot merges it with the SSD.

As the one who started this thread, I'll note that after alot of toying, I've landed on Kuki Linux, [www.kuki.me](www.kuki.me), as my distro for my Acer Aspire One.

---

### Post by Sokraates on 2009-05-29
> **Warpnow said:**
> They mean that they don't have the feature linpus does where inserting an SD card into the left SD slot merges it with the SSD.

Aha. I always thought that UNR supported Storage Expansion since it was not listed among the prominent bugs. 

I didn't toy around with Linpus long enough to find out how Storage Expansion should work, since it did not recognize my 3G-modem I I couldn't make it work despite some very good How-Tos (and I'm not afraid of the CLI either). So I wiped Linpus and installed UNR, which supported the modem out of the box.

---

### Post by Warpnow on 2009-05-29
The Storage Expansion is purely software driven so it not being supported is not really a bug. Its just the lack of a feature.

---

### Post by Sokraates on 2009-05-29
> **Warpnow said:**
> The Storage Expansion is purely software driven so it not being supported is not really a bug. Its just the lack of a feature.

Right. Thanks for the explanation.

---

