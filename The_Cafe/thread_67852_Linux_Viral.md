---
title: "Linux Viral"
date: 2005-09-21
forum: The Cafe
---

### Post by linbetwin on 2005-09-21
Here's a story from [Slashdot](http://linux.slashdot.org/article.pl?sid=05/09/21/1252213&from=rss):

*[INDENT]"Korean distributions of Mozilla and Thunderbird for Linux were infected with Virus.Linux.RST.b. This virus searches for executable ELF files in the current and /bin directories and infects them. It also contains a backdoor, which downloads scripts from another site, and executes them, using a standard shell."[/INDENT]*
I'm no expert on security, especially on Linux. Can anyone explain if this is a real risk? What should Ubuntu users do to stay safe?

---

### Post by newbie2 on 2005-09-21
Linux users warned over Firefox flaw
"Firefox users at risk are advised to upgrade to version 1.0.7 to guard against attack."
[http://www.theregister.co.uk/2005/09/21/linux_firefox_security_bug/](http://www.theregister.co.uk/2005/09/21/linux_firefox_security_bug/)

---

### Post by linbetwin on 2005-09-21
Here's a [link to the Symantec website](http://securityresponse.symantec.com/avcenter/venc/data/linux.rst.b.html) with information about the virus Linux.RST.B. Not very helpful information though.

---

### Post by kblood on 2005-09-21
Hey there,

This worries me a bit. I have until now lived under the belief that you only need an antivirus in Linux if you are going to be serving files to Windows machines, that is, so that Windows machines don't get infected.

Do we now need to start running antivirus programs as well in our stand-alone Linux machines?

Somebody shed some light, please...  :-? 

(I ask out of actual curiosity, don't want to screw up or spread FUD)

---

### Post by KingBahamut on 2005-09-21
Korean distributions of Mozilla and Thunderbird for Linux were infected with Virus.Linux.RST.b. This virus searches for executable ELF files in the current and /bin directories and infects them. It also contains a backdoor, which downloads scripts from another site, and executes them, using a standard shell.

External Links
[http://www.viruslist.com/en/weblog?calendar=2005-09](http://www.viruslist.com/en/weblog?calendar=2005-09)

Doing a little bit of poking around I notice that Symantec Recognizes this guy as a Class 1 blended threat with low impact.

---

### Post by karuptdata on 2005-09-21
I was under the impression that linux cant get a virus??This is really interesting....Ill search around and see what i can find..

[b]Thread continued in Community forum. --KB
[http://ubuntuforums.org/showthread.php?p=363327](http://ubuntuforums.org/showthread.php?p=363327)
[/b]

---

### Post by Brunellus on 2005-09-21
[QUOTE=KingBahamut]Korean distributions of Mozilla and Thunderbird for Linux were infected with Virus.Linux.RST.b. This virus searches for executable ELF files in the current and /bin directories and infects them. It also contains a backdoor, which downloads scripts from another site, and executes them, using a standard shell.

External Links
[http://www.viruslist.com/en/weblog?calendar=2005-09](http://www.viruslist.com/en/weblog?calendar=2005-09)

Doing a little bit of poking around I notice that Symantec Recognizes this guy as a Class 1 blended threat with low impact.[/QUOTE]
 It does, however, give the lie to our claims of virus impregnability....which leads me to wonder aloud just how secure a large project like mozilla can be.

Maybe Theo de Raadt is right about there being a need to step back and really lock down..

---

### Post by newbie2 on 2005-09-21
"Tristan Nitot, president of Mozilla Europe, has said Symantec's figures don't tell the whole story. For one thing, Firefox patches arrive faster than those for Explorer, he said, pointing out that Microsoft won't even issue its monthly patch in September. More flaws are being discovered in Firefox in the short term because of its newfound popularity, but overall, Explorer's flaws are more numerous and more severe, according to Nitot."
[http://www.techworld.com/security/news/index.cfm?NewsID=4449](http://www.techworld.com/security/news/index.cfm?NewsID=4449)

---

### Post by karuptdata on 2005-09-21
"Linux is also generally seen as a lower-risk platform than Windows, partly because it is less widely used on the desktop and therefore isn't targeted as often. The security picture is changing, though, according to the Symantec report, with platforms like Linux and Mac OS X coming under increasing scrutiny by potential attackers."

Do you guys see anti-vrus software and spyware affecting the linux community in large  amounts or do you think this is over blown hype slightly biased in M$ favor?

---

### Post by David Marrs on 2005-09-21
I've never heard claims that Linux can't get viruses, only that it's built around a better security model than Windows and that very few viruses have been written for it. That doesn't mean you shouldn't scan suspicious files for viruses or take any of the other sensible precautions.

You can download the **clamav** anti-virus utility from the ubuntu repositories. I'd also recommend installing **firestarter**, which is a really nice front-end to the iptables firewall.

I don't think the threat to Linux from viruses has been downplayed - it's definitely much safer today running Linux than Windows - but obviously it's folly to presume one's completely immune. I do occasional system scans and make sure my anti-virus database is up-to-date.

---

### Post by KingBahamut on 2005-09-21
I think that natively the nature of spyware and malware existing in a unix envoirment would be diffcult to pull off. If it were easy, youd see it in MAC by now, or Id imagine you would. So to the over all ramification of Spyware/Malware I say none. Viral contagion, that seems likely but what Id have to notice with respect to us in the Linux world, pragmatic upgrades would be easily addressed. While security might need to increase, I see an overall benefit to us. No, we arent Virus impregneble , but we are a hard rock to crack.

---

### Post by GeneralZod on 2005-09-21
[QUOTE=karuptdata]"Linux is also generally seen as a lower-risk platform than Windows, partly because it is less widely used on the desktop and therefore isn't targeted as often. The security picture is changing, though, according to the Symantec report, with platforms like Linux and Mac OS X coming under increasing scrutiny by potential attackers."

Do you guys see anti-vrus software and spyware affecting the linux community in large  amounts or do you think this is over blown hype slightly biased in M$ favor?[/QUOTE]

Linux has no defense against uneducated users with root access (and remember: every Ubuntu user has *access to* root by default) manually installing viruses.  Possibly SELinux will make things better.  If Linux ever becomes extremely popular, expect to see Funny.Screensaver!.deb on a web-site near you!

If you are not in the habit of installing software from untrusted sources, you are far better off with Linux or Mac than with Windows, for reasons that have been expounded over the years ad nauseum.

---

### Post by linbetwin on 2005-09-21
Companies like Symantec and other AV giant are probably thinking:

a) If people switch to Linux, which is much safer than Windows, we lose our customers, so...

b) we must start spreading the news about Linux viruses and vulnerabilities so that people will wake up in the middle of the night terrified and call us to order AV products.

Do you really think that AV companies really want to make the Internet "a safer place"? Hackers, phisers, spammers and virus creators are their best friends!

---

### Post by Kyral on 2005-09-21
Wait....if I understand this (and Linux User Permissions) if this thing infects me while I'm under my normal user, it can only attack the directories I have access to, right?

Oh well, time to run chkrootkit again :P

Also...its only Korean versions right? Ah, so it won't affect me

---

### Post by papangul on 2005-09-21
[QUOTE=linbetwin]Companies like Symantec and other AV giant are probably thinking:

a) If people switch to Linux, which is much safer than Windows, we lose our customers, so...

b) we must start spreading the news about Linux viruses and vulnerabilities so that people will wake up in the middle of the night terrified and call us to order AV products.

Do you really think that AV companies really want to make the Internet "a safer place"? Hackers, phisers, spammers and virus creators are their best friends![/QUOTE]
There is a high chance that the Korean virus thing is a conspiracy ? Maybe not, if it was really a conpiracy, they would target American or European repositories, that would get much more attention.

---

### Post by linbetwin on 2005-09-21
[QUOTE=papangul]There is a high chance that the Korean virus thing is a conspiracy ? Maybe not, if it was really a conpiracy, they would target American or European repositories, that would get much more attention.[/QUOTE]
 
I'm not saying this is a conspiracy, but we cannot rule out that possibility. It's not a virus that *attacks* Mozilla and Thunderbird, it's a virus that *ships* with Mozilla and Thunderbird! I smell a rat here!

---

### Post by primeirocrime on 2005-09-21
big rat indeed. Its seems clear that this more an act of sabottage than it is an act of virus spreading. Dirty hands lurk.

---

### Post by az on 2005-09-21
Well, linux works differently than windows and it is less vulnerable to a foreign piece of code.  However, in this case, the code was written into an application.  

This is a threat very different from the ones that windows users know about, since if it more easily tracked down (because more people are looking at the code)

I think these threats will pop up and we will see virus scanners which run on source code before it is compiled, rather than scanning binaries.

Sounds like a hook for Launchpad.  (Launchpad is a combination of utilities which will service open source development.  One-source one-stop shopping, if you will.  It is a Canonical project, just like Ubuntu is.)

---

### Post by KingBahamut on 2005-09-21
[QUOTE=azz]Well, linux works differently than windows and it is les vulnerable to a forigh peice of code.  However, in this case, the code was written into an application.  

This is a thread a lot different from the ones that windows users know about, since if it more easily tracked down (because more people are looking at the code)

I think these threats will pop up and we will see virus scanners which run on source code before it is compiled, rather than scanning binaries.

Sounds like a hook for Launchpad.  (Launchpad is a combination of utilities which will service open source development.  One-source one-stop shopping, if you will.  It is a Canonical project, just like Ubuntu is.)[/QUOTE]
 Regardless of its immediate ramifications what we need to realize is that as we grow in popularity, we are going to be faced with more and more vunlerabilities and security risks. What I do note in this however, is that I feel the Linux community is more than prepared to deal with this, both on the kernel level as well as the Desktop Level. Ill easily remind everyone that Linux was developed by Network geeks and Hackers for Network Geeks and Hackers. That alone gives us more strength than the proprietary nature of Microsoft. Ergo I feel that the spread of vulnerability and security risk will be much lower to us than it was/is for MS. Though dont doubt my words in this statement , We are not invulnerable, but much stronger.

---

### Post by lotusleaf on 2005-09-21
I always scan new files with clamav just in case because I believe in tin foil hat security. :) Chkrootkit and rkhunter are also good tools to keep in use.

---

### Post by jimcooncat on 2005-09-21
So if we stick to the official repositories, won't we be safe (or at least safer) from this type of attack? Are measures in place to ensure the integrity of the source code, compilers used, and distribution?

I can see in ten to twenty years that binary distributions may be obsolete. Ubuntu does support a source-based distribution model, correct?

---

### Post by lotusleaf on 2005-09-21
[QUOTE=jimcooncat]So if we stick to the official repositories, won't we be safe (or at least safer) from this type of attack?[/QUOTE]

Safer, yes. I hardly consider this issue newsworthy though, the whole issue amounts to common sense. For example, if you were a Windows user, would you download updates for MSIE from some random server or from M$'s site? It's pretty simple, really.

IMO this is probably just another anti-nix smear psy-op effort.

[gnupg](http://www.gnupg.org/) is your friend with plenty of documentation available. Rather than focusing so much on anti-virus solutions, people should understand how to properly verify files before installing them.

---

### Post by jimcooncat on 2005-09-21
[QUOTE=lotusleaf]Safer, yes. I hardly consider this issue newsworthy though, the whole issue amounts to common sense. For example, if you were a Windows user, would you download updates for MSIE from some random server or from M$'s site? It's pretty simple, really.[/QUOTE]Actually, it's not quite the same thing. I'm waiting to download a Firefox update from a Ubuntu site as soon as it's available.

[QUOTE=lotusleaf]This is probably just another anti-nix smear psy-op effort.[/QUOTE] No doubt planned by those covert "old Korean" extremist Opera zealots.

---

### Post by -Rick- on 2005-09-21
Thats makes me wonder...what if someone just modified the source of a popular program, compiled it and submitted his package to a download site. I guess that might be a drawback from open source.
And even if the user doesn't run this program as root, it could still mess with their personal files.

---

### Post by lotusleaf on 2005-09-21
[QUOTE=jimcooncat]I'm waiting to download a Firefox update from a Ubuntu site as soon as it's available.[/quote]

[ftp://ftp.mozilla.org/](ftp://ftp.mozilla.org/) works [just fine](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.0.7/linux-i686/en-US/) for those who don't want to wait for .debs :)

> No doubt planned by those covert "old Korean" extremist Opera zealots.

Consider: who stands to benefit most from any attempts to smear mozilla?

[more food for thought](http://slashdot.org/comments.pl?sid=162931&cid=13615119)

[QUOTE=-Rick-]Thats makes me wonder...what if someone just modified the source of a popular program, compiled it and submitted his package to a download site.[/QUOTE]

Again, gnupg is your friend ;) Anyone who downloads software from random places on the net and fails to gpg --verify, match good checksums, etc. deserves what they get.

[size=1]all text within this post was written in my opinion[/size]

---

### Post by az on 2005-09-21
[QUOTE=jimcooncat]So if we stick to the official repositories, won't we be safe (or at least safer) from this type of attack? Are measures in place to ensure the integrity of the source code, compilers used, and distribution?

I can see in ten to twenty years that binary distributions may be obsolete. Ubuntu does support a source-based distribution model, correct?[/QUOTE]


What ends up in the official repositories is well-tested and closely examined.   Also, by using the repositories and getting your regular updates, you diminish the risk.  And yes, all packages are signed by the maintainers, so that makes sure that not just anyone can add crap to them.

Some people complain about bleeding-edge stuff not being included, but *this* is a good reason to wait a bit.  For my needs, this is truly the best of bothworlds.


As for what will happen in ten to twenty years, I think we will all be wearing spandex and will no longer have the need to eat, due to surgical implantation of self-sustaining caloric packs.  But I may be wrong.

---

### Post by jimcooncat on 2005-09-21
One of the first distros I tried was Source Mage, which was supposed to avoid security problems such as this. The idea was that the source code would be copied from the original author's web site, checked against the distro's MD5 hash of it.

A lot of the installations (especially older tools) didn't work well this way, because the sites were no longer up, the version specified wasn't posted, or a new release would get swamped by requests.

The only way you could install a full working environment was through a mirror that a couple of volunteers maintained through a residential cable connection. Once I found this out, I bailed to Gentoo.

That was a few years ago, I'm sure they have a more sophisticated infrastructure in place now.

---

### Post by -Rick- on 2005-09-21
[QUOTE=lotusleaf]Again, gnupg is your friend ;) Anyone who downloads software from random places on the net and fails to gpg --verify, match good checksums, etc. deserves what they get.[/QUOTE]
Only for the ones who aren't lazy to do so, who know where to get the key/MD5 sum/something similar and know how to use the tool to check it.
I don't think everyone who uses or is going to use linux qualifies to that.
Also noone deserves to get a virus or any other malware, even if they don't give shit about computers and thus don't know how to 'protect' their PC from some stupid geeks who think making something like that is cool ;)

---

### Post by az on 2005-09-21
[QUOTE=jimcooncat]That was a few years ago, I'm sure they have a more sophisticated infrastructure in place now.[/QUOTE]


I think they call it Gentoo, these days  :)

