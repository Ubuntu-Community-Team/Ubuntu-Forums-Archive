---
title: "Possible virus? Process 'bioset'"
date: 2014-06-03
forum: Security
---

### Post by dshauld on 2014-06-03
I can't really find much info online and there are multiple instances running.
```
. ~ $ ps -A | grep bioset
   67 ?        00:00:00 bioset
  355 ?        00:00:00 bioset
  359 ?        00:00:00 bioset
  383 ?        00:00:00 bioset
  386 ?        00:00:00 bioset
 2488 ?        00:00:00 bioset
 2491 ?        00:00:00 bioset
 2506 ?        00:00:00 bioset
 2509 ?        00:00:00 bioset
 2554 ?        00:00:00 bioset
 2557 ?        00:00:00 bioset
 2620 ?        00:00:00 bioset
 2623 ?        00:00:00 bioset
 2636 ?        00:00:00 bioset
 2641 ?        00:00:00 bioset
 2685 ?        00:00:00 bioset
 2688 ?        00:00:00 bioset
 2711 ?        00:00:00 bioset
 2714 ?        00:00:00 bioset
 2760 ?        00:00:00 bioset
 2763 ?        00:00:00 bioset
 2783 ?        00:00:00 bioset
 2786 ?        00:00:00 bioset
 2836 ?        00:00:00 bioset
 2840 ?        00:00:00 bioset
 2859 ?        00:00:00 bioset
 2862 ?        00:00:00 bioset
 2915 ?        00:00:00 bioset
 2918 ?        00:00:00 bioset
 2938 ?        00:00:00 bioset
 2941 ?        00:00:00 bioset

```

More info here:

