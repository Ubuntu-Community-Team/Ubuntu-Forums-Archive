---
title: "First day with Kubuntu"
date: 2008-04-25
forum: Testimonials &amp; Experiences
---

### Post by thenes on 2008-04-25
I wanted to try something new and made a fresh install of Kubuntu 8.04 in stead of Ubuntu.

I thought I would give Konqueror a try while in KDE.

Some of the internet pages I use does not work with icetea, so I always install java from java.com. So I did this time, expecting it to work with Konqueror.

Googling the question, I found out that Konqueror does not use a java plugin (.so-file in plugins like in Firefox), but a direct path to java in the jre-folder. I set this up.

Java does not work.

I observe that Konqueror gathers plugins from .mozilla in the home folder, and so I create a symbolic link to libjavaplugin there, hoping that this will help Konqueror find java.

Java still does not work.

I google some more, but finds nothing. Gives up, apt get Firefox. Adds the java plugin to /usr/lib/firefox/plugins. Java works in Firefox.

Later that day I want to show my wife how java does not work in Konqueror. In Konqueror I open java.com and suddenly Java works.

I know Konqueror is feeding plugins from /usr/lib/firefox. But I had already provided a plugin for Konqueror through .mozilla in the home folder. I have no clue what happened, but it works.

This was my first day in Kubuntu.

---

