---
title: "Attach to existing DBUS session over SSH"
date: 2009-02-03
forum: Tutorials
---

### Post by SeanHodges on 2009-02-03
One thing that was frustrating me for a while was being unable to remotely control my running desktop applications over SSH. This was something I had got accustomed to with DCOP, and the advent of DBUS appeared to take the functionality away from me.

The script below allows you to attach to an existing DBUS session when connecting to a machine remotely via SSH. This gives the ability to control DBUS-enabled applications remotely using utilities like qdbus, similar to how DCOP used to work.


**Instructions for use**

1) Login to the target machine locally first. Start some applications that you want to remote control (e.g. Rhythmbox).

2) Run the script below onto the target machine, and run it from a remote SSH session **by typing "source ./name_of_script.sh"**. Doing this allows the script to export the variable correctly. 

```
#!/bin/bash

# Remember to run this script using the command "source ./filename.sh"

# Search these processes for the session variable 
# (they are run as the current user and have the DBUS session variable set)
compatiblePrograms=( nautilus kdeinit kded4 pulseaudio trackerd )

# Attempt to get a program pid
for index in ${compatiblePrograms[@]}; do
	PID=$(pidof -s ${index})
	if [[ "${PID}" != "" ]]; then
		break
	fi
done
if [[ "${PID}" == "" ]]; then
	echo "Could not detect active login session"
	return 1
fi

QUERY_ENVIRON="$(tr '\0' '\n' < /proc/${PID}/environ | grep "DBUS_SESSION_BUS_ADDRESS" | cut -d "=" -f 2-)"
if [[ "${QUERY_ENVIRON}" != "" ]]; then
	export DBUS_SESSION_BUS_ADDRESS="${QUERY_ENVIRON}"
	echo "Connected to session:"
	echo "DBUS_SESSION_BUS_ADDRESS=${DBUS_SESSION_BUS_ADDRESS}"
else
	echo "Could not find dbus session ID in user environment."
	return 1
fi

return 0
```

3) Once the script has been run successfully, you will be able to remotely control your applications using qdbus:

```
qdbus org.gnome.Rhythmbox /org/gnome/Rhythmbox/Player playPause false
```

Consult the "qdbus" man page for information on how to use it.

If you want to add this to your .bashrc, see [this post]("http://ubuntuforums.org/showpost.php?p=7222765&postcount=4").


**Caveat**

This script was written to detect the first session it finds, if there are multiple logins on the target machine it may break the script or connect to the wrong session. If you have some suggestions for this, please let me know. 


Constructive criticism/feedback is welcome :) I've also uploaded the script to the "[League of Scripters]("https://launchpad.net/~scripters")" repository, feel free to commit fixes directly if you would prefer.

---

### Post by jpeddicord on 2009-02-04
Interesting tips. Though I see this depends on Nautilus to be running - any way to scan the environ for something desktop-agonistic? (Shooting in the dark - pulseaudio maybe?)

---

### Post by SeanHodges on 2009-02-05
> **jacobmp92 said:**
> Interesting tips. Though I see this depends on Nautilus to be running - any way to scan the environ for something desktop-agonistic? (Shooting in the dark - pulseaudio maybe?)

Good idea. The original version depended on either nautilus or kdeinit to be running, which I figured would work in most scenarios (stock Ubuntu/Kubuntu/Xubuntu installs), but obviously you can't depend on any single process to be running if you want to be desktop neutral. 

I've amended the script to include both pulseaudio and trackerd in the scan, and made it easier to expand on these in the future.

---

### Post by snowboarder13 on 2009-05-06
I had trouble getting the script to actually export the variable, so I rewrote it and packed it into a one-liner and stuck it in my .bashrc file.  :)

```
alias getdbus="export DBUS_SESSION_BUS_ADDRESS=`cat /proc/$(pidof kded4)/environ | tr '\0' '\n' | grep DBUS_SESSION_BUS_ADDRESS | cut -d '=' -f2-`"
```

I used kded4 as the process as it should always be running for me.  Now that I logged in here to post this and say I couldn't get the script working, I noticed that I initially read your post too fast.  Running ./script.sh is not the same as running "source ./script.sh".  *Smacks head*.  Anyhow, great work, I wouldn't be happy with remote amarok control w/o this post. :)

Ps. For anyone who doesn't know the 'alias' command, it just takes everything in the quotes and maps it to whatever command name you choose.  Thus, after logging in via SSH, just type "getdbus" and it will get the variable, just like Sean's script.

---

### Post by SeanHodges on 2009-05-11
> **snowboarder13 said:**
> I had trouble getting the script to actually export the variable, so I rewrote it and packed it into a one-liner and stuck it in my .bashrc file.  :)

Thanks for the feedback :) I've added the "kded4" target to the script so that it is compatible with KDE4 as well as KDE3. I like the one-liner approach as well, some people do prefer compact solutions instead of verbose ones.

---

### Post by dfm21 on 2009-07-22
Thank you, SeanHodges, for the initial implementation!

And thank you, snowboarder13, for the one-liner!

There is a way to determine if you are logging in via ssh, so you can safely add the following to your remote box's .bashrc:

```
#!/bin/bash
if [[ -n $SSH_CLIENT ]]; then
    export DBUS_SESSION_BUS_ADDRESS=`cat /proc/$(pidof kded4)/environ | tr '\0' '\n' | grep DBUS_SESSION_BUS_ADDRESS | cut -d '=' -f2-`
fi
```

(I found this tip [here]("http://forums.macosxhints.com/archive/index.php/t-6513.html").)

---

### Post by wump on 2010-08-29
Thanks, this was very useful :D

---

### Post by Ganton on 2011-12-03
> **dfm21 said:**
> 
```
#!/bin/bash
if [[ -n $SSH_CLIENT ]]; then
    export DBUS_SESSION_BUS_ADDRESS=`cat /proc/$(pidof kded4)/environ | tr '\0' '\n' | grep DBUS_SESSION_BUS_ADDRESS | cut -d '=' -f2-`
fi
```


"-z" from grep is there for something :-) . Also, beware that "pidof kded4" sometimes returns two values, we can avoid that using "pgrep -u "$USER":

```

#!/bin/bash
if [[ -n $SSH_CLIENT ]]; then
     export $(cat /proc/$(pgrep "kded4" -u "$USER")/environ | grep -z "^DBUS_SESSION_BUS_ADDRESS=")
fi

```

---

