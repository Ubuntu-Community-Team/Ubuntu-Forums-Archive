---
title: "do i need ssh files to configure the connection or not"
date: 2018-12-07
forum: Windows
---

### Post by dilbert_one on 2018-12-07
Dear experts
 

do i need ssh files to configure the connection or not
 
i just have installed the git package on my windows machine.
i have up and running the bash client
 
now i want to do the configuration - ....
question - do i need to have ssh-files for setting up the connection?
 ```
Mitarbeiter@260-36-B3-PC-04 MINGW64 ~
$ git config
usage: git config [<options>]

Config file location
    --global              use global config file
    --system              use system config file
    --local               use repository config file
    -f, --file <file>     use given config file
    --blob <blob-id>      read config from given blob object

Action
    --get                 get value: name [value-regex]
    --get-all             get all values: key [value-regex]
    --get-regexp          get values for regexp: name-regex [value-regex]
    --get-urlmatch        get value specific for the URL: section[.var] URL
    --replace-all         replace all matching variables: name value [value_regex]
    --add                 add a new variable: name value
    --unset               remove a variable: name [value-regex]
    --unset-all           remove all matches: name [value-regex]
    --rename-section      rename section: old-name new-name
    --remove-section      remove a section: name
    -l, --list            list all
    -e, --edit            open an editor
    --get-color           find the color configured: slot [default]
    --get-colorbool       find the color setting: slot [stdout-is-tty]

Type
    -t, --type <>         value is given this type
    --bool                value is "true" or "false"
    --int                 value is decimal number
    --bool-or-int         value is --bool or --int
```

---

### Post by TheFu on 2018-12-07
You don't need ssh unless you want to access remote systems over ssh.  github would use an ssh connection.  Local git repo management doesn't need ssh.

Normal network connections don't need ssh. For example, network manager and using email programs and web browsers do not require ssh.

OTOH, having sshd running on every system so you can access each of them over network connections can be very helpful.  I setup sshd with fail2ban on all my systems.  The openssh-server package includes the sshd daemon.

Based on your prompt, I doubt this is an Ubuntu question.

---

### Post by slickymaster on 2018-12-07
Thread moved to **Windows** for a better fit

---

