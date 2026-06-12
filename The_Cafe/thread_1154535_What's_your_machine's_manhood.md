---
title: "What's your machine's manhood?"
date: 2009-05-09
forum: The Cafe
---

### Post by monsterstack on 2009-05-09
Linux users seem to love stats. A good conky thread will prove that. Lots of users here also show off some tasty stats in their signatures. All well and good. But how about we test our machines to see who has the manliest machine of all?

```
echo `uptime|grep days|sed 's/.*up \([0-9]*\) day.*/\1\/10+/'; cat /proc/cpuinfo|grep '^cpu MHz'|awk '{print $4"/30 +";}';free|grep '^Mem'|awk '{print $3"/1024/3+"}'; df -P -k -x nfs -x smbfs | grep -v '(1k|1024)-blocks' | awk '{if ($1 ~ "/dev/(scsi|sd)"){ s+= $2} s+= $2;} END {print s/1024/50"/15+70";}'`|bc|sed 's/\(.$\)/.\1cm/'
```

I'm operating at 108.0 cm. How about you?

---

### Post by Sealbhach on 2009-05-09
119.1cm

.

---

### Post by MikeTheC on 2009-05-09
My computer's manhood can out-fly and out-shoot your computer's manhood any day of the week! :p


And here it is...

[img]http://www.thewellers.com/twiki/twiki4.jpg[/img]

---

### Post by monsterstack on 2009-05-09
:rolleyes:

---

### Post by sports fan Matt on 2009-05-09
203.5cm

---

### Post by monsterstack on 2009-05-09
We have a new leader.

I wonder if anyone has an old server that's been running for years lying around. That might turn out to be manlier still!

---

### Post by OutOfReach on 2009-05-09
darn 150.0cm

---

### Post by Kingsley on 2009-05-09
Wow. This gives a whole other meaning to the term 'e-penis.'

---

### Post by monsterstack on 2009-05-09
> **Kingsley said:**
> Wow. This gives a whole other meaning to the term 'e-penis.'

Doesn't it just!

---

### Post by klange on 2009-05-09
86.4cm
Congratulations, you've emasculated my server.

---

### Post by tubezninja on 2009-05-09
wow... 819.5cm

:D

In case you were wondering: Intel Core2Quad Q9400 processor, 4GB of RAM, 1.75TB of hard drive space.  Only about 20 days of uptime however.

---

### Post by InfinityCircuit on 2009-05-09
Damn, I was hoping I could get 1st with my 238.1 cm but it was not to be!

---

### Post by -grubby on 2009-05-09
Wow, my VPS gets 52.5 CM. I'm not even sure if it's male at this point.

---

### Post by monsterstack on 2009-05-09
> **scaredpoet said:**
> wow... 819.5cm

:D

In case you were wondering: Intel Core2Quad Q9400 processor, 4GB of RAM, 1.75TB of hard drive space.  Only about 20 days of uptime however.

Incredible stuff! Looks like we have a clear leader!

---

### Post by FuturePilot on 2009-05-09
I got 229.8cm

---

