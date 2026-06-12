---
title: "Memory usage on Ubuntu Desktop 12.04 64 bits"
date: 2012-11-10
forum: Server Platforms
---

### Post by icaka92 on 2012-11-10
Hello,

I am running my ubuntu desktop 12.04 to host 1 site on it. The machine is good, but i have a little problem. 
PC Specs:
CPU: MD FX-6200 /3.8G/X6/BOX AM3+
RAM: 8GB DDR III 1333Mhz

When i check my ram usage i got this:
```
             total       used       free     shared    buffers     cached
Mem:          7970       6907       1062          0         38       6039
-/+ buffers/cache:        830       7139
Swap:         8173          0       8173
```

and something the server use all 8 GB ram and the site stop work. Any ideas from where come the problem and i can't understand what is really memory usage Mem or +/-buffers/cache, because the difference is big.

Thanks !

---

### Post by jerome1232 on 2012-11-10
you have nearly 7 GB's free, install htop, it'll show you more clearly.

you subtract buffers and cache to find how much ram is free.

---

### Post by icaka92 on 2012-11-11
Okay thanks, but then why the site stop work when the first line use all memory ? I restart apache and mysql server and the pc still use 6.5 GB ram ? Is there a way to increase it or from where can come the problem. Thanks !

---

### Post by jerome1232 on 2012-11-11
I doubt it's your ram, since you have a ton of free ram.

Check your logs to see if there are any clues in there (when they stop working)
(I'm just guessing at which logs might be useful, I am neither an apache or a mysql server expert and am just trying help you get some useful info in your thread)
```
tail /var/log/apache2/error.log
```

I'm not sure what mysql's log would be called but it should be somewhere under /var/log

---

### Post by thnewguy on 2012-11-11
When you run the "free" command the second line shows you how much RAM is used and how much is free. You have 7GB of free memory, so your RAM isn't full. The problem with your web server is probably unrelated to memory. 

Maybe you're getting a lot of connection attempts? Is it possible the server is still running and is just backed up and slow to respond?

---

### Post by icaka92 on 2012-11-11
I don't think that the problem comes from apache or mysql I restart both and when i type:
free -m, the first line show used: 6500 free 1500. What is this and the second line show about 1 use and 7 free.

Thnaks !

---

### Post by Wim Sturkenboom on 2012-11-11
Maybe this helps you understand how it works: [Help! Linux ate my RAM](http://www.linuxatemyram.com/)

And please, use code tags when posting code and results so formatting is maintained.

---

### Post by icaka92 on 2012-11-12
Thanks, I read it, but i don't understand why the site stop work when the firs line use all my memory, but actually it use 1 gb ram of 8 gb.

---

### Post by Wim Sturkenboom on 2012-11-12
Neither do we ;) First of all it's totally not clear what you mean by 'stop work'. No access? Slow? Corrupted data? What type of site? Some static html pages? Dynamic content with a database behind it? Which database (mysql or something else)? Which webserver (apache or something else)? Have you coded your site yourself from scratch (not really applicable if it's a static site)? 

What does _top_ say? Any process that use extreme processing power? You can sort the processes by CPU usage by pressing capital P and by memory usage by pressing capital M.

---

### Post by CharlesA on 2012-11-12
> **Wim Sturkenboom said:**
> Neither do we ;) First of all it's totally not clear what you mean by 'stop work'. No access? Slow? Corrupted data? What type of site? Some static html pages? Dynamic content with a database behind it? Which database (mysql or something else)? Which webserver (apache or something else)? Have you coded your site yourself from scratch (not really applicable if it's a static site)? 

What does _top_ say? Any process that use extreme processing power? You can sort the processes by CPU usage by pressing capital P and by memory usage by pressing capital M.

What he said ^.

Also check the apache error log, like jerome mentioned. That will help you narrow down what it going on.

---

### Post by icaka92 on 2012-11-13
Stop work mean that when i try to load the site with browser, I can't. It takes too long to respond.

Type of site: Dynamic content with a database behind it.
Database: Mysql
Webserver: Apache

