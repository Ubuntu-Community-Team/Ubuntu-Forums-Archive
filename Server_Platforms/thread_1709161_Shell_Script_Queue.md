---
title: "Shell Script Queue"
date: 2011-03-17
forum: Server Platforms
---

### Post by Alan James on 2011-03-17
Is there a program that can queue shell scripts so that the first script submitted to it will complete before the second script is started?

Think of it like a video render queue where the first video has to be rendered before the second video starts rendering.

---

### Post by BkkBonanza on 2011-03-17
You can just make a simple script to do this. Or even one line at the prompt.

Put your list of scripts in a file one line each (full path specified).

eg. mylist
```

/usr/local/myscript1
/usr/local/myscript2
/home/joe/superscript43

```

Then run this command,

while read X; do sh "$X"; done<mylist

Or place the same in a script to make it a simple command,
eg. doQ  (and chmod +x doQ)
```

#!/bin/bash
while read X;
do
sh "$X"
done < $1

```

This way you can type,

doQ mylist

to run the scripts listed in the file mylist.

The **while read.. done < file** structure reads file in a loop line by line until no more lines exist.

---

### Post by Alan James on 2011-03-18
I'm trying to use this queue for video compression with FFMPEG, so new tasks need to be added on the fly. If all my scripts were initiated in by another script, as you suggested, new tasks wouldn't be able to be added to the queue without restarting the entire script, if I understand correctly.

I'm looking for sorta a task list. New items can be added to the list at anytime, even if another task on the list are already being run.

---

### Post by Alan James on 2011-03-18
Can Cron be used as a task queue system? I know it can run tasks at specific times set by the user, but can it run them in relation to when the previous task ended?

---

### Post by sisco311 on 2011-03-18
Maybe something like:
```

#!/bin/bash
mkfifo ~/pipe
while read -r command; do
  $command
  sleep 5
done < ~/pipe

```

```
echo "echo 1" > ~/pipe &
echo "echo 2" > ~/pipe &
echo "echo 3" > ~/pipe &
```

---

### Post by Alan James on 2011-03-18
That seems to work but it quits after 5 seconds of inactivity. I know this is caused by the &#8220;sleep 5&#8221; line. Is there a way to keep it running forever, or at least until it is closed by a user?

---

### Post by BkkBonanza on 2011-03-18
Maybe more like this then...

```

#!/bin/bash

mkfifo ~/videoQ

while true; do

while read -r command; do
  $command
done < ~/videoQ

sleep 5
done

```

This one sleeps outside the read loop and waits to check for new pipe content. It will check every 5 seconds forever. Start it in the background with a & on the line, eg.

doQ &

But if you want to stop it then use **pkill doQ**. **ps** to see it is still running.

Add items with the same echo "command" > videoQ  (if in home, or ~/videoQ if not)

I tested this here and it seemed to work ok. Sat in background there waiting for commands and did them right away.

---

### Post by Alan James on 2011-03-18
Awesome! That works perfectly! Is there anyway I can view what is queued up? I tried cat videoQ but it gave me nothing.

---

### Post by BkkBonanza on 2011-03-18
You can view the queue using cat with a pipe, but I believe that will clear out the pipe too. So I think the idea is to tee it into the pipe again. I'm not sure about this though and haven't tested it... it may create some loop.

cat <videoQ |tee videoQ

This should read the videoQ and pipe it back into videoQ but also to stdout for viewing.

If it does work I'd make an alias so it's easy to type,

alias viewQ='cat <videoQ |tee videoQ'

put that in your ~/.bashrc to make always available. Then you can just type

viewQ

---

### Post by Alan James on 2011-03-18
I'm now thinking that it doesn't work. I am submitting a script to the queue then while that script runs, which takes several minuets, I am submitting a second script. The first script finishes but the queue does not move to the second script. If I resubmit the second script it starts, but the point of a queue is to be able to submit the scripts while other scripts are running.

If I submit something simple like "echo 1" "echo 2" it works, something that takes very little time.

