---
title: "stunning best looking most feature rich mail-server?"
date: 2006-09-10
forum: Server Platforms
---

### Post by Bjoeboo on 2006-09-10
Any suggestions on the best-of-breed linux solution (or mixed solution) mail server that does everything?

Basically, I'm looking for a linux solution or linux mixed solution that can do MTA, SMTP, IMAP, POP, SSL,TLS and has web interface capability on par with or better than  the newest Exchange [2007 with OWA support]("http://www.msexchange.org/img/upl/image0841086265302516.jpg")  It would be my personal mail server.  I would use thunderbird or outlook to connect to it at home, and connect via webmail while away from home.  I'm sorry I have to compare to MS, but its what I'm familier with; (from my work & school).  Anyways, we all have to start somewhere...

---

### Post by simone.brunozzi on 2006-09-11
Hi,
I suppose postfix is the right choice for you. I think even qmail is good, but its license is not as good as postfix's one.

cheers,

---

### Post by BoneKracker on 2006-09-11
yeah, it's called GMail

---

### Post by Bjoeboo on 2006-09-11
I checked out [Hula]("http://www.hula-project.org/Hula_Project"), some [other op here said]("http://www.ubuntuforums.org/showthread.php?t=92505&highlight=zimbra") its easy setup 'turnkey' to get going, but the only fully supported desktop client is uglyass [Sylpheed-Claws]("http://claws.sylpheed.org/screenshots.php"), Hula says other clients like [thunderbird and outlook work]("http://www.hula-project.org/General_FAQ") with Hula but don't support contacts & calendar functionality.  I also looked at [Scalix]("http://www.scalix.com/") but their [web access]("http://www.scalix.com/products/scalixwebaccess2.html") looks old-school, Outlook 2000ish.  I've guinea-pigged their myRealbox webmail before - same thing.  Not impressed.

I think I may try [Zimbra]("http://www.zimbra.com/index.html"); you got to watch their demo to understand why.  its got the gorgeous ajax web gui I want, works with outlook, thunderbird, blackberries, whatever.  But it may be a PITA to get going.  They don't have a binary for Ubuntu; just Suse, Mac, RH, & Fedora, but thay got binary for Debian, dunno if that'll work?  I may install from source.  Many dependancies to pre-install but the binary would set up half of them though if I could use it.  **Anybody have a successful Zimbra running on Ubuntu?:-k**

_Zimbra Dependencies:_
• NPTL. Native POSIX Thread Library
• Sudo. Superuser, required to delegate admins.
• libidn. For internationalizing domain names in applications (IDNA)
• cURL. A command line tool for transferring files with URL syntax
• fetchmail. A remote-mail retrieval and forwarding utility used for on-demand TCIP/IP links.
• GMP. GNU Multiple-Precision Library.
• compat-libstdcc++-33. Compatibility Standard C++ libraries. NOTE: The 32-bit version of the compat-libstdc rpm package is required for both 32-bit or 64-bit servers.
• For Red Hat Enterprise only: compatlibstdcc++-296
• Apache Tomcat
• Postfix, an open source message transfer agent (MTA) that routes mail messages to the appropriate Zimbra server.
• OpenLDAP software, an open source implementation of the Lightweight Directory Access Protocol (LDAP) that provides user authentication. Zimbra Collaboration Suite Open Source Edition 4.0 Page 11 Product Overview
• MySQL database software.
• Lucene, an open-source full featured text index and search engine.
• Anti-virus and anti-spam open source components including:
• ClamAV, an anti-virus scanner that protects against malicious files.
• SpamAssassin and DSPAM, mail filters that attempt to identify spam.
• Amavisd-new, which interfaces between the MTA and one or more content checkers.
• James/Sieve filtering, used to create filters for email.

---

### Post by Bjoeboo on 2006-09-11
> **BoneKracker said:**
> yeah, it's called GMail
 
What good is 2GB storage if the attachment size is limited?
How do I sort mail by sender? subject? attendees?
How do I make Gmail connect to and d-lode my other mail like my ISPs SMTP or other POP, IMAP, SMTP accounts?
How do I create complicated rules like "sort all incoming mail from bgates, or from MS.com, or from 5555555555@vtext into "from bill inbox"?
 
P.S.
and I want it all for free :)

---

