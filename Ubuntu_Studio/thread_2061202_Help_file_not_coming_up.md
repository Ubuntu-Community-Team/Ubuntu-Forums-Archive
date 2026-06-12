---
title: "Help file not coming up"
date: 2012-09-21
forum: Ubuntu Studio
---

### Post by JXR on 2012-09-21
I just instilled UStudio (dual boot currently) and am thrilled.

I expect I have a lot to learn about this OS so I immediately tried to read the ("Start Menu") Help option.

Help
When I attempt to enable Help I get the browser message

 > **File not found**  Firefox can't find the file at /usr/share/ubuntustudio-docs/about/ubuntustudio-index.html.How can I enable Help?

---

### Post by CrocoDuck on 2012-09-22
Hi. I think I just find out that actually both the directory ubuntustudio-docs and the file ubuntustudio-index.html  doesn't exist in the system. But don't worry, everything is online: [http://ubuntustudio.org/support](http://ubuntustudio.org/support)

---

### Post by jerrrys on 2012-09-22
Have you updated and upgraded your system since the install?

---

### Post by JXR on 2012-09-22
Good Idea!
 
I updated the "system" (something like 350+ files!) this morning (2 AM). Haven't checked yet to see if it brought in Help. Will let you know.

---

### Post by smartboyhw on 2012-09-23
Uh I actually reported a bug on this 3-4 weeks ago but anyway you guys said it works then it works:)

---

### Post by JXR on 2012-09-23
Help file still not coming up (after completing updates). Same Firefox message.

---

### Post by smartboyhw on 2012-10-01
OK here is the problem.

I have reported a bug (LP:#1041882) in July. Actually the bug IS fixed however the Ubuntu Studio Team didn't get it into SRU. Len Ovenwerks is working on putting it into an SRU (Stable Release Update). Solution for now:

```
sudo add-apt-repository ppa:smartboyhw/ubuntustudio
``````
sudo apt-get update
``````
sudo apt-get upgrade && sudo apt-get dist-upgrade
```This installs the updated package "ubuntustudio-default-settings" so you can see the help file.

Thanks everybody.

Regards,
Howard Chan
Ubuntu Studio QA Lead

---

### Post by HomeOnThePlains on 2012-10-04
For XFCE desktop help you can go to:

Applications Menu > About XFCE > ? Help

That will take you to: file:///usr/share/doc/xfce4-utils/html/C/index.html

---

### Post by jerrrys on 2012-10-04
So smartboyhw has provided the fix (nice job); is this solved?

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by smartboyhw on 2012-10-05
> **jerrrys said:**
> So smartboyhw has provided the fix (nice job); is this solved?

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Er I didn't provide the fix. The problem is that there is no Stable Release Update for that, so I just made a packaging recipe in Launchpad that builds the fixed code to my ppa:P

---

### Post by jerrrys on 2012-10-05
Thanks smartboyhw; yet another opps on me  :)

---

