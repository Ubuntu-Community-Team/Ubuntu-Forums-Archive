---
title: "Help with daemon scripts"
date: 2016-10-04
forum: Ubuntu/Debian BASED
---

### Post by jackofdiamond5 on 2016-10-04
Hello,

I made this script that is supposed to run an executable file with mono, and I want to start the script as daemon and have it restart the process should it be killed (-r). I have made the script executable and it runs just fine, but when I try to run it as daemon, the daemon process shows up in the System Monitor, but mono doesn't start. I have currently located the script on the GUI desktop and as for the executable that it should run, it's located in Documents (it doesn't bother me at all to point the path to the files). I'm clearly missing something.

Any help will be greatly appreciated!

---

### Post by TheFu on 2016-10-05
Daemon's are started without much environment.  You need to set any variables required. Also, use the full path to all programs, config files and log files.  Don't expect HOME to be set, for example.

Also - the way processes start on Ubuntu has drastically changed the last 3 LTS releases.  Which are you using?
Also - if you post the script - perhaps we can critique it?  
[http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting](http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting) has some more stuff.

---

### Post by jackofdiamond5 on 2016-10-05
I am using Ubuntu 16.04 and as for the script it is as simple as it can get:
#!/bin/bash
mono path/to/file/<filename>.exe (it was compiled on windows)

It works the same if I do something like:
#!/bin/bash
cd path/to/file
mono <filnename>.exe

All it has to do is simply run the .exe file, no more, no less. And it succeeds in doing that but only if I run the script by itself (./path/to/script/<scriptname.sh). If any errors occur, or if something disrupts the program, or make it crash, and kills the process then daemon should come into play and start it again.
But if I try to run it as daemon (daemon -r path/to/script/<scriptname.sh) it does nothing. The daemon process starts, but I think I should be seeing mono as well. Also another thing that makes me certain that mono is not started is because the program that should be run takes it's toll on the CPU, and when I run the script normally, I can see the changes in System Monitor, however when I run it as daemon, nothing changes. So mono doesn't start my program, which means that the script hasn't been executed. My script is executable, because it starts on it's own just fine, with daemon, however, it doesn't. No idea why though.

---

### Post by ian-weisser on 2016-10-05
Remember to use /path/to/mono 

Also remember that daemons don't have a $DISPLAY variable set, so if the .exe file won't either. if either need $DISPLAY, it will crash.

---

### Post by TheFu on 2016-10-05
For Windows programs, isn't a GUI required?  That means you'll need to trick it into thinking it is running as a normal userid (not root) and probably need to use xvfb for the faked DISPLAY.  Hopefully, it doesn't need a mouse click to work. That won't be possible.

Always use the full path to all programs, config files and log files. Don't forget to setup any required environment variables.  Do not trust the PATH, for example.

---

### Post by jackofdiamond5 on 2016-10-05
I apologise for not saying sooner that my program is not GUI, so it does not need [COLOR=#000000]xvfb. It runs completely in the terminal and it generally doesn't need input (it has some commands that can be inputed but they are not required for it to run). It just displays some output information. In the script I'm using the full path to the .exe file, and when I call the script I also use the full path to it. What about the "/path/to/mono"? I can't seem to understand that. Am I not just calling mono to run the .exe file? Why would I need to specify a path to it?[/COLOR]

---

### Post by TheFu on 2016-10-05
What is this line?
```
mono <filnename>.exe
```
The exact line would be helpful.  I won't use mono for political reasons, so can't test it here.  Actually when I initially replied, I thought it said mongo - as in the DB. My mistake.

The final solution will be getting all the required environment variables correct. Does mono have required vars like Java does? Just guessing on my side.

---

### Post by jackofdiamond5 on 2016-10-05
I just saw I made a silly typo <filnename> should really be <FileName>.exe

mono <filnename>.exe simply calls the .exe file at the specified location. 
Like nano TextFile would start the TextFile in a the text editor nano.
In this case <filename> is "the name of the file":

[COLOR=#000000]#!/bin/bash[/COLOR]
[COLOR=#000000]mono path/to/file/MyProgram.exe - calls MyProgram.exe at the specified location[/COLOR]

The same as:
[COLOR=#000000]#!/bin/bash[/COLOR]
[COLOR=#000000]cd path/to/file - changes to the location of MyProgram.exe[/COLOR]
[COLOR=#000000]mono MyProgram.exe - calls MyProgram.exe

Both of these scripts run just fine if I start them by themselves.

[/COLOR]As for mono's environmental variables, the short answer is - I'm not quite sure - [http://www.monodevelop.com/developers/articles/environment-variables/](http://www.monodevelop.com/developers/articles/environment-variables/) - these should be environmental variables for mono, if I'm not mistaken. Though how vital they are is a complete guesswork for me.
I'm not required to use mono, I can easily switch to something else, if you have any suggestions.

---

### Post by TheFu on 2016-10-05
What does "which mono" return?

---

### Post by jackofdiamond5 on 2016-10-05
[INDENT]Which mono? Didn't quite get that.[/INDENT]

---

### Post by TheFu on 2016-10-05
> **jackofdiamond5 said:**
> [INDENT]Which mono? Didn't quite get that.[/INDENT]

Open a terminal.
Type "which mono" into it.
Press <enter> key.

What does that return?

---

### Post by ian-weisser on 2016-10-05
> **jackofdiamond5 said:**
> [COLOR=#000000]It just displays some output information. In the script I'm using the full path to the .exe file, and when I call the script I also use the full path to it. What about the "/path/to/mono"? I can't seem to understand that. Am I not just calling mono to run the .exe file? Why would I need to specify a path to it?[/COLOR]

'mono' isn't a system-recognized command unless /path/to/mono is in the $PATH environment variable. Same for *all* commands.

'just displays some output information' means it needs a display. Which means you need to assign a $DISPLAY environment variable because daemons are designed to run headless and so lack a $DISPLAY. Without an assigned display, it will crash. That's not a mono thing, it's a running-as-a-daemon thing. It's a running-as-root-insead-of-user thing.

You seem to have a classic user/service issue.
The normal answer is to convert the daemon to a real service, launched by dbus or systemd, and communicating with your user client via dbus.

Since we don't know what your daemon does, I cannot say if the normal answer is appropriate for you or not.

---

### Post by TheFu on 2016-10-05
If the output from this program writes to stderr and/or stdout, then it should just work if the environment and paths are fully specified.
If the output is **anything else**, it cannot be run.  Plus, if the program even links to GUI libraries, then they will usually fail to work as daemons.  I've seen this from lazy Oracle developers who never thought that a DB reporting tool would only run on a server without a GUI.  We had to use xvfb to get around that issue, which is quite a hack to be required for software that was so very, very, very expensive.

Rather than hiding the details, why not post the actual script and explain the purpose of the code so we might be able to help?  I'd rather not be a dentist here.

---

