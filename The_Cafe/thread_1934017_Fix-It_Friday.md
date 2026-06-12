---
title: "Fix-It Friday"
date: 2012-03-01
forum: The Cafe
---

### Post by dholbach on 2012-03-01
Coinciding with Ubuntu Global Jam, the Ubuntu developers have a really nice treat for you on Friday, 2nd March. They’ll make themselves available to answer all your questions on [#ubuntu-motu on irc.freenode.net]("http://webchat.freenode.net/?channels=ubuntu-motu"), help you get involved, review your code and upload your changes to Ubuntu. As we are eight weeks away from release, this is just the perfect time to go and fix a few bugs. All you need to do is, check out these articles: [Introduction to Ubuntu development]("http://developer.ubuntu.com/packaging/html/introduction-to-ubuntu-development.html"), [Getting Set Up]("http://developer.ubuntu.com/packaging/html/getting-set-up.html") and [Fixing a bug in Ubuntu]("http://developer.ubuntu.com/packaging/html/fixing-a-bug.html"), and turn up in #ubuntu-motu.

What we are going to work on is
[LIST=1]
[*]**[Packages which don’t build anymore.]("http://qa.ubuntuwire.com/ftbfs/")**
If you have worked with compiling source code before, you know that a mistake like a syntax error can get you into a situation where the build is broken and does not succeed. There are lots of other reasons why this might happen, a good idea is usually to review the build log referenced in the link above.
[*]**[Bugs which have been fixed elsewhere.]("https://bugs.launchpad.net/ubuntu/+bugs?field.status_upstream=resolved_upstream&orderby=-id")**
Our bug life cycle works like this: make sure the bug can be reproduced reliably, gather all the information necessary, figure out if it’s an Ubuntu-specific problem or if it happens in the vanilla code of the software authors as well, then forward the bug with all the relevant information upstream. The Launchpad bug tracker is a great tool, which puts us into the situation where we are able to go through bugs which were fixed elsewhere already. Taking these fixes and applying them to Ubuntu is a great target for improvements, especially being eight weeks away from release.
[/LIST]


It’s going to be a fun event and maybe your first patch which goes into Ubuntu! :-)

---