### Post by BoneKracker on 2006-09-13
I was only joking.  I completely understand your desire to set up your own mta and so on.

I think cyrus and postfix are the way to go.  If you're on KDE, you might want to check out Kolab.

Also take a look a Scalix, eGroupware, OpenGroupware, and Open-Xchange.

---

### Post by TSMJ on 2006-09-13
[http://www.qmailrocks.org](http://www.qmailrocks.org)

It does everything you need, and v3 should be out soon, which will be even better. It uses Squirrelmail btw, which seems a bit basic at first, but it's fast, clean and easy to use. I'd be surprised if you could find anything as good as MS Exchange webmail for free, and would recommend setting your sights a little lower in that area! Seach for IMP - it's hard to set up (I believe) but is the best looking webmail I've used.

---

### Post by Bjoeboo on 2006-09-13
Are there any screenshots or demos of qmailrocks?   I can't find any.  I looked at open-Xchange  and I  like  the appearance and branding: OX. looks pretty cool.  But its lacking the slick Ajax/lamp stuff I want.  It seems somehow static, and antiquated... Like a distant cousin of office '97 or '2000ish era...

Sadly now that I've seen their flash tour of open-source [Zimbra]("http://www.zimbra.com/") I've become seduced by their eye-candy.  I must have it!  [This guy]("http://wiki.zimbra.com/index.php?title=Building_the_software_yourself") got it running on Breezy.  It should be doable on Dapper.  I opened an Ubuntu MOTU request to add Zimbra package, and I submitted a bug report to zimbra devs concerning the glaring omission of an Ubuntu package on their repository which includes packages for RH, Fedora5, Suse, Mac, and Debian available for download.  Evil bastards... 

**Could somebody that knows more than I do please create a ****Zimbra package for **[B]dapper?

[/B]**sudo apt-get install zimbra**

---

### Post by crazymonkey on 2006-09-17
The debian package should wortk with ubuntu. I'm downloading it atm and will give it a try in vmware and see if i can get it working. I'll keep you updated.

---

### Post by Bjoeboo on 2006-09-19
> **crazymonkey said:**
> The debian package should wortk with ubuntu. I'm downloading it atm and will give it a try in vmware and see if i can get it working. I'll keep you updated.Awesome!  Please post how it goes.  Any tweaks you have to make.

[This guy]("http://wiki.zimbra.com/index.php?title=Building_the_software_yourself") did it on Breezy... give it a look if you get stuck.

PS I just checked this post again in frustration after Thunderbird and Outlook refuse to connect to my gmail or Road Runner accounts to send mail.  It was working all last week, but now it decides smtp settings (turn ssl on/off? TLS? plaintext?) are no good.  I'm logging into their crummy little web interfaces and sending stuff that way.  What a drag.  Every time you hit "compose" you get a popup to type your email into.. Want to attach something?  Thats another popup...
AAAAAAAAAARRRRRRRRGGGGGGHHHHH!!!!!!!](*,)](*,)](*,)](*,)](*,)

---

### Post by hkgonra on 2006-09-19
I have been checking the zimbra forums and they seem to be on the verge of releasing a package for ubuntu. There was a zimbra employee responding on their forum to " wait a week" not long ago.

---

### Post by Bjoeboo on 2006-09-19
I read that.  It seemed more to me like the dev was telling the op to wait a week for the next stable Zimbra release (from source or for Debian)  not an Ubuntu build.

---

### Post by hkgonra on 2006-09-20
I didn't take it that way but you might be right.

---

### Post by loupy on 2006-09-20
I've installed Zimbra 4.0.1 on my dapper server and so far it's been working quite well.  A couple of bugs but nothing major.

---

### Post by Bjoeboo on 2006-09-27
I'm thinking of trying it on Edgy..  Maybe just some changes in the Breezy patches that get applied to the Debian package of Zimbra.

---

### Post by hkgonra on 2006-09-27
[http://www.ubuntuforums.org/showthread.php?t=265797](http://www.ubuntuforums.org/showthread.php?t=265797)

Might want to check this out.

---

### Post by yellowtip on 2006-09-28
I've been using Communigate Pro from Stalker ([http://www.stalker.com](http://www.stalker.com)) for many years now. It's rock solid and does everything you could ever imagine and more.

One problem might be...that it's commercial, ie, you need to pay for it.

---

