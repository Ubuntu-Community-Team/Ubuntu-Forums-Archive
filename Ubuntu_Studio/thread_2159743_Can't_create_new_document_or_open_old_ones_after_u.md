---
title: "Can't create new document or open old ones after update - Krita problem"
date: 2013-07-04
forum: Ubuntu Studio
---

### Post by limbo on 2013-07-04
I updated my system (raring 13.04)  at 2nd of July and after that Krita doesn't work anymore. The first screen is OK, which shows "Recent Documents", "Open Document", etc. but if I'll try to create new document or open old document Krita crashes and I'll get this:

```
Compiled for arch: ::Vc::SSSE3Impl 
Features supported: 
	 "SSE2" 	---	 yes 
	 "SSE3" 	---	 yes 
	 "SSSE3" 	---	 yes 
	 "SSE4.1" 	---	 no 
	 "SSE4.2" 	---	 no 
	 "SSE4a" 	---	 no 
	 "AVX " 	---	 no 
krita(6215)/koffice (lib pigment) KoColorConversionSystem::insertColorSpace: Cannot add node for  "YCBCR (8-bit integer/channel)" , since there are no profiles available 
krita(6215)/koffice (lib pigment) KoColorConversionSystem::insertColorSpace: Cannot add node for  "YCBCR (16-bit integer/channel)" , since there are no profiles available 
krita(6215)/koffice (lib pigment) KoColorConversionSystem::insertColorSpace: Cannot add node for  "YCBCR (32-bit float/channel)" , since there are no profiles available 
Object::connect: No such signal KisResourceServerProvider::notifyBrushBlacklistCleanup()
krita(6215)/koffice (lib kopageapp) KoOdfLoadingContext::KoOdfLoadingContext: could not parse manifest document 
krita(6215)/koffice (lib kopageapp) KoOdfLoadingContext::KoOdfLoadingContext: could not parse manifest document 
krita(6215)/kdeui (KAction) KActionCollection::setComponentData: this does not work on a KActionCollection containing actions! 
The program 'krita' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAtom (invalid Atom parameter)'.
  (Details: serial 2297 error_code 5 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
CRITICAL: According to statistics of the KisTileDataStore some tiles have leaked from the Krita control! 
CRITICAL: Tiles in memory: 2 Total tiles: 2 

```

Updates that I installed in 2nd of July were

```
Start-Date: 2013-07-02  11:05:57
Commandline: aptdaemon role='role-commit-packages' sender=':1.56'
Upgrade: 
libkresources4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1),
libkldap4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libqt4-declarative:amd64 (4.8.4+dfsg-0ubuntu9, 4.8.4+dfsg-0ubuntu9.1), 
libqt4-qt3support:amd64 (4.8.4+dfsg-0ubuntu9, 4.8.4+dfsg-0ubuntu9.1), 
libkxmlrpcclient4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libknewstuff3-4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
qdbus:amd64 (4.8.4+dfsg-0ubuntu9, 4.8.4+dfsg-0ubuntu9.1), 
libkdeclarative5:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libnepomukquery4a:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
nepomuk-core-data:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libqt4-test:amd64 (4.8.4+dfsg-0ubuntu9, 4.8.4+dfsg-0ubuntu9.1), 
libqt4-script:amd64 (4.8.4+dfsg-0ubuntu9, 4.8.4+dfsg-0ubuntu9.1), 
libqt4-designer:amd64 (4.8.4+dfsg-0ubuntu9, 4.8.4+dfsg-0ubuntu9.1), 
libqt4-network:amd64 (4.8.4+dfsg-0ubuntu9, 4.8.4+dfsg-0ubuntu9.1), 
libqt4-dbus:amd64 (4.8.4+dfsg-0ubuntu9, 4.8.4+dfsg-0ubuntu9.1), 
libthreadweaver4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libkdecore5:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libnepomukutils4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libktexteditor4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libkmediaplayer4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
plasma-scriptengine-javascript:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libkrosscore4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libqt4-opengl:amd64 (4.8.4+dfsg-0ubuntu9, 4.8.4+dfsg-0ubuntu9.1), 
libsolid4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libqt4-xmlpatterns:amd64 (4.8.4+dfsg-0ubuntu9, 4.8.4+dfsg-0ubuntu9.1), 
libqt4-sql-sqlite:amd64 (4.8.4+dfsg-0ubuntu9, 4.8.4+dfsg-0ubuntu9.1), 
update-manager:amd64 (0.186, 0.186.1), 
update-manager-core:amd64 (0.186, 0.186.1), 
libnepomuk4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
python3-update-manager:amd64 (0.186, 0.186.1), 
libqt4-help:amd64 (4.8.4+dfsg-0ubuntu9, 4.8.4+dfsg-0ubuntu9.1), 
libkdnssd4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libkparts4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
kde-runtime-data:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libkabc4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
kdoctools:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libqtcore4:amd64 (4.8.4+dfsg-0ubuntu9, 4.8.4+dfsg-0ubuntu9.1), 
libkrossui4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libkidletime4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
katepart:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libkcmutils4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libkcal4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libqt4-sql:amd64 (4.8.4+dfsg-0ubuntu9, 4.8.4+dfsg-0ubuntu9.1), 
libkfile4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libqt4-svg:amd64 (4.8.4+dfsg-0ubuntu9, 4.8.4+dfsg-0ubuntu9.1), 
libkpty4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libqt4-xml:amd64 (4.8.4+dfsg-0ubuntu9, 4.8.4+dfsg-0ubuntu9.1), 
libkntlm4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libplasma3:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libkemoticons4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libnepomukcore4abi1:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libkmime4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
kdelibs-bin:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libkdewebkit5:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libqtgui4:amd64 (4.8.4+dfsg-0ubuntu9, 4.8.4+dfsg-0ubuntu9.1), 
kde-runtime:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libkjsembed4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
nepomuk-core:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libkio5:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libkjsapi4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
kdelibs5-data:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libkpimutils4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libqt4-sql-mysql:amd64 (4.8.4+dfsg-0ubuntu9, 4.8.4+dfsg-0ubuntu9.1), 
libqt4-scripttools:amd64 (4.8.4+dfsg-0ubuntu9, 4.8.4+dfsg-0ubuntu9.1), 
libkde3support4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libknotifyconfig4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
kdelibs5-plugins:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libkhtml5:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libkdeui5:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libkdesu5:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
libkatepartinterfaces4:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1), 
kate-data:amd64 (4.10.3-0ubuntu0.1~ubuntu13.04, 4.10.4-0ubuntu0.1)
End-Date: 2013-07-02  11:07:49
```

Any ideas which package might be the root cause of this crash? I checked some of them via synaptic but for some reason I couldn't find right version eg. libkdewebkit5 in synaptic force update show version number that is 4.10.2 and I believe that it should be that 4.10.3 like in history.log. And I'm not even sure what to look in package changelogs. String "BadAtom"? Any other ideas how I can solve this problem?

Thanks in advance.

---

