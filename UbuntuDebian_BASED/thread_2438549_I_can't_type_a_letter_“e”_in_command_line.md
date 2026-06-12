---
title: "I can't type a letter “e” in command line"
date: 2020-03-14
forum: Ubuntu/Debian BASED
---

### Post by lateralus2 on 2020-03-14
When I'm using terminal I can't type the letter "e". I can, however,  type a capital "E" using either shift keys. The letter "e" won't work  even if I copy command with the letter "e" in it.  Very strange problem!  Everything was working fine and I don't know what happened to it.

---

### Post by TheFu on 2020-03-14
does 'e' work in any other programs?

is capslock on?  is a metakey stuck?
if you boot a "Try Ubuntu" flash drive, does the problem continue?

BTW, i have issues with 'i' and 'k' keys on one of my systems.  i think the root issue is 100% mechanical - i need a new keyboard.

---

### Post by ajgreeny on 2020-03-14
When you say "in command line" are you talking about a terminal-emulator, eg gnome-terminal or xfce4-terminal, etc, or one  of the tty terminals from using Ctrl+Alt+F#?

Have you tried all the terminal GUI applications available on your system, eg xterm, if it's installed?

---

### Post by lateralus2 on 2020-03-14
'e' works fine in any other program apart from terminals. I've got feeling I accidentally changed something somewhere that's why it doesn't work.

---

### Post by lateralus2 on 2020-03-14
I'm only using UNIX shell which is a default terminal by Elementary OS. The lowercase letter ''e'' was working fine before.

---

### Post by coffeecat on 2020-03-14
*Thread moved to **Ubuntu/Debian Based** sub-forum.*

I have found three old threads on other forums where users were having the same or similar problem to you - unable to type the character e in their bash shells. In each case it was down to a bad line in their /etc/inputrc file. Have you edited this at all?

---

### Post by lateralus2 on 2020-03-14
Originally I was trying to make terminal to be non-sensative to capitalize letters. If I type cd downloads it wouldn't recognize the path (cd Downloads) as downloads folder starts with a capital "D". After I've done some unsuccessful changes I've noticed my 'e' stopped working. Now, I don't know how to make any changes to inputrc file as I have a warning text saying I can not make any changes to this file. 
[https://i.postimg.cc/RhtwyC6c/Screenshot-from-2020-03-14-17-59-45.png](https://i.postimg.cc/RhtwyC6c/Screenshot-from-2020-03-14-17-59-45.png)

---

### Post by TheFu on 2020-03-14
> **lateralus2 said:**
> Originally I was trying to make terminal to be non-sensative to capitalize letters. If I type cd downloads it wouldn't recognize the path (cd Downloads) as downloads folder starts with a capital "D".  


Can't do that.  Put it back the way it was .  Unix file systems are case sensitive.
Restoring a backup is how i would do it.

---

### Post by ajgreeny on 2020-03-14
The image you added to post #7 was no use at all and could not be read so I have removed it and replaced it with a link.

If you think it will help please copy the text back here, not as an image but text, and maybe someone will be able to offer suggestions.

Please use **Code-Tags** for terminal output, if that's what you are copying, as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

