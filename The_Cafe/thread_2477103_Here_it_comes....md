---
title: "Here it comes..."
date: 2022-07-14
forum: The Cafe
---

### Post by Shibblet on 2022-07-14
Here it comes...

[https://www.omglinux.com/lenovos-new-amd-thinkpads-only-boot-windows-by-default/]("https://www.omglinux.com/lenovos-new-amd-thinkpads-only-boot-windows-by-default/")

---

### Post by Frogs Hair on 2022-07-15
Perhaps Linux laptops will start getting more attention if this becomes more prevalent. I don't see a problem with TPM +Windows as long as the buyer is aware of it. This would be a big disappointment and headache  if not.

---

### Post by #&amp;thj^% on 2022-07-15
I warned everyone, a month or so back.
This is my last year testing for Lenovo. :P
I'll just keep the ones that work ATT (at this time)
I have to find that link oldfred posted about testing the Thinkpad Z13
I'm telling you MS is running hard at Linux. But we will prevail. :)

---

### Post by Bashing-om on 2022-07-15
Well - 

Not all bad :(

Michael Larabel in testing advises that there is a bios switch to enable us 3rd parties :P
[https://www.phoronix.com/scan.php?page=article&item=rembrandt-linux-boot&num=1](https://www.phoronix.com/scan.php?page=article&item=rembrandt-linux-boot&num=1)

-don't shut us out-

---

### Post by #&amp;thj^% on 2022-07-16
Thanks B-om, i was waiting to hear about Michael's findings.
Ok, so now on this model at least and more tested/information made clear by Michael.
> This is the part that wasn't made clear in Garrett's blog post -- the 3rd party certificate can be easily enabled. But I do agree with his assessment that it's a stupid mandate to now have to disable this certificate by default and doesn't seem to be based on firm security reasons. Particularly around the lack of messaging over this change in default behavior it leads to a poor user experience and customers may just assume Linux is having technical troubles in booting on new laptops or other troubles.
What added security dose it add>>> little to none. But the contention here is: this shouldn&#8217;t be necessary. Lenovo is actively making it hard to boot anything other than Windows for &#8230;no apparent reason or detailed information.

---

### Post by grahammechanical on 2022-07-16
So, it is buyer beware! Don't buy AMD. Buy Intel. At least for the moment. At least make sure the third party certificates can be enabled in the UEFI.

Regards

---

### Post by QIII on 2022-07-17
From the article, it seems that the problem is with the Pluton coprocessor, not the AMD processor.  AMD is a very long-standing member of the Linux Foundation.

---

### Post by mIk3_08 on 2022-07-17
> **Shibblet said:**
> Here it comes...
[https://www.omglinux.com/lenovos-new-amd-thinkpads-only-boot-windows-by-default/](https://www.omglinux.com/lenovos-new-amd-thinkpads-only-boot-windows-by-default/)
Lenovo ThinkPad X13 Gen3 Laptop can still run Linux Ubuntu. :-) Happy to say that we can still use Linux Ubuntu on new Lenovo laptop. Regards and cheers.

---

### Post by grahammechanical on 2022-07-17
The issue is indeed the Pluton co-processors that Microsoft is insisting be included as part of the CPU. Added to this is the policy of Microsoft that Windows 11 take ownership of what the Pluton co-processors are able to do.

> We hadn't heard much of Microsoft's Pluton since 2020 but integration  into the silicon obviously takes a while and now we find out AMD is  ready to introduce it with their forthcoming Ryzen 6000 series  processors. AMD's CES 2022 keynote is later today but the CES website  has exposed early that the Ryzen 6000 series mobile processors will  indeed have Microsoft Pluton

[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Ryzen-6000-Pluton](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Ryzen-6000-Pluton)

Intel's 12th generation Alder Lake processors will not include Microsoft's Pluton security

[https://www.theregister.com/2022/03/02/microsoft_pluton_chip/](https://www.theregister.com/2022/03/02/microsoft_pluton_chip/)

The key question in my opinion is: does the UEFI allow Pluton to be disabled? If not then don't be surprised if you cannot dual boot Linux with Windows 11 and onwards. You may find that you cannot even run a live session.

Regards

---

### Post by Shibblet on 2022-07-18
> **Bashing-om said:**
> Well - 

Not all bad :(

Michael Larabel in testing advises that there is a bios switch to enable us 3rd parties :P
[https://www.phoronix.com/scan.php?page=article&item=rembrandt-linux-boot&num=1](https://www.phoronix.com/scan.php?page=article&item=rembrandt-linux-boot&num=1)

-don't shut us out-

I both like and dislike that.
I like the fact that you can flash the BIOS to fix the PC and then run Linux.
I dislike that, because it's one extra step in the process that may cause new Linux users to back-away.  Unless you flash your BIOS, this essentially removes the "Try it out" Live-Session feature available from booting off of a USB Drive.


> **grahammechanical said:**
> The issue is indeed the Pluton co-processors that Microsoft is insisting be included as part of the CPU. Added to this is the policy of Microsoft that Windows 11 take ownership of what the Pluton co-processors are able to do.

[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Ryzen-6000-Pluton](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Ryzen-6000-Pluton)

Intel's 12th generation Alder Lake processors will not include Microsoft's Pluton security

[https://www.theregister.com/2022/03/02/microsoft_pluton_chip/](https://www.theregister.com/2022/03/02/microsoft_pluton_chip/)

The key question in my opinion is: does the UEFI allow Pluton to be disabled? If not then don't be surprised if you cannot dual boot Linux with Windows 11 and onwards. You may find that you cannot even run a live session.

Regards

Even if you can disable Pluton... If you dual-noot, you may run into some "other" issues...  i.e. Secure Boot, TPM 2, etc.
[https://ubuntuforums.org/showthread.php?t=2476355]("https://ubuntuforums.org/showthread.php?t=2476355")

What's to keep Microsoft from turning it on remotely?

---

### Post by schwim-dandy on 2022-07-18
> **1fallen said:**
> ATT (at this time)

This is the first time I have seen someone make an abbreviation take more time than just typing out what it abbreviated :)

On to the topic, the optimist in me hopes that perhaps this push will result in us seeing more linuxcentric laptop vendors as well as a larger interest in already existing linux laptop sellers but the realist in me suspects not.

---

### Post by grahammechanical on 2022-07-18
Does anyone want to help this person?

[https://ubuntuforums.org/showthread.php?t=2477222](https://ubuntuforums.org/showthread.php?t=2477222)

As @shibblet said: "Here it comes."

Regards

---

### Post by ajgreeny on 2022-07-18
It looks as if that problem is now solved and nothing to do with proton

---

### Post by Shibblet on 2022-07-18
> **grahammechanical said:**
> Does anyone want to help this person?

[https://ubuntuforums.org/showthread.php?t=2477222](https://ubuntuforums.org/showthread.php?t=2477222)

As @shibblet said: "Here it comes."

Regards

Are you turning me into a "Prophet," or "Harbinger?"  :lolflag:

---

### Post by grahammechanical on 2022-07-18
I am the one who cried wolf! :) Next time the first thing I will ask will be "Does Windows recognize that the USB stick is plugged in to the USB port".

Regards

---

### Post by TheFu on 2022-07-18
Virtual machines ... 


just sayin'.

---

### Post by jamesbrown2 on 2022-08-04
I am not any kind of fan of Windows, but the logic is faulty:  If you allow other boot types, you DO increase the security-risk vectors of a system.  Period.

---

### Post by grahammechanical on 2022-08-04
Please do not ignore history. For many decades the biggest security threat to computers was a Microsoft operating system. Many businesses delayed upgrading to a newer version of Windows because it meant buying newer, more powerful hardware. So, these businesses (including government departments) continued using a version of Windows that had security vulnerabilities and they continued using it even when Microsoft stopped supplying security updates. When you see in the news media a report of ransomware locking a government department's computers ask what operating system are those computers using.

Regards

---

### Post by TheFu on 2022-08-04
Normal people don't realize this, but govts and huge businesses usually pay MSFT for support up to 10 yrs AFTER they've pulled support from the rest of us. They get security fixes during that time. No business computers running Windows will last 10 (MORE) years. It just doesn't happen.

I've had to replace systems that were dead end in a previous day job. These were not running any OS touched by MSFT. They were typically 1-off systems providing specific services to customers for 20-40 yrs. This was in a regulated business and getting govt approval to pull the service wasn't possible, but when hardware failed and couldn't be replaced at-any-price, then we could drop it to those clients only.  Over a decade, I think we lost about 60% of the systems because no used hardware was available anywhere. I spent days searching around the world for replacements and spoke to at least 50 used equipment resellers around the world.  Imagine trying to find a niche computer from 1988 to run a critical service today - plus the systems ran in very harsh locations with no temperature controls.  Anyway, I silently begged for systems to fail quicker, since migrating the clients to newer, better, solutions would actually help everyone - them and us.  We were charging them at least 3x what a current generation solution would cost too, but few were interesting in any change.  They had the same belief I often have - if it ain't broke, don't touch it.

TPM is there to fix something that most Linux people don't consider broken. It has good qualities, but it isn't completely pain free for everyone. The same could be said about UEFI.  Only 1 of my systems uses UEFI. All the rest are using "legacy BIOS" for booting.  It ain't broke, so I'm not fixing it.

---

### Post by Shibblet on 2022-08-05
> **TheFu said:**
> Normal people don't realize this, but govts and huge businesses usually pay MSFT for support up to 10 yrs AFTER they've pulled support from the rest of us. They get security fixes during that time. No business computers running Windows will last 10 (MORE) years. It just doesn't happen.

I've had to replace systems that were dead end in a previous day job. These were not running any OS touched by MSFT. They were typically 1-off systems providing specific services to customers for 20-40 yrs. This was in a regulated business and getting govt approval to pull the service wasn't possible, but when hardware failed and couldn't be replaced at-any-price, then we could drop it to those clients only.  Over a decade, I think we lost about 60% of the systems because no used hardware was available anywhere. I spent days searching around the world for replacements and spoke to at least 50 used equipment resellers around the world.  Imagine trying to find a niche computer from 1988 to run a critical service today - plus the systems ran in very harsh locations with no temperature controls.  Anyway, I silently begged for systems to fail quicker, since migrating the clients to newer, better, solutions would actually help everyone - them and us.  We were charging them at least 3x what a current generation solution would cost too, but few were interesting in any change.  They had the same belief I often have - if it ain't broke, don't touch it.

TPM is there to fix something that most Linux people don't consider broken. It has good qualities, but it isn't completely pain free for everyone. The same could be said about UEFI.  Only 1 of my systems uses UEFI. All the rest are using "legacy BIOS" for booting.  It ain't broke, so I'm not fixing it.

I understand the need for security.  I also understand that computers need to be upgraded.

It's not about the needs, it's about the ways they are going about it.  Why does TPM need to be a requirement, but only for Microsoft?  Why couldn't they have come up with a less invasive way of adding security?  They don't get to hold all the keys!

Now with Pluton, they are not only holding all the keys, but also setting all the locks!

Really what this all comes down to is simple...  "Do you trust Microsoft to handle your computers security?"

---

### Post by ajgreeny on 2022-08-06
It sounds just like the monopolistic actions of business that are mainly banned in the European Union and also in the UK in many cases.
Remember what happened a long time ago when Microsoft tried to make Internet Explorer impossible to get rid of!

---

### Post by TheFu on 2022-08-06
TPM is mandated on all chromebooks too and has been since at least 2011.  That's why breaking the warranty is required to run any other OS on chromebook hardware. It is also why some chromebooks/chromeboxes cannot run any other OS.

---

### Post by #&amp;thj^% on 2022-08-06
> **Shibblet said:**
> 
Really what this all comes down to is simple...  "Do you trust Microsoft to handle your computers security?"

Oh, Oh, Oh. pick me, pick me. Absolutely Not!
The only thing I trust is a learned wisdom, and Linux is the biggest part of that wisdom.
I can go over the top here, but i won't.
We all use our systems differently, I get that and lets face it the majority of people run MS it's just easier for them to lay trust with MS.
Linux is an open-source project and you can always look at the source code of any Linux distribution at any time. Some people might not care about this or take this into consideration but for some people, it is a huge deal. (Like Me)

With that said do I completely trust Linux>>>No I trust in what I've learned period.
The security of Linux is far better than Windows.  Although Linux is not as vulnerable as Windows but it is vulnerable to some extent, however, it is more secure than Windows.
To Me this TPM thing is just another approach to FUD.
If you are a Old Timer,  you have learned by now that security mostly rests on the user.

---

### Post by mIk3_08 on 2022-08-07
> **Shibblet said:**
>  "Do you trust Microsoft to handle your computers security?"
hahahaha  :-D They can't even handle their own viruses. Why should you trust them  the (MS Windows) while they can't be trusted at all. Though not all of  them but generally, you can't trust them. Here in our place many here  uses MS Windows even in businesses but sad to say many of them  encountered inconvenience using their machine. If you are about to  handle security you have to be solid/static. Solid/Static to your rules  because you cannot please everyone as well as you cannot control  everybody. Even if you are doing good to others somebody has to say not  good things to you but it doesn't mean that you have to response to  their non-sense. You have to think twice before you decide. Regards and  cheers.

---

