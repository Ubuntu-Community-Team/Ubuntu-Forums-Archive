---
title: "OpenDirectory Authentication for Dummies"
date: 2008-05-03
forum: Server Platforms
---

### Post by LegoAddict on 2008-05-03
Ok, so I'm a student responsible for testing Edubuntu on my school's PCs.  They use a mixed OS infrastructure, right now consisting of Macs and Windows XP PCs.

They use Apple's OpenDirectory to authenticate people on to the school's system.  I have no clue how to get this to work on Ubuntu.

I don't know anything about servers.  I'm pretty good with administrative functions in Ubuntu, but I've never gone this far.  I need a for dummies guide.

If all goes well, my school will go from a Windows/Mac system to Edubuntu/Mac

---

### Post by TroyDowling on 2008-05-12
Kudos on the project man. I'm a high-school student from a town near Vancouver, BC Canada trying to do the same thing. Long story short, I'm sick and tired of our slow, locked down, useless, slow, XP, slow computer network. Recently, I took an online course and met a teacher with a similar view. Now, we have a meeting with the Minister of Education in a few weeks to propose this plan, and I'm still trying to get Edubuntu to work correctly among the PCs in my basement. I don't know if this is out of place, but someone should write/link to a solid, easy to follow rollout guide for setting up a lab environment with LTSP and Edubuntu. I'm having a hard time grasping the concept on my own.

EDIT:

I'm setting this up on Hardy because it's an LTS distro. I've so far installed Ubuntu 8.04, then the Edubuntu suite on top of that. I'm starting work on the LTSP boot tomorrow at school; I'll SSH back home.

---

### Post by songshu on 2008-05-12
i'm sort of in the same boat, 

as far as i know apple open directory is a combination of Open LDAP and Kerberos.

it should be compatible, normally, but since i'm doing the same thing i found that there are improvements made to set up the client authentication since gutsy, altough it does not seem to work yet as it should i guess and not really well documented yet. altough these links should get you somewhere.

[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer) [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication) [http://ubuntuforums.org/showthread.php?t=597056](http://ubuntuforums.org/showthread.php?t=597056) 

ldap-auth-client is the thing to look for i think in Hardy.

i'm pretty well known with linux and bsd in general but LDAP is something new for me as well.

there is a working set up described in my signature, altough i still get some small errors and so far its LDAP only without Kerberos but it might give you an idea to look for.

besides the links above i could not find much more dummy guides, so i decided to basically write my own, if any idea's on your side i would love to hear as well offcourse

---

### Post by LegoAddict on 2008-05-15
Thanks for the replies.  I'll run it past my teacher.

@Troy nice.  I wish Ontario would implement Edubuntu.  When I'm not in North Africa I live in eastern Ontario where my summer job was assembling Windows PCs for the school district.

You can follow the progress at acstedubuntu.wordpress.com , which is the blog that my teacher is having me do on the project.

This computer they gave me is really old and slow, but it's working like a charm.  All systems have been operational without any fiddling.  I'm very impressed.

---

