---
title: "system monitor soing problem"
date: 2012-01-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by shubham1 on 2012-01-01
in system monitor when i am browsing ALL THE PROCESS WHILE GOING UP OR DOWN
it shows an erro see the image i have done nothing expect browsing is it a bug

---

### Post by Paddy Landau on 2012-01-01
I don't understand all of your question, specifically about the going up and down. Processes will constantly change position, if that's what you mean.

Regarding the error: did you try to change the priority of the process?

If this continues to happen, please log out then in, and try again.

---

### Post by shubham1 on 2012-01-01
> **Paddy Landau said:**
> I don't understand all of your question, specifically about the going up and down. Processes will constantly change position, if that's what you mean.

Regarding the error: did you try to change the priority of the process?

If this continues to happen, please log out then in, and try again.
i dont know how to describe in words
open system monitor switch to tab processe
select any process
press down and up key continusaly this i meant to say
i logged out and did again it gives the same error

---

### Post by Paddy Landau on 2012-01-01
Oh, I understand now.

It seems that, somehow, when you press up or down, it thinks you want to change the priority.

You may have to browse using the mouse. I'm sorry, I don't know why it should show that error -- it is strange!

---

### Post by shubham1 on 2012-01-01
yes man is it  a bug ? then we should report it.
does this problem comes to you too
if this bug comes to any one else please report here so i can see and think what to do

---

### Post by scradock on 2012-01-01
> **shubham1 said:**
> yes man is it  a bug ? then we should report it.
does this problem comes to you too
if this bug comes to any one else please report here so i can see and think what to do
Well, I just did exactly what you described, and there was no error. The highlight just goes up or down the process list as expected.

PP updated a few hours ago, 64-bit.

---

### Post by shubham1 on 2012-01-01
> **scradock said:**
> Well, I just did exactly what you described, and there was no error. The highlight just goes up or down the process list as expected.

PP updated a few hours ago, 64-bit.
ok i am running a 32 bit so it may be a 32bit image bug an one with 32bit having the same problem
please report here

---

### Post by keithpeter on 2012-01-02
> **Paddy Landau said:**
> Oh, I understand now.

It seems that, somehow, when you press up or down, it thinks you want to change the priority.

You may have to browse using the mouse. I'm sorry, I don't know why it should show that error -- it is strange!

Hello Shubham1 and Paddy: is this what we are talking about...

[LIST]
[*]Using the up/down keys to change the selected process.
[*]You get the error message because the next key you press is interpreted as an attempt to change priority
[*]I could use the up/down arrows quite a lot before the error box appeared
[/LIST]

Never seen or thought of that one before! This is on 32bit

Happy new year

---

### Post by Paddy Landau on 2012-01-02
Interesting. I cannot duplicate the error (64-bit). If two of you are getting the problem on 32-bit, it may be an idea for one of you to [raise a bug]("https://help.ubuntu.com/community/ReportingBugs"), and post the bug link here so the other can add your vote.

---

### Post by ronacc on 2012-01-02
tried this on my 64 bit sys and it works normally , scrolls and no error , used both dedicated arrow keys and arrow keys on the numeric pad (numlock off) . so it seems to be a 32 bit only bug .

---

### Post by mdurham on 2012-01-02
32 bit here, I can reproduce the error if I hold the key down in auto repeat.

---

### Post by shubham1 on 2012-01-02
then this is a bug any one please report its a bug for 32 bit image

---

