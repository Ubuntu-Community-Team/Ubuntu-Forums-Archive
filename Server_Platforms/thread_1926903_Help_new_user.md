---
title: "Help new user"
date: 2012-02-17
forum: Server Platforms
---

### Post by joblafors on 2012-02-17
Hello. I had a friend who set up a custom program that listens to port and then forwards data to php script. It was working fine for a year, but now it suddenly stopped. I have very basic server knowledge so its hard for me to find the problem. I`m trying to connect to that port bot it refuses, so i have to find out if problem is that program is not running or something with ports.
Here are all processes running :
[IMG]https://lh5.googleusercontent.com/-uUf3Al4m7UE/Tz4kVvxM-UI/AAAAAAAAACg/DFVOjEnqad8/s512/Bitvise%2520xterm%2520-%252089.111.20.10822.jpg[/IMG]

Here are all the files from that program:
[IMG]https://lh5.googleusercontent.com/-yO4NP2YsE8I/Tz4k-mnA57I/AAAAAAAAACo/UevGBqZVZtQ/s483/CDocuments%2520and%2520SettingshomeDesktopeurtrip_2.jpg[/IMG]

Ok now i think i found how to run the program, but i get this error:
[IMG]https://lh6.googleusercontent.com/-CnNobtXJu-o/Tz4nHSa-AOI/AAAAAAAAACw/hqnIwL9DGU4/s422/Bitvise%2520xterm%2520-%252089.111.20.10822_2.jpg[/IMG]

---

### Post by cabaro on 2012-02-17
To see if the port is listening, run following command:
(port 1234 in example)

```
netstat -nlp | grep 1234
```

---

### Post by jonobr on 2012-02-17
Hey


There is a readme file in the same directory

Try reading it to see if it gives information on running that application,

Also, take a look into /etc/init.d maybe there is something in there that may ring a bell for you.

Lastly looking through the /etc/rcx.f directories you may find something in there that starts it at boot time

---

### Post by SeijiSensei on 2012-02-20
A segmentation fault is a failure during program execution.  It can't typically be fixed just by adjusting a configuration file.

Whenever something just "stops working," I'm suspicious that something else changed.

Was this version of the program compiled on this machine, or was the binary copied over from somewhere else?  If the latter, that would explain why it cannot run.  It was probably compiled with different headers and libraries on the other machine that aren't present on yours.  You, or he, should try recompiling.  The file list shows there's a "configure" script so compiling should just require following the usual steps described [here](https://help.ubuntu.com/community/CompilingEasyHowTo).

---

