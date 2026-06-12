---
title: "Lxsession new options enabled by default approaching in Saucy"
date: 2013-07-02
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2013-07-02
I received the following message recently and thought I'd share it here:

[https://lists.launchpad.net/lubuntu-qa/msg03064.html](https://lists.launchpad.net/lubuntu-qa/msg03064.html)

> Hi,

I just push a switch in Lubuntu default settings, which will turn on
some features of lxsession. As it changes many aspect of the default
session, you will probably see some regression in the next daily
builds (probably in 1 or 2 days, when lubuntu-default-settings 0.32
will be included). Please let me know if you see some. There is
already some know bugs :
- No network notification icon on non-laptop installation (but network
is working)
- Launching the terminal in pcmanfm open it on home, not the current directory

I will try to send another mail with the details of the new features
enabled. Most of them are relative to the autostarted applications,
which are handle in lxsession-default-apps (autostart directory is
muted by default, and autostart conf file is empty). In the meantime,
if you have any questions, feel free to ask them.

Finally, the QLubuntu session is coming too, but you should install
razorqt package before using it, and I also recommend to install
pcmanfm-qt from lubuntu daily PPA
([https://launchpad.net/~lubuntu-dev/+archive/lubuntu-daily](https://launchpad.net/~lubuntu-dev/+archive/lubuntu-daily)). However,
it's highly experimental, fixing bugs on it is very low in my TODO
list :-)

Regards,
Julien Lavergne

---

