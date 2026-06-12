---
title: "date +%s does not work on server???"
date: 2023-08-15
forum: Server Platforms
---

### Post by pqwoerituytrueiwoq on 2023-08-15
from my server (over ssh):
```
[FONT=monospace][COLOR=#000000]$ lsb_release -a && echo "Kernel: $(uname -r)" && echo -e "LANG: $LANG\n"  && date --version && date[/COLOR]
 && date +%s
[/FONT][FONT=monospace][COLOR=#000000]No LSB modules are available. [/COLOR]
Distributor ID: Ubuntu 
Description:    Ubuntu 22.04.3 LTS 
Release:        22.04 
Codename:       jammy 
Kernel: 5.15.0-78-generic 
LANG: en_US.UTF-8 

date (GNU coreutils) 8.32 
Copyright (C) 2020 Free Software Foundation, Inc. 
License GPLv3+: GNU GPL version 3 or later <https://gnu.org/licenses/gpl.html>. 
This is free software: you are free to change and redistribute it. 
There is NO WARRANTY, to the extent permitted by law. 

Written by David MacKenzie. 
Tuesday August 15, 01:45 PM 
date: extra operand ‘+%s’ 
Try 'date --help' for more information.
[/FONT]

```
from my desktiop:
```
[FONT=monospace][COLOR=#000000]$ lsb_release -a && echo "Kernel: $(uname -r)" && echo -e "LANG: $LANG\n"  && date --version &[/COLOR]
& date && date +%s 
No LSB modules are available. 
Distributor ID: Ubuntu 
Description:    Ubuntu 22.04.3 LTS 
Release:        22.04 
Codename:       jammy 
Kernel: 5.19.0-46-generic 
LANG: en_US.UTF-8 

date (GNU coreutils) 8.32 
Copyright (C) 2020 Free Software Foundation, Inc. 
License GPLv3+: GNU GPL version 3 or later <https://gnu.org/licenses/gpl.html>. 
This is free software: you are free to change and redistribute it. 
There is NO WARRANTY, to the extent permitted by law. 

Written by David MacKenzie. 
Tue Aug 15 01:45:55 PM EDT 2023 
1692121555
[/FONT]
```

---

### Post by #&amp;thj^% on 2023-08-15
On your sever over ssh, will you include this as well:
```
 timedatectl status
```

---

