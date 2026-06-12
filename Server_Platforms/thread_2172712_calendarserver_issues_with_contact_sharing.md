---
title: "calendarserver issues with contact sharing"
date: 2013-09-06
forum: Server Platforms
---

### Post by MatsWolpers on 2013-09-06
setup:
i run ubuntu 12.04 on a server.
i installed calendarserver package via apt (receiving version 2.4.dfsg-7.
i managed to edit an /etc/caldavd/accounts.xml to match my environment (home lan: one server, several mac and win clients) 
from a client mac, i made contact with the calendar part of this server and managed to move appointments from local calendars to server based calendar.
i understand this to mean that so far i haven't done much wrong.

issue:
i tried to make similar contact to share cardDAV contacts through the mac's addressbook application and failed.
tinkering with the dialog's settings (mostly port numbers and enabling SSL or not) revealed these symptoms:
- server side:
in /var/log/caldavd/error.log i find entries: <timestamp> [-] [PooledMemCacheProtocol,client] [twistedcaldav.directory.principal#error] File not found: /var/spool/caldavd/.well-known/carddav (true enough, no such thing at that location)

- client side:
in system.log, i find entries (where i used X, Y to overwrite real numbers)
Sep  6 10:49:22 Muddy.local Contacts[5717]: [CardDAVPlugin-ERROR] -getPrincipalInfo:[_controller discoverServer [http://matthias@192.168.X.Y:8008(null)]](http://matthias@192.168.X.Y:8008(null)]) Error Domain=CoreDAVHTTPStatusErrorDomain Code=404 "The operation couldn’t be completed. (CoreDAVHTTPStatusErrorDomain error 404.)" UserInfo=0x7f841dbbf250 {CoreDAVHTTPHeaders=<CFBasicHash 0x7f841d85d7a0 [0x7fff758b1110]>{type = immutable dict, count = 5,
	entries =>
		0 : Case Insensitive Key: Server = <CFString 0x7f841dbd5530 [0x7fff758b1110]>{contents = "Twisted/8.2.0 TwistedWeb/8.2.0"}
		3 : Case Insensitive Key: Content-Type = <CFString 0x7f841d8e01e0 [0x7fff758b1110]>{contents = "text/html;charset=utf-8"}
		4 : Case Insensitive Key: Content-Length = <CFString 0x7fff7588bb40 [0x7fff758b1110]>{contents = "135"}
		5 : Case Insensitive Key: DAV = <CFString 0x7f841d8d92f0 [0x7fff758b1110]>{contents = "1, access-control"}
		6 : Case Insensitive Key: Date = <CFString 0x7f841d9d7650 [0x7fff758b1110]>{contents = "Fri, 06 Sep 2013 08:54:19 GMT"}
	}
	}

and 
Sep  6 11:00:57 Muddy.local CalendarAgent[278]: [com.apple.calendar.store.log.caldav.queue] [Account refresh failed with error: Error Domain=CoreDAVHTTPStatusErrorDomain Code=404 "The operation couldn’t be completed. (CoreDAVHTTPStatusErrorDomain error 404.)" UserInfo=0x7fe60de73050 {AccountName=matthias@victoria, CalDAVErrFromRefresh=YES, CoreDAVHTTPHeaders=<CFBasicHash 0x7fe60c1f5180 [0x7fff758b1110]>{type = immutable dict, count = 4,
	entries =>
		3 : Case Insensitive Key: Content-Type = <CFString 0x7fe60c1f4f30 [0x7fff758b1110]>{contents = "text/html;charset=utf-8"}
		4 : Case Insensitive Key: Content-Length = <CFString 0x7fe60c1237d0 [0x7fff758b1110]>{contents = "173"}
		5 : Case Insensitive Key: Server = <CFString 0x7fe60c1f5460 [0x7fff758b1110]>{contents = "Twisted/8.2.0 TwistedWeb/8.2.0"}
		6 : Case Insensitive Key: Date = <CFString 0x7fe60c1c6af0 [0x7fff758b1110]>{contents = "Fri, 06 Sep 2013 09:05:55 GMT"}
	}
	}]

in the addressbook application, the account is shown with a triangled ! sign that explodes into a The operation couldn’t be completed. (CoreDAVHTTPStatusErrorDomain error 404.) message.

i am not smart enough to tell if this points to a problem in the user, or in the client software, or on the server side.

the questions:
can anyone please explain where the problem probably is?
would anyone using calendarserver to share cardDAV contacts (not dates, i can do that) please explain how it is made to work?



many thanks, mats

---

