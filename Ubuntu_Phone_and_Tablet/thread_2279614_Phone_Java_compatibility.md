---
title: "Phone Java compatibility?"
date: 2015-05-24
forum: Ubuntu Phone and Tablet
---

### Post by CaesarS on 2015-05-24
Hello,

I'm researching porting an Oracle Java 7 service/server application to Ubuntu phone.

What Java flavor & version does the Ubuntu phone support? 

How different is it to develop console applications in Ubuntu phone?

Is it possible to just compile and run on command line? (i.e. no UX as it is a service)

Thank you, Caesar.

---

### Post by grahammechanical on 2015-05-25
It depends on what you mean by "support." I do not think that Java is installed by default as part of the OS. All applications are Click packages. I think that for applications to run on Java the Java runtime would have to be included in the app click package. 

The Ubuntu SDK is used to write the code usually in QML or HTML 5 and then the SDK takes care of the packaging and the application to put the app in the app store.

Ubuntu phone has a terminal application. Is that what you would call a console application? Keep in mind that the file system is read only. What applications can do and what they can access is tightly controlled.

[https://developer.ubuntu.com/en/](https://developer.ubuntu.com/en/)

Two other things to keep in mind are that in future Ubuntu phone is moving on from Click packing to Snap packaging. It is a development of Click packaging. Also, there will be in future a parallel development of Ubuntu Desktop based on Snap packaging instead of Debian packaging. This is part of the convergence plan.

[https://developer.ubuntu.com/en/snappy/guides/packaging-format-apps/](https://developer.ubuntu.com/en/snappy/guides/packaging-format-apps/)

[https://developer.ubuntu.com/en/snappy/](https://developer.ubuntu.com/en/snappy/)

Regards.

---

### Post by CaesarS on 2015-05-25
Yes, I mean applications running in a terminal when I say console. Android's development environment is Java so it has Java runtime capability.

I'm trying to get a better picture of how a Java application running in a terminal could be ported to Ubuntu phone. 

I'm thinking of it as an Android service running in the background (written in Java), so a real service vs. having a UI. The UI itself could be done using Ubuntu SDK.

Or a simpler way might be is if Ubuntu (without phone flavor) could be run in a phone, and porting the java application itself would be much easier.

Is there an official partner manager from Ubuntu where established partner could engage? (vs. individual public developers)

Many Thanks! Caesar.

---

### Post by CaesarS on 2015-05-25
[Apologies, tagging my own post via reply, haven't found a way to auto-subscribe yet]

---

