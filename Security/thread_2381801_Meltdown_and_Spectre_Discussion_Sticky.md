---
title: "Meltdown and Spectre Discussion Sticky"
date: 2018-01-04
forum: Security
---

### Post by dirk-lehmann on 2018-01-04
Which software kernel solves and protect server against hacking via Intels bug, please see:

OVERVIEW: [https://www.intel.com/content/www/us/en/architecture-and-technology/facts-about-side-channel-analysis-and-intel-products.html](https://www.intel.com/content/www/us/en/architecture-and-technology/facts-about-side-channel-analysis-and-intel-products.html)

NEWSROOM: [https://newsroom.intel.com/news/intel-responds-to-security-research-findings/](https://newsroom.intel.com/news/intel-responds-to-security-research-findings/)

Is there a kernel availabe yet, where and which version?

I was wondering if you would and could let me know

DK

---

### Post by Doug S on 2018-01-04
For only 4 days now, [Kernel 4.15-rc6]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.15-rc6/") (release candidate 6) has the PIT (Page Isolation Table) stuff included. However, the default kernel configuration still has it disabled, so you would need to compile it yourself with CONFIG_PAGE_TABLE_ISOLATION=y (which I did yesterday). I believe it has also been backported to mainline kernel 4.11.13. I think it will still be awhile before Ubuntu kernels have this stuff.

---

### Post by oldfred on 2018-01-04
More details on amount of performance hit. A lot less than the preliminary quoted 30%.

 [https://www.phoronix.com/scan.php?page=article&item=linux-more-x86pti&num=1](https://www.phoronix.com/scan.php?page=article&item=linux-more-x86pti&num=1)
To see if your system is impacted (but it basically comes down to being Intel x86 CPUs or temporarily for AMD CPUs) can check for "cpu_insecure" on the bug line in the /proc/cpuinfo output if running the Linux 4.15-rc6 or later.
When testing on AMD Ryzen but with PTI active, indeed, there is a similar performance hit to Intel. But if using a mainline kernel until that patch ends up being there, just reiterating you can boot your kernel with the "nopti" kernel parameter. Intel users can also opt for the nopti switch if they want to retain maximum performance, but it's a potential security risk. The Ryzen impact:

---

### Post by deadflowr on 2018-01-04
Ubuntu's current meltdown/spectre status:
[https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown]("https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown")

---

### Post by bluemagoo on 2018-01-04
There are two research papers from this site - this topic has been asked a lot over on the OpenBSD list and someone there referenced this link with these two papers.  

[https://spectreattack.com/](https://spectreattack.com/)

---

### Post by Doug S on 2018-01-04
> **oldfred said:**
> More details on amount of performance hit. A lot less than the preliminary quoted 30%.

 [https://www.phoronix.com/scan.php?page=article&item=linux-more-x86pti&num=1](https://www.phoronix.com/scan.php?page=article&item=linux-more-x86pti&num=1)
I did some of those same phoronix tests yesterday: no change for kernel compile; 4.2% degradation for himeno test; no degradation for fs-mark test type 1 (1000 Files, 1MB Size); 16% degradation for fs-mark test type 3 (5000 Files, 1MB Size, 4 Threads).

System: Ubuntu server, i7-2600k.

---

### Post by ra7411 on 2018-01-04
Does anybody have any info or guesses as to what the Meltdown and Spectre microprocessor flaws mean to Ubuntu users?

---

### Post by Frogs Hair on 2018-01-04
Updates in the works

[https://insights.ubuntu.com/2018/01/04/ubuntu-updates-for-the-meltdown-spectre-vulnerabilities/](https://insights.ubuntu.com/2018/01/04/ubuntu-updates-for-the-meltdown-spectre-vulnerabilities/)

---

### Post by mastablasta on 2018-01-05
meltdown affects those using intel, spectre affects those using all CPU, but looks like it is not that bad.

keep your systems up to date. you can also setup unnatended upgrades for automatic patching as well as live patch for home use if needed.

---

### Post by ventrical on 2018-01-05
> **ra7411 said:**
> Does anybody have any info or guesses as to what the Meltdown and Spectre microprocessor flaws mean to Ubuntu users?

Basically it means "patch-city". As long as you keep updated it will keep the exploit vulnerability at bay but it will not eliminate the vulnerability as more methods are devised to crack it. This is a basic hardware flaw in many CPU designs.

It is reported that "this will haunt us for some time.".

Researchers have verified Spectre "breaks down the isolation between different applications" and will affect Intel, AMD and Arm.

 In a statement Arm said the majority of it's processors are not affected by Spectre or Meltdown but admitted it has been working with Intel , AMD and other partners to develop defences against the vulnerabilites......>

Security patches exist for Linux, Windows and OSX but the fix can potentially slow down a PCs performance by 30%.

source.. Hamza Shaban, The Washington Post with files from The Canadian Press

Edit:
Smartphones as well.  

[http://windsorstar.com/pmn/business-pmn/google-says-phones-tablets-also-affected-by-newly-discovered-security-issue/wcm/93efd940-70d8-45c5-a939-cbbd68c0e5cc](http://windsorstar.com/pmn/business-pmn/google-says-phones-tablets-also-affected-by-newly-discovered-security-issue/wcm/93efd940-70d8-45c5-a939-cbbd68c0e5cc)

---

### Post by ardouronerous on 2018-01-05
I was reading this article: [Ubuntu will fix Meltdown and Spectre by January 9th]("https://www.neowin.net/news/ubuntu-will-fix-meltdown-and-spectre-by-january-9th") and this is what caught my attention:

> According to Kirkland, Ubuntu users of “the 64-bit x86 architecture  (aka, amd64)” can expect patched kernels, it’s unclear what will happen  with 32-bit installs, though.

I have two 32-bit computers are home, my Xubuntu desktop and my dad's Lubuntu laptop, both of which are still running great.

---

### Post by joverstreet1 on 2018-01-05
Do Meltdown and Spectre vulnerability problems only apply to 64 bit processors ?

Thanks.

---

### Post by coffeecat on 2018-01-05
*Thread moved to **Security**.*

"Hardware" is for help getting hardware to work with Ubuntu.

---

### Post by Frogs Hair on 2018-01-05
I find a few posts about this . There will probably be more info in the coming days. Most intel chips since 1995 use speculative execution. 

[https://security.stackexchange.com/questions/176737/are-meltdown-and-spectre-exploitable-on-32-bit-linux-platforms/176739#176739](https://security.stackexchange.com/questions/176737/are-meltdown-and-spectre-exploitable-on-32-bit-linux-platforms/176739#176739)



> Any CPU that performs speculative execution is vulnerable to Spectre, so yes, 32-bit OSs are vulnerable.

Meltdown is an issue with how Intel CPUs enforce memory protection while performing speculative execution (in short, memory protection isn't enforced until the point at which speculative execution is turned into real execution). 32-bit OSs on Intel CPUs are vulnerable, but the heavier use of swap reduces the impact somewhat (Meltdown can only read physical memory; data that's been swapped out to disk is inaccessible).


---

### Post by mikewhatever on 2018-01-05
This is a partial quote that looks much like FUD. The original one looks like this:
[http://blog.dustinkirkland.com/2018/01/ubuntu-updates-for-meltdown-spectre.html](http://blog.dustinkirkland.com/2018/01/ubuntu-updates-for-meltdown-spectre.html)
> 
Ubuntu users of the 64-bit x86 architecture (aka, amd64) can expect updated kernels by the original January 9, 2018 coordinated release date, and sooner if possible.

Presumably, 32bit kernels will get updates at a later date, when patches are available.

PS: In case you can't wait, there is mainline kernel 4.14.12 from the PPA with KPTI enabled. It's available, among others, for i386 architecture.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14.12/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14.12/)

---

### Post by mörgæs on 2018-01-05
It has never happened before that a supported release does not receive security updates. This is the definition of support.

My guess is that they are working under time pressure and must release the fix coordinated with other operative systems. Because of this the 64 bit task is first in priority.

(Ninja'ed by Mike)

---

### Post by QIII on 2018-01-05
I read an article posted by another user (mikewhatever posted it above as well) that indicated both Microsoft and Linux OSes expect to have *official* patched and packaged kernels on Tuesday, 9 January.  I know that there is already a patched Linux kernel available (and another RC) if one wants to apply it.

---

### Post by j3984 on 2018-01-05
What do you do to protect your pc against this memory problem on INtel chips??  14.04

---

### Post by pqwoerituytrueiwoq on 2018-01-05
> **j3984 said:**
> What do you do to protect your pc against this memory problem on INtel chips??  14.04
aside from the normal things like do not run untrusted software on your system i have read this can the exploited via javascript, so i would suggest using [noscript]("https://noscript.net") to minimize the threat until the patches are out or compile your own kerenl

from all the benchmarks i have seen at phonorix the performance impact is 0 to 2%, affecting wine, and very high I/O operations eg: SQL benchmark

---

### Post by Frogs Hair on 2018-01-05
Relevant to Firefox users and I suspect other browsers are doing the same.

[https://www.mozilla.org/en-US/firefox/57.0.4/releasenotes/](https://www.mozilla.org/en-US/firefox/57.0.4/releasenotes/)

---

### Post by ardouronerous on 2018-01-05
Once the kernel update is done, is there a way to test if my computer is still vulnerable?

Thanks.

---

### Post by pqwoerituytrueiwoq on 2018-01-05
the patch can be turned on/off via a boot parameter (not sure what it is yet)
also you can check /proc/cpuinfo for the cpu_insecure flag (i think this only appears for affected CPUs)

---

### Post by litlesam on 2018-01-05
Firefox was quick to update, even my Android phone updated to the latest Firefox.

---

### Post by corradoventu on 2018-01-06
Being a problem of isolation between applications may wayland reduce the risk?

---

### Post by rattskjelke on 2018-01-06
Ubuntu's [Meltdown/Spectre info page]("https://insights.ubuntu.com/2018/01/04/ubuntu-updates-for-the-meltdown-spectre-vulnerabilities/") says there will be a patch for
[LIST]
[*]Ubuntu 16.04 LTS (Xenial) &#8212; Linux 4.4 (and 4.4 HWE)
[/LIST]
A few weeks ago I did a fresh install of Xubuntu 16.04.3 LTS and the kernel was automatically updated to 4.10.0-42.
Does this mean there is no patch for the latest HWE kernel version?

---

### Post by deadflowr on 2018-01-06
> **rattskjelke said:**
> Ubuntu's [Meltdown/Spectre info page]("https://insights.ubuntu.com/2018/01/04/ubuntu-updates-for-the-meltdown-spectre-vulnerabilities/") says there will be a patch for
[LIST]
[*]Ubuntu 16.04 LTS (Xenial) — Linux 4.4 (and 4.4 HWE)
[/LIST]
A few weeks ago I did a fresh install of Xubuntu 16.04.3 LTS and the kernel was automatically updated to 4.10.0-42.
Does this mean there is no patch for the latest HWE kernel version?

Most likely because they'll be rolling everyone using the HWE stacks to the 4.13 kernel soon.
(This might even cause an expedited roll out.)
You were going to get the 4.13 eventually anyway, so...

---

### Post by j3984 on 2018-01-06
MY laptop has the 2006 T5500 dual core Intel chip. Is this at risk???
also  will INtel recall all chips that are at risk that have not been sold yet..??

---

### Post by poorguy on 2018-01-06
From everything I've read most Intel processors are at risk.

I really doubt that Intel will recall any processors.

Supposedly Intel is suppose to release a bug fix for some of the newer processors. 

I have more faith in the Linux devs to come up with a solution than to trust what Intel will do if anything.

---

### Post by #&amp;thj^% on 2018-01-06
Not just Intel>>>AMD and Arm are affected.
[https://www.macrumors.com/2018/01/03/intel-addresses-chip-design-flaw/](https://www.macrumors.com/2018/01/03/intel-addresses-chip-design-flaw/)

[https://www.reuters.com/article/us-cyber-intel/security-flaws-put-virtually-all-phones-computers-at-risk-idUSKBN1ES1BO](https://www.reuters.com/article/us-cyber-intel/security-flaws-put-virtually-all-phones-computers-at-risk-idUSKBN1ES1BO)
Please Note there are no known events posted "Yet"
Relax have a cocktail enjoy life. :)
And  avoid downloading apps from unknown sources.;)

---

### Post by TheFu on 2018-01-06
Yes. Every CPU made in the last 20+ yrs has the issue to some extent. 
[https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown) has more details.

What intel does won't be known until after all the lawsuits finish in 3-8 yrs.  If anything at all, I expect a $10 check after all the legal fees are paid. Any CPUs over 5 yrs old aren't supported anymore, so none of those will be specifically addressed by anything Intel does do.

---

### Post by poorguy on 2018-01-06
I only mentioned Intel as that is what the OP ask about.

I agree with your way of relaxation 1fallen. ;)

---

### Post by grahammechanical on 2018-01-06
A quote from the Insights Ubuntu Update Meltdown/spectre page

> Furthermore, you can expect Ubuntu security updates for a number of  other related packages, including CPU microcode, GCC and QEMU in the  coming days.

To get the updated CPU microcode we will need the microcode driver activated

System settings>Software & Updates>Additional Drivers. There should be a radio button that can be ticked to install the microcode driver.

And just what does a microcode driver do?

[https://wiki.debian.org/Microcode](https://wiki.debian.org/Microcode)

Regards

---

### Post by ubuntini2 on 2018-01-07
So apparently even though I am running an AMD cpu I am still susceptible to at least 1 variant of the well publicized Spectre security flaw.


For Ubuntu (I'm running Ubuntu Mate 17.10 artful) I see Jan 9 as a release date for the update


[https://insights.ubuntu.com/2018/01/04/ubuntu-updates-for-the-meltdown-spectre-vulnerabilities/](https://insights.ubuntu.com/2018/01/04/ubuntu-updates-for-the-meltdown-spectre-vulnerabilities/)


Anyone know it there will be a performance hit with this update on AMD processors?

---

### Post by lah-ca on 2018-01-07
Hi,

Over the past few days, there have been many rumours about Meltdown and Spectre but far fewer facts.  I am starting this thread as repository for good articles about the two CPU vulnerabilities and what is being done about them.

The best practical advice I can find anywhere is this:  Don't panic.  There isn't a lot you can do personally at this point (unless you are a developer doing kernel rewrites) except to keep your system up to date and to practice caution on the Internet, two things which are just best practices anyway.  Panic won't help.

Try to stay informed, though.

The best summary of the situations and what is being done to address them that I have found to date is from Ars Technica: 

[https://arstechnica.com/gadgets/2018/01/meltdown-and-spectre-heres-what-intel-apple-microsoft-others-are-doing-about-it/](https://arstechnica.com/gadgets/2018/01/meltdown-and-spectre-heres-what-intel-apple-microsoft-others-are-doing-about-it/)

Please feel free to update this thread with new ***information*** as it is reliably available.  

My intention is that this not be a discussion thread, but once I hit the submit button the thread is out of my control.  Do as you see fit.

Bye.  Have a nice day.

):P


Edit:  Hmmm ... I didn't see the sticky at the top of the Security page.  Maybe this post should have there.  Sorry.

---

### Post by coffeecat on 2018-01-07
Thread merged to sticky.

---

### Post by DuckHook on 2018-01-07
One of the most ironic aspects of the Spectre/Meltdown debacle is that the performance hit being imposed on all operating systems by the needed fixes may very well result in more CPU sales, as everyone from server and cloud farms to private backoffices find themselves forced to implement more hardware to make up for the performance hit.

&#8230;the cruelest of ironies.

---

### Post by TheFu on 2018-01-08
> **DuckHook said:**
> One of the most ironic aspects of the Spectre/Meltdown debacle is that the performance hit being imposed on all operating systems by the needed fixes may very well result in more CPU sales, as everyone from server and cloud farms to private backoffices find themselves forced to implement more hardware to make up for the performance hit.

…the cruelest of ironies.

10 yrs ago, most CPUs were running at 13% utilization, or less.  Virtualization inside most corporations increased that some, but not above 80% in most cases, so it is only the places that run on the edge which will be impacted, IMHO.  And cloud providers that run closer to full capacity (we know which ones those are), which most of us avoid anyway due to very poor performance and their constant push to upgrade to a higher end plan when it shouldn't be needed that will be impacted.

In my reading, most workloads will take a nominal 3%-5% performance hit.  It is only the heavy I/O workloads, which are always pushing upgrades for servers already, that would force more HW.  How many systems are pushing 1,000-20,000 tps through their DBMS and aren't already planning some set of upgrades in architecture and server HW already?

In my tiny bit of the world, a 5+% hit matters not, except, perhaps, during backups. ;)

---

### Post by clivend on 2018-01-08
hello everyone,

I checked my cpu with [the intel]("https://downloadcenter.intel.com/download/27150") tool and seems like I am not affected by the bug. Now I wonder if the patched will cause the performance loss also on non affected cpus like mine.

thanks

---

### Post by mc4man on 2018-01-08
As a run of the mil, no nothing personal laptop user this concerns me not at all. Actually I'm hoping that hype & the resultant consumer hysteria provides a chance to get a new Intel laptop shortly at a reduced price.

---

### Post by Frogs Hair on 2018-01-08
Here is a list from intel as of 1-3-18


[https://security-center.intel.com/advisory.aspx?intelid=INTEL-SA-00088&languageid=en-fr](https://security-center.intel.com/advisory.aspx?intelid=INTEL-SA-00088&languageid=en-fr)

---

### Post by Frogs Hair on 2018-01-08
> **clivend said:**
> hello everyone,

I checked my cpu with [the intel]("https://downloadcenter.intel.com/download/27150") tool and seems like I am not affected by the bug. Now I wonder if the patched will cause the performance loss also on non affected cpus like mine.

thanks

My reading suggests you may need a different tool to test for these vulnerabilities.  See the list in the previous post.


Intel-SA-00088 Detection Tool instead of the Intel-SA-00086 Detection Tool

---

### Post by TheFu on 2018-01-08
> **Frogs Hair said:**
> Here is a list from intel as of 1-3-18


[https://security-center.intel.com/advisory.aspx?intelid=INTEL-SA-00088&languageid=en-fr](https://security-center.intel.com/advisory.aspx?intelid=INTEL-SA-00088&languageid=en-fr)

I'm fairly certain that list is only for officially supported Intel products (5 yrs), since basically every CPU they have made in the last 20 yrs has the issue.

I assume all my Intel CPUs have this issue and all my CPUs (ARM, AMD, and Intel) have the other issue.
This called being realistic.

---

### Post by Frogs Hair on 2018-01-08
The list may be incomplete and thats why I wrote as of . There is reference to product families as well which would include many unlisted processors. 

> [COLOR=#111111][FONT=&amp]The following Intel-based platforms are impacted by this issue. Intel may modify this list at a later time. Please check with your system vendor or equipment manufacturer for more information regarding updates for your system.[/FONT][/COLOR]

---

### Post by TheFu on 2018-01-08
Sorry, I overlooked that.

In the end, my plans:
* Make a list of all my systems. To check off each, since not all of them are currently used.
* Patch the OSes, like I currently do.
* Patch the applications and libraries, like I currently do. There are compiler updates which will impact almost all programs and libraries. We all need these too.  Don't forget snaps and flatpaks and manually installed programs (/usr/local/).
* Look for firmware/BIOS patches in about a week from each motherboard and system vendor.  I don't want/need to be on the bleeding edge, so if they aren't found easily, waiting another week, month, 6 months isn't an issue.
* Continue using high-risk programs inside containers or jails (firejail is handy) with fairly secure settings.  No JS, no flash, no pdf viewing in browsers or email programs. Simplified HTML only in email.

---

### Post by poorguy on 2018-01-08
> **Frogs Hair said:**
> Here is a list from intel as of 1-3-18


[https://security-center.intel.com/advisory.aspx?intelid=INTEL-SA-00088&languageid=en-fr](https://security-center.intel.com/advisory.aspx?intelid=INTEL-SA-00088&languageid=en-fr)

Am I reading this list right*** Intel Core 2 Duo*** processors aren't affected as I don't see them listed.

Thanks

---

### Post by DuckHook on 2018-01-08
> **poorguy said:**
> Am I reading this list right*** Intel Core 2 Duo*** processors aren't affected as I don't see them listed.

Thanks

I'm with TheFu on this one: I'll assume everything from Intel is compromised and I'll believe the exceptions when I see it, test it and prove it.

---

### Post by Frogs Hair on 2018-01-08
> **poorguy said:**
> Am I reading this list right*** Intel Core 2 Duo*** processors aren't affected as I don't see them listed.

Thanks

Look at the note on top regarding product family. [TABLE="class: table table-bordered table-striped table-intel, width: 100%"]
[TR]
[TD]Product family:[/TD]
[TD]Systems with Speculative Execution[/TD]
[/TR]
[/TABLE]

This includes most intel processors going back 20 years or so.

---

### Post by poorguy on 2018-01-08
Kinda figured as much and would rather be safe behind a wall then out in the line of fire.

Thanks for the replies figured this is the place to find the right answers.

Going to have a couple shots of "Wild Turkey 101" and keep trying to learn and understand all of this.

Thanks again.

The PoorGuy

---

### Post by poorguy on 2018-01-08
> **Frogs Hair said:**
> Look at the note on top regarding product family. [TABLE="class: table table-bordered table-striped table-intel, width: 100%"]
[TR]
[TD]Product family:[/TD]
[TD]Systems with Speculative Execution[/TD]
[/TR]
[/TABLE]

This includes most intel processors going back 20 years or so.

Gotcha.

Thanks

The PoorGuy

---

### Post by DuckHook on 2018-01-08
A good and more in-depth write-up of the detective work behind this debacle: [https://www.wired.com/story/meltdown-spectre-bug-collision-intel-chip-flaw-discovery/?mbid=email_onsiteshare](https://www.wired.com/story/meltdown-spectre-bug-collision-intel-chip-flaw-discovery/?mbid=email_onsiteshare)

---

### Post by poorguy on 2018-01-08
> **DuckHook said:**
> A good and more in-depth write-up of the detective work behind this debacle: [https://www.wired.com/story/meltdown-spectre-bug-collision-intel-chip-flaw-discovery/?mbid=email_onsiteshare](https://www.wired.com/story/meltdown-spectre-bug-collision-intel-chip-flaw-discovery/?mbid=email_onsiteshare)

Thanks

---

### Post by ckrles on 2018-01-09
Hi! I've got a computer with Xubuntu 14.04 lts. Will it receive the meltdown and spectre patches? I know Xubuntu 14.04 has run out of support but so has ubuntu 12.04 lts and it is going to receive the patch too according to what I read in [https://insights.ubuntu.com/2018/01/04/ubuntu-updates-for-the-meltdown-spectre-vulnerabilities/](https://insights.ubuntu.com/2018/01/04/ubuntu-updates-for-the-meltdown-spectre-vulnerabilities/)

So, do I have to upgrade to the next Xubuntu release (compatibility issues are expected I think) or should I expect the patch on Xubuntu 14.04 lts? In case it doesn't update... is there a way to manually force the update of the patch or manual installation?

Thanks.

---

### Post by linuxyogi on 2018-01-09
> **clivend said:**
> hello everyone,

I checked my cpu with [the intel]("https://downloadcenter.intel.com/download/27150") tool and seems like I am not affected by the bug. Now I wonder if the patched will cause the performance loss also on non affected cpus like mine.

thanks

I  have downloaded the tool, extracted it. How do I run it ?

---

### Post by j3984 on 2018-01-09
the only update I found was about 800KB of something called Ubuntu Base. Is that the fix for Intel issue??

---

### Post by deadflowr on 2018-01-09
> **ckrles said:**
> Hi! I've got a computer with Xubuntu 14.04 lts. Will it receive the meltdown and spectre patches? I know Xubuntu 14.04 has run out of support but so has ubuntu 12.04 lts and it is going to receive the patch too according to what I read in [https://insights.ubuntu.com/2018/01/04/ubuntu-updates-for-the-meltdown-spectre-vulnerabilities/](https://insights.ubuntu.com/2018/01/04/ubuntu-updates-for-the-meltdown-spectre-vulnerabilities/)

So, do I have to upgrade to the next Xubuntu release (compatibility issues are expected I think) or should I expect the patch on Xubuntu 14.04 lts? In case it doesn't update... is there a way to manually force the update of the patch or manual installation?

Thanks.

While true that Xubuntu 14.04 has run out of support, the base for it has not so you will get the kernel patched just the same as if running normal Ubuntu.
(basically they use the same repos, only difference in that all the Xubuntu goodies are no longer supported)

---

### Post by linuxyogi on 2018-01-09
I  have managed to run the tool. Here's the result :

```
$ sudo python ./intel_sa00086.py 
[sudo] password for xubuntu: 
INTEL-SA-00086 Detection Tool
Copyright(C) 2017, Intel Corporation, All rights reserved

Application Version: 1.0.0.152
Scan date: 2018-01-09 17:15:24 GMT

*** Host Computer Information ***
Name: xubuntu
Manufacturer: System manufacturer
Model: System Product Name
Processor Name: Intel(R) Core(TM) i3-6100 CPU @ 3.70GHz
OS Version: Ubuntu 18.04 bionic (4.14.0-15-generic)

*** Intel(R) ME Information ***
Engine: Intel(R) Management Engine
Version: 11.6.10.1196
SVN: 1

*** Risk Assessment ***
Based on the analysis performed by this tool: [COLOR=#ff0000]This system is vulnerable.[/COLOR]
Explanation:
The detected version of the Intel(R) Management Engine firmware
  is considered vulnerable for INTEL-SA-00086.
  Contact your system manufacturer for support and remediation of this system.

For more information refer to the INTEL-SA-00086 Detection Tool Guide or the
  Intel Security Advisory Intel-SA-00086 at the following link:
  https://www.intel.com/sa-00086-support


```

---

### Post by mc4man on 2018-01-09
16.04 should have pti in the release kernel now or shortly, 16.04-HWE has it in the edge kernel - ex. 
4.13.0-24-generic #28~16.04.1-Ubuntu
> flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm abm cpuid_fault epb invpcid_single [COLOR="#FF0000"]pti[/COLOR] tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts
bugs		: cpu_insecure

18.04 has it in proposed, somewhat incomplete packages - ex.
> flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm abm cpuid_fault epb invpcid_single [COLOR="#FF0000"]pti [/COLOR]tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts
bugs		: cpu_meltdown


18.04 *could*  better described as this may only address meltdown, the other (spectre) is likely not addressed at all or maybe somewhat..
[http://www.kroah.com/log/blog/2018/01/06/meltdown-status/](http://www.kroah.com/log/blog/2018/01/06/meltdown-status/)

---

### Post by linuxyogi on 2018-01-09
> **mc4man said:**
> 16.04 should have pti in the release kernel now or shortly, 16.04-HWE has it in the edge kernel - ex. 
4.13.0-24-generic #28~16.04.1-Ubuntu


18.04 has it in proposed, somewhat incomplete packages - ex.



18.04 *could*  better described as this may only address meltdown, the other (spectre) is likely not addressed at all or maybe somewhat..
[http://www.kroah.com/log/blog/2018/01/06/meltdown-status/](http://www.kroah.com/log/blog/2018/01/06/meltdown-status/)

I am running 18.04 with bionic-proposed enabled. Just received a kernel update. Rebooted the system. Now when I run the Intel tool I still get

 "[COLOR=#ff0000]This system is vulnerable".[/COLOR]

```
$ uname -a
Linux xubuntu 4.14.0-16-generic #19-Ubuntu SMP Mon Jan 8 17:50:31 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux 
```

---

### Post by deadflowr on 2018-01-09
> **linuxyogi said:**
> I am running 18.04 with bionic-proposed enabled. Just received a kernel update. Rebooted the system. Now when I run the Intel tool I still get

 "[COLOR=#ff0000]This system is vulnerable".[/COLOR]

```
$ uname -a
Linux xubuntu 4.14.0-16-generic #19-Ubuntu SMP Mon Jan 8 17:50:31 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux 
```

Because the scan tool has nothing to do with meltdown.
That's about flaws in intel's management engine.
(which seemingly intel does not care enough to help anyone with outside of passing the buck over to whomever the machine's manufacturers are,
who in turn probably do not care about any machine not under warranty; I rant little)

---

### Post by linuxyogi on 2018-01-09
> **deadflowr said:**
> Because the scan tool has nothing to do with meltdown.
That's about flaws in intel's management engine.
(which seemingly intel does not care enough to help anyone with outside of passing the buck over to whomever the machine's manufacturers are,
who in turn probably do not care about any machine not under warranty; I rant little)

Frankly I am yet to understand clearly what Meltdown and Spectre is. 

I am running 
```
 4.14.0-16-generic 
``` 

Do you think I am safe ?

---

### Post by Welly Wu on 2018-01-09
It is my understanding that I am using Ubuntu 16.04.3 64 bit LTS and I have Linux kernel 4.10.0-42 AMD64 generic installed. I would have to download and install Linux kernel 4.13.x-y AMD64 generic from the pti ppa in order for this to be patched, right? In other words, I can wait for Ubuntu 16.04.4 64 bit LTS due on February 15th, 2018 or I can turn on Ubuntu proposed and do an update, correct?

---

### Post by DerPC on 2018-01-09
For starters, the intel tool referenced is NOT to detect the Spectre/Meltdown flaws. It's to detect the Intel Management Engine flaw.

The Spectre/Meltdown detection script is here: [https://github.com/speed47/spectre-meltdown-checker](https://github.com/speed47/spectre-meltdown-checker)

---

### Post by DuckHook on 2018-01-09
> **deadflowr said:**
> That's about flaws in intel's management engine.
(which seemingly intel does not care enough to help anyone with outside of passing the buck over to whomever the machine's manufacturers are,
who in turn probably do not care about any machine not under warranty; I rant little)
&#8593;&#8593;&#8593;&#8593; =d>

Far more than a mere rant. It's absolutely true.

---

### Post by Welly Wu on 2018-01-09
Should I download Linux kernel 4.13 AMD64 from the mainline Linux kernel archive? Does it contain the Ubuntu patches needed or is it not recommended? What should I do about Meltdown and Spectre? Someone please clue me in. Thanks.

---

### Post by linuxyogi on 2018-01-09
> **Welly Wu said:**
> What should I do about Meltdown and Spectre? Someone please clue me in. Thanks.

I too want to know the same thing.

---

### Post by Welly Wu on 2018-01-09
Should I add this ppa: [https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/pti/](https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/pti/) ?

---

### Post by deadflowr on 2018-01-09
> **Welly Wu said:**
> Should I download Linux kernel 4.13 AMD64 from the mainline Linux kernel archive? Does it contain the Ubuntu patches needed or is it not recommended? What should I do about Meltdown and Spectre? Someone please clue me in. Thanks.

A ppa is available for testing.
[https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/pti/]("https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/pti/")
I figure once these pass muster they'll move into the repos and be made available as normal updates.
16.04-hwe will simply roll from 4.10 to 4.13, I would expect sooner than the Feb 15 date.

Edit: seems you figure that one out.

---

### Post by Welly Wu on 2018-01-09
So, the Ubuntu mainline kernel PTI ppa is for testing for now and 4.13 will roll out sooner than next month, right?

---

### Post by linuxyogi on 2018-01-09
I am using ```
4.14.0-16-generic
```

So I am safe ?

---

### Post by deadflowr on 2018-01-09
> **Welly Wu said:**
> So, the Ubuntu mainline kernel PTI ppa is for testing for now and 4.13 will roll out sooner than next month, right?

I think that's the plan.
fingers crossed with a smooth and quick testing period.
> **linuxyogi said:**
> I am using ```
4.14.0-16-generic
```

So I am safe ?
&#65532;look at your flags in the /proc/cpuinfo file
```
cat /proc/cpuinfo
```
and look for the pti flag.

---

### Post by linuxyogi on 2018-01-09
I see **pti** here

[https://paste.ubuntu.com/26355474/](https://paste.ubuntu.com/26355474/)

Does that mean I am okay ?

---

### Post by cruzer001 on 2018-01-09
> **DerPC said:**
> The Spectre/Meltdown detection script is here: [https://github.com/speed47/spectre-meltdown-checker](https://github.com/speed47/spectre-meltdown-checker)

Nice script, thanks for the pointer.

---

### Post by deadflowr on 2018-01-09
> **linuxyogi said:**
> I see **pti** here

[https://paste.ubuntu.com/26355474/](https://paste.ubuntu.com/26355474/)

Does that mean I am okay ?

You've got the kernel mc4man described here:
[https://ubuntuforums.org/showthread.php?t=2381801&page=2&p=13728710#post13728710]("https://ubuntuforums.org/showthread.php?t=2381801&page=2&p=13728710#post13728710")
So it seems you're at least partially patched.

---

### Post by linuxyogi on 2018-01-09
> **deadflowr said:**
>  So it seems you're at least [COLOR=#ff0000]partially patched[/COLOR].

So what do you think I should do ? Remove 18.04 ? Installed 16.04 ?

Frankly I do not want to reinstall.

---

### Post by w00sterf1 on 2018-01-09
On 17.10, I just installed the latest kernel available and reran a check:

 ```

$ sudo bin/spectre-meltdown-checker.sh 
[sudo] password for wooster: 
Spectre and Meltdown mitigation detection tool v0.20


Checking for vulnerabilities against live running kernel Linux 4.13.0-25-generic #29-Ubuntu SMP Mon Jan 8 21:14:41 UTC 2018 x86_64
Will use vmlinux image /boot/vmlinuz-4.13.0-25-generic
Will use kconfig /boot/config-4.13.0-25-generic
Will use System.map file /proc/kallsyms


CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Checking count of LFENCE opcodes in kernel:  NO  (only 42 opcodes found, should be >= 70)
> STATUS:  VULNERABLE  (heuristic to be improved when official patches become available)


CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Mitigation 1
*   Hardware (CPU microcode) support for mitigation:  NO 
*   Kernel support for IBRS:  NO 
*   IBRS enabled for Kernel space:  NO 
*   IBRS enabled for User space:  NO 
* Mitigation 2
*   Kernel compiled with retpoline option:  NO 
*   Kernel compiled with a retpoline-aware compiler:  NO 
> STATUS:  VULNERABLE  (IBRS hardware + kernel support OR kernel with retpoline are needed to mitigate the vulnerability)


CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Kernel supports Page Table Isolation (PTI):  YES 
* PTI enabled and active:  YES 
> STATUS:  NOT VULNERABLE  (PTI mitigates the vulnerability)

```

So, it is partial on my system. The kernel version is:

```

$ uname -a
Linux Baba-Yaga 4.13.0-25-generic #29-Ubuntu SMP Mon Jan 8 21:14:41 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by DuckHook on 2018-01-09
> **linuxyogi said:**
> So what do you think I should do ? Remove 18.04 ? Installed 16.04 ?

Frankly I do not want to reinstall.

There are two reactions to the Meltdown/Spectre fiasco that are equally unwise. One is to ignore it altogether. The other is to behave as if the sky is falling. Both are likely to buy you a mess of avoidable trouble.

The Ubuntu team is methodically pushing out patched kernels. In the meantime, it is *highly* unlikely that you will attract the attention of bad actors intent on targetting you before they attack, say, the London Stock Exchange. In fact, I would guesstimate that you will be struck by lightning before you succumb to some Meltdown attack. So, don't panic, stick with what you're running now and be patient.

---

### Post by linuxyogi on 2018-01-09
@DuckHook 
Got it. Thanks

---

### Post by mc4man on 2018-01-09
> **Welly Wu said:**
> So, the Ubuntu mainline kernel PTI ppa is for testing for now and 4.13 will roll out sooner than next month, right?
I would just wait for the kernels to come to you, should not be long.. 
 As far as the 16.04 hwe (edge) i installed, it's only in proposed & is missing signed images atm.
There is from what i see no immediate threat to users from these vulnerabilities. I only installed the kernel to see, not because I think I currently need it.
(and I don't need the signed images.

---

### Post by DuckHook on 2018-01-09
> **linuxyogi said:**
> @DuckHook 
Got it. Thanks

You're welcome.

To expand a bit by way of explanation (for others following this thread):

This is purely my personal opinion, but installing PPA kernels is fine if you are a tester or someone used to recovering from such things. However, it is bound to increase the general level of breakage and incompatibility in ordinary users. It's an extension of the problem that people run into running standard releases over LTS, only magnified further, because PPA kernels have *not been tested for compatibility with an earlier version's ecosystem.*

So, the quandary facing users is: are they more worried about a theoretical exposure that is getting everyone in a tizzy because it has been hyped to the stratosphere, or are they more worried about installing a "test" kernel that may break their current install? Gurus, experts and testers have no problem with the latter because they know how to recover to an earlier kernel. But general users really have to think twice.

This is what I meant when I cautioned against precipitous action. It's a given that this vulnerability has to be patched. No one in their right mind would dispute that. However, if you are confident that the kernel developers are on top of their game, and the Ubuntu maintainers are on top of theirs, then the best course of action is to keep informed, remain diligent, don't do anything stupid, keep practicing good security *habits* and wait for the proper upgrade that presumably will have been at least somewhat tested to work with your version.

I believe the FireFox patch has already been rolled out with their last upgrade. Make sure you have that installed. Then run noscript on top of it (you should be doing that anyway) and you will have as much protection from javascript exposure as you can achieve in the real world on the one app that is probably your biggest threat.

---

### Post by jsilveronnelly on 2018-01-09
I see that Canonical has released kernel patches (not the PPAs) for one CVE, (Meltdown), but not the other (Spectre)

Any word on when the Spectre patch(es) will be available?

(re: [https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown))

I know I should just sit tight but I have 140 servers to patch and I'm getting jumpy.

Thanks!

---

### Post by bcschmerker on 2018-01-09
**Thanks for opening a Thread on the status of the speculative-execution security patches.**  I posted a question Share to a specific Community at Google+® (an Alphabet Corp. service) on whether speculative execution can be disabled at the microcode level to stop cold, insofar as possible, bounds check bypass (CVE-2017-5753) and branch target injection (CVE-2017-5715), to which I'm assuming both my AMD64 rigs vulnerable to some degree (AMD Athlon 64 in LinUX Kernel 4.13.0-24; AMD Athlon II in Windows 10.0.16299.192), plus the rogue data cache load vulnerability (CVE-2017-5754) of all Intel x86/-64 CISC's since the Pentium II that threatens to derail an extracurricular project of mine.  I proactively upgraded to 4.13.0-22 over the weekend, and 4.13.0-24 replaced it today (viz., 9 January 2018).  Anybody aware of developments affecting either or both of the Packages **amd-microcode** and **intel-microcode**?  Patching the microcode is probably the most effective way to mitigate the problems, short of system change-out - the OMS Japanese Christian Church projection-computer project is known in peril due to the lack of PCI-Express system boards for the Intel® Itanium Processors®, and going AMD for this project is contingent on availability of Threadripper-based Opterons, as registered ECC main memory is non-negotiable.

**Update:**  Kernel 4.13.0-25 was in Proposed later on, now installed as of 23:30, 9 January 2018 (UTC).

---

### Post by DuckHook on 2018-01-09
> **jsilveronnelly said:**
> …I know I should just sit tight…
On the contrary. Like I said:
> **DuckHook said:**
> …the best course of action is to keep informed, remain diligent…
I'm as "jumpy" as you are. This is not a small matter. It's only natural to want better information and you are right to be constantly on the lookout. We hope you'll report back to this thread if you hear anything.

I'm not remotely close to being a kernel or security expert, but from what I've read, Meltdown is the more immediate threat because it is more exploitable. Fortunately, it is also the easier one to remedy, though at the cost of a performance hit. It needs to be dealt with first because it has the larger exposure footprint and is easier for scoundrels to implement. It is capable of allowing one app to directly peer into the private memory space of another app or the kernel itself.

Spectre is far harder to exploit and requires some real finesse involving drawing inferences from very accurate timing of cache hits. This is a level of subtlety that isn't easy to implement. Unfortunately, it is also much harder to defend against. The combination of both factors means that the devs have decided to tackle Spectre later.

Sometimes, we lose sight of what heroic work the devs do to give us the OSes we take so much for granted. By and large, Linux purrs along so nicely that it recedes into the background of our lives. It takes a shock like this to bring home to us how complex and finely tuned the OS is. I have no further info on when the Spectre patches are expected, but I'm sure the devs are working flat out on it and I appreciate how much sacrifice they've put in giving up even their holiday season to work on this emergency.

---

### Post by DuckHook on 2018-01-10
> **jsilveronnelly said:**
> …Any word on when the Spectre patch(es) will be available?…

Nothing specific, but this may be interesting: [http://enews.zdnet.com/ct/33592165:sD4uM9oNH:m:1:2002210373:873ea31d4ad58f396657c1e6ee82f056:r](http://enews.zdnet.com/ct/33592165:sD4uM9oNH:m:1:2002210373:873ea31d4ad58f396657c1e6ee82f056:r)

Especially:> All these patches address the Meltdown problem. Spectre is a different story. There are no Spectre patches available yet. That's because, as Kroah-Hartman explained, "Spectre issues were the last to be addressed by the kernel developers. All of us were working on the Meltdown issue, and we had no real information on exactly what the Spectre problem was at all, and what patches were floating around were in even worse shape than what have been publicly posted."

Therefore, it will take the kernel developers several weeks to "resolve these issues and get them merged upstream." Is this ideal? No. But, Kroah-Hartman shrugged. "It's not the best news, I know, but it's reality. If it's any consolation, it does not seem that any other operating system has full solutions for these issues either, the whole industry is in the same boat right now, and we just need to wait and let the developers solve the problem as quickly as they can," he said.

---

### Post by rattskjelke on 2018-01-10
> **rattskjelke said:**
> Ubuntu's [Meltdown/Spectre info page]("https://insights.ubuntu.com/2018/01/04/ubuntu-updates-for-the-meltdown-spectre-vulnerabilities/") says there will be a patch for
[LIST]
[*]Ubuntu 16.04 LTS (Xenial) — Linux 4.4 (and 4.4 HWE)
[/LIST]
A few weeks ago I did a fresh install of Xubuntu 16.04.3 LTS and the kernel was automatically updated to 4.10.0-42.
Does this mean there is no patch for the latest HWE kernel version?
Today I did an upgrade and the 16.04.3 LTS HWE kernel is now 4.13.0-26.

---

### Post by flocculant on 2018-01-10
> **deadflowr said:**
> While true that Xubuntu 14.04 has run out of support, the base for it has not so you will get the kernel patched just the same as if running normal Ubuntu.
(basically they use the same repos, only difference in that all the Xubuntu goodies are no longer supported)

Thanks for answering deadflowr :)

---

### Post by maglin2 on 2018-01-10
I have the latest kernel 4.4.0-109-generic #132

cat /proc/cpuinfo shows no pti flag.

flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm kaiser dtherm

Does this mean I am still vulnerable, or never was in the first place, or something else?

---

### Post by galacticstone on 2018-01-10
Are these patches something that will be served up automatically through the Ubuntu Software Center? Over the last few days, I have noticed that OS updates were available and installed them, but I don't know if those are related to the Meltdown/Spectre issue. 

Is there any way I can check to see if I am up to date with my patches?

I am running 16.04 LTS and my current kernel is (Linux 4.10.0-42-generic).

Thanks!

---

### Post by deadflowr on 2018-01-10
> Does this mean I am still vulnerable, or never was in the first place, or something else?

A regrettable regression for that kernel:
[https://usn.ubuntu.com/usn/usn-3522-3/]("https://usn.ubuntu.com/usn/usn-3522-3/")
> Is there any way I can check to see if I am up to date with my patches?

Look at the update history logs at /var/log/apt and also, if running automatic updates /var/log/unattended-upgrades.
Both history logs will tell you what packages have been updated recently, and also to what new package version.

---

### Post by maglin2 on 2018-01-10
Thanks deadflowr, but I'm still confused.

Ubuntu Security Notice USN-3522-3 tells me to update to 4.4.0-109.132 - but that is what I have, and I have no PTI flag.
I have no problem booting, and the system seems to be running just fine.

---

### Post by deadflowr on 2018-01-10
Indeed updates for regressions tend to remove or disable the patches or configurations that where in the original updates until such time as they can be fixed.
The original update with the patches was for 4.4.0-108.
But problems problems problems.

Also, are you running an intel cpu?
I think it auto disables the patch if running non-intel processors like amd or arm.
Since meltdown does not (as far as is known) affect non-intel cpus.

Or at least that was what was I thought was suppose to happen.

---

### Post by galacticstone on 2018-01-10
> **deadflowr said:**
> A regrettable regression for that kernel:
[https://usn.ubuntu.com/usn/usn-3522-3/](https://usn.ubuntu.com/usn/usn-3522-3/)

Look at the update history logs at /var/log/apt and also, if running automatic updates /var/log/unattended-upgrades.
Both history logs will tell you what packages have been updated recently, and also to what new package version.

Thanks for the answer. I looked at the logs but it all looks like Greek to me (still a noob with this). I update manually, so only the first log was there.

What should I look for in this log? I can see stuff that I recognize, like packages I installed/updated through Synaptic, but a bunch of it just looks like Greek to me. Can I post a copy/paste of the log here?

Thanks!

MikeG

---

### Post by maglin2 on 2018-01-10
deadflowr,
Yes, I am running an intel cpu
dave-aspire-7736          
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3881MiB
     *-cpu
          product: Pentium(R) Dual-Core CPU       T4400  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 2200MHz
          capacity: 2200MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm kaiser dtherm cpufreq

Thanks for the help.
PS (IIRC 4.4.0-108 also failed to show the pti flag, but since I was aware it had various problems for others I dodn't bother mch about it).
PPS - I see I do have the flag kaiser.
If I understand things correctly (which I often don't) this is another form of kernel page table isolation - ie pti?

---

### Post by ardouronerous on 2018-01-10
I've just received these updates:
```
Install: linux-image-extra-4.4.0-109-generic:i386 (4.4.0-109.132, automatic), linux-headers-4.4.0-109-generic:i386 (4.4.0-109.132, automatic), linux-headers-4.4.0-109:i386 (4.4.0-109.132, automatic), linux-image-4.13.0-26-generic:i386 (4.13.0-26.29~16.04.2, automatic), linux-image-4.4.0-109-generic:i386 (4.4.0-109.132, automatic), linux-headers-4.13.0-26:i386 (4.13.0-26.29~16.04.2, automatic), linux-image-extra-4.13.0-26-generic:i386 (4.13.0-26.29~16.04.2, automatic), linux-headers-4.13.0-26-generic:i386 (4.13.0-26.29~16.04.2, automatic)
Upgrade: linux-headers-generic:i386 (4.4.0.108.113, 4.4.0.109.114), linux-libc-dev:i386 (4.4.0-108.131, 4.4.0-109.132), linux-image-generic-hwe-16.04:i386 (4.10.0.42.44, 4.13.0.26.46), linux-image-generic:i386 (4.4.0.108.113, 4.4.0.109.114), linux-generic-hwe-16.04:i386 (4.10.0.42.44, 4.13.0.26.46), linux-headers-generic-hwe-16.04:i386 (4.10.0.42.44, 4.13.0.26.46), linux-generic:i386 (4.4.0.108.113, 4.4.0.109.114)
```

Am I safe?

How would I be able test if my computer isn't vulnerable? Thanks.

---

### Post by maglin2 on 2018-01-10
Perhaps look at post #68 in this thread?

I couldn't find flag pti. I did find kaiser, which may, or may not, be relevant, but is a form of page table isolation [https://en.wikipedia.org/wiki/Kernel_page-table_isolation](https://en.wikipedia.org/wiki/Kernel_page-table_isolation)

---

### Post by DuckHook on 2018-01-10
So far, my own highly anecdotal and subjective observations: I'm noticing significant slowdown on VM update/upgrades with the patch. Browsing also seems to be slower. Everything else still appears as responsive as before.

---

### Post by galacticstone on 2018-01-11
Can someone translate this Greek for me and let me know if I have received the patch(es) ??  Thanks!

(This is about 90% of my entire Linux history - so here is a snapshot of what a noob does after a fresh installation. Trying out and removing various packages. I can understand some of this log, but I can't decipher whether the patches are there.)

------------------------------------------------------------


```
Start-Date: 2018-01-01  17:49:02
Commandline: /usr/sbin/synaptic
Requested-By: galacticstone (1000)
Install: icc-profiles:amd64 (2.0.1-1), icc-profiles-free:amd64 (2.0.1+dfsg-1, automatic)
Remove: crawl:amd64 (2:0.20.1-1)
End-Date: 2018-01-01  17:49:11


Start-Date: 2018-01-03  21:19:35
Commandline: aptdaemon role='role-upgrade-system' sender=':1.71'
Install: libllvm5.0:amd64 (1:5.0-3~16.04.1, automatic), libllvm5.0:i386 (1:5.0-3~16.04.1, automatic), libdrm-common:amd64 (2.4.83-1~16.04.1, automatic)
Upgrade: libgles2-mesa:amd64 (17.0.7-0ubuntu0.16.04.2, 17.2.4-0ubuntu1~16.04.2), libseccomp2:amd64 (2.2.3-3ubuntu3, 2.3.1-2.1ubuntu2~16.04.1), libdrm-nouveau2:amd64 (2.4.76-1~ubuntu16.04.1, 2.4.83-1~16.04.1), libdrm-nouveau2:i386 (2.4.76-1~ubuntu16.04.1, 2.4.83-1~16.04.1), grub-common:amd64 (2.02~beta2-36ubuntu3.14, 2.02~beta2-36ubuntu3.15), libglapi-mesa:amd64 (17.0.7-0ubuntu0.16.04.2, 17.2.4-0ubuntu1~16.04.2), libglapi-mesa:i386 (17.0.7-0ubuntu0.16.04.2, 17.2.4-0ubuntu1~16.04.2), squashfs-tools:amd64 (1:4.3-3ubuntu2, 1:4.3-3ubuntu2.16.04.1), libxatracker2:amd64 (17.0.7-0ubuntu0.16.04.2, 17.2.4-0ubuntu1~16.04.2), grub2-common:amd64 (2.02~beta2-36ubuntu3.14, 2.02~beta2-36ubuntu3.15), libegl1-mesa:amd64 (17.0.7-0ubuntu0.16.04.2, 17.2.4-0ubuntu1~16.04.2), libgbm1:amd64 (17.0.7-0ubuntu0.16.04.2, 17.2.4-0ubuntu1~16.04.2), libdrm-amdgpu1:amd64 (2.4.76-1~ubuntu16.04.1, 2.4.83-1~16.04.1), libdrm-amdgpu1:i386 (2.4.76-1~ubuntu16.04.1, 2.4.83-1~16.04.1), grub-efi-amd64-bin:amd64 (2.02~beta2-36ubuntu3.14, 2.02~beta2-36ubuntu3.15), libwayland-egl1-mesa:amd64 (17.0.7-0ubuntu0.16.04.2, 17.2.4-0ubuntu1~16.04.2), libdrm2:amd64 (2.4.76-1~ubuntu16.04.1, 2.4.83-1~16.04.1), libdrm2:i386 (2.4.76-1~ubuntu16.04.1, 2.4.83-1~16.04.1), libgl1-mesa-dri:amd64 (17.0.7-0ubuntu0.16.04.2, 17.2.4-0ubuntu1~16.04.2), libgl1-mesa-dri:i386 (17.0.7-0ubuntu0.16.04.2, 17.2.4-0ubuntu1~16.04.2), grub-efi-amd64:amd64 (2.02~beta2-36ubuntu3.14, 2.02~beta2-36ubuntu3.15), xserver-xorg-core-hwe-16.04:amd64 (2:1.19.3-1ubuntu1~16.04.4, 2:1.19.5-0ubuntu2~16.04.1), libgl1-mesa-glx:amd64 (17.0.7-0ubuntu0.16.04.2, 17.2.4-0ubuntu1~16.04.2), libgl1-mesa-glx:i386 (17.0.7-0ubuntu0.16.04.2, 17.2.4-0ubuntu1~16.04.2), grub-efi-amd64-signed:amd64 (1.66.14+2.02~beta2-36ubuntu3.14, 1.66.15+2.02~beta2-36ubuntu3.15), unattended-upgrades:amd64 (0.90ubuntu0.8, 0.90ubuntu0.9), libdrm-intel1:amd64 (2.4.76-1~ubuntu16.04.1, 2.4.83-1~16.04.1), libdrm-intel1:i386 (2.4.76-1~ubuntu16.04.1, 2.4.83-1~16.04.1), libdrm-radeon1:amd64 (2.4.76-1~ubuntu16.04.1, 2.4.83-1~16.04.1), libdrm-radeon1:i386 (2.4.76-1~ubuntu16.04.1, 2.4.83-1~16.04.1), xserver-xorg-legacy-hwe-16.04:amd64 (2:1.19.3-1ubuntu1~16.04.4, 2:1.19.5-0ubuntu2~16.04.1), mesa-va-drivers:amd64 (17.0.7-0ubuntu0.16.04.2, 17.2.4-0ubuntu1~16.04.2)
End-Date: 2018-01-03  21:21:11


Start-Date: 2018-01-03  22:22:57
Commandline: aptdaemon role='role-upgrade-system' sender=':1.71'
Upgrade: apport:amd64 (2.20.1-0ubuntu2.14, 2.20.1-0ubuntu2.15), python3-apport:amd64 (2.20.1-0ubuntu2.14, 2.20.1-0ubuntu2.15), libwebkit2gtk-4.0-37:amd64 (2.18.3-0ubuntu0.16.04.1, 2.18.4-0ubuntu0.16.04.1), apport-gtk:amd64 (2.20.1-0ubuntu2.14, 2.20.1-0ubuntu2.15), gir1.2-webkit2-4.0:amd64 (2.18.3-0ubuntu0.16.04.1, 2.18.4-0ubuntu0.16.04.1), libjavascriptcoregtk-4.0-18:amd64 (2.18.3-0ubuntu0.16.04.1, 2.18.4-0ubuntu0.16.04.1), python3-problem-report:amd64 (2.20.1-0ubuntu2.14, 2.20.1-0ubuntu2.15), libwebkit2gtk-4.0-37-gtk2:amd64 (2.18.3-0ubuntu0.16.04.1, 2.18.4-0ubuntu0.16.04.1), gir1.2-javascriptcoregtk-4.0:amd64 (2.18.3-0ubuntu0.16.04.1, 2.18.4-0ubuntu0.16.04.1)
End-Date: 2018-01-03  22:23:19


Start-Date: 2018-01-04  13:44:56
Commandline: aptdaemon role='role-install-file' sender=':1.61'
Install: libindicator7:amd64 (12.10.2+16.04.20151208-0ubuntu1, automatic), libappindicator1:amd64 (12.10.1+16.04.20170215-0ubuntu1, automatic)
End-Date: 2018-01-04  13:45:00


Start-Date: 2018-01-05  18:05:20
Commandline: apt-get upgrade
Requested-By: galacticstone (1000)
Upgrade: firefox-locale-en:amd64 (57.0.3+build1-0ubuntu0.16.04.1, 57.0.4+build1-0ubuntu0.16.04.1)
End-Date: 2018-01-05  18:05:25


Start-Date: 2018-01-05  18:07:15
Commandline: apt install glances
Requested-By: galacticstone (1000)
Install: ttf-bitstream-vera:amd64 (1.10-8, automatic), fonts-lyx:amd64 (2.1.4-2, automatic), python3-pystache:amd64 (0.5.4-5, automatic), javascript-common:amd64 (11, automatic), python3-dateutil:amd64 (2.4.2-1, automatic), blt:amd64 (2.5.3+dfsg-3, automatic), python3-netifaces:amd64 (0.10.4-0.1build2, automatic), libjs-jquery:amd64 (1.11.3+dfsg-4, automatic), python-matplotlib-data:amd64 (1.5.1-1ubuntu1, automatic), python3-matplotlib:amd64 (1.5.1-1ubuntu1, automatic), python3-psutil:amd64 (3.4.2-1, automatic), python3-numpy:amd64 (1:1.11.0-1ubuntu1, automatic), python3-cycler:amd64 (0.9.0-1, automatic), python3-docker:amd64 (1.9.0-1~16.04.1, automatic), python3-pysnmp4:amd64 (4.2.5-1, automatic), libjs-jquery-ui:amd64 (1.10.1+dfsg-1, automatic), tk8.6-blt2.5:amd64 (2.5.3+dfsg-3, automatic), python3-crypto:amd64 (2.6.1-6ubuntu0.16.04.2, automatic), glances:amd64 (2.3-1build1), python3-tk:amd64 (3.5.1-1, automatic), python3-tz:amd64 (2014.10~dfsg1-0ubuntu2, automatic), lm-sensors:amd64 (1:3.4.0-2, automatic), python3-influxdb:amd64 (2.12.0-1, automatic), python3-websocket:amd64 (0.18.0-2, automatic), python3-bottle:amd64 (0.12.7-1+deb8u1build0.16.04.1, automatic)
End-Date: 2018-01-05  18:07:55


Start-Date: 2018-01-05  21:00:59
Commandline: apt-get install crawl-tiles
Requested-By: galacticstone (1000)
Upgrade: crawl-tiles:amd64 (2:0.20.1-1, 2:0.21.0-1), crawl-tiles-data:amd64 (2:0.20.1-1, 2:0.21.0-1), crawl-common:amd64 (2:0.20.1-1, 2:0.21.0-1)
End-Date: 2018-01-05  21:01:07


Start-Date: 2018-01-06  23:32:32
Commandline: /usr/sbin/synaptic
Requested-By: galacticstone (1000)
Install: libntlm0:amd64 (1.4-7, automatic), gkrellm:amd64 (2.3.6~rc1-1build1)
End-Date: 2018-01-06  23:32:42


Start-Date: 2018-01-06  23:43:10
Commandline: /usr/sbin/synaptic
Requested-By: galacticstone (1000)
Install: gkrellweather:amd64 (2.0.8-2)
End-Date: 2018-01-06  23:43:11


Start-Date: 2018-01-06  23:47:31
Commandline: /usr/sbin/synaptic
Requested-By: galacticstone (1000)
Remove: gkrellweather:amd64 (2.0.8-2), gkrellm:amd64 (2.3.6~rc1-1build1)
End-Date: 2018-01-06  23:47:34


Start-Date: 2018-01-09  00:04:14
Commandline: /usr/sbin/synaptic
Requested-By: galacticstone (1000)
Install: indicator-application-gtk2:amd64 (12.10.0.1-0ubuntu3), libmate-panel-applet-4-1:amd64 (1.12.2-1)
End-Date: 2018-01-09  00:04:20


Start-Date: 2018-01-09  00:23:24
Commandline: aptdaemon role='role-upgrade-system' sender=':1.74'
Upgrade: poppler-utils:amd64 (0.41.0-0ubuntu1.5, 0.41.0-0ubuntu1.6), libpoppler-glib8:amd64 (0.41.0-0ubuntu1.5, 0.41.0-0ubuntu1.6), libpoppler58:amd64 (0.41.0-0ubuntu1.5, 0.41.0-0ubuntu1.6)
End-Date: 2018-01-09  00:23:31


Start-Date: 2018-01-09  23:48:32
Commandline: /usr/sbin/synaptic
Requested-By: galacticstone (1000)
Install: python-gnome2:amd64 (2.28.1+dfsg-1.1, automatic), aweather:amd64 (0.8.1-1ubuntu3), libidl-2-0:amd64 (0.8.14-4, automatic), gdesklets:amd64 (0.36.1-7build3), librsl1:amd64 (1.43-1ubuntu1, automatic), gpsd:amd64 (3.15-2build1, automatic), python-pyorbit:amd64 (2.24.0-7.1, automatic), libgrits5:amd64 (0.8.1-1, automatic), python-gconf:amd64 (2.28.1+dfsg-1.1, automatic), liborbit2:amd64 (1:2.14.19-1build1, automatic)
End-Date: 2018-01-09  23:49:34


Start-Date: 2018-01-09  23:50:57
Commandline: /usr/sbin/synaptic
Requested-By: galacticstone (1000)
Purge: aweather:amd64 (0.8.1-1ubuntu3)
End-Date: 2018-01-09  23:51:01


Start-Date: 2018-01-10  00:08:46
Commandline: /usr/sbin/synaptic
Requested-By: galacticstone (1000)
Purge: gdesklets:amd64 (0.36.1-7build3)
End-Date: 2018-01-10  00:09:23


Start-Date: 2018-01-10  00:27:15
Commandline: aptdaemon role='role-upgrade-system' sender=':1.68'
Upgrade: linux-libc-dev:amd64 (4.4.0-104.127, 4.4.0-108.131)
End-Date: 2018-01-10  00:27:17


Start-Date: 2018-01-10  14:40:24
Commandline: apt-get install gis-weather
Requested-By: galacticstone (1000)
Install: gir1.2-rsvg-2.0:amd64 (2.40.13-3, automatic), gis-weather:amd64 (0.8.2.5~xenial~Noobslab.com)
End-Date: 2018-01-10  14:40:30


Start-Date: 2018-01-10  15:32:51
Commandline: aptdaemon role='role-upgrade-system' sender=':1.68'
Install: linux-image-4.13.0-26-generic:amd64 (4.13.0-26.29~16.04.2, automatic), linux-headers-4.13.0-26:amd64 (4.13.0-26.29~16.04.2, automatic), linux-signed-image-4.13.0-26-generic:amd64 (4.13.0-26.29~16.04.2, automatic), linux-image-extra-4.13.0-26-generic:amd64 (4.13.0-26.29~16.04.2, automatic), linux-headers-4.13.0-26-generic:amd64 (4.13.0-26.29~16.04.2, automatic)
Upgrade: linux-libc-dev:amd64 (4.4.0-108.131, 4.4.0-109.132), linux-image-generic-hwe-16.04:amd64 (4.10.0.42.44, 4.13.0.26.46), linux-signed-generic-hwe-16.04:amd64 (4.10.0.42.44, 4.13.0.26.46), linux-generic-hwe-16.04:amd64 (4.10.0.42.44, 4.13.0.26.46), linux-signed-image-generic-hwe-16.04:amd64 (4.10.0.42.44, 4.13.0.26.46), linux-headers-generic-hwe-16.04:amd64 (4.10.0.42.44, 4.13.0.26.46)
End-Date: 2018-01-10  15:33:58


Start-Date: 2018-01-10  21:30:48
Commandline: /usr/sbin/synaptic
Requested-By: galacticstone (1000)
Remove: rhythmbox-plugins:amd64 (3.3-1ubuntu7), rhythmbox-data:amd64 (3.3-1ubuntu7), rhythmbox-plugin-zeitgeist:amd64 (3.3-1ubuntu7), rhythmbox:amd64 (3.3-1ubuntu7)
End-Date: 2018-01-10  21:31:02


Start-Date: 2018-01-10  21:45:58
Commandline: /usr/sbin/synaptic
Requested-By: galacticstone (1000)
Remove: fortune-mod:amd64 (1:1.99.1-7), finger:amd64 (0.17-15), speech-dispatcher:amd64 (0.8.3-1ubuntu3), libespeak1:amd64 (1.48.04+dfsg-2), espeak-data:amd64 (1.48.04+dfsg-2), fortunes-min:amd64 (1:1.99.1-7), gnome-gmail:amd64 (2.0.1-2), firefox-locale-en:amd64 (57.0.4+build1-0ubuntu0.16.04.1), brltty:amd64 (5.3.1-2ubuntu2.1)
End-Date: 2018-01-10  21:46:12
```

---

### Post by deadflowr on 2018-01-11
> I can understand some of this log, but I can't decipher whether the patches are there.
```
Start-Date: 2018-01-10  15:32:51
Commandline: aptdaemon role='role-upgrade-system' sender=':1.68'
Install: linux-image-4.13.0-26-generic:amd64 (4.13.0-26.29~16.04.2, automatic), linux-headers-4.13.0-26:amd64 (4.13.0-26.29~16.04.2, automatic), linux-signed-image-4.13.0-26-generic:amd64 (4.13.0-26.29~16.04.2, automatic), linux-image-extra-4.13.0-26-generic:amd64 (4.13.0-26.29~16.04.2, automatic), linux-headers-4.13.0-26-generic:amd64 (4.13.0-26.29~16.04.2, automatic)
Upgrade: linux-libc-dev:amd64 (4.4.0-108.131, 4.4.0-109.132), linux-image-generic-hwe-16.04:amd64 (4.10.0.42.44, 4.13.0.26.46), linux-signed-generic-hwe-16.04:amd64 (4.10.0.42.44, 4.13.0.26.46), linux-generic-hwe-16.04:amd64 (4.10.0.42.44, 4.13.0.26.46), linux-signed-image-generic-hwe-16.04:amd64 (4.10.0.42.44, 4.13.0.26.46), linux-headers-generic-hwe-16.04:amd64 (4.10.0.42.44, 4.13.0.26.46)
End-Date: 2018-01-10  15:33:58
```
This is the kernel update.
So it seems to have installed the 4.13.0-26 kernel which has the patch(es).

---

### Post by galacticstone on 2018-01-11
Thanks deadflowr!

I am still learning as I go.  :)

FWIW, I have not noticed any change in system performance.

---

### Post by DuckHook on 2018-01-11
> **galacticstone said:**
> Can someone translate this Greek for me and let me know if I have received the patch(es) ?
At the risk of repetitiveness, an easy way to see if the patch has been applied is as per [deadflowr's post 68]("https://ubuntuforums.org/showthread.php?t=2381801&page=3&p=13728770#post13728770"). An easier version of that command is:```
lscpu
```You can look for the pti flag by filtering the output through grep:```
lscpu | grep pti
```You can check what kernel you have installed by running:```
uname -r
```This may save you the trouble of parsing through long log reports (though it *is* useful to learn how to read logs ;)).

---

### Post by linuxyogi on 2018-01-11
```
lscpu | grep pti
Flags:               fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault invpcid_single [COLOR=#ff0000]pti [/COLOR]intel_pt tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt xsaveopt xsavec xgetbv1 xsaves dtherm arat pln pts hwp hwp_notify hwp_act_window hwp_epp 
```

```
$ uname -r
4.14.0-16-generic 
```

Using 18.04 is rather problematic.

---

### Post by Frogs Hair on 2018-01-11
```
lscpu | grep pti
```

Thanks DuckHook !

---

### Post by DuckHook on 2018-01-11
> **linuxyogi said:**
> …Using 18.04 is rather problematic.
:confused:

Why are you on Bionic? It is in beta—i.e. for testers and other bleeding edge types. Of *course* it's problematic.

---

### Post by deadflowr on 2018-01-11
> **linuxyogi said:**
> <snip>

Using 18.04 is rather problematic.

It is when running proposed...

Edit: also that ^^^^^^^ in the post above this one.

---

### Post by linuxyogi on 2018-01-11
> **DuckHook said:**
> :confused:

Why are you on Bionic? It is in beta&#8212;i.e. for testers and other bleeding edge types. Of *course* it's problematic.

Under 16.04 I was facing issues with pulseaudio. I had to use ```
pulseaudio -k
``` a lot to recover from failed audio. 

18.04 has no such issue.


I enabled  proposed due to this [https://ubuntuforums.org/showthread.php?t=2380665&p=13723825#post13723825](https://ubuntuforums.org/showthread.php?t=2380665&p=13723825#post13723825)

---

### Post by galacticstone on 2018-01-11
> **DuckHook said:**
> At the risk of repetitiveness, an easy way to see if the patch has been applied is as per [deadflowr's post 68]("https://ubuntuforums.org/showthread.php?t=2381801&page=3&p=13728770#post13728770"). An easier version of that command is:```
lscpu
```You can look for the pti flag by filtering the output through grep:```
lscpu | grep pti
```You can check what kernel you have installed by running:```
uname -r
```This may save you the trouble of parsing through long log reports (though it *is* useful to learn how to read logs ;)).

Thanks Duckhook. I put those on my cheat-sheet.  :)

---

### Post by djchandler on 2018-01-11
> **Welly Wu said:**
> It is my understanding that I am using Ubuntu 16.04.3 64 bit LTS and I have Linux kernel 4.10.0-42 AMD64 generic installed. I would have to download and install Linux kernel 4.13.x-y AMD64 generic from the pti ppa in order for this to be patched, right? In other words, I can wait for Ubuntu 16.04.4 64 bit LTS due on February 15th, 2018 or I can turn on Ubuntu proposed and do an update, correct?

4.13 is in the Xenial repository now. Just got upgraded from 4.10 to 4.13.0-28. I don't do unsupported backports. This is supported.

---

### Post by deadflowr on 2018-01-11
I see we are now on to the next phase of updates:
[https://usn.ubuntu.com/usn/usn-3531-1/]("https://usn.ubuntu.com/usn/usn-3531-1/")

---

### Post by galacticstone on 2018-01-11
Will these continue be served up automatically by the software center, or do we need to go out and get them?

---

### Post by deadflowr on 2018-01-11
> **galacticstone said:**
> Will these continue be served up automatically by the software center, or do we need to go out and get them?

They will be available as any normal update would be.
Just keep your system up-to-date as usual.

Once they post the Security notice for a package that package is available.
I would think that only the Software Updater might not show new packages right away, since it still uses the phased-updates implementation, which nothing else uses.
(apt-get, synaptic, unattended-upgrades, and Software Center do not use or have phased-updates configured. )

Phased updates is Ubuntu's method of rolling out updates to small groups of systems first, then expanding that to all users depending on whether the systems report back problems or not.
But thus far as I can tell only update-manager (software updater) has ever been configured to use it.

Note that Software Updater is a different thing than Software Center, which has it's own builtin updater. fwiw

---

### Post by galacticstone on 2018-01-11
> **deadflowr said:**
> They will be available as any normal update would be.
Just keep your system up-to-date as usual.

Once they post the Security notice for a package that package is available.
I would think that only the Software Updater might not show new packages right away, since it still uses the phased-updates implementation, which nothing else uses.
(apt-get, synaptic, unattended-upgrades, and Software Center do not use or have phased-updates configured. )

Phased updates is Ubuntu's method of rolling out updates to small groups of systems first, then expanding that to all users depending on whether the systems report back problems or not.
But thus far as I can tell only update-manager (software updater) has ever been configured to use it.

**Note that Software Updater is a different thing than Software Center, which has it's own builtin updater. fwiw**

Is there a preferred method? I've actually never used the Software Updater and usually update through the Software Center.\

Thanks!

---

### Post by Frogs Hair on 2018-01-11
> **deadflowr said:**
> I see we are now on to the next phase of updates:
[https://usn.ubuntu.com/usn/usn-3531-1/](https://usn.ubuntu.com/usn/usn-3531-1/)

Thanks and done !

---

### Post by mc4man on 2018-01-11
> **deadflowr said:**
> I see we are now on to the next phase of updates:
[https://usn.ubuntu.com/usn/usn-3531-1/]("https://usn.ubuntu.com/usn/usn-3531-1/")

I believe intel-microcode is not default installed so users would need to either have already enabled it in > Software & Updates > Additional Drivers or install it manually, (sudo apt install intel-microcode) to either have it installed or receive updates to it
Obviously not for amd users.. (there is a amd-microcode, amd users should read changelog, no clue if involved in this spectre stuff

---

### Post by linuxyogi on 2018-01-11
I am using 18.04 using kernel.

```
4.14.0-16-generic #19-Ubuntu SMP Mon Jan 8 17:50:31 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

I am still getting "pti"

```
$ lscpu | grep pti
Flags:               fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault invpcid_single [COLOR=#ff0000]**pti**[/COLOR] intel_pt tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt xsaveopt xsavec xgetbv1 xsaves dtherm arat pln pts hwp hwp_notify hwp_act_window hwp_epp 
```

Any way out for me ?

---

### Post by DuckHook on 2018-01-11
> **linuxyogi said:**
> I am still getting "pti"
You are *supposed* to get pti. That means you are patched!

---

### Post by linuxyogi on 2018-01-11
> **DuckHook said:**
> You are *supposed* to get pti. That means you are patched!

Thats a big relief. Thanks a lot.

BTW, I dont notice any slow down.

---

### Post by h113331pp on 2018-01-12
Hi, does Linux kernel 4.4 and 3.13 for Ubuntu 14.04 LTS 32-bit also got spectre&meltdown patches? I got two computers running 32-bit 14.04 with these kernels.

---

### Post by onlineguy on 2018-01-12
My 16.04 install was just updated to 4.13. As you probably know PCID is only supported starting in 4.14. I take it I would have to install a mainline kernel OR wait til 16.04.4 to make use of my CPU's PCID capability, is that correct?

---

### Post by corradoventu on 2018-01-12
So after last updates my Artful should be partially protected against meltdown
```
corrado@corrado-p5-art:~$ inxi -SCGx
System:    Host: corrado-p5-art Kernel: 4.13.0-25-generic x86_64 bits: 64 gcc: 7.2.0
           Desktop: Gnome 3.26.2 (Gtk 3.22.25-0ubuntu0.1) Distro: Ubuntu 17.10
CPU:       Dual core Intel Core i3-7100 (-HT-MCP-) arch: Skylake rev.9 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 15648
           clock speeds: max: 3900 MHz 1: 3900 MHz 2: 3900 MHz 3: 3900 MHz 4: 3900 MHz
Graphics:  Card: Intel HD Graphics 630 bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.5 ) driver: i915 Resolution: 1920x1080@60.00hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 630 (Kaby Lake GT2)
           version: 4.5 Mesa 17.2.2 Direct Render: Yes
corrado@corrado-p5-art:~$ apt policy *microcode*
intel-microcode:
  Installed: 3.20180108.0~ubuntu17.10.1
  Candidate: 3.20180108.0~ubuntu17.10.1
corrado@corrado-p5-art:~$ apt policy firefox
firefox:
  Installed: 57.0.4+build1-0ubuntu0.17.10.1
  Candidate: 57.0.4+build1-0ubuntu0.17.10.1

``` but what about spectre?

---

### Post by DuckHook on 2018-01-12
> **corradoventu said:**
> …but what about spectre?
See [my post #81]("https://ubuntuforums.org/showthread.php?t=2381801&page=3&p=13729084#post13729084").

---

### Post by DuckHook on 2018-01-12
> **h113331pp said:**
> …does Linux kernel 4.4 and 3.13 for Ubuntu 14.04 LTS 32-bit also got spectre&meltdown patches?
No patches for 32-bit yet. No further word either, that I am aware of.

I also have 32-bit machines. They are not exposed to the internet and I don't run anything other than really basic, proven server apps on them. That's a good strategy for remaining safe in the interim.

The Ubuntu devs are being forced to engage in a high-stakes game of whack-a-mole right now. I suspect that 32-bit support is not high on their priority list. You and I will just have to sit tight until they get around to it.

---

### Post by DuckHook on 2018-01-12
> **onlineguy said:**
> My 16.04 install was just updated to 4.13. As you probably know PCID is only supported starting in 4.14. I take it I would have to install a mainline kernel OR wait til 16.04.4 to make use of my CPU's PCID capability, is that correct?Yes. Correct.

Careful about installing forward kernels. It tends to break things. Not always, but frequently enough to need care. Of course, if you are testing, then by all means go ahead.

---

### Post by DuckHook on 2018-01-12
> **ardouronerous said:**
> …Am I safe?No, unfortunately, you are not. You are running 32-bit Linux. Ubuntu has not patched that yet. No word on when they will either. See [post #118]("https://ubuntuforums.org/showthread.php?t=2381801&page=4&p=13729898#post13729898") above.
> How would I be able test if my computer isn't vulnerable? Thanks.
See [post #97]("https://ubuntuforums.org/showthread.php?t=2381801&page=4&p=13729494#post13729494") above.

---

### Post by cruzer001 on 2018-01-12
I did a thread search and got nothing, so I ask...

Would running a virtual machine (virtualbox) offer any protection to the host?  Or sharing the same processor will do nothing useful.

---

### Post by QIII on 2018-01-12
One of the vulnerabilities in this mess is that Spectre crosses the VM boundary.  So there is not, as yet, fully dependable protection.

---

### Post by DuckHook on 2018-01-12
> **cruzer001 said:**
> &#8230;Would running a virtual machine (virtualbox) offer any protection to the host?  Or sharing the same processor will do nothing useful.
One of the biggest problems with both of these side channel attacks is that they can theoretically bypass VM protection and peer into adjacent VMs (even the kernel, which is really serious). Therefore, guest OSes must by patched in addition to that of the host.

However, keep in mind that these vulnerabilities are still *theoretical* (for now). Meltdown has already been mitigated. Spectre is much harder, both to patch but also to exploit. In the meantime, best advice is to stay informed and vigilant, but not to panic either&#8212;which does just as much harm&#8212;especially taking action that compromises a functional working system. It's admittedly a tough balancing act.

Edit: Ninja'd by QIII (the rascal :p).

---

### Post by cruzer001 on 2018-01-12
I had not considered VM side channel attacks.  ouch

Thanks guys

---

### Post by Frogs Hair on 2018-01-12
Post kernel and microcode updates. 
Model name:          Intel(R) Core(TM) i5-2540M CPU @ 2.60GHz.

```
Spectre and Meltdown mitigation detection tool v0.27


Checking for vulnerabilities against live running kernel Linux 4.13.0-25-generic #29-Ubuntu SMP Mon Jan 8 21:14:41 UTC 2018 x86_64


CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Checking count of LFENCE opcodes in kernel:  NO 
> STATUS:  VULNERABLE  (only 29 opcodes found, should be >= 70, heuristic to be improved when official patches become available)


CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Mitigation 1
*   Hardware (CPU microcode) support for mitigation:  NO 
*   Kernel support for IBRS:  NO 
*   IBRS enabled for Kernel space:  NO 
*   IBRS enabled for User space:  NO 
* Mitigation 2
*   Kernel compiled with retpoline option:  NO 
*   Kernel compiled with a retpoline-aware compiler:  NO 
> STATUS:  VULNERABLE  (IBRS hardware + kernel support OR kernel with retpoline are needed to mitigate the vulnerability)


CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Kernel supports Page Table Isolation (PTI):  YES 
* PTI enabled and active:  YES 
> STATUS:  NOT VULNERABLE  (PTI mitigates the vulnerability)


A false sense of security is worse than no security at all, see --disclaimer

```

---

### Post by DuckHook on 2018-01-12
> **Frogs Hair said:**
> Post kernel and microcode updates&#8230;
Hi Frogs Hair. When did you receive your microcode update? I have the driver installed, but don't remember receiving an update. Did you install manually? Also, I'm not sure that a microcode update alone will mitigate Spectre. I believe that both microcode and patch is required to do any good.

Edit:

Never mind. Just got it now with today's update.

---

### Post by Frogs Hair on 2018-01-12
> **DuckHook said:**
> Hi Frogs Hair. When did you receive your microcode update? I have the driver installed, but don't remember receiving an update. Did you install manually? Also, I'm not sure that a microcode update alone will mitigate Spectre. I believe that both microcode and patch is required to do any good.

It was manually installed since installation and it was updated on 1-11-18


```
Commit Log for Thu Jan 11 15:28:01 2018




Upgraded the following packages:
intel-microcode (3.20170707.1) to 3.20180108.0~ubuntu17.10.1



```

---

### Post by DuckHook on 2018-01-12
> **Frogs Hair said:**
> It was installed since installation and it was updated on 1-11-18

Thanks. Just got it right now.

---

### Post by DuckHook on 2018-01-12
Just rebooted and ran spectre-meltdown-checker.sh

Rats. I have a Sandy-bridge, so microcode can't be applied in my case. Will have to rely entirely on future kernel patches, unless Intel releases better microcode.

---

### Post by Frogs Hair on 2018-01-13
Enabled proposed updates on 17.10 and eliminated one more vulnerability. I don't recommend this unless you want to deal with potential problems caused by proposed packages.

Before Proposed Updates:```
[COLOR=#000000][FONT=&amp]Checking for vulnerabilities against live running kernel Linux 4.13.0-25-generic #29-Ubuntu SMP Mon Jan 8 21:14:41 UTC 2018 x86_64[/FONT][/COLOR]

CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Checking count of LFENCE opcodes in kernel:  NO 
> STATUS:  VULNERABLE  (only 29 opcodes found, should be >= 70, heuristic to be improved when official patches become available)

```

After Proposed:
```
Spectre and Meltdown mitigation detection tool v0.28


Checking for vulnerabilities against running kernel Linux 4.13.0-29-generic #32-Ubuntu SMP Fri Jan 12 12:02:18 UTC 2018 x86_64
CPU is Intel(R) Core(TM) i5-2540M CPU @ 2.60GHz


CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Checking count of LFENCE opcodes in kernel:  YES 
> STATUS:  NOT VULNERABLE  (114 opcodes found, which is >= 70, heuristic to be improved when official patches become available)

```

---

### Post by deadflowr on 2018-01-13
I sort of now understand the layout of the microcode updates
To find out if you have the new microcode that actually works for your machine, you need to
run
```
lscpu
```
and find the output for Family, Model, and Stepping.
and then look through the /lib/firmware/intel-ucode directory and see if what your have matches anything in that directory.
If it matches good on you as you should have patched up microcode for your system, if not well then we wait and see
(though I think it'll be akin to Waiting for Godot)

FWIW

> **Frogs Hair said:**
> Enabled proposed updates on 17.10 and eliminated one more vulnerability. I don't recommend this unless you want to deal with potential problems caused by proposed packages.

Before Proposed Updates:```
[COLOR=#000000][FONT=&amp]Checking for vulnerabilities against live running kernel Linux 4.13.0-25-generic #29-Ubuntu SMP Mon Jan 8 21:14:41 UTC 2018 x86_64[/FONT][/COLOR]

CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Checking count of LFENCE opcodes in kernel:  NO 
> STATUS:  VULNERABLE  (only 29 opcodes found, should be >= 70, heuristic to be improved when official patches become available)

```

After Proposed:
```
Spectre and Meltdown mitigation detection tool v0.28


Checking for vulnerabilities against running kernel Linux 4.13.0-29-generic #32-Ubuntu SMP Fri Jan 12 12:02:18 UTC 2018 x86_64
CPU is Intel(R) Core(TM) i5-2540M CPU @ 2.60GHz


CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Checking count of LFENCE opcodes in kernel:  YES 
> STATUS:  NOT VULNERABLE  (114 opcodes found, which is >= 70, heuristic to be improved when official patches become available)

```

Good to know something more might be coming soon.
I wonder if they've got that patch to anything other than the 4.13 series.

---

### Post by maglin2 on 2018-01-14
> **deadflowr said:**
> I sort of now understand the layout of the microcode updates
To find out if you have the new microcode that actually works for your machine, you need to
run
```
lscpu
```
and find the output for Family, Model, and Stepping.
and then look through the /lib/firmware/intel-ucode directory and see if what your have matches anything in that directory.
If it matches good on you as you should have patched up microcode for your system, if not well then we wait and see
(though I think it'll be akin to Waiting for Godot)

I'm now as confused by intel microcode as I was by Waiting for Godot!

Looking in Software and Updates I see that intel microcode firmware is in use (and I know it was recently updated).

Looking at /lib/firmware/intel-ucode directory I see nothing that matches my processor's Family, Model, and Stepping.

So what is it that is in use, and would I be better off selecting Do not use the device?

This is a 9 year old cpu, so perhaps Godot is dead!

---

### Post by mc4man on 2018-01-14
> **maglin2 said:**
> I'm now as confused by intel microcode as I was by Waiting for Godot!

Looking in Software and Updates I see that intel microcode firmware is in use (and I know it was recently updated).

Looking at /lib/firmware/intel-ucode directory I see nothing that matches my processor's Family, Model, and Stepping.

So what is it that is in use, and would I be better off selecting Do not use the device?

This is a 9 year old cpu, so perhaps Godot is dead!
If you want to see where you *may* stand download this script, unpack, & run. As far as to intel microcode part of it's name may be partially in hex, for example here my family is 6,  model is 60, stepping is 3, the microcode file name is 06-3c-03.initramfs (3c=60

[https://github.com/speed47/spectre-meltdown-checker](https://github.com/speed47/spectre-meltdown-checker)

Ex. here see screen, notice this latest 16.04 hwe kernel doesn't have or is reported not to have the kernel opcodes..
Overall as simple home user I'm not concerned in the least.

---

### Post by maglin2 on 2018-01-14
Thanks - I hadn't twigged to the hex.

---

### Post by bcschmerker on 2018-01-14
[@mc4man](https://ubuntuforums.org/member.php?u=320715)  **Thank speed47 @ github.com for us.**  I can run Spectre-Meltdown-Checker.sh during offline installation testing, come back with any returned issues detected.

---

### Post by frogotronic on 2018-01-15
Running Xenial 16.04.3 LTS and updated to 4.13.0-29-generic via SOFTWARE UPDATES and machine will no longer boot.  Had to roll back to 4.13.0-26-generic.

Anyone else have this issue with *-29 being unbootable with 16.04?

```

$ inxi -SCGx
System:    Host: ******-******* Kernel: 4.13.0-26-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Unity 7.4.5 (Gtk 3.18.9-1ubuntu3.3)
           Distro: Ubuntu 16.04 xenial
CPU:       Dual core Intel Core i7-7500U (-HT-MCP-) cache: 4096 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 11616
           clock speeds: max: 3500 MHz 1: 2900 MHz 2: 2900 MHz 3: 2900 MHz
           4: 2900 MHz
Graphics:  Card: Intel Device 5916 bus-ID: 00:02.0
           Display Server: X.Org 1.19.5 drivers: (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.02hz
           GLX Renderer: Mesa DRI Intel HD Graphics 620 (Kaby Lake GT2)
           GLX Version: 3.0 Mesa 17.2.4 Direct Rendering: Yes

```

```

$ sudo ./spectre-meltdown-checker.sh 
Spectre and Meltdown mitigation detection tool v0.31

Checking for vulnerabilities against running kernel Linux 4.13.0-26-generic #29~16.04.2-Ubuntu SMP Tue Jan 9 22:00:44 UTC 2018 x86_64
CPU is Intel(R) Core(TM) i7-7500U CPU @ 2.70GHz

CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Checking count of LFENCE opcodes in kernel:  NO 
> STATUS:  VULNERABLE  (only 29 opcodes found, should be >= 70, heuristic to be improved when official patches become available)

CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Mitigation 1
*   Hardware (CPU microcode) support for mitigation
*     The SPEC_CTRL MSR is available:  YES 
*     The SPEC_CTRL CPUID feature bit is set:  YES 
*   Kernel support for IBRS:  NO 
*   IBRS enabled for Kernel space:  NO 
*   IBRS enabled for User space:  NO 
* Mitigation 2
*   Kernel compiled with retpoline option:  NO 
*   Kernel compiled with a retpoline-aware compiler:  NO 
> STATUS:  VULNERABLE  (IBRS hardware + kernel support OR kernel with retpoline are needed to mitigate the vulnerability)

CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Kernel supports Page Table Isolation (PTI):  YES 
* PTI enabled and active:  YES 
* Checking if we're running under Xen PV (64 bits):  NO 
> STATUS:  NOT VULNERABLE  (PTI mitigates the vulnerability)

A false sense of security is worse than no security at all, see --disclaimer

```

---

### Post by mc4man on 2018-01-15
> **frogotronic said:**
> Running Xenial 16.04.3 LTS and updated to 4.13.0-29-generic via SOFTWARE UPDATES and machine will no longer boot.  Had to roll back to 4.13.0-26-generic.

Anyone else have this issue with *-29 being unbootable with 16.04?


works ok here on a haswell machine though it's still in proposed. Possibly 10+ hrs ago it wasn't as ready to be used.
Maybe wait till released then see how it treats you...
For what it's worth or not fleshes out the ...
```
Spectre and Meltdown mitigation detection tool v0.31
Checking for vulnerabilities against running kernel Linux 4.13.0-29-generic #32~16.04.1-Ubuntu SMP Fri Jan 12 13:08:03 UTC 2018 x86_64
CPU is Intel(R) Core(TM) i7-4700MQ CPU @ 2.40GHz

CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Checking count of LFENCE opcodes in kernel:  YES 
> STATUS:  NOT VULNERABLE  (114 opcodes found, which is >= 70, heuristic to be improved when official patches become available)

CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Mitigation 1
*   Hardware (CPU microcode) support for mitigation
*     The SPEC_CTRL MSR is available:  YES 
*     The SPEC_CTRL CPUID feature bit is set:  YES 
*   Kernel support for IBRS:  YES 
*   IBRS enabled for Kernel space:  YES 
*   IBRS enabled for User space:  NO 
* Mitigation 2
*   Kernel compiled with retpoline option:  NO 
*   Kernel compiled with a retpoline-aware compiler:  NO 
> STATUS:  NOT VULNERABLE  (IBRS mitigates the vulnerability)

CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Kernel supports Page Table Isolation (PTI):  YES 
* PTI enabled and active:  YES 
* Checking if we're running under Xen PV (64 bits):  NO 
> STATUS:  NOT VULNERABLE  (PTI mitigates the vulnerability)
```

---

### Post by frogotronic on 2018-01-15
My update came through on Thursday night and it won't boot.

---

### Post by DuckHook on 2018-01-16
> **frogotronic said:**
> My update came through on Thursday night and it won't boot.
You appear to have "proposed" activated. Incompatibilities are only to be expected with proposed. Unfortunately, turning it off at this point is also problematic. It probably dragged in tons of forward apps the first time you updated, so now you have a vegetable stew of old and new. For now, your best bet is simply to use the 4.13.0-26 kernel.

---

### Post by espectro2 on 2018-01-16
In the case of Ubuntu 16.04.2 which kernel is safer to use that fixes the flaws mentioned in this notice
[https://insights.ubuntu.com/2018/01/04/ubuntu-updates-for-the-meltdown-spectre-vulnerabilities/](https://insights.ubuntu.com/2018/01/04/ubuntu-updates-for-the-meltdown-spectre-vulnerabilities/)
This version is safe or I have to upgrade 4.13.0-26-generic # 29 ~ 16.04.2-Ubuntu
I should add this ppa ppa: canonical-kernel-team / pti. to be safer?
How do I add this ppa?Thanks for listening.

---

### Post by slickymaster on 2018-01-16
> **espectro2 said:**
> In the case of Ubuntu 16.04.2 which kernel is safer to use that fixes the flaws mentioned in this notice
[https://insights.ubuntu.com/2018/01/04/ubuntu-updates-for-the-meltdown-spectre-vulnerabilities/](https://insights.ubuntu.com/2018/01/04/ubuntu-updates-for-the-meltdown-spectre-vulnerabilities/)
This version is safe or I have to upgrade 4.13.0-26-generic # 29 ~ 16.04.2-Ubuntu
I should add this ppa ppa: canonical-kernel-team / pti. to be safer?
How do I add this ppa?Thanks for listening.

Merged with the Meltdown and Spectre Discussion Sticky

---

### Post by deadflowr on 2018-01-16
> **espectro2 said:**
> In the case of Ubuntu 16.04.2 which kernel is safer to use that fixes the flaws mentioned in this notice
[https://insights.ubuntu.com/2018/01/04/ubuntu-updates-for-the-meltdown-spectre-vulnerabilities/](https://insights.ubuntu.com/2018/01/04/ubuntu-updates-for-the-meltdown-spectre-vulnerabilities/)
This version is safe or I have to upgrade 4.13.0-26-generic # 29 ~ 16.04.2-Ubuntu
I should add this ppa ppa: canonical-kernel-team / pti. to be safer?
How do I add this ppa?Thanks for listening.

> **This version is safe** 
I bolded this because I haven't any idea what version it refers.
But the 4.13.0-26 kernel is what you would automatically get just by running a regular update.
There are caveats though such as various driver versions might not be functional, such as nvidia drivers (or at least the 387 nvidia version, I guess 384 and 390 might work)
Other issues involve using the Virtualbox version that is available from Ubuntu which may cause system freezes.
(The Virtualbox issue can be remedied by installing the newer version from Oracle)

There is no need to install or add the ppa at this point.

---

### Post by DuckHook on 2018-01-16
> **espectro2 said:**
> In the case of Ubuntu 16.04.2 which kernel is safer to use that fixes the flaws mentioned in this notice
[https://insights.ubuntu.com/2018/01/04/ubuntu-updates-for-the-meltdown-spectre-vulnerabilities/](https://insights.ubuntu.com/2018/01/04/ubuntu-updates-for-the-meltdown-spectre-vulnerabilities/)
This version is safe or I have to upgrade 4.13.0-26-generic # 29 ~ 16.04.2-Ubuntu
I should add this ppa ppa: canonical-kernel-team / pti. to be safer?
How do I add this ppa?Thanks for listening.
I do not recommend adding PPAs unless you are a very knowledgeable user who knows what the risks are and can recover from bad updates easily.

I'm confused by your post. Are you running 4.13.0-26 now or are you asking how to install it?

If I remember correctly, 16.04.2 didn't automatically update to newer kernel series. That didn't start until 16.04.3. You needed to install the HWE stack to make it install automatically going forward. To check, please do:```
sudo apt update && sudo apt full-upgrade
```…then post results of:```
uname -r
```If this result is not *4.13.0-26* then you will need to do:```
sudo apt install --install-recommends xserver-xorg-hwe-16.04
```If you have already done this in the past, then you should be OK and no need to install any newer kernel.

---

### Post by deadflowr on 2018-01-16
(Rolling) HWE started for 16.04.2:
[https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack#Implementation]("https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack#Implementation")

---

### Post by DuckHook on 2018-01-16
> **DuckHook said:**
> …If I remember correctly…

> **deadflowr said:**
> (Rolling) HWE started for 16.04.2…
My bad.

Obviously, my aging memory is *not* correct anymore.

---

### Post by bcschmerker on 2018-01-16
I'd already planned on an upgrade MPU to restore the performance of the Hot Rod gPC&#8482; to where it was on the Athlon 64 X2 5600+ (it runs a 3500+ as of 16 January 2018), but these CVE's add a factor to the selection process.  How early Advanced Micro Devices processors for PGA 939 (excepting the FX-Series, Socket AM3b) can handle IBRS?  Spectre and Meltdown Mitigation Detection Tool v0.31 (which has my rig marked as vulnerable to both bounds check bypass and branch target injection under Kernel 4.13.0-26-generic) specifically mentioned SPEC_CTRL on the CVE-2017-5715 Mitigation 1 section.

---

### Post by deadflowr on 2018-01-16
> **DuckHook said:**
> My bad.

Obviously, my aging memory is *not* correct anymore.

Probably thinking back to every previous LTS with hwe like 14.04 which left the hwe upgrades up to the user.
I wonder how many users are running 14.04 with dead hwe kernel stacks like 14.04.3 (or 4) which are the last stacks that could run the amd fglrx driver.
Or are running those just because they never even thought about it. /meandering side thought.

---

### Post by espectro2 on 2018-01-16
[**[COLOR=#C61919][B]DuckHook**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1256508") I'm currently  running 4.13.0-26-generic 4.13.0-26-generic # 29 ~ 16.04.2-Ubuntu  installed. Would you like to know if it's already upgraded or do you  need any more updates?
Thanks for listening.

---

### Post by DuckHook on 2018-01-16
> **espectro2 said:**
> [**[COLOR=#C61919][B]DuckHook**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1256508") I'm currently  running 4.13.0-26-generic 4.13.0-26-generic # 29 ~ 16.04.2-Ubuntu  installed. Would you like to know if it's already upgraded or do you  need any more updates?
Thanks for listening.
You are in good shape. You already have the latest mainline kernel with the fix for Meltdown. No need for further info.

Good Luck and Happy Ubuntu-ing!

---

### Post by espectro2 on 2018-01-18
[**[COLOR=#C61919][B]DuckHook**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1256508") One last question to  check if vulnerability is affecting the machine or which of these two  tools give the most successful result?

thanks for listening

> [https://github.com/speed47/spectre-meltdown-checker](https://github.com/speed47/spectre-meltdown-checker)

> Intel&#8211;SA&#8211;00086 Detection Tool
[https://security-center.intel.com/advisory.aspx?intelid=INTEL-SA-](https://security-center.intel.com/advisory.aspx?intelid=INTEL-SA-)
00086&languageid=en-fr

---

### Post by deadflowr on 2018-01-18
> **espectro2 said:**
> [**[COLOR=#C61919][B]DuckHook**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1256508") One last question to  check if vulnerability is affecting the machine or which of these two  tools give the most successful result?

thanks for listening

> [https://github.com/speed47/spectre-meltdown-checker](https://github.com/speed47/spectre-meltdown-checker)

> Intel–SA–00086 Detection Tool
[https://security-center.intel.com/advisory.aspx?intelid=INTEL-SA-](https://security-center.intel.com/advisory.aspx?intelid=INTEL-SA-)
00086&languageid=en-fr

They're different detection tools for different problems.

The github script is for detecting your system's meltdown/spectre situation.
(whether or not you have been patched or not and also what has been patched)
So that deals directly with the purpose of this thread.

The intel-sa-00086 tool is for detecting what intel management engine version you have.
That's unrelated to this thread.

---

### Post by espectro2 on 2018-01-18
[**[COLOR=#C61919][B]DuckHook **[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1256508")Our excuse, I understood everything wrong, even though you clarified it, I thought it was related.
Thanks for listening.

---

### Post by MoebusNet on 2018-01-19
I found this command to check for patch installation:

```
grep CONFIG_PAGE_TABLE_ISOLATION=y /boot/config-`uname -r` && echo "patched :)" || echo "unpatched :("
```

Unfortunately for me, 32-bit machines haven't been patched yet. Output of command attached.

---

### Post by corradoventu on 2018-01-21
[https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown)
2018 Jan 12: Linux kernel version 4.13.0-29.32 for Artful 17.10 with Spectre mitigations is available in artful-proposed for testing. but up today (Jan 21) is not yet in the stable channel, does this indicate that there are problems?

---

### Post by DuckHook on 2018-01-21
> **corradoventu said:**
> &#8230;does this indicate that there are problems?
Of course there are problems. That is normal. That's also the point in having a testing process. Newer kernels must be tested and debugged thoroughly. This takes time. The fact that it is in proposed means that it is being worked on.

BTW, I would not recommend turning on proposed unless you are used to hosing your system and rebuilding it. Testers and developers revel in proposed, but it is not for the timid like me.

---

### Post by corradoventu on 2018-01-22
I have 2 partitions with Artful, one without proposed and one on which i have enabled proposed just to install the new kernel, and then again disabled. Same for Bionic. I was just amazed for this long time.

---

### Post by linuxyogi on 2018-01-22
```
$ sudo sh spectre-meltdown-checker.sh 
[sudo] password for xubuntu: 
Spectre and Meltdown mitigation detection tool v0.21

Checking for vulnerabilities against live running kernel Linux 4.14.0-16-generic #19-Ubuntu SMP Mon Jan 8 17:50:31 UTC 2018 x86_64

CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Checking count of LFENCE opcodes in kernel:  NO  (only 42 opcodes found, should be >= 70)
> STATUS:  VULNERABLE  (heuristic to be improved when official patches become available)

CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Mitigation 1
*   Hardware (CPU microcode) support for mitigation:  NO 
*   Kernel support for IBRS:  NO 
*   IBRS enabled for Kernel space:  NO 
*   IBRS enabled for User space:  NO 
* Mitigation 2
*   Kernel compiled with retpoline option:  NO 
*   Kernel compiled with a retpoline-aware compiler:  NO 
> STATUS:  VULNERABLE  (IBRS hardware + kernel support OR kernel with retpoline are needed to mitigate the vulnerability)

CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Kernel supports Page Table Isolation (PTI):  YES 
* PTI enabled and active:  YES 
> STATUS:  NOT VULNERABLE  (PTI mitigates the vulnerability)

A false sense of security is worse than no security at all, see --disclaimer


```

Can someone please translate the above in English and tell me if I am safe ?

---

### Post by pqwoerituytrueiwoq on 2018-01-22
You patched against meltdown, but not Spectre

---

### Post by linuxyogi on 2018-01-22
> **pqwoerituytrueiwoq said:**
> You patched against meltdown, but not Spectre

How do I patch against Spectre ? By installing the microcode firmware ?

---

### Post by frogotronic on 2018-01-22
Hello,

  On 16.04.3 LTS, most recent kernel in proposed (4.13.0-31-generic) now boots.

```
$ inxi -SCGx
System:    Host: XXXXXXXXX Kernel: 4.13.0-31-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Unity 7.4.5 (Gtk 3.18.9-1ubuntu3.3)
           Distro: Ubuntu 16.04 xenial
CPU:       Dual core Intel Core i7-7500U (-HT-MCP-) cache: 4096 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 11616
           clock speeds: max: 3500 MHz 1: 2900 MHz 2: 2900 MHz 3: 2900 MHz
           4: 2900 MHz
Graphics:  Card: Intel Device 5916 bus-ID: 00:02.0
           Display Server: X.Org 1.19.5 drivers: (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.02hz, 1920x1080@60.00hz
           GLX Renderer: Mesa DRI Intel HD Graphics 620 (Kaby Lake GT2)
           GLX Version: 3.0 Mesa 17.3.2 - padoka PPA Direct Rendering: Yes
```



```
$ sudo ./spectre-meltdown-checker.sh
Spectre and Meltdown mitigation detection tool v0.31

Checking for vulnerabilities against running kernel Linux 4.13.0-31-generic #34~16.04.1-Ubuntu SMP Fri Jan 19 17:11:01 UTC 2018 x86_64
CPU is Intel(R) Core(TM) i7-7500U CPU @ 2.70GHz

CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Checking count of LFENCE opcodes in kernel:  YES 
> STATUS:  NOT VULNERABLE  (114 opcodes found, which is >= 70, heuristic to be improved when official patches become available)

CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Mitigation 1
*   Hardware (CPU microcode) support for mitigation
*     The SPEC_CTRL MSR is available:  NO 
*     The SPEC_CTRL CPUID feature bit is set:  NO 
*   Kernel support for IBRS:  YES 
*   IBRS enabled for Kernel space:  NO 
*   IBRS enabled for User space:  NO 
* Mitigation 2
*   Kernel compiled with retpoline option:  NO 
*   Kernel compiled with a retpoline-aware compiler:  NO 
> STATUS:  VULNERABLE  (IBRS hardware + kernel support OR kernel with retpoline are needed to mitigate the vulnerability)

CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Kernel supports Page Table Isolation (PTI):  YES 
* PTI enabled and active:  YES 
* Checking if we're running under Xen PV (64 bits):  NO 
> STATUS:  NOT VULNERABLE  (PTI mitigates the vulnerability)

A false sense of security is worse than no security at all, see --disclaimer
```

---

### Post by DuckHook on 2018-01-22
> **linuxyogi said:**
> How do I patch against Spectre ? By installing the microcode firmware ?
By patiently waiting until the patched kernel is properly tested and then rolled out in due time. Microcode is already present and is automatically downloaded and updated in most versions and flavours. You can check with:```
apt policy intel-microcode
``` If Intel hasn't gotten around to providing microcode for your CPU, then you'll also just have to wait. If you simply can't wait for the new kernel and know how to handle system breakage, or you want to contribute to testing it, then there are a dozen ways. Some ways are with the following PPAs:

[LIST]
[*]**Mainline kernels:** [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
[*]**Daily builds:** [https://launchpad.net/~kernel-ppa/+archive/ubuntu/ppa](https://launchpad.net/~kernel-ppa/+archive/ubuntu/ppa) Especially note the **warning**:> The quality of these packages is such that you had better know what you're doing. Don't come crying to the kernel team if it kills all of your kittens.
[*]**Pre-release:** [https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/ppa](https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/ppa) **Note**:> This ppa is used for building pre-release and test kernels. It IS NOT RECOMMENDED that you subscribe to this PPA.
[/LIST]
You asked, I answered. However, the general user would be a fool to add these PPAs.

---

### Post by #&amp;thj^% on 2018-01-22
> **DuckHook said:**
> 
You asked, I answered. However, the general user would be a fool to add these PPAs.
Well you found one of the biggest fools here...:popcorn:
I however don't use the ppa's I hand install all my kernels for testing.
Good to see you DH.;)
Take care DuckHook is very wise in his advice.

---

### Post by DuckHook on 2018-01-22
> **1fallen said:**
> Well you found one of the biggest fools here...:popcorn:
To anyone following this thread, don't be fooled by 1fallen''s self-effacing reply. He is the furthest thing from a *general* user. While I strongly caution general users against installing stuff that has high chance of breaking their system, this does not apply to users like 1fallen. If we didn't have testers and power users like 1fallen, those kernels would never get properly tested in the first place.
> I however don't use the ppa's I hand install all my kernels for testing.
…I rest my case.
> Good to see you DH.;)Good to run into you too, buddy.

---

### Post by mc4man on 2018-01-22
> **linuxyogi said:**
> How do I patch against Spectre ? By installing the microcode firmware ?

Some spectre mitigation is via the microcode **&** a matching kernel 
So for example on 16.04 here screen 1 shows more so-called protection on 4.13.0-29-generic vs. screen 2 which is the latest 4.13.0-31-generic.
Overall don't sweat it, over time things will be more complete & settled. Personally can't see why anyone would try a reasonably complex targeted spectre attack against my crappy no nothing laptop..

---

### Post by DuckHook on 2018-01-22
> **mc4man said:**
> …Overall don't sweat it, over time things will be more complete & settled. Personally can't see why anyone would try a reasonably complex targeted spectre attack against my crappy no nothing laptop..
&#8593;&#8593;&#8593;+10

---

### Post by fr33z0n3r on 2018-01-23
today it sounds complex.  And probably is.  But tomorrow?

Does anyone know how stable a system is applying the latest 16.04 kernel update, when you have a CPU not getting any microcode updates?  Does it risk stability?  Or is the bad firmware the ONLY known cause of the stability problems?

---

### Post by DuckHook on 2018-01-23
The real problem with the Spectre vulnerability in particular is that it is very subtle and low level, so is extremely difficult to mitigate. It's not simply patching a hole like it is with most software. There is no magic bullet solution. There will be a *series* of patches that clever developers come up with to forestall exploits from clever crackers. The developers have the additional burden of trying to make sure that those patches don't adversely impact existing apps and usage. But because the exploits are so subtle, that sort of balancing act is very difficult. We already see breakage on these forums (search for VirtualBox 5.0 breaking with the latest kernels).

My guess is that it will always be complex. The microcode updates are only half the solution. Like mc4man states in post 164, you need *both* microcode *and* matching kernel. And even when they both match, it's not really a "solution" in the classical sense. It just raises the bar for the attacker.

With regard to stability: while it isn't as bad as "your guess is as good as mine", it really is impossible to answer your question. Even before this mess, we had occasions when a kernel or microcode update destabilized the system, and that was back when the pressure to push out patches was not as intense as it is now.

I use the following philosophy: keep your data backed up (that's more important now than ever), then apply the patches when they naturally roll out. Don't rush the process by installing kernel PPA's or the latest development kernel. That's just playing Russian roulette. Don't expect the same stability we had before, but have some confidence as well that smart people are working on things and problems will eventually get straightened out. Stop worrying about things that we have no control over and go have a beer.

---

### Post by kostkon on 2018-01-23
> **DuckHook said:**
> Even before this mess, we had occasions when a kernel or microcode update destabilized the system, and that was back when the pressure to push out patches was not as intense as it is now.
[They just reverted]("https://usn.ubuntu.com/usn/usn-3531-2/") the microcode patch for that very reason :(

---

### Post by DuckHook on 2018-01-23
[Intel again.]("https://www.extremetech.com/computing/262647-linus-torvalds-says-intels-spectre-fix-complete-utter-garbage")

Does Intel truly not understand that their namby pamby approach to a really serious problem will come back to haunt them?

Throughout corporate history, from the Tylenol poisoning tragedy to the recent Volkswagon diesel fiasco, the proven damage control strategy—the only one that works—is:

[list=1]
[*]Come clean about the problem.
[*]Apologize.
[*]Fix it.
[/list]
I'm not going to get into the first two. That might morph into Intel-bashing, which would offend the forum CoC that I both agree with and am pledged to defend.

But purely on the technical side: how is Intel's strategy remotely like a fix? Their default is to leave the hole open??? Did I understand that properly??? "Oh, you can close off the security hole if you like, but then, the resulting performance hit is on you!" Really???

At the very least, it should be the other way around. The hole is closed off by default. If you want better performance, you can turn the flag off, but then you are on your own. Don't complain if you get cracked. In fact, I'm not sure that there should even be any choice in the matter. Shouldn't security holes simply be closed—period? I'm not knowledgeable enough in the higher echelons of the computing stratosphere to insist on this last bit. Maybe such a patch would break every supercomputer in the world. Maybe the International Space Station would come plummeting back down to earth. So, I'm not insisting. But, surely, the *default* ought to be "patched" and the *option* ought to be "proceed at your own risk".

Am I missing something?

---

### Post by linuxyogi on 2018-01-24
> **DuckHook said:**
> By patiently waiting until the patched kernel is properly tested and then rolled out in due time. Microcode is already present and is automatically downloaded and updated in most versions and flavours. You can check with:```
apt policy intel-microcode
``` 

I am getting this

```
$ apt policy intel-microcode
intel-microcode:
  Installed: (none)
  Candidate: 3.20180108.1+really20171117.1
  Version table:
     3.20180108.1+really20171117.1 500
        500 http://debian.linux.org.tw/ubuntu bionic/main amd64 Packages
```

---

### Post by espectro2 on 2018-01-25
everything ok in my output I should update some more package this output is without administrative previgelios ie without root or sudo gave this result should I test with root or sudo?
Thanks for listening.

```
Intel-microcode:
  Instalado: 3.20180108.0+really20170707ubuntu16.04.1
  Candidato: 3.20180108.0+really20170707ubuntu16.04.1
  Tabela de versão:
 *** 3.20180108.0+really20170707ubuntu16.04.1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/main amd64 Packages
        100 /var/lib/dpkg/status
     3.20151106.1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/restricted amd64 Packages
```

---

### Post by frogotronic on 2018-01-26
Yep, couldn't agree more.  Should have immediately stopped selling chips through the Xmas season.  Apologised, worked to fix.

---

### Post by frogotronic on 2018-01-26
Hi,

  So, I guess at this point, we need a proper INTEL microcode/firmware update to deal with Spectre Variant 2?  Would that be correct?

Thanks

```
$ lsb_release -a
LSB Version:	core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:printing-9.20160110ubuntu0.2-amd64:printing-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.3 LTS
Release:	16.04
Codename:	xenial
```


```
Spectre and Meltdown mitigation detection tool v0.32

Checking for vulnerabilities on current system
Kernel is Linux 4.13.0-32-generic #35~16.04.1-Ubuntu SMP Thu Jan 25 10:13:43 UTC 2018 x86_64
CPU is Intel(R) Core(TM) i7-7500U CPU @ 2.70GHz

Hardware check
* Hardware support (CPU microcode) for mitigation techniques
  * Indirect Branch Restricted Speculation (IBRS)
    * SPEC_CTRL MSR is available:  NO 
    * CPU indicates IBRS capability:  NO 
  * Indirect Branch Prediction Barrier (IBPB)
    * PRED_CMD MSR is available:  NO 
    * CPU indicates IBPB capability:  NO 
  * Single Thread Indirect Branch Predictors (STIBP)
    * SPEC_CTRL MSR is available:  NO 
    * CPU indicates STIBP capability:  NO 
  * Enhanced IBRS (IBRS_ALL)
    * CPU indicates ARCH_CAPABILITIES MSR availability:  NO 
    * ARCH_CAPABILITIES MSR advertises IBRS_ALL capability:  NO 
  * CPU explicitly indicates not being vulnerable to Meltdown (RDCL_NO):  NO 
* CPU vulnerability to the three speculative execution attacks variants
  * Vulnerable to Variant 1:  YES 
  * Vulnerable to Variant 2:  YES 
  * Vulnerable to Variant 3:  YES 

CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Checking count of LFENCE opcodes in kernel:  YES 
> [COLOR="#008080"]STATUS:  NOT VULNERABLE  (114 opcodes found, which is >= 70, heuristic to be improved when official patches become available)[/COLOR]

CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Mitigation 1
  * Kernel is compiled with IBRS/IBPB support:  YES 
  * Currently enabled features
    * IBRS enabled for Kernel space:  NO  (echo 1 > /proc/sys/kernel/ibrs_enabled)
    * IBRS enabled for User space:  NO  (echo 2 > /proc/sys/kernel/ibrs_enabled)
    * IBPB enabled:  NO  (echo 1 > /proc/sys/kernel/ibpb_enabled)
* Mitigation 2
  * Kernel compiled with retpoline option:  NO 
  * Kernel compiled with a retpoline-aware compiler:  NO 
  * Retpoline enabled:  NO 
> [COLOR="#FF0000"]STATUS:  VULNERABLE  (IBRS hardware + kernel support OR kernel with retpoline are needed to mitigate the vulnerability)[/COLOR]

CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Kernel supports Page Table Isolation (PTI):  YES 
* PTI enabled and active:  YES 
* Running as a Xen PV DomU:  NO 
>[COLOR="#008080"] STATUS:  NOT VULNERABLE  (PTI mitigates the vulnerability)[/COLOR]

A false sense of security is worse than no security at all, see --disclaimer
```

---

### Post by ivanagui2 on 2018-01-27
Hi,

It seems like there won't be 32-bit x86 architecture  Meltdown patched kernels:

> No fix is currently available for Meltdown on 32-bit x86; moving to a 64-bit kernel is the currently recommended mitigation.

[URL="https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown"]https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown
[/URL]
Sigh.

---

### Post by linuxyogi on 2018-01-28
Before installing microcode 

```
$ sudo sh spectre-meltdown-checker.sh 
[sudo] password for xubuntu: 
Spectre and Meltdown mitigation detection tool v0.21

Checking for vulnerabilities against live running kernel Linux 4.14.0-16-generic #19-Ubuntu SMP Mon Jan 8 17:50:31 UTC 2018 x86_64

CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Checking count of LFENCE opcodes in kernel:  NO  (only 42 opcodes found, should be >= 70)
> STATUS:  VULNERABLE  (heuristic to be improved when official patches become available)

CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Mitigation 1
*   Hardware (CPU microcode) support for mitigation:  NO 
*   Kernel support for IBRS:  NO 
*   IBRS enabled for Kernel space:  NO 
*   IBRS enabled for User space:  NO 
* Mitigation 2
*   Kernel compiled with retpoline option:  NO 
*   Kernel compiled with a retpoline-aware compiler:  NO 
> STATUS:  VULNERABLE  (IBRS hardware + kernel support OR kernel with retpoline are needed to mitigate the vulnerability)

CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Kernel supports Page Table Isolation (PTI):  YES 
* PTI enabled and active:  YES 
> STATUS:  NOT VULNERABLE  (PTI mitigates the vulnerability)

A false sense of security is worse than no security at all, see --disclaimer
```




After installing microcode

```
$ sudo sh spectre-meltdown-checker.sh 
[sudo] password for xubuntu: 
Spectre and Meltdown mitigation detection tool v0.21

Checking for vulnerabilities against live running kernel Linux 4.14.0-16-generic #19-Ubuntu SMP Mon Jan 8 17:50:31 UTC 2018 x86_64

CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Checking count of LFENCE opcodes in kernel:  NO  (only 42 opcodes found, should be >= 70)
> STATUS:  VULNERABLE  (heuristic to be improved when official patches become available)

CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Mitigation 1
*   Hardware (CPU microcode) support for mitigation:  NO 
*   Kernel support for IBRS:  NO 
*   IBRS enabled for Kernel space:  NO 
*   IBRS enabled for User space:  NO 
* Mitigation 2
*   Kernel compiled with retpoline option:  NO 
*   Kernel compiled with a retpoline-aware compiler:  NO 
> STATUS:  VULNERABLE  (IBRS hardware + kernel support OR kernel with retpoline are needed to mitigate the vulnerability)

CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Kernel supports Page Table Isolation (PTI):  YES 
* PTI enabled and active:  YES 
> STATUS:  NOT VULNERABLE  (PTI mitigates the vulnerability)

A false sense of security is worse than no security at all, see --disclaimer


```

Kindly have a  look and tell me if I am patched.

---

### Post by lah-ca on 2018-01-28
AMD Speaks

Well spoke ... 4 days ago - the white paper:

[http://www.amd.com/en/corporate/speculative-execution?utm_source=silverpop&utm_medium=email&utm_campaign=32769594&utm_term=button_article2&utm_content=global-component-channel-pru-Jan2018%20(1):&spMailingID=32769594&spUserID=NzMzNTc1NzI4MTkS1&spJobID=1203148707&spReportId=MTIwMzE0ODcwNwS2](http://www.amd.com/en/corporate/speculative-execution?utm_source=silverpop&utm_medium=email&utm_campaign=32769594&utm_term=button_article2&utm_content=global-component-channel-pru-Jan2018%20(1):&spMailingID=32769594&spUserID=NzMzNTc1NzI4MTkS1&spJobID=1203148707&spReportId=MTIwMzE0ODcwNwS2)

---

### Post by mörgæs on 2018-02-01
> **ivanagui2 said:**
> Hi,

It seems like there won't be 32-bit x86 architecture  Meltdown patched kernels:

[URL="https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown"]https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown
[/URL]
Sigh.

There won't for the time being, like there won't for ARM. It's not the same as 'there will never be a patch'. The developers just have to focus on the most common hardware platform first. Please see the first two pages of the thread.

If I have the choice between A) unpatched 32 bit hardware with a theoretical risk of a future attack if Spectre and Meltdown should happen to be exploited some day and B) patched 64 bit hardware with their built in so-called management engines and other kinds of backdoors my choice is A. In fact it's one of the reasons why I keep old hardware alive as long as possible.

---

### Post by corradoventu on 2018-02-02
in [https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/spectre/?field.series_filter=artful](https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/spectre/?field.series_filter=artful) I see a kernel 4.13.0-33.36~retpoline4 
on my Artful I have the PPA and proposed enabled, but still the old kernel also after apt update+upgrade
may you explain that? thanks.
```
corrado@corrado-p6-aa:~$ date
ven  2 feb 2018, 11.36.46, CET
corrado@corrado-p6-aa:~$ inxi -CSx
System:    Host: corrado-p6-aa Kernel: 4.13.0-32-generic x86_64
           bits: 64 gcc: 7.2.0
           Desktop: Gnome 3.26.2 (Gtk 3.22.25-0ubuntu0.1)
           Distro: Ubuntu 17.10
CPU:       Dual core Intel Core i3-7100 (-HT-MCP-) 
           arch: Skylake rev.9 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 15648
           clock speeds: max: 3900 MHz 1: 3900 MHz 2: 3900 MHz 3: 3900 MHz
           4: 3900 MHz
corrado@corrado-p6-aa:~$ sudo apt update
[sudo] password for corrado: 
Hit:1 http://archive.ubuntu.com/ubuntu artful InRelease
Hit:2 http://ppa.launchpad.net/canonical-kernel-team/spectre/ubuntu artful InRelease
Get:3 http://archive.ubuntu.com/ubuntu artful-updates InRelease [78,6 kB]
Get:4 http://archive.ubuntu.com/ubuntu artful-backports InRelease [72,2 kB]
Get:5 http://archive.ubuntu.com/ubuntu artful-security InRelease [78,6 kB]
Get:6 http://archive.ubuntu.com/ubuntu artful-proposed InRelease [235 kB]
Get:7 http://archive.ubuntu.com/ubuntu artful-updates/main i386 Packages [172 kB]
Get:8 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 Packages [174 kB]
Get:9 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 DEP-11 Metadata [73,3 kB]
Get:10 http://archive.ubuntu.com/ubuntu artful-updates/main DEP-11 64x64 Icons [49,2 kB]
Get:11 http://archive.ubuntu.com/ubuntu artful-updates/universe i386 Packages [69,3 kB]
Get:12 http://archive.ubuntu.com/ubuntu artful-updates/universe amd64 Packages [69,8 kB]
Get:13 http://archive.ubuntu.com/ubuntu artful-updates/universe amd64 DEP-11 Metadata [48,5 kB]
Get:14 http://archive.ubuntu.com/ubuntu artful-updates/universe DEP-11 64x64 Icons [49,7 kB]
Get:15 http://archive.ubuntu.com/ubuntu artful-backports/universe i386 Packages [3.396 B]
Get:16 http://archive.ubuntu.com/ubuntu artful-backports/universe amd64 Packages [3.404 B]
Get:17 http://archive.ubuntu.com/ubuntu artful-backports/universe amd64 DEP-11 Metadata [4.712 B]
Get:18 http://archive.ubuntu.com/ubuntu artful-security/main amd64 DEP-11 Metadata [2.924 B]
Get:19 http://archive.ubuntu.com/ubuntu artful-security/universe amd64 DEP-11 Metadata [10,4 kB]
Get:20 http://archive.ubuntu.com/ubuntu artful-security/universe DEP-11 64x64 Icons [10,1 kB]
Get:21 http://archive.ubuntu.com/ubuntu artful-proposed/universe amd64 DEP-11 Metadata [8.556 B]
Get:22 http://archive.ubuntu.com/ubuntu artful-proposed/main amd64 DEP-11 Metadata [6.272 B]
Fetched 1.219 kB in 1s (834 kB/s)                                         
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
corrado@corrado-p6-aa:~$ 

```

---

### Post by mc4man on 2018-02-04
> **corradoventu said:**
> in [https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/spectre/?field.series_filter=artful](https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/spectre/?field.series_filter=artful) I see a kernel 4.13.0-33.36~retpoline4 
on my Artful I have the PPA and proposed enabled, but still the old kernel also after apt update+upgrade
may you explain that? thanks.
```
corrado@corrado-p6-aa:~$ date
ven  2 feb 2018, 11.36.46, CET
corrado@corrado-p6-aa:~$ inxi -CSx
System:    Host: corrado-p6-aa Kernel: 4.13.0-32-generic x86_64
           bits: 64 gcc: 7.2.0
           Desktop: Gnome 3.26.2 (Gtk 3.22.25-0ubuntu0.1)
           Distro: Ubuntu 17.10
CPU:       Dual core Intel Core i3-7100 (-HT-MCP-) 
           arch: Skylake rev.9 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 15648
           clock speeds: max: 3900 MHz 1: 3900 MHz 2: 3900 MHz 3: 3900 MHz
           4: 3900 MHz
corrado@corrado-p6-aa:~$ sudo apt update
[sudo] password for corrado: 
Hit:1 http://archive.ubuntu.com/ubuntu artful InRelease
Hit:2 http://ppa.launchpad.net/canonical-kernel-team/spectre/ubuntu artful InRelease
Get:3 http://archive.ubuntu.com/ubuntu artful-updates InRelease [78,6 kB]
Get:4 http://archive.ubuntu.com/ubuntu artful-backports InRelease [72,2 kB]
Get:5 http://archive.ubuntu.com/ubuntu artful-security InRelease [78,6 kB]
Get:6 http://archive.ubuntu.com/ubuntu artful-proposed InRelease [235 kB]
Get:7 http://archive.ubuntu.com/ubuntu artful-updates/main i386 Packages [172 kB]
Get:8 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 Packages [174 kB]
Get:9 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 DEP-11 Metadata [73,3 kB]
Get:10 http://archive.ubuntu.com/ubuntu artful-updates/main DEP-11 64x64 Icons [49,2 kB]
Get:11 http://archive.ubuntu.com/ubuntu artful-updates/universe i386 Packages [69,3 kB]
Get:12 http://archive.ubuntu.com/ubuntu artful-updates/universe amd64 Packages [69,8 kB]
Get:13 http://archive.ubuntu.com/ubuntu artful-updates/universe amd64 DEP-11 Metadata [48,5 kB]
Get:14 http://archive.ubuntu.com/ubuntu artful-updates/universe DEP-11 64x64 Icons [49,7 kB]
Get:15 http://archive.ubuntu.com/ubuntu artful-backports/universe i386 Packages [3.396 B]
Get:16 http://archive.ubuntu.com/ubuntu artful-backports/universe amd64 Packages [3.404 B]
Get:17 http://archive.ubuntu.com/ubuntu artful-backports/universe amd64 DEP-11 Metadata [4.712 B]
Get:18 http://archive.ubuntu.com/ubuntu artful-security/main amd64 DEP-11 Metadata [2.924 B]
Get:19 http://archive.ubuntu.com/ubuntu artful-security/universe amd64 DEP-11 Metadata [10,4 kB]
Get:20 http://archive.ubuntu.com/ubuntu artful-security/universe DEP-11 64x64 Icons [10,1 kB]
Get:21 http://archive.ubuntu.com/ubuntu artful-proposed/universe amd64 DEP-11 Metadata [8.556 B]
Get:22 http://archive.ubuntu.com/ubuntu artful-proposed/main amd64 DEP-11 Metadata [6.272 B]
Fetched 1.219 kB in 1s (834 kB/s)                                         
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
corrado@corrado-p6-aa:~$ 

```
Did the kernel packages install or not (3), if not then they're not an upgrade but stand-alone meaning you need to specifically install them.
Note that those ppa packages may never get updated or may be determined to not be suitable, ect.

---

### Post by bcschmerker on 2018-02-05
**Concerning CVE-2017-5715, which Kernel series will have Retpoline backported?**  As of February 2018 I've Kernel 4.13.0-32-generic but anticipate availability initially for 4.16.0-5-generic as a HWE-Edge backport from 18.04.0-LTS, when Bionic Beaver is released for distribution, to 16.04.5-LTS.  (AFaIK, 18.01a2 Bionic has 4.16.0-1 as of 5 February 2018, but this will be upgraded through 18.02b1, 18.03b2 and 18.04rc.)

---

### Post by corradoventu on 2018-02-07
On my Artful with PPA from [https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/spectre/?field.series_filter=artful](https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/spectre/?field.series_filter=artful) I have now the new kernel 4.13.0-33 with retpoline mitigations```
corrado@corrado-p6-aa:~$ sudo ./Downloads/spectre-meltdown-checker-master/spectre-meltdown-checker.sh
[sudo] password for corrado: 
Spectre and Meltdown mitigation detection tool v0.34+

Checking for vulnerabilities on current system
Kernel is Linux 4.13.0-33-generic #36-Ubuntu SMP Tue Feb 6 20:30:50 UTC 2018 x86_64
CPU is Intel(R) Core(TM) i3-7100 CPU @ 3.90GHz

Hardware check
* Hardware support (CPU microcode) for mitigation techniques
  * Indirect Branch Restricted Speculation (IBRS)
    * SPEC_CTRL MSR is available:  NO 
    * CPU indicates IBRS capability:  NO 
  * Indirect Branch Prediction Barrier (IBPB)
    * PRED_CMD MSR is available:  NO 
    * CPU indicates IBPB capability:  NO 
  * Single Thread Indirect Branch Predictors (STIBP)
    * SPEC_CTRL MSR is available:  NO 
    * CPU indicates STIBP capability:  NO 
  * Enhanced IBRS (IBRS_ALL)
    * CPU indicates ARCH_CAPABILITIES MSR availability:  NO 
    * ARCH_CAPABILITIES MSR advertises IBRS_ALL capability:  NO 
  * CPU explicitly indicates not being vulnerable to Meltdown (RDCL_NO):  NO 
  * CPU microcode is known to cause stability problems:  NO  (model 158 stepping 9 ucode 0x5e)
* CPU vulnerability to the three speculative execution attacks variants
  * Vulnerable to Variant 1:  YES 
  * Vulnerable to Variant 2:  YES 
  * Vulnerable to Variant 3:  YES 

CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Kernel has array_index_mask_nospec:  NO 
* Checking count of LFENCE instructions following a jump in kernel...  NO  (only 5 jump-then-lfence instructions found, should be >= 30 (heuristic))
> STATUS:  NOT VULNERABLE  (Mitigation: OSB (observable speculation barrier, Intel v6))

CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Mitigation 1
  * Kernel is compiled with IBRS/IBPB support:  NO 
  * Currently enabled features
    * IBRS enabled for Kernel space:  NO 
    * IBRS enabled for User space:  NO 
    * IBPB enabled:  NO 
* Mitigation 2
  * Kernel compiled with retpoline option:  YES 
  * Kernel compiled with a retpoline-aware compiler:  YES  (kernel reports full retpoline compilation)
  * Retpoline enabled:  YES 
> STATUS:  NOT VULNERABLE  (Mitigation: Full generic retpoline)

CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Kernel supports Page Table Isolation (PTI):  YES 
* PTI enabled and active:  YES 
* Running as a Xen PV DomU:  NO 
> STATUS:  NOT VULNERABLE  (Mitigation: PTI)

A false sense of security is worse than no security at all, see --disclaimer
corrado@corrado-p6-aa:~$ 

```

---

### Post by Frogs Hair on 2018-02-07
Protected after kernel update on 17.10.(proposed enabled)

```
uname -a
Linux ubuntu 4.13.0-33-generic #36-Ubuntu SMP Tue Feb 6 20:30:50 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

```
Checking for vulnerabilities against running kernel Linux 4.13.0-33-generic #36-Ubuntu SMP Tue Feb 6 20:30:50 UTC 2018 x86_64
CPU is  Intel(R) Core(TM) i5-2540M CPU @ 2.60GHz


CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Checking whether we're safe according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
> STATUS:  NOT VULNERABLE  (Mitigation: OSB (observable speculation barrier, Intel v6))


CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Checking whether we're safe according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
> STATUS:  NOT VULNERABLE  (Mitigation: Full generic retpoline)


CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Checking whether we're safe according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
> STATUS:  NOT VULNERABLE  (Mitigation: PTI)


A false sense of security is worse than no security at all, see --disclaimer



```

---

### Post by linuxyogi on 2018-02-10
Xubuntu 18.04 (Proposed enabled)
 
```
$ uname -a
Linux xubuntu 4.15.0-9-generic #10-Ubuntu SMP Thu Feb 8 20:22:38 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux 
```

```
$ sudo sh spectre-meltdown-checker.sh 
[sudo] password for xubuntu: 
Spectre and Meltdown mitigation detection tool v0.21

Checking for vulnerabilities against live running kernel Linux 4.15.0-9-generic #10-Ubuntu SMP Thu Feb 8 20:22:38 UTC 2018 x86_64

CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Checking count of LFENCE opcodes in kernel:  YES  (186 opcodes found, which is >= 70)
> STATUS:  NOT VULNERABLE  (heuristic to be improved when official patches become available)

CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Mitigation 1
*   Hardware (CPU microcode) support for mitigation:  NO 
*   Kernel support for IBRS:  NO 
*   IBRS enabled for Kernel space:  NO 
*   IBRS enabled for User space:  NO 
* Mitigation 2
*   Kernel compiled with retpoline option:  YES 
*   Kernel compiled with a retpoline-aware compiler:  NO 
> [COLOR=#ff0000]STATUS:  VULNERABLE  (IBRS hardware + kernel support OR kernel with retpoline are needed to mitigate the vulnerability)
[/COLOR]
CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Kernel supports Page Table Isolation (PTI):  YES 
* PTI enabled and active:  YES 
> STATUS:  NOT VULNERABLE  (PTI mitigates the vulnerability)

A false sense of security is worse than no security at all, see --disclaimer


```

What do you think I should do now ? How do I get rid of this "STATUS:  VULNERABLE" ?

---

### Post by Frogs Hair on 2018-02-10
> [COLOR=#000000][INDENT]What do you think I should do now ? How do I get rid of this "STATUS: VULNERABLE" ?[/INDENT]


[/COLOR]
 

Wait , it took 4 updates  for my cpu to be covered.

---

### Post by #&amp;thj^% on 2018-02-10
> **Frogs Hair said:**
> Wait , it took 4 updates  for my cpu to be covered.

+1
```
sudo sh spectre-meltdown-checker.sh 
Spectre and Meltdown mitigation detection tool v0.32

Checking for vulnerabilities against running kernel Linux 4.15.2-2-ARCH #1 SMP PREEMPT Thu Feb 8 18:54:52 UTC 2018 x86_64
CPU is  Intel(R) Core(TM) i5-6400 CPU @ 2.70GHz

CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Checking whether we're safe according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
> STATUS:  NOT VULNERABLE  (Mitigation: __user pointer sanitization)

CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Checking whether we're safe according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
> STATUS:  NOT VULNERABLE  (Mitigation: Full generic retpoline)

CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Checking whether we're safe according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
> STATUS:  NOT VULNERABLE  (Mitigation: PTI)

A false sense of security is worse than no security at all, see --disclaimer
```
And:
```
grep . /sys/devices/system/cpu/vulnerabilities/*
/sys/devices/system/cpu/vulnerabilities/meltdown:Mitigation: PTI
/sys/devices/system/cpu/vulnerabilities/spectre_v1:Mitigation: __user pointer sanitization
/sys/devices/system/cpu/vulnerabilities/spectre_v2:Mitigation: Full generic retpoline
```

---

### Post by DuckHook on 2018-02-11
@linuxyogi,

Patience is a necessary virtue at this time. I am not covered either, nor is practically anyone else:```
duckhook@Zeus:~/bin$ sudo ./spectre-meltdown-checker.sh
Spectre and Meltdown mitigation detection tool v0.34

Checking for vulnerabilities on current system
Kernel is Linux 4.13.0-32-generic #35-Ubuntu SMP Thu Jan 25 09:13:46 UTC 2018 x86_64
CPU is Intel(R) Core(TM) i7-3930K CPU @ 3.20GHz

Hardware check
* Hardware support (CPU microcode) for mitigation techniques
  * Indirect Branch Restricted Speculation (IBRS)
    * SPEC_CTRL MSR is available:  NO 
    * CPU indicates IBRS capability:  NO 
  * Indirect Branch Prediction Barrier (IBPB)
    * PRED_CMD MSR is available:  NO 
    * CPU indicates IBPB capability:  NO 
  * Single Thread Indirect Branch Predictors (STIBP)
    * SPEC_CTRL MSR is available:  NO 
    * CPU indicates STIBP capability:  NO 
  * Enhanced IBRS (IBRS_ALL)
    * CPU indicates ARCH_CAPABILITIES MSR availability:  NO 
    * ARCH_CAPABILITIES MSR advertises IBRS_ALL capability:  NO 
  * CPU explicitly indicates not being vulnerable to Meltdown (RDCL_NO):  NO 
  * CPU microcode is known to cause stability problems:  NO  (model 45 stepping 7 ucode 0x710)
* CPU vulnerability to the three speculative execution attacks variants
  * Vulnerable to Variant 1:  YES 
  * Vulnerable to Variant 2:  YES 
  * Vulnerable to Variant 3:  YES 

CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Kernel has array_index_mask_nospec:  NO 
* Checking count of LFENCE instructions following a jump in kernel:  YES  (65 jump-then-lfence instructions found, which is >= 30 (heuristic))
> STATUS:  NOT VULNERABLE  (Kernel source has PROBABLY been patched to mitigate the vulnerability (jump-then-lfence instructions heuristic))

CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Mitigation 1
  * Kernel is compiled with IBRS/IBPB support:  YES 
  * Currently enabled features
    * IBRS enabled for Kernel space:  NO 
    * IBRS enabled for User space:  NO 
    * IBPB enabled:  NO 
* Mitigation 2
  * Kernel compiled with retpoline option:  NO 
  * Kernel compiled with a retpoline-aware compiler:  NO 
  * Retpoline enabled:  NO 
> STATUS:  VULNERABLE  (IBRS hardware + kernel support OR kernel with retpoline are needed to mitigate the vulnerability)

CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Kernel supports Page Table Isolation (PTI):  YES 
* PTI enabled and active:  YES 
* Running as a Xen PV DomU:  NO 
> STATUS:  NOT VULNERABLE  (PTI mitigates the vulnerability)
```
In my case, I am running the latest *tested* kernel for Artful (17.10). You must carefully note that both Frogs Hair and 1fallen are running more dangerous kernels. In Frogs Hair's case, he has *proposed* turned on. Do not do this unless you are accustomed to living dangerously with possible breakage in other parts of your system. In 1fallen's case, he compiles his own kernels. This yields essentially a customized install that he is on his own to maintain and update. Both of these gentlemen are very skilled Linux experts. You must assess your own level of expertise and decide if the small theoretical exposure posed by Spectre at this time is worth trading for either potential breakage of your system, or continual need to maintain a personally customized system.

---

### Post by linuxyogi on 2018-02-11
Thanks everyone for the replies. I will simply wait and follow this thread.

---

### Post by frogotronic on 2018-02-15
```
$ lsb_release -a
LSB Version:	core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:printing-9.20160110ubuntu0.2-amd64:printing-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.3 LTS
Release:	16.04
Codename:	xenial
```

```
$ inxi -SCGx
System:    Host: XXXXX Kernel: 4.13.0-35-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Unity 7.4.5 (Gtk 3.18.9-1ubuntu3.3) Distro: Ubuntu 16.04 xenial
CPU:       Dual core Intel Core i7-7500U (-HT-MCP-) cache: 4096 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 11616
           clock speeds: max: 3500 MHz 1: 2900 MHz 2: 2900 MHz 3: 2900 MHz 4: 2900 MHz
Graphics:  Card: Intel Device 5916 bus-ID: 00:02.0
           Display Server: X.Org 1.19.5 drivers: (unloaded: fbdev,vesa) Resolution: 1920x1080@60.02hz
           GLX Renderer: Mesa DRI Intel HD Graphics 620 (Kaby Lake GT2)
           GLX Version: 3.0 Mesa 18.1.0-devel - padoka PPA Direct Rendering: Yes
```

```
Spectre and Meltdown mitigation detection tool v0.34+

Checking for vulnerabilities on current system
Kernel is Linux 4.13.0-35-generic #39~16.04.1-Ubuntu SMP Mon Feb 12 15:02:37 UTC 2018 x86_64
CPU is Intel(R) Core(TM) i7-7500U CPU @ 2.70GHz

Hardware check
* Hardware support (CPU microcode) for mitigation techniques
  * Indirect Branch Restricted Speculation (IBRS)
    * SPEC_CTRL MSR is available:  NO 
    * CPU indicates IBRS capability:  NO 
  * Indirect Branch Prediction Barrier (IBPB)
    * PRED_CMD MSR is available:  NO 
    * CPU indicates IBPB capability:  NO 
  * Single Thread Indirect Branch Predictors (STIBP)
    * SPEC_CTRL MSR is available:  NO 
    * CPU indicates STIBP capability:  NO 
  * Enhanced IBRS (IBRS_ALL)
    * CPU indicates ARCH_CAPABILITIES MSR availability:  NO 
    * ARCH_CAPABILITIES MSR advertises IBRS_ALL capability:  NO 
  * CPU explicitly indicates not being vulnerable to Meltdown (RDCL_NO):  NO 
  * CPU microcode is known to cause stability problems:  NO  (model 142 stepping 9 ucode 0x62)
* CPU vulnerability to the three speculative execution attacks variants
  * Vulnerable to Variant 1:  YES 
  * Vulnerable to Variant 2:  YES 
  * Vulnerable to Variant 3:  YES 

CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Kernel has array_index_mask_nospec:  NO 
* Checking count of LFENCE instructions following a jump in kernel:  YES  (70 jump-then-lfence instructions found, which is >= 30 (heuristic))
> STATUS:  [COLOR="#FF0000"]NOT VULNERABLE[/COLOR]  (Mitigation: OSB (observable speculation barrier, Intel v6))

CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Mitigation 1
  * Kernel is compiled with IBRS/IBPB support:  YES 
  * Currently enabled features
    * IBRS enabled for Kernel space:  NO 
    * IBRS enabled for User space:  NO 
    * IBPB enabled:  NO 
* Mitigation 2
  * Kernel compiled with retpoline option:  YES 
  * Kernel compiled with a retpoline-aware compiler:  YES  (kernel reports full retpoline compilation)
  * Retpoline enabled:  YES 
> STATUS:  [COLOR="#FF0000"]NOT VULNERABLE[/COLOR]  (Mitigation: Full generic retpoline)

CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Kernel supports Page Table Isolation (PTI):  YES 
* PTI enabled and active:  YES 
* Running as a Xen PV DomU:  NO 
> STATUS:  [COLOR="#FF0000"]NOT VULNERABLE[/COLOR]  (Mitigation: PTI)

A false sense of security is worse than no security at all, see --disclaimer
```

---

### Post by corradoventu on 2018-02-21
new intel microcode promoved to production: [https://newsroom.intel.com/wp-content/uploads/sites/11/2018/02/microcode-update-guidance.pdf](https://newsroom.intel.com/wp-content/uploads/sites/11/2018/02/microcode-update-guidance.pdf)
how long do we have to wait? some predictions?

---

### Post by cruzer001 on 2018-02-22
[https://insights.ubuntu.com/2018/01/24/meltdown-spectre-and-ubuntu-what-you-need-to-know/?utm_source=marketo&utm_medium=email&mkt_tok=eyJpIjoiTldJeE16bGlZMkl4TVRoaCIsInQiOiJBdG4ybVMrWnc0Y1FqeGd6c3FSaEwwYjNKc1F6RFdyRml5UDd2SDkxNnhKd3kwekdmXC8yclwvWm5ZTmlpWWNvbjVFM0lSVExnUVBlZ0hlXC80cHhHWEhVeU9FdGlvbk1TcTkrQUtPeTVZMGJaWkxXN2hwT2k0WWw1dlF1YUhpdE0yaCJ9](https://insights.ubuntu.com/2018/01/24/meltdown-spectre-and-ubuntu-what-you-need-to-know/?utm_source=marketo&utm_medium=email&mkt_tok=eyJpIjoiTldJeE16bGlZMkl4TVRoaCIsInQiOiJBdG4ybVMrWnc0Y1FqeGd6c3FSaEwwYjNKc1F6RFdyRml5UDd2SDkxNnhKd3kwekdmXC8yclwvWm5ZTmlpWWNvbjVFM0lSVExnUVBlZ0hlXC80cHhHWEhVeU9FdGlvbk1TcTkrQUtPeTVZMGJaWkxXN2hwT2k0WWw1dlF1YUhpdE0yaCJ9)

---

### Post by DuckHook on 2018-02-22
Kernel 4.13.0-36-generic available as a regular update this morning. These are my results:
```
duckhook@Zeus:~/bin$ sudo ./spectre-meltdown-checker.sh
[sudo] password for duckhook: 
Spectre and Meltdown mitigation detection tool v0.35

Checking for vulnerabilities on current system
Kernel is Linux 4.13.0-36-generic #40-Ubuntu SMP Fri Feb 16 20:07:48 UTC 2018 x86_64
CPU is Intel(R) Core(TM) i7-3930K CPU @ 3.20GHz

Hardware check
* Hardware support (CPU microcode) for mitigation techniques
  * Indirect Branch Restricted Speculation (IBRS)
    * SPEC_CTRL MSR is available:  NO 
    * CPU indicates IBRS capability:  NO 
  * Indirect Branch Prediction Barrier (IBPB)
    * PRED_CMD MSR is available:  NO 
    * CPU indicates IBPB capability:  NO 
  * Single Thread Indirect Branch Predictors (STIBP)
    * SPEC_CTRL MSR is available:  NO 
    * CPU indicates STIBP capability:  NO 
  * Enhanced IBRS (IBRS_ALL)
    * CPU indicates ARCH_CAPABILITIES MSR availability:  NO 
    * ARCH_CAPABILITIES MSR advertises IBRS_ALL capability:  NO 
  * CPU explicitly indicates not being vulnerable to Meltdown (RDCL_NO):  NO 
  * CPU microcode is known to cause stability problems:  NO  (model 45 stepping 7 ucode 0x710)
* CPU vulnerability to the three speculative execution attacks variants
  * Vulnerable to Variant 1:  YES 
  * Vulnerable to Variant 2:  YES 
  * Vulnerable to Variant 3:  YES 

CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Kernel has array_index_mask_nospec:  NO 
* Kernel has the Red Hat/Ubuntu patch:  YES 
> STATUS:  NOT VULNERABLE  (Mitigation: OSB (observable speculation barrier, Intel v6))

CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Mitigation 1
  * Kernel is compiled with IBRS/IBPB support:  YES 
  * Currently enabled features
    * IBRS enabled for Kernel space:  NO 
    * IBRS enabled for User space:  NO 
    * IBPB enabled:  NO 
* Mitigation 2
  * Kernel compiled with retpoline option:  YES 
  * Kernel compiled with a retpoline-aware compiler:  YES  (kernel reports full retpoline compilation)
> STATUS:  NOT VULNERABLE  (Mitigation: Full generic retpoline)

CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Kernel supports Page Table Isolation (PTI):  YES 
* PTI enabled and active:  YES 
* Running as a Xen PV DomU:  NO 
> STATUS:  NOT VULNERABLE  (Mitigation: PTI)

A false sense of security is worse than no security at all, see --disclaimer
```
So… am now waiting for Intel to get around to releasing microcode for my CPU. Many of you may already have new microcode, so your results may look even better.

---

### Post by #&amp;thj^% on 2018-02-22
> **DuckHook said:**
> Kernel 4.13.0-36-generic available as a regular update this morning. These are my results:
```
duckhook@Zeus:~/bin$ sudo ./spectre-meltdown-checker.sh
[sudo] password for duckhook: 
Spectre and Meltdown mitigation detection tool v0.35

Checking for vulnerabilities on current system
Kernel is Linux 4.13.0-36-generic #40-Ubuntu SMP Fri Feb 16 20:07:48 UTC 2018 x86_64
CPU is Intel(R) Core(TM) i7-3930K CPU @ 3.20GHz

Hardware check
* Hardware support (CPU microcode) for mitigation techniques
  * Indirect Branch Restricted Speculation (IBRS)
    * SPEC_CTRL MSR is available:  NO 
    * CPU indicates IBRS capability:  NO 
  * Indirect Branch Prediction Barrier (IBPB)
    * PRED_CMD MSR is available:  NO 
    * CPU indicates IBPB capability:  NO 
  * Single Thread Indirect Branch Predictors (STIBP)
    * SPEC_CTRL MSR is available:  NO 
    * CPU indicates STIBP capability:  NO 
  * Enhanced IBRS (IBRS_ALL)
    * CPU indicates ARCH_CAPABILITIES MSR availability:  NO 
    * ARCH_CAPABILITIES MSR advertises IBRS_ALL capability:  NO 
  * CPU explicitly indicates not being vulnerable to Meltdown (RDCL_NO):  NO 
  * CPU microcode is known to cause stability problems:  NO  (model 45 stepping 7 ucode 0x710)
* CPU vulnerability to the three speculative execution attacks variants
  * Vulnerable to Variant 1:  YES 
  * Vulnerable to Variant 2:  YES 
  * Vulnerable to Variant 3:  YES 

CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Kernel has array_index_mask_nospec:  NO 
* Kernel has the Red Hat/Ubuntu patch:  YES 
> STATUS:  NOT VULNERABLE  (Mitigation: OSB (observable speculation barrier, Intel v6))

CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Mitigation 1
  * Kernel is compiled with IBRS/IBPB support:  YES 
  * Currently enabled features
    * IBRS enabled for Kernel space:  NO 
    * IBRS enabled for User space:  NO 
    * IBPB enabled:  NO 
* Mitigation 2
  * Kernel compiled with retpoline option:  YES 
  * Kernel compiled with a retpoline-aware compiler:  YES  (kernel reports full retpoline compilation)
> STATUS:  NOT VULNERABLE  (Mitigation: Full generic retpoline)

CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Kernel supports Page Table Isolation (PTI):  YES 
* PTI enabled and active:  YES 
* Running as a Xen PV DomU:  NO 
> STATUS:  NOT VULNERABLE  (Mitigation: PTI)

A false sense of security is worse than no security at all, see --disclaimer
```
So… am now waiting for Intel to get around to releasing microcode for my CPU. Many of you may already have new microcode, so your results may look even better.

I'm pretty sure we are all in the same state as you are. I have not seen anyone(AMD, Intel, Arm)  yet pass these:
```
 CPU vulnerability to the three speculative execution attacks variants
  * Vulnerable to Variant 1:  YES 
  * Vulnerable to Variant 2:  YES 
  * Vulnerable to Variant 3:  YES 
```
Even with the new microcode, and Bios Patch's.

---

### Post by DuckHook on 2018-02-22
Hi 1fallen,

I believe that the section of the report you are pointing to refers only to the CPU's native unmitigated vulnerabilities. The new kernel actually mitigates some of these. The operative lines are: ```
&#8230;
> STATUS:  NOT VULNERABLE  (Mitigation: OSB (observable speculation barrier, Intel v6))
&#8230;
> STATUS:  NOT VULNERABLE  (Mitigation: Full generic retpoline)
&#8230;
> STATUS:  NOT VULNERABLE  (Mitigation: PTI)
&#8230;
```

At this point, the section still exposed is Mitigation 1 of Spectre Variant 2:
```
CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Mitigation 1
  * Kernel is compiled with IBRS/IBPB support:  YES 
  * Currently enabled features
    * IBRS enabled for Kernel space:  NO 
    * IBRS enabled for User space:  NO 
    * IBPB enabled:  NO 
```
If I understand things properly, IBRS can only be enabled by a microcode update. The latest kernel is ready to do its part once IBRS is enabled, but that is now up to Intel.

I suppose that there's nothing more that I can really do at this point but go have a beer. It will arrive when it arrives.

---

### Post by SuperFreak on 2018-02-24
Last Kernel update on my Mint 18.3 PC seemed to have mitigated all 3 vulnerabilities (Kernel 4.13.0-36 Generic)

```
CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Checking whether we're safe according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
> STATUS:  NOT VULNERABLE  (Mitigation: OSB (observable speculation barrier, Intel v6))

CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Checking whether we're safe according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
> STATUS:  NOT VULNERABLE  (Mitigation: Full generic retpoline)

CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Checking whether we're safe according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
> STATUS:  NOT VULNERABLE  (Mitigation: PTI)

A false sense of security is worse than no security at all, see --disclaimer

```

---

### Post by bcschmerker on 2018-03-08
**I have results for the just-released Image 4.13.0-37-generic** (as of 8 March 2018) on the Hot Rod gPC™ and its AMD Athlon64® 3500+:

```
Spectre and Meltdown mitigation detection tool v0.35

Checking for vulnerabilities on current system
Kernel is [35mLinux 4.13.0-37-generic #42~16.04.1-Ubuntu SMP Wed Mar 7 16:03:28 UTC 2018 x86_64[0m
CPU is [35mAMD Athlon(tm) 64 Processor 3500+[0m

[1;34mHardware check[0m
* Hardware support (CPU microcode) for mitigation techniques
  * Indirect Branch Restricted Speculation (IBRS)
    * SPEC_CTRL MSR is available: [41m[30m NO [0m
    * CPU indicates IBRS capability: [41m[30m NO [0m
  * Indirect Branch Prediction Barrier (IBPB)
    * PRED_CMD MSR is available: [41m[30m NO [0m
    * CPU indicates IBPB capability: [41m[30m NO [0m
  * Single Thread Indirect Branch Predictors (STIBP)
    * SPEC_CTRL MSR is available: [41m[30m NO [0m
    * CPU indicates STIBP capability: [41m[30m NO [0m
  * Enhanced IBRS (IBRS_ALL)
    * CPU indicates ARCH_CAPABILITIES MSR availability: [41m[30m NO [0m
    * ARCH_CAPABILITIES MSR advertises IBRS_ALL capability: [41m[30m NO [0m
  * CPU explicitly indicates not being vulnerable to Meltdown (RDCL_NO): [44m[30m NO [0m
  * CPU microcode is known to cause stability problems: [44m[30m NO [0m
* CPU vulnerability to the three speculative execution attacks variants
  * Vulnerable to Variant 1: [41m[30m YES [0m
  * Vulnerable to Variant 2: [41m[30m YES [0m
  * Vulnerable to Variant 3: [42m[30m NO [0m

[1;34mCVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'[0m
* Mitigated according to the /sys interface: [42m[30m YES [0m (kernel confirms that the mitigation is active)
* Kernel has array_index_mask_nospec: [41m[30m NO [0m
* Kernel has the Red Hat/Ubuntu patch: [42m[30m YES [0m
> [46m[30mSTATUS:[0m [42m[30m NOT VULNERABLE [0m (Mitigation: OSB (observable speculation barrier, Intel v6))

[1;34mCVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'[0m
* Mitigated according to the /sys interface: [42m[30m YES [0m (kernel confirms that the mitigation is active)
* Mitigation 1
  * Kernel is compiled with IBRS/IBPB support: [42m[30m YES [0m
  * Currently enabled features
    * IBRS enabled for Kernel space: [41m[30m NO [0m
    * IBRS enabled for User space: [41m[30m NO [0m
    * IBPB enabled: [41m[30m NO [0m
* Mitigation 2
  * Kernel compiled with retpoline option: [42m[30m YES [0m
  * Kernel compiled with a retpoline-aware compiler: [42m[30m YES [0m (kernel reports full retpoline compilation)
> [46m[30mSTATUS:[0m [42m[30m NOT VULNERABLE [0m (Mitigation: Full generic retpoline)

[1;34mCVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'[0m
* Mitigated according to the /sys interface: [42m[30m YES [0m (kernel confirms that your CPU is unaffected)
* Kernel supports Page Table Isolation (PTI): [42m[30m YES [0m
* PTI enabled and active: [41m[30m NO [0m
* Running as a Xen PV DomU: [42m[30m NO [0m
> [46m[30mSTATUS:[0m [42m[30m NOT VULNERABLE [0m (your CPU vendor reported your CPU model as not vulnerable)

A false sense of security is worse than no security at all, see --disclaimer
```

Be advised that the original has color-formatting Escape codes.

---

### Post by corradoventu on 2018-03-14
New intel-microcode arrived for Ubuntu Bionic [https://launchpad.net/ubuntu/+source/intel-microcode](https://launchpad.net/ubuntu/+source/intel-microcode)
```
corrado@corrado-p8-bb-0308:~$ apt policy intel-microcode
intel-microcode:
  Installed: (none)
  Candidate: 3.20180312.0~ubuntu18.04.1
  Version table:
     3.20180312.0~ubuntu18.04.1 500
        500 http://archive.ubuntu.com/ubuntu bionic/main amd64 Packages
corrado@corrado-p8-bb-0308:~$ 
```but not automatically installed. Whi?
it seems ok for my cpu Kaby Lake i3-7100 sig 0x000806e9, pf mask 0xc0, 2018-01-21, rev 0x0084, size 98304
Should I install it?

---

### Post by wildmanne39 on 2018-03-14
Here is a PPA for Ubuntu Security Proposed for the intel to mitigate Spectre, still needs more testing, so use at your own risk.

[https://launchpad.net/~ubuntu-security-proposed/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-security-proposed/+archive/ubuntu/ppa)

---

### Post by corradoventu on 2018-03-15
new intel-microcode on bionic```
corrado@corrado-p8-bb-0308:~$ apt policy intel-microcode
intel-microcode:
  Installed: 3.20180312.0~ubuntu18.04.1
  Candidate: 3.20180312.0~ubuntu18.04.1
  Version table:
 *** 3.20180312.0~ubuntu18.04.1 500
        500 http://archive.ubuntu.com/ubuntu bionic/main amd64 Packages
        100 /var/lib/dpkg/status
corrado@corrado-p8-bb-0308:~$ sudo ./spectre-meltdown-checker.sh
[sudo] password for corrado: 
Spectre and Meltdown mitigation detection tool v0.35

Checking for vulnerabilities on current system
Kernel is Linux 4.15.0-12-generic #13-Ubuntu SMP Thu Mar 8 06:24:47 UTC 2018 x86_64
CPU is Intel(R) Core(TM) i3-7100 CPU @ 3.90GHz

Hardware check
* Hardware support (CPU microcode) for mitigation techniques
  * Indirect Branch Restricted Speculation (IBRS)
    * SPEC_CTRL MSR is available:  YES 
    * CPU indicates IBRS capability:  YES  (SPEC_CTRL feature bit)
  * Indirect Branch Prediction Barrier (IBPB)
    * PRED_CMD MSR is available:  YES 
    * CPU indicates IBPB capability:  YES  (SPEC_CTRL feature bit)
  * Single Thread Indirect Branch Predictors (STIBP)
    * SPEC_CTRL MSR is available:  YES 
    * CPU indicates STIBP capability:  YES 
  * Enhanced IBRS (IBRS_ALL)
    * CPU indicates ARCH_CAPABILITIES MSR availability:  NO 
    * ARCH_CAPABILITIES MSR advertises IBRS_ALL capability:  NO 
  * CPU explicitly indicates not being vulnerable to Meltdown (RDCL_NO):  NO 
  * CPU microcode is known to cause stability problems:  NO  (model 158 stepping 9 ucode 0x84)
* CPU vulnerability to the three speculative execution attacks variants
  * Vulnerable to Variant 1:  YES 
  * Vulnerable to Variant 2:  YES 
  * Vulnerable to Variant 3:  YES 

CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Kernel has array_index_mask_nospec:  YES  (1 occurence(s) found of 64 bits array_index_mask_nospec())
* Kernel has the Red Hat/Ubuntu patch:  NO 
> STATUS:  NOT VULNERABLE  (Mitigation: __user pointer sanitization)

CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Mitigation 1
  * Kernel is compiled with IBRS/IBPB support:  NO 
  * Currently enabled features
    * IBRS enabled for Kernel space:  NO 
    * IBRS enabled for User space:  NO 
    * IBPB enabled:  NO 
* Mitigation 2
  * Kernel compiled with retpoline option:  YES 
  * Kernel compiled with a retpoline-aware compiler:  YES  (kernel reports full retpoline compilation)
> STATUS:  NOT VULNERABLE  (Mitigation: Full generic retpoline, IBPB)

CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Kernel supports Page Table Isolation (PTI):  YES 
* PTI enabled and active:  YES 
* Running as a Xen PV DomU:  NO 
> STATUS:  NOT VULNERABLE  (Mitigation: PTI)

A false sense of security is worse than no security at all, see --disclaimer
corrado@corrado-p8-bb-0308:~$ 

```

---

### Post by pqwoerituytrueiwoq on 2018-03-31
> **1fallen said:**
> I'm pretty sure we are all in the same state as you are. I have not seen anyone(AMD, Intel, Arm)  yet pass these:
```
 CPU vulnerability to the three speculative execution attacks variants
  * Vulnerable to Variant 1:  YES 
  * Vulnerable to Variant 2:  YES 
  * Vulnerable to Variant 3:  YES 
```
Even with the new microcode, and Bios Patch's.
ARM you say lets just test my new RPI 3B+
correct me if i am wrong, but that part just means the hardware is vulnerable, meaning you should be using a software level patch right?
```
pi@raspberrypi:/tmp/ram $ sudo sh spectre-meltdown-checker.sh -v
Spectre and Meltdown mitigation detection tool v0.36

Checking for vulnerabilities on current system
Kernel is Linux 4.9.80-v7+ #1098 SMP Fri Mar 9 19:11:42 GMT 2018 armv7l
CPU is ARM v7 model 0xd03
Will use no vmlinux image (accuracy might be reduced)
Will use no kconfig (accuracy might be reduced)
Will use System.map file /proc/kallsyms
We're missing some kernel info (see -v), accuracy might be reduced

Hardware check
* CPU vulnerability to the three speculative execution attack variants
  * Vulnerable to Variant 1:  NO 
  * Vulnerable to Variant 2:  NO 
  * Vulnerable to Variant 3:  NO 

CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Kernel has array_index_mask_nospec:  UNKNOWN  (couldn't check (couldn't find your kernel image in /boot, if you used netboot, this is normal))
* Kernel has the Red Hat/Ubuntu patch:  UNKNOWN  (couldn't check (couldn't find your kernel image in /boot, if you used netboot, this is normal))
* Checking count of LFENCE instructions following a jump in kernel...  UNKNOWN  (couldn't check (couldn't find your kernel image in /boot, if you used netboot, this is normal))
> STATUS:  NOT VULNERABLE  (your CPU vendor reported your CPU model as not vulnerable)

CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Mitigation 1
  * Kernel is compiled with IBRS/IBPB support:  NO 
  * Currently enabled features
    * IBRS enabled for Kernel space:  NO 
    * IBRS enabled for User space:  NO 
    * IBPB enabled:  NO 
* Mitigation 2
  * Kernel compiled with retpoline option:  UNKNOWN  (couldn't read your kernel configuration)
  * Kernel compiled with a retpoline-aware compiler:  NO 
> STATUS:  NOT VULNERABLE  (your CPU vendor reported your CPU model as not vulnerable)

CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Kernel supports Page Table Isolation (PTI):  NO 
* PTI enabled and active:  NO 
* Performance impact if PTI is enabled
  * CPU supports PCID:  NO  (no security impact but performance will be degraded with PTI)
  * CPU supports INVPCID:  NO  (no security impact but performance will be degraded with PTI)
* Running as a Xen PV DomU:  NO 
> STATUS:  NOT VULNERABLE  (your CPU vendor reported your CPU model as not vulnerable)

A false sense of security is worse than no security at all, see --disclaimer
```
Here is my desktop, with a BIOS recent BIOS update
```
Spectre and Meltdown mitigation detection tool v0.36

Checking for vulnerabilities on current system
Kernel is Linux 4.4.0-112-generic #135~14.04.1-Ubuntu SMP Tue Jan 23 20:41:48 UTC 2018 x86_64
CPU is Intel(R) Core(TM) i5-4690K CPU @ 3.50GHz

Hardware check
* Hardware support (CPU microcode) for mitigation techniques
  * Indirect Branch Restricted Speculation (IBRS)
    * SPEC_CTRL MSR is available:  YES 
    * CPU indicates IBRS capability:  YES  (SPEC_CTRL feature bit)
  * Indirect Branch Prediction Barrier (IBPB)
    * PRED_CMD MSR is available:  YES 
    * CPU indicates IBPB capability:  YES  (SPEC_CTRL feature bit)
  * Single Thread Indirect Branch Predictors (STIBP)
    * SPEC_CTRL MSR is available:  YES 
    * CPU indicates STIBP capability:  YES 
  * Enhanced IBRS (IBRS_ALL)
    * CPU indicates ARCH_CAPABILITIES MSR availability:  NO 
    * ARCH_CAPABILITIES MSR advertises IBRS_ALL capability:  NO 
  * CPU explicitly indicates not being vulnerable to Meltdown (RDCL_NO):  NO 
  * CPU microcode is known to cause stability problems:  NO  (model 60 stepping 3 ucode 0x24)
* CPU vulnerability to the three speculative execution attack variants
  * Vulnerable to Variant 1:  YES 
  * Vulnerable to Variant 2:  YES 
  * Vulnerable to Variant 3:  YES 

CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Kernel has array_index_mask_nospec:  NO 
* Kernel has the Red Hat/Ubuntu patch:  YES 
> STATUS:  NOT VULNERABLE  (Kernel source has been patched to mitigate the vulnerability (Red Hat/Ubuntu patch))

CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Mitigation 1
  * Kernel is compiled with IBRS/IBPB support:  YES 
  * Currently enabled features
    * IBRS enabled for Kernel space:  YES 
    * IBRS enabled for User space:  NO 
    * IBPB enabled:  YES 
* Mitigation 2
  * Kernel compiled with retpoline option:  NO 
  * Kernel compiled with a retpoline-aware compiler:  NO 
> STATUS:  NOT VULNERABLE  (IBRS/IBPB are mitigating the vulnerability)

CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Kernel supports Page Table Isolation (PTI):  YES 
* PTI enabled and active:  YES 
* Running as a Xen PV DomU:  NO 
> STATUS:  NOT VULNERABLE  (PTI mitigates the vulnerability)

A false sense of security is worse than no security at all, see --disclaimer

```
here is my laptop (no recent bios update and i do not expect one)
```
Spectre and Meltdown mitigation detection tool v0.36

Checking for vulnerabilities on current system
Kernel is Linux 4.13.0-37-generic #42-Ubuntu SMP Wed Mar 7 14:13:23 UTC 2018 x86_64
CPU is Intel(R) Pentium(R) CPU B970 @ 2.30GHz

Hardware check
* Hardware support (CPU microcode) for mitigation techniques
  * Indirect Branch Restricted Speculation (IBRS)
    * SPEC_CTRL MSR is available:  NO 
    * CPU indicates IBRS capability:  NO 
  * Indirect Branch Prediction Barrier (IBPB)
    * PRED_CMD MSR is available:  NO 
    * CPU indicates IBPB capability:  NO 
  * Single Thread Indirect Branch Predictors (STIBP)
    * SPEC_CTRL MSR is available:  NO 
    * CPU indicates STIBP capability:  NO 
  * Enhanced IBRS (IBRS_ALL)
    * CPU indicates ARCH_CAPABILITIES MSR availability:  NO 
    * ARCH_CAPABILITIES MSR advertises IBRS_ALL capability:  NO 
  * CPU explicitly indicates not being vulnerable to Meltdown (RDCL_NO):  NO 
  * CPU microcode is known to cause stability problems:  NO  (model 42 stepping 7 ucode 0x23)
* CPU vulnerability to the three speculative execution attack variants
  * Vulnerable to Variant 1:  YES 
  * Vulnerable to Variant 2:  YES 
  * Vulnerable to Variant 3:  YES 

CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Kernel has array_index_mask_nospec:  NO 
* Kernel has the Red Hat/Ubuntu patch:  YES 
> STATUS:  NOT VULNERABLE  (Mitigation: OSB (observable speculation barrier, Intel v6))

CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Mitigation 1
  * Kernel is compiled with IBRS/IBPB support:  YES 
  * Currently enabled features
    * IBRS enabled for Kernel space:  NO 
    * IBRS enabled for User space:  NO 
    * IBPB enabled:  NO 
* Mitigation 2
  * Kernel compiled with retpoline option:  YES 
  * Kernel compiled with a retpoline-aware compiler:  YES  (kernel reports full retpoline compilation)
> STATUS:  NOT VULNERABLE  (Mitigation: Full generic retpoline)

CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Kernel supports Page Table Isolation (PTI):  YES 
* PTI enabled and active:  YES 
* Running as a Xen PV DomU:  NO 
> STATUS:  NOT VULNERABLE  (Mitigation: PTI)

A false sense of security is worse than no security at all, see --disclaimer
```

---

### Post by corradoventu on 2018-04-02
On my laptop```
corrado@corrado-HP-p4-bb-0319:~$ inxi -SCx
System:    Host: corrado-HP-p4-bb-0319 Kernel: 4.15.0-13-generic x86_64
           bits: 64 gcc: 7.3.0
           Desktop: Gnome 3.28.0 (Gtk 3.22.29-2ubuntu1)
           Distro: Ubuntu Bionic Beaver (development branch)
CPU:       Dual core Intel Core i5-4210U (-MT-MCP-) 
           arch: Haswell rev.1 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9577
           clock speeds: max: 2700 MHz 1: 1303 MHz 2: 1446 MHz 3: 1209 MHz
           4: 1422 MHz

```
with intel-microcode installed```
corrado@corrado-HP-p4-bb-0319:~$ apt policy intel-microcode
intel-microcode:
  Installed: 3.20180312.0~ubuntu18.04.1
  Candidate: 3.20180312.0~ubuntu18.04.1
  Version table:
 *** 3.20180312.0~ubuntu18.04.1 500
        500 http://archive.ubuntu.com/ubuntu bionic/main amd64 Packages
        100 /var/lib/dpkg/status
corrado@corrado-HP-p4-bb-0319:~$ 

``` spectre-meltdown-checker gived a strange result:```
* Kernel is compiled with IBRS/IBPB support:  YES 
  * Currently enabled features
    * IBRS enabled for Kernel space:  UNKNOWN 
    * IBRS enabled for User space:  UNKNOWN 
    * IBPB enabled:  UNKNOWN 

```
```
corrado@corrado-HP-p4-bb-0319:~$ sudo ./spectre-meltdown-checker.sh
[sudo] password for corrado: 
Spectre and Meltdown mitigation detection tool v0.36+

Checking for vulnerabilities on current system
Kernel is Linux 4.15.0-13-generic #14-Ubuntu SMP Sat Mar 17 13:44:27 UTC 2018 x86_64
CPU is Intel(R) Core(TM) i5-4210U CPU @ 1.70GHz

Hardware check
* Hardware support (CPU microcode) for mitigation techniques
  * Indirect Branch Restricted Speculation (IBRS)
    * SPEC_CTRL MSR is available:  YES 
    * CPU indicates IBRS capability:  YES  (SPEC_CTRL feature bit)
  * Indirect Branch Prediction Barrier (IBPB)
    * PRED_CMD MSR is available:  YES 
    * CPU indicates IBPB capability:  YES  (SPEC_CTRL feature bit)
  * Single Thread Indirect Branch Predictors (STIBP)
    * SPEC_CTRL MSR is available:  YES 
    * CPU indicates STIBP capability:  YES 
  * Enhanced IBRS (IBRS_ALL)
    * CPU indicates ARCH_CAPABILITIES MSR availability:  NO 
    * ARCH_CAPABILITIES MSR advertises IBRS_ALL capability:  NO 
  * CPU explicitly indicates not being vulnerable to Meltdown (RDCL_NO):  NO 
  * CPU microcode is known to cause stability problems:  NO  (model 69 stepping 1 ucode 0x23)
* CPU vulnerability to the three speculative execution attack variants
  * Vulnerable to Variant 1:  YES 
  * Vulnerable to Variant 2:  YES 
  * Vulnerable to Variant 3:  YES 

CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Kernel has array_index_mask_nospec:  YES  (1 occurence(s) found of 64 bits array_index_mask_nospec())
* Kernel has the Red Hat/Ubuntu patch:  NO 
> STATUS:  NOT VULNERABLE  (Mitigation: __user pointer sanitization)

CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Mitigation 1
  * Kernel is compiled with IBRS/IBPB support:  YES 
  * Currently enabled features
    * IBRS enabled for Kernel space:  UNKNOWN 
    * IBRS enabled for User space:  UNKNOWN 
    * IBPB enabled:  UNKNOWN 
* Mitigation 2
  * Kernel has branch predictor hardening (ARM):  NO 
  * Kernel compiled with retpoline option:  YES 
  * Kernel compiled with a retpoline-aware compiler:  YES  (kernel reports full retpoline compilation)
> STATUS:  NOT VULNERABLE  (Mitigation: Full generic retpoline, IBPB, IBRS_FW)

CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Kernel supports Page Table Isolation (PTI):  YES  (found 'CONFIG_PAGE_TABLE_ISOLATION=y')
* PTI enabled and active:  YES 
* Running as a Xen PV DomU:  NO 
> STATUS:  NOT VULNERABLE  (Mitigation: PTI)

A false sense of security is worse than no security at all, see --disclaimer
corrado@corrado-HP-p4-bb-0319:~$ 

```

---

### Post by Bejamin_Hastings on 2018-04-02
Hi

i need some help please with interpreting the results of the speed47 tool. What does it say?

Mainly, my questions are
[LIST]
[*]Does Ubuntu recognize the patched firmware, even though the firmware version is not exposed to the virtual machine (ucode 0xffffffff), but the individual mitigation capability flags seem to be exposed? 
[*]What is the meaning of _*STATUS:  NOT VULNERABLE  (Mitigation: Full generic retpoline, IBPB (Intel v4))*_ for Spectre v2 and it is in any way better than it would be if the firmware wasn't patched? 
[/LIST]
 
system info: 
The system is Sandy Bridge (Core i5-2500) with patched firmware.
Microcode version in the firmware is 0x2d (with Spectre v2 mitigation)
The operating system is Ubuntu server 17.10 with kernel 4.13.0-37-generic running in a virtual machine on Windows Server 2016 with Hyper-V.

```
Spectre and Meltdown mitigation detection tool v0.36+

Checking for vulnerabilities on current system
Kernel is Linux 4.13.0-37-generic #42-Ubuntu SMP Wed Mar 7 14:13:23 UTC 2018 x86_64
CPU is Intel(R) Core(TM) i5-2500 CPU @ 3.30GHz

Hardware check
* Hardware support (CPU microcode) for mitigation techniques
  * Indirect Branch Restricted Speculation (IBRS)
    * SPEC_CTRL MSR is available:  YES
    * CPU indicates IBRS capability:  YES  (SPEC_CTRL feature bit)
  * Indirect Branch Prediction Barrier (IBPB)
    * PRED_CMD MSR is available:  NO
    * CPU indicates IBPB capability:  YES  (SPEC_CTRL feature bit)
  * Single Thread Indirect Branch Predictors (STIBP)
    * SPEC_CTRL MSR is available:  YES
    * CPU indicates STIBP capability:  YES
  * Enhanced IBRS (IBRS_ALL)
    * CPU indicates ARCH_CAPABILITIES MSR availability:  NO
    * ARCH_CAPABILITIES MSR advertises IBRS_ALL capability:  NO
  * CPU explicitly indicates not being vulnerable to Meltdown (RDCL_NO):  NO
  * CPU microcode is known to cause stability problems:  NO  (model 42 stepping 7 ucode 0xffffffff)
* CPU vulnerability to the three speculative execution attack variants
  * Vulnerable to Variant 1:  YES
  * Vulnerable to Variant 2:  YES
  * Vulnerable to Variant 3:  YES

CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Kernel has array_index_mask_nospec:  NO
* Kernel has the Red Hat/Ubuntu patch:  YES
> STATUS:  NOT VULNERABLE  (Mitigation: OSB (observable speculation barrier, Intel v6))

CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Mitigation 1
  * Kernel is compiled with IBRS/IBPB support:  YES
  * Currently enabled features
    * IBRS enabled for Kernel space:  NO
    * IBRS enabled for User space:  NO
    * IBPB enabled:  YES
* Mitigation 2
  * Kernel has branch predictor hardening (ARM):  NO
  * Kernel compiled with retpoline option:  YES
  * Kernel compiled with a retpoline-aware compiler:  YES  (kernel reports full retpoline compilation)
> STATUS:  NOT VULNERABLE  (Mitigation: Full generic retpoline, IBPB (Intel v4))

CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Mitigated according to the /sys interface:  YES  (kernel confirms that the mitigation is active)
* Kernel supports Page Table Isolation (PTI):  YES  (found 'CONFIG_PAGE_TABLE_ISOLATION=y')
* PTI enabled and active:  YES
* Running as a Xen PV DomU:  NO
> STATUS:  NOT VULNERABLE  (Mitigation: PTI)
```

```
root@ownCloud:/tmp# cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 42
model name      : Intel(R) Core(TM) i5-2500 CPU @ 3.30GHz
stepping        : 7
microcode       : 0xffffffff
cpu MHz         : 3300.021
cache size      : 6144 KB
physical id     : 0
siblings        : 4
core id         : 0
cpu cores       : 4
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx rdtscp lm constant_tsc rep_good nopl xtopology cpuid pni pclmulqdq ssse3 cx16 pcid sse4_1 sse4_2 popcnt aes xsave avx hypervisor lahf_lm pti retpoline spec_ctrl xsaveopt
bugs            : cpu_meltdown spectre_v1 spectre_v2
bogomips        : 6600.04
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:
```

---

### Post by corradoventu on 2018-04-22
Intel has published the new microcode revision [https://newsroom.intel.com/wp-content/uploads/sites/11/2018/04/microcode-update-guidance.pdf](https://newsroom.intel.com/wp-content/uploads/sites/11/2018/04/microcode-update-guidance.pdf) and for for some CPUs the microcode will NEVER be updated

---

### Post by bcschmerker on 2018-04-26
**Thanks for the confirmation.**  That shelves the Gateway®/Acer® DX4822-01 desktop proposal for ubuntu® 18.04.0-LTS, as the Wolfdale platform (on which the intel® Pentium Processor® E5300 (FCLGA775) is built) is excluded from the fix, probably due to microarchitectural limitations making restrictions on indirect-branch processing (necessary to mitigate CVE-2017-5715) impossible to implement.  I've decided to repurpose the DX4822 as a mission-specific music hardware for an implementation of Aeolus under ubuntustudio® 18.04.0-LTS; the Creative Laboratories® SB0350 pulled from the Hot Rod gPC™ should have enough outputs in the Creative® E-MU® CA0102.  The main problem now will be an implementation of an Artisan Classic Organs two-manual and pedal console (consistent with input implementation for Milan Digital® Hauptwerk®) with one row of 24 drawknobs above Manual II than can communicate with the DX4822 via IEEE 1394....

---

### Post by lordgallen on 2018-05-26
Is Spectre likely to be intentional by these companies to apease certain government agencies, or is this truely a design flaw, as it is being told to us??

---

### Post by mörgæs on 2018-05-27
The government agencies don't need software to get access to the contents of a suspect's computer. Any modern computer with Intel Management Engine can be monitored remotely. Copy the screen picture, monitor the keys pressed, watch witch applications are running and so on. 

I am not familiar with AMD but I guess that they offer similar 'functionality'.

---

### Post by mohicann on 2018-06-03
I really don't believe these flaws were implemented on purpose. I'm a occasional reader of Bruce Schneier's blog and here is one of his numerous interesting posts : 

[https://www.schneier.com/blog/archives/2018/05/another_spectre.html](https://www.schneier.com/blog/archives/2018/05/another_spectre.html)

IMHO, it was far too risky to implement this kind of vulnerabilities, thinking it won't be discovered by anyone else. I believe in flaws intentionally implemented such as kernel code bugs, the kind of stuff you won't even figure out it could have been possibly done on purpose, such as races conditions, all that things. But yes, it could have been. On the other hand, such critical flaws (spectre, meltdown) that can't even be patched remotely, or in the worse case, that can't even be patched, period, it's something you can't reasonably assume it's been done on purpose, and that everything which has been following has been working exactly as planned. I don't think that shuttles or military devices only use flawless hardwares. Just as I don't believe in God, I won't believe in a more unlikely story.  

To come back to meltdown and spectre, I waited several weeks before patching to a new PTI kernels, as I was using a unofficial fork of Grsecurity, I thought my outer computer boundary was hardened enough to be safe for some months more. But it seems that the team who was in charge of maintaining this Grsecurity fork didn't get over the PTI implementation and gave up. A shame as it was a really a great job done. But I feared much more to let an exploit get through my browser, my torrent client or anything else, than to find out that my computer's been taken over from the inside (kernel exploit such as metldown, etc)...

---

### Post by corradoventu on 2018-06-15
New Vulnerability Variants 3a and 4 also in US security site: [https://www.us-cert.gov/ncas/alerts/TA18-141A](https://www.us-cert.gov/ncas/alerts/TA18-141A)

---

### Post by pqwoerituytrueiwoq on 2018-08-26
Intel has released some new microcode for my CPU:
[https://downloadcenter.intel.com/download/28039/Linux-Processor-Microcode-Data-File?product=80811](https://downloadcenter.intel.com/download/28039/Linux-Processor-Microcode-Data-File?product=80811)
Should I update it myself or will there be a normal update for it?
```
$ sudo ./spectre-meltdown-checker.sh --explain
Spectre and Meltdown mitigation detection tool v0.39+

Checking for vulnerabilities on current system
Kernel is Linux 4.15.0-33-generic #36-Ubuntu SMP Wed Aug 15 16:00:05 UTC 2018 x86_64
CPU is Intel(R) Core(TM) i5-4690K CPU @ 3.50GHz

Hardware check
* Hardware support (CPU microcode) for mitigation techniques
  * Indirect Branch Restricted Speculation (IBRS)
    * SPEC_CTRL MSR is available:  YES 
    * CPU indicates IBRS capability:  YES  (SPEC_CTRL feature bit)
  * Indirect Branch Prediction Barrier (IBPB)
    * PRED_CMD MSR is available:  YES 
    * CPU indicates IBPB capability:  YES  (SPEC_CTRL feature bit)
  * Single Thread Indirect Branch Predictors (STIBP)
    * SPEC_CTRL MSR is available:  YES 
    * CPU indicates STIBP capability:  YES  (Intel STIBP feature bit)
  * Speculative Store Bypass Disable (SSBD)
    * CPU indicates SSBD capability:  NO 
  * L1 data cache invalidation
    * FLUSH_CMD MSR is available:  NO 
  * Enhanced IBRS (IBRS_ALL)
    * CPU indicates ARCH_CAPABILITIES MSR availability:  NO 
    * ARCH_CAPABILITIES MSR advertises IBRS_ALL capability:  NO 
  * CPU explicitly indicates not being vulnerable to Meltdown (RDCL_NO):  NO 
  * CPU explicitly indicates not being vulnerable to Variant 4 (SSB_NO):  NO 
  * Hypervisor indicates host CPU might be vulnerable to RSB underflow (RSBA):  NO 
  * CPU microcode is known to cause stability problems:  NO  (model 0x3c family 0x6 stepping 0x3 ucode 0x24 cpuid 0x306c3)
  * CPU microcode is the latest known available version:  NO  (you have version 0x24 and latest known version is 0x25)
* CPU vulnerability to the speculative execution attack variants
  * Vulnerable to Variant 1:  YES 
  * Vulnerable to Variant 2:  YES 
  * Vulnerable to Variant 3:  YES 
  * Vulnerable to Variant 3a:  YES 
  * Vulnerable to Variant 4:  YES 
  * Vulnerable to Variant l1tf:  YES 

CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Mitigated according to the /sys interface:  YES  (Mitigation: __user pointer sanitization)
* Kernel has array_index_mask_nospec:  YES  (1 occurrence(s) found of x86 64 bits array_index_mask_nospec())
* Kernel has the Red Hat/Ubuntu patch:  NO 
* Kernel has mask_nospec64 (arm64):  NO 
> STATUS:  NOT VULNERABLE  (Mitigation: __user pointer sanitization)

CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Mitigated according to the /sys interface:  YES  (Mitigation: Full generic retpoline, IBPB, IBRS_FW)
* Mitigation 1
  * Kernel is compiled with IBRS support:  YES 
    * IBRS enabled and active:  YES  (for kernel and firmware code)
  * Kernel is compiled with IBPB support:  YES 
    * IBPB enabled and active:  YES 
* Mitigation 2
  * Kernel has branch predictor hardening (arm):  NO 
  * Kernel compiled with retpoline option:  YES 
    * Kernel compiled with a retpoline-aware compiler:  YES  (kernel reports full retpoline compilation)
> STATUS:  NOT VULNERABLE  (Full retpoline + IBPB are mitigating the vulnerability)

CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Mitigated according to the /sys interface:  YES  (Mitigation: PTI)
* Kernel supports Page Table Isolation (PTI):  YES 
  * PTI enabled and active:  YES 
  * Reduced performance impact of PTI:  YES  (CPU supports INVPCID, performance impact of PTI will be greatly reduced)
* Running as a Xen PV DomU:  NO 
> STATUS:  NOT VULNERABLE  (Mitigation: PTI)

CVE-2018-3640 [rogue system register read] aka 'Variant 3a'
* CPU microcode mitigates the vulnerability:  NO 
> STATUS:  VULNERABLE  (an up-to-date CPU microcode is needed to mitigate this vulnerability)

> How to fix: The microcode of your CPU needs to be upgraded to mitigate this vulnerability. This is usually done at boot time by your kernel (the upgrade is not persistent across reboots which is why it's done at each boot). If you're using a distro, make sure you are up to date, as microcode updates are usually shipped alongside with the distro kernel. Availability of a microcode update for you CPU model depends on your CPU vendor. You can usually find out online if a microcode update is available for your CPU by searching for your CPUID (indicated in the Hardware Check section). The microcode update is enough, there is no additional OS, kernel or software change needed.

CVE-2018-3639 [speculative store bypass] aka 'Variant 4'
* Mitigated according to the /sys interface:  NO  (Vulnerable)
* Kernel supports speculation store bypass:  YES  (found in /proc/self/status)
> STATUS:  VULNERABLE  (Your CPU doesn't support SSBD)

> How to fix: Your kernel is recent enough to use the CPU microcode features for mitigation, but your CPU microcode doesn't actually provide the necessary features for the kernel to use. The microcode of your CPU hence needs to be upgraded. This is usually done at boot time by your kernel (the upgrade is not persistent across reboots which is why it's done at each boot). If you're using a distro, make sure you are up to date, as microcode updates are usually shipped alongside with the distro kernel. Availability of a microcode update for you CPU model depends on your CPU vendor. You can usually find out online if a microcode update is available for your CPU by searching for your CPUID (indicated in the Hardware Check section).

CVE-2018-3615/3620/3646 [L1 terminal fault] aka 'Foreshadow & Foreshadow-NG'
* Mitigated according to the /sys interface:  YES  (Mitigation: PTE Inversion; VMX: conditional cache flushes, SMT disabled)
> STATUS:  NOT VULNERABLE  (Mitigation: PTE Inversion; VMX: conditional cache flushes, SMT disabled)

A false sense of security is worse than no security at all, see --disclaimer
$ dmesg | grep microcode
[    0.840992] microcode: sig=0x306c3, pf=0x2, revision=0x24
[    0.841029] microcode: Microcode Update Driver: v2.2.

```
EDIT:
manual update does work:
```

$ cp -r /lib/firmware/intel-ucode intel-ucode.backup
$ sudo cp -r intel-ucode/* /lib/firmware/intel-ucode/
$ echo 1 | sudo tee /sys/devices/system/cpu/microcode/reload
$ dmesg | grep microcode
[    0.840992] microcode: sig=0x306c3, pf=0x2, revision=0x24
[    0.841029] microcode: Microcode Update Driver: v2.2.
[56165.335616] microcode: updated to revision 0x25, date = 2018-04-02
[56165.338238] x86/CPU: CPU features have changed after loading microcode, but might not take effect.
$ sudo ./spectre-meltdown-checker.sh --explain
Spectre and Meltdown mitigation detection tool v0.39+

Checking for vulnerabilities on current system
Kernel is Linux 4.15.0-33-generic #36-Ubuntu SMP Wed Aug 15 16:00:05 UTC 2018 x86_64
CPU is Intel(R) Core(TM) i5-4690K CPU @ 3.50GHz

Hardware check
* Hardware support (CPU microcode) for mitigation techniques
  * Indirect Branch Restricted Speculation (IBRS)
    * SPEC_CTRL MSR is available:  YES 
    * CPU indicates IBRS capability:  YES  (SPEC_CTRL feature bit)
  * Indirect Branch Prediction Barrier (IBPB)
    * PRED_CMD MSR is available:  YES 
    * CPU indicates IBPB capability:  YES  (SPEC_CTRL feature bit)
  * Single Thread Indirect Branch Predictors (STIBP)
    * SPEC_CTRL MSR is available:  YES 
    * CPU indicates STIBP capability:  YES  (Intel STIBP feature bit)
  * Speculative Store Bypass Disable (SSBD)
    * CPU indicates SSBD capability:  YES  (Intel SSBD)
  * L1 data cache invalidation
    * FLUSH_CMD MSR is available:  YES 
  * Enhanced IBRS (IBRS_ALL)
    * CPU indicates ARCH_CAPABILITIES MSR availability:  NO 
    * ARCH_CAPABILITIES MSR advertises IBRS_ALL capability:  NO 
  * CPU explicitly indicates not being vulnerable to Meltdown (RDCL_NO):  NO 
  * CPU explicitly indicates not being vulnerable to Variant 4 (SSB_NO):  NO 
  * Hypervisor indicates host CPU might be vulnerable to RSB underflow (RSBA):  NO 
  * CPU microcode is known to cause stability problems:  NO  (model 0x3c family 0x6 stepping 0x3 ucode 0x25 cpuid 0x306c3)
  * CPU microcode is the latest known available version:  YES  (you have version 0x25 and latest known version is 0x25)
* CPU vulnerability to the speculative execution attack variants
  * Vulnerable to Variant 1:  YES 
  * Vulnerable to Variant 2:  YES 
  * Vulnerable to Variant 3:  YES 
  * Vulnerable to Variant 3a:  YES 
  * Vulnerable to Variant 4:  YES 
  * Vulnerable to Variant l1tf:  YES 

CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Mitigated according to the /sys interface:  YES  (Mitigation: __user pointer sanitization)
* Kernel has array_index_mask_nospec:  YES  (1 occurrence(s) found of x86 64 bits array_index_mask_nospec())
* Kernel has the Red Hat/Ubuntu patch:  NO 
* Kernel has mask_nospec64 (arm64):  NO 
> STATUS:  NOT VULNERABLE  (Mitigation: __user pointer sanitization)

CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Mitigated according to the /sys interface:  YES  (Mitigation: Full generic retpoline, IBPB, IBRS_FW)
* Mitigation 1
  * Kernel is compiled with IBRS support:  YES 
    * IBRS enabled and active:  YES  (for kernel and firmware code)
  * Kernel is compiled with IBPB support:  YES 
    * IBPB enabled and active:  YES 
* Mitigation 2
  * Kernel has branch predictor hardening (arm):  NO 
  * Kernel compiled with retpoline option:  YES 
    * Kernel compiled with a retpoline-aware compiler:  YES  (kernel reports full retpoline compilation)
> STATUS:  NOT VULNERABLE  (Full retpoline + IBPB are mitigating the vulnerability)

CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Mitigated according to the /sys interface:  YES  (Mitigation: PTI)
* Kernel supports Page Table Isolation (PTI):  YES 
  * PTI enabled and active:  YES 
  * Reduced performance impact of PTI:  YES  (CPU supports INVPCID, performance impact of PTI will be greatly reduced)
* Running as a Xen PV DomU:  NO 
> STATUS:  NOT VULNERABLE  (Mitigation: PTI)

CVE-2018-3640 [rogue system register read] aka 'Variant 3a'
* CPU microcode mitigates the vulnerability:  YES 
> STATUS:  NOT VULNERABLE  (your CPU microcode mitigates the vulnerability)

CVE-2018-3639 [speculative store bypass] aka 'Variant 4'
* Mitigated according to the /sys interface:  NO  (Vulnerable)
* Kernel supports speculation store bypass:  YES  (found in /proc/self/status)
> STATUS:  NOT VULNERABLE  (your system provides the necessary tools for software mitigation)

CVE-2018-3615/3620/3646 [L1 terminal fault] aka 'Foreshadow & Foreshadow-NG'
* Mitigated according to the /sys interface:  YES  (Mitigation: PTE Inversion; VMX: conditional cache flushes, SMT disabled)
> STATUS:  NOT VULNERABLE  (Mitigation: PTE Inversion; VMX: conditional cache flushes, SMT disabled)

A false sense of security is worse than no security at all, see --disclaimer

```
Now lets see how much a performance hit it gives...
Well this is a surprise, it loos like it buffed performance, i only did one pass with no rebooting between test, so it is not a good sample size

---

### Post by deadflowr on 2018-08-26
> Intel has released some new microcode for my CPU:
[https://downloadcenter.intel.com/download/28039/Linux-Processor-Microcode-Data-File?product=80811]("https://downloadcenter.intel.com/download/28039/Linux-Processor-Microcode-Data-File?product=80811")
Should I update it myself or will there be a normal update for it?
microcode packages are now dependencies of the linux-generic meta packages.
So whenever the linux-generic or linux-image-generic packages get an update, it should pull in the latest microcode updates.
[https://bugs.launchpad.net/ubuntu/+source/intel-microcode/+bug/1780399]("https://bugs.launchpad.net/ubuntu/+source/intel-microcode/+bug/1780399")

I guess the real question (for me, at least) would probably be the lag time between when intel (or amd) releases the updated microcode and the time it gets updated in Ubuntu's repositories.
I think Ubuntu is trying to keep the microcode as up-to-date as possible, or at least within a reasonable time frame from when the packages is initially released upstream and when it becomes available for regular user updates in Ubuntu's ecosystem.

---

### Post by aminbahgat on 2019-09-15
thank you for sharing it !

---

### Post by corradoventu on 2019-11-13
On my PC meltdown-checker find 2 vulnerabilities on Ubuntu 19.10 with kernel 5.3.0-22-generic
but NO vulnerabilities on Ubuntu 19.04 w kernel 5.0.0-32-generic

```
corrado@corrado-p6-eoan-1017:~$ sudo ./spectre-meltdown-checker.sh
[sudo] password for corrado: 
Spectre and Meltdown mitigation detection tool v0.42

Checking for vulnerabilities on current system
Kernel is Linux 5.3.0-22-generic #24-Ubuntu SMP Sat Nov 9 17:34:30 UTC 2019 x86_64
CPU is Intel(R) Core(TM) i3-7100 CPU @ 3.90GHz

Hardware check
* Hardware support (CPU microcode) for mitigation techniques
  * Indirect Branch Restricted Speculation (IBRS)
    * SPEC_CTRL MSR is available: intel_rapl_msr 20480 0 - Live 0xffffffffc0873000
intel_rapl_common 24576 1 intel_rapl_msr, Live 0xffffffffc0839000
 UNKNOWN  (is msr kernel module available?)
    * CPU indicates IBRS capability:  YES  (SPEC_CTRL feature bit)
  * Indirect Branch Prediction Barrier (IBPB)
    * PRED_CMD MSR is available:  UNKNOWN  (is msr kernel module available?)
    * CPU indicates IBPB capability:  YES  (SPEC_CTRL feature bit)
  * Single Thread Indirect Branch Predictors (STIBP)
    * SPEC_CTRL MSR is available:  UNKNOWN  (is msr kernel module available?)
    * CPU indicates STIBP capability:  YES  (Intel STIBP feature bit)
  * Speculative Store Bypass Disable (SSBD)
    * CPU indicates SSBD capability:  YES  (Intel SSBD)
  * L1 data cache invalidation
    * FLUSH_CMD MSR is available:  UNKNOWN  (is msr kernel module available?)
    * CPU indicates L1D flush capability:  YES  (L1D flush feature bit)
  * Microarchitectural Data Sampling
    * VERW instruction is available:  YES  (MD_CLEAR feature bit)
  * TSX Asynchronous Abort
    * TSX support is available:  NO 
  * Enhanced IBRS (IBRS_ALL)
    * CPU indicates ARCH_CAPABILITIES MSR availability:  NO 
    * ARCH_CAPABILITIES MSR advertises IBRS_ALL capability:  NO 
  * CPU explicitly indicates not being vulnerable to Meltdown/L1TF (RDCL_NO):  NO 
  * CPU explicitly indicates not being vulnerable to Variant 4 (SSB_NO):  NO 
  * CPU/Hypervisor indicates L1D flushing is not necessary on this system:  NO 
  * Hypervisor indicates host CPU might be vulnerable to RSB underflow (RSBA):  NO 
  * CPU explicitly indicates not being vulnerable to Microarchitectural Data Sampling (MDS_NO):  NO 
  * CPU explicitly indicates not being vulnerable to TSX Asynchrnonous Abort (TAA_NO):  NO 
  * CPU supports Software Guard Extensions (SGX):  YES 
  * CPU microcode is known to cause stability problems:  NO  (model 0x9e family 0x6 stepping 0x9 ucode 0xc6 cpuid 0x906e9)
  * CPU microcode is the latest known available version:  YES  (latest version is 0xc6 dated 2019/08/14 according to builtin MCExtractor DB v130 - 2019/11/04)
* CPU vulnerability to the speculative execution attack variants
  * Vulnerable to CVE-2017-5753 (Spectre Variant 1, bounds check bypass):  YES 
  * Vulnerable to CVE-2017-5715 (Spectre Variant 2, branch target injection):  YES 
  * Vulnerable to CVE-2017-5754 (Variant 3, Meltdown, rogue data cache load):  YES 
  * Vulnerable to CVE-2018-3640 (Variant 3a, rogue system register read):  YES 
  * Vulnerable to CVE-2018-3639 (Variant 4, speculative store bypass):  YES 
  * Vulnerable to CVE-2018-3615 (Foreshadow (SGX), L1 terminal fault):  YES 
  * Vulnerable to CVE-2018-3620 (Foreshadow-NG (OS), L1 terminal fault):  YES 
  * Vulnerable to CVE-2018-3646 (Foreshadow-NG (VMM), L1 terminal fault):  YES 
  * Vulnerable to CVE-2018-12126 (Fallout, microarchitectural store buffer data sampling (MSBDS)):  YES 
  * Vulnerable to CVE-2018-12130 (ZombieLoad, microarchitectural fill buffer data sampling (MFBDS)):  YES 
  * Vulnerable to CVE-2018-12127 (RIDL, microarchitectural load port data sampling (MLPDS)):  YES 
  * Vulnerable to CVE-2019-11091 (RIDL, microarchitectural data sampling uncacheable memory (MDSUM)):  YES 
  * Vulnerable to CVE-2019-11135 (Transactional Synchronization Extensions (TSX) Asynchronous Abort (TAA)):  NO 

CVE-2017-5753 aka 'Spectre Variant 1, bounds check bypass'
* Mitigated according to the /sys interface:  YES  (Mitigation: usercopy/swapgs barriers and __user pointer sanitization)
* Kernel has array_index_mask_nospec:  UNKNOWN  (couldn't check (missing 'lzop' tool, please install it, usually it's in the 'lzop' package))
* Kernel has the Red Hat/Ubuntu patch:  UNKNOWN  (couldn't check (missing 'lzop' tool, please install it, usually it's in the 'lzop' package))
* Kernel has mask_nospec64 (arm64):  UNKNOWN  (couldn't check (missing 'lzop' tool, please install it, usually it's in the 'lzop' package))
* Checking count of LFENCE instructions following a jump in kernel...  UNKNOWN  (couldn't check (missing 'lzop' tool, please install it, usually it's in the 'lzop' package))
> STATUS:  NOT VULNERABLE  (Mitigation: usercopy/swapgs barriers and __user pointer sanitization)

CVE-2017-5715 aka 'Spectre Variant 2, branch target injection'
* Mitigated according to the /sys interface:  YES  (Mitigation: Full generic retpoline, IBPB: conditional, IBRS_FW, STIBP: conditional, RSB filling)
* Mitigation 1
  * Kernel is compiled with IBRS support:  YES 
    * IBRS enabled and active:  YES  (for firmware code only)
  * Kernel is compiled with IBPB support:  YES 
    * IBPB enabled and active:  YES 
* Mitigation 2
  * Kernel has branch predictor hardening (arm):  NO 
  * Kernel compiled with retpoline option:  YES 
    * Kernel compiled with a retpoline-aware compiler:  YES  (kernel reports full retpoline compilation)
  * Kernel supports RSB filling:  UNKNOWN  (couldn't check (missing 'lzop' tool, please install it, usually it's in the 'lzop' package))
> STATUS:  VULNERABLE  (IBRS+IBPB or retpoline+IBPB+RSB filling, is needed to mitigate the vulnerability)

CVE-2017-5754 aka 'Variant 3, Meltdown, rogue data cache load'
* Mitigated according to the /sys interface:  YES  (Mitigation: PTI)
* Kernel supports Page Table Isolation (PTI):  YES 
  * PTI enabled and active:  YES 
  * Reduced performance impact of PTI:  YES  (CPU supports INVPCID, performance impact of PTI will be greatly reduced)
* Running as a Xen PV DomU:  NO 
> STATUS:  NOT VULNERABLE  (Mitigation: PTI)

CVE-2018-3640 aka 'Variant 3a, rogue system register read'
* CPU microcode mitigates the vulnerability:  YES 
> STATUS:  NOT VULNERABLE  (your CPU microcode mitigates the vulnerability)

CVE-2018-3639 aka 'Variant 4, speculative store bypass'
* Mitigated according to the /sys interface:  YES  (Mitigation: Speculative Store Bypass disabled via prctl and seccomp)
* Kernel supports disabling speculative store bypass (SSB):  YES  (found in /proc/self/status)
* SSB mitigation is enabled and active:  YES  (per-thread through prctl)
* SSB mitigation currently active for selected processes:  YES  (boltd firefox fwupd geoclue irqbalance ModemManager pulseaudio systemd-journald systemd-logind systemd-resolved systemd-timesyncd systemd-udevd upowerd)
> STATUS:  NOT VULNERABLE  (Mitigation: Speculative Store Bypass disabled via prctl and seccomp)

CVE-2018-3615 aka 'Foreshadow (SGX), L1 terminal fault'
* CPU microcode mitigates the vulnerability:  NO 
> STATUS:  VULNERABLE  (your CPU supports SGX and the microcode is not up to date)

CVE-2018-3620 aka 'Foreshadow-NG (OS), L1 terminal fault'
* Mitigated according to the /sys interface:  YES  (Mitigation: PTE Inversion; VMX: conditional cache flushes, SMT vulnerable)
* Kernel supports PTE inversion: strings: '': No such file
 NO 
* PTE inversion enabled and active:  YES 
> STATUS:  NOT VULNERABLE  (Mitigation: PTE Inversion; VMX: conditional cache flushes, SMT vulnerable)

CVE-2018-3646 aka 'Foreshadow-NG (VMM), L1 terminal fault'
* Information from the /sys interface: Mitigation: PTE Inversion; VMX: conditional cache flushes, SMT vulnerable
* This system is a host running a hypervisor:  NO 
* Mitigation 1 (KVM)
  * EPT is disabled:  NO 
* Mitigation 2
  * L1D flush is supported by kernel:  YES  (found flush_l1d in /proc/cpuinfo)
  * L1D flush enabled:  YES  (conditional flushes)
  * Hardware-backed L1D flush supported:  YES  (performance impact of the mitigation will be greatly reduced)
  * Hyper-Threading (SMT) is enabled:  YES 
> STATUS:  NOT VULNERABLE  (this system is not running a hypervisor)

CVE-2018-12126 aka 'Fallout, microarchitectural store buffer data sampling (MSBDS)'
* Mitigated according to the /sys interface:  YES  (Mitigation: Clear CPU buffers; SMT vulnerable)
* Kernel supports using MD_CLEAR mitigation:  YES  (md_clear found in /proc/cpuinfo)
* Kernel mitigation is enabled and active:  YES 
* SMT is either mitigated or disabled:  NO 
> STATUS:  NOT VULNERABLE  (Your microcode and kernel are both up to date for this mitigation, and mitigation is enabled)

CVE-2018-12130 aka 'ZombieLoad, microarchitectural fill buffer data sampling (MFBDS)'
* Mitigated according to the /sys interface:  YES  (Mitigation: Clear CPU buffers; SMT vulnerable)
* Kernel supports using MD_CLEAR mitigation:  YES  (md_clear found in /proc/cpuinfo)
* Kernel mitigation is enabled and active:  YES 
* SMT is either mitigated or disabled:  NO 
> STATUS:  NOT VULNERABLE  (Your microcode and kernel are both up to date for this mitigation, and mitigation is enabled)

CVE-2018-12127 aka 'RIDL, microarchitectural load port data sampling (MLPDS)'
* Mitigated according to the /sys interface:  YES  (Mitigation: Clear CPU buffers; SMT vulnerable)
* Kernel supports using MD_CLEAR mitigation:  YES  (md_clear found in /proc/cpuinfo)
* Kernel mitigation is enabled and active:  YES 
* SMT is either mitigated or disabled:  NO 
> STATUS:  NOT VULNERABLE  (Your microcode and kernel are both up to date for this mitigation, and mitigation is enabled)

CVE-2019-11091 aka 'RIDL, microarchitectural data sampling uncacheable memory (MDSUM)'
* Mitigated according to the /sys interface:  YES  (Mitigation: Clear CPU buffers; SMT vulnerable)
* Kernel supports using MD_CLEAR mitigation:  YES  (md_clear found in /proc/cpuinfo)
* Kernel mitigation is enabled and active:  YES 
* SMT is either mitigated or disabled:  NO 
> STATUS:  NOT VULNERABLE  (Your microcode and kernel are both up to date for this mitigation, and mitigation is enabled)

CVE-2019-11135 aka 'Transactional Synchronization Extensions (TSX) Asynchronous Abort (TAA)'
* Mitigated according to the /sys interface:  YES  (Not affected)
* TAA mitigation is supported by kernel:  UNKNOWN  (missing 'lzop' tool, please install it, usually it's in the 'lzop' package)
* TAA mitigation enabled and active:  NO 
> STATUS:  NOT VULNERABLE  (your CPU vendor reported your CPU model as not vulnerable)

> SUMMARY: CVE-2017-5753:OK CVE-2017-5715:KO CVE-2017-5754:OK CVE-2018-3640:OK CVE-2018-3639:OK CVE-2018-3615:KO CVE-2018-3620:OK CVE-2018-3646:OK CVE-2018-12126:OK CVE-2018-12130:OK CVE-2018-12127:OK CVE-2019-11091:OK CVE-2019-11135:OK

Need more detailed information about mitigation options? Use --explain
A false sense of security is worse than no security at all, see --disclaimer
corrado@corrado-p6-eoan-1017:~$ 
```

```
corrado@corrado-p5-disco:~$ date
mer 13 nov 2019, 13:46:48, CET
corrado@corrado-p5-disco:~$ 

corrado@corrado-p5-disco:~$ sudo ./spectre-meltdown-checker.sh
Spectre and Meltdown mitigation detection tool v0.42

Checking for vulnerabilities on current system
Kernel is Linux 5.0.0-32-generic #34-Ubuntu SMP Wed Oct 2 02:06:48 UTC 2019 x86_64
CPU is Intel(R) Core(TM) i3-7100 CPU @ 3.90GHz

Hardware check
* Hardware support (CPU microcode) for mitigation techniques
  * Indirect Branch Restricted Speculation (IBRS)
    * SPEC_CTRL MSR is available:  YES 
    * CPU indicates IBRS capability:  YES  (SPEC_CTRL feature bit)
  * Indirect Branch Prediction Barrier (IBPB)
    * PRED_CMD MSR is available:  YES 
    * CPU indicates IBPB capability:  YES  (SPEC_CTRL feature bit)
  * Single Thread Indirect Branch Predictors (STIBP)
    * SPEC_CTRL MSR is available:  YES 
    * CPU indicates STIBP capability:  YES  (Intel STIBP feature bit)
  * Speculative Store Bypass Disable (SSBD)
    * CPU indicates SSBD capability:  YES  (Intel SSBD)
  * L1 data cache invalidation
    * FLUSH_CMD MSR is available:  YES 
    * CPU indicates L1D flush capability:  YES  (L1D flush feature bit)
  * Microarchitectural Data Sampling
    * VERW instruction is available:  YES  (MD_CLEAR feature bit)
  * TSX Asynchronous Abort
    * TSX support is available:  NO 
  * Enhanced IBRS (IBRS_ALL)
    * CPU indicates ARCH_CAPABILITIES MSR availability:  NO 
    * ARCH_CAPABILITIES MSR advertises IBRS_ALL capability:  NO 
  * CPU explicitly indicates not being vulnerable to Meltdown/L1TF (RDCL_NO):  NO 
  * CPU explicitly indicates not being vulnerable to Variant 4 (SSB_NO):  NO 
  * CPU/Hypervisor indicates L1D flushing is not necessary on this system:  NO 
  * Hypervisor indicates host CPU might be vulnerable to RSB underflow (RSBA):  NO 
  * CPU explicitly indicates not being vulnerable to Microarchitectural Data Sampling (MDS_NO):  NO 
  * CPU explicitly indicates not being vulnerable to TSX Asynchrnonous Abort (TAA_NO):  NO 
  * CPU supports Software Guard Extensions (SGX):  YES 
  * CPU microcode is known to cause stability problems:  NO  (model 0x9e family 0x6 stepping 0x9 ucode 0xb4 cpuid 0x906e9)
  * CPU microcode is the latest known available version:  NO  (latest version is 0xc6 dated 2019/08/14 according to builtin MCExtractor DB v130 - 2019/11/04)
* CPU vulnerability to the speculative execution attack variants
  * Vulnerable to CVE-2017-5753 (Spectre Variant 1, bounds check bypass):  YES 
  * Vulnerable to CVE-2017-5715 (Spectre Variant 2, branch target injection):  YES 
  * Vulnerable to CVE-2017-5754 (Variant 3, Meltdown, rogue data cache load):  YES 
  * Vulnerable to CVE-2018-3640 (Variant 3a, rogue system register read):  YES 
  * Vulnerable to CVE-2018-3639 (Variant 4, speculative store bypass):  YES 
  * Vulnerable to CVE-2018-3615 (Foreshadow (SGX), L1 terminal fault):  YES 
  * Vulnerable to CVE-2018-3620 (Foreshadow-NG (OS), L1 terminal fault):  YES 
  * Vulnerable to CVE-2018-3646 (Foreshadow-NG (VMM), L1 terminal fault):  YES 
  * Vulnerable to CVE-2018-12126 (Fallout, microarchitectural store buffer data sampling (MSBDS)):  YES 
  * Vulnerable to CVE-2018-12130 (ZombieLoad, microarchitectural fill buffer data sampling (MFBDS)):  YES 
  * Vulnerable to CVE-2018-12127 (RIDL, microarchitectural load port data sampling (MLPDS)):  YES 
  * Vulnerable to CVE-2019-11091 (RIDL, microarchitectural data sampling uncacheable memory (MDSUM)):  YES 
  * Vulnerable to CVE-2019-11135 (Transactional Synchronization Extensions (TSX) Asynchronous Abort (TAA)):  NO 

CVE-2017-5753 aka 'Spectre Variant 1, bounds check bypass'
* Mitigated according to the /sys interface:  YES  (Mitigation: usercopy/swapgs barriers and __user pointer sanitization)
* Kernel has array_index_mask_nospec:  YES  (1 occurrence(s) found of x86 64 bits array_index_mask_nospec())
* Kernel has the Red Hat/Ubuntu patch:  NO 
* Kernel has mask_nospec64 (arm64):  NO 
> STATUS:  NOT VULNERABLE  (Mitigation: usercopy/swapgs barriers and __user pointer sanitization)

CVE-2017-5715 aka 'Spectre Variant 2, branch target injection'
* Mitigated according to the /sys interface:  YES  (Mitigation: Full generic retpoline, IBPB: conditional, IBRS_FW, STIBP: conditional, RSB filling)
* Mitigation 1
  * Kernel is compiled with IBRS support:  YES 
    * IBRS enabled and active:  YES  (for firmware code only)
  * Kernel is compiled with IBPB support:  YES 
    * IBPB enabled and active:  YES 
* Mitigation 2
  * Kernel has branch predictor hardening (arm):  NO 
  * Kernel compiled with retpoline option:  YES 
    * Kernel compiled with a retpoline-aware compiler:  YES  (kernel reports full retpoline compilation)
  * Kernel supports RSB filling:  YES 
> STATUS:  NOT VULNERABLE  (Full retpoline + IBPB are mitigating the vulnerability)

CVE-2017-5754 aka 'Variant 3, Meltdown, rogue data cache load'
* Mitigated according to the /sys interface:  YES  (Mitigation: PTI)
* Kernel supports Page Table Isolation (PTI):  YES 
  * PTI enabled and active:  YES 
  * Reduced performance impact of PTI:  YES  (CPU supports INVPCID, performance impact of PTI will be greatly reduced)
* Running as a Xen PV DomU:  NO 
> STATUS:  NOT VULNERABLE  (Mitigation: PTI)

CVE-2018-3640 aka 'Variant 3a, rogue system register read'
* CPU microcode mitigates the vulnerability:  YES 
> STATUS:  NOT VULNERABLE  (your CPU microcode mitigates the vulnerability)

CVE-2018-3639 aka 'Variant 4, speculative store bypass'
* Mitigated according to the /sys interface:  YES  (Mitigation: Speculative Store Bypass disabled via prctl and seccomp)
* Kernel supports disabling speculative store bypass (SSB):  YES  (found in /proc/self/status)
* SSB mitigation is enabled and active:  YES  (per-thread through prctl)
* SSB mitigation currently active for selected processes:  YES  (boltd firefox fwupd geoclue irqbalance ModemManager systemd-journald systemd-logind systemd-resolved systemd-timesyncd systemd-udevd upowerd)
> STATUS:  NOT VULNERABLE  (Mitigation: Speculative Store Bypass disabled via prctl and seccomp)

CVE-2018-3615 aka 'Foreshadow (SGX), L1 terminal fault'
* CPU microcode mitigates the vulnerability:  YES 
> STATUS:  NOT VULNERABLE  (your CPU microcode mitigates the vulnerability)

CVE-2018-3620 aka 'Foreshadow-NG (OS), L1 terminal fault'
* Mitigated according to the /sys interface:  YES  (Mitigation: PTE Inversion; VMX: conditional cache flushes, SMT vulnerable)
* Kernel supports PTE inversion:  YES  (found in kernel image)
* PTE inversion enabled and active:  YES 
> STATUS:  NOT VULNERABLE  (Mitigation: PTE Inversion; VMX: conditional cache flushes, SMT vulnerable)

CVE-2018-3646 aka 'Foreshadow-NG (VMM), L1 terminal fault'
* Information from the /sys interface: Mitigation: PTE Inversion; VMX: conditional cache flushes, SMT vulnerable
* This system is a host running a hypervisor:  NO 
* Mitigation 1 (KVM)
  * EPT is disabled:  NO 
* Mitigation 2
  * L1D flush is supported by kernel:  YES  (found flush_l1d in /proc/cpuinfo)
  * L1D flush enabled:  YES  (conditional flushes)
  * Hardware-backed L1D flush supported:  YES  (performance impact of the mitigation will be greatly reduced)
  * Hyper-Threading (SMT) is enabled:  YES 
> STATUS:  NOT VULNERABLE  (this system is not running a hypervisor)

CVE-2018-12126 aka 'Fallout, microarchitectural store buffer data sampling (MSBDS)'
* Mitigated according to the /sys interface:  YES  (Mitigation: Clear CPU buffers; SMT vulnerable)
* Kernel supports using MD_CLEAR mitigation:  YES  (md_clear found in /proc/cpuinfo)
* Kernel mitigation is enabled and active:  YES 
* SMT is either mitigated or disabled:  NO 
> STATUS:  NOT VULNERABLE  (Your microcode and kernel are both up to date for this mitigation, and mitigation is enabled)

CVE-2018-12130 aka 'ZombieLoad, microarchitectural fill buffer data sampling (MFBDS)'
* Mitigated according to the /sys interface:  YES  (Mitigation: Clear CPU buffers; SMT vulnerable)
* Kernel supports using MD_CLEAR mitigation:  YES  (md_clear found in /proc/cpuinfo)
* Kernel mitigation is enabled and active:  YES 
* SMT is either mitigated or disabled:  NO 
> STATUS:  NOT VULNERABLE  (Your microcode and kernel are both up to date for this mitigation, and mitigation is enabled)

CVE-2018-12127 aka 'RIDL, microarchitectural load port data sampling (MLPDS)'
* Mitigated according to the /sys interface:  YES  (Mitigation: Clear CPU buffers; SMT vulnerable)
* Kernel supports using MD_CLEAR mitigation:  YES  (md_clear found in /proc/cpuinfo)
* Kernel mitigation is enabled and active:  YES 
* SMT is either mitigated or disabled:  NO 
> STATUS:  NOT VULNERABLE  (Your microcode and kernel are both up to date for this mitigation, and mitigation is enabled)

CVE-2019-11091 aka 'RIDL, microarchitectural data sampling uncacheable memory (MDSUM)'
* Mitigated according to the /sys interface:  YES  (Mitigation: Clear CPU buffers; SMT vulnerable)
* Kernel supports using MD_CLEAR mitigation:  YES  (md_clear found in /proc/cpuinfo)
* Kernel mitigation is enabled and active:  YES 
* SMT is either mitigated or disabled:  NO 
> STATUS:  NOT VULNERABLE  (Your microcode and kernel are both up to date for this mitigation, and mitigation is enabled)

CVE-2019-11135 aka 'Transactional Synchronization Extensions (TSX) Asynchronous Abort (TAA)'
* TAA mitigation is supported by kernel:  NO 
* TAA mitigation enabled and active:  NO  (tsx_async_abort not found in sysfs hierarchy)
> STATUS:  NOT VULNERABLE  (your CPU vendor reported your CPU model as not vulnerable)

> SUMMARY: CVE-2017-5753:OK CVE-2017-5715:OK CVE-2017-5754:OK CVE-2018-3640:OK CVE-2018-3639:OK CVE-2018-3615:OK CVE-2018-3620:OK CVE-2018-3646:OK CVE-2018-12126:OK CVE-2018-12130:OK CVE-2018-12127:OK CVE-2019-11091:OK CVE-2019-11135:OK

Need more detailed information about mitigation options? Use --explain
A false sense of security is worse than no security at all, see --disclaimer
corrado@corrado-p5-disco:~$ 
```

Opened a problem on github: [https://github.com/speed47/spectre-meltdown-checker/issues/316](https://github.com/speed47/spectre-meltdown-checker/issues/316)
script has been updated, it was a false positive.

---

### Post by kinddolphin8827 on 2022-08-13
You can also always create a bootable persistent thumb drive installation of freedos and place the bios update packages provided by your equipment vender on the aforementioned freedos thumb drive.

---

### Post by martinr on 2023-07-27
On July 25th 2023 Tavis Ormandy, a member of Google's Project Zero security team, disclosed a bug in many of AMD's newer consumer, workstation, and server processors. It is an encryption-breaking, password-leaking bug in many AMD CPUs, which could take months to fix.

The AMD Zen 2 architecture is vulnerable to the so called Zenbleed bug (see [arstechnica.com]("https://arstechnica.com/information-technology/2023/07/encryption-breaking-password-leaking-bug-in-many-amd-cpus-could-take-months-to-fix/"), [CVE-2023-20593]("https://nvd.nist.gov/vuln/detail/CVE-2023-20593"), [AMD Security Bulletin]("https://www.amd.com/en/resources/product-security/bulletin/amd-sb-7008.html") and the [Debian Security Advisory DSA-5459-1]("https://www.debian.org/security/2023/dsa-5459")).
This includes AMD CPUs:

[table]
[tr]
[th]CPU[/th]
[th]Released[/th]
[th]Planned fix[/th]
[th]AGESA version with fixes[/th]
[/tr]
[tr]
[td][strong]Ryzen 3000 (desktop)[/strong][/td]
[td]Mid-2019[/td]
[td]December 2023[/td]
[td]ComboAM4v2PI_1.2.0.C[/td]
[/tr]
[tr]
[td][strong]Ryzen 4000G (desktop)[/strong][/td]
[td]Mid-2020[/td]
[td]December 2023[/td]
[td]ComboAM4v2PI_1.2.0.C[/td]
[/tr]
[tr]
[td][strong]Ryzen 4000 (laptop)[/strong][/td]
[td]Early-mid 2020[/td]
[td]November 2023[/td]
[td]RenoirPI-FP6_1.0.0.D[/td]
[/tr]
[tr]
[td][strong]Ryzen 5700U/5500U/5300U (laptop)[/strong][/td]
[td]Early 2021[/td]
[td]December 2023[/td]
[td]CezannePI-FP6_1.0.1.0[/td]
[/tr]
[tr]
[td][strong]Ryzen 7020 (laptop)[/strong][/td]
[td]Late 2022[/td]
[td]December 2023[/td]
[td]MendocinoPI-FT6_1.0.0.6[/td]
[/tr]
[tr]
[td][strong]Ryzen Threadripper 3000[/strong][/td]
[td]Late 2019[/td]
[td]October 2023[/td]
[td]CastlePeakPI-SP3r3 1.0.0.A[/td]
[/tr]
[tr]
[td][strong]Ryzen Threadripper Pro 3000WX[/strong][/td]
[td]Mid-2020[/td]
[td]November/December 2023[/td]
[td]CastlePeakWSPI-sWRX8 1.0.0.C/ChagallWSPI-sWRX8 1.0.0.7[/td]
[/tr]
[tr]
[td][strong]EPYC 7002[/strong][/td]
[td]Mid-2019[/td]
[td]Patch available[/td]
[td]RomePI 1.0.0.H[/td]
[/tr]
[/tbody]
[/table]

My rig is an Acer Swift 3 SF314-43 laptop with an AMD 5700U SoC / CPU.
I'm running XUbuntu 22.04 LTS. 

How can I check the AGESA version currently active on my laptop from within Ubuntu?

When I check my XUbuntu for vulnerability for the Zenbleed bug with the [spectre-meltdown-checker]("https://github.com/speed47/spectre-meltdown-checker").
Then I get:
```

CVE-2023-20593 aka 'Zenbleed, cross-process information leak'
Zenbleed mitigation is supported by kernel:  NOZenbleed kernel mitigation enabled and active:  NO  (FP_BACKUP_FIX is cleared in DE_CFG)
Zenbleed mitigation is supported by CPU microcode:  NO
STATUS:  VULNERABLE  (Your kernel is too old to mitigate Zenbleed and your CPU microcode doesn't mitigate it either)

```

Which confirms it's vulnerable. 

Before I bought this rig I tried to check vulnerability for the spectre and meltdown bugs, but couldn't find any information.

AMD plans to release a firmware fix by December, the motherboard or PC manufacturer will be responsible for distributing the update.

As I understand the vulnerability should be fixed in microcode which is to be released via a Firmware / BIOS update by my manufacturer Acer. Now Acer is terrible at releasing updated Firmware / BIOS code fixes even for brand new laptops.

But the [Debian Security Advisory DSA-5459-1]("https://www.debian.org/security/2023/dsa-5459") seems to be mentioning a fix already. =d>

The Debian fix is inside the [amd64-microcode]("https://packages.debian.org/search?searchon=sourcenames&keywords=amd64-microcode") package according to the [Debian Security Advisory]("https://www.debian.org/security/2023/dsa-5459")
Now what has always riddled me is the [amd64-microcode]("https://packages.debian.org/search?searchon=sourcenames&keywords=amd64-microcode") package in Ubuntu / Debian.
Did Debian patch the processor's microcode even before AMD were able to provide a patch (which is scheduled for December 2023)?
Is such a patch persistent to the microcode on my laptop or is it lost after a reboot to lets say Windows (it's a dual boot machine)?

How does the microcode package work?
Is the fix to microcode transitorilly installed at each boot of Ubuntu and lost from (microcode-)memory when shut down?

---

### Post by #&amp;thj^% on 2023-07-27
> **martinr said:**
> On July 25th 2023 Tavis Ormandy, a member of Google's Project Zero security team, disclosed a bug in many of AMD's newer consumer, workstation, and server processors. It is an encryption-breaking, password-leaking bug in many AMD CPUs, which could take months to fix.

The AMD Zen 2 architecture is vulnerable to the so called Zenbleed bug (see [arstechnica.com]("https://arstechnica.com/information-technology/2023/07/encryption-breaking-password-leaking-bug-in-many-amd-cpus-could-take-months-to-fix/"), [CVE-2023-20593]("https://nvd.nist.gov/vuln/detail/CVE-2023-20593"), [AMD Security Bulletin]("https://www.amd.com/en/resources/product-security/bulletin/amd-sb-7008.html") and the [Debian Security Advisory DSA-5459-1]("https://www.debian.org/security/2023/dsa-5459")).
This includes AMD CPUs:

[table]
[tr]
[th]CPU[/th]
[th]Released[/th]
[th]Planned fix[/th]
[th]AGESA version with fixes[/th]
[/tr]
[tr]
[td][strong]Ryzen 3000 (desktop)[/strong][/td]
[td]Mid-2019[/td]
[td]December 2023[/td]
[td]ComboAM4v2PI_1.2.0.C[/td]
[/tr]
[tr]
[td][strong]Ryzen 4000G (desktop)[/strong][/td]
[td]Mid-2020[/td]
[td]December 2023[/td]
[td]ComboAM4v2PI_1.2.0.C[/td]
[/tr]
[tr]
[td][strong]Ryzen 4000 (laptop)[/strong][/td]
[td]Early-mid 2020[/td]
[td]November 2023[/td]
[td]RenoirPI-FP6_1.0.0.D[/td]
[/tr]
[tr]
[td][strong]Ryzen 5700U/5500U/5300U (laptop)[/strong][/td]
[td]Early 2021[/td]
[td]December 2023[/td]
[td]CezannePI-FP6_1.0.1.0[/td]
[/tr]
[tr]
[td][strong]Ryzen 7020 (laptop)[/strong][/td]
[td]Late 2022[/td]
[td]December 2023[/td]
[td]MendocinoPI-FT6_1.0.0.6[/td]
[/tr]
[tr]
[td][strong]Ryzen Threadripper 3000[/strong][/td]
[td]Late 2019[/td]
[td]October 2023[/td]
[td]CastlePeakPI-SP3r3 1.0.0.A[/td]
[/tr]
[tr]
[td][strong]Ryzen Threadripper Pro 3000WX[/strong][/td]
[td]Mid-2020[/td]
[td]November/December 2023[/td]
[td]CastlePeakWSPI-sWRX8 1.0.0.C/ChagallWSPI-sWRX8 1.0.0.7[/td]
[/tr]
[tr]
[td][strong]EPYC 7002[/strong][/td]
[td]Mid-2019[/td]
[td]Patch available[/td]
[td]RomePI 1.0.0.H[/td]
[/tr]
[/tbody]
[/table]

My rig is an Acer Swift 3 SF314-43 laptop with an AMD 5700U SoC / CPU.
I'm running XUbuntu 22.04 LTS. 

How can I check the AGESA version currently active on my laptop from within Ubuntu?

When I check my XUbuntu for vulnerability for the Zenbleed bug with the [spectre-meltdown-checker]("https://github.com/speed47/spectre-meltdown-checker").
Then I get:
```

CVE-2023-20593 aka 'Zenbleed, cross-process information leak'
Zenbleed mitigation is supported by kernel:  NOZenbleed kernel mitigation enabled and active:  NO  (FP_BACKUP_FIX is cleared in DE_CFG)
Zenbleed mitigation is supported by CPU microcode:  NO
STATUS:  VULNERABLE  (Your kernel is too old to mitigate Zenbleed and your CPU microcode doesn't mitigate it either)

```

Which confirms it's vulnerable. 

Before I bought this rig I tried to check vulnerability for the spectre and meltdown bugs, but couldn't find any information.

AMD plans to release a firmware fix by December, the motherboard or PC manufacturer will be responsible for distributing the update.

As I understand the vulnerability should be fixed in microcode which is to be released via a Firmware / BIOS update by my manufacturer Acer. Now Acer is terrible at releasing updated Firmware / BIOS code fixes even for brand new laptops.

But the [Debian Security Advisory DSA-5459-1]("https://www.debian.org/security/2023/dsa-5459") seems to be mentioning a fix already. =d>

The Debian fix is inside the [amd64-microcode]("https://packages.debian.org/search?searchon=sourcenames&keywords=amd64-microcode") package according to the [Debian Security Advisory]("https://www.debian.org/security/2023/dsa-5459")
Now what has always riddled me is the [amd64-microcode]("https://packages.debian.org/search?searchon=sourcenames&keywords=amd64-microcode") package in Ubuntu / Debian.
Did Debian patch the processor's microcode even before AMD were able to provide a patch (which is scheduled for December 2023)?
Is such a patch persistent to the microcode on my laptop or is it lost after a reboot to lets say Windows (it's a dual boot machine)?

How does the microcode package work?
Is the fix to microcode transitorilly installed at each boot of Ubuntu and lost from (microcode-)memory when shut down?

This could end up as a very very long post, and I'll try to explain briefly. (This was explained to me by a couple of the Developers)

The origin of the word firmware is a mid-point between hardware and software - software embedded on hardware. It refers to software that is stored in non-volatile memory (such as ROM, EEPROM or Flash memory) on a hardware device, and is used by the device itself.

It's becoming more common in some types of hardware for its "firmware" to be stored in driver software and loaded onto the device when it's booted/initialized, instead of leaving it permanently on the device. It's not a big deal nowadays, for example, to store a few hundred KB of firmware code in a software driver loaded onto the host OS, and to send that down to the device as it's initialized by the driver.

Microcode is a subset of this. Microcode is not a generic term for all firmware that is loaded onto a device at boot. Instead, it's specific to CPUs, where the microcode forms the translation layer between higher level standard CPU instructions and the lower-level operations specific to that CPU. It may be loaded onto the CPU at boot, by the BIOS, and replaced later in the boot stage by the OS as well.

PLEASE NOTE:  that unlike Spectre, Meltdown cannot be fixed with microcode updates alone and requires changes to core OS functionality, which may reduce performance even further. (This has not effected mine much at all)

Yes, microcode is basically firmware that runs on the processor. The special term "microcode" specifically refers to the firmware on a processor that contains the blueprint for translating from standard machine language to low level processor instructions. So it is a more specific term than firmware.

Oh to answer your question "How can I check the AGESA version currently active on my laptop from within Ubuntu"

It's a utility built into the BIOS of later AMD platforms.
(AMD Generic Encapsulated Software Architecture) - basically controls CPU, RAM etc. It's updated by updating your BIOS.
 

It's a utility built into the BIOS of later AMD platforms.
(AMD Generic Encapsulated Software Architecture) - basically controls CPU, RAM etc. It's updated by updating your BIOS.

---

### Post by martinr on 2023-07-27
> **1fallen said:**
> This could end up as a very very long post, and I'll try to explain briefly. (This was explained to me by a couple of the Developers)
...
It's becoming more common in some types of hardware for its "firmware" to be stored in driver software and loaded onto the device when it's booted/initialized, instead of leaving it permanently on the device. It's not a big deal nowadays, for example, to store a few hundred KB of firmware code in a software driver loaded onto the host OS, and to send that down to the device as it's initialized by the driver.

Microcode is a subset of this. Microcode is not a generic term for all firmware that is loaded onto a device at boot. Instead, it's specific to CPUs, where the microcode forms the translation layer between higher level standard CPU instructions and the lower-level operations specific to that CPU. It may be loaded onto the CPU at boot, by the BIOS, and replaced later in the boot stage by the OS as well.

Oh to answer your question "How can I check the AGESA version currently active on my laptop from within Ubuntu"

It's a utility built into the BIOS of later AMD platforms.
(AMD Generic Encapsulated Software Architecture) - basically controls CPU, RAM etc. It's updated by updating your BIOS.


Thank you for your reply, can you get specific about the AMD 5700U SoC / CPU?

I always thought that micro code updates arrived in sealed blobs by Intel for Intel CPU's and assumed the same held true for AMD processors. So only AMD or Intel can make microcode updates that can be installed on their CPUs. Does this still hold true for the AMD 5700U?

If I understand you correctly then the amd64-microcode package can undo any microcode updates that are present in and installed by the UEFI Firmware (former BIOS on the fly at every boot). (Doesn't this bypass secure boot?)

When the OS boots, the microcode has to have been initialized already, hasn't it? Can it really be initialized again by the OS? The OS code runs on the very CPU that has to be re-initialized with new microcode.

Now I really don't understand how Debian can have patched amd64-microcode for the Zenbleed vulnerability already, whilst AMD still have to come up with a fix? And how the microcode can be reinitialized on an already running CPU.

Regarding finding out the AGESA version,  I have an Insyde H2O UEFI Firmware interface (former BIOS), which doesn't reveal the AGESA version in any visible menus. Is there another way to determine it from within Ubuntu?

> 
Handy list of abbreviations:

AGESA = AMD’s Generic Encapsulated Software Architecture
APU = AMD Accelerated Processing Unit, general purpose processors that feature integrated graphics processors
BIOS = Basic Input/Output Systen (is a legacy term that nowadays denotes UEFI firmware code)
MCU = CPU Microcode
PI = Platform Initialization
PSP = Platform Security Processor (the PSP itself is a simple ARM Cortex processor core)
SMU = System Management Unit
SoC = System on a Chip


---

### Post by #&amp;thj^% on 2023-07-27
The time and effort needed to execute exploit is mind numbing. (You would have to have something they really really wanted)
But I can only speak about mine here in this thread.
```
sudo inxi -CsM
[sudo] password for me: 
Machine:
  Type: Laptop System: LENOVO product: 82B5 v: Lenovo Legion 5 15ARH05
    serial: PF29L70E
  Mobo: LENOVO model: LNVNB161216 v: SDK0J40709 WIN serial: <Snip>
    UEFI: LENOVO v: EUCN37WW date: 04/14/2022
CPU:
  Info: 6-core model: AMD Ryzen 5 4600H with Radeon Graphics bits: 64
    type: MT MCP cache: L2: 3 MiB
  Speed (MHz): avg: 1558 min/max: 1400/3000 cores: 1: 1400 2: 1400 3: 1400
    4: 1400 5: 1700 6: 3000 7: 1400 8: 1400 9: 1400 10: 1400 11: 1400 12: 1400
Sensors:
  System Temperatures: cpu: 46.8 C mobo: N/A gpu: nvidia temp: 37 C
  Fan Speeds (RPM): N/A

```
```
Spectre and Meltdown mitigation detection tool v0.46

Checking for vulnerabilities on current system
Kernel is Linux 6.2.0-25-generic #25-Ubuntu SMP PREEMPT_DYNAMIC Fri Jun 16 17:05:07 UTC 2023 x86_64
CPU is AMD Ryzen 5 4600H with Radeon Graphics

Hardware check
* Hardware support (CPU microcode) for mitigation techniques
  * Indirect Branch Restricted Speculation (IBRS)
    * SPEC_CTRL MSR is available:  YES 
    * CPU indicates IBRS capability:  YES  (IBRS_SUPPORT feature bit)
    * CPU indicates preferring IBRS always-on:  NO 
    * CPU indicates preferring IBRS over retpoline:  YES 
  * Indirect Branch Prediction Barrier (IBPB)
    * CPU indicates IBPB capability:  YES  (IBPB_SUPPORT feature bit)
  * Single Thread Indirect Branch Predictors (STIBP)
    * SPEC_CTRL MSR is available:  YES 
    * CPU indicates STIBP capability:  YES  (AMD STIBP feature bit)
    * CPU indicates preferring STIBP always-on:  NO 
  * Speculative Store Bypass Disable (SSBD)
    * CPU indicates SSBD capability:  YES  (AMD SSBD in SPEC_CTRL)
  * L1 data cache invalidation
    * CPU indicates L1D flush capability:  NO 
  * CPU supports Transactional Synchronization Extensions (TSX):  NO 
  * CPU supports Software Guard Extensions (SGX):  NO 
  * CPU supports Special Register Buffer Data Sampling (SRBDS):  NO 
  * CPU microcode is known to fix Zenbleed:  NO  (required version: 0x0860010b)
  * CPU microcode is known to cause stability problems:  NO  (family 0x17 model 0x60 stepping 0x1 ucode 0x8600106 cpuid 0x860f01)
  * CPU microcode is the latest known available version:  NO  (latest version is 0x8600109 dated 2022/03/28 according to builtin firmwares DB v271+i20230614)
* CPU vulnerability to the speculative execution attack variants
  * Affected by CVE-2017-5753 (Spectre Variant 1, bounds check bypass):  YES 
  * Affected by CVE-2017-5715 (Spectre Variant 2, branch target injection):  YES 
  * Affected by CVE-2017-5754 (Variant 3, Meltdown, rogue data cache load):  NO 
  * Affected by CVE-2018-3640 (Variant 3a, rogue system register read):  NO 
  * Affected by CVE-2018-3639 (Variant 4, speculative store bypass):  YES 
  * Affected by CVE-2018-3615 (Foreshadow (SGX), L1 terminal fault):  NO 
  * Affected by CVE-2018-3620 (Foreshadow-NG (OS), L1 terminal fault):  NO 
  * Affected by CVE-2018-3646 (Foreshadow-NG (VMM), L1 terminal fault):  NO 
  * Affected by CVE-2018-12126 (Fallout, microarchitectural store buffer data sampling (MSBDS)):  NO 
  * Affected by CVE-2018-12130 (ZombieLoad, microarchitectural fill buffer data sampling (MFBDS)):  NO 
  * Affected by CVE-2018-12127 (RIDL, microarchitectural load port data sampling (MLPDS)):  NO 
  * Affected by CVE-2019-11091 (RIDL, microarchitectural data sampling uncacheable memory (MDSUM)):  NO 
  * Affected by CVE-2019-11135 (ZombieLoad V2, TSX Asynchronous Abort (TAA)):  NO 
  * Affected by CVE-2018-12207 (No eXcuses, iTLB Multihit, machine check exception on page size changes (MCEPSC)):  NO 
  * Affected by CVE-2020-0543 (Special Register Buffer Data Sampling (SRBDS)):  NO 
  * Affected by CVE-2023-20593 (Zenbleed, cross-process information leak):  YES 

CVE-2017-5753 aka 'Spectre Variant 1, bounds check bypass'
* Mitigated according to the /sys interface:  YES  (Mitigation: usercopy/swapgs barriers and __user pointer sanitization)
* Kernel has array_index_mask_nospec:  YES  (1 occurrence(s) found of x86 64 bits array_index_mask_nospec())
* Kernel has the Red Hat/Ubuntu patch:  NO 
* Kernel has mask_nospec64 (arm64):  NO 
* Kernel has array_index_nospec (arm64):  NO 
> STATUS:  NOT VULNERABLE  (Mitigation: usercopy/swapgs barriers and __user pointer sanitization)

CVE-2017-5715 aka 'Spectre Variant 2, branch target injection'
* Mitigated according to the /sys interface:  YES  (Mitigation: Retpolines, IBPB: conditional, STIBP: always-on, RSB filling, PBRSB-eIBRS: Not affected)
* Mitigation 1
  * Kernel is compiled with IBRS support:  YES 
    * IBRS enabled and active:  UNKNOWN 
  * Kernel is compiled with IBPB support:  YES 
    * IBPB enabled and active:  YES 
* Mitigation 2
  * Kernel has branch predictor hardening (arm):  NO 
  * Kernel compiled with retpoline option:  YES 
    * Kernel compiled with a retpoline-aware compiler:  YES  (kernel reports full retpoline compilation)
> STATUS:  NOT VULNERABLE  (Full retpoline + IBPB are mitigating the vulnerability)

CVE-2017-5754 aka 'Variant 3, Meltdown, rogue data cache load'
* Mitigated according to the /sys interface:  YES  (Not affected)
* Kernel supports Page Table Isolation (PTI):  YES 
  * PTI enabled and active:  NO 
  * Reduced performance impact of PTI:  NO  (PCID/INVPCID not supported, performance impact of PTI will be significant)
* Running as a Xen PV DomU:  NO 
> STATUS:  NOT VULNERABLE  (your CPU vendor reported your CPU model as not affected)

CVE-2018-3640 aka 'Variant 3a, rogue system register read'
* CPU microcode mitigates the vulnerability:  YES 
> STATUS:  NOT VULNERABLE  (your CPU vendor reported your CPU model as not affected)

CVE-2018-3639 aka 'Variant 4, speculative store bypass'
* Mitigated according to the /sys interface:  YES  (Mitigation: Speculative Store Bypass disabled via prctl)
* Kernel supports disabling speculative store bypass (SSB):  YES  (found in /proc/self/status)
* SSB mitigation is enabled and active:  YES  (per-thread through prctl)
* SSB mitigation currently active for selected processes:  NO  (no process found using SSB mitigation through prctl)
> STATUS:  NOT VULNERABLE  (Mitigation: Speculative Store Bypass disabled via prctl)

CVE-2018-3615 aka 'Foreshadow (SGX), L1 terminal fault'
* CPU microcode mitigates the vulnerability:  N/A 
> STATUS:  NOT VULNERABLE  (your CPU vendor reported your CPU model as not affected)

CVE-2018-3620 aka 'Foreshadow-NG (OS), L1 terminal fault'
* Mitigated according to the /sys interface:  YES  (Not affected)
* Kernel supports PTE inversion:  YES  (found in kernel image)
* PTE inversion enabled and active:  NO 
> STATUS:  NOT VULNERABLE  (your CPU vendor reported your CPU model as not affected)

CVE-2018-3646 aka 'Foreshadow-NG (VMM), L1 terminal fault'
* Information from the /sys interface: Not affected
* This system is a host running a hypervisor:  NO 
* Mitigation 1 (KVM)
  * EPT is disabled:  N/A  (the kvm_intel module is not loaded)
* Mitigation 2
  * L1D flush is supported by kernel:  YES  (found flush_l1d in kernel image)
  * L1D flush enabled:  NO 
  * Hardware-backed L1D flush supported:  NO  (flush will be done in software, this is slower)
  * Hyper-Threading (SMT) is enabled:  YES 
> STATUS:  NOT VULNERABLE  (your CPU vendor reported your CPU model as not affected)

CVE-2018-12126 aka 'Fallout, microarchitectural store buffer data sampling (MSBDS)'
* Mitigated according to the /sys interface:  YES  (Not affected)
* Kernel supports using MD_CLEAR mitigation:  YES  (found md_clear implementation evidence in kernel image)
* Kernel mitigation is enabled and active:  NO 
* SMT is either mitigated or disabled:  NO 
> STATUS:  NOT VULNERABLE  (your CPU vendor reported your CPU model as not affected)

CVE-2018-12130 aka 'ZombieLoad, microarchitectural fill buffer data sampling (MFBDS)'
* Mitigated according to the /sys interface:  YES  (Not affected)
* Kernel supports using MD_CLEAR mitigation:  YES  (found md_clear implementation evidence in kernel image)
* Kernel mitigation is enabled and active:  NO 
* SMT is either mitigated or disabled:  NO 
> STATUS:  NOT VULNERABLE  (your CPU vendor reported your CPU model as not affected)

CVE-2018-12127 aka 'RIDL, microarchitectural load port data sampling (MLPDS)'
* Mitigated according to the /sys interface:  YES  (Not affected)
* Kernel supports using MD_CLEAR mitigation:  YES  (found md_clear implementation evidence in kernel image)
* Kernel mitigation is enabled and active:  NO 
* SMT is either mitigated or disabled:  NO 
> STATUS:  NOT VULNERABLE  (your CPU vendor reported your CPU model as not affected)

CVE-2019-11091 aka 'RIDL, microarchitectural data sampling uncacheable memory (MDSUM)'
* Mitigated according to the /sys interface:  YES  (Not affected)
* Kernel supports using MD_CLEAR mitigation:  YES  (found md_clear implementation evidence in kernel image)
* Kernel mitigation is enabled and active:  NO 
* SMT is either mitigated or disabled:  NO 
> STATUS:  NOT VULNERABLE  (your CPU vendor reported your CPU model as not affected)

CVE-2019-11135 aka 'ZombieLoad V2, TSX Asynchronous Abort (TAA)'
* Mitigated according to the /sys interface:  YES  (Not affected)
* TAA mitigation is supported by kernel:  YES  (found tsx_async_abort in kernel image)
* TAA mitigation enabled and active:  NO 
> STATUS:  NOT VULNERABLE  (your CPU vendor reported your CPU model as not affected)

CVE-2018-12207 aka 'No eXcuses, iTLB Multihit, machine check exception on page size changes (MCEPSC)'
* Mitigated according to the /sys interface:  YES  (Not affected)
* This system is a host running a hypervisor:  NO 
* iTLB Multihit mitigation is supported by kernel:  YES  (found itlb_multihit in kernel image)
* iTLB Multihit mitigation enabled and active:  NO 
> STATUS:  NOT VULNERABLE  (your CPU vendor reported your CPU model as not affected)

CVE-2020-0543 aka 'Special Register Buffer Data Sampling (SRBDS)'
* Mitigated according to the /sys interface:  YES  (Not affected)
* SRBDS mitigation control is supported by the kernel:  YES  (found SRBDS implementation evidence in kernel image. Your kernel is up to date for SRBDS mitigation)
* SRBDS mitigation control is enabled and active:  NO 
> STATUS:  NOT VULNERABLE  (your CPU vendor reported your CPU model as not affected)

CVE-2023-20593 aka 'Zenbleed, cross-process information leak'
* Zenbleed mitigation is supported by kernel:  NO 
* Zenbleed kernel mitigation enabled and active:  NO  (FP_BACKUP_FIX is cleared in DE_CFG)
* Zenbleed mitigation is supported by CPU microcode:  NO 
> STATUS:  VULNERABLE  (Your kernel is too old to mitigate Zenbleed and your CPU microcode doesn't mitigate it either)

> SUMMARY: CVE-2017-5753:OK CVE-2017-5715:OK CVE-2017-5754:OK CVE-2018-3640:OK CVE-2018-3639:OK CVE-2018-3615:OK CVE-2018-3620:OK CVE-2018-3646:OK CVE-2018-12126:OK CVE-2018-12130:OK CVE-2018-12127:OK CVE-2019-11091:OK CVE-2019-11135:OK CVE-2018-12207:OK CVE-2020-0543:OK CVE-2023-20593:KO

Need more detailed information about mitigation options? Use --explain
A false sense of security is worse than no security at all, see --disclaimer

```

---

### Post by martinr on 2023-07-29
I checked all my computers for vulnerability to Spectre and Meltdown with the [spectre-meltdown-checker]("https://github.com/speed47/spectre-meltdown-checker"). Three were vulnerable. Which led me to the following challenge. For my rig with with a 64 bit Intel processor:
```

Kernel is Linux 5.4.0-155-generic #172-Ubuntu SMP Fri Jul 7 16:10:02 UTC 2023 x86_64
CPU is Celeron(R) Dual-Core CPU       T3000  @ 1.80GHz

```
The checker reported:
```

CVE-2018-3639 aka 'Variant 4, speculative store bypass'
* Mitigated according to the /sys interface:  NO  (Vulnerable)
* Kernel supports disabling speculative store bypass (SSB):  YES  (found in /proc/self/status)
* SSB mitigation is enabled and active:  NO 
> STATUS:  VULNERABLE  (Your CPU doesn't support SSBD)

> How to fix: Your kernel is recent enough to use the CPU microcode features for mitigation, but your CPU microcode doesn't actually provide the necessary features for the kernel to use. The microcode of your CPU hence needs to be upgraded. This is usually done at boot time by your kernel (the upgrade is not persistent across reboots which is why it's done at each boot). If you're using a distro, make sure you are up to date, as microcode updates are usually shipped alongside with the distro kernel. Availability of a microcode update for you CPU model depends on your CPU vendor. You can usually find out online if a microcode update is available for your CPU by searching for your CPUID (indicated in the Hardware Check section).

```
The Celeron T3000 has a 64-bit architecture.
The advise from the  spectre-meltdown-checker is to upgrade the microcode of the CPU in order for the kernel to make use of it to fix the vulnerability. 

The computer has the latest BIOS version installed already, but apparently that does not have the microcode fix in it.
Now I was hoping that the [intel-microcode]("https://packages.debian.org/source/bullseye/intel-microcode") package might contain fixed microcode that fixes this?
I'm running the latest updates.

This led me to the following two questions:

Is there newer microcode for the CPU that fixes the vulnerability?

How can I check which version of microcode is currently running on the CPU?
How can I check what the latest microcode version is, that is released for my processor: the Intel Celeron(R) Dual-Core CPU T3000 @ 1.80GHz.

I searched a lot on the internet, but couldn't find an answer only [this microcode-update-guidance document]("https://www.intel.com/content/dam/www/public/us/en/documents/corporate-information/SA00233-microcode-update-guidance.pdf"), but it doesn't mention the T3000 CPU.

---

### Post by DuckHook on 2023-07-29
> **martinr said:**
> …Is there newer microcode for the CPU that fixes the vulnerability?

How can I check which version of microcode is currently running on the CPU?
How can I check what the latest microcode version is, that is released for my processor: the Intel Celeron(R) Dual-Core CPU T3000 @ 1.80GHz…
```
duckhook@Zeus:~$  apt show intel-microcode
Package: intel-microcode
Version: 3.20230214.0ubuntu0.22.04.1
Priority: extra
Section: admin
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Henrique de Moraes Holschuh <hmh@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 12.1 MB
Depends: iucode-tool (>= 1.0)
Recommends: initramfs-tools (>= 0.113~)
Conflicts: microcode.ctl (<< 0.18~0)
[COLOR="#FF0000"]Homepage: https://github.com/intel/Intel-Linux-Processor-Microcode-Data-Files[/COLOR]
Download-Size: 5,821 kB
APT-Manual-Installed: no
APT-Sources: http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
Description: Processor microcode firmware for Intel CPUs
 This package contains updated system processor microcode for
 Intel i686 and Intel X86-64 processors.  Intel releases microcode
 updates to correct processor behavior as documented in the
 respective processor specification updates.
 .
For AMD processors, please refer to the amd64-microcode package.
```Note the highlighted URL
Reading through that github site should give you sufficient guidance on how to determine if your CPU has any outstanding microcode updates.

Further, note that Ubuntu's microcode updates will lag behind the the most recent issued by Intel. This is a designed safeguard: something as mission critical as microcode must be thoroughly tested before it is implemented system&#8209;wide. Bad microcode will bork your system.

Yet further, note that Intel will abandon CPUs that it deems obsolete. Some Atom processors come to mind. I don't know about your Celeron—you can find this out on your own following the instructions in that github page. Such abandonware will not get updates or mitigations of any kind.

---

### Post by #&amp;thj^% on 2023-10-08
> **martinr said:**
> 
Now I really don't understand how Debian can have patched amd64-microcode for the Zenbleed vulnerability already, whilst AMD still have to come up with a fix? And how the microcode can be reinitialized on an already running CPU.

Now fixed
```
pro fix CVE-2023-20593

CVE-2023-20593: Linux kernel (BlueField) vulnerabilities
 - https://ubuntu.com/security/CVE-2023-20593

2 affected source packages are installed: amd64-microcode, linux
(1/2, 2/2) amd64-microcode, linux:
A fix is available in Ubuntu standard updates.
The update is already installed.

&#10004; CVE-2023-20593 is resolved.

```

---

### Post by martinr on 2024-01-29
Thanks for your reply. I've retested 20593 and low and behold here are the results:
```

CVE-2023-20593 aka 'Zenbleed, cross-process information leak'
* Zenbleed mitigation is supported by kernel:  YES  (found zenbleed message in kernel image)
* Zenbleed kernel mitigation enabled and active:  YES  (FP_BACKUP_FIX bit set in DE_CFG)
* Zenbleed mitigation is supported by CPU microcode:  NO 
> STATUS:  NOT VULNERABLE  (Your kernel mitigates Zenbleed)

```
I can confirm that it's fixed in kernel 5.15.0-91-generic in XUbuntu 22.04.3 LTS on  Acer Swift 3 SF314-43 laptop with an AMD 5700U SoC / CPU.
Great! =d>

---

