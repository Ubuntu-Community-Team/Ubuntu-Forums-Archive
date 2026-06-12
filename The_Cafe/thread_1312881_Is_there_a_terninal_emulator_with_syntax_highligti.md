---
title: "Is there a terninal emulator with syntax highligting for bash?"
date: 2009-11-03
forum: The Cafe
---

### Post by MaxIBoy on 2009-11-03
Is there such a thing? And if so, what is it?

(FISH has something like this, but FISH doesn't count, because it's not BASH.)

To clarify, I want something along the lines of what you get in a text editor, but I want it to appear real-time as I type it in a terminal emulator.

The screenshot is a screenshot of a text editor showing a bash script I wrote; this is more or less the style of syntax highlighting I'd like.

---

### Post by Xbehave on 2009-11-03
I think you would do the syntax highlighting with bash not the terminal emulator
some of these may help help:
[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html]("http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html")
[http://www.funtoo.org/en/articles/linux/tips/prompt/]("http://www.funtoo.org/en/articles/linux/tips/prompt/")
[http://wiki.archlinux.org/index.php/Color_Bash_Prompt]("http://wiki.archlinux.org/index.php/Color_Bash_Prompt")

if you want some examples I have this in bashrc:
```
# User specific aliases and functions
GREP_OPTIONS='--color=auto'
LESS=-R

```
and the following in /etc/profile.d/ (its called colorls.sh but UF doesn't like that)

---

### Post by Dragonbite on 2009-11-03
Sounds interesting.

---

### Post by MaxIBoy on 2009-11-03
Yes, you I know how to change the *prompt* color, buth that's not what I'm looking for. 


I want proper syntax highlighting like you'd get in a text editor. I'm editing a screenshot into my first post.

---

### Post by cb951303 on 2009-11-03
then it's the job of the text editor?

---

### Post by FuturePilot on 2009-11-03
I don't think there's too much sense in writing a ton of code directly into the shell. You can't exactly do line breaks and stuff. I think if you're writing that much code it makes a lot more sense to use a text editor.

---

### Post by Xbehave on 2009-11-03
> **FuturePilot said:**
> I don't think there's too much sense in writing a ton of code directly into the shell. You can't exactly do line breaks and stuff. I think if you're writing that much code it makes a lot more sense to use a text editor.

echo meet \
the \
/\ \
character

---

### Post by FuturePilot on 2009-11-03
> **Xbehave said:**
> echo meet \
the \
/\ \
character

Ok, well I mean is you can't organize the code that well, and it becomes hard to go back and edit things if you have **a lot** of code.

---

### Post by Simian Man on 2009-11-03
> **Xbehave said:**
> echo meet \
the \
/\ \
character

And if you make a mistake, you have to type it all out again.  I agree with FuturePilot; if I'm typing so much that highlighting will be helpful, I'm using vim anyway.

---

### Post by Xbehave on 2009-11-03
> **Simian Man said:**
> And if you make a mistake, you have to type it all out again.
meet the up key
> I agree with FuturePilot; if I'm typing so much that highlighting will be helpful, I'm using vim anyway.
that's nice for you two, but not everybody has to work in the same way.

---

### Post by FuturePilot on 2009-11-03
> **Xbehave said:**
> meet the up key

The up key usually brings up the previous command ran from your history.

> 
that's nice for you two, but not everybody has to work in the same way.
True. Just throwing my $.02 out there. For me at least doing such coding is much easier in a text editor. But whatever floats your boat.

---

### Post by Xbehave on 2009-11-03
> **FuturePilot said:**
> The up key usually brings up the previous command ran from your history.
```
[juan@Juan-fedora ~]$ eco \
> meet \
> the \
> /\ \
> key
bash: eco: command not found
[juan@Juan-fedora ~]$ eco meet the /\ key

```
You loose the multi-line formatting but the command is there for editing

> True. Just throwing my $.02 out there. For me at least doing such coding is much easier in a text editor. But whatever floats your boat.
Sorry If i was overly harsh, bad day, it sounded like you were dismissing his idea when you were just giving your $.02 after rereading I realise it was just friendly advice, probably good advice, I too do most of my coding in a text editor (largely because it was python). my bad

Still i hope somebody posts a way to do what MaxIBoy wants because it would be pretty cool, but I think it would have to be done by the emulator instead of bash to keep the code itself unedited, alternatively a non-bash shell may be able to do it

---

