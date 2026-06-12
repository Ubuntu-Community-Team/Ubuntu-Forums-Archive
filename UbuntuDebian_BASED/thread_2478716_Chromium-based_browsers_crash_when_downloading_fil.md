---
title: "Chromium-based browsers crash when downloading files"
date: 2022-09-03
forum: Ubuntu/Debian BASED
---

### Post by leonardohenao on 2022-09-03
Hi,


The inconvenience that I have is that when downloading a file which requests a specific path to save and that opens the nautilus, when selecting the path it stays "stuck" or "frozen".


Although in the video I only show the error when trying to change the downloads folder, I want to show that the error is always when that "selector" of the routes is opened.


Install this version that I have on another PC and notice that it works perfectly there, it happens to me with all the kernels that I have tried so I discarded it, I know what happens with the chromium-based browser since I downloaded others different from brave like Edge, Chromium, Vivaldi and the error is the same.


[Video where I show the error]
[https://www.youtube.com/watch?v=LD0s-_LW-Zc](https://www.youtube.com/watch?v=LD0s-_LW-Zc)



Thanks in advance for your attention

---

### Post by ajgreeny on 2022-09-03
Is your chromium installed as the snap version which is now the default?

All snap have limitations in the manner in which they can connect with the filesystem other than specific locations in your home; this is one of the reasons why I do not use any snaps for any of the installations I use.

Let's see the output in terminal of command ***snap list***.

I use a PPA for a dev version of chromium installed as a .deb package but will have to find the PPA address when no longer on my Android tablet and will post back here.

EDIT:
Here it is with all the information on how to add it to your sources.
[https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev)

I've been using it for a few years with no difficulties or problems, and it is not restricted in any way.

---

### Post by leonardohenao on 2022-09-03
Thank you for your support, I have installed Brave browser by PPA, I don't use snap store, even I have it disabled,

[img]https://i.imgur.com/fTzYkxC.jpg[/img]
[IMG]https://imgur.com/fTzYkxC[/IMG]

But before I didn't have that error, I don't know when it started to happen.

[IMG]https://imgur.com/fTzYkxC[/IMG]

---

### Post by ajgreeny on 2022-09-03
Too late for this thread but please, in future do not use images to show us terminal content but copy the text from terminal (by highlighting the text with mouse then using Ctrl+Shift+C or right click and choose copy.
Please then paste the terminal output using **Code-Tags** as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by mIk3_08 on 2022-09-04
> **leonardohenao said:**
> Thank you for your support, I have installed Brave browser by PPA,
 Why you are using ppa when you can download brave browser directly from their website? Regards and cheers

---

