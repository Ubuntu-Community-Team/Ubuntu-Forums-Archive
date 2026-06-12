---
title: "Bash apt-get update script"
date: 2008-12-12
forum: Server Platforms
---

### Post by twilight7345 on 2008-12-12
I am trying to write a script that downloads and installs updates using apt-get. The core of my script is:
```
apt-get update && apt-get upgrade
```
This command, however, gives a Y/N prompt which would stop the script. I tried giving the upgrade command a /y switch but it did not like it. Anyone have any ideas?

---

### Post by dnairb on 2008-12-12
Try:

-y or --yes

instead of /y

---

### Post by tubezninja on 2008-12-12
Another possibility: 

```
sudo apt-get update && **echo 'y' |** sudo apt-get upgrade
```


Call me a control freak, but I'd personally prefer getting the chance to look over the updates and then give the okay myself, rather than blindly letting them happen.

---

### Post by Krupski on 2008-12-12
> **twilight7345 said:**
> I am trying to write a script that downloads and installs updates using apt-get. The core of my script is:
```
apt-get update && apt-get upgrade
```
This command, however, gives a Y/N prompt which would stop the script. I tried giving the upgrade command a /y switch but it did not like it. Anyone have any ideas?

Cut-n-paste this into a file named "update". Set it's permissions as executable (chmod 0755 update) and then copy it to a directory in your path such as "/usr/bin". This one will ask you if you want to install updates.

```

#!/bin/sh
/usr/bin/apt-get -V update
/usr/bin/apt-get -V dist-upgrade

```

If you want to run quietly and automatically (like in a cron job), use this instead. Set "[COLOR="Red"]**email@address**[/COLOR]" to your own email address of course:

```

#!/bin/bash
tmpfile=$( /bin/mktemp -t )
myname=[COLOR="Red"]**email@address.com**[/COLOR]
/bin/echo return-path: $myname >> $tmpfile
/bin/echo for: $myname >> $tmpfile
/bin/echo from: $myname >> $tmpfile
/bin/echo to: $myname >> $tmpfile
/bin/echo subject: Linux Update Status >> $tmpfile
/bin/echo Hello there ROOT... this is an informational message: >> $tmpfile
/bin/echo >> $tmpfile
/bin/echo APT-GET Update was run: $( /bin/date +%c ) >> $tmpfile
/bin/echo >> $tmpfile
/bin/echo -n "Result: " >> $tmpfile
/usr/bin/apt-get -qy update > /dev/null
/usr/bin/apt-get -qy dist-upgrade | grep -i installed >> $tmpfile
/bin/echo >> $tmpfile
/bin/echo Yours truly, "Your Linux Computer" >> $tmpfile
/bin/echo >> $tmpfile
/bin/cat $tmpfile | sendmail -t
/bin/rm $tmpfile
exit 0

```


If you want one that runs without any output or prompts, and does NOT send you email, use this:

```

#!/bin/bash
/usr/bin/apt-get -qy update > /dev/null
/usr/bin/apt-get -qy dist-upgrade > /dev/null
exit 0

```


Hope this helps.

-- Roger

---

### Post by Krupski on 2008-12-12
> **scaredpoet said:**
> Another possibility: 

```
sudo apt-get update && **echo 'y' |** sudo apt-get upgrade
```


Call me a control freak, but I'd personally prefer getting the chance to look over the updates and then give the okay myself, rather than blindly letting them happen.

Why not just use the "-y" command line option?

---

### Post by twilight7345 on 2008-12-15
> **Krupski said:**
> Cut-n-paste this into a file named "update". Set it's permissions as executable (chmod 0755 update) and then copy it to a directory in your path such as "/usr/bin". This one will ask you if you want to install updates.

```

#!/bin/sh
/usr/bin/apt-get -V update
/usr/bin/apt-get -V dist-upgrade

```

If you want to run quietly and automatically (like in a cron job), use this instead. Set "email@address" to your own email address of course:

```

#!/bin/bash
tmpfile=$( /bin/mktemp -t )
myname=email@address.com
/bin/echo return-path: $myname >> $tmpfile
/bin/echo for: $myname >> $tmpfile
/bin/echo from: $myname >> $tmpfile
/bin/echo to: $myname >> $tmpfile
/bin/echo subject: Linux Update Status >> $tmpfile
/bin/echo Hello there ROOT... this is an informational message: >> $tmpfile
/bin/echo >> $tmpfile
/bin/echo APT-GET Update was run: $( /bin/date +%c ) >> $tmpfile
/bin/echo >> $tmpfile
/bin/echo -n "Result: " >> $tmpfile
/usr/bin/apt-get -qy update > /dev/null
/usr/bin/apt-get -qy dist-upgrade | grep -i installed >> $tmpfile
/bin/echo >> $tmpfile
/bin/echo Yours truly, "Your Linux Computer" >> $tmpfile
/bin/echo >> $tmpfile
/bin/cat $tmpfile | sendmail -t
/bin/rm $tmpfile
exit 0

```


If you want one that runs without any output or prompts, and does NOT send you email, use this:

```

#!/bin/bash
/usr/bin/apt-get -qy update > /dev/null
/usr/bin/apt-get -qy dist-upgrade > /dev/null
exit 0

```


Hope this helps.

-- Roger

-y switch worked; I must have been using /y (brain still reverts to DOS occasionally). Thanks for the script, that is exactly what I was looking for.

-Jared

---

### Post by Krupski on 2008-12-15
> **twilight7345 said:**
> -y switch worked; I must have been using /y (brain still reverts to DOS occasionally). Thanks for the script, that is exactly what I was looking for.

-Jared

Glad it worked for you.

I always get confused when I go between Linux and Windows (DOS window in XP actually).

I'll type something like "chdir c:/imconing/tmp" and it fails... oops it's a BACKSLASH in Windows! :(

I've even aliased common Unix commands in my Windows DOS box because I get tired of typing "cp" or "ls" and getting "bad command or filename".

I wish I could totally divorce myself from Windows XP... but there's just some stuff that I *have* to use it for.

Maybe someday...

---

### Post by cariboo on 2008-12-15
There is a ready made solution in the repositories, it is called apt-cron, It goes out and checks daily for updates and downloads the updated packages and emails you when there downloads available. It doesn't install the updates, so you have to install them yourself.

Jim

---

### Post by gtdaqua on 2008-12-16
> **twilight7345 said:**
> I am trying to write a script that downloads and installs updates using apt-get. The core of my script is:
```
apt-get update && apt-get upgrade
```
This command, however, gives a Y/N prompt which would stop the script. I tried giving the upgrade command a /y switch but it did not like it. Anyone have any ideas?

Whenever in doubt, always use the --help switch or check the man pages. Almost anything can be scripted in linux without user interruption or in quiet mode or even super verbose mode.

apt-get --help would have reproduced this: [partly truncated]
```

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
**  -y  Assume Yes to all queries and do not prompt**
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.

```

---

