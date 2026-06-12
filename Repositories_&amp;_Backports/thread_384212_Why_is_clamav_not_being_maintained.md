---
title: "Why is clamav not being maintained"
date: 2007-03-14
forum: Repositories &amp; Backports
---

### Post by GrammatonCleric on 2007-03-14
Why is clamav not being maintained for all ubuntu versions (at least back to Dapper LTS)? Some of us actually use clamav in a production enviroment in conjuntion with spam filtering. 

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


Those are also the current versions by ubuntu distribution avaible to download at this time. Feisty is the only one that is current. If you seach through the forum you'll find that others are wondering why clamav is not at least at .88.7. Others are getting....

```

WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.88.4 Recommended version: 0.90.1
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Current functionality level = 8, recommended = 14

```So what does this mean? 
([http://www.clamav.net/support/faq](http://www.clamav.net/support/faq))

What does *WARNING: Current functionality level = 1, required = 2* mean?[LIST]
[*]The *functionality level* of the database determines which scanner engine version is required to use all of its signatures. If you don&#8217;t upgrade immediately you will be missing the latest viruses.[/LIST][LIST]
[*]What does *Your ClamAV installation is OUTDATED* mean?[LIST]
[*]You&#8217;ll get this message whenever a new version of ClamAV is released. In order to detect all the latest viruses, it&#8217;s not enough to keep your database up to date. You also need to run the latest version of the scanner. You can download the [sources]("http://www.clamav.net/download/sources") of the latest release from our website. Upgrade instructions are on the [WikiWiki]("http://wiki.clamav.net/"). If you are afraid to break something while upgrading, use  the [precompiled packages]("http://www.clamav.net/download/packages") for your operating system/distribution.  Remember: running the latest stable release also improves stability.[/LIST] [/LIST]The common reply is "complie it youself."    If it is believed that .88.4 is current I beg to differ...and others with me.

---

### Post by andydread on 2007-03-18
I really would like to know the same thing.  As I have Dapper LTS on 15 mail servers
and planning to upgrade 12 more from Mandrake to Dapper LTS.  We chose dapper
LTS because of the LTS and was hoping that would mean we could simply apt-get
update apt-get upgrade to keep the servers fairly up to date.  Now some newer
worms are starting to get through and all the servers are spewing  . . .
This...

```

LibClamAV Warning: ********************************************************
LibClamAV Warning: ***  This version of the ClamAV engine is outdated.  ***
LibClamAV Warning: *** DON'T PANIC! Read http://www.clamav.net/faq.html ***
LibClamAV Warning: ********************************************************
LibClamAV Warning: ********************************************************
LibClamAV Warning: ***  This version of the ClamAV engine is outdated.  ***
LibClamAV Warning: *** DON'T PANIC! Read http://www.clamav.net/faq.html ***
LibClamAV Warning: ********************************************************

```

And this...

```

ClamAV update process started at Sun Mar 18 09:38:58 2007
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.88.4 Recommended version: 0.90.1
DON'T PANIC! Read http://www.clamav.net/faq.html
main.cvd is up to date (version: 42, sigs: 83951, f-level: 10, builder: tkojm)
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Current functionality level = 8, recommended = 10
DON'T PANIC! Read http://www.clamav.net/faq.html
daily.cvd is up to date (version: 2863, sigs: 16094, f-level: 14, builder: ccordes)
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Current functionality level = 8, recommended = 14
DON'T PANIC! Read http://www.clamav.net/faq.html

```

I thought long term support meant critical packages are kept up to date.  

So here are a few questions I would like to know if you keen folks can 
shed some light on. 

Is there other AV solutions that integrates well with Postfix/AMAVISd etc. 
for LTS servers that is easy to keep up to date that Ubuntu developers /Canonical recommends.?

is the clamav package that is in the repositories offically supported by Ubuntu?

Do we have to purchase commercial support to get the latest version of ClamAV
version kept updated in the repositories for LTS versions? 

TIA

---

### Post by MJN on 2007-03-18
Hi Andydread,

> I thought long term support meant critical packages are kept up to date.

ClamAV is not a critical package.

> is the clamav package that is in the repositories offically supported by Ubuntu?No - it is from the Universe repository hence is community supported. (see [http://www.ubuntu.com/community/ubuntustory/components](http://www.ubuntu.com/community/ubuntustory/components) for definitions of each repository)

> Do we have to purchase commercial support to get the latest version of ClamAV
version kept updated in the repositories for LTS versions? No. Compile it yourself, or use a pre-built package as discussed in the duplicate thread at [http://ubuntuforums.org/showthread.php?t=384190](http://ubuntuforums.org/showthread.php?t=384190).

Mathew

---

