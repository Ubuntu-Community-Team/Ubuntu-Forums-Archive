---
title: "Nautilus-Clamscan, installed yet not working in 12.04,"
date: 2014-02-14
forum: Security
---

### Post by marksmarks on 2014-02-14
Ubuntu 12.04LTS

Installed Clamav & Databases (via FreshClam)

Command line scanning working.

Installed Nautilus-Clamscan (via synaptic)
Unable to see “scan file” in Nautilus RH click menu.
Reinstalled Nautilus-Clamscan.  Still not seen

Looking for protection from Hand of Thief maleware.

---

### Post by fugu2 on 2014-02-14
> **marksmarks said:**
> Ubuntu 12.04LTS

Installed Clamav & Databases (via FreshClam)

Command line scanning working.

Installed Nautilus-Clamscan (via synaptic)
Unable to see “scan file” in Nautilus RH click menu.
Reinstalled Nautilus-Clamscan.  Still not seen

Looking for protection from Hand of Thief maleware.

This is a nautilus-script for the clamscan tool. if you place this file in your ~/.gnome2/nautilus-scripts/ directory:
```

#!/bin/bash
#make a standard zenity title; intentionally unquoted throughout
title="--title Clamscan"

if [ "${#@}" -eq 1 ]; then
	(
	#make sure list has time to show up below progress bar
	sleep 0.5

	#zenity progress bar hack; echo is required to begin pulsating
	while echo; do sleep 10; done |
	    zenity --progress --pulsate $title \
		--text "Scanning. May take some time..." \
		--width 320 &
	progressbar="$!"

	#only process normal files
	if [ -f "$@" ]; then
		clamscan --no-summary "$@"
	fi
	kill "$progressbar"
	) | zenity --list $title --text "" \
	    --height 360 --width 820 \
	    --column "Result"
else
	(
	#make sure list has time to show up below progress bar
	sleep 0.5

	#zenity progress bar hack; echo is required to begin pulsating
	while echo; do sleep 10; done |
	    zenity --progress --pulsate $title \
		--text "Scanning. May take some time..." \
		--width 320 &
	progressbar="$!"

	for file in "$@"
	do
	    #only process normal files
	    if [ -f "$file" ]; then
		clamscan --no-summary "$file"
	    fi
	done
	kill "$progressbar"
	) | zenity --list $title --text "" \
	    --height 360 --width 820 \
	    --column "Result"
fi

```
then mark it as executable:
```
$ chmod +x ~/.gnome2/nautilus-scripts/clamscan
```
then when you right-click on a file in nautilus >> Scripts >> clamscan
it will scan the file for you.

---

### Post by deadflowr on 2014-02-14
> Looking for protection from Hand of Thief maleware

You already have it built in.
[https://blogs.rsa.com/rsa-peeks-into-the-bits-of-new-linux-based-trojan-hand-of-thief/](https://blogs.rsa.com/rsa-peeks-into-the-bits-of-new-linux-based-trojan-hand-of-thief/)
scroll down to Test Machine #2.
More on [ptrace scope]("https://wiki.ubuntu.com/Security/Features#ptrace")

---

### Post by open2reason on 2014-02-15
> Looking for protection from Hand of Thief maleware. 				

Some would suggest that HoT is passed abut by social engineering exploits, so be careful on what you click.

---

