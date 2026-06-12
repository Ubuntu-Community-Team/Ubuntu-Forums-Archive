---
title: "virus found during scan."
date: 2010-07-04
forum: Security
---

### Post by JABP on 2010-07-04
Hi , I'm quite new to Ubuntu and I am running Ubuntu Studio 10.04 . I have just installed Klam AV and had it scan my computer . I was surprised to find that it had found two 'viruses' . I don't know if anyone can help me in finding out if they are real or only false positives . The following is the output that I received .

Name of File
/usr/src/fglrx-8.723.1/libfglrx_ip.a.GCC3 and GCC4

Name of Problem
Heuristics.Broken.Executable

Status
Loose

Does anyone know if this is a problem.

---

### Post by cariboo on 2010-07-04
It's more than likely a false positive, but if you got your Ati video driver from an untrusted source, I'd get rid of it.

---

### Post by ajgreeny on 2010-07-04
There's only one file listed there.  Did it list another one as well?

---

### Post by rookcifer on 2010-07-04
> **cariboo907 said:**
> It's more than likely a false positive, but if you got your Ati video driver from an untrusted source, I'd get rid of it.

I concur.  The fact that it appears to have been detected by "heuristics" leads one to this conclusion.

---

### Post by JABP on 2010-07-05
Hi , I got the ATI video driver from Ubuntu via driver search . And it was the same file name , just the last 4 characters were different eg GCC3 & GCC4 .

---

### Post by bodhi.zazen on 2010-07-05
> **JABP said:**
> Hi , I'm quite new to Ubuntu and I am running Ubuntu Studio 10.04 . I have just installed Klam AV and had it scan my computer . I was surprised to find that it had found two 'viruses' . I don't know if anyone can help me in finding out if they are real or only false positives . The following is the output that I received .

Name of File
/usr/src/fglrx-8.723.1/libfglrx_ip.a.GCC3 and GCC4

Name of Problem
Heuristics.Broken.Executable

Status
Loose

Does anyone know if this is a problem.

The next step is to do a google search on those files ...

---

### Post by JABP on 2010-07-06
Hi , I Googled the file names , not much help . Although the Poles do seem to be having a problem
with this . At least they do in Netbooks , as far as I can tell from the translated pages they don't have  
a solution . It could be a false positive result , or the file could be corrupted . I don't know !

---

