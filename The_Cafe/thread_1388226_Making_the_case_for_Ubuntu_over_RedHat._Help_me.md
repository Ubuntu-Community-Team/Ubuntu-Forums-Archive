---
title: "Making the case for Ubuntu over RedHat. Help me?"
date: 2010-01-22
forum: The Cafe
---

### Post by briwood on 2010-01-22
Hello,

I've been asked to submit a document to the the technical powers that be at) the (educational institution that I work at) stating why they should let me install Ubuntu as opposed to their standard Red Hat Enterprise offering. I'm using these Ubuntu VMs to run a Drupal hosting service.

Please let me know if you have any edits, additions, or comments about accuracy:

# In the Drupal community there is wide adoption of Ubuntu and Debian.  Scripts and utilities provided by this community are easily leveraged if we use Ubuntu.
# We favor apt over rpm for package mangement. We depend on the ability to control upgrades of discrete packages with  the "pin" feature. We are also using the Python "smart" library to apply security upgrades.
# We will be using Aegir ([http://groups.drupal.org/aegir-hosting-system](http://groups.drupal.org/aegir-hosting-system)) which is moving towards a packaging system based on Apt (Debian/Ubuntu) and not RPM (RedHat/CentOS).
# RedHat does not have a great history of keeping their php packages up to date.  In the past RedHat users have had to resort to non-offical 3rd part RPM repositories to get the latest version of PHP.
# RedHat/CentOS packaged PHP suffered from a timezone bug in 2008-9.  Manual package installs were required to fix this. Since I am not allowed to even *browse* the RHN as a non licensed user, I can't determine if this has been resolved.
# Ubuntu doesn't maintain separate os versions the way RedHat does.  You can get everything for free. 
# Canonical's commerical support offerings are strong.  We have been using their Landscape service for OS upgrades and we are very happy with it. 
# Because it is free community support for Ubuntu is incredibly strong. Lots of friendly help available.  We believe that RedHat cannot compete in terms of community.
# We use Ubuntu “Long Term Support” releases, with a commitment by Canonical to maintain security releases for 5 years on designated versions
# We feel Ubuntu has a superior upgrade path when a version reaches end-of-life
# Ubuntu offers a great balance between cutting-edge versions of new software, with a commitment to stability.

---

### Post by bodhi.zazen on 2010-01-22
It is difficult to claim one version of Linux is superior to another. You make both good and bad points.

I believe it is a matter of preference and you would not go wrong with Centos.

---

### Post by stmiller on 2010-01-22
Here are some of my thoughts:

Redhat does not support upgrades from version to version. Each new number release is a clean install which could be a pain.

Redhat does not have many packages. Overall Ubuntu or Debian have many more packages in the 'official' supported channels. I think the number is around 20,000.

The only reason IMO to go with redhat is if you have a commercial app that 'requires' redhat for license or support reasons. Even then I would rather choose CentOS over redhat which does not have the channel and package restrictions.

---

