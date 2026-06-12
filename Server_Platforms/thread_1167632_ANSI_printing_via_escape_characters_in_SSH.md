---
title: "ANSI printing via escape characters in SSH"
date: 2009-05-23
forum: Server Platforms
---

### Post by bulgarion on 2009-05-23
Hi,
I must admit in advance that I'm not much skilled in terminal emulations, and stuff like this :P 
I'm trying to reproduce the behavior of the terminal emulator and SSH client PuTTY under ubuntu's GNOME. The feature that I can't reproduce is the native ANSI printing, via escape characters sent inside the SSH data stream (I found more info [here]("http://linux.derkeiler.com/Mailing-Lists/SuSE/2008-09/msg00333.html")). PuTTY has an explicit way to configure the destination of the "raw printer stream" but the native ubuntu's SSH client has no such option.
I have no control of the server-side application; it's given as-is from the Application Provider. I need both a text terminal and being able to print the raw stream that comes through that single SSH connection, like I was doing with PuTTY.
Is there any willing soul that could point me to the solution?
Thanks!

Marco

---

### Post by tkgamble on 2009-08-18
If your version of the openssh client is 5.1p1 or newer, interpretation of ansi escape codes embedded in a login banner page is no longer possible. They will be displayed as their octal code. They should still work once logged in, however.

---

