---
title: "Ubuntu iCal Server howto"
date: 2007-12-26
forum: Server Platforms
---

### Post by cammj on 2007-12-26
Just thought i'd share my experiences guys.

I have successfully setup an iCal server using Apples open source Calender Server based on CalDAV.

I've posted the step by step at

[http://cam.moobox.org/blog/?p=5]("http://cam.moobox.org/blog/?p=5")

---

### Post by timeshifter on 2008-01-07
First, thanks for the instructions.  Even for a Ubuntu novice like myself, they were pretty easy to follow.

I tried this on clean installs of both 7.10 desktop and server.  The desktop install worked fine.  The server install did not.

Here's the command line output when I try to start the Calendar Server.

/usr/local/CalendarServer/run: line 463: type: krb5-config: not found
Traceback (most recent call last):
  File "/usr/local/Twisted/twisted/application/app.py", line 354, in parseOptions
    usage.Options.parseOptions(self, options)
  File "/usr/local/Twisted/twisted/python/usage.py", line 184, in parseOptions
    for (cmd, short, parser, doc) in self.subCommands:
  File "/usr/local/Twisted/twisted/application/app.py", line 364, in subCommands
    for plug in plugins:
  File "/usr/local/Twisted/twisted/plugin.py", line 186, in getPlugins
    allDropins = getCache(package)
--- <exception caught here> ---
  File "/usr/local/Twisted/twisted/plugin.py", line 151, in getCache
    provider = pluginModule.load()
  File "/usr/local/Twisted/twisted/python/modules.py", line 378, in load
    return self.pathEntry.pythonPath.moduleLoader(self.name)
  File "/usr/local/Twisted/twisted/python/modules.py", line 614, in moduleLoader
    return self._moduleLoader(modname)
  File "/usr/local/Twisted/twisted/python/reflect.py", line 361, in namedAny
    topLevelPackage = __import__(trialname)
  File "/usr/local/CalendarServer/twisted/plugins/caldav.py", line 1, in <module>
    from twistedcaldav.tap import CalDAVServiceMaker
  File "/usr/local/CalendarServer/twistedcaldav/tap.py", line 45, in <module>
    from twistedcaldav.resource import CalDAVResource
  File "/usr/local/CalendarServer/twistedcaldav/resource.py", line 35, in <module>
    from twisted.web2.dav.idav import IDAVPrincipalCollectionResource
exceptions.ImportError: cannot import name IDAVPrincipalCollectionResource
Traceback (most recent call last):
  File "/usr/local/Twisted/twisted/application/app.py", line 354, in parseOptions
    usage.Options.parseOptions(self, options)
  File "/usr/local/Twisted/twisted/python/usage.py", line 184, in parseOptions
    for (cmd, short, parser, doc) in self.subCommands:
  File "/usr/local/Twisted/twisted/application/app.py", line 364, in subCommands
    for plug in plugins:
  File "/usr/local/Twisted/twisted/plugin.py", line 186, in getPlugins
    allDropins = getCache(package)
--- <exception caught here> ---
  File "/usr/local/Twisted/twisted/plugin.py", line 151, in getCache
    provider = pluginModule.load()
  File "/usr/local/Twisted/twisted/python/modules.py", line 378, in load
    return self.pathEntry.pythonPath.moduleLoader(self.name)
  File "/usr/local/Twisted/twisted/python/modules.py", line 614, in moduleLoader
    return self._moduleLoader(modname)
  File "/usr/local/Twisted/twisted/python/reflect.py", line 361, in namedAny
    topLevelPackage = __import__(trialname)
  File "/usr/local/Twisted/twisted/plugins/twisted_lore.py", line 4, in <module>
    from twisted.lore.scripts.lore import IProcessor
  File "/usr/local/Twisted/twisted/lore/scripts/lore.py", line 8, in <module>
    from twisted.lore import process, indexer, numberer, htmlbook
  File "/usr/local/Twisted/twisted/lore/process.py", line 7, in <module>
    import tree #todo: get rid of this later
  File "/usr/local/Twisted/twisted/lore/tree.py", line 8, in <module>
    from twisted.web import microdom, domhelpers
  File "/usr/local/Twisted/twisted/web/microdom.py", line 30, in <module>
    from twisted.web.sux import XMLParser, ParseError
  File "/usr/local/Twisted/twisted/web/sux.py", line 23, in <module>
    from twisted.internet.protocol import Protocol, FileWrapper
  File "/usr/local/Twisted/twisted/internet/protocol.py", line 394, in <module>
    interfaces.IConsumer)
  File "/usr/local/Twisted/twisted/python/components.py", line 87, in registerAdapter
    raise ValueError("an adapter (%s) was already registered." % (factory, ))
exceptions.ValueError: an adapter (twisted.internet.protocol.ProtocolToConsumerAdapter) was already registered.
Traceback (most recent call last):
  File "/usr/local/Twisted/twisted/python/usage.py", line 373, in __str__
    return self.getSynopsis() + '\n' + self.getUsage(width=None)
  File "/usr/local/Twisted/twisted/python/usage.py", line 407, in getUsage
    for (cmd, short, parser, desc) in self.subCommands:
  File "/usr/local/Twisted/twisted/application/app.py", line 364, in subCommands
    for plug in plugins:
  File "/usr/local/Twisted/twisted/plugin.py", line 186, in getPlugins
    allDropins = getCache(package)
