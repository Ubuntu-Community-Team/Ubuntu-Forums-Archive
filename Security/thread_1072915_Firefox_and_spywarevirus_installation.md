---
title: "Firefox and spyware/virus installation"
date: 2009-02-17
forum: Security
---

### Post by JrSprad on 2009-02-17
Hi, 

I'm new to Linux and I have a question that I'm sure has been addressed many different ways, but I haven't found specifically what I'm looking for.  

My understanding is that currently viruses and spyware aren't really much of a concern in Linux, but here is my situation.  I was browsing a website which I trust using Firefox.  I somehow clicked a link that I wasn't aiming for and ended up on one of those fake virus scanning sites that seems to take control of the browser by "running a scan" of the computer (fake of course), popping up a dialogue box saying that the computer may not be clean, and requiring me to click either "Cancel" or "OK" to close the dialogue box.  This is one of those sites that typically when you click "Cancel" doesn't truly cancel and which usually ends up infecting Windows with some adware/spyware/virus.

My question is can this type of site infect Linux with any adware/spyware/virus?  Do any features in Firefox such as Java or Javascript allow the installation of such malware in Linux?

Sorry to be so long winded and if I missed where this has already been addressed, but I'd appreciate any feedback.

Thank you.

---

### Post by bodhi.zazen on 2009-02-17
This is referred to as a browser hijack and the solution is to use adblock + noscript.

Nothing is "installed" although information is kept in your firefox profile (similar to storing cookies).

---

### Post by matteojg on 2009-02-17
1) For added protection you may wish to get the noscript add-on for firefox.
2) Never click on pop-ups in suspicious circumstances...better off just closing the browser, if that don't work then force quit.
3) If someone manages to download malware to your linux only system chances are it will be benign because:
   a) The vast majority of malware is written for windows.
   b) Files are not automatically executable on a linux system.

Using linux does not mean you have license to abandon common sense when it comes to safety: 
  Don't download, open, or run files from sources you do not know and trust.
  Don't log on with user privileges you don't need.
  Use strong passwords.
  Use sudo/su only when absolutely sure of what you are doing.
  Never launch a ground war against Russia.
  And never bet against a Sicilian when the wager is death.

---

### Post by JrSprad on 2009-02-17
Thanks for the replies.  

This brings up a few of additional questions.

First, if browser hijacking has taken place, how can I tell or better yet what can I do to clean up any files that may have been added/manipulated?  Is it as easy as cleaning out Firefox privacy files?

Second, how do you force a closing of the browser if simply clicking the close button isn't an option?  I'm know how to do this using Task Manager in Windows, but not sure in Linux.

And finally, if I use noscript, does this prevent Javascript/Java from running?  If so is this really feasible considering so many sites require these to run properly?

I try to be as cautious as possible when working on the web, unfortunately all the caution in the world isn't a 100% guarantee which is why it's nice to have a place like this where one can get advice when things don't go as planned.

---

### Post by bodhi.zazen on 2009-02-17
See this thread :

[How to Secure Firefox - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=671604") 

The problem is that there are things that are OS independent, such as java script.

NoScript blocks java, you then grant sites privileges to run java script, temp or long standing.

DNS poisoning is another method, although that is rare.

Easiest way to cleanse your firefox is to either delete ~/.mozilla (will delete cookies, book makrs, etc).

Unless you know java it may be hard to figure out how your browser was hacked.

The reality is security is not install and forget on any OS.

To kill an application, open a terminal and :

```
killall firefox
```

Or ```
xkill
```With xkill, click the skull and crossbones on teh firefox window.

Ther is a gui way, it is in the system meny somewhere (don't recall where).

---

### Post by JrSprad on 2009-02-17
Okay. I've got everything installed/working.  My last question is about deleting ~/.mozilla.  Should I just delete everything in the directory (including the directory itself) or some specific file in the directory?

Thanks again.

---

### Post by bodhi.zazen on 2009-02-17
Depends, do you have anything you wish to save ?

You may wish to export your bookmarks ;)

Otherwise delete away, then re-start firefox. 

You will need to re-install any extensions you wish to use as well (noscript).

---

### Post by tiggsy on 2009-02-26
This morning sometime I read a post somewhere about a binary post on twitter purportedly from google, which translated said "im feeling lucky" The post went on about how it was a historic incident, googles first ever post from its longheld twitter account, and meant this and that... 
so i thought i would take a look at the google page on twitter, and typed in the url twitter.com/Google into the browser.

When i got there I was taken to a page about twickie and when i pressed Back i ended up on scobleizer.com

Now whenever i do a search from the google toolbar i end up on that page, if i dont click on the G at the end. and even on google.com half the time i end up on the twickie page with the single back location: scobleizer.

I use my toolbar all the time and this is not helpful. how do i get rid of it. All the solutions i can find online relate to windows computers. this is a linux only computer. HELP

---

### Post by markharding557 on 2009-03-04
> **tiggsy said:**
> This morning sometime I read a post somewhere about a binary post on twitter purportedly from google, which translated said "im feeling lucky" The post went on about how it was a historic incident, googles first ever post from its longheld twitter account, and meant this and that... 
so i thought i would take a look at the google page on twitter, and typed in the url twitter.com/Google into the browser.

When i got there I was taken to a page about twickie and when i pressed Back i ended up on scobleizer.com

Now whenever i do a search from the google toolbar i end up on that page, if i dont click on the G at the end. and even on google.com half the time i end up on the twickie page with the single back location: scobleizer.

I use my toolbar all the time and this is not helpful. how do i get rid of it. All the solutions i can find online relate to windows computers. this is a linux only computer. HELPdelete ~/.mozilla and don't install any toolbars just use a search page instead.
adding a block list to the hosts file adds an extra layer of protection you can get one here [http://blocklistpro.com/download-center/view-details/blocklist-pro-blocklists-mirror/1501-hosts.zip.html](http://blocklistpro.com/download-center/view-details/blocklist-pro-blocklists-mirror/1501-hosts.zip.html).
copy its contents into your hosts file

---

