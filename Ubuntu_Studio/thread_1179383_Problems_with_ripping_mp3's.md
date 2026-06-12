---
title: "Problems with ripping mp3's"
date: 2009-06-05
forum: Ubuntu Studio
---

### Post by rEgonicS on 2009-06-05
I've been playing around with a few programs that rip CD's to mp3's and I've run into an error with each one ;___;'' The three I tried are GRIP, abcde, and Sound Juicer. 
 
Sound Juicer 
This is the first one I tried to rip my CD with. When I began to rip my CD, the 
estimated time left was nearly 2 hours so I quit immediately. (The CD I was 
trying to rip is a bit old... that won't affect it though would it?)
 
abcde
After I installed this I tried to follow the tutorial shown here (the one for mp3's)
[COLOR=#008000][www.andrews-corner.org/**abcde**.html]("http://www.andrews-corner.org/abcde.html") [/COLOR][COLOR=black]I couldn't get my command line to [/COLOR]
change directories to match the one in the tutorial. 
 
GRIP
This was the one I liked the most so far. Mainly because it recognized the
track's names and other various imformation that's on the track as opposed to
Sound Juicer and Amarock where it only showed up as "Track #". The program 
could rip my CD fine but when I tried to rip+encode, an error popped up saying
to write the complete path for the encoding? Or something similar to that.
 
Help with any of these is greatly appreciated although fixing GRIP would be preferred :D''

---

### Post by logos34 on 2009-06-05
> **rEgonicS said:**
> 
abcde
After I installed this I tried to follow the tutorial shown here (the one for mp3's)
[COLOR=#008000][www.andrews-corner.org/**abcde**.html]("http://www.andrews-corner.org/abcde.html") [/COLOR][COLOR=black]I couldn't get my command line to [/COLOR]
change directories to match the one in the tutorial.

If you mean the *output* folder, does it already exist?

> cd

mkdir mymusic

you could try it without enclosing " " (but I doubt that's the problem):
 
OUTPUTDIR=$HOME/mymusic

or

OUTPUTDIR=~/mymusic


> GRIP
...
The program 
could rip my CD fine but when I tried to rip+encode, an error popped up saying to write the complete path for the encoding? Or something similar to that.

Either the encoder executable path or output directory path is wrong

lame needs to be installed for mp3

go to >Config>Encode>Encoder

set the codec in the dropdown menu

the encoder executable should by default point to /usr/bin or /usr/local/bin

here's a standard mp3/lame encoder command-line:

> -V 2 --vbr-new --add-id3v2 --pad-id3v2 --ta "%a" --tt "%n" --tl "%d" --ty "%y" --tn "%t" %w %m

Try this line in "Encode File Format" box:

> ~/mymusic/%A/%d/%t. %n.%x

For "mymusic" substitute your folder

---

### Post by khelben1979 on 2009-06-05
You really should try [Jack]("http://www.home.unix-ag.org/arne/jack/"). (see the link) It's a nice program which doesn't even need a GUI.

---

### Post by igorzwx on 2009-06-05
If nothing help, try dd :)

It is a universal solution to many problems (DVD, USB, etc)

then mount ISO

man dd

or Google -> "dd CD to ISO" or something like this

or ask geeks

I will certainly try jack :)

sudo apt-get install jack

Many thanks for the hint!

---

### Post by rEgonicS on 2009-06-05
Thanks for the help guys :D'

I set my encoder executable and encode file format to what logos said and it works great now. I think I'll look into Jack later to see how it compares to grip.

---

### Post by andrew.46 on 2009-06-05
Hi rEgonics,

> **rEgonicS said:**
> 
abcde
After I installed this I tried to follow the tutorial shown here (the one for mp3's)
[COLOR=#008000][www.andrews-corner.org/**abcde**.html]("http://www.andrews-corner.org/abcde.html") [/COLOR][COLOR=black]I couldn't get my command line to [/COLOR]
change directories to match the one in the tutorial. 


Well, that is actually my page so I am a little curious about the error you have experienced :-). Can I ask if you have duplicated exactly this line in your $HOME/.abcde.conf file:

```

# Give the base location here for the encoded music files.
OUTPUTDIR="$HOME/music/"

```

and if so simply run the following and the directory structure should be set:

```

andrew@skamandros~$ **[COLOR="Purple"]mkdir -v $HOME/music[/COLOR]**
mkdir: created directory `/home/andrew/music'

```

and then you should be able to simply put the cd in and type *abcde*... Let me know if this works?

All the best,

Andrew

---

