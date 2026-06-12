---
title: "Convince someone to use Ubuntu."
date: 2010-11-17
forum: The Cafe
---

### Post by ctult on 2010-11-17
Hi,
I might switch an entire school to Ubuntu.  There is only one reason that we are not going to use it:  it is not the completely most-used operating system in the world.  Is there any counter to that?:(

Thanks in advance,
CTuLT


EDIT: Another factor is that they need educational software that is easy to use for teachers and the kids with netbooks.  Their current software supports screen sharing, turning off and on monitors, showing their research (presentations, documents, etc...) on the projector, and managing homework.  Is there any tool like that?

---

### Post by wojox on 2010-11-17
The words **Free, Non-Proprietary, Easy Maintenance, Automated Patching, Support Options, and Reliable** come to mind.

---

### Post by thomas9459 on 2010-11-17
I found this article.

[http://www.wikivs.com/wiki/Linux_vs_Windows](http://www.wikivs.com/wiki/Linux_vs_Windows)

---

### Post by dnguyen1963 on 2010-11-17
> **ctult said:**
> Hi,
I might switch an entire school to Ubuntu.  There is only one reason that we are not going to use it:  it is not the completely most-used operating system in the world.  Is there any counter to that?:(

Thanks in advance,
CTuLT

Please see the thread about random freezes that many users are experiencing with Ubuntu before making the switch.  Most schools have older computers which can be problematic with 10.04 LTS.  I suggest that you test PCLinuxOS before making the final decision.

---

### Post by thomas9459 on 2010-11-17
I had many problems with 10.04 on my old Dimension 2400. But after I upgraded to 10.10, it all worked again.

---

### Post by ctult on 2010-11-17
> **wojox said:**
> The words **Free, Non-Proprietary, Easy Maintenance, Automated Patching, Support Options, and Reliable** come to mind.
I've used all of those.  They don't work.

---

### Post by InTheMarket on 2010-11-17
If you can put on all the standard stuff that windows has (open office, gimp, plugins for browser etc) it'll be user friendly enough once you remove their rights to do anything besides those applications. Nothings more user friendly than having minimal control over your system xD

---

### Post by laurenbanjo on 2010-11-17
Say how it's almost impossible for it to get viruses since not many people have it and no one really wants to make a virus for a small amount of people.

---

### Post by smeelkin on 2010-11-17
an issue with windows is that students aren't able to do a damn thing to make sure they dont do something wrong. in ubuntu, you could configure the user so they have some restrictions, while being able to do the basic stuff

---

### Post by smeelkin on 2010-11-17
oh, and this one: ITS FREE!!! Next time getting new computers you wont have to buy the Windows OS for extra money.

---

### Post by Mark Phelps on 2010-11-17
Two things you need to address BEFORE you do this ... seriously ...

First, are you going to be the sole person responsible for maintaining these machines once you switch them over?  IF so, you had better be up to that task.

Second, it is a bad idea to force ANYTHING on ANYONE.  Period. If it succeeds, they won't thank you; if it fails, the WILL blame you -- and quite rightly.

You would do a LOT better if you did the following:
1) Pick out one of the machines that is most typical of the whole set
2) Install Ubuntu (or PC Linux OS) dual-boot on that machine.
3) Find and install the Linux-equivalents of the apps the students and teachers need to do their projects
4) Do NOT install Wine or anything like it.  This will CREATE problems, not eliminate them.
5) Show the results (presuming all of this goes well) to select students and teachers -- to demonstrate how well it works.

There's nothing like a live demo to (1) win over the timid and (2) silence the naysayers.

And, horror of horrors, if it does NOT go well, you can restore the one machine you messed with and not have to endure the wrath of the entire school being out of business due to your desire to force them into using Ubuntu.

---

