---
title: "clear command line history on exit"
date: 2006-09-29
forum: Server Platforms
---

### Post by nick1 on 2006-09-29
Greetings,

I'm using Ubuntu 6 server with LAMP and no GUI, just command line.
Is there a way to automatically clear the command lines history when the command line is closed?  I don't like the idea of keeping a history of what I typed, including passwords, available at the command line.  Perhaps including some code in a command line config file, if such a file exists?

Thank you for your time,

*Nick*

---

### Post by sonic2000gr on 2006-09-29
You could add the following line to the end of your .bash_logout file:

rm -f .bash_history 

Manolis

---

### Post by nick1 on 2006-09-29
Thank you for the suggestion, however it does not appear to be working.  Here is what my .bash_logout file looks like:

```
# ~/.bash_logout: executed by bash(1) when login shell exits.

# when leaving the console clear the screen to increase privacy

if [ "$SHLVL" = 1 ]; then
    [ -x /usr/bin/clear_console ] && /usr/bin/clear_console -q
fi

rm -f .bash_history
```

The only part I added to this file was "rm -f .bash_history".

Thanks,

*Nick*

---

### Post by sonic2000gr on 2006-09-29
weird... I just tested it on my server just to make sure...
You could also write it as

rm -f ~/.bash_history

just to make sure

---

### Post by nick1 on 2006-09-29
Very weird.

```
# ~/.bash_logout: executed by bash(1) when login shell exits.

# when leaving the console clear the screen to increase privacy

if [ "$SHLVL" = 1 ]; then
    [ -x /usr/bin/clear_console ] && /usr/bin/clear_console -q
fi

rm -f ~/.bash_history
```

...also fails. :-k

---

### Post by sonic2000gr on 2006-09-29
Well, final resort...

Add these lines at the end of your .bash_profile

export HISTSIZE=100
export HISTFILESIZE=100
unset HISTFILE

Change the 100 to the number of commands you would like bash to remember while you use the session. Everything will be erased when you logout (this is the unset HISTFILE)

---

### Post by K.Mandla on 2006-09-29
There's also a 'history -c' command that clears the terminal history, but I'm not sure if that's useful to you.

---

### Post by big_gie on 2006-11-03
> **nick1 said:**
> Greetings,

I'm using Ubuntu 6 server with LAMP and no GUI, just command line.
Is there a way to automatically clear the command lines history when the command line is closed?  I don't like the idea of keeping a history of what I typed, including passwords, available at the command line.  Perhaps including some code in a command line config file, if such a file exists?

Thank you for your time,

*Nick*

Are you talking about the bash history file or the lines on the screen?

I don't like keeping what I've type as root written on screen. So I use :
```
# echo "# Clear the screen for security's sake." >> ~/.bash_logout
# echo "clear" >> ~/.bash_logout
```
You could add something to clear the bash history file :
```
# echo "# Clear bash's history file for security's sake." >> ~/.bash_logout
# echo "history -c" >> ~/.bash_logout
```
I don't use the latter, so the command could be wrong... Just test it.

---

### Post by stream303 on 2006-11-13
If you don't even want to keep on in the first place just put

**export HISTSIZE=0**

in your **.bashrc** file

---

### Post by speedman on 2006-11-13
rm -fr ~/.bash_history

ln -s /dev/null ~/.bash_history

Your history will be available in ram for each bash session, but will be gone once you log out.


Regards,

SM

---

### Post by yabbadabbadont on 2006-11-13
```
# Prevent a bash history file from ever being saved.
unset HISTFILE

# Prevent less from creating a history file.
export LESSHISTFILE="-"

```
Just include that in your .bashrc file.

EDIT: Note that it won't change your current shell session.  You will have to exit that shell, open it again, and remove the .bash_history and .lesshst (sp?) files.  Then they should not show up again.

---

