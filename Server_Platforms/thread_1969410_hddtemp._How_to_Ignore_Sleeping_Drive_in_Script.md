---
title: "hddtemp. How to Ignore Sleeping Drive in Script?"
date: 2012-04-30
forum: Server Platforms
---

### Post by Bushflyr on 2012-04-30
OK this one is giving me fits too. :mad: I have a server setup with sda as my OS drive and sd[b,c,d] as my operating RAID5 drives and sde as a spare. This leads to sde sleeping most of the time. I have a script to check hddtemp every hour and shut down the server and email me if a temp gets above 50degrees C.

[COLOR=Red][COLOR=Black]```
#!/bin/bash
HDDS="/dev/sda /dev/sdb /dev/sdc /dev/sdd /dev/sde"
HDT=/usr/sbin/hddtemp
LOG=/usr/bin/logger
DOWN=/sbin/shutdown
ALERT_LEVEL=50
args="--numeric"
for disk in $HDDS
do
if [ -b $disk ]; then
    HDTEMP=$($HDT $disk $args)
    $LOG "HDTEMP for $disk is $HDTEMP"
        if [ $HDTEMP -ge $ALERT_LEVEL ]; then
            echo "The server **** is shutting down due to excessive hard  drive temp. Drive: $disk has reached a temperature of $HDTEMP°C and has  crossed its limit of $ALERT_LEVEL°C" | mail -s "ALERT! The server ****  is shutting down due to excessive hard drive temperature" ****@gmail.com             
            $LOG "System going down as hard disk : $disk temperature $HDTEMP°C exceeded its limit"
            sync;sync
            $DOWN -h 0
        fi
fi
done
```[/COLOR][/COLOR] [COLOR=Red][COLOR=Black]

It works well except that the output of:

```
hddtemp --numeric /dev/sd[a,b,c,d,e]
```is

```

44
39
38
40
/dev/sde: ST2000DL003-9VT166: drive is sleeping

```Which is where I run into problems because the sleeping drive throws an error which results in my getting an email every hour. 

[/COLOR][/COLOR]```
From:root 
To:me

/dev/sde: ST2000DL003-9VT166: drive is sleeping
/usr/local/sbin/hourly.active/hddtemp_monitor.sh: line 13: [: -ge: unary operator expected
```So, how do I get the script to ignore the sleeping drive? I've searched all over and can't seem to find any way to do it at all, let alone elegantly.
[COLOR=Red][COLOR=Black]

[/COLOR][/COLOR]

---

### Post by josephmills on 2012-04-30
[SIZE="3"]old
[/SIZE]
```

#!/bin/bash
HDDS="/dev/sda /dev/sdb /dev/sdc /dev/sdd /dev/sde"
HDT=/usr/sbin/hddtemp
LOG=/usr/bin/logger
DOWN=/sbin/shutdown
ALERT_LEVEL=50
args="--numeric"
for disk in $HDDS
do
if [ -b $disk ]; then
    HDTEMP=$($HDT $disk $args)
    $LOG "HDTEMP for $disk is $HDTEMP"
        if [ $HDTEMP -ge $ALERT_LEVEL ]; then
            echo "The server **** is shutting down due to excessive hard  drive temp. Drive: $disk has reached a temperature of $HDTEMP°C and has  crossed its limit of $ALERT_LEVEL°C" | mail -s "ALERT! The server ****  is shutting down due to excessive hard drive temperature" ****@gmail.com             
            $LOG "System going down as hard disk : $disk temperature $HDTEMP°C exceeded its limit"
            sync;sync
            $DOWN -h 0
        fi
fi
done


```

