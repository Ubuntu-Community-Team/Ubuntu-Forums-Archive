---
title: "Why is ClamAV NOT being maintained?"
date: 2007-03-14
forum: Server Platforms
---

### Post by GrammatonCleric on 2007-03-14
Why is clamav not being maintained for all ubuntu versions (at least back to Dapper LTS)?  Some of us actually use clamav in a production enviroment in conjuntion with spam filtering.  

```
[LIST]
[*][warty]("http://packages.ubuntu.com/warty/utils/clamav") (utils): Antivirus scanner for Unix   [[COLOR=red]universe[/COLOR]] 
0.73-2: amd64 i386 powerpc
[*][hoary]("http://packages.ubuntu.com/hoary/utils/clamav") (utils): antivirus scanner for Unix   [[COLOR=red]universe[/COLOR]] 
0.83-2ubuntu1: amd64 i386 powerpc
[*][hoary-backports]("http://packages.ubuntu.com/hoary-backports/utils/clamav") (utils): antivirus scanner for Unix   [[COLOR=red]universe[/COLOR]] 
0.87-1~hoary1: amd64 i386 powerpc
[*][breezy]("http://packages.ubuntu.com/breezy/utils/clamav") (utils): antivirus scanner for Unix   [[COLOR=red]universe[/COLOR]] 
0.87-1: amd64 i386 powerpc
[*][breezy-backports]("http://packages.ubuntu.com/breezy-backports/utils/clamav") (utils): antivirus scanner for Unix   [[COLOR=red]universe[/COLOR]] 
0.87.1-1~breezy1: amd64 i386 powerpc
[*][dapper]("http://packages.ubuntu.com/dapper/utils/clamav") (utils): antivirus scanner for Unix   [[COLOR=red]universe[/COLOR]] 
0.88.2-1ubuntu1.3: amd64 i386 powerpc 
0.88.2-1ubuntu1: amd64 i386 powerpc
[*][dapper-backports]("http://packages.ubuntu.com/dapper-backports/utils/clamav") (utils): antivirus scanner for Unix   [[COLOR=red]universe[/COLOR]] 
0.88.4-1ubuntu1~dapper1: amd64 i386 powerpc
[*][edgy]("http://packages.ubuntu.com/edgy/utils/clamav") (utils): antivirus scanner for Unix   [[COLOR=red]universe[/COLOR]] 
0.88.4-1ubuntu2.1: amd64 i386 powerpc 
0.88.4-1ubuntu2: amd64 i386 powerpc
[*][feisty]("http://packages.ubuntu.com/feisty/utils/clamav") (utils): antivirus scanner for Unix   [[COLOR=red]universe[/COLOR]] 
0.90.1-1ubuntu1: amd64 i386 power[/LIST]
```

---

### Post by MJN on 2007-03-14
What do you mean by 'not maintained'? It'll only ever receive *security* updates... The differing versions through the distributions reflect the version current at the time of initial distro release.
 
Or have I misunderstood what you're saying?
 
Mathew

---

### Post by GrammatonCleric on 2007-03-14
Those are also the current versions by ubuntu distribution avaible to download at this time.  Feisty is the only one that is current.  If you seach through the forum you'll find that others are wondering why clamav is not at least at .88.7.  Others are getting....

