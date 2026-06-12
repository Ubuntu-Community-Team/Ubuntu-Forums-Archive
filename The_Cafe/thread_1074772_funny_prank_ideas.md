---
title: "funny prank ideas?"
date: 2009-02-19
forum: The Cafe
---

### Post by jmd9qs on 2009-02-19
hey all,

i recently set up my sister's laptop w/ ubuntu 8.10, and i installed the opensshserver on it. i have figured out how to ssh into the laptop, and i can get it working fine.

i would like to do some HARMLESS pranks over ssh to freak her out, so i'm asking for ideas. right now, all i've got is this:

```
amixer -c 0 sset Master,0 100%; mplayer /home/mysister/.scream11.ogg; amixer -c 0 sset Master,0 20%
```

basically, this is a hidden .ogg file of a loud scream... i set this up as an alias in her .bashrc as SCARE, so i can log in and type that from wherever i am and it'll freak her out. i know, i should just make it a script, but i've no clue how to write those yet (if you know some good tutorials, let me know).

please, any ideas are welcome! remember, no **harmfull** pranks! i don't want to mess up her computer, just have a little fun and maybe freak her out in the process!

---

### Post by apoth on 2009-02-19
Along similar lines, festivaltts?

---

### Post by kestrel1 on 2009-02-19
This is cruel, leave your poor sis alone.

---

### Post by mttman on 2009-02-19
Look into cron jobs, they execute commands at a specified time which means you can have an alibi.

---

### Post by bapoumba on 2009-02-19
So funny. Does she know you have remote access to her stuff?

---

### Post by jmd9qs on 2009-02-19
i actually have tried festival --tts, and it's pretty funny! i did this:

```
sleep 45s; echo 'you are a loser' | festival --tts
```

and she thought it was pretty funny. i did the sleep 45s so i could run upstairs and sit next to her before it went off, thus "proving" my innocence!

kestrel1, like i said before, i'm not doing any harm. just messing around, and it gives my bragging rights because all of the rest of the family uses windbloze! they think i'm a computer god!:D

---

### Post by jimmy the saint on 2009-02-19
ssh into her machine and execute something like
```
sudo-apt get install windows-vista
```

Naw, that would just be too mean and prbably piss her off a little!

---

### Post by jmd9qs on 2009-02-19
> **bapoumba said:**
> So funny. Does she know you have remote access to her stuff?

yes she does. it is her comp, so i asked her permission first. i set it up originally so that i could help her fix any problems remotely, in case i wasn't home

---

### Post by bapoumba on 2009-02-19
> **bapoumba said:**
> So funny. Does she know you have remote access to her stuff?

Does she?

Edit: Ah okay, we posted at the same time.

You know, we have access to your account. letsse what kind of funny prank ideas I can come up with.

---

### Post by jmd9qs on 2009-02-19
> **jimmy the saint said:**
> ssh into her machine and execute something like
```
sudo-apt get install windows-vista
```

Naw, that would just be too mean and prbably piss her off a little!

HEY!! remember, i said no **HARMFUL** pranks! lol:D

---

### Post by jmd9qs on 2009-02-19
> **bapoumba said:**
> Does she?

Ah okay, we posted at the same time.

**You know, we have access to your account**. letsse what kind of funny prank ideas I can come up with.

why do you say that? i've tried to stress that i don't wish to do anything malicious...

---

### Post by bapoumba on 2009-02-19
> **jmd9qs said:**
> why do you say that? i've tried to stress that i don't wish to do anything malicious...

Neither do I, neither do I. I just want to have fun !

---

### Post by kestrel1 on 2009-02-19
[QUOTE=]
kestrel1, like i said before, i'm not doing any harm. just messing around, and it gives my bragging rights because all of the rest of the family uses windbloze! they think i'm a computer god!:D[/QUOTE]
You are lucky, I think my family think I am mad :lolflag:
I was only messin' with you, wish I had a sis to play pranks on. I am also a bit long in the tooth to do that sort of thing now. If I played a prank I am sure it would get out of hand. You need to know when to quit.

