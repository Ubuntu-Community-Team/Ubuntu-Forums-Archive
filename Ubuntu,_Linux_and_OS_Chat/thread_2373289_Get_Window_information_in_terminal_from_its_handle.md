---
title: "Get Window information in terminal from its handle"
date: 2017-10-04
forum: Ubuntu, Linux and OS Chat
---

### Post by avidichard on 2017-10-04
I would like to know if it's possible to retrieve the application and icon path from a window handle in the terminal. I use xprop to retrieve the window handle but I can't seem to be able to retrieve anything else than the window dimensions. I would like to know which application the window is associated with and if possible the icon path of that particular window.

---

### Post by TheFu on 2017-10-05
It is usually easiest just to check the process table for the process using most of the CPU.  Use top, htop, or any of the 20 other tools for that.  If you want to do it in a programmatic way, I think it can be done, but it isn't trivial.

Never underestimate the power of 'which' and 'ps' and 'whereis' and 'locate'.

It is also possible to look through the menus. /usr/share/applications

---

### Post by avidichard on 2017-10-06
The question is: How to get the application, icon and other information from a WINDOW HANDLE!!!! I do not want to know which application takes the most CPU. I've done 2 days of search with half answers. I do not want to use other applications or install any apks. I just want to know if something is possible in command line or bash script.

---

### Post by ian-weisser on 2017-10-06
Application: See  _NET_WM_PID(CARDINAL)
The PID will lead you to the application.

There are several ways to get the icon from there.
For example, use .desktop file for that application.

---

### Post by TheFu on 2017-10-06
> **avidichard said:**
> The question is: How to get the application, icon and other information from a WINDOW HANDLE!!!! I do not want to know which application takes the most CPU. I've done 2 days of search with half answers. I do not want to use other applications or install any apks. I just want to know if something is possible in command line or bash script.

Another half answer ... 

```
$ xprop | awk '/PID/ {print $3}' | xargs ps h -o pid,cmd
```

returns the path to the running program.  "other info" is a little vague.  Icon's aren't stored with the application. They are part of the ".desktop" file ... from my prior post.  You can parse the application and grep in the /usr/share areas for the icons.

I wouldn't have a clue how to get "other information." Sorry.


OTOH, if your question is: "I just want to know if something is possible in command line or bash script. " then the answer is yes.

---

