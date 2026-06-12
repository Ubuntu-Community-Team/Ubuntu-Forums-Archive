---
title: "Accessing core features and system apps from the browser"
date: 2010-04-21
forum: The Cafe
---

### Post by lovinglinux on 2010-04-21
Some of you might have noticed that I have been developing some Firefox extensions that can perform unusual actions, like running commands posted in the forums from context menu or backing up Ubuntu packages and restoring them after a clean install of Ubuntu.

I knew that at some point some people will criticize them, because of the belief that some things shouldn't be done though the browser. In my opinion, as long as you make sure the user security is not compromised and makes sense to perform such actions while browsing the Internet, why not? Even if it doesn't make much sense to do some stuff through the browser, but using the browser extension API would allow the developer to create a better tool to the users, why not? Isn't Google creating a lot of hype with an OS that does everything through the browser?

In regard to security, Firefox puts anything from the web on an unprivileged layer, which means a web site cannot access extension functions. So as long as you don't create any code that triggers any action performed by the extension when visiting a particular web site, the extension works pretty much as a standalone application. The only possible issue I see is if the browser is compromised and someone gets total control of it remotely. But in this case, you don't need an extension to screw things up, because if someone gets full control of your browser, you are pretty much screwed anyway, since they could perform any actions using the same API functions an extension developer would use. The only solution for this situation would be using AppArmor, which would also work as a strong security layer for any extension based action. Besides, you can't perform any action that needs root privileges anyway.

So, I created this thread to know what other users/developers think about enhancing the browser with core features? I know this subject has the potential to trigger some deep feelings among the purists and generate some flames, but before categorizing what I'm doing as an abomination and bashing it publicly, please consider that I'm putting a lot of effort on making these tools safe and useful for other users besides myself and I'm exposing this issue here in order to generate a healthy discussion.

On a personal note, if I could do everything I do everyday from the browser, I would do it, since I hate switching windows to do multitasking. Additionally, my browser wasn't ever cracked.

---

### Post by bodhi.zazen on 2010-04-21
Security is always risk vs benefit and often security vs convenience. There are no set of rules that will apply to everyone. One of the criticisms of security is that it cripples the system.

You should be aware, there are security issues reported with firefox on a regular basis and if one allows firefox access to do more and more things the risk of compromise goes up.

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

Just look at the security advisories against firefox and xulrunner :twisted: .

Personally I like the idea of jailing / sandboxing browsers, either the way Chromium does, or with apparmor or selinux.

