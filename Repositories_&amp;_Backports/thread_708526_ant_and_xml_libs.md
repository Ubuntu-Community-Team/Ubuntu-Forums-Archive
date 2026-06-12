---
title: "ant and xml libs"
date: 2008-02-26
forum: Repositories &amp; Backports
---

### Post by rgrig on 2008-02-26
If I turn on warnings in an ANT build.xml file (by passing "-Xlint:all" to javac) I get the following:

    [javac] warning: [path] bad path element "/usr/share/ant/lib/xml-apis.jar": no such file or directory
    [javac] warning: [path] bad path element "/usr/share/ant/lib/xercesImpl.jar": no such file or directory
    [javac] warning: [path] bad path element "/usr/share/ant/lib/xalan.jar": no such file or directory

Is there any Ubuntu package to which those files belong? I would prefer to use it rather than symlinking to them myself.

---

