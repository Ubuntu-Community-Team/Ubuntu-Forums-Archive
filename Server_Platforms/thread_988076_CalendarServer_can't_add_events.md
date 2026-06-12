---
title: "CalendarServer can't add events"
date: 2008-11-20
forum: Server Platforms
---

### Post by hagueb on 2008-11-20
Hi,
I'm trying to get the CalendarServer from Apple working on Ubuntu 8.04. I've tried installing in various ways. The most recent one was using the script from [http://www.sicem.biz/personal/erny/dcs/darwin-calendarserver-install/view?searchterm=None](http://www.sicem.biz/personal/erny/dcs/darwin-calendarserver-install/view?searchterm=None). It seems to work correctly and connect to the calendar until I try to add an event of any description. When I do that it fails and the sort of error message below appears in the error.log. Does anyone know of a fix? Do I need a particular version?

Thanks
Ben

2008-11-20 11:36:50+0000 [-] [caldav-8008]  [HTTPChannel,18,127.0.0.1] [twistedcaldav.extensions#info] PUT /calendars/users/hagueb/calendar/20081120T113650Z.ics HTTP/1.1
2008-11-20 11:36:50+0000 [-] [caldav-8008]  [HTTPChannel,18,127.0.0.1] [twisted.web2.dav.method.put#info] Writing request stream to /home/hagueb/darwin/CalendarServer/twistedcaldav/test/data/calendars/__uids__/3F/25/3F2504E0-4F89-11D3-9A0C-0305E82C3301/calendar/20081120T113650Z.ics
2008-11-20 11:36:51+0000 [-] [caldav-8008]  [HTTPChannel,18,127.0.0.1] [twisted.web2.dav.method.put_common#error] Rollback: rollback
2008-11-20 11:36:51+0000 [-] [caldav-8008]  [HTTPChannel,18,127.0.0.1] Exception rendering:
2008-11-20 11:36:51+0000 [-] [caldav-8008]  [HTTPChannel,18,127.0.0.1] Unhandled Error
2008-11-20 11:36:51+0000 [-] [caldav-8008] 	Traceback (most recent call last):
2008-11-20 11:36:51+0000 [-] [caldav-8008] 	  File "/home/hagueb/darwin/Twisted/twisted/internet/defer.py", line 191, in addCallback
2008-11-20 11:36:51+0000 [-] [caldav-8008] 	    callbackKeywords=kw)
2008-11-20 11:36:51+0000 [-] [caldav-8008] 	  File "/home/hagueb/darwin/Twisted/twisted/internet/defer.py", line 182, in addCallbacks
2008-11-20 11:36:51+0000 [-] [caldav-8008] 	    self._runCallbacks()
2008-11-20 11:36:51+0000 [-] [caldav-8008] 	  File "/home/hagueb/darwin/Twisted/twisted/internet/defer.py", line 317, in _runCallbacks
2008-11-20 11:36:51+0000 [-] [caldav-8008] 	    self.result = callback(self.result, *args, **kw)
2008-11-20 11:36:51+0000 [-] [caldav-8008] 	  File "/home/hagueb/darwin/Twisted/twisted/internet/defer.py", line 813, in unwindGenerator
2008-11-20 11:36:51+0000 [-] [caldav-8008] 	    return _inlineCallbacks(None, f(*args, **kwargs), Deferred())
2008-11-20 11:36:51+0000 [-] [caldav-8008] 	--- <exception caught here> ---
2008-11-20 11:36:51+0000 [-] [caldav-8008] 	  File "/home/hagueb/darwin/Twisted/twisted/internet/defer.py", line 724, in _inlineCallbacks
2008-11-20 11:36:51+0000 [-] [caldav-8008] 	    result = g.throw(result.type, result.value, result.tb)
2008-11-20 11:36:51+0000 [-] [caldav-8008] 	  File "/home/hagueb/darwin/CalendarServer/twistedcaldav/method/put.py", line 76, in http_PUT
2008-11-20 11:36:51+0000 [-] [caldav-8008] 	    result = (yield super(CalDAVFile, self).http_PUT(request))
2008-11-20 11:36:51+0000 [-] [caldav-8008] 	exceptions.IOError: [Errno 95] Operation not supported: '/home/hagueb/darwin/CalendarServer/twistedcaldav/test/data/calendars/__uids__/3F/25/3F2504E0-4F89-11D3-9A0C-0305E82C3301'

---

### Post by threetimes on 2008-11-20
If you tried to install thi multiple times before, but with problems, something may be presentt from one of your failed installations. That can couse yoir problem.

---

### Post by hagueb on 2008-11-20
It's possible something's left, but as far as I can see it's a single folder that's created during the install, so deleting it should get the system back to the previous state.

---

