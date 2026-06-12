---
title: "Who's watching the keepers, or &quot;is it safe?&quot;"
date: 2010-10-24
forum: Security
---

### Post by emarkay on 2010-10-24
Been doing some reading on "Windows versus Ubuntu", beyond simple "malware" and Google led me here: [http://cryptome.org/0002/clsid-beyond.htm](http://cryptome.org/0002/clsid-beyond.htm)

Yea, the Windows Registry is a hive of unknowns, and once it's modified, it's no longer "threaded" in a literal sense, to "undo".

Philosophically speaking, and please no "ya pays yer munny ..." statements, but how does one know if anything added to Ubuntu (let's presume for now we are talking about the legit repos as found in Synaptic; no PPA, no "Install with Arcive Manager" dowloads) is "clean and pure".

Not considering locked down Crypto applications, or "Echo to terminal everything" systems, but a typical research or corporate, networked, online and updated & managed system.

From unintended memory leaks-to-disk, to a few more bits than needed on an upload, to a genuine rogue application of danger, what realistic assurances are there that there's no "MIB behind the curtain" taking notes.  I know there's a great deal  "self policing" and cross validation in Open Source, but...

No, I am not a tin-foil paranoid, nor a well versed expert in SIGINT and all that, but I've never "seen" anything that validated the perception that "Ubuntu is safer (for want of a better term) than Windows".

---

### Post by amauk on 2010-10-24
> Who's watching the keepers?It's open source, so potentially everyone is watching

The packages stored in the repos (this goes for the majority of distros, not just Ubuntu) are cryptographically signed, so you can be 99.999% sure that any package in the repos is "genuine" and not been tampered with

---

### Post by emarkay on 2010-10-24
> **amauk said:**
> It's open source, so potentially everyone is watching
The packages stored in the repos (this goes for the majority of distros, not just Ubuntu) are cryptographically signed, so you can be 99.999% sure that any package in the repos is "genuine" and not been tampered with


Correct, but I was more curious about the content, not the container.  What sort of review is done, and/or is there any validation or inspection of the applications? 

Is there any method where, for an example, an apparently legit and functioning application may be poorly written to cause an unseen corruption or unwarranted access to user data; is anyone "checking" the apps, other than the combined userbase of the OS and the app?

Have there, for reference, been any instances where an inadvertent or intentional "backdoor"  or other aforementioned issue has been found in a Ubuntu application?  What was the response of the community?

---

### Post by perspectoff on 2010-10-24
GnuBeard is watching.


---------------------------------------------------------

I've heard of GnuBeard!

Apparently he runs a pirate software distribution network from an offshore island, even though he has offices in London.

He raids software concepts from the big software corporations, like the Redmond East India Software Company.

He was given the Order of the Empire, however, by the United Kingdom of Google and now is known as Sir GnuBeard.

In fact, his piratical crew embodies concepts of classicalists such as Locke, Hobbes, and Stallman, and some say that true democracy lives here moreso than in any other software distribution network.

While some of his crew gets inebriated singing his praises, and while there are frequent congregations of his followers in far-off ports, GnuBeard himself stands as the overseer of all his crews and makes sure they do not stray far from "the code."

---

### Post by perspectoff on 2010-10-24
> **emarkay said:**
> 

Have there, for reference, been any instances where an inadvertent or intentional "backdoor"  or other aforementioned issue has been found in a Ubuntu application?  What was the response of the community?

Sure. That can happen in any collection of software programs, anytime, anywhere. No one is 100% safe from espionage and malfeasance, ever. 

BTW, you can't get rid of germs, either. (There's probably some on your keyboard right now!)

See:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

---

### Post by rookcifer on 2010-10-24
> **emarkay said:**
> No, I am not a tin-foil paranoid, nor a well versed expert in SIGINT and all that, but I've never "seen" anything that validated the perception that "Ubuntu is safer (for want of a better term) than Windows".

So you trust Windows, a closed-source OS developed by a company that has done a lot of very shady things like adding [NSA backdoor crypto keys]("http://www.heise.de/tp/r4/artikel/5/5263/1.html"), yet you want to doubt Ubuntu?

---

### Post by uRock on 2010-10-24
Windows has a common-criteria EAL rating, ubuntu doesn't.

I do trust Ubuntu's repos. The reason is this, open source gets looked at by a lot of people. Geeks like me like to run Wireshark and other applications that sniff the network and see where the PC is sending information, if at all, when the PC is supposed to be "at idle." I have seen no communications that would make me suspect a program is talking to servers other than those which handle the network facing services that I am running, such as Pidgin connecting to Yahoo and MSN's servers, as well as XChat connecting to Freenode's servers. Once opening a browser it is hard to know which IPs are which until one looks into the packets to see what info is being shared within them. I am not on that level yet, but I am working to get there. I have faith that there are geeks like me who do have the knowledge to strip packets and decode exactly what is being sent and that said geeks would raise an alarm, either here on the forums or directly communicating with the devs to get the problem solved.

Windows doesn't have a repo, so the only way you can trust an application for Windows is if they come with an EAL rating, because the code is not open source for others to check into it.

---

### Post by rookcifer on 2010-10-24
> **uRock said:**
> Windows has a common-criteria EAL rating, ubuntu doesn't.

I do trust Ubuntu's repos. The reason is this, open source gets looked at by a lot of people. Geeks like me like to run Wireshark and other applications that sniff the network and see where the PC is sending information, if at all, when the PC is supposed to be "at idle." I have seen no communications that would make me suspect a program is talking to servers other than those which handle the network facing services that I am running, such as Pidgin connecting to Yahoo and MSN's servers, as well as XChat connecting to Freenode's servers. Once opening a browser it is hard to know which IPs are which until one looks into the packets to see what info is being shared within them. I am not on that level yet, but I am working to get there. I have faith that there are geeks like me who do have the knowledge to strip packets and decode exactly what is being sent and that said geeks would raise an alarm, either here on the forums or directly communicating with the devs to get the problem solved.

Windows doesn't have a repo, so the only way you can trust an application for Windows is if they come with an EAL rating, because the code is not open source for others to check into it.
ith EAL4+

EAL is meaningless.  Besides, there are Linux distros with with EAL4+ ratings anyway.  Red Hat is one.

---

### Post by emarkay on 2010-10-24
> **uRock said:**
> 
I do trust Ubuntu's repos. The reason is this, open source gets looked at by a lot of people. Geeks like me like to run Wireshark and other applications that sniff the network and see where the PC is sending information, if at all, when the PC is supposed to be "at idle." I have seen no communications that would make me suspect a program is talking to servers other than those which handle the network facing services that I am running, such as Pidgin connecting to Yahoo and MSN's servers, as well as XChat connecting to Freenode's servers. Once opening a browser it is hard to know which IPs are which until one looks into the packets to see what info is being shared within them. I am not on that level yet, but I am working to get there. I have faith that there are geeks like me who do have the knowledge to strip packets and decode exactly what is being sent and that said geeks would raise an alarm, either here on the forums or directly communicating with the devs to get the problem solved. Windows doesn't have a repo, so the only way you can trust an application for Windows is if they come with an EAL rating, because the code is not open source for others to check into it.


Thanks.  Glad someone here's not trying to be a total jokster...  My point was to see if anyone else was concerned, curious or aware of this issue.  FWIW, I thought it was obvious that I don't "do" Windows...

---

### Post by uRock on 2010-10-24
> **emarkay said:**
> Thanks.  Glad someone here's not trying to be a total jokster...  My point was to see if anyone else was concerned, curious or aware of this issue.  FWIW, I thought it was obvious that I don't "do" Windows...
I do feel that Ubuntu's servers are in great hands as far as security goes. If bad programming were to be placed on the servers it would get detected and fixed pretty quickly.

EAL is a trusted source for finding trustable programs for Windows and UNIX/Linux systems. I think it is good for people to look up software that is actually rated for safety.

---

### Post by DZ* on 2010-10-24
> **rookcifer said:**
> So you trust Windows, a closed-source OS developed by a company that has done a lot of very shady things like adding [NSA backdoor crypto keys]("http://www.heise.de/tp/r4/artikel/5/5263/1.html"), yet you want to doubt Ubuntu?

I personally woudn't even go online from Windows (I keep w7 as a virtual guest to edit docx colleagues keep sending me).

However, that article smacks of a conspiracy theory. There are accusations, like that there is "conclusive evidence that the second key belongs to NSA". But where is that evidence?

*'Windows developers attending the conference did not deny that the "NSA" key was built into their software. But they refused to talk about what the key did, or why it had been put there without users' knowledge.'*

The only "evidence" that NSA has an "access system" [to Windows installations] appears to be in that the key name contained the letters NSA. Here is the exchange:
[http://cryptome.org/nsakey-ms-dc.htm](http://cryptome.org/nsakey-ms-dc.htm)

---

### Post by amauk on 2010-10-24
I'd love to see some stats and general info regarding packages in the repos.
A behind-the-scenes view of the packaging & verification process.

Any package from a major upstream will have many eyes on it (GNU, Gnome, Firefox, etc.) so they're not an issue

and I'm guessing most the packages in "main" are given a once over by both Debian & Ubuntu
but what about "universe"?

Take some small random app in universe
Who has looked at this, and when?
Only when app first packaged, or is it inspected more regularly?
How closely are updates scrutinised?

With things like AppArmor and other LSM's, is this even an issue?

Probably something to ask Kees Cook (he seems to be the main security bod at Canonical)

---

### Post by anomie on 2010-10-24
[QUOTE=emarkay]From unintended memory leaks-to-disk, to a few more bits than needed on an upload, to a genuine rogue application of danger, what realistic assurances are there that there's no "MIB behind the curtain" taking notes.  I know there's a great deal  "self policing" and cross validation in Open Source, but...[/QUOTE]

I would go so far as to say that if you haven't personally reviewed (and understood) every line of source code, you can't be 100% sure that something nasty is *not* happening under the covers. Even if no one in the history of FOSS ever has or ever will manage to check in a snippet of malicious code (unlikely!), there are unintentional problems that are exploited regularly by researchers and - much worse - by people who make money ripping you off. 

That said, there's always going to be a leap of faith when it comes to computing. FOSS makes the leap a whole lot easier. More eyeballs on the code is a very good thing. Sane levels of peer scrutiny and line-by-line audits are a very good thing. Literally forcing applications to be designed securely because they can not hide implementation in a proprietary binary is a very good thing. 

But if you want a *sure thing* without getting your head around all the source you compile and execute, you're not going to get it. Take an informed leap, or throw in the towel on computing.

---

### Post by cariboo on 2010-10-24
The process a devolper has to go through, is documented [here]("https://wiki.ubuntu.com/UbuntuDevelopment"). Another big plus is that a developer has to sign his/her packages, so if something does go wrong, we know who to blame. :)

---

### Post by leeper69 on 2010-10-24
Window$ is a virus! Ubuntu is free and that about says it all!

---

### Post by Chayak on 2010-10-25
I work as a security researcher and what I've learned over the years is that no OS is 100% secure.  Windows has it's flaws, but overall because it's targeted by everyone it can be fairly secure if configured correctly.  I'm not denying that it has it's problems but the majority of exploits affect 3rd party software running on windows.  PDF exploits being the biggest right now.

Linux has it's own problems but there are a number of people constantly looking at the code which allows it to be fairly secure itself if configured correctly.  I've taken an Ubuntu laptop to DEFCON for the past three years and after doing hash comparisons and forensic examination before and after the installs were not compromised.  That says a lot since DEFCON's wireless network is said to be the most hostile on the planet, which I'm not inclined to dispute.

In the end security rests mostly upon the users, which are the biggest risk in any system.  I do mostly malware research so I run all my browsing and other tasks inside of a virtual machine when I'm using windows.  I just revert it back to a known good state after I'm done.  I do the same thing for my analysis VMs.  In the end you have to assess your realistic risk, your usability needs, your security needs, and find a balance.

---

### Post by emarkay on 2010-10-27
Thanks - and yes, it really is about common sense, awareness and the ability to do one's own investigation (research), but I guess I can sum this all up by using a favorite analogy: "One can be the best test pilot in the world, but if you are flying commercial, you are at the mercy of the unseen nut behind the wheel."

I see that Mr. Young's site was referenced again here; alas, someone needs to remind the naked emperor once in a while.  Glad there's someone out there willing to tickle the dragon's tail.

Peace!
MRK

---

### Post by emarkay on 2010-10-27
Also, I am surprised no one mentioned:
[https://wiki.ubuntu.com/SecurityTeam/Policies](https://wiki.ubuntu.com/SecurityTeam/Policies)

---

### Post by SeijiSensei on 2010-10-28
> **emarkay said:**
> Correct, but I was more curious about the content, not the container.  What sort of review is done, and/or is there any validation or inspection of the applications?

By my count of [this list]("http://packages.ubuntu.com/maverick/allpackages?format=txt.gz") there are over 37,000 packages in the Maverick repositories.  Even if just ten percent of these projects issue a new source code version within a six-month release cycle, that's still almost 4,000 different packages to review.  Does someone at Ubuntu compile, install and test each of these upgraded packages?  How much do they rely on the Debian project?  Are they examined for malicious code?

In the end, though, I don't trust the applications on my machine because they came from Ubuntu.  I'd trust those same applications if they came from Fedora or CentOS or Arch or Gentoo.  That's because I trust the process by which open-source applications are written.  My sense is that most major applications are written either by large entities like the Mozilla Organization or by volunteer "committees" linked by mailing lists and shared svn or git repositories.  When multiple people have to agree before a patch is committed to the official source, and that patch appears on publicly-accessible mailing lists or repositories, it's hard to create hidden back doors.  Ultimately, for me, it comes down to trusting that the developers will continue to maintain the extraordinarily high standards of coding and ethics that have characterized the development of free and open source software since its beginning.

---

### Post by Soul-Sing on 2010-10-28
nice discussion bout the NSA and Selinux, on the edge of paranoia imo.
: [http://forums.fedoraforum.org/archive/index.php/t-171053.html](http://forums.fedoraforum.org/archive/index.php/t-171053.html)

---

### Post by mainerror on 2010-10-28
> **SeijiSensei said:**
> By my count of [this list]("http://packages.ubuntu.com/maverick/allpackages?format=txt.gz") there are over 37,000 packages in the Maverick repositories.  Even if just ten percent of these projects issue a new source code version within a six-month release cycle, that's still almost 4,000 different packages to review.  Does someone at Ubuntu compile, install and test each of these upgraded packages?  How much do they rely on the Debian project?  Are they examined for malicious code?

In the end, though, I don't trust the applications on my machine because they came from Ubuntu.  I'd trust those same applications if they came from Fedora or CentOS or Arch or Gentoo.  That's because I trust the process by which open-source applications are written.  My sense is that most major applications are written either by large entities like the Mozilla Organization or by volunteer "committees" linked by mailing lists and shared svn or git repositories.  When multiple people have to agree before a patch is committed to the official source, and that patch appears on publicly-accessible mailing lists or repositories, it's hard to create hidden back doors.  Ultimately, for me, it comes down to trusting that the developers will continue to maintain the extraordinarily high standards of coding and ethics that have characterized the development of free and open source software since its beginning.

Hold on. You don't trust code from Ubuntu repositories but from Fedora and CentOS? Care to elaborate why. I'm very interested.

---

### Post by SeijiSensei on 2010-10-28
I don't trust them any more or less than Ubuntu.  I wrote that I trust all the major distributions about equivalently, but ultimately, though, I have to trust the developers and the processes by which open software is created.  There's not going to be much difference among the versions of most open applications shipped by the major distributors.  They may differ a bit in patch level, but a copy of Apache is going to be about the same regardless of who ships it.  Dangerous security flaws are usually fixed by all the major players within largely similar time frames as well.

---

### Post by mainerror on 2010-10-28
> **SeijiSensei said:**
> I don't trust them any more or less than Ubuntu.  I wrote that I trust all the major distributions about equivalently, but ultimately, though, I have to trust the developers and the processes by which open software is created.  There's not going to be much difference among the versions of most open applications shipped by the major distributors.  They may differ a bit in patch level, but a copy of Apache is going to be about the same regardless of who ships it.  Dangerous security flaws are usually fixed by all the major players within largely similar time frames as well.

Ah got you now.

---

### Post by kliq on 2010-10-28
For those who tend to just trust developers read the last post in this:- [http://forums.debian.net/viewtopic.php?p=105900#105900](http://forums.debian.net/viewtopic.php?p=105900#105900)
& Never let yourself think - 'that wont happen again'

---

### Post by tgm4883 on 2010-10-29
> **kliq said:**
> For those who tend to just trust developers read the last post in this:- [http://forums.debian.net/viewtopic.php?p=105900#105900](http://forums.debian.net/viewtopic.php?p=105900#105900)
& Never let yourself think - 'that wont happen again'

The link he posted is invalid. Wish I could see more on that story but until I can see some sort of research on that i'll take it with a grain of salt.

---

### Post by uRock on 2010-10-29
If one is that paranoid about software, then why use a computer at all?

---

### Post by anomie on 2010-10-29
Possibly he was referring to this incident: 
[list]
[*] [http://www.theregister.co.uk/2008/05/16/debian_openssl_flaw/](http://www.theregister.co.uk/2008/05/16/debian_openssl_flaw/)
[*] [http://blogs.computerworld.com/fixing_debian_openssl](http://blogs.computerworld.com/fixing_debian_openssl)
[/list]

Even if he wasn't, it's worth considering in the context of this discussion.

---

### Post by mainerror on 2010-10-29
> **uRock said:**
> If one is that paranoid about software, then why use a computer at all?

This.

---

### Post by Chayak on 2010-10-29
Yeah there's always the chance of a backdoor.  If you're the tinfoil hat type of person then just remember that the NSA has contributed code to the Linux kernel itself, not just SELinux.

Oh and don't forget the hardware! There are a lot of motherboards and parts that come from China who's known to want backdoors in systems. You could have backdoors in the network chipsets.

You don't think a group of expert programmers couldn't obfuscate something in open source code?

Take off the tinfoil hat or just stop using computers.

---

### Post by cariboo on 2010-10-29
This thread has veered so far off topic, it's time for it to be closed.

---