--- <exception caught here> ---
  File "/usr/local/Twisted/twisted/plugin.py", line 151, in getCache
    provider = pluginModule.load()
  File "/usr/local/Twisted/twisted/python/modules.py", line 378, in load
    return self.pathEntry.pythonPath.moduleLoader(self.name)
  File "/usr/local/Twisted/twisted/python/modules.py", line 614, in moduleLoader
    return self._moduleLoader(modname)
  File "/usr/local/Twisted/twisted/python/reflect.py", line 361, in namedAny
    topLevelPackage = __import__(trialname)
  File "/usr/local/CalendarServer/twisted/plugins/caldav.py", line 1, in <module>
    from twistedcaldav.tap import CalDAVServiceMaker
  File "/usr/local/CalendarServer/twistedcaldav/tap.py", line 37, in <module>
    from twisted.web2.channel import http
  File "/usr/local/Twisted/twisted/web2/channel/__init__.py", line 9, in <module>
    from twisted.web2.channel.http import HTTPFactory
  File "/usr/local/Twisted/twisted/web2/channel/http.py", line 8, in <module>
    from twisted.protocols import policies, basic
  File "/usr/local/Twisted/twisted/protocols/policies.py", line 16, in <module>
    from twisted.internet.protocol import ServerFactory, Protocol, ClientFactory
  File "/usr/local/Twisted/twisted/internet/protocol.py", line 394, in <module>
    interfaces.IConsumer)
  File "/usr/local/Twisted/twisted/python/components.py", line 87, in registerAdapter
    raise ValueError("an adapter (%s) was already registered." % (factory, ))
exceptions.ValueError: an adapter (twisted.internet.protocol.ProtocolToConsumerAdapter) was already registered.
Traceback (most recent call last):
  File "/usr/local/Twisted/twisted/python/usage.py", line 373, in __str__
    return self.getSynopsis() + '\n' + self.getUsage(width=None)
  File "/usr/local/Twisted/twisted/python/usage.py", line 407, in getUsage
    for (cmd, short, parser, desc) in self.subCommands:
  File "/usr/local/Twisted/twisted/application/app.py", line 364, in subCommands
    for plug in plugins:
  File "/usr/local/Twisted/twisted/plugin.py", line 186, in getPlugins
    allDropins = getCache(package)
--- <exception caught here> ---
  File "/usr/local/Twisted/twisted/plugin.py", line 151, in getCache
    provider = pluginModule.load()
  File "/usr/local/Twisted/twisted/python/modules.py", line 378, in load
    return self.pathEntry.pythonPath.moduleLoader(self.name)
  File "/usr/local/Twisted/twisted/python/modules.py", line 614, in moduleLoader
    return self._moduleLoader(modname)
  File "/usr/local/Twisted/twisted/python/reflect.py", line 361, in namedAny
    topLevelPackage = __import__(trialname)
  File "/usr/local/Twisted/twisted/plugins/twisted_lore.py", line 4, in <module>
    from twisted.lore.scripts.lore import IProcessor
  File "/usr/local/Twisted/twisted/lore/scripts/lore.py", line 8, in <module>
    from twisted.lore import process, indexer, numberer, htmlbook
  File "/usr/local/Twisted/twisted/lore/process.py", line 7, in <module>
    import tree #todo: get rid of this later
  File "/usr/local/Twisted/twisted/lore/tree.py", line 8, in <module>
    from twisted.web import microdom, domhelpers
  File "/usr/local/Twisted/twisted/web/microdom.py", line 30, in <module>
    from twisted.web.sux import XMLParser, ParseError
  File "/usr/local/Twisted/twisted/web/sux.py", line 23, in <module>
    from twisted.internet.protocol import Protocol, FileWrapper
  File "/usr/local/Twisted/twisted/internet/protocol.py", line 394, in <module>
    interfaces.IConsumer)
  File "/usr/local/Twisted/twisted/python/components.py", line 87, in registerAdapter
    raise ValueError("an adapter (%s) was already registered." % (factory, ))
exceptions.ValueError: an adapter (twisted.internet.protocol.ProtocolToConsumerAdapter) was already registered.
Usage: twistd [options]
Options:
      --savestats        save the Stats object rather than the text output of
                         the profiler.
  -o, --no_save          do not save state on shutdown
  -e, --encrypted        The specified tap/aos/xml file is encrypted.
      --nothotshot       Don't use the 'hotshot' profiler even if it's
                         available.
  -n, --nodaemon         don't daemonize
  -q, --quiet            No-op for backwards compatability.
      --originalname     Don't try to change the process name
      --syslog           Log to syslog, not to file
      --euid             Set only effective user-id rather than real user-id.
                         (This option has no effect unless the server is running
                         as root, in which case it means not to shed all
                         privileges after binding ports, retaining the option to
                         regain privileges in cases such as spawning processes.
                         Use with caution.)
  -l, --logfile=         log to a specified file, - for stdout
  -p, --profile=         Run in profile mode, dumping results to specified file
  -f, --file=            read the given .tap file [default: twistd.tap]
  -y, --python=          read an application from within a Python file (implies
                         -o)
  -x, --xml=             Read an application from a .tax file (Marmalade
                         format).
  -s, --source=          Read an application from a .tas file (AOT format).
  -d, --rundir=          Change to a supplied directory before running [default:
                         .]
      --report-profile=  E-mail address to use when reporting dynamic execution
                         profiler stats. This should not be combined with other
                         profiling options. This will only take effect if the
                         application to be run has an application name.
      --prefix=          use the given prefix when syslogging [default: twisted]
      --pidfile=         Name of the pidfile [default: twistd.pid]
      --chroot=          Chroot to a supplied directory before running
  -u, --uid=             The uid to run as.
  -g, --gid=             The gid to run as.
      --help-reactors    Display a list of possibly available reactor names.
      --version          Print version information and exit.
      --spew             Print an insanely verbose log of everything that
                         happens. Useful when debugging freezes or locks in
                         complex code.
  -b, --debug            run the application in the Python Debugger (implies
                         nodaemon), sending SIGUSR2 will drop into debugger
  -r, --reactor=         Which reactor to use (see --help-reactors for a list of
                         possibilities)
      --help             Display this help and exit.
Commands:
    web2             An HTTP/1.1 web server that can serve from a filesystem or
                     application resource.
    ftp              An FTP server.
    telnet           A simple, telnet-based remote debugging service.
    socks            A SOCKSv4 proxy service.
    manhole-old      An interactive remote debugger service.
    portforward      A simple port-forwarder.
    web              A general-purpose web server which can serve from a
                     filesystem or application resource.
    inetd            An inetd(8) replacement.
    news             A news server.
    words            A modern words server
    toc              An AIM TOC service.
    dns              A domain name server.
    mail             An email service
    manhole          An interactive remote debugger service accessible via
                     telnet and ssh and providing syntax coloring and basic line
                     editing functionality.
    conch            A Conch SSH service.

