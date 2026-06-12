---
title: "For how long is 14.04 supported ?"
date: 2016-11-06
forum: Ubuntu, Linux and OS Chat
---

### Post by linuxyogi on 2016-11-06
Hi,
I tried 16.04 but unfortunately I faced audio issues.I created a thread but nobody replied so I went back to 14.04.

What I want to know is for how long is 14.04 supported ?

[https://www.ubuntu.com/info/release-end-of-life](https://www.ubuntu.com/info/release-end-of-life)

^^ This page indicates begining of 2019. 

But what is the exact date ?

---

### Post by sudodus on 2016-11-06
I know it is April 2019 for standard Ubuntu, but I don't know the exact date. The community flavours support the LTS versions for 3 years, so until April 2017.

There is time for you to create a bug report and to get the problem solved.

---

### Post by linuxyogi on 2016-11-06
Got it. Thanks.

---

### Post by cariboo on 2016-11-07
Have you checked [here]("https://wiki.ubuntu.com/Releases")?

---

### Post by linuxyogi on 2016-11-08
> **cariboo said:**
> Have you checked [here]("https://wiki.ubuntu.com/Releases")?

Yes. It says 

[TABLE]
[TR]
[TD="bgcolor: #762852"]Ubuntu 14.04.2 LTS 
[/TD]
   [TD="bgcolor: #f1f1dd"][Trusty Tahr]("https://wiki.ubuntu.com/TrustyTahr")
[/TD]
   [TD="bgcolor: #f1f1dd"] [Changes]("https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/ChangeSummary/14.04.2")
[/TD]
   [TD="bgcolor: #f1f1dd"] [February 20, 2015]("https://lists.ubuntu.com/archives/ubuntu-announce/2015-February/000192.html") 
[/TD]
   [TD="bgcolor: #f1f1dd"] [HWE August 2016]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support")

[/TD]
[/TR]
[/TABLE]

Frankly I don't know what "HWE" is. I have installed [Debian 8]("https://wiki.debian.org/LTS/") which will be supported 

until end of April/May 2020.

---

### Post by Bucky Ball on 2016-11-08
Good-o. An upgrade to Ubuntu 16.04 LTS would have got you to April 2021.

HWE = hardware enablement stack. Are you even on 14.04.2, which is the one you give there. You should be at 14.04.5. If you are on .2 your are EOL arleady. Open a terminal and

```
lsb_release -a
```

.2 or .5? Anyway, doesn't sound like you're running Ubuntu any more so all a bit redundant from this point.

---

### Post by linuxyogi on 2016-11-08
> **Bucky Ball said:**
> Good-o. An upgrade to Ubuntu 16.04 LTS would have got you to April 2021.

I tried 16.04 but it became impossible to use because of a sound issue. I opened[ a thread]("https://ubuntuforums.org/showthread.php?t=2324107") but no one replied 
so I went back to 14.04.

> **Bucky Ball said:**
> 
HWE = hardware enablement stack. Are you even on 14.04.2, which is the  one you give there. You should be at 14.04.5. If you are on .2 your are  EOL arleady. Open a terminal and

```
lsb_release -a
```

.2 or .5? Anyway, doesn't sound like you're running Ubuntu any more so all a bit redundant from this point.

lsb_release -a printed 14.04.2. It was a fully updated installation updated with apt-get dist-upgrade.

---

### Post by Bucky Ball on 2016-11-08
```
sudo apt-get update
sudo apt-get dist-upgrade
```

... should have got you to .5 Strange. Anyway, doesn't matter now ...

---

### Post by mastablasta on 2016-11-10
it seems dist-upgrade is not enough if you run a HWE. at least i remember i had to do some acrobatics to get to .5. it did give me a notice to upgrade when i logged in to the server.

[SIZE=2]https://wiki.ubuntu.com/Kernel/LTSEnablementStack
[/SIZE]so it was:
> [FONT=Courier New] sudo apt-get install --install-recommends linux-generic-lts-xenial [/FONT]

and as i know i installed server with .3. or maybe it was .4 ?!

i regulary run dist-upgrade manually, i am thinking to also automate it in the unattended updates.

---

