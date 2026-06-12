---
title: "Simple FW / HIDS (If there is such a thing?)"
date: 2012-05-14
forum: Security
---

### Post by computeratin on 2012-05-14
I went book shopping this weekend. But they're not all here yet. I need some help finding a starting point.

I'm building a project for my wife. I went and got her a descent used computer. I'm going to put 12.04 on it as the host. I'm going to turn her win7 install in to a VM. She will work almost exclusively in the VM.

The reason for this is that she needs it for work. She works at a small office with a very, very, VERY poorly maintained network. Basically, any win or even just general network security protocol you can think of has been thrown out the door. And their net is dirty. I know this for a fact b/c I stood over her shoulder and told her what to click for an hour.

I won't let her take her "real" computer to work and connect it to their network. My win security skills are above average. But, it's like trying to plug all the holes in a sponge. 

She's a win girl all the way. It will be simpler to try and build the machine in a way that she will use than trying to get her to change her ways.

I've been playing with UB in VMs for a year now. I'm starting to get a handle on a lot of the basics. But, there are two areas where I am still very confused. 

1) IP Tables

2) HIDS

So, I am trying to find out:

1) Is what I want do even possible

2) If so where do I start / Can you recommend so good apps?

I need a client / GUI of some kind that will listen on my outbound ports and tell me when a program is trying to connect and then give me an easy (preferably point and click way) to allow it to do so.

I've tried GUFW in 11.04. It does listen. But, unless I missed something there's no easy way to say "Allow". And I've tried manually inputting values from the stuff I'm reading in the interface to create rules. Evidently I'm not bright enough to just wing it, hence the books that are on the way.

I also need some sort of limited functionality HIDS. And I have no idea where to even start on that. All my research has led me fairly deep in to some pretty serious network protection stuff that is, quite frankly, over my head. 

What I need to find is a way to set up her host so that if an actual secuity breach of some kind starts to happen it will throw a message. It doesn't really matter what the message is. B/c at that point I will tell her just to turn it off and bring it to me. I'll keep a good back up image and just do a full restore if I'm not 100% sure what happened.

On the other hand I need something that won't throw a message every time an automated port scanner on her dirty work network pings her. If she gets flooded with too many messages she'll start to ignore them and then we really will have problems.

Is there any such animal?

Can you give links to configuration info?

I appreciate any any and all help.

---

### Post by Ms. Daisy on 2012-05-14
I don't know of any firewalls or HIDS that would do what you want.  

iptables is the underlying firewall in Ubuntu, and ufw is a front-end which attempts to simplify iptables (hence Uncomplicated FireWall).  Then there's GUFW which is a GUI for ufw. But iptables, ufw, and gufw all require that you open the appropriate ports before you need them. None of them throw an alert that you can click on to allow.  If you don't understand basic TCP/IP and networking traffic, then it will probably be a challenge to set up iptables, ufw, or gufw IMO.  There's a good tutorial [here]("http://ubuntuforums.org/showthread.php?t=1876124") which may get it working if she needs basic services.  But if she has a network printer/scanner at work then you'll have to do some configuring for the firewall.

There's a HIDS tutorial [here]("http://ubuntuforums.org/showthread.php?t=1477662") but HIDS are generally command line with no GUI.  So not a point-and-click kind of approach.

---

### Post by Ms. Daisy on 2012-05-14
So there's that ^^^ which directly answers your question.

I'd like to add this though:

So she'll work on the Windows 7 VM inside of an Ubuntu host, right?  You  can lock down the Ubuntu host, but if the Windows 7 VM is networked to  the malware-infested work LAN, then it will essentially bypass the  Ubuntu security settings.  Maybe you can revert to a snapshot after each  day of work. Of course that will erase any work she saves inside the  VM. 

What is your goal by putting a Windows VM on an Ubuntu host?

---

### Post by computeratin on 2012-05-14
Goal: Voice recognition / dictation.

