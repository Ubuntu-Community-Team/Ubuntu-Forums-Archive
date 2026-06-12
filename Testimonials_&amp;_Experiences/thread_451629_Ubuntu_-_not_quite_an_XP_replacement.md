---
title: "Ubuntu - not quite an XP replacement"
date: 2007-05-22
forum: Testimonials &amp; Experiences
---

### Post by raves71 on 2007-05-22
I installed Ubuntu on my laptop with the hope I could replace Windows XP, not because theirs anything wrong with Windows XP, just mainly as a bit of a test to see if it was up to the job.

 Now I'm no linux expert, in fact I work doing Technical support for windows based Technical Support for a Citrix Partner so I spend most of my life on windows servers and XP workstations.

 In the most part Ubuntu has satisfied my needs

[LIST]
[*]Most of my laptops hardware worked out of the box apart from my Broadcom wireless card which only took a couple of minutes to set up after reading an article someone had kindly posted on these forums. a plus for ubuntu as when I installed windows XP on the same laptop I had to find, download and install the drivers for most of the components.

[*]The most important thing for me is that I could connect to the resources on my corperate network, again everything was ok there.

[*] It was even able to join AD and recieve mails form my Exchange server after looking through a few articles, didnt take very long and was quite effective
[/LIST]
 
 The cons are, as Id imagine they might have been, that I cant completely rely on Ubuntu to do everything I need it to. While this isnt really the fault of the OS, it's the fault of the software vendors, unfortunately these are the things that have made this OS useless for me on a day to day basis

 So far I'v ebeen unable to get the following working:

[LIST]
[*]Citrix Access Gateway - net6VPN, although this comes with a linux client I've not been able to get this working - probably my fault but it still doesnt work.

[*] Streaming DivX videos from websites such as TV-links.co.uk, while videos from stage6 work they dont seem to when linked form another website.

[*] Citrix program neighbourhood, This works when I install the windows client using WINE but only for custom ICA connections. Not Application sets

[*]I cannot find an email client that supports public folders in exchange

[*] GPOs are not applied when you log into Ubuntu using an AD account - but in all honesty I never thought they would be.

[*] GoToAssist wont work, theirs no linux client and even WINE hasnt helped - yet another problem caused by the narrow mindedness of Citrix
[/LIST]

 This is not to say I wouldnt recommend ubuntu, I really would for a home user but it's not quite ready for the workplace yet I dont think.

 Anyway my experiences, I like it, just cant quite get it to do everything I need it to.

---

### Post by codesplice on 2007-05-22
Hi **raves71**,
I can't help with most of those issues, though I can testify that I just viewed a streaming video from tv-links.co.uk (great site!) that worked perfectly.  

I just followed the steps at [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) to get all my multimedia needs taken care of.

Cheers

---

### Post by lazyart on 2007-05-22
Is there a reason why you didnt use the Citrix Linux client?

What you have are compelling reasons to stay with Windows.

However there are other ways of publishing apps to a linux box-- 2X Application Server stands out in my mind.  I personally use rdesktop as I have a couple apps that only run from Windows, so I host them on my existing Domain Controller and bring them in seamlessly that way.  But to use that requires a commitment from your IT dept and I wouldn't imagine they would move their app publishing schema for a single linux user.  Now if you could convince them that they would save a ton of money on licensing fees for OS and applications like Office (and even Exchange) and convert the whole office then you're on to something.

Thanks for peeking though.  Maybe it doesn't work for you but you gave it an honest go. :)

---

