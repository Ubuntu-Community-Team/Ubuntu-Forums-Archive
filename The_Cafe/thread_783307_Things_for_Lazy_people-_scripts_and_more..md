---
title: "Things for Lazy people- scripts and more."
date: 2008-05-05
forum: The Cafe
---

### Post by Omnios on 2008-05-05
Hi there are a lot of word game threads etc so think im going to try something a bit different. The idea is to post something useful for lazy people such as right click scripts. terminal stuff etc etc or even programs that fall within the lazy catagory.

 To start off I am playing around with bin/bash scripting etc so came up with a right click script to make a sh executable.

```

#!/bin/bash
# By Omnios
# adds execute permissions for files- sh.ell files for lazy people.
#newline-delimited paths for selected files (only if local)
chmod 754 $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS

```

---

### Post by blithen on 2008-05-05
Aliases ftw!!!

alias install='sudo apt-get install'

put that in your .bashrc at the end of it, and then you can just type in the terminal
install <package_name>

---

### Post by swoll1980 on 2008-05-05
```
#! /bin/bash
gksu nautilus $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
```

open selected folder with root privileges

---

### Post by Nevon on 2008-05-05
> **blithen said:**
> Aliases ftw!!!

alias install='sudo apt-get install'

put that in your .bashrc at the end of it, and then you can just type in the terminal
install <package_name>

Oh man this is great! Starting up my server is just a pain ("sudo /etc/init.d/apache2 start")! Now I can just type "server-start" and I'm all set! This is awesome!

---

### Post by kerry_s on 2008-05-05
> **blithen said:**
> Aliases ftw!!!

alias install='sudo apt-get install'

put that in your .bashrc at the end of it, and then you can just type in the terminal
install <package_name>

lol, i use that every day. mine->
```
alias su='sudo -i'
alias update='sudo apt-get update;sudo apt-get -u dist-upgrade'
alias install='sudo apt-get install'
alias remove='sudo apt-get remove --purge'
alias search='apt-cache search -n'
alias show='apt-cache show'
alias clean='sudo apt-get clean'

```


> terminal stuff etc etc or even programs that fall within the lazy catagory.


i use "clex" file manager in the terminal/tty cause i got tired of using straight bash, clex is like a shell add on. you can still type out the commands or just stick them to a F# button. :)
sudo apt-get install clex

i use "unp" to unpack anything, no need to remember.> unp compressed.file
sudo apt-get install unp

---

### Post by Phenax on 2008-05-05
```

find . -iname \*.zip -exec unzip {} \;

```

Unzip all zips in a directory recursively. Find is a *very* useful tool.

---

### Post by original_jamingrit on 2008-05-05
Something I recommend to those of you that want to GUI-fy you desktop even more.  It's called zenity and allows you easily script prompts and pop-up windows, for GNOME.  Since I have a laptop and I am sometimes not connected to the Internet, I have this run every time I boot:

```
#!/bin/bash

#Additional Boot Script
#released under the wtfpl ( sam.zoy.org/wtfpl/COPYING )
#have this script start as a normal program under System->Preferences->Sessions

PROMPT="Start Internet Services?  (Are you connected?)"

if zenity --question --text="$PROMPT"; then
##If you pressed OK...
        pidgin &
        xchat &
        rtorrent &
        #Add whatever else you want, as long as it has an & at the end.
else
#If you pressed cancel...
        zenity --warning --text="D'ohh!"
fi
```

Especially handy, since actually using zenity in your scripts is a no-brainer.

---

### Post by Nevon on 2008-05-06
This is strange... How come my aliases were all erased after I closed the terminal? Isn't there some way to save them?

---

### Post by jw5801 on 2008-05-06
> **Nevon said:**
> This is strange... How come my aliases were all erased after I closed the terminal? Isn't there some way to save them?

Add them to ~/.bashrc

---

### Post by myle on 2008-05-06
> **original_jamingrit said:**
> Something I recommend to those of you that want to GUI-fy you desktop even more.  It's called zenity and allows you easily script prompts and pop-up windows, for GNOME.  Since I have a laptop and I am sometimes not connected to the Internet, I have this run every time I boot:

```
#!/bin/bash

#Additional Boot Script
#released under the wtfpl ( sam.zoy.org/wtfpl/COPYING )
#have this script start as a normal program under System->Preferences->Sessions

PROMPT="Start Internet Services?  (Are you connected?)"

if zenity --question --text="$PROMPT"; then
##If you pressed OK...
        pidgin &
        xchat &
        rtorrent &
        #Add whatever else you want, as long as it has an & at the end.
else
#If you pressed cancel...
        zenity --warning --text="D'ohh!"
fi
```

Especially handy, since actually using zenity in your scripts is a no-brainer.

where did you put this script? If I put it in .bashrc it is executed every time I open a terminal.

---

### Post by jw5801 on 2008-05-06
> **myle said:**
> where did you put this script? If I put it in .bashrc it is executed every time I open a terminal.

It'd be more like something to put in your sessions bit so it runs when you log in, I would think.

Personally I'd be more inclined to simply tell the script only to run if I were connected to my preferred network:

```
if [ "`iwconfig wlan0 | grep \"essid\"`" ]; then
    #execute commands
fi
```

---

### Post by aktiwers on 2008-05-06
Nice thread!
I will keep an eye on this one :)

---

### Post by picpak on 2008-05-06
[mp3Convert.sh](http://ubuntuforums.org/showthread.php?t=653006): a script that converts the quality of MP3 files.

text2waveui: an incredibly simple GUI for text2wave.

```
#!/bin/sh

# Check for dependencies
if [ -z "`which zenity`" ]; then
  xmessage "zenity is required for this program."
  exit;
else
TEXT=`zenity --title "Text-to-Speech" --entry --text "Enter text to be converted to speech:"`
fi

if [ "$TEXT" ]; then
echo $TEXT > text.txt
text2wave -o text.wav text.txt
zenity --info --title "Completed" --text="Conversion completed. Goodbye!"
fi
```

And, of course, my aliases:

```

alias kill='pkill'
alias apt='sudo apt-get install'
alias remove='sudo apt-get remove'
alias search='apt-cache search'
alias edit='gedit'
alias suedit='gksudo gedit'
alias i='sudo dpkg -i'
alias update='sudo apt-get update'
alias dist-upgrade='sudo apt-get dist-upgrade'
alias upgrade='sudo apt-get upgrade'
alias clean='sudo apt-get clean'
alias build-dep='sudo apt-get build-dep'
alias autoremove='sudo apt-get autoremove'
alias df='df -Hl'
alias home='cd ~'
alias mktar='tar -cvf'
alias mkbz2='tar -cvjf'
alias mkgz='tar -cvzf'
alias untar='tar -xvf'
alias unbz2='tar -xvjf'
alias ungz='tar -xvzf'
alias xorg.conf='gksudo gedit /etc/X11/xorg.conf'
alias sources.list='gksudo gedit /etc/apt/sources.list'
alias ds='desmume --disable-sound --disable-3d'
uucc() {
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get clean
clear
}

```

---

### Post by urukrama on 2008-05-06
For more aliases, see also this thread: [Show us your bashrc!]("http://ubuntuforums.org/showthread.php?t=679762")

---

### Post by jw5801 on 2008-05-06
> **picpak said:**
> [mp3Convert.sh](http://ubuntuforums.org/showthread.php?t=653006): a script that converts the quality of MP3 files.


Ew... transcoding. :frown:

---

