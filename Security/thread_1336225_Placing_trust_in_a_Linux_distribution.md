---
title: "Placing trust in a Linux distribution"
date: 2009-11-24
forum: Security
---

### Post by securefire on 2009-11-24
This is something that I've been wondering for a while and have not found an answer yet.  
 

 How do we know that we can trust a specific Linux distribution?  “Trust” being defined as trusting that the software bundled with the base Linux system, or included within the repositories of that distribution, is free of backdoors, spyware, or anything else undesirable?  If the repositories are all open source, I suppose that somebody with enough programming know-how could examine the code to confirm that something is legitimate before installing it, but for something like Ubuntu where the repositories are all compiled binaries, how does one trust this software?
 

 Take the following example:  Lets say while browsing the web I hear about a new Linux distribution and I want to install it.  How do I confirm that this Linux distribution is safe to install and isn't the product of a group who wishes to spy on you?  Typically, I'll try to see who else uses or recommends it, and if I trust those people I therefore trust (perhaps hesitantly) that distribution.  But is there a better way than this?

Likewise, in Ubuntu, when I'm looking to add new software to my computer through  Synaptic, how do I know that I can trust what's included in those packages?  For example, is there a way to check the validity of sleuthkit in the Ubuntu repositories?
 

 I think a lot of people believe that if in fact something malicious is added to some software, that eventually (hopefully quickly) somebody will discover an anomaly with their system (ex: while messing around with tcpdump he/she notices his/her computer is establishing connections to random IP addresses) and report it on a forum where other users perhaps more knowledgeable in programming will eventually discover the root cause.  But is this realistic?  And for things that are complex (ex: cryptography) how long could it take before something like this is discovered?  For example, how many people can honestly say that they could read through and understand every line of code and logic for TrueCrypt?   And how many people (excluding government agencies) actually bother doing this?

---

### Post by lykwydchykyn on 2009-11-24
You can never really know what's going on, but when it comes to open source software you can take comfort in a few facts:

 - Ubuntu has source repositories, as does Debian and most other major distros.  You can very easily compile anything you want from source, check out apt-src for example.

 - Any major distro is going to get a lot of third-party scrutiny.  There are organizations like CERT that publish vulnerabilities and other flaws they find within code.

 - The stakes are high; if a major distro was found to contain malicious code, it'd be over for that project.  Could even result in civil or criminal prosecution.  And with the code open, I have to believe that the truth would come out pretty quick.  Even if the problem was only in the binary, it'd probably be obvious when the compiled version didn't match the binary.

---

### Post by tubbygweilo on 2009-11-24
securefire,
Put the name of the distribution into your favoured search engine (plus a few others) and see what a hundred entries say about it. Gather the views of others, have a think then take an action - crowd sourcing at its very best?

---

### Post by benj1 on 2009-11-24
how can we trust that closed source OSs and programs are free of malware, backdoors, etc

i know who i would trust, and even if i didn't i at least have the option of reviewing code and compiling myself

---

### Post by OpSecShellshock on 2009-11-24
I think it makes more sense to think of it in terms of managing risk than "trust." It's reasonable to consider, for example, that software that is available in the official repositories has been packaged specifically for a given distro by people who have worked on the distro itself. Risk increases when you go outside the repositories, but I'd argue not by very much. A strong user community (such as this one) provides decent vetting for third-party code.

Also, it's important to consider what kinds of activities you use your computer for, and realize that risk assessment and management have more to do with that than with the trustworthiness of the distribution. Here are some examples (long-ish post ahead):

1. Physical access is the highest risk category. Granted, it's also one of the easiest to manage (for most home users all they have to do is lock the door).

2. Anything of value to data thieves that can be done through the relatively difficult (on Linux) process of getting a rootkit/backdoor installed can be done more easily and anonymously within the context of a browser session. Data theft techniques don't have to be particularly good; they just have to be good *enough*.

