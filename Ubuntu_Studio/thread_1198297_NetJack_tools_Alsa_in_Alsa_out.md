---
title: "NetJack tools Alsa_in Alsa_out"
date: 2009-06-27
forum: Ubuntu Studio
---

### Post by JDPP on 2009-06-27
Hi, 

Is there a way to easily add those tools to the jack version bundled in ubuntu studio 9.04 dosn't have them. 

I read [http://ubuntuforums.org/showthread.php?t=1128748](http://ubuntuforums.org/showthread.php?t=1128748) witch was form 8.04 version, and I dont know how to compile from source...

thx

---

### Post by bobince on 2009-06-27
It's simple to compile Jack from source: just download the source tarball from jackaudio.org, unpack it into a working directory, then the standard &#8216;configure, make&#8217; commands. You can then copy the alsa_in/out commands from the build directory to a bin directory, or just run them where they are.

Unfortunately, the quality of the results hasn't been brilliant for me so far: I often get a bunch of crackling in the signal. I'm not using the RT kernel, but I'm not convinced that's the problem either.

---

### Post by JDPP on 2009-06-27
something like :  ```
cd /home/Desktop/
wget http://jackaudio.org/downloads/jack-audio-connection-kit-0.116.2.tar.gz
tar xzfv jack-audio-connection-kit-0.116.2.tar.gz
cd jack-audio-connection-kit-0.116.2
./configure
make

```  without installing and then I just find the alsa_in and alsa_out files and put them into /bin/ directory ?

---

### Post by bobince on 2009-06-30
Yes. I personally put them in /home/me/.local/bin, but any bin should do.

---

### Post by thorgal on 2009-07-01
I would put them into /usr/local/bin and make sure /usr/local/bin is part of the $PATH environment variable. Or you can make it even more local:

/home/<yourself>/bin and put that path in $PATH as well.

/usr/local/bin is for user home compiled / installed stuff that can be used by other users as well (unix is multiuser).

/usr/bin is for apps that were preinstalled or came from distro packages

/bin is for system stuff
/sbin is for system special admin stuff
/usr/sbin is for special admin app stuff

I would think twice before putting an app in any bin. Avoid /sbin and /usr/sbin. This is usually reserved to root / admin activities.

---

### Post by JDPP on 2009-07-01
ok thanks for the replies.
I'd like to be sure about one thing (I'm still quite noob...) :
Does it means that :
- I can compile the 0.116, with a make (and not a make install), 
- then copy and paste alsa_in and alsa_out in the /usr/local/bin
so that I can use alsa_in and alsa_out with the jack wich is in the last ubuntu studio distrib (1.9 ?) ?

or if I may say it in a diferent way ( noob, and not as fluent in english as I wish...) :
By compiling 0.116 with netjack I can add the alsa_{in, out} functions to the 1.9 version of jack ?

---

### Post by thorgal on 2009-07-01
jack 0.116.x is JACK1
jack 1.9.x is JACK2

they have different netjack stuff. alsa_in/out are part of JACK1 and cannot be used with JACk2.

I believe I have an early post in this thread of discussion about netjack2 (that comes with JACk2).

Otherwise, you can always derive some inspiration from my netjack2 howto there:

[http://linuxmusicians.com/viewtopic.php?f=19&t=1010](http://linuxmusicians.com/viewtopic.php?f=19&t=1010)

---

### Post by JDPP on 2009-07-01
yes you have :
[http://ubuntuforums.org/showthread.php?t=1128748](http://ubuntuforums.org/showthread.php?t=1128748) (was mentionned in my first post of this thread ;) )
I bookmarked it a few weeks ago, but still have some hard time to understand all ;)

I'll read also your /linuxmusicians.com post.

My goal is : be able to use both headphone output on the netbook and an external audio device.

Thanks for your answer !

---

### Post by JDPP on 2009-07-14
I did manage to compile and install 0.116.2 Jack version
I did 

```
$alsa_out -d hw:0
```

and it looked like working but :

```
$ alsa_out -d hw:0
delay = -648
res: 1.000000,     diff = 0.000000,     offset = 0.000000 
delay = -728
res: 1.000000,     diff = 0.000000,     offset = 0.000000 
delay = -704
res: 1.000000,     diff = 0.000000,     offset = 0.000000 
delay = -736
res: 1.000000,     diff = 0.000000,     offset = 0.000000 
delay = -736
res: 1.000000,     diff = 0.000000,     offset = 0.000000 
delay = -728
res: 1.000000,     diff = 0.000000,     offset = 0.000000 
delay = -728
res: 1.000000,     diff = 0.000000,     offset = 0.000000 
delay = -728
res: 1.000000,     diff = 0.000000,     offset = 0.000000 
delay = -688
res: 1.000000,     diff = 0.000000,     offset = 0.000000 
delay = -736
res: 1.000000,     diff = 0.000000,     offset = 0.000000 
delay = -728
res: 1.000000,     diff = 0.000000,     offset = 0.000000 
delay = -728
res: 1.000000,     diff = 0.000000,     offset = 0.000000 
delay = -729
res: 1.000000,     diff = 0.000000,     offset = 0.000000 
delay = -728
res: 1.000000,     diff = 0.000000,     offset = 0.000000 
delay = -640
res: 1.000000,     diff = 0.000000,     offset = 0.000000 
delay = -640
res: 1.000000,     diff = 0.000000,     offset = 0.000000 
delay = -640
res: 1.000000,     diff = 0.000000,     offset = 0.000000 
delay = -648
res: 1.000000,     diff = 0.000000,     offset = 0.000000 
delay = -648
res: 1.000000,     diff = 0.000000,     offset = 0.000000 
delay = -592
res: 1.000000,     diff = 0.000000,     offset = 0.000000 
alsa_out: time_smoother.c:69: time_smoother_put: Assertion `oldest_index != -1' failed.
Aborted
```any idea ?

I'm on Ubuntu Jaunty updated to ubuntu studio

---

### Post by thorgal on 2009-07-15
you will need to tune it at startup. It comes with a few options. I don't think the default is good enough, not to my knowledge.


I am not too familiar with alsa_in/out since I use jack2 and the netadapter jack in-process client. Not sure how to advise you here. You could probably join the jack or ardour IRC channel and talk to Torben H., the author of netjack1. He's very often dwelling on these IRC channels.

---

### Post by JDPP on 2009-07-15
thx for your anwser.

I'll try to find them on irc.
meanwhile, I have compiled jack2, and have also some issues, I'll post them in a new thread.

---

