---
title: "How many people here with Gutsy have M$ Office 2k3 and AWN"
date: 2007-12-21
forum: The Cafe
---

### Post by radlations on 2007-12-21
I'm trying to convince myself that I don't want MS Office.

Although I actually have MS office installed and running fine on Ubuntu, I can't seem to add it to my AWN dock or Cairo Dock (some mysterious error that no one can fix) and it is driving me MAD.

So how many people here are able to to add a MS Office App launcher on their AWN or Cairo dock?

---

### Post by cawill on 2007-12-21
Whats the command that runs ms office?

You can probably find out by using the menu editor.

---

### Post by bailout on 2007-12-21
How are you running MS office in ubuntu? Is it through wine? I need office for work and it is one of the programs I still go to windows for.

---

### Post by AndyCooll on 2007-12-21
> **radlations said:**
> I'm trying to convince myself that I don't want MS Office.

Although I actually have MS office installed and running fine on Ubuntu, I can't seem to add it to my AWN dock or Cairo Dock (some mysterious error that no one can fix) and it is driving me MAD.

So how many people here are able to to add a MS Office App launcher on their AWN or Cairo dock?

In what way do you need convincing? :lolflag:

:cool:

---

### Post by Fixman on 2007-12-21
> **bailout said:**
> How are you running MS office in ubuntu? Is it through wine? I need office for work and it is one of the programs I still go to windows for.

I guess hes using CrossOver Office. That program rules, and can run the two most important programs on a computer: Office, and World of Warcraft (throught with wine functions best the latter)

---

### Post by radlations on 2007-12-22
Yeah Im using crossover. In order for MS Office 2k3 to work with Wine, I had to do some weird instructions which meant I had to make a thread and ask for help. So I chose the easy solution and got crossover.

Seems like if youre new to ubuntu WHATEVER you want to do, you have to do some research first.

So the question was "Does anyone here with Ubuntu Gutsy run MS office 2k3? And have it as a launcher on their AWN dock?"

---

### Post by teet on 2007-12-22
> **radlations said:**
> Yeah Im using crossover. In order for MS Office 2k3 to work with Wine, I had to do some weird instructions which meant I had to make a thread and ask for help. So I chose the easy solution and got crossover.


Off Topic:  The most recent version of WINE can now handle office 2003 without any weird tweaking.  Just install WINE and double-click on the setup executable.  Word seems to run well as does excel.  PowerPoint has some pretty major bugs.  You can't advance to the next slide in full-screen-presentation mode, but the last version of crossover I tried had the exact same problem.

-teet

---

### Post by Sordelka on 2007-12-22
Why would you need something from microsoft anyways...

---

### Post by radlations on 2007-12-22
> **teet said:**
> Off Topic:  The most recent version of WINE can now handle office 2003 without any weird tweaking.  Just install WINE and double-click on the setup executable.  Word seems to run well as does excel.  PowerPoint has some pretty major bugs.  You can't advance to the next slide in full-screen-presentation mode, but the last version of crossover I tried had the exact same problem.

-teet

Actually you're wrong, for some users Word wont even run. They get a "Microsoft office was not installed for current user, rerun the installation blah"

Theres a solution to it on the Wine database though.

---

### Post by frup on 2007-12-22
What have you tried doing, what is the command on the icon?

Does it run properly from your desktop? Have you tried maybe making a link to the launcher? Maybe a small shell script would be able to open it for you instead?

---

### Post by Soarer on 2007-12-22
> **radlations said:**
> 
Seems like if youre new to ubuntu WHATEVER you want to do, you have to do some research first.



Consider what you are trying to do, which is to run an application built for one OS (Windows) on an entirely different OS (Ubuntu).

Try asking on a Windows forum how to run the Linux version of Open Office on Windows. 

Yes, you can run the Windows version, but only because the developers are being kind to Windows users. There is no Wine or Crossover Office equivalent on Windows.

It is a touch unfair to say 'whatever you want to do', as you are doing something which would be impossible on any other OS.

---

### Post by radlations on 2007-12-22
I've solved the problem. I've tried a  bunch of methods(creating a link to the exe and dropping it on the bar, a bash script to run the exe, creating a launcher to the exe). None worked. 

What I did was I ran the Crossover Run exe and created a shortcut to MS Word. And then dragged that shortcut onto the dock. And it worked!

I will make a thread for this.

---

### Post by slimdog360 on 2007-12-22
nope

---

