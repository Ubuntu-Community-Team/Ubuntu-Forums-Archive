---
title: "ls -l work differently when used in bash script"
date: 2013-06-30
forum: Server Platforms
---

### Post by bigmonmulgrew on 2013-06-30
Hi guys

I have a script I'm writing. The part I'm having trouble with takes a folder as an input from the user and lists the contents. When I use the the ls -l command over SSH in a command prompt it lists the destination contents of folders and links.

When I use the same command in a bash script it does not list the links.

Any idea how i can solve this

```
read -e -p "Destination > " Destination
  echo "$Destination"
    mDIRS=`ls -l $Destination | egrep '^d' | awk '{print $9}'`
    echo
    echo_f "## Previewing ##"
    #loop through the directories
    for mDIR in $mDIRS
    do
    echo "$mDIR"
    done
```

---

### Post by bigmonmulgrew on 2013-06-30
I've realised the egrep '^d' limits it to only showing directories. I'm googling but cant find the correct syntax for directories and links '^l' any ideas

---

### Post by bigmonmulgrew on 2013-06-30
ok never mind at a suggestion of the missus who is looking over my shoulder, and has never even used linux, I have deleted the egrep command completely and its working as intended

---

### Post by Cheesemill on 2013-06-30
Using ls in a script is a very bad idea and can lead to all sorts of unexpected behaviour.

What is it you are trying to achieve? I'm sure we can come up with a better solution.

PS - If you are new to bash scripting I've recently discovered [this]("http://www.shellcheck.net/") great site. Just paste your script and it will let you know of any syntax errors and bad practices it sees.

---

### Post by bigmonmulgrew on 2013-06-30
part of the script removes the folder and recreates it empty. The ls is there to allow the user to optionally view the contents before proceeding.

---

### Post by bigmonmulgrew on 2013-06-30
by the way that checker is pretty sweet I've bookmarked it thanks a lot

---

### Post by CharlesA on 2013-06-30
> **Cheesemill said:**
> 
PS - If you are new to bash scripting I've recently discovered [this]("http://www.shellcheck.net/") great site. Just paste your script and it will let you know of any syntax errors and bad practices it sees.

I'm not new to bash scripting, but that is a pretty sweet site. Thanks for the link!

---

