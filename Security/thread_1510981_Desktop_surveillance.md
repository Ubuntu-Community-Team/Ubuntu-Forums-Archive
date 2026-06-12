---
title: "Desktop surveillance"
date: 2010-06-16
forum: Security
---

### Post by MarkusIggy on 2010-06-16
Hi!

This might be the wrong place to post this, but I'll share it here anyway. :)

As I am a paranoid bastard, I made a bash screencap-script for my Ubuntu-computer, so I can check if anyone uses my computer for things I don't want them to do (eg. checking if anyone is viewing passwords stored in FireFox, looking at private files, or other things I find disturbing). There might be other people than me that is paranoid and want to monitor what's going on on their computers while they are away or letting someone else use their computer when going to the bathroom.

This is a small script, and as I'm quite new to bash-scripting, I'd like to hear if there is any improvements that can be done, so I can learn more and become better at such scripting.

The script requires Imagick (sudo apt-get install imagemagick) and a folder in the ~-directory (/home/username) called ".screen" (hidden, as this makes it more difficult to "intruders" to find it and it looks more like a system-folder than a monitoring-folder).

The script:
```

#!/bin/bash

i=1;
j=`date`;
user=`whoami`;
cd "/home/$user/.screen";
mkdir "$j";
cd "$j";
while [ $i ];
do
	import -window root scrn$i.png;
	sleep 3s;
	i=$(($i+1));
done;

```

Add this script to /usr/local/bin and then go to keyboard-shortcuts in GNOME and add a shortcut-key-combination of your own choice for the script. Call it whatever you'd like, and the command you want to run is simply "screen". To add a shortcut for stopping the script, you add another shortcut-key-combination to the command "killall screen".

This enables you to monitor activity on your computer while you're away, saving png-screenshots of your desktop every three seconds in the folder /home/username/.screen/date. 

NOTE: I'm not taking any responsibility for what you do with this script. Remember that monitoring someone's activities is never the right way to handle anything. Also, it's illegal many places. Take care and use it only for educational and testing purposes.

---

### Post by anomie on 2010-06-16
[QUOTE=MarkusIggy]... so I can check if anyone uses my computer for things I don't want them to do (eg. checking if anyone is viewing passwords stored in FireFox, looking at private files, or other things I find disturbing)[/QUOTE]

Not to sidestep the crux of the matter, but I'd point out that all three have solutions that don't require screenshot monitoring: 
[list=1]
[*] Encrypt your Firefox saved passwords (i.e. use a master password)
[*] Encrypt your private files (e.g. filesystem encryption, or gnupg or openssl for single file encryption)
[*] Mind your own business WRT things other people are doing that you find disturbing ;) 
[/list]

While we're going down tangents, the semi-colons at the end of your bash script lines are superfluous.

---

### Post by mdebusk on 2010-06-16
> **MarkusIggy said:**
> As I am a paranoid bastard, I made a bash screencap-script for my Ubuntu-computer

A paranoid person, or even a reasonably intelligent person, would lock their system before walking away from it.

---

### Post by yeleek on 2010-06-16
> **mdebusk said:**
> A paranoid person, or even a reasonably intelligent person, would lock their system before walking away from it.

Hear, Hear - if you have to let people use your machine, give them guest access.

---

### Post by needhelppeeps on 2010-06-16
maybe he wants to see what kinda sites they are going to, though. Like to see if hot chicks look at porn on his pc or something lol

---

### Post by FuturePilot on 2010-06-16
> **anomie said:**
> Not to sidestep the crux of the matter, but I'd point out that all three have solutions that don't require screenshot monitoring: 
[list=1]
[*] Encrypt your Firefox saved passwords (i.e. use a master password)
[*] Encrypt your private files (e.g. filesystem encryption, or gnupg or openssl for single file encryption)
[*] Mind your own business WRT things other people are doing that you find disturbing ;) 
[/list]

While we're going down tangents, the semi-colons at the end of your bash script lines are superfluous.

In addition, lock your computer when you're not using it, and if you want to let someone use your computer, give them the guest session. That's why it's there.

---

