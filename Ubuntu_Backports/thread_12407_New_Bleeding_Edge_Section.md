---
title: "New Bleeding Edge Section"
date: 2005-01-24
forum: Ubuntu Backports
---

### Post by jdong on 2005-01-24
At revision 9, I've added a "bleeding" section to all the backports repositories (alongside the usual main, universe, etc).

This is an area where I'll experiment with beta or bleeding technology. This may include:

[list]
[*] Smart Package Manager
[*] CVS Snapshots of Firefox, etc.
[*] Wine snapshots
[*] Not-so-stable enhancements, like enhanced features from the upstream release (i.e. upgrade-notifier, simple synaptic from Hoary).
[/list]

The main difference between bleeding and -staging, is that staging stuff is going to go into the stable branch **for sure**, while the bleeding stuff is more experimentally natured.

So, common sense says that the stability won't be a big part of the bleeding branch, so **don't add it to your sources.list** unless you're really sure of what you're doing!

---

### Post by pulp on 2005-01-30
[QUOTE=jdong]At revision 9, I've added a "bleeding" section to all the backports repositories (alongside the usual main, universe, etc).

This is an area where I'll experiment with beta or bleeding technology. This may include:

[list]
[*] Smart Package Manager
[*] CVS Snapshots of Firefox, etc.
[*] Wine snapshots
[*] Not-so-stable enhancements, like enhanced features from the upstream release (i.e. upgrade-notifier, simple synaptic from Hoary).
[/list]

The main difference between bleeding and -staging, is that staging stuff is going to go into the stable branch **for sure**, while the bleeding stuff is more experimentally natured.

So, common sense says that the stability won't be a big part of the bleeding branch, so **don't add it to your sources.list** unless you're really sure of what you're doing![/QUOTE]
 Maybe I'm wrong, but wouldn't it be useful, if there was

warty-backports
warty-backports-staging
warty-backports-bleeding

with the main, universe etc. sections for the first two of them (same for warty-extras)

instead of

warty-backports
warty-backports-staging

with "main" etc. AND "bleeding"?

I do think, that the "bleeding" section has nothing to do with stable and staging.

You're doing a great job with the backports. Thanks

---