[SIZE="3"]New
[/SIZE]
[SIZE="2"]What is $disk ? 
[/SIZE]sorry for not indenting 
```

#!/usr/bin/env bash 
#we use  the shebang with the full path + env for if bash is not #installed under /bin 

##COMMENT YOUR CODE 
##SETTING UP VAR

myemail=somathing@gmail.com
serversid=$(hostname && hostname -I)

##
##You can use reg ex too match that pattern 

hdds=/dev/sd[abcde]
hdt=/usr/sbin/hddtemp
logaroo=/usr/bin/logger
downer=/sbin/shutdown
alertlv=50
args="--numeric"

##testing 

for disk in $hdd
do
##test
     if [ -b $disk ]; then
         hdtemp=$($hdt $disk $args)

#NEVER call vars by caps or names like log usr user ect these #are already set vars

      $logaroo "hdtemp for $disk is $hdtemp"

##USE > I think you mean -gt also    
     if [ $hdtemp > $alertlv ]; then

##send error             
echo "The server $serverid is shutting down due to excessive hard  drive temp. Drive: $disk has reached a temperature of 

## Dont know if this is a var or not you did not comment 
$hdtemp °C \n

and has  crossed its limit of $alertlv °C" | mail -s "ALERT! The server $serverid  is shutting down due to excessive hard drive temperature" $myemail \n $logaroo "System going down as hard disk : $disk temperature $hdtemp°C exceeded its limit"
sync;sync
$downer -h 0
   fi
fi
done

```

---

### Post by Bushflyr on 2012-04-30
Cool, thank you! 

I'll give it a try in the AM. I just lightly modified another script I found to make it work and recently noticed getting errors. I have no clue when it comes to actually writing something. Trying to learn, though.

---

### Post by josephmills on 2012-04-30
yeah just take your time there is a great bash tutorial just google **_greg's bash guide_** 

all the 
## are called comments and they are there asking you questions that I have above 

good luck and come hang out on irc with us it is the link below

---

### Post by Bushflyr on 2012-04-30
I'm currently working my through that Bash guide, but it's slow going for someone who's only programming experience was an ADA class 20 years ago. That I nearly flunked. :p

In going through it line by line I see you cleaned up the variables, but I don't see anything that would allow the script to disregard the sleeping drive. An I just missing it?

Regarding the -gt vs -ge, it doesn't matter much to me. 1 degree difference isn't going to cook my drives so either one is OK. 

Thanks again for the help.

---

### Post by rubylaser on 2012-04-30
There isn't anything in that revised script to escape a sleeping drive.  I'd replace your first if statement with a test for the sleeping disk.  This is untested, but should give you the idea of what I'm thinking.

```
#!/bin/bash
HDDS="/dev/sda /dev/sdb /dev/sdc /dev/sdd /dev/sde"
HDT=/usr/sbin/hddtemp
LOG=/usr/bin/logger
DOWN=/sbin/shutdown
ALERT_LEVEL=50
args="--numeric"
for disk in $HDDS
do
if [ -b $disk ]; then
    HDTEMP=$($HDT $disk $args)
    $LOG "HDTEMP for $disk is $HDTEMP"
    if [[ "$HDTEMP" == *drive is sleeping* ]]; then
        echo "$disk is sleeping"
    else [ $HDTEMP -ge $ALERT_LEVEL ]; then
            echo "The server **** is shutting down due to excessive hard  drive temp. Drive: $disk has reached a temperature of $HDTEMP°C and has  crossed its limit of $ALERT_LEVEL°C" | mail -s "ALERT! The server ****  is shutting down due to excessive hard drive temperature" ****@gmail.com             
            $LOG "System going down as hard disk : $disk temperature $HDTEMP°C exceeded its limit"
            sync;sync
            $DOWN -h 0
        fi
fi
done
```

---