### Post by raves71 on 2007-05-22
thanks for your replies.


 codesplice - I've just given your suggestions on the TV links website a go but unfortunately I have been unsuccessful - it is only the videos that are streamed via Divx stage 6 that are effected by this issue I can run all other formats (java and flash).

 However I've not given up and will continue to try anything I can to see if I can get this working :)

 lazyart - I have used the linux ICA client but from what I can see version 10 only supplies you with the Web client for Web Interface and PNAgent, not program neighbourhood :( - although it is entirely possible I've just missed it!

Unfortunately as I work in Citrix technical support I need ot be able to use Citrix on my local machine. RDP is working fine from Ubuntu which is a bonus as technically all I would need is an XP machine on the network to connect to.

 I Will however check out 2X Application Server, but I doubt I'll be able to persuade us as a Citrix reseller and partner to take the plunge :)

---

### Post by Tomosaur on 2007-05-22
> **raves71 said:**
> I installed Ubuntu on my laptop with the hope I could replace Windows XP, not because theirs anything wrong with Windows XP, just mainly as a bit of a test to see if it was up to the job.

 Now I'm no linux expert, in fact I work doing Technical support for windows based Technical Support for a Citrix Partner so I spend most of my life on windows servers and XP workstations.

 In the most part Ubuntu has satisfied my needs

[LIST]
[*]Most of my laptops hardware worked out of the box apart from my Broadcom wireless card which only took a couple of minutes to set up after reading an article someone had kindly posted on these forums. a plus for ubuntu as when I installed windows XP on the same laptop I had to find, download and install the drivers for most of the components.

[*]The most important thing for me is that I could connect to the resources on my corperate network, again everything was ok there.

[*] It was even able to join AD and recieve mails form my Exchange server after looking through a few articles, didnt take very long and was quite effective
[/LIST]
 
 The cons are, as Id imagine they might have been, that I cant completely rely on Ubuntu to do everything I need it to. While this isnt really the fault of the OS, it's the fault of the software vendors, unfortunately these are the things that have made this OS useless for me on a day to day basis

 So far I'v ebeen unable to get the following working:

[LIST]
[*]Citrix Access Gateway - net6VPN, although this comes with a linux client I've not been able to get this working - probably my fault but it still doesnt work.

[*] Streaming DivX videos from websites such as TV-links.co.uk, while videos from stage6 work they dont seem to when linked form another website.

[*] Citrix program neighbourhood, This works when I install the windows client using WINE but only for custom ICA connections. Not Application sets

[*]I cannot find an email client that supports public folders in exchange

[*] GPOs are not applied when you log into Ubuntu using an AD account - but in all honesty I never thought they would be.

[*] GoToAssist wont work, theirs no linux client and even WINE hasnt helped - yet another problem caused by the narrow mindedness of Citrix
[/LIST]

 This is not to say I wouldnt recommend ubuntu, I really would for a home user but it's not quite ready for the workplace yet I dont think.

 Anyway my experiences, I like it, just cant quite get it to do everything I need it to.

If you approach it as an XP replacement, then it will never suit your needs. It's an **alternative**. If Windows suits you, then use Windows. If Linux suits you, then use Linux. There are some things which either aren't available on Linux, and there are some things which aren't available on Windows. It really isn't that great an idea to use Ubuntu (or any other Linux distro) with a view to making everything you use on Windows work on it. You really just need to find alternatives to what you would normally use. If your only possible solution in getting your 'must have' apps to work is to use Wine - then really, you should just use Windows.

---

### Post by raves71 on 2007-05-22
Tomosaur   - Thanks for your input and I've discovered that you are right, it is an alternative and I shouldn't expect it to do everything windows XP does, especially when the applications I expect to be able to use have absolutely no Linux support.

 My aim wasn't to knock Ubuntu at all, I just wanted to explain my findings during my ubuntu experience.

 As for only being able to use wine to use my must have windows applications, this is the only way I've found so far of doing the job. Any other suggestions are greatly appreciated,

 All in all I would suggest that you are correct, I should be using Windows XP, but life's boring when you always do what you should ;)

---

### Post by Kobalt on 2007-05-22
raves71 : correct me if I'm wrong, but it doesn't seem to me that you posted a lot in order to get adapted alternatives. I'm sure if you do you'll find solutions :)

---