Is it possible that because the first script takes several minuets that the queue is somehow being cleared in that time? What am I doing wrong?

---

### Post by stmiller on 2011-03-18
Probably not what you are after, but handbrake features an encoding queue. [http://handbrake.fr](http://handbrake.fr)

:)

---

### Post by BkkBonanza on 2011-03-18
Here's a different version I tested out that doesn't use a named pipe.
It reads into an array, does the first cmd and writes the remainder out again.
This allows using a normal file that can be viewed and appended to as needed.

```

#!/bin/bash

while true; do

if [ -f videoQ ]; then
cmds=( `cat "videoQ" `)
cmd=${cmds[0]}
unset  cmds[0]
rm videoQ
for x in "${cmds[@]}"; do echo "$x" >>videoQ; done
$cmd >>video.log 2>&1
fi

sleep 5
done


```

You can add commands with 

**echo "cmd" >> ~/videoQ**

and view the remaining commands with normal

**cat ~/videoQ**

but this will give a file missing error when the queue is empty, but cause no problem otherwise.

Note this one I add redirection on command output (and errors) so that it gets logged rather than dumping into your console.

view the log with **less video.log**

You can start the queue on reboots by adding doQ to the /etc/rc.local file but note it runs as root there and you may want to run it as a user with 

**sudo -u username /path/to/doQ**

(Note - I edited the script here after posting.)

---

### Post by Alan James on 2011-03-19
stmiller I have looked into Handbrake's render queue and yes, that isn't exactly what I am looking for.

BkkBonanza I can't get that script you posted to work at all. I run the script in one terminal, then in another terminal I echo the command I want to run into videoQ. It creates the video queue file but doesn't run the command. When I cat the videoQ file it shows me just the options I entered, not the command. 

```
./videoconvert -i 01.mp4 
```

becomes 

```
-i
01.mp4
```

---

### Post by BkkBonanza on 2011-03-19
It must be that this line,

cmds=( `cat "videoQ" `)

is reading in the command as multiple lines instead of a single line. You could try adding quotes around it but probably I need to look at it again. I won't be able to do that right this momment but I will come back later and figure out the fix for that. I only tested it with a single word command so missed that.

---

### Post by sisco311 on 2011-03-19
I don't have time to explain it, but this should work:

server:
```

#!/bin/bash

pipe=/tmp/pipe
queue=/tmp/queue

trap "rm -f $pipe" EXIT

if [[ ! -p "$pipe" ]]
then
  mkfifo "$pipe"
fi

if [[ ! -f "$queue" ]]
then
  > "$queue"
fi

while read -r command || true
do
  $command
  sed -i 1d "$queue"
  sleep 5   # added for testing; you can remove this
done < "$pipe"

```

client:
```
#!/bin/bash

pipe="/tmp/pipe"
queue="/tmp/queue"


if [[ ! -p "$pipe" ]]
then
  echo "server not running" >&2
  exit 1
fi

if [[ "$1" != "list" ]]
then
  echo "$*" > "$pipe"
  echo "$*" >> "$queue"
elif [[ "$1" == "list" ]]
then
  cat "$queue"
else
  echo "USAGE: $0 COMMAND [ARGS] or $0 list" >&2
fi

```

```
server &
client command1 
client command2
client command3
client list

```

---

### Post by Alan James on 2011-03-19
> I don't have time to explain it, but this should work

It doesn't. It finishes the first render then doesn't move on to the second render, until the second render is resubmitted, which defeats the purpose of a queue.

I'm attaching the script I am running to compress my video. The problem might be with the script itself, but I can't be sure.

---

### Post by Alan James on 2011-03-19
sisco311 I understand its design. The first code acts as a daemon and the second is a way of interacting with the daemon. The queue is saved to /tmp/queue. So if I wanted to view the queue I can cat that file. 

That sounds great and it should work perfectly, however, I don't know why it's not working. I will poke around with it some more.

---

### Post by BkkBonanza on 2011-03-19
This is a new version that seems to work with multi-part commands,

