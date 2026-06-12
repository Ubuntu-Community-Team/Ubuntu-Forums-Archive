---
title: "Centralized Authentication Service (Drupal, CAS, Apache, Tomcat, LDAP)"
date: 2009-04-30
forum: Server Platforms
---

### Post by SpenserJ on 2009-04-30
Hey everyone,

Hopefully someone in here has experienced my problem, or at least part of it. But if you have ANY advice or experience, please let me know, as I am flying blind right now

I am working at my university over the summer and they have asked me to rebuild their website from scratch.  We are running in a virtualized environment (so we can throw up a new server fairly easily) and we would like to use drupal, as it will allow the staff to easily modify content when it is convenient for them.

I have already gotten PHP, Apache, and MySQL configured properly, and everything is running Drupal 6 fine.  However, we would like to have multiple websites up (my.website, programs.website, admissions.website, etc), which is not a problem either as that is now configured.  But when it comes to setting up a single sign-on system, I am a little lost.  I have found that CAS would be a good choice, as we could also integrate our Moodle website into it, but there is very little documentation that I could find about configuring everything that we need.

I played around with a few things and have CAS running with the default authentication system, but cannot access that from Apache (Apache SHOULD pass any requests for /cas or /cas/* to tomcat, but it just sits there loading nothing).  I think I have something configured incorrectly (wouldn't surprise me as I screwed around with it a bunch now) or that some versions are incompatible, so I would definitely be fine with starting fresh.

Any assistance would be greatly appreciated.  In summary, I need PHP, Apache, MySQL, Drupal, CAS, CAS authenticating through LDAP, and possibly a few other small things.  And we can run CAS, MySQL, and the web server on different VMs too. Please let me know how to go about this!

Spenser Jones

P.S.
We are running ubuntu 8.04 right now (Although we may upgrade seeing as Jaunty is out now, this was set up last month, hence the older version)

Links:
[http://drupal.org](http://drupal.org)
[http://drupal.org/project/cas](http://drupal.org/project/cas)
[http://www.jasig.org/cas](http://www.jasig.org/cas)

---

