---
title: "no login screen on clients"
date: 2010-09-17
forum: Server Platforms
---

### Post by keiffee30 on 2010-09-17
I have got a 10.4 LTS LTSP server running as i needed it should do. 

When i boot-up one of the terminal it sees the DHCP and starts loading from the LTSP all working ok.... when it gets the login screen some of the terminals get the box on the screen to enter the user name and password. the other terminal dose not. 

The work around i have got is that i have to click on the blank screen at the bottom left to get the "pick a session" button then i can login and can login as normal. 

When all the clients login all is well, And works as if the system was loaded locally its fast and at the mow its reliable. The only thing that is not working as it should is the log in screen.

Could anyone give me any information on this?

---

### Post by a9k3d on 2010-10-02
It has been several years since the last time I worked with LTSP but I had a similar problem.

One machine didn't want to work - it had a different video card and needed a different X config to work. I had to setup a special config for it. See [http://manpages.ubuntu.com/manpages/lucid/man5/lts.conf.5.html#toptoc9]("http://manpages.ubuntu.com/manpages/lucid/man5/lts.conf.5.html#toptoc9")

In particular CONFIGURE_X and X_CONF

---

