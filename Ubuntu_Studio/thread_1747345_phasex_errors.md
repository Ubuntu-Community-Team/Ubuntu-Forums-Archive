---
title: "phasex errors"
date: 2011-05-02
forum: Ubuntu Studio
---

### Post by il lupo on 2011-05-02
Hello, All--

i just upgraded to Natty and decided to play with phasex.  Unfortunately, it won't start.  i get a variety of errors.  Here is the first:

Using client name phasex
Bus error

i could use some more information, there.  Outside of that, here is the second:

Using client name phasex
Connect: can't connect named semaphore name = jack_sem.1000_default_system err = Permission denied
Cannot open phasex client
Using client name phasex-01
Connect: can't connect named semaphore name = jack_sem.1000_default_system err = Permission denied
Cannot open phasex-01 client

It does that repeatedly, all the way to phasex-15, and then starts, again.  In any event, i've added myself to the audio group, so i don't know why i would be denied permission.  Nonetheless, i called phasex using sudo, only to receive the last error:

Using client name phasex
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Using client name phasex-01
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket

Again, the behaviour is the same, all the way to phasex-15 client.  More importantly, jack is running.  i've run it both in real time and not in real time, getting the same errors.

As for now, i'm searching for documentation, having found [this article]("http://www.linuxjournal.com/node/1000425").  If anybody has a lead for me or a solution, please let me know.

Thank you, kindly.
il lupo

---

### Post by Pablo_F on 2011-05-02
Hi, 

jackd and phasex have to be started by the same user without sudo. The bus error is probably caused by pulseaudio. Take a look at:

ls -lah /dev/shm

If you see a lot of pulse-shm* files, you have to remove them:

rm -f /dev/shm/pulse*


I recommend putting this line in the pre-start script of qjackctl although there could be better workarounds. 

For the record, this is a bug:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/470073](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/470073)


Cheers, Pablo

---

### Post by il lupo on 2011-05-02
Hi, Pablo--

Thank you for the reply.  Yup.  A small handful of those files.  Your solution is simple enough, but i lack experience.  Here is where i run into trouble:

I recommend putting this line in the pre-start script of qjackctl

i hope i'm not asking too many questions, but here goes.  Just what file is used for the pre-start script?  i suspect a .conf file and have found some possible candidates.  i just don't know which one.  Also, will i be able to enter "rm -f /dev/shm/pulse*" as you typed it, or will it have to be executed as a shell script?  And one last question.  One of the owners of one of the pulse-shm files is gdm.  Who, or what, is gdm?  i've never heard of it, before today, and /var/lib/gdm has no files in it, just an empty directory called Seat1.

Thank you, again, for the time, Pablo.
il lupo (bill)

---

### Post by Pablo_F on 2011-05-03
Hi il lupo, 

In Jack Control, Setup, Options tab, in the first field, "execute script at server startup", just write down *rm -f /dev/shm/pulse**

gdm is the gnome display manager. I know this command can't clean the pulse-shm file that belongs to gdm, but don't worry about it. 

By the way, how much RAM do you have? Are you using your computer mainly for making music? (It could be that your best choice is getting rid of pulseaudio or at least disabling it when you are running jack)

Cheers, Pablo

---

### Post by il lupo on 2011-05-03
Pablo,

Thank you for the excellent and beautiful solution!  Phasex was up and running on the first try.

To answer your question, i'm using an hp pavilion ze4400 with 431.9MiB of RAM.  i do use it for mostly music, but not all my compositions.  i still compose at a piano and do all my scores by hand when writing for traditional acoustic instruments.  If you're curious, [have a listen]("http://www.myspace.com/billwolf1967")!

i've thought about disabling pulseaudio when running jack.  i don't understand the architecture, though, and would like to do some reading before trying anything.  Let's see, i have jack, alsa, and pulseaudio on one system.  How do they work together--or don't work together, as the case may be?  i understand, though, that my machine is old.  i could easily upgrade my memory, but would still be working without, say, high-speed usb ports.  The best solution would be a new computer.  Unfortunately, i'm still downstream from both these fixes.

Thank you, again, Pablo!

Best,
il lupo (bill)

---

### Post by Pablo_F on 2011-05-03
Hi Bill, 

Nice music, thank you!

Well, if I were you I would definitely disable pulseaudio while running jack.

First, avoid pulseaudio autospawn by default. In a terminal:
[B]
echo "autospawn=no" > ~/.pulse/client.conf[/B]

Then I suggest you prepare some scripts. You can name them "jackd-prestart", "jackd-poststart", "jackd-prestop" and "jackd-poststop". These are text files. Use gedit or a similar text editor and put them in a folder named "qjackctl-scripts" in your home directory.

Contents of the files:

*/home/bill/qjackctl-scripts/jackd-prestart*

```
#!/bin/bash
#Avoid autospawn and kill pulseaudio
sed -i 's/yes/no/g' ~/.pulse/client.conf 
pulseaudio -k 
sleep 1
#Clean /dev/shm
rm -f /dev/shm/pulse*
```


