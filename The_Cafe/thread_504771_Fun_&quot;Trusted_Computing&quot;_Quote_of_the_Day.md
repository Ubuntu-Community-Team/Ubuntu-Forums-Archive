---
title: "Fun &quot;Trusted Computing&quot; Quote of the Day"
date: 2007-07-19
forum: The Cafe
---

### Post by Sporkman on 2007-07-19
> 
**Remote attestation**

Remote attestation allows changes to the user's computer to be detected by authorized parties. That way, software companies can avoid users tampering with their software to circumvent technological protection measures. It works by having the hardware generate a certificate stating what software is currently running. The computer can then present this certificate to a remote party to show that its software hasn't been tampered with.

Remote attestation is usually combined with public-key encryption so that the information sent can only be read by the programs that presented and requested the attestation, *and not by an eavesdropper, such as the computer owner*.

:lol: :roll:

[http://en.wikipedia.org/wiki/Trusted_computing](http://en.wikipedia.org/wiki/Trusted_computing)

---

### Post by Atomic Dog on 2007-07-19
Oxymoron.   ..kinda like jumbo shrimp

---

### Post by tszanon on 2007-07-19
I just can't understand how someone can support such thing...

---

### Post by marco123 on 2007-07-19
LMAO.  - So now you don't own the computer as well as the software on it.  I'm so glad I don't use any of these spyware programs like Windows! :)

---

### Post by Tomosaur on 2007-07-19
Next they'll be telling us that taking part in a phone conversation is eavesdropping!

---

### Post by aks44 on 2007-07-19
> **Tomosaur said:**
> Next they'll be telling us that taking part in a phone conversation is eavesdropping!

And next they'll be telling us that taking part in a conversation is eavesdropping... And as we all know, eavesdropping is a crime (well, when you're not part of the govt, mind you).

---

### Post by SunnyRabbiera on 2007-07-19
I am not fully against TC, in fact in outline its a good idea, heck even DRM is in outline a good idea (somewhat)* but its implementation that matters.
For me if TC was used good it could help in avoiding malicious stuff like viruses, spyware, addware and other junk but knowing the majority of companies these days it will be used for ill use.
hopefully though if TC is made a standard open source apps will not be lost in the sauce, but these days even with the best intentions something can be used for evil.

*for those who might misread me, I am not 100% supporting DRM, in fact the way its been implemented really pisses me off. I can get DRM to a point in wanting to protect an investment, say you made a movie and you want to sell it as opposed to putting it on say youtube, you might want to put something like DRM on your video to protect it, sure you dont mind if someone makes a copy of your movie but you really wish you had that extra cash in your pocket.
But the way the MPAA and the RIAA treats everything you are treated like a criminal as soon as you purchase your copy of a CD or that movie you liked that came out on DVD the other day.
I can understand digital protection, i can understand certain companies wanting to protect their products, but shove DRM down our throats and act like we are going to sell a copy of a movie like we are a bunch of pirates then i draw the line

---

### Post by Arisna on 2007-07-19
Another really excellent way to avoid viruses, malware, etc., is to use GNU/Linux, *BSD, another Free Software operating system, or, to be honest, anything other than Windows.  Unfortunately, TC will prevent anyone from doing that.  It threatens to destroy free computing.

The simple fact is that if I pay for a piece of hardware, I am entitled to complete control over it.  If Microsoft et al. want to ship garbage software with it, that's fine, as long as I can use the software I want instead.

---

### Post by vambo on 2007-07-19
> **Atomic Dog said:**
> Oxymoron.   ..kinda like jumbo shrimp

Totally agree

Trusted computing indeed, it's an oxymoron on a par with Microsoft Works :)

How about a computing oxymoron thread ;)

---

