---
title: "Having problems with udev rules"
date: 2011-01-12
forum: Ubuntu Dev Link Forum
---

### Post by extraordinary_boy08 on 2011-01-12
I'm having a problem in implementing my udev rule. What I want is whenever I inserted a usb device, a script will be executed. 
This is the udevrule that I've made:
```
ACTION=="add", SUBSYSTEM=="usb", RUN+="home/jcjo/info.sh"
```

I've placed it in /etc/udev/rules.d just like what I see in different tutorials. 

When I tried to insert any usb device, the script wasn't working. I already tested and executed the script it in the terminal and it worked.

PS. Also, I'm not sure if the udevrule is right. Kindly check it for errors.

My version of ubuntu is 9.10.

Thank you very much.

---

### Post by IcarusR on 2011-01-16
Never mind, my error.

---

### Post by Dr.Helperstein on 2011-01-26
I was having a similar problem, but I think I know what you are missing.

Make sure you are using an execute bit.

Also, I made all my rules in this format, not sure if it makes a difference.

SUBSYSTEM=="usb", ACTION=="add",  RUN+="home/jcjo/info.sh"

This is the rule I'm using:
SUBSYSTEMS=="usb", ACTION=="add", RUN+="/usr/local/bin/USB.sh"

You need an execute bit to give your script permission to run, on my system something like this does the trick:

sudo chmod +x /usr/local/bin/USB.sh

(in the terminal) 

Should work after that, check out:
[http://ubuntuforums.org/showthread.php?t=1290438]("http://ubuntuforums.org/showthread.php?t=1290438")

---

### Post by extraordinary_boy08 on 2011-01-28
> **Dr.Helperstein said:**
> I was having a similar problem, but I think I know what you are missing.

Make sure you are using an execute bit.

Also, I made all my rules in this format, not sure if it makes a difference.

SUBSYSTEM=="usb", ACTION=="add",  RUN+="home/jcjo/info.sh"

This is the rule I'm using:
SUBSYSTEMS=="usb", ACTION=="add", RUN+="/usr/local/bin/USB.sh"

You need an execute bit to give your script permission to run, on my system something like this does the trick:

sudo chmod +x /usr/local/bin/USB.sh

(in the terminal) 

Should work after that, check out:
[http://ubuntuforums.org/showthread.php?t=1290438](http://ubuntuforums.org/showthread.php?t=1290438)

Thanks for the response! Appreciate it. 

I will test it later. I'll just post some updates regarding the result of your suggestion. Thank you very much!

---

