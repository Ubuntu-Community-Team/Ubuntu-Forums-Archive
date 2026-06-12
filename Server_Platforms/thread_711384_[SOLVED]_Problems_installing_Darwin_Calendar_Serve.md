---
title: "[SOLVED] Problems installing Darwin Calendar Server (aka iCal Server or caldavd)"
date: 2008-02-29
forum: Server Platforms
---

### Post by Apfelmaennchen on 2008-02-29
Hi there!

I've been trying to setup DCS on Ubuntu 7.10 x86_64 following the tutorial from [http://cam.moobox.org/blog/?p=5](http://cam.moobox.org/blog/?p=5) except that I'm avoiding the sudoing.

I have to apologize for kind of double posting this question (my original question is the last one in [http://ubuntuforums.org/showthread.php?t=650443](http://ubuntuforums.org/showthread.php?t=650443)) but since the last comments on that thread were older than a month I feared, no one would read it.

The first thing that "just didn't work"(tm) was that the setup script failed me with a timeout trying to fetch Twisted via svn.
As far as I can tell there's just no reason for that:
iptables are not blocking outgoing traffic neither is the netpolicy of our site.
So even if this is a total newbee-question:
Am I missing something here?
EDIT
Turned out that - although stated otherwise - our site blocked outgoing traffic (except the absolute standards) for this machine...
I kind of hate our site-admins sometimes!
END_EDIT

I've "overcome" this problem, by downloading the required revisions of Twisted and vObject onto another machine and scp'ed both directories to the place where the setup script is looking for them.

However (and this is the real problem):
When I call "./run -s -I TEST_INSTALL_DIR" almost everything seems to be fine, but trying to start caldavd results in
"/usr/bin/twistd: Unknown command: caldav"

EDIT
Turned out that "patch" was not present and the installer doesn't warn on not having this prerequisite installed...
I somehow missed the corresponding error message in between of the O(1000) lines of somewhat uninteresting output of the installer-script...
Which by the way should have just gone poof running into that error instead of continuing it's work.
END_EDIT

A

---

