---
title: "Pass Serv"
date: 2008-12-08
forum: Server Platforms
---

### Post by cowboy.bebop on 2008-12-08
Is it possible to set up a server that generates a password so one can crack it then regens a new one when it has been cracked, kinda like a hands on training deal, cause  I have a large HDD that I partitioned into 7/8 drives and wanted to put most of them, to use.

---

### Post by opscure on 2008-12-08
Yes, this is possible, but not without some scripting/programming.  
I'll help you outline your tasks a bit better.

-First you are going to want to set up a generic user
-Next you will want to monitor your lastlog for a logged in user using a repeating while script that continually runs about every minute or so
you can do this with something like
```
while [ 1 ]; do last |grep still>~/tempLogin.txt; sleep 60; done
```
-Then you will have to check this file to see if it's not empty so you will need to add an if statement to your while loop:
```
if [ -s ~/tempLogin.txt ] 
then
#password change and null echo go here
else 
#do nothing
fi
```
-After you grep out any logged in sessions you will want to generate some random data for a password.  You can use the $RANDOM function in bash for this.
-Then you will want to run the passwd command with an expect script to change the users password for the one you just generated.  All this will occur inside the if statement if the file exists and the filesize is greater then 0 
-finally you will echo nothing to the tempLogin file so the if statement doesn't execute after the password is changed.

---

### Post by cowboy.bebop on 2008-12-08
I gotcha, I do have a bit of experience with c++, would that be a great choice in this case to set up the interface for the randomization of the alphanumerical passwords or will nix do that for me through scripting?

or I could just use:

```

% dd if=/dev/urandom count=1 2> /dev/null | uuencode -m - | sed -ne 2p | cut -c-8
v1/oVN+S

then_

% for ((n=0;n<10;n++)); do dd if=/dev/urandom count=1 2> /dev/null | uuencode -m -| sed -ne 2p | cut -c-8; done

```

---

### Post by opscure on 2008-12-09
You can use either.  If you go with scripting be sure to seed it with a psudo-random number like:
SEED=$(head -1 /dev/urandom | od -N 1 | awk '{ print $2 }')
but if you use c, I believe (not 100% on this) this functionality is built into random().

The thing with doing this all in c is that you will be making a bunch of system calls, where in bash this whole process would be much simpler since you are basically just calling other applications to do this for you.  I think you may be best using C for the password generation and bash for the rest of the functionality and just calling the C program from within the bash script.

The main thing after you get this coded is to have this program/script running in the background on boot so, you may want to add it to your auto starting scripts in the respective users home directory (~/.config/autostart/yourscript.desktop).  This has to be a desktop file to execute properly.

The *.desktop files are in the form of:
[Desktop Entry]
Type=Application
Encoding=UTF-8
Version=1.0
Name=MyProgramName
Name[en_US]=MyProgramName
Comment[en_US]=This will do stuff
Comment=This will do stuff
Exec=sh /home/user/myScriptGoesHere.sh
X-GNOME-Autostart-enabled=true

---

