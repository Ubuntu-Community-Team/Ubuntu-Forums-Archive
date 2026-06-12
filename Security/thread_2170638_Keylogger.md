---
title: "Keylogger"
date: 2013-08-27
forum: Security
---

### Post by Quarkrad on 2013-08-27
I understand you can get keyloger software for Linux/Ubuntu.  I would like to know what the threat is of an 'undesirable'  putting such software on one's Ubuntu machine 'in the background' whilst surfing (have firewall installed).  I.e. is a Ubuntu machine as vulnerable as a windows machine re nasty keyloggers whilst surfing/emailing?  My understanding is no.

---

### Post by aperezhrd on 2013-08-27
I guess you can install a keylogger in Ubuntu. But to read the keyboard out of a defined focus (like a window or a textbox or the console) I think you have to get some special permission, or do a sudo :/

---

### Post by hakermania on 2013-08-27
> **aperezhrd said:**
> I guess you can install a keylogger in Ubuntu. But to read the keyboard out of a defined focus (like a window or a textbox or the console) I think you have to get some special permission, or do a sudo :/

No, you are completely wrong, here. I don't want to sound harsh or an expert, but you had better not answer at all if you are not sure about the correct answer, especially in security questions (I am not an expert, but I've seen things [http://i.imgur.com/cPUWj1j.jpg](http://i.imgur.com/cPUWj1j.jpg))

1) Fetch the package xmacro from the repositories
2) Run from a terminal
```
xmacrorec2 -k 9
```
3) Open another terminal, give
```
sudo su
```

4) Watch xmacrorec2 from the 1st terminal to log your password. To stop xmacrorec2 from logging, focus to the first terminal and press the Escape key, or Ctrl+C

So, here's the senario: You download an untrustworthy script from an online source which does what it says but it also downloads without your knowledge a program similar to xmacrorec2, using **wget**. Then, it gives **executable permissions** to it, it **hides it somewhere inside your home folder, ****gives it a name of its preference, e.g. zeitgeist-control** and it **executes** it as a background job. Also, it makes it **start everytime at startup **using a hidden desktop file (starting with dot) under a hidden directory (~/.config/autostart) and declares it as "Zeitgeist database indexer" in case you open some time the start-up applications and find it.

Please note that all the above may as well be in encoded into the original script, using some simple 2-way encryption, like base64. So, even if you inspect the script, you won't see the actual commands, but something weirder, like 

```
VEhJUyBJUyBBIE5JQ0UgWU9VVFVCRSBWSURFTzogaHR0cDovL3lvdXR1LmJlL1dpYm1jc0VHTEtvCg==
```

Everything you do now is being logged! And my guess is that it will take the average Ubuntu user more than a couple of days to realize that something's wrong - time enough to log a good amount of passwords.

Please notice that on the above story nothing requires root privileges to be done. All the bold points can be executed as simple user actions after you execute the malicious script.

_Never_ execute untrustworthy scripts or install untrustworthy DEBs!

---

### Post by Bucky Ball on 2013-08-27
Thanks for that comprehensive explanation, hakermania. ;)

So, how would you identify if a keylogger is running on your machine if you suspect such? Is there any simple way? Any prevention apart from not executing untrustworthy scripts or .debs?

---

### Post by hakermania on 2013-08-27
> **Bucky Ball said:**
> Thanks for that comprehensive explanation, hakermania. ;)

So, how would you identify if a keylogger is running on your machine if you suspect such? Is there any simple way? Any prevention apart from not executing untrustworthy scripts or .debs?

Short answer: There is not a simple way that I am aware of. Using techniques like the ones that xmacrorec2 uses, you are able to record the keystrokes without locking them: For example, there can be more than one instances of xmacrorec2 recording all of your keystrokes. If a keylogger is recording your strokes and you simultaneously run xmacrorec2, it won't have any problem recording your strokes as well. This isn't true for e.g. the camera of your laptop, if you are being recorded through your camera and you attempt to open e.g. Cheese, then you will be notified that your camera is in use = suspicious.

Long answer: The usual way to detect an unwanted process:

I don't know if these would be the best steps to follow, but if I suspected that a keylogger was running in my system, I would take the following steps:

1) Disconnect from the network - I wouldn't like any other keystrokes going anywhere

2) Go to ~/.config/autostart and do a

```
ls -al
```

Inspect the desktop files there for suspicious commands.

2) If nothing is found, then open System Monitor / top / htop and see every single process running under my user. I would also enable the "Status" of the process to be shown. A keylogger is always in Running status. That way, if the attacker has given it a name similar to other processes, the identification will be easier (e.g. if there are X instances of an executable and only one is in Running mode)

3) If I cannot find any suspicious command, I would run

```
ps aux | grep "$HOME" | grep -v grep
```

to see what is currently running through my home directory. The reason why I believe that if a keylogger is running then it is being done through my home directory is that getting root access to my system is quite a difficult thing to do. There aren't many efficient exploits out in the wild if your system is updated.

