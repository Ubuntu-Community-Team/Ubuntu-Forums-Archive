---
title: "SSD + HDD Desktop Setup"
date: 2010-01-22
forum: The Cafe
---

### Post by arranmc182 on 2010-01-22
Was thinking about a future set up in my desktop PC that would have a 32 or 64GB SSD and then a normal 500GB or 1TB HDD would like the main system on SDD to speed up the OS.

I set up my own partitions like this.

40GB to /
2GB or more to Swap
the rest to /home

Could I put / on the SDD then put /home on the HDD & would Swap be best on SSD or HDD as I hear with SSD that there not so good with random read and rights to the drive or have things got better.

---

### Post by xir_ on 2010-01-22
> **arranmc182 said:**
> Was thinking about a future set up in my desktop PC that would have a 32 or 64GB SSD and then a normal 500GB or 1TB HDD would like the main system on SDD to speed up the OS.

I set up my own partitions like this.

40GB to /
2GB or more to Swap
the rest to /home

Could I put / on the SDD then put /home on the HDD & would Swap be best on SSD or HDD as I hear with SSD that there not so good with random read and rights to the drive or have things got better.

with the sort of cost of that system, why even use a swap. why not shell out for 8gb of ram?

---

### Post by castrojo on 2010-01-22
I have this setup at home. I create a little directory in /var owned by my user account so I can symlink .gconf and my browser profiles from /home to the SSD, since those get accessed a bunch and I want that to be fast. 

It's a great combo btw.

---

### Post by squilookle on 2010-01-22
A friend of mine was talking about doing that yesterday. 

Might become a popular setup.

---

### Post by cascade9 on 2010-01-22
If it was me, I would setup like this- 

SSD-
/- 15-20GB
/home- the rest of the SSD.

HDD-
Swap (if 2GB or less, RAM x2, if 4GB or more, RAM + 0.5GB. That is what I use anyway....)
/whatever mount point you like for your stoarge/archive area. 

> **arranmc182 said:**
> 40GB to /
2GB or more to Swap
the rest to /home

Could I put / on the SDD then put /home on the HDD & would Swap be best on SSD or HDD as I hear with SSD that there not so good with random read and rights to the drive or have things got better.

40GB for /root?!?!?!!!? Do you ever manage to even get close to filling that? I normally run 15GB, and that is more than enough. IMO anyway.

Swap is better on a HDD still.

---

### Post by earthpigg on 2010-01-22
i have a 60gb ssd and also a 1tb 'conventional' hard drive.

no swap (6gb ram)
12gb /
48gb /home
1tb havent-been-forced-to-install-it yet... unopened, in the shrink wrap.

the 1tb came after the computer was otherwise assembled. i keep movies and a backup of all my music on my server. streaming speeds over the lan are fast enough to watch movies on. haven't had a reason to install the 1tb hd yet - my 'temporary' solution of keeping movies on the old desktop is working smooth as silk... and i enjoy fiddling with software more than hardware anyways :P hence my preference for a software solution instead of hardware.

worth mentioning because, hell, maybe you don't need the 1tb at all? how big is the hd on your old/current computer? maybe convert it into a server, as i have done? even though it is a 'server', it is concurrently used as a desktop by a household member. plane-jane ubuntu install (actually, masonux...) on it and not ubuntu server edition.

the multimedia is kept on the server computer in a phantom user's /home. the user (username "multimedia") has no password and cant login, but everyone has full read access, so all can play/watch what is kept there. 

i use sshfs and an alias to mount it into my /home on my computer. if anyone is curious, i made a thread a while ago detailing this that i can dig up. it's especially nice with my netbook - the 8gb hard drive in the netbook 'magically' has 200gb or so of music and movies on it.

---

### Post by arranmc182 on 2010-01-22
> **xir_ said:**
> with the sort of cost of that system, why even use a swap. why not shell out for 8gb of ram?

Wow that is a good point 8GB of RAM would be good for me as I always use a 64bit OS on my desktop but with a 32bit OS I could see 4GB of RAM doing the job fine.

> **cascade9 said:**
> 40GB for /root?!?!?!!!? Do you ever manage to even get close to filling that? I normally run 15GB, and that is more than enough. IMO anyway.

LOL I like to install a lot of programs that are not in the repo's so I like to have more space than I will need I would hate to run out of space.

> **whiprush said:**
> I have this setup at home. I create a little directory in /var owned by my user account so I can symlink .gconf and my browser profiles from /home to the SSD, since those get accessed a bunch and I want that to be fast. 

It's a great combo btw.

So I take it is easy to set up and dose it Speed things up at all?? I'm guessing it would but by how much??

---

