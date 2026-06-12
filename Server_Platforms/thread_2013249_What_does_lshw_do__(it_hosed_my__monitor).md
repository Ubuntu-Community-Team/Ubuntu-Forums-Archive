---
title: "What does lshw do?  (it hosed my  monitor)"
date: 2012-06-30
forum: Server Platforms
---

### Post by nosmadar on 2012-06-30
I'm running 10.04.3 server.  I was just checking something and ran:
sudo lshw -class network

The monitor flickered and I saw a few characters appear in the lower left hand corner and then all I saw was a message from the monitor firmware "Display not supported".  I also tried the command from a SSH login from a laptop also running the same version (10.04.3) and the same thing happened to that terminal window.  Nothing I tried (CRTL+C, Reset, Reset & Clear) fixed it. Eventually I think the process timed out because I saw a message "broken pipe" appear in the terminal window.

But the main thing I'm curious about is what this command really does to obtain the information it's going to display, so I can figure out what the actual problem might be.

Looked at the man page, so there's an option "-disable" to disable the test.  Which might help for the short term.  But I don't feel lucky today :-)

---

