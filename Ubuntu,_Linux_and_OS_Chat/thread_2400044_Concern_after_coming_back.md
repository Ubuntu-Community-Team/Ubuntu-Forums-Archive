---
title: "Concern after coming back"
date: 2018-09-01
forum: Ubuntu, Linux and OS Chat
---

### Post by joel-swanson on 2018-09-01
I don't know if I am the only one feeling this way.  It has been a while since I used Ubuntu very much.  I used to teach classes on servers and Linux and always used Ubuntu because it was the easiest and friendliest to use.  But I just did a fresh install of 18.04 and I have had issue after issue getting things to work.

I originally had an older version installed.  17.something.  I was a bit annoyed to find that I couldn't update the software to install what I needed and I was unable to perform an upgrade.  I found several very complicated sets of instructions and a reason why I couldn't update (something to do with LTS support).  But nothing I could do would allow and update.  So I decided a fresh install was really the only way to go.  Downloading the software immediately locked up the browser but since it was an older version of Ubuntu, I didn't think too much about it.  I booted to windows.  Downloaded the ISO and wrote it to disk.  And did a fresh install of 18.04.  

The reason I was using Ubuntu is that a student asked about a java gui software I had posted.  They couldn't get it to work on ubuntu.  So I thought I would try it.  After fighting just to get 18.04 installed, I finally was able to downloade the java jar file and sure enough it wouldn't run.  Troubleshooting and trying different things (running from the terminal) led me to an error with Assistive Technologies.  I had never actually done anything with assistive technologies but assumed netbeans had maybe added some things in.  So 4 or 5 web searches later and a good 10 to 15 minutes more, I finally found I either had to either back down the version of java or edit a configuration file in etc.  

Then I tried to set up the calendar to connect to google calendar, one of the windows wouldn't give me a scroll bar to get to the button that I assumed must exist as it was asking for permissions. Apparently two confirmation windows was open, but neither would work.   I was able to kill the calendar app with the system monitor but couldn't figure out how kill the two confirmation windows.  I eventually rebooted to get rid of them.

Then I decided to install netbeans so that I could try some things to see if I could get the problem to go away on the jar file.  I used apt to install netbeans, but now it wont run.  I get the splash screen and then nothing.  Running from the terminal gives me some warnings and a stern warning that these warnings will be denied in the future.  But nothing about now.  It just doesn't run.

I know all of these issues are more about add on software rather than the operating system itself.  But the whole point of Ubuntu is that is was supposed to be easy.  It used to be easy.  What I experienced today was not easy.  Installation issues.  Locking up.  Slow starting apps (firefox didn't seem to start so I clicked again, nothing.  SO I clicked again, and three firefox windows opened.  I have a very fast, very new I7 processor and a 1080 nvidia graphic card.  My computer isn't the issue.  I think the calendar issue above was a slow window issue.) Things just not working.  

I'm concerned, is my issue.  I don't want help getting these things to run.  I can manage the troubleshooting.  But new users to Linux will have a harder time and will be turned off by these types of problems.  For years Linux had the "hard to use" label and fought to get rid of it.  I thought Ubuntu was the pinnacle of that fight.  But after having come back after several years away it looks to me like Ubuntu has taken several steps backwards.

---

### Post by TheFu on 2018-09-02
18.04 changed many underlying things.
* snaps for package management
* netplan for network setups

Snaps seem like a great idea. Basically, all packages are loaded with their dependencies and each runs inside a sandbox/container.   More secure and fewer dependency issues, right?   Well, except when you need a program to work with other programs also running inside different sandboxes/containers or you want to extend the program using a library.  Every snap creates a new loop mount too. It is easy to have 50+ mounts, each with a little overhead.
16.04 has some snaps, but you can remove those 100% and the snap subsystem.  I don't know if 18.04 will work without snaps.  Heck, even the DE runs inside a snap on 18.04.  So does firefox, which is probably a good thing for system security.

Netplan ... I like the idea, but the example implementations show the main 5 commonly used configs and seem to lack the 20% of network configs that are used outside a normal house network.  I have no doubt it will be better, eventually.

The easy answer for your students is to point them at Ubuntu 16.04 installs for now.  They can run 18.04 inside a virtual machine to become familiar.

Intel CPU patches.  This week, another round of Intel mitigations against the CPU security issues were released.  These tend to slow higher-end CPUs more than the lower end ones.  Those I saw some performance tests a few days ago which showed the performance impact with this last set was mostly with heavy I/O tasks and usually 5%. For other tasks, I don't remember thinking there was any statistical difference with or without the latest CPU firmware.

BTW, nobody here works for Canonical. We are all just volunteers.  Canonical seems more focused on business juju deployments the last few years.

I think flatpack has won the self-contained, Linux packaging wars already. It took Canonical 5 yrs to stop Unity, so I'm guessing snaps will be around that long too.

---

### Post by monkeybrain20122 on 2018-09-02
> **TheFu said:**
>  I don't know if 18.04 will work without snaps.  Heck, even the DE runs inside a snap on 18.04.  So does firefox, which is probably a good thing for system security.



No, Firefox is not snap. There are only maybe three or four gnome packages which are snaps: system monitor, calculator .. and finally something for running some gnome apps that nobody cares such as recipe(for cooking), this last one has a name like gnome core or something like that so many people mistaken it to be the DE itself but actually it is quite useless and can be removed without consequence (unless you like to cook). Other than the last bit you can install the normal deb packages via apt. I have removed all of them along with snapd so my 18.04 is snap free.

+1 for sticking with 16.04. I find it a lot more stable.

---

### Post by ajgreeny on 2018-09-02
The problem with your java GUI apps not running may be due to the problems reported already with openjdk-11-jre version 10.0.2+13-1ubuntu0.18.04.1 which appeared in the repos last month on the 23rd for me.

I have looked for a bug related to this but not found one specifically for this openjdk version, but all GUI apps ran perfectly with the previous version 10.0.2+13-1ubuntu0.18.04.1 so I imagine a new version will put this right, hopefully very soon.

EDIT:
I have now found a bug [https://bugs.launchpad.net/ubuntu/+source/openjdk-lts/+bug/1788250](https://bugs.launchpad.net/ubuntu/+source/openjdk-lts/+bug/1788250) which gives a workaround at post #4 that works for me using Xubuntu 18.04, though others have said it did not work in Ubuntu 18.04.
Try it out and it may be successful for you.

---

### Post by monkeybrain20122 on 2018-09-02
> **ajgreeny said:**
> The problem with your java GUI apps not running may be due to the problems reported already with openjdk-11-jre version 10.0.2+13-1ubuntu0.18.04.1 which appeared in the repos last month on the 23rd for me.

I have looked for a bug related to this but not found one specifically for this openjdk version, but all GUI apps ran perfectly with the previous version 10.0.2+13-1ubuntu0.18.04.1 so I imagine a new version will put this right, hopefully very soon.

EDIT:
I have now found a bug [https://bugs.launchpad.net/ubuntu/+source/openjdk-lts/+bug/1788250](https://bugs.launchpad.net/ubuntu/+source/openjdk-lts/+bug/1788250) which gives a workaround at post #4 that works for me using Xubuntu 18.04, though others have said it did not work in Ubuntu 18.04.
Try it out and it may be successful for you.

I noticed that problem  right the way when I installed 18.04 3 months ago. I just installed openjdk8 from repo and set it to be the default java with update alternatibves, problem solved. I need java just for running the gui for a few applications, I only need something that works, not care for updating to the newest version.

---

