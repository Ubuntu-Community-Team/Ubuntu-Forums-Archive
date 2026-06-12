---
title: "No icon"
date: 2009-11-09
forum: Ubuntu One (CLOSED)
---

### Post by bvpainter on 2009-11-09
According to Synaptic I have the Ubuntu One client loaded, but there does not appear to be an icon on my desktop, for me to get into it.

Can I get into it any other way or get the icon on my desktop.

When I open Ubuntu One from the entry in Applications/Internet all I get  is a preferences screen asking if I want the icon to show, and a connect on start query box.

---

### Post by spacesearcher on 2009-11-09
> **bvpainter said:**
> According to Synaptic I have the Ubuntu One client loaded, but there does not appear to be an icon on my desktop, for me to get into it.

Can I get into it any other way or get the icon on my desktop.

When I open Ubuntu One from the entry in Applications/Internet all I get  is a preferences screen asking if I want the icon to show, and a connect on start query box.

Make sure you have ubuntuone-client-gnome installed also. This integrates everything with gnome desktop.

---

### Post by bvpainter on 2009-11-09
I do have  ubuntuone-client-gnome installed.

---

### Post by joshuahoover on 2009-11-09
> **bvpainter said:**
> I do have  ubuntuone-client-gnome installed.

OK, you have it installed. What you likely want to do is select "Always" in the preferences for when to show the icon. Then you can quit Ubuntu One from a terminal session (Applications->Accessories->Terminal): killall ubuntuone-client-applet ubuntuone-syncdaemon  After that you can start Ubuntu One normally and it should show up in your task bar.

Thank you,

Joshua

---

### Post by bvpainter on 2009-11-09
Rebooted Ubuntu and now it is working. Problem seems that I did not actually recognise the icon. ROTFL.

---

