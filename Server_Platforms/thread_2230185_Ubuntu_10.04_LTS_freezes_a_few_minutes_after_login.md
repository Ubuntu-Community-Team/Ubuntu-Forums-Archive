---
title: "Ubuntu 10.04 LTS freezes a few minutes after login"
date: 2014-06-17
forum: Server Platforms
---

### Post by c_xy on 2014-06-17
Hello,

I've run into some recent issues with Ubuntu 10.04 LTS.

Everytime i log in, either directly to the server or remotely using nomachine the server freezes up.

Here is a run down:


1) Log in
2)  Open up a terminal window
3) A minute elapses
4) I try to open a new terminal window, it does not appear.
5) I try to exit out of the existing terminal window and the window changes from black to white screen. I can move the cursor, but I cannot remove the blank white terminal window.

Oddly enough, I don't have a problem if I ssh to the server from another server. I can open up displays, run commands, and it does not freeze up. So, I wondering what the issue could be?

Any ideas, thoughts or input is greatly appreciated.

Thanks,

c

---

### Post by sudodus on 2014-06-19
There is a bug affecting desktop environments in 10.04 LTS, where the server is supported but not the desktop version (flavours). So if you have to continue with 10.04 LTS, please stay away from the graphical desktops. They have not received any security updates for more than one year, and now we have this bug that might not be fixed, because the desktops are no longer supported.

Otherwise, if you need graphics, please upgrade to 12.04 or reinstall. See this link

[Forums Staff recommendations on EOL Ubuntu releases, in particular 10.04 desktop.]("http://ubuntuforums.org/showthread.php?t=2229730")

*Edit*: It may help temporarily to use the previous kernel.
[URL="http://ubuntuforums.org/showthread.php?t=2229730"]

[/URL]

---

### Post by c_xy on 2014-08-20
Thank you for your response. Sorry for responding so late.  I was using the server 10.04 LTS. I think there was a bug in one of the updates at the time for server 10.04 LTS. After another update, it was working fine again and no problems since that time.

Thanks again.

c.

---