A lot of what she does at work could be sped up greatly if she had a machine that she could talk to. She types 80 wpm. But, she also spends much of her day away from the desk / computer. So, she handwrites notes and then transcribes. Double the work. And she types faster than she writes, so it all takes longer.

The company is not going to pay for anything that has no more purpose than to make her life easier. I could get her a tape recorder. But that still only fixes 1/2 the problem. If I set this up correctly I can save her even more time because she can just speak directly in to any document that she wants to create.

I researched *nix voice recognition. It didn't look very promising. But, Dragon Speak works great. In a perfect world the people she works for would hire somebody that has 1/2 a clue to admin their network and clean it up. But, that's not going to happen. And I'm not going to let her take her $2000 "real" computer and intentionally connect to a known dirty node everyday.  

I found a really good machine at the pawn shop. I got it for about 25% of retail because it was so jacked up and full of nasties that the previous owner dumped it. I took it to bare metal and am starting over from zero.

I will not set it up to directly connect to her work network. No file / print sharing etc.

But, she needs a way to get the stuff from her machine to her work machine; which will be e-mail.

However, that means connecting to their wi-fi; which I know for a fact has a worm in it.

I'll let UB handle that connection. 

I'm not too awfully worried about the file transmission vector since everything will go through web mail and be scanned at both up and down loading.

I just have to figure out a way to keep her win7 install safe from a worm that is only god knows how entrenched and has called out to / downloaded only god knows what.

So, reverse the roles of the machines. Right now on the "real" computers doze handles the connection to the home (CLEAN!) router and UB piggybacks in a VM to handle the internet and protect doze.

Now I need to connect her to a known DIRTY node. I'm going to use VMplayer on this project and use their Unity feature to integrate the two OS's in to a single desktop. The only thing the VM will handle is office / Dragon / good tight win security. I'll set the host and the VM to have a shared folder. Everything else will be UB w/ a win7 theme laid over it.

I'm hoping that from her perspective she'll never know the dif.

---

### Post by Ms. Daisy on 2012-05-15
Obviously  you have put a lot of thought into this.  From what you describe, it sounds like she will need to move files from work to her computer & back daily.  She'll use the clean windows computer at home to do the work and she'll use the other computer with the VM to connect to the work network. So the home computer will never be connected to the dirty work network, but it will see documents emailed to & from the work network, right?  How will you prevent moving infected files from the dirty work network to your clean computer at home?

---

### Post by computeratin on 2012-05-15
Actually her "real" machine will never come in to contact with any of her work product. That's another point to this project. To be able to seperate the two from each other, but still give her everything that she needs to do her job.
 
She has been in her industry for 15 years. She has a lot of custom file templates (letters, inventory, etc.) in her "real" machine that could also make her job a lot easier.
 
So, I'm going to use VMware to export her windows 7 installation to a UB host. I'll go back and strip anything personal out of the VM and leave the business stuff. Then I'll clone the drive to an image on my USB back up drive. 
 
If the VM gets corrupted I can restore it several ways. If UB gets corrupted I can restore the image. Then she can recover anything she was working on from the work e mail account. Worst case senario she looses anything in the VM that she hasn't mailed to herself yet. And I can always use an incremnetal back up program (know a good one?) that I can run a couple of times a week. Then she'll only lose from last back up.
 
And, if the image gets corrupted she'll still have clean copies of all of the templates on her "real" machine.
 
Also, I'll set it up so that the VM is NAT only. Then I'll go in to the VM and turn off the network connection. That way there will never be a direct connection of any kind between the VM and the dirty node.
 
Every couple of days (when I back up the system) I'll re-enable the network connection and get all the win side security updates on the clean router at home. But, that means that I'll also need a way to know if UB has been corrupted so that it doesn't bring anything home and spread it through the router. That's not too much of a concern right now as there is zero networking of any kind going on at home. But, as I dig in to my books that will change and I'll have to loosen up the router a little bit to let things run that are currently turned off.
 
I know that the plan is not fool proof. But, I've built as much redundancy and compartmentalization in to it as I can think of.
 
