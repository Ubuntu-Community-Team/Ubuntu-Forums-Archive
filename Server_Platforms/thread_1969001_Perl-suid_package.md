---
title: "Perl-suid package"
date: 2012-04-29
forum: Server Platforms
---

### Post by Yammyguy on 2012-04-29
Hello all,

Trying to install OpenWebMail on my server (ubuntu 12.04 Precise) - I have all the Perl pre requisites installed EXCEPT for perl-suid!!! running apt-get install perl-suid returns 

"E: Package 'perl-suid' has no installation candidate"

I've manually downloaded all versions of the package - the latest being:
```
perl-suid_5.10.1-17ubuntu4_i386.deb
```when I try to manually run using dpkg -i I get an error stating the versions of perl installed are too new and there are dependency problems as package libper15.10 is not installed.

Any help with this would be greatly appreciated!

Thank you in advance!
Chris.

---

### Post by Yammyguy on 2012-04-30
Bump...

Anyone???

---

### Post by ian dobson on 2012-04-30
Hi,

Maybe try using cpan (perl package manager) to install the package:-

cpan
install Unix::SetUser

Note: This is untested.

Regards
Ian Dobson

---

### Post by Yammyguy on 2012-04-30
> **ian dobson said:**
> Hi,

Maybe try using cpan (perl package manager) to install the package:-

cpan
install Unix::SetUser

Note: This is untested.

Regards
Ian Dobson

Thanks for the suggestion, but no dice.  I've run through cpan and wen I try installing OWM - still getting the error missing perl-suid package...

I don't understand why perl-suid isn't working.  it should be an installable package, no?

---

### Post by ian dobson on 2012-05-01
Hi,

Looking abit further it looks as if perl-suid has been removed from perl [http://perldoc.perl.org/perl5120delta.html#Deprecations](http://perldoc.perl.org/perl5120delta.html#Deprecations)
 
Maybe just wait abit until OpenWebMail gets fixed to not require it.

Regards
Ian Dobson

---

