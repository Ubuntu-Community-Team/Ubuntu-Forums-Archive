---
title: "Fritz chip?"
date: 2007-02-22
forum: System76 Support
---

### Post by oswaldkelso on 2007-02-22
hi I'm looking for a laptop and was wondering if the system 76 lappys were "fritz chip free" thanks

---

### Post by crichell on 2007-02-22
"fritz chip" - what is it?

---

### Post by serag on 2007-02-22
[http://en.wikipedia.org/wiki/Fritz-chip](http://en.wikipedia.org/wiki/Fritz-chip)

---

### Post by AusIV4 on 2007-02-22
I may be wrong, but I was under the impression that fritz chips weren't very widespread yet, and you'd probably know if you had one.

---

### Post by crichell on 2007-02-22
I hadn't heard TPM chips called that.  The Serval has one that can be disabled in the BIOS.  I'm not sure about our other laptops.

---

### Post by 23meg on 2007-02-23
TC needs both hardware and software components to function, thus as long as you're using an OS that doesn't implement it in any form, as well as not using any userspace apps that make use of it, there's no reason to fear the presence of a TPM chip. 

```
lsmod | grep tpm
```will list any existing TPM-related modules that are loaded, which you can then remove and blacklist.

---

### Post by airtonix on 2007-02-23
as the wiki may have divulvged...its called the fritz chip due to the zealous soddomite who proposed it.

Hi there Senator Fritz....heres a present from georgy porgey. 
ho hum...who got a attache case of green bills for the summer solstice festival?  
whats that you've an idea for the future of computing....ohh yeah that sounds dandy...more lockdown on the society is always good for our trust funds. ahem

---

### Post by oswaldkelso on 2007-02-23
> **23meg said:**
> TC needs both hardware and software components to function, thus as long as you're using an OS that doesn't implement it in any form, as well as not using any userspace apps that make use of it, there's no reason to fear the presence of a TPM chip. 

```
lsmod | grep tpm
```will list any existing TPM-related modules that are loaded, which you can then remove and blacklist.

Thanks for that info see ing the tcp members [list ]("https://www.trustedcomputinggroup.org/about/members/") I think it will be getting harder and harder to get a fritz chip free laptop. I guess my main concern is someone else switching the dam thing on!!  via attachments, firmware updates, etc and me not  knowing.  

It would be realy nice if we could have some "free hardware" as well as "free software" to run on it. I just worry that that the next step will be lock out via the hardware, and in the not to distant future  once the chip is activated you will not be able to deactivate it.

If as looks likely and the chip is enbedded in graphics card and  other components swopping parts and building a custom pc from OLD PARTS may be a thing of the past. This would suit MS and hardware manufacturersors alike. 

As for System 76. I think if any of their laptops do have the chip to turn the chip off in the bios before sale, with auto warning message if its going to be activated would be a real nice move and a good selling point.

Thanks

---

### Post by fmarier on 2007-02-23
```
lsmod | grep tpm
```

I can confirm that none of these modules are loaded on my Darter laptop.

---

### Post by 23meg on 2007-02-23
> **oswaldkelso said:**
> Thanks for that info see ing the tcp members [list ]("https://www.trustedcomputinggroup.org/about/members/") I think it will be getting harder and harder to get a fritz chip free laptop. I guess my main concern is someone else switching the dam thing on!!  via attachments, firmware updates, etc and me not  knowing.  Just about every new laptop and motherboard will have TPM chips from now on. There's not much that can be done about it, but there's not much to worry about either; my only concern with its presence in my computer is that it sits idle doing nothing, and it's part of what I've paid for, no matter how small. That said, there are non-evil uses for a TPM chip such as personal encryption as well, and it's good to know the Linux kernel *can* utilize it. 

The possibility of someone else switching the TPM chip on when you're running an open source OS that you're sure isn't utilizing it with its kernel is zero. That's the huge advantage of using (and especially connecting to the net with) an open source OS regarding privacy and basic rights: you can be 100% sure that the OS isn't talking to the TPM chip, and if it isn't, nothing else in userspace can. With a closed source proprietary OS, you can never be sure; there's always the chance that the OS and its proprietor will spy on you without you knowing.

Practical, straight edge solution: even if you have to use a closed source OS such as Windows on a computer that has a TPM chip in it, simply don't connect to the net with it. Unplug the ethernet cable, turn the wireless kill switch off. 

> **oswaldkelso said:**
> 
It would be realy nice if we could have some "free hardware" as well as "free software" to run on it. I just worry that that the next step will be lock out via the hardware, and in the not to distant future  once the chip is activated you will not be able to deactivate it.That's only possible with an OS that actually utilizes it, such as Windows Vista. Just opt out of using proprietary software and you're free.

> **oswaldkelso said:**
> If as looks likely and the chip is enbedded in graphics card and  other components swopping parts and building a custom pc from OLD PARTS may be a thing of the past. This would suit MS and hardware manufacturersors alike. They've tried similar schemes before; the new Pentium chips do have TC components but I haven't heard about graphics chips having them; can you cite a source for that information? Again, as long as the components in the individual hardware aren't utilized, you have nothing to worry about. 

> **oswaldkelso said:**
> 
As for System 76. I think if any of their laptops do have the chip to turn the chip off in the bios before sale, with auto warning message if its going to be activated would be a real nice move and a good selling point.

I don't think they can practically do that, but it would be nice of them to provide a brochure with information regarding the TPM chip, what it works for, why it can be nasty, and how not to allow it to be utilized.

crichell, would you be interested in shipping something like that with the System76 computers that have TPM chips? I may be able to assist with its creation if needed.

---

### Post by oswaldkelso on 2007-02-24
> **23meg said:**
> Just about every new laptop and motherboard will have TPM chips from now on. There's not much that can be done about it, but there's not much to worry about either;

I fear you may be [right ]("http://www.tonymcfadden.net/tpmvendors.html#other")but **I** ultimately re vender lockin. As for not much to worry about well each to his own, but I do find it rather scary. 

> **23meg said:**
> my only concern with its presence in my computer is that it sits idle doing nothing, and it's part of what I've paid for, no matter how small. 

I agree

> **23meg said:**
> That said, there are non-evil uses for a TPM chip such as personal encryption as well, and it's good to know the Linux kernel *can* utilize it.

I agree it's not the tool it's how it's used. You can use a gun to defend your kids from robbers, but it's usually the robbers that want guns and fire them in anger. 

> **23meg said:**
> The possibility of someone else switching the TPM chip on when you're running an open source OS that you're sure isn't utilizing it with its kernel is zero.

I hope your right. but it's early days.

 > **23meg said:**
> That's the huge advantage of using (and especially connecting to the net with) an open source OS regarding privacy and basic rights: you can be 100% sure that the OS isn't talking to the TPM chip, and if it isn't, nothing else in userspace can.

I can see the day when the internet wont be free and only certified computers can see content. In short lock in/out. I do hope I'm wrong but fear the days of a free internet maybe numbered.

 > **23meg said:**
> With a closed source proprietary OS, you can never be sure; there's always the chance that the OS and its proprietor will spy on you without you knowing.

Agreed.

> **23meg said:**
> Practical, straight edge solution: even if you have to use a closed source OS such as Windows on a computer that has a TPM chip in it, simply don't connect to the net with it. Unplug the ethernet cable, turn the wireless kill switch off. 

You mean lock in/out :)


