---
title: "Make Sun's Java the default Java"
date: 2009-04-22
forum: Ubuntu Brainstorm
---

### Post by samjh on 2009-04-22
Thus far, Ubuntu's default installed Java runtime is GCJ.

In the days gone by, Sun's restrictive licensing was a major factor in not making Sun's Java runtime the default installation of Java for Ubuntu.  However, times have changed, and Java is now free and open source with only minuscule portions still encumbered.  The JRE is completely under GPL.

What I propose is that GCJ should no longer be the default Java runtime on Ubuntu, and that it should be replaced by Sun's JRE.

Against GCJ:
1. No significant development since 2007.
2. Substantial compatibility with only Java 1.4.  Compatibility with Java 1.5 is still poor, not to mention 1.6.
3. As far as I am aware, there are no significant applications which absolutely require GCJ and cannot use Sun's JRE.

For GCJ:
1. Native compilation.
2. All components are completely FOSS.

Against Sun's JRE:
1. No native compilation.

For Sun's JRE:
1. Industry's reference implementation of Java's runtime.
2. Source for the runtime are licensed under GPL.
3. Provides maximum compatibility for users.
4. Arguably better performance than GCJ.

---

