---
title: "Wow. How disappointing Canonical's patch policy is..."
date: 2023-02-03
forum: Ubuntu, Linux and OS Chat
---

### Post by meyergru on 2023-02-03
Hi all,


sorry that I have to make my entree here by something so bitter, but this is a sad day for me,

I have been a long private user and strong proponent of Ubuntu Linux in the commercial field. However, that may come to an end.

Today, I was greeted by the following message on one of my VMs (22.04.1 LTS):

> 
[FONT=Helvetica]Expanded Security           Maintenance for Applications is not enabled.[/FONT]
        
        [FONT=Helvetica]0 updates can be           applied immediately.[/FONT]
        
        [FONT=Helvetica]15 additional security           updates can be applied with ESM Apps.[/FONT]
        [FONT=Helvetica]Learn more about           enabling ESM Apps service at [https://ubuntu.com/esm](https://ubuntu.com/esm)
[/FONT]

Investigating a bit further, I found that when using "apt update" now, I not only come to know what updates have NOT been applied (aka phased updates), but that there are also updates that I never knew of because I do not use Ubuntu Pro yet.

Among those was python2, which under ESM, can be upgraded to python2.7/2.7.18-13ubuntu1.1+esm2, which suggests this was already the 2nd upgrade from the now-current python2.7/2.7.18-13ubuntu1.1 without ESM. Looking at: [https://ubuntu.com/security/CVE-2022-0391](https://ubuntu.com/security/CVE-2022-0391), one can find that everything before the ESM release is vulnerable.

It appears that it is even worse than Canonical states ([https://ubuntu.com/pro):](https://ubuntu.com/pro):)

> 
Reduce your average CVE exposure time from 98 days to 1 day 
with expanded CVE patching, ten-years security maintenance, optional support and operations for the full stack of open-source applications.
 

because said python2 vulnerability has been fixed almost a year ago (2022-02-09). It is only now that this is becoming more visible and I am quite astonished that there is not any more uproar about it. As for me, I did not expect such a thing and python2 was just one example for this. All in all, I found to be using ~20 vulnerable packages without knowing.

While everyone can protect 5 of their systems with a free Ubuntu Pro subscription, the fee for a single server (virtual or real) at $500 seems a bit steep when it is just security updates that are needed. I can understand the monetarisation needs for a company, which became visible with the latest promotion of Ubuntu Pro, phased updates a.s.o., however I find it hard to swallow that existing security updates are held back for that long.

 I sure have to re-think the advice I will be giving to my customers w/r to Ubuntu.

---

### Post by BBQdave on 2023-02-03
Reading information from [https://ubuntu.com/pro](https://ubuntu.com/pro) it appears to offer extended patches beyond normal LTS support.

I installed ubuntu-advantage-tools and then ran:
$ sudo pro security-status
$ sudo apt update
$ sudo apt upgrade
$ sudo snap refresh

Everything is up to date. The same as before *pro security-status*. I believe this is a service for extended patches beyond normal support time of the release. And it's free for personal users, up to 5 machines.

---

### Post by meyergru on 2023-02-04
No, this is nothing like ESM for old releases that are out out  normal LTS support, it affects current packages like python2 in current  LTS releases like 22.04.1 LTS. Matter-of-fact the CVE page cited clearly  states that everything before python2.7/2.7.18-13ubuntu1.1+esm2 is  affected by a CVE that has a score of 7.5. If you install it, you will  still get python2.7/2.7.18-13ubuntu1.1, which clearly is affected by  CVE-2022-0391.

Good for you if you did not have any of the affected packages installed. I have seen these ones affected so far, which obviously are installed on some of my maschines:

> 
[FONT=Helvetica]The following security updates require Ubuntu Pro with         'esm-apps' enabled:
          **libmagickcore-6.q16-6-extra imagemagick libzmq5           libmagickwand-6.q16-6****  fail2ban roundcube-core imagemagick-6.q16           libjs-jquery-ui roundcube-mysql**[B]  roundcube libopenexr24 libmysofa1 libmagickcore-6.q16-6           imagemagick-6-common
  [FONT=Helvetica]**libopenexr25 [FONT=Helvetica]ansible [FONT=Helvetica]libmaven3-core-java [FONT=Helvetica]libpython2.7-minimal [FONT=Helvetica]libpython2.7-stdlib [/FONT][/FONT][/FONT][/FONT]**[/FONT]
  [FONT=Helvetica]maven [FONT=Helvetica]python2.7-minimal [FONT=Helvetica][COLOR=#ff0000]python2.7[/COLOR][/FONT][/FONT][/FONT]
[/B][/FONT][FONT=Helvetica][/FONT]
I do not see why any one of those packages qualify more or less than any other package, so what will or will not be updated in the future without Ubunto Pro support is unclear at least.

---

### Post by MAFoElffen on 2023-02-04
As a whole, they could have just let it die without any support:
> 
The Python Software Foundation sunset Python 2 on January 1, 2020. End of Life (EOL) means there are no more official updates or security fixes, not even for critical security vulnerabilities.

Count your blessings were they appear. It was an upstream thing, beyond their own control, were they didn't have to do it, but they did anyways.

For companies that haven't migrated their codebase from Python 2.7.x, thrid party vendors are charging big money to provide securities updates to... Because
> 
Vendors are phasing out support for Python 2 distributions (e.g. Red Hat, Apple, AWS, Heroku, Ubuntu).

That quote was from years ago. Pythoin 2.7 EOL is not something "new."

---

### Post by meyergru on 2023-02-04
I think I have not made myself clear on that front because everyone is picking up about python2: Either a distribution contains something or it does not. But if it does, it has to support the package security-wise. Ubuntu 22.04.1 LTS contains python2. Being an LTS release that is guaranteed to be supported for at least 5 years, Canonical even did patch a vulnerability in that package which was and is still present in that distribution. But they fixed the problem only for paying customers (well, at least commerical ones) and left the rest vulnerable for almost a year.

Also, there are other packages that have been handled the same way, like ansible, imagemagick, libjs-jquery-ui, roundcube, maven and maybe many more that I do not use (if ansible and maven are not patched, will docker be if there is a problem)?

 Essentially, I can never be sure that security fixes will be available for any package in the future unless I have Ubuntu Pro. Which in turn limits me to 5 installations or comes at a hefty price and forces me to enable snap, which I do not like. Even Red Hat offers up to 16 installations (even for commerical use) when they gave up Cent OS. What is worse here is that this situation has been going on for about a year and now they come forward and say: Guess what? We have so many security fixes that you did not even know about... use Ubuntu Pro now! 

As for the upstream argument: Well, I could use many packages from upstream and get newer versions of those besides the security fixes, but what is the point of using a distribution, then?

I might be better of with Debian: On one hand, the updates can be limited to security fixes, resulting in no risk of problems by upgraded packages and coming with no strings attached.

---

### Post by MAFoElffen on 2023-02-04
I am not, in any way, connected with Canonical. So do not take this out on me. My position is that I have to deal with the cards dealt, just like everyone else.

Transition from Python2 to Python3 in Ubuntu started between 16.04 LTS and 18.04 LTS... 6 years ago. Not just suddenly in 22.04 LTS. I had to start changing my own Python scripts back then. Eventually, support for Python2.x it is going to die.

Like I said, this is not new.

Heck. I know COBOL. Not something I put on my RESUME. LOL. You know how many companies still hang on to that as their base? Yet...

---

### Post by Impavidus on 2023-02-04
> **meyergru said:**
> Either a distribution contains something or it does not.

You missed the difference between the main and the universe repositories. The main repository is fully supported by Canonical for 5 years. The universe repository is not. As is commented in your sources.list:```
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
```There may be updates from the community, and it appears that Canonical may provide some support for Ubuntu Pro users. But for those who don't use Ubuntu Pro, it does exactly what it says on the tin.

The message we now get from Canonical is of course intended to make us sign up for Ubuntu Pro.

---

### Post by meyergru on 2023-02-04
I did not mean you, but Canonical.

 However, I do not buy the python2 argument not being "new", first because that is just one example for my point and second, because if Canonical had no intent of supporting that any more, they should (and could) have not included it in 22.04 (or even 20.04). Besides, they are plenty of packages that even in their newest incarnations still rely on python2, like OpenSIPS.

Canonical did actually decide to include it, just not supporting it in full (i.e. "for free") as I had expected. My whole point being that assumption has turned out to be plain wrong, which essentially means: **Canonical obviously does NOT do full support security fixes in the (otherwise) free Ubuntu LTS distributions. They keep back known fixes for paying customers. If you are unwilling to pay for Ubuntu, you cannot rely on it staying secure. That is, modulo up to 5 installations with the free subscription.**

Or to put it like this: There is no such thing as a free lunch.

P.S.: I do know COBOL as well (I am 58).

---

### Post by BBQdave on 2023-02-04
> **Impavidus said:**
> The message we now get from Canonical is of course intended to make us sign up for Ubuntu Pro.

Which for personal use, is free on up to 5 machines. Seems like a nice offer to have patch support on programs that are no longer supported.

As said before, Canonical is jumping into a support space for programs no longer supported and in transition. So you get to try the service for free and then decide if it is of value to scale it up and pay.


Personally, the normal flow of LTS and applications works great. Though I could hang on to a LTS for longer than two years, I don't. Happy to upgrade to the latest LTS :)

If you have a lot of machines with set programs for a group of users with set services and production for income, Canonical's Ubuntu Pro is a value.

If you're a small group with tight services and production for income, or personal use, LTS is your scene :)

---

### Post by ian-weisser on 2023-02-04
Sigh. Time for FUD control.

"*The following security updates require Ubuntu Pro with 'esm-apps' enabled:*" Those packages are in Universe, not Main.

- Patches in Main (UNCHANGED) still go to the Security pocket, and are free to all. NOTHING has been removed/paywalled. Nobody is getting charged for a service that used to be free.

- Patches in Universe (NEW) go to esm/apps and are available to Pro subscribers. Previously, almost nobody did this work -- the Canonical engineers kept to Main, and the community mostly whined without doing much. The business model is essentially that enterprise subscriptions subsidize patches for non-enterprise users.

Want an alternative to Pro? Just use the normal 6-month release of Ubuntu, You will get all the Universe security patches every six months when you release-upgrade. It's still an improvement for LTS non-Pro users (Pro is LTS only), who currently aren't getting Universe security patches for (many) years until they migrate to the next LTS*.*

Alternately, the community is welcome to organize, implement, test, and document patches for Universe. That path has been open since 2004. MOTUs will happily upload your tested work.

---

### Post by mIk3_08 on 2023-02-05
I am not into canonical since I am not one of them but Glad to use their free package. I just totally respect the canonical's decision regarding this issues. Regards and cheers.

---

### Post by monkeybrain20122 on 2023-02-05
> **MAFoElffen said:**
> 
Heck. I know COBOL. Not something I put on my RESUME. LOL. You know how many companies still hang on to that as their base? Yet...

Actually I heard that if you know COBOL you can easily get a cushy job in the banks because no one knows it. I had a teaching gig in a college a few years ago, this first year kid told me he was quitting his com science degree because his uncle who worked for tech support in the bank told him he didn't need a degree, if he learned COBOL in the summer he would be sure to get a well paid job in the banks. No one graduates in com science today would know it so he had no competition. The only thing I know about COBOL is you should keep your cap lock on because it screams at you. :) I know that from the book this kid showed me.

It is an obsolete language but the only people who still use it happen to also have the most $$ :)

---

### Post by mIk3_08 on 2023-02-05
This COBOL is now popular again but I prefer to use python though. :-D But as far as I know that python nowadays is a very high level language than java language. As an expert of specified field according to my only own terms. :-D :-D Be firm of what you do. Solid as stone. Regards and cheers.

---

### Post by tea for one on 2023-02-05
> **meyergru said:**
> Ubuntu 22.04.1 LTS contains python2.
I've just had a look at the package manifest and I cannot find python2.
[https://releases.ubuntu.com/22.04/ubuntu-22.04.1-desktop-amd64.manifest](https://releases.ubuntu.com/22.04/ubuntu-22.04.1-desktop-amd64.manifest)

---

### Post by meyergru on 2023-02-05
O.K., then, technically it is correct that Canonical "told us so", but apart from an obscure comment for the universe repository, it is activated by default (even in Ubuntu server minimal).

And why wouldn't it, when it contains essential packages?

Everyone is invited to see what they would be missing out without universe by trying "aptitude search -F "%s# %p %v" "~i ?section(universe)". Of my 4004 installed packages, 1866 come from universe. Before you disable universe, be sure to uninstall those packages first, because then, you would not get any updates even if there were some.

Then again, maybe you cannot do that because you already disabled universe and therefore do not have "aptitude", nor "apt-transport-https", which would give you the opportunity to use many upstream repos, nor many python and php modules, nor "sqlite", nor "nodejs", nor "npm", just to name a few.

For a web server, you would probably need php-fpm, and guess what? Correct. Universe.

---

### Post by meyergru on 2023-02-05
> **tea for one said:**
> I've just had a look at the package manifest and I cannot find python2.
[https://releases.ubuntu.com/22.04/ubuntu-22.04.1-desktop-amd64.manifest](https://releases.ubuntu.com/22.04/ubuntu-22.04.1-desktop-amd64.manifest)

Just try to install it or "apt search python2" and you will that that it exists. In my case, it came as a dependency of Opensips, which was in Ubuntu up to bionic and was retained through LTS upgrades.

---

### Post by tea for one on 2023-02-05
Just a matter of curiosity based on the following info:-

Python2 reached End of Life on 01 January 2020.
The oldest maintained version of OpenSIPS (version3.1 LTS) was released on 22 July 2020.
[https://www.opensips.org/About/AvailableVersions](https://www.opensips.org/About/AvailableVersions)

I would expect that a maintained version of OpenSIPS would not depend on python2?

---

### Post by TheFu on 2023-02-05
> **meyergru said:**
>  
For a web server, you would probably need php-fpm, and guess what? Correct. Universe.

None of our public web servers run php.  ZERO. NONE.  It is a choice we make, mainly for security reasons.
We don't use python2 since the python team decided not to support it in 2020, which was clearly announced.  Don't blame Canonical.  Blame the Python team.

[https://www.python.org/doc/sunset-python-2/](https://www.python.org/doc/sunset-python-2/)
> 
Sunsetting Python 2

We are volunteers who make and take care of the Python programming language. We have decided that January 1, 2020, was the day that we sunset Python 2. That means that we will not improve it anymore after that day, even if someone finds a security problem in it. You should upgrade to Python 3 as soon as you can.

It is fine to be unhappy about choices other people make.  This choice actually broke my backup tools, so I've been dealing with it since 2020 on some level.  I don't blame Canonical, nor the backup tool team and really, I don't blame the python team either.  We had a very long run with python2 - probably 10 yrs longer than it should have lasted.

Sometimes problems are what they are.  Complaining won't fix it.
If you've been telling your clients to use python2 the last 3 yrs, that's your failure.

---

### Post by mIk3_08 on 2023-02-05
Sad to say that we should now leave behind the Python 2. It really hurts but It is necessary for us to accept the fact that we should need to turn to the next page. The new chapter of Python.
Its been so long enough giving some extensions to Python 2. I think now is the time for us to grow to face the new challenges using the new environment. Regards and cheers.

---

### Post by meyergru on 2023-02-06
Correct, However, as I said, python2 was only an example and obviously not a good one as it draws attention to the wrong aspect.

 My main point here is that by actively promoting Ubuntu Pro, Canonical has made evident (well, at least for me) that large parts of their distribution are - as documented - not covered by "free" LTS security updates.

Everyone is entitled to having their own opinion about the price of Ubuntu pro or the number of free installations and I fully understand commerical obligations.

But what is worse is that I doubt (call that FUD) that those parts (namely "universe") are even fully covered by ESM. This is only an educated guess because of the fact that there are only 15 ESM patches for 1866 "universe" packages on my system, while there were three-digit numbers of patches for the rest (2138).

I would be happy to hear that getting a license actually guarantees the support of "universe" packages, some of them being essential to at least many installations that I know of.

Besides: While some may think that the "phased updates" are a good thing (tm), I consider this might as well be a means to distribute poorly tested updates and see if they cause problems. That way, every installation could potentially become an involuntary test candidate.

---

### Post by TheFu on 2023-02-06
> **meyergru said:**
>  Besides: While some may think that the "phased updates" are a good thing (tm), I consider this might as well be a means to distribute poorly tested updates and see if they cause problems. That way, every installation could potentially become an involuntary test candidate.

A changes introduce risk.  Humans make mistakes.  I worked for 5 yrs in a CMMI level 5 software development environment, where not introducing **any** bugs was the most important consideration, always.  We slipped schedules for months when we needed more time for reviews and/or testing.  Bug-free code was more important than anything. Every time a bug was uncovered at any level, we'd perform root cause analysis on the bug to determine what allowed it into the code at all.  It was seldom that any bug would be seen by the client, but it did happen.  When I started, bugs would get through about 2 a year for our team of 22 programmers, but would be caught by the client's experts at review time. Perhaps 1 a year would make it passed the first 6 levels of testing.  One of my bugs made it to level 7 testing before it was caught.  Plus, during development, I'd specifically asked the "experts" about the code line where the bug existed.  It wasn't a complex thing.  I just wasn't setting all the redundant outputs to the calculated value, so only 4 of the 5 redundant buses had the correct value flowing.  Within a few years, our team through process modification and increased expertise, was creating 1 new bug every other year.  Based on statistical analysis, the team of experts on code review process believed that all SEV-1 bugs had been found and corrected in the code. Effectively, it was bug free, or so that was the belief.  Jump forward to the year after the program was shut down and the process team experts compiled all the errors and found that over 100 SEV-1 bugs had been found that were in the code at the time it was declared SEV-1 bug free about 15 yrs earlier.

What's my point?  All non-trivial code has bugs.  All of it. No amount of money and expertise will uncover them all.  It is impossible.  Only time with the code working will show how bug free it is. Doing phased patching is a smart thing, provided the phased patches are consistent across the systems.  If anywhere, THAT is where I think Canonical might have failed ... but I don't really know, since I've never noticed that I've been impacted by the phased patches.  I'm not a normal end-user.  Alas, I run a package caching server, so when 1 system requests a package to be updated, that package is pulled to the cache and gets used by all other systems under the same caching server.  Consistency is what matters, not getting the absolutely latest version of the software.  Heck, I consider "new" code to be the enemy most of the time.  Stability is more important than almost everything else, followed by avoiding security bugs.  

Every once in a while, a released patch has to be updated due to some failure that the developer team missed.  That means in the following 1-3 days, an updated version will be released.  Because I only patch once a week, on weekends, I miss most of those less-great updates.  I won't patch on a Friday if I'll be gone for the weekend. The patches can wait an extra week, until I return and can get console access easier.

Avoiding issues is a key aspect for being a good admin.  New is the enemy of stable.

---

### Post by slickymaster on 2023-02-06
Not a support request

*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by DuckHook on 2023-02-07
I'm detecting a bit of "arguing for the sake of arguing" going on here.

Several clarifications have been made:

[LIST]
[*]Universe is maintained by others. Stuff in Universe is therefore subject to sunsetting and you use it at your own risk.
[*]If Canonical chooses to maintain it notwithstanding, then this is a completely extraneous benefit. You don't get to turn it into an expectation.
[*]*Everything* sunsets at some point. It's just that Canonical will "guarantee" a five year stint on stuff that's in Main.
[*]Self-promotion is not a crime. If it were, then we are all guilty when we, say, post our LinkedIn profiles with the intent of career promotion.
[/LIST]
I will note one thing further that ought to be glaringly obvious: Canonical has retired/abandoned/dropped support for tons of stuff over the years, from Unity to Upstart to even such fundamental stuff as 32-bit architecture and the pending retirement of Xorg and PulseAudio, any one of which are far more "mission&#8209;critical" than python2. This has been happening since Canonical was founded and will continue to happen so long as they exist, yet you choose to get all worked up about a tiny piece of this incredibly complex puzzle, going so far as to accuse them of being guilty of some reprehensible moral failure justifying corporate shunning and opprobrium.

Like everyone else here, I don't work for Canonical and have nothing to do with them except the use—and appreciation—of their product. I too have found myself confounded and frustrated by their past decisions, especially each and every one of the changes that I've stated above, but I've never gone so far as to accuse them of trickery or treachery.

One adapts and moves on.

---

### Post by grahammechanical on 2023-02-09
It is standard practice in Free and Open Source Software (F.O.S.S.) for the user to be used as a tester. It is called "bug reporting." Anyone can report a bug. Here is an article that shows the effort that Canonical engineers put in to keeping Ubuntu secure.

[https://ubuntu.com/blog/3-ways-to-apply-security-patches-in-linux](https://ubuntu.com/blog/3-ways-to-apply-security-patches-in-linux)

It is not an easy read. How could it be? But educational none-the-less

Regards

---

