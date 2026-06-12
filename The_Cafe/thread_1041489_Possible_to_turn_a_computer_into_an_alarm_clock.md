---
title: "Possible to turn a computer into an alarm clock?"
date: 2009-01-16
forum: The Cafe
---

### Post by hatten on 2009-01-16
I have a hard time getting up on the mornings (no i won't leave the comp earlier!:P) and my alarm clock sucks so i thought if it was possible to make the computer boot/revive from suspend/or just stay powered on the whole night and at a specific time start rythmbox (or any program) that starts playing music.

I believe that have the computer booting from power-off state can be like impossible to do, but if it's possible i will...be happy

Reviving from suspend could be able, or? 

Doing it while the screen is locked (alternatively not even that) must be possible to do, right? Isn't it just to have a timer/countdown of some sort before launching a script?

I'm not entirely experienced with ubuntu, a few months, so don't tell me  do that, say do like this. (more detailed)

---

### Post by JoshuaRL on 2009-01-16
I'd suggest Songbird.  You can get the deb from [www.getdeb.net](www.getdeb.net), and install it the normal way.  Then go to the addons page and install Morning Peeps.  It is an alarmclock addon, with a few features.  Works for me.

---

### Post by uberdonkey5 on 2009-01-16
I think you have to keep the power on for this though?? (hmm not very environmentaly friendly).

If you want your computer to boot up you need to have an appropriate bios (basically, your software runs when computer has power, so how does it know it boot up??)

These links may help:
[http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)
[http://ubuntuforums.org/archive/index.php/t-317927.html](http://ubuntuforums.org/archive/index.php/t-317927.html)

An alternative is to use the alarm on your mobile phone :D

---

### Post by hatten on 2009-01-16
BIOS setting found and changed :popcorn:

But now it will boot to a login prompt. Of course i can skip that (right?) if i have to. But is it possible to have it start playing at login prompt, or only skip login prompt when BIOS have powered it on.

I'm playing around with songbird and are gonna look at startup applications. (that's what i should use, right?)

---

### Post by hatten on 2009-01-16
If i boot comp at 6.55, skip login prompt, put songbird in startup applications and uses morningpeeps to start at 7.00. done:popcorn:


It is just the login prompt, I don't want anybody to be able to boot my comp and check all my personal stuff...

---

### Post by damis648 on 2009-01-16
I wrote a script for this a while back.
[http://ubuntuforums.org/showpost.php?p=6227380&postcount=18](http://ubuntuforums.org/showpost.php?p=6227380&postcount=18)
Directions here:
[http://ubuntuforums.org/showpost.php?p=6225125&postcount=15](http://ubuntuforums.org/showpost.php?p=6225125&postcount=15)

You will need festival first, though. Have a look at [this]("http://ubuntuforums.org/showthread.php?t=751169") guide.

Cheers!

---

### Post by hatten on 2009-01-16
cool, but that's not what i want. But thanks anyway, i found out a way to use Rythmbox instead of songbird there too:P


Off to rebooting, hope it works =D

---

### Post by pp. on 2009-01-16
> **hatten said:**
> It is just the login prompt, I don't want anybody to be able to boot my comp and check all my personal stuff...

Perhaps you can run some application without logging in, much like a daemon?

---

### Post by hatten on 2009-01-16
EVerything works perfect...except for that Rythmbox refuses to start playing:(

system>preferences>sessions
I have added pidgin, transmission and checkgmail as simply one-word commandos that launches them.

I use the commando ```
rhythmbox-client --hide ; sleep 10 ; rhythmbox-client --play
```for rythmbox, it works perfect in terminal but at rebooting it doesn't start to play for some reason.


Help will be appreciated


solved, i moved the code above into a file and let the startup manager launch that file. working. Let's see what happends tomorrow:guitar:



cannot the startup manager handle ";"'s?

---

### Post by hatten on 2009-01-17
worked to perfection:popcorn:

Only thing i don't like is that now anybody can reboot my computer and get straight to my files, I'm thinking of making a new account just for that.

---

### Post by billgoldberg on 2009-01-17
I just leave my pc on.

You could write a script and use cron to run it every morning.

But I just type in the command before I go to sleep.

I use this:

```
sleep 8h && vlc /path/to/music.mp3
```

This will play a music file 8 hours after entering the command.

You will need to keep the terminal window open.

---

### Post by xouns on 2009-01-23
But when I use (for instance) vlc /path/to/playlist(with brackets).m3u it says "bash: syntax error near unexpected token `('" and it won't run.

I have installed the program called Alarm Clock and it has the function to run a script at a specific time. What script should I use to let vlc run a playlist?

---

### Post by xouns on 2009-01-23
Ok, I get it, I can use

vlc "/path/to/any file/on my (harddisk).m3u"

And it works! Forgot to turn my volume down again. Since I use Ubuntu for downloading mostly, I leave my computer on during the nights, so that's not really a problem. This works great.

BTW, I love the test function in Alarm Clock, it saves me the annoyance of a not working alarm!

---

### Post by thegreenblob on 2009-01-23
I use a program called alarm-clock. Which I don't use it to wake me up but it can be used that way :P

```
sudo apt-get install alarm-clock
```

And just set it to run a command at a certain time. Such as:

```
vlc /path/to/a/mp3.mp3
```

---

### Post by andrewpmk on 2009-01-23
You don't even have to do that - you can set alarm-clock to play a sound file directly.

---

### Post by 3rdalbum on 2009-01-23
```
 at now + 8 hours
play "alarm.wav"

```

Then press Control-D, and in 8 hours time the sound file will play.

---

### Post by hatten on 2009-02-05
Okay, i wanna wake up, keep my computer turned off and still save my uptime, by putting it into sleep mode or hibernating.

I read at a (vista) forum that the bios won't start the computer at a special time if the computer is hibernated, is it the same for linux?

Is it possible to wake by computer from sleep by running a command or anything similar?

---

### Post by Wv0wvw88wvw0vW on 2009-02-06
Try KAlarm from Add/Remove Applications.

---

### Post by sharon.gmc on 2009-02-06
I also use Songbird.  I love it.

---

### Post by hatten on 2009-02-06
Heck, are you even reading my post/earlier posts before replying? Well, thanks for trying anyway.

I found out that it worked to perfection to start playing music and then hibernating without pausing or stopping, then bios will boot my comp at a specified time and it will go directly to a locked screen asking me to enter possward while still playing music.:popcorn:

---

### Post by Nevon on 2009-02-06
I've submitted an idea to brainstorm about this. I'd like to see an alarm function intergrated into the gnome-panel clock applet.

[http://brainstorm.ubuntu.com/idea/17496/](http://brainstorm.ubuntu.com/idea/17496/)

---

### Post by mockdeep on 2009-02-24
Hey everybody,

I'm trying to create an alarm clock script to wake me up in the morning and I'm having a problem getting it to run properly in cron.  It looks like this:

#!/bin/bash
rhythmbox &
sleep 5
amixer -c 0 set Master 0% > /dev/null
rhythmbox-client --play
rhythmbox-client --hide
for ((x=0; x<100; x++))
do
    amixer -c 0 set Master $x% > /dev/null
    sleep 1
done

Basically, it starts rhythmbox music player and plays the default playlist while gradually increasing the volume.  When I run it on its own it works fine, but when I add it to cron it doesn't.  I added this line:

*/5 *    * * *   root /home/me/scripts/alarm.sh

Occasionally when it runs I will see rhythmbox pop up and quickly disappear, but it never starts playing.  I can tell the script is running as the 'for' loop hijacks the volume control for 100 seconds until it's finished.  Any ideas why it's not working?  Could it have anything to do with the fact that rhythmbox is a graphical player?

---

### Post by keypox on 2010-08-27
Any gui based program ever come out for this?

---

### Post by Ric_NYC on 2010-08-27
Applications > Ubuntu Software Center... type "alarm"... enter
:p

---

### Post by keypox on 2010-08-28
> **Ric_NYC said:**
> Applications > Ubuntu Software Center... type "alarm"... enter
:p

really? It will wake computer from suspend? No extra setup? I can't find any options that mentions suspend in the program.

---

### Post by keypox on 2010-08-28
Is there any alarm that will wake the computer from suspend mode?  Mac and windows have had these for years...

---

### Post by smellyman on 2010-08-28
I suggest your mobile phone.....

---

### Post by nrs on 2010-08-28
> **mockdeep said:**
> Hey everybody,

I'm trying to create an alarm clock script to wake me up in the morning and I'm having a problem getting it to run properly in cron.  It looks like this:

#!/bin/bash
rhythmbox &
sleep 5
amixer -c 0 set Master 0% > /dev/null
rhythmbox-client --play
rhythmbox-client --hide
for ((x=0; x<100; x++))
do
    amixer -c 0 set Master $x% > /dev/null
    sleep 1
done

Basically, it starts rhythmbox music player and plays the default playlist while gradually increasing the volume.  When I run it on its own it works fine, but when I add it to cron it doesn't.  I added this line:

*/5 *    * * *   root /home/me/scripts/alarm.sh

Occasionally when it runs I will see rhythmbox pop up and quickly disappear, but it never starts playing.  I can tell the script is running as the 'for' loop hijacks the volume control for 100 seconds until it's finished.  Any ideas why it's not working?  Could it have anything to do with the fact that rhythmbox is a graphical player?
Cron neuters PATH, to what extent I do not know. Try doing echo $PATH in your terminal and copy the result to your script.

---

### Post by mamamia88 on 2010-08-30
```
sleep 8h && vlc /path/to/music.mp3
```

This will play a music file 8 hours after entering the command.

You will need to keep the terminal window open.[/QUOTE]  taking this one step farther you can create a simple bash script that will let play a song file after a certain user defined interval  paste this into gedit and save it as whatever.sh.  

#!/bin/bash
cd /home/username/music
sleep amount of time (h,m,s) && vlc nameofmusicfile.mp3

of course be sure to replace username with your username and correct name of the mp3.  make the script executable and run it in a terminal.  all you have to do is edit the amount of time depending on when you want to wake up.

---

### Post by markp1989 on 2010-08-30
> **mamamia88 said:**
> ```
sleep 8h && vlc /path/to/music.mp3
```

This will play a music file 8 hours after entering the command.

You will need to keep the terminal window open.  taking this one step farther you can create a simple bash script that will let play a song file after a certain user defined interval  paste this into gedit and save it as whatever.sh.  

#!/bin/bash
cd /home/username/music
sleep amount of time (h,m,s) && vlc nameofmusicfile.mp3

of course be sure to replace username with your username and correct name of the mp3.  make the script executable and run it in a terminal.  all you have to do is edit the amount of time depending on when you want to wake up.[/QUOTE]

you could also have it so when you run the script you set the time like this: 



```
#!/bin/bash
cd /home/username/music
sleep $1$2 && vlc nameofmusicfile.mp3

```

then run it like this 
```
/path/to/script.sh 1 h
```   for 1 hour delay .


a good option would be to use cron + mpd, becuase it would run even if your not loged in .

---

### Post by mamamia88 on 2010-08-30
what do the dollar signs do?  is there a way to set up the script to play a music file at certain time?  how about setting am pm?  kind of curious i'm kind of new to this whole scripting thing in fact i seriously only started playing around with them yesterday.

---

### Post by markp1989 on 2010-08-31
> **mamamia88 said:**
> what do the dollar signs do?  is there a way to set up the script to play a music file at certain time?  how about setting am pm?  kind of curious i'm kind of new to this whole scripting thing in fact i seriously only started playing around with them yesterday.

$1 is the first command line parameter you parse to the script $2 is the 2nd etc. 

eg: 

mark@mark-laptop:~$ /path/to/script.sh parameter1 parameter2

in this case, $1=parameter1 and $2=parameter2

for more info , see here [http://linuxreviews.org/beginner/bash_GNU_Bourne-Again_SHell_Reference/#toc7](http://linuxreviews.org/beginner/bash_GNU_Bourne-Again_SHell_Reference/#toc7)

---

