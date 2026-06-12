---
title: "How to not diplay shell script lines running"
date: 2013-01-24
forum: The Cafe
---

### Post by sectshun8 on 2013-01-24
So I created a small bash script to consolidate some files across a couple different unix machines, what they are is irrelevant.  Script works fine.

I have a batch file on a PC that remotely executes this script, again, no hiccups in the process.  However in batch scripting, by running the script in null mode I can have the script only display specific lines of operation by ending that line of code with ">&2"

Is there a way in bash scripting to do the same?  The consolidation script, runs through the multiple machines getting files and bringing them to a single location... but it outputs every single operation to the terminal. 

I'd like it to ONLY display the line in the script that prompts for a an SFTP connection password, and that's it...

Possible?

---

### Post by fdrake on 2013-01-24
> **sectshun8 said:**
> So I created a small bash script to consolidate some files across a couple different unix machines, what they are is irrelevant.  Script works fine.

I have a batch file on a PC that remotely executes this script, again, no hiccups in the process.  However in batch scripting, by running the script in null mode I can have the script only display specific lines of operation by ending that line of code with ">&2"

Is there a way in bash scripting to do the same?  The consolidation script, runs through the multiple machines getting files and bringing them to a single location... but it outputs every single operation to the terminal. 

I'd like it to ONLY display the line in the script that prompts for a an SFTP connection password, and that's it...

Possible?

```

./myscript.sh 1>/dev/null

```

---

### Post by sectshun8 on 2013-01-24
Thanks for that... the exact syntax did not work for me, but it put me in the right direction.  Running it locally from the unix machine works exactly as I want...  but now writing the command file for the PC batch file to execute this script remotely is going to be a pain.

Currently in the command file, I use the line to out to the command file
```
echo bash xf1.sh>>%xf%
```Unfortunately, the following does not work with that.  The ">" and "&" characters don't transfer very well..
```
echo bash xf1.sh > & null.txt>>%xf%
```:-k

---

### Post by sectshun8 on 2013-01-24
Google is my friend, haha.  batch scripting uses "^" as escape character... so the working code is:
```
echo bash xf1.sh ^> ^& null.txt>>%xf%
```

---

### Post by sectshun8 on 2013-01-25
The new script is working just as I hoped it would.  However a couple of end users note that after the remote bash script prompts for the SFTP password, and it is entered, all that remains is a blinking cursor, with no way of telling if the program is running until the remote script finishes and the local script continues.

Is there a way in the bash script to single out a line to echo into the terminal to "Please wait, remotes script in progress..." even when the script is outputting to null, or in my case a temp text file?

As I stated earlier, I know in batch scripting, running the script in "null mode", you can override the null output by putting a >&2 at the end of the line, this will allow that given line of code to be displayed in the terminal regardless.  Surely I can do this in bash?

---

### Post by Lucradia on 2013-01-25
Check Multiple Redirections section:

[http://wiki.bash-hackers.org/syntax/redirection](http://wiki.bash-hackers.org/syntax/redirection)

May give a hint.

---

