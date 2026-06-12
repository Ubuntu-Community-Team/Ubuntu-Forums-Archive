---
title: "Snap packages and Security."
date: 2016-05-06
forum: Security
---

### Post by poorguy on 2016-05-06
Howdy,

I'm trying to understand this about Snap packages and the security but just don't seem to be getting a grip about it.
Is Snap packages available for all versions of Ubuntu 16.04 based spin offs. (Ubuntu Mate 16.04) 32 bit and 64 bit.
Are Snap packages really needed for security and if not installed does that mean that my Ubuntu Mate 16.04 isn't secure.
Seems all I'm able to find on it is rather vague and doesn't really say yes they are needed no they aren't needed.
Where are they downloaded and installed from as I haven't been able to find them anywhere in my Ubuntu Mate 16.04 distro.
Don't find anything to do with them in the software boutique.

Confused.

Thanks

---

### Post by howefield on 2016-05-06
> **poorguy said:**
> I'm trying to understand this about Snap packages and the security but just don't seem to be getting a grip about it.
Is Snap packages available for all versions of Ubuntu 16.04 based spin offs. (Ubuntu Mate 16.04) 32 bit and 64 bit.
Are Snap packages really needed for security and if not installed does that mean that my Ubuntu Mate 16.04 isn't secure.
Seems all I'm able to find on it is rather vague and doesn't really say yes they are needed no they aren't needed.
Where are they downloaded and installed from as I haven't been able to find them anywhere in my Ubuntu Mate 16.04 distro.
Don't find anything to do with them in the software boutique.

No, snaps don't really have any relation to the security of your system, snaps are just a new way of packaging software just as you would install a deb package currently. Perhaps you could clarify what you mean by "secure" - what security issue are you referring to ?

If you open a terminal and use the command

```
snap find
```

you'll get a list of the snap packages available to download and install.

Ubuntu Software can search for and install snaps but not sure if the Software Boutique can also, try a search for ubuntu-clock-app.

The snap is downloaded to /var/lib/snapd/snaps (deb packages would typically be /var/cache/apt) and installed from there.

---

### Post by poorguy on 2016-05-06
Hey howefield,

Ok so snap packages don't have anything to do with Ubuntu security.
So then it is nothing that is needed.
I still don't understand what they are but at this point I'm to confused.

All I do is web search and stream videos and email so I don't download any software from repositories or software boutique as it isn't needed for what I do. 
Enable the firewall and I'm good.
Bottom line what I do on a computer I do from Live DVD session.

Ok well It doesn't sound like I am going to need snap packages so I am not going to wonder about them.

Thanks howefield.

---

### Post by poorguy on 2016-05-06
Here is an example of what I am always seeing about snap packages and security.

[http://ubuntuforums.org/showthread.php?t=2323541](http://ubuntuforums.org/showthread.php?t=2323541)

**Re: ubuntu or linux mint?**[INDENT]                     You want to know if Ubuntu is more secure than Linux Mint?

I do not know what answer you are happy with but I will tell you this.  Unless the Linux Mint developers replace the X server with_ Mir and make  it possible for users to_ _install snap packaged applications,_ then in a  couple of years time Linux Mint will definitely _be less secure than  Ubuntu_.                 


This is only one example but I see this stuff posted about snap packages and security everywhere and it just confuses the hell out of me.

Maybe it is just me that is confusing me but what I'm reading here I interpret as to do with security in Ubuntu.
[/INDENT]

---

### Post by ZoiaGuyver on 2016-05-06
The "Snap" packages are being used in the wrong context there. 

You can think of Snap like a .deb file we have now, but the Snap is basically "self contained" where as the .deb has to pull additional stuff in. If you are familiar with other operating systems Snaps act a little like .dmg files on macs.

Snap is no more secure or less secure than anything else on the system from a "User" standpoint. They are better constructed and more "Secure" from a developer aspect and will be better for User security once Mir/Wayland are the default display managers i.e programs outside of the Snap itself will not be allowed access to change or "inject" stuff.

A lot of the security issues at the moment are due to the way Xorg works as a display manager. The problem is X can't tell who or what wants access and whether it should be allowed or not. So it basically allows everything as it has had to do for years to get around other issues. 

The major thing is people are taking it that "Snappy Packages" are advertised as more secure then they are picking it apart. Although imo half of that is what the people writing the articles want to hear and not what was said. 

One answer is Snappy is no more or less secure than the debs we use now (its a different approach to installing programs and offers a crap ton of advantages i.e being able to seamlessly roll back to older versions of a program if the need arise) but with the future being Mir and Wayland it has the prospect of becoming much more secure than anything we have now.

---

### Post by mc4man on 2016-05-06
Just my opinion but the so-called 'security' of snap packages is only  needed when providing apps without their source code & relatively  trivial checking before publishing. 
Can't quite remember the last time official repo .debs were found to contain malicious code nor in any ppa I've used or looked at.

---

### Post by poorguy on 2016-05-06
Hey ZoiaGuyver,

Ok this is actually starting to make some sense to me.

Snap packages are complete software packages with everything needed all in one package. 

A different way of doing software downloads.

You have cleared a lot of confusion as to what the snap packages are and how the term secure is being used / misused.

Alright I still have some brain cells left.

Ok I really appreciate all of your help with this.

Thanks ZoiaGuyver

---

### Post by cogset on 2016-05-09
> **ZoiaGuyver said:**
> The "Snap" packages are being used in the wrong context there.   You can think of Snap like a .deb file we have now, but the Snap is basically "self contained" where as the .deb has to pull additional stuff in. If you are familiar with other operating systems Snaps act a little like .dmg files on macs.   But because they won' t have to interface correctly with system libraries any more as they will provide their own, won't this eventually make it easier to use malicious ones bundled with the app itself?

---

### Post by ZoiaGuyver on 2016-05-09
@cogset Well they are still pgp signed like the repos we have now. They will still have package maintainers (afaik) and the files that are linked to the app are listed in a yaml file. 

In theory I guess someone could put something malicious in there, but then it come downs to how likely that is with all the people looking at the code, plus having to use a pretty traceable way of getting the malicious content onto someone's system (pgp signing and the repo which it came from which is normally linked to a launchpad account/website). Being as we don't really suffer with that at the moment I can't see it being a big problem (although don't quote me on that lol). 

There will always be security risks that as a community we can't exactly "beat" as such, but we can lower the effect so much as it becomes pretty much useless for anyone to even try bothering.

Snappy just has a lot of advantages over the current formats. Self contained, Sandboxed and being able to Roll back to whichever version to state a few. That's just my opinion, I know some of the more security concious users will pick fault with it, but then I expect they are running something like Tomoyo or other kernel level protection (Selinux, Apparmor) that uses MAC and if they aren't then they aren't exactly that hung up about security.

---

### Post by ubu_dynamite on 2016-05-09
Just wondering how the dependencies will be maintained in snap what if there is a security bug in one of the dependencies all of the snap packages that will use that same buggy dependency will have to be update instead of just one package.

---

### Post by ZoiaGuyver on 2016-05-09
If I remember right from what I had read the Snaps are transactional (so they could have a patch added to them by the developer) also there was meant to be a "staging area" where most of the dependencies could be linked to and built. My guess would be that if there was a security fix that it would only have to be pushed to the Staging Area and from there any package requiring the fix would get it.

---

