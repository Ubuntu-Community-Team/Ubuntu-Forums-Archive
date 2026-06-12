---
title: "hide folder in shared network drive in samba"
date: 2007-01-04
forum: Server Platforms
---

### Post by Pitt Stains on 2007-01-04
Hello, I am using Samba to share a folder which the XP boxes on the network all have mapped as a network drive.  As they are all members of the group "users", they all have access to the files.

I have added one folder to the share which I'd like only the user "bjones" to be able to access.  I made "bjones" the owner of the file and made sure the group was not "users", then set the permissions to 770.  Problem solved, I thought.

Well, almost.  The other users can see the folder on the share, but they can't open it.  What I'd prefer is for the folder to be invisible to everyone but bjones.

Does anyone have suggestions?  I think I've maxed out the power of file ownership/permissions here, but if someone knows of some way to do this, I'm all ears.

I was thinking that another was to do this, which I'd prefer not to do mostly out of laziness, might be to edit smb.conf to set up another share (a "nested" share?) for this folder...  I can't recall the exact values, but could I achieve this effect with a "nested" share by messing with the "browseable", "valid users", and maybe some other settings?

Just sorta thinking out loud here, folks...
-Pitt

---

