---
title: "Trac and SVN for Multiple Projects"
date: 2009-08-24
forum: Server Platforms
---

### Post by stefanadelbert on 2009-08-24
I'm looking at options for a Bug/Issue Tracking platform, preferably with a built-in Wiki, that integrates with SVN. I really like the look of [Trac]("http://trac.edgewall.org/"), but it seems to be aimed at catering for one project.

My requirement would be to have one Trac instance covering multiple projects which all live in the same SVN repository. Each project should have its own Wiki page within Trac. One milestone would incorporate all projects, but projects would be individually versioned, e.g. ProjectA-1.3 and ProjectB-2.6 would both form part of Milestone-10 (which would tie back to one unique SVN revision). Issues/bugs/tickets would all be raised/visible from the one Trac instance, but should be assigned against a particular project.

Has anyone used Trac and SVN for this purpose? is [Redmine]("http://www.redmine.org/") better suited? Any other recommendations?

---

