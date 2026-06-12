---
title: "samba4 pam_winbind"
date: 2013-04-10
forum: Server Platforms
---

### Post by hashi825 on 2013-04-10
Hey all,

Ive recently set up a test lab with a samba 4 pdc.
Its all up and running and Ive set up winbind to allow authentication of domain users on the box itself.

Problem is I am trying to restrict to only allow logons to members of a particular group.

My smb.conf has obey pam restrictions = yes in the global section.
My pam.d/common-auth file for the winbind auth is set up as follows:

auth sufficient pam_winbind.so require_membership_of=[SID]

Now if I put an incorrect SID in there, the authentication will fail because it doesnt exist and I cant login, which means obey restrictions in smb.conf is working.

If I put the correct SID, it will resolve and allow logins.
The catch is that it will allow any domain login regardless of if you are a member of that group or not.


Ive done my googling and found that there are a few people experiencing that the membership gets ignored.

Is this is a known issue or is there any way around it? 

Thanks

---

