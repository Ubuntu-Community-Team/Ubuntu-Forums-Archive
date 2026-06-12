---
title: "Server Console Goes Blank and Other maybe related problems"
date: 2009-01-14
forum: Server Platforms
---

### Post by stormblue on 2009-01-14
Good Morning All,

I'm having a few issues that maybe related...or not.

When I boot up my computer running Ubuntu Server(2.6.15-51) if I just let it boot normally it loads a blank screen, as in there is nothing there.  I don't see the prompt at all.  If I boot up into the recovery console, it seems fine.

The second issue is that my FTP server isn't work, and I can't get logged it. However, my scripts were working well enough to get at least one file about 6 hours ago because the scripts automatically download from it and there is one file that was modified.

The last issue is that I can't log into ssh.  I was using key authentication, but I modified the config file and turned this off so I should be able to login, however I can't log in.  I double checked the IP address and port numbers and I did an /etc/init.d/ssh restart and a /etc/init.d/vsftp restart and that didn't seem to help.  I get a network error connection refused when I try logging in over putty, however, I can login on the local machine using it's 192.168.0.20 IP address.  If I go and restart ssh I get Network Error: Software caused connection abort.

Thanks in advance for any help.  Does anyone have any ideas?

---

### Post by stormblue on 2009-01-15
I've removed the blank and quiet from the end of the default login in grub and that fixed that.

The other issue was caused by putty and still not resolved.

---