### Post by MAFoElffen on 2023-08-15
IDK. I tested this on both my servers via ssh... At first, when I copy pasted your command to the prompt, it hung on the "date +%s" part of it. But if I retyped it, it did fine(?)
```

mafoelffen@Mikes-B460M:~$ lsb_release -a && echo "Kernel: $(uname -r)" && echo -e "LANG: $LANG\n"  && date --version && date && date --version && date +%s
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.3 LTS
Release:    22.04
Codename:    jammy
Kernel: 6.2.0-26-generic
LANG: en_US.UTF-8

date (GNU coreutils) 8.32
Copyright (C) 2020 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <https://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Written by David MacKenzie.
Tue Aug 15 03:02:38 PM PDT 2023
date (GNU coreutils) 8.32
Copyright (C) 2020 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <https://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Written by David MacKenzie.
1692136958
mafoelffen@Mikes-B460M:~$ exit
logout
Connection to 10.0.0.3 closed.
mafoelffen@Mikes-ThinkPad-T520:~$ ssh mafoelffen@10.0.0.5
Welcome to Ubuntu 22.04.3 LTS (GNU/Linux 6.2.0-26-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Tue Aug 15 03:03:03 PM PDT 2023

  System load:                 0.51318359375
  Usage of /home:              unknown
  Memory usage:                19%
  Swap usage:                  0%
  Temperature:                 66.0 C
  Processes:                   1099
  Users logged in:             1
  IPv4 address for br0:        10.0.0.6
  IPv4 address for enp6s0:     10.0.0.5
  IPv6 address for enp6s0:     2601:603:4900:77e0::c5f
  IPv6 address for enp6s0:     2601:603:4900:77e0:67c:16ff:fec3:58a0
  IPv6 address for enp9s0f0:   2601:603:4900:77e0::7c56
  IPv6 address for enp9s0f0:   2601:603:4900:77e0:1efd:8ff:fe79:e80e
  IPv4 address for enp9s0f0v0: 10.0.0.10
  IPv6 address for enp9s0f0v0: 2601:603:4900:77e0::4d0d
  IPv6 address for enp9s0f0v0: 2601:603:4900:77e0:e466:b4ff:fe2d:4b44
  IPv4 address for enp9s0f0v1: 10.0.0.11
  IPv6 address for enp9s0f0v1: 2601:603:4900:77e0::36be
  IPv6 address for enp9s0f0v1: 2601:603:4900:77e0:5c78:5fff:fe90:e109
  IPv4 address for enp9s0f0v2: 10.0.0.12
  IPv6 address for enp9s0f0v2: 2601:603:4900:77e0::56a5
  IPv6 address for enp9s0f0v2: 2601:603:4900:77e0:dc39:abff:fe9a:db58
  IPv4 address for enp9s0f0v3: 10.0.0.13
  IPv6 address for enp9s0f0v3: 2601:603:4900:77e0::f0d0
  IPv6 address for enp9s0f0v3: 2601:603:4900:77e0:505d:78ff:fefa:d314
  IPv4 address for enp9s0f0v4: 10.0.0.14
  IPv6 address for enp9s0f0v4: 2601:603:4900:77e0::5df1
  IPv6 address for enp9s0f0v4: 2601:603:4900:77e0:9414:e8ff:fe98:6f7b
  IPv4 address for enp9s0f0v5: 10.0.0.15
  IPv6 address for enp9s0f0v5: 2601:603:4900:77e0::6f2b
  IPv6 address for enp9s0f0v5: 2601:603:4900:77e0:3d:f6ff:fe89:baeb
  IPv4 address for enp9s0f0v6: 10.0.0.16
  IPv6 address for enp9s0f0v6: 2601:603:4900:77e0::970f
  IPv6 address for enp9s0f0v6: 2601:603:4900:77e0:88e:d2ff:fe76:85fc
  IPv4 address for virbr0:     192.168.122.1
  IPv4 address for virbr1:     192.168.100.1
  IPv4 address for virbr2:     192.168.130.1
  IPv4 address for virbr3:     192.168.120.1
  IPv4 address for wlo1:       10.0.0.11
  IPv6 address for wlo1:       2601:603:4900:77e0:fdde:1c85:80cc:e1ef
  IPv6 address for wlo1:       2601:603:4900:77e0:c4b4:889d:a033:f95b
  IPv6 address for wlo1:       2601:603:4900:77e0::4d3

 * Strictly confined Kubernetes makes edge and IoT secure. Learn how MicroK8s
   just raised the bar for easy, resilient and secure K8s cluster deployment.

   https://ubuntu.com/engage/secure-kubernetes-at-the-edge

Expanded Security Maintenance for Applications is enabled.

13 updates can be applied immediately.
To see these additional updates run: apt list --upgradable




Last login: Tue Aug 15 14:26:29 2023 from 10.0.0.170
mafoelffen@msi-ubuntu:~$ lsb_release -a && echo "Kernel: $(uname -r)" && echo -e "LANG: $LANG\n"  && date --version && date && date --version && date +%s
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.3 LTS
Release:    22.04
Codename:    jammy
Kernel: 6.2.0-26-generic
LANG: en_US.UTF-8

date (GNU coreutils) 8.32
Copyright (C) 2020 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <https://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Written by David MacKenzie.
Tue Aug 15 03:03:34 PM PDT 2023
date (GNU coreutils) 8.32
Copyright (C) 2020 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <https://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Written by David MacKenzie.
1692137014

```

---

