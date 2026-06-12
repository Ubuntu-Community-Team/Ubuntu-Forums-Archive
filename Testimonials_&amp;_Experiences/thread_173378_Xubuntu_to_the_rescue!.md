---
title: "Xubuntu to the rescue!"
date: 2006-05-10
forum: Testimonials &amp; Experiences
---

### Post by Sushi on 2006-05-10
I have an old laptop with 333MHz P2 and 256MB of RAM. It works well with Linux, but I found Ubuntu (with GNOME) to be a bit sluggish with that machine. So I decided to give Xubuntu (with XFCE) a try.

I installed it, and everything went without any problems. And it was considerably faster than Ubuntu was. Of course, there was still occasional slowness due to the slow hard-drive (4-5MB/sec transfer-rate). But I was happy, I had turned an old computer in to a working and usable computer.

But then I noticed something... The computer did not have 256MB of RAM as I remembered, it had 128! The 256MB SODIMM was installed on another old laptop by mistake! So even with 128MB of RAM Xubuntu worked just fine! After putting that 256MB stick in to the laptop, it worked even better!

Needless to say that I was seriously impressed at how well Xubuntu/XFCE worked even with just 128MB of RAM! Good job people!

---

### Post by ubuntu_demon on 2006-05-10
I use xubuntu on my p3 (gateway/fileserver/2nd machine). It rocks!

Here's how to get a bit more speed  :

installing an optimized kernel (686 in your case) :
$sudo apt-get install linux-686

and prelinking :
[http://www.ubuntuforums.org/showthread.php?t=74197](http://www.ubuntuforums.org/showthread.php?t=74197)

---

### Post by Sushi on 2006-05-10
[QUOTE=ubuntu_demon]I use xubuntu on my p3 (gateway/fileserver/2nd machine). It rocks!

Here's how to get a bit more speed  :

installing an optimized kernel (686 in your case) :
$sudo apt-get install linux-686

and prelinking :
[http://www.ubuntuforums.org/showthread.php?t=74197](http://www.ubuntuforums.org/showthread.php?t=74197)[/QUOTE]

Of it's already plenty fast :). The things that are somehwhat sluggish are due to the dismal hard-drive. And even that was considerably helped by doubling the RAM ;)

---

### Post by ubuntu_demon on 2006-05-10
[QUOTE=Sushi]Of it's already plenty fast :). The things that are somehwhat sluggish are due to the dismal hard-drive. And even that was considerably helped by doubling the RAM ;)[/QUOTE]
these speed ups I suggested will help even more :)

If you think your systems swaps too much you can reduce the tendency to swap a bit with the following :
$ sudo sysctl -w vm.swappiness=0

To check that is really 0 :

$ sysctl vm.swappiness
vm.swappiness = 0

if you like it you can add :
```

vm.swappiness=0

```
to /etc/sysctl.conf

---

### Post by Sushi on 2006-05-10
[QUOTE=ubuntu_demon]these speed ups I suggested will help even more :)[/QUOTE]

Well, I do know of prelinking, so I'll have to give it a thought. Haven't had any issues with swapping. The occasional sluggishness is due to the fact that when I launch an app, it needs to be read from the HD. And since the HD is so slow....

Well, just about the only app I have experienced the sluggishness so far is Synaptic.

---

### Post by ubuntu_demon on 2006-05-10
sometimes when you start an app you hear the HD also because there's swapping going on. To see how much is swapped out :

$free -m

(swappiness doesn't help much and you might have to experiment with the values to get any improvement at all)

---

### Post by Sushi on 2006-05-10
[QUOTE=ubuntu_demon]sometimes when you start an app you hear the HD also because there's swapping going on. To see how much is swapped out :

$free -m

(swappiness doesn't help much and you might have to experiment with the values to get any improvement at all)[/QUOTE]

I have used Linux since 1998, I do know how to check the status of the RAM ;).

---

### Post by ubuntu_demon on 2006-05-10
[QUOTE=Sushi]I have used Linux since 1998, I do know how to check the status of the RAM ;).[/QUOTE]
okay I didnt know that :)

---

### Post by IYY on 2006-05-11
I'd say that even XFCE is slow on my 333 MHz machine. IceWM and Fluxbox make it work faster than most modern computers, though. ;)

---