### Post by MaxIBoy on 2009-05-09
Server: [http://pastebin.com/f72d379c2](http://pastebin.com/f72d379c2)


Laptop: [http://pastebin.com/f2e0c8a28](http://pastebin.com/f2e0c8a28)


Desktop: [currently broken, pending new motherboard]

---

### Post by fedex1993 on 2009-05-09
I got 53.5cm on my VPS.

---

### Post by Calmatory on 2009-05-09
96.9 cm with 6 days of uptime and hardware @ sig. :)

---

### Post by kostkon on 2009-05-09
Ah cr*p! Only
```
38.0cm
```

I had an uptime of 28 days until a kernel update killed it some days ago...

---

### Post by monsterstack on 2009-05-09
Interesting results everybody. Dreams have been shattered, hopes have been lost, male self-confidence torn to shreds. Who will emerge victorious?

---

### Post by MikeTheC on 2009-05-09
207.2cm here, not that I have the foggiest what the result actually *really* means.

---

### Post by Keithhed on 2009-05-09
290.9cm,  is there a masculinity scale attached? like:

under 100 = do you have a heartbeat?
100 - 200 = average joe
200 - 300 = Vin Diesel
300 - 400 = Ubermensch
400 +     = Chuck Norris

---

### Post by steev182 on 2009-05-09
426.3cm

---

### Post by Sealbhach on 2009-05-09
> **MikeTheC said:**
> 207.2cm here, not that I have the foggiest what the result actually *really* means.

I think it measures 

uptime
processor power
ram
disk size

and creates a result in cm based on these readings.

.

---

### Post by crl0901 on 2009-05-09
270.2 here.

---

### Post by Eviltechie on 2009-05-09
196.0cm

It would be interesting to see what the stats are for the LUG and my hosting server are.

---

### Post by Einsamkeit on 2009-05-09
66.9cm :(
But you know what they say:  It's not the size of the ship but the *motion* of the *ocean* that [I]counts. ;)
[/I]

---

### Post by Sealbhach on 2009-05-09
> **einsamkeit said:**
> 66.9cm :(
but you know what they say:  It's not the size of the ship but the *motion* of the *ocean* that [i]counts. ;)
[/i]

lol :)

.

---

### Post by MikeTheC on 2009-05-09
Where are the Ubuntu female geeks when you need them? ;)

---

### Post by monsterstack on 2009-05-09
> **Sealbhach said:**
> I think it measures 

uptime
processor power
ram
disk size

and creates a result in cm based on these readings.

.

That's my understanding of it too. Please note I didn't make this myself: I found it posted someplace a while back. It could do with a bit of explanation. Here's my best effort:

```
echo `uptime|grep days|sed 's/.*up \([0-9]*\) day.*/\1\/10+/'`
```

First it takes the number of days your system has been up and divides it by ten. Then it adds it to this:

```
cat /proc/cpuinfo|grep '^cpu MHz'|awk '{print $4"/30 +";}'
```

Which takes the Mhz of your processors and divides them by thirty, and then adds them to:

```
free|grep '^Mem'|awk '{print $3"/1024/3+"}'
```

Which takes the free megabytes of your system, divides them by three, and adds it to:

```
df -P -k -x nfs -x smbfs | grep -v '(1k|1024)-blocks' | awk '{if ($1 ~ "/dev/(scsi|sd)"){ s+= $2} s+= $2;} END {print s/1024/50"/15+70";}'``
```

which takes the filesystems on your computer, finds the unused blocks, adds them together, divides them by fifty, divides them by fifteen and adds seventy. Finally, it performs a bit of arithmetic with

```
stuff|bc|sed 's/\(.$\)/.\1cm/'
```

which works it all out for you and gives you a handy centimetre output.

At least it's something along those lines, anyhow.

---

### Post by MaxIBoy on 2009-05-09
Looking at the script, I think this is how it works:

[LIST]
[*]Take the number of days in the uptime (hours and minutes don't count.) Divide it by ten, add it to the total.
[*]Take the MHz of the CPU, divide it by 30, add it to the total. Repeat this for every CPU/core. (NOTE! This script does not take into account CPU scaling, so on laptops with on-demand scaling, the answer will reflect how much load your CPU is under at the time.)
[*]Take the amount of free memory in Kb, divide it by 1024, then divide it again by 3. Add this number to the total.
[*]Get info on all the filesystems mounted (excluding network ones.) Add up the number of blocks in each filesystem (add double the amount if it's a SCSI or SATA drive.) Divide this number by 1024, then by 50, then by 15, and add 70. Add this number to the total. I'm pretty sure it goes for total blocks, not free blocks.
[*]Divide the total by 10, and that's your answer.
[/LIST]

Wow, I have homework to do.

---

### Post by Einsamkeit on 2009-05-09
> **MikeTheC said:**
> Where are the Ubuntu female geeks when you need them? ;)

Then we would have to deal with enormous e-clitorises. :-\"

---

### Post by monsterstack on 2009-05-09
> **MaxIBoy said:**
> Looking at the script, I think this is how it works:

[LIST]
[*]Take the number of days in the uptime (hours and minutes don't count.) Divide it by ten, add it to the total.
[*]Take the MHz of the CPU, divide it by 30, add it to the total. Repeat this for every CPU/core. (NOTE! This script does not take into account CPU scaling, so on laptops with on-demand scaling, the answer will reflect how much load your CPU is under at the time.)
[*]Take the amount of free memory in Kb, divide it by 1024, then divide it again by 3. Add this number to the total.
[*]Get info on all the filesystems mounted (excluding network ones.) Add up the number of blocks in each filesystem (add double the amount if it's a SCSI or SATA drive.) Divide this number by 1024, then by 50, then by 15, and add 70. Add this number to the total. I'm pretty sure it goes for total blocks, not free blocks.
[*]Divide the total by 10, and that's your answer.
[/LIST]

Wow, I have homework to do.

Thanks. That's a little bit easier to digest than my lousy explanation.

---

### Post by MaxIBoy on 2009-05-09
Since the CPU is clocked higher under greater load, I decided to run Super-Pi while the test was taking place. Result: 138 cm, which is 5.3 cm longer. 

However, the clock speed of the CPU isn't an accurate measure of performance. In fact, CPU makers should really get with the program and figure out ways to clock their CPUs lower, instead of driving up a meaningless statistic. (Joking-- this isn't a serious benchmark anyway.)

---

### Post by Keithhed on 2009-05-09
Maxi, i got a similar result 292.5cm under load.  playing a video and running deluge in the background.  so less than 2cm "length" increase.  or would it be height?

---

### Post by HappyFeet on 2009-05-09
261.9

---

### Post by pat23_2007 on 2009-05-09
276.8cm

---

### Post by Sef on 2009-05-09
Locked for too many violations of the [Ubuntu Code of Conduct #6]("http://ubuntuforums.org/index.php?page=policy") besides this thread's title is questionable.

> Adult Content/Violence/Illegal Activity: Messages containing sexually oriented/violent/illegal dialogue, images, content, or links to these things will be deleted. Messages with links to or suggesting illegal activity will also be deleted. Posting or linking to any of these could result in a ban.

---

