---
title: "apparmor 'anon_hugepage' what to do?"
date: 2012-01-28
forum: Security
---

### Post by Xo-Mige on 2012-01-28
I am in the process off writing a apparmor profile for oracle java and geogebra
 

 and after I run those programs to do a aa-logprof session for those programs
 apparmor asks me If I whant to allow read to 'anon_hugepage'
 

```
Profile:  /usr/lib/jvm/java-7-oracle/jre/bin/javaws
 Path:     anon_hugepage
 Mode:     r
 Severity: unexpected rank input: anon_hugepage
 

 

  [1 - anon_hugepage]
 

 (A)llow / [(D)eny] / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts

```

 the problem is that no matter wheather I allow or deny the next time I start A logprof session apparmor tells me that there is a syantex error like so


```
/etc/apparmor.d/usr.lib.jvm.java-7-oracle.jre.bin.javaws contains syntax errors. Line [  anon_hugepage r,]
```



the geogebra profile is complete and im working on the java profile.

---