*/home/bill/qjackctl-scripts/jackd-poststart*

```
#!/bin/bash
a2jmidid -e &
#Clean /dev/shm again, just in case
rm -f /dev/shm/pulse*
#Uncomment the next two lines to run phasex automatically. 
#sleep 1
#phasex &
```

Thanks to "a2jmidid -e" you will be able to connect software and hardware alsa midi clients to jack MIDI clients.  

*/home/bill/qjackctl-scripts/jackd-prestop*

```
#!/bin/bash
#Kill all jack clients. 
killall phasex qsynth rosegarden hydrogen vmpk a2jmidid
```

You can change or extend this list to the jack clients you normally use. If you didn't launch, say, rosegarden, it will be just ignored, so you can make the list as big as you wish. You should make sure that the process names of the clients are correct. You can check with top or htop.

*/home/bill/qjackctl-scripts/jackd-poststop*

```
#!/bin/bash
# kill jackd
killall jackd
sleep 1
# Start pulseaudio
sed -i 's/no/yes/g' ~/.pulse/client.conf
pulseaudio --start
#kill qjackctl
sleep 1
killall qjackctl
```


Once the files are saved, you have to enable the execution bit on them. Just rigth click on the files, properties, permissions, and enable execution.

Now, in qjackctl, options tab, write the absolute paths to these files, in this order:

*/home/bill/qjackctl-scripts/jackd-prestart*
*/home/bill/qjackctl-scripts/jackd-poststart*
*/home/bill/qjackctl-scripts/jackd-prestop*
*/home/bill/qjackctl-scripts/jackd-poststop*

This way, you only have to press start in Jack Control and pulseaudio will be out of the way. When you press Stop, pulseaudio will be up and running again. Plus some nice automatic features that you yourself can extend if you wish to save mouse clicks.


> Let's see, i have jack, alsa, and pulseaudio on one system. How do they work together--or don't work together, as the case may be?

In this context, pulseaudio and jack are sound servers (they talk with the alsa driver and with the applications which are their clients, i.e., pulseaudio-aware or jack-aware). I strongly recommend this article by Lennart, the author of pulseaudio:

[http://0pointer.de/blog/projects/when-pa-and-when-not.html](http://0pointer.de/blog/projects/when-pa-and-when-not.html)

And the jack documentation and faq:

[http://jackaudio.org/](http://jackaudio.org/)

Cheers! Pablo

---

### Post by il lupo on 2011-05-03
Pablo,

Thank you so much for listening and enjoying!  Thank you, also, for the great article and informative, helpful response.  i had to make a few changes that i will detail for anybody who might find this of use.

First, my client.conf file for pulseaudio is in /etc/pulse.  So, i ran this:

sudo su
echo "autospawn=no" > /etc/pulse/client.conf
exit

This necessitated some changes in your code.  Here is jackd-prestart:

#!/bin/bash
#Avoid autospawn and kill pulseaudio
sudo sed -i 's/yes/no/g' /etc/pulse/client.conf
sleep 1
exit
pulseaudio -k
sleep 1
#Clean /dev/shm
sudo rm -f /dev/shm/pulse*
sleep 1
exit

The message bay kept telling me that jack wasn't running the scripts because it didn't have permission.  i don't know if i needed to add the exit commands after adding sudo, but i felt it couldn't hurt.  Also, i didn't want jack thinking it was root all the time.

Here is jackd-poststart:

#!/bin/bash
a2jmidid -e &
#Clean /dev/shm again, just in case
sudo rm -f /dev/shm/pulse*
sleep 1
exit
#Uncomment the next two lines to run phasex automatically
#sleep 1
#phasex &

i'd never heard of a2jmidid and installed it after learning what it does.  That's going to come in handy, Pablo!

jackd-prestop needed no modifications.  Also, both it and jackd-poststart can be curtailed given the programs needed for a specific project.

Finally, here is jackd-poststop:

#!/bin/bash
#Kill jackd
killall jackd
sleep 1
#Start pulseaudio
sudo sed -i 's/no/yes/g' /etc/pulse/client.conf
sleep 1
exit
pulseaudio --start

i took away your command to kill qjackctl, as sometimes i will stop the engine to change some settings and then restart it.  Once i start jackd, again, pulseaudio is disabled--or, at least, i assume that, as the client.conf file reads, "autospawn=no."

Thank you, again, Pablo:  not only for the time, but also for teaching me a great deal.

Best,
bill

---

### Post by Pablo_F on 2011-05-04
Hi Bill, 

Oops, it is a bad idea putting sudo commands in a user script. It will not work. 

There is a system-wide */etc/pulse/client.conf* but you should write to  *~/.pulse/client.conf* (just in case you don't know, "~" means "/home/your_user_name", I assumed "/home/bill" in my previous post). 


This is a valid configuration file and it overrides (for your user) the system-wide configuration in */etc/pulse/client.conf*.

As you noted, *~/.pulse/client.conf* does not exist by default but you are creating it with the "echo" command. You can also create it with gedit and write down the line, of course. 

Cheers, Pablo

---

