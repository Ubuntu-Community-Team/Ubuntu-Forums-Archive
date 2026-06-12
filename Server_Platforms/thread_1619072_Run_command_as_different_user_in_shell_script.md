---
title: "Run command as different user in shell script"
date: 2010-11-11
forum: Server Platforms
---

### Post by radovid on 2010-11-11
Hi,

I have a problem running a command from a shell script impersonating another user than root. I need it, because I would like different environment avriables for running that command (actually the home variable)
Here we have an example script:
```

#!/bin/bash
test2="echo test2"
exec /bin/su - username -c $test2

```

The output in the shell is:
> 
declare -x DISPLAY="localhost:10.0"
declare -x HOME="/home/username"
declare -x LANG="sl_SI.utf8"
declare -x LOGNAME="kiki"
declare -x MAIL="/var/mail/username"
declare -x OLDPWD
declare -x PATH="/home/kiki/bin:/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games"
declare -x PWD="/home/username"
declare -x SHELL="/bin/bash"
declare -x SHLVL="1"
declare -x SPEECHD_PORT="7562"
declare -x TERM="xterm"
declare -x USER="username"
declare -x XDG_SESSION_COOKIE="8f79ba8af47464ea5b79ed4f4caefb32-1289496053.495498-283670387"

But he command does not get executed.

Does anybody have an idea why?

Thank you for your kind help.

---

### Post by arnavk007 on 2010-11-11
do 
```

su username
enter password
run the shell script

```

---

### Post by PapaNerd on 2010-11-11
Or, if you are root, you can do```
su - [username]
```and then run the script.

---

### Post by radovid on 2010-11-11
Hi,

I am aware of that, but I would like to avoid that somebody would accidentally run the script directly as root.

Also I would like to use it in the init procedure.

Thank you for your kind answer.

---

### Post by tgm4883 on 2010-11-11
You want

```
#!/bin/bash
test2="echo test2"
exec /bin/su - username -c "$test2"
```

And obviously username needs to be an actual username

---

### Post by radovid on 2010-11-12
I will copy you part of the actual script:

```

#!/bin/bash
export JAVA_HOME="/usr/lib/jvm/java-6-sun"
test="/bin/sh /home/username/tomcat55/bin/startup.sh"
exec /bin/su - username -c $test
```

So, this is it. The problem is that it does not lounch the target script and I cannot understand why.

And, yes, I am aware that I have to change "username" with the actual user name.

So, does anybody hava an Idea, why it does not want to work?

Thank you for your kind help.

---

### Post by koenn on 2010-11-12
remove the call to /bin/sh in $test ; it's unnecessary (scripts are executed by the interpreter mentioned on the first line of the script, and su already runs a login shell by itself) and interferes with your sudo statement (sudo executes /bin/sh but doesn't pass that script as a parameter to the shell it opened)

if you really think you need that /bin/sh, you need to quote the whole thing to make it 1 param to sudo : .... -c '/bin/sh /path/to/script'

you probably can loose the 'exec' as well


also, init scripts do run at root by default, so why are you absessing about this script not being run as root ?

I think you are making things too complicated and have no clear idea of what your trying to do

---

### Post by radovid on 2010-11-12
Because the server hosts two applications (a production and a test version) and booth are set up to store some important data into the home dir of the user which starts the application.

So if I start booth with the root user, they will start to write data in the same folders (and perhaps files)... no good.

It is a legacy I have to cope with with a long story of breaking the 1st administrator's law: "Don't touch things that simply work (usually because you want to enhance them)" 

I will test it and let you know ASAP.

Thank you for your kind understanding.

---

