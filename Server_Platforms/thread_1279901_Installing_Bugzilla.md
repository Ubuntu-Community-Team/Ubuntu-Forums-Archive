---
title: "Installing Bugzilla"
date: 2009-10-01
forum: Server Platforms
---

### Post by TUOggy on 2009-10-01
I'm not sure if this is the right forum to use...  hopefully it is.

I am trying to install Bugzilla for our local intranet.  I have tried to use the Bugzilla package in the default repositories, but (1)it doesn't work, and (2)I want the installation to be in our local web directory rather than just using a symlink.

I have started installing the Perl modules, and it keeps hanging on the following:

```

Warning (usually harmless): 'YAML' not installed, will not store persistent state

  CPAN.pm: Going to build T/TU/TURNSTEP/DBD-Pg-2.15.1.tar.gz

Configuring DBD::Pg 2.15.1
Path to pg_config? Path to pg_config?

```

I have read on other forums that this can be skipped, so I'll just press enter to pass it up, but when I do, I get the following:

```

Use of uninitialized value $ENV{"POSTGRES_HOME"} in concatenation (.) or string at Makefile.PL line 99, <STDIN> line 2.
Use of uninitialized value $ENV{"POSTGRES_HOME"} in concatenation (.) or string at Makefile.PL line 101, <STDIN> line 2.
PostgreSQL version: 0 (default port: 0)
POSTGRES_HOME: (not set)
POSTGRES_INCLUDE: /include
POSTGRES_LIB: /lib
OS: linux
The value of POSTGRES_INCLUDE points to a non-existent directory: /include
Cannot build unless the directories exist, exiting.
Warning (usually harmless): 'YAML' not installed, will not store persistent state
  TURNSTEP/DBD-Pg-2.15.1.tar.gz
  /usr/bin/perl Makefile.PL INSTALLDIRS=site LIB="/home/admin3/web/bugzilla/lib" INSTALLMAN1DIR="/home/admin3/web/bugzilla/lib/man/man1" INSTALLMAN3DIR="/home/admin3/web/bugzilla/lib/man/man3" INSTALLBIN="/home/admin3/web/bugzilla/lib/bin" INSTALLSCRIPT="/home/admin3/web/bugzilla/lib/bin" INSTALLDIRS=perl -- NO Makefile created
Skipping test because of notest pragma
Running make install
  Make had some problems, won't install
Could not read '/home/admin3/web/bugzilla/lib/.cpan/build/DBD-Pg-2.15.1-X82zGj/META.yml'. Falling back to other methods to determine prerequisites

```

The strangest thing is that it looks like it is trying to use PostGRE SQL.  We are running MySQL.

When navigating to the website, I get the following messages:

```

Software error:

Can't locate List/MoreUtils.pm in @INC (@INC contains: . lib/i486-linux-gnu-thread-multi lib /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl) at /usr/local/share/perl/5.10.0/DateTime/Locale/Base.pm line 8.
BEGIN failed--compilation aborted at /usr/local/share/perl/5.10.0/DateTime/Locale/Base.pm line 8.
Compilation failed in require at /usr/local/share/perl/5.10.0/DateTime/Locale.pm line 10.
BEGIN failed--compilation aborted at /usr/local/share/perl/5.10.0/DateTime/Locale.pm line 10.
Compilation failed in require at lib/i486-linux-gnu-thread-multi/DateTime.pm line 46.
BEGIN failed--compilation aborted at lib/i486-linux-gnu-thread-multi/DateTime.pm line 46.
Compilation failed in require at Bugzilla/Util.pm line 53.
BEGIN failed--compilation aborted at Bugzilla/Util.pm line 53.
Compilation failed in require at Bugzilla/Hook.pm line 26.
BEGIN failed--compilation aborted at Bugzilla/Hook.pm line 26.
Compilation failed in require at Bugzilla/Config.pm line 37.
BEGIN failed--compilation aborted at Bugzilla/Config.pm line 37.
Compilation failed in require at Bugzilla.pm line 38.
BEGIN failed--compilation aborted at Bugzilla.pm line 38.
Compilation failed in require at /home/admin3/web/bugzilla/index.cgi line 34.
BEGIN failed--compilation aborted at /home/admin3/web/bugzilla/index.cgi line 34.

For help, please send mail to the webmaster (webmaster@localhost), giving this error message and the time and date of the error. 

```
*Obviously, it's not going to work since the install didn't complete.  I'm just including this for more info in case it can tell someone anything...