### Post by pqwoerituytrueiwoq on 2023-08-16
Server:
```
[FONT=monospace][COLOR=#000000]$ timedatectl status [/COLOR]
               Local time: Wed 2023-08-16 00:39:43 EDT 
           Universal time: Wed 2023-08-16 04:39:43 UTC 
                 RTC time: Wed 2023-08-16 04:39:43 
                Time zone: America/New_York (EDT, -0400) 
System clock synchronized: yes 
              NTP service: n/a 
          RTC in local TZ: no
[/FONT]

```
Desktop:
```
[FONT=monospace][COLOR=#000000]$ timedatectl status [/COLOR]
               Local time: Wed 2023-08-16 00:40:27 EDT 
           Universal time: Wed 2023-08-16 04:40:27 UTC 
                 RTC time: Wed 2023-08-16 04:40:30 
                Time zone: America/New_York (EDT, -0400) 
System clock synchronized: no 
              NTP service: n/a 
          RTC in local TZ: no
[/FONT]
```

now this is odd, so i made this file using nano on the server via ssh
```
[FONT=monospace][COLOR=#000000]$ cat test.sh  [/COLOR]
echo "$(date +%s)" 
[COLOR=#000000]$ bash test.sh     [/COLOR]
1692160888 
[/FONT]
```
:confused:

---

### Post by MAFoElffen on 2023-08-16
That is just strange. Like i said, I can run it on mine, and is fine. But if I copy pasted from your post, it hung. As far as i could see, it was the same exact commands. I can't explain that at all.

---

### Post by Paddy Landau on 2023-08-16
Are you maybe not running bash on your server?

Try these commands for thoroughness:
```
echo $0
readlink /proc/${$}/exe
ps -p ${$}
```
You could also try digging into [FONT=courier new]date[/FONT] itself:
```
which date
type date
date --help
```

---

### Post by pqwoerituytrueiwoq on 2023-08-16
I found it... thanks Paddy for solving issue of my own creation...