/usr/local/Twisted/bin/twistd: Unknown command: caldav


As I said above, I'm a Ubuntu novice, so any help would be appreciated.

Thanks!

---

### Post by tegwilym on 2008-01-08
I do ok until I get to the...

 [I]&#8220;/usr/local/CalendarServer/run -s&#8221;
[/I]
I get ***"SVN: Can't connect to host 'svn.twistedmatrix.com' : connection refused"***

any idea how to get around that problem?  I've been trying for a while to get an iCal server running for our office (and avoid Exchange/Outlook!), but have had nothing but trouble getting anything working.

OS X Leopard server version?  Blah!  Even harder to configure than anything else.   I'm trying Linux again.

Any ideas??

Tom

---

### Post by cammj on 2008-01-08
> **tegwilym said:**
> I do ok until I get to the...

 [I]“/usr/local/CalendarServer/run -s”
[/I]
I get ***"SVN: Can't connect to host 'svn.twistedmatrix.com' : connection refused"***

any idea how to get around that problem?  I've been trying for a while to get an iCal server running for our office (and avoid Exchange/Outlook!), but have had nothing but trouble getting anything working.

OS X Leopard server version?  Blah!  Even harder to configure than anything else.   I'm trying Linux again.

Any ideas??

Tom

It sounds like SVN access is blocked!

---

### Post by cammj on 2008-01-08
> **timeshifter said:**
> First, thanks for the instructions.  Even for a Ubuntu novice like myself, they were pretty easy to follow.

I tried this on clean installs of both 7.10 desktop and server.  The desktop install worked fine.  The server install did not.

Here's the command line output when I try to start the Calendar Server.

/usr/local/CalendarServer/run: line 463: type: krb5-config: not found
Traceback (most recent call last):
  File "/usr/local/Twisted/twisted/application/app.py", line 354, in parseOptions
    usage.Options.parseOptions(self, options)
  File "/usr/local/Twisted/twisted/python/usage.py", line 184, in parseOptions
    for (cmd, short, parser, doc) in self.subCommands:
  File "/usr/local/Twisted/twisted/application/app.py", line 364, in subCommands
    for plug in plugins:
  File "/usr/local/Twisted/twisted/plugin.py", line 186, in getPlugins
    allDropins = getCache(package)
--- <exception caught here> ---
  File "/usr/local/Twisted/twisted/plugin.py", line 151, in getCache
    provider = pluginModule.load()
  File "/usr/local/Twisted/twisted/python/modules.py", line 378, in load
    return self.pathEntry.pythonPath.moduleLoader(self.name)
  File "/usr/local/Twisted/twisted/python/modules.py", line 614, in moduleLoader
    return self._moduleLoader(modname)
  File "/usr/local/Twisted/twisted/python/reflect.py", line 361, in namedAny
    topLevelPackage = __import__(trialname)
  File "/usr/local/CalendarServer/twisted/plugins/caldav.py", line 1, in <module>
    from twistedcaldav.tap import CalDAVServiceMaker
  File "/usr/local/CalendarServer/twistedcaldav/tap.py", line 45, in <module>
    from twistedcaldav.resource import CalDAVResource
  File "/usr/local/CalendarServer/twistedcaldav/resource.py", line 35, in <module>
    from twisted.web2.dav.idav import IDAVPrincipalCollectionResource
exceptions.ImportError: cannot import name IDAVPrincipalCollectionResource
Traceback (most recent call last):
  File "/usr/local/Twisted/twisted/application/app.py", line 354, in parseOptions
    usage.Options.parseOptions(self, options)
  File "/usr/local/Twisted/twisted/python/usage.py", line 184, in parseOptions
    for (cmd, short, parser, doc) in self.subCommands:
  File "/usr/local/Twisted/twisted/application/app.py", line 364, in subCommands
    for plug in plugins:
  File "/usr/local/Twisted/twisted/plugin.py", line 186, in getPlugins
    allDropins = getCache(package)
--- <exception caught here> ---
  File "/usr/local/Twisted/twisted/plugin.py", line 151, in getCache
    provider = pluginModule.load()
  File "/usr/local/Twisted/twisted/python/modules.py", line 378, in load
    return self.pathEntry.pythonPath.moduleLoader(self.name)
  File "/usr/local/Twisted/twisted/python/modules.py", line 614, in moduleLoader
    return self._moduleLoader(modname)
  File "/usr/local/Twisted/twisted/python/reflect.py", line 361, in namedAny
    topLevelPackage = __import__(trialname)
  File "/usr/local/Twisted/twisted/plugins/twisted_lore.py", line 4, in <module>
    from twisted.lore.scripts.lore import IProcessor
  File "/usr/local/Twisted/twisted/lore/scripts/lore.py", line 8, in <module>
    from twisted.lore import process, indexer, numberer, htmlbook
  File "/usr/local/Twisted/twisted/lore/process.py", line 7, in <module>
    import tree #todo: get rid of this later
  File "/usr/local/Twisted/twisted/lore/tree.py", line 8, in <module>
    from twisted.web import microdom, domhelpers
  File "/usr/local/Twisted/twisted/web/microdom.py", line 30, in <module>
    from twisted.web.sux import XMLParser, ParseError
  File "/usr/local/Twisted/twisted/web/sux.py", line 23, in <module>
    from twisted.internet.protocol import Protocol, FileWrapper
  File "/usr/local/Twisted/twisted/internet/protocol.py", line 394, in <module>
    interfaces.IConsumer)
  File "/usr/local/Twisted/twisted/python/components.py", line 87, in registerAdapter
    raise ValueError("an adapter (%s) was already registered." % (factory, ))
exceptions.ValueError: an adapter (twisted.internet.protocol.ProtocolToConsumerAdapter) was already registered.
Traceback (most recent call last):
  File "/usr/local/Twisted/twisted/python/usage.py", line 373, in __str__
    return self.getSynopsis() + '\n' + self.getUsage(width=None)
  File "/usr/local/Twisted/twisted/python/usage.py", line 407, in getUsage
    for (cmd, short, parser, desc) in self.subCommands:
  File "/usr/local/Twisted/twisted/application/app.py", line 364, in subCommands
    for plug in plugins:
  File "/usr/local/Twisted/twisted/plugin.py", line 186, in getPlugins
    allDropins = getCache(package)
