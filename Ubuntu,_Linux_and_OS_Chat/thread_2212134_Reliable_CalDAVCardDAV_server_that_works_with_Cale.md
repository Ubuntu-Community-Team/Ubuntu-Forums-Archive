---
title: "Reliable CalDAV/CardDAV server that works with Calendar.app &amp; Addressbook.app"
date: 2014-03-19
forum: Ubuntu, Linux and OS Chat
---

### Post by bubblun on 2014-03-19
Hello all!

This being my first post and all, I've decided to jump in full force: with a *comprehensive question* of all things…

I've typed my fingers bloody in search for and teasing out a reliable CalDAV/CardDAV combination that actually works with Mac OS X Mavericks Calendar.app, Addressbook.app plus their iOS equivalents. Besides that my only further requirement is that calendar invitations can be sent to internal and external addresses. I believe that these are pretty basic requirements for any kind of business, startup, NGO or charity project. Yet what I've found so far is so seriously disheartening and frustrating that it could be enough to drive me away from Linux altogether as an SMB platform. Which is unfortunate because I really enjoy most aspects of Linux and especially Ubuntu as a server platform.

I've test-installed and tried out:


[LIST]
[*]Baïkal (does not support invitations)
[*]Radicale (does not support invitations)
[*]Chandler (can't remember but didn't work very well)
[*]ownCloud (does not support invitations)
[*]Zimbra (lots I don't need, does not support external invitations, problems with Calendar.app, Addressbook.app)
[*]Zarafa (lots I don't need, does not reliably support external invitations, missing CardDAV support)
[*]calendarserver.org (a pain to set up, bad documentation but kind-of-works)
[*]Kolab (experimental Ubuntu packages only, breaks on installation, practically no community support except for RHEL/CentOS, uses Courier mail server)
[*]DAViCal (really, really complex – gave up before I could get useful results)
[/LIST]

So far the only software I found to be mostly working was a commercial one: Kerio Connect. Besides installing Mac OS X (on a Mac of course) plus the server component.

Maybe I'm under a wrong impression or I'm doing something fundamentally wrong. I'd appreciate if someone with possibly more knowledge than me would take the time to give some feedback to a couple of points:


[LIST]
[*]Shared calendars (with external invitations), shared contacts and email are main staples of any kind of digital communication. Why seems to be no open source solution out there that works? I don't expect a just-install-and-use kind of solution. I'd actually appreciate a modular setup in true Linux spirit. But literally nothing calendar- or contact-related works as expected. This frustrates me as this is a situation in which most people are going to set up and exchange environment – something that ironically works with Mac OS X and iOS.
[*]Is there really no alternative to using a Mac OS X server or a Microsoft Exchange server to get basic groupware functionality reliably working on Ubuntu?
[*]Is there really no developer interest besides commercial products to support the Apple platform? Mac OS X is the best desktop operating system out there and many developers are using it.
[/LIST]

Maybe someone has even found a solution and is willing to share the setup idea and the software used. Any kind of information to get me on my way would be tremendously helpful and much appreciated.

---

### Post by TheFu on 2014-03-20
We use Zimbra. It follows standards. We use delegation, shared calendars, shared address books.  I've used Thunderbird and Lightning from an OSX machine and connected to Zimbra without any issues. It "just worked" - like it does on Windows and Linux.  There have been small challenges connecting from Android - we don't use iOS.

I've been running Zimbra servers since 2008-ish.

I've heard good things about Zafara - don't have any personal knowledge, however.

Why are you stuck with .app clients?  Also, I think the Zimbra web-client is better than gmail - by far - though I don't use it more than a few times a year.

For NGOs, I'd lean towards a [Citadel]("http://citadel.org/") deployment.  All-in-one communications server. Very simple interface, small footprint, small target for being hacked and no external clients, so that limits all the screwing around with desktop clients that don't work.

---

### Post by bubblun on 2014-03-25
Thanks for taking the time to reply and sorry for my lag in a response.

The thing with the Apple applications is that they come built-in and are what pretty much every Mac user expects to use. And frankly, the Thunderbird/Lightning combo is not at all comparable to the seamless integration of Mail.app, Calendar.app and Contacts.app. I tried to get customers to use a web interface for years but they just won't do it. They use Mail.app and expect it to work. They use the iPhone Mail.app and expect it just works. They use the Mac Calendar.app and expect it to just work. They use the iOS Calendar.app and expect it to just work. They use&#8230; (you get the idea) And I have to say: rightly so. Except for the fact that Apple software more often than not really does not output meaningful logs. "An error occurred while&#8230;" does not help at all.

Zimbra did not work so well for me. But maybe I need to give it another run.

I'd really prefer to use a combination of Dovecot for email, Roundcube for Webmail and anything for calendar and contacts (what I'm searching for). So far the best I have been able to come up with is [SOGo]("http://www.sogo.nu").

Thanks again. If anyone has more ideas, please let me know.

---

