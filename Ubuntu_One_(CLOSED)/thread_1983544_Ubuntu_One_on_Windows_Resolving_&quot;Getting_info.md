---
title: "Ubuntu One on Windows: Resolving &quot;Getting information, please wait&quot;"
date: 2012-05-20
forum: Ubuntu One (CLOSED)
---

### Post by gsparky2004 on 2012-05-20
I tried out Ubuntu One on one of my dual-boot systems running Windows 7 Home Premium (64-bit).  I double-clicked on the installer .exe file, it went through some motions, then it came to a window that said, "Getting information, please wait".  And there it stopped.  I Googled around a bit and found that other people had this same problem.  
I found the answer that worked for me <a href="https://bugs.launchpad.net/ubuntuone-client/+bug/852107">in one of the bug reports</a>.  Here's what I did:
*** NOTE: If you've already tried to install Ubuntu One, UN-INSTALL before going to Step 1. ***
1) Click on the "Start" button.
2) In the window just above the "Start" button, type "uac" (without the quotes) and hit enter.
3) In the window that shows up, click on the link "Change User Account Control Settings".
4) In the new window that pops up, there's a slider bar with four vertical positions.  Move the slider bar to the position such that the text on the right should start with "Default" followed by some more text. In some cases, this is the second-from-the-top position; in others, it's the top position.
5) Click "Okay".
6) REBOOT YOUR COMPUTER. (This is an important step left out of the bug report instructions.)
7) Try to install Ubuntu One again.  Follow the various prompts provided.
8) Check to see if it works.  This worked perfectly for me.

---

