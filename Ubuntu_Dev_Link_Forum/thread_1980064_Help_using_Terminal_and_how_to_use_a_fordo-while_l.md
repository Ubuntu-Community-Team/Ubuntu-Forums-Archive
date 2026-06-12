---
title: "Help using Terminal and how to use a for/do-while loop"
date: 2012-05-14
forum: Ubuntu Dev Link Forum
---

### Post by grandadevans on 2012-05-14
Hi All,

I am a PHP Programmer and so I cannot see the transition being too bad but I am quite new to Linux/bash and I need a bit of help.

Today I have been downloading some videos from Hulu but I don't know the loop commands for bash.

What I did (in vim) is to create the following 
```

echo "Beginning Script....." && \
echo "" && \
\
echo "S01E01 - Flash Version Downloaded" && \
get_flash_player http://www.hulu.com/watch/166698/men-behaving-badly-intruders -f "S01E01.flv" -q && \
echo "S01E01 - Flash Version Downloaded" && \
ffmpeg -i S01E01.flv -acodec copy -vcodec copy S01E01.mp4 && \
echo "S01E01 - Flash Converted" && \
rm S01E01.flv && \
echo "S01E01 - Flash Version Deleted" && \
echo "" && \
\
echo "S01E02 - Flash Version Downloaded" && \
get_flash_player http://www.hulu.com/watch/166697/men-behaving-badly-the-bet#s-p4-so-i0 -f S01E02.flv -q && \
echo "S01E02 - Flash Version Downloaded" && \
ffmpeg -i S01E02.flv -acodec copy -vcodec copy S01E02.mp4 && \
echo "S01E02 - Flash Converted" && \
rm S01E02.flv && \
echo "S01E02 - Flash Version Deleted" && \
echo "" && \
\
echo "Disconnecting from Strong VPN" && \
sudo killall pppd && \
echo "Disconnected from Strong VPN" && \
\
sudo mount -t cifs //main/media /home/john/Desktop/TV/main -o username=john,password=mypass,rw,uid=john,gid=john && \
echo "Server mounted" && \
mv ./* /home/john/Desktop/TV/main/Men\ Behaving\ Badly && \
echo "All files moved across to server" && \
echo "Script has finished"

```

There are 18 episodes and so this is highly inpractical (luckily with vim it wasn't too much trouble). I know that there has to be an easier way of doing this and I am keen to learn.

Once the code was complete I copied and pasted into the Terminal (again I'm sure there's a better way to do this).

So far the script is running ok (I have made a few alterations to the one above but you get the idea).

Anyway....the question.....How would I go about creating a for loop and maybe passing an array with the names & URLs in? Also, is there a better way to do it than this? How would you guys (excuse sex) go about doing this task?

Thanks in advance for any replies and I look forward with anticipation to any that are sent.

John

---

### Post by steeldriver on 2012-05-14
Hi John, I'm not really an expert in this stuff but I like to tinker ;)

You can wrap your command sequence into a *shell script* - basically just a text file with a special instruction in the top to tell the terminal shell what interpreter to use for the commands. Exactly how you do that depends a bit what you want to do, I'm guessing a bit here but I would probably separate out the <episode number>/<episode name> parts into a simple text file, e.g.

mbb.in
```

166698/men-behaving-badly-intruders
166697/men-behaving-badly-the-bet#s-p4-so-i0

```and then make a more generic bash script that you could reuse for other shows - something like

hulu.sh
```

#!/bin/bash

s=1
e=1

while read EPINAME 
do
    FLVFILE=$(printf "S%02dE%02d.flv" "$s" "$e")

    echo "get_flash_player http://www.hulu.com/watch/$EPINAME -f $FLVFILE -q"
    echo "$FLVFILE - Flash Version Downloaded"

    echo "ffmpeg -i $FLVFILE -acodec copy -vcodec copy ${FLVFILE%.flv}.mp4"
    echo "$FLVFILE - Flash Version Converted"

    echo "rm  $FLVFILE"
    echo "$FLVFILE - Flash Version Deleted"

    e=$(($e + 1))
done < $1

```Note I have wrapped the actual commands in "echo" statements - I didn't want it to execute anything until it is working right - I've also left you to add the bits outside the loop

You can then execute it as 
```

./hulu.sh mbb.in

```Hope this gets you started! as always with *nix there are many ways to skin every cat, I'm sure someone will come along and suggest something far more elegant. You could also have the 'S0xE0x' prefixes passed in on the command line, change the initial values, ... whatever.

---

