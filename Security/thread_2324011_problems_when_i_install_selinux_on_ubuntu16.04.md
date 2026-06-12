---
title: "problems when i install selinux on ubuntu16.04"
date: 2016-05-10
forum: Security
---

### Post by Hanjey on 2016-05-10
hello,recently i tried to install selinux on ubuntu16.04,but failed!!!the following is error message:



Can not stat: /etc/selinux/ubuntu/contexts/files/file_contexts.local: No such file or directory
libsemanage.sefcontext_compile: sefcontext_compile returned error code 1. Compiling /etc/selinux/ubuntu/contexts/files/file_contexts.local
libsemanage.semanage_install_active: Could not copy /etc/selinux/ubuntu/modules/active/file_contexts.homedirs to /etc/selinux/ubuntu/contexts/files/file_contexts.homedirs. (No such file or directory).
/usr/sbin/semodule:  Failed!
dpkg: error processing package selinux (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Errors were encountered while processing:
 selinux
E: Sub-process /usr/bin/dpkg returned an error code (1)


i beg someone can help me solve the problem!!!

---

### Post by HermanAB on 2016-05-10
If you want to use SELinux, then you should use Fedora:
[https://spins.fedoraproject.org/](https://spins.fedoraproject.org/)

---

### Post by Hanjey on 2016-05-10
thanks,however I have to use ubuntu!!!

---

### Post by ZoiaGuyver on 2016-05-11
Is there a reason for you needing Selinux? Ubuntu already has [AppArmor]("https://en.wikipedia.org/wiki/AppArmor") which offers the same level of MAC. Also the selinux in Ubuntu afaik hasn't had updates since around 2009 it's just been rebuilt against later versions of Ubuntu.

If for some reason you really, really need selinux you would need to start by removing AppArmor as they would conflict. Depending on how you tried to install the package you may need to actually get the selinux-policy-ubuntu.

Other than that I can't help much as on systems that come with Selinux i tend to remove it for either AppArmor or Tomoyo.

---

### Post by HermanAB on 2016-05-12
Well, configuring SELinux from scratch is extremely difficult/well nigh impossible - not something a single person can do.

So, if you have to use Ubuntu, then use AppArmor.  If you have to use SELinux, then use a RedHat version.  

If your boss told you that you have to use Ubuntu with SELinux, then tell him it will take about 5 man years.

---

### Post by Hanjey on 2016-05-19
thanks!

---

