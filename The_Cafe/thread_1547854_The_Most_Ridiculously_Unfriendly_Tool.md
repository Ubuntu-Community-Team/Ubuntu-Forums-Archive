---
title: "The Most Ridiculously Unfriendly Tool"
date: 2010-08-07
forum: The Cafe
---

### Post by nrs on 2010-08-07
What is the most ridiculously unfriendly tool you've come across in an operating system? 

For my own part, I nominate our very own 'tc', part of iproute2. This application makes me wish I was using FreeBSD w/ ipfw. Unfortunately using FreeBSD makes me wish I was using a GNU system.

---

### Post by cascade9 on 2010-08-07
Windows Registry Editor. 

Thats the nastiest, least user friendly 'tool' I've ever come across.

---

### Post by devondashla on 2010-08-07
> **cascade9 said:**
> Windows Registry Editor. 

Thats the nastiest, least user friendly 'tool' I've ever come across.

It's not supposed to be used by the average end-user, so if you're smart enough to edit the registry, you should be smart enough to figure it out.

---

### Post by phrostbyte on 2010-08-07
[malbolge]("apt:malbolge") :D

---

### Post by betrunkenaffe on 2010-08-07
> **devondashla said:**
> It's not supposed to be used by the average end-user, so if you're smart enough to edit the registry, you should be smart enough to figure it out.

That wasn't the question. Since the thread could be renamed "What is the most ridiculously unfriendly tool in your opinion which can't be refuted because it's how you feel and not based on reality in any way"

I'd say some of the tools we have at work are worse than anything in public sector.

---

### Post by mendhak on 2010-08-07
> **nrs said:**
> What is the most ridiculously unfriendly tool you've come across in an operating system? 

For my own part, I nominate our very own 'tc', part of iproute2. This application makes me wish I was using FreeBSD w/ ipfw. Unfortunately using FreeBSD makes me wish I was using a GNU system.
You don't know what ridiculously unfriendly is until you've used Visual Source Safe.

---

### Post by giddyup306 on 2010-08-07
Any of the software uninstallers in Ubuntu.  They almost never completely delete a program.

---

### Post by praveenthivari on 2010-08-07
kpackage kit:-)

---

### Post by Simian Man on 2010-08-07
ddd is pretty awful.  It has a ton of powerful features, and I use it almost every day, but God the interface is so bad I want to gouge my eyes out.

---

### Post by Lucradia on 2010-08-07
> **devondashla said:**
> It's not supposed to be used by the average end-user, so if you're smart enough to edit the registry, you should be smart enough to figure it out.

neither is that fancy GNOME Settings Editor thing, which acts like Windows Registry Editor, but is a lot more user-friendly.

---

### Post by mobilediesel on 2010-08-07
AptURL
Maybe not unfriendly but an idiotic piece of software.

---

### Post by NCLI on 2010-08-07
> **mobilediesel said:**
> AptURL
Maybe not unfriendly but an idiotic piece of software.

Why?

---

### Post by Simian Man on 2010-08-07
> **NCLI said:**
> Why?

I'm not going to put words in mobilediesel's mouth, but I personally don't use Ubuntu and I can't stand clicking on a link that seems like it should go to a project's home page and having it be an apturl instead.  "Firefox doesn't know what to do with protocol apt://".  Ughh.

---