### Post by FatalKeystroke on 2010-11-17
If you want to counter how it's not often used, let them know about Samba and how most Linux desktop applications can work with a wider range of file formate than Windows could ever dream of, including Microsofts own formats. Mention what laurenbanjo said about there being fewer security threats (Although it's not that there are fewer just because of the smaller userbase [http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/#rpc).]("http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/#rpc")
As for things like screen sharing and all that, let them know about iTALC and let them know just how the X Window System works. As for turning off monitors, the following command would work:
```
sudo vbetool dpms off
```
switching "off" for "on" would turn them back on. you could run this command through ssh, though i'm not sure how you would do that for large numbers of computers without needing to retype it each time.
Also, let them know that it would be fairly easy to set up a central server with all the students home folders on it and then mount them via NFS. This would allow each student to have a COMPLETELY personal account (unlike my experience with my former schools network). I can get you some more and I'll be back.

---

### Post by SeijiSensei on 2010-11-17
> **ctult said:**
> I might switch an entire school to Ubuntu.

The first question I'd ask is why.  What is there about their current setup that causes problems?  Problems for whom?  What can't they do now that they could do if you switched to Linux?  What can they do now that they won't be able to do after you switch?  Who's going to train the staff (and maybe the students)?  Who's going to work with the staff to convert their current teaching materials and methods of doing things to Ubuntu?  

What happens when things go wrong?  Who'll be there for them today? Next month? Next year? Five years?

---

### Post by MrRichard on 2010-11-17
I agree with Mark Phelps post. Give the teachers a demo, and if they like Ubuntu, go all the way. Don't become a MiniMicrosoft and pressure people to use their programs :p

---

### Post by Tibuda on 2010-11-17
you are doing a disservice to linux by preaching it like that

---

### Post by JustinR on 2010-11-17
> **ctult said:**
> 
EDIT: Another factor is that they need educational software that is easy to use for teachers and the kids with netbooks.  Their current software supports screen sharing, turning off and on monitors, showing their research (presentations, documents, etc...) on the projector, and managing homework.  Is there any tool like that?

Hi, the Linux/Windows Software [iTalc]("http://italc.sourceforge.net/"). It works great - > iTALC is a use- and powerful didactical tool for teachers. It lets you view and control other computers in your network in several ways. It supports Linux and Windows 2000/XP and it even can be used transparently in mixed environments!
> 
TALC has been designed for usage in school. Therefore it offers a lot of possibilities to teachers, such as:

see what's going on in computer-labs by using overview mode and make snapshots

remote-control computers to support and help other people

show a demo (either in fullscreen or in a window) - the teacher's screen is 
shown on all student's computers in realtime

lock workstations for moving undivided attention to teacher

send text-messages to students

powering on/off and rebooting computers per remote
remote logon and logoff and remote execution of arbitrary commands/scripts

home-schooling - iTALC's network-technology is not restricted to a subnet and therefore students at home can join lessons via VPN-connections just by installing iTALC client


---

### Post by Khakilang on 2010-11-17
> **Mark Phelps said:**
> Two things you need to address BEFORE you do this ... seriously ...

First, are you going to be the sole person responsible for maintaining these machines once you switch them over?  IF so, you had better be up to that task.

Second, it is a bad idea to force ANYTHING on ANYONE.  Period. If it succeeds, they won't thank you; if it fails, the WILL blame you -- and quite rightly.

You would do a LOT better if you did the following:
1) Pick out one of the machines that is most typical of the whole set
2) Install Ubuntu (or PC Linux OS) dual-boot on that machine.
3) Find and install the Linux-equivalents of the apps the students and teachers need to do their projects
4) Do NOT install Wine or anything like it.  This will CREATE problems, not eliminate them.
5) Show the results (presuming all of this goes well) to select students and teachers -- to demonstrate how well it works.

There's nothing like a live demo to (1) win over the timid and (2) silence the naysayers.

And, horror of horrors, if it does NOT go well, you can restore the one machine you messed with and not have to endure the wrath of the entire school being out of business due to your desire to force them into using Ubuntu.

+1. I couldn't think of a better way than what Mark has mention. On top of that if the school have someone, teacher or student who are familiar with Linux will be an advantage. It is good to mention but not good to force someone down the throat.

---

### Post by FatalKeystroke on 2010-11-17
Have you considered perhaps just phasing it in over time? Maybe do a computer lab or two running Linux and go from there? I wholly support Linux, but I do agree with many of the arguments posed by the other posters...
A sudden COMPLETE switch would be a terrible idea. If you were to spread it out though, it would be more likely to succeed.

---

### Post by Austin25 on 2010-11-17
> **ctult said:**
> Hi,
I might switch an entire school to Ubuntu.  There is only one reason that we are not going to use it:  it is not the completely most-used operating system in the world.  Is there any counter to that?:(

Thanks in advance,
CTuLT


EDIT: Another factor is that they need educational software that is easy to use for teachers and the kids with netbooks.  Their current software supports screen sharing, turning off and on monitors, showing their research (presentations, documents, etc...) on the projector, and managing homework.  Is there any tool like that?
I don't see how "not the completely most-used operating system in the world" is a bad thing, as uniformity leads to vulnerability, whereas diversity leads to immunity.

---

