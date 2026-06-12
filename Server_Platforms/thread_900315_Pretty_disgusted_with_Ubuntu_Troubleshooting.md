---
title: "Pretty disgusted with Ubuntu Troubleshooting"
date: 2008-08-25
forum: Server Platforms
---

### Post by Just4Fun20 on 2008-08-25
I really hate windows.  Ubuntu is the best Linux distribution but it sure is weak when there's a problem.  

I've posted two requests for help and received no responses.  I see two huge holes in the "support" structure.  

1)  Versioning - trying to find the right troubleshooting information, for the right release, is very difficult.  You can find what you want but it's for two releases back and things may have changed.  

2)  Logical troubleshooting guides.  Something along the lines of:  It's broken...  Start here.  Here are some basic steps to get started, some diagnostic tools and some basic terminology.  

I'll start with networking.  A simple walk up the stack would be nice.  How do you determine a card / chipset is installed and recognized with the proper driver?  What are the basic steps to verify the TCP/IP stack is operating?  What are the more complex tests that can be run?  

Such guides must have versioning information.  You know, this guide has been verified to work with Hardy Heron.  

I'm not trying to be difficult but "dumb" or not properly searched questions get ignored or criticized.  However, it's pretty hard to search without the proper terminology.  Much of the terminology or commands are unique to Linux and someone could know other platforms (Windows) quite well and yet have great difficulty with Linux.

Simple troubleshooting guides would get people pushed in the right direction and give them a base to get started.  Ideally these would be in the "sticky" section of each forum or at least a pointer in the sticky section.  

If I'm missing something I apologize but I honestly feel some basic, fundamental troubleshooting documentation would dramatically reduce the forum traffic and the number of repeat or basic posts.  

Also, I tried on something like this for MythBuntu awhile back (in regards to remote control troubleshooting) and the level of interest was so depressingly low that I got the feeling I was the only one that cared about it.

---

### Post by ilrudie on 2008-08-25
Some useful networking commands:
lspci | grep [e,E]thernet # list detected ethernet controllers
ifconfig -a #list config info for all interfaces
ping #ping something
traceroute #give me the route packets took
netstat -rn #routing tables
tcpdump #packet sniffer, must be run as root
wireshark #same as tcpdump but with nice GUI
nslookup #lookup ip addresses from dns

Basic troubleshooting
1) check physical layer (are the cables plugged in, are lights lighting up, etc...)
2) can I see the interface in ifconfig? does it have an ip address? Lots of errors? No hardware address?
3) can I ping anything? by name and by ip(localhost, something on your LAN, something on the internet?)
4) are names resolving with nslookup if I can't ping by name?
5) do I have a default route in netstat -rn?  Is the gateway correct?
6) does traceroute show the connection stopping before it reaches the destination (blocked by firewall, ISP blocking, ISP down)
7) finally tcpdump can be used to see all the network traffic.  You will probably want to filter it.  Wireshark is a gui packet sniffer that may be easier to use.

Kindof a quick overview.  If one of these tests fails you will have a better idea what to search online for.  You can use the output from lspci to narrow the search results if you think its hardware related.  It takes time and practice to learn what to look for because with networking (and so many other things in life) the devil is in the details.  Don't give up.

Also regarding your assertion that Linux has wierd commands and terminology you have it backwords.  Windows has odd commands and calls things by weird names.  Unix/Linux/BSD/OS X all have a similar set of commands and terminology.  Most of the commands listed above work on the above mentioned systems with little or no modification.  If they fail you can always check the man pages to find out how to run them properly.

---

