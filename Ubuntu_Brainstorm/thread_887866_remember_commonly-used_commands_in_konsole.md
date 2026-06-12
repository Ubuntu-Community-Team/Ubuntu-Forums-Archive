---
title: "remember commonly-used commands in konsole"
date: 2008-08-12
forum: Ubuntu Brainstorm
---

### Post by skullmunky on 2008-08-12
I bet this would be easy and really helpful.  Actually I bet it already exists :)  

A scrapbook of handy commands in the the terminal.  That way once you've used ubuntuforums to figure out how to batch convert images, or convert windows icons to png's, or do a specific thing with ffmpeg and mencoder, or do other things in the terminal you could just save it with a description and then later choose it from a menu instead of going back to ubuntuforums or scrolling through man pages for hours.  

allow it to be sorted alphabetically, by date, or with subfolders.

---

### Post by MickS on 2008-08-12
I try and do the near the same thing by using Knotes, keep all my useful bits on a sticky note.

Mick

---

### Post by theyranos on 2008-08-12
You can always add functions to your .bashrc. For example,

[php]
# Converts files to png
function to_png() {
  for file in $*; do
    convert "$file" "${file%%.*}".png
  done
}
[/php]

Then I have my own little commands for stuff that took me forever to find. And, I can easily get a list of them all by

grep -F function ~/.bashrc

which itself can be a function :)
[php]
function functions() {
  grep -F function ~/.bashrc
}
[/php]

---

### Post by skullmunky on 2008-08-12
@theyranos - that's cool, I should do try that!  

This menu thing would also be for people new to the shell.  One thing I notice is that it often takes a while for real basic things like "cd .." or "cd ~/Desktop" or "sudo gedit /etc/X11/xorg.conf" or "sudo apt-get install such-and-such" or "ls -lh *.jpg" to become easy to remember, so maybe this would help...

---

### Post by smartboyathome on 2008-08-13
You can also use aliases to "symlink" commands from one to the other. Examples:

```
alias install='sudo apt-get install'
alias update='sudo apt-get update'
alias upgrade='sudo apt-get upgrade'
```

---

