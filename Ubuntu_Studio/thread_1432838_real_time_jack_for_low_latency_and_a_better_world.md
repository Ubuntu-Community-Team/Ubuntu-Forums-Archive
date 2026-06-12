---
title: "real time jack for low latency and a better world"
date: 2010-03-18
forum: Ubuntu Studio
---

### Post by icon-x on 2010-03-18
hello reader, 
here is my story: i have made a recording yesterday with a million of Xruns which sounded like cxzbztpkzzttzz... today, i woke up and started reading. 
i have learned about real time kernels, fifo scheduling, alsaproject and so on. i have read about 60-70 pages and after 4 hours i found myself reading about kernel modding. as you can understand today was my first day of understanding what a real time kernel is so you can easily guess that it has been a few months since i have first heard about the word: kernel.!

so as a simple newbie linux user i think i did my best to arrange this realtime kernel thingy. as:

-i have linux-rt 2.6.3.1, linux-headers-2.6.28.3-rt, linux-rt-headers-2.6.28.3 installed on synaptic. also shown in grub and can be succesfully loaded.

-my /etc/security/limits.conf file has the proper lines which are: 
@audio          -       rtprio          99
@audio - nice -10
@audio - memlock 512000

-jack doesnt start when i select 'realtime' parameter in settings giving the well known error of : 
 p, li { white-space: pre-wrap; }  

cannot use real-time scheduling (FIFO at priority 10) [for thread -1953663248, from thread -1953663248] (1: Operation not permitted)
 cannot create engine
 [COLOR=#999999]15:16:52.817 JACK was stopped successfully.[/COLOR]

and stops successfully...

i really am bored of holding my breath and diving in the unknown deepness of ubuntu (jaunty by the way) for today. and i feel close enough to the low latency-Xrunwise stable solution so please guide me forward from now on.
-what else should i say?
-what else should i do?

thank you

---

### Post by AutoStatic on 2010-03-18
Add yourself to the 'audio' group: [https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support](https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support)

---

### Post by sgx on 2010-03-19
Its great to see people dig in and read, and implement
their learning. You will conquer where others fear to tread!
You might be an Amiga user, to have chosen that nik? :o
cheers

---

