---
title: "Cannot upgrade perl, system broken."
date: 2012-02-25
forum: Server Platforms
---

### Post by kahrn on 2012-02-25
Hi all,

I am having some very serious problems with my ubuntu server. Basically, I need to upgrade it as it is running Ubuntu 8.04. 

I attempt to run apt-get upgrade, and I get the following output:

```
Unpacking perl (from .../perl_5.8.8-12ubuntu0.5_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/perl_5.8.8-12ubuntu0.5_amd64.deb (--unpack):
 unable to create `./usr/lib/perl/5.8.8/auto/DB_File/autosplit.ix': Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/perl_5.8.8-12ubuntu0.5_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Does anyone have any idea on what could be causing this?

---

### Post by ian dobson on 2012-02-26
Hi,

Looks as if usr/lib/perl/5.8.8/auto/DB_File/autosplit.ix can't be written to. Maybe try uninstalling DB_File then trying again. Once the update is finished just reinstall DB_File.

Regards
Ian Dobson

---

### Post by kahrn on 2012-02-26
Unfortunately it's still pretty broken. I have also tried manually downloading the package from the repositories and installing it that way -- but that didn't work either.

```

(Reading database ... 2132 files and directories currently installed.)
Preparing to replace perl 5.8.8-12ubuntu0.5 (using perl_5.8.8-12ubuntu0.5_amd64.deb) ...
Unpacking replacement perl ...
Setting up perl (5.8.8-12ubuntu0.5) ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/update-alternatives line 3.
BEGIN failed--compilation aborted at /usr/sbin/update-alternatives line 3.
dpkg: error processing perl (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 perl

```

It seems to be quite broken. Any ideas? Is there any way I can just start a fresh? I also tried the following with no luck: 

```

cd /var/lib/dpkg/info
rm perl.*
dpkg --remove --force-remove-reinstreq perl

```

Any help is greatly appreciated. Thanks.

---

### Post by ian dobson on 2012-02-26
Hi,

OK perl is totally screwed. Uninstall it (with -force option if necessary)

Sorry, I don't have access to a ubuntu box so I'm going from memory.

Regards
Ian Dobson

---

### Post by kahrn on 2012-02-28
I have removed it.

However, it leaves me with a broken package manager still. For instance, when trying to install update-manager-core:

```
After this operation, 66.7MB of additional disk space will be used.
Do you want to continue [Y/n]? 
debconf: Perl may be unconfigured (Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at (eval 1) line 2.
BEGIN failed--compilation aborted at (eval 1) line 2.
) -- aborting
(Reading database ... 700 files and directories currently installed.)
Unpacking coreutils (from .../coreutils_6.10-3ubuntu2_amd64.deb) ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/dpkg-divert line 3.
BEGIN failed--compilation aborted at /usr/sbin/dpkg-divert line 3.
dpkg: error processing /var/cache/apt/archives/coreutils_6.10-3ubuntu2_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/coreutils_6.10-3ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So it would seem perl is required for the package manager to work? Also, I have tried to replace strict.pm manually by using the one from my Archlinux desktop -- but that does not work either. Wondering if I should try and manually replace it from a version of Ubuntu.. 

I just can't figure out why it isn't possible to completely remove perl and then reinstall it.

---

### Post by drmrgd on 2012-02-28
I have seen another person with a similar problem (down to the inability to locate strict.pm).  I'm not sure there's a way around installing Perl manually from source.  We tried a few things with no luck as it seems that the package manager needs Perl configured to run correctly.  At this point, since things are sort of hosed, I would recommend trying to install Perl from source to see if you can get it running.  

If anyone else has a better trick, though, I would love to know what it is.  Seems pretty bad that one needs Perl to install Perl :D

---

