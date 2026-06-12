---
title: "Making Ubuntu safe for work in the US"
date: 2011-08-03
forum: The Cafe
---

### Post by jhargis1012 on 2011-08-03
Hello. Over the past few months, I've been researching the legality of using some software, mainly audio/video codecs, in Linux in the United States. It looks like here in the US we enjoy one of the WORST patent law situations on Earth. I eagerly await serious reform as more and more people realize how ridiculous software/algorithm patents really are.

Yet, in the meantime, I feel it's important to be equipped with some knowledge of how to legally navigate these messy waters. My main question is does anybody know where I can find some kind of straightforward outline for how to keep an Ubuntu installation legally suitable for, say, a work or non-profit environment in the US? Is there a clear-cut way to know which packages are safe and which are legally iffy? Thanks a bunch for any insights.

---

### Post by arubislander on 2011-08-03
There used to be the option of installing Gobuntu, which was all the goodness of Ubuntu but only the Free (as in Speech) bits.

from [http://en.wikipedia.org/wiki/Gobuntu]("http://en.wikipedia.org/wiki/Gobuntu") I understand that it is possible to choose only Free software when installing Ubuntu. The article also mentions gNewSense as an alternative.

---

### Post by jhargis1012 on 2011-08-03
Thanks for the reply. See, the only problem with that is I'm looking for more than just totally free software. I'm interested in software that functions acceptably within the US legal framework. An good example of what I'm trying to stay away from is VLC. VLC is a great program, totally free and open-source. The problem is, in the US, it's a downright patent NIGHTMARE.

---

### Post by PhilGil on 2011-08-03
A default Ubuntu install should be legal in the US. I would either avoid installing any additional audio/video packages or [purchase the codecs]("http://shop.canonical.com/product_info.php?products_id=244").

---

### Post by grahammechanical on 2011-08-03
It does not matter if the software is open or closed source, is it legal to use it? And are you using it legally?

I do not think that Canonical, the distributors of Ubuntu would put any program in the Ubuntu Software Centre that was illegal to download, install and use.

I am legally using a closed source video adapter driver and I can listen to music and watch videos by using legally provided codecs.

Illegality enters in if I download and play music and video and I install programs that I do not have the legal right to use.

If you are worried about this, then install Ubuntu without ticking the box that tells the install process to install proprietary codecs.

Regards.

---

### Post by jhargis1012 on 2011-08-03
> **grahammechanical said:**
> I do not think that Canonical, the distributors of Ubuntu would put any program in the Ubuntu Software Centre that was illegal to download, install and use.

Unfortunately, there are PLENTY of packages in the Software Center that are illegal to use in the United States. That doesn't mean they are in any way inherently faulty, shady, or illegal, they're just no-go in countries that allow software/algorithm patents (e.g., the US).

---

### Post by jhargis1012 on 2011-08-03
> **PhilGil said:**
> A default Ubuntu install should be legal in the US. I would either avoid installing any additional audio/video packages or [purchase the codecs]("http://shop.canonical.com/product_info.php?products_id=244").

This is what I'm thinking as well.

---

### Post by Megaptera on 2011-08-03
You could look at Linux Mint - based on Ubuntu. In their download choices they include a version...

"A version which fits on a CD, without multimedia support and extra applications. For magazines, companies and distributors in the USA, Japan and countries where the legislation allows patents to apply to software and distribution of restricted technologies may require the acquisition of 3rd party licenses."

[http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php)

---

### Post by PhilGil on 2011-08-03
> **Megaptera said:**
> You could look at Linux Mint - based on Ubuntu. In their download choices they include a version...

Once you strip out the encumbered codecs from Mint the multimedia functionality is much the same as a standard Ubuntu install. It would give the OP some certainty he was compliant, however.

---

### Post by jhargis1012 on 2011-08-03
> **Megaptera said:**
> You could look at Linux Mint - based on Ubuntu. In their download choices they include a version...

"A version which fits on a CD, without multimedia support and extra applications. For magazines, companies and distributors in the USA, Japan and countries where the legislation allows patents to apply to software and distribution of restricted technologies may require the acquisition of 3rd party licenses."

[http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php)

Wow, that is great. Thanks for the link.

---

### Post by Megaptera on 2011-08-04
You're welcome!

---

### Post by Sef on 2011-08-04
moved to community cafe

---

### Post by uRock on 2011-08-04
> **jhargis1012 said:**
> Unfortunately, there are PLENTY of packages in the Software Center that are illegal to use in the United States. That doesn't mean they are in any way inherently faulty, shady, or illegal, they're just no-go in countries that allow software/algorithm patents (e.g., the US).

Which packages are illegal in the states?

---

### Post by Zlatan on 2011-08-04
> **uRock said:**
> Which packages are illegal in the states?

I suppose guys were meaning ubuntu-restricted-extras package

---

### Post by Bandit on 2011-08-04
> **PhilGil said:**
> A default Ubuntu install should be legal in the US. I would either avoid installing any additional audio/video packages or [purchase the codecs]("http://shop.canonical.com/product_info.php?products_id=244").

++ This..

Without Admin rights, your employees will not be able to install anything else that could possibly infringe anything. To the best of my knowledge the base CD is legal globally..  So your safe..

---

### Post by szymon_g on 2011-08-04
> **Bandit said:**
> ++ This..

Without Admin rights, your employees will not be able to install anything else that could possibly infringe anything. To the best of my knowledge the base CD is legal globally..  So your safe..

oh, yes, they are able to "install" software /sure- without touching package manager/- for unzipping /or untaring/ archive with program.
but, frankly speaking- IMO canonical should stop caring about usa market and be more focused on normal countries /i.e. with normal patent system/.

btw, how many users of ubuntu are from US and A? does anyone have any charts with collected data?

---

### Post by SeijiSensei on 2011-08-04
As others have said, don't give your users administrative (root) privileges, so they can't (easily) install additional software.  That's a good idea in a managed office environment regardless of the operating system you're using.  

The packages on the standard CD images are globally legal (as least as far as Canonical can tell), but as others have said, packages found in restricted-extras may not be legally installed in the US and other countries which recognize software patents or enforce copy-protection.  Good examples of these include the MP3 codecs and libdvdcss2 which breaks copy-protection on commercial DVDs.

Another option is to buy licenses for the [gstreamer codecs]("http://shop.canonical.com/product_info.php?products_id=244") from Ubuntu.  I can't tell from a quick scan whether this includes software to play DVDs or not.  It does cover encumbered technologies like MP3 and the Windows codecs.

---

### Post by jhargis1012 on 2011-08-04
Thank you for your replies, everyone. This helps a lot.

---

### Post by jhargis1012 on 2011-08-04
> **SeijiSensei said:**
> packages found in restricted-extras may not be legally installed in the US and other countries which recognize software patents or enforce copy-protection.

Excellent. So, in the software sources settings (under 10.04), unchecking the multiverse sources should keep me in the clear, correct? I assume the main and universe are all safe, and that the restricted device drivers sources are just proprietary, though not illegal.

---

### Post by Bandit on 2011-08-04
> **szymon_g said:**
> oh, yes, they are able to "install" software /sure- without touching package manager/- for unzipping /or untaring/ archive with program.
but, frankly speaking- IMO canonical should stop caring about usa market and be more focused on normal countries /i.e. with normal patent system/.

btw, how many users of ubuntu are from US and A? does anyone have any charts with collected data?

I am not sure how this is possible as to install/copy ANY thing to ANY directory other then the user directory they will require root password. If this is happening, then this is a security flaw that needs to be addressed promptly as it can leave us just as screwed as windows users.

---

### Post by Bandit on 2011-08-04
> **jhargis1012 said:**
> Excellent. So, in the software sources settings (under 10.04), unchecking the multiverse sources should keep me in the clear, correct? I assume the main and universe are all safe, and that the restricted device drivers sources are just proprietary, though not illegal.

True, but honestly I wouldnt sweet it. Unless your copying movies or downloading MP3s from the net no one is going to say anything to you. Unless I am mistaken multiverse-restricted-extras (aka: Software restricted by Copyright or legal issue (multiverse)) should be unchecked by default.
The other that says Propreitory Drivers for devices (restricted) is ok and legal to use, we just have that for those that want ONLY FLOSS. :popcorn:

---