```
[FONT=monospace][COLOR=#000000]$ type date [/COLOR]
date is aliased to `date +"%A %B %d, %I:%M %p"'
[/FONT]
```
wait what!? why...
*reads .bash_aliases*
why did i do that?
why do i not recall doing that?

---

### Post by Paddy Landau on 2023-08-16
> **pqwoerituytrueiwoq said:**
> wait what!? why...
That's funny! Sometimes, we do things that we later forget — and regret. I've done similar things.

These days, when I use an alias for an everyday command, I change the name slightly; for example:
```
alias cpi='copy --interactive'
```
I don't even alias [FONT=courier new]ls[/FONT].

---

### Post by SeijiSensei on 2023-08-16
> **pqwoerituytrueiwoq said:**
> 
wait what!? why...
*reads .bash_aliases*
why did i do that?
why do i not recall doing that?
That's what comments are for.

---

### Post by pqwoerituytrueiwoq on 2023-08-16
> **SeijiSensei said:**
> That's what comments are for.
i rarely comment my code, and when i do it is cause it is VERY confusing to read, unless it is a config file, then i will put notes in it

---

### Post by Paddy Landau on 2023-08-17
> **pqwoerituytrueiwoq said:**
> i rarely comment my code, and when i do it is cause it is VERY confusing to read, unless it is a config file, then i will put notes in it
The first three rules for a programmer: Document, document, document.

---

### Post by TheFu on 2023-08-17
All my trivial coding starts with comments (aka pseudo-code), then I fill in the code that does what the comments say.   It is how I work.  

It lets me design the software as quickly as I type without getting hung up on syntax.  Plus, for software that takes over an hour to create, I don't need to wonder "what was I trying to do here" when I return later.

---

### Post by pqwoerituytrueiwoq on 2023-08-18
i just go and read my code
Examples of how bad i am about comments
[https://github.com/GM-Script-Writer-62850/PICO_W_Thermostat/blob/main/PICO/main.py](https://github.com/GM-Script-Writer-62850/PICO_W_Thermostat/blob/main/PICO/main.py)
[https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/blob/master/res/main.js](https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/blob/master/res/main.js)

---

### Post by TheFu on 2023-08-18
> **pqwoerituytrueiwoq said:**
> i just go and read my code
Examples of how bad i am about comments
[https://github.com/GM-Script-Writer-62850/PICO_W_Thermostat/blob/main/PICO/main.py](https://github.com/GM-Script-Writer-62850/PICO_W_Thermostat/blob/main/PICO/main.py)
[https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/blob/master/res/main.js](https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/blob/master/res/main.js)

At every professional coding job I had, a lack of comments would be considered a major bug on the review.  It is part of ensuring that code is maintainable.  People go crazy about it.  The trick is NOT to just have the code comment say EXACTLY what the code does - people aren't stupid.  It is the more subtle purpose for the code that needs to be in the comments.  Writing self-documenting code is impossible. Every block of code needs to document the overall purpose.  Document the area of the forest, not the trees. Every once in a long while, 1 tree is particularly obtuse and needs documenting, but 95+% of the time, the trees are just trees doing their job.  Think of a tree as a line of code and a group of trees as a code block, say 10 SLOC.

I've reviewed code from hundreds of other people in my career.  These reviews were NOT optional.  I had to sign a form stating that I'd either not found any issues at all or that all issues found were documented above and in attached sheets.  I've created some truly nasty code - a huge set of binary logic statements that had been simplified from requirements with a huge grid.  The "simplification" process was over 20 full pages of hand work to get down to 1 5 line binary statement full of **and**s and **or**s.  We were tight on memory (only has 104Kb), so I'd packed the bits into as few variables as possible.  At the 2 formal code reviews, only 1 other person in about 20 people attending, actually reviewed the equations.  Everyone else said they were going to trust unit testing for validation.  Unit testing sucked.  My office was full of boxed paper printouts stacked 4ft high for a few weeks as I and some of my peers reviewed everything, including all these bits.  Fortunately, that code worked perfectly and worked for another 20 yrs without flaw before the program was shutdown.

And the code comment for those nasty statements?  It was just a reference to the table number in the requirements - known as FSSRs.
 [https://www.allacronyms.com/FSSR/Flight_System_Software_Requirements](https://www.allacronyms.com/FSSR/Flight_System_Software_Requirements)

---

### Post by Paddy Landau on 2023-08-18
When I studied computer science at university, a lack of proper comments in a program was an instant fail, even if your code worked perfectly.

For assembly code, not only did you need the usual type of comments, but also the professors insisted on a comment on each and every line — which was sometimes really hard to do appropriately if you were, say, incrementing a counter by 1.

But it did instill an excellent habit in me, which paid dividends many times when going back to old code in a working environment.

---

### Post by TheFu on 2023-08-18
An example of self-documenting code:
```
$ more srt-dump-trk2-as-es-translate-to-en
#!/bin/bash

for i in "$@" ; do
   nice mkvextract tracks $i 2:$i.es.srt
   nice apertium spa-eng_US $i.es.srt $i.en.srt
   rm $i.es.srt
   rename 's/.mkv.en.srt/.en.srt/g' $i.en.srt
done
```

Of course, it is perfectly clear to me.  The name of the file tells much ... but to the next guy, it really should be documented more like this:
```
$ more srt-dump-trk2-as-es-translate-to-en
#!/bin/bash

# Usage:  $0 <glob of mkv files>
#    $ srt-dump-trk2-as-es-translate-to-en   *mkv

# Loop over each mkv in the glob
for i in "$@" ; do

   # Pull the 2nd track, hopefully a Spanish SRT caption from an mkv video
   nice mkvextract tracks $i 2:$i.es.srt

   # Use translation to convert from Spanish to US English
   nice apertium spa-eng_US $i.es.srt $i.en.srt

   # Remove the temporary Spanish srt
   rm $i.es.srt

   # rename the new translation to match the expected pattern
   rename 's/.mkv.en.srt/.en.srt/g' $i.en.srt
