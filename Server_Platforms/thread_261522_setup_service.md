---
title: "setup service"
date: 2006-09-20
forum: Server Platforms
---

### Post by ossie on 2006-09-20
Hi,
How do I configure a program to run as a service in ubuntu.

In Redhat you have the program chkconfig but I don't find it in ubuntu.

Thanks.

---

### Post by bswilson on 2006-09-20
> **ossie said:**
> How do I configure a program to run as a service in ubuntu.

I guess it depends on the program.  I'm not familiar with the Red Hat tool you mentioned, but many programs have the ability to run as a daemon or service with an additional startup flag.  Have you checked the help (*command -h* or *command --help*) or the man entry for your program?

---

### Post by RoyArne on 2006-09-20
> **ossie said:**
> Hi,
How do I configure a program to run as a service in ubuntu.

In Redhat you have the program chkconfig but I don't find it in ubuntu.

Thanks.

The debian equivalent of chkconfig is **update-rc.d**.

---

