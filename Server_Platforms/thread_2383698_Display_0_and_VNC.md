---
title: "Display :0 and VNC"
date: 2018-01-28
forum: Server Platforms
---

### Post by goemonburo on 2018-01-28
I am curious if anyone knows how to fix this quirky problem:

I am running VNC server on Computer A.

I can access the VNC session from Computer A, or anywhere else.  

My problem is that if I have opened an application, such as LibreOffice, on the local (non VNC) desktop of Computer A, and I want to open a LibreOffice document inside the VNC session, instead of opening on the current VNC window it opens on the local desktop.

And vice versa...if I've opened Adobe Reader to view a PDF and it's currently active on the VNC session, if I go to my local directory when I'm at the computer and click on a PDF, it opens up inside the VNC window.

I would love to know if there's a way to force an application to open up on the current, live window, be that VNC or the local desktop.  

Any thoughts?

Thank you in advance for any suggestions!

---

### Post by steeldriver on 2018-01-28
It sounds like you are using a 'desktop sharing' type of VNC server (such as Vino or x11vnc) whereas you need the kind that enables you to start a separate session on a distinct display (as tightvncserver / vnc4server do for example)

---

### Post by goemonburo on 2018-02-06
How would I check?  I'm starting the server via the command line, as I've done for some years:  vncserver -geometry blahxblah -depth 24 -nevershared :2  

Should I try using vnc4server at the command line instead?

(To view, I've always just typed "xtightvncserver" and that's worked, prompts me for the session and password, etc.  

Thanks for any additional help!

---

### Post by wildmanne39 on 2018-02-06
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by steeldriver on 2018-02-07
Hmm... in that case it sounds like the problem is elsewhere - sorry I don't have any idea about that

---

