---
title: "Could Installer Show Message Before Screen Blacks If  Nouveau Can't Support Card?"
date: 2015-09-13
forum: Ubuntu, Linux and OS Chat
---

### Post by buzzingrobot on 2015-09-13
You know that black screen you see when you boot an install image on a machine with a video card that the default open driver that's on the iso can't deal with?

Like the Nvdia 750TI.  15.04 and the 14.04 install images boot to a black screen.  There's nothing there except... nothing.

Question:  What's in charge just before the screen goes black?  The kernel? The installer?  Nouveau? Does anything actually identify the specific video card in use?

I ask because I wonder if a message of some sort could be displayed at that point in the install -- presumably prior to Nouveau's initialization -- that says something like "Your hardware contains a video card that is not supported by this installation image.  If you proceed, your screen will not function and will simply go entirely black...."  Followed, one hopes, by useful guidance about how to work around this supreme annoyance.

Because I've used Linux for a long time, I know I need to get into the BIOS, switch to the onboard Intel video, make sure I actually have the display connected to that port on the machine, reboot, install and reboot, add the correct proprietary driver from the correct PPA, reboot, get back into the BIOS to switch back to Nvidia, reboot again, and cross my fingers.

There's no way first-time users can be expected to have a clue about how to navigate that particular maze. They'll just see a black screen and assume Ubuntu Doesn't Work.

Displaying that message wouldn't fix the problem, but at least it might point people in the right direction.  

Is that possible?

---

