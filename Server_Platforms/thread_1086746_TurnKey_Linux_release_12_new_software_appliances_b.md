---
title: "TurnKey Linux release 12 new software appliances based on Ubuntu 8.04.2 LTS"
date: 2009-03-04
forum: Server Platforms
---

### Post by lirazsiri on 2009-03-04
Hi guys,

We just finished updating the site for our most exciting and ambitious batch of releases yet. The 2009.02 release, based on Ubuntu 8.04.2 LTS, includes 12 new software appliance images and features extensive improvements to usability, security and stability.  We've done a terrific amount of quality assurance on our end and blocked the release until we had resolved every single bug and issue we found.

Highlights:

[LIST]

[*] New appliances since last announcement: Ruby on Rails, Mediawiki,
  Drupal6, LAPP stack, Django stack, MySQL, PostgreSQL, TurnKey Core
  (102MB) and Bootstrap (67MB)

    [http://www.turnkeylinux.org/appliances](http://www.turnkeylinux.org/appliances)

[*] Rebuilt all appliances on top of TurnKey Core, the new common base for
  all software appliances, which is assembled from Ubuntu 8.04.2 LTS
  packages.

[*] Security enhancements: SSL support out of the box, regenerating
  crypographic keys at installation time, database password setting
  during installation.

[*] Usability improvements: phpMyAdmin included in all LAMP based
  appliances, also included many generically useful webmin modules and
  improved embedded documentation, configuration console support for
  systems with multiple NICs, and password-free login in live CD/demo
  mode.

[*] Many bugfixes including one that fixes a potential breakage to the
  daily auto-updates mechanism.

[/LIST]

Full details:

[http://www.turnkeylinux.org/news/good-news-everyone](http://www.turnkeylinux.org/news/good-news-everyone)

Link to blueprints for this release:

 [https://blueprints.launchpad.net/turnkeylinux/2009.02-hardy-x86](https://blueprints.launchpad.net/turnkeylinux/2009.02-hardy-x86)

We got this far thanks to everyone in the Ubuntu community who tried out the previous crop of beta appliances, especially those who gave us feedback and encouragement on the forums. Part of the
what's great about starting out small is that we've been able to  keep up
with all comments and questions and personally respond to every single one of them, even in the middle of a development cycle.

**What is a software appliance? (AKA virtual appliance)**

A virtual software appliance is a self contained system combining an application with just enough operating system to run on real hardware or a virtual machine (e.g., VMWare, VirtualBox, Xen HVM, KVM).

Manual installation and configuration of a server solution can be
painful and time consuming, especially for users lacking technical proficiency.

Some users find that using a pre-integrated software appliance is an easier way to get up and running quickly, especially in combination with virtual machine software.

A software appliance allows users to altogether skip manual installation of the desired application components and required dependencies, and instead deploy a self-contained, ready-to-use system that requires little to no setup.

For further details see 
[What is a virtual software appliance?]("http://www.turnkeylinux.org/what-is-a-software-appliance")

Cheers,
Liraz

---