--- <exception caught here> ---
  File "/usr/local/Twisted/twisted/plugin.py", line 151, in getCache
    provider = pluginModule.load()
  File "/usr/local/Twisted/twisted/python/modules.py", line 378, in load
    return self.pathEntry.pythonPath.moduleLoader(self.name)
  File "/usr/local/Twisted/twisted/python/modules.py", line 614, in moduleLoader
    return self._moduleLoader(modname)
  File "/usr/local/Twisted/twisted/python/reflect.py", line 361, in namedAny
    topLevelPackage = __import__(trialname)
  File "/usr/local/CalendarServer/twisted/plugins/caldav.py", line 1, in <module>
    from twistedcaldav.tap import CalDAVServiceMaker
  File "/usr/local/CalendarServer/twistedcaldav/tap.py", line 37, in <module>
    from twisted.web2.channel import http
  File "/usr/local/Twisted/twisted/web2/channel/__init__.py", line 9, in <module>
    from twisted.web2.channel.http import HTTPFactory
  File "/usr/local/Twisted/twisted/web2/channel/http.py", line 8, in <module>
    from twisted.protocols import policies, basic
  File "/usr/local/Twisted/twisted/protocols/policies.py", line 16, in <module>
    from twisted.internet.protocol import ServerFactory, Protocol, ClientFactory
  File "/usr/local/Twisted/twisted/internet/protocol.py", line 394, in <module>
    interfaces.IConsumer)
  File "/usr/local/Twisted/twisted/python/components.py", line 87, in registerAdapter
    raise ValueError("an adapter (%s) was already registered." % (factory, ))
exceptions.ValueError: an adapter (twisted.internet.protocol.ProtocolToConsumerAdapter) was already registered.
Traceback (most recent call last):
  File "/usr/local/Twisted/twisted/python/usage.py", line 373, in __str__
    return self.getSynopsis() + '\n' + self.getUsage(width=None)
  File "/usr/local/Twisted/twisted/python/usage.py", line 407, in getUsage
    for (cmd, short, parser, desc) in self.subCommands:
  File "/usr/local/Twisted/twisted/application/app.py", line 364, in subCommands
    for plug in plugins:
  File "/usr/local/Twisted/twisted/plugin.py", line 186, in getPlugins
    allDropins = getCache(package)
--- <exception caught here> ---
  File "/usr/local/Twisted/twisted/plugin.py", line 151, in getCache
    provider = pluginModule.load()
  File "/usr/local/Twisted/twisted/python/modules.py", line 378, in load
    return self.pathEntry.pythonPath.moduleLoader(self.name)
  File "/usr/local/Twisted/twisted/python/modules.py", line 614, in moduleLoader
    return self._moduleLoader(modname)
  File "/usr/local/Twisted/twisted/python/reflect.py", line 361, in namedAny
    topLevelPackage = __import__(trialname)
  File "/usr/local/Twisted/twisted/plugins/twisted_lore.py", line 4, in <module>
    from twisted.lore.scripts.lore import IProcessor
  File "/usr/local/Twisted/twisted/lore/scripts/lore.py", line 8, in <module>
    from twisted.lore import process, indexer, numberer, htmlbook
  File "/usr/local/Twisted/twisted/lore/process.py", line 7, in <module>
    import tree #todo: get rid of this later
  File "/usr/local/Twisted/twisted/lore/tree.py", line 8, in <module>
    from twisted.web import microdom, domhelpers
  File "/usr/local/Twisted/twisted/web/microdom.py", line 30, in <module>
    from twisted.web.sux import XMLParser, ParseError
  File "/usr/local/Twisted/twisted/web/sux.py", line 23, in <module>
    from twisted.internet.protocol import Protocol, FileWrapper
  File "/usr/local/Twisted/twisted/internet/protocol.py", line 394, in <module>
    interfaces.IConsumer)
  File "/usr/local/Twisted/twisted/python/components.py", line 87, in registerAdapter
    raise ValueError("an adapter (%s) was already registered." % (factory, ))
exceptions.ValueError: an adapter (twisted.internet.protocol.ProtocolToConsumerAdapter) was already registered.
Usage: twistd [options]
Options:
      --savestats        save the Stats object rather than the text output of
                         the profiler.
  -o, --no_save          do not save state on shutdown
  -e, --encrypted        The specified tap/aos/xml file is encrypted.
      --nothotshot       Don't use the 'hotshot' profiler even if it's
                         available.
  -n, --nodaemon         don't daemonize
  -q, --quiet            No-op for backwards compatability.
      --originalname     Don't try to change the process name
      --syslog           Log to syslog, not to file
      --euid             Set only effective user-id rather than real user-id.
                         (This option has no effect unless the server is running
                         as root, in which case it means not to shed all
                         privileges after binding ports, retaining the option to
                         regain privileges in cases such as spawning processes.
                         Use with caution.)
  -l, --logfile=         log to a specified file, - for stdout
  -p, --profile=         Run in profile mode, dumping results to specified file
  -f, --file=            read the given .tap file [default: twistd.tap]
  -y, --python=          read an application from within a Python file (implies
                         -o)
  -x, --xml=             Read an application from a .tax file (Marmalade
                         format).
  -s, --source=          Read an application from a .tas file (AOT format).
  -d, --rundir=          Change to a supplied directory before running [default:
                         .]
      --report-profile=  E-mail address to use when reporting dynamic execution
                         profiler stats. This should not be combined with other
                         profiling options. This will only take effect if the
                         application to be run has an application name.
      --prefix=          use the given prefix when syslogging [default: twisted]
      --pidfile=         Name of the pidfile [default: twistd.pid]
      --chroot=          Chroot to a supplied directory before running
  -u, --uid=             The uid to run as.
  -g, --gid=             The gid to run as.
      --help-reactors    Display a list of possibly available reactor names.
      --version          Print version information and exit.
      --spew             Print an insanely verbose log of everything that
                         happens. Useful when debugging freezes or locks in
                         complex code.
  -b, --debug            run the application in the Python Debugger (implies
                         nodaemon), sending SIGUSR2 will drop into debugger
  -r, --reactor=         Which reactor to use (see --help-reactors for a list of
                         possibilities)
      --help             Display this help and exit.
