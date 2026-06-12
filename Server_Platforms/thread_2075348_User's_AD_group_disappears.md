---
title: "User's AD group disappears"
date: 2012-10-23
forum: Server Platforms
---

### Post by ifrisbie on 2012-10-23
I have Active Directory setup on my 11.10 system and everything seemed to work just fine initially.  Originally I had local accounts setup and one group that multiple users were tied to.  Once I connected it to the AD, to aid the access process I used usermod to add the local group to the AD users.

The problem is this, some of the user accounts (which were all configured the same) are no longer part of the group as far as the "groups <user>" command is concerned and the file system is concerned.  When I run groups <user> command it lists some of the basic AD groups (built-in ones), and the local one I added, but no long shows the active directory group I'm dealing with.  When I run the getent groups I see that all of my 5 users that were originally part of the group are still listed.

So "getent groups" and "groups <user>" do not agree.  Rebooting the linux server doesn't work and I'm not in an administrative position to reboot the AD server (although I'm not sure what difference that would make).

Does anyone have any idea under what circumstances these two commands might not agree and why that one particular group seems to be dropped as far as ubuntu is concerned (for file access).

---

### Post by ifrisbie on 2012-10-24
The wbinfo -g command  properly indicates the AD domain group I am interested in and shows a  particular user in that group - this is always true, so on the linux  side it seems to have the proper information.
  However - the "groups" command will initially show the user being  part of the group in question, but some time after having logged in that  user - the membership to the group goes away in the "groups" command  (but remains in the wbinfo -g).
  I say erratic because I'm not confident yet that it is somehow timing  out versus a result of something.  I've chased down 3 things so far  that I thought may have caused it, but when trying to repeat I couldn't  see the problem - so I'm left with some kind of timeout theory.
  Anyone have any experience seeing something like this?  Are there  different rules for different group type/scopes (domain local, global,  universal)?  Does the nsswitch.conf file somehow play a part in the  translation between AD info cached, and the information that is actually  used by the file system?  Any help would be appreciated.

---

### Post by ifrisbie on 2012-10-24
To be more specific: 

wbinfo --gid-info 10009

lists 'user28' as a member


wbinfo -r user28

won't list the group id 10009, but it lists others

---

