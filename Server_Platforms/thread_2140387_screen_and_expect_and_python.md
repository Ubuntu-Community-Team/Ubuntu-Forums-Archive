---
title: "screen and expect and python"
date: 2013-04-29
forum: Server Platforms
---

### Post by Johnny-Gear on 2013-04-29
Hi All,

I am trying to write a bash script which launches a python application.

Unfortunately the python application needs to be interactive.

Also, I am running this python application in a screen.

I am trying to send the required interactions using expect but I am failing hard.

Here is my bash script:

```

sent=blah
expexec=$(/usr/bin/expect -c "/usr/bin/python /opt/app.py expect \"Interaction:\" send \"$sent\r\" interact")

/usr/bin/screen -L -dmS spawner /bin/sleep 30
/bin/sleep 1
/usr/bin/screen -S spawner -X screen screen -L -dR myDaemon
/bin/sleep 1
/usr/bin/screen -S myDaemon -X detach
/usr/bin/screen -S myDaemon -X stuff "echo $expexec"
/usr/bin/screen -S spawner -X stuff "exit\r"


```

I would really appreciate it if someone could tell me what I am missing / doing wrong.

Thanks,

JG

---

### Post by MAFoElffen on 2013-04-30
Let me see if I read this right. May be just style differences, but... 
```

#!/bin/sh 
# Debug expect & screen script.

# You have to add quotes around a string to init your variable.
sent="blah"
# Debugged it by adding the next ine and seeing what it was initialized to...
echo $sent

# This was trying to execute the command instead of loading a variable with your
# variable = string = commandline... showed executing with errors, but blank as
# a variable... 
# expexec=$(/usr/bin/expect -c "/usr/bin/python /opt/app.py expect \"Interaction:\" send \"$sent\r\" interact")

# This is what I came up with:
expexec="/usr/bin/expect -c \"/usr/bin/python /opt/app.py expect \"Interaction:\" send \"$sent\r\" interact\""
# This was the debug line to see what it loaded as:
echo $expexec


/usr/bin/screen -L -dmS spawner /bin/sleep 30
/bin/sleep 1
/usr/bin/screen -S spawner -X screen screen -L -dR myDaemon
/bin/sleep 1
/usr/bin/screen -S myDaemon -X detach

## Can the Op explain this one? Is he tring to "echo" it or execute it? I'm thinking he needs to take the echo out of that next line...
/usr/bin/screen -S myDaemon -X stuff "echo $expexec"

/usr/bin/screen -S spawner -X stuff "exit\r"

```
When I'm trying to work out (debug) a bash or python script... I'll put in debug code (echo or print statements) to see if my code is reacting like I'm expecting it too and to show me what is going on underneath. I can always comment it out or remove it when I get it going. What it showed me is that your variable were not loading... ad your expect commandline string varaible was trying to execute on the string init.

Try the changes and see if that works. ...At least that part of it is working now.  Didn't really look at the screen lines... I know some say bash and expect play weird together sometimes, so some, if using bash, call to an expect script... then return.

Look in my comments. I have questions

The application is a python app? Why not a python script (sys:exec) talking with each other? Just a thought.

---

### Post by Johnny-Gear on 2013-05-02
> **MAFoElffen said:**
> Let me see if I read this right. May be just style differences, but... 
```

#!/bin/sh 
# Debug expect & screen script.

# You have to add quotes around a string to init your variable.
sent="blah"
# Debugged it by adding the next ine and seeing what it was initialized to...
echo $sent

# This was trying to execute the command instead of loading a variable with your
# variable = string = commandline... showed executing with errors, but blank as
# a variable... 
# expexec=$(/usr/bin/expect -c "/usr/bin/python /opt/app.py expect \"Interaction:\" send \"$sent\r\" interact")

# This is what I came up with:
expexec="/usr/bin/expect -c \"/usr/bin/python /opt/app.py expect \"Interaction:\" send \"$sent\r\" interact\""
# This was the debug line to see what it loaded as:
echo $expexec


/usr/bin/screen -L -dmS spawner /bin/sleep 30
/bin/sleep 1
/usr/bin/screen -S spawner -X screen screen -L -dR myDaemon
/bin/sleep 1
/usr/bin/screen -S myDaemon -X detach

## Can the Op explain this one? Is he tring to "echo" it or execute it? I'm thinking he needs to take the echo out of that next line...
/usr/bin/screen -S myDaemon -X stuff "echo $expexec"

/usr/bin/screen -S spawner -X stuff "exit\r"

```
When I'm trying to work out (debug) a bash or python script... I'll put in debug code (echo or print statements) to see if my code is reacting like I'm expecting it too and to show me what is going on underneath. I can always comment it out or remove it when I get it going. What it showed me is that your variable were not loading... ad your expect commandline string varaible was trying to execute on the string init.

Try the changes and see if that works. ...At least that part of it is working now.  Didn't really look at the screen lines... I know some say bash and expect play weird together sometimes, so some, if using bash, call to an expect script... then return.

Look in my comments. I have questions

The application is a python app? Why not a python script (sys:exec) talking with each other? Just a thought.

Thanks for the help mate. I admittedly did try your modifications, but they still weren't getting me there.

I ended up finding some other expect examples ([http://www.thegeekstuff.com/2010/10/expect-examples/](http://www.thegeekstuff.com/2010/10/expect-examples/)) which inspired me to split this script out into 2 scripts.

expect script:
```

#!/usr/bin/expect
set timeout 60

set sent [lindex $argv 0]

spawn /usr/bin/python /opt/app.py

expect "Interaction:"

send "$sent\r";

interact

```

main script:
```

#!/bin/sh

# variables
sent=blah
expectScript=/path/to/expect/script

# bash screen detachment foo
/usr/bin/screen -L -dmS spawner /bin/sleep 30
/bin/sleep 1
/usr/bin/screen -S spawner -X screen screen -L -dR myDaemon
/bin/sleep 1
/usr/bin/screen -S myDaemon -X detach

# sending the command to the screen
/usr/bin/screen -S myDaemon -X stuff "$expectScript $sent\r"

# close the screen spawner
/usr/bin/screen -S spawner -X stuff "exit\r"

```

---

