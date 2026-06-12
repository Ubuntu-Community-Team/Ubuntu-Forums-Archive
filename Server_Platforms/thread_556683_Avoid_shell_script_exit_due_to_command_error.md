---
title: "Avoid shell script exit due to command error"
date: 2007-09-21
forum: Server Platforms
---

### Post by frankabel on 2007-09-21
Hi all,

I want make a script that continue its execution even ones of its commands have error. See the following script:

#!/bin/sh -e
cp $1 "$1`date`$USER" > /dev/null 2>&1;
/bin/nano $1

In case that the user execute the above script passing as first parameter the name of a file that is in a folder that he don't have right to write or the name of a file that don't exist, the script exit after executing the “cp” command and never execute the “nano” program. What I want is that even the “cp” commnd fail, the other commands are executed.

Beside the question, I want share the idea of put scripts like this in the “/usr/local/sbin/” (in this case “nano”) with the name of the editor that users will use to edit text files (almost of them are configuration files)  on a server. The objective is that every time in a production server when somebody change or look a text file (that don't must so frequently) an automatic backup of the file will be done with data of the user (in this case I just use the date, but can be used as part of the backup file name the SSH session and user name etc.) that saw or edit the file.

Salute
Frank Abel

---

### Post by koenn on 2007-09-21
you could first test if a file (directory, ...) exists before you operate on it, eg something like
```
if [ -e $1 ] ; then
    cp .....
fi

```

Very common in shell scripts is the use of 'AND' (&&) and "OR' (||) to trap errors. When 2 statements are joined by &&, the second will only be executed if the first one completed succesfully. With ||, the second will only be executed if the 1st one failed. (There's a logic behind this).

So you could do
```
cp $1 $1....    && nano $1 
``` 
or 
```
cp $1 $1.... || /bin/true
nano $1

```

or even
```
[ -e $1 ] && cp $1 ....
nano $1

```

besides the question :
if you put this in /us/bin/local or anywhere else on your path, you risc creating an infinite loop : the nano in the script might call the script again (instead of the nano program), and again, and again, ....
you might want to look into "alias' instead. 
*edit : didn't notice at first - you have this coverd by stating the full path , /bin/nano*

and backticjs as you use to include the date in the filename are depreciated. try something like $(date +%y%m%d) instead.

it's a good idea, though.

---

### Post by frankabel on 2007-09-21
Well I just find a way...

Just add "|| continue" to the end of the command and even a command error the script don't exit

Salute
Frank Abel

---

### Post by frankabel on 2007-09-21
Thanks Koenn!

---

### Post by koenn on 2007-09-21
welcome.

---

