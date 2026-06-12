---
title: "Launching exe files on the command-line now results in an error"
date: 2009-05-31
forum: Wine
---

### Post by bobtestact on 2009-05-31
When I first installed wine, I was able to run a Windows console program by entering its name on the bash command-line, like so:

$  [COLOR=Blue]/winapps/prog.exe[/COLOR]

Now, suddenly, this doesn't work anymore, and I get the following error:

[COLOR=Blue]run-detectors: unable to find an interpreter for /winapps/prog.exe[/COLOR]

Other than this problem, wine continues to work fine, and I can still run the console program by using this command:

$ [COLOR=Blue]wine /winapps/prog.exe[/COLOR]

What happened?  How can I restore the ability of the "run-detector" (whatever that is) to recognize that exe files should be run with wine, like they used to?

Can somebody give me a pointer to information to figure out what this "run-detector" is, and how to configure it to run Win32 exe files under wine?

(By the way, this bug also prevents me from using a desktop application launcher where Command="/winapps/winprog.exe".  I had to go and change all of my launchers to be like Command="wine '/winapps/winprog.exe' ".)

This is quite an annoyance, as I'm a very heavy user of the bash command-line, and I have a huge number of legacy Win32 console programs that I still rely on.

[Ubuntu 9.04, wine 1.0.1]

---

### Post by crusaderbond on 2009-06-01
I've had this problem before. Most likely, wine is no longer your default app for opening .exes. What you do, is navigate to the exe in question, right click on it, and hit open with. Then select wine. This will probably fix it. 

There is no such thing as a run detector though. Ubuntu has a database type thing that tells it which program to use to open a file. Wine is no longer associated with your exe. When you hit open with, then select wine, it should fix that.

---

### Post by hikaricore on 2009-06-01
> **crusaderbond said:**
> I've had this problem before. Most likely, wine is no longer your default app for opening .exes. What you do, is navigate to the exe in question, right click on it, and hit open with. Then select wine. This will probably fix it. 

There is no such thing as a run detector though. Ubuntu has a database type thing that tells it which program to use to open a file. Wine is no longer associated with your exe. When you hit open with, then select wine, it should fix that.

Nautilus/Konqueror/Dolphin/Thunar file associations have nothing to do with running binaries through WINE from command line.
Please pay attention when you reply to threads as to what you're about.

---

### Post by YokoZar on 2009-06-01
Hmm, it sounds like something went wrong in binfmt-misc

---

### Post by bobtestact on 2009-06-01
Thanks for the tip about binfmt-misc -- I think that's the starting point I needed.

FYI, when I use the following command:

$ [COLOR=Blue]update-binfmts --display[/COLOR]

I get this result:

[COLOR=Green]cli (disabled):
     package = mono-common
        type = magic
      offset = 0
       magic = MZ
        mask = 
 interpreter = /usr/bin/cli
    detector = /usr/lib/cli/binfmt-detector-cli
wine (disabled):
     package = wine
        type = magic
      offset = 0
       magic = MZ
        mask = 
 interpreter = /usr/bin/wine
    detector = 
jar (disabled):
     package = sun-java6
        type = magic
      offset = 0
       magic = PK\x03\x04
        mask = 
 interpreter = /usr/lib/jvm/java-6-sun-1.6.0.13/jre/lib/jexec
    detector = 
python2.6 (disabled):
     package = python2.6
        type = magic
      offset = 0
       magic = \xd1\xf2\x0d\x0a
        mask = 
 interpreter = /usr/bin/python2.6
    detector = [/COLOR]

All those "(disabled)" tags are interesting.  I'll experiment with the command "[COLOR=Blue]update-binfmts --enable[/COLOR]" to try to re-enable them.

I'd like to see some examples of other people's output for "[COLOR=Blue]update-binfmts --display[/COLOR]", just to compare with mine.

Does anyone have an idea what could cause all your binfmts to get disabled like this?  My latest apt installs have been (in reverse chronological order): mdbtools, openoffice.org-base, xclip, tofrodos, and putty.  Prior to that, my binfmts were working fine.

---

