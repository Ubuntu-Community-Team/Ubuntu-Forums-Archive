---
title: "crontab: How to run GUI programs with cron"
date: 2006-06-01
forum: Tutorials
---

### Post by henriquemaia on 2006-06-01
This is an updated Thread from 5.10. It works on 6.06.


First of all, please refer to this [howto]("http://ubuntuforums.org/showthread.php?t=102626&highlight=cron") to learn more about crontab.


My motivation to find this out was because there are several radio shows I really like and I was always missing them. As such, I needed something to make amarok play the chosen radio station at specific times. Probably this could be achieved through a more elegant solution, but what is explained here works great. Also, I knew that by learning how to do this, I could use it for many other things.

To accomplish this, you have to edit your crontab:

```
crontab -e
```you can also use a nicer GUI tool to edit crontab, like **gnome-schedule** or **KCron** (both available on the repositories).

If you use a GUI tool, please adapt the instructions accordingly. I will explain this using as basis the default crontab editor.

To run a GUI command on cron, you'll have to tell cron what display the program should use. For that you use:

```
export DISPLAY=:0 
```The '**:0**' is the default. If you like the program to run on other display, please change the number accordingly (e.g. **:1**, **:2**, etc).

So, you add to what is explained [here]("http://ubuntuforums.org/showthread.php?t=102626&highlight=cron"):  

```
01 04 * * * /usr/bin/somedirectory/somecommand
```the **export** variable, like this: 

```
01 04 * * * **export DISPLAY=:0** && /usr/bin/somedirectory/somecommand
```You can omit the full path to the application bin. For **amarok**, you just need to use the 'amarok' command. Works fine both ways.

So, in my case, as I want **amarok** to play Antena2 (Portuguese classical radio station) at a specific time, I use:

```
30 16 * * 7     export DISPLAY=:0 && amarok mms://rdp.oninet.pt/antena2 
```This will make amarok start the Antena2 url every Sunday, at 16:30. But I want also to shut up amarok after the show is finished. So, I use:

```
0 17 * * 7     export DISPLAY=:0 && amarok -s

```This will shut up amarok at 17:00 every Sunday.

[SIZE=1](Just a side note - to make amarok play mms urls, you have to set it to use xine engine)[/SIZE]

You can use this export trick to the limits of your imagination with every kind of application you want. 

Another example that occurs to me is when you neet to use an application for a certain period of time, from 3AM to 9AM, for exemple.

```
0 3 * * * export DISPLAY=:0 && your_favorite_application
```that will start **your_favorite_application** (change this to the command that runs the application you desire) everyday at 3AM. To shut it down, I use:

```
0 9 * * * killall your_favorite_application
```This will shut it down at 9AM.

Hope this helps some of you.

If you have more ideas how to use this trick (or how to improve this HowTo), please share with us in this thread.

---

### Post by TomG on 2006-08-31
Thanks a lot ! 
It started to drive me crazy :)

---

### Post by Watcher on 2006-08-31
That is a very neat trick, thank you! (I was looking earlier for something like that)

---

### Post by henriquemaia on 2006-09-13
To both previous posters, I just like to say that I'm very glad that this HowTo helped you. When I found this, I was going mad trying to accomplish this without success. It's really nice to be able to share knowledge.

---

### Post by Shay Stephens on 2006-11-26
Bravo!  Thank you for the info.  This helped me a lot!

---

### Post by nchase on 2007-03-23
Thank you SO much. This is one of the most useful threads I've ever found on this forum. I had been trying to find a fix to this problem for weeks, and none of them worked -- except this one.

---

### Post by kinson on 2007-04-24
Hi henriquemaia,

Firstly, thanks for this useful post :) the DISPLAY=:0 did the trick for me. Previously I was wondering why my stuff didn't run :)

Actually, I have a question though.

When you say "DISPLAY" here, are we talking about desktop workspaces? Cause I have a teeny little problem.

