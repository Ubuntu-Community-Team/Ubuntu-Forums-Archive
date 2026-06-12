---
title: "Installing Bugzilla3 via apt fails in 8.10"
date: 2008-12-03
forum: Server Platforms
---

### Post by Briga on 2008-12-03
Hi, 
I have been trying, unsuccessfully, to install bugzilla from repository. I am running it on a 8.10 ubuntu-server. Here is the dump (mind the local language in the beginning, saucy stuff is in English). 

I tried looking it up here, and in google but no luck....
```

paolo@rf-s01t:~$ sudo apt-get install bugzilla3
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso       
Lettura informazioni sullo stato... Fatto        
bugzilla3 è già alla versione più recente.
0 aggiornati, 0 installati, 0 da rimuovere e 2 non aggiornati.
1 non completamente installati o rimossi.
Dopo quest'operazione, verranno occupati 0B di spazio su disco.
Configuro bugzilla3 (3.0.4.1-2ubuntu1) ...
dbconfig-common: writing config to /etc/dbconfig-common/bugzilla3.conf
granting access to database bugzilla3 for bugzilla3@localhost: already exists.
creating database bugzilla3: already exists.
dbconfig-common: flushing administrative password
init_db_vars (, bugzilla3, bugzilla3, secret)
Creating new localconfig (localhost, bugzilla3, bugzilla3, secret)
/usr/share/bugzilla3/debian/localconfig /etc/bugzilla3/localconfig differ: byte 764, line 13
ucf --debconf-ok /etc/bugzilla3/localconfig.jHBIeZ9245 /etc/bugzilla3/localconfig
Running checksetup.pl with answer file

* This is Bugzilla 3.0.4.1-2ubuntu1 on perl 5.10.0
* Running on Linux 2.6.27-7-server #1 SMP Fri Oct 24 07:37:55 UTC 2008

Checking perl modules...
Checking for          CGI.pm (v3.33)   ok: found v3.42 
Checking for        TimeDate (v2.21)   ok: found v2.22 
Checking for             DBI (v1.41)   ok: found v1.605 
Checking for       PathTools (v0.84)   ok: found v3.2501 
Checking for Template-Toolkit (v2.12)   ok: found v2.19 
Checking for      Email-Send (v2.00)   ok: found v2.192 
Checking for Email-MIME-Modifier (any)     ok: found v1.442 

Checking available perl DBD modules...
Checking for          DBD-Pg (v1.45)    not found 
Checking for       DBD-mysql (v2.9003) ok: found v4.007 

The following Perl modules are optional:
Checking for              GD (v1.20)   ok: found v2.39 
Checking for     Template-GD (any)     ok: found v1.56 
Checking for           Chart (v1.0)    ok: found v2.4.1 
Checking for         GDGraph (any)     ok: found v1.44 
Checking for      GDTextUtil (any)     ok: found v0.86 
Checking for        XML-Twig (any)     ok: found v3.32 
Checking for      MIME-tools (v5.406)  ok: found v5.426 
Checking for     libwww-perl (any)     ok: found v5.810 
Checking for     PatchReader (v0.9.4)  ok: found v0.9.5 
Checking for      PerlMagick (any)     ok: found v6.3.7 
Checking for       perl-ldap (any)     ok: found v0.36 
Checking for       SOAP-Lite (any)     ok: found v0.710.07 
Checking for     HTML-Parser (v3.40)   ok: found v3.56 
Checking for   HTML-Scrubber (any)     ok: found v0.08 
Checking for Email-MIME-Attachment-Stripper (any)     ok: found v1.315 
Checking for     Email-Reply (any)     ok: found v1.202 
Checking for        mod_perl (v1.999022) ok: found v2.000004 
Reading /etc/bugzilla3/localconfig...

OPTIONAL NOTE: If you want to be able to use the 'difference between two
patches' feature of Bugzilla (which requires the PatchReader Perl module
as well), you should install patchutils from:

    http://cyberelk.net/tim/patchutils/

Checking for       DBD-mysql (v2.9003) ok: found v4.007 
Checking for           MySQL (v4.1.2)  ok: found v5.0.67-0ubuntu6

Creating skins/contrib directory...
Creating skins/custom directory...
Removing existing compiled templates ...
Precompiling templates...
Failed to symlink from ../../../template to /var/lib/bugzilla3/data/template/var/lib/bugzilla3: File exists at /usr/share/perl5/Bugzilla/Template.pm line 919.
Fixing file permissions...
Initializing "Dependency Tree Changes" email_setting ...

Looks like we don't have an administrator set up yet.
Either this is your first time using Bugzilla, or your
administrator's privileges might have accidentally been deleted.

stty: standard input: Invalid argument
```

I tried also remove and install with no luck too.

Anyone can point me in the right direction. 
Thanks

---

### Post by lazlohf on 2009-01-02
I don't know if this helps, but I was getting weird failures during install due to the fact that my bugzilla admin password had a single-quote character in it. Apparently the install scripts do not properly encode the user input.

---

### Post by swap_i on 2009-01-26
> **Briga said:**
> Anyone can point me in the right direction. 
Thanks

I agree with you. I'm trying now to install bugzilla. And I have same problems. I try install latest version - 3.3.1. And I can't find 4 perl libraries:
```

Checking perl modules...
Checking for              CGI.pm (v3.33)   ok: found v3.42
Checking for          Digest-SHA (any)     ok: found v5.47
Checking for            TimeDate (v2.21)   ok: found v2.22
Checking for            DateTime (v0.28)   ok: found v0.42
Checking for           PathTools (v0.84)   ok: found v3.2501
Checking for                 DBI (v1.41)   ok: found v1.605
Checking for    Template-Toolkit (v2.15)   ok: found v2.19
Checking for          Email-Send (v2.00)   ok: found v2.192
Checking for          Email-MIME (v1.861)  ok: found v1.861
Checking for Email-MIME-Modifier (v1.442)  ok: found v1.442

Checking available perl DBD modules...
Checking for              DBD-Pg (v1.45)    not found
Checking for           DBD-mysql (v4.00)   ok: found v4.007
Checking for          DBD-Oracle (v1.19)    not found

The following Perl modules are optional:
Checking for                  GD (v1.20)   ok: found v2.39
Checking for               Chart (v1.0)    ok: found v2.4.1
Checking for         Template-GD (any)     ok: found v1.56
Checking for          GDTextUtil (any)     ok: found v0.86
Checking for             GDGraph (any)     ok: found v1.44
Checking for            XML-Twig (any)     ok: found v3.32
Checking for          MIME-tools (v5.406)  ok: found v5.426
Checking for         libwww-perl (any)     ok: found v5.810
Checking for         PatchReader (v0.9.4)   not found
Checking for          PerlMagick (any)     ok: found v6.3.7
Checking for           perl-ldap (any)     ok: found v0.36
Checking for         Authen-SASL (any)     ok: found v2.12
Checking for          RadiusPerl (any)     ok: found v0.13
Checking for           SOAP-Lite (any)     ok: found v0.710.07
Checking for         HTML-Parser (v3.40)   ok: found v3.56
Checking for       HTML-Scrubber (any)     ok: found v0.08
Checking for Email-MIME-Attachment-Stripper (any)      not found
Checking for         Email-Reply (any)      not found
Checking for         TheSchwartz (any)     ok: found v1.04
Checking for      Daemon-Generic (any)      not found
Checking for            mod_perl (v1.999022) ok: found v2.000004

```
I can't find them in apt repository and I can't install them from command promt with install-modules.pl (from bugzilla manual). I have 8.10 server if it is important. Anybody can help?

---

