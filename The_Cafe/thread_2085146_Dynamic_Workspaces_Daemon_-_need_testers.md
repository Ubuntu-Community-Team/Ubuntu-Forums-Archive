---
title: "Dynamic Workspaces Daemon - need testers"
date: 2012-11-17
forum: The Cafe
---

### Post by Speaktrap on 2012-11-17
Hi there,
I wrote this bash script so any window manager could behave like GNOME Shell - there is always one workspace more than you are currently using ;). I enjoyed this concept in GNOME3 a lot, but the whole environment was just too heavy for my PC, so I started to work on a script which would work similarly. This is first public release :)
Just make sure you have *wmctrl* installed (*sudo apt-get install wmctrl*), *chmod +x* it and run (optionally place it in your *~/.local/bin*). I'm using it with Openbox, but I wish to know if it's working on Xfce, KDE etc.
I'm afraid it might be not compatible with Compiz (as it's using viewport instead of workspaces) and thus with Unity.

Download:
[http://dl.dropbox.com/u/46268581/bash/dynspacesd](http://dl.dropbox.com/u/46268581/bash/dynspacesd)

Please report feedback!

---

### Post by cariboo on 2012-11-17
This comes up fairly often that someone with zero posts, and no history on the forums asks us to test their scripts. How are we to know if it's safe to use the the script, if we don't know who you are?

I'd suggest you use launchpad to host your script. It is a lot more work, but if you've read and accepted the Ubuntu code of conduct, many more users would be willing to test your script.

---

### Post by Speaktrap on 2012-11-17
You're absolutely right, it's A LOT of work, not sure if it's really worth it. This is what I ended with: [https://launchpad.net/dynspacesd](https://launchpad.net/dynspacesd) (I still don't understand managing launchpad, but that's not the point)

If you don't trust the script, why don't you take a look? It's quite short, doesn't use sudo, there's no file operational commands (including *rm* ;) ), I'd say it's safe

---

### Post by rai4shu2 on 2012-11-17
Or, you know just paste it on the forum:

```
#!/bin/bash
#Dynamic Workspaces Daemon by Speaktrap (spazus@gmail.com)
exec_name="$(basename "$(test -L "$0" && readlink "$0" || echo "$0")")"
if [ $(echo ${#exec_name}) -gt 15 ]; then
	echo "Basename too long!"
	exit 1
fi
if [ $(ps -A | grep $exec_name | wc -l) -lt 3 ] ; then
while : ; do
	refresh_rq=1
	while [ $refresh_rq = 1 ] ; do
		refresh_rq=0
		for i in $(seq $((`wmctrl -d | wc -l` - 1))) ; do	
			if [[ -z `wmctrl -l | grep " "$(($i - 1))" "` ]] ; then
				for k in $(seq $((`wmctrl -l | grep " "${i}" " | wc -l`))) ; do
wmctrl -i -r $(wmctrl -l | grep " "${i}" " | cut -d ' ' -f 1 | sed -n 1p) -t $((${i} - 1))
					refresh_rq=1
					done
				fi
			done
	done
	k=0
	i=`wmctrl -d | wc -l`
	while [[ -z `wmctrl -l | grep " "$i" "` ]] ; do
		k=`expr $k + 1`
		i=`expr $i - 1`
		done
	if [ $k -gt 2 ] ; then wmctrl -n $((`wmctrl -d | wc -l` - k + 2)) ; fi
	if [ $k -eq 1 ] ; then wmctrl -n $((`wmctrl -d | wc -l` + 1)) ; fi
	sleep 1
	done
fi
```

---

