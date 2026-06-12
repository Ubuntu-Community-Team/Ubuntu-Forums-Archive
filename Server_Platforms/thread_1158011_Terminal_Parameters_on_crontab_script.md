---
title: "Terminal Parameters on crontab script"
date: 2009-05-13
forum: Server Platforms
---

### Post by nkout on 2009-05-13
Hi!

I use an Option HSDPA modem and Ubuntu 8.10 server.

Driver used is hso1.12 available at:
[http://www.pharscape.org/forum/index.php?topic=720.0](http://www.pharscape.org/forum/index.php?topic=720.0)

Driver has a script included, so I can connect using shell

But there are problems when I run the script through crontab as terminal parameters are missing!

The script uses chat program in order to connect with the device and without a terminal, stty cannot configure the bitrate!!

Do you have any idea about that??

Thannks a lot,
Nikos

---

### Post by nkout on 2009-05-15
The problem is more general:

how can I run bash in terminal (or terminal emulator) through crontab?

Thanks a lot!

---

### Post by 3L33T on 2009-05-17
> **nkout said:**
> 
Driver has a script included, so I can connect using shell

But there are problems when I run the script through crontab as terminal parameters are missing!



Question for you:  what happens when you run the script manuall?  does it work or does it still require manual user interaction during the login process?

> 
The script uses chat program in order to connect with the device and without a terminal, stty cannot configure the bitrate!!



If the provided login script works by itself and does not need any further user interaction during login process then insert a line in the crontab that will call the login script.

So if your login script is called 'logmein.sh' then in your crontab add:

```


  10 0 0 * *  /home/myshells/logmein.sh


```

---

### Post by nkout on 2009-05-19
The problem is that the script communicates with serial port, using the terminal parameters for the bitrate!

That's why I need to run it inside a terminal!

---

### Post by nkout on 2009-05-25
An alternative question is how you can set the bitrate on "chat" program ([http://www.manpagez.com/man/8/chat/](http://www.manpagez.com/man/8/chat/)) used for writing communication scripts with a modem????

---