---

### Post by lotusleaf on 2005-09-21
[QUOTE=-Rick-]even if they don't give shit about computers and thus don't know how to 'protect' their PC[/QUOTE]

A person who doesn't know how to drive shouldn't operate a car without proper instruction. The car doesn't care that they don't care, and they will likely find misfortune quickly. As they say "the tree of life is self-pruning"

Perhaps in the future there will be a global AI which will protect the careless, who knows.

[food for thought](http://slashdot.org/comments.pl?sid=162931&cid=13614945)

---

### Post by KingBahamut on 2005-09-21
[QUOTE=jimcooncat]One of the first distros I tried was Source Mage, which was supposed to avoid security problems such as this. The idea was that the source code would be copied from the original author's web site, checked against the distro's MD5 hash of it.

A lot of the installations (especially older tools) didn't work well this way, because the sites were no longer up, the version specified wasn't posted, or a new release would get swamped by requests.


The only way you could install a full working environment was through a mirror that a couple of volunteers maintained through a residential cable connection. Once I found this out, I bailed to Gentoo.

That was a few years ago, I'm sure they have a more sophisticated infrastructure in place now.[/QUOTE]
 You know but I had issues with casting spells to get my programs installed. Not wholely unsimilar to Sorcerer distro. And with MD5 being as easily hacked as it is, that doesnt give me anymore security in mind than anything else.

---

### Post by blastus on 2005-09-21
[QUOTE=GeneralZod]Linux has no defense against uneducated users with root access (and remember: every Ubuntu user has *access to* root by default) manually installing viruses.[/QUOTE]

Exactly. Most people who use computers use MSWindows and are not interested in learning the basics of how the OS or the Internet works. I'd say the vast majority of them just know how to turn it on, use Outlook Express, Internet Explorer, a little bit of MSOffice, and turn it off. They've bought their computer with MSWindows and MSOffice preinstalled and someone else has configured Outlook Express and Internet Explorer for them. 

To them, the OS is rightfully just a means to an end, just like a car is a way to commute. And you can't blame them for thinking that way. The problem is that they don't know how to "drive" the OS. And Microsoft encourages them to sit back and let Microsoft handle the wheel. They trust that Microsoft knows what it's doing and they are unable to challenge their trust in Microsoft because they don't have the computer expertise. However, in this scenario, Microsoft is like a defective "autodriver" that doesn't know how to drive the car safely.

---

### Post by lotusleaf on 2005-09-21
[QUOTE=KingBahamut]And with MD5 being as easily hacked as it is, that doesnt give me anymore security in mind than anything else.[/QUOTE]

Which makes me wonder, with the state of md5/sha1, why aren't more people switching to [tiger](http://www.cs.technion.ac.il/~biham/Reports/Tiger/), [whirlpool](http://planeta.terra.com.br/informatica/paulobarreto/WhirlpoolPage.html) and the like, or including several sums to choose from rather than just md5/sha1?

FWIW: ["New Cryptanalytic Results Against SHA-1"](http://www.schneier.com/blog/archives/2005/08/new_cryptanalyt.html)

---

### Post by jimcooncat on 2005-09-21
[QUOTE=blastus]Exactly. Most people who use computers use MSWindows.....[/QUOTE]

<rhetorical>I wonder how MS Windows got into this discussion?</rhetorical>

I'll wager that the majority of Ubuntu users rely on apt, synaptic, or whatever to do any security checking for them that's needed. I know I do. If I need to do more than that to use the official repositories, we really should discuss it here and now. 

The reason I use Ubuntu now instead of Gentoo is the same as why I drive a Honda now instead of spending time under the hood of my old Ford.

---

### Post by xequence on 2005-09-21
If I EVER get a linux virus that does anything, im gonna consider some BSD variant. SInce this is only in Firefox, and im using opera...

---

### Post by bob_c_b on 2005-09-21
So I was quickly perusing this debate over at /. for a few minutes and several people pointed out that this was basically a fan site providing the binaries and then someone asked a relevant question...

"If you find an infected version of Winzip on an internet site, would you blame Winzip.com ?"

Possibly the first intelligent reply I have seen over there in weeks.

And I think that sums up the whole debate for me. This virus has been around since 2002 and if you keep patched and avoid installing stuff as root whenver possible you certainly mitigate your risk of this kind of thing. That is a little simplistic on my part, and it begs the question as to what will happen as Linux grows, but *nix in general have survived for a long time without massive malware/virus issues, I hardly think this is a new trend. 

The moral of the story is, if you are going to provide any software to the public, make sure your own house is in order first.

---

### Post by phen on 2005-09-21
lotusleaf: your car/computer analogy is somehow not correct: 

you have to know how to drive a car, to drive a car. but you do NOT have to know how to set up the airbag ignition time and how to design a frame so that a maximum of energy is absorbed by it, to drive a car. 

hence it is very important for an os to have security solutions everybody can use. 

But like driving safely, everybody should be aware of the risks of surfing/installing downloaded sw etc. and therefore surf safeley :-)

but hey, we're lucky because linux has a perfect grip in corners and a whole bouncy castle as airbag!

---

### Post by DirtDawg on 2005-09-21
I'm sorry, but I'm confused.
Were the actual install files for Korean Firefox infected? If so, where were people getting the files? Otherwise, if the virus was "piped" in from the net through a security hole, wouldn't the users have to okay the install (via root access)? 
Were they more like small scripts that launched when the executable files were launched? If that's the case, wouldn't the scripts need root access to do any real harm?

---

### Post by bob_c_b on 2005-09-21
[QUOTE=DirtDawg]I'm sorry, but I'm confused.
Were the actual install files for Korean Firefox infected? If so, where were people getting the files? Otherwise, if the virus was "piped" in from the net through a security hole, wouldn't the users have to okay the install (via root access)? 
Were they more like small scripts that launched when the executable files were launched? If that's the case, wouldn't the scripts need root access to do any real harm?[/QUOTE]

From what I understand a Korean "fan" site had pre-compiled binaries they were hosting, those files were infected. It has little to nothing to do with Mozilla or FireFox actually, but it's tough to grab headlines with facts all the time ](*,)

---

### Post by BoyOfDestiny on 2005-09-21
Heh, why I stopped reading slashdot and the register. Anyway on to the topic.

It seems this was a tad "hoaxish", but I think just as with people, when you get sick you will build up immunity (hopefully!). 

In the case of open source, you are likely to get the patch more quickly, and thus be immuned. The more flaws are found, the stronger Linux gets. 

Security by obscurity (closed sourced style) might seem like a good idea, but once a "malevolent" group exploits it, you are in trouble. I think of this as being in a biodome, which is great until something you don't expect gets in. Without a lot of safeguards in place, explotation is even simpler (poor immunity.) Plus, unless you are decompiling wizard... you don't really know what's in the binary...

The only downside in the case of open source is if you don't update your apps (or get a bug fix) or you download software that has the code tainted... (not getting your immunization leaves you vulnerable)

Again the first primarily deals with the user, and I'd recommend not picking up debs from XXX sites or sites with the word warez :P As for the other, there is trust, and I trust the eyes of the intelligentsia.

---

### Post by savage on 2005-09-22
Linux safety out of the box is very dependent on distro and configuration. Ubuntu is fairly secure. This is not the first time something like this has happened. Open source projects have had code tampered with before. For instance there was a security breach with CVS [http://www.securityfocus.com/advisories/4908]("http://www.securityfocus.com/advisories/4908") that if I remember correctly was actually taken advantage of. Source code was altered on several open source projects, however the reaction was fairly quick, and no known lasting damage was done (wish I could find the exact news story). BIND for instance has come under such severe attack that only a madman runs their own personal DNS server.

Seperation of source code and binaries from hashes is important. Then a cracker needs to break into two servers simultaneously.

Remember though that open source in general has an excellent track record for security vulnerabities. Also keep in mind that *nix is the server environment of choice, *nix has been on the frontline, and has been under attack for much of it's existence. If someone could create a virus that would infect the worlds linux servers why haven't they done so yet?

Some of the answers are; linux is fragmented, which is good because there are differences between distros, and highly configured environments, that complicate a malicious persons job. There isn't enough small fish (basic users) market share to make it worth the time. Many of the viruses are written to gather personal information; emails for spam, credit cards, etc. Linux systems have alot of the basic security tenets right for more in that vein read [The Six Dumbest Ideas in Computer Security.]("http://www.ranum.com/security/computer_security/editorials/dumb/")

---

