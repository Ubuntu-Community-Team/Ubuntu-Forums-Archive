---
title: "unrecognized keyword 'KeywordExpand' in cvs 1.12.13"
date: 2009-01-13
forum: Server Platforms
---

### Post by vlc on 2009-01-13
From "Version Management with CVS":

> If there is a desire to not have any RCS keywords expanded and not use the -ko flags everywhere, an administrator may disable all keyword expansion using the ‘CVSROOT/config’ line:
        # Do not expand any RCS keywords
        KeywordExpand=i

As soon as I add this line to the *config* file, I get the following error:

> cvs [checkout aborted]: unrecognized auth response from server: cvs 
pserver: /cvs/CVSROOT/config: unrecognized keyword 'KeywordExpand'

Is there anyone with the same problem or does anyone know the solution to it?

Thanks a lot in advance!

---

