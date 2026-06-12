---
title: "Lucid PHP 5.3.3 Backport?"
date: 2010-12-05
forum: Server Platforms
---

### Post by rsteinmetz70112 on 2010-12-05
I'm having problems segfault problems with the PHP 5.3.2 currently in the repositories. Is the an available, reliable backport of PHP 5.3.3 for Lucid?

I don't want to upgrade the entire install, unless I can't get around it.

---

### Post by rsteinmetz70112 on 2010-12-06
There is a conflict somewhere in between php modules apc and XCache (Bug #681167). Removing php-apc solved the problem.

No need to install PHP 5.3.3

---

