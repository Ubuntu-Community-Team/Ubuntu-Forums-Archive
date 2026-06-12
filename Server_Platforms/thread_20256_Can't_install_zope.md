---
title: "Can't install zope"
date: 2005-03-15
forum: Server Platforms
---

### Post by sesquipedality on 2005-03-15
I'm having some problems installing Zope on a server I've upgraded to Ubuntu 4.10 from Debian stable.  Now I've installed zope without a hitch on a machine I clean installed Ubuntu on, but on the upgraded system, I'm getting the following:

$ sudo apt-get install zope
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  zope: Depends: python2.2-xml but it is not going to be installed
E: Broken packages
$ sudo apt-get install python2.2-xml
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  python2.2-xml: Depends: python2.2-xmlbase but it is not going to be installed
E: Broken packages
$ sudo apt-get install python2.2-xmlbase
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  python2.2-xmlbase: Depends: python2.2 (= 2.2.3-10) but 2.2.3-10ubuntu0.1 is to be installed
E: Broken packages
$

So it seems to be complaining because python has been ubuntified, but not all of the python packages in "universe" have.  What's the best way to get around this?  If this really is the problem, then why did the install work at all on my clean installed machine?  How do I fix this?

Thanks.

---

### Post by Myles3 on 2005-03-15
Change the package verson of python2.2, I don't remeber what to change it to, sorry.

---

### Post by sesquipedality on 2005-03-18
[QUOTE=Myles3]Change the package verson of python2.2, I don't remeber what to change it to, sorry.[/QUOTE]
I don't know how to do this.

---

