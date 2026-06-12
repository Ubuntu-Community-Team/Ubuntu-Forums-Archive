---
title: "How to jazz up your remote login terminal with fortune"
date: 2005-05-06
forum: Tutorials
---

### Post by crazybill on 2005-05-06
Getting bored with the same dull login terminal when you do remote administration to your Hoary Ubuntu Linux computer? I figured out how to jazz it up some.

First, you should find an interesting random-quote/fortune/joke program at 
**/usr/games/fortune**

Fortune is a neat program that yields adages, fortunes, quotes, humor, etc in a "random" fashion.

First you want to make sure that the binary command fortune is in a path defined by the bash shell's envionmental variable, $PATH

The easiest way to do that is 
```
**# cp /usr/games/fortune /usr/bin/fortune**
``` 

Now, the*** fortune** * command should run from any directory with simply typing ***fortune***
Here is an example run:

```
teacher@ubuntu4:~ $ fortune
Always do right.  This will gratify some people and astonish the rest.
                -- Mark Twain
```

Now we are set to run *** fortune*** at setup. The key is to modify the file, ** /etc/bash.bashrc**

You will edit /etc/bash.bashrc by adding  "fortune" to the bottom of the bash configuration file and save it, such as you see I did here:
```

***teacher@ubuntu4:~ $ tail /etc/bash.bashrc***

export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH
fortune
```

Now everytime you log into your server in the bash shell, you will get ***fortune** *greeting you with humor, wisdom, and wit.

---

### Post by crazybill on 2005-05-06
By the way if you want to jazz up your login screen even more, add cowsay before fortune.
```
**# apt-get install cowsay**
```

Then edit /etc/bash.bashrc again by adding 
cowsay 'howdy'
on the line above fortune, as I have done here::
```

teacher@ubuntu4:~ $ **tail /etc/bash.bashrc**

PATH=$PATH:$JAVA_HOME/bin
export PATH
cowsay 'howdy'
fortune
```

Noter that what is typed inbetween the single quotes following cowsay will be what the cow exclaims. Here is an example screen:
```

 _______
< howdy >
 -------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
You should emulate your heros, but don't carry it too far.  Especially
if they are dead.
```

Have fun!

---

### Post by JonahRowley on 2005-05-06
Great tip, only a few issues.

First, **~/.bashrc** or **/etc/bash.bashrc** should not produce output when running in non-interactive mode.  This will break things like scp, and it's not something that's easy to diagnose.  It's OK to add it to the end of **/etc/bash.bashrc** because of the **[ -z "$PS1" ] && return** line, but if you add this to **~/.bashrc**, beware!  Add it within the **if [ "$PS1" ]; then** conditional.

[QUOTE=crazybill]First you want to make sure that the binary command fortune is in a path defined by the bash shell's envionmental variable, $PATH

The easiest way to do that is 
```
**# cp /usr/games/fortune /usr/bin/fortune**
``` 
[/QUOTE]

By default, **/usr/games** is already in your path.  If it's not, copying it to **/usr/bin** is not the best idea, if fortune is updated in the future (for some reason), **/usr/bin/fortune** will still be the old code.  Use **ln -s /usr/games/fortune /usr/bin/fortune** instead, or call it with its complete path, add **/usr/games/fortune** to your bashrc instead of just **fortune**.

---

### Post by Gandalf on 2005-05-06
beautifull tip, Thx

---

### Post by fng on 2005-05-06
how could you remove the following text at login?

```
The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

```

---

### Post by Estevon on 2005-05-06
The text you are talking about is in /etc/motd

Just open the file and delete the text.

---

### Post by kvidell on 2005-05-06
[QUOTE=crazybill]
```

 _______
< howdy >
 -------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
You should emulate your heros, but don't carry it too far.  Especially
if they are dead.
```

Have fun![/QUOTE]
 Or better yet:
fortune | cowsay -n
;)
```
44/kvidell: fortune | cowsay -n
 ________________________________________________________________________ 
/ Q:      What does friendship among Soviet nationalities mean?          \
| A:      It means that the Armenians take the Russians by the hand; the |
|         Russians take the Ukrainians by the hand; the Ukranians take   |
\         the Uzbeks by the hand; and they all go and beat up the Jews.  /
 ------------------------------------------------------------------------ 
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

```

