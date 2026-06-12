---
title: "How to correctly terminate remote ssh connection?"
date: 2009-04-19
forum: Server Platforms
---

### Post by botfish on 2009-04-19
How do I correctly terminate a remote ssh connection?

I am getting the following errors and I think it is because I have too many remote shells. I terminate the ssh connection with either 
logout, or
exit.

When attempting to create a conection I get:
$ ssh domain.name
Connection closed by xxx.xx.xxx.xx

Also, if I do manage to connect I often get errors relating to memory e.g.
-bash: /usr/bin/lesspipe: Cannot allocate memory
-bash: fork: Cannot allocate memory

---

### Post by gombadi on 2009-04-19
logout, exit or CTRL-d will all log you out of your ssh session.

> 
Also, if I do manage to connect I often get errors relating to memory e.g.
-bash: /usr/bin/lesspipe: Cannot allocate memory
-bash: fork: Cannot allocate memory 


Looks like your OpenVZ/Virtuozzo based VPS is running out of memory.

As root at a command prompt type 

```

cat /proc/user_beancounters

```

See how many allocations have failed - right hand column.

You will have to cut back on the amount of programs you are running.

The OpenVZ site has some hints on how to reduce your memory usage.

---

### Post by botfish on 2009-04-19
Below is the result of  cat /proc/user_beancounters
I've no idea how to interpret it!

<code>
$ sudo cat /proc/user_beancounters
Version: 2.5
       uid  resource                     held              maxheld              barrier                limit              failcnt
   210672:  kmemsize                  7915061              7998209             11418624             12687360                  987
            lockedpages                     0                    0                 1024                 1024                    0
            privvmpages                 43902                44354               131072               145636                    0
            shmpages                      669                  669                32768                32768                    0
            dummy                           0                    0  9223372036854775807  9223372036854775807                    0
            numproc                        41                   41                   80                   80                    0
            physpages                    9691                 9752                    0  9223372036854775807                    0
            vmguarpages                     0                    0                65536           2147483647                    0
            oomguarpages                 9700                 9761  9223372036854775807           2147483647                    0
            numtcpsock                      6                    6                  160                  160                    0
            numflock                        7                    7                   64                   72                    0
            numpty                          1                    1                    8                    8                    0
            numsiginfo                      0                    1                  128                  128                    0
            tcpsndbuf                  107152               107152              1572864              2621440                    0
            tcprcvbuf                   98304                98304              1572864              2621440                    0
            othersockbuf               146160               147456               446464              1146880                    0
            dgramrcvbuf                     0                 8464              1310720              1310720                    0
            numothersock                   96                   98                  160                  160                    0
            dcachesize                 757773               773736              1588400              1764889                    0
            numfile                      1197                 1256                 2888                 2888                    0
            dummy                           0                    0                    0                    0                    0
            dummy                           0                    0                    0                    0                    0
            dummy                           0                    0                    0                    0                    0
            numiptent                      18                   18                  128                  128                    0
</code>

---

### Post by gombadi on 2009-04-19
> 
uid resource held maxheld barrier limit failcnt
210672: kmemsize 7915061 7998209 11418624 12687360 987


Looks like there were 987 attempts to allocate memory that failed.

The OpenVZ site has quite a lot of information and will help to explain what each value means - [http://www.openvz.org](http://www.openvz.org)

Also it is better to wrap text output in quote tags as it keeps the columns and makes it easier to read.

---

