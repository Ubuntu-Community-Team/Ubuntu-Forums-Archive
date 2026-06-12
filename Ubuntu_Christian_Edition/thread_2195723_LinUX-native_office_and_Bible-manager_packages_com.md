---
title: "LinUX-native office and Bible-manager packages compatible with OpenLP?"
date: 2013-12-26
forum: Ubuntu Christian Edition
---

### Post by bcschmerker on 2013-12-26
I am dissatisfied with the Unity&#8482; window manager and LibreOffice® business software packages for Ubuntu® 12.04.4-LTS Precise Pagolin&#8482; for a projection-system project and already have plans to restart development using a new subrelease, probably [Ubuntu® GNOME® 14.04.1-LTS Trusty Tahr&#8482;](http://www.ubuntugnome.org/) as released to market.  This project in behalf of the OMS® Japanese Christian Church must distract neither the end-viewers, both Members and otherwise, with a second desktop launcher on the projector (as I found to be the case with Unity&#8482;); nor the Operator with a task-launcher pop-up (as I found to be the case with LibreOffice®).  The project is to be deployed on an eMachines®/Acer® EL1210-09 upgraded with a 500W Shuttle® power supply and an Asus® EN210/DI/512MD3 video display adapter. 

Known vulnerabilities in all Releases of Microsoft® Windows® 6-up (viz., Vista&#8482; 6.0.600x, Se7en&#8482; 7.0.800x, 8ight&#8482; 8.0.10000 and 8.1.10600, Server 2008 6.0.600x and 6.1.760x, and Server 2012 6.2.9200 and 6.3.9600) contraindicate Ubuntu® Christian Edition&#8482; for the mission, as targeted malware could compromise this system by leveraging compatibility libraries in Wine&#8482;.  I do, however, anticipate needing native LinUX support for Crosswire® e-SWORD&#8482; for Bibles in multiple languages.  Deployment of this system will be contingent on availability of e-SWORD&#8482; releases for the following texts:

*Biblia Hebraica Stuttgartensia*.  Stuttgart: Deut&#383;che Bibelge&#383;ell&#383;chaft, 1997.  (Pending release of the *Biblia Hebraica Quinta* as completed.)

New Testament, Aramaic Peshitta Text with a Hebrew Translation.  Yerushalay'm:  Aramaic Scriptures Research Society in Israel, 1986.
(This is needed for hard reference for the Gospels of Sts. Mark, Matthew, and John, all of which were originally sourced in Aramaic.)

*Novum Testamentum Graece*, 28th Edition.  Stuttgart: Deut&#383;che Bibelge&#383;ell&#383;chaft, 2012.
(This is needed for hard reference for the New Testament except the Gospels of Sts. Mark, Matthew and John.)

New Interconfessional Translation of the Bible (&#26032;&#20849;&#21516;&#35379;&#32854;&#26360;).  T&#333;ky&#333;:  Japan Bible Society, 1987.  (Fallback:  New Revised Version of the Bible (&#26032;&#25913;&#35379;&#32854;&#26360;).  T&#333;ky&#333;:  Bible Society of Japan, 1970.)

The Amplified Bible.  1965; Grand Rapids, MI, USA: Zondervan Corporation, 1987.

---

### Post by Elfy on 2013-12-26
Is there a support request in there somewhere?

---

### Post by bcschmerker on 2013-12-27
Specifically, what Bible-manager and office-productivity packages will not interfere with OpenLP.

---

### Post by CharlesA on 2013-12-27
You would probably have better luck by asking the folks at OpenLP:
[http://openlp.org/en/support](http://openlp.org/en/support)

---

### Post by lisati on 2013-12-27
If you don't like Wine and the possible exposure to MS-based vulnerabilities, check out Xiphos from Crosswire. It comes in an Ubuntu-friendly version.

---

### Post by bcschmerker on 2013-12-28
The OpenLP Forums search directed me to [Bible Technologies LLP](http://www.bibletechnologies.com/), which has some information on an Open Scripture Information Standard.  Troublingly, [American Bible Society](http://www.americanbible.org/) is in the process of shutting down ForMinistry.com and I barely managed to find and download a copy of the OSIS 2.1.1 draft specification.

It does appear, fortunately, that Crosswire® does have specific libraries for SWORD™ 1.7 available for download; Launchpad™ already has SWORD™ 1.6.2, along with Xiphos™ 3.1.5, in the Ubuntu® Universe repositories, as of 27 December 2013.

---

### Post by jonathonblake on 2014-01-01
> **bcschmerker said:**
>  I do, however, anticipate needing native LinUX support for Crosswire® e-SWORD™

There is no such critter as [COLOR="#A52A2A"]Crosswire® e-SWORD™[/COLOR].

There is [COLOR="#A52A2A"]e-Sword[/COLOR], which is a closed source program that has a native version for iOS, and Windows, and arguably Windows Mobile 6.5, albeit development on that version ceased 3 years ago. Roughly 10% of e-Sword 10.2 functionality is not available, when run under WINE.  

There is [COLOR="#A52A2A"]The Crosswire Bible Society[/COLOR], which has native front ends for about a dozen operating systems currently in use, and has ceased development on about a dozen obsolete operating system. 

>  Deployment of this system will be contingent on availability of e-SWORD™ releases for the following texts:

If you want resources for e-Sword, you need to either talk to Rick Meyers, the developer of e-Sword, or Josh Bond, webmaster of BibleSupport.com, which is the largest collection of legally distributed resources for e-Sword on the net.

If you are requesting those resources for use with the front ends supported by The Crosswire Bible Society, discuss it on the Sword Project Developer's Mailing List. 

jonathon

---

### Post by jonathonblake on 2014-01-01
> **bcschmerker said:**
> I barely managed to find and download a copy of the OSIS 2.1.1 draft specification.

That version contained a number of errors and ommisions.  It also is out of date.
The current version is either on the Crosswire site, or the site of one of the Bible Translation Societies that they work with.

jonathon

---

### Post by bcschmerker on 2014-01-01
Apparently OSIS&#8482; 2.1.1, which dates from 2006, *is* the current release.  Following a link from BibleTechnologies.net gave me a problem:  BibleTechnologiesWG.org has a **blank** page /osis/docs with no information - apparently the BibleTechnologiesWG.org Website is being torn down, judging from what I can read of its source code.  Additionally, I found that the E-Sword.net Website mentions nothing about system requirements for Release 10.2.1, although Microsoft® Windows® 2000 Professional, XP, and/or 6-up can be inferred from the downloadable Binary /files/setup1021.exe at /downloads.html.

At least Crosswire® has GNU® GZip&#8482; tape-archive downloads for the SWORD source code at /ftpmirror/pub/sword/source, which covers all Releases 1.x.

---

### Post by bcschmerker on 2014-01-22
**Update:**  In UbuntuGNOME™ 13.12a1, I found the LibreOffice™ installation better behaved than in Ubuntu® 12.04.4-LTS (presumably the same will hold true at RTM of 14.04-LTS), and Canonical® maintains a complete related set of BiblEdit packages in the Multiverse repository.  Preliminary plan is to test Xiphos™, a LinUX-native Bible reader, with OpenLP®.  The X.org Nouveau server (package: xserver-xorg-video-nouveau) in 13.12a1 also handles the nVIDIA® GT218 GPU better than I found the case in 12.04.4-LTS.  Will report back once programming in OpenLP® is completed.

---

### Post by jonathonblake on 2014-01-31
[QUOTE=bcschmerker]Apparently OSIS™ 2.1.1, which dates from 2006, *is* the current release.  [/quote]

There has to be a more recent version, because at least a dozen markup constructs in it have been depreciated, and another dozen or so have been redefined.

>  the E-Sword.net Website mentions nothing about system requirements for Release 10.2.1,.

Some functionality in  e-Sword 10.1.x was not available in Win2K,  but was available in WinXP, and higher. I've forgotten the specifics, bt my guess is that it is the same functionality as is missing from e-Sword under WINE.

jonathon

---

### Post by jonathonblake on 2014-01-31
> Deployment of this system will be contingent on availability of e-SWORD™ releases for the following texts:

*Biblia Hebraica Stuttgartensia*.  Stuttgart: Deut&#383;che Bibelge&#383;ell&#383;chaft, 1997.  (Pending release of the *Biblia Hebraica Quinta* as completed.)

New Testament, Aramaic Peshitta Text with a Hebrew Translation.  Yerushalay'm:  Aramaic Scriptures Research Society in Israel, 1986.
(This is needed for hard reference for the Gospels of Sts. Mark, Matthew, and John, all of which were originally sourced in Aramaic.)

*Novum Testamentum Graece*, 28th Edition.  Stuttgart: Deut&#383;che Bibelge&#383;ell&#383;chaft, 2012.
(This is needed for hard reference for the New Testament except the Gospels of Sts. Mark, Matthew and John.)

New Interconfessional Translation of the Bible (&#26032;&#20849;&#21516;&#35379;&#32854;&#26360;).  T&#333;ky&#333;:  Japan Bible Society, 1987.  (Fallback:  New Revised Version of the Bible (&#26032;&#25913;&#35379;&#32854;&#26360;).  T&#333;ky&#333;:  Bible Society of Japan, 1970.)

The Amplified Bible.  1965; Grand Rapids, MI, USA: Zondervan Corporation, 1987.

Inasmuch as those texts are not currently available in a format that can be utilized by your proposed solution, how are you going to handle the copyright issue, in converting them to a format that can be utiized by your proposed solution?

jonathon

---

### Post by bcschmerker on 2014-02-01
> **jonathonblake said:**
> Inasmuch as those texts are not currently available in a format that can be utilized by your proposed solution, how are you going to handle the copyright issue, in converting them to a format that can be utiized by your proposed solution?

jonathon
I only half-expected this complication.  As of January 2014, the only open-source releases of original-tongues documents are the Leningrad Codex (package: sword-text-wlc), which has several significant variances from the *Biblia Hebraica*; and the Textus Receptus (package: sword-text-tr), which has several significant variances from the *Novum Testamentum Graece*:  Both are in the Ubuntu® Universe Repository.  Unfortunately, no Japanese Bible is available to either OpenLP® or Canonical® as of January 2014; and the King James Version as updated 1730 (package: sword-text-kjv) is in the Ubuntu® Restricted Repository, as the Crown of the United Kingdom of Great Britain and Her Other Territories (PRS) maintains mechanical copyright to this day.

I will probably have to see whether the International Bible Society has an online release of the New International Version available, as an English-language fallback from the Amplified.

**Update:**  Another complication:  The Bibles from the Ubuntu® Universe Repository refuse to import.  From the File Extensions, the Bibles may have been compressed using BZip (the Files identified for each Bible * include a Text tar *.bzv and two Metadata tars *.bzs and *.bzz), but I cannot make a positive ID from the information in the OpenLP® Forums.

---

### Post by bcschmerker on 2014-04-19
As of 19 April 2014, OpenLP® has Version 2.2 in development, as Python 3.2 is a pre-dependency for LibreOffice™ 4.x compatibility.  (The LibreOffice™ upgrade, for practical purposes, broke the Presentation Module in OpenLP® 2.0, which was developed with Python 2.7, and the required code changes cannot be backported to 2.0.x.)  Several different Bibles for English, Koine, and Hebrew are available from alternate repositories to Crosswire® Official, although I have not found one for the Japanese Bible translation(s) I anticipate needing (Priority: Wishlist, due to native kernel-level differences between LinUX and uTRON/BTRON; Status: Undecided).  Will update once OpenLP® 2.2 is checked out.

---

