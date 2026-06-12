---
title: "New To Ubuntu - Need Advice on New Server Computer"
date: 2017-05-23
forum: Server Platforms
---

### Post by duffann on 2017-05-23
Hello,

First of all I am a new ubuntu user , trying the ubuntu 16.04 lts on my old computer. It has been 2 weeks and I coud set up my apache server php mysql etc.. so I decided that I can use my own server. After long messing around , I decided to make a new server with the following to use with my new 16.04 LTS :

Ryzen 7 1700 
Asus Prime b350-plus
corsair venegance 2x8 gb lpx ddr4 3000mhz
samsung pro ssd 250gb

I was just about the hit order now button from amazon when I realized some people are having problems with ryzen and ubuntu. Made some research and saw that some people with gigabyte boards are having the problem but also some people with b350 also having problems. Also some people having only seen 1 core by ubuntu . Some people says latest kernels are ok now with ryzen some not. And At last my head is a mess ! 

Should I continue and buy the new system or not ? 
I really need advice on this.

Regards
[COLOR=#0066C0][FONT=&quot]**Corsair Vengeance LPX 16GB (2x8GB) DDR4 DRAM 3000MHz C15 **[/FONT][/COLOR]

---

### Post by TheFu on 2017-05-23
New chipsets and sometimes new CPUs don't really have good support.

It is best to wait year for others to find all the issues and get them resolved, especially if you are new to Linux or just don't want to deal with the hassles.

That doesn't mean this is always necessary, but there isn't any way to know, in advance.  There are some Atom CPUs with lots of cores that have been out a few years and still have issues. That's bad, because those specific CPUs would be ideal for Linux-based routers.

IMHO.

Hopefully someone else will post with their experiences.

I can suggest that your use the **ESX whitebox** supported hardware lists as a guide.  There are a few of them.  [http://www.ryanbirk.com/esxi-6-5-home-lab-whitebox-options/](http://www.ryanbirk.com/esxi-6-5-home-lab-whitebox-options/) is one.

---

### Post by duffann on 2017-05-24
Thanks for the reply,

I selected ryzen as it is a new processor and want the build to be a new one but you are right about choosing a known,stable build.
I hope some people with ryzen experience can point me to right direction.

---

### Post by mastablasta on 2017-05-24
ryzen is not fully supported. since you want to use LTS i would suggest older hardware. by that i mean intel options or "older" AMD server CPUs.

depending on server use, you might want to choose server components (ECC RAM, reliable disk etc.). what will the server be doing? what is its primary task?

propper server hardware is usually more reliable and usually not the latest one found. since you will probably want it to run 24/7/365

something to think about - ssd on server: [http://forums.crucial.com/t5/Crucial-SSDs/Installing-an-SSD-in-a-Server-NAS-or-Workstation/ta-p/174229](http://forums.crucial.com/t5/Crucial-SSDs/Installing-an-SSD-in-a-Server-NAS-or-Workstation/ta-p/174229)

---

### Post by duffann on 2017-05-24
thanks for reply,

server will serve mainly serve data to mobile applications with a php file that is connecting to mysql and transmitting data to customers.
I wanted to buy new hardware but I ee that a lot of things can happen with ryzen and I am not experienced enough to solve them if happens.

I also considered xeon e5 but the prices are too high for lower clock speeds ( 8 core 2.1 e2620 v4 is %30 expensive than ryzen 7 1700 )

What would you suggest me , as I am looking for more than 4 cores because on pak hours my current vps on a hosting company shows nearly full cpu usage on htop.

Thanks

---

### Post by mastablasta on 2017-05-24
if you are using server for some business i would say you should get propper server equipment and not some home PC.

ECC ram, Enteprise SSD or hard drives that won't go suddnely bad after 2 years. possibly some hot swapable drive rack, to avoid posisble downtimes etc. ther eis a reason why enteprise hardware is more expensive. same with business laptops. they are just made better than average ones.

but if this is more of a hobby, go with one if core i CPUs for now. i am not sure SSD is neede unless you see there will be some bottle neck with hard drive I/O. it also depends on how many clients are accessing the server concurrently.

---

### Post by duffann on 2017-05-24
I could go with i7 4790k . I have one more confusion. I currently own a vps on a quality hosting firm. They offer 4 cores in my plan but dont know the specifics ( clock speed etc ) they just saythey are xeon . 
With current load of my server , nearly all 4 cores are working at total of %80 workload which means they are not enough. If I use my own server with 4 cores like 4790k , will the load numbers be same or it will be less as 4790k probably have much more clock speed etc than my vps is running ?

---

### Post by sp40140 on 2017-05-24
You should at least go with enterprise workstations like HP Z series or DELL Precision. Use Xeon cpu and most offer ECC RAM. 
You don't want high clockspeed. But you want more cores.
If cost is concern, go with pre-owned ones, there are a lot of those on ebay.
If cost is no concern and you just want powerful server, wait a bit and get AMD's server chip which is coming out in few months. 
By then most critical of the bios issues would have been fixed. 
And It's unlikely that AMD will jump into server market without proper compatibility with linux.
I wouldn't recommend core cpus for what you are trying to do.

---

### Post by TheFu on 2017-05-24
Impossible to say.  Most hosting providers provide VPS, not HW-based systems. Depending on their sales model, there could be very-low or very-high overhead for all I/O and processing or not.  
A friend of mine works at a collocation data center. The system they provide are all low-end Xeons - slow. They don't do any virtualization. Zero.  Clients either rent or bring their own hardware - the HW must fit into their racks, so no "desktops" allowed.

80% workload is ideal, IMHO.  The system is working.  I've seen many systems (thousands) running at 13% just doing monitoring, no real work.  I'm actually a little jealous. 80% is good.

Also, is this a collocation thing? You provide the hardware and they provide power-n-ping?  It is very unlikely that any home/small biz internet connection would be able to provide sufficient bandwidth when compared to **any** real data center. Bandwidth is a real issue for performance.  
I've been running systems for a number of clients from my home (business internet connection) after giving them the option of paying the VPS or collocation bills instead. The lack of bandwidth **is** an issue, but they've decided the costs aren't worth it.  Of course, I put 20 systems on a single physical box and only have local failover.  RAID has saved the uptime about 5 times the last 8 yrs. I don't regret using RAID.  Lets a storage failure be an inconvenience for the next weekend, not an outage.  All disks fail. Some fail slowly, so we can see it coming, but others *just fail immediately* and never work again.  Data recovery on an SSD is non-existent, BTW.  Backups are the only answer there.

I agree on the server hardware suggestion from mastablasta if this isn't a hobby.  You can go cheap, but not too cheap.  Look at supermicro and some FreeNAS builds.  
Or
if you feel you must go cheaper, then expect to buy 2 of everything to have sufficient redundancy against failures.  Put each into a geographically different location (not your house) - best if they are 500 miles apart to avoid common natural disasters.

There are used Xeon systems with amazing performance. Last year, using a Xeon 2670 was all the rage because facebook was upgrading their old systems and used CPUs were/are cheap, cheap, cheap.
[http://www.techspot.com/review/1155-affordable-dual-xeon-pc/](http://www.techspot.com/review/1155-affordable-dual-xeon-pc/)
[http://www.tomshardware.com/answers/id-2955621/xeon-2670-system-build-400.html](http://www.tomshardware.com/answers/id-2955621/xeon-2670-system-build-400.html)
[https://news.ycombinator.com/item?id=11455701](https://news.ycombinator.com/item?id=11455701)

For a server, more cores are usually better. This isn't for gaming.

For the disks, you'll want a quality RAID card (LSI) for each system and at least 1 spare RAID card, though running 2 enterprise SSDs in a SW-RAID1 would be a good idea too. If you have 2 systems, geographically separate, then they can backup each other.

Actually, I need to build a new server.  Looked at the Xeon 2670's last fall, but was unable to find a solid, reputable, motherboard, that would fit my full-sized case.  I need to try again. Some old systems are a little underpowered here.

Plus, by using older components, you avoid the DDR4 extra costs.  Every few years, RAM and motherboard makers collude together and force RAM slot changes for tiny, tiny, tiny, performance improvements.  I've been avoiding DDR4 and plan to skip that completely.

Anyway, that's my $0.20 after working as a systems/enterprise architect for a decade.

Good luck!

---

### Post by duffann on 2017-05-24
Thanks for your replies. I will not provide a professional service to anyone , just for my self. My current vps uses around 1.5mbit / second and around 4mbit / second at peak times so I don't think bandwith will not be a problem with a total use of around 200gb traffic / month. ( all I serve is php files to customers which they use to retrieve data from mysql server ) .  I can't afford and also I am not professional enough to run professional systems . 
What I am planning is besides my vps , I want to divide some traffic to my vps , because customers are increasing and my cpu to serve those files thruogh apache server is not enough. I have to upgrade my vps nearly every 3months that costs too much, so I am planning to serve customers in my home country from my server ( if server goes offline for some reason it is no problem because my apps that customers using will first try my homeserver if cant reach it , will use the vps so small downtimes is no problem )

According to these info I tought that a normal computer would be enough. I just want to take some load from the vps , vps will still do the important things. ( this way I am planning to stop upgrading my vps every 3 months )

Turning back to ryzen issue , I see that people having problem with ryzen are using gigabyte mobos , people using asus prime or msi could make it work. It is a cost efficient cpu for me but I am just afraid of what if it doesnt work =)

---

### Post by slickymaster on 2017-05-24
*Thread moved to **Server Platforms**.*

---

### Post by TheFu on 2017-05-24
I'd forget Ryzen for a year. Some issues take longer to appear.

If you aren't making enough to pay for VPS ... definitely calculate WHEN that will happen.  

Have you looked at using a more efficient web server than apache?

---

### Post by duffann on 2017-05-24
I can pay for the vps , but as i said , I want to take some of the load on my own to 
1) dont pay much for further vps upgrades
2) learn some basics with linux servers

I want to start from somewhere and I think this is the correct time to start , you do not reccommend core i series and also ryzen as I understood , I dont have time to wait for naples also having problems with cpu load on my vps now , so should I stop this and continue with vps ? Even my 10 year amd athlox is running without any problems now for about 2 weeks wihtout problem, I tought that ryzen would at least show the same performance but now I am not sure after your posts .

another question , if we assume that ryzen has no problems with linux support , which processor would perform better : Xeon e2620 v4 with 8 cores and 16 threads with 2.1 base freq or ryzen 7 1700 with 8 cores and 16 threads at 3.0 base freq ?

---

### Post by TheFu on 2017-05-24
Let's be clear.  Ryzen may be perfect for your needs, but since you are new to Linux and don't want hassles, I'm recommending that you stay away, for now, based on your statements.

I looked at Ryzen for my needs too.  Decided against it for the **possible** hassle-factor.  I've had to patch kernels for years due to HW issues. I don't ever want to do that again.

As for performance, the type of workload matters. Every workload is a little different and depends on networking, storage, RAM use, CPUs AND the motherboard architecture.  Concurrent requests? concurrent users? Response size?  DB performance?  

Do you have performance stats for all those things for the last 3 months?  
Even with those, it is still guesswork.

---

### Post by duffann on 2017-05-24
I understand. Thanks for all your help. I will stay away for now and try on my currenc 4790k .

---

### Post by TheFu on 2017-05-24
Gather stats, if you aren't already. That will help make informed decisions later.  It also will show issues BEFORE they become outages.

---

### Post by Michael_McKenney on 2017-05-24
If you are buying an HP, Dell or another real server, I would check their compatibility page to see which OS is supported.   HP only supports certain OS versions of Linux.

---

### Post by mastablasta on 2017-05-25
HP supports RHEL (CentOS), SUSE EL and Ubuntu. Perhaps one of the smaller Proliants would be enough?!
FreeNAS or rarther ixSystems is also an option.

in any case as other said get the stats, see what you are actually dealing with and then plan according to the needs. 
for example my home server is overkill for the usage. so i plan to introduce some extra tasks to it.

---

### Post by gordintoronto on 2017-05-25
Getting a 25/10 Internet connection would probably be more useful than a state-of-the-art server. Regular home DSL is 1 mbps upload speed, not enough for your workload.

---

### Post by duffann on 2017-05-26
I will be using cable 50/10 ,

by the way I took a risk and went on with ryzen with a plan of : If not works as expected I was going to use it for my own computer and make my 4790k the server.
I have no problems with ryzen 7 1700 , asus prime b350 plus with ubuntu16.04 and latest kernel.

All 8 cpu and 16 thread is visible and no problem for about 24 hours.

---

### Post by sp40140 on 2017-05-26
> **duffann said:**
> I will be using cable 50/10 ,

by the way I took a risk and went on with ryzen with a plan of : If not works as expected I was going to use it for my own computer and make my 4790k the server.
I have no problems with ryzen 7 1700 , asus prime b350 plus with ubuntu16.04 and latest kernel.

All 8 cpu and 16 thread is visible and no problem for about 24 hours.

Good news.
I am curious about the RAM and the RAM bandwidth. As, I have seen complaints about it. This might be not specific to linux though.

---

### Post by duffann on 2017-05-27
My mobo was saying that my ram was compatible to work at 2933 ( my ram is corasir venegance 2x8 3000 ) but I could only make it work on 2666 . These issues I hoe will be solved with bios updates.

---

### Post by mastablasta on 2017-05-29
that is very good news indeed! hopefully they will make Ryzen compatible soon with other combinations as well. 

current reviews show promise and best of all it is not as expencive as Intel.

---

### Post by TheFu on 2017-05-29
It is good news, but I'd want 3+ more months to be certain.  Sometimes there are odd interactions that aren't noticed on first use or by everyone.  There are always edge conditions and I tend to discover those. ;(

---

### Post by duffann on 2017-05-29
on the second day i had a little freeze. I first changed ram to 2133 mhz , which was default setting on mobo. I wil try this. If i experience a crash again in 2-3 days I will try another kernel as i am using 4.12.rc2 now . If I cant solve this with this 2 , I am currently running with desktop , I will try to change to no-desktop verison.

---

### Post by TheFu on 2017-05-29
Did you look at the log files?  Anything useful in dmesg?
You'll need to boot from alternate media (a different OS image/instance), then mount the HDD with /var/ on the normal boot (not the current /var), then look through all the log files there and in all directories below it for issues.

---

### Post by duffann on 2017-06-01
No I didnt but after i rollback to latest stable kernel (not a rc ) i have no problems for about 48 hours

---

### Post by TheFu on 2017-06-01
> **duffann said:**
> No I didnt but after i rollback to latest stable kernel (not a rc ) i have no problems for about 48 hours

```
$ uptime
 17:07:59 up 32 days,  9:13, 

```
and on another physical box
```
$ uptime
 17:08:38 up 54 days,  9:39, 

```
and
```
# uptime
 16:11:27 up 210 days, 23:30,

```Just sayin'.

These are fully patched weekly systems. The last 1 isn't linux.  Stability is more important than almost anything else to me. A lockup just isn't acceptable here.

But we all have different priorities, which is completely fine.

---

### Post by duffann on 2017-06-04
Hello,
after the kernel update no crashes, this is the fifth day. I will post the updates. The problem was obviously the kernel.

---

### Post by TheFu on 2017-06-04
> **duffann said:**
> Hello,
after the kernel update no crashes, this is the fifth day. I will post the updates. The problem was obviously the kernel.

So far.  Please take notes of the issues and set a reminder to update this in August after you start using the system more and trusting it and add in a few modules.

Sorry to be pessimistic.  I've just learned over the years that things like this seldom really are solved, completely.


**August Update: **
Ryzen CPUs are causing core dumps when overloaded - that's my simplistic description (probably wrong).
* [https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-Test-Stress-Run](https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-Test-Stress-Run)
* [https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-Segv-Response](https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-Segv-Response) 
has more.

Be careful folks.

---

