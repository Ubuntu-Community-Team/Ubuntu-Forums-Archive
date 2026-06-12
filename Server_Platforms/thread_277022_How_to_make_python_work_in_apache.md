---
title: "How to make python work in apache?"
date: 2006-10-13
forum: Server Platforms
---

### Post by BrianK on 2006-10-13
I'm trying to get apache2's modpython working.  I've installed mod_python & added the following lines to my apache2.conf:

[FONT="Courier New"]AddHandler mod_python .py
PythonHandler mod_python.publisher
PythonDebug On[/FONT]

Is this correct?  What is mod_python.publisher?  How do I know if I have it?

If I look at my apache2 error log, I see these lines every time I try to access the python script through a browser:

[FONT="Courier New"][Wed Oct 11 18:59:36 2006] [notice] mod_python: (Re)importing module 'mod_python.publisher'
[Wed Oct 11 18:59:36 2006] [notice] mod_python: (Re)importing module 'example1' with path set to '['/job/drqueue/python/examples ']'[/FONT]

... and then the page comes up as a 404. ??

---

### Post by BrianK on 2006-10-15
One bump for prosperity.

I've asked this question on three forums now... not a single answer. hmm.

For the record, I'm running Ubuntu 6.06 on the server in question.

---

### Post by BrianK on 2006-10-17
FYI, for other people who come searching, I enclosed the code from the first post into a <directory> block & everything seems to work.  I don't know if it wasn't working without the directory block, but I know it is working with it.

I also still don't know what mod_python.publisher is or how to tell if you have it.  ::shrug::

---

