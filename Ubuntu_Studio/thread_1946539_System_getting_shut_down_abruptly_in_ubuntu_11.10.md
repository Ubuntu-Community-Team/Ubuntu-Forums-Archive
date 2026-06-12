---
title: "System getting shut down abruptly in ubuntu 11.10"
date: 2012-03-25
forum: Ubuntu Studio
---

### Post by cyclokar on 2012-03-25
Hello,
       I recently partitioned my hard drive and used around 55 GB of my D drive for Ubuntu 11.10 , i am also running windows 7 in my system.(Dual) Whenever i use ubuntu my system get shut down suddenly after half an hour or so , abruptly! irrespective of the processes I am running. And if I try to boot immediately it never happens , as in I dont even reach the OS loader page where I usually get to choose between Windows or Ubuntu , system again shuts down well before that. But I dont see any such problems when using Windows 7 .I am not sure if it is a hardware related issue cause the problem is only with  Ubuntu.Could anyone please help me out with the issue.

---

### Post by mwinthrop on 2012-03-25
I don't know the answer, but do have one idea.  I am wondering if the computer could be overheating?  You could try looking at any temperature sensors the computer might have.  My thought was to try the following program:
[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

and since you are using Ubuntu 11.10

[http://askubuntu.com/questions/66624/how-do-i-get-sensors-applet-working](http://askubuntu.com/questions/66624/how-do-i-get-sensors-applet-working)

This assumes you are using Unity desktop - if not, then you would have to figure out if there is a way of installing for your desktop.  I am using Ubuntu Studio 11.04 with gnome so I don't know if the program will work or not on your system, but it does work in 11.04 at least for my computer.  I suppose you could also consider installing Ubuntu Studio 11.04 to see if something changes.

I guess another thing to see is if there is something Ubuntu 11.10 is running that is using many CPU cycles, which might be the cause of an overheating situation.  Maybe there is something wrong with the hardware that does not get triggered in Windows 7 but does in Ubuntu.  Another thought is to get temperature monitoring software in Windows 7 and compare the results with the temperatures reported by Ubuntu.  Anyway, not sure if this helps or not.

---

### Post by rk0r on 2012-03-28
> **cyclokar said:**
> Hello,
       I recently partitioned my hard drive and used around 55 GB of my D drive for Ubuntu 11.10 , i am also running windows 7 in my system.(Dual) Whenever i use ubuntu my system get shut down suddenly after half an hour or so , abruptly! irrespective of the processes I am running. And if I try to boot immediately it never happens , as in I dont even reach the OS loader page where I usually get to choose between Windows or Ubuntu , system again shuts down well before that. But I dont see any such problems when using Windows 7 .I am not sure if it is a hardware related issue cause the problem is only with  Ubuntu.Could anyone please help me out with the issue.


What i would do is monitor the temperatures by using conky, you can get this in the software repo. Once you run this on your desktop you should be able to monitor whats going on. Do you have an old system or new? post some specs.

---

