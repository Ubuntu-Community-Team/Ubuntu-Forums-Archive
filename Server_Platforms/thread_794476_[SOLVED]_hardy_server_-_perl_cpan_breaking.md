---
title: "[SOLVED] hardy server - perl cpan breaking"
date: 2008-05-14
forum: Server Platforms
---

### Post by inphektion on 2008-05-14
I have a fresh 32 hardy server install.  I want to install latest bugzilla on it.  I download, untar, run ./checksetup.pl --check-modules
then I ran: /usr/bin/perl -MCPAN -e 'install "Bundle::Bugzilla"'
and it failed and after that I install build-essential, linux-headers, etc. and ran again.

Basically when first run cpan or try to configure it by running /usr/bin/perl -MCPAN -e shell and then o conf init it steps you through a bunch of questions.  I think I typed some in wrong like PREFIX=~/ and that messed things up as then it wasn't finding stuff in @INC.  

If i rerun the config how do I clear what it remembers for the values I put in?  I tried PREFIX= and leaving blank but then it uses that which is wrong.  I need it to be unset....

Basically my perl/cpan is messed up and I want a fresh start but aptitude reinstall perl doesn't do it and it doesn't seem i can do a remove of perl without messing up the entire system.

For example here is what i get now:
```
root@havoc:/var/www/bugzilla# /usr/bin/perl -MCPAN -e 'install "GD"'
CPAN: File::HomeDir loaded ok (v0.69)
CPAN: Storable loaded ok (v2.18)
Going to read /root/.cpan/Metadata
  Database was generated on Tue, 13 May 2008 08:30:29 GMT
CPAN: YAML loaded ok (v0.66)
Going to read /root/.cpan/build/
............................................................................DONE
Found 4 old builds, restored the state of 4
Running install for module 'GD'
Running make for L/LD/LDS/GD-2.39.tar.gz
  Has already been unwrapped into directory /root/.cpan/build/GD-2.39-HPBlPm
  '/usr/bin/perl Makefile.PL PREFIX=' returned status 512, won't make
Running make test
  Make had some problems, won't test
Running make install
  Make had some problems, won't install
```

---

### Post by inphektion on 2008-05-15
got it all working... I found I could edit Config.pm directly and that is where those variables are set so I could remove PREFIX= and just make it blank.  However I was still getting Makefile.PL status 512 and to resolve that I went into the cpan shell again and did an install Bundle::CPAN which I believe is a reinstall of it.
After that it worked.

The biggest thing I realized is that on a package based system like ubuntu I don't really need to use cpan to install the bugzilla modules.  I learned this when cpan wouldn't install Charts::Base but an aptitude install of the equiv package worked fine.  My prob started when I used cpan to try to install Bundle::Bugzilla but it seems that is outdated and shouldn't be used on package based systems like ubuntu, fedora, etc.  

lesson(s) learned.

---