And don't forget you can do cowsay -f for other cow files!
```
52/kvidell: ls /usr/share/cowsay/cows
apt.cow         bud-frogs.cow  cower.cow    dragon-and-cow.cow  elephant-in-snake.cow  ghostbusters.cow  kiss.cow   kosh.cow        mech-and-cow.cow  moofasa.cow    ren.cow      skeleton.cow   stegosaurus.cow  surgery.cow     turkey.cow  udder.cow        www.cow
beavis.zen.cow  bunny.cow      daemon.cow   dragon.cow          eyes.cow               head-in.cow       kitty.cow  luke-koala.cow  meow.cow          moose.cow      satanic.cow  small.cow      stimpy.cow       telebears.cow   turtle.cow  vader.cow
bong.cow        cheese.cow     default.cow  elephant.cow        flaming-sheep.cow      hellokitty.cow    koala.cow  mech-and-cow    milk.cow          mutilated.cow  sheep.cow    sodomized.cow  supermilker.cow  three-eyes.cow  tux.cow     vader-koala.cow
53/kvidell: fortune | cowsay -n -f cheese.cow
 __________________________________________ 
< You are capable of planning your future. >
 ------------------------------------------ 
   \
    \
      _____   _________
     /     \_/         |
    |                 ||
    |                 ||
   |    ###\  /###   | |
   |     0  \/  0    | |
  /|                 | |
 / |        <        |\ \
| /|                 | | |
| |     \_______/   |  | |
| |                 | / /
/||                 /|||
   ----------------|
        | |    | |
        ***    ***
       /___\  /___\

```
- Kev

---

### Post by RastaMahata on 2005-05-06
I love this! This goes to the index right away :D

PD: It's a good thing to note the fortunes-xx packages, containing fortunes in many languages (I downloaded fortunes-es as my native language is spanish...)

---

### Post by fng on 2005-05-06
Gentoo had like a dozen of extra fortune packages in portage. Eg. futurama, simpsons, calvin and hobbes, movie quotes, offensive, ....

We should get these into universe/multiverse.

---

### Post by crazybill on 2005-05-06
This is exactly what I placed on my current machine:

edited the last line of ***/etc/bash.bashrc*** with 

**fortune -s | cowsay -n -f tux.cow**

and edited the text intro in ***/etc/motd***

and produced this login screen:

```
Linux ubuntu1 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i586 GNU/Linux

Welcome to cvc.org's Ubuntu Linux (Hoary Hedghog 5.04) ACC server:

PENGUIN POWER!!

Last login: Fri May  6 15:09:35 2005 from 66.17.34.8
 ______________________________________________________________________________
/ It were not best that we should all think alike; it is difference of opinion \
| that makes horse-races.                                                      |
\                 -- Mark Twain, "Pudd'nhead Wilson's Calendar"                /
 ------------------------------------------------------------------------------
   \
    \
        .--.
       |o_o |
       |:_/ |
      //   \ \
     (|     | )
    /'\_   _/`\
    \___)=(___/

crazybill@ubuntu1:~ $
```

---

### Post by Karma_Police on 2005-11-04
I placed this at bash.bashrc:
```

cow_images=(apt beavis.zen bong bud-frogs bunny cheese cower daemon default dragon dragon-and-cow elephant elephant-in-snake eyes flaming-sheep ghostbusters head-in hellokitty kiss kitty koala kosh luke-koala mech-and-cow meow milk moofasa moose mutilated ren satanic sheep skeleton small sodomized stegosaurus stimpy supermilker surgery telebears three-eyes turkey turtle tux udder vader vader-koala www)

cow_random=RANDOM%47

fortune | cowsay -n -f ${cow_images[cow_random]}

```


to get random cow pictures everytime. Those are all the cow pictures I have installed from synaptic.

I'm not very good at bash, so I gess we could optimize it by getting the output from "cowsay -l" (minus the first line) to the cow_images array... another way to improve it would be to randomize the eyes and thong flags, but I guess that would be a bit too much. :P

---

### Post by matthew on 2005-11-04
This is just silly...and I love it. This will now be standard on all my *nix boxes.

---

### Post by doclivingston on 2005-11-04
[QUOTE=crazybill]# cp /usr/games/fortune /usr/bin/fortune[/quote]

It's probably better to do ```
ln -s /usr/games/fortune /usr/bin/fortune
``` so that odd things won't happen if you update fortune.

But fortune and cowsay are cool.

---

### Post by Nameless_one on 2007-02-26
I guess this might be the place to ask how I can stop fortune from displaying fortunes from certain files :)

---

### Post by Rinon on 2007-03-23
> **Karma_Police said:**
> I placed this at bash.bashrc:
```

cow_images=(apt beavis.zen bong bud-frogs bunny cheese cower daemon default dragon dragon-and-cow elephant elephant-in-snake eyes flaming-sheep ghostbusters head-in hellokitty kiss kitty koala kosh luke-koala mech-and-cow meow milk moofasa moose mutilated ren satanic sheep skeleton small sodomized stegosaurus stimpy supermilker surgery telebears three-eyes turkey turtle tux udder vader vader-koala www)

cow_random=RANDOM%47

fortune | cowsay -n -f ${cow_images[cow_random]}

```


to get random cow pictures everytime. Those are all the cow pictures I have installed from synaptic.

I'm not very good at bash, so I gess we could optimize it by getting the output from "cowsay -l" (minus the first line) to the cow_images array... another way to improve it would be to randomize the eyes and thong flags, but I guess that would be a bit too much. :P

Here's an improvement on this script that doesn't require a list of cow files:
```
if [ !$COWPATH ]
then
	COWPATH='/usr/share/cowsay/cows/'
fi

cow_file_length=`ls -1 $COWPATH | wc -l`

RANDOM=$$ # initialized the random seed with the process id of this script
let "random_line = $RANDOM % $cow_file_length + 1"
cow=`ls -1 $COWPATH | head -n $random_line | tail -n 1`

fortune | cowsay -n -f $cow
```

Enjoy! :)

---

### Post by Onimae on 2007-04-01
I just want to say that this is fantastic. I had just read up on fortune from the Deb Package of the day and noted that people had this pop up in their terminals whenever they started them. This is just what I was looking for. Thank you, good sirs and ladies for brightening this mans terminal world :). 

Another reason why everyone should have a *nix system is this right here.

**Onimae**

---

### Post by psoup1965 on 2010-11-25
This is all great advice.  However, do not edit /etc/motd... this is a generated file. It will be overwritten, instead if you want to change the message perform: sudo vi /etc/motd.tail

;)

---

### Post by asomad on 2012-02-19
> **Rinon said:**
> Here's an improvement on this script that doesn't require a list of cow files:
```
if [ !$COWPATH ]
then
    COWPATH='/usr/share/cowsay/cows/'
fi

cow_file_length=`ls -1 $COWPATH | wc -l`

RANDOM=$$ # initialized the random seed with the process id of this script
let "random_line = $RANDOM % $cow_file_length + 1"
cow=`ls -1 $COWPATH | head -n $random_line | tail -n 1`

fortune | cowsay -n -f $cow
```Enjoy! :)


Ive put fortune | cowsay in my .bashrc on almost evey distro I've installed. I always thought it would be cool to have a switch for random cows. you should contact the developer and try to work this tiny bit of code in!

AND THANKS!

---

### Post by optimuscream on 2012-02-22
same function with much much less lines : :D

```
randlst=`ls /usr/share/cowsay/cows/ | sort -R | head -1`
fortune | cowsay -n -f $randlst
```

---

### Post by Jorox on 2012-03-15
A slight modification:

With random eyes for the cows and all fortune cookies - offensive and nonoffensive:

```
randlst=`ls /usr/share/cowsay/cows/ | sort -R | head -1`
STR=('b' 'd' 'g' 'p' 's' 't' 'w' 'y')
k=$RANDOM%8

fortune -a | cowsay -${STR[${k}]} -n -f $randlst 
```

(My first bash script :) )

---