My concern is that the office network is a Frankenstein hodge-podge. When I stood over her shoulder I didn't really attempt to dig in to their network very deeply. I just had her check endpoint stuff. It was totally trashed. And she has a new horror story almost daily about something computer related.
 
Part of their net may well be *nix. I know they have a server, but no idea what it runs on.
 
My fear is that they have *nix in the mix and are full of *nix bad stuff and win bad stuff.
 
So, while UB is protecting the VM from the worm I need to figure out how to protect UB from the worm as well.
 
And this is the first project I've ever built for intentionally connecting to a dirty node; kind of goes against my religion. I know best practice / how to create a clean setup from scratch / what to implement to most likely keep the bad crap out of a known clean system with a windows host.
 
I'm still new to keeping *nix bad stuff out of an "actual" system. I can keep it out of a specific use (web surfing) UB VM with a win host with each performing various complementary security functions, but this is getting in to an area that is not my strong suite.

---

### Post by computeratin on 2012-05-15
So, I guess the best way to summarize is to say that I need:
 
1) an easier way to admin the firewall. I'd like to set it to deny all then only open whatever it is I actually need.
 
2) A monitoring package that will throw an error message on a probable UB system corruption so that she can shut it down and I can restore the clean image.

---

### Post by computeratin on 2012-05-15
3) Last but not least: A good backup program that can both backup / restore / clone an entire disk at the sector level and do incremental back ups as well.

---

### Post by JKyleOKC on 2012-05-15
A few messages back you expressed a worry about "*nix bad stuff" making its way into your home machines. While it's true that bad stuff does exist for *nix -- the very first computer worm ran on a Unix network -- it's also true that little, if any, of it is actually out in the wild these days. The reason is simple: Windows offers so much more opportunity for the bad guys to profit, that they don't bother with other systems.

As for preventing outbound traffic of the "call home" variety, the built-in iptables package can be set up to deny all outbound traffic. Of course, that prevents Email and web access, but you can open ports to permit those. You can restrict outbound Email so that only a few known addresses will be allowed. Web access is a bit more tricky, unfortunately.

I get the impression that you're looking for something similar to the Windows firewalls ZoneAlarm or Tiny Personal Firewall, both of which allow pop-ups to ask permission for outbound traffic to previously unknown addresses. It's undoubtedly possible to create such utilities in Linux, but I don't know of any, and the standard approaches don't work quite that way. 

It would be relatively easy to force iptables to reject such attempts, and log them; you could then set up a "cron job" to check the log periodically (as often as every minute if you like) and do a pop-up report. However a one-minute delay between the attempt and the pop-up might well be far too long for your wife to accept!

Creating a nightly snapshot of the VM would certainly help in the backup area. Since the entire VM actually consists of just two files (plus any snapshot files) they could be backed up quite easily, and if the VM is "saved" rather than "shut down" at quitting time each day, they can easily be moved from one machine to another (using save will also eliminate the long start-up delay of Windows). I use VirtualBox rather than any of VMWare's offerings (I started with VMWare but found VirtualBox much easier to use) so the details undoubtedly differ, but I've moved entire VMs from one box to another while saved, and it can even be done with command-line scripts quite easily!

Hope this helps. I know the kind of problems you're facing; the only machine running Windows that's in daily use here belongs to my wife!

---

### Post by computeratin on 2012-05-15
You actually bring up a point on which I need clarification:
 
I understand that worlds of *nix bad stuff and win bad stuff are 1000% dif.
 
I know that there is *nix bad stuff.
 
I know that compared to win bad stuff that it is few and far between.
 
