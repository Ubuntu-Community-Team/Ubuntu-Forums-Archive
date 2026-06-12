---
title: "Ventrilo Push to Talk Script"
date: 2008-12-14
forum: Wine
---

### Post by SBFC on 2008-12-14
I've made an update to my Ventrilo Push to Talk script and decided to start this thread so that it would focus on the script specifically. 

The update pertains to people (like myself) who run games on separate X displays. Prior to this update pyvent would only work on the display it was launched. Now, however, once running PTT functionality should work on any display.

[Original instructions:]("http://ubuntuforums.org/showpost.php?p=6304758&postcount=299")

> 
You'll need python2.5 and python-xlib

```
sudo apt-get install python2.5 python-xlib
```

Download the attachment and drop it wherever you want. Run it without any arguments and you'll be able to monitor your key presses/mouse clicks

```

oblivion@macabre:~/dev/python$ ./pyvent.py

Required arguments not supplied so
will run findkey.

Running findkey...
Press the key or mouse button you wish to
have as your PTT and findkey will tell you
the command to execute.
Press Ctrl-C to exit.

./pyvent.py 2 64


```

Follow the instructions and press the key you wish to have as your PTT. This will will tell you the proper arguments to run pyvent with.

In the above I pressed the left alt button.

As for Ventrilo settings, the original ventriloctrl rules still apply. As per their README:

```

Make sure to set these things exactly like below:
	* Check: "Use Push To Talk Hotkey ( PTT Mode )"
	* Uncheck: "Use Direct Input to detect Hotkey"
	* Hotkey: "Keyboard: A" (if you are pushing the key that you setup in the Getting Started section, and it is not appearing as "Keyboard: A" then we have a problem)
	* Check: "Use Direct Sound" for "Output device"
	* Uncheck: "Use Direct Sound" for "Input device"

```

Once this is all done fire up Ventrilo and then execute pyvent with the command it gave you.

As of right now pyvent is constrained to whatever X display it is executed on. So if you use a separate X server to play games you'll have to launch Ventrilo, pyvent, and your game on the additional X screen. I'm attempting to get around this but ran into a snag.

Any questions feel free to ask and I'll do my best to answer them.

NOTE:

If you have multiple versions of python installed you'll probably have to run pyvent as follows:

```

python2.5 pyvent.py

```

It may work with previous versions, I didn't try. I know it won't work with Python3.0, however.


To use it on a new display simply run .pyvent.py on the new display (no arguments needed) and enjoy. 

Any questions feel free to ask.

---

### Post by SoAnIs on 2009-01-06
Thank you VERY much for this script.

---

### Post by Jaz969 on 2009-01-06
What is this supposed to do besides monitor your keys-That's all it seems to do for me?

---

### Post by SBFC on 2009-01-07
It sends a key event to the Ventrilo window so that PTT works without Ventrilo having focus.

Are you referring to output similar to this?

```
./pyvent.py 2 64
```

---

### Post by hexilum on 2009-01-15
pyvent.py is located on my desktop. What am I doing wrong?


hexilm@machine-desktop:~$ ./pyvent.py
bash: ./pyvent.py: No such file or directory

> **SBFC said:**
> If you have multiple versions of python installed you'll probably have to run pyvent as follows:
```

python2.5 pyvent.py
```

hexilm@machine-desktop:~$ python2.5 pyvent.py
python2.5: can't open file 'pyvent.py': [Errno 2] No such file or directory
hexilm@machine-desktop:~$

---

### Post by hexilum on 2009-01-15
Didn't know that 'hexilm@machine-desktop:~$' is actually '/home/hexilm' and not '/home/hexilm/Desktop'. :(

Anyways I moved the 'pyvent.py' file from 'home/hexilm/Desktop' to 'home/hexilm' and ran:

```
python2.5 pyvent.py
```

Which immediately prompted:

```
Required arguments not supplied so
will run findkey.

Running findkey...
Press the key or mouse button you wish to
have as your PTT and findkey will tell you
the command to execute.
Press Ctrl-C to exit.

pyvent.py 2 50

^C
Bye.

```