> **23meg said:**
> That's only possible with an OS that actually utilizes it, such as Windows Vista. Just opt out of using proprietary software and you're free.

I don't think its the using proprietary software in it's self that will require lockin more a case of you will be required to provied authentication to access adata.

> **23meg said:**
> They've tried similar schemes before; the new Pentium chips do have TC components but I haven't heard about graphics chips having them; can you cite a source for that information? 

I may have been wrong re the graphic cards I thought the referance was on the [tcg]("https://www.trustedcomputinggroup.org/home") web sit but have not been able to find it again. I may have confused this which I think ties in with the tpm on the board?

RADEON XPRESS 200 Crossfire Edition
•_ATI's first discrete PCI Express chipset for AMD K8 platforms
•_Offers flexible platform design options for the mainstream and enthusiast markets
•_Pin and BIOS compatible with onboard graphics platform

I do see the seagate have tpm hard [drives]("http://www.anandtech.com/tradeshows/showdoc.aspx?i=2507&p=9")

My worry here is say in 3 years time you buy a secondhand [dell laptop]("http://www1.euro.dell.com/content/products/productdetails.aspx/precn_m65?c=uk&cs=ukbsdt1&l=en&s=bsd&~section=specs#tabtop") on ebay. Will you be able to install Linux ? I hope so. 


> **23meg said:**
> I don't think they can practically do that, but it would be nice of them to provide a brochure with information regarding the TPM chip, what it works for, why it can be nasty, and how not to allow it to be utilized.

Good idea.

> **23meg said:**
> crichell, would you be interested in shipping something like that with the System76 computers that have TPM chips? I may be able to assist with its creation if needed.

Great news I know I might sound I bit paranoid, but I do feel a lot of these security features are in the commercial interest and not the publice interest.

Heres a few links to mull over:) 
[eff]("http://www.eff.org/Infrastructure/trusted_computing/20031001_tc.php")[URL="http://daringfireball.net/2005/08/trusted#fn1-2005-08-05"]
daring fireball[/URL] 
[wiki]("http://en.wikipedia.org/wiki/Trusted_computing#Opponents_of_trusted_computing")
[URL="http://www.lafkon.net/tc/"]video

[/URL]Thanks

---

### Post by 23meg on 2007-02-24
> **oswaldkelso]I hope your right. but it's early days.[/QUOTE]As long as you have no TPM related modules loaded, and no TPM support compiled in the kernel, it's technically impossible to utilize the TPM chip, that's the end of the story. As long as *you're* in control of what your kernel can and cannot talk to, there's no possibility of a malicious userspace app getting your TPM chip to do nasty things. 

[QUOTE=oswaldkelso]I can see the day when the internet wont be free and only certified computers can see content. In short lock in/out. I do hope I'm wrong but fear the days of a free internet maybe numbered.[/QUOTE]

That has more to do with content and service providers adopting TC. I'm not losing sleep over the possibility of not being able to connect to some proprietary services (such as music stores etc.) said:**
> I do see the seagate have tpm hard drives

That's a good thing, as long as you can utilize the TPM chip and the unit's TC components to work along with it in an open source environment. I'd never trust it with a proprietary OS though, hence the thin line: the technology is quite useful if *you* are in control of what it's doing (in an open environment), and totally horrific if the software proprietor is or can be (in a proprietary environment).
 
[QUOTE=oswaldkelso]Great news I know I might sound I bit paranoid, but I do feel a lot of these security features are in the commercial interest and not the publice interest.[/QUOTE]

They are completely in the commercial corporate interest. But as long as you don't use a proprietary OS and opt out of commercial services that utilize TC, you're safe.

---