---

### Post by donkyhotay on 2009-02-19
Heh, if you can get it I would play voice clip of HAL. A really fun one would be to 'free the fish' (assuming she uses gnome) but I don't know how (or even if) that can be done from the terminal. If you want to know what I'm talking about in gnome press alt-f2, type in 'free the fish' without quotes, then press enter. Wanda the gnome fish will then start swimming around the screen.

---

### Post by jmd9qs on 2009-02-19
> **kestrel1 said:**
>  You need to know when to quit.


agreed! if she freaks out too much and is actually *frightened*, like thinks that someone is stalking her or something, i'll let her in on the joke! she is my sis, after all.

---

### Post by kestrel1 on 2009-02-19
Good on you.

---

### Post by jenkinbr on 2009-02-19
> **jmd9qs said:**
> 
```
amixer -c 0 sset Master,0 100%; mplayer /home/mysister/.scream11.ogg; amixer -c 0 sset Master,0 20%
```

basically, this is a hidden .ogg file of a loud scream... i set this up as an alias in her .bashrc as SCARE, so i can log in and type that from wherever i am and it'll freak her out. i know, i should just make it a script, but i've no clue how to write those yet (if you know some good tutorials, let me know).

please, any ideas are welcome! remember, no **harmfull** pranks! i don't want to mess up her computer, just have a little fun and maybe freak her out in the process!

```

#!/bin/bash
amixer -c 0 sset Master,0 100%;
mplayer /home/mysister/.scream11.ogg;
amixer -c 0 sset Master,0 20%

```

There's your bash script, provided your original code works.

You can save it to ~/bin as .scream, make it executable (chmod +x ~/bin/.scream), and then log out and back in again (if ~/bin didn't exist already), and then you can run .scream and it will do the trick.

You could set up a hidden bin folder at ~/.bin if you want, but to have it added to your path on login, you will need to add these lines to the user's ~/.bashrc file:
```

if [ -d ~/.bin ] ; then
PATH=~/.bin:"${PATH}"
fi
```
Those lines look similar to a set for the ~/bin directory, but this code block is for ~/.bin .

---

### Post by Elfy on 2009-02-19
Perhaps next time the Cafe would be a better place to put this ...

---

### Post by jmd9qs on 2009-02-19
> **jenkinbr said:**
> ```

#!/bin/bash
amixer -c 0 sset Master,0 100%;
mplayer /home/mysister/.scream11.ogg;
amixer -c 0 sset Master,0 20%

```

There's your bash script, provided your original code works.


cool man, thanks! doesn't look that hard, really...

---

### Post by jmd9qs on 2009-02-19
> **forestpixie said:**
> Perhaps next time the Cafe would be a better place to put this ...

ahhh... agreed, sorry. however, i'm a beginner and i'm learning! why not have a little fun?

---

### Post by schauerlich on 2009-02-19
There's always espeak.

```
sudo apt-get install espeak
```

```
espeak "your phrase here"
```

Make it say whatever you want. :)

Also, try "beep"

```
sudo apt-get install beep
```

There are a bunch of options, so try 
```
man beep
```

To see what you can do. Basically, it makes it do a system beep. Combine it with cron and you can have a lot of fun. :)

---

### Post by kestrel1 on 2009-02-19
> **donkyhotay said:**
> Heh, if you can get it I would play voice clip of HAL. A really fun one would be to 'free the fish' (assuming she uses gnome) but I don't know how (or even if) that can be done from the terminal. If you want to know what I'm talking about in gnome press alt-f2, type in 'free the fish' without quotes, then press enter. Wanda the gnome fish will then start swimming around the screen.
You could also try out 'gegls from outer space' from the run application panel (alt + F2) You get a space invaders game start up.

---

### Post by bapoumba on 2009-02-19
So moved, thanks forestpixie :)

---

### Post by jenkinbr on 2009-02-19
> **jmd9qs said:**
> cool man, thanks! doesn't look that hard, really...

