---
title: "Setting up an sftp file dump site?"
date: 2012-03-06
forum: Server Platforms
---

### Post by MycahM on 2012-03-06
Back in the old days, we could easily setup an ftp server with anonymous upload access whereas once the file was uploaded, the user couldn't see, delete, or modify the files they have uploaded.

I'm trying to set something like that up now in Oneiric, but we are transferring sensitive data that needs to be over an sftp/scp/ftps connection. I've tried using a chrooted sftp connection, however due to the way linux folder and file permissions work, if a user has write access to a folder they can delete a file in that folder no matter what.

Has anyone else setup a similar environment? I'd like for them to have a username or username/password combination that would log so we would know who uploaded what file, however once the file is uploaded they should no longer have access to remove or modify the file.

---

### Post by kevdog on 2012-03-07
I'm going to take a stab in the dark at this one.  When setting up a chrooted environment, isn't a path set up to the executables the user can run within the environment?  I suppose you could just delete the rm command.  However if someone uploaded the rm binary, you would have to make sure they couldn't change the permission of the file to be executable.  I'm just thinking out loud so if this is way off base, just ignore me.

---

