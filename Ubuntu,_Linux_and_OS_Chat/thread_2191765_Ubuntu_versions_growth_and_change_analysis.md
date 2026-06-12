---
title: "Ubuntu versions growth and change analysis"
date: 2013-12-04
forum: Ubuntu, Linux and OS Chat
---

### Post by ctayjt on 2013-12-04
Hi everyone.

I'm currently writing a research report and one of the section is to focus on the growth and change analysis of the evolution of Ubuntu system lifetime and which will need numbers for the charts. Hit a brick wall at the moment as I can't seem to find any topic regarding the LOC(Lines of Codes) number of classes, number of methods, number of fields, number of public methods or any other metrics for the source code of any version. The most I could find were popularity charts. Does anyone know where I can get these informations? 

Thank you.

-Chris

---

### Post by deadflowr on 2013-12-04
Why don't you call Ubuntu?
[http://www.ubuntu.com/about/contact-us](http://www.ubuntu.com/about/contact-us)

---

### Post by cariboo on 2013-12-04
The [devel-discuss]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss") mailing list may be a better place to ask your questions, as it is open to anyone. It also means you don't have to deal with any of the phone-drones, that really have no idea what you are asking about.

---

### Post by ian-weisser on 2013-12-04
The "source code" of the core Ubuntu install is spread across hundreds of packages from dozens of upstream projects. By "core," I mean the packages included with the ubuntu-standard metapackage. What you want to track may differ.

Ubuntu's release manager and engineering manager have not historically cared much about the metrics you seek...because they don't need to maintain the code or publish an API. The upstream projects do that. 

For your tracking purposes, you may need to go project by project pr package by package.
Some projects may not keep the kind of data you are looking for.
Or you may need to script up some counters and start crunching old source packages.

You may need to find a smaller-scope project to measure. Like a single upstream project.

---

