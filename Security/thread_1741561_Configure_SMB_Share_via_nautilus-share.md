---
title: "Configure SMB Share via nautilus-share"
date: 2011-04-28
forum: Security
---

### Post by ASolano on 2011-04-28
Hi All,

Can anyone help me do the equivalent of "force_user" when sharing with nautilus-share?

To put this question into context, I have shared out a folder with "Allow others to create ..." and "Guest Access ..." turned on via the GUI (I believe nautilus-share is applicaition behind the GUI).  When Guest accounts create files or folders, I want the owner of the files or folders to be a specific user, rather then "nobody".

In a Samba Server, I know you can use the parameter "force_user" in the smb.conf (under an individual sharename) which will specify the owner of the files and subfolders created through the share.  I have tried to add this parameter to the files created in /var/lib/samba/usershares but the owner of the files and folders are still "nobody" (NOTE: I rebooted the PC after making the change to the file)

I have just done a fresh installation of Ubuntu 10.10 Desktop with nothing else installed (except the current Updates and the necessary components needed when sharing folders)

As a follow on question, I also want to set the permissions for files and folders.  To replicate what the "create_mask", "force_create_mode", "directory_mask" and "force_directory_mode" parameters do within a Samba Server.

Regards,

Andrew

---

### Post by ASolano on 2011-05-11
mmm over 90 view but no response.

Can I assume that this can't be done.

What a shame, I like the GUI, just not enough functionality, setting up a Samba server is easy enough anyway.

---

