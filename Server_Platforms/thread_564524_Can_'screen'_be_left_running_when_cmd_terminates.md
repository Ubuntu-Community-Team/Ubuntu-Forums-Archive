---
title: "Can 'screen' be left running when cmd terminates?"
date: 2007-10-01
forum: Server Platforms
---

### Post by gerbilsonh on 2007-10-01
I'm trying to use screen with a cmd (in my case in daemon mode with -dm but I don't think it matters). 

However, whenever the command exits, screen also terminates, making me lose all the output from the command. Is there any way to get screen to exit into a shell but still be running detached if the command exits for some reason?

---

### Post by scruff on 2007-10-01
I simply start a screen session like:

```

# screen

```

and leave it running for months. I'm frequently ssh'd into my home machine from work, and I run things I know won't complete before I leave the office. I just close the terminal I am using at work, go home and type:

```

# screen -Dr

```

and I reconnect to the screen session with any and all output that I missed while commuting. Try running it this way and see how it goes.

---

### Post by Brazen on 2007-10-01
Yeah, that's essentially the same way I use it, and the session gets left open after commands complete.

One thing I might mention though, is instead of just killing your ssh terminal, detach from the screen console with "ctl-a, d".  Then you reattach to it with "screen -r".

Some other usefull commands are "ctl-a, c" to create a new screen window, then "ctl-a, n" to cycle through the windows.  You can also forcibly kill the current screen window with "ctl-a, k".

As long as you remember "ctl-a, ?" then you can also look up these commands in the list that is displayed with this command.

---

### Post by gerbilsonh on 2007-10-01
Hi and thanks for all the replies. 

However, I specifically want to start screen with a command, since I'm starting it from a cron job.  But then, if something fails all the output is lost.

Although I guess I could have the cron job reattach to a specific screen session instead of starting its own. 

Still, there must be a way to tell screen to stay alive after the cmd it runs is dead, no?

---

### Post by scruff on 2007-10-01
How about just sending output to a file so you can examine it later?

0 2 * * * cmd > /home/user/textfile

You can even get control over what types of output to send to the file if you like. Google stdout stderr redirection.

---

### Post by scruff on 2007-10-01
As far as telling screen to stay alive when running in daemon, I have no idea. Never used it that way, sorry. However, if all you want is the output to remain, skip screen altogether and do as I suggested above.

---

### Post by gerbilsonh on 2007-10-01
Ok, I found a crappy (but working) solution. Still on the lookout for something better...

[LIST=1]

[*]Put this in my .tcshrc file:

```

if ($?FROMCRON) then
   <the command>
endif
```

[*]Make a new .screenrc.cron file with a single line:

```

set tcsh
setenv FROMCRON 1

```

[*]Put this in my crontab:

```

0 4 * * *  screen -dmS myscreen -c /home/robots/.screenrc.cron
```

[/LIST]

---

### Post by scruff on 2007-10-01
Just curious - is there something I am missing? It doesn't seem like  screen is the best solution from your description or the problem, that is why I am asking.

Nice workaround on screen tho :)

---

### Post by gerbilsonh on 2007-10-02
my command runs for about 18 hours when it does, starting every day at 4am, and screen is a nice way to "check in on it", although i guess i could always just tail the output file. that would mean, though that i need to change all my print-outs to flush stdout, which is something i don't usually like doing. 

more than anything - screen was the way i did it when i ran the long-running command manually, and now that it runs automatically i didn't want to change much around. plus it's disconcerting that i can't run a command in screen that would exit into a shell when it's done or crashes.

---