3. Licensed/proprietary operating systems and software quite frequently tell you right in the EULA that they will be connecting to a verification server, trying to automatically update, gathering personal information for registration purposes, and selling "anonymized" user data to third parties (beyond which point they wash their hands of it, and you don't know what they have, how much, how it's being used, and where it's going after that). Given that, it's not likely that FOSS would present any increased risk.

---

### Post by securefire on 2009-11-24
I was not familiar with apt-src.  Thank you, I'll look into that.  And thank everybody else for your input.  I appreciate your opinion on this topic.  I do agree that it is a question of accepting risk versus placing blind trust.

 Is anybody here familiar with the approval process before a given program is added to the repositories?  I'll give you an example.  If you subscribe to the SecurityFocus pen test mailing list, you will notice frequent e-mails of somebody announcing either a new or updated tool that they created for vulnerability assessment or penetration testing.  Now, if this is a brand new tool that I haven't heard of before, or I don't know the person/organization who created the tool, I won't blindly install it.  However, after a while some of these tools do eventually make their way into official repositories.  What I'm curious about is who at what point decides that this program is "trusted enough" to be included in an official repository?  Is there an approval process or examination before something new gets added?

---

### Post by cariboo on 2009-11-24
Have a look at [this]("https://wiki.ubuntu.com/UbuntuDevelopers") page. It has the steps needed to become an Ubuntu developer, which allows you to then submit packages for consideration to be placed in the repositories.

---

### Post by __p1n__ on 2009-11-24
Trust no one.  Build your own kernel from source.  Add only foss projects that you need and have code reviewed (and have built yourself.)

Actually you'll probably have to trust the GNU compiler.  Perhaps you have a compiler that you trust already and can build the GNU compiler from that.  Bootstrap-type dependency problems like this are always interesting.

---

### Post by falconindy on 2009-11-24
I don't trust installation software or compilers. Nothing but fancy jargon for "spyware". I use a pair of magnetic needles and a steady hand to install my software.

---

### Post by rookcifer on 2009-11-24
> **securefire said:**
> This is something that I've been wondering for a while and have not found an answer yet.  
 

 How do we know that we can trust a specific Linux distribution?  “Trust” being defined as trusting that the software bundled with the base Linux system, or included within the repositories of that distribution, is free of backdoors, spyware, or anything else undesirable?  If the repositories are all open source, I suppose that somebody with enough programming know-how could examine the code to confirm that something is legitimate before installing it, but for something like Ubuntu where the repositories are all compiled binaries, how does one trust this software?

How does one trust M$ Windows?  How does one trust the software bundled with OSX?  How does one trust the microcode on the Athlon or Core2Duo CPUs?  The fact of the matter is we have to have trust in software at some point down the line.  If you need 100% security, go work for the NSA and use their top-secret, formally verified computer systems.
 

> Likewise, in Ubuntu, when I'm looking to add new software to my computer through  Synaptic, how do I know that I can trust what's included in those packages?  For example, is there a way to check the validity of sleuthkit in the Ubuntu repositories?

You can trust it by the fact that probably thousands or millions of people have also installed the software and someone somewhere would have discovered already that the software is a bit suspicious.
 

>  I think a lot of people believe that if in fact something malicious is added to some software, that eventually (hopefully quickly) somebody will discover an anomaly with their system (ex: while messing around with tcpdump he/she notices his/her computer is establishing connections to random IP addresses) and report it on a forum where other users perhaps more knowledgeable in programming will eventually discover the root cause.  But is this realistic?  

Yes, it's realistic.  Look at the famous Sony rootkit or all the spying past versions of Windows has done.  These are closed-source and people still discover suspicious activity.  There is always some geek somewhere who will be a step ahead of you.

> And for things that are complex (ex: cryptography) how long could it take before something like this is discovered?  For example, how many people can honestly say that they could read through and understand every line of code and logic for TrueCrypt?   And how many people (excluding government agencies) actually bother doing this?

You can look at the news and surmise that popular encryption software is not crackable by the authorities.  There are stories all over the web about Police in various countries trying to force suspects to give up their encryption keys.  Obviously they cannot crack it otherwise.

---

### Post by necromonger on 2009-11-24
All you have to do is look at windows history it speaks for it's self.That is 1 reason open source came along having said that no os is 100% secure.We all have to do our jobs and keep up with the latest security updates.And don't do any thing stupid.

---

### Post by benj1 on 2009-11-24
> **__p1n__ said:**
> Trust no one.  Build your own kernel from source.  Add only foss projects that you need and have code reviewed (and have built yourself.)

Actually you'll probably have to trust the GNU compiler.  Perhaps you have a compiler that you trust already and can build the GNU compiler from that.  Bootstrap-type dependency problems like this are always interesting.

reminds me of [this]("http://www.science.uva.nl/~mes/jargon/b/backdoor.html")

---

