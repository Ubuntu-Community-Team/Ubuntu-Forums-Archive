---
title: "mod_python, trac and Apache - security problem for trac?"
date: 2006-09-10
forum: Server Platforms
---

### Post by leo_m on 2006-09-10
I have enabled mod_python on Apache for trac.  This required that I make the project db folder both write- and read-able by the Apache user.

Does this mean that all files under the project area are written to as the Apache user?  Actually, I ceated the trac environment in a sub-folder in my home directory, so the project area is under a directory in my home directory.

Elsewhere, I had read it is not a good idea to use WebDAV on Apache as all files that are created using WebDAV are created as Apache user and in the event of Apache daemon compromise, these would be compromised directly.  Does the same apply to the trac files as well then (I needed to give write permissions to the Apache user to be able to make trac accessible using web-browser) ?

What is the workaround in case it is a problem?

---