### Post by tszanon on 2007-07-19
> **Sporkman said:**
> [http://en.wikipedia.org/wiki/Trusted_computing](http://en.wikipedia.org/wiki/Trusted_computing)
I just read this in the end of that link:
> The Linux kernel has included trusted computing support since version 2.6.13, and there are several projects to implement trusted computing for Linux. In January 2005, members of Gentoo Linux's "crypto herd" announced their intention of providing support for TC - in particular support for the Trusted Platform Module.[22] There is also a TCG-compliant software stack for Linux named TrouSerS, released under an open source license.
Should I be worried? Does it mean that Linux - specifically Ubuntu - is willing to jump into the abyss? Does it mean that, somewhere in the future, we may be forced to obey the Trusted Computing Group? :confused:

---

### Post by strabes on 2007-07-19
I doubt it, considering the negative opinions about Microsoft held by the linux community, as demonstrated by bug #1.

---

### Post by 23meg on 2007-07-19
[QUOTE=tszanon]Should I be worried? [/QUOTE]

No, because you're using a Free, open source OS and can be 150% sure that your OS isn't doing anything outside your will and control. 

TC as a technology has plenty of potential "non-evil" uses, and if they are to be utilized under "non-evil" terms in the Free software world, the Linux kernel has to provide support for TC hardware. 

If your computer is younger than two years old, your motherboard most likely has a TPM chip. To see whether your kernel provides support for it, type ```
lsmod | grep tpm
```

If it returns results, that means it's recognized, like the rest of your hardware. You can remove the module of your choice with ```
sudo rmmod module_name
``` and to make that permanent, you can choose not to load the module(s) by adding their names to the /etc/modprobe.d/blacklist file.

Note that the fact that the kernel is working with your TPM chip doesn't necessarily mean it's being used; the kernel is merely making the chip available to userspace apps to access, just like it does with all your other hardware. As long as you don't install software that utilizes the hardware, it's just sitting idle. Removing the kernel module just makes sure there's no way any "evil" or "non-evil" app can ever utilize the TPM chip. 

You can also disable the chip in your BIOS configuration in most computers.

---

### Post by tszanon on 2007-07-20
Thanks, 23meg. I'll take a look at this when I get home.

---

### Post by pistcivet on 2007-07-20
I think as Linux users, we are going to love the TPM.
Windows users, not so much love.

If you're bored, and don't mind listening to Leo Laporte and Steve Gibson,
there's a pretty good podcast on the subject. Episode 99 here:
[http://www.grc.com/securitynow.htm](http://www.grc.com/securitynow.htm)

---

### Post by tszanon on 2007-07-20
> **pistcivet said:**
> I think as Linux users, we are going to love the TPM.
Windows users, not so much love.

If you're bored, and don't mind listening to Leo Laporte and Steve Gibson,
there's a pretty good podcast on the subject. Episode 99 here:
[http://www.grc.com/securitynow.htm](http://www.grc.com/securitynow.htm)
Instead I read the transcription. So, the Trusted Platform Module is something designed with a good purpose, but, as most things, can be used for the worse. It depends only on who YOU trust, as it has always been.

Thanks for the text. But, until I have a reason, I'm not planning to enabling my TPM anytime soon (if I have one). :)

---

### Post by MetalOverlord on 2007-07-20
I've been following this for a bit now and the more I read about it, the more I don't like it.

It seems like there's a not-so-hidden agenda underneath the trappings of security. I keep reading terms like "may reduce identity theft" or "might reduce damage from malware". May or might does not = will.

The whole thing seems geared more towards detecting changes in software/hardware to protect licensing and copyrights. If I create a Word document, only Word can read the document. I can't switch to another program and convert it. Essentially, any and all content created by the licensee of the program becomes the property of the licensor since they have complete control over it and it can't be used by any other product without the express written consent of the licensor.

I also don't like the idea that as the purchaser of hardware and licensee of software that I am "untrusted" and that trustworthiness is determined by some anonymous third party I don't know about. TC seems more about me being forced to "trust" these third parties good intentions rather than I am being provided with a "trustworthy" product.

While there are probably some good aspects to this, it seems like there's more potential downside than upside.

---

### Post by kamaboko on 2007-07-21
> **MetalOverlord said:**
> 
The whole thing seems geared more towards detecting changes in software/hardware to protect licensing and copyrights. _If I create a Word document, only Word can read the document_. I can't switch to another program and convert it. Essentially, any and all content created by the licensee of the program becomes the property of the licensor since they have complete control over it and it can't be used by any other product without the express written consent of the licensor.


Now I'm truly baffled.  How is it then that I have word docs created in Office 2007, Office 2003, Office 2000 and Office 97 that can be read in Mac and Linux platforms?

---

### Post by aks44 on 2007-07-21
> **kamaboko said:**
> Now I'm truly baffled.  How is it then that I have word docs created in Office 2007, Office 2003, Office 2000 and Office 97 that can be read in Mac and Linux platforms?

Because these don't use TC yet. MetalOverlord's point was about a TC-enabled Word version (or any other TC-enabled software for the matter).

---

### Post by cprofitt on 2007-07-23
> **aks44 said:**
> Because these don't use TC yet. MetalOverlord's point was about a TC-enabled Word version (or any other TC-enabled software for the matter).

I don't think that is the purpose.

The purpose behind TC is two things:

1)  Only the intended recipient or owner can open documents

and

2) There is a way for a recipient to verify the sender as authentic

and this is done in hardware not software.

---

### Post by jiminycricket on 2007-07-23
I think Vista already has this.  "Network Application Protection"...or something similarly-named.

---