What do I need to do to get this installed and working?  I need to get this moving so I can migrate from a Windows server.

---

### Post by TUOggy on 2009-10-01
Okay, I tried to run ./checksetup.pl again to see what happens, and this is what I get:

```

* This is Bugzilla 3.4.2 on perl 5.10.0
* Running on Linux 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009

Checking perl modules...
Checking for              CGI.pm (v3.33)   ok: found v3.42
Checking for          Digest-SHA (any)     ok: found v5.45
Checking for            TimeDate (v2.21)   ok: found v2.22
Checking for            DateTime (v0.28)   ok: found v0.50
Checking for   DateTime-TimeZone (v0.71)   ok: found v0.98
Checking for                 DBI (v1.41)   ok: found v1.607
Checking for    Template-Toolkit (v2.22)   ok: found v2.22
Checking for          Email-Send (v2.00)   ok: found v2.198
Checking for          Email-MIME (v1.861)  ok: found v1.861
Checking for Email-MIME-Encodings (v1.313)  ok: found v1.313
Checking for Email-MIME-Modifier (v1.442)  ok: found v1.442
Checking for                 URI (any)     ok: found v1.37

Checking available perl DBD modules...
Checking for              DBD-Pg (v1.45)    not found
Checking for           DBD-mysql (v4.00)   ok: found v4.008
Checking for          DBD-Oracle (v1.19)    not found

The following Perl modules are optional:
Checking for                  GD (v1.20)   ok: found v2.39
Checking for               Chart (v1.0)    ok: found v2.4.1
Checking for         Template-GD (any)     ok: found v1.56
Checking for          GDTextUtil (any)     ok: found v0.86
Checking for             GDGraph (any)     ok: found v1.44
Checking for            XML-Twig (any)     ok: found v3.32
Checking for          MIME-tools (v5.406)  ok: found v5.427
Checking for         libwww-perl (any)     ok: found v5.819
Checking for         PatchReader (v0.9.4)  ok: found v0.9.5
Checking for          PerlMagick (any)     ok: found v6.4.5
Checking for           perl-ldap (any)     ok: found v0.39
Checking for         Authen-SASL (any)     ok: found v2.13
Checking for          RadiusPerl (any)     ok: found v0.14
Checking for           SOAP-Lite (v0.710.06) ok: found v0.710.08
Checking for         HTML-Parser (v3.40)   ok: found v3.59
Checking for       HTML-Scrubber (any)     ok: found v0.08
Checking for Email-MIME-Attachment-Stripper (any)     ok: found v1.316
Checking for         Email-Reply (any)     ok: found v1.202
Checking for         TheSchwartz (any)      not found
Checking for      Daemon-Generic (any)     ok: found v0.61
Checking for            mod_perl (v1.999022) ok: found v2.000004
***********************************************************************
* OPTIONAL MODULES                                                    *
***********************************************************************
* Certain Perl modules are not required by Bugzilla, but by           *
* installing the latest version you gain access to additional         *
* features.                                                           *
*                                                                     *
* The optional modules you do not have installed are listed below,    *
* with the name of the feature they enable. Below that table are the  *
* commands to install each module.                                    *
***********************************************************************
* MODULE NAME * ENABLES FEATURE(S)                                    *
***********************************************************************
* TheSchwartz * Mail Queueing                                         *
***********************************************************************
COMMANDS TO INSTALL OPTIONAL MODULES:

    TheSchwartz: /usr/bin/perl install-module.pl TheSchwartz


To attempt an automatic install of every required and optional module
with one command, do:

  /usr/bin/perl install-module.pl --all

Attempt to reload DateTime.pm aborted.
Compilation failed in require at Bugzilla/Util.pm line 53, <DATA> line 275.
BEGIN failed--compilation aborted at Bugzilla/Util.pm line 53, <DATA> line 275.
Compilation failed in require at Bugzilla/Hook.pm line 26, <DATA> line 275.
BEGIN failed--compilation aborted at Bugzilla/Hook.pm line 26, <DATA> line 275.
Compilation failed in require at Bugzilla/Config.pm line 37, <DATA> line 275.
BEGIN failed--compilation aborted at Bugzilla/Config.pm line 37, <DATA> line 275.
Compilation failed in require at Bugzilla.pm line 38, <DATA> line 275.
BEGIN failed--compilation aborted at Bugzilla.pm line 38, <DATA> line 275.
Compilation failed in require at ./checksetup.pl line 98, <DATA> line 275.

```

