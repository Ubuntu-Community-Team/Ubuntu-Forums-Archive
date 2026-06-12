---
title: "People ask...what's different about Unbuntu?"
date: 2010-06-28
forum: The Cafe
---

### Post by KingArthur72076 on 2010-06-28
I've been running ubuntu 10.04 on my laptop for a month now. The guys at work ask me about the difference in windows and ubuntu. Like how is made that most windows virus don't work on it or why can't it use windows programs?

I do know that Windows is mostly .dll based(correct me if I'm wrong). What is Linux products based on. What do I tell people when they ask?

---

### Post by Paqman on 2010-06-28
> **KingArthur72076 said:**
> What is Linux products based on. 

Penguiny magic stuff :)

---

### Post by steveneddy on 2010-06-28
Answer:

[http://www.google.com/search?hl=en&source=hp&q=difference+windows+linux&aq=f&aqi=g1&aql=&oq=&gs_rfai=CP84ZGzYoTMiJIYuugATN08X2CgAAAKoEBU_QrGw1](http://www.google.com/search?hl=en&source=hp&q=difference+windows+linux&aq=f&aqi=g1&aql=&oq=&gs_rfai=CP84ZGzYoTMiJIYuugATN08X2CgAAAKoEBU_QrGw1)

Google is your friend!

---

### Post by endotherm on 2010-06-28
one of the primary differences that every new user should know about in advance, is the way software is installed. show them software center, and explain repositories. for more advanced users, a description of sudo/gksu is also useful. I describe it as UAC, but far more elegant. 

the differances between windows and linux executables is far deeper than just the way libraries are broken up, but I think you are alluding to system APIs (which in windows are dll files in system32). the windows kernel and the linux kernel are simillar in that they both provide functions to upper level code to do very basic things like work with ram, the cpu, and all other hardware. most win32 applications call functions defined in the windows systems apis, that dont exist in the linux system space. Wine attempts to intercept windows api calls, transmute them into linux system calls, and then execute them, but there are literally tens of thousands of api functions, so mapping every one exactly right is probably an intractable task.

---

### Post by KingArthur72076 on 2010-06-28
> **steveneddy said:**
> Answer:

[http://www.google.com/search?hl=en&source=hp&q=difference+windows+linux&aq=f&aqi=g1&aql=&oq=&gs_rfai=CP84ZGzYoTMiJIYuugATN08X2CgAAAKoEBU_QrGw1](http://www.google.com/search?hl=en&source=hp&q=difference+windows+linux&aq=f&aqi=g1&aql=&oq=&gs_rfai=CP84ZGzYoTMiJIYuugATN08X2CgAAAKoEBU_QrGw1)

Google is your friend!

Thank you for the search link.

---

### Post by KingArthur72076 on 2010-06-28
> **endotherm said:**
> one of the primary differences that every new user should know about in advance, is the way software is installed. show them software center, and explain repositories. for more advanced users, a description of sudo/gksu is also useful. I describe it as UAC, but far more elegant. 

the differances between windows and linux executables is far deeper than just the way libraries are broken up, but I think you are alluding to system APIs (which in windows are dll files in system32). the windows kernel and the linux kernel are simillar in that they both provide functions to upper level code to do very basic things like work with ram, the cpu, and all other hardware. most win32 applications call functions defined in the windows systems apis, that dont exist in the linux system space. Wine attempts to intercept windows api calls, transmute them into linux system calls, and then execute them, but there are literally tens of thousands of api functions, so mapping every one exactly right is probably an intractable task.

Good write-up....thanks

---

