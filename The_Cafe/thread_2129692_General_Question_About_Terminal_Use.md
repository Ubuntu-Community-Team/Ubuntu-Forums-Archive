---
title: "General Question About Terminal Use"
date: 2013-03-27
forum: The Cafe
---

### Post by nbagf on 2013-03-27
I was just wondering that when you guys find lists of commands you need to put into the terminal does anyone else do what I do, that is paste them into a gedit or whatever text editing program and save as a .sh file to run in terminal. I am pretty sure I already know the answer, but i wanted to post this as a consensus kind of thing.

---

### Post by carl4926 on 2013-03-27
No
I have a text file where I keep a list of commands to remind me and to look back at and can copy from

---

### Post by deadflowr on 2013-03-27
I made a bunch of aliases, so typing commands I use a lot have been simplified.

---

### Post by oldos2er on 2013-03-27
+1 for aliases.

---

### Post by mamamia88 on 2013-03-27
First line of documetnt is #! /bin/bash then everything after that is 1 line per command.  You need to make it executable by running chmod +x /path/to/file before it will run. Then just cd to the directory the script is in and ./script.sh

---

### Post by nbagf on 2013-03-29
> **deadflowr said:**
> I made a bunch of aliases, so typing commands I use a lot have been simplified.

I did not know that that was possible until I googled it. This seems like a much more efficient way of initiating commands than pasting them into a .sh file. I guess my theory was wrong. I'm going to set some aliases up soon.

---

### Post by mamamia88 on 2013-03-29
> **nbagf said:**
> I did not know that that was possible until I googled it. This seems like a much more efficient way of initiating commands than pasting them into a .sh file. I guess my theory was wrong. I'm going to set some aliases up soon.

They are both very useful.  For example I use xfce with dual monitors.   I need 3 separate commands to get everything working.  But instead of trying to combine them into a single command I just use one command for monitor 1 one command for montor 2 and one command for setting the possition.   I put those in an sh file and added my scripts folder to PATH in bashrc.  So when it's time to start up the monitors all i have to do is type monitors into my terminal.  Aliases can be useful so you don't have to remember a bunch of complex commands.    Scripts are useful for when you want to run a single command but have multiple commands carried out without typing them all in. In other words aliases is just that you type in your nickname for a command and it's carried out.  A script on the other hand carries out multiple commands at once in the order they where typed.  Which makes it useful for automating some basic stuff

---

### Post by philinux on 2013-03-29
> **carl4926 said:**
> No
I have a text file where I keep a list of commands to remind me and to look back at and can copy from

I use ctrl r in the terminal to search for relevant commands I've used in the past.

---

### Post by mamamia88 on 2013-03-29
Also history or using the arrow keys up/down will display past commands.  So if you only use a few no real need for aliases since you can just arrow up to the last command.  Also if you are using a command but don't know all the available options you can type man command and it will give you detailed info on all the command is capable of

---

### Post by SeijiSensei on 2013-03-29
I write bash scripts all the time, if that's what you are asking about.  Note that you do not need the .sh extension since Unix doesn't use extensions to identify executable files at all.  A script can be called simply "myprogram", and it will run as a bash script as long as it is marked executable and has a first line that reads "#!/bin/bash".

---

