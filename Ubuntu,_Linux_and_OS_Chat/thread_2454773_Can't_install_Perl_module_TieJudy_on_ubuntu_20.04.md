---
title: "Can't install Perl module Tie::Judy on ubuntu 20.04"
date: 2020-12-05
forum: Ubuntu, Linux and OS Chat
---

### Post by perlmaster56 on 2020-12-05
I was able to install a judy package on my ubuntu 20.04 witrh "sudo apt-get"

Now when I try to install the Perl module Tie::Judy using the "cpan" command the installation fails. A few tests failed due to ot returning the expected results.

#   Failed test at t/Tie-Judy.t line 292.
#     Structures begin differing at:
#          $got->[0][1] = ARRAY(0x55a6f91e43f0)
#     $expected->[0][1] = '4'

#   Failed test at t/Tie-Judy.t line 297.
#     Structures begin differing at:
#          $got->[0][1] = ARRAY(0x55a6f91e3d60)
#     $expected->[0][1] = '4'

#   Failed test at t/Tie-Judy.t line 302.
#     Structures begin differing at:
#          $got->[0][0] = '5'
#     $expected->[0][0] = 'food'
# Looks like you failed 3 tests of 140.
t/Tie-Judy.t .. Dubious, test returned 3 (wstat 768, 0x300)
Failed 3/140 subtests



Has anyone been able to install Tie::Judy  ?

---

### Post by TheFu on 2020-12-05
cpan has been deprecated for cpanminus for years. 

But if you don't want too do perl programming, then look for the ubuntu packaged version via apt.
```
sudo apt search judy
```
That doesn't return anything useful related to perl. Looks like you'll need to use **sudo cpanm Tie::Judy** after setting up cpanm. To  do that, you'll probably want to switch to using **perlbrew** to manage your own perl environment separate from the OS perl.

[LIST=1]
[*]Install perlbrew.
[*]Using perlbrew, install the version of perl you desire. 10-20 versions are allowed. Tell perlbrew to use that version.  
[*]Using perlbrew, install cpanm, then 
[*]cpanm Tie::Judy
[/LIST]

Now setup maintenance for the perl version and updating all the cpan modules for that specific perl version.

Perlbrew keeps our custom perl separate from the OS perl. This is the best practice for custom perl, ruby, python, php, etc.

That's how I would do it given that there isn't a pre-built deb package for this.

---

