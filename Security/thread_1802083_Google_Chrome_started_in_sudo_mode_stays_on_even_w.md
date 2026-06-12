---
title: "Google Chrome started in sudo mode stays on even when terminal closed."
date: 2011-07-11
forum: Security
---

### Post by UncleClover on 2011-07-11
I've noticed something with Google Chrome which -might- be considered a "security issue" on Ubuntu, but if it isn't then please just disregard this.

At some point (and this is a separate problem I'm not asking for help on here, though feel free if you think you might know something that could help), during the past several installations, I eventually reach the point with Google Chrome that if I want to be able to store profiles and use all extensions, I have to start it up in terminal with sudo. Otherwise, starting it as just a normal user, it will tell me that my profile cannot be read or stored, and that some features may thus be unavailable.

Okay, that's a problem, but not a real big one to me. But when I start it in terminal, I usually have to keep the terminal open or it closes Chrome, too - a good thing, I suppose, since I'd started Chrome as root. However, if I have the extension "Chromey Calculator" active and detached, I can close the terminal window and when I close the warning that closing the terminal will terminate the active process in progress, miracle of miracles it leaves the browser running and in-tact - su priveleges and all.

I actually -like- this ability, but yet I can see how for some, that might constitute a security concern of some sort. However, if it doesn't, then might I request it be used (assuming others can replicate it) to enable one to do that with -all- apps started from terminal? It's kind of a pain having to keep the terminal open just to run an application started in it.

Extra info: I've tried launching Chrome from an icon set to call up Chrome with the gksudo command so that I can enter my root-user privelege password, but that doesn't work. It still gives me the "profile can't be read" error. Why would it get me to the right place with a sudo command in Termnial, but not a gksudo command spawned by a launcher? :-?

Thanks for any and all replies. :-)

:popcorn:

---

### Post by Bachstelze on 2011-07-11
You should not run Chrome with root privileges.  Period.  If you feel the need to, then something is very, very wrong.

---

### Post by Bucky Ball on 2011-07-11
> **Bachstelze said:**
> You should not run Chrome with root privileges.  Period.  If you feel the need to, then something is very, very wrong.

+1. Running *anything* as root is a secuity risk. You possibly need to add your user to the appropriate group at a wild guess, or change a permission setting in the Chrome config.

---

### Post by karlson on 2011-07-11
> **UncleClover said:**
> Otherwise, starting it as just a normal user, it will tell me that my profile cannot be read or stored, and that some features may thus be unavailable.


Check the permissions on .config/* in your home directory.

I would agree with the previous posters that running a Chrome as root is a bad, bad, bad, bad idea.

The problem is most likely is that you have a lingering process running as root that has your profile owned by root.

As far as a terminal is concerned Chrome's extension may be detaching the process from the controlling terminal and would remain running if the terminal is closed.

---

### Post by UncleClover on 2011-07-12
Thank you VERY much! I had already been through the other suggestions & more, but this one turned out to be it. I couldn't figure out what permissions were getting goofed up. While I'm not too new to Linux as a whole, I've not delved too far into its directory structure to date - I find it a bit intimidating. ;-) But I changed the permissions on the folders you mentioned, and that fixed it up perfectly. Thanks again VERY much!  :-)


> **karlson said:**
> Check the permissions on .config/* in your home directory.

I would agree with the previous posters that running a Chrome as root is a bad, bad, bad, bad idea.

The problem is most likely is that you have a lingering process running as root that has your profile owned by root.

As far as a terminal is concerned Chrome's extension may be detaching the process from the controlling terminal and would remain running if the terminal is closed.

---

