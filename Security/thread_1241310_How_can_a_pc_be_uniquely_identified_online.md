---
title: "How can a pc be uniquely identified online?"
date: 2009-08-15
forum: Security
---

### Post by Ulysses_ on 2009-08-15
Is it possible to uniquely identify a pc by running javascript, asp, cgi, perl, or any other scripts?  I am looking for a means of identification other than cookies (these are usually deleted between sessions) or ActiveX (which most people do not trust and disable) or any other unsuitable identification such as IP's (which are usually shared and therefore not unique).  If yes, what are some examples of scripts for unique identification?    Might be useful for detecting clone accounts on this forum too.

---

### Post by hansdown on 2009-08-15
Hi Ulysses_.

I don't have a good answer, so this should hopefully help.

[http://www.google.ca/search?q=How+can+a+pc+be+uniquely+identified+online%3F&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=How+can+a+pc+be+uniquely+identified+online%3F&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by wojox on 2009-08-15
Look into Apache and php.

---

### Post by niteshifter on 2009-08-16
Hi,

At present there isn't a way.

And I hope there never is one. That would be a very dangerous thing to have in the world.

---

### Post by uljanow on 2009-08-16
Well, there's an approach to identify host by their clock skew variations which are send in TCP timestamp fields.



[http://www.cl.cam.ac.uk/~sjm217/](http://www.cl.cam.ac.uk/~sjm217/)

---

### Post by Dr Small on 2009-08-16
> **niteshifter said:**
> Hi,

At present there isn't a way.

And I hope there never is one. That would be a very dangerous thing to have in the world.
Ditto. Being able to unique identify any given system, by whatever means, seems like an invasion of privacy. You could no longer surf the internet anonymously, for that matter.

---

### Post by Ulysses_ on 2009-08-16
> **niteshifter said:**
> Hi,

At present there isn't a way.

And I hope there never is one. That would be a very dangerous thing to have in the world.

 Why would it be dangerous?  The authorities already have other ways of uniquely identifying people by name, simply by asking ISPs and anonymity proxy providers.  What harm is there if everybody can uniquely everybody's pc, but not a person's name?

---

### Post by lswb on 2009-08-16
> **Ulysses_ said:**
> Why would it be dangerous?  The authorities already have other ways of uniquely identifying people by name, simply by asking ISPs and anonymity proxy providers.  What harm is there if everybody can uniquely everybody's pc, but not a person's name?

By that same logic why is there any need for unlisted telephone numbers? Also, it is one thing for "The authorities" to have access to this information, it is another for any random website operator or internet presence to have it.

---

### Post by Ulysses_ on 2009-08-16
> **lswb said:**
> By that same logic why is there any need for unlisted telephone numbers? Also, it is one thing for &quot;The authorities&quot; to have access to this information, it is another for any random website operator or internet presence to have it.

 But you are still mixing computer anonymity with person anonymity: a person's name and postal address is still private if the computer is identified as the one that was trolling in the forum the other day. It's not like listed versus unlisted telephone numbers because these identify people's names and postal addresses.

---

### Post by niteshifter on 2009-08-16
> **uljanow said:**
> Well, there's an approach to identify host by their clock skew variations which are send in TCP timestamp fields.



[http://www.cl.cam.ac.uk/~sjm217/](http://www.cl.cam.ac.uk/~sjm217/)

Easily spoofed. The timestamps, and for that matter your clock are under your control.

---

### Post by niteshifter on 2009-08-16
> **Ulysses_ said:**
> But you are still mixing computer anonymity with person anonymity: a person's name and postal address is still private if the computer is identified as the one that was trolling in the forum the other day. It's not like listed versus unlisted telephone numbers because these identify people's names and postal addresses.

As would a malevolent entity. You're assuming play by the rules, I'm saying there are entities that don't: people, corporations and governments. With the last two well positioned by having the wealth and personnel to mine databases and examine network traffic to tie a machine (or machines) to individuals and organizations.

---

### Post by scorp123 on 2009-08-16
> **Ulysses_ said:**
> Is it possible to uniquely identify a pc by running javascript, asp, cgi, perl, or any other scripts? Interesting question. I am not a programmer so I can't really answer that question directly. But out of curiosity I typed "uniquely identify a computer" into Google and it seems there are plenty of such discussions going on, on JavaScript, PERL and PHP forums ..... I don't really mean to be rude, but it really seems that Googling this might be your best option?

[http://www.google.ch/#hl=en&q=uniquely+identify+a+computer&meta=&aq=0&fp=437dc858a1e6c729](http://www.google.ch/#hl=en&q=uniquely+identify+a+computer&meta=&aq=0&fp=437dc858a1e6c729)

---

### Post by Baneblade on 2009-08-16
MAC address?

---

### Post by Dr Small on 2009-08-16
> **Baneblade said:**
> MAC address?
MAC Addresses can be spoofed as well.

---

### Post by Ulysses_ on 2009-08-17
It appears chase manhattan and the bank of america have found a way to uniquely identify computers:  > "In a nutshell they gather 30 or so pieces of information to identify your machine and compare it to a known list of your 'trusted machines'. This includes things such as browser version, plugin versions, etc. If you've ever used bank of america for you know that the site knows who you are when you login from the same machine and performs additional challenge responses when you try logging in from another one.  (...)  You could grab those checkpoints in a similar fashion to the machineid technologies, and send them off to an ad server over ssl in a query string. If example.com hosts ads from adserver.com, then the code in example.com could fetch adserver.com code to first gather this info, dynamically generate a url and css history theft to see if that unique user has visited the specific adserver.com url. If they had visited it then the user had loaded an ad from adserver.com in the past. At that point additional JS could fire performing a request to adserver.com with the name of the URL being visited or obtain this information via a referer header. Next the user visits cnn.com it also has the same code/src include, generates the same url, css history theft compares then continues doing the same thing. The adserver company now can track without cookies which sites the specific user has visited regardless of browser or IP.&quot;   [http://web.archive.org/web/20080127145309/http://www.cgisecurity.com/2007/04/10](http://web.archive.org/web/20080127145309/http://www.cgisecurity.com/2007/04/10)

---

### Post by Ulysses_ on 2009-08-17
Here's evidence of chase manhattan bank doing something similar:  [http://www.tek-tips.com/viewthread.cfm?qid=1359398&page=4](http://www.tek-tips.com/viewthread.cfm?qid=1359398&page=4)

---

### Post by Ulysses_ on 2009-08-17
**Does anyone know of a good programming forum?**

---

### Post by jeffathehutt on 2009-08-17
> Does anyone know of a good programming forum?

There is a programming section on the ubuntuforums: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

:)

---

### Post by Ulysses_ on 2009-08-18
I want to find implementations of this or similar ideas.  Surely if someone from the programming part of ubuntuforums has seen or developed something like this, they would have told us here.

---

### Post by Rob_H on 2009-08-18
There is no fool-proof mechanism to identify a single computer online. But it's certainly possible to link someone's online activity to a unique IP address, which is almost as effective. This is the approach the RIAA has taken to identify alleged music pirates, for example. There are counter-measures, though. Anonymizing networks like Tor and browser plugins like NoScript can allow you to surf the web anonymously, for example, so that even your ISP can't link you to the activity. There are theoretical attacks against Tor, but I've never heard of one successfully carried out in practice.

---

### Post by bobince on 2009-08-18
There are plenty of advertisers, spammers and other nefarious parties who would love to be able to do such a thing. Luckily, the browser disallows it because, strangely enough, users don't actually want to be uniquely identified to every page they look at.

The bank's solution in the article you pointed to does not uniquely identify anything: it gets assorted information points available from a browser, and checks that against the last few times you accessed the site. If they happen to be the same, it guesses that you're from the same machine, and might be a little less challenging on the login process. But the amount of information you can get from a browser is limited (things a script might need to know, like browser version, plugins, screen size...); it works fine as a backup to a proper user-account system that explicitly asks a user to identify themselves, but as an identification mechanism on its own it would be worse than useless.

The Windows Media Player plugin on IE used to have a unique ID you could read, but this is typically disabled these days (because, guess what, users hated it). You might be able to find another similarly lame plugin to exploit, maybe. There's always Flash, which allows ‘local storage’. This behaves in the same way as cookies, except the controls to disallow it are more well-hidden and less-configurable than cookies, so more people have it left on.

Many advertisers are abusing this feature already. You can join them, but it's pretty unpleasant and far from reliable.

---

### Post by Tamalin on 2009-08-18
You would be able to obtain a relative geographic location, at least partially accurately, from the ip address, which can be obtained through easily through just a few lines of PHP code.  If a person had a static IP address for their network, you would be able to indentify that network anytime that IP address was used.  However, this is **not** always an accurate solution to any problem.

---

### Post by cariboo on 2009-08-19
+1 for lack of accuracy. I quite often see that I'm located in Red Deer Alberta, which is depending on what highway you take 650km or 710km from where I actually am.

---

### Post by Ulysses_ on 2009-08-19
> **bobince said:**
> There's always Flash, which allows ‘local storage’. This behaves in the same way as cookies, except the controls to disallow it are more well-hidden and less-configurable than cookies, so more people have it left on.

Many advertisers are abusing this feature already. You can join them, but it's pretty unpleasant and far from reliable.When we POST on a forum, we do not mind the forum knowing we were there before, we are openly saying we are the same person.  While reading the forum can still be anonymous, with IPs seen by the admin being just a clue and not proof of identity.  

Flash local storage can be used only when you log on, to check that your computer has not been previously banned, and not for cross-site tracking.  So the admin would have their consciousness clear.  And trolls would be unable to get back in.    

How do I find out about flash local storage?

---

### Post by bobince on 2009-08-20
> **Ulysses_ said:**
> How do I find out about flash local storage?

[Try this tutorial](http://www.permadi.com/tutorial/flashSharedObject/index.html).

---

### Post by Tamalin on 2009-08-20
> **cariboo907 said:**
> +1 for lack of accuracy. I quite often see that I'm located in Red Deer Alberta, which is depending on what highway you take 650km or 710km from where I actually am.

When I said at least partially accurate, I meant that it would sometimes work at least relatively close, and sometimes not close in any way.  For me, sometimes I get a location near me, and I have in past instances gotten a location on a separate continent (don't ask me why, I think the software is messed up.).

---

### Post by joelgsf on 2009-08-24
I can tell you that the bank I have my account in Brazil (Banco do Brasil - [http://www.bb.com.br]("http://www.bb.com.br")), with full access over the Internet, for any kind of transaction, uses some script which collects information from the system (mainly from the OS and motherboard, I presume) and generates some kind of hashing for comparing with a value computed when you register your computer for such use. Besides the usual login procedures, you can only have access to services if you are using a registered machine. I don't know the details but, at large, this is what is done. I think that this is a good use of such a scheme as anyone from another machine cannot access my account, even if he/she gets to know my credentials.

---

### Post by Tclarkie on 2009-08-25
there would be ways, by the mac address
apps like umit can find them on local networks, so they'd be out there for the internet

---

### Post by running_rabbit07 on 2009-08-25
Being able to be tracked could be a good thing or bad. To be able to make a 911 call via the net would be great if they knew where you were. Getting into a flame war then having someone realize you are a neighbor and knocking on your door would be a bad thing. Having your daughter start a facebook account and someone tracking her down with an IP, very bad.

Honestly though, unless your are doing something really illegal, there shouldn't be much to worry about. Especially with firewalled routers, there isn't much worry about cyber attacks.

---

### Post by lisati on 2009-08-25
> **Tclarkie said:**
> there would be ways, by the mac address
apps like umit can find them on local networks, so they'd be out there for the internet

Even using mac addresses has its limits - in some situations they can be spoofed. I don't know how and don't want to, but could probably find out.

---

### Post by cascade9 on 2009-08-25
Well..this wont work for every PC, or even close, and I have no idea of what coding etc you would need to do to use this, but there sure was a way. p3s had embedded serial numbers. Supposedly inel disabled that with thelate p3s, but who really knows?

> The Pentium III was the first x86 CPU to include a unique, retrievable, identification number, called PSN (Processor Serial Number). A Pentium III's PSN can be read by software through the [CPUID]("http://en.wikipedia.org/wiki/CPUID") instruction if this feature has not been disabled in [BIOS]("http://en.wikipedia.org/wiki/BIOS"). On [November 29]("http://en.wikipedia.org/wiki/November_29"), [1999]("http://en.wikipedia.org/wiki/1999"), the [Science and Technology Options Assessment]("http://en.wikipedia.org/wiki/Science_and_Technology_Options_Assessment") (STOA) Panel of the [European Parliament]("http://en.wikipedia.org/wiki/European_Parliament"), following their report on electronic surveillance techniques asked parliamentary committee members to consider legal measures that would "prevent these chips from being installed in the computers of European citizens."[]("http://en.wikipedia.org/wiki/Pentium_III#cite_note-9")
 Eventually Intel decided to remove the PSN feature on Tualatin-based Pentium IIIs, and the feature was not carried through to the Pentium 4 or Pentium M.


[http://en.wikipedia.org/wiki/Pentium_III](http://en.wikipedia.org/wiki/Pentium_III)

---

### Post by kliq on 2010-10-28
Searching about this general topic [initially CPU I.D] brought me to this old thread [amongst others].
I have recently started using Ubuntu and have been Very irritated by the use of 32 or 8 characters-long [volume labels?] to identify drives or partitions in the file browser (Nautilus?) tabs rather than standard partition labels [hda1 hda2 etc.] (I have many partitions on my drive_**s**_ and some are of similar sizes).
Anyway, these long 'numbers' seem to be 'fixed' to the hardware/partition - they never seem to change.
Since this information is available to me as an ordinary user, then it follows that any application [webb browser] will also know them too and be able to pass them onto websites [etc.'!' ] as identification.
So our privacy is not so safe.

---

### Post by mainerror on 2010-10-28
> **Ulysses_ said:**
> But you are still mixing computer anonymity with person anonymity: a person's name and postal address is still private if the computer is identified as the one that was trolling in the forum the other day. It's not like listed versus unlisted telephone numbers because these identify people's names and postal addresses.

People use computers so definitely you would easily get more information of ones identity than you'd want.

> **Ulysses_ said:**
> Why would it be dangerous?  The authorities already have other ways of uniquely identifying people by name, simply by asking ISPs and anonymity proxy providers.  What harm is there if everybody can uniquely everybody's pc, but not a person's name?

Authorities in countries with working a democracy will have to provide a court decision to the provider in order to get any information.

> **Baneblade said:**
> MAC address?

Besides that it can be spoofed in a second this information gets lost when it passes your router.

> **kliq said:**
> Searching about this general topic [initially CPU I.D] brought me to this old thread [amongst others].
I have recently started using Ubuntu and have been Very irritated by the use of 32 or 8 characters-long [volume labels?] to identify drives or partitions in the file browser (Nautilus?) tabs rather than standard partition labels [hda1 hda2 etc.] (I have many partitions on my drive_**s**_ and some are of similar sizes).
Anyway, these long 'numbers' seem to be 'fixed' to the hardware/partition - they never seem to change.
Since this information is available to me as an ordinary user, then it follows that any application [webb browser] will also know them too and be able to pass them onto websites [etc.'!' ] as identification.
So our privacy is not so safe.

Nah. A browser which would collect that information would be quite unpopular at least if it is open source and everyone would be able to check out the code. Also closed source browsers won't do that since if anyone would find out, they'd be screwed.

Sure there is a way to uniquely identify a computer but thankfully only with a plugin which the visitor of your site would need to install. And I said thankfully because otherwise the internet would be the most horrible place on earth.

---

### Post by friv_livs on 2010-12-08
I know of a CS major who wrote a program that could see local and remote logins, what tabs are open in firefox, and how long the system was idle for each station.

I forget how they did it, though.

This applies to a CS lab running fedora towers.

Not sure if this is any advance in this thread's topic, but it seemed to fit.

---

### Post by cariboo on 2010-12-08
> I know of a CS major who wrote a program that could see local and remote logins, what tabs are open in firefox, and how long the system was idle for each station.

I forget how they did it, though.

This applies to a CS lab running fedora towers.

Not sure if this is any advance in this thread's topic, but it seemed to fit.


If you have administrative access to all the systems, it's fairly simple to do, which really has nothing to do with this thread.

---

