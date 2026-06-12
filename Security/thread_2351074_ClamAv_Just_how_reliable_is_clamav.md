---
title: "ClamAv: Just how reliable is clamav?"
date: 2017-01-30
forum: Security
---

### Post by martemarziano on 2017-01-30
Hi,
After a full run with clamav on my Ubuntu 16.06 installed some two weeks ago, I am presented with a list of 68 possible threats, mostly related to LibreOffice and other things. Could that be right? I am a bit confused as how to interpret this horrifying result. I appreciate your comments.

---

### Post by martemarziano on 2017-01-30
> **martemarziano said:**
> 
After a full run with clamav on my Ubuntu 16.06 installed some...

Well, with that version I should be happy to be able to run anything at all, malware included:confused:

---

### Post by &amp;KyT$0P# on 2017-01-30
> **martemarziano said:**
> Well, with that version I should be happy to be able to run anything at all, malware included:confused:
?

---

### Post by martemarziano on 2017-01-31
I wrote 16.06 by mistake. Thinking that that version was non-existent I wrote the second post. Later I found out that there is such a version but not as an update to 16.04 but as steps towards 16.10. Sorry for all that!

---

### Post by HermanAB on 2017-01-31
Well, the purpose of ClamAV is mainly to weed out Windows email viruses.  If it detects anything at all on a Linux machine, then you can be pretty much 110% sure that it is a false positive.

I ran mail and web servers for many years and ClamAV was very useful to keep my Windows users safe.  In all that time, I never had a Linux malware problem, because there pretty much isn't any.  If you use long passwords and think and read up a bit on the security issues of a service before installing something, you should not have a problem with Linux, ever.

---

### Post by Habitual on 2017-01-31
My advice:
Don't enable PUA scan (it is disabled by default)
Don't scan /

Other than that. I don't care if Windows viruses are on my Linux desktop.

---

### Post by DuckHook on 2017-01-31
> **HermanAB said:**
> Well, the purpose of ClamAV is mainly to weed out Windows email viruses.  If it detects anything at all on a Linux machine, then you can be pretty much 110% sure that it is a false positive.

I ran mail and web servers for many years and ClamAV was very useful to keep my Windows users safe.  In all that time, I never had a Linux malware problem, because there pretty much isn't any.  If you use long passwords and think and read up a bit on the security issues of a service before installing something, you should not have a problem with Linux, ever.&#8593;+1

@OP

Please keep in mind HermanAB's qualifiers, though… " If you use long passwords and ***think*** and read up a bit on the security issues of a service before installing something…" (emphasis mine) This is critically important and should be emphasized.

Your question about ClamAV pops up on these forums regularly. We all have our personal opinions about whether AV software serves any useful purpose at all on a pure Linux system&#8213;I think they are useless, give a false sense of security, and perpetuate a misguided app-based way of thinking&#8213;but what we all agree on is that no app is a substitute for good computing habits. 90% of security is good habits, vigilance, judicious conduct, a knowledgeable community and hardening your various subsystems intelligently. Apps are just that 10% comprising the tools needed to get the job done. No app will save you from yourself.

All this written at length before so no point in repeating. If you are interested, [this thread]("https://ubuntuforums.org/showthread.php?t=2184758&p=12833795#post12833795").

You may also find the ***Security Basics*** link in my sig useful.

---

### Post by liam.gutierrez on 2017-01-31
If I were you, uninstall ClamAV. If you really need an Anti-Virus (because you got Windows PC on your network, have Wine installed or similar), get SOPHOS Anti-Virus for Linux. It's free, low on resources and way more reliable. It used to have a web interface but now works only by CLI. It offers on-access scanning and you get a desktop notification if it detects malware. SOPHOS AV is well documented and there are many helpful videos on YouTube on how to properly install and use SOPHOS.

---

### Post by Habitual on 2017-01-31
I rely on clamav on servers. 
I rely on it to tell me that I need to engage if an infection is found.
**It does not clean.**