I know that UB was built with security in mind and that there is really not all that much for an end user to do. (All I do is set to deny all then *try* to open what's needed / install the default apparmor profiles / install the ArpOn daemon / secure my browser.)
 
But, here's the point that I'm unclear on:
 
What little *nix bad stuff there is: How much is automated and how much is manual?
 
I know that at my current skill level I'm not capable of building a box that could completely lock out a compentent butthead actively trying to break the box. I also know how to keep a low profile. In 30 years of win use I was never "cracked". (Infected is another story). I'm not really worried about some "elite hacker" trying to crack her little dictation machine.
 
I'm more concerned that they make have cracked her work server and what they left behind is capable of crawling out without manual input.
 
If that is not the case then I'll just take my usual security precations / stick with redundant back ups and not sweat it.

---

### Post by jerome1232 on 2012-05-15
AFAIK, the only legitimate threats right now are to Linux servers running services witch can be exploited. Particularly things such as VNC, SSH, Apache with some poorly written PHP scripts on the pages, and others.

One threat is a rootkit, but these generally require that your machine first be exploited by some other means, and someone usually has to actively install and configure the rootkit, meaning a live person is actively working to crack your machine.

Have you browsed through the stickies in this forum?

HIDS
[http://ubuntuforums.org/showthread.php?t=1477662](http://ubuntuforums.org/showthread.php?t=1477662)

General Ubuntu Security
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

AppArmor
[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

---

### Post by JKyleOKC on 2012-05-15
So far as I know, there's none of the *nix bad stuff out loose in the wild. Browser exploits do exist, however, and might easily lead to bad stuff being downloaded behind the curtain. The good part is that these would only run on Windows and could not damage *nix systems.

A distinction between "manual" and "automated" is difficult to make. A very large part of the Windows bad stuff these days depends on social engineering; it tricks someone into clicking a link, which is "manual" but everything after that is "automated."

I'm told that if you set up AppArmor properly, it's almost impossible for any of the automated stuff to propagate. However I deal with extremely sensitive information for my customers (i.e. database recovery of medical practice management programs) and have not yet felt any need to enable AppArmor. The one time I was invaded in the past 10 years resulted from my own misconfiguration of a backup program, coupled with storing a few passwords in a plain-text file; I caught it within an hour or so, backed up my data and VMs, and reformatted completely. No firewall would have protected me from that fiasco.

---

### Post by computeratin on 2012-05-15
> **jerome1232 said:**
>  
Have you browsed through the stickies in this forum?
 
HIDS
[http://ubuntuforums.org/showthread.php?t=1477662](http://ubuntuforums.org/showthread.php?t=1477662)
 
General Ubuntu Security
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
 
AppArmor
[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)
 
Yes, and a lot of it just makes no sense.
 
I couldn't code my way out of a wet paperbag with a blowtorch and a bulldozer.
 
I'm a GUI guy all the way. I've been on win for 30 years. And things are just so bleeeeeeeeeep dif. I'm used to having to check a box and maybe, once in a while, having to copy and paste something from a reputable source in to the cmd prompt.
 
Also, every box I've ever had before was cheap and was doing good just to be able to run windows. Now I have a totally awesome box that can run the host and 4 VMs no sweat. So I want to start teching myself all this stuff I've been missing out on.
 
Not only were my boxes cheap, but I also never had more than one at a time. So I would hack the box all to pieces and rip all of the network stuff out of them. Why open holes for stuff I'm not using? (And it makes the box run faster.) By the time I was done all it would do is establish a NAT connection and talk on port 80. Everything else was locked down. And for years that kept crap out of my system. Now it won't. So for the last year I've been using self configured specific use UB VMs to web surf and protect my win install from the net.
 
But now, not only can I run a host and 4 VMs on my "real" computer; so can my wife.
 
Plus I have an two old junk ones to play with and the descent one I just bought her.
 
So I went and ordered a lot of begginer guides on things like shell scripting and networking becuase all the info I found on the web was either way, way over my head or so basic I already new it. (All the books I picked up are like self study guide / lesson plan / project / teach yourself.)
 
In the mean time though I need to get this project off the ground b/c the wfie really needs it for work.
 
So the question becomes (for those who know far more): With what I've described, will the usual end user stuff that I've been doing to protect my UB VMs be enough in this case or am I getting in over my head and need to seriously up my skill level before I can pull this off?

---

### Post by computeratin on 2012-05-15
Disregard that last question. Re-reading this thread and looking again at some of the threads that have been linked to I think it's already been answered. 
 
As I understand it: Even if her server at work is *nix and not win and even if it has been rooted the root kit cannot "crawl out of" the server "all on its own".
 
And the worm would be written to propigate in a win environment.
 
So I just need to take all of the above described precautions to protect the win VM.
 
I think good basic UB security precautions will be sufficent in this case.
 
I'm going to mark this one as solved as the main issue has been clarified for me.
 
Then I'll open two more. One about the firewall here and one about backups over in general.
 
Thankx for the help.
 
:)

---

### Post by jerome1232 on 2012-05-15
> **computeratin said:**
>  
I couldn't code my way out of a wet paperbag with a blowtorch and a bulldozer.


Love it!

I'm not sure what steps you have taken, but on a desktop the biggest vector for attack is via exploits in your browsers Flash and Java plugins. A big step is firstly enable the default AppArmor Profile for Firefox (demonstrated in AppArmor sticky). You might want to visit this [HOW TO CONFIGURE NO SCRIPT]("http://ubuntuforums.org/showthread.php?t=1912426") Sticky. I personally just use Addblock+, Ghostery, and WoT addons for firefox, noscript was to much work for me.

---

### Post by Ms. Daisy on 2012-05-16
Am I the only one here concerned about sharing files between the Windows VM in wife's computer & the infected server at work?

---

### Post by JKyleOKC on 2012-05-16
It looks like computeratin has addressed that concern already and his major concern is about infection/invasion leaking through from an infected VM to the rest of his home system. 

It's pretty much a "given" that the VM will get infected on a daily basis thanks to the server at her workplace, but he plans to deal with that at the VM level, possibly through the use of snapshots.

---

### Post by computeratin on 2012-05-16
Well, in so far browser security goes: I've got that nailed. I could probably write a sticky on that. 
 
I went to [panpopticlick]("http://panopticlick.eff.org/"): With my anonymity protocols in place my browser finger print is like one in 50K browsers in their sample. When I dropped my shields (so to speak) and let them do a "real" scan of my browser I was unique in their data base.
 
I've got so many tools in my FF it's not even funny.
 
But see, that's the biggest dif between win and *nix. I like to use this anaology: It's like being a mechanic. I don't have to know how to build a water pump from scratch. I don't have to know how to make a screw driver either. Because in win somebody has already done all that work for me. All I have to do is understand the concept that the water pump needs to be changed (say, blocking LSO's) and go get a screw driver (Better Privacy) that will do it for me. In that way FF is still very much like working with a win system as it is GUI driven with more pre-built tools than you'll ever need. But, with *nix not only do you end up, at the very least, having to take a bunch of prefabbed parts and making your own water pump. But a lot of times you have to make your own screw driver too, so you can build the water pump.
 
Want to defrag my page file? Want to scan the ADS? Want to take a look at what's going on in the HAL or the HIVE? Want to dig something nasty out of a null value in the registry? Want to create new custom features in the LGPE? Want to whatever on and on and on; somebody reputable, somewhere has probably created a tool to do it. I didn't need to understand how the screw driver was made, just how to use it.
 
There are thousands of tools for FF. And I've got dozens of them!
 
But, at this point, with *nix I don't know enough about the engine yet to even know if I need a screw driver or a cresent wrench. Much less how to make either one. That will change in time. I'm hard headed. I'll figure it; with some help. :)
 
In so far as virus transmission goes: 
 
1) The potentially infected work product will never come in contact with her "real" box. (No transmission possible.)
 
2) When she is at work the NAT connection inside of the VM will be turned off. (The worm can't crawl out of the UB host and in to the VM on a disabled connection.)
 
3) All materials generated in the VM will be dropped in to a shared folder on the UB host. (Clean materials.)
 
4) UB will then handle the connection to the infected wi-fi node. (Will not catch win coodies in the host.)
 
5) Materials from work to the VM will be transmitted via web mail. (This is the biggest potential hole, but the best I can do under the circumstances. At upload to yahoo NAV will scan it. On DL to the host ClamAV will scan it. Before being opened in the VM KAV will scan it. The VM will also have all of my custom security tools and tweaks that are implemented on her "real" box; like deep registry and LGPE hacks, sandboxes, registry virtualization and on and on. This is NOT a 100% gaurantee that the VM will not get infected. But, what else can I do?)
 
