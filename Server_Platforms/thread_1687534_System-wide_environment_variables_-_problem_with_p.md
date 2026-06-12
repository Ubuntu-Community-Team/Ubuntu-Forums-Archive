---
title: "System-wide environment variables - problem with parsing variables on BOOT"
date: 2011-02-14
forum: Server Platforms
---

### Post by nicolasdiogo on 2011-02-14
hi folks,

i find the documentation about ubuntu Environment variables a little strange.

[https://help.ubuntu.com/community/EnvironmentVariables#System-wide%20environment%20variables]("https://help.ubuntu.com/community/EnvironmentVariables#System-wide%20environment%20variables")

on **/etc/environment**

if i try to set a variable say;

```

MY_APP_HOME="/opt/my_app"

```

and then add this variable to the system PATH variable like;

```
PATH=$PATH":"$MY_APP_HOME

```
it fails after i reboot.


however, if i run;

```
source /etc/environment
```

my variable are translated correctly.  so clearly it is a problem when booting the system - as it does not PARSE variables.

it seems odd since other linux distributions do variable parsing (eg: CentOS).

is this a flaw or should i just copy the same string more then once in the file.

thanks,


Nicolas

---

### Post by ashikaga on 2011-02-14
Your question is well-answered [_here._]("http://old.nabble.com/Re%3A--etc-environment%2C-variables-aren%27t-expanded-p17287569.html")

---

### Post by nicolasdiogo on 2011-02-14
thanks for clarifying that

/etc/environment is just useless..

even though the official documentation says otherwise.

with regards,

---