I'm trying to run the command:
```

rhythmbox-client --play-pause"

```

And it does run. The only problem is, that it launches a new instance of rhythmbox(therefore I have 2 music players). If I directly type the command "rhythmbox-client --play-pause" into the terminal, it just pauses/plays the current instance of rhythmbox, and doesn't create a new instance. Is this caused by the DISPLAY? 

Hope you can enlighten me on this :)

Thanks,
Kinson.

---

### Post by rubberglove on 2007-05-05
thanks a million - that did the trick. I was just about to give up altogether...

---

### Post by yeahthisisrob on 2007-07-27
I was just about to give up when I find this... thaanks

---

### Post by seventynine on 2007-12-23
Thanks.

---

### Post by sidefx2 on 2007-12-23
I've been going crazy trying to figure out why I can't get deluge working...

I'm trying to schedule my torrents to automatically turn on at night after I sleep, so I have this in  my crontab:

41 11 * * * DISPLAY=:0 && /usr/bin/deluge

(The time there is just for testing purposes) basically  it seems to execute this command but nothing runs.  Anyone have any idea would I could be doing wrong?

---

### Post by seventynine on 2007-12-23
> **sidefx2 said:**
> I've been going crazy trying to figure out why I can't get deluge working...

I'm trying to schedule my torrents to automatically turn on at night after I sleep, so I have this in  my crontab:

41 11 * * * DISPLAY=:0 && /usr/bin/deluge

(The time there is just for testing purposes) basically  it seems to execute this command but nothing runs.  Anyone have any idea would I could be doing wrong?

here's my working one:
> 0 0 * * * export DISPLAY=:0 && deluge           #start torrents
0 6 * * * killall -9 deluge                     #stop torrents


you're just missing "export" in your line, it seems

---

### Post by sidefx2 on 2008-01-03
That was the problem, thanks a lot!

---

### Post by FooAtari on 2008-01-15
Is there a way to select which Desktop the application opens on?

I'm using crontab to stop and start klibido and it works great.  However I would like to open on Desktop 2 if possible?

Thanks

---

### Post by henriquemaia on 2008-01-15
> **FooAtari said:**
> Is there a way to select which Desktop the application opens on?

I'm using crontab to stop and start klibido and it works great.  However I would like to open on Desktop 2 if possible?

Thanks

Just change the 

DISPLAY=:**0**

to the number of the display where you want to run the application.

ex:

DISPLAY=:**1**

or

DISPLAY=:**2**

---

### Post by FooAtari on 2008-01-16
Hmmm, Ok, ill try that.  When I tried it before Klibido didn't load at all.  Maybe I made a mistake though I'll try it again

Ta

---

### Post by henriquemaia on 2008-01-16
> **FooAtari said:**
> Hmmm, Ok, ill try that.  When I tried it before Klibido didn't load at all.  Maybe I made a mistake though I'll try it again

Ta

On the display you want to run the application, run the following command (from a terminal emulator):

```
echo $DISPLAY
```It will give you something like this, (according to the display you’re running):

:0.0

For instance, I opened another display through issuing a 

```
xinit -- :2
```and when I ran

```
echo $DISPLAY
```I got:

:2.0

---

### Post by FooAtari on 2008-01-16
Ok I get 0.0 on both desktops

Maybe I wasn't clear.  I only have one display, maybe workspace is a better word.  I want to open Klibido on workspace 2.

---

### Post by henriquemaia on 2008-01-16
> **FooAtari said:**
> Ok I get 0.0 on both desktops

Maybe I wasn't clear.  I only have one display, maybe workspace is a better word.  I want to open Klibido on workspace 2.

For that you will have to mess with your window manager options or use some software like [Devil’s Pie]("http://burtonini.com/blog/computers/devilspie"). I’m not sure if this helps.

---

### Post by FooAtari on 2008-01-16
I'll figure something out.  Thanks for trying :)

---

