---
title: "squeezeboxserver on 10.10 maverick (with mysql 5.1)"
date: 2010-11-14
forum: Server Platforms
---

### Post by surfer on 2010-11-14
did anyone get a clean install of squeezeboxserver (7.5.1) on ubuntu 10.10 - with mysql 5.1 - to work?

mine keeps crashing. the database seems to have issues which causes the squeezeboxserver do die and restart ad infinitum...

any ideas?

---

### Post by surfer on 2010-11-14
for some more detail: here are the logs of the mysql server (/var/lib/squeezeboxserver/cache/mysql-error-log.txt):

```
101114 19:48:01  InnoDB: Started; log sequence number 0 44233
101114 19:48:01 [ERROR] Can't open and lock privilege tables: Table 'mysql.servers' doesn't exist
101114 19:48:01 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.1.49-1ubuntu8.1'  socket: '/var/lib/squeezeboxserver/cache/squeezebox-mysql.sock'  port: 9092  (Ubuntu)
101114 19:51:06 [Note] /usr/sbin/mysqld: Normal shutdown

```

and the log of the squeezeboxserver (/var/log/squeezeboxserver/server.log)
```
2010-11-14 19:47:41 squeezeboxserver_safe started.
[10-11-14 19:47:50.1379] main::init (323) Starting Squeezebox Server (v7.5.1, r30836, Tue Jun  1 05:57:28 PDT 2010) perl 5.010001
[10-11-14 19:51:06.5238] Slim::Schema::Storage::throw_exception (82) Error: DBI Connection failed: DBI connect('hostname=127.0.0.1;port=9092;database=slimserver','slimserver',...) failed: Lost connection to MySQL server at 'reading initial communication packet', system error: 0 at /usr/share/squeezeboxserver/CPAN/DBIx/Class/Storage/DBI.pm line 950
[10-11-14 19:51:06.5281] Slim::Schema::Storage::throw_exception (82) Backtrace:

   frame 0: Slim::Utils::Log::logBacktrace (/usr/share/perl5/Slim/Schema/Storage.pm line 82)
   frame 1: Slim::Schema::Storage::throw_exception (/usr/share/squeezeboxserver/CPAN/DBIx/Class/Storage/DBI.pm line 972)
   frame 2: DBIx::Class::Storage::DBI::_connect (/usr/share/squeezeboxserver/CPAN/DBIx/Class/Storage/DBI.pm line 814)
   frame 3: DBIx::Class::Storage::DBI::_populate_dbh (/usr/share/squeezeboxserver/CPAN/DBIx/Class/Storage/DBI.pm line 753)
   frame 4: DBIx::Class::Storage::DBI::ensure_connected (/usr/share/perl5/Slim/Schema/Storage.pm line 41)
   frame 5: (eval) (/usr/share/perl5/Slim/Schema/Storage.pm line 41)
   frame 6: Slim::Schema::Storage::dbh (/usr/share/perl5/Slim/Schema.pm line 290)
   frame 7: Slim::Schema::_connect (/usr/share/perl5/Slim/Schema.pm line 126)
   frame 8: Slim::Schema::init (/usr/share/perl5/Slim/Music/Import.pm line 744)
   frame 9: Slim::Music::Import::_checkLibraryStatus (/usr/share/perl5/Slim/Music/Import.pm line 677)
   frame 10: Slim::Music::Import::useImporter (/usr/share/perl5/Slim/Music/MusicFolderScan.pm line 48)
   frame 11: Slim::Music::MusicFolderScan::init (/usr/share/perl5/Slim/Utils/Prefs.pm line 769)
   frame 12: Slim::Utils::Prefs::__ANON__ (/usr/share/perl5/Slim/Utils/Prefs/Base.pm line 307)
   frame 13: Slim::Utils::Prefs::Base::set (/usr/share/perl5/Slim/Web/Settings/Server/Wizard.pm line 106)
   frame 14: Slim::Web::Settings::Server::Wizard::handler (/usr/share/perl5/Slim/Web/HTTP.pm line 1118)
   frame 15: Slim::Web::HTTP::generateHTTPResponse (/usr/share/perl5/Slim/Web/HTTP.pm line 924)
   frame 16: Slim::Web::HTTP::processURL (/usr/share/perl5/Slim/Web/HTTP.pm line 735)
   frame 17: Slim::Web::HTTP::processHTTP (/usr/share/perl5/Slim/Networking/IO/Select.pm line 139)
   frame 18: (eval) (/usr/share/perl5/Slim/Networking/IO/Select.pm line 123)
   frame 19: Slim::Networking::IO::Select::__ANON__ (/usr/share/perl5/Slim/Networking/IO/Select.pm line 183)
   frame 20: (eval) (/usr/share/perl5/Slim/Networking/IO/Select.pm line 183)
   frame 21: Slim::Networking::IO::Select::loop (/usr/sbin/squeezeboxserver line 626)
   frame 22: main::idle (/usr/sbin/squeezeboxserver line 580)
   frame 23: main::main (/usr/sbin/squeezeboxserver line 1072)

[10-11-14 19:51:06.5338] Slim::Schema::Storage::dbh (53) Warning: Unable to connect to the database - trying to bring it up!
[10-11-14 19:51:06.5515] Slim::Schema::Storage::throw_exception (82) Error: DBI Connection failed: DBI connect('hostname=127.0.0.1;port=9092;database=slimserver','slimserver',...) failed: Lost connection to MySQL server at 'reading initial communication packet', system error: 0 at /usr/share/squeezeboxserver/CPAN/DBIx/Class/Storage/DBI.pm line 950
[10-11-14 19:51:06.5552] Slim::Schema::Storage::throw_exception (82) Backtrace:

   frame 0: Slim::Utils::Log::logBacktrace (/usr/share/perl5/Slim/Schema/Storage.pm line 82)
   frame 1: Slim::Schema::Storage::throw_exception (/usr/share/squeezeboxserver/CPAN/DBIx/Class/Storage/DBI.pm line 972)
   frame 2: DBIx::Class::Storage::DBI::_connect (/usr/share/squeezeboxserver/CPAN/DBIx/Class/Storage/DBI.pm line 814)
   frame 3: DBIx::Class::Storage::DBI::_populate_dbh (/usr/share/squeezeboxserver/CPAN/DBIx/Class/Storage/DBI.pm line 753)
   frame 4: DBIx::Class::Storage::DBI::ensure_connected (/usr/share/perl5/Slim/Schema/Storage.pm line 59)
   frame 5: (eval) (/usr/share/perl5/Slim/Schema/Storage.pm line 59)
   frame 6: Slim::Schema::Storage::dbh (/usr/share/perl5/Slim/Schema.pm line 290)
   frame 7: Slim::Schema::_connect (/usr/share/perl5/Slim/Schema.pm line 126)
   frame 8: Slim::Schema::init (/usr/share/perl5/Slim/Music/Import.pm line 744)
   frame 9: Slim::Music::Import::_checkLibraryStatus (/usr/share/perl5/Slim/Music/Import.pm line 677)
   frame 10: Slim::Music::Import::useImporter (/usr/share/perl5/Slim/Music/MusicFolderScan.pm line 48)
   frame 11: Slim::Music::MusicFolderScan::init (/usr/share/perl5/Slim/Utils/Prefs.pm line 769)
   frame 12: Slim::Utils::Prefs::__ANON__ (/usr/share/perl5/Slim/Utils/Prefs/Base.pm line 307)
   frame 13: Slim::Utils::Prefs::Base::set (/usr/share/perl5/Slim/Web/Settings/Server/Wizard.pm line 106)
   frame 14: Slim::Web::Settings::Server::Wizard::handler (/usr/share/perl5/Slim/Web/HTTP.pm line 1118)
   frame 15: Slim::Web::HTTP::generateHTTPResponse (/usr/share/perl5/Slim/Web/HTTP.pm line 924)
   frame 16: Slim::Web::HTTP::processURL (/usr/share/perl5/Slim/Web/HTTP.pm line 735)
   frame 17: Slim::Web::HTTP::processHTTP (/usr/share/perl5/Slim/Networking/IO/Select.pm line 139)
   frame 18: (eval) (/usr/share/perl5/Slim/Networking/IO/Select.pm line 123)
   frame 19: Slim::Networking::IO::Select::__ANON__ (/usr/share/perl5/Slim/Networking/IO/Select.pm line 183)
   frame 20: (eval) (/usr/share/perl5/Slim/Networking/IO/Select.pm line 183)
   frame 21: Slim::Networking::IO::Select::loop (/usr/sbin/squeezeboxserver line 626)
   frame 22: main::idle (/usr/sbin/squeezeboxserver line 580)
   frame 23: main::main (/usr/sbin/squeezeboxserver line 1072)

[10-11-14 19:51:06.5601] Slim::Schema::Storage::dbh (62) Error: Unable to connect to the database - even tried restarting it twice!
[10-11-14 19:51:06.5621] Slim::Schema::Storage::dbh (63) Error: Check the event log for errors on Windows. Fatal. Exiting.
[10-11-14 19:51:06.5664] Slim::Schema::forceCommit (1622) Warning: Trying to commit transactions before DB is initialized!
2010-11-14 19:51:07 Squeezebox Server died. Restarting.
[10-11-14 19:51:14.0021] main::init (323) Starting Squeezebox Server (v7.5.1, r30836, Tue Jun  1 05:57:28 PDT 2010) perl 5.010001
[10-11-14 19:51:17.9827] Slim::Schema::Storage::throw_exception (82) Error: DBI Connection failed: DBI connect('hostname=127.0.0.1;port=9092;database=slimserver','slimserver',...) failed: Lost connection to MySQL server at 'reading initial communication packet', system error: 0 at /usr/share/squeezeboxserver/CPAN/DBIx/Class/Storage/DBI.pm line 950
[10-11-14 19:51:17.9859] Slim::Schema::Storage::throw_exception (82) Backtrace:

   frame 0: Slim::Utils::Log::logBacktrace (/usr/share/perl5/Slim/Schema/Storage.pm line 82)
   frame 1: Slim::Schema::Storage::throw_exception (/usr/share/squeezeboxserver/CPAN/DBIx/Class/Storage/DBI.pm line 972)
   frame 2: DBIx::Class::Storage::DBI::_connect (/usr/share/squeezeboxserver/CPAN/DBIx/Class/Storage/DBI.pm line 814)
   frame 3: DBIx::Class::Storage::DBI::_populate_dbh (/usr/share/squeezeboxserver/CPAN/DBIx/Class/Storage/DBI.pm line 753)
   frame 4: DBIx::Class::Storage::DBI::ensure_connected (/usr/share/perl5/Slim/Schema/Storage.pm line 41)
   frame 5: (eval) (/usr/share/perl5/Slim/Schema/Storage.pm line 41)
   frame 6: Slim::Schema::Storage::dbh (/usr/share/perl5/Slim/Schema.pm line 290)
   frame 7: Slim::Schema::_connect (/usr/share/perl5/Slim/Schema.pm line 126)
   frame 8: Slim::Schema::init (/usr/share/perl5/Slim/Music/Import.pm line 744)
   frame 9: Slim::Music::Import::_checkLibraryStatus (/usr/share/perl5/Slim/Music/Import.pm line 677)
   frame 10: Slim::Music::Import::useImporter (/usr/share/perl5/Slim/Music/MusicFolderScan.pm line 48)
   frame 11: Slim::Music::MusicFolderScan::init (/usr/sbin/squeezeboxserver line 435)
   frame 12: main::init (/usr/sbin/squeezeboxserver line 578)
   frame 13: main::main (/usr/sbin/squeezeboxserver line 1072)

[10-11-14 19:51:17.9900] Slim::Schema::init (129) Error: Couldn't connect to database! Fatal error: [] Exiting!
[10-11-14 19:51:17.9923] Slim::Schema::init (129) Backtrace:

   frame 0: Slim::Utils::Log::logBacktrace (/usr/share/perl5/Slim/Schema.pm line 129)
   frame 1: Slim::Schema::init (/usr/share/perl5/Slim/Music/Import.pm line 744)
   frame 2: Slim::Music::Import::_checkLibraryStatus (/usr/share/perl5/Slim/Music/Import.pm line 677)
   frame 3: Slim::Music::Import::useImporter (/usr/share/perl5/Slim/Music/MusicFolderScan.pm line 48)
   frame 4: Slim::Music::MusicFolderScan::init (/usr/sbin/squeezeboxserver line 435)
   frame 5: main::init (/usr/sbin/squeezeboxserver line 578)
   frame 6: main::main (/usr/sbin/squeezeboxserver line 1072)

[10-11-14 19:51:17.9955] Slim::Schema::forceCommit (1622) Warning: Trying to commit transactions before DB is initialized!
2010-11-14 19:51:22 Squeezebox Server died. Restarting.
2010-11-14 19:51:27 squeezeboxserver_safe stopped.
```

---

### Post by surfer on 2010-11-14
update: squeezeboxserver 7.5.1 does not seem to work with mysql 5.1.

i changed the sources.list to
```
deb http://debian.slimdevices.com/ unstable main
```
and installed the beta of squeezeboxserver 7.6.

this seems to work.

---

### Post by yumgnomeandthensome on 2011-01-21
hi
i'm running 
Version: 7.5.1 - r30836 
MySQL Version: 5.1.49-1ubuntu8.1

on 10.10

I'm having trouble allowing my update mgr to successfully grab the update.
Can anyone offer up some steps to allow me to carry this out?

---

### Post by surfer on 2011-01-21
you may try to change the sources.list entry to
```
deb http://debian-origin.slimdevices.com/  unstable main
```

and remember to install the unstable (7.6) version. the other version did not work for me...

---

