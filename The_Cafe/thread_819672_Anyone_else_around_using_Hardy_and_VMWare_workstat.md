---
title: "Anyone else around using Hardy and VMWare workstation 6.0.4?"
date: 2008-06-05
forum: The Cafe
---

### Post by FFighter on 2008-06-05
If so, please, share your experiences. I'm facing a big annoying problem here where X stops recognizing key combos and dead-keys after a while when I have the VM opened - I think it happens when I switch from the VM to another desktop but I couldn' really identify the root of the problem yet. When this happens, I have to manually close the session and log-in again (and re-start every app I was using), a big waste of time :(.

I have XP SP2 running in the VM.

---

### Post by Midahed on 2008-08-01
Yes, I have the same VMware Workstation / Hardy configuration and a similar problem.

It appears to be related to running a VM in full-screen mode.  I have no problems unless I do that.  After running full-screen, if I open an OpenOffice document or a text editor, a mail client or a Google search (and probably others) and then use the keyboard, the application in the active window is crashed by any keystroke.

Avoid running VM full-screen and the problem doesn't arise.

There's a thread here that spells it out, although the precise symptoms of the problem and the viability of some of the workrounds do seem to vary a bit.

[http://communities.vmware.com/message/1010317](http://communities.vmware.com/message/1010317)

Hope this helps - if a bit late. :)

**[Edit]** I've been using it for a few days now and it appears that the problem only arises if full-screen mode is selected using ctrl-alt-return (or whatever the shortcut is).  Provided that only the GUI buttons are used to switch between full-screen or windowed display,the problem doesn't arise.  So at least there's a reasonable workround.

---

