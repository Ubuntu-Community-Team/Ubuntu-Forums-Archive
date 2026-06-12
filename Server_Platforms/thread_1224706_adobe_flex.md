---
title: "adobe flex"
date: 2009-07-27
forum: Server Platforms
---

### Post by bluethundr on 2009-07-27
someone expects me to configure adobe flex. he tells me it works under his windows and he is naive to mysql and linux.  does anyone have advice? he is most unruly.


this is the connect code:

```

<assql:MySqlService id="service" # yes I just noticed it was capitalized
               hostname="localhost" 
               username="theAcct"
               password="ourp455"
               database="dbs_qabeezag"
               autoConnect="true"
               connect="handleConnected(event)" 
               sqlError="handleError(event)" />

```


looks a lot like php to me. he insists it's not. :confused:

---

### Post by bluethundr on 2009-07-27
I tried installing flex but it claims I do not have a jvm on my path when clearly I do:

```
analytics:/home/bluethundr# echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/local/sbin:/usr/sbin:/sbin:/usr/lib/jvm/java-1.5.0-sun-1.5.0.17

```

```

analytics:/home/bluethundr# ./flexbuilder_linux_install_a4_081408.binPreparing to install...Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
No Java virtual machine could be found from your PATH
environment variable.  You must install a VM prior to
running this program.
```

---

### Post by komputes on 2009-07-30
> **bluethundr said:**
> it claims I do not have a jvm on my path when clearly I do:

/usr/lib/jvm/java-1.5.0-sun-1.5.0.17


Not too sure, but since that path does not hold executables I would try /usr/lib/jvm/java-1.5.0-sun-1.5.0.17/bin/

---