[http://linux.die.net/man/3/bio_set_nbio](http://linux.die.net/man/3/bio_set_nbio)

[http://lunaticoutpost.com/Topic-Bioset](http://lunaticoutpost.com/Topic-Bioset)

Would this post be better suited in Security?

Edit: Even in the event it isn't anything, how can I go about finding more information about where it runs from and what it does?

Edit 2: Observation. The first link has a date of 7/2013. Result of searches in the forum for 'bioset' start 10/2013

---

### Post by Frogs Hair on 2014-06-04
*Moved to **Security Discussions ***

---

### Post by gifford on 2014-06-04
Are you running a raid configuration?

---

### Post by dshauld on 2014-06-04
> **gifford said:**
> Are you running a raid configuration?

Thank you for the reply.

No. I have three drives. One 30G ssd for the OS and two 1TBs for media. The two larger drives are not automatically mounted and not in a RAID configuration. 

This is from the second link:

> 
Have a bunch of new processes.  Bioset is one of them.
[http://linux.die.net/man/3/bio_set_nbio](http://linux.die.net/man/3/bio_set_nbio)

This is a wrapper round the platform's TCP/IP socket connection routines.

Using connect BIOs, TCP/IP connections can be made and data transferred  using only BIO routines. In this way any platform specific operations  are hidden by the BIO abstraction.


TCP/IP connections hidden by abstraction sounds scary.

Being at 67, this process is loaded pretty early in the chain. How can I find out about where it is run from and what it does?

---

### Post by unspawn on 2014-06-05
> **dshauld said:**
> How can I find out about where it is run from and what it does? There's some clues you can get from checking the process list open files like, what directory the processes are started in (CWD), what files the process keeps open (BASH?, PERL?), if there's any connections made. Run (as root): ```
\ps --no-headers -C bioset -opid|xargs -iX lsof -Pwlnp 'X'
```

---

### Post by dshauld on 2014-06-05
> **unspawn said:**
> There's some clues you can get from checking the process list open files like, what directory the processes are started in (CWD), what files the process keeps open (BASH?, PERL?), if there's any connections made. Run (as root): ```
\ps --no-headers -C bioset -opid|xargs -iX lsof -Pwlnp 'X'
```

Thank you for the reply.

That command doesn't return anything with or without the leading /.
sudo lsof | grep bio 
```

sudo lsof | grep bio
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/1000/gvfs
      Output information may be incomplete.
bioset       67             root  cwd       DIR              252,1         4096          2 /
bioset       67             root  rtd       DIR              252,1         4096          2 /
bioset       67             root  txt   unknown                                            /proc/67/exe
bioset      355             root  cwd       DIR              252,1         4096          2 /
bioset      355             root  rtd       DIR              252,1         4096          2 /
bioset      355             root  txt   unknown                                            /proc/355/exe
bioset      359             root  cwd       DIR              252,1         4096          2 /
bioset      359             root  rtd       DIR              252,1         4096          2 /
bioset      359             root  txt   unknown                                            /proc/359/exe
bioset      383             root  cwd       DIR              252,1         4096          2 /
bioset      383             root  rtd       DIR              252,1         4096          2 /
bioset      383             root  txt   unknown                                            /proc/383/exe
bioset      386             root  cwd       DIR              252,1         4096          2 /
bioset      386             root  rtd       DIR              252,1         4096          2 /
bioset      386             root  txt   unknown                                            /proc/386/exe
bioset     2488             root  cwd       DIR              252,1         4096          2 /
bioset     2488             root  rtd       DIR              252,1         4096          2 /
bioset     2488             root  txt   unknown                                            /proc/2488/exe
bioset     2491             root  cwd       DIR              252,1         4096          2 /
bioset     2491             root  rtd       DIR              252,1         4096          2 /
bioset     2491             root  txt   unknown                                            /proc/2491/exe
bioset     2506             root  cwd       DIR              252,1         4096          2 /
bioset     2506             root  rtd       DIR              252,1         4096          2 /
bioset     2506             root  txt   unknown                                            /proc/2506/exe
bioset     2509             root  cwd       DIR              252,1         4096          2 /
bioset     2509             root  rtd       DIR              252,1         4096          2 /
bioset     2509             root  txt   unknown                                            /proc/2509/exe
bioset     2554             root  cwd       DIR              252,1         4096          2 /
bioset     2554             root  rtd       DIR              252,1         4096          2 /
bioset     2554             root  txt   unknown                                            /proc/2554/exe
bioset     2557             root  cwd       DIR              252,1         4096          2 /
bioset     2557             root  rtd       DIR              252,1         4096          2 /
bioset     2557             root  txt   unknown                                            /proc/2557/exe
bioset     2620             root  cwd       DIR              252,1         4096          2 /
bioset     2620             root  rtd       DIR              252,1         4096          2 /
bioset     2620             root  txt   unknown                                            /proc/2620/exe
bioset     2623             root  cwd       DIR              252,1         4096          2 /
bioset     2623             root  rtd       DIR              252,1         4096          2 /
bioset     2623             root  txt   unknown                                            /proc/2623/exe
bioset     2636             root  cwd       DIR              252,1         4096          2 /
bioset     2636             root  rtd       DIR              252,1         4096          2 /
bioset     2636             root  txt   unknown                                            /proc/2636/exe
bioset     2641             root  cwd       DIR              252,1         4096          2 /
bioset     2641             root  rtd       DIR              252,1         4096          2 /
bioset     2641             root  txt   unknown                                            /proc/2641/exe
bioset     2685             root  cwd       DIR              252,1         4096          2 /
bioset     2685             root  rtd       DIR              252,1         4096          2 /
bioset     2685             root  txt   unknown                                            /proc/2685/exe
bioset     2688             root  cwd       DIR              252,1         4096          2 /
bioset     2688             root  rtd       DIR              252,1         4096          2 /
bioset     2688             root  txt   unknown                                            /proc/2688/exe
bioset     2711             root  cwd       DIR              252,1         4096          2 /
bioset     2711             root  rtd       DIR              252,1         4096          2 /
bioset     2711             root  txt   unknown                                            /proc/2711/exe
bioset     2714             root  cwd       DIR              252,1         4096          2 /
bioset     2714             root  rtd       DIR              252,1         4096          2 /
bioset     2714             root  txt   unknown                                            /proc/2714/exe
bioset     2760             root  cwd       DIR              252,1         4096          2 /
bioset     2760             root  rtd       DIR              252,1         4096          2 /
bioset     2760             root  txt   unknown                                            /proc/2760/exe
bioset     2763             root  cwd       DIR              252,1         4096          2 /
bioset     2763             root  rtd       DIR              252,1         4096          2 /
bioset     2763             root  txt   unknown                                            /proc/2763/exe
bioset     2783             root  cwd       DIR              252,1         4096          2 /
bioset     2783             root  rtd       DIR              252,1         4096          2 /
bioset     2783             root  txt   unknown                                            /proc/2783/exe
bioset     2786             root  cwd       DIR              252,1         4096          2 /
bioset     2786             root  rtd       DIR              252,1         4096          2 /
bioset     2786             root  txt   unknown                                            /proc/2786/exe
bioset     2836             root  cwd       DIR              252,1         4096          2 /
bioset     2836             root  rtd       DIR              252,1         4096          2 /
bioset     2836             root  txt   unknown                                            /proc/2836/exe
bioset     2840             root  cwd       DIR              252,1         4096          2 /
bioset     2840             root  rtd       DIR              252,1         4096          2 /
bioset     2840             root  txt   unknown                                            /proc/2840/exe
bioset     2859             root  cwd       DIR              252,1         4096          2 /
bioset     2859             root  rtd       DIR              252,1         4096          2 /
bioset     2859             root  txt   unknown                                            /proc/2859/exe
bioset     2862             root  cwd       DIR              252,1         4096          2 /
bioset     2862             root  rtd       DIR              252,1         4096          2 /
bioset     2862             root  txt   unknown                                            /proc/2862/exe
bioset     2915             root  cwd       DIR              252,1         4096          2 /
bioset     2915             root  rtd       DIR              252,1         4096          2 /
bioset     2915             root  txt   unknown                                            /proc/2915/exe
bioset     2918             root  cwd       DIR              252,1         4096          2 /
bioset     2918             root  rtd       DIR              252,1         4096          2 /
bioset     2918             root  txt   unknown                                            /proc/2918/exe
bioset     2938             root  cwd       DIR              252,1         4096          2 /
bioset     2938             root  rtd       DIR              252,1         4096          2 /
bioset     2938             root  txt   unknown                                            /proc/2938/exe
bioset     2941             root  cwd       DIR              252,1         4096          2 /
bioset     2941             root  rtd       DIR              252,1         4096          2 /
bioset     2941             root  txt   unknown                                            /proc/2941/exe

```
sudo ps -elf | gerp bio
```

1 S root        67     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root       355     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root       359     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root       383     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root       386     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root      2488     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root      2491     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root      2506     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root      2509     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root      2554     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root      2557     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root      2620     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root      2623     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root      2636     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root      2641     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root      2685     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root      2688     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root      2711     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root      2714     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root      2760     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root      2763     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root      2783     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root      2786     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root      2836     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root      2840     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root      2859     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root      2862     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root      2915     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root      2918     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root      2938     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
1 S root      2941     2  0  60 -20 -     0 rescue Jun03 ?        00:00:00 [bioset]
0 S c        31451 30959  0  80   0 -  2364 pipe_w 07:10 pts/0    00:00:00 grep --colour=auto bio

```
ps faux | grep bioset
```

ps faux | grep bioset
root        67  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root       355  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root       359  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root       383  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root       386  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root      2488  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root      2491  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root      2506  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root      2509  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root      2554  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root      2557  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root      2620  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root      2623  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root      2636  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root      2641  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root      2685  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root      2688  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root      2711  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root      2714  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root      2760  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root      2763  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root      2783  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root      2786  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root      2836  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root      2840  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root      2859  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root      2862  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root      2915  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root      2918  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root      2938  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]
root      2941  0.0  0.0      0     0 ?        S<   Jun03   0:00  \_ [bioset]

```

---

### Post by unspawn on 2014-06-05
Thanks. Now I don't know why it lists the binary type as "unknown" (or actually shows an "exe" entry for it) and while its process name can be faked items with a process name between square brackets usually denote kernel threads and the "\_ " part indicates they're children of process Id 2 (should be kthreadd aka the kernel thread daemon). If that's the case these commands hopefully won't return anything of use: ```
readlink -f /proc/67/exe ldd /proc/67/exe
```

---

### Post by dshauld on 2014-06-05
> **unspawn said:**
> Thanks. Now I don't know why it lists the binary type as "unknown" (or actually shows an "exe" entry for it) and while its process name can be faked items with a process name between square brackets usually denote kernel threads and the "\_ " part indicates they're children of process Id 2 (should be kthreadd aka the kernel thread daemon). If that's the case these commands hopefully won't return anything of use: ```
readlink -f /proc/67/exe ldd /proc/67/exe
```

Thanks for your help. That command returns nothing. Actually I get 'readlink: extra operand &#8216;ldd&#8217;' when I run that command but separately they return nothing.

What do you make of that post by the Guest I linked to on the forum? When I was looking for information about this process it was sparse and that post got me thinking it may be a virus.

Every other process I looked for I could find information on. How is it that a process doesn't have any explanation or documentation?

---

### Post by hollowsyndicate on 2014-06-05
after googling it doesn't appear to be a virus.

---

### Post by dshauld on 2014-06-05
> **hollowsyndicate said:**
> after googling it doesn't appear to be a virus.

Thank you for the optimism. 

What do you think it is? I would be happy to run any commands that may shed some light. I'm not an expert by any means so I have no idea what to do. 

All I know is I have a process that's impossible to kill, has little to no documentation and supposedly abstracts TCP/IP connections.

---

### Post by unspawn on 2014-06-06
> **dshauld said:**
> Thanks for your help. That command returns nothing. Actually I get 'readlink: extra operand ‘ldd’' when I run that command but separately they return nothing. Yeah sorry, that was a formatting fsckup the commands should indeed be run separately.   > **dshauld said:**
> What do you make of that post by the Guest I linked to on the forum?  Which post do you mean?   > **dshauld said:**
> When I was looking for information about this process it was sparse and that post got me thinking it may be a virus. The reflex should be to gather nfo. Now you've got some commands for next time.   > **dshauld said:**
> Every other process I looked for I could find information on. How is it that a process doesn't have any explanation or documentation? Common kernel processes may be mentioned deep in the bowels of the kernel Documentation/ but simply don't have any manual or info pages. Like I said they'll usually be children (have a PPID) of the kthreadd.

---

### Post by dshauld on 2014-06-07
> **unspawn said:**
> Yeah sorry, that was a formatting fsckup the commands should indeed be run separately.    Which post do you mean?    The reflex should be to gather nfo. Now you've got some commands for next time.    Common kernel processes may be mentioned deep in the bowels of the kernel Documentation/ but simply don't have any manual or info pages. Like I said they'll usually be children (have a PPID) of the kthreadd.

The post on the 'lunaticoutpost' forum. The guest poster says, 'Have a bunch of new processes.  Bioset is one of them.' and links to linux.die.net. That's a strange post if it was intended for kernel developers. If it were for the kernel wouldn't I be able to find more information about it even with no man or info page?

Also thank you for the information about it being a child process but doesn't that make it more suspicious with no info? Wouldn't a virus/rootkit try to get loaded/attached to a process near ring 0?

Sorry if that doesn't make much sense, I am not a programmer or sysadmin. I just have an interest in security.

---

### Post by dshauld on 2014-06-07
It appears to be related to Truecrypt

```

After restart, before starting truecrypt
ps -A | grep bioset
   67 ?        00:00:00 bioset
  355 ?        00:00:00 bioset
  359 ?        00:00:00 bioset
  383 ?        00:00:00 bioset
  386 ?        00:00:00 bioset

After starting truecrypt
ps -A | grep bioset
   67 ?        00:00:00 bioset
  355 ?        00:00:00 bioset
  359 ?        00:00:00 bioset
  383 ?        00:00:00 bioset
  386 ?        00:00:00 bioset
 2506 ?        00:00:00 bioset
 2509 ?        00:00:00 bioset
 2523 ?        00:00:00 bioset
 2526 ?        00:00:00 bioset
 2568 ?        00:00:00 bioset
 2573 ?        00:00:00 bioset
 2632 ?        00:00:00 bioset
 2635 ?        00:00:00 bioset
 2647 ?        00:00:00 bioset
 2650 ?        00:00:00 bioset
 2694 ?        00:00:00 bioset
 2697 ?        00:00:00 bioset
 2715 ?        00:00:00 bioset
 2718 ?        00:00:00 bioset
 2764 ?        00:00:00 bioset
 2767 ?        00:00:00 bioset
 2785 ?        00:00:00 bioset
 2789 ?        00:00:00 bioset
 2836 ?        00:00:00 bioset
 2839 ?        00:00:00 bioset
 2857 ?        00:00:00 bioset
 2860 ?        00:00:00 bioset
 2911 ?        00:00:00 bioset
 2914 ?        00:00:00 bioset
 2932 ?        00:00:00 bioset
 2935 ?        00:00:00 bioset

```

---

### Post by unspawn on 2014-06-08
> **dshauld said:**
> It appears to be related to Truecrypt Ha! Thanks for the clue. See: [http://lxr.free-electrons.com/ident?i=bio_set](http://lxr.free-electrons.com/ident?i=bio_set) ("bio" as in "block I/O").

---

