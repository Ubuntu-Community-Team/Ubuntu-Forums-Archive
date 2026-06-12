---
title: "Does Ubuntu support this?"
date: 2012-09-01
forum: The Cafe
---

### Post by ki4jgt on 2012-09-01
[http://www.intel.com/content/www/us/en/architecture-and-technology/anti-theft/anti-theft-consumer-technology.html](http://www.intel.com/content/www/us/en/architecture-and-technology/anti-theft/anti-theft-consumer-technology.html)

---

### Post by Mikeb85 on 2012-09-01
I'm pretty sure it's controlled through the BIOS...

---

### Post by whatthefunk on 2012-09-02
Im guessing that it doesnt.  You have to get a service provider for the system to work.  They are listed on this page:
[http://www.intel.com/content/www/us/en/architecture-and-technology/anti-theft/anti-theft-service-providers.html](http://www.intel.com/content/www/us/en/architecture-and-technology/anti-theft/anti-theft-service-providers.html)

The Lo Jack site requires either Windows or Apple.  Email the others to see what they say.  A lot of things like this that are controlled by the bios dont work well in Linux...

---

### Post by Lucradia on 2012-09-02
Linux doesn't even support Intel's CPU boosting system (which requires a driver), I wouldn't have expected them to support this either.

---

### Post by mips on 2012-09-03
ki4jgt,

Not the same but a possible alternative [http://preyproject.com/](http://preyproject.com/)



> **Lucradia said:**
> Linux doesn't even support Intel's CPU boosting system (which requires a driver), I wouldn't have expected them to support this either.

Please elaborate? If you are talking about Turbo Boost then it's supposed to work from what I have read.
Have you seen [http://code.google.com/p/i7z/](http://code.google.com/p/i7z/)

---

### Post by Lucradia on 2012-09-03
> **mips said:**
> Please elaborate? If you are talking about Turbo Boost then it's supposed to work from what I have read.
Have you seen [http://code.google.com/p/i7z/](http://code.google.com/p/i7z/)

What if we don't want QT, and still want the GUI?

---

### Post by doorknob60 on 2012-09-03
> **Lucradia said:**
> What if we don't want QT, and still want the GUI?

Write your own in GTK? Seriously, it's no big deal to just install it, that's like asking to get VLC without any video or audio codecs, or something like that. If you don't like what's offered, code it yourself. Otherwise, deal with it :P

---

### Post by vexorian on 2012-09-03
> **Lucradia said:**
> What if we don't want QT, and still want the GUI?
picky guys tend not to get the cake.

---

### Post by Lucradia on 2012-09-04
> **vexorian said:**
> picky guys tend not to get the cake.

Cake's fattening, so is KDE.

---

### Post by cbennett926 on 2012-09-04
I have researched this as well, I can confirm that it does not because it states that it can only work with Windows/Mac :'( I wish they did though!

---

### Post by pqwoerituytrueiwoq on 2012-09-04
have access to a server?
you could make a script to check a page/file on the net and put a 1/0 in it 1=stolen, also waits for net connection
on xubuntu 12.04 at least with xfce 4.10 this will flood the screen with stolen messages and then shutdown
```
#!/bin/sh
while [ 1 -eq 1 ]; do # infinite loop for checking without reboot
    while [ -n "`ping www.google.com -c 1 2>&1 | grep '1 received'`" ]; do # while there is a net connection
        if [ "`curl **http://myserver.com/istolen.txt**`" == "1" ];do # if stolen
            while [ -z "`users`" ]; do # wait for a user to login (eg guest or normal user)
                sleep 1
            done
            i=0
            export DISPLAY=:0
            while [ $i -lt 154 ]; do # make 154 stolen alerts
                sudo -u "`users | sed 's/ /\n/g' | head -1`" notify-send --icon=info "STOLEN" "THIS COMPUTER IS STOLEN"
                i=$(($i+1))
            done
            sleep 5
            poweroff # shut off stolen system to make it unusable
        done
        sleep 5
    done
    sleep 5
done
```in /ect/rc.local add this line before exist
sh /path/to/script &
i suggest having a php script on the server that will record the ip address the stolen system is at
feel free to add a line to play a audio file and max out the volume and say something
"this computer is stolen 100 dollar cash reward, call 000-000-0000"
google has a text to speech generator

---

### Post by vexorian on 2012-09-05
> **Lucradia said:**
> Cake's fattening, so is KDE.
What does KDE have to do with any of this?

---

### Post by ki4jgt on 2012-09-07
> **pqwoerituytrueiwoq said:**
> have access to a server?
you could make a script to check a page/file on the net and put a 1/0 in it 1=stolen, also waits for net connection
on xubuntu 12.04 at least with xfce 4.10 this will flood the screen with stolen messages and then shutdown
```
#!/bin/sh
while [ 1 -eq 1 ]; do # infinite loop for checking without reboot
    while [ -n "`ping www.google.com -c 1 2>&1 | grep '1 received'`" ]; do # while there is a net connection
        if [ "`curl **http://myserver.com/istolen.txt**`" == "1" ];do # if stolen
            while [ -z "`users`" ]; do # wait for a user to login (eg guest or normal user)
                sleep 1
            done
            i=0
            export DISPLAY=:0
            while [ $i -lt 154 ]; do # make 154 stolen alerts
                sudo -u "`users | sed 's/ /\n/g' | head -1`" notify-send --icon=info "STOLEN" "THIS COMPUTER IS STOLEN"
                i=$(($i+1))
            done
            sleep 5
            poweroff # shut off stolen system to make it unusable
        done
        sleep 5
    done
    sleep 5
done
```in /ect/rc.local add this line before exist
sh /path/to/script &
i suggest having a php script on the server that will record the ip address the stolen system is at
feel free to add a line to play a audio file and max out the volume and say something
"this computer is stolen 100 dollar cash reward, call 000-000-0000"
google has a text to speech generator

I've already taken care of it from the software side :). I have a .onion address pointing to a secure shell :). I also have a warning message which will open up in firefox and tell the user it's hot. I've also got a python script setup that upon running will snap a photo from the webcame, capture audio from the microphone and lock the computer down so I'm not worried about that as much as if someone gets smart and erases the OS.

---

### Post by the8thstar on 2012-09-07
> **ki4jgt said:**
> I've already taken care of it from the software side :). I have a .onion address pointing to a secure shell :). I also have a warning message which will open up in firefox and tell the user it's hot. I've also got a python script setup that upon running will snap a photo from the webcame, capture audio from the microphone and lock the computer down so I'm not worried about that as much as if someone gets smart and erases the OS.

How did you do all that ?

---

### Post by ki4jgt on 2012-09-07
> **the8thstar said:**
> How did you do all that ?

- Install Tor without Vidalia
- Install ssh
- Setup ssh to only serve on localhost
- Setup a hidden Tor service [https://www.torproject.org/docs/tor-hidden-service.html.en](https://www.torproject.org/docs/tor-hidden-service.html.en) Point it to the ssh port and give it a custom connection port.
- Install Motion (also doubles as an http cam server)
- using python's os.system module you can have a custom script to exucute any terminal commands you want, which I sent to Motion and a python pulse audio script I downloaded.
- Save an html file somewhere. When you know the computer is online, you have to issue a certain command over ssh to open applications remotely but once the command is entered you simply enter firefox file.html.
- I'm working on sharing X over the ssh connection.

---

### Post by Stonecold1995 on 2012-09-08
You mind sharing any of the scripts?

---

### Post by Artemis3 on 2012-09-10
Don't you think if anyone stole a laptop, would format it and install something else?

---

### Post by Stonecold1995 on 2012-09-10
> **Artemis3 said:**
> Don't you think if anyone stole a laptop, would format it and install something else?

I think the average thief would just keep the computer the way it is, unless they can't access it because it's password protected.

---

### Post by ki4jgt on 2012-09-10
> **Stonecold1995 said:**
> You mind sharing any of the scripts?

Audio capture is here [https://bbs.archlinux.org/viewtopic.php?pid=325723](https://bbs.archlinux.org/viewtopic.php?pid=325723) and motion is what I used for the webcam. As for the lockup It's basically a poweroff since I have it password protected (except for guest where I'm hoping my target will go first :))

> **Artemis3 said:**
> Don't you think if anyone stole a laptop, would format it and install something else?

You'd be surprised. There have already been two reported cases of returned computers because theifs didn't wipe anything off the hard drive and if I'm not mistaken one of the owners had a DDNS pointed at his machine so he was able to really mess with the guy on the other end.

---

### Post by Ubun2to on 2012-09-12
> **ki4jgt said:**
> - Install Tor without Vidalia
- Install ssh
- Setup ssh to only serve on localhost
- Setup a hidden Tor service [https://www.torproject.org/docs/tor-hidden-service.html.en](https://www.torproject.org/docs/tor-hidden-service.html.en) Point it to the ssh port and give it a custom connection port.
- Install Motion (also doubles as an http cam server)
- using python's os.system module you can have a custom script to exucute any terminal commands you want, which I sent to Motion and a python pulse audio script I downloaded.
- Save an html file somewhere. When you know the computer is online, you have to issue a certain command over ssh to open applications remotely but once the command is entered you simply enter firefox file.html.
- I'm working on sharing X over the ssh connection.

Just make sure you have a computer to view all of this on after you get it setup-it would be a shame not to be able to use any of it.

---