```

#!/bin/bash

while true; do

if [ -f videoQ ]; then
while read -r line; do cmds=("${cmds[@]}" "$line"); done <videoQ
cmd=${cmds[0]}
unset  cmds[0]
rm videoQ
for x in "${cmds[@]}"; do echo "$x" >>videoQ; done
$cmd >>video.log 2>&1
unset cmds
fi

sleep 5
done

```

It just uses the original read method rather than the shortcut trying to read a whole array at once. Hope that works!

---

### Post by Alan James on 2011-03-19
BkkBonanza that works well. I'm going to do some testing on it now but I think that got it. Thank you for helping a non-programmer out.

---

### Post by BkkBonanza on 2011-03-19
Note that the videoQ is in the current directory there and it would be better if it were hard code to some fixed location like ~/videoQ.

I was thinking it would be nice if the support functions were built in like,

doQ list
doQ add "..."
doQ run

That would be easy to do but no time at the moment.

---

### Post by Alan James on 2011-03-19
That would be pretty cool. I am thinking about a remove function, but currently this works great.

---

### Post by BkkBonanza on 2011-03-20
I had some time so extended this now to a command structure.
Also some refinements. Will work with any name given and stores que and log in home.
Just type the scriptname for command usage.

```

#!/bin/bash

qfile=~/$(basename $0).que
logfile=~/$(basename $0).log
pidfile=/tmp/$(basename $0).pid

case "$1" in
add)
  echo "$2" >> $qfile
  ;;

del)
  if [ "$2" = "" ]; then
    echo "Missing queue #. Use list command #s."
  elif [ -f $qfile ]; then
    while read -r line; do cmds=("${cmds[@]}" "$line"); done <$qfile
    unset cmds[$2]
    rm $qfile
    for x in "${cmds[@]}"; do echo "$x" >>$qfile; done
  else
    echo "Queue empty"
  fi
  ;;

clear)
  if [ -f $qfile ]; then
    rm $qfile
  fi
  ;;

list)
  if [ -f $qfile ]; then
    while read -r line; do cmds=("${cmds[@]}" "$line"); done <$qfile
    for ((x=0; x<${#cmds[@]}; x++ )); do echo "$x: ${cmds[$x]}"; done
  else
    echo "Queue empty"
  fi
  ;;

log)
  if [ -f $logfile ]; then
    less $logfile
  else
    echo "Log empty"
  fi
  ;;

start)
  if [ -f $pidfile ]; then
    kill `cat $pidfile` >/dev/null
  fi
  $0 process&
  ;;

stop)
  if [ -f $pidfile ]; then
    kill `cat $pidfile`
    rm $pidfile
  fi
  ;;

process)
  echo $$ >$pidfile
  while true; do

  if [ -f $qfile ]; then
    while read -r line; do cmds=("${cmds[@]}" "$line"); done <$qfile
    cmd=${cmds[0]}
    unset  cmds[0]
    rm $qfile
    for x in "${cmds[@]}"; do echo "$x" >>$qfile; done
    $cmd >>$logfile 2>&1
    unset cmds
  fi

  sleep 5
  done
  ;;

*)
  echo "Usage: add,del,clear,list,log,start,stop"
  ;;
esac

```

---

### Post by Alan James on 2011-03-20
That is amazingly cool! That is exactly what I was after. This should be part of FFMPEG its so awesome.

---

### Post by Alan James on 2011-03-21
How can I get this to run at startup?

---

### Post by BkkBonanza on 2011-03-21
The simplest insecure way is to add the command to /etc/rc.local,

doQ start

(or whatever you named the script if changed). This runs as root, so you are better to start it as a certain user for security reasons as anyone adding a command to the queue could force it to run with root permissions.

sudo -u user doQ start
(where user is the intended user name)
(but make sure that user has permissions to wherever the data files get stored)

To edit /etc/rc.local you need to edit with sudo as well, eg.

sudo nano /etc/rc.local

---

