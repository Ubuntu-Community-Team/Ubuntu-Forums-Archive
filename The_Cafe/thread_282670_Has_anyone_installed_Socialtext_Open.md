---
title: "Has anyone installed Socialtext Open?"
date: 2006-10-23
forum: The Cafe
---

### Post by transistor on 2006-10-23
[Socialtext]("http://socialtext.com/") wiki seems to be getting very good reviews and there is now an "open" version of it. It's written in Perl and the install process has hundreds of questions. I think I'm going around in a loop on the install.

Has anyone intstalled this yet? (Oh, and is the Cafe the best place to ask this?)

---

### Post by petdance on 2006-10-23
Hi, I'm the programmer working on Socialtext Open, and yes, the install process does have a lot of Perl modules to install.  Fortunately, we just set up a package repository, so installing those dependencies is as simple as

```
$ sudo apt-get install st-perl-deps
```

The details are in the docs/INSTALL.apt-get document. This document is new, and is not yet in the downloadable tarball from SourceForge, but it is in Subverison.  The URL is [http://svn.sourceforge.net/viewvc/socialtext/trunk/docs/INSTALL.apt-get?view=markup](http://svn.sourceforge.net/viewvc/socialtext/trunk/docs/INSTALL.apt-get?view=markup)

We only have packages set up for Dapper at this point.

You may also be interested in our mailing lists, also hosted at SourceForge: [http://sourceforge.net/mail/?group_id=170460](http://sourceforge.net/mail/?group_id=170460)

You can also email me directly at andy.lester at socialtext.com.

Thanks,
Andy

---

### Post by .t. on 2006-10-23
Please don't recommend the use of apt-get. Use aptitude:
[http://psychocats.net/ubuntu/aptitude](http://psychocats.net/ubuntu/aptitude)

---

### Post by sud0n1m on 2006-10-25
Im taking a look at Socialtext Open as a replacement for Mediawiki on my work intranet. Unfortunately our wiki has not seen wide adoption due to the lack of a wysiwyg editor. Im doing some updating now and will post my experience getting it installed in this thread.

Update:
No mysql support and no apache 2 support killed the project for me! Hopefully I'll check back in a couple versions and it will work there. I guess either we have to be happy with Mediawiki or pay for a wiki service like socialtext or jotspot

---

### Post by transistor on 2006-10-27
Petdance: Thanks for the info. 

Andy: What's wrong with apt-get? Isn't that what Synaptic uses?

sud0n1m: (I get it!) The Perl installer mentions mySQL. It isn't clear to me what is and isn't supported. Why do you think mySQL isn't?

I'm in the same position as Sud0n1m. I have a MediaWiki on our intranet and find it invaluable for recording various bits of information as well as explanatory material. The markup language is off-putting for 95% of people.

Petdance: I reckon I need shell access to install this. That means I couldn't install on my internet host (no shell). Is that right?

Thanks, all.

---

### Post by petdance on 2006-10-30
It's not just a matter of running in a shell.  It needs some pretty intimate configging with Apache, and also to run our ceqlotron indexer job.

Socialtext is much larger and more comprehensive package than you might have been thinking.  It's well worth looking into, but it's not something you'll be able to just drop into your hosted service.

---

### Post by shining on 2006-10-30
> **.t. said:**
> Please don't recommend the use of apt-get. Use aptitude:
[http://psychocats.net/ubuntu/aptitude](http://psychocats.net/ubuntu/aptitude)

Just because aptitude is possibly slightly better doesn't mean apt-get should be avoided like the plague.

---

### Post by transistor on 2006-10-30
Thanks again, chaps. I'll hold off on SocialText then until it's a bit easier to install.

I found SocialText while I was scrouring around looking for something more friendly than MediaWiki. I suppose my basic requirements are:
[LIST]
[*]WYSIWYG to encourage participation.
[*]Proper Wiki revision history and roll-back.
[*]Non camel-case. (CamelCaseLooksAwfulInText.)
[*]Easy image upload.
[*]Easy categorisation.
[*]PHP/mySQL preferred due to its wide user base.
[/LIST]

Any ideas?

---

### Post by tareo on 2007-11-07
I would like to try socialtext but I can't install it:
with v2.15.0.1
> make
make -f build/tmp/Makefile.perl
make[1]: Entering directory `/home/tareo/Desktop/Socialtext-
Open-2.15.0.1'
make[1]: build/tmp/Makefile.perl: No such file or directory
make[1]: *** No rule to make target `build/tmp/Makefile.perl'.  Stop.
make[1]: Leaving directory `/home/tareo/Desktop/Socialtext-
Open-2.15.0.1'
make: *** [default] Error 2

with v2.11.6.1
> make install
[ ! -e /etc/dont-install-nlw-here ] || [ -e configure-stamp ]
rm -f -R /usr/share/nlw
rm -f -R /usr/local/share/perl/5.8.7/{Public,Control,Socialtext}
sudo -u postgres /usr/bin/perl dev-bin/create-db-user
Use of uninitialized value in concatenation (.) or string at dev-bin/create-db-user line 15.
Can't locate Socialtext/AppConfig.pm in @INC (@INC contains: /../lib /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at dev-bin/create-db-user line 18.
BEGIN failed--compilation aborted at dev-bin/create-db-user line 18.
make: *** [db-user] Error 2

Even if I copy
/usr/share/perl5/AppConfig.pm into @INC paths.

I have follow this tuto:
"Socialtext Open Install Guide for Ubuntu 6.06"
[http://www.eu.socialtext.net/open/index.cgi?socialtext_open_install_guide_for_ubuntu_6_06](http://www.eu.socialtext.net/open/index.cgi?socialtext_open_install_guide_for_ubuntu_6_06) 

What's wrong?
Thanks for your help.

---

### Post by tareo on 2007-11-09
here I found:
[https://repo.socialtext.net:8999/svn/socialtext/trunk/nlw/docs/INSTALL.troubleshooting](https://repo.socialtext.net:8999/svn/socialtext/trunk/nlw/docs/INSTALL.troubleshooting)

> 
== dev-bin/create-db-user can't locate Socialtext/AppConfig.pm ==

If you're doing a make install, and this happens:

    $ sudo make install
    [ ! -e /etc/dont-install-nlw-here ]
    rm -f -R /usr/share/nlw 
    rm -f -R /usr/lib/perl5/site_perl/5.8.5/{Public,Control,Socialtext}
    sudo -u postgres /usr/bin/perl dev-bin/create-db-user
    Can't locate Socialtext/AppConfig.pm in @INC (@INC contains:
    /home/andy/socialtext/dev-bin/../lib .... long list of directories ....

it's because your postgres user doesn't have read permissions to
the directory you've built Socialtext into.  Make sure that it's
world-readable.

I execute this command:
chmod -R 777 /home/tareo/Desktop/Socialtext-Open-2.15.0.1

but I have the same problem 
:(

---

### Post by tareo on 2007-11-12
no one can help me?

---

### Post by dddddd on 2008-01-29
Is it possible that socialtext open is installed on a virtual host,such as Bluehost?

---

### Post by mydatespots on 2009-03-05
I don't see any [downloadable packages]("http://sourceforge.net/project/showfiles.php?group_id=170460") for SocialText Open at sourceforge. Is it still open sourced? No mention of an open sourced version at [http://www.socialtext.com/products/](http://www.socialtext.com/products/).

**UPDATE**: [SocialText no longer plans to update the open source version]("http://www.socialtext.net/open/index.cgi?socialtext_open")

So I'll go ahead with [MojoMojo]("http://mojomojo.org"). Works great so far and I like that it's powered by Catalyst and has live preview. Better than WYSIWYG, which somehow always ends up messing up your code.

---

