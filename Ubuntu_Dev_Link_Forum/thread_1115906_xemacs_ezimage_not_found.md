---
title: "xemacs: ezimage not found"
date: 2009-04-04
forum: Ubuntu Dev Link Forum
---

### Post by maitrebart on 2009-04-04
Since a few days, I try to install some packages related to xemacs (e.g. php-mode) with synaptic and I get the same error for those packages that fails:

> Errors were encountered while processing:
 php-mode
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up php-mode (0.1-1ubuntu1) ...
install/php-mode: Handling install for emacsen flavor xemacs21
Compiling /usr/share/xemacs21/site-lisp/php-mode/php-mode.el...
While compiling toplevel forms in file /usr/share/xemacs21/site-lisp/php-mode/php-mode.el:
  !! File error (("Cannot open load file" "ezimage"))
>>Error occurred processing php-mode.el: Cannot open load file: ezimage

Compiling /usr/share/xemacs21/site-lisp/php-mode/php3-mode.el...
Wrote /usr/share/xemacs21/site-lisp/php-mode/php3-mode.elc
Done
emacs-package-install: /usr/lib/emacsen-common/packages/install/php-mode xemacs21 xemacs21 failed at /usr/lib/emacsen-common/emacs-package-install line 30, <TSORT> line 1.
dpkg: error processing php-mode (--configure):
 subprocess post-installation script returned error exit status 1


I found the missing file (ezimage.el) on the net and I copied it in the directory that seemed to me the most appropriate (based on what already exists on my machine): /usr/share/emacs/site-lisp/emacs-goodies-el/.

But when I try to reinstall the failing packages, I get the same error again.

So I wonder if one of you had that kind of error before?
Or maybe is there a way to add a .el file in xemacs in order it takes it into account?

Btw I have Xemacs 21.4.21.

Thanks.

---

### Post by jpkotta on 2009-04-05
ezimage is in the emacs22-common package, which should have been installed with Xemacs as a dependency.

---

### Post by maitrebart on 2009-04-05
I will try to fix the dependency.

Is it normal that I need emacs22-... package while using xemacs21 ?

---

### Post by jpkotta on 2009-04-05
I've looked into it a bit more, and it seems like emacsXX-common is common files for emacsXX and emacsXX-nox, both of which are packages for GNU Emacs, not XEmacs.  I guess I've always had GNU Emacs installed, which may be why I've never encountered your problem.  I'd say try the emacs21-common package, then the emacs22-common package, and whether either works or not, file an Ubuntu bug report, since it seems like a packaging bug.

---

### Post by maitrebart on 2009-04-11
None of emacs21 nor emacs22 solved the problem. I filed a bug. Thanks.

---

