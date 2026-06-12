---
title: "Error compiling iFolder server in Feisty"
date: 2007-07-01
forum: Server Platforms
---

### Post by jdogzilla on 2007-07-01
Hello, I'm getting the following error compiling iFolder in Feisty ... any suggestions?

make[3]: Entering directory `/ifolder3-server-3.5.7039.1/src/server/Simias.Server'
resgen Report.resx Simias.Server.Report.resources
Error: Cannot load support for ResX format: File or assembly name System.Windows.Forms, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, or one of its dependencies, was not found.
make[3]: *** [Simias.Server.Report.resources] Error 1

---

### Post by sphim on 2007-08-23
I have the exact same problem. Hopefully somebody with more skills than me can help. Please, help!

---

### Post by mlucio on 2007-09-27
try with
apt-get install libmono-winforms1.0-cil

---

