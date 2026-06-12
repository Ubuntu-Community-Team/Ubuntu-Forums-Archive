---
title: "Monitor you Broadband usage"
date: 2010-04-08
forum: Sudan Team
---

### Post by zero-n on 2010-04-08
I was searching for a program that keep statistics about my data usage until i found this tools:

**[COLOR=Red]KNemo[/COLOR]**

It a good tool for monitoring and keep track of data usage (Daily, Monthly & Yearly)

To install it :
```
sudo apt-get install knemo

```Run the program from:    **Applications** >> **Internet **>> **KNemo**

To allow recording statistics:
1- right click on KNemo tray icon & select [COLOR=Red]**Configure Knemo**[/COLOR]
2- Check [COLOR=Red]**Activate Statistics**[/COLOR]

---

### Post by ajgreeny on 2010-04-08
I simply use **vnstat** and the command ```
vnstat -d
```to give me the download and uploads per day for the last month.  If I want to save the info as a file it is easy with the following script:-
```
#!/bin/bash
vnstat -d > /tmp/$(date +%F-%T)-DLs
gedit /tmp/*DLs
```
Try it, you'll see what I mean.  You don't have to use /tmp for the txt file if you want to keep it; you could put it in /home just as easily, but I did it this way so the file disappears on rebooting, but can be saved to /home very quickly.

Here's the output of my use of this system with a lot of the lines deleted for space saving.
```
eth0  /  daily

    day         rx      |     tx      |  total
------------------------+-------------+----------------------------------------
   10.03.     38.95 MB  |    4.69 MB  |   43.64 MB
   11.03.      1.05 GB  |   49.91 MB  |    1.10 GB   %%%%%%%%%%%%:
   12.03.    260.51 MB  |   15.24 MB  |  275.74 MB   %%%   
   -----
   07.04.    142.68 MB  |    8.43 MB  |  151.11 MB   %
   08.04.     15.93 MB  |    4.03 MB  |   19.96 MB
------------------------+-------------+----------------------------------------
 estimated       16 MB  |       4 MB  |      20 MB
```

---

### Post by oracle2b on 2010-04-08
Do you know of a tool that functions and displays like Dumeter or Networx in windows? I need that equivalent in realtime.

---

### Post by zero-n on 2010-04-08
i have installed vnstat:

```
sudo apt-get install vnstat
```after that i change the command to be:
```
vnstat -i ppp0 -d > /tmp/$(date +%F-%T)-DLs
```but it gave me this error:
```

Error:
Unable to read database "/var/lib/vnstat/ppp0".
 ppp0: Not enough data available yet.

```

---

### Post by ajgreeny on 2010-04-08
That's because you only just installed it.  Have a look at ```
man vnstat
``` which shows all the options available to you.  I also use some of those, but the **vnstat -d** is the most useful to me.

It will work as I showed you from the date of installation, but not backdated, I'm afraid.

---

### Post by ajgreeny on 2010-04-08
> **oracle2b said:**
> Do you know of a tool that functions and displays like Dumeter or Networx in windows? I need that equivalent in realtime.
Right click panel ->Add to panel ->Network Monitor.

---

### Post by MZ250Supa5 on 2010-05-04
Tried KNemo on Lucid - and no joy.  It downloaded well enough, but refuses to run.

---

### Post by zazlox on 2010-12-13
about ppp0

try this command :

> vnstat -u -i ppp0


wait a while to collect some data , then try this command

> vnstat -d


after that , you'll get something like that :

> ppp0  /  daily

         day         rx      |     tx      |    total    |   avg. rate
     ------------------------+-------------+-------------+---------------
      12/14/10       609 KiB |      73 KiB |     682 KiB |    2.74 kbit/s
     ------------------------+-------------+-------------+---------------
     estimated        --     |      --     |      --     |
r

---

### Post by zero-n on 2010-12-14
Thansk [zazlox]("http://ubuntuforums.org/member.php?u=976197"),

now vnstat is working well with me

---

### Post by LordFury on 2012-02-19
strangely when i type your command 

vnstat -u -i ppp0 

it say's Error: Unable create database backup "/var/lib/vnstat/.ppp0".

any clues....am too new to this ubuntu and am using ubuntu 11.10 

Thanks

---