### Post by euphemus on 2008-10-25
Problem solved - I switched from crond to fcron and I could execute a program with a word - like "firefox" or "kaffeine" or "limewire"

Great - I'll use fcron from now on.

---

### Post by meg23 on 2008-12-10
Praise the lord! It works!

---

### Post by arunprasad13 on 2008-12-27
hi..i have ubuntu edgy 6.10 ..i m not able to run azureus at a particular time in gui...i have copied the different option which i tried and pasted here.

arun@arun-desktop:/opt/azureus$ sudo crontab -e
crontab: installing new crontab
arun@arun-desktop:/opt/azureus$ sudo crontab -l
# m h  dom mon dow   command
39 00 * * * export DISPLAY=:0 && ./azureus
arun@arun-desktop:/opt/azureus$ sudo crontab -e
crontab: installing new crontab
arun@arun-desktop:/opt/azureus$ sudo crontab -l
# m h  dom mon dow   command
41 00 * * * export DISPLAY=:0 && /opt/azureus/azureus
arun@arun-desktop:/opt/azureus$ sudo crontab -e
crontab: installing new crontab
arun@arun-desktop:/opt/azureus$ sudo crontab -l
# m h  dom mon dow   command
43 00 * * * env DISPLAY=:0.0 /opt/azureus/azureus
arun@arun-desktop:/opt/azureus$ sudo crontab -e
crontab: installing new crontab
arun@arun-desktop:/opt/azureus$ sudo crontab -e
crontab: installing new crontab
arun@arun-desktop:/opt/azureus$ sudo crontab -l
# m h  dom mon dow   command
45 00 * * * env DISPLAY=:0.0 ./azureus
arun@arun-desktop:/opt/azureus$ 

pl help

---

### Post by steve101101 on 2009-04-16
thanks

---

### Post by jelevin on 2009-11-22
Is there a way to use this even if there isn't a display running (i.e., on a headless server)?

---

### Post by henriquemaia on 2009-11-22
> **jelevin said:**
> Is there a way to use this even if there isn't a display running (i.e., on a headless server)?

Well, of course. cron main use is precisely that, to be used on servers, headless or not. But probably what you want is on another thread. Try searching for crontab tutorials on these forums.

---

### Post by sparklyprgs on 2010-05-24
Excellent! Bad thing is it took over an hour of pain to find this out but it was worth it in the end.

---

### Post by coskibukowski on 2010-05-28
Just **THANKS**!

---

### Post by ccczzx on 2011-12-01
Thanks is not enough to express my feelings!
And Thanks all of you!

---

### Post by thiyagi on 2011-12-01
Thanks, was useful..

---

### Post by rob2468 on 2013-01-12
```
export DISPLAY=:0.0 && /usr/bin/gnome-terminal
```
There is something different between GUI app started from cron and normal ways. In terminal, env variables for example are not the same. Settings set in .bashrc do not work.
What's different between cron and normal ways. I'm curious about it.

---

### Post by henriquemaia on 2013-01-12
> **rob2468 said:**
> ```
export DISPLAY=:0.0 && /usr/bin/gnome-terminal
```
There is something different between GUI app started from cron and normal ways. In terminal, env variables for example are not the same. Settings set in .bashrc do not work.
What's different between cron and normal ways. I'm curious about it.

If unspecified, they're started as root (or as the cron user). You have to specify the user for it. This will set the proper environment variables.

Example:
11 * * * *  your_user_here   /path/to/command
<timing>    <user>           <command>

---

### Post by noisygecko on 2013-08-27
One thing that a lot of people probably don't realize is that you can set environment variables for a specific command by just putting them in front of the line.  So, for the example of setting the DISPLAY variable in this thread, you can do this in cron:

```

0 11 * * *  DISPLAY=:0 /usr/bin/gnome-terminal

```

Just make sure you only put spaces in between the variable setting and the command.  It is actually more useful in other cases where you only want to change an environment variable for a specific command.

---