### Post by de0xyrib0se on 2008-08-25
Surprise: [http://help.ubuntu.com](http://help.ubuntu.com)

How about them apples...

---

### Post by Just4Fun20 on 2008-08-25
That's an excellent reply.  

Believe it or not I've been fixing things for decades and I'm very good at what I do.  The frustration is knowing the proper tools to use.  

For my network problem I followed exactly those steps (although several days ago).  I did have a light.  I used ping and ifconfig, etc.  Those are pretty standard.  The piece I needed was the command "sudo lshw -C network".  This showed no MAC address (well, all FF's) which indicated a driver problem.  I took the easy way out and just used a more generic ethernet card.  :-)  

Am I crazy or is there a need for guides, such as what you wrote?

---

### Post by Just4Fun20 on 2008-08-25
> **de0xyrib0se said:**
> Surprise: [http://help.ubuntu.com](http://help.ubuntu.com)

How about them apples...

Thanks for the link, but been there, done that.  They are excellent installation guides.  They are not nearly as good for troubleshooting and are arguably poor in that regard.

---

### Post by WeeWoh on 2008-08-25
> Also regarding your assertion that Linux has wierd commands and terminology you have it backwords. Windows has odd commands and calls things by weird names. Unix/Linux/BSD/OS X all have a similar set of commands and terminology. Most of the commands listed above work on the above mentioned systems with little or no modification. If they fail you can always check the man pages to find out how to run them properly.

I'd rather like to counter that one about weird commands in Windows. Linux commands seem to be a lot weirder than Windows commands.

On the theme of Ubuntu troublehshooting read [this]("http://linux.oneandoneis2.org/LNW.htm") or [this.]("http://jjtcomputing.co.uk/Linux_Help.html")

With your network problem have you tried ndiswrapper? Much as it specifically for wireless drivers, it apparantly will work for most network devices.

---

### Post by mbeach on 2008-08-25
Regarding the lack of replies, its possible as you point out that because of the lack of interest, you are among the early adopters sorting out some of the problems.  Mythbuntu is by no means mainstream (imo), so its possible nobody reading these forums has had your particular problem.  I have a difficult enough time finding resources on Win Media PC when something goes astray with it ie: trying to get it to fill the screen when attached to HDTV in full screen mode.  

Have you posted what you have tried, all the steps involved, which problems you ran into, which versions were used etc in a clear howto?  I only ask because to make these things better it will depend on folks like you that have been through the process and now got it working (or attempting to).  When someone goes through the trouble, typically, I've seen it become that sticky which continues to be updated for each new release if need be.  Its not a perfect support system, but its pretty good.  

The only other thing I'd point out is that you may have to wait a few days for a response, especially if its not a common problem - there are some wicked smart people in these forums, but they may not be scanning posts every day.  Give it some time.  I've paid for support which cannot provide the type of response times that many people get on these forums. 

If you need a 'walk up the stack', there is probably not a tremendous amount of difference between 8.04 and 7.x etc (complete guess on my part I'll admit).  Perhaps a decent Linux Administrator book would provide that info - its not knowledge many folks are going to be able to provide.  

I'll agree with you that it would be nice to be able to point someone to a 'wizard' or at least the flowchart which walked through the troubleshooting process and be able to solve every problem from the simple to the complex, then have it updated for every release.  I've yet to see it and I'm not holding out for it.  The terminology issue is one that many will struggle with, and will be present whether moving from Mac to Linux, Linux to Windows, Window to Mac .... its the learning curve.  I find this much like learning a new language - you know exactly what you want to do, but not knowing the functions in all the libraries off the top of your head, its tough - need the time/will to educate.  Same as switching (or trying to) from MS office to Open office, Photoshop to Gimp.  Even though a fella is quite capable in the area, the new software has differences.  

I find that if you know how to do it in Windows, then saying something like, "I use 'getmac' from the command line in WinXP, whats the equivalent commend in Linux?" works well.  Sure you'll get a few of the "this is not Windows" responses but it will surely help someone know exactly what you are after.  I'd say the quality of the replies here are quite good for being so open (especially after trolling around a bit on youtube video comments).

In the meantime, continue posting your problems, describing as best you can what it is (someone will fill in the terminology), and be patient.

---

### Post by Vadi on 2008-08-25
There is commercial support available for Ubuntu, just like with Windows. If you'd like quick and quality support, I'd recommend contacting that.

If you don't mind letting luck have it's course (it's usually good on ubuntu forums), can do a bit of digging yourself, etc., then stick with the free stuff.

---

### Post by ilrudie on 2008-08-25
> **WeeWoh said:**
> I'd rather like to counter that one about weird commands in Windows. Linux commands seem to be a lot weirder than Windows commands.

On the theme of Ubuntu troublehshooting read [this]("http://linux.oneandoneis2.org/LNW.htm") or [this.]("http://jjtcomputing.co.uk/Linux_Help.html")

With your network problem have you tried ndiswrapper? Much as it specifically for wireless drivers, it apparantly will work for most network devices.

I don't mean to seem rude to Windows users migrating over but Linux was not meant to be Windows-like.  Its a UNIX-like operating system.  It has a wide array of standard UNIX commands.  The new commands are made to be UNIX-like and they make pretty good sense.  If you learned Windows first I can understand why you would think they are weird but for those wanting a free UNIX-like OS its normal.  The UNIX CLI is so standard the new shell in Windows Vista/Server 2008 aliases most of the Windows commands to UNIX analog.  With that in mind you can make a .bash_aliases file that aliases all your favorite Windows commands to their Linux analog and then you won't have to learn all new commands anymore.  Make sure to source it from your .bashrc if it isn't already there.

---

### Post by windependence on 2008-08-25
> **Just4Fun20 said:**
> Thanks for the link, but been there, done that.  They are excellent installation guides.  They are not nearly as good for troubleshooting and are arguably poor in that regard.

What exactly was the problem you posted about and where did you post it?

Changing the NIC out is certainly what I would have probably done. It makes no sense to work half a day on something that costs less than $10 to eliminate the problem.

-Tim

---

### Post by zcubed on 2008-08-25
> **Just4Fun20 said:**
> < snip >The piece I needed was the command "sudo lshw -C network".  < snip >

I have a document that I paste all the commands that I might need in the future.  Thanks for that one.  I keep learning more and more.

---

### Post by Just4Fun20 on 2008-08-27
> **windependence said:**
> What exactly was the problem you posted about and where did you post it?

Changing the NIC out is certainly what I would have probably done. It makes no sense to work half a day on something that costs less than $10 to eliminate the problem.

-Tim

Thanks, to you and everyone else who replied to this thread.  

I posted my problems in the networking section of these forums.  I don't know if I know how to paste a link but it was here:  [http://ubuntuforums.org/showthread.php?t=896720](http://ubuntuforums.org/showthread.php?t=896720)  I came over to the server section with some Samba problems.  

It's working now, although at 10/100.  That doesn't matter since I don't have a 5E/Gigabit cable to the new location anyway.  

I suspect the problem was in the drivers.  The key seems to be that I got no MAC address back when I queried the adapter(s).  Certainly changing out the adapter was a quick, easy fix and I've a few adapters laying around anyway.  

Thanks again.

---

### Post by cariboo on 2008-08-28
I've worked for a couple of large multi-national computer companies and we have always checked the easy things first, due to the cost of down time. It would be great to diagnose a problem and repair it the right way, but unfortunately the cost of parts has gotten to the point where it is cheaper to just throw parts at it until it's fixed and never know what the underlying problem was.

Jim

---