4) There is a possibility that once the script detected that there was no internet connection, it shut itself down. I would search for all the executable files in my home directory and inspect them one by one:

```
find ~/ -executable -type f
```

In case the executed file is a script without the executable bit (which can be executed through e.g. the command *bash scriptname *then I would run this slow but reliable script:

```
#!/bin/bash
find ~/ -type f > all_files
while read i; do
   file -b "$i" | grep script &> /dev/null
   if [[ $? -eq 0 ]]; then
      echo "$i" >> script_files
   fi
done < all_files


rm -rf all_files

```
that will create a script_files file that will contain all the scripts inside your home directory. Recognizing what each one of them is and does would be a good move.

5) If nothing is found then probably your system is secure. There is the case that the file is run with root privileges, using one of the many ways to do this. The only way that someone could do this is if you run something as root or you gave it your password.

6) If you want, you can install Wireshark and see the packages that go in and out of your PC. I haven't used it a lot but I find it hard to distinguish between malicious packets and non malicious ones - I guess you need to be more of an expert to properly understand the packets. Your keystrokes can leave your PC encrypted (in base64, for example) so as to be hard for you to find out. Also, there is no way that every keystroke is leaving your pc while it is being typed, They are logged and they are leaving your PC e.g. once every hour, or even once every day or week.


As for what I would recommend in order to avoid such attacks, which can be from a keylogger to a password stealer to a home directory remover, that is my opinion:

1) Install a good firewall and learn to configure it.
2) DO NOT run servers for fun. Do not install apache or ssh servers in your laptop if you can avoid it.
3) If you can't avoid it, then DO NOT use the default ports for them!
4) Always install all the available updates as soon as possible.

---

### Post by 3rdalbum on 2013-08-28
Gksudo warns you if it doesn't have an exclusive keyboard and mouse lock, though. Wont this alert you?

---

### Post by hakermania on 2013-08-28
> **3rdalbum said:**
> Gksudo warns you if it doesn't have an exclusive keyboard and mouse lock, though. Wont this alert you?

I don't get any warning if I am running xmacrorec2 and I run gksudo. XMacrorec2 does not have any problem logging your password, too. Try it yourself.

---

### Post by ulkoma on 2013-11-24
> **hakermania said:**
> No, you are completely wrong, here. I don't want to sound harsh or an expert, but you had better not answer at all if you are not sure about the correct answer, especially in security questions (I am not an expert, but I've seen things [http://i.imgur.com/cPUWj1j.jpg](http://i.imgur.com/cPUWj1j.jpg))

1) Fetch the package xmacro from the repositories
2) Run from a terminal
```
xmacrorec2 -k 9
```
3) Open another terminal, give
```
sudo su
```

4) Watch xmacrorec2 from the 1st terminal to log your password. To stop xmacrorec2 from logging, focus to the first terminal and press the Escape key, or Ctrl+C

So, here's the senario: You download an untrustworthy script from an online source which does what it says but it also downloads without your knowledge a program similar to xmacrorec2, using **wget**. Then, it gives **executable permissions** to it, it **hides it somewhere inside your home folder, ****gives it a name of its preference, e.g. zeitgeist-control** and it **executes** it as a background job. Also, it makes it **start everytime at startup **using a hidden desktop file (starting with dot) under a hidden directory (~/.config/autostart) and declares it as "Zeitgeist database indexer" in case you open some time the start-up applications and find it.

Please note that all the above may as well be in encoded into the original script, using some simple 2-way encryption, like base64. So, even if you inspect the script, you won't see the actual commands, but something weirder, like 

```
VEhJUyBJUyBBIE5JQ0UgWU9VVFVCRSBWSURFTzogaHR0cDovL3lvdXR1LmJlL1dpYm1jc0VHTEtvCg==
```

Everything you do now is being logged! And my guess is that it will take the average Ubuntu user more than a couple of days to realize that something's wrong - time enough to log a good amount of passwords.

Please notice that on the above story nothing requires root privileges to be done. All the bold points can be executed as simple user actions after you execute the malicious script.

_Never_ execute untrustworthy scripts or install untrustworthy DEBs!

Many apologies for bumping a zombie but installing package xmacro requires sudo i.e. root privileges , doesn't this mean no browser exploit can ever install a keylogger on my device as the browsers privileges themselves are not sufficient ?

---

### Post by cariboo on 2013-11-24
Almost anything can be installed in your home directory, so you don't really need elevated privileges to install a keylogger if it's installed in ~/USER.

---

### Post by hakermania on 2013-11-24
> **ulkoma said:**
> Many apologies for bumping a zombie but installing package xmacro requires sudo i.e. root privileges , doesn't this mean no browser exploit can ever install a keylogger on my device as the browsers privileges themselves are not sufficient ?

Pretty much what cariboo907 said. I didn't say that the malicious program would install something into your system folders, but into your home folder.

It doesn't need any special privilege in order to download something into your home directory, give it executable permissions and run it.

---

### Post by DuckHook on 2013-11-25
Insanely useful. Thanks for taking the time to write it. I'm subscribing to this one permanently to pass on in future.

---

