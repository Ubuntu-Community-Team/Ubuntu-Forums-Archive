---
title: "Ubuntu server becomes slow after a couple of days"
date: 2024-08-24
forum: Server Platforms
---

### Post by tecnomiky on 2024-08-24
Hi, I'm writing here to ask for clarification on a situation that is bothering me a bit. I thank those who will help me.
I have a desktop that I use as a home server with an Asrock motherboard, i5 3rd gen and 24 GB of RAM. I had previously installed Centos 7 on it. Given the end of support, I wanted to switch to Ubuntu Server 22.04. To be precise, the version is 22.04.4 with kernel 5.15.0-119.
I noticed that after it is left on for a few days the system slows down and to restore it I have to reboot. This situation has never happened to me with Centos that I have had for at least 5 years.
What could it be?

---

### Post by currentshaft on 2024-08-24
Start by describing what exactly "slows down" and how, because literally nobody but you understands what that means.

---

### Post by LHammonds on 2024-08-25
I have not seen such behavior before on an Ubuntu Server.  However, I also do not run a desktop GUI on my servers either.  Maybe there is something going on where its going into a powersaver mode...something related to the motherboard features and desktop GUI.

At a terminal prompt, run "htop" to see what the memory and CPU is doing when you first boot up the server.  When it becomes "slower" take another look at "htop" and see if anything changed.  Generally, you shouldn't see much activity in swap unless you are running out of RAM and "swapping" to the hard drive to make temporary room in RAM...which could cause performance issues too.

Also check the temperature of your CPU / GPU.  You might have dust bunnies or poor ventilation that causes it to get hotter the longer it runs.

Check for hardware failures such as the hard drive and RAM.

If your hard drive is thrashing, run "iotop" to see what is chewing up disk bandwidth.

If your Internet speed is what's slow, check network bandwidth.  Sites like speedtest.net can show you your maximum download / upload speed from your PC...but keep in mind it does not account for other devices on your network consuming bandwidth.

Beyond this, its just a WAG on anyone's part as there isn't enough data /  evidence about what fast / slow and the measure between them.

LHammonds

---

### Post by tecnomiky on 2024-08-25
The problem reoccurred after a day. Yesterday I restarted the server. I insert here the links to the pastebins of dmesg [https://pastebin.com/mRtVc6hd](https://pastebin.com/mRtVc6hd) and journalctl [https://pastebin.com/g4iLfLd0](https://pastebin.com/g4iLfLd0) .   
     A very obvious symptom is that the speed of the gigabit network card drops to a few kilobits.

On this server you have the non-snap version of docker and kvm installed

---

### Post by Doug S on 2024-08-25
You do have one occurrence of the processor getting to hot:

```

Aug 24 20:36:21 rohan kernel: intel_powerclamp: Start idle injection to reduce power
...
Aug 24 20:36:56 rohan kernel: intel_powerclamp: Stop forced idle injection

```

There is a lot of information in the logs you provided, but I'm not going to spend the time trying to isolate the potentially relevant parts.

If it were my system, I would always have turbostat (linux tools common package, I think) running watching power and clock frequencies. Something like:

```

sudo turbostat --quiet --Summary --show Busy%,Bzy_MHz,IRQ,PkgWatt,PkgTmp,RAMWatt,GFXWatt,CorWatt --interval 15

```
You might not have RAMWatt or GFXWatt available. If so, just delete them from the show list.

---

### Post by currentshaft on 2024-08-25
genius

---

### Post by stephan4 on 2024-08-27
Yep, can't stress this enough. I've seen whole reddit channels which lost every quality due to these kind of questions.

---

### Post by tecnomiky on 2024-08-28
Last day the situation recurred and after numerous investigations and tests I discovered that the problem concerns the network interfaces. After having performed a down and up of the interface with ```
sudo ip link set enp5s1 down ; sudo ip link set enp5s1 up
``` and restarted the services that use the network it seems that the problem has been solved. 

Can you hypothesize what this anomaly could depend on?

---

