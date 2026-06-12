---
title: "Something Very Strange happened yesterday"
date: 2010-09-02
forum: Security
---

### Post by cybrsaylr on 2010-09-02
To my PC running Karmic. Not sure if this is the right forum report this strange happening. I've been using Ubuntu for 4 yrs and this is the first time this ever happened and was wondering what may have caused it. 

I boot up Ubuntu and out of habit daily check my free space in my Linux partition. Usually this is what I see when checking in terminal, I put G-Parted results on top:

[IMG]http://i.imgur.com/6Hy7A.jpg[/IMG]

This is what I usually see on my ~400GB Linux partition at about 10:30 AM yesterday and again today at the same time.

Well yesterday my PC was acting a little 'funny'.
Vagalume which usually plays LastFM failed and quit on me around 2AM. Plus this very fast PC acted a bit sluggish, which is very unusual.

Out of curiosity I checked my partition condition by opening terminal and putting in > df to see what my  free space was.

The results shocked me.
Terminal reported my 'use' was now 73% at 2AM, up from 3% at 10:30 in the morning!

Opened up G-Parted for a double check and G-Parted confirmed what terminal reported. 
G-Parted showed the 399.73 GB Linix partition usage was about 229 GB with only ~102 GB free! 
At this point I rebooted a couple times to see if this would clear things up but both terminal and G-Parted gave the same results saying my Linux partition was now 73% full. I then tried checking to see where these 'extra files' or whatever were but couldn't find them after a search. They seemed to be in my 'Home' folder but going through my Home folder I could not find them! 

All this happening between 10:30 AM to 2AM yesterday!
I wasn't doing any downloading except for about 5 mp3 songs for a total of about 12 megs. The only other apps I played around with and have used in the past were Skype and now Google Voice. They both work very well on this PC. Besides doing that, only normal PC use and normal web surfing took place yesterday. So I have no idea why my PC usage went from 3% to 73% in a matter of ~16 hours yesterday on the Ubuntu partition! I then shutdown the PC for the night.

Now the kicker is, today when this PC was booted up, I checked again in terminal and G-Parted and got the results posted above in the screenshot! All looks like PC usage is back to normal! 

So the question is what caused this massive spike in usage that almost filled up the Ubuntu partition? This has never happened in the 4 yrs I've been using Ubuntu.

---

### Post by anomie on 2010-09-02
[QUOTE=cybrsaylr]So the question is what caused this massive spike in usage that almost filled up the Ubuntu partition? This has never happened in the 4 yrs I've been using Ubuntu.[/QUOTE]

We don't know. ;) Probably some process got crazy with writing a temporary file or log. 

Next time it happens, capture output from: 
```
$ sudo find / -xdev -size +50M -exec du -h {} \;
```

You can redirect the output to a text file and hang onto it. Then browse through the output and look for any unusually large matches.

---

### Post by BkkBonanza on 2010-09-03
You weren't running a disk wiping tool like **sfill** or **shred** to wipe free space, right?

---

### Post by linux18 on 2010-09-03
sudo find /var/log -size +50M -print
sudo find /tmp -size +50M -print

this is similar to post #2 but a much faster at finding the easy errors crazy logs and tmp files

---

### Post by cybrsaylr on 2010-09-03
> **anomie said:**
> We don't know. ;) Probably some process got crazy with writing a temporary file or log. 

Kind of thought that is what happened. Like I said this is the first time anything like this happened but as we know strange things can happen with any OS at times. I did check temp files then but found nothing out of the ordinary. 
All has been normal since.

---

### Post by cybrsaylr on 2010-09-03
> **BkkBonaza said:**
> You weren't running a disk wiping tool like **sfill** or **shred** to wipe free space, right?

Nope, wasn't doing anything like that.

---

### Post by cybrsaylr on 2010-09-03
> **linux18 said:**
> sudo find /var/log -size +50M -print
sudo find /tmp -size +50M -print

this is similar to post #2 but a much faster at finding the easy errors crazy logs and tmp files

Will keep that in mind, along with what anomie posted in post # 2, and will try not to forget about it because this is most likely a rare fluke problem that hopefully will not occur again.

---

### Post by cybrsaylr on 2010-09-04
FWIW....
Discovered Vagalume has an intermittent bug that was responsible for my PC acting 'funny'. I listen to Vagalume a lot and at times it cuts out and fails. Usually you just have to restart Vagalume and all is well till the next time it cuts out. Well there were a couple times when I could not shut down Vagalume after it failed. Vagalume became totally unresponsive and even 'force quit' would not work. 

I then thought to check:
System > Administration > System Monitor > Resources
and discovered a core was pegged at 100% on the CPU History chart!
I then clicked on Processes which showed Vagalume was the offending process @ 100%. I then clicked on Vagalume to 'kill that process' and Vagalume was shut down and all went back to normal.

Just thought of passing this info along.

---

