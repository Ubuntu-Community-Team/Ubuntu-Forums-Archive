---
title: "Linux Trojan Goes Unnoticed for A Year (Unreal IRCd)"
date: 2010-06-13
forum: The Cafe
---

### Post by MCVenom on 2010-06-13
Apparently the Linux version of a popular IRC server has been found to potentially contain malware. No one had noticed this until now, but it's said that the download had been compromised since November 2009.

> An announcement on the [Unreal IRCd  Forums]("http://forums.unrealircd.com/viewtopic.php?t=6562") states "This is very embarrassing...We found out that the  Unreal3.2.8.1.tar.gz file on our mirrors has been replaced quite a while  ago with a version with a backdoor (trojan) in it. This backdoor allows  a person to execute ANY command with the privileges of he user running  the ircd. The backdoor can be executed regardless of any user  restrictions (so even if you have passworded server or hub that doesn't  allow any users in)."                       The post goes on to say "It appears the replacement of the .tar.gz  occurred in November 2009 (at least on some mirrors). It seems nobody  noticed it until now."
From PCWorld's article [here]("http://www.pcworld.com/businesscenter/article/198686/linux_trojan_raises_malware_concerns.html"); please note though that they do *not* seem to have done their research, as the compromised application in question doesn't seem to be related at all to the Unreal Tournament game, as they claim it is.

What do you all think about this? Is it only a matter of time before we see more attacks like this?

---

### Post by spoons on 2010-06-13
It proves that no matter how bulletproof or not an operating system is, the real security threat is the carbon-based bag of mostly-water using it.

---

### Post by Bachstelze on 2010-06-13
Stuff happens... The real question would be *how* it got replaced.

---

### Post by undecim on 2010-06-13
Their servers got compromized and they never noticed, for two reasons:

1: They never did periodic MD5 checks.

2: They never signed the files with GPG.

This is why Ubuntu has keyrings. No one can modify the file except someone with Ubuntu's private key, which is well guarded (or so I assume). In other words, this is the result of bad management of the download servers.

---

### Post by MCVenom on 2010-06-13
I just sent an email to the writer of the artice informing him the Unreal IRCd is not Unreal Tournament. I wonder if he'll retract the statement:
> Unreal is a popular first-person shooter game--similar to Doom or Quake.  I don't have any numbers on the total downloads since November of 2009,  but it seems safe to assume there are a lot of Linux systems out there  compromised by a backdoor Trojan.
:roll:

---

### Post by jrusso2 on 2010-06-13
What happened to these "thousands of eyes pouring over the code" we hear about so often?

---

### Post by Frogs Hair on 2010-06-13
I don't use unreal ,  but I am wondering what the next step should be for users with possibly  affected systems ?

---

### Post by undecim on 2010-06-13
> **jrusso2 said:**
> What happened to these "thousands of eyes pouring over the code" we hear about so often?

They looked over the code before it was compromised. The code was perfectly clean when it was first uploaded. It was afterwards that it was changed to be malicious.

---

### Post by MCVenom on 2010-06-13
> **undecim said:**
> They looked over the code before it was compromised. The code was perfectly clean when it was first uploaded. It was afterwards that it was changed to be malicious.
Also as was mentioned, there were no hash checks on the files, nor were they signed; so that ignorance comes into play also.

---

### Post by undecim on 2010-06-13
> **Frogs Hair said:**
> I don't use unreal ,  but I am wondering what the next step should be for users with possibly  affected systems ?

Well, if they still had the archive they downloaded, check the MD5. It it's one of the compromised files, it will have a bad MD5. 

If it is compromised, probably removing the affected binaries would be enough, unless the backdoor is more advanced. A diff of the source code from the affected and unaffected sources of the same version would reveal the code used in the backdoor and someone can determine what other actions might need to be taken.

---

### Post by jrusso2 on 2010-06-13
I am thinking all these eyes watching the code is a myth.

---

### Post by kittykis on 2010-06-13
Oy. 

People saying that Linux obviously isn't secure because of this sort of thing make my head hurt. For one, this is an attack on _servers_, not desktop users. Servers running Unreal. 

For two, this isn't really comparable to Windows malware...it doesn't propagate, it's not the sort of thing an AV looks for. The eyes are watching the code when it is uploaded, and it is regretful that the Unreal developers did not manage their mirrors better. But that is it. It is _not_ a weakness in Linux; it is a human flaw, a security oversight. It is a lesson from which they will have most definitely learned. Malicious actions can be performed on any system. We've known this for ages, because when you have full access to a system, yes, you can do harm.

The only real shock to me is that such a big (in my mind; I've been on networks running Unreal for ages, and even ran it myself for a small home-project for a while) project was affected. Again, it is hard to equate to a situation on Windows...but it is simple to say that it is the responsibility of the maintainers to regularly ensure that their software is safe and that no one has tampered with the repositories. The eyes do watch the code -- the code *being developed*. It is also the responsibility of a user -- *especially* one managing a server of this sort! -- to ensure that they do not run unsafe software! If you are downloading software from the web and not a tightly-locked repository, there is always this risk.


Also, Windows systems pretty much weren't affected because A) they have poor server marketshare, particularly chez IRC users, and B) most Windows servers probably use the binaries anyway. Too much trouble to muck with those.

---

### Post by Shining Arcanine on 2010-06-13
> **BlackOtaku said:**
> Apparently the Linux version of a popular IRC server has been found to potentially contain malware. No one had noticed this until now, but it's said that the download had been compromised since November 2009.

From PCWorld's article [here]("http://www.pcworld.com/businesscenter/article/198686/linux_trojan_raises_malware_concerns.html"); please note though that they do *not* seem to have done their research, as the compromised application in question doesn't seem to be related at all to the Unreal Tournament game, as they claim it is.

What do you all think about this? Is it only a matter of time before we see more attacks like this?
It is not a trojan. It is a backdoor that was inserted into the source code. There is a significant difference between the two.

---

### Post by wilee-nilee on 2010-06-13
> **spoons said:**
> It proves that no matter how bulletproof or not an operating system is, the real security threat is the carbon-based bag of mostly-water using it.
:lolflag:

> Stuff happens... The real question would be how it got replaced.
So true.

---

### Post by MCVenom on 2010-06-13
> **Shining Arcanine said:**
> It is not a trojan. It is a backdoor that was inserted into the source code. There is a significant difference between the two.
I was using the term used in the PCWorld article. However, given the ignorance already displayed in the article, I should have known better. :lolflag:

---

### Post by Chronon on 2010-06-13
> **jrusso2 said:**
> I am thinking all these eyes watching the code is a myth.

A tarball got replaced without their knowledge.  Tarballs usually don't get much review after they have been packaged, so I'm not sure what you're getting at here.  This problem could have been prevented by 
a) using digital signatures 
or 
b) downloading source from the project's CVS system instead of using the tarball.

---

### Post by SunnyRabbiera on 2010-06-13
> **jrusso2 said:**
> I am thinking all these eyes watching the code is a myth.

Well try one of those magic eye pictures sometime, thats how reading code sometimes is

---