Anything it says it finds, I up to [https://virustotal.com](https://virustotal.com) and have analyzed (not system files, ***my*** stuff)

---

### Post by martemarziano on 2017-01-31
Thank you all! It's always a pleasure reading your responses to all these newbie's questions of mine. I really feel secure knowing to have the support of this fantastic community and all you knowledgeable people out there! I truly feel indebted to you because of everything I learn from you everyday. Being part of the Linux/Ubuntu community is a completely new experience for me and I must say I enjoy it very much. Now I know better what ClamAv is good for and what it can do and what it cannot. I am quite cautious myself with my computing activities and with what I download and install from the web. So far I have only installed applications from Ubuntu Software Center except for Chrome and Opera which I have downloaded from their sites. Those are the browsers that I have been using for years. I feel I am having still a Windows frame of mind and I am just beginning to understand that I have to learn to do things Ubuntu-way from now and on.
:KS
Cheers,
Marte

---

### Post by Habitual on 2017-01-31
clamav has found in the past, "exploits" from files downloaded directly from Lenovo (likely, "China"?)
Yawn. 
It has also found an mbr rewrite program I wrote with debug.exe.
in 1995.

So, Caution and Safe Hex. 
A Good router and some safe surf habits are a rockin' good time.

"Didn't get it from ***me***." :)

