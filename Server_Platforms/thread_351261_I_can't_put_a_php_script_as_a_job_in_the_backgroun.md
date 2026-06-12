---
title: "I can't put a php script as a job in the background"
date: 2007-02-01
forum: Server Platforms
---

### Post by iperich on 2007-02-01
I have a 64 bits Ubuntu in a Xeon Dual Core box, and I'm having the following problem

I want to execute a php script in the background. It takes a long time to execute, since it is working in a big DB and it have very long loops. So, I do the following (through ssh)

root@mybox:/# php script.php > /dev/null &
[1] 3461
root@mybox:/#  

I press enter and i get this:

[1]+  Stopped                 php script.php > /dev/null 

So I did

root@mybox:/# %1&
root@mybox:/#  


I press enter and i get the same again:

[1]+  Stopped                 php script.php > /dev/null 

I can't execute the script in the background. I test if the script is working anyway and it isn't. 
Is this a security issue? I did the same thing in a Mandriva box and it worked.

Thanks in advice.

iperich

---

### Post by xela321 on 2007-02-02
iperich-

Have you thought of using screen?

I liked this tutorial very much: [http://www.howtoforge.com/linux_screen]("http://www.howtoforge.com/linux_screen")

You could also set it as a cron job maybe?

---

### Post by iperich on 2007-02-02
I cant do it as a cron job, but it seems that screen should work it out... I will check it out. Thanks....

iperich

---

