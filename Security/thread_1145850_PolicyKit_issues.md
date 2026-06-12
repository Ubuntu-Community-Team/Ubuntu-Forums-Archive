---
title: "PolicyKit issues"
date: 2009-05-02
forum: Security
---

### Post by cdmdotnet on 2009-05-02
Since I upgraded from 8.10 to 9.04 I cannot use anything that uses the newer authentication system.

I get an issue when I try to edit a network connection via the new network manager or edit a user.
Taking the network manager example, I added a strace session to the authenticate dialogue box , entered my password and watched the output... which wasn't much - I've masked the password.

17:42:06.448553 read(0, "********\n"..., 4096) = 9
17:42:15.951992 write(9, "********\n"..., 9) = 9
17:42:15.952043 read(10, "PAM_TEXT_INFO Could not locate an"..., 4096) = 90
17:42:16.221059 write(1, "PAM_TEXT_INFO Could not locate an"..., 90) = 90
17:42:16.221115 read(0, 

and that's it. it just hangs, I can't close the dialogue I can't do anything... short of killing the process.
My system isn't using an AD authentication it should just be a stock standard install of 8.10 upgraded to 9.04

At this point I'm not sure how I can modify the network connection without dropping it out of the newer network manager and going back to manual management via the /etc/network/interfaces file - which I'd really like to avoid.

any ideas on how to get the authentication system working?

---