Anyways, my problem is when I type 'python2.5 pyvent.py' and it tells me that Ventrilo is found, It doesn't allow me to use that bind key if I'm not focusing on the ventrilo client.

---

### Post by hexilum on 2009-01-16
Any help would be appreciated. I've also noticed that PTTM enables if I'm focusing on any Window's application in wine. Which is great, and is working as intended :popcorn:

But I'm still unable to use PTTM on ventrilo if I'm using native applications. 

Ex. Unable to queue microphone while surfing on browser. 

Is there a fix for this?

---

### Post by mbrang00 on 2009-01-25
Just got done running this script...first of all, Thank you...

whats funny about it is the fact that it only works while i have World of Warcraft active (in other words) while im playing on it....) as soon as i go to a diff window or screen...it doesn't work anymore unless i select vent window.

but for right now...WoW is all i need it for!!!


thanks again...

---

### Post by SBFC on 2009-01-25
> **hexilum said:**
> Any help would be appreciated. I've also noticed that PTTM enables if I'm focusing on any Window's application in wine. Which is great, and is working as intended :popcorn:

But I'm still unable to use PTTM on ventrilo if I'm using native applications. 

Ex. Unable to queue microphone while surfing on browser. 

Is there a fix for this?

Could you please post a screenshot of your Ventrilo settings?

---

### Post by dardack on 2009-02-01
Don't know if anyone else has this luck.  But I don't need this script, my push to talk as long as i'm in a wine window, ie WoW, push to talk works for me.  I am using 1.14 of wine.

---

### Post by SBFC on 2009-02-01
> **dardack said:**
> Don't know if anyone else has this luck.  But I don't need this script, my push to talk as long as i'm in a wine window, ie WoW, push to talk works for me.  I am using 1.14 of wine.

The purpose of this script is to enable the use of push-to-talk when you **don't** have a Wine window active.

Push-to-talk has always worked with a Wine window active.

---

### Post by dardack on 2009-02-02
My bad.  And no it hasn't, back pre 1.0 days, I had an old script (found on the Gentoo WIKI) that enabled push to talk for wine.  Sorry I misunderstood.

---

### Post by airu on 2009-03-09
This is great, I finally have vent PTT working, thanks!

However, if I wanted to change my PTT key to something else, what do I do? If I run the .py file it just loads up my last setting.

---

### Post by SBFC on 2009-03-09
> **airu said:**
> This is great, I finally have vent PTT working, thanks!

However, if I wanted to change my PTT key to something else, what do I do? If I run the .py file it just loads up my last setting.

If you exit the script via Ctrl+C it will delete the settings file. If you want to do it manually just delete the .pyvent.pkl file from your home directory.

---

### Post by rogerSync on 2009-03-19
Works like a charm, thank you Nate!!:KS

(Using vent through codeweavers' crossover office and followed the instructions on the starting post for this thread.)

---

### Post by infinitevalence on 2009-04-22
Important to note, you must have a working microphone setup in vent for your PTT to work :P

Also anyone know a good way to run this script when i first start Vent so i dont have to fire the script manually?

---

### Post by nsfnd on 2009-04-22
> **infinitevalence said:**
> Important to note, you must have a working microphone setup in vent for your PTT to work :P

Also anyone know a good way to run this script when i first start Vent so i dont have to fire the script manually?

What i did was;
```
sudo gedit /usr/bin/vent
```

xmodmap -e "clear Lock" 
cd /home/enes/Ventrilo
wine Ventrilo.exe &
PID="$!"
sleep 1
pyvent.py 2 66 &
wait $PID
pkill -f pyvent.py

```
sudo chmod +x /usr/bin/vent
```

I use caps lock, first line makes caps lock key to not be able to change caps status :)
My pyvent.py is also in /usr/bin folder.

---

### Post by Joker722 on 2009-05-01
For some reason, when I'm prompted to press a key, nothing happens... nothing at all.

I have a logitec G5 and an IBM Model M keyboard, but I can never get any output...

