---
title: "Removal of stone age relics"
date: 2014-03-21
forum: Ubuntu, Linux and OS Chat
---

### Post by uwe-bungto on 2014-03-21
i am just thinking out loud about a LinuxStone_Age-Relic that needs to be polished.

I think most of us have slipped in to the naming convention for files and directories of writing in recognizable plain text.
eg. ```
This Song.mpg 
``` or a directory. called```
My Songs Dir
```from the desktop [COLOR=#ffd700]almost[/COLOR] everything can be done to this file or dir. [COLOR=#daa520]Almost.[/COLOR]
Some times the command line is needed ```
sudo chown xxx My Songs Dir
```
Linux falls over because it can not handle separate words as a name.

Do you think that this feature, wanted or forgotten, will be updated?

---

### Post by steeldriver on 2014-03-21
You can use any of these options

1. backslash escaping
```
sudo chown xxx My\ Songs\ Dir
```

2. single quotes
```
sudo chown xxx 'My Songs Dir'
```

3. double quotes
```
sudo chown xxx "My Songs Dir"
```

Double quotes allow parameter expansion e.g.

```
sudo chown xxx "My Songs Dir/*.mp3"
```

whereas single quotes treat everything them as literal. Tab completion makes escaping spaces particularly painless.

---

### Post by sffvba[e0rt on 2014-03-21
> **steeldriver said:**
> Tab completion makes escaping spaces particularly painless.

Tab complete FTW!

---

### Post by ralph-beeby on 2014-03-21
> **not found said:**
> Tab complete FTW!

+1 to that!

I think it comes down to familiarity. Sure, the issue you describe is less-than-ideal, but once you're comfortable with workarounds like tab-complete, or backslash delimiting, the terminal can be very efficient. Personally, I've found that it's easier than trying to point-and-click everything if you're moving large numbers of files around. You do have to be careful with commands like mv and rm though, as I'm not aware of any undo switch or Rubbish Bin if you accidentally delete something via the terminal - though I could be mistaken!

---

### Post by buzzingrobot on 2014-03-21
The alternative is always treating arguments with spaces  as if they are always escaped. That doesn't work when you want the arguments treated individually.  So, you would need to escape, or otherwise qualify them, in some manner, when you did.

In the end, it's a wash.

---

### Post by ajgreeny on 2014-03-21
> **ralph-beeby said:**
> +1 to that!

I think it comes down to familiarity. Sure, the issue you describe is less-than-ideal, but once you're comfortable with workarounds like tab-complete, or backslash delimiting, the terminal can be very efficient. Personally, I've found that it's easier than trying to point-and-click everything if you're moving large numbers of files around. You do have to be careful with commands like mv and rm though, as I'm not aware of any undo switch or Rubbish Bin if you accidentally delete something via the terminal - though I could be mistaken!

To allow for second thought I use aliases to add the -i option (interactive) for **cp**, **mv** and **rm** in my .bash_aliases file to make them all safer, eg **alias cp='cp -i'** 

Then if I attempt to copy a file which will overwrite another file of the same name, the terminal will ask if I want to continue, allowing me to investigate further before doing something I might regret later.  Similarly for mv and most importantly rm; once you have rm'd a file it is gone.

---

### Post by lykwydchykyn on 2014-03-21
If there's a command line interpreter out there that can deal with spaces in a file name without escaping or quoting, I'm not aware of it.  It's the nature of the beast.

---

### Post by uwe-bungto on 2014-03-21
> **steeldriver said:**
> You can use any of these options

1. backslash escaping
```
sudo chown xxx My\ Songs\ Dir
```

2. single quotes
```
sudo chown xxx 'My Songs Dir'
```

3. double quotes
```
sudo chown xxx "My Songs Dir"
```

Double quotes allow parameter expansion e.g.

```
sudo chown xxx "My Songs Dir/*.mp3"
```

whereas single quotes treat everything them as literal. Tab completion makes escaping spaces particularly painless.

Thanks 
I got into the habit of just cuting & pasteing into a terminal, I can't remember if I forgot this or never knew it.

I think it would be better if some of the old code was brought up to date.

---

### Post by steeldriver on 2014-03-21
> **uwe-bungto said:**
> I think it would be better if some of the old code was brought up to date.

So... let me play devil's advocate here

```

$ mkdir tests

$ touch tests/file tests/file\ -al

$ ls tests
file  file -al

```

Now, what do you expect to be the result of

```

$ ls tests/file -al

```

? The point being that there needs to be some agreed delimiter (or field  separator) in order for the command to be broken into lexical units -  if not whitespace then what?

---

### Post by buzzingrobot on 2014-03-22
Just occurred to me that if someone took the notion of removing this 'relic' seriously, they would need to rewrite Bash, rewrite every tool that depends on Bash to parse its command line arguments, and also cope with the blowback for forcing rewrites of a significant majority of all Bash scripts ever written.

Such things help explain why software is a conservative affair.

---

### Post by coffeecat on 2014-03-23
> **uwe-bungto said:**
> Linux falls over because it can not handle separate words as a name.


You are referring to the bash terminal, of course, since this is not an issue in the GUI. Exactly the same non-problem occurs in the Windows command prompt. If you wish to change directory into a subdirectory that has a space in its name, in the Windows command prompt you have to:

```
cd "directory name"
```

Exactly as in the bash terminal. Or escape the space with the ^ symbol, thus:

```
cd directory^ name
```

Also, as in the bash terminal, but using a different escape character.

In the interest of fairness, I have to ask you two questions. Why are you picking on Linux? And - have you written to Microsoft complaining about "stone age relics" in their command prompt? :)

---

### Post by uwe-bungto on 2014-03-23
> **coffeecat said:**
> You are referring to the bash terminal, of course, since this is not an issue in the GUI. Exactly the same non-problem occurs in the Windows command prompt. If you wish to change directory into a subdirectory that has a space in its name, in the Windows command prompt you have to:

```
cd "directory name"
```

Exactly as in the bash terminal. Or escape the space with the ^ symbol, thus:

```
cd directory^ name
```

Also, as in the bash terminal, but using a different escape character.

In the interest of fairness, I have to ask you two questions. Why are you picking on Linux? And - have you written to Microsoft complaining about "stone age relics" in their command prompt? :)

I have learnt something. 
Thanks

---