I tried to install TheSchwartz and it tells me that it is up to date (I know that this isn't a requirement for installation, so a big issue).

---

### Post by TUOggy on 2009-10-02
anyone have any idea about what's going on?

---

### Post by TUOggy on 2009-10-05
anyone have any ideas why this isn't installing?

---

### Post by TUOggy on 2009-10-12
Okay, so I had to scour the web because it seems like nobody had any idea about what was going on...

The actual issue had nothing to do with Postgres, or the Postgres module.

The real problem was that List::MoreUtils was missing.  I don't know if Bugzilla is supposed to check for this, or if this is something that I should have installed anyway, but I kept getting the weird TimeDate::Locale error.

I tried and tried to reinstall the TimeDate::Locale module, but it kept telling me that I had the most recent.

If you are getting this strange error, then try the following command:

```

/usr/bin/perl install-module.pl List::MoreUtils

```

Hope this helps someone else =)

---

### Post by ceagan on 2009-11-24
I had a similar error, but I had to install DateTime::Locale

```
# perl install-module.pl DateTime::Locale
```

---

### Post by arcanus on 2009-12-07
> **ceagan said:**
> I had a similar error, but I had to install DateTime::Locale

```
# perl install-module.pl DateTime::Locale
```

This saved me hours on the google! Thanks a bunch!

-- arcanus

---

### Post by mlissner on 2009-12-17
Hmmm...no dice here.

---

### Post by arcanus on 2010-05-03
Had this again when trying to upgrade to bugzilla 3.6.

Had to install the DateTime module aswell as the DateTime::Locale plugin.

If someone still has this error, reinstalling DateTime might solve the issue. I had to remove the cached DateTime modules prior to the install though (was located in /root/.cpan/build)

---

### Post by Queue29 on 2010-05-03
If it's not critical to use BugZilla, I recommend [Mantis]("http://www.mantisbt.org/"). It's infinitely easier to set up and use.

---

### Post by skumar1 on 2010-05-21
Hello All,

I was getting below error message while trying to upgrade Bugzilla 3.4.3 to Bugzilla 3.6 :

**[B]Software error:Can't locate DateTime/Locale.pm in @INC (@INC  contains: . lib/i486-linux-gnu-thread-multi lib /etc/perl  /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5  /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl)  at lib/DateTime.pm line 41.BEGIN failed--compilation aborted at lib/DateTime.pm  line 41.Compilation failed in require at Bugzilla/Util.pm line 53.BEGIN  failed--compilation aborted at Bugzilla/Util.pm line 53.Compilation failed in  require at Bugzilla/Error.pm line 33.BEGIN failed--compilation aborted at  Bugzilla/Error.pm line 33.Compilation failed in require at  Bugzilla/Install/Filesystem.pm line 31.BEGIN failed--compilation aborted at  Bugzilla/Install/Filesystem.pm line 31.Compilation failed in require at  Bugzilla/Config.pm line 38.BEGIN failed--compilation aborted at  Bugzilla/Config.pm line 38.Compilation failed in require at Bugzilla.pm line  38.BEGIN failed--compilation aborted at Bugzilla.pm line 38.Compilation failed  in require at /var/www/bugzilla-3.4.3/index.cgi line 34.BEGIN  failed--compilation aborted at /var/www/bugzilla-3.4.3/index.cgi line 34.For  help, please send mail to the webmaster (webmaster@localhost), giving this error  message and the time and date of the error.**[/B]


