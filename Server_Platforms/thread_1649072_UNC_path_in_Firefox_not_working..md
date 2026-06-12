---
title: "UNC path in Firefox not working."
date: 2010-12-19
forum: Server Platforms
---

### Post by Coder68 on 2010-12-19
I setup Dokuwiki (local use only) and have done some testing.  The following works under Windows in IE and Firefox: (Firefox needed some tweaks to open local links. no errors in the console)

file://///192.168.0.150/images/test.jpg

But it does not work in Ubuntu. I get 
Firefox can't find the file at ///192.168.0.150/images/test.jpg

I have to use the locallink plugin, and several clicks, and this syntax for it to work in Ubuntu.  

smb://192.168.0.150/images/test.jpg

I hate having to open each link using several clicks and even more so, having to make two types of links in my wiki posts! (SMB:// does not work in Windows.)

192.168.0.150 is a WD NAS.  I will also be setting  up my software RAID 5 that runs on Ubuntu to hold data for clickable in links on the wiki as well.

What do I need to do to get Firefox/Ubuntu to be able to click on and use file://///192.168.0.150/images/test.jpg

Wirehsark shows NO PACKETS when I click on the link file://///192.168.0.150/images/test.jpg, so Firefox is not even trying to find the file!

**HELP!!**

Thanks,

Coder68

I have tried epiphany and it did not work either.  (No packets being sent either.) This seems to be a Linux issue.

---

### Post by Coder68 on 2010-12-20
I can open a file from FF with the open file, but using the same exact path in a link does not work.  WTH? 

Now for my rant:
I have come to the conclusion that I can't use Linux with any web based  LAN search engines. All the links use UNC paths, even when the item is  on my WD NAS which runs Linux. 

With browsers being used more and more as the interface to the world and the local LAN, Ubuntu needs to add some functionality here.  The lack of this functionality makes Ubuntu unusable in a corporate environment.  (Can't click on links using LAN search engines to view or save the files.) This is not a Firefox issue, as Mozilla provides a secure workaround. That workaround works in Windows, but does not work in Ubuntu due to limitations of the OS. You can't take over the world without taking over corporations! To start down that path, you need to work WITH Windows. Support UNC paths!

This is one area that Windows trumps Linux. :(

/rant

C68

---