### Post by Paddy Landau on 2012-01-02
> **shubham1 said:**
> then this is a bug any one please report its a bug for 32 bit image
Yes, it is clearly a bug. Please to [raise a bug report]("https://help.ubuntu.com/community/ReportingBugs"), and post the report link here so that other people can vote for the bug. (I can't raise the bug report as I have 64-bit.)

---

### Post by shubham1 on 2012-01-02
i am going to start a new thread then if major of the people are facing problem then i will report it as a bug this can be the proof too

---

### Post by shubham1 on 2012-01-02
all 32 bit users attention please we need your help to get this is a bug or not
open system monitor switch to tab processe
select any process
press down and up key continusaly
does a popup like this appears
[http://ubuntuforums.org/showthread.php?t=1902931](http://ubuntuforums.org/showthread.php?t=1902931)
look the image:
[http://ubuntuforums.org/attachment.php?attachmentid=210046&d=1325422483](http://ubuntuforums.org/attachment.php?attachmentid=210046&d=1325422483)
then this is a bug if this problem comes then please report here and dont come please report here later we will take this bug to developers
another 32 bit user([keithpeter]("http://ubuntuforums.org/member.php?u=20948")) has that problem
[http://ubuntuforums.org/attachment.php?attachmentid=210106&stc=1&thumb=1&d=1325500407](http://ubuntuforums.org/attachment.php?attachmentid=210106&stc=1&thumb=1&d=1325500407)
[mdurham]("http://ubuntuforums.org/member.php?u=48410")
also faced the same problem he is to 32 bit we want more people who are 32bit users

---

### Post by ronacc on 2012-01-02
just go ahead and report the bug on launchpad , that way anyone having the same bug can add themselves to it .

once filed post the bug # here so people can find it easily .

---

### Post by MacUntu on 2012-01-02
Not an i386 issue. Seeing it here on an up-to-date amd64 system. Happens every time you select a process with a different priority than the currently selected one.

---

### Post by shubham1 on 2012-01-02
> **ronacc said:**
> just go ahead and report the bug on launchpad , that way anyone having the same bug can add themselves to it .

once filed post the bug # here so people can find it easily .
can you help me to submit bug i have never done before i might face problem so i will ask for problem here

---

### Post by ronacc on 2012-01-02
Hmm this one may be a hardware issue then , from the other thread we have several 32 bit users having the bug and none yet not having it and myself and 2 other 64bit users not having it , on my 64bit sys I updated this AM just before I tried it .

---

### Post by ronacc on 2012-01-02
> **shubham1 said:**
> can you help me to submit bug i have never done before i might face problem so i will ask for problem here

sure , we will help

---

### Post by fabricator4 on 2012-01-02
Confirmed for 32 bit 12.10 alpha on my test machine (Celeron 2.8Ghz)

Every time I select pulse-audio with the up or down arrow I get this error.

Chris

---

### Post by collisionystm on 2012-01-02
Not 32 bit... but.

11.10 64 bit.

Working good for me. No errors to report.

---

### Post by ronacc on 2012-01-02
> **fabricator4 said:**
> Confirmed for 32 bit 12.10 alpha on my test machine (Celeron 2.8Ghz)

Every time I select pulse-audio with the up or down arrow I get this error.

Chris

aha  , on my 64bit sys it shows the error ONLY on pulse-audio so file the bug on pusle-audio .

---

### Post by MacUntu on 2012-01-02
Got a second 64-bit system showing the bug.

Steps to reproduce:
1. Open the System Monitor.
2. Go to the 'Processes' tab.
3. Sort the processes by the 'Priority' column.
4. Select a process, then select a process with a different priority.

Doesn't happen 100% of time, but almost always.

> **ronacc said:**
> aha  , on my 64bit sys it shows the error ONLY on pulse-audio so file the bug on pusle-audio .

Please don't. File it against gnome-system-monitor:

```
ubuntu-bug gnome-system-monitor
```

You'll need a Launchpad account to upload the report ([https://launchpad.net](https://launchpad.net)).

---

### Post by ronacc on 2012-01-02
MacUntu  is correct file it against gnome-system-monitor .

---

### Post by shubham1 on 2012-01-02
the you should report it as i have reported my bug
please report it

---

### Post by shubham1 on 2012-01-02
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/910845](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/910845)
url of the bug secondly
[MacUntu]("http://ubuntuforums.org/member.php?u=164090") please report the bug as this bug comes to you and i am 32bit so you should report i cant

---

### Post by fabricator4 on 2012-01-02
> **shubham1 said:**
> [https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/910845](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/910845)
url of the bug secondly
[MacUntu]("http://ubuntuforums.org/member.php?u=164090") please report the bug as this bug comes to you and i am 32bit so you should report i cant

Done.  I've also added some extra information, as I found you don't need to use the up/down arrow keys to re-create the problem.  It happens if you select pulse-audio with the mouse as well.

Could 64 bit users look at this as failure to re-create the problem may have been because pulse-audio was not being hit during testing, the priority is not set the same, or some other factor we don't know about yet.

(Edit)  By the way you'll notice the system up time on that screen shot I posted above: 1 minute is all it took to figure out how to re-create it.

Chris

---

### Post by cariboo on 2012-01-02
I merged the two threads, as there doesn't need to be to separate threads for this issue. I also removed the solved tag.

---

### Post by scradock on 2012-01-02
> **fabricator4 said:**
> Done.  I've also added some extra information, as I found you don't need to use the up/down arrow keys to re-create the problem.  It happens if you select pulse-audio with the mouse as well.

Could 64 bit users look at this as failure to re-create the problem may have been because pulse-audio was not being hit during testing, the priority is not set the same, or some other factor we don't know about yet.

(Edit)  By the way you'll notice the system up time on that screen shot I posted above: 1 minute is all it took to figure out how to re-create it.

Chris

Yes, confirming that this is happening on 64-bit PP as well.

My process list has everything with Priority "Normal" except for pulse-audio ("Very High"). Any attempt to access that process line (mouse-click, up/down arrow) generates the warning about being unable to change the priority.

Once I have clicked on the p-a process, and dismissed the warning box, I get the same error message again if I try to shift to another process, which has another priority level.

If I dismiss the warning box, I can change the priority of p-a from "Very High" to "Normal" using the right-click menu - no error message appears. But I can't change it back again - the error message appears and the priority doesn't change.

So there might be two problems - 1) simply accessing the process line triggers the request to change priority, presumably to the same level as the LAST process selected; and 2) changing priority level from Very Hiogh to Normal works, but changing from Normal to Very High doesn't. These may be related, but could logically be separate issues.

So, again - this IS a problem on 64-bit systems, fully updated, not 32-bit only.

---

### Post by Paddy Landau on 2012-01-02
> **shubham1 said:**
> [https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/910845](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/910845)
Thank you. Now everyone who has the problem can go to the bug report and vote for it (the green text at the top of the report).

Would people please say which version of Ubuntu you are using if you get the bug? I'm using 11.04 64-bit and cannot replicate the problem.

---

### Post by fabricator4 on 2012-01-02
> **scradock said:**
> Yes, confirming that this is happening on 64-bit PP as well.

My process list has everything with Priority "Normal" except for pulse-audio ("Very High"). Any attempt to access that process line (mouse-click, up/down arrow) generates the warning about being unable to change the priority.

Once I have clicked on the p-a process, and dismissed the warning box, I get the same error message again if I try to shift to another process, which has another priority level.

If I dismiss the warning box, I can change the priority of p-a from "Very High" to "Normal" using the right-click menu - no error message appears. But I can't change it back again - the error message appears and the priority doesn't change.

So there might be two problems - 1) simply accessing the process line triggers the request to change priority, presumably to the same level as the LAST process selected; and 2) changing priority level from Very Hiogh to Normal works, but changing from Normal to Very High doesn't. These may be related, but could logically be separate issues.

So, again - this IS a problem on 64-bit systems, fully updated, not 32-bit only.

On 32 bit the priority can not be changed at all since the user is not a superuser.  This is probably as it should be.

Also, see my extra comments on the bug report: If you use top (sudo top) to change the niceness of the pulse-audio process to normal (0) then the problem goes away, even if you subsequently change the niceness back again (-20) then the problem can still NOT be created.

Chris.

---