```

WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.88.4 Recommended version: 0.90.1
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Current functionality level = 8, recommended = 14

```So what does this mean? 
([http://www.clamav.net/support/faq](http://www.clamav.net/support/faq))

What does *WARNING: Current functionality level = 1, required = 2* mean?     [LIST]
[*]The *functionality level* of the database determines which scanner engine version is required to use all of its signatures. If you don&#8217;t upgrade immediately you will be missing the latest viruses.[/LIST]    [LIST]
[*]What does *Your ClamAV installation is OUTDATED* mean?[LIST]
[*]You&#8217;ll get this message whenever a new version of ClamAV is released. In order to detect all the latest viruses, it&#8217;s not enough to keep your database up to date. You also need to run the latest version of the scanner. You can download the [sources]("http://www.clamav.net/download/sources") of the latest release from our website. Upgrade instructions are on the [WikiWiki]("http://wiki.clamav.net/"). If you are afraid to break something while upgrading, use  the [precompiled packages]("http://www.clamav.net/download/packages") for your operating system/distribution.  Remember: running the latest stable release also improves stability.[/LIST] [/LIST] The common reply is "complie it youself."    If it is believed that .88.4 is current I beg to differ...and others with me.

---

### Post by MJN on 2007-03-14
Remember that the versions in the repositories will never be 'current' (i.e. latest release incorporating all new functionality) however they should be updated in response to security vulnerabilities found in those packages.
 
Are you saying that the available versions have security (not functional) shortfalls? If so, I suggest finding and asking the package maintainer for an update. Developer activity on the forums is low hence your pleas for help may well be going unheard.
 
Mathew

---

### Post by GrammatonCleric on 2007-03-14
Seeing how the version of clamav has not been updated in more than a year...and I would think... "[COLOR=Red]**The *functionality level* of the database determines which scanner engine version is required to use all of its signatures.** **If you don’t upgrade immediately you will be missing the latest viruses**[/COLOR]"...is a security shortfall. 

and I have emailed...

Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>


-GC

---

### Post by MJN on 2007-03-14
Finger's crossed you'll get a result.
 
However, poor virus scanning ability is not a security vulnerability _of the product_. Sure, it makes it arguably less useful as a tool doing what it's designed to do hence I too would be looking for an upgrade or alternative solution, however it's not a vulnerability of the code itself (e.g. like a buffer overflow exploit etc would be) and hence possibly not eligible for an obligatory update.
 
Again, the packages in the repositories don't get updated because they're crap compared with the latest-and-greatest, it's because they may suffer security vulnerabilities or gross compatibility issues. To get better functionality one has to upgrade the distribution or compile/upgrade the packges themselves.
 
Mathew

---

### Post by GrammatonCleric on 2007-03-14
> **MJN said:**
> Finger's crossed you'll get a result.
 
However, poor virus scanning ability is not a security vulnerability _of the product_. Sure, it makes it arguably less useful as a tool doing what it's designed to do hence I too would be looking for an upgrade or alternative solution, however it's not a vulnerability of the code itself (e.g. like a buffer overflow exploit etc would be) and hence possibly not eligible for an obligatory update.


I still beg to differ.  If the native code in the package, that was installed from the Ubuntu repo's, allows through a virus or malware but the definitions that you have are current I still think that this constitutes a security vulnerability in the native code.   It is allowing something that has been fixed in th updated versions.  Essentially it's ignoring something that the definitions would not let it do it the engine was updated.  

To follow your argument.  If there is nothing wrong with .88.4  then why was Feisty version of clamav  updated to .90.1? 


 > **MJN said:**
> 
Again, the packages in the repositories don't get updated because they're crap compared with the latest-and-greatest, it's because they may suffer security vulnerabilities or gross compatibility issues. To get better functionality one has to upgrade the distribution or compile/upgrade the packages themselves.
 

This is crazy.  Packages are updated in the repo's all the time.

-GC

---

### Post by MJN on 2007-03-14
> **GrammatonCleric said:**
> I still beg to differ. If the native code in the package, that was installed from the Ubuntu repo's, allows through a virus or malware but the definitions that you have are current I still think that this constitutes a security vulnerability in the native code. It is allowing something that has been fixed in th updated versions
 
No no no!! These aren't _fixes_! Go and read the ClamAV warning again, particularly the bit about **functionality levels**. Functional updates are not included for existing packages.
 
> To follow your argument. If there is nothing wrong with .88.4 then why was Feisty version of clamav updated to .90.1? 
 
What?! Feisty has yet to be released yet and hence last-minute pre-release updates have been allowed to be incorporated. Come back on April 19th and then we can discuss why Feisty packages are not being updated. 
 
> This is crazy. Packages are updated in the repo's all the time.
 
But **only in response to security and major compatibility/stability fixes**! How many times have I said that now?! They are not updated to incorporate added functionality - that's what the backports repository was created for!
 
Let's take a look at one of the most popular packages that we all use - Firefox. The latest-and-greatest is version 2.something-or-other whereas on Dapper we're 'still on' version 1.5. The only updates we will ever expect are related to, again, security/bug-fixes and not functionality updates.
 
Once a distro hits the streets that's it as far as functional release changes are concerned.
 
I'm not sure how else I can say it so without repeating what I've already said... Please, someone else step in before my ! key runs out... ;)
 
Mathew

---

### Post by GrammatonCleric on 2007-03-14
> **MJN said:**
> Okay, we'll have to agree to disagree on this one then. 
 

 
What?! Feisty has yet to be released yet and hence last-minute pre-release updates have been allowed to be incorporated. Come back on April 19th and then we can discuss why Feisty packages are not being updated.
 


Ok... my money is on .90.1.  


 > **MJN said:**
> 
But **only in response to security and major compatibility/stability fixes**! How many times have I said that now?! They are not updated to incorporate added functionality - that's what the backports repository was created for!


If the purpose of clamav is not for security then is what for.   So you are saying that if there's an issue with **iptables **not fully filtering packets but there nothing wrong with the code that it would not be updated?

-GC

---

### Post by MJN on 2007-03-14
> **GrammatonCleric said:**
> Ok... my money is on .90.1.
 
You have missed the point entirely. Of course it'll be .90.1 but that'll be that. The only updates you'll then get will be directly related to security/bugfixes and not added functionality.
 
The ClamAV enhancements you're missing out on are exactly that - enhancements to functionality!
 
> If the purpose of clamav is not for security then is what for. So you are saying that if there's an issue with **iptables **not fully filtering packets but there nothing wrong with the code that it would not be updated?
 
Of course it's purpose is for security. However the lack of the latest functionality is not down to buggy code!!
 
I give up - you are willfully ignoring the philosophy behind distribution releases so I'm on a hiding to nothing trying to explain it to you.
 
Mathew

---

### Post by GrammatonCleric on 2007-03-14
> **MJN said:**
> 
 
I give up - you are willfully ignoring the philosophy behind distribution releases so I'm on a hiding to nothing trying to explain it to you.
 
Mathew

No I'm not but I think it's dumb to update the entire distro to get an update for one package.   That's like saying... "Well my XP antivirus is our of date...Guess I need to update to Vista."

---

### Post by durant1958 on 2007-03-14
It's a philosophical difference.

Ubuntu walks away from a distribution once it is done ( except for security updates ) and they won't revisit it.

This is why I scrubbed an install of Dapper, that I had a lot of time invested in, from my main PC and replaced it with SUSE 10.1.  Novell keeps the SUSE distributions current.

Mark Gosdin

---

### Post by tribaal on 2007-03-14
If you absolutely need the latest version of whatever program you want, just download it and install/compile it yourself...

The versions in the repositories are tested to be *stable secure code*, not the latest. It's a design choice most linux system admins agree with.
Now, linux is about choice - you might not agree with this choice. 
Feel free to try out Debian Sid (unstable) or maybe Gentoo linux instead of Ubuntu?

Edit: Actually, installing the latest version of an antivirus yourself is in no way different from what you'd have to do with Windows. Except you wouldn't have an antivirus at all in the first place, not even an "outdated" one.

- trib'

---

### Post by durant1958 on 2007-03-15
> If you absolutely need the latest version of whatever program you want, just download it and install/compile it yourself...

Not a viable option for everyone.  Other distributions, even Windows for that matter, make this a far less iffy proposition by taking the rough edges off. 

> The versions in the repositories are tested to be *stable secure code*, not the latest. It's a design choice most linux system admins agree with.

The majority of any given group is not necessarily right.  Admins aren't Users, and in the end Users are what count. 

> Now, linux is about choice - you might not agree with this choice.
Feel free to try out Debian Sid (unstable) or maybe Gentoo linux instead of Ubuntu?

Agreed, that is why I'm using Firefox 2 patched to the latest update on openSUSU 10.1, also patched to the latest versions available for it.  Not a perfect distribution, but one that I have confidence in.

Mark Gosdin

---

### Post by GrammatonCleric on 2007-03-15
I understand what everyone is saying about Ubuntu.  I guess what my point is I think that if a package by it functionality is used for security reasons that the package, in this case clamav,  should be updated and maintained for security reasons. Even though the code does not contain a vulnerability, per se.  Not keeping the package updated to use the latest definitions is a security vulnerability.   In short I'd like to see clamav reclassified as a package that is maintained under the guise that each  release is  a security  update.

---

### Post by Rickster888 on 2007-03-15
**DISCLAIMER:** I have not tested these throughly yet.  I built them as it seems people want them.

You can rebuild the packages designed for feisty for edgy (and/or dapper) easily enough,
I have uploaded 0.90.1 for your use, you can use apt, or can download the deb as you wish:

For Edgy (6.10):

deb [http://www.ricky-chan.co.uk/ubuntu](http://www.ricky-chan.co.uk/ubuntu) edgy main

For Dapper (6.06):

deb [http://www.ricky-chan.co.uk/ubuntu](http://www.ricky-chan.co.uk/ubuntu) dapper main

I use edgy (6.10) as my desktop and dapper (6.06 )for my server.  

If you want to build yourself (there is no reason to trust my build), here is how I did it:

wget [http://librarian.launchpad.net/6628285/clamav_0.90.1.orig.tar.gz](http://librarian.launchpad.net/6628285/clamav_0.90.1.orig.tar.gz)
wget [http://librarian.launchpad.net/6628286/clamav_0.90.1-1ubuntu1.diff.gz](http://librarian.launchpad.net/6628286/clamav_0.90.1-1ubuntu1.diff.gz)
cd clamav-0.90.1/
zcat ../clamav_0.90.1-1ubuntu1.diff.gz | patch -p1
(if you want to build on dapper, replace debian/control with [http://www.ricky-chan.co.uk/ubuntu-dapper/debian/control](http://www.ricky-chan.co.uk/ubuntu-dapper/debian/control), this
 seems to be the macro replacement has been changed from 6.10 onwards, so I hard coded the value 0.90.1 instead.  For Edgy this is
no required)
make -f debian/rules
make -f debian/rules binary
cd ..

deb packages built for you.

To build you will probably need to install these packages:

apt-get install libgmp3-dev libwrap0-dev libmilter-dev zlib1g-dev libbz2-dev patch dpatch
(as well as package tools (like dpkg-dev and debhlper and of course compiler et al)

Note: pay attention to config files as 0.9x there has been a lot of changes.


Ricky

---

### Post by Nikron on 2007-03-17
> **Rickster888 said:**
> **DISCLAIMER:** I have not tested these throughly yet.  I built them as it seems people want them.

You can rebuild the packages designed for feisty for edgy (and/or dapper) easily enough,
I have uploaded 0.90.1 for your use, you can use apt, or can download the deb as you wish:

For Edgy (6.10):

deb [http://www.ricky-chan.co.uk/ubuntu](http://www.ricky-chan.co.uk/ubuntu) edgy main

For Dapper (6.06):

deb [http://www.ricky-chan.co.uk/ubuntu](http://www.ricky-chan.co.uk/ubuntu) dapper main

I use edgy (6.10) as my desktop and dapper (6.06 )for my server.  

If you want to build yourself (there is no reason to trust my build), here is how I did it:

wget [http://librarian.launchpad.net/6628285/clamav_0.90.1.orig.tar.gz](http://librarian.launchpad.net/6628285/clamav_0.90.1.orig.tar.gz)
wget [http://librarian.launchpad.net/6628286/clamav_0.90.1-1ubuntu1.diff.gz](http://librarian.launchpad.net/6628286/clamav_0.90.1-1ubuntu1.diff.gz)
cd clamav-0.90.1/
zcat ../clamav_0.90.1-1ubuntu1.diff.gz | patch -p1
(if you want to build on dapper, replace debian/control with [http://www.ricky-chan.co.uk/ubuntu-dapper/debian/control](http://www.ricky-chan.co.uk/ubuntu-dapper/debian/control), this
 seems to be the macro replacement has been changed from 6.10 onwards, so I hard coded the value 0.90.1 instead.  For Edgy this is
no required)
make -f debian/rules
make -f debian/rules binary
cd ..

deb packages built for you.

To build you will probably need to install these packages:

apt-get install libgmp3-dev libwrap0-dev libmilter-dev zlib1g-dev libbz2-dev patch dpatch
(as well as package tools (like dpkg-dev and debhlper and of course compiler et al)

Note: pay attention to config files as 0.9x there has been a lot of changes.


Ricky

Thanks man.. worked perfectly..  However I can't really find anything I need to change in the config files.  Are the defaults fine?

---

### Post by andydread on 2007-03-18
If the purpose of a package is to provide security then
updated functionality & features = security.

If a security package is not up to date then 
then it provides no security.  

I simply do not know why we cant backport 
the feisty versions to dapper.  What is the problem ?

---

### Post by MJN on 2007-03-18
As I said above, ClamAV is not from the Main repository[1] hence is not a core Ubuntu-supported package so any updates will come from the community (of which some Ubuntu members may of course be contributory members). Hence, there is no particular level of support that you are 'entitled to expect'. You'll get what the community offers.

I don't think there is any reason the latest version (nevermind the one in Feisty) is not available other than noone has built it. As it's clear there is requirement for it why don't you guys get together to do so - you'd become overnight heros by the sound of it! ;)

Mathew

[1] Remember there are around 20,000 packages across the repositories - the Ubuntu team are stretched as it is supporting the Main packages so we can't expect them to keep all the others up-to-date too!

---

### Post by Geoffaz on 2007-03-30
I can see both sides of this debate.  I recently moved my development box to Feisty just to get Apache 2.2.x in a package.

You might want to consider Gentoo, or something like Sidux, if you disagree with the way Ubuntu handles updates.

---

### Post by sgenchev on 2007-04-10
In case of a clamav you can argue both ways if being able to use latest signatures is a security issue or not. One important difference in my mind  between old version of  clamav and, say, Apache is that Apache does not lose existing functionality as time goes by. It will serve the same stuff it did before. Clamav on the other hand will definitely be losing functionality - as the time goes by it will catch fewer and fewer *relevant*, in the wild, viruses. Dapper server is going to be supported for another 3.5 years. By that time probably a very sizable number of signatures will not work any more.
 I would love to move my mail servers to Dapper from debian Sarge but seems like debian Etch is my only viable option as it is now.  I do not like the "it's released when it is ready and supported until it isn't any more" predictability of debian but I will pick it over "I know that viruses are getting through my mail servers and I cannot do a thing about it".
  Debian has an official semi-blessed debian-volatile repository presicely for (very few) packages that have upstream development model totally incompatible wit the way distro works. Clamav is in there.  I am not sure I understand why backports do not have current clamav  - it would still be unsupported and all but so is compile-it-yourself option.
  Please, backport maintainers! Could you reconsider your clamav policy?

---

### Post by baastie on 2007-04-10
I agree with sgenchev on this. It's nice that LTS stands for long term support.. but it has to
be usable for long term support. One of the packages is indeed clamav which i think need to be maintained in LTS.

For now.. Etch ( and previously Sarge ) is our choice with the volatile repository...

I also hope it will be backported and 'maintained'...

just my 2 cents...

Cheers...

---

### Post by MJN on 2007-04-11
Correct me if I'm wrong but isn't ClamAV from the Universe repository? Hence, it's not a core Ubuntu package thus the Ubuntu team have no responsibility for keeping it up-to-date.

Rather, Universe packages are **community maintained** so, as part of the community, why don't _**you**_ take a share of that responsibility instead of moaning that no one else is doing it! :confused:

Mathew

---

### Post by GrammatonCleric on 2007-04-11
Yes it is...hence my request "*In short I'd like to see clamav reclassified as a package that is maintained under the guise that each release is a security update.*"

I have an idea why don't ***you*** stop your moaning.  

-GC

---

### Post by MJN on 2007-04-11
Tell you what, why don't we **both** stop moaning (I didn't actually realise I was - I'm quite happy with the situation but for the sake of argument... :)) and get a package put together with the current latest stable build? I'm sure we'd all learn a lot in the process and stop all this bickering about why it's not the latest version and whether it should or shouldn't be...?
 
Mathew

---

### Post by Brazen on 2007-04-11
MJN is absolutely correct.  GrammatonCleric just doesn't seem to get how package development works.  If you want a newer version of a package, to be put in backports for instance, than a physical person has to take charge of developing and maintaining that package.  Since no has done that yet, you have a couple choices:

1)  You do it.
2)  You pay someone to do it.
3)  You live without it.
4)  You ask for a refund, and spend that money on something that works for you.

Complaining and moaning is not going to get people to want to spend their free time helping you.  If you want this done and you feel you are either too lazy or under qualified to do this, than you can ASK around NICELY if anybody out there could HELP YOU do it, or offer to HELP THEM do it.

---

### Post by GrammatonCleric on 2007-04-11
It feels so nice to be singled out but if you actually READ all posts in this thread you'll see others agree with me that ClamAV should be maintained for security reasons.  As for maintaining the package I just might ...may be then you'll stop moaning about a simple request about a single package.  Or is that asking the impossible?

-GC

---

### Post by MJN on 2007-04-12
On behalf of the the community, I think we'd actually all be quite grateful! :)
 
Mathew

---

### Post by pppetter on 2007-04-12
Reading throu [this]("https://wiki.ubuntu.com/BackportRequestProcess") it seems like Clamav complies to the rules of backports. 
I suggest that you start with taking contact with the [Backporters team]("https://launchpad.net/~ubuntu-backporters"). And later on you might become a backporter yourselfes!

Edit: you just gotta love the wiki --> searched for "backports" after reading this thread, and woila! I love the wiki.

---

### Post by jimwillsher on 2007-04-12
Apologies if this has already been mentioned (I just jumped to the last page in this thread), but a few months ago I had the same problem. In the end I uninstalled ClamAv and then compiled it from source. Definitely not as easy as apt-get, but at least it got rid of those annoying OUTDATED messages.

If I knew what I was doing, I would offer to help with the backports. But it was the limit of my Linux skills getting it compiled and insatlled!

Therefore....I too wish it was being maintained....


Jim

---

### Post by GrammatonCleric on 2007-04-13
May be ***Now* **ClamAv will be updated!

> 
------------------------------------------------------------------------------------
** VULNERABILITY ALERT from the Financial Services ISAC**
------------------------------------------------------------------------------------

Advisory ID:    2007-04-041

Date/Time Reported (GMT):    4/13/2007 4:00 PM

Title:    Clam AntiVirus (ClamAV) "cab_extract()" and "chm_decompress_stream()" Vulnerabilities ([https://core.fsisac.com/?requestUrl=..%2fcontent%2fview.aspx%3fPageID%3di6015%26Id%3d433933]("https://core.fsisac.com/?requestUrl=..%2fcontent%2fview.aspx%3fPageID%3di6015%26Id%3d433933"))

Risk:    4

Summary:    [B]Multiple vulnerabilities have been fixed in the latest release (ver 0.90.2) of Clam Anti Virus. Administrators are advised to download the latest version.
[/B] 
Business Impact:    Denial of Service
Remote Code Execution

Severity:    2 - Minimal Impact (Normal)

Urgency:    2 - Action Recommended

Credibility:    5 - Verified

Technology:    Clam Antivirus

Description:    
The severest of these vulnerabilities is a buffer overflow vulnerability. The other vulnerabilities are fixes for 'file descriptor' memory leaks.

The following were some of the security bugs that were fixed:
    - libclamav/chmunpack.c: fixed fd leak in chm_decompress_stream (CVE-2007-1745)
    - libclamav/cab.c: fixed buffer overflow (CVE-2007-1997)
    - libclamav/pdf.c: fixed fd leak on empty objects. 

[COLOR=Red][B] Affected Software: 
Clam AntiVirus (ClamAV) version 0.90.1 and prior [/B][/COLOR]

Corrective Action:    Upgrade to Clam AntiVirus (ClamAV) version 0.90.2 :
[http://sourceforge.net/projects/clamav/](http://sourceforge.net/projects/clamav/) ( [http://sourceforge.net/projects/clamav/](http://sourceforge.net/projects/clamav/) ) 

Source(s):    [http://sourceforge.net/project/shownotes.php?release_id=500765&group_id=86638](http://sourceforge.net/project/shownotes.php?release_id=500765&group_id=86638) ( [http://sourceforge.net/project/shownotes.php?release_id=500765&group_id=86638](http://sourceforge.net/project/shownotes.php?release_id=500765&group_id=86638) ) 

BUGTRAQ ID:    23473

CVE Number:    CVE-2007-1745, CVE-2007-1997



---

### Post by jimwillsher on 2007-04-15
There's also an interesting note on the Feisty page here:

[https://launchpad.net/ubuntu/feisty/+source/clamav/0.90.2-0ubuntu1](https://launchpad.net/ubuntu/feisty/+source/clamav/0.90.2-0ubuntu1)


> 
Upstream is disabling virus definition support for 0.90.0/1 will
      be disabled starting on April 16 2007.



The version in the "standard" Ubuntu repository is 0.88.2, which is very old now.



Jim

---

### Post by Brazen on 2007-04-18
> **GrammatonCleric said:**
> May be ***Now* **ClamAv will be updated!

You just don't get it.  ClamAV IS being maintained.  The security team will take the 0.88 version of Ubuntu and make a patch for the vulnerability you quoted.  It will NOT be the latest version of Ubuntu, but it will get patched for the vulnerability and be updated through apt from the standard repositories.  It will be the same version but with an extra patch for that (and other) particular vulnerability.  That is how packages are maintained on Debian and Ubuntu.

The only way for there to be a newer version of any software, is for it to make it into the Backports repository, which doesn't get a lot of attention.

---

### Post by ikonia on 2007-05-24
are you suggesting that the 0.9X version will be patched into the 0.88 version currently in ubuntu 6.06 ?

eg: take the source package ox 0.88 and apply patches to make it current 0.9X ?

---

### Post by MJN on 2007-05-24
No, the source for 0.88 will be patched to only fix the vulnerability that is now fixed in 0.9X - any added functionality within 0.9X will be left out (unless it is fundamentally required to enable the vulnerability to be closed).

Mathew

---

### Post by ikonia on 2007-05-24
this is an interesting take on "maintaining a package"

In breezey recently firefox was updated (along with its dependencies) to the 1.5 branch from the 1.0 branch for security reasons.

something such as an antivirus product engine and virus definitions really needs to be maintained the latest possible versions.

I think this approach to anti-virus maintaine potentially puts a slant on the "LTS" approach to the ubuntu products as for seucirty and usability in this instance it would be actually better to drop the LTS release and move to say fesity. Which is not a good options for business and schools who the LTS product is aimed at.

---

### Post by MJN on 2007-05-24
Would I be right in thinking you didn't realise ClamAV is from the Universe repository..?

(See [http://www.ubuntu.com/community/ubuntustory/components](http://www.ubuntu.com/community/ubuntustory/components) for the definitions)

Mathew

---

### Post by ikonia on 2007-05-25
totally right that I didn't realise that its from universe.

I guess I'll have to look at other options for long term support machines.

thanks for pointing that out though.

---

### Post by MJN on 2007-05-25
If ClamAV is the only package you're lacking, update-wise, then it might be worth you checking out Ricky's post above (#16) to keep this one updated yourself. Sure, I appreciate you're after automation for updates but it'd be a shame to leave such a great distro for want of a single package...?

Mathew

---

### Post by ikonia on 2007-05-25
I totally appricaite what your saying and suggesting and I certainly won't be using ubuntu for this one reason, I'll be using ubuntu for other functions as its not the only distro I use and install for business use, however I'll just remote it out of the selection for mail server functions, as you said it is a reasonable simple step to update it, but the whole point of the LTS support for me is the package manager compatability and dependeny maintainability, if the package is as trivial to maintain (which it looks like it as as I've just packaged up the almsot latest clam and installed it) it may be nice for ubuntu in the next lts to consider moving this package under true LTS support and defining a better policy for pacakges like this (thats no slant on ubuntu) but for me long term support means addressing this sort of issue, more so when the package is internet facing services. No point including a mail scanner in the repo if its not really maintainable for security use. 

This is no negative comment towards ubuntu, I'm finding it an excellent distro for business use with the LTS model and I very much take on board the fact that its in the universe repo, but if this is going to be classed as production support then it could do with addressing, from my personal needs anyway.

Side note, I'll make the clamav package available to anyone who wants it.

---

### Post by Wasca on 2007-06-01
Here's a Good Idea

Why not post a "How To Manually Install and Update Clam-AV in Ubuntu" in this forum or on the wiki.

I found this post on another website if anyone wants to start making the how to.

[http://www.configserver.com/free/clamav.html](http://www.configserver.com/free/clamav.html)

This would be very helpful to a lot of people.

---

### Post by vertigo23 on 2007-06-15
> **GrammatonCleric said:**
> It feels so nice to be singled out but if you actually READ all posts in this thread you'll see others agree with me that ClamAV should be maintained for security reasons. 
-GC

I agree with this.  There's essentially no purpose in using the current packaged ClamAV, as it will never be able to keep up with the latest signatures.  I have a fair amount of experience installing software from source, so not using the package isn't a big problem for me, but it's sure annoying that I can't.

Consider me another volunteer to keep an up-to-date backport available.

---

### Post by jimwillsher on 2007-06-15
Me too, I'll gladly maintain it if somebody tells me what to do!

Only a matter of weeks since Feisty was released, I get daily nags from freshclam becuase clamav is outdated.

And Ubuntu is supposed to be security-conscious (even as mailserver, if any smart-alecs want to say that Linux doesn't have viruses!)


Jim

---

### Post by keithweddell on 2007-06-20
I have been playing with the directions given by Rickster888 at post #16 of this thread.  On the principle of "give a man a fish ..." I have written a simple script to produce debs that can be installed with dpkg 

1. Creates working directory in your home directory.
2. Uses aptitude to ensure that necessary packages are installed on your system.
2. Downloads source and ubuntu patch from Launchpad.
3. Extracts and patches source code.
4. Builds debs.

You will have to decide which debs to install: I needed clamav-base, clamav-daemon, clamav-freshclam and libclamav2.  Watch out for error messages about dependencies.

sudo dpkg -i /path/to/deb1.deb /path/to/deb2.deb

Feel free to use if it is useful.  I'm sure it can be improved so feel free to chip in with amendments.  However, be warned: **This script has not been extensively tested - I have tried it once on my system - so no guarantees, use at your own risk.**


Keith

PS I did this on Edgy.  It may be different on Dapper.


```
#!/bin/bash
PATH=$PATH:/bin:/sbin:/usr/bin:/usr/sbin

# Script to create clamav deb files. Deb files will be created in the Working Directory.
# To install, use sudo dpkg -i /path/to/deb1.deb /path/to/deb2.deb.  Watch for dependencies.
# To keep up to date, check https://launchpad.net/ubuntu/+source/clamav for most recent clamav package.
# Click on most recent package link to find package page.
# Links to source and diff download locations are at foot of page.
# Amend SOURCE and DIFF variables to reflect latest download locations.


### Set Variables ###

SOURCE=http://launchpadlibrarian.net/7927299/clamav_0.90.3.orig.tar.gz
DIFF=http://launchpadlibrarian.net/7927300/clamav_0.90.3-1ubuntu1.diff.gz
WORKDIR=~/clam


### Derived Variables ###

SOURCEFILE=$(basename $SOURCE)
DIFFFILE=$(basename $DIFF)
MAKEDIR=$(echo $SOURCEFILE | sed 's/.orig.tar.gz//' | sed 's/_/-/')


### Make sure we have the tools ###

sudo aptitude install libgmp3-dev libmilter-dev libwrap0-dev zlib1g-dev libbz2-dev patch dpatch dpkg-dev debhelper wget


### Create working directory ###

if [ ! -d $WORKDIR ]; then
  mkdir $WORKDIR
fi

cd $WORKDIR


### Download Source and Ubuntu Patch ###

wget -O $WORKDIR/$SOURCEFILE $SOURCE
wget -O $WORKDIR/$DIFFFILE $DIFF


### Extract source ###

zcat ./$SOURCEFILE | tar xvf -


### Apply Patch ###

cd $MAKEDIR

zcat ../$DIFFFILE | patch -p1


### Build the Debs ###

make -f debian/rules

sudo make -f debian/rules binary
```

---

### Post by LaserJock on 2007-06-20
Once a release has been released it's not just dropped, there are several ways the release is updated. For security issues, fixes are backported to the current stable release version and go to the -security repo. For critical bugs, fixes are also backported to the current stable release version and go to the -updates repo. Our policy however is to not include newer upstream versions because it's very difficult to know the consequences (we might introduce more bugs in the process) so we stick to backporting the specific fix to the bug in question. The only way to get newer upstream releases currently is to use -backports repos but that's not very helpful for software like clamav because you don't want everything in -backports, just the latest clamav.

The MOTU have been working on a special policy for clamav and related packages (around 20 packages depend on clamav) for a little while now. Please don't assume that developers don't care about packages or security. It's just not always that easy. We've had discussions in MOTU meetings recently about what to do. You can find more info on the [ubuntu-motu]("https://lists.ubuntu.com/archives/ubuntu-motu/2007-June/001747.html") mailing list.

-LaserJock

---

### Post by kitterma on 2007-06-20
There are a few points no one mentioned....

If you are on Feisty (at least, maybe earler, I tested Feisty) and install all the build dependencies, you can use the klamav GUI to keep your clamav current if you want.

The jump from 0.8x to 0.9x changed the interfaces between clamav and the packages that depend on it and also change the library from libclamav1 to libclamav2.  As a result, if you just backported the current clamav to Dapper and Edgy, it'd break a number of packages (in fact the clamtk we released with Feisty is essentially useless because an updated clamtk was available in time that would work with clamav 0.9x - I've asked for a backport of the Gutsy version that does work, but it's still pending).

The why is, of course, not enough volunteers.  As Laserjock mentioned we are trying to figure out the most workable solution to this problem.  No matter what solution we use, we'll need help with testing and packaging.  If anyone is interested in helping and not just whining about the problem, look me up (ScottK) on #ubuntu-motu on IRC.

---

### Post by kitterma on 2007-07-12
Well so far exactly one person has showed up to help.  

If you want a newer clamav in Dapper or Edgy, show up and help.  It's a very complex backport.  All of which is in Universe, so there are no paid devs working on it.

---

### Post by primski on 2007-07-12
There is a good howto for updating clamav on zimbra's wiki

[http://wiki.zimbra.com/index.php?title=Updating_CLAMAV](http://wiki.zimbra.com/index.php?title=Updating_CLAMAV)

---

### Post by jimwillsher on 2007-07-12
I'll gladly help. I'm skilled in a number of languages (MFC C++, PHP, ASP, X++) but I've never done *any* development for Linux.

Happy to help where i can though.


Jim

---

### Post by kitterma on 2007-07-12
> **primski said:**
> There is a good howto for updating clamav on zimbra's wiki

[http://wiki.zimbra.com/index.php?title=Updating_CLAMAV](http://wiki.zimbra.com/index.php?title=Updating_CLAMAV)

Don't use that though.  If you are using Feisty, you have all the security fixes in the current release and 0.91 will get backported reasonably soon, so there's no risk or reason to rush.  

If you are using Dapper or Edgy installing the current clamav will almost certainly break stuff.  We're working on it, but it's a lot more complex.  An obsolete but working virus scanner is more useful than one that is current but doesn't work.  As an example, clamtk will claim it's scanning for virii, but never actually find them.

---

### Post by kitterma on 2007-07-12
> **jimwillsher said:**
> I'll gladly help. I'm skilled in a number of languages (MFC C++, PHP, ASP, X++) but I've never done *any* development for Linux.

Happy to help where i can though.


Jim
Well what we mostly need help with right now is testing, so please join us.

---

### Post by Rickster888 on 2007-08-09
For those who want it:

deb [http://www.ricky-chan.co.uk/ubuntu](http://www.ricky-chan.co.uk/ubuntu) dapper main 

Has clamav 0.91.1 for dapper (6.10) in it now.

Built using the gutsy patches, as per my example earlier.  debian/control file changed as version macros not supported in dapper.

Note: I didn't update the edgy release as it isn't LTS and most people on edgy now on feisty or gutsy which port have 0.91.1 (feisty is a back port).

I have been using on my live 6.10 boxes without any issues (so far).

Many Thanks.


Ricky

---

