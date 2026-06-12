---
title: "Does spyware exist in the Linux world?"
date: 2006-08-18
forum: Server Platforms
---

### Post by xp_newbie on 2006-08-18
One of the reasons I switched to Linux is that I got sick of all the spyware, viruses and trojan horses in the Microsoft Windows world.

I thought that since Linux is open source, it is easy to find out whether someone tries to sneak in spyware, a virus or a trojan.

Thus, I conveniently let the Update Manager update my system (or should I say "blindly"?)

Recently however I came across a need for playing some video clips from web sites that support only Windows Media Player. I didn't know whether this was possible in Linux, but after some research I discovered that this is possible if I install a package called **w32codecs**.

Alas, w32codes was nowhere to be found using Synaptic (even with "universe" and "multiverse" enabled).

But after a while, I found [this Ubuntu Blog]("https://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/") that explains how to obtain and install the w32codecs. I even managed to add [the Penguin Liberation Front]("http://doc.ubuntu-fr.org/doc/plf") to Synaptic as a 5th repository, do a search and find the much-yearned-for w32codecs package.

But when I attempted to install it, I received a warning message:

> You are about to intall software that can't be authenticated!
Doing this could allow a malicious individual to damage
or take control of your system

Huh??? :???: I went through all this just to find out that I may be downloading "unsafe software"?

My questions are basically the following:
[LIST=1]
[*]Is the PLF web site trustworthy, despite its "underground appearance"?
[*]How do you deal in general with the possibility of installing malware? Do you only install from the "Officially Supported" repository?
[*]Would you recommend avoiding the w32codecs package due to its dubious status?
[/LIST]

Thanks!
Alex

---

### Post by aysiu on 2006-08-18
I don't know all the details, but basically the official Ubuntu repositories are authenticated with keys for extra security.

The PLF repositories are just fine, but they are not authenticated.

It's sort of like how when you install Firefox extensions and themes--almost all of them on the Mozilla website are just fine, but for most you'll get a warning about how it should be from a trusted source.

If you want to just know if PLF is okay, I'm saying "Yes, they're okay."

If you're superparanoid and will absolutely not use any repository that's not authenticated, then just stick to the official Ubuntu repositories. I've never heard of anyone getting spyware from the PLF repositories.

---

### Post by 23meg on 2006-08-19
> How do you deal in general with the possibility of installing malware? Do you only install from the "Officially Supported" repository?There's an unwritten law of trust; it's mostly automatically assumed that nobody setting up a repository to help others in the community download Free / open source software easily has any bad intentions. 

Needless to say, this assumption is technically very dangerous, but in practice, it's more or less how things work: no well regarded repository contains malware.

---

### Post by rag on 2006-08-19
1. I've had no problems with PLF. I take it as trustworthy.
2. Very rare for commonly used files like this.
3. w32codecs are OK (used them for years).

You could also temporarily add the repository 
 deb [http://debian-multimedia.org/](http://debian-multimedia.org/) sid main
add what multimedia files your want then disable it again.

---

### Post by Pumm4 on 2006-08-19
It would be very hard for someone creating apps under the GPL to make backdoor's, spyware, etc. On the other hand, open source may allow a individual to find a vulnerability faster - true, but it also alows for anyone to fix that vulnerability and very fast.

Spyware is "addicted" to closed-source where user can't see what is going on and they are on disadvantage.

[SIZE=2]Spyware is Windows-only ;)
[/SIZE]

---

### Post by missmoondog on 2006-08-19
to answer #3, only avoid the w32codecs if you don't want to play very many videos!

---

### Post by xp_newbie on 2006-08-21
> **Penguinux Pumma said:**
> It would be very hard for someone creating apps under the GPL to make backdoor's, spyware, etc.

Do I understand from this that the w32codecs are open-source and under GPL?

Thanks,
Alex

---

### Post by 23meg on 2006-08-23
> **xp_newbie said:**
> Do I understand from this that the w32codecs are open-source and under GPL?

Thanks,
Alex
That's wrong; they're the opposite end: they're just a bunch of closed binary codecs torn apart from Windows apps.

---

### Post by MrHorus on 2006-08-23
> **xp_newbie said:**
> Do I understand from this that the w32codecs are open-source and under GPL?

Hardly - they are closed source, proprietry codecs that are not shared by Microsoft.

---

### Post by Rhubarb on 2006-08-23
If you don't wish to install w32codecs, you could always try out VLC (do a search for 'vlc' in synaptic).
It'll play most of the video formats around, except for wmv.

---

