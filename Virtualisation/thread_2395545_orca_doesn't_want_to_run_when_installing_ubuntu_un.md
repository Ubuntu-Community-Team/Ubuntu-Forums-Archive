---
title: "orca doesn't want to run when installing ubuntu under virtualbox"
date: 2018-07-03
forum: Virtualisation
---

### Post by computerlover2 on 2018-07-03
Hellow to you all!
Before answering, please take in account that I am as new to ubuntu as to this forum, so, to say, for one day.
My name is alberto, , I am totaly blind and, as I said before, I am new to ubuntu.
Some  days ago, I read an article that speaks about different operating  systems, there use in programming, advantages and disadvantages for each  of the major desktop operating systems(windows, linux and mac OS X),  here I heard for the first time about linux and its  distributions(fedora, opensuse, ubuntu, debian...).
I did'nt like  windows so much, so I needed to find an operating system that is more  accessible for blind poeple. Inspecting the list of features, I've found  ubuntu the most suitable for my needs.
The following days, I spent  the majority of my time reading about ubuntu and, for my surprise,  Ubuntu has a built-in screen reader?
After some searching, I came to  the thought of trying ubuntu out to see how grate(or not) it is, but, I  wanted to know how it works with out actualy installing it on my  computer, so, here the idea, to use a virtual machine, I choose virtual  box.
I downloaded the iso file from the provided torent, created a  new ubuntu virtual machine, mounted the newly downloaded disk image and  started the virtual machine.
After some time in witch I thought that  it crashed because it did't make any sound, some sound popped up, it was  like a bouncing sound.
I pressed alt+windows+S and, after some time,  my favourite voice(espeak) began to speak on my speaker. The sound was  at a very low volume and crappy, but after some time, I got used to it.
I pushed the button "try ubuntu" and, after the ubuntu desktop poped up, orca went sillent.
I tryed to press the orca shortcut again, but, orca didn't start.
I oppened the terminal and typed the following command:
$orca
The terminal pops up with this message:
"Something has hung. aborting."
After this failure, I tryed typing:
$orca -t
This time, espeak starts to guide me through orca setup process, but, assoon as the setup finishes its execution, the failure message appears on the console window.
Disperatly, I tryed to install the operating system on virtual box. During instalation, the orca screen reader works well, allthough it refuses to read some of the informations on the screen, with some help from sighted man, I managed to install it. After the instalation, when I enter the login screen.... the same aas when trying out ubuntu.
I am running ubuntu 16.04 LTS. Please help, I desperatly need it.

---

### Post by computerlover2 on 2018-08-26
Hellow again, forum members!
There is quite abit of time since my last post during wich I waited for your kind response. And, yet again I return, helpless to this topic.
I searched some topics on the forum with out being able to find any answer to my question. I also searched on google and, as expected, no result. Is my question two hard or ambiguous for anyone to answer? if yes, moderators, please notify me when you will see this topic through all those other topics.
Some time ago, I thought that the comunity is dead, noone posts new questions excluding spam bots. That was until today, when I discovered that the most recent post was two minutes ago.
Probably I should move this topic to virtualisation, but, I new nothing about this forum at that time of the first post's writing and I am also a complete beginner with ubuntu and a blind person, I thought that the best choice is to put it there, the only section that I new for sure that newbie questions are allowed there. Besides, if I would move it to virtualisation, you will ask me whether I have virtualisation support turned on in the bios settings, another thing that screen reader users can't use, the bios. note: I don't know how to move a topic from a section to another and, as far as the forums are concerned, excluding moderators, noone should be allowed to move topics around.
I also though, and continue to think until I see an answer, even an, I don't know, kind of answer, is that probably, you don't offer help and support for newbie questions anymore, anyway, It's my right to know whether this is the case.
Besides all of those, I managed to, somehow, mess up with the virtual box drivers, so that, when I try to run an ubuntu instalation iso, an already prepaired ubuntu virtual appliance or virtual box harddisk(vdi), after some seconds of booting, instead of the regular VM window title, the ubuntu guru meditation witch some critical error message appears on the screen along with two buttons "Ignore" and"close". When I press the "ignore button", the machine hangs with a vbox.exe is not responding message, but when I press the "close" button, the virtual machine terminates imediately. Can anyone find a solution to those problems?
As I don't know to attach files to posts yet, I will paste the entire log file here, if there is no message size limit.
there coms the log file in it's entirety.
containt of the "VBox.log" file(dropbox link):
[https://www.dropbox.com/s/xl3sfo95bneju8s/VBox.log?dl=0](https://www.dropbox.com/s/xl3sfo95bneju8s/VBox.log?dl=0)

Containt for the "VBoxHardening.log" file(dropbox link):
[https://www.dropbox.com/s/a6lufa2pr4yms8n/VBoxHardening.log?dl=0](https://www.dropbox.com/s/a6lufa2pr4yms8n/VBoxHardening.log?dl=0)
That are all my comments, regards and information for my problem, please help me, I really want to begin using ubuntu.

---

### Post by computerlover2 on 2019-03-08
I found a way to solve my problem. When I arive at a terminal, I must run "orca -r" before attempting anything else. Please note that this strange thing is happening only with my computer and  virtual box. Please mark this thread as solved because I don't know how.

---

### Post by slickymaster on 2019-03-08
*Thread moved to **Virtualisation**.*

---

