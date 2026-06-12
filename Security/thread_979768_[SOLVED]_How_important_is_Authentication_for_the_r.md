---
title: "[SOLVED] How important is Authentication for the repos"
date: 2008-11-12
forum: Security
---

### Post by crazyness003 on 2008-11-12
Hello. I had that simple question.
The reason why im asking is that I wanted to try out OOo 3 and found an article on [Softpedia]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml") that lets you install a repo package source for OOo3. Its not authenticated though. The source is called [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu)

Later I installed the repo package source for wine, from wineHQ. After adding the APT line, I noticed it had instructions on how to authenticate that particular software source. Si i did.

How much of a thread is leaving the OOo3 software source unauthenticated
Another repo package source iv noticed to do this is one of the AWN package sources.

So, i hope i asked in the correct forum, since this may be considered a security threat.
If so, is there anyway i can get the GPG key to authenticate is? or can i just leave it as it is?

---

### Post by lemming465 on 2008-11-15
> **crazyness003 said:**
> ... I ... found ... a repo package source for OOo3. It's not authenticated though ...
Trust is a matter of belief, bolstered by evidence.  Signed packages from organizations with good server security and careful key handling practices are best, definitely.  We like Ubuntu, RedHat, Microsoft, Postgres, PGP, and other projects and organizations that get this right.

This is not a guarantee; look at Redhat's recent problems with near-compromises in its RPM build/sign chain.  Or Microsoft's problem in January 2001 when two Verisign code signing certificates were bought using stolen credit cards.  Ken Thompson's Turing Award lecture *[Reflections on trusting trust]("http://cm.bell-labs.com/who/ken/trust.html")* is a famous reminder of how subtle security problems can get.  Contemporary American military avionics built with Chinese-manufactured chips have trust problems a lot like the ones Dr. Thompson described back in 1984, unsurprisingly.

As you rightly suspect, blithely adding any old repository someone touted on the web is almost as unsafe as running random binary code sent to you via e-mail or chat.  It might be what it purports to be, or it might be full of trojan'd botnet code or other malware.  You have to research its reputation and provenance to decide.  Bad guys can sign code too; all a signature does in that case is guarantee you got the genuine malware.  Professional malware vendors tend to include their own backdoors, so genuine signed malware as supplied to you by some downstream spamming miscreant may do more than he wanted, too.

If you are running 3rd party code, you need to know if it is being updated when security bugs are found.  Keep a wary eye out for compromises and security bugs, because you may have to do something yourself if your supplier doesn't.

Computer security is basically an ongoing process of risk management, at bottom.  On average, repositories holding signed code tend to be better run and less risky than ones that just blast the bits out there willy-nilly.  But the specifics will vary from project to project and can vary from month to month.

In your cases - OOo3 from launchpad.net and official Wine builds - you are probably OK, in my judgment.  (But can you trust me?)

---

### Post by crazyness003 on 2008-11-16
> **lemming465 said:**
> ...In your cases - OOo3 from launchpad.net and official Wine builds - you are probably OK, in my judgment.  (But can you trust me?)

okay. that was indepth. and yes, i will trust you for the fact that you spent [about] 3-7 minutes explaining this to me. I dont think a maleware-agent would do that...hopefully.

thanks. im sure someone else will ask this question in the future, and lo. it will be here, waiting for them.

Again, thanks for the insight.

---

