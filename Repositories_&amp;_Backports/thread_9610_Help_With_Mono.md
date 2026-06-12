---
title: "Help With Mono"
date: 2004-12-29
forum: Repositories &amp; Backports
---

### Post by burntash on 2004-12-29
whenever i try to install mono i get the following error:

The following packages have unmet dependencies:
  libgnome-cil: Depends: mono-jit (>= 1.0.1) but it is not going to be installed or
                         mono-mint (>= 1.0.1) but it is not going to be installed
                Depends: libgconf-cil (>= 1.0) but it is not going to be installed
                Depends: libglade-cil (>= 1.0) but it is not going to be installed
                Depends: libglib-cil (>= 1.0) but it is not going to be installed
                Depends: libgtk-cil (>= 1.0) but it is not going to be installed
                Depends: mono-assemblies-base (>= 1.0) but it is not going to be installed
  mono: Depends: mono-jit (= 1.0.4-1) but it is not going to be installed or
                 mono-mint (= 1.0.4-1) but it is not going to be installed
        Depends: mono-utils (= 1.0.4-1) but it is not going to be installed
        Depends: mono-assemblies-arch but it is not going to be installed
  monodoc: Depends: monodoc-browser (>= 1.0.1-1) but it is not going to be installed
           Depends: monodoc-manual but it is not going to be installed
E: Broken packages

I am currently pointed to hoary repos.

---

### Post by TravisNewman on 2004-12-29
have you done apt-get update lately? I was having this problem a few days ago, but it's all good now. At least it was, I haven't tried to install it lately, so they could have gone out again

---

### Post by Juergen on 2004-12-30
You could look at the backports:
[http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net)

There you can get mono 1.0.5; installed without problems here.

---