Good manual for new Linux Users: [http://rlworkman.net/howtos/rute/](http://rlworkman.net/howtos/rute/)

---

### Post by &amp;KyT$0P# on 2017-01-31
If you are thinking about running any sort of anti-malware software on Linux, [read this first]("https://ubuntuforums.org/showthread.php?t=2337052&p=13546076&viewfull=1#post13546076").

---

### Post by SeijiSensei on 2017-01-31
On a largely vanilla and fully-updated installation of Kubuntu 16.04, clamav flagged just two objects, both of which were symbolic links to other files. Symbolic links can be a way of hiding dangerous software, but in my case they were simply the consequence of how kernel updates are handled and not at all malicious.

Without seeing a representative sampling of the "threats" you cite, it is impossible to determine which of them might be plausible threats and which are simply false positives.  We'd need to see a list.

When you say files "related to LibreOffice" do you mean the executables themselves or documents?  Trojan documents with dangerous embedded macros are pretty commonplace on the Internet these days.  Usually they target MS Office programs like Word and Excel though.  It might be that on Linux systems those kinds of documents are flagged as associated with LibreOffice.  But again, without any knowledge of the kinds of files that have been flagged, we're all operating in the dark.

---

### Post by martemarziano on 2017-01-31
> **SeijiSensei said:**
>  But again, without any knowledge of the kinds of files that have been flagged, we're all operating in the dark.

You are right about that. I made some screenshots from the reslut of the scan which can be seen here:

[https://postimg.org/image/bck1loixb/](https://postimg.org/image/bck1loixb/)
[https://postimg.org/image/veijvz8rd/](https://postimg.org/image/veijvz8rd/)
[https://postimg.org/image/dsielvguf/](https://postimg.org/image/dsielvguf/)
[https://postimg.org/image/jdth829k9/](https://postimg.org/image/jdth829k9/)

I ran the ClamAv with pua checked and got 68 hits. At this very moment I am running it again with pua unchecked and so far after scanning about 180000 files, it still shows possible threats:0

---

### Post by martemarziano on 2017-01-31
ClamAv has just finished a full scan of the entire file system and this is the result:

Files scanned: 215987
Possible threats: 0

I must say that I am a happier man than yesterday at this time, though I don't know what stand to take regarding all the PUAs that formerly were flagged.

---

### Post by &amp;KyT$0P# on 2017-01-31
> **martemarziano said:**
> though I don't know what stand to take regarding all the PUAs that formerly were flagged.
For the hits in /usr - if those files are identical to the same files from fresh download of the package(s) they came from, then the hits are likely false positives.

---

### Post by SeijiSensei on 2017-02-01
I have no idea what a PUA is, but none of the files in /usr/lib/libreoffice/share/basic/FormWizard on my system was marked as infected.

---

### Post by #&amp;thj^% on 2017-02-01
Just for information only: (PUA) Potentially Unwanted Application, a type of privacy-invasive software

---

### Post by DuckHook on 2017-02-01
> **martemarziano said:**
> ClamAv has just finished a full scan of the entire file system and this is the result:

Files scanned: 215987
Possible threats: 0

I must say that I am a happier man than yesterday at this time, though I don't know what stand to take regarding all the PUAs that formerly were flagged.
@martemarziano

The following questions are very pertinent to your situation. Please take the time to answer them:

[LIST]
[*]Do you dual boot into Windows or run Windows in a VM?
[*]Do you habitually run questionable executables using WINE?
[*]Are you running a mail/database/file server on this machine that Windows machines rely on?
[*]Do you have Windows machines elsewhere on your LAN that you are trying to protect?
[/LIST]
If the answer to all of the above is "no", then ***AV is a waste of your effort and time.***

*Any AV only catches **Windows** viruses.* Installing it in a *pure* Linux environment is like insisting on a parachute aboard a boat. *It is useless*. It just wastes space, distracts from what really matters, and perpetuates "magic app" thinking. The amount of time and effort that you will spend fiddling with the thing, fussing over it, downloading signatures and chasing down false positives would be far better spent, say, creating and tuning apparmor profiles.

Just my two pennies worth.

---

### Post by martemarziano on 2017-02-01
> **DuckHook said:**
> 

[LIST]
[*]Do you dual boot into Windows or run Windows in a VM?
[*]Do you habitually run questionable executables using WINE?
[*]Are you running a mail/database/file server on this machine that Windows machines rely on?Marte
[*]Do you have Windows machines elsewhere on your LAN that you are trying to protect?
[/LIST]
If the answer to all of the above is "no", then ***AV is a waste of your effort and time.***


The answer to all the questions above is no. I guess I have been wasting some time on ClamAv and chasing all the PUAs that was flagged by it. Thank you DuckHook for putting my mind at ease!

cheers,
Marte
:KS

---

### Post by SeijiSensei on 2017-02-01
I honestly fail to understand how an app that enables you to design forms in LibreOffice could be "unwanted."  Here's the definition of a PUA from the [ClamAV FAQ ]("https://www.clamav.net/documents/miscellaneous-faq")which admits that scanning for them could lead to many false positives:

> 
    What is PUA? I get a lot of false positives named PUA.

    With the release of ClamAV 0.91.2 we introduce the option to scan for Potentially Unwanted Applications.

    The PUA database contains detection for applications that are not malicious by itself but can be used in a malicious or unwanted context. As an example: A tool to retrieve passwords from a system can be useful as long as the person who uses it, is authorized to do so. However, the same tool can be used to steal passwords from a system. To make use of the PUA database you can use the &#8211;detect-pua switch for clamscan or enable it in the config file for clamd (add: DetectPUA yes).

    At this point we DO NOT recommend using it in production environments, because the detection may be too aggressive and lead to false positives. In one of the next releases we will provide additional features for fine-tuning allowing better adjustments to different setups. NOTE: A detection as PUA does NOT tell if an application is good or bad. All it says is, that a file MAY BE unwanted or MAYBE could compromise your system security and it MAY BE a good idea to check it twice.


One problem with ClamAV is that, as an non-commercial enterprise, there are fewer controls over what constitutes a threat.  On the page where people can post alleged malware, they write "Our Virus Database is kept up to date with the help of the community. If you have a virus that is not detected by ClamAV, please fill out this form and the Detection Content Team will review your submission and update the virus database."  Considering that literally dozens of files get uploaded to the "Team" each day, I doubt any of them can get a very in-depth review.  I don't know if anyone gets paid to be a member of the Team.

Having said that I've used ClamAV for years on mail servers, in conjunction with [MailScanner]("http://www.mailscanner.info/") and [SpamAssassin]("http://spamassasin.apache.org/"), with great success.  Recently, though, as the nature of threats have changed, we've been relying on other features of ClamAV besides simple scanning for viruses, in particular its ability to treat MS Office documents with embedded macros as potential malware.  These are a very common threat in today's email world.  We already block all incoming Windows executables through MailScanner, so the range of threats for which we depend upon ClamAV is fairly limited.  We also use it in conjunction with [SquidClamAV]("http://squidclamav.darold.net/") to scan every web object my client's workforce downloads.

---

### Post by martemarziano on 2017-02-02
> **SeijiSensei said:**
> I honestly fail to understand how an app that enables you to design forms in LibreOffice could be "unwanted."  Here's the definition of a PUA from the [ClamAV FAQ ]("https://www.clamav.net/documents/miscellaneous-faq")which admits that scanning for them could lead to many false positives

Yes, I have realized now that a search with ClamAv and the PUA option checked can/may/will lead to flagging legit files as being possible threats. Following the advices from Herman AB and DuckHook, I think ClamAv is of no or very little use to me. 
Thanks everyone for this very engaging exchange! 
Ciao!
:KS

ps. I think I should mark the thread [solved]

---