### Post by mr_niceguy on 2006-08-23
If you think about it, only open source software can be known to be spyware free. You could theoretcially write an open source application which was spyware but anyone can look through your code and it would be found out.

So the point where you are most susceptible to spyware on Linux is when you start installing closed source software on it.

---

### Post by az on 2006-08-23
> **23meg said:**
>  no well regarded repository contains malware.


I wouldn't say that.

You have to look at the big picture:  What apps are in that repo and why are they not in the Ubuntu repos?  If it is because they are binary-only apps, then you are not so safe.

If they are backported or newer versions of some apps, which are offered along with source packages, you probably are a bit safer.  If they are apps that are not packaged for Ubuntu, but licenced in a GPL-compatible way (and hence can be part of the Ubuntu archive), you have to wonder why they (the owners of the third-party repo) are not packaging them for MOTU.

As for the keys, a GPG key only does one thing - it proves that I am me.

It is very hard to forge a GPG key.  If I compile a package and sign it with my key, anyone who has access to my key signature can be sure that the package they just got via email or downloaded from somewhere is in fact the same one I compiled.

PLF offers their key sigs.  Import them into you package manager settings and you will no longer get that warning.  

Does that mean that the packages are safe?  No.  But it does ensure (more or less without a doubt) that those packages were built by the people who's keys you have.  If you trust those people, the key provides you with the security of knowing they are themselves.  It provides authentification.

---

### Post by xp_newbie on 2006-08-24
OK - so both **[COLOR="Navy"]23meg[/COLOR]** and **[COLOR="Navy"]MrHorus[/COLOR]** said that the w32codecs, coming from FLP, are:

> they're just a bunch of closed binary codecs torn apart from Windows appsand 
> Hardly - they are closed source, proprietry codecs that are not shared by Microsoft.
While I understood from **[COLOR="Navy"]azz[/COLOR]** that because it is closed source, this w32codecs package can be trusted not to contain malware (if downloaded directly from PLF and signed properly by their GPG key) **only if I trust the PLF**.

So, my question is: Should I trust the FLP? If so, **why**? (after all, they did not release the source code for this package)

Thanks,
Alex

---

### Post by az on 2006-08-24
> **xp_newbie said:**
> 
So, my question is: Should I trust the FLP? If so, **why**? (after all, they did not release the source code for this package)

Thanks,
Alex

They cannot release the source code since there is no source code available.  These are the windows codecs, copied from a windows machine.

I think a few million people use the PLF repositories, so they are regarded as safe.  If they wanted to distribute malware, it probably wouldn't take too long before someone noticed.

Now is there is malware embedded in the binary-only codecs from windows? Will there never be?

---

### Post by xp_newbie on 2006-08-27
> **azz said:**
> These are the windows codecs, **copied from a windows machine**.

Is this legal? :confused: 

If not, how come Microsoft doesn't go after the "writers" of that package or owners of that web site?

Thanks,
Alex

---

### Post by Nonno Bassotto on 2006-08-27
> **xp_newbie said:**
> Is this legal?
AFAIK it depends on the country you live in. By the way, this is why these codecs are not provided by Canonical repositories (not because they're closed source, in fact part of Ubuntu official repos are for closed source apps). If you live in USA, probably this is not legal. The rule of thumb is: if it is illegal somewhere, then it is illegal in the USA.

For what concerns security: are you just making a theorical discussion or are you really afraid to install these codecs? In the second case, you really don't have to worry. An enormous number of people have used PLF repos (both on Mandriva and Ubuntu) without a problem. Unless they have an evil plan to be trustworthy for years, just to gain people's trust, and then start sending spyware to laugh at everyone who uses their repository, you can use it safely.

---

### Post by az on 2006-08-27
> **xp_newbie said:**
> Is this legal? :confused: 


You would have to read the licencing agreement for each and every one of the codecs that are included in the package.  There are no distribution or redistribution licence by the software vendors for linux for these.

If they are distriuted with/in windows and specifically state that it is for use only with a windows-based OS, it's illegal to use them in Linux.  If they don't say anything like that, I dunno.

---

### Post by skymt on 2006-08-28
I have w32codecs installed. I have libdvdcss installed. I play videos and DVDs (that I have legal rights to play) under Linux. I live in the United States. Therefore, I am a criminal. Isn't freedom wonderful?

EDIT: Now I'm depressed. I'm moving to Canada.

---

### Post by az on 2006-08-28
> **skymt said:**
> 
EDIT: Now I'm depressed. I'm moving to Canada.

Moving to Canada is a good way to get happy.  I don't plan on ever leaving Canada.

You have not seen beautiful women until you have gone to a shopping mall in Montreal.

---

