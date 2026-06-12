---
title: "Need to have OS detected as Server or Desktop"
date: 2023-10-13
forum: Ubuntu, Linux and OS Chat
---

### Post by akaranjkar7880 on 2023-10-13
Hey There!!

I am trying to identify installed OS is **server or desktop** by checking the text in the file **/etc/os-release and /etc/lsb-release** but there is no clue for identifying whether it is server or desktop.
I would like to suggest **Ubuntu developers** to add some text here to identify the installed OS if it is server or desktop or workstation etc.
This will help up to list the machines with count in the network and can be used for monthly reporting.

---

### Post by coffeecat on 2023-10-13
@akaranjkar7880, two points:

You posted in the *Forum Feedback & Help* sub-forum, whose strapline states:

> Report technical problems with the website here (i.e. broken features), or ask questions pertaining to forum features.

So, not the right place. Since this doesn't appear to be a support request, I've moved the thread to *Ubuntu, Linux and OS Chat*, as this could be the foundation of an interesting discussion. Bearing in mind that you can install a desktop on a server install, or use a desktop version as a server, I can't see that there is a binary choice here so I will be intrigued to see what other forum members may say. 

> **akaranjkar7880 said:**
> 
I would like to suggest **Ubuntu developers**

This is not the place to contact Ubuntu developers and maintainers. This is a volunteer forum of end users who help each other. We are not responsible for developing or maintaining Ubuntu, or instituting new features.

---

### Post by ian-weisser on 2023-10-13
Seems like an XY Problem.

Your actual problem seems to determine how many of each type are on the network.
You are *assuming* that /etc/os-release or /etc/lsb-release are the best way to locate that information. You are also assuming the Desktops and Servers are discrete. Both assumptions are false.

Servers can install desktop packages, remove server packages, and became a full desktop install. Similarly, Desktops can become servers with a bit of package juggling. Many folks share files by installing server packages onto their desktop system. Many admins install graphical desktops onto their server.

Don't ask about your assumed solution. Ask about the actual problem that you want to solve.

---