No problem - it was a simple matter of breaking down your command into chunks at the semicolons [noparse](;)[/noparse], and adding the '#!/bin/bash' line.  If you can do it with commands at the command line, you can almost certainly automate it with a simple bash script.

> **bapoumba said:**
> So moved, thanks forestpixie :)

Darnit! You made my post count drop! *cries* j/k :)
I'm surprised you didn't do that when you first posted...:)

---

### Post by jmd9qs on 2009-02-19
> **kestrel1 said:**
> You could also try out 'gegls from outer space' from the run application panel (alt + F2) You get a space invaders game start up.

that's funny! remember, though, i'm doing this via ssh... i haven't run across a terminal command to run Wanda the Fish o gegls from outer space.

if anyone knows what they could be, let me know... it looks like they don't even run as individual processes but are attached to gnome-panel

---

### Post by Dr Small on 2009-02-19
```
export DISPLAY=:0
xmessage 'YOU ARE BEING WATCHED. MUHAHAHAHahaha'
```

---

### Post by bapoumba on 2009-02-19
> **jenkinbr said:**
> 
Darnit! You made my post count drop! *cries* j/k :)
I'm surprised you didn't do that when you first posted...:)

Eheh, talk about mine :tongue:
I thought about it. There were other things going on, and I forgot.

---

### Post by jmd9qs on 2009-02-19
> **Dr Small said:**
> ```
export DISPLAY=:0
xmessage 'YOU ARE BEING WATCHED. MUHAHAHAHahaha'
```

hey that's neat! is there a way to have one of these xmessages ssh over to my server to let me know when my sis logs on? so that when she logs into her computer, it automatically does something like this:

```
ssh jmd9qs@myhostname.com xmessage -center -timeout 360 'your sister has logged on!'
```

i don't think it would work in the .bashrc, 'cause that's just terminal options, right? 

what file do i edit for logon options?

---

### Post by jenkinbr on 2009-02-19
Copy that code and then open up gnome-session-properties and add that line into a new entry.  Not at ubuntu at the moment, so can't really provide more info...

---

### Post by donkyhotay on 2009-02-19
> **Dr Small said:**
> ```
export DISPLAY=:0
xmessage 'YOU ARE BEING WATCHED. MUHAHAHAHahaha'
```

That one is fun, I didn't know you could do that. I could see myself having some fun with that. "Warning: this computer may not conform to NSA remote surveillance requirements. Please purchase and install microsoft windows to allow backdoor access to this system." :twisted:

---

### Post by jmd9qs on 2009-02-19
> **donkyhotay said:**
> That one is fun, I didn't know you could do that. I could see myself having some fun with that. "Warning: this computer may not conform to NSA remote surveillance requirements. Please purchase and install microsoft windows to allow backdoor access to this system." :twisted:

it's cool but when i try to do that over ssh, it shows up on *my* screen, not the remote... how do i fix that?

---

### Post by Dr Small on 2009-02-19
> **jmd9qs said:**
> it's cool but when i try to do that over ssh, it shows up on *my* screen, not the remote... how do i fix that?
Are you setting the display on the remote machine before executing the command, and how are you ssh'ing to the box? Don't use -X

---

### Post by donkyhotay on 2009-02-19
Just use basic ssh
```
ssh 192.168.0.1 -l username
```
without anything fancy (like the -X command). Also make certain you have the 
```
export DISPLAY=:0
```
command typed in after you login but before using xmessage. Then you can use xmessage to your hearts content. Works on macs too! (c;

---

### Post by jmd9qs on 2009-02-19
here's what i'm doing:

i'm on the laptop now, and i open up gnome-session-properties. i add a new launcher, with this command:

```
ssh jmd9qs@myhostname.com export DISPLAY:0; xmessage 'Your Sister is Now Logged In'
```

but i've tried a few times, and nothing happens on the remote end... if i do it straight via terminal, it will wait for the ssh to authenticate (i've set it up passwordless), but then it displays my message on the machine i'm on, not the remote machine.

if i ssh into the remote computer and run them as two commands, it works. that's all fine and dandy, but i want to have this run after she logs on in order to notify me that she's on; obviously, if it's going to be automatic, i have to change the command somehow...