done
```

Pulling the tracks out takes a long time, but the translation is less than 1 second.  Sometimes the translation is literal and doesn't reflect the true, intended, meaning.  For better translation, give up some privacy and pay Google for an API key.
I really dislike when SRT captions are provided, claim to be English, but aren't.  Definitely a 1st world problem.  I also wish captions weren't in all caps, which is lazy, but I suppose different languages have different capitalization rules to follow and this skips that completely. In English, seems like SHOUTING.

---

### Post by MAFoElffen on 2023-08-18
I do the same as TheFu... I start out with comments to map out the logic flow and what I intend to do. 

Much longer than I would like to admit, I was a COBOL Maintenance Programmer for production systems. Much of my time was going through code that usually already had 10 patches on it, trying to figure out where the logic broke. I hated when the comments didn't match what was there, or didn't exist at all. That taught me that I should always comment what I did, so that others reading it later could follow what it was meant to do.

As you can see from my own code ([https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info))

In the ToDo Section:
```

#
# Add comments as script documentation:
#   - Document logic flow
#

```
As time allows, I still go back and add more comments... I want things to live on, and be useful, beyond my own existence.

When I taught Computer Science, I was a stickler for comments, and code formatting. I tried to instill habits that made thing easy to follow, read, made sense and were relatable. Even with the names of functions and variables. Information Technology people have a certain sense of humor. Things are easier and the time passes better when it reads like a story.

---

### Post by #&amp;thj^% on 2023-08-18
> **MAFoElffen said:**
> I start out with comments to map out the logic flow and what I intend to do. 

Much longer than I would like to admit, I was a COBOL Maintenance Programmer for production systems. Much of my time was going through code that usually already had 10 patches on it, trying to figure out where the logic broke. I hated when the comments didn't match what was there, or didn't exist at all. That taught me that I should always comment what I did, so that others reading it later could follow what it was meant to do.

As you can see from my own code ([https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info))

In the ToDo Section:
```

#
# Add comments as script documentation:
#   - Document logic flow
#