joker@Monolith:~$ cd ./Documents
joker@Monolith:~/Documents$ python2.5 pyvent.py

Required arguments not supplied so
will run findkey.

Running findkey...
Press the key or mouse button you wish to
have as your PTT and findkey will tell you
the command to execute.
Press Ctrl-C to exit.
^C
Bye.
joker@Monolith:~/Documents$

---

### Post by SBFC on 2009-05-01
> **Joker722 said:**
> For some reason, when I'm prompted to press a key, nothing happens... nothing at all.

I have a logitec G5 and an IBM Model M keyboard, but I can never get any output...

joker@Monolith:~$ cd ./Documents
joker@Monolith:~/Documents$ python2.5 pyvent.py

Required arguments not supplied so
will run findkey.

Running findkey...
Press the key or mouse button you wish to
have as your PTT and findkey will tell you
the command to execute.
Press Ctrl-C to exit.
^C
Bye.
joker@Monolith:~/Documents$

What version of Ubuntu are you using?

---

### Post by Joker722 on 2009-05-01
Kubuntu Jaunty

---

### Post by SBFC on 2009-05-02
> **Joker722 said:**
> Kubuntu Jaunty

Yeah, something's different in Jaunty that prevents pyvent from working properly. You're the third person I've seen now unable to use pyvent in the newest release of Ubuntu. 

Unfortunately I have not upgraded yet so I have no way test and see what the problem is. I recommend trying to use the original ventriloctrl as pyvent was created because ventriloctrl did not work in Ubuntu 8.10. Maybe it functions properly in Jaunty now.

---

### Post by infinitevalence on 2009-05-06
add me to the list, i could not get it to work under 9.04 so i downgraded back to 8.10 still works fine there.  Im no linux guru so i guess im just stuck here till you update :( thanks so much though for providing this ctrl.  Vent is the ONLY critical program i have since i use my linux box for 90% gaming.

If there is anything i can do to help let me know :) I would love to move up to 9.04

---

