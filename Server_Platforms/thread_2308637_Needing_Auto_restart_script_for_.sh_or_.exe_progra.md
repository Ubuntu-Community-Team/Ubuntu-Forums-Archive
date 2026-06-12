---
title: "Needing Auto restart script for .sh or .exe program"
date: 2016-01-04
forum: Server Platforms
---

### Post by Higgins909 on 2016-01-04
I need a script that, when I have the game server  set to shutdown after some hours, it will automatically restart the game server.
I don't know if it's a exe or what, windows explorer properties just says its a file. (it's not restarting the whole server, just the app)
What language is this script in? (I have some programming curiosity)

Thanks,
Higgins909

---

### Post by nerdtron on 2016-01-04
A bash script can do this. Since you are familiar with programming, then the flow is easy to understand.
1. Check running processes to see if "Game server" is not running.
2. If true, then restart the "Game server", else, do nothing.

Then just save this script file and set it to run on regular intervals, say every 5 minutes.

```

#!/bin/bash

# Test is the process is running using the if statement. 
if ! ps -ef | grep [n]tp ;
then
      echo "program ntp is not running - run the program"
      # [insert command to start the app here]
else
      echo "program ntp is running - nothing to do"
      exit
fi

```

---

### Post by Higgins909 on 2016-01-04
I seem to have forgotten to mention that I run the game server process in a screen(screen -S).
And that I think it requires a active terminal?  Don't think it will work as only a background process like ts3 severs will.
Depending how much resources that script will use, I may end up setting it to run 30-60 seconds, because the server has a countdown till shutdown.
I want it to be back up as quickly as possible.  Otherwise i'm not sure how easily I could sync the two.

I know how to setup a crontab (think that's what it was called, i'm a bit rusty as I use it only when first setting the server up)
I also only know very minimal about programming.  I've tried to learn many languages but never got much further then "hello world".
But I still find programming interesting, and like to try and understand bits and pieces.

But yeah, how is this going to work with the process running through a screen?

---

### Post by nerdtron on 2016-01-05
First test the program to run on a screen using a single command:

```
 /usr/bin/screen -d -m -S "screen-name" /full/path/command/of/the/program.sh 
```

If the above command is successful, then you should have a new screen, and running process inside it. Now that whole line is the one you'll insert to the the above script (below the "program not running" line).


For crontab setup, the minimum frequency is every minute. 
1. You save the script, say /home/username/script.sh
2. You test the script that if functions properly
```
 /bin/bash /home/username/script.sh 
```

3. If the above is successful, then add it to the crontab entry
```
 crontab -e 
```
If you need root to launch the program, add it to the root crontab instead.
```
 sudo crontab -e 
```

4. You will be presented with the cron table, add this entry to run it every minute:
```
 * * * * * /bin/bash /home/username/script.sh 
```

5. Save the crontab and exit. Wait for it to trigger on the next minute.

---

### Post by Higgins909 on 2016-01-06
unfortunately I was not able to start the program like that.
It seems that it has to be started, while in it's dir.
Otherwise it won't work because of all the stuff that is after the program, or I was having issues with the program finding steam.
This is what I was trying to go for, but it ended up opening another program every minute along with screen not working.
Screen may not be working as I saw it being used like that in another bash script.
```

#!/bin/bash
#cd /home/admin-ben/Steam/steamapps/common/Arma\ 3\ Server
# Test is the process is running using the if statement.
if ! ps -ef | grep [n]tp ;
then
      echo "program ntp is not running - run the program"
      cd /home/admin-ben/Steam/steamapps/common/Arma\ 3\ Server
      screen -dmS arma
      ./arma3server >>/home/admin-ben/gameserver/logs/log.rpt 2>&1 -mod=@Exile\;@mas\;@NATO_Rus_Vehicle -servermod=@ExileServer -config=@ExileServer/config.cfg -port=2302 -profiles=SC -cfg=@ExileServer/basic.cfg -name=SC -autoinit -filePatching
else
      echo "program ntp is running - nothing to do"
      exit
fi

```

---

### Post by nerdtron on 2016-01-06
Why are you checking the ntp process? you shoudl check the arma3 process instead of ntp.

The "screen" command and the ./arma3server command should be on a single line.

Also the space on the "Arma 3 Server" folder name can cause problems on launching the program, and you can use absolute path to make sure the program is located properly:

Try to run this command manually and see if it creates a screen properly.
```
cd /home/admin-ben/Steam/steamapps/common/Arma\ 3\ Server
screen -dmS arma      ./arma3server >> /home/admin-ben/gameserver/logs/log.rpt 2>&1 -mod=@Exile\;@mas\;@NATO_Rus_Vehicle -servermod=@ExileServer -config=@ExileServer/config.cfg -port=2302 -profiles=SC -cfg=@ExileServer/basic.cfg -name=SC -autoinit -filePatching 
```

---

### Post by Higgins909 on 2016-01-06
> **nerdtron said:**
> Why are you checking the ntp process? you shoudl check the arma3 process instead of ntp.
I don't know how to have it check the arma3server process instead :/  I only got to the basics on programming, but understand...
maybe its called the arithmetic? A bit more then regular people.

Your code has worked.

What is "absolute path"? heheh turing into 20 questions. Edit: I think I know what full path is.

I knew I was doing something wrong with that part of the line, but couldn't figure out what.
I can get the whole screen + arma3server line to work, when I manually enter it, when in the arma3server dir.
But I think I've still done something wrong with line 3 of the code, it now says that arma3server is always running?
New nubers every time, for bith sets.
```

admin-ben@LangweilerG:~$ sudo ./armaboot.sh
root      1505  1503  0 20:58 pts/1    00:00:00 grep arma3server

```
Also in the script, does home need the have a slash before it or not? (Found out it does, but not sure why)
```

#!/bin/bash
# Test is the process is running using the if statement.
if ! ps -ef | grep arma3server ; #<< I even tried to remove that space after server
then
      echo "program arma3server is not running - run the program"
      cd /home/admin-ben/Steam/steamapps/common/Arma3Server
      screen -dmS arma ./arma3server >>/home/admin-ben/gameserver/logs/log.rpt 2>&1 -mod=@Exile\;@mas\;@NATO_Rus_Vehicle -servermod=@ExileServer -config=@ExileServer/config.cfg -port=2302 -profiles=SC -cfg=@ExileServer/basic.cfg -name=SC -autoinit -filePatching
else
      echo "program arma3server is running - nothing to do"
      exit
fi

```

Edit: sorry, forgot I made another thread for this bit.
-Removed-
-Removed-

---

### Post by nerdtron on 2016-01-07
[QUOTE=Higgins909;13418920]

Yes the / in the beginning of home is needed. Absolute paths means always start with the /

Ok, let's try this again, looks like you're improving. First edit the script and be sure to include the brackets [] i have added below. It's needed to prevent false detection from the grep process it self.
```

#!/bin/bash
# Test is the process is running using the if statement.
if ! ps -ef | grep [a]rma3server ; #<< I even tried to remove that space after server
then
      echo "program arma3server is not running - run the program"
      cd /home/admin-ben/Steam/steamapps/common/Arma3Server
      screen -dmS arma ./arma3server >>/home/admin-ben/gameserver/logs/log.rpt 2>&1 -mod=@Exile\;@mas\;@NATO_Rus_Vehicle -servermod=@ExileServer -config=@ExileServer/config.cfg -port=2302 -profiles=SC -cfg=@ExileServer/basic.cfg -name=SC -autoinit -filePatching
else
      echo "program arma3server is running - nothing to do"
      exit
fi

```

(Be sure the arma3 process is not running. )
Then try to run the script again.
```

admin-ben@LangweilerG:~$ sudo ./armaboot.sh
root      1505  1503  0 20:58 pts/1    00:00:00 grep arma3server     #####---You should not see this line.

```

Paste here the terminal outputs when you run the updated script. Also after you run the script, post the output of these commands:
```
ps -ef | grep [a]rma3
sudo screen -ls

```

---

### Post by Higgins909 on 2016-01-07
ps -ef | grep [a]rma3
```

admin-ben@LangweilerG:~$ ps -ef | grep [a]rma3server
root      3421     1  0 00:39 ?        00:00:00 SCREEN -dmS arma ./arma3server -mod=@Exile;@mas;@NATO_Rus_Vehicle -servermod=@ExileServer -config=@ExileServer/config.cfg -port=2302 -profiles=SC -cfg=@ExileServer/basic.cfg -name=SC -autoinit -filePatching
root      3422  3421 88 00:39 pts/3    00:01:58 ./arma3server -mod=@Exile;@mas;@NATO_Rus_Vehicle -servermod=@ExileServer -config=@ExileServer/config.cfg -port=2302 -profiles=SC -cfg=@ExileServer/basic.cfg -name=SC -autoinit -filePatching
admin-ben@LangweilerG:~$

```
sudo screen -ls
```

admin-ben@LangweilerG:~$ sudo screen -ls
There is a screen on:
        3421.arma       (01/07/2016 12:39:10 AM)        (Detached)
1 Socket in /var/run/screen/S-root.

admin-ben@LangweilerG:~$

```
I think it's working fine now.  Thank you so much!

---

### Post by nerdtron on 2016-01-07
Looks good! Glad to help.

---

