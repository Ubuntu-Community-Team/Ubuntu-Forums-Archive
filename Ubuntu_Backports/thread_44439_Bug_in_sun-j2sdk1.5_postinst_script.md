---
title: "Bug in sun-j2sdk1.5 postinst script"
date: 2005-06-26
forum: Ubuntu Backports
---

### Post by kaarlov on 2005-06-26
I just installed Ubuntu+Kubuntu+Backports and found a bug in Sun J2SDK from backports. I'm sorry if this is already discussed, but didn't find anything about it from first few pages in this forum.

The plugin_dir variable in postinst script (line 44) is set to "$j2se_base/plugin/$arch_dir" and it should be "$j2se_base/jre/plugin/$arch_dir" with J2SDK. I believe the former is right with JRE-package, but the paths are a bit different in SDK.

As a result of this bug the symlinks to java-plugins in /etc/alternatives so not point to any file, and Java-plugin doesn't work in Mozilla-family browsers.

Excact package version in question is sun-j2sdk1.5_1.5.0+update03_i386

---

