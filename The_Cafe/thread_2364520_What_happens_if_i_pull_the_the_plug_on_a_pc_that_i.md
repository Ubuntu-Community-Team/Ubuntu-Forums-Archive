---
title: "What happens if i pull the the plug on a pc that is in suspension?"
date: 2017-06-24
forum: The Cafe
---

### Post by alex1222003 on 2017-06-24
One day i put my pc in suspension. at nigth, i had to shut down the router, but i forgot that both the router and the pc were attached to the same multi-plug([https://www.google.it/imgres?imgurl=https%3A%2F%2Fwww.silamp.it%2Fuserfiles%2Fmultipresa-6-posti.jpg&imgrefurl=https%3A%2F%2Fwww.silamp.it%2Fciabatte-prese-prese-multiple-c-24.html&docid=2PslMzL0MPH-zM&tbnid=in3oQUf0ic6tBM%3A&vet=10ahUKEwj1lZXz_NXUAhUJuhQKHbuCBlMQMwg3KAEwAQ..i&w=900&h=900&client=firefox-b&bih=971&biw=1920&q=ciabatte%20elettriche&ved=0ahUKEwj1lZXz_NXUAhUJuhQKHbuCBlMQMwg3KAEwAQ&iact=mrc&uact=8](https://www.google.it/imgres?imgurl=https%3A%2F%2Fwww.silamp.it%2Fuserfiles%2Fmultipresa-6-posti.jpg&imgrefurl=https%3A%2F%2Fwww.silamp.it%2Fciabatte-prese-prese-multiple-c-24.html&docid=2PslMzL0MPH-zM&tbnid=in3oQUf0ic6tBM%3A&vet=10ahUKEwj1lZXz_NXUAhUJuhQKHbuCBlMQMwg3KAEwAQ..i&w=900&h=900&client=firefox-b&bih=971&biw=1920&q=ciabatte%20elettriche&ved=0ahUKEwj1lZXz_NXUAhUJuhQKHbuCBlMQMwg3KAEwAQ&iact=mrc&uact=8)) so i shut down both. i realize it was still in suspension after i turned it off. fortunately, the pc worked great like everytime the following day, but is there a way it can damage the pc by doing this?

---

### Post by ian-weisser on 2017-06-24
Damage the PC hardware? Not if it's occasional.

Damage the OS Software? Not if it's suspended.

Lose all your unsaved work? Definitely and certainly.

---

### Post by paulconnolly on 2017-07-21
I run ubuntu 16 on mine and must admit, I pull the plug while it's alseep quite a lot.

It boots up same as normal

---

### Post by #&amp;thj^% on 2017-07-24
> **ian-weisser said:**
> Damage the PC hardware? Not if it's occasional.

Damage the OS Software? Not if it's suspended.

_Lose all your unsaved work? Definitely and certainly._

+1
The likelihood of "frying" anything from "randomly" pulling the plug is very low. The most likely thing that might happen is some corrupted data if you happened to be writing data to HDD/SSD/USB when the power cut off. 
In addition, since voltage fluctuation can sometimes occur during normal operation, without total power loss, a high quality PSU or some kind of power conditioning UPS will help preserve the longevity of your equipment.
Just my 2 cents worth. :)

---

### Post by gsng on 2017-08-02
I think should be alright since it's in suspension.

---

### Post by 1clue on 2017-08-02
You'll lose unsaved work as people mentioned above, but with regards to damage the only case would be if you're writing to the disk at the time power was lost.  This was mentioned above too.

What wasn't mentioned is that the degree of data loss varies depending on what type of filesystems you're using/writing to when the power is cut.

Some filesystems (xfs comes to mind) are 'high performance' and strongly recommend dual power supplies with battery backup. These filesystems tend to write to a large cache which may or may not write back immediately. Part of the advantage of these filesystems is that they don't force the OS to wait on writes, they just look for cache hits on reads and write to the cache on the writes. Depending on what task is streaming data, it can take quite awhile to sync the cache to the disk. On top of that these filesystems have a pretty complex journal and if that journal gets corrupted you're going to lose data, and chances are it's something you'd rather not lose.

---

### Post by RobGoss on 2017-08-02
I think it's safe to say it's never good to pull the plug on any electrical device especially a computer, I can assure you if your system is updating and someone pulls the plug that system it will not be able to boot in to that operating system. I don't know how that would effect a system that's is in suspension

---

