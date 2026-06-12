---
title: "Problems with 8.04.2 LTS server"
date: 2009-04-10
forum: Server Platforms
---

### Post by kaj on 2009-04-10
I had an Ubuntu 6.06 LTS server running perfectly for a long time. Then I decided to upgrade to the 8.04 LTS, but something went wrong, and it was totally spoiled.

As I also had some hardware problems, I tried to install the Ubuntu 8.04.2 LTS on another computer. After the 3. attempt I now have the system installed, but it is not working properly. 
On the old server, I had the Gnome Desktop installed although it is a server, as I am using it for some web development.
I can't install the Desktop on the new system. When I try, I get the message, that gnome-keyring-manager is needed, but it cannot be installed.

What can I do about that?
I know, that you will say, that a server shall not have a desktop environment installed, but I WANT that.

Another thing is that when I install phpmyadmin, it is not shown in the /var/www directory. On my old server, it did show up in that directory, as soon as it was installed.
Maybe it has to do with some symlinking, but from where to where?

I have followed the howto on [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts) and the guide on ubuntu.com, but there are a lot of things, that doesn't work out the way as described. I haven't tried to install the mail server yet, as I could expect a lot of problems there.
I also have problems with the network setup, as I cannot reach the internet, when I try to set up as static, so now my network is set up with dhcp, and that is not the correct way for a server.

When I installed the 6.06 LTS server two years ago, everything was easy and worked at the first try, so what have changed with the 8.04 server?

And what can I do about it? Would it be better to install the desktop version and then install the server packages afterwards?

Kaj Rasmussen
from Denmark

---

### Post by jonabyte on 2009-04-20
How are you installing the gui desktop, what error message (specifically) are you getting?

I have not had any problems, so far installing 8.04.2 on my servers. Could the new one have hardware issues?

---

