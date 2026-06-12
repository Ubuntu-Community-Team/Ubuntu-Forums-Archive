---
title: "Samba 3.2 conflicting default options"
date: 2009-04-04
forum: Server Platforms
---

### Post by almogaver on 2009-04-04
I am baffled by some of the options existing in the default Samba's 3.2.3 smb.conf for Ubuntu Server 8.10.

For instance ...
   obey pam restrictions = yes
   encrypt passwords = true
... according to Samba's docs for option "obey pam restrictions":
> Note that Samba always ignores PAM for authentication in the case of encrypt passwords = yes. The reason is that PAM modules cannot support the challenge/response authentication mechanism needed in the presence of SMB password encryption.
Does this mean that the second option overrides the first one?

Another instance is ...
  unix password sync = Yes
  passwd program = /usr/bin/passwd %u
  passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\
  n *password\supdated\ssuccessfully* .
  pam password change = Yes
...

According to Samba's docs for "pam password change":
> If enabled, then PAM will be used for password changes when requested by an SMB client instead of the program listed in passwd program.
So,  when enabled (as it is) the other options in this group should be removed or commented out.

I am not saying that Samba is not working with these options, it is. It is just that it is hard to explain them without contradicting yourself. I would appreciate some guidance.
What am I missing?

---

