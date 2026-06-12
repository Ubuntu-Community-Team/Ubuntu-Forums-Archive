---
title: "Bugzilla Template customization"
date: 2011-04-30
forum: Server Platforms
---

### Post by skri79 on 2011-04-30
Hello @ all,

currently I'm working on customizing templates of Bugzilla.
The create.html.tmpl and the edit.html.tmpl.
As read in the bugzilla templating guide, I chose to alter the default templates
in first place.
Something stranges happens: Every time I alter a template,
changes are saved. Next time I open the file, changes are
overridden.

What I did to find a solution:
1. Change permissions to 777 (for testing purposes).
2. Tried to change files via ssh and machine's own editors (joe, mc, nanon)
3. Download Files, changed them locally, uploaded files again via SFTP.
4. Created a "custom" folder and saved changed files to this directory.

And again: Changes are not saved...
In case of 4., complete folder disappears.

Somebody an idea?

BR

K-

---