[http://danwalsh.livejournal.com/31146.html](http://danwalsh.livejournal.com/31146.html)
[http://www.chromium.org/developers/design-documents/sandbox/Sandbox-FAQ](http://www.chromium.org/developers/design-documents/sandbox/Sandbox-FAQ)

IMO the more we move to one click and install types of features the less secure we will be.

---

### Post by madnessjack on 2010-04-21
My opinion: It's a browser not a games platform. It shouldn't even be an application platform :P

---

### Post by lovinglinux on 2010-04-21
> **bodhi.zazen said:**
> Security is always risk vs benefit and often security vs convenience. There are no set of rules that will apply to everyone. One of the criticisms of security is that it cripples the system.

You should be aware, there are security issues reported with firefox on a regular basis and if one allows firefox access to do more and more things the risk of compromise goes up.

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

Just look at the security advisories against firefox and xulrunner :twisted: .

Personally I like the idea of jailing / sandboxing browsers, either the way Chromium does, or with apparmor or selinux.

[http://danwalsh.livejournal.com/31146.html](http://danwalsh.livejournal.com/31146.html)
[http://www.chromium.org/developers/design-documents/sandbox/Sandbox-FAQ](http://www.chromium.org/developers/design-documents/sandbox/Sandbox-FAQ)

IMO the more we move to one click and install types of features the less secure we will be.

It seems from the articles you have posted that Chrome plugins (I guess extensions too) are not sandboxed, because they need full access to the local system. Do you think is really possible to have a fully sandboxed browser without a per user/application configuration scheme, like when using AppArmor profiles to sandbox Firefox?

I'm sure if I sandbox Firefox with AppArmor I will get tons of warnings, not only because of my extensions, but also because several of the 52 third-party extensions I use.

---

### Post by lovinglinux on 2010-04-21
I started to read about how to create chrome extensions and found [this video](http://www.youtube.com/watch?v=DO-nzPqhdXw&feature=channel). Very interesting. Nevertheless, it seems they lack security with regard of their extension gallery, since most of them are not reviewed by Google before entering the gallery. If an user download a malicious extension, then Least Privilege  does not help at all.

---

### Post by Simian Man on 2010-04-21
> **madnessjack said:**
> My opinion: It's a browser not a games platform. It shouldn't even be an application platform :P

I agree.  People try to cram way to many things into the web already.

---

### Post by 2hot6ft2 on 2010-04-21
I like and use your Foxrunner one. Some of the others look interesting and I'll have to take a closer look at them after dinner like CheckIt ,  UMarks and FoxMediaCenter.

Shouldn't that be CheckIt in your signature?
You have CheckI

Keep up the good work.

---

### Post by bodhi.zazen on 2010-04-21
> **lovinglinux said:**
> It seems from the articles you have posted that Chrome plugins (I guess extensions too) are not sandboxed, because they need full access to the local system. Do you think is really possible to have a fully sandboxed browser without a per user/application configuration scheme, like when using AppArmor profiles to sandbox Firefox?

I'm sure if I sandbox Firefox with AppArmor I will get tons of warnings, not only because of my extensions, but also because several of the 52 third-party extensions I use.

I confine Firefox with apparmor =)

I agree it is difficult to do so and it depends on what one uses firefox for exactly.

At least with apparmor I restrict what ff can access.

Chromium and sandboxing X apps with selinux are in development.

---

### Post by lovinglinux on 2010-04-21
> **2hot6ft2 said:**
> I like and use your Foxrunner one. Some of the others look interesting and I'll have to take a closer look at them after dinner like CheckIt ,  UMarks and FoxMediaCenter.

Shouldn't that be CheckIt in your signature?
You have CheckI

Keep up the good work.

Thanks.

:oops: Yes it should be CheckIt :)

---

### Post by 2hot6ft2 on 2010-04-21
You're welcome
I installed CheckIt, it looks like it could be a time saver.

UMarks looks like what people ask for on a regular interval here in the forum. One thing that jumped out at me that might make people shy away from it was under features where it says:
> The extension will then download the missing packages on the new system, **remove the unnecessary ones** and update the system,
I take it that means it removes the ones that were un-installed by the user from the stock install. But it might be worth clarifying that a little.

FoxMediaCenter. WOW, makes me wish I knew where my TV Capture card was now. One day I'll have to get another one so I can try it out.
Did I see you select Portuguese as a second language?
I flashed my cell phone with Portuguese firmware a while back to unlock all the Motorola features that Verizon locked. My hat's off to you if you actually have it as a second language.

---

### Post by lovinglinux on 2010-04-21
> **2hot6ft2 said:**
> I installed CheckIt, it looks like it could be a time saver.

Indeed. I was kind of tired of comparing checksums from command-line, so when I went to download Lucid, this extension idea came up. It is very simple, but I love it. :)

> **2hot6ft2 said:**
> I take it that means it removes the ones that were un-installed by the user from the stock install. But it might be worth clarifying that a little.

Yes, exactly that. I will improve that, thanks a lot.

> **2hot6ft2 said:**
> FoxMediaCenter. WOW, makes me wish I knew where my TV Capture card was now. One day I'll have to get another one so I can try it out.

It can be used without a TV card, for example to keep track of what movies you have already seen.

> **2hot6ft2 said:**
> Did I see you select Portuguese as a second language?
I flashed my cell phone with Portuguese firmware a while back to unlock all the Motorola features that Verizon locked. My hat's off to you if you actually have it as a second language.

Actually, Portuguese is my first language :) Send me a PM if you need any help.

---

### Post by 2hot6ft2 on 2010-04-21
> **lovinglinux said:**
> 
Actually, Portuguese is my first language :) Send me a PM if you need any help.
Wow. It's been a couple years since I did it, and the instructions I followed were very clear on how to change it to English.
You use great English. From what little experience I have had with Portuguese it seems like a difficult language for anyone to have as a second language.
But I will keep that in mind if I do another phone that way. Thanks.

FoxMediaCenter will have to wait until I can get another capture card I guess. Keeping track of what I've already watched would be a full time job on its own.

---

### Post by undecim on 2010-04-21
I like extended functionality of web browsers. I've got the browser open already, why not let it do something useful?

And to computer users nowadays, there is little difference between the computer and the browser.

P.S: I love your addons. I'm about to try out FoxMediaCenter on my HTPC as soon as my mom's tv show is over.

---

