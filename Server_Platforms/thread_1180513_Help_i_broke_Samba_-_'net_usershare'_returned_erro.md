---
title: "Help i broke Samba - 'net usershare' returned error 255: net usershare add: cannot co"
date: 2009-06-06
forum: Server Platforms
---

### Post by ouchmyhand on 2009-06-06
error message when trying to create shares in Nautilus by right click -> share -> create share

'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Invalid parameter.

I have found some other thread son this but running Nautilus as root using alt+f2 did not work, still get the same error.

Simply i want to have user access to a share from windows computers and PS3 but don't wnat to have to manage seperate accounts and passwords for Smaba and Ubuntu.

I had it mostly working (including not having to create extra UID's for Samba) but then I ran a GUI Samba config tool that messed things up.
I removed Samba & all configs, then reinstalled and now can't create shares???

Help please???

---

### Post by ouchmyhand on 2009-06-08
Anyone???

---

### Post by ouchmyhand on 2009-06-09
Can anyone redirect me to somewhere that could help? I'm so new i don't know where to look. I thought the Ubuntu forums would be a good start but so far no assistance.

---

### Post by ouchmyhand on 2009-06-10
any help, surely someone else has had this error before?

---

### Post by Iowan on 2009-06-10
I haven't seen the error before...
but I found a similar [thread]("http://ubuntuforums.org/showthread.php?t=1026668"). (starting about post #5)

---

### Post by ouchmyhand on 2009-06-10
Thanks for the post.
Unfortunately using root to share the folder didn't work. I assume the last two posts on the thread also didn't have their issue resolved by the link in that thread.
My guess is that there is a permission issue somewhere but as a newbie i have no idea where to start troubleshooting. Maybe even a way to reset all permissions that samba cares about?
Any help may actually help these other two posters at the end of the above mentioned thread.
Samba gurus, please help.

---

### Post by practic on 2009-06-22
This is a work-around, not a solution.

1. Install system-config-samba from Synaptic
2. Run the program from the menu System->Administration->Samba
3. Add the share using this program and it will be shared on the network

Nautilus will not recognize it as shared since it didn't create it, so you won't see the little sharing icon under the folder, but it seems to work anyway.

---

### Post by giyad on 2009-11-12
Mark as solved ;-)

[http://ubuntuforums.org/showthread.php?t=958457](http://ubuntuforums.org/showthread.php?t=958457)

---

### Post by kpetersen on 2010-12-28
> **giyad said:**
> Mark as solved :wink:

[http://ubuntuforums.org/showthread.php?t=958457](http://ubuntuforums.org/showthread.php?t=958457)

I'm on Ubuntu 10.10. For me this didn't work. The problem for me was, that I had not associated a system account to the samba guest account. All other settings were already like mentioned in the posting above.

Using the tool from post #7 is the right way... but not for adding the share.
I used it to assign the system user nobody to guest by choosing 
settings->server-settings->security from the menu.

```
sudo service smbd restart
``` from the terminal and the usershares worked from nautilus like they should.

HTH.

---

