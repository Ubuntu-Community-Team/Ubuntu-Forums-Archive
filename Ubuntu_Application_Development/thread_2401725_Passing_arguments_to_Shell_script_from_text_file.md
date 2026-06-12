---
title: "Passing arguments to Shell script from text file"
date: 2018-09-21
forum: Ubuntu Application Development
---

### Post by Lewis Arthurton on 2018-09-21
Hello All,

I hope you are all well and I'm really sorry to post this, I know that similar things have been posted before but I am really struggling to get my head around it.

Essentially, I want to feed in selective arguments from a configuration file to my shell script. As an example my config file is as follows: 

```
                                                 
#Randomcheck here
randvariable=0

#Cut off
Cutoff=10

```

How would I write a script in bash to only take the value of Cutoff and ignore Randvariable? Please please please write it as if you are speaking to a 5 year old :lolflag:

Best wishes and thanks,

Lewis

---

### Post by TheFu on 2018-09-21
```
$ grep "Cutoff" /tmp/t | sed 's/^.*=//g'
```

But really if you can be certain all the non-comment lines are valid bash, you can use 
```
source /tmp/t
```
to get the values loaded and use them within the script.  If you don't want a value, ignore it or "unset" it.  I'd use the source method myself.  It is a commonly used method to share settings for a group of scripts that need different values for different systems.

---

### Post by SeijiSensei on 2018-09-21
If you just want the value, 10, I'd modify TheFu's script so that the result of the command is stored in an environment variable:

```

CUTOFF=$(grep "Cutoff" /tmp/t | sed 's/^.*=//g')

```

Encasing a command in $() returns the value of the command which is then stored in the environment variable CUTOFF.  You can then use $CUTOFF in the calling script where you want the value "10" to be used.

---

### Post by Lewis Arthurton on 2018-09-24
Thank you both for your responses I am very very grateful for your help. 

thanks,

Lewis

---