### Post by Bushflyr on 2012-04-30
```
#!/bin/bash
HDDS="/dev/sda /dev/sdb /dev/sdc /dev/sdd /dev/sde"
HDT=/usr/sbin/hddtemp
LOG=/usr/bin/logger
DOWN=/sbin/shutdown
ALERT_LEVEL=50
args="--numeric"
for disk in $HDDS
do
if [ -b $disk ]; then
    HDTEMP=$($HDT $disk $args)
    $LOG "HDTEMP for $disk is $HDTEMP"
    if [[ "$HDTEMP" == "*drive is sleeping*" ]]; then
        echo "$disk is sleeping"
          if [ $HDTEMP -ge $ALERT_LEVEL ]; then
            echo "The server **** is shutting down due to excessive hard  drive temp. Drive: $disk has reached a temperature of $HDTEMP°C and has  crossed its limit of $ALERT_LEVEL°C" | mail -s "ALERT! The server ****  is shutting down due to excessive hard drive temperature" ****@gmail.com             
            $LOG "System going down as hard disk : $disk temperature $HDTEMP°C exceeded its limit"
            sync;sync
            $DOWN -h 0
               fi
        fi
fi
done
```

Thanks, that was a good idea. When I ran it like you posted it gave me an error:

```

/usr/local/sbin/hourly.active/hddtemp_monitor.sh: line 13: syntax error in conditional expression
/usr/local/sbin/hourly.active/hddtemp_monitor.sh: line 13: syntax error near `is'
/usr/local/sbin/hourly.active/hddtemp_monitor.sh: line 13: `    if [[ "$HDTEMP" == *drive is sleeping* ]]; then'
```

So I wrapped the "*drive is sleeping*" expression in quotes. Then it gave me another error:

```
/usr/local/sbin/hourly.active/hddtemp_monitor.sh: line 15: syntax error near unexpected token `then'
/usr/local/sbin/hourly.active/hddtemp_monitor.sh: line 15: `    else [ $HDTEMP -ge $ALERT_LEVEL ]; then'

```

So I tried replacing the else with an elif and it kicked:

```

/dev/sde: ST2000DL003-9VT166: drive is sleeping
/usr/local/sbin/hourly.active/hddtemp_monitor.sh: line 15: [: -ge: unary operator expected
```

So I replaced the elif with an if and wound up with the above. It's not booting out any errors or sending me nasty emails, but now when I change the ALERT_LEVEL to 1 it's not shutting down. So for some reason it's not getting to the  if [ $HDTEMP -ge $ALERT_LEVEL ]; then portion of the script.

Sorry. More help please.](*,)

---

### Post by Bushflyr on 2012-05-04
OK, after a TON of reading and fiddling I've managed to come full circle back to where I started. But at least I know exactly what the problem is. An I know a lot more about bash. In another month I should have a pretty good handle on just how much I don't know. :confused:

I've gotten back around to this as the script. After trying multiple variations of Rubnylaser's suggestion.

```

[COLOR=Red][COLOR=Black]#!/bin/bash
HDDS="/dev/sda /dev/sdb /dev/sdc /dev/sdd /dev/sde"
HDT=/usr/sbin/hddtemp
LOG=/usr/bin/logger
DOWN=/sbin/shutdown
ALERT_LEVEL=50
args="--numeric"
for disk in $HDDS
do
if [ -b $disk ]; then
        HDTEMP=$($HDT $disk $args)
        $LOG "HDTEMP for $disk is $HDTEMP"
       if [ $HDTEMP -ge $ALERT_LEVEL [/COLOR][/COLOR][COLOR=Red][COLOR=Black]2>&- [/COLOR][/COLOR][COLOR=Red][COLOR=Black]]; then
                echo "The server **** is shutting down due to excessive hard drive temp. Drive: $disk has reached a temperature of $HDTEMP°C and has crossed its limit of $ALERT_LEVEL°C" | mail -s "ALERT! The server **** is shutting down due to excessive hard drive temperature" ****@gmail.com        
                $LOG "System going down as hard disk : $disk temperature $HDTEMP°C exceeded its limit"
                sync;sync
                $DOWN -h 0
        fi
fi
done

[/COLOR][/COLOR]
```[COLOR=Red][COLOR=Black]
[/COLOR][/COLOR]
Which when I run it -x results in:

