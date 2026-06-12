---
title: "How to self-correct named pipe"
date: 2021-11-25
forum: Ubuntu Application Development
---

### Post by tc2020 on 2021-11-25
Hello,

We develop a program that runs as a service on Ubuntu Server 20.04 LTS. This program creates several API's based on named pipes as IPC. Other on-board apps can only read from these pipes, no write. The 'program' writes the same data to various pipes, allowing several apps to read data on a one-to-one basis (dedicated pipe for each app).

For whatever cause it is, a pipe stops working. Under this condition, a command line "systemctl stop program" takes a long time and times out before the user prompt returns. The 'systemctl status program' command says "Failed" (with timeout status message). When we "systemctl restart program", it says "Active (running)". However, the pipe is still stuck and not running. We can check this by looking at the file the pipe writes data to. Under this problem condition, if we delete all the pipes and then restart the program, it works perfectly.

Questions:

1). What are possible causes for such a problem?. Pipe broken?. Who is causing it?.
2). Why is it systemctl restart (or stop/start) does not fix it?. It says active but does not really clear the problem. Is there a way to get this systemd to clear and return resources?.
3). Is there a way to incorporate some sort of self monitoring/self correcting mechanism within the program/service or external to the program to resolve this problem automatically?.

Any help would be very much appreciated. Thank you.

---

### Post by TheFu on 2021-11-27
1. I'd think that the reader is holding the pipe.  Use **lsof** to check that.
2. I don't know. Systemd cannot fix some things.  It asks a program to terminate, nicely.  I suppose you could tell it to take the program down (in the mean way), but that can leave junk behind.
3. Yes.

---

