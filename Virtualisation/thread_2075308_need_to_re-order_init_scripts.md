---
title: "need to re-order init scripts"
date: 2012-10-23
forum: Virtualisation
---

### Post by Skaperen on 2012-10-23
I need to re-order init scripts, particularly so that some of my own will run before certain others.  What documentation should I be looking at for thorough information on how that is done (aside from the effects of the changes).

This is in a cloud environment using the cloud-images tree, with cloud-init in the mix.  Things I want to do **include**:

[LIST]
[*]set the host name before most things start
[*]configure ntpd.conf before NTP starts (is based on which instance it is)
[*]re-arrange the file tree layout before most things start
[/LIST]
MAYBE it would be sufficient to do a local init script BEFORE all others.  Is there a simple (and maybe sanctioned) way to do that?

I'm running into issues **like** Postgresql is NOT shutting down because the mount points are re-arranged such that its current directory is no longer available (don't focus on Postgresql ... this is only an example ... programs starting too soon is the general problem).

I'm looking for the "how to do this" documentation first.  If you are inclined to tell me all about how to do this, it might be better to write a wiki page for that.

---

### Post by Lars Noodén on 2012-10-23
You'll want to look around for tips on using [update-rc.d](http://manpages.ubuntu.com/manpages/precise/en/man8/update-rc.d.8.html)  It's not hard once you get the idea.

---

### Post by Lars Noodén on 2012-10-23
If you're talking about upstart scripts, then you can look at [stanzas](http://upstart.ubuntu.com/wiki/Stanzas) to control when a service starts or stops.

---

### Post by Skaperen on 2012-10-23
> **Lars Noodén said:**
> If you're talking about upstart scripts, then you can look at [stanzas]("http://upstart.ubuntu.com/wiki/Stanzas") to control when a service starts or stops.
I'm talking about being able to do things like make MY script run BEFORE, or another one run AFTER, a specific service or group of services.  I may need to have one of mine run BEFORE everything else, too.  And it needs to be able to specify before or after cloud-init particularly.  I'm hoping I will not need to modify any existing system or package script.  The rc.local script (apparently last) just doesn't cut it.

One important thing I need to do is set up my own mount point arrangement that will vary according to aspects of the environment.  For example one arrangement will be used if it is an instance of the micro type with no instance storage.  Also, in some cases it will have to wait (possibly for a very long time) for a particular volume to be attached before it finishes (because it is critical to its purpose and other services, such as a database, may need to be using it).  In other cases it may be downloading files from another instance to populate special configurations.  This will all be integrated into a custom AMI based on the Ubuntu cloud-image tree (so I don't have to use a zillion different AMIs for all the variety of purposes).

I will have a look at these links and see what might fulfill my needs.  Thanks.

---

### Post by Lars Noodén on 2012-10-23
rc.local does get run last.

There is also a little more detail in the Upstart Cookbook:
[http://upstart.ubuntu.com/cookbook/](http://upstart.ubuntu.com/cookbook/)

but not much more detail.  (See 5.1.1.9)  In some ways the System V scripts were easier to place, naming the symlink 00-99 for the relative timing.

I saw a page yesterday that would have answered your question, but can't find it now that it is needed.  

It *is* possible to have a start or shutdown contingent on several conditions that must be met first.  The best I can do at the moment is to point to this one which does have a few examples:
[http://superuser.com/questions/133595/running-a-script-on-startup-before-x-starts-in-ubuntu-9-10](http://superuser.com/questions/133595/running-a-script-on-startup-before-x-starts-in-ubuntu-9-10)

---

### Post by Skaperen on 2012-10-24
> **Lars Noodén said:**
> rc.local does get run last.

There is also a little more detail in the Upstart Cookbook:
[http://upstart.ubuntu.com/cookbook/](http://upstart.ubuntu.com/cookbook/)

but not much more detail.  (See 5.1.1.9)  In some ways the System V scripts were easier to place, naming the symlink 00-99 for the relative timing.

I saw a page yesterday that would have answered your question, but can't find it now that it is needed.  

It *is* possible to have a start or shutdown contingent on several conditions that must be met first.  The best I can do at the moment is to point to this one which does have a few examples:
[http://superuser.com/questions/133595/running-a-script-on-startup-before-x-starts-in-ubuntu-9-10](http://superuser.com/questions/133595/running-a-script-on-startup-before-x-starts-in-ubuntu-9-10)

I will check these out.  Thanks.

I got the impression Ubuntu was moving ahead to convert as much as possible to upstart.  That could be useful for more abstractly saying what must run before or after what.  The numbered links let you have explicit control, but had issues with where some new package would place its script links which might not work well with how some sysadmin changes it.

How's that wiki book on OpenSSH going?

---

### Post by Lars Noodén on 2012-10-24
Yes, each release, there are fewer System V scripts left.  It's nearly all upstart now.  

There are still not too many advanced examples of configuring upstart yet.  I think you are partially breaking new ground.  So be sure to describe your solution when you get it.

I found that scripts are run with 'sh -e'
[https://wiki.frugalware.org/index.php/Upstart_Job_HOWTO](https://wiki.frugalware.org/index.php/Upstart_Job_HOWTO)

About the wikibook, it gets a small but steady stream of readers.  Few contributors even on the talk pages.  The writing is mostly at a pause now.  I redid the section on multiplexing a few weeks ago.

---