Commands:
    web2             An HTTP/1.1 web server that can serve from a filesystem or
                     application resource.
    ftp              An FTP server.
    telnet           A simple, telnet-based remote debugging service.
    socks            A SOCKSv4 proxy service.
    manhole-old      An interactive remote debugger service.
    portforward      A simple port-forwarder.
    web              A general-purpose web server which can serve from a
                     filesystem or application resource.
    inetd            An inetd(8) replacement.
    news             A news server.
    words            A modern words server
    toc              An AIM TOC service.
    dns              A domain name server.
    mail             An email service
    manhole          An interactive remote debugger service accessible via
                     telnet and ssh and providing syntax coloring and basic line
                     editing functionality.
    conch            A Conch SSH service.

/usr/local/Twisted/bin/twistd: Unknown command: caldav


As I said above, I'm a Ubuntu novice, so any help would be appreciated.

Thanks!

Did you get any errors on the apt-get command? It has just occurred to me that my guide shows to run apt-get as a normal user and not a super user, editing that now! Try entering sudo -s before doing the apt-get

it's also important that if your installing this on ubuntu server to take special note of part 7. extended file attributes are not enabled by default on ubuntu server, and you will have to enable them yourself by manually editing the /etc/fstab file.. its in the docco if you have any difficulty

---

### Post by tegwilym on 2008-01-08
D'oh!

Yeah, the 3690 port was closed.  Opened that up and I got a little farther.   :-)

Thanks!

tom

---

### Post by timeshifter on 2008-01-08
> **cammj said:**
> Did you get any errors on the apt-get command? It has just occurred to me that my guide shows to run apt-get as a normal user and not a super user, editing that now! Try entering sudo -s before doing the apt-get

it's also important that if your installing this on ubuntu server to take special note of part 7. extended file attributes are not enabled by default on ubuntu server, and you will have to enable them yourself by manually editing the /etc/fstab file.. its in the docco if you have any difficulty

Yeah, I ran into the permissions issue with apt-get, and did it as super user and it worked fine.

Here's what /etc/fstab looks like after I edited it.  Not being very familiar with adding something to the options, I guessed at where it should go.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b7df3f48-2873-41d0-9241-c445af32f5d8 /               ext3    defaults,errors=remount-ro,user_xattr 0       1
# /dev/sda5
UUID=c2d2554e-aca0-458e-9f1a-2581d1c68ecc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

Thanks for the help!

---

### Post by tegwilym on 2008-01-08
So I seem to be missing python-kerberos.  Tred a few apt-get and synapitc searches, but couldn't find that for installing. 

Still not working.  I had high hopes for the Leopard iCal server, but seems that linux is better, but still doesn't work.  

- calendar challenged
Tom

---

### Post by timeshifter on 2008-01-08
Because I had the time, I did a clean reinstall of 7.10 [server], followed the instructions on the blog, and ended up with the exact same issue as above.

Unless I've done step 7 incorrectly, there must be something else going on.

---

### Post by techn-o-tronic on 2008-01-09
> **timeshifter said:**
> Because I had the time, I did a clean reinstall of 7.10 [server], followed the instructions on the blog, and ended up with the exact same issue as above.

Unless I've done step 7 incorrectly, there must be something else going on.

I've had the same issue (same configuration). After installing the packages mentioned in [http://blog.jl42.de/index.php?/archives/231-Installation-of-the-Apple-Calendar-Server-on-Ubuntu-Edgy.html](http://blog.jl42.de/index.php?/archives/231-Installation-of-the-Apple-Calendar-Server-on-Ubuntu-Edgy.html) it worked for me.

Edit: You may also need "apt-get install patch" which is not included in the standard 7.10 server install.

Martin.

---

### Post by timeshifter on 2008-01-09
> **techn-o-tronic said:**
> I've had the same issue (same configuration). After installing the packages mentioned in [http://blog.jl42.de/index.php?/archives/231-Installation-of-the-Apple-Calendar-Server-on-Ubuntu-Edgy.html](http://blog.jl42.de/index.php?/archives/231-Installation-of-the-Apple-Calendar-Server-on-Ubuntu-Edgy.html) it worked for me.

Edit: You may also need "apt-get install patch" which is not included in the standard 7.10 server install.

Martin.

