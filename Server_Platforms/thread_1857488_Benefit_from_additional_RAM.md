---
title: "Benefit from additional RAM?"
date: 2011-10-10
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2011-10-10
As a fugitive from Windows, was wondering as to the benefits or otherwise of increasing the RAM from 1 to 2 Gb on an Ubuntu Server 11.04 running a 2.6 MHz processor with IDE drive.

Server's primary function being webpages, no use of any database backend.

TIA

---

### Post by snowpine on 2011-10-10
Use the terminal command 'top' to evaluate your RAM use. If you are approaching 100% usage, then you will benefit from additional RAM. 

You may also find this essay informative/entertaining: [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by raja.genupula on 2011-10-10
If you improve you ram then your server performance will be improve.All operations will be done with better time.

---

### Post by collisionystm on 2011-10-10
> **ChrisRChamberlain said:**
> As a fugitive from Windows, was wondering as to the benefits or otherwise of increasing the RAM from 1 to 2 Gb on an Ubuntu Server 11.04 running a 2.6 MHz processor with IDE drive.

Server's primary function being webpages, no use of any database backend.

TIA

Install HTOP on your server.

sudo apt-get install htop

run htop

htop

watch your memory usage. Do you ever get near 700mb?

I think around there is when the system will start writing to swap and slowing itself down.

If you are no where near that, then NO, adding more RAM will not help your performance.

---

### Post by a2j on 2011-10-10
2Gb or 6Gb ... my server uses it all. disk cache or other... but with 6Gb it almost does not use any swap space.

---

### Post by arrrghhh on 2011-10-10
> **a2j said:**
> 2Gb or 6Gb ... my server uses it all. disk cache or other... but with 6Gb it almost does not use any swap space.

This is of course based on usage.

My server never goes over 512mb under normal usage.  When I run a VM, obviously RAM usage spikes - so I have 3gb in the rig.

However, if I didn't host VM's, 1 gb would be plenty.

OP - heed the other posts here.  Use HTOP, look at your usage - try to recreate some situations where the server would be saturated, worst-case scenarios.  If your RAM usage doesn't get near 1gb, then you don't need any additional RAM.

Are you asking because of performance issues, or are you just trying to stay ahead of any issues?  If it's the latter, then good for you - use htop to see usage ;).

---

### Post by Lucky. on 2011-10-10
> **snowpine said:**
> 
You may also find this essay informative/entertaining: [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

The photo on that site made my day.

---

### Post by Vegan on 2011-10-10
I always believe the more RAM the better.

That page made me laugh too. Thanks,

---

### Post by ChrisRChamberlain on 2011-10-11
Thanks for all your replies.

Without being able to accurately simulate a number of users online at the same time, the server never goes over 350 mb. 

> Originally Posted by arrrghhh
Are you asking because of performance issues, or are you just trying to stay ahead of any issues? If it's the latter, then good for you - use htop to see usageThe latter

---

### Post by arrrghhh on 2011-10-11
> **ChrisRChamberlain said:**
> Thanks for all your replies.

Without being able to accurately simulate a number of users online at the same time, the server never goes over 350 mb. 

The latter

Good!

As was stated previously, you can never have too much RAM... but it sounds like you don't need it.  If you're not swapping (ever, even when usage does spike) then you won't gain any immediate benefits from the additional RAM.  You'll just be scaled for more capacity in the future.

---

