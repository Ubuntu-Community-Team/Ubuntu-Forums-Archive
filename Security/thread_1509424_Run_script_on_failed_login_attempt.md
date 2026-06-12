---
title: "Run script on failed login attempt"
date: 2010-06-14
forum: Security
---

### Post by kkaldroma on 2010-06-14
I have a simple bash script that takes a picture of the user with my webcam, I want it to run when a login attempt fails.

I understand messing with the login is a terrible security risk...
But I want know, is it possible.

---

### Post by bruno9779 on 2010-06-14
Interesting question. I am watching the thread.

I have also another approach. Maybe it is easier to just take a pick of whoever tries to log in.
putting your script before the login attempt, would almost surely prove easier than running it after a failed attempt

---

### Post by Ryan Dwyer on 2010-06-14
You could set up a script to run on boot which checks /var/log/auth.log every 5 seconds or so.

---

### Post by kkaldroma on 2010-06-14
> script to run on boot which checks /var/log/auth.log every 5 seconds 

I was thinking of something like the log checker but I figured since there is already an event [failed login] I could try and tap into that.

> Maybe it is easier to just take a pick of whoever tries to log in

This would work for an initial login attempt but I also want it to take a picture of failed logins after I lock my screen.

Thank you for the feed back and the quick responses.

---

### Post by kkaldroma on 2010-06-14
I took everyones suggestions and threw this script together.
I needed to install 'gstreamer' and to change auth.log permissions to 666 for it to work.

To prevent the script from just looping until more logs are dumped into 'auth.log' I have the echo \n\n\n... line. 
I hate it, if anyone has a better idea please let me know.

Also, as you can see caps 1 and 2 are just deleted. This is because my camera needs a second or two to kick on (i guess) and the first two pics are either black or garbled.


```

! /bin/bash

cd /home/USER/Pictures/Webcam/
LOG="/var/log/auth.log"

while true
do
TIMESTAMP=$(date +%R.%S-%B-%d)
TRIGGER=$(tail $LOG | grep "fail" | wc -l)
if [ $TRIGGER -gt 0 ]
then
        streamer -t 10 -r 1 -s 640x480 -o cap00.jpeg > /dev/null

        cp cap03.jpeg $TIMESTAMP\ 1.jpg
        cp cap04.jpeg $TIMESTAMP\ 2.jpg
        cp cap05.jpeg $TIMESTAMP\ 3.jpg
        cp cap06.jpeg $TIMESTAMP\ 4.jpg
        cp cap07.jpeg $TIMESTAMP\ 5.jpg
        rm cap*
        echo -e "\n\n\n\n\n\n\n\n\n\n" >> /var/log/auth.log

fi
done

```If anyone has any better ideas, or knows how to incorporate it into my original question [Run script on failed log attempt] ((I.E without a constantly running while loop))
Please post.

---

### Post by bruno9779 on 2010-06-14
I have another idea.

/var/log/auth could be watched with [inotify]("http://en.wikipedia.org/wiki/Inotify") for changes.

You would need a startup script at boot, for inotify
This would then call on your webcam script every time the log get modified

If you use the 2 scripts approach, the first one would be good for anyone wanting to run a script at failed logon.

EDIT: this probably helps, but I am no good at C...

[http://ik.homelinux.org/index.rhtml/projects/c/inotify](http://ik.homelinux.org/index.rhtml/projects/c/inotify)

---

### Post by bruno9779 on 2010-06-14
I have also found this:

[http://pwet.fr/man/linux/administration_systeme/famd](http://pwet.fr/man/linux/administration_systeme/famd)

but it also involves system calls.


This is another approach yet using stat: 

[http://nixcraft.com/shell-scripting/657-if-file-modified-execute-script.html](http://nixcraft.com/shell-scripting/657-if-file-modified-execute-script.html)

---

### Post by kkaldroma on 2010-07-03
Update:
I did run into a few strange problems after incorporating this script. My virtual box 'ose... something or other' would fail to start and some other emulation devices would freeze at odd intervals. To fix this I added a "sleep 1" after the while true ; do"
This drastically dropped the PC usage %'s and solved the Vbox and other issues while still doing it's job.

Since no one has touched this thread in about 2 weeks I will just figure this solution is the best solution ( does anyone else smell a challenge? ).

---

### Post by kkaldroma on 2010-09-09
I guess this is the best we can do.




[Solved]

---

### Post by BkkBonanza on 2010-09-10
The only way to do this properly is to hook it into PAM.
PAM already processes the failed login attempt by reporting it in the log.

I looked into this a bit and found an elegant way to do it.

Edit the /etc/pam.d/common-auth file and insert this line immediately before the line with **pam_deny.so** module,

**auth    [default=ignore]    pam_exec.so seteuid /usr/bin/grab**

Now edit the two lines above (pam_unix and pam_winbind) and change the success=2 to success=3 and likewise success=1 to success=2. This has it skip an extra line when auth is successful. So it skips our script.

That's it. Make a script /usr/bin/grab to do what you want when login fails.

I used ffmpeg since I had that already and this is mine,

```
#!/bin/bash
ts=`date +%s`
ffmpeg -f video4linux2 -s vga -i /dev/video0 -vframes 3 /tmp/vid-$ts.%01d.jpg
exit 0
```

Note it must return 0. Of course, you can have it do whatever.
It would be good to save a short video actually.

---

### Post by kkaldroma on 2010-09-10
We have a winner!

BkkBonaza
Your solution is much better thank you.

---

### Post by BkkBonanza on 2010-09-13
If for a laptop/notebook in a theft situation...

My latest thoughts are that a pam script should upload captured images to some file hosting service and/or email them, or a link. This way once they're captured they get sent off to "somewhere" you can get to, along with some IP info.

The reason being that once they boot up and try to login a couple times unsuccessfully they'll probably install Windows and be done with it. You want to catch as much ID/Location info as you can in the briefest opportunity before it's gone.

---

### Post by kkaldroma on 2010-09-29
Here we go, this is the end result.
Using the uuencode and mailx will send the captured jpgs to my e-mail account the second a network connection is found.

Since I am on a college campus with an auto-connect set up for the campus wide wifi this will work fine for a anti-theft device (or at least I can see the face of the dude that stole my laptop while he is within range of campus). 

Thanks for all of the help everyone.

```

#! /bin/bash

EMAIL='[your@email.address]'
USR=[your user name]
TIMESTAMP=$(date +%R.%S-%B-%d)

cd /home/$USR/Pictures/Webcam/
streamer -t 10 -r 1 -s 640x480 -o cap00.jpeg > /dev/null

        cp cap03.jpeg $TIMESTAMP-1.jpg
        cp cap04.jpeg $TIMESTAMP-2.jpg
        cp cap05.jpeg $TIMESTAMP-3.jpg
        cp cap06.jpeg $TIMESTAMP-4.jpg
        cp cap07.jpeg $TIMESTAMP-5.jpg
        rm cap*

(for i in *.jpg
do 
      uuencode $i $(basename $i) 
done
) | mailx -s "Security Allert- $TIMESTAMP" $EMAIL

mv /home/$USR/Pictures/Webcam/*.jpg /home/$USR/Pictures/Webcam/old/


```

---