When i run command:
```
top
```
i receive this:
top - 15:52:05 up 11:21,  1 user,  load average: 9.16, 6.43, 5.89
```
Tasks: 195 total,   8 running, 187 sleeping,   0 stopped,   0 zombie
Cpu(s): 89.8%us,  9.2%sy,  0.0%ni,  0.3%id,  0.0%wa,  0.0%hi,  0.7%si,  0.0%st
Mem:   8161688k total,  7344168k used,   817520k free,   117612k buffers
Swap:  8370172k total,        0k used,  8370172k free,  6308200k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
  515 mysql     20   0 2464m 105m 7444 S  174  1.3  16:16.88 mysqld
13888 www-data  20   0  161m  31m 5472 R   99  0.4 377:15.31 ffmpeg
12936 www-data  20   0  153m  23m 5040 R   98  0.3 399:06.39 ffmpeg
 1910 www-data  20   0  152m  21m 5228 R   60  0.3   0:04.11 ffmpeg
 1828 www-data  20   0  166m  38m 5772 R   47  0.5   1:13.89 ffmpeg
 1909 www-data  20   0  133m 6592 4496 R   39  0.1   0:03.21 ffmpeg
 1836 www-data  20   0  158m  26m 5264 R   37  0.3   1:04.56 ffmpeg
 1603 www-data  20   0  134m 8372 4904 S   32  0.1   0:39.91 ffmpeg
 1898 www-data  20   0  134m 8004 4896 S   11  0.1   0:02.67 ffmpeg
  741 www-data  20   0  471m  13m 4388 S    0  0.2   0:00.06 apache2
  794 root      20   0     0    0    0 S    0  0.0   0:00.13 kworker/1:1
 1892 www-data  20   0  469m  14m 4308 S    0  0.2   0:00.03 apache2
 1923 www-data  20   0  471m  13m 4232 S    0  0.2   0:00.01 apache2
 1924 www-data  20   0  470m  13m 3852 S    0  0.2   0:00.01 apache2
    1 root      20   0 24440 2424 1356 S    0  0.0   0:01.22 init
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      20   0     0    0    0 S    0  0.0   0:00.44 ksoftirqd/0

```

No erros in mysql error log.
In apache log there are only information about ffmpeg converstion.

---

### Post by CharlesA on 2012-11-13
> ```
  PID USER      PR  NI  VIRT  RES  SHR S [COLOR="Red"]%CPU[/COLOR] %MEM    TIME+  COMMAND
  515 [COLOR="Blue"]mysql     [/COLOR]20   0 2464m 105m 7444 S  [COLOR="Blue"]174  [/COLOR]1.3  16:16.88 [COLOR="Blue"]mysqld[/COLOR]
13888 [COLOR="Red"]www-data[/COLOR]  20   0  161m  31m 5472 R   [COLOR="Red"]99  [/COLOR]0.4 377:15.31 [COLOR="Red"]ffmpeg[/COLOR]
12936 [COLOR="Red"]www-data[/COLOR]  20   0  153m  23m 5040 R   [COLOR="Red"]98  [/COLOR]0.3 399:06.39 [COLOR="Red"]ffmpeg[/COLOR]
 1910 [COLOR="Red"]www-data[/COLOR]  20   0  152m  21m 5228 R   [COLOR="Red"]60  [/COLOR]0.3   0:04.11 [COLOR="Red"]ffmpeg[/COLOR]
 1828 [COLOR="Red"]www-data[/COLOR]  20   0  166m  38m 5772 R   [COLOR="Red"]47  [/COLOR]0.5   1:13.89 [COLOR="Red"]ffmpeg[/COLOR]
 1909 [COLOR="Red"]www-data[/COLOR]  20   0  133m 6592 4496 R   [COLOR="Red"]39  [/COLOR]0.1   0:03.21 [COLOR="Red"]ffmpeg[/COLOR]
 1836 [COLOR="Red"]www-data[/COLOR]  20   0  158m  26m 5264 R   [COLOR="Red"]37  [/COLOR]0.3   1:04.56 [COLOR="Red"]ffmpeg[/COLOR]
 1603 [COLOR="Red"]www-data[/COLOR]  20   0  134m 8372 4904 S   [COLOR="Red"]32  [/COLOR]0.1   0:39.91 [COLOR="Red"]ffmpeg[/COLOR]
 1898 [COLOR="Red"]www-data[/COLOR]  20   0  134m 8004 4896 S   [COLOR="Red"]11  [/COLOR]0.1   0:02.67 [COLOR="Red"]ffmpeg[/COLOR]
```

Is apache supposed to be running ffmpeg?

---

### Post by jerome1232 on 2012-11-13
also a load average of 9 how many cores do you have, sounds like your CPU is pegged and that's why your site is unresponsive.

---

