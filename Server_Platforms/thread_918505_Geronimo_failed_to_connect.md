---
title: "Geronimo failed to connect"
date: 2008-09-13
forum: Server Platforms
---

### Post by 007casper on 2008-09-13
I have installed Geronimo without a problem in /var/www

went to localhost:8080/console/

was able to access it without any glitches... log out and refresh the page and I got 

> Failed to Connect

Firefox can't establish a connection to the server at localhost:8080.

Though the site seems valid, the browser was unable to establish a connection.

    * Could the site be temporarily unavailable? Try again later.
    * Are you unable to browse other sites?  Check the computer's network connection.
    * Is your computer or network protected by a firewall or proxy? Incorrect settings can interfere with Web browsing.

It worked to seconds ago, and I dont know why it didnt work again.  I have reinstalled it.  Nothing.  I have stopped, restart, and move the geronimo to /usr/local/.... nothing... 

disabled firewall, checked proxy on the browser I have set it to "use system proxy settings"

any help will be really appreciate it :(

---

### Post by windependence on 2008-09-13
I couldn't find a solution to your problem but I will give you a tip. Re-installing usually does not solve much and sometimes can make the problem worse if there are remnants of the previous install left on the machine. I know that in Windoze, this seems to be common practice, but on Linux/Unix, we usually try to fix things without doing this. Try one thing at a time, and if that doesn't work, put things back the way they were and try something else.

I'll keep looking for a solution for you. ;)

-Tim

---

### Post by 007casper on 2008-09-15
got it almost figured out... it is geronimo issue, some reported that it is bug.  It has to do with permissions, and you have to be in root and access everything from root

thanks for your help especially regarding install, uninstall... I guess I am used to too much of Win

---