Hey, thanks for the tip Martin.  I had already done "apt-get install patch."  I did go through and install packages (with the exception of "build-essentials" because it couldn't find it) in the link you provided. Unfortunately, the only improvement is I no longer get the error "/usr/local/CalendarServer/run: line 463: type: krb5-config: not found" which I'm assuming was due to installing libkrb5-dev.  I did notice in the other instructions the source is checked out from a different location.  Maybe that's the issue?  Anyway, thanks again for the help.

---

### Post by timeshifter on 2008-01-09
A quick reply to myself.  The other web site lists the package as "build-essentials" when it's "build-essential", no "s".  After finding that mistake, installing build-essential, and trying to start the calender server again, the same problem still exists.

---

### Post by timeshifter on 2008-01-09
Well, I guess the 3rd, 4th, 5th, time is the charm.   I finally got it running.

Once again, I started with a fresh install of 7.10 server.  After doing apt-get update, and assigning a static IP address, I installed the combined list of packages from these two installation instructions.

[http://blog.jl42.de/index.php?/archives/231-Installation-of-the-Apple-Calendar-Server-on-Ubuntu-Edgy.html](http://blog.jl42.de/index.php?/archives/231-Installation-of-the-Apple-Calendar-Server-on-Ubuntu-Edgy.html)  "build-essential" no "s"

[http://cam.moobox.org/blog/?p=5](http://cam.moobox.org/blog/?p=5)

Then I followed the steps in the first blog ([http://blog.jl42.de/index.php?/archives/231-Installation-of-the-Apple-Calendar-Server-on-Ubuntu-Edgy.html](http://blog.jl42.de/index.php?/archives/231-Installation-of-the-Apple-Calendar-Server-on-Ubuntu-Edgy.html)).  After doing "cp conf/caldavd-test.plist conf/caldavd-dev.plist" I edited caldavd-dev.plist and changed the loopback IP address to the assigned IP address.  ./run, and the server started right up.

Hope this helps anyone that might be struggling with this.

Thanks!

---

### Post by tegwilym on 2008-01-09
I'm ready to go to the 36th floor roof, walk to the edge and toss the server over the edge.  So much for Apple's server being easy to set up.  Bleah!

I couldn't get Cam's thing working, but I'll try again on another machine.  Maybe I had something screwed up?  Thanks for the links, I'll play some more.

Tom
- iCal server victim.

---

### Post by bodybybuddha on 2008-01-09
Following Cam's directions to the letter, I was not able to get the server up and running.  After some playing around with the installation process, I was able to do a fresh install with modified instructions and got the server up!

I used a VM running Gusty Gibbon to do all this work.  The VM is located on a VMWare Server on another machine in the house.  The VM was loaded and fully patched with the latest updates for all default packages before attempting Cam's installation process.

The minor change was to apt-get all the required packages one at a time - in the order that Cam has listed.  Zope3 attempted to install a lot of the required python modules by itself.  Instead of just trusting the Zope3 installation, I went ahead and continued to add all the require packages one at a time.  Each Python package, that was already 'installed' by Zope3, came back with 'modified'/updated content.  I'm assuming that if you didn't already have the Python modules already installed from previous experiments and this was the first time you attempted to get these packages, they may have been installed incorrectly.  

After completing the list, I went back and attempted to reload Zope3, and it came back that I was running the latest.  

Hope this was helpful!
JT

---

### Post by cammj on 2008-01-10
Thanks guys for all of the feedback. The tutorial was done as written on 7.04, so I think something may have changed in the packages in the 7.10 release.

I'm wondering what the extra packages were that you have to install?

Fyi: the first time you run "./run -s" it will attempt to check out some source, so make sure that you are actually able to load something over the net to do this!

---

### Post by timeshifter on 2008-01-10
> **cammj said:**
> Thanks guys for all of the feedback. The tutorial was done as written on 7.04, so I think something may have changed in the packages in the 7.10 release.

I'm wondering what the extra packages were that you have to install?

Fyi: the first time you run "./run -s" it will attempt to check out some source, so make sure that you are actually able to load something over the net to do this!

Hey Cam, thanks again for the guide.

Yeah, something must have changed in 7.10.  As you know, I meticulously went through your guide, without success, and with a fresh install, also went through the other guide without success.  It was only after I installed the packages from both guides did things start to come together.  Which package(s) actually made the difference, I don't know.  libkrb5-dev from the other guide appears to have made this error go away (/usr/local/CalendarServer/run: line 463: type: krb5-config: not found).  But, that shouldn't have prevented the server from starting.

Other than that, the main differences in the steps of the two guides, are when the change to /etc/fstab is made, the location for retrieving the source, and running "/usr/local/CalendarServer/run -s" vs changing directories to CalendarServer and running "./run -s"

---

### Post by tegwilym on 2008-01-10
Tried a fresh install of 7.04, updated it, and followed guided exactly.  First problem that showed up was that it couldn't find python-kerberos again, then couldn't find "Command 'gcc' failed with exit status 1" after running the 
 /usr/local/CalendarServer/run

I'm unplugging this and heading up to the roof on the 36ths floor!

All I want is to set up an iCal server for Mozilla Sunbird/Lightning to run inside the company.  Apple Leopard failed me, now Ubuntu.  

I'm totally frustrated.  I got my MythTV set up easier than this!

Grumble grumble grumble......

Tom

---

### Post by onno-itmaze on 2008-01-11
After much hair pulling post #13 from timeshifter made it all come together. All in one place it looked like this, note that for me the fstab edit was the crucial step. (Done for me on gutsy, ubuntu-jeos, that is a vmware guest install)

**Note that this just makes it run, we haven't done any configuration, haven't confirmed we can actually use it, that it won't fill up your hard disk or kill kittens.**

Add universe to your sources:
```
vi /etc/apt/sources.list
apt-get update
```

Install stuff:
```
apt-get install python2.4-dev libkrb5-dev attr subversion curl build-essential libssl-dev python-pysqlite2 bzip2
```

Install more stuff:
```
apt-get install curl zope3 python-xml python-pyopenssl python-dateutil python-xattr python-pysqlite2 python-twisted python-vobject python-kerberos
```

Update fstab (mine says: UUID=b3f3f4bb-98cd-47b4-9830-f9e7061a81b6 opt       ext3    defaults,user_xattr        0       1):
```
vi /etc/fstab
```

Remount it:
```
umount /opt ; mount -a
```

Now setup the tree:
```
mkdir /opt/iCalServer
```

Get stuff:
```
cd /opt/iCalServer
svn checkout [http://svn.macosforge.org/repository/calendarserver/CalendarServer/trunk](http://svn.macosforge.org/repository/calendarserver/CalendarServer/trunk) CalendarServer
cd CalendarServer
./run -s
cp conf/caldavd-test.plist conf/caldavd-dev.plist
```

Modify the bind address to empty so you can get to it from outside:
```
vi conf/caldavd-dev.plist
```

Run the thing:
```
./run
```

---

### Post by tegwilym on 2008-01-11
Thanks for sharing that!  I'll try your method and see if I can get something running.....the door to the 36th floor roof was locked, so the server lived to see another day!  hehe!

:)

Tom

---

### Post by tegwilym on 2008-01-11
> **onno-itmaze said:**
> A
Install stuff:

Install more stuff:
```
apt-get install curl zope3 python-xml python-pyopenssl python-dateutil python-xattr python-pysqlite2 python-twisted python-vobject python-kerberos
```


Again, I get stuck on things not found.  Can't apt-get the following: 
python-dateutil
python-xattr
python-kerberos
python-vobject

The other parts installed ok, or where already the latest version.  Where the heck do I get these other missing things from??  
Tom

---

### Post by onno-itmaze on 2008-01-11
You need to add universe to your sources. I've updated the HowTo here to reflect that: [https://wiki.ubuntu.com/CalendarServer](https://wiki.ubuntu.com/CalendarServer)

---

### Post by tegwilym on 2008-01-14
> **onno-itmaze said:**
> You need to add universe to your sources. I've updated the HowTo here to reflect that: [https://wiki.ubuntu.com/CalendarServer](https://wiki.ubuntu.com/CalendarServer)

I did get all the parts installed when I tried it in order, and one at a time, but still getting a bunch of strange things happening and see the word "error" showing up when I get down to the 'run' part.

Tom

---

### Post by onno-itmaze on 2008-01-14
The only time I saw errors during the creation of the HowTo was when I had not applied the user_xattr attributes correctly to the /etc/fstab and the subsequent remount didn't actually succeed in adding the attribute.

Also, the link to [Maxime Macker's troubleshooting tips]("http://www.nabble.com/Re:-'Run'-script-crashes-p11433982.html") has some things you might like to test.

---

### Post by tegwilym on 2008-01-14
I've gone back to this one again to see if I can figure it out better this time.  [http://tinyurl.com/yqdf75](http://tinyurl.com/yqdf75)
I'm able to get things published with this one, but the subscribe thing is totally confusing me.  How do I get the file on another computer and read it?  
I guess that gets more into functionality than setup, so that's a whole different forum...


Tom

---

### Post by onno-itmaze on 2008-01-14
You do understand that WebDAV and CalDAV are two different things. The HowTo and this thread are describing CalDAV by using Apple's iCal server and the URL you showed us is WebDav.

In a nut-shell, CalDAV is for coordinating calendars between people, WebDAV is for publishing files, which can be used to publish a calendar file.

---

### Post by tegwilym on 2008-01-14
Yeah, I know.  Just tying to find something that works!

---

### Post by Apfelmaennchen on 2008-02-28
Hi there!

I also have a hard time getting this thing running:

For some reason I don't understand, my outgoing svn connections time out.
(Which doesn't make any sense to me, since iptables aren't blocking anything - I even threw an explicit ACCEPT in - and the netpolicy of our campus allows all outgoing traffic...)](*,)

EDIT: Maybe, this ^^ is the time to tell that I'm a Mac guy most of the day, so don't hesitate to post the most obvious reason for this strange behaviour, it might well be the thing I missed.
Another thing that may be noteworthy:
I've put the whole stuff into $HOMEDIR/iCalServer/ and ran the whole business with normal user privileges
(call me paranoid, if you wish, but I prefer playing it safe)
END_EDIT

Anyway, I've downloaded "twisted" as well as "vobject" (which has an external reference that is accessed via svn) to another machine and put it into place.

Running "run -s" seemed to go quite fine, but as soon as I'm trying to fire the server up, I get ugly ugly tracebacks and finally the messace that "twisted" wouldn't now the caldav command.

Any suggestions?

Thanks in advance,
Apfellmaennchen

P.S.:
Running ./run -s -i SOME_PATH didn't help either:
It looked very promising at first glance but then again twisted complained aboit not knowing the caldav command.

UPDATE:
I've re-retried the whole procedure but skipped the initial "run -s" and went directly into "run -s -I $MY_TESTBED"
Some during the resultung procedure, her are the lines of output that were a little .. dunno

<snip1>
pydirector-1.0.0/setup.py
pydirector-1.0.0/PKG-INFO

Applying patches to PyDirector in $HOMEDIR/iCalServer/pydirector-1.0.0...
$HOMEDIR/iCalServer/CalendarServer/lib-patches/PyDirector/pydirector.pdamp.patch
find: patch: No such file or directory
$HOMEDIR/iCalServer/CalendarServer/lib-patches/PyDirector/pydirector.pdnetworktwisted.patch
find: patch: No such file or directory
$HOMEDIR/iCalServer/CalendarServer/lib-patches/PyDirector/pydirector.pdmain.patch
find: patch: No such file or directory
$HOMEDIR/iCalServer/CalendarServer/lib-patches/PyDirector/pydirector.pdconf.patch
find: patch: No such file or directory
$HOMEDIR/iCalServer/CalendarServer/lib-patches/PyDirector/setup.patch
find: patch: No such file or directory

Removing build directory $HOMEDIR/iCalServer/pydirector-1.0.0/build...
Removing pyc files from $HOMEDIR/iCalServer/pydirector-1.0.0...
</snip1>
<snip2>
creating build/lib/twisted
creating build/lib/twisted/plugins
copying twisted/plugins/caldav.py -> build/lib/twisted/plugins
package init file 'twisted/__init__.py' not found (or not a regular file)
running build_scripts
creating build/scripts-2.5
</snip2>

---

### Post by leetcharmer on 2008-06-16
This is where I error out when doing ./run -s

```
make[2]: Entering directory `/opt/iCalServer/libevent-1.4.4-stable'
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I./compat     -m64 -c -o event.lo event.c
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I./compat -m64 -c event.c  -fPIC -DPIC -o .libs/event.o
In file included from /usr/include/features.h:354,
                 from /usr/include/sys/types.h:27,
                 from event.c:36:
/usr/include/gnu/stubs.h:9:27: error: gnu/stubs-64.h: No such file or directory
make[2]: *** [event.lo] Error 1
make[2]: Leaving directory `/opt/iCalServer/libevent-1.4.4-stable'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/iCalServer/libevent-1.4.4-stable'
make: *** [all] Error 2
```

I'm not sure what to do, please help.

---

### Post by sunstriker on 2008-06-16
I've the same error, some googling brought me to this.
[http://www.mail-archive.com/debian-glibc@lists.debian.org/msg36983.html](http://www.mail-archive.com/debian-glibc@lists.debian.org/msg36983.html)
I'm trying to install this 64 bit package right now...

---

### Post by sunstriker on 2008-06-16
That did the trick, but: new error -> /usr/bin/ld: cannot find -lgcc

Anyone?

---

### Post by sunstriker on 2008-06-16
You have to install gcc-3.4 and point gcc in /usr/bin/gcc to this. Next on the error list:
cannot run C compiled programs...
Anyone?

---

### Post by mathieubill on 2008-06-17
Hi there,

I followed the howto step by step in order to compile and run CalendarServer on my ubuntu 8.04 server version but I had many problems with the 64 bits architecture.

I had to compile and install libevents by hands then I copied the lib files into /usr/lib

I had also to modify the CalendarServer/run script in order to replace the -m64 option by -m32 in order to compile memcached correctly.
This was difficult to solve because the run script wants to compile its own memcached even if you download and compile your memcached by hands.

I then managed to run the server but I have a python error:
[caldav-8010]  [-]   File "/usr/local/Twisted/twisted/web2/static.py", line 203, in __init__
[caldav-8010]  [-]     if isinstance(path, FilePath):
[caldav-8010]  [-] NameError: global name 'FilePath' is not defined

I don't know where this error comes from.

When I try to connect to the caldav server with my iCal client, i can't connect:
Account information not found

And the server log says:

[pydir] 17/06/2008 17:12:14 marking host ('127.0.0.1', 8009) down ([Failure instance: Traceback (failure with no frames): <class 'twisted.internet.error.ConnectionRefusedError'>: Connection was refused by other side: 111: Connection refused.
[pydir] ])
[pydir] 17/06/2008 17:12:14 retrying with ('127.0.0.1', 8010)
[pydir] 17/06/2008 17:12:14 marking host ('127.0.0.1', 8010) down ([Failure instance: Traceback (failure with no frames): <class 'twisted.internet.error.ConnectionRefusedError'>: Connection was refused by other side: 111: Connection refused.
[pydir] ])
[pydir] 17/06/2008 17:12:14 no working servers, manager -> aggressive
[pydir] 17/06/2008 17:12:24 re-adding ('127.0.0.1', 8009) automatically
[pydir] 17/06/2008 17:12:24 re-adding ('127.0.0.1', 8010) automatically

Do you have any hint?

Thanks in advance,

---

### Post by mathieubill on 2008-06-18
Hello all,

I finally managed to get rid of the python error by editing the following python script:

```

sudo vi /usr/local/Twisted/twisted/web2/static.py

```

and adding the following line at the top of the file :

```
from twisted.python.filepath import FilePath
```

I can now connect to the calendar server via a web browser both with [http://localhost:8008](http://localhost:8008) and [https://localhost:8444](https://localhost:8444)

But I cannot connect to the calendar server via iCal. I've got the error:
Account information not found
equest for [http://myserver:8008/principals/users/admin/admin](http://myserver:8008/principals/users/admin/admin) failed.

The server responded with
"HTTP/1.1 500 Internal Server Error"

On the server, the logs say:
[AMP,client] [twistedcaldav.directory.sudo.SudoDirectoryService#info] Directory service <SudoDirectoryService 'Test Realm': FilePath('/usr/local/CalendarServer/conf/sudoers.plist')> has no GUID; generating service GUID from realm name.
[caldav-8009]  [AMP,client] Starting factory <twistedcaldav.memcachepool.MemCacheClientFactory object at 0x8ac76cc>
[caldav-8009]  [AMP,client] [twistedcaldav.directory.xmlfile.XMLDirectoryService#info] Directory service <XMLDirectoryService 'Test Realm': FilePath('/usr/local/CalendarServer/conf/accounts-test.xml')> has no GUID; generating service GUID from realm name.
[caldav-8009]  [AMP,client] Unhandled error in Deferred:
[caldav-8009]  [AMP,client] Unhandled Error
[caldav-8009] 	Traceback (most recent call last):
[caldav-8009] 	  File "/usr/local/Twisted/twisted/internet/defer.py", line 182, in addCallbacks

Any ideas?

Thanks in advance for your help.

---

### Post by mathieubill on 2008-06-21
Hi again,

I finally managed to connect to my Calendar Server on linux from iCal.

I did not entirely solved the problem of the GUID but I found a workaround:
In the accounts-test.xml file, I put my linux user login of the local server files for user AND group and it works.
It seems that it works also if there is no group indicated.

I don't know if we can play directly with the extended attributes xattr of the files like sudoers.xml or users descriptions and how they are related to the DCS server.

I haven't tried neither to create groups and to play with. This will be the next step.

It seems also that the kerberos authentication does not work. As I can connect to my DCS with https, it is not that crucial.

---

### Post by JeremyLaurenson on 2008-06-24
I am getting errors on using run - I am hoping its not because I am running a GUI-less Ubuntu server:

/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I./compat     -m64 -c -o strlcpy.lo strlcpy.c
 gcc -DHAVE_CONFIG_H -I. -I./compat -m64 -c strlcpy.c  -fPIC -DPIC -o .libs/strlcpy.o
 gcc -DHAVE_CONFIG_H -I. -I./compat -m64 -c strlcpy.c -o strlcpy.o >/dev/null 2>&1
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I./compat     -m64 -c -o select.lo select.c
 gcc -DHAVE_CONFIG_H -I. -I./compat -m64 -c select.c  -fPIC -DPIC -o .libs/select.o
/tmp/ccAmRpf6.s: Assembler messages:
/tmp/ccAmRpf6.s:152: Error: Incorrect register `%rcx' used with `l' suffix
/tmp/ccAmRpf6.s:176: Error: Incorrect register `%rcx' used with `l' suffix
/tmp/ccAmRpf6.s:509: Error: Incorrect register `%rax' used with `l' suffix
/tmp/ccAmRpf6.s:539: Error: Incorrect register `%rax' used with `l' suffix
/tmp/ccAmRpf6.s:609: Error: Incorrect register `%rax' used with `l' suffix
/tmp/ccAmRpf6.s:638: Error: Incorrect register `%rax' used with `l' suffix
make[2]: *** [select.lo] Error 1
make[2]: Leaving directory `/opt/caldavd/libevent-1.4.4-stable'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/caldavd/libevent-1.4.4-stable'
make: *** [all] Error 2



Any ideas?

---