6) Lots of back ups of lots of types: A remote clean copy of the VM. A remote clean image of the entire disk. An incremental back up of the entire system. VM snapshots. (When something gets through the maze to the center she's going to lose some work product. I'll just have to drill it in to her to back up often and keep redundant copies.)
 
7) When the VM is at home (on a clean node) I will re-enable the NAT and get all of the security updates for it. (Since the UB host will handle this connection and cannot catch or spread win coodies then it should not infect the router at home. Since there is zero networking at home as long as the router is clean then nothing is crawling around at home. I'll just have to make dang sure the VM is in clean state before I do it. For that I'll prob do something like boot from a KAV *nix disc and scan the whole system.)
 
Did I miss anything?

---

### Post by JKyleOKC on 2012-05-16
> **computeratin said:**
> But, with *nix not only do you end up, at the very least, having to take a bunch of prefabbed parts and making your own water pump. But a lot of times you have to make your own screw driver too, so you can build the water pump.

..(snipped)..
 
But, at this point, with *nix I don't know enough about the engine yet to even know if I need a screw driver or a cresent wrench. Much less how to make either one. That will change in time. I'm hard headed. I'll figure it; with some help.It's not quite as bad as it looks to you right now. There are literally thousands of pre-built tools available in *nix-land too, just not as widely known as in the Windows world. Many of them do require a bit of customizing, since *nix comes in so many different flavors, but as you pick up more knowledge about the system you'll discover the simplest ways to do things.

