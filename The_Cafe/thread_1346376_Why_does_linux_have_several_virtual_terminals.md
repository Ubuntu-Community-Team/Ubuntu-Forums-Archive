---
title: "Why does linux have several virtual terminals?"
date: 2009-12-05
forum: The Cafe
---

### Post by mahela007 on 2009-12-05
Why does linux have 6 or so terminals (The ones which can be accessed by the Alt + function keys)?

---

### Post by lloyd_b on 2009-12-05
> **mahela007 said:**
> Why does linux have 6 or so terminals (The ones which can be accessed by the Alt + function keys)?

So you can have multiple terminals at once, of course :D

The virtual consoles were a convenience feature built into the system in the days before there was a GUI.  Back then, you couldn't just open up more terminal windows, so it was handy to have multiple virtual terminals available.

The feature is still quite useful for those who work on servers that don't have a GUI installed. 

Lloyd B.

---

### Post by Marvin666 on 2009-12-05
Does anybody know which terminal is which?
I think 4 is used for debug, but I'm not for sure...

---

### Post by mahela007 on 2009-12-05
I'm curious.. when I run a command , say 'xterm' in the terminal emulator, I get an xterm window. However, I can't to anything else with that terminal untill I close that xterm window. Hitting Ctrl + C in the terminal will also close the xterm window. 
(Is that why it's handy to have several terminals?)

Now, keeping in mind what I've just said, how can several applications be opened in the same virtual terminal and run simultaneously?

---

### Post by slakkie on 2009-12-05
You can send jobs to the background:

xterm # fire up initial xterm
xterm & # fire up xterm within your xterm, and send it to the background

---

### Post by amauk on 2009-12-05
> **mahela007 said:**
> Now, keeping in mind what I've just said, how can several applications be opened in the same virtual terminal and run simultaneously?Read up on Unix job control

Start a terminal app, say vim
vim takes over the terminal window, preventing you from doing anything else

Press ctrl-z, this pauses the running process, and returns you to the cli
(you'll see a message that the process has been stopped - it'll also give you a job number in brackets)

the command
```
jobs
```
will tell you any processes the terminal has control over, and their status

You can bring the process back to the foreground by issuing
```
fg 1
```
where 1 is the job number of the process

again, you can suspend the job with ctrl-z

for long running (non-interactive) proceses, you can also run in the background

make a script, called "foo.sh"
```
#!/bin/sh
while true; do echo "foo" >&2; sleep 5; done
```

At the CLI prompt, run foo.sh
```
./foo.sh
```

The process takes control of the CLI, and prints "foo" every 5 seconds

suspend the process (ctrl-z)
you're back at the CLI, and the process is suspended
(no more foo's)

```
jobs
```says the process is stopped (suspended)

background the process
```
bg 1
```
You're still at the cli, but foo is being printed to stderr (foo.sh is being run in the background)

```
jobs
```says the process is running in the background

bring foo to the foreground
```
fg 1
```
and terminate it with ctrl-c

---

### Post by audiomick on 2009-12-05
@ amauk
nice post... :D

---

### Post by mahela007 on 2009-12-05
yeah.. Very Good post! 
But if all this is possible, why have multiple terminals...? Is it just for convenience and not an absolute necessity (back when GUI weren't around)?

---

### Post by audiomick on 2009-12-05
> **mahela007 said:**
> yeah.. Very Good post! 
But if all this is possible, why have multiple terminals...? Is it just for convenience and not an absolute necessity (back when GUI weren't around)?

I'd say yes. It is still useful because lots of people prefer to work in terminals.

---

### Post by mahela007 on 2009-12-05
They do? :-0
apologies to lloyd_b. To anyone reading this thread it would seem that I have completely ignored his post.. (about terminals being a convenience.. that's not the case. I just misunderstood ;-) :-) )

---

### Post by audiomick on 2009-12-05
> **mahela007 said:**
> They do? :-0

So I hear. I am very GUI oriented, but even I do some stuff in the terminal. Some things are easier/ quicker in the terminal.
Don't forget, when you click on something in the GUI, effectively what happens is that the GUI goes off and issues a command that you could also issue in a terminal. For some things, it is easier if you cu out the middle man.

---

### Post by mahela007 on 2009-12-05
Does the GUI always go through the terminal?

---

### Post by audiomick on 2009-12-05
I don't think it functionally actually "goes through the terminal".As I understand it, the terminal is a translator for keyboard input into commands. The GUI issues the same commands, but I don't know if there is actually a terminal involved.

---

### Post by mahela007 on 2009-12-05
from what I've read, I don't think there is a terminal involved either. However, I do agree that using the terminal can make ones' work more efficient. (if you're good at typing and proficient with the commands).
Thanks for your help ;-)

---

### Post by theozzlives on 2009-12-05
So in otherwords, the GUI is a "friendly" user interface (kinda like Windows and DOS Shell used to be) that can multi-task. People nowdays wouldn't know what to do without a GUI. I'm an old DOS man, and use Ubuntu's GUI simply cause I'm not yet proficient enough to run Linux from the prompt. Also, I've become accustomed to the pretty pictures (hehe).

---

### Post by oldos2er on 2009-12-05
> **mahela007 said:**
> Does the GUI always go through the terminal?

 Your GUI runs through the tty at Ctrl-Alt-F7

---

### Post by falconindy on 2009-12-05
GNU/Screen (known as a multiplexer) allows you to run multiple terminal sessions within a single terminal. Since having learned to set it up properly, I'm not sure what I would do without it. I suppose you could use the 6 or so tty sessions that are created on bootup to similar effect, but personally I've only created 2 tty's (gotta have a backup!). My GUI launches on tty3.

---

### Post by amauk on 2009-12-05
> **audiomick said:**
> [QUOTE=mahela007;8444528]They do? :-0So I hear. I am very GUI oriented, but even I do some stuff in the terminal. Some things are easier/ quicker in the terminal.
Don't forget, when you click on something in the GUI, effectively what happens is that the GUI goes off and issues a command that you could also issue in a terminal. For some things, it is easier if you cu out the middle man.[/QUOTE]Mainly, the command line is scriptable and easy to automate
The GUI is not

---

### Post by itlarson on 2009-12-05
I'd like to point out that many GUI programs in Linux are actually front ends for a command line program, or a collection of command line programs.  A good illustration of this is to look in k3b under settings->configure k3b->programs.  This shows a list of thirteen different programs which k3b relies on.  I pretty sure all of these can be used at the command line by someone who knows what they are doing.

---

### Post by mahela007 on 2009-12-06
Since you guys said  the GUI runs through a terminal, I assume that the command line and terminal are different things.
 Anyway, how would an application use the terminal? Wikipedia just says a terminal is just for showing output and taking input as text.

---

### Post by audiomick on 2009-12-06
Command line and Terminal are the same thing, or rather, the command line is the line in the terminal where your cursor is for putting in commands.

---

### Post by mahela007 on 2009-12-06
I thought the command line was an application which ran on the terminal
[http://en.wikipedia.org/wiki/Terminal_emulator](http://en.wikipedia.org/wiki/Terminal_emulator)

---

### Post by lloyd_b on 2009-12-06
> **mahela007 said:**
> I thought the command line was an application which ran on the terminal
[http://en.wikipedia.org/wiki/Terminal_emulator](http://en.wikipedia.org/wiki/Terminal_emulator)

The "terminal" (aka "Terminal Emulator") is exactly that - it's a piece of software the emulates the input/output characteristics of a physical terminal.  The virtual consoles on Linux are effectively terminal emulators, as are the "terminal windows" you open up within the GUI.

What you're calling the "command line" is what's known in the *nix world as a "shell", a type of "command interpreter".  This is a piece of software that normally connects to a terminal (physical, virtual, whatever) to get its input and send its output, and provide for the basics of interaction with the user.

The shell *can* (and frequently *is*) used without any terminal.  There are many "shell scripts" that are used by the system that require no input and generate no (necessary) output, so they are typically run without being "attached" to any terminal.

A terminal *can* also be used without a shell.  For instance, a terminal window can be created that executes *any* CLI program.  This is sometimes done with specific users - have a special user account that instead of running a shell, it runs one specific program, with no access to the shell.  A shell isn't the *only* type of software that can handle user interaction, it's just the most common type.

Lloyd B.

---

### Post by audiomick on 2009-12-06
Hallo LLoyd,
Thank you for the clear and precise explanation. :popcorn:
Michael

---

### Post by mahela007 on 2009-12-06
Yes.. great post. But what's the difference between the GUI terminal (the one I get when I go to apps> accessories > terminal) and the other terminals (the ones I get with alt + Function keys)?
EDIT : Sorry to be asking so many questions at the same time, but, since you said that there are things called shell scripts, is it correct to assume that the shell need not necessarily take input from the user?

---

### Post by fluffman86 on 2009-12-06
> **mahela007 said:**
> Yes.. great post. But what's the difference between the GUI terminal (the one I get when I go to apps> accessories > terminal) and the other terminals (the ones I get with alt + Function keys)?
EDIT : Sorry to be asking so many questions at the same time, but, since you said that there are things called shell scripts, is it correct to assume that the shell need not necessarily take input from the user?

There is no real difference between the two.  Originally, computers ran as a server in a big room.  These giant computers were loud and big and needed lots of AC.  So you could run a Serial cable from the big server room to a terminal that you could work on.  You could have lots of people all using this one computer in different rooms via multiple physical terminal stations with a monitor and keyboard.

Now, we each have our own computer, but for the reasons listed earlier it's convenient to have multiple *virtual* terminals at one physical workstation, rather than having multiple physical terminals.

By default, when you log into a terminal in Ubuntu (virtual or emulated by the gui), it also starts a shell--BASH, the Bourne Again SHell.  Also look up bash scripting for more, or flip back a few pages...there's an example here.  As stated before, you might have users on your system that you don't want to have access to bash...maybe they need ZSH or JailShell or the grub shell.  Each of these are able to accept different commands and have different "languages" that you can program in to tell them to do things.  In fact, for Computer Science, students at my university have to write their own shell that connects to the terminal and issues commands.  And shells aren't just limited to command line terminal functions.  Remember that a terminal is also a physical place where you sit to work on the computer.  That means that GNOME is technically a "shell" for your computer...a way for you to interact with it!  

Another user here mentioned screen, which creates virtual "windows" inside of a terminal.  I found this pretty difficult to use.  In Karmic, open a terminal (TTY or xterm or whatever) and type "byobu" which will open a simplified screen session.  Go ahead and run a command like top.  While that's running, press F2 and a new screen will open at the bottom, where you can run more commands, like elinks maybe.  you can switch between them with F4 and F3.  I used to use lots of VTs and gnome-terminals, but now that's not really necessary with byobu!

---

### Post by raktarok on 2009-12-06
thanks for the byobu tip.made my day! :)

a very nice thread guys, keep it going!

---

### Post by mahela007 on 2009-12-07
Thanks for the great info fluffman. However, I'm afraid I still don't understand the concept quite well. I did understand that the terminal is the hardware or software that allows a person to interact with a computer. The shell runs on the terminal and accepts commands typed (if it's a CLI)  by the user. But what happens when a GUI is involved? 
I did understand that a GUI is also a shell. (I read somewhere that kernel refers to the 'soft' vulnerable part of the OS and the shell acts like the shell of a mollusc protecting the innards of the OS. Not a very charming analogy but still... )
Does the GUI issue commands to the shell?

---

### Post by amauk on 2009-12-07
The way CLI & GUI interact with the OS is similar, but not identical
(no, 99% of the time a GUI does not "issue CLI commands" - there's a better way to operate)

Often times there is a low level system call that does something
(A system call is a function in the kernel that is exported out - other programs #include the relevant header in their source code, and can call the kernel function)

As a fictitious example, lets say you have a system call named: get_file_loc()

get_file_loc() will accept a file path, and return that files location on a storage device

For CLI usage, there will be a program written that wraps this system call up into a user operable format
Say the program is called: get_file_loc

The get_file_loc program will #include the relevant kernel header, and be able to give the user direct access to the system call

get_file_loc accepts a file path as an argument
and simply calls the get_file_loc() system call with the argument and outputs the system call's returned value to the CLI

For GUI usage, the CLI program get_file_loc is not used at all
but the underlying system call is

The GUI program will #include the relevant kernel header, and the system call will be available to the GUI program
The GUI application will directly call the the get_file_loc() system call, and does what it wants with the sys-call's return value

---

### Post by amauk on 2009-12-07
Just as an addendum

As you can see from the above, command line programs and GUI programs are on an equal footing
(a CLI program is not "underneath" a GUI one)

CLI or GUI is a matter of preference and suitability
(as I mentioned before, CLI programs can be strung together, scripted and automated - GUI cannot)

A good example of this, is libparted

libparted is a library for creating and manipulating filesystem partitions

There are various user-facing wrappers that use libparted, but all the donkey work is done by this library

One user-facing wrapper is "parted"
this is a CLI program that wraps up the various functions of the libparted library into a command line menu and keyboard input program

Another user-facing wrapper is "gparted"
this the GTK GUI front-end to libparted
Functionally, it does the exact same thing as the "parted" CLI app - simply giving the user the ability to use the libparted library

There's also "qtparted"
identical function to gparted, but for QT

All three wrappers for the libparted library do identical things, the only differences are the way the user inputs commands and gets feedback

---

### Post by Chame_Wizard on 2009-12-07
In Kubuntu,I got 7 different virtual terminals:Ctrl+Alt+F1 to F6(tty1 to tty6) let's you log in,Ctrl+Alt+F8 gives you some kernel info/upstart??.And ctr+ALT+F7 going  immediately to the GUI.

:lolflag:

---

### Post by mahela007 on 2009-12-07
Thanks Amauk. That , I think, pretty much makes this thread complete. 
I just notices something interesting. In this thread, I saw posts which came from Sri lanka, England, Germany, America and the Netherlands. (in no specific order). Wow.. that's impressive.. :-) :-)

I thank everyone for posting and helping out.. Thanks to you, there's one more newbie who's learnt something on the forums.

---

### Post by Xbehave on 2009-12-07
To clear up a few misconceptions in this thread:[LIST=1]
[*]All terminals are the same (all run the same login prompt and if you login on any you get the same shell)
[*]I don't think Xorg run through/in a terminal (It's running on one here but i have a strange setup, if you run ```
ps a | grep -iE "(/usr/bin/X11/X|*dm)"
```, the second colum gives the tty or lack of and xorg or xdm is defiantly not running in a shell.
[*]Xorg doesn't have to be bound to ctrl+alt+f7, on fedora it's on ctrl+alt+f1
[/LIST]

note: everything can ofc be reconfigured to make me wrong.

---

