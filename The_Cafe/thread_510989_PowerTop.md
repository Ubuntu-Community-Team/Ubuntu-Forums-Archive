---
title: "PowerTop"
date: 2007-07-27
forum: The Cafe
---

### Post by Kosimo on 2007-07-27
Should we take care about it?
Will Gutsy have some of this options enabled by default?
I really wish to have the same Lifetime with Ubuntu than in Win...  
(3 hours in win)
(1:30 hours in ubuntu...)  :-(

---

### Post by Kosimo on 2007-07-27
By the way this is the link:


[PowerTop]("http://linuxpowertop.org/faq.php")

---

### Post by Sayers on 2007-07-27
I'm sure there are some settings that *you* need to configure. However I'm not a laptop user so I don't have much to comment.

---

### Post by apoth on 2007-07-30
I think it's great. I get longer battery life in Ubuntu than Windows but powertop's helped me extend that already.

---

### Post by Kosimo on 2007-07-30
> **apoth said:**
> I think it's great. I get longer battery life in Ubuntu than Windows but powertop's helped me extend that already.

How did you install it?

---

### Post by prizrak on 2007-07-30
I only have like 10 minute difference between Windows and Linux on my laptop and that's with Beryl running on Ubuntu. I think it depends more on ACPI than anything else really

---

### Post by apoth on 2007-07-31
> **Kosimo said:**
> How did you install it?

I'm running Gutsy, it's in the repositories for it.

---

### Post by incubus on 2007-08-02
Kosimo,

Did you get to install it?  If not, you'd do something in the lines of:
```

First, install the dependencies:
$ sudo apt-get install build-essential libncurses5-dev libncursesw5-dev

Now, let's compile powertop
$ tar xvf powertop-1.7.tar.gz
$ cd powertop-1.7
$ make
$ sudo make install

The last command installs powertop in /usr/bin/, so now you can run it through:
$ sudo powertop

```

Note that you have to run powertop with root privileges.

Happy hacking,

incubus

EDIT: Added ncurses dependencies, thanks to reacocard.

---

### Post by Kosimo on 2007-08-02
> **incubus said:**
> Kosimo,

Did you get to install it?  If not, you'd do something in the lines of:
```

$ sudo apt-get install build-essential
$ tar xvf powertop-1.7.tar.gz
$ cd powertop-1.7
$ make
$ sudo ./powertop

$ # To install (i.e., copy the executable to /usr/bin/)
$ sudo make install 

```

Note that you have to run powertop with root privileges.

Happy hacking,

incubus


No, I couldn't! Thanks for your answer.

But this code works for Feisty or Gutsy?

---

### Post by reacocard on 2007-08-02
> **Kosimo said:**
> No, I couldn't! Thanks for your answer.

But this code works for Feisty or Gutsy?

feisty, but you may need to install build-essential and the ncursus dev packages before it'll work.

I get about the same battery life in windows and ubuntu, 6-7 hours.

---

### Post by Kosimo on 2007-08-02
> **reacocard said:**
> feisty, but you may need to install build-essential and the ncursus dev packages before it'll work.

I get about the same battery life in windows and ubuntu, 6-7 hours.

Was following your guide since "make"

I got this message from the terminal:

> /Desktop/powertop-1.7$ make
cc -Os -g -Wall  -W -Wshadow   -c -o powertop.o powertop.c
powertop.c: In function ‘main’:
powertop.c:375: warning: unused parameter ‘argc’
powertop.c:375: warning: unused parameter ‘argv’
cc -Os -g -Wall  -W -Wshadow   -c -o config.o config.c
cc -Os -g -Wall  -W -Wshadow   -c -o process.o process.c
cc -Os -g -Wall  -W -Wshadow   -c -o misctips.o misctips.c
cc -Os -g -Wall  -W -Wshadow   -c -o bluetooth.o bluetooth.c
cc -Os -g -Wall  -W -Wshadow   -c -o display.o display.c
display.c:32:21: error: ncurses.h: No such file or directory
display.c:38: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
display.c:39: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
display.c:40: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
display.c:41: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
display.c:42: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
display.c:43: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
display.c:44: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
display.c: In function ‘cleanup_curses’:
display.c:50: warning: implicit declaration of function ‘endwin’
display.c: In function ‘zap_windows’:
display.c:55: error: ‘title_bar_window’ undeclared (first use in this function)
display.c:55: error: (Each undeclared identifier is reported only once
display.c:55: error: for each function it appears in.)
display.c:56: warning: implicit declaration of function ‘delwin’
display.c:59: error: ‘cstate_window’ undeclared (first use in this function)
display.c:63: error: ‘wakeup_window’ undeclared (first use in this function)
display.c:67: error: ‘acpi_power_window’ undeclared (first use in this function)
display.c:71: error: ‘timerstat_window’ undeclared (first use in this function)
display.c:75: error: ‘suggestion_window’ undeclared (first use in this function)
display.c:79: error: ‘status_bar_window’ undeclared (first use in this function)
display.c: In function ‘setup_windows’:
display.c:93: warning: implicit declaration of function ‘getmaxyx’
display.c:93: error: ‘stdscr’ undeclared (first use in this function)
display.c:97: error: ‘title_bar_window’ undeclared (first use in this function)
display.c:97: warning: implicit declaration of function ‘subwin’
display.c:98: error: ‘cstate_window’ undeclared (first use in this function)
display.c:99: error: ‘wakeup_window’ undeclared (first use in this function)
display.c:100: error: ‘acpi_power_window’ undeclared (first use in this function)
display.c:101: error: ‘timerstat_window’ undeclared (first use in this function)
display.c:104: error: ‘suggestion_window’ undeclared (first use in this function)
display.c:105: error: ‘status_bar_window’ undeclared (first use in this function)
display.c:110: warning: implicit declaration of function ‘werase’
display.c:111: warning: implicit declaration of function ‘refresh’
display.c: In function ‘initialize_curses’:
display.c:116: warning: implicit declaration of function ‘initscr’
display.c:117: warning: implicit declaration of function ‘start_color’
display.c:118: warning: implicit declaration of function ‘keypad’
display.c:118: error: ‘stdscr’ undeclared (first use in this function)
display.c:118: error: ‘TRUE’ undeclared (first use in this function)
display.c:119: warning: implicit declaration of function ‘nonl’
display.c:120: warning: implicit declaration of function ‘cbreak’
display.c:121: warning: implicit declaration of function ‘noecho’
display.c:122: warning: implicit declaration of function ‘curs_set’
display.c:123: warning: implicit declaration of function ‘use_default_colors’
display.c:125: warning: implicit declaration of function ‘init_pair’
display.c:125: error: ‘COLOR_WHITE’ undeclared (first use in this function)
display.c:125: error: ‘COLOR_BLACK’ undeclared (first use in this function)
display.c:127: error: ‘COLOR_RED’ undeclared (first use in this function)
display.c:129: error: ‘COLOR_YELLOW’ undeclared (first use in this function)
display.c:130: error: ‘COLOR_GREEN’ undeclared (first use in this function)
display.c: In function ‘show_title_bar’:
display.c:140: warning: implicit declaration of function ‘wattrset’
display.c:140: error: ‘title_bar_window’ undeclared (first use in this function)
display.c:140: warning: implicit declaration of function ‘COLOR_PAIR’
display.c:141: warning: implicit declaration of function ‘wbkgd’
display.c:144: warning: implicit declaration of function ‘mvwprintw’
display.c:146: warning: implicit declaration of function ‘wrefresh’
display.c:148: error: ‘status_bar_window’ undeclared (first use in this function)
display.c:154: warning: implicit declaration of function ‘wattron’
display.c:154: error: ‘A_REVERSE’ undeclared (first use in this function)
display.c:156: warning: implicit declaration of function ‘wattroff’
display.c: In function ‘show_cstates’:
display.c:165: error: ‘cstate_window’ undeclared (first use in this function)
display.c:169: error: ‘A_BOLD’ undeclared (first use in this function)
display.c: In function ‘show_acpi_power_line’:
display.c:193: error: ‘acpi_power_window’ undeclared (first use in this function)
display.c: In function ‘show_wakeups’:
display.c:211: error: ‘wakeup_window’ undeclared (first use in this function)
display.c:219: error: ‘A_BOLD’ undeclared (first use in this function)
display.c: In function ‘show_timerstats’:
display.c:227: error: ‘timerstat_window’ undeclared (first use in this function)
display.c:235: error: ‘A_BOLD’ undeclared (first use in this function)
display.c: In function ‘show_suggestion’:
display.c:258: error: ‘suggestion_window’ undeclared (first use in this function)
make: *** [display.o] Error 1


Any idea?

---

### Post by reacocard on 2007-08-02
> **Kosimo said:**
> Was following your guide since "make"

I got this message from the terminal:



Any idea?

As I said, you need the ncurses dev package:
```
sudo apt-get install libncurses5-dev libncursesw5-dev
```

---

### Post by incubus on 2007-08-05
Sorry guys, I've been busy lately and wrote my post from memory.  I fixed it, so that other people avoid that issue.

Thanks,

incubus

---

### Post by shof2k on 2007-08-28
I took the liberty of writing up a simple HOWTO at [http://ubuntuforums.org/showthread.php?p=3256380#post3256380](http://ubuntuforums.org/showthread.php?p=3256380#post3256380), mentioning this post as my source.

Feel free to read and post your comments.

---

### Post by sudo_t43p on 2007-09-04
Hi all,

How many W is your computer using? I tested this morning what is the min. W and 9.6W was my "record". Average is 12.6W

I think I have a bug with my Intel gfx, when running e.g compiz / beryl my gfx is on the first place on my hall of shame list (see attatchment) :(

Is there a way of getting lower wakeups on Intels 3945 card? I would like to "disable/standby" it when there is no activity.

BR,
Chrisse

---

### Post by ChamPro on 2007-09-04
PowerTop runs fine on my Gutsy server, but I can't get the changes that program makes to stick.

I run PowerTop and then after I reboot, I run PowerTop again and it goes through all the same steps.

Here are the changes PowerTop suggests:
A - Turn AC97 powersave on
W - Increase writeback time
U - Enable USB suspend
T - Enable noatime

---

### Post by Kosimo on 2007-09-04
> **ChamPro said:**
> PowerTop runs fine on my Gutsy server, but I can't get the changes that program makes to stick.

I run PowerTop and then after I reboot, I run PowerTop again and it goes through all the same steps.

Here are the changes PowerTop suggests:
A - Turn AC97 powersave on
W - Increase writeback time
U - Enable USB suspend
T - Enable noatime

I'm experiencing exactly the same issues .
Does powertop need to be running all time in order to have this power savings enabled?  
Do I have to enable them each time I run powertop?
When powertop in a simple and nice GUI?

---

### Post by sudo_t43p on 2007-09-05
> **Kosimo said:**
> I'm experiencing exactly the same issues .
Does powertop need to be running all time in order to have this power savings enabled?  
Do I have to enable them each time I run powertop?
When powertop in a simple and nice GUI?

You have to enable the right kernel modules and / or modify the bootup script

---

### Post by bruce89 on 2007-09-05
There is no point in using Powertop in feisty and below, it needs a 2.6.22 kernel to do anything interesting.

---

### Post by zorkerz on 2007-09-22
I just installed powerTOP today. Im trying to figure out how to use it. Im running gutsy so i have a new enough kernel.

Basically im trying to maximize my power efficiency. What are the key areas that powertop can help withhere?

Right now im averaging around  16.5 w on batter that seems like a very hight number I would like to get it down.

im also waking up from idle often 200 times a second. I read on lesswatts.org that you could get this down to 3 with GNOME so I figure I should improve this some how.

Id also like to disable bluetooth since i use it little.

Where do I start?
thanks

---

### Post by UbuWu on 2007-09-23
For more tips to save energy: [http://www.lesswatts.org/](http://www.lesswatts.org/)

---

