---
title: "Help with getting variables from text file in Bash script"
date: 2011-05-04
forum: Server Platforms
---

### Post by spynappels on 2011-05-04
Hi guys, 

A Bash scripting query here, go easy on me, I'm just starting to write scripts.

I have a script which does a specific job, but I want it to read a few variables from a text file which I specify.

So essentially, I want the first thing the script does to be read a text file which is in the format

```
VAR1=Variable1
VAR2=Variable2
VAR3=Variable3
etc....
```

and then I want to be able to use $VAR1 etc further down in the script.

The script works when I declare the variables individually in the script, but I want to be able to use the same script with a different vars.txt file on different servers.

Can someone help a complete scripting N00B please?

---

### Post by SeijiSensei on 2011-05-04
You can incorporate a file in a script by using the dot operator like this:

```
.  /path/to/my/file
```

The "source" command in bash performs the same function.

---

