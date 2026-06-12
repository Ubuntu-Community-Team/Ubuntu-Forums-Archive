---
title: "Bash Script if empty result do something"
date: 2010-04-20
forum: Server Platforms
---

### Post by prodsacnetworking on 2010-04-20
HI,

I need to monitor process.
if the process is there, do something, if not there, do something else...

here is my code and it always see the process as there.

any ideas?

```

#!/bin/sh
if [ "ps aux |grep xinet |grep -v grep |grep -v cmagent" = "" ]; then
echo OFF
else
echo ON
fi

```

---

### Post by lloyd_b on 2010-04-20
> **prodsacnetworking said:**
> HI,

I need to monitor process.
if the process is there, do something, if not there, do something else...

here is my code and it always see the process as there.

any ideas?

```

#!/bin/sh
if [ "ps aux |grep xinet |grep -v grep |grep -v cmagent" = "" ]; then
echo OFF
else
echo ON
fi

```

You're not telling it to actually execute the "ps aux ..." command - as far as the shell is concerned, it's just another text string.

Instead of surrounding it with quotation marks, use the backtic (` - located above the TAB key on US keyboards).  This will tell the shell to actually execute the command, and use the results for the comparison.

Lloyd B.

---

### Post by prodsacnetworking on 2010-04-20
thanks a lot.

> if [`ps aux |grep xinet |grep -v grep |grep -v "pmon.sh" |grep -v cmagent` = ""]; then

it works.

---

### Post by prodsacnetworking on 2010-04-20
now I get:

[SIZE="5"][COLOR="black"]./check-pmon.sh: line 3: [oracle: command not found[/COLOR][/SIZE]

WARNING
oracle    6331  0.0  0.1 818980  9184 ?        Ss   Apr19   0:00 ora_pmon_ocogdev

my script:

```
#!/bin/sh
#sleep 5
if [`ps aux |grep pmon |grep -v grep |grep -v "check-pmon" |grep -v cmagent` = ""]; then
echo OK
#mailx -s "OK $HOSTNAME databases were closed for backup" boperator@domain
else
echo WARNING
ps aux |grep pmon |grep -v grep |grep -v "check-pmon" |grep -v cmagent #|mailx -s "WARNING $HOSTNAME databases were not closed for backup" boperator@domain
fi
```

---

### Post by Xipher on 2010-04-20
the test command (which [ is based on) actually has a flag to check if a string is empty, so you can do 

```

[ -z `ps aux |grep pmon |grep -v grep |grep -v "check-pmon" |grep -v cmagent` ]

```

help test in a shell will give you all of the flags you can use.

---

### Post by lloyd_b on 2010-04-21
> **prodsacnetworking said:**
> now I get:

[SIZE="5"][COLOR="black"]./check-pmon.sh: line 3: [oracle: command not found[/COLOR][/SIZE]

WARNING
oracle    6331  0.0  0.1 818980  9184 ?        Ss   Apr19   0:00 ora_pmon_ocogdev

my script:

```
#!/bin/sh
#sleep 5
if [`ps aux |grep pmon |grep -v grep |grep -v "check-pmon" |grep -v cmagent` = ""]; then
echo OK
#mailx -s "OK $HOSTNAME databases were closed for backup" boperator@domain
else
echo WARNING
ps aux |grep pmon |grep -v grep |grep -v "check-pmon" |grep -v cmagent #|mailx -s "WARNING $HOSTNAME databases were not closed for backup" boperator@domain
fi
```

Bash is kinda picky - make sure that there is a space after the "[" and before the "]", otherwise it doesn't realize you're doing a test.

Lloyd B.

---

### Post by KiLaHuRtZ on 2010-04-22
```
#!/bin/bash

# Set environment variables.
SHELL=/bin/bash
PATH=/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin:/bin:/sbin

# Check for running process and store results to variable.
myProc=`ps aux | grep pmon | grep -v grep | grep -v check-pmon | grep -v cmagent`

# Process results and compute logic.
if [[ (-z "$myProc") ]]; then
  echo OK
  mailx -s "OK $HOSTNAME databases were closed for backup" boperator@domain
else
  echo WARNING
  echo "$myProc" | mailx -s "WARNING $HOSTNAME databases were closed for backup" boperator@domain
fi

# End of file marker.
#eof
```

---

