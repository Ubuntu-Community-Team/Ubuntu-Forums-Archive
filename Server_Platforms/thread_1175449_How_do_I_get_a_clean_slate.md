---
title: "How do I get a clean slate?"
date: 2009-06-01
forum: Server Platforms
---

### Post by dugald on 2009-06-01
Hi all,

I have managed to screw up my Apache / mod_mono configuration and I fairly sure that if I can start from scratch I could get it working correctly.  The hosting firm I use charge quite a bit for this - is there any way I can do it myself?  

I basically need to remove all traces of apache and mono (including all the config files) and start again.  I am using 9.04.

---

### Post by LepeKaname on 2009-06-01
Use for example:

sudo aptitude purge apache2 mono

This will erase also the config files... and then install them again.

---

### Post by dugald on 2009-06-01
Thanks for the reply LepeKaname.  I tried purging every mono or apache related package and installing them again, but my problems continue.  Perhaps they are a bug.  Basically I get lots of these entries in my apache error log:
> 
Cannot open assembly '/usr/lib/mono/2.0/mod-mono-server2.exe': No such file or directory.

I am using the default mod_mono.conf file with the ASP.NET libraries enabled:

> Include /etc/mono-server/mono-server-hosts.conf

So why is it looking for mod-mono-server2.exe?  I did a system wide grep for "mod-mono-server2.exe" but it returned nothing.  I am really stuck!

If I DO install the "mono-apache-server2" package I get this in the apache log:

> [Mon Jun 01 13:25:46 2009] [notice] Apache/2.2.11 (Ubuntu) mod_mono/2.0 PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Mon Jun 01 13:25:46 2009] [warn] long lost child came home! (pid 23926)
[Mon Jun 01 13:25:46 2009] [warn] long lost child came home! (pid 23927)
[Mon Jun 01 13:25:46 2009] [warn] long lost child came home! (pid 23929)

** (/usr/lib/mono/2.0/mod-mono-server2.exe:23928): WARNING **: The class System.Collections.IEqualityComparer could not be loaded, used in mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089

** (/usr/lib/mono/2.0/mod-mono-server2.exe:23928): WARNING **: Missing method System.String::IsNullOrEmpty(string) in assembly /usr/lib/mono/1.0/mscorlib.dll, referenced in assembly /usr/lib/mono/gac/System.Configuration/2.0.0.0__b03f5f7f11d50a3a/System.Configuration.dll

** (/usr/lib/mono/2.0/mod-mono-server2.exe:23928): WARNING **: exception inside UnhandledException handler: Cannot access a class member.

Help!

EDIT:  if I change mod_mono.conf to use the ASP>NET 2.0 libraries everything works.  However, I want to use 1.1 and I should be able to do this by editing mod_mono.conf??  It seems like it is set on using mod-mono-server2.exe instead of mod_mono-server.exe... why?

---

### Post by directhex on 2009-06-01
> **dugald said:**
> Thanks for the reply LepeKaname.  I tried purging every mono or apache related package and installing them again, but my problems continue.  Perhaps they are a bug.  Basically I get lots of these entries in my apache error log:


I am using the default mod_mono.conf file with the ASP.NET libraries enabled:



So why is it looking for mod-mono-server2.exe?  I did a system wide grep for "mod-mono-server2.exe" but it returned nothing.  I am really stuck!

If I DO install the "mono-apache-server2" package I get this in the apache log:



Help!

Bizarre - you seem to be mixing 1.0 and 2.0 somehow

---

### Post by Iowan on 2009-06-01
> **dugald said:**
> I basically need to remove all traces of apache and mono (including all the config files) and start again.  I am using 9.04.**fdisk** is pretty effective. :twisted:
Seriously, now. There's a section in [this]("https://help.ubuntu.com/community/ApacheMySQLPHP") help page for removing LAMP stack.  I'm curious how an .exe file got into a Linux install. :confused:

---

### Post by directhex on 2009-06-01
> **Iowan said:**
> **fdisk** is pretty effective. :twisted:
Seriously, now. There's a section in [this]("https://help.ubuntu.com/community/ApacheMySQLPHP") help page for removing LAMP stack.  I'm curious how an .exe file got into a Linux install. :confused:

.exe is the normal ending for CLI assemblies, e.g. /usr/lib/f-spot/f-spot.exe

---

### Post by directhex on 2009-06-01
> **dugald said:**
> EDIT:  if I change mod_mono.conf to use the ASP>NET 2.0 libraries everything works.  However, I want to use 1.1 and I should be able to do this by editing mod_mono.conf??  It seems like it is set on using mod-mono-server2.exe instead of mod_mono-server.exe... why?

For ASP.NET 2.0, install the packages: mono-apache-server2, mono-xsp2-base, libapache2-mod-mono
For ASP.NET 1.1, install the packages: mono-apache-server, mono-xsp-base, libapache2-mod-mono

To switch between which to serve, do as it says in /etc/apache2/mods-available/mod_mono.conf, namely:
```
# If want want to use ASP.NET 1.1 (via mono-apache-server), use:
# Include /etc/mono-server/mono-server-hosts.conf
#
# If you want to use ASP.NET 2.0 (via mono-apache-server2), use:
# Include /etc/mono-server2/mono-server2-hosts.conf
```

---

### Post by dugald on 2009-06-02
Thanks for the replies - this is what I have tried:
```
apt-get purge apache2 mysql-server libapache2-mod-mono mono-common
```

Then I made sure that /etc/apache2 had been removed.  Then I remove the /tmp folders.

The first time I got this:

```
Failed to attach to existing dashboard, and removing dashboard file (etc) 
```

So after purging again I did a restart and then installed.  I also removed all files from /var/www

Howver, even before touching the fresh configuration, when apache starts it looks for /usr/lib/mono/2.0/mod-mono-server2.exe.

---

### Post by dugald on 2009-06-02
I just reimaged my server with a fresh install of Jaunty.

I installed mysql, apache2 and mono, started apache and then checked the logs.

```
Cannot open assembly '/usr/lib/mono/2.0/mod-mono-server2.exe': No such file or directory.

```

If this is happening from a completely fresh install does that mean that it is a bug in Ubuntu?

---

### Post by directhex on 2009-06-02
> **dugald said:**
> I just reimaged my server with a fresh install of Jaunty.

I installed mysql, apache2 and mono, started apache and then checked the logs.

```
Cannot open assembly '/usr/lib/mono/2.0/mod-mono-server2.exe': No such file or directory.

```

If this is happening from a completely fresh install does that mean that it is a bug in Ubuntu?

That depends on whether you followed the instructions in my post

---

### Post by dugald on 2009-06-03
The only way I could fix this in the end was by removing the ubuntu mono packages and compiling libgdiplus, mono, xsp and mod_mono (2.4) from source.  It is working as expected now.

EDIT:  That didn't fix it.  Turns out it was still running in 2.0 mode.  The culprit was actually /usr/local/bin/mod-mono-server.exe as it references the mod-mono-server2.exe.  You will see another file in /usr/local/bin/ called mod-mono-server1.exe.  If you copy its contents into mod-mono-server.exe that fixes it.  Not a very elegant solution but it works.  I can now run 1.1 mode.

If using the normal ubuntu mono packages the file needing changed is /usr/bin/mod-mono-server and I edited mine to look like this:
> #!/bin/sh
exec /usr/bin/mono $MONO_OPTIONS "/usr/lib/mono/1.0/mod-mono-server.exe" "$@"

---

