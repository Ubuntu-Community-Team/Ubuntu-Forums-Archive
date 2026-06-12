---
title: "Is Ubuntu/Lubuntu more secure than Linux Mint?"
date: 2017-08-02
forum: Ubuntu, Linux and OS Chat
---

### Post by AbleTassie on 2017-08-02
I am wondering because I know people who are using Mint and I came across the 2016 article below (it describes a hacking episode of the Mint website) that seems to indicate that Mint is not all that secure. I am thinking of telling the people I know who use Mint to try Lubuntu instead.

Why the Linux Mint hack is an indicator of a larger problem
[URL="http://www.techrepublic.com/article/why-the-linux-mint-hack-is-an-indicator-of-a-larger-problem/"]
http://www.techrepublic.com/article/why-the-linux-mint-hack-is-an-indicator-of-a-larger-problem/[/URL]

Does anybody have any comments?

I notice that Mint verifies it's downloaded iso images with both SHA256SUMs and GPG signature verification, see [https://linuxmint.com/verify.php](https://linuxmint.com/verify.php) . In downloading Lubuntu iso files, I don't  remember the GPG signature being stressed. Is this because of the 2016 hack described above?

Or is it just that I am not aware that the GPG signature is frequently used to verify a downloaded Ubuntu/Lubuntu iso file? 

Thanks,

Able[URL="http://www.techrepublic.com/article/why-the-linux-mint-hack-is-an-indicator-of-a-larger-problem/"]


[/URL]

---

### Post by mastablasta on 2017-08-02
if you look at the article and this part:
> [COLOR=#333333][FONT=&quot]The problem with this scenario is that the fault lies with practically everyone. The impetus for the creation of Cinnamon, and the rise of Mint's popularity, is due to the poor reception of early versions of GNOME 3, KDE 5, and Ubuntu Unity. Generally speaking, these were pushed to end-users well before they were ready for primetime, thereby driving users away.[/FONT][/COLOR]

the problem is always the small team size. but even bigger teams are not imune to hacking and security holes. it's the nature of opensource i guess. look at the OpenSSH vulnerability for example. reported long ago, pathced only very recently.

Ubuntu forums also got hacked, but security was stepped up since then. i am sure mint also increased it.

---

### Post by Habitual on 2017-08-02
What does a Wordpress file upload hack have to do with the Mint Desktop?

I was in the same camp, thinking my beloved OS was somehow "less than".
Not even an issue for me any more.

Mint switched to sha256sum hashed because md5sum hash routine previous to this incident, has been shown it can be manipulated.

Why? Likely cause of the method the "hacker" used to try and deceive, (he changed published md5sums)
Just sayin'

---

### Post by TheFu on 2017-08-02
Please use std fonts.

I don't know anything about how Mint is created or maintained except that they start with Ubuntu as the base.

As for using gpg signatures.  That is extremely common.  Every debian package has a gpg signature attached that is part of the pre-installation validation. [https://wiki.debian.org/SecureApt](https://wiki.debian.org/SecureApt) will explain.

So it appears you just are not aware.

---

### Post by vocx on 2017-08-02
> **AbleTassie said:**
> I am wondering because I know people who are using Mint and I came across the 2016 article below (it describes a hacking episode of the Mint website) that seems to indicate that Mint is not all that secure. I am thinking of telling the people I know who use Mint to try Lubuntu instead.
[http://www.techrepublic.com/article/why-the-linux-mint-hack-is-an-indicator-of-a-larger-problem/](http://www.techrepublic.com/article/why-the-linux-mint-hack-is-an-indicator-of-a-larger-problem/)
...
Or is it just that I am not aware that the GPG signature is frequently used to verify a downloaded Ubuntu/Lubuntu iso file? 

Thanks,

Able[URL="http://www.techrepublic.com/article/why-the-linux-mint-hack-is-an-indicator-of-a-larger-problem/"]
[/URL]
Personally I feel you are getting unnecessarily worried. I don't regularly check the MD5 or SHA256 sums of ISO files and other downloads. Have I done it before? Yes, of course, but just to see how it works.

Truth is, Linux is very secure because many people are looking at it the entire time. It's like having a house were the walls are transparent. Everybody can take a peek and see if there is a problem inside. They can easily tell the maintainers where the problems are, and they can even correct them themselves.

I have never used Mint, so I don't know how it works specifically. If that 2016 article is still current to this day, I find it odd the way they freeze their repositories to prevent breaking of the system with security updates. I don't think that is a good way of maintaining the environment. However, the "hacking" problem really seems to be unrelated to the operating system; it was about the organization of the project, that is, the people that were able to put together the distribution and the website and forums.

> **mastablasta said:**
> if you look at the article and this part:
**the problem is always the small team size.** but even bigger teams are not imune to hacking and security holes. **it's the nature of opensource** i guess. look at the OpenSSH vulnerability for example. reported long ago, pathced only very recently.

...
I agree that basically that reported problem was an issue of scale. When your product becomes popular, you better have the necessary team to support it. Otherwise, you will let your users down.

When I originally started using Ubuntu, I wanted something with enough support. There were a myriad of distributions to choose from, but only a few seem to be backed up by reputable organizations, with enough resources and communities to keep the system going. I don't know if Mint is at that level yet. I don't discredit Mint users, they make their own choice, just as I make mine.

By the way, "hacking" has nothing to do with open source. It is a product of "social engineering". Many big companies, open and closed source (celebrities as well) have been hacked, Yahoo!, Sony, etc. It is the fragile human condition that is not thinking all the time about security that allows this. It is also the size of the market, and potential gains from it. There are computer viruses for Windows because Windows is the most used operating system, so hackers trow a big net, and they expect to catch at least a few unaware fish. If Linux were to become a much more common operating system, then you can bet the number of "viruses" and exploits would increase. By the way, a "virus" in this sense doesn't necessarily mean a binary program that will corrupt your computer, it could be simple scripts or phishing websites that trick you into opening fraudulent websites and things like that.

So, to summarize. I don't worry too much about that hacking incident. The size of the community plays a big role in my decision to use a Linux project, as I know there will be many eyes catching all the issues that present themselves. And it's also about common sense and general responsibility when using a computer. I don't go to shady websites; if I suspect something is wrong, I stop and research the issue; I check that the website is not redirecting to strange domains, etc.

---

### Post by #&amp;thj^% on 2017-08-02
> **vocx said:**
> Personally I feel you are getting unnecessarily worried. 
So, to summarize. I don't worry too much about that hacking incident. The size of the community plays a big role in my decision to use a Linux project, as I know there will be many eyes catching all the issues that present themselves. _And it's also about common sense and general responsibility when using a computer._ I don't go to shady websites; if I suspect something is wrong, I stop and research the issue; I check that the website is not redirecting to strange domains, etc.

+1 Nicely Put.

---

### Post by mastablasta on 2017-08-03
> **vocx said:**
> 
By the way, "hacking" has nothing to do with open source. It is a product of "social engineering". 

not the hacking itself. 

bu tthe way projects are ran can leave holes. you would have a nice porgram that is maintained by small team or is a one man band. then it suddenly get's dropped. maybe even with no notice. and the app is still in the repositories. no one checking for any security holes and such.

or ther eis a bug report that no one picks up and is left unresolved for longer time. i bet there are a few security ones in the 414 critical bugs

66184 New bugs
132058 Open bugs
1339 In-progress bugs
414 Critical bugs
6130 High importance bugs


though usually security bugs get patched quickly, there are many bugs out there that are not flagged or seen as security issue. but they actually are.

---

