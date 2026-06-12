---
title: "Software Sources broken"
date: 2014-04-26
forum: Security
---

### Post by Charlie_Smith on 2014-04-26
My laptop running Ubuntu 12.04 LTS has a minor problem. I have been trying to install packages using apt-get and whenever I try to it fails. I went to mange software sources and I went to save options that I wanted, but when I tried I got a error Message box that said "E:Malformed line 59 in source list /etc/apt/sources.list (dist parse)". I have been getting this all day. :neutral:

---

### Post by Bashing-om on 2014-04-26
Charlie_Smith; Hi !

Let's take a gander at what the package manager says is the problem.
Post back the output - between code tags - of the terminal command:
```

cat -n /etc/apt/sources.list

```
and let's see what is wrong with the line 59.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT]aint nothing
[INDENT][INDENT][INDENT]but a thing
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Charlie_Smith on 2014-04-26
And I have a notification on my task bar (the one that tells me my name) and I have a error message that says "An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: Error: Opening the cacheE:Malformed line 59 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read., E;The package lists or status file could not be parsed or opened.)'. This usually means that your installed packages have unmet dependencies. I can not close this notification.

---

### Post by Charlie_Smith on 2014-04-26
Thanks!

---

### Post by Charlie_Smith on 2014-04-26
cat -n /etc/apt/sources.list
```

```

---

### Post by Bashing-om on 2014-04-26
Charlie_Smith; Yep.

Malformed line there !
Make it like so:
```

deb http://archive.canonical.com/ubuntu precise partner

```

[INDENT][INDENT]my little bit to help
[/INDENT][/INDENT]

---

### Post by Charlie_Smith on 2014-04-26
Thank you! :)

---

### Post by Charlie_Smith on 2014-04-26
Sorry to bug you again, but how do I change the code line?

---

### Post by Bashing-om on 2014-04-26
Charlie_Smith; Hey,

Ask'n for help is not bugging ! - if you had of followed directions from above I would have already so advised -

1st backup the file, Murphy's law always applies - !
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list-26apr2014

```
 Now fire up the text editor gedit with the required elevated privilege to edit a system file; opening to that file.
```

gksudo gedit /etc/apt/sources.list

```
Insert the terms ubuntu precise at that correct line and  field(s).
Save the file and exit back to the terminal.

Make sure now that all is good:
```

sudo apt-get update
sudo apt-get upgrade

```

All is good ? .. is USC now happy happy ?

[INDENT][INDENT]again
[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Charlie_Smith on 2014-04-26
Now it says line 54 is malformed when I try to do that... What's happening?

---

### Post by Bashing-om on 2014-04-26
Charlie_Smith; No real telling.

Fix and see what happens.
Show us that entire file and we see what it looks like for any other errors.
```

cat -n /etc/apt/sources.list

```
Use the code tags, Luke


[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

