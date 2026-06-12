---
title: "Account for SMB which can not be used to logon with"
date: 2021-02-10
forum: Security
---

### Post by johnfm3 on 2021-02-10
Its been a long time since I last posted a question here.  But here is a new one.

I am building a new PLEX media server for my house, and I need to be upload content such as pictures to the server via single SMB share.
What I am looking for is a user account that I can only use to authenticate with when connecting to SMB server share.

SSH, console, and GUI access should be denied.

My only thought on this would be to create a Security Group and make it a member of what ever SG is used for SMB access, then create the account removing all the SGs except the SMB one I created.
Am I on track?  Further explanation on what SGs to be removed from and which SG my smbaccess SG should be added to would be good to know.



Thaks,
John

---

### Post by TheFu on 2021-02-10
why not use **smbpasswd** to create the account and force the userid to *plex* on the Linux file system?

---

### Post by johnfm3 on 2021-02-10
Been a long time since admin on linux.  Can you please elaborate on what you mean?

I am guessing there is a smb utility to create account for use in smb service based on part of your suggestion.

I am not sure about forcing to plex portion.

Thanks
John

---

