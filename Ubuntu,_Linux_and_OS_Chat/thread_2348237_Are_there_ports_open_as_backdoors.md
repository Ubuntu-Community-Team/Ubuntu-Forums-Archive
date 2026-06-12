---
title: "Are there ports open as backdoors?"
date: 2017-01-01
forum: Ubuntu, Linux and OS Chat
---

### Post by xenon3 on 2017-01-01
In other newsgroups its said that microsoft keeps some ports open as backdoors, and when hackers trace them, microsoft changes them by security updates. Is that true?

microsoft does that on behave of the FEDS they say, by law.

Does that law apply for UBUNTU Linux too?

---

### Post by TheFu on 2017-01-02
Ubuntu doesn't have any listeners running by default unless you enable them.  

Use **netstat** or **lsof** to verify this.  If you install any network server (something that listens for incoming connections), then you should setup the firewall to only allow connections that YOU want and block all others.

A law would apply to any OS, but I'm not aware of any such law.  A NSL may require MSFT to do stuff for specific systems and may have a gag order to prevent any notification.  You can look up all the complains and issues about NSL elsewhere.  I have had to implement systems to meet EU laws around capturing all the header information in emails (TO/FROM/SUBJECT/DATE/X-headers and send those to systems in France which could be queried by any law enforcement in Europe. The EU law can be read on wikipedia. [Searching tonight seems to show that parts of that law have been repealed]("http://www.nytimes.com/2015/10/28/opinion/europe-is-spying-on-you-mass-surveillance.html?_r=0"). Don't know how much.

I believe the USA has a similar law, but don't quote me on it. I don't have any first-hand knowledge about that. The [EFF says this]("https://www.eff.org/nsa-spying").

I think using wifi is like talking in public and is fair game for anyone who wants to listen. The same for cell phones and cordless phones - they are broadcasting.  But transmissions through a wire are more like telephone conversations, which have been deemed protected.

I do fall on the side of a privacy advocate, a properly paranoid group today CAN hide the details of their communications on the internet. I don't think they can hide that they are communicating.

Alas, I've wandered 1000 miles off topic. Sorry

---

### Post by wildmanne39 on 2017-01-02
*Thread moved to **Ubuntu, Linux and OS Chat**.*

> Discussion of the politics of open source is permissible in this area of the forum only, but only the politics of open source. Wider political discussion is disallowed in all areas of the forum
Please stay on topic.

---

