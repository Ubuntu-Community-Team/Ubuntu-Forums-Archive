---
title: "Xfce, replace Control-C in Terminal?"
date: 2008-03-25
forum: Server Platforms
---

### Post by Sunnz on 2008-03-25
So I am running a server that has a simple Xfce login when I need to access it physically.

Just wondering if it is possible to replace the Control-C shortcut in the Terminal with another key combination. Currently I believe Control-C sends a TERM signal to the current running process in the Terminal.

But I want to do it so that when I ssh in it is still Control-C...

So say Super-C while I am in front of the server running Xfce but Control-C when I ssh in from my laptop.

Thanks.

---

### Post by dmizer on 2008-03-27
i am not exactly sure what you're wanting, but i believe you want to be able to locally terminate a currently running task which you opened remotely via ssh.

easiest way would be to simply find the task with something like ps or top, and kill it.
```
sudo killall task
```

alternatively, you could explore the incredibly useful tool called screen.  when you ssh to your server, you can open a screen session, and run your task.  then, later when you have physical access to your server, you can use the screen utility to reattach to your screen session opened via ssh, and then kill your task.

screen howto: [http://www.amitu.com/blog/2004/12/screen-howto.html](http://www.amitu.com/blog/2004/12/screen-howto.html)

---

