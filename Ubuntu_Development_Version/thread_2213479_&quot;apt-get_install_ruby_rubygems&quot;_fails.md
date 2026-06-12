---
title: "&quot;apt-get install ruby rubygems&quot; fails"
date: 2014-03-26
forum: Ubuntu Development Version
---

### Post by dankegel on 2014-03-26
Looks like ruby is halfway through switching default from 1.8 to 1.9;
ruby is 1.9, but rubygems is 1.8.

This is in a freshly created lxc container.  

$ apt-cache policy ruby rubygems
ruby:
  Installed: (none)
  Candidate: 1:1.9.3.4
  Version table:
     1:1.9.3.4 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
rubygems:
  Installed: 1.8.24-1ubuntu2
  Candidate: 1.8.24-1ubuntu2
  Version table:
 *** 1.8.24-1ubuntu2 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/universe amd64 Packages
        100 /var/lib/dpkg/status

Caused me a few hiccups.  Looking forward to this being resolved.
Hoping I just forgot to do 'apt-get upgrade' in the lxc container, or something.

---

### Post by TheFu on 2014-03-26
If you are programming ruby and/or rails - use rbenv or rvm to manage everything about the ruby environment. DO NOT TRUST the OS versions.

---

### Post by dankegel on 2014-03-27
This is an OS forum, this thread is about fixing OS versions.

So the issue is that rubygems is 1.8 only.  As [https://launchpad.net/ubuntu/trusty/i386/rubygems/1.8.24-1ubuntu2](https://launchpad.net/ubuntu/trusty/i386/rubygems/1.8.24-1ubuntu2) says,
 "In Ruby 1.9.X, Rubygems is provided with the interpreter".

At the moment, rubygems1.8 is a transitional package that depends on the package rubygems.
Given that Trusty is moving to 1.9 by default, that should be flipped; the real package
should be rubygems1.8, and rubygems should become a transitional package that does nothing.

---

### Post by dankegel on 2014-03-27
I think the following dependency lines would let my private app's source package build and work across the range ubuntu 10.04-14.04:

 libopenssl-ruby | dash,
 ruby (>= 1:1.9.3.4) | rubygems,
 ruby-dev,

I'll post back here if that's not a good enough workaround.

---

