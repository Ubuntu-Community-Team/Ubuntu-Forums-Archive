---
title: "How to install Jack on Ubuntu?"
date: 2010-12-23
forum: Ubuntu Studio
---

### Post by orange2k on 2010-12-23
I want to use Jack as default output for EnergyXT2, but I dont seem to be able to find the right package in Synaptic...

---

### Post by Pablo_F on 2010-12-23
Through synaptic or apt-get, the jack server package is called "jackd" and the gui front-end is "qjackctl". The package called "jack" has nothing to do with the jack server.

Or just use the software center and install "Jack Control" and you are done.

EDIT: When you are asked, normally, you want rtprio and memlock privileges so you can run jackd in realtime mode. Also, do in the terminal a: "sudo adduser your_user_name audio" and reboot.

Cheers, Pablo

---

### Post by orange2k on 2010-12-23
Thanks, but I did a little search and I found a good thread where my answer is...

[http://ubuntuforums.org/showthread.php?t=806730](http://ubuntuforums.org/showthread.php?t=806730)

---

### Post by cchhrriiss121212 on 2010-12-23
That thread is 2 years old and has outdated information. Just follow what Pablo said.

---

### Post by Pablo_F on 2010-12-23
Hi, 

Yes, the method I told the OP to get rtprio and memlock privileges for the user is faster and cleaner than editing system files manually, but in the end it is the same.

However, I just realised that EnergyXT is an exception. Installing jackd from the repos is not enough. You have to compile the jack.cpp they provide. Follow instructions:

[http://www.energy-xt.com/index.php?id=1201](http://www.energy-xt.com/index.php?id=1201)

Maybe, this can help too:

[http://georgia.ubuntuforums.org/showthread.php?t=1050404](http://georgia.ubuntuforums.org/showthread.php?t=1050404)

Cheers, Pablo

---

### Post by cchhrriiss121212 on 2010-12-23
> Yes, the method I told the OP to get rtprio and memlock privileges for  the user is faster and cleaner than editing system files manually, but  in the end it is the same.
The thread shows information on editing the old limits.conf file, so I'm guessing it won't be the same if he tries it.

---

### Post by Pablo_F on 2010-12-23
Hi, 

Well, the result is the same, you can try and test it if you have the time. 

From: [http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_limits.html](http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_limits.html)
> 
By default limits are taken from the /etc/security/limits.conf config file. Then individual *.conf files from the /etc/security/limits.d/ directory are read.


So, "/etc/security/limits.conf" and text files in the directory "/etc/security/limits.d/" (like "audio.conf" created by the post-installation script of jackd package) is somehow comparable to "/etc/apt/sources.list" and text files in the directory "/etc/apt/sources.list.d/".

Debian packagers did it fine with that script imho. Of course, it is better if the lines are in a unique file.

If in doubt, the "ulimit" command will tell which are the actual user limits. "ulimit -r" for rtprio, "ulimit -l" for memlock, "ulimit -a" for all.

Cheers, Pablo

---

### Post by cchhrriiss121212 on 2010-12-23
Why does every manual on jack now mention the new audio.conf file if it is not necessary? 
Examples like this really makes linux audio more complicated than it needs to be.

---

### Post by Pablo_F on 2010-12-23
> Examples like this really makes linux audio more complicated than it needs to be. 

I don't agree. It is easier than before. New users don't even need to know that audio.conf exists at all. They only need to answer "yes" to a question that pops up automatically. Admittedly, they still need to know that they have to add the user to the audio group to complete the required configuration.

Regards, Pablo

---

### Post by cchhrriiss121212 on 2010-12-24
It is easier now, but not if the user decides to click "no" instead (there are examples here on the forums of users doing just that).

I know this is only a small change, but these all add up when a user is trying to troubleshoot. One page will tell him to edit file x and another will tell him to edit file y. Then he will waste time changing them both, and if lucky, he will find this thread and see that it doesn't even make a difference. You see what I mean?

---

### Post by Pablo_F on 2010-12-24
Yes I see what you mean. But we can't change the ever-evolving nature of Linux and FOSS. And life I dare say. There are examples like this one all over the place. You gave a good advice: "That thread is 2 years old". In this case, it was not that it does not work, it is that it can be done more easily nowadays. My point is that this is fine. If a thing can be done in a better way, why not?

> It is easier now, but not if the user decides to click "no" instead (there are examples here on the forums of users doing just that).

They can do the old trick of manually editing /etc/security/limits.conf.

Or, cleaner (I am not saying this is intuitive, just as a reminder):

sudo dpkg-reconfigure -p high jackd

or 

sudo dpkg-reconfigure -p high jackd2

or

sudo dpkg-reconfigure -p high jackd1

depending on ubuntu version and jackd version installed. Just try what works for you. It doesn't harm if nothing happens.

Cheers! Pablo

---