### Post by Xianath on 2010-08-07
Norton Commander and any of its minions (TC, MC, Kommander etc)
GIMP (nuff said)
vi (I myself like it, but I've seen people ctrl-alt-del to quit it)

tc on the other hand is quite straightforward provided you know what you're doing. It's that last part that ranks really high.

---

### Post by mobilediesel on 2010-08-07
> **NCLI said:**
> Why?

> **Simian Man said:**
> I'm not going to put words in mobilediesel's mouth, but I personally don't use Ubuntu and I can't stand clicking on a link that seems like it should go to a project's home page and having it be an apturl instead.  "Firefox doesn't know what to do with protocol apt://".  Ughh.

Partly what Simian Man said. Partly that it is a tool that can be used for social engineering.

Someone pretending to help can have someone install an innocent program. Once the superuser password has been entered he can say "Now run this script" and whatever it is will have superuser access without asking for a password. Yes, the same thing can be done by having someone copy-paste the apt-get command but just clicking something makes things seem more innocent.

---

### Post by Sporkman on 2010-08-07
Testdisk.

---

### Post by nrs on 2010-08-07
> **Xianath said:**
> 
tc on the other hand is quite straightforward provided you know what you're doing. It's that last part that ranks really high.
Are we speaking of the 'tc'? I think IPFW / Dummynet is an example of things done right.

---

### Post by chriswyatt on 2010-08-07
> **cascade9 said:**
> Windows Registry Editor. 

Thats the nastiest, least user friendly 'tool' I've ever come across.

Really?  You have keys, keys contain values.  You click on a key, it opens up to show you more keys, you click on a value and you can edit it, how can it be any simpler than that?  For the job it needs to do which is edit the registry it does it well.

---

### Post by eriktheblu on 2010-08-07
It might be Active Directory (if we are just talking OS functions)

If we include all software, QWS3270 or Delrina FormFlow. Whatever software ran our UCOFT simulators wasn't all that fun either.

---

### Post by JustinR on 2010-08-07
> **Xianath said:**
> 
GIMP (nuff said)
 
What? GIMP is very easy to use.

---

### Post by red_Marvin on 2010-08-07
> **mobilediesel said:**
> Partly what Simian Man said. Partly that it is a tool that can be used for social engineering.

Someone pretending to help can have someone install an innocent program. Once the superuser password has been entered he can say "Now run this script" and whatever it is will have superuser access without asking for a password. Yes, the same thing can be done by having someone copy-paste the apt-get command but just clicking something makes things seem more innocent.

Correct me if I'm wrong but isn't apt url's still confined to what's in the repositories listed in /etc/apt/sources.list? -- so an apt://foo link is no more (or less) prone to social engineering than a line saying 'run apt-get install foo'.

Back to the topic though: Sometimes there are programs where I feel that I would need a manual for the manual for the program. It is usually a sign that I need to read up on the subject the program is *about* before attempting to use any program of the kind (e.g. firewall).

---

### Post by SoFl W on 2010-08-07
A boss I had several years ago was a ridiculously unfriendly tool.

---

### Post by mobilediesel on 2010-08-07
> **red_Marvin said:**
> Correct me if I'm wrong but isn't apt url's still confined to what's in the repositories listed in /etc/apt/sources.list? -- so an apt://foo link is no more (or less) prone to social engineering than a line saying 'run apt-get install foo'.

As I mentioned, that would be just to get someone to type their superuser password. Then have them download a short script that can now have access to the whole system without further requests for the password. The reason I say apt://whatever could be more prone to social engineering is that someone new to Linux might think that click was part of their OS and not a program installation.

---

### Post by Sporkman on 2010-08-07
> **SoFl W said:**
> A boss I had several years ago was a ridiculously unfriendly tool.

:lol:

---

### Post by Xianath on 2010-08-08
> **JustinR said:**
> What? GIMP is very easy to use.

Its interface has a fundamental design flaw that, ironically, its authors seem quite proud of. Not unlike *commander. When my taskbar area is dominated by two dozen GIMP windows, I can't help but question the sanity of the decision not to use a parent window, and the veracity with which they defend it. I try to use it at least once a year to see if they've made any progress in almost fifteen years but alas, they haven't. Apparently it's more important to defend some stupid principle than give users what they've been screaming about for over a decade. Oh well, like I haven't seen that one before.

---

### Post by Naiki Muliaina on 2010-08-08
Private sector software and the reason I ended up the admin for my bosses company and 3 of his mates company's.

[**http://www.ramdis.org/**]("http://www.ramdis.org/")

It sucks... Royally... Vile company with vile employees with extortionate prices.... Hate them, the company, and the utterly rubbish unusable software...

---

### Post by neoargon on 2010-08-08
> **praveenthivari said:**
> kpackage kit:-)

I vote for this ^^

But for the god's sake we will be having "muon" in 11.04

---

### Post by Ebuntor on 2010-08-08
TOPDesk, it's an app to register IT support calls and was made by the Dutch IT company I work for. It is probably the most illogical piece of software I have ever worked with. It just like the developers intentionally tried to hide certain features. The most used options are always buried in some sub-sub-sub menu and the descriptions are so vague I'm afraid to click on anything.

The worst part is that it is very popular among Dutch IT departments (for some unexplainable reason) so anywhere I go I have to work with it.

---

### Post by neoargon on 2010-08-08
> **Sporkman said:**
> Testdisk.

Very useful but a bit difficult to figure it out for the first time .

---

### Post by johnb820 on 2010-08-08
GRUB

Nothing is more unfriendly than "grub error *random number*." That's wonderful if you know what specific error it is but if you couldn't look it up you would be up a creek without a paddle.

---

### Post by Frogs Hair on 2010-08-08
Software that I don't know how to use and can't find good instructions for .

---

### Post by Zorgoth on 2010-08-08
vi :P

---

### Post by Spice Weasel on 2010-08-08
> **Zorgoth said:**
> vi :P

This, heh. I've been using Nano for years and don't plan to stop. :p

---