In Windows-land, one of the most versatile tools (in older times, anyway) was the batch file. It made creation of your own custom tools quite easy, and led to a number of special tool-making tools to simplify the process even more.

Something quite similar exists for *nix systems: the shell script. It's a text file that contains a sequence of commands, exactly like the Windows batch file. However it has a lot more power, once learned, than did the batch file. In fact, many of the standard system tools -- such as most of the boot-up process -- are simply shell scripts! And while these scripts are written in a programming language, that language is much closer to everyday activity than are the more widely known programming languages such as C or Pascal...

In fact, when I set out to create a new tool for myself as a shell script, I first do the job from the command line, one step at a time, and then haul up the command history file (~/.bash_history) in a text editor, copy out the sequence of commands, and paste them into a new file that becomes my script. It doesn't get much easier than that.

You have 30 years of experience with Windows, which takes you all the way back to Win 1.0 days. Don't expect to become equally comfortable with any *nix system overnight, but it ought not take another 30 years to reach the same level of confidence. While *nix isn't Windows, the systems are similar enough in many respects for your knowledge to apply in general. Only the details will differ -- and you're on the right track to learn those differences in a hurry.

One of the biggest differences, in fact, is that the "Unix style" is based on creating lots of special-purpose programs, each of which does one job but does it very very well, and then stringing several of these together to do a bigger job. Many of the more popular Windows tools attempt to do many jobs within one program, by means of multiple options.

For example, consider the problem of eliminating duplicate lines from a text file. In Windows, you might do this by loading the file into a general-purpose editor such as UltraEdit, setting the program sort options to "unique", sorting the file, and saving it back (or optionally to a different file). In *nix, you could use a sequence of commands such as ```
cat thefile | sort | uniq >newfile
```all typed on one line to get the job done in less time and without loading up the entire general-purpose editor. And if you needed to do this often, you could create a file like this:
```
#! /bin/bash
cat $1 | sort | uniq >$2
```Save it as MakeUnique, set it to be executable, move it to a location in your path such as ~/bin, and then use it by typing ```
MakeUnique oldfile newfile
```
The books you've ordered will probably help a lot. And just yell here any time things seem confusing -- we're always happy to help.

---

