---
title: "Put home folders in a different location?"
date: 2009-09-01
forum: Server Platforms
---

### Post by Silver565 on 2009-09-01
How would one go about putting all the home folders for users on another server?

I have two ltsp servers (well this is the plan). Booting clients. The problem is i'd like the users to be the same and have all the same files so that despite what server you login to via a client the "documents, Desktop, pictures" etc will remain the same.

I presumed that moving the home folder to a server linked to both ltsp server would be an easy way of doing this?

Any help would be appreciated

---

### Post by hessiess on 2009-09-01
> **Silver565 said:**
> How would one go about putting all the home folders for users on another server?

I have two ltsp servers (well this is the plan). Booting clients. The problem is i'd like the users to be the same and have all the same files so that despite what server you login to via a client the "documents, Desktop, pictures" etc will remain the same.

I presumed that moving the home folder to a server linked to both ltsp server would be an easy way of doing this?

Any help would be appreciated

Move the contents of /home onto the file server, then mount it as a remote filesystem into /home. you would also need to find a way of syncing /etc/shadow and /etc/passwd

---

