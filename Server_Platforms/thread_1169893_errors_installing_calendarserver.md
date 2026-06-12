---
title: "errors installing calendarserver"
date: 2009-05-25
forum: Server Platforms
---

### Post by Darryl Moore on 2009-05-25
I followed the instructions [here]("https://wiki.ubuntu.com/CalendarServer") to get CalDav calendarserver running on my server. everything appeared to work, though there was no need to change the 127.0.0.1 ip addresses as the code I got via svn already had that deleted.

What I did get though was a miserable bunch of messages posted below.

In particular to note are these ones:

> /usr/lib/python2.5/distutils/dist.py:263: UserWarning: Unknown distribution option: 'include_package_data'

which I got when I ran ./run -s

and 
> 
2009-05-25 17:11:06-0400 [-] [caldav-8009]  [-] twisted.internet.error.CannotListenError: Couldn't listen on 127.0.0.1:8009: (98, 'Address already in use').

which I got when I ran

 sudo -u caldavd -b /opt/caldavd/CalendarServer/run 

anybody have any ideas why this isn't working?

here is the full output from the last command which simply keeps retrying in an endless loop

> 2009-05-25 17:11:02-0400 [-] [caldav-8009]  [-] Log opened.
2009-05-25 17:11:02-0400 [-] [caldav-8009]  [-] twistd 2.5.0+rUnknown (/usr/bin/python 2.5.2) starting up
2009-05-25 17:11:02-0400 [-] [caldav-8009]  [-] reactor class: <class 'twisted.internet.selectreactor.SelectReactor'>
2009-05-25 17:11:02-0400 [-] [caldav-8009]  [-] [calendarserver.tap.caldav.CalDAVServiceMaker#info] Configuring directory service of type: twistedcaldav.directory.xmlfile.XMLDirectoryService
2009-05-25 17:11:02-0400 [-] [caldav-8009]  [-] [twistedcaldav.directory.xmlaccountsparser#error] Invalid GUID (badly formed hexadecimal UUID string) in accounts XML: 'admin'
2009-05-25 17:11:02-0400 [-] [caldav-8009]  [-] [twistedcaldav.directory.xmlaccountsparser#error] Invalid GUID (badly formed hexadecimal UUID string) in accounts XML: 'apprentice'
2009-05-25 17:11:02-0400 [-] [caldav-8009]  [-] [twistedcaldav.directory.xmlaccountsparser#error] Invalid GUID (badly formed hexadecimal UUID string) in accounts XML: 'user%02d'
2009-05-25 17:11:02-0400 [-] [caldav-8009]  [-] [twistedcaldav.directory.xmlaccountsparser#error] Invalid GUID (badly formed hexadecimal UUID string) in accounts XML: 'public%02d'
2009-05-25 17:11:02-0400 [-] [caldav-8009]  [-] [twistedcaldav.directory.xmlaccountsparser#error] Invalid GUID (badly formed hexadecimal UUID string) in accounts XML: 'location%02d'
2009-05-25 17:11:02-0400 [-] [caldav-8009]  [-] [twistedcaldav.directory.xmlaccountsparser#error] Invalid GUID (badly formed hexadecimal UUID string) in accounts XML: 'resource%02d'
2009-05-25 17:11:02-0400 [-] [caldav-8009]  [-] [twistedcaldav.directory.xmlaccountsparser#error] Invalid GUID (badly formed hexadecimal UUID string) in accounts XML: 'group01'
2009-05-25 17:11:02-0400 [-] [caldav-8009]  [-] [twistedcaldav.directory.xmlaccountsparser#error] Invalid GUID (badly formed hexadecimal UUID string) in accounts XML: 'group02'
2009-05-25 17:11:02-0400 [-] [caldav-8009]  [-] [twistedcaldav.directory.xmlaccountsparser#error] Invalid GUID (badly formed hexadecimal UUID string) in accounts XML: 'group03'
2009-05-25 17:11:02-0400 [-] [caldav-8009]  [-] [twistedcaldav.directory.xmlaccountsparser#error] Invalid GUID (badly formed hexadecimal UUID string) in accounts XML: 'group04'
2009-05-25 17:11:02-0400 [-] [caldav-8009]  [-] [twistedcaldav.directory.xmlaccountsparser#error] Invalid GUID (badly formed hexadecimal UUID string) in accounts XML: 'disabledgroup'
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-] [calendarserver.tap.caldav.CalDAVServiceMaker#info] Configuring SudoDirectoryService with file: conf/sudoers.plist
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-] [calendarserver.tap.caldav.CalDAVServiceMaker#info] Configuring authentication for realm: Test Realm
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-] [calendarserver.tap.caldav.CalDAVServiceMaker#info] Setting up scheme: wiki
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-] [calendarserver.tap.caldav.CalDAVServiceMaker#info] Setting up scheme: digest
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-] [calendarserver.tap.caldav.CalDAVServiceMaker#info] Setting up scheme: basic
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-] [calendarserver.tap.caldav.CalDAVServiceMaker#info] Setting up document root at: twistedcaldav/test/data/
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-] [calendarserver.tap.caldav.CalDAVServiceMaker#info] Setting up principal collection: <class 'twistedcaldav.directory.principal.DirectoryPrincipalProvisioningResource'>
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-] [calendarserver.tap.caldav.CalDAVServiceMaker#info] Setting up calendar collection: <class 'twistedcaldav.static.CalendarHomeProvisioningFile'>
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-] [calendarserver.tap.caldav.CalDAVServiceMaker#info] Setting up root resource: <class 'calendarserver.provision.root.RootResource'>
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-] [calendarserver.tap.caldav.CalDAVServiceMaker#info] Setting up time zone service resource: <class 'twistedcaldav.static.TimezoneServiceFile'>
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-] [calendarserver.tap.caldav.CalDAVServiceMaker#info] Setting up WebCalendar resource: /usr/share/collaboration
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-] [calendarserver.tap.caldav.CalDAVServiceMaker#info] Setting up WebAdmin resource
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-] [calendarserver.tap.caldav.CalDAVServiceMaker#info] Setting up Timezone Cache
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-] [calendarserver.tap.caldav.CalDAVServiceMaker#info] Configuring authentication wrapper
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-] [calendarserver.tap.caldav.CalDAVServiceMaker#info] Setting up service
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-] [calendarserver.tap.caldav.CalDAVServiceMaker#info] Logging via AF_UNIX: logs/caldavd.sock
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-] [calendarserver.tap.caldav.CalDAVServiceMaker#info] Configuring log observer: <twistedcaldav.accesslog.AMPCommonAccessLoggingObserver object at 0x8adbdec>
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-] [calendarserver.tap.caldav.CalDAVServiceMaker#info] Adding SSL server at 127.0.0.1:8444
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-] [calendarserver.tap.caldav.CalDAVServiceMaker#info] Adding server at 127.0.0.1:8009
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-] twext.web2.channel.http.HTTP503LoggingFactory starting on 8444
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-] Traceback (most recent call last):
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-]   File "../Twisted/bin/twistd", line 21, in <module>
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-]     run()
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-]   File "/opt/caldavd/Twisted/twisted/scripts/twistd.py", line 27, in run
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-]     app.run(runApp, ServerOptions)
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-]   File "/opt/caldavd/Twisted/twisted/application/app.py", line 379, in run
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-]     runApp(config)
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-]   File "/opt/caldavd/Twisted/twisted/scripts/twistd.py", line 23, in runApp
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-]     _SomeApplicationRunner(config).run()
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-]   File "/opt/caldavd/Twisted/twisted/application/app.py", line 158, in run
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-]     self.postApplication()
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-]   File "/opt/caldavd/Twisted/twisted/scripts/_twistd_unix.py", line 213, in postApplication
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-]     startApplication(self.config, self.application)
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-]   File "/opt/caldavd/Twisted/twisted/scripts/_twistd_unix.py", line 174, in startApplication
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-]     service.IService(application).privilegedStartService()
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-]   File "/opt/caldavd/Twisted/twisted/application/service.py", line 228, in privilegedStartService
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-]     service.privilegedStartService()
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-]   File "/opt/caldavd/CalendarServer/calendarserver/tap/caldav.py", line 119, in privilegedStartService
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-]     MultiService.privilegedStartService(self)
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-]   File "/opt/caldavd/Twisted/twisted/application/service.py", line 228, in privilegedStartService
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-]     service.privilegedStartService()
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-]   File "/opt/caldavd/Twisted/twisted/application/internet.py", line 68, in privilegedStartService
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-]     self._port = self._getPort()
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-]   File "/opt/caldavd/Twisted/twisted/application/internet.py", line 86, in _getPort
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-]     return getattr(reactor, 'listen'+self.method)(*self.args, **self.kwargs)
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-]   File "/opt/caldavd/Twisted/twisted/internet/posixbase.py", line 467, in listenTCP
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-]     p.startListening()
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-]   File "/opt/caldavd/Twisted/twisted/internet/tcp.py", line 733, in startListening
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-]     raise CannotListenError, (self.interface, self.port, le)
2009-05-25 17:11:04-0400 [-] [caldav-8009]  [-] twisted.internet.error.CannotListenError: Couldn't listen on 127.0.0.1:8009: (98, 'Address already in use').


---

