---
title: "Looking for a downloader program for windows/ubuntu"
date: 2024-04-11
forum: Security
---

### Post by hyperlinxe on 2024-04-11
Hi guys, I was wondering if anyone knew of a good downloader program for ubuntu, and for windows too ideally that has security in mind,
but of course also speed...my network is shared with lots of people and my download speeds are terrible. Apparently the the solution to this
problem is to use a downloader program, but I am worried about the security implications involved.

---

### Post by TheFu on 2024-04-12
It depends on what you are downloading.

I like to use a queue manager called "task spooler", then I can use whatever downloader I like and put them into the queue.  **curl**, **wget**, **yt-dlp**, whatever. I have them run starting at 2am local time using the **at** command.  Just put the list of URLs into a file and feed that file into my downloader that starts at 2am.  By the next morning, everything is there waiting for me.  Or I can add more and more items to be downloaded one at a time to the queue manager.

Task Spooler will run 1 task at a time or it can be configured to run 2, 5, 20 concurrently.  Generally, it is best to run 1 at a time to limit disk, network, and CPU contention.  Plus, after I download stuff, I usually want to do some other processing on it.  That can be added to the queue for processing either in order or later too.

Having things happen later, in an orderly fashion is one of the most powerful things that UNIX systems give us.  Master this and you'll get so much more power than a simple point-n-click user can ever achieve.

---

### Post by hyperlinxe on 2024-04-12
TheFu are you recommending that I download from websites automatically every day without even being present at my own compputer for security?

That doesn't sound like a very good idea to me : d

---

### Post by TheFu on 2024-04-12
How does you sitting at the computer help security at all?  I don't think it does, but what you download and what I download a likely extremely different. I'm not downloading programs, just data.

Data being downloaded isn't exactly a risk - well, not for non-Microsoft OSes.
If you are going to download anyways, that act isn't exactly risky if you use the suggested programs.  Now, if you use a web browser and do this with browser extensions, THAT is completely different and I'd consider it high-risk.  For things that I want and can only get with a full web browser that supports javascript, I'll run that browser instance inside a firejail container to prevent nasty things.  If I think the source is REALLY bad, I probably won't download it at all.  If I need to file, then I'll run a browser inside a "private" firejail container. That will prevent the file from ever touching any storage. It will be held in RAM until the firejail container is closed.  I do online banking this way too.  Every start of the private filejail container is like the very first time the program was run.

If you want to play with firejail to get an idea around the restrictions it offers, take a look around inside two different bash shell environments.
1) firejail bash
2) firejail --private bash

See what you can see and what you can run from both those bash shells.

Whether you choose to download an entire website is between you and the website.  Many will block you if they recognize an attempt like that.   I do automatically pull RSS feeds from a number of different places every few hours, around the clock.  RSS has specific format requirements.  The feeds are stored in my nextcloud server, so that information can be access from any client, anywhere I have internet.

I'm about the most paranoid person in these forums. Ask anyone.

---

### Post by hyperlinxe on 2024-04-12
The way that programs are designed to take advantage of people is first and foremost to hide what they are doing from the users.
If you step away from your computer, you are in effect accomplishing the first goal of people that use programs to take advantage of people.

Downloader programs are designed to help facilitate downloading from the internet, and to resolve the issues that typical download methods present to users

---

### Post by TheFu on 2024-04-12
> **hyperlinxe said:**
> The way that programs are designed to take advantage of people is first and foremost to hide what they are doing from the users.
If you step away from your computer, you are in effect accomplishing the first goal of people that use programs to take advantage of people.

Downloader programs are designed to help facilitate downloading from the internet, and to resolve the issues that typical download methods present to users

I take it you've never used curl, wget, or yt-dlp?  They don't hide anything.  wget and curl have been around over 2 decades.  They are used constantly, daily, to keep different parts of the internet working.  yt-dlp is newer, but nothing is hidden behind a GUI.  Anyone can grab the source code for each of these download tools and review it - or pay someone else to review it.  Feel free.  

I trust those 3 programs 1000x more than any browser that supports javascript and video playback. When I just want the information, I'll use either Lynx or have Wallabag grab the article to strip out all the bloat so I can read an article without it, in peace, later ... or archive it.  Wallabag uses pandoc, which is an X-to-Y document converter.  Converting a file/document using a tool that I control, not the source website, into a format I prefer is a great way to remove any malware.  The malware included in the source files won't be recognized and will not be included in the converted file.  There might be exceptions, but I've never heard of any that survived an X-to-Y conversion.  I have heard of Xa -to- Xb malware getting through, however.  Mainly with images.

---

### Post by hyperlinxe on 2024-04-12
Dude nothing you just said made any sense to me at all. I am a windows user of ubuntu. I want to find a windows program for ubuntu. You clearly don't get what I'm talking about here. Don't you know the giant flashing advertisements on the internet, ya know the internet for people that use microsoft windows, with all those downloader programs to help people solve the problem of downloading and download speeds, and like they're made for windows, I'm looking for one of those that will work on Ubuntu.

---

### Post by Rubi1200 on 2024-04-12
I think this might suit your needs:
[https://ugetdm.com/](https://ugetdm.com/)

Take a look at the Features page.

---

### Post by hyperlinxe on 2024-04-13
idk I think it sounds like something the chinese would make, maybe Ill just stick with firefox... I don't get why people make those things anyways

---

### Post by 14nd on 2024-04-13
all good advice you received ,but you shoot everything down...
what download manager are u using in windows ?

---

### Post by TheFu on 2024-04-13
> **hyperlinxe said:**
> Dude nothing you just said made any sense to me at all. I am a windows user of ubuntu. I want to find a windows program for ubuntu. You clearly don't get what I'm talking about here. Don't you know the giant flashing advertisements on the internet, ya know the internet for people that use microsoft windows, with all those downloader programs to help people solve the problem of downloading and download speeds, and like they're made for windows, I'm looking for one of those that will work on Ubuntu.

Linux is not Windows.   [https://linux.oneandoneis2.org/LNW.htm](https://linux.oneandoneis2.org/LNW.htm)  You will be disappointed as long as you think it is.

I've never seen that "advertisement, sorry."  MS-Windows didn't have an IP stack in the early years. Windows networking was really bad, actually.  

**wget** and **curl** run on MS-Windows, BTW.  They are clunky on that platform due to the terrible shell experience there. I do not know of any built-in queue manager for MS-Windows.  There's a tool built-into all Linux called "batch". It is part of **cron** and **at** that are used on your Linux computer all the time to keep the OS running and handle maintenance jobs.  I just prefer Task Spooler for handling my work queues.  I've been trying to lead you to the pond to drink, but I cannot force it.

If you want the MS-Windows experience, there's an entire OS that does it. A few people use it.  I run it about once a week for a few minutes too handle 1 specific job that I don't have a better solution on Linux, yet.  It runs a program from 2012 for me. I expect to keep using that program until I'm dead, worst case.

---

### Post by hyperlinxe on 2024-04-13
It's pretty simple guys...

Looking for a downloader program for windows/ubuntu

I'll stick with firefox

Why the hell would I use anything else? (there's no alternative)

---

### Post by 14nd on 2024-04-13
pls mark this as solved then 
God speed 
:D

---

