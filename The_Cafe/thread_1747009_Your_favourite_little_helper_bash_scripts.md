---
title: "Your favourite little helper bash scripts"
date: 2011-05-02
forum: The Cafe
---

### Post by Blutkoete on 2011-05-02
Hello!

I was wondering whether anyone wants to share his or her favourite self-programmed bash scripts that make small, but recurring tasks easier. I'm no expert on the subject, but I started to produce some scripts, so I'm curious what's out there that doesn't need to be reinvented.

My favourite at the moment is my **psgrep** script (I don't know whether there is a built-in command that does this):

```

#!/bin/bash
# psgrep: Combines ps with grep to look for specific programs directly.
ps -A | grep $1

```It's simple and saved me quite some typing.

So what little helpers do you use?

Blutkoete

---

### Post by matt_symes on 2011-05-02
Hi

> **Blutkoete said:**
> 
```

#!/bin/bash
# psgrep: Combines ps with grep to look for specific programs directly.
ps -A | grep $1

```It's simple and saved me quite some typing.

Nice. You can also set this up as an alias and pop it into your alias file.

```
[matthew@localhost ~]$ alias a="ps -A | grep $1"
[matthew@localhost ~]$ a screen
 1363 ?        00:00:00 gnome-screensav
 1583 pts/0    00:00:00 screen
 1584 ?        00:00:00 screen
[matthew@localhost ~]$
```

Kind regards

---

### Post by Blutkoete on 2011-05-02
> **matt_symes said:**
> 
Nice. You can also set this up as an alias and pop it into your alias file.


Thank you! That's much easier than my symlink-from-/usr/bin-approach :D.

---

### Post by amauk on 2011-05-02
**chroot_to**
If you have multiple Linux installs, this eases the process of booting into one and chrooting to another

Say you're messing around with a Gentoo install, and mess up X or the kernel - unable to boot
Boot into another distro (say Ubuntu), chroot to your Gentoo install, and you can run the Gentoo emerge package manager from the chroot

This even deals with updating grub should you install a new kernel in the chroot environment```
#!/bin/bash

if [ -n "$1" ] && [ -d "$1" ]; then
	CHROOT_PATH="$1"
else
	exit 0
fi

mount -o bind /proc ${CHROOT_PATH}/proc
mount -o bind /dev ${CHROOT_PATH}/dev
mount -o bind /dev/pts ${CHROOT_PATH}/dev/pts
mount -o bind /sys ${CHROOT_PATH}/sys
chroot ${CHROOT_PATH} /bin/bash

CHROOT_PID=$!
wait $CHROOT_PID

echo "Unmounting chroot environment"
umount $CHROOT_PATH/sys
umount $CHROOT_PATH/dev/pts
umount $CHROOT_PATH/dev
umount $CHROOT_PATH/proc

read -p "Re-install Grub on base config? " -n 1
echo ""
if [ "$REPLY" == "y" ]; then
	grub-install /dev/sda
	update-grub
fi
```



**metadata_extract**
Extracts metadata from video files into a spreadsheet (resolution, aspect ratio, runtime, etc.)
See this thread for details
[http://ubuntuforums.org/showthread.php?t=1300629&page=2](http://ubuntuforums.org/showthread.php?t=1300629&page=2)
```
#!/bin/bash

TOP_DIR="/media/raid5/media/Films/"
ASPECT_RATIOS=( 1.33 1.50 1.78 1.85 2.39 )

IFS=$'\n'
MIL_SECS=1
SECS=1000
FILES=`find "$TOP_DIR" -type f | sort`

# Col headers
echo "\"Directory\",\"File Name\",\"Extension\",\"Width\",\"Height\",\"Definition\",\"Aspect Ratio\",\"Closest AR\",\"Closest AR (Human)\",\"Run Time (Accuracy is codec dependant)\""

for FILE in $FILES
do
    FILENAME=`basename "$FILE" | sed 's|\(.*\)\.\(.*\)|\1|'`
    FILEEXT=`basename "$FILE" | sed 's|\(.*\)\.\(.*\)|\2|'`
    FILEDIR=`echo "$FILE" | sed "s|${TOP_DIR}||" | sed "s|${FILENAME}\.${FILEEXT}||" | sed 's|/$||'`

    METADATA=`mplayer -vo null -identify -frames 0 "$FILE" 2>/dev/null | grep '^ID_'`

    # Dimensions, Aspect Ratios, etc.
    VID_WIDTH=`echo "$METADATA" | grep 'ID_VIDEO_WIDTH' | grep -o '[0-9]\+$'`
    VID_HEIGHT=`echo "$METADATA" | grep 'ID_VIDEO_HEIGHT' | grep -o '[0-9]\+$'`
	if [ -n "$VID_WIDTH" -o -n "$VID_HEIGHT" ]; then
        VID_ASPECT_RATIO=`echo $VID_WIDTH $VID_HEIGHT | awk '{ printf("%.2f", $1/$2 ) }'`

        # Hi-Def or Standard Def
        if [ "$VID_WIDTH" -gt 720 ]; then
            VID_DEF="HD"
        else
            VID_DEF="SD"
        fi

        # Find closest AR from 'common' film AR's
        CLOSEST_AR_INDEX=""
        for ((i=0; i<${#ASPECT_RATIOS[@]}; i++))
        do
            HOW_CLOSE=`echo "scale=2; $VID_ASPECT_RATIO - ${ASPECT_RATIOS[$i]}" | bc -l`
            CLOSEST_AR_INDEX=`echo -e "${CLOSEST_AR_INDEX}\n${HOW_CLOSE}:${i}"`
        done
        CLOSEST_AR_INDEX=`echo "$CLOSEST_AR_INDEX" | sed 's/^-//;s/^\./0./' | sort -n | grep -o ':.*$' | sed 's/^://' | head -1`
        CLOSEST_AR=${ASPECT_RATIOS[$CLOSEST_AR_INDEX]}

        # Get human readable AR (x:y)
        MULTIPLE=1
        BREAK=0
        while [ $BREAK -eq 0 ]; do
            RATIO_INT=`echo "scale=2; $CLOSEST_AR * $MULTIPLE" | bc -l`
            if [[ $RATIO_INT =~ ^[0-9]+\.0[0-4]$ ]]; then
                RATIO_INT=`echo "$RATIO_INT" | grep -o '^[0-9]\+'`
                BREAK=1
            elif [[ $RATIO_INT =~ ^[0-9]+\.9[5-9]$ ]]; then
                RATIO_INT=`echo "$RATIO_INT" | grep -o '^[0-9]\+'`
                RATIO_INT=`expr $RATIO_INT + 1`
                BREAK=1
            else
                MULTIPLE=`expr $MULTIPLE + 1`
            fi
        done
        RATIO_HUMAN="${RATIO_INT}:${MULTIPLE}"
    else
        VID_WIDTH=0
        VID_HEIGHT=0
        VID_DEF="N/A"
        VID_ASPECT_RATIO=0.00
        CLOSEST_AR=0.00
        RATIO_HUMAN="N/A"

		if [ "$FILEEXT" == "mp4" ]; then
			# mp4 - give benefit of doubt, and label as HD
			VID_DEF="HD"
		fi
    fi

    # Runtime calcs
    RUNTIME_S=`echo "$METADATA" | grep 'ID_LENGTH' | sed 's|ID_LENGTH=\([0-9]\+\).*|\1|'`

	if [ -n "$RUNTIME_S" ]; then
        while [ "$RUNTIME_S" -gt 59 ]; do
            RUNTIME_M=`expr $RUNTIME_S / 60`
            RUNTIME_SUB=`expr $RUNTIME_M \* 60`
            RUNTIME_S=`expr $RUNTIME_S - $RUNTIME_SUB`
        done
        while [ "$RUNTIME_M" -gt 59 ]; do
            RUNTIME_H=`expr $RUNTIME_M / 60`
            RUNTIME_SUB=`expr $RUNTIME_H \* 60`
            RUNTIME_M=`expr $RUNTIME_M - $RUNTIME_SUB`
        done
        if [ "$RUNTIME_S" -lt 10 ]; then
            RUNTIME_S="0${RUNTIME_S}"
            RUNTIME_S=`echo "$RUNTIME_S" | sed 's|^0\+|0|;s|^0$|00|'`
        fi
        if [ "$RUNTIME_M" -lt 10 ]; then
            RUNTIME_M="0${RUNTIME_M}"
            RUNTIME_M=`echo "$RUNTIME_M" | sed 's|^0\+|0|;s|^0$|00|'`
        fi
        if [ "$RUNTIME_H" -lt 10 ]; then
            RUNTIME_H="0${RUNTIME_H}"
            RUNTIME_H=`echo "$RUNTIME_H" | sed 's|^0\+|0|;s|^0$|00|'`
        fi
        RUNTIME_NICE="${RUNTIME_H}:${RUNTIME_M}:${RUNTIME_S}"
	else
		RUNTIME_NICE="00:00:00"
	fi

    echo "\"${FILEDIR}\",\"${FILENAME}\",\"${FILEEXT}\",${VID_WIDTH},${VID_HEIGHT},\"${VID_DEF}\",${VID_ASPECT_RATIO},${CLOSEST_AR},\"${RATIO_HUMAN}\",\"${RUNTIME_NICE}\""
done
```

---

### Post by matt_symes on 2011-05-02
Hi[B]

@[/B][amauk]("http://ubuntuforums.org/member.php?u=384906")

**chroot_to. **I really like this. I have been chrooting the long way for far too long. Thanks for posting it. It saved me knocking up one myself. :P

Kind regards

---

### Post by amauk on 2011-05-02
> **matt_symes said:**
> Hi[B]

@[/B][amauk]("http://ubuntuforums.org/member.php?u=384906")

**chroot_to. **I really like this. I have been chrooting the long way for far too long. Thanks for posting it. It saved me knocking up one myself. :P

Kind regardsJust remember to make sure you change stuff to reflect your system
(like the assumption that grub is on /dev/sda)

I do tend to write stuff for my systems' setup, rather than generic stuff for any system

---

### Post by amauk on 2011-05-02
Not full scripts, but bash snippets designed for sourcing into other scripts

root_forbid & root_require
fairly self-explanatory, forbid or require root privs to run script

Example:
```
#!/bin/bash

. /media/scripts/include/root_require.sh

cat /etc/shadow
```


**root_forbid**
```
ROOT_UID=0     # Only users with $UID 0 have root privileges.
E_ROOT=68      # root exit error.

# Forbid running as root
if [ "$UID" -eq "$ROOT_UID" ]
then
  echo "You are running this script as root."
  echo "This has been forbidden for security reasons."
  exit $E_ROOT
fi
```


**root_require**
```
ROOT_UID=0     # Only users with $UID 0 have root privileges.
E_NOTROOT=67   # Non-root exit error.

# Run as root, of course.
if [ "$UID" -ne "$ROOT_UID" ]
then
  echo "Must be root to run this script."
  exit $E_NOTROOT
fi
```

---

### Post by DaithiF on 2011-05-02
> **Blutkoete said:**
> My favourite at the moment is my **psgrep** script (I don't know whether there is a built-in command that does this):

There *is *a command for this: **pgrep**  :)

---

### Post by Blutkoete on 2011-05-02
Argh! **pgrep** is even shorter than **psgrep**.

I really like the root/no-root verification scripts. They come in handy.

---

### Post by matt_symes on 2011-05-02
Hi

DaithiF is bang on the money again.

pgrep is great if you just want the PID or the PID and name. It allows to do things like

```
kill -9 $(pgrep -x vi)
```

You can use the small L switch to get the process name.

```
matthew@matthew-laptop:~$ pgrep -l fire*
1195 firegl
3445 firefox-bin
matthew@matthew-laptop:~$ 
```

Of course there are many ways in Linux to get the same job done ;)

Kind regards

---

### Post by wizard10000 on 2011-05-02
Not a script but an alias - it helps since you can't dump top to a text file.  First section is sorted by memory use, second section by CPU use.

```
alias processes="ps -eo pid,rtprio,ni,pri,pcpu,rss,comm --sort -rss && ps -eo pid,rtprio,ni,pri,pcpu,rss,comm --sort -pcpu"
```

---

### Post by Lars Noodén on 2011-05-03
> **matt_symes said:**
> It allows to do things like

```
kill -9 $(pgrep -x vi)
```

Which can be done with **pkill**

```

pkill -9 -x vi

```

---

### Post by matt_symes on 2011-05-03
Hi

> **Lars Noodén said:**
> Which can be done with **pkill**

```

pkill -9 -x vi

```

> Of course there are many ways in Linux to get the same job done

Exactly. :D

Kind regards

---

### Post by Blutkoete on 2011-05-04
Ok, I have to admit that I'm a real beginner when it's up to bash scripts (wow, amauk!), but I'll give it another shot and post something here. Maybe this time there isn't a built-in command that does the same only better :D.

```
#!/bin/bash
# apt-get-proxy: Executes apt-get with proxy settings (e.g. for use with apt-cache-ng). Use 0 for proxy to don't use a no proxy.
if [ "$1" = "0" ]
then
  apt-get $2 $3 $4 $5 $6 $7 $8 $9
else
  apt-get -o Acquire::http::Proxy="http://$1" $2 $3 $4 $5 $6 $7 $8 $9
fi

```

*Usage:* sudo apt-get-proxy <proxy-address-and-port> <normal apt-get arguments>

I use apt-cacher-ng with my netbook as the server (I take that one to the university all the time) because at home my bandwith is limited. apt-get is configured to use the netbook as a apt-cacher-ng-proxy, so I use this script if the netbook isn't running. I was always wondering whether there is something like an expression for "I want $*, only without $1" for scripting this.

I think I'll pimp up this script with amauk's root-require script.

---

