---
title: "Web Site monitoring tool"
date: 2017-07-06
forum: Server Platforms
---

### Post by Michael_McKenney on 2017-07-06
I have installed 4 virtual web sites on my Apache Web Server.   I want a tool to be able to monitor traffic and resource usage.   I read about ApacheTop.  Most say it is no longer in development.  Any other suggestions for a monitoring tool?

---

### Post by SeijiSensei on 2017-07-06
There are programs that process Apache logs and create reports.  I use the ancient [analog]("http://www.c-amie.co.uk/analog/") program.  Another commonly used summarizer is [webalizer](https://blog.100tb.com/analyze-your-website-statistics-with-webalizer-on-debian-and-ubuntu).

[Google Analytics]("http://analytics.google.com/") offers a number of useful reports if you register your sites there.

---

### Post by Michael_McKenney on 2017-07-06
I will check them out, thanks.

---

### Post by Michael_McKenney on 2017-07-07
I need to work through webalizer for virtual servers.   I did the base install.  Now working on setting up each virtual server in it.  Not straight forward.

---

### Post by SeijiSensei on 2017-07-08
I run a script with analog that cycles over the virtual hosts.  Maybe you can modify it for webalizer:

```

#!/bin/sh

# where program files are stored
ANALOG="/usr/local/analog"
# path to the analog executable
ANALOGBIN="$ANALOG/analog"
# where to write log
LOG="$ANALOG/analog-reporter.log"

# I created a .cfg configuration file for each virtual
# in this directory.  Analog also writes a DNS cache
# file here to speed name resolution.
cd "$ANALOG/cfgs"

# delete stale dns lockfiles, if any
rm -f *.dnslock

# build the list of virtual hosts from the configuration files
# or analyze one host specified on the command line
if [ "$1" != "" ] 
then
    SITES=$1
else
    SITES=`ls *.cfg | grep -v analog`
fi

# iterate over the virtual hosts and write the analog report 
# specified in that host's .cfg file; run all the jobs in parallel
# in the background
for S in $SITES
do
    echo "`date` - Starting up $S" >> $LOG 2>&1

    $ANALOGBIN +g$S  >> $LOG 2>&1  &

    echo "$S started"     >> $LOG 2>&1 
done

exit 0

```

---

### Post by Michael_McKenney on 2017-07-10
Thank you, I will look at it.   Webalizer does not go very far into virtual web sites.

---