what am i missing here?

---

### Post by Dr Small on 2009-02-19
> **jmd9qs said:**
> what am i missing here?

You obviously forgot that you were ending the command and starting a new one. Try:
```
ssh jmd9qs@myhostname.com "export DISPLAY=:0; xmessage 'Your Sister is Now Logged In'"
```

---

### Post by wangsuda on 2009-02-19
> **donkyhotay said:**
> Heh, if you can get it I would play voice clip of HAL. A really fun one would be to 'free the fish' (assuming she uses gnome) but I don't know how (or even if) that can be done from the terminal. If you want to know what I'm talking about in gnome press alt-f2, type in 'free the fish' without quotes, then press enter. Wanda the gnome fish will then start swimming around the screen.

I just had to try this one. Now I have a fish swimming around my desktop. Pretty cool. So how do I stop it?

---

### Post by Kopachris on 2009-02-19
Hey, I never thought about ssh'ing into my Mom's Ubuntu machine to prank her!  She has to work tonight (graveyard shift), so that'll be the perfect time to set up ssh! :twisted:

[TODO]
Look up how to set up ssh in Ubuntu
Look up how to set the volume from the command line
Look up the command for Ubuntu's speech synthesis
[/TODO]

---

### Post by MaxIBoy on 2009-02-19
> **wangsuda said:**
> I just had to try this one. Now I have a fish swimming around my desktop. Pretty cool. So how do I stop it?


Click on her and she'll go a way temporarially.

To get rid of her entirely, just restart.

---

### Post by Dr Small on 2009-02-19
> **Kopachris said:**
> Hey, I never thought about ssh'ing into my Mom's Ubuntu machine to prank her!  She has to work tonight (graveyard shift), so that'll be the perfect time to set up ssh! :twisted:

[TODO]
Look up how to set up ssh in Ubuntu
Look up how to set the volume from the command line
Look up the command for Ubuntu's speech synthesis
[/TODO]
Here's some tips for starting:
```
sudo apt-get install openssh-server
amixer set PCM 100%
espeak 'goodnight mother'
```

---

### Post by Dr Small on 2009-02-19
Restart?! Why not just kill the program?

---

### Post by MaxIBoy on 2009-02-19
Well, you could also do a full X restart (ctrl-alt-backspace.)

Wanda becomes part of GNOME's main process when you run it.

---

### Post by wangsuda on 2009-02-19
> **MaxIBoy said:**
> To get rid of her entirely, just restart.That's kinda what I figured.

[QUOTE=Dr Small]Restart?! Why not just kill the program?[/quote]And how does one do that?

---

### Post by Dr Small on 2009-02-19
> **wangsuda said:**
> That's kinda what I figured.

And how does one do that?
I don't have the program, but I would certainly be looking through htop, or searching with terms in grep like 'wanda', 'fish', or 'free'...

---

### Post by wangsuda on 2009-02-19
> **Dr Small said:**
> I don't have the program, but I would certainly be looking through htop, or searching with terms in grep like 'wanda', 'fish', or 'free'...
Thanks, I'll try that. However, I don't think I'll be running fish real soon!

---

### Post by jmd9qs on 2009-02-19
> **wangsuda said:**
> That's kinda what I figured.

And how does one do that?

don't restart the whole comp! just do:
```

sudo killall gnome-panel
```

this will kill the panel, but don't worry, your open programs wont go away. the panels will come back in a minute, too

---

### Post by wangsuda on 2009-02-19
> **jmd9qs said:**
> don't restart the whole comp! just do:
```

sudo killall gnome-panel
```

this will kill the panel, but don't worry, your open programs wont go away. the panels will come back in a minute, too

Thanks!

---

### Post by jmd9qs on 2009-02-19
no problem man

---

### Post by bapoumba on 2009-02-20
I'm closing the thread, it's been answered. For other ideas, or to make jokes on some other people you know, please go search or ask elsewhere. Now, I'm going play funny jokes my way too :)

---