### Post by SBFC on 2009-05-11
Have you tried the original ventriloctrl?
[http://ubuntuforums.org/showpost.php?p=2662867&postcount=83]("http://ubuntuforums.org/showpost.php?p=2662867&postcount=83")

The only reason I made mine was because the above original didn't work in Ubuntu 8.10. I'd try that one with 9.04 to see if it works again.

---

### Post by brainiac1000 on 2009-05-12
Hey, new linux user here, using 9.04 Ubuntu.  I've looked over the situation a bit and I'm having the same issue as the others in this tool and in ventriloctrl.  It looks like the key detection scheme or the output system after key press is what's failing.  I'm going to look over the code and edit this message if I find anything that jumps out at me.

---

### Post by olol on 2009-05-21
I would really appreciate if someone finds a solution to this problem (ptt + ventrilo + ubuntu 9.04) and tells us!

I will post in here if I can get it to work of course!

---

### Post by bentron on 2009-05-21
> **olol said:**
> I would really appreciate if someone finds a solution to this problem (ptt + ventrilo + ubuntu 9.04) and tells us!

I will post in here if I can get it to work of course!

I was having the same problem when I came across a script provided in the winehq appdb page for ventrilo.  The post with instructions and a link to the script is titled "New push-to-talk key listener" by John Hanely.  I've quoted his post below in case anyone can't find it.

I apologize to the OP for sort of hijacking his script thread, but I figured a working solution would be appreciated.  Maybe you can take a look at the perl script and figure out why yours doesn't work?

[QUOTE=John Hanely on WineHQ AppDB]
Hi guys. I got tired of ventriloctrl, so I wrote my own (in perl).
It uses normal X input rather than the event interface, so there are no kernel options or device file permissions to configure. It can be activated/deactivated with a keyboard shortcut, and sends in the same key it captures.

So for example:
1) Configure your desktop manager to launch keylistener.pl when CTRL+` is pressed.
2) Start Ventrilo
3) With the Ventrilo window in focus, press CTRL+`
A small window titled 'Press a Key' will appear.
4) Tap the key you want to capture (right CTRL for me) a few times until the 'Press a Key' window closes.
The Ventrilo window's title will change to: Ventrilo (Key R_Control Captured)
5) Make sure Ventrilo is configured to use that same key for push-to-talk.
6) Use and Enjoy.
7) If you want to uncapture the key, activate your keyboard shortcut again (CTRL+`)
The Ventrilo window title will return to normal.

It requires the following perl modules installed:
X11::GUITest
X11::Protocol
X11::Keyboard

They can all be installed with cpan. As root, run:
cpan -fi X11::Keyboard X11::Protocol X11::GUITest


I haven't tested this extensively, so use at your own risk.
[www.splitreflection.com/~calin/keylistener.pl](www.splitreflection.com/~calin/keylistener.pl)

-John
[/QUOTE]

---

### Post by infinitevalence on 2009-06-10
> **SBFC said:**
> Have you tried the original ventriloctrl?
[http://ubuntuforums.org/showpost.php?p=2662867&postcount=83](http://ubuntuforums.org/showpost.php?p=2662867&postcount=83)

The only reason I made mine was because the above original didn't work in Ubuntu 8.10. I'd try that one with 9.04 to see if it works again.

BTW willing to pay for the development of a vent client for linux ( i keep offering the company and they never reply) or at the very least i will pay to keep my PTT on my mouse :P  so if you want to make some spending $$ feel free to update this script and PM me.

---

### Post by el Arm on 2009-06-20
Here's a note on getting it to work without changing your hotkey to 'A' in Ventrilo.

Change line 106 from;
```
            detail      = self.sim_key,
```
to
```
            detail      = self.keycode,
```

This will send the keycode passed to the script directly to the Ventrilo window.

This is my first look at the Python language and I know nothing of X programming, so the original author probably has some reason for doing it.  Use at your own peril!

For the record, I'm using Hardy and run Ventrilo in it's own dedicated  Wine (set to use OSS) and started through the padsp wrapper.  This was the only way I could get the sound on both WoW and Ventrilo to work reliably.

---

### Post by ResumeMan on 2009-06-21
So just another bit of input on this. I have **not upgraded** my OS to Jaunty. However, I've upgraded Wine when new Intrepid versions have come along. And the script no longer works for me either. Not sure which change caused it because I'd gone awhile w/o using Vent.

So, FYI, there's another way pyvent can break :( Any solutions much appreciated!

---

### Post by el Arm on 2009-06-22
> **ResumeMan said:**
> I've upgraded Wine when new Intrepid versions have come along [...] So, FYI, there's another way pyvent can break :( Any solutions much appreciated!

Which OS and version of wine are you running?  I'm using wine 1.1.10 on Hardy.

Start a bash shell and run this command to change the title;

```
PROMPT_COMMAND='echo -ne "\033]0;"blah"\007"'
```

Now edit the pyvent.py script and search for where it says window='Ventrilo'.  Change 'Ventrilo' to 'blah'.  Run the script in a different shell (e.g. pyvent.py 2 109 for right-ctrl) and press and release the PTT button.  Do 'a' characters appear in the 'blah' shell?

---

### Post by ResumeMan on 2009-06-26
I'm running Intrepid (8.10) and Wine 1.1.24.


I copied pyvent.py to another directory to avoid screwing it up. I ran your "blah" command, then edited pyvent as instructed. Just as a niggle, it was actually "Window_name=" not "Window="

Anyhow, when I ran pyvent with the key arguments, I got the error "ventrilo not found." Even with vent running,and after  several re-starts of the command you gave me, nothing.

Question: If I were to uninstall Wine thru Synaptic and re-install it in an older version, would that be expected to mess anything up?

---

### Post by Laice on 2009-08-14
now forgive me for gravedigging, but i was wondering, are the results returned from pyvent relative to a key, say, from the example, A = 2 64

would it be possible for someone to actually run the script on an older version they still have installed and find out all the different key codes if that were possible?

or is it that jaunty stops pyvent working completely, even after entering a certain key?

---