```

+ HDDS='/dev/sda /dev/sdb /dev/sdc /dev/sdd /dev/sde'
+ HDT=/usr/sbin/hddtemp
+ LOG=/usr/bin/logger
+ DOWN=/sbin/shutdown
+ ALERT_LEVEL=50
+ args=--numeric
+ for disk in '$HDDS'
+ '[' -b /dev/sda ']'
++ /usr/sbin/hddtemp /dev/sda --numeric
+ HDTEMP=43
+ /usr/bin/logger 'HDTEMP for /dev/sda is 43'
+ '[' 43 -ge 50 ']'
+ for disk in '$HDDS'
+ '[' -b /dev/sdb ']'
++ /usr/sbin/hddtemp /dev/sdb --numeric
+ HDTEMP=39
+ /usr/bin/logger 'HDTEMP for /dev/sdb is 39'
+ '[' 39 -ge 50 ']'
+ for disk in '$HDDS'
+ '[' -b /dev/sdc ']'
++ /usr/sbin/hddtemp /dev/sdc --numeric
+ HDTEMP=38
+ /usr/bin/logger 'HDTEMP for /dev/sdc is 38'
+ '[' 38 -ge 50 ']'
+ for disk in '$HDDS'
+ '[' -b /dev/sdd ']'
++ /usr/sbin/hddtemp /dev/sdd --numeric
+ HDTEMP=39
+ /usr/bin/logger 'HDTEMP for /dev/sdd is 39'
+ '[' 39 -ge 50 ']'
+ for disk in '$HDDS'
+ '[' -b /dev/sde ']'
++ /usr/sbin/hddtemp /dev/sde --numeric
/dev/sde: ST2000DL003-9VT166: drive is sleeping
+ HDTEMP=
+ /usr/bin/logger 'HDTEMP for /dev/sde is '
+ '[' -ge 50 ']'

```Which is good on the one front because it suppresses the "unary operator expected error." However, I'm still getting the emails about "/dev/sde: ST2000DL003-9VT166: drive is sleeping" from root.

I tried suppressing those with 2>&- but it doesn't work because it's the output from the "/usr/sbin/hddtemp /dev/sde --numeric" call, not an error. So, any ideas about how I can intercept or suppress non numeric output from hddtemp?

---

### Post by Zikofski on 2012-10-11
hello, Bushflyr

I am stuck on this same problem 

i get this through my command line

```
/usr/local/sbin/hourly.active/hddtemp_monitor.sh.save.2: line 12: [: -ge: unary operator expected
```

```
/usr/local/sbin/hourly.active/hddtemp_monitor.sh.save: line 11: [: -geHDTEMP=WD20EARX-00PASB0:: binary operator expected
```

with an email saying, exactly the same thing, i am running 6 WD 2Tb HDD, when i do

```
/usr/sbin/hddtemp /dev/sda 
(I GET)
/dev/sda: WDC WD20EARX-00PASB0: 31°C
```

so i know hddtemp is working

and this is my code for hddtemp_monitor.sh

```
#!/bin/bash
HDDS="/dev/sda"
HDT=/usr/sbin/hddtemp
LOG=/usr/bin/logger
DOWN=/sbin/shutdown
ALERT_LEVEL=5
for disk in $HDDS
do
if [ -b $disk ]; then
        HDTEMP=$($HDT $disk | sed 's/\(.*\)://g' | awk -F '°' '{ print $1}')
        $LOG "HDTEMP for $disk is $HDTEMP"
       if [ $HDTEMP -ge $ALERT_LEVEL 2>&- ]; then
                echo "The server **** is shutting down due to excessive hard drive temp. Drive: $disk has reached a temperature of $HDTEMP°C and $
                $LOG "System going down as hard disk : $disk temperature $HDTEMP°C exceeded its limit"
                sync;sync
        fi
fi
done
```

i have tried 3 or 4 different versions to work i have been following this topic 

[http://ubuntuforums.org/showthread.php?t=1895084&page=1](http://ubuntuforums.org/showthread.php?t=1895084&page=1)

originally and i have no solution, i hope you can find a small error in the code that maybe i missed or am missing

Thank you
Andrew

---