### Post by CharlesA on 2012-11-13
> **jerome1232 said:**
> also a load average of 9 how many cores do you have, sounds like your CPU is pegged and that's why your site is unresponsive.
From their OP, it looks like it's a hex core CPU.

I have a feeling the load is that high because ffmpeg is running 8 times, all as www-data, which shouldn't be launching ffmpeg, as far as I know...

---

### Post by icaka92 on 2012-11-13
CPU : AMD FX-6200 /3.8G/X6/BOX AM3+
Many users use ffmpeg to convert at same time. This can be the problem or no ? And if this is the problem how to correct it ?

Thanks !

---

### Post by CrucifiedEgo on 2012-11-13
> **icaka92 said:**
> CPU : AMD FX-6200 /3.8G/X6/BOX AM3+
Many users use ffmpeg to convert at same time. This can be the problem or no ? And if this is the problem how to correct it ?

Thanks !

Yes, this would be the problem.  I assume your site is calling ffmpeg to convert video.  Video conversion is very, very CPU and RAM intensive and what's most likely happening is that there are too many conversions happening at once.  If there are more than 6, then your CPU can't really keep up and will stop responding while it tries to chug through all the video data.  You'll either need to reprogram the site to queue video conversions and limit them to 4 or 5 at a time, or add more CPU cores to your server (though there are very diminishing returns on that as the highest you'd be able to go with that platform is 8 cores with an FX-8xxx CPU.

EDIT: perhaps this will be helpful in reorganizing your application: [http://ffmpeg.org/trac/ffmpeg/wiki/Using%20FFmpeg%20from%20PHP%20scripts](http://ffmpeg.org/trac/ffmpeg/wiki/Using%20FFmpeg%20from%20PHP%20scripts)

---

### Post by sandyd on 2012-11-13
Small explanation in order.

Immagine each CPU is a checkout line at the supermarket.

Each = represents full processor utilization, and is equal to 1.0 load in linux.


So, if you have two lines, it looks like this


------------------
==================
------------------
==================
------------------

And if you have more lanes, and so on.

Now, If you have four processors, and a load of 8, it will look something like this


------------------
==
------------------
==
------------------
==
------------------
==
------------------

The second = (after the first) shows that there is exactly 4.0 loads waiting to process ( one on each processor due to SMP).

That means that there are tasks queued to run on the processor, but cannot due to the fact that the processors are still processing the first =. Those tasks will be queued until some of the tasks in the first '=' finish running.

As a result, you are experiencing very slow response times- your query is queued somewhere in the line

---

### Post by icaka92 on 2012-11-14
Hello,

Thanks you for help ! I try [URL="http://ffmpeg.org/trac/ffmpeg/wiki/Using%20FFmpeg%20from%20PHP%20scripts"]```
http://ffmpeg.org/trac/ffmpeg/wiki/Using%20FFmpeg%20from%20PHP%20scripts
```[/URL] , but it is the same. I don't know how to correct it to work okay :(

---

### Post by icaka92 on 2012-11-18
Any ideas ?

---

### Post by CrucifiedEgo on 2012-11-20
> **icaka92 said:**
> Any ideas ?

Yes, fix your code and buy more hardware, your site is taxing the server and it can't handle the load.

---

### Post by icaka92 on 2012-11-24
Hello. I try to fix it with using [FONT=monospace][/FONT]shell_exec , but without success.

---

### Post by CrucifiedEgo on 2012-11-26
> **icaka92 said:**
> Hello. I try to fix it with using [FONT=monospace][/FONT]shell_exec , but without success.

simply using shell_exec isn't enough.  You need to create a queueing system likely with multiple rendering machines.  It's not just a quick fix nor is it something that could be handled within the scope of a post like this.

---

### Post by icaka92 on 2012-11-28
Hello,

Thanks all for the answers. I understand that there is no problem with mu code, but this process (convert) need much cpu power.

Thanks agan !

---

### Post by CharlesA on 2012-11-28
> **CrucifiedEgo said:**
> simply using shell_exec isn't enough.  You need to create a queueing system likely with multiple rendering machines.  It's not just a quick fix nor is it something that could be handled within the scope of a post like this.

What he said. ^

> **icaka92 said:**
> Hello,

Thanks all for the answers. I understand that there is no problem with mu code, but this process (convert) need much cpu power.

Thanks agan !

The problem is you are trying to do multiple conversions at the same time and that is overworking the CPU. The best thing to do would be to modify your code to allow jobs to be queued instead of running at the same time.

---

