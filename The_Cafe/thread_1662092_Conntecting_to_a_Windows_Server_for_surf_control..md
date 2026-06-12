---
title: "Conntecting to a Windows Server for surf control."
date: 2011-01-07
forum: The Cafe
---

### Post by Paul Evers on 2011-01-07
I have been working with a K - 8 school on donating HP tablet pc's. They have a tight budget and have decided to use ubuntu (Ubuntu 10.10 netbook) for these desktops which works great. My company is about to deliver these tablets to the school. 

One question: The school have a windows server. Their surf control sits on the server. How do you connect the desktop tablets to the servers surf control?

I'm the salesman trying to help out.

I am just fishing trying to get some help.

---

### Post by CharlesA on 2011-01-07
Depending on how it's set up, you could just tell the browser to use that machine as a proxy.

It really depends on how they've set the content filter up.

---

### Post by Captain Smiley Pants on 2011-01-07
Wouldn't you want to tell the OS to use the Windows machine as a proxy instead of setting up some template for the browser? Because then you could limit permission on tampering with IP settings... vs. Me at work with my browser having proxy settings and, even though I don't have Administrator settings, could easily change the browser proxy settings...

---

### Post by koenn on 2011-01-07
> **Paul Evers said:**
> 
One question: The school have a windows server. Their surf control sits on the server. How do you connect the desktop tablets to the servers surf control?

I'm the salesman trying to help out.

I am just fishing trying to get some help.


You should find out what exactly they're using as "surf control". 
If it's some generic web proxy, it's merely a matter of browser configuration - piece of cake. 

Chances are that they're using MS ISA server (Internet Security and Acceleration) or something similar, which will apply firewall and content filtering rules based on Active Directory accounts/groups for the logged on user. Getting that to work with Ubuntu clients might be a bit of challenge - MS isn't big on standards and interoperability.

---

