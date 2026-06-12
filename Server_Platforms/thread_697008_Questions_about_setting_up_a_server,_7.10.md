---
title: "Questions about setting up a server, 7.10"
date: 2008-02-14
forum: Server Platforms
---

### Post by kill4killin on 2008-02-14
I'm a member of a computer security team at my university. We are going to be entering the SECCDC competition in mid March. The school hosting the event has asked us for a list of websites that they should add to their proxy to allow us to have some outbound traffic for tools and updates we might need for our servers to help secure them for the competition but so we can't access un-authorized tools (we're only allowed to use open source or free for corporate use tools and programs). I already have a few written down but I'm sure I'm missing a bunch and I figured you guys know a lot more about setting up a Ubuntu server then I do so I thought I might see if anyone had any suggestions.

Thank you very much, your help is greatly appreciated.

---

### Post by crouton on 2008-02-14
It sounds like you will want to review the /etc/apt/sources.list file - these are the repositories for the various packages of your current distribution.  If you aren't allowed access to these addresses you won't be able to grab any updates or install software over the network.

Hope this helps.

---