```
As time allows, I still go back and add more comments... I want things to live on, and be useful, beyond my own existence.

When I taught Computer Science, I was a stickler for comments, and code formatting. I tried to instill habits that made thing easy to follow, read, made sense and were relatable. Even with the names of functions and variables. Information Technology people have a certain sense of humor. Things are easier and the time passes better when it reads like a story.
+1 Nice Post
At my work if it's not commented, well that person's future there becomes less bright. (I was trying to sound nice)
It's just the Proper thing to do for any programmer. (novice to guru)

---

### Post by TheFu on 2023-08-18
My first real job was 50% maintenance handling issues in code that was 15+ yrs old. Every line could be traced to a specific programmer and authorization. Every programmer would put a new header in a file that made it clear which lines they'd touched.  A/C/D = Added/Changed/Deleted After the line numbers were hex codes which were incremented each time a line was changed. Every final change that was formally checked into the version control system would get a permanent tag.  100% traceable using 1960s technology.

We learned about long retired programmers and got a feel for the types of mistakes they'd make. There were also many fantastic programmers who seldom made any mistakes.  If they did something and it wasn't obvious, there was usually a very good reason.  Fortunately, they were still working on the project  ... er ... 5 levels higher than me and at a different company, but we could exchange messages to find out what really happened.  They always remembered the tricky stuff. Some of the other stuff, where their wasn't a specific reason, wouldn't be remembered.  Do you remember every module you coded 10 yrs ago?  I don't.

Some of the original code was created with very few processes.  It amazed me how well it all worked within the hardware constraints.  OTOH, later changed needed to be carefully inserted so they didn't inadvertently break anything that was already working.  There were a few modules where touching anything was known to cause an unintentional bug.  Considering that we had a mandate for bug-free code, this wasn't good.  The software was extremely high quality.  When I started, 10 programmers were creating 2 bugs per year.  5 yrs later, 20 programmers were creating 1 bug every other year. That's how good the development process was. It was nearly impossible for any code changes to slip passed all the formal reviews.  I probably wrote the most SLOCs there because I had 1 authorization that included a huge array.  Most of the changes would be 1 - 100 lines, but that array was over 4000 lines.  And each programmer would probably work 5-10 projects each year.  We weren't crapping out code like most commercial programmers do.  Plus, it wasn't like we had huge reuse libraries.  The languages involved were all very special use and not used anywhere else.

When I moved to more general programming in C/C++, I brought some of the processes with me.  At one job, I was brought in as a senior developer and had to teach everyone in the company about a software development process along with automation.  When I got there, they were actually manually swapping DLLs that only 1 person could build. When that person was gone, nobody else could build the DLL/library they maintained.  They seemed to put code where it was convenient, not where it made sense for building a library.  Once I talked the team through my intent, they quickly jumped on-board and in just a few days, we had completely re-organized the code, layered the dependencies, removing circular dependencies completely, and had automatic build scripts to support 3 different platforms.  Over the next year, we grew to support 10 platforms.  None of that would have been possible without a smart team and their understanding for what we needed for layering of the libraries.

Anyway, after all that was done, we started working team programming standards to make for more maintainable software.  It really wasn't about the standards, but training the team members to think about the next guy and to create defensive code that failed at compile time, not run-time.  We also wanted bugs to jump out based on our standard formatting and indentation.  We prohibited some valid coding techniques because they were prone to hiding bugs.  When new people joined the team, we could pass them the Coding Standards doc and have them review it, ask questions, and gain a shared understanding for "why" things needed to be coded a specific way.  Plus, if they came with experience, they'd be able to teach us and modify the standards for the better, so we'd all learn.

The trick is not to get too tied up in process steps that don't actually help make more code that has no user-impacting bugs.  In the commercial world, it is all about avoiding bugs that the end-users see. There can be 500 bugs that nobody sees. Those are fine.

---

### Post by Paddy Landau on 2023-08-18
Some impressive work there!

I worked for a while at a company where previous programmers, since retired or even dead, had competed with each other to create "funny" code (like MOVE GOLFBALL TO TEE instead of using meaningful names), and to obfuscate their code.

It was a nightmare to deal with.

---

### Post by #&amp;thj^% on 2023-08-18
> **Paddy Landau said:**
> 
It was a nightmare to deal with.

Good Grief Paddy that makes my head spin....YUCK.
TheFu sums it up nicely
> The trick is not to get too tied up in process steps that don't actually help make more code that has no user-impacting bugs. In the commercial world, it is all about avoiding bugs that the end-users see. There can be 500 bugs that nobody sees. Those are fine. 

---

### Post by TheFu on 2023-08-18
On my first C++ project team, we didn't have any process and any known bug, including memory leaks, were snuffed out within 1-2 days.  It was a point of pride for the 5 person team. Never again did I see a project like that.  Plus, that code ran on 12 platforms all nearly bug free.  Little did I realize that was highly unusual.  Most teams have thousands of bugs in their code that is always growing.  

At my next job, I was on the bug triage committee assigning levels to every bug that was found.  That's when I learned that bugs never actually reduce, they just expand to become more numerous.  We had a few programmers that would close 5 bugs in 1 day, but introduce 10 more and not actually fix 2 of the 5 they claimed to have closed.  As their manager, I got to point out that we could use that data when it came time for salary discussions.  One of the guys left the company. The other guy became much more careful and is both a friend AND a much better coder ... er ... until he disappeared in his home country.  Think he was jailed as a political prisoner, but nobody knows. Hopefully, his wife and daughter are safely in hiding. The ruler there was just reelected for his last allowed term, unfortunately.

---

### Post by Paddy Landau on 2023-08-19
> **TheFu said:**
> Think he was jailed as a political prisoner
That sucks. I'm sorry to hear that.

---