**Thanks for your post. I had installed all required perl module but  getting the same erroe message. Then I installed two perl module by running commands ****[B]: **[/B] 
[FONT=Arial][SIZE=2][FONT=Times New Roman][SIZE=3]                           : /usr/bin/perl install-module.pl  List::MoreUtils[/SIZE][/FONT][/SIZE][/FONT]
                            : /usr/bin/perl  install-module.pl DateTime::Locale

It is working fine now. Please accept my warm thanks for posting such a nice message.

Regards
Shailesh

---

### Post by paultag on 2010-06-01
> **TUOggy said:**
> Okay, so I had to scour the web because it seems like nobody had any idea about what was going on...

The actual issue had nothing to do with Postgres, or the Postgres module.

The real problem was that List::MoreUtils was missing.  I don't know if Bugzilla is supposed to check for this, or if this is something that I should have installed anyway, but I kept getting the weird TimeDate::Locale error.

I tried and tried to reinstall the TimeDate::Locale module, but it kept telling me that I had the most recent.

If you are getting this strange error, then try the following command:

```

/usr/bin/perl install-module.pl List::MoreUtils

```

Hope this helps someone else =)

TUOggy, I owe ya a beer!

Thanks mate!

---

### Post by ppgengler on 2011-07-12
> **skumar1 said:**
> Hello All,

I was getting below error message while trying to upgrade Bugzilla 3.4.3 to Bugzilla 3.6 :

**[B]Software error:Can't locate DateTime/Locale.pm in @INC (@INC  contains: . lib/i486-linux-gnu-thread-multi lib /etc/perl  /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5  /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl)  at lib/DateTime.pm line 41.BEGIN failed--compilation aborted at lib/DateTime.pm  line 41.Compilation failed in require at Bugzilla/Util.pm line 53.BEGIN  failed--compilation aborted at Bugzilla/Util.pm line 53.Compilation failed in  require at Bugzilla/Error.pm line 33.BEGIN failed--compilation aborted at  Bugzilla/Error.pm line 33.Compilation failed in require at  Bugzilla/Install/Filesystem.pm line 31.BEGIN failed--compilation aborted at  Bugzilla/Install/Filesystem.pm line 31.Compilation failed in require at  Bugzilla/Config.pm line 38.BEGIN failed--compilation aborted at  Bugzilla/Config.pm line 38.Compilation failed in require at Bugzilla.pm line  38.BEGIN failed--compilation aborted at Bugzilla.pm line 38.Compilation failed  in require at /var/www/bugzilla-3.4.3/index.cgi line 34.BEGIN  failed--compilation aborted at /var/www/bugzilla-3.4.3/index.cgi line 34.For  help, please send mail to the webmaster (webmaster@localhost), giving this error  message and the time and date of the error.**[/B]


**Thanks for your post. I had installed all required perl module but  getting the same erroe message. Then I installed two perl module by running commands ****[B]: **[/B] 
[FONT=Arial][SIZE=2][FONT=Times New Roman][SIZE=3]                           : /usr/bin/perl install-module.pl  List::MoreUtils[/SIZE][/FONT][/SIZE][/FONT]
                            : /usr/bin/perl  install-module.pl DateTime::Locale

It is working fine now. Please accept my warm thanks for posting such a nice message.

Regards
Shailesh

I know this is an older thread, but I had this issue and none of the solutions solved it.  While I was looking around I saw someone mention that it wanted the headers, which led me to the solution that fixed it for me:

```
sudo apt-get install libpq-dev
```

To install the postgresql development headers.  After that it worked.  I had already installed the List::MoreUtils and DateTime::Locale so I'm not really sure if they were necessary or not, but I know they didn't fix it alone.

Hopefully this helps someone in the future wandering through this thread.

Thanks,
\Peter

---

