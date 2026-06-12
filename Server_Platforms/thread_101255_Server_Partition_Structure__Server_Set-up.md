---
title: "Server Partition Structure / Server Set-up"
date: 2005-12-09
forum: Server Platforms
---

### Post by Jayson Wonder on 2005-12-09
I have 2 questions I'd like to ask as a newbie tryign to set up a server.

#1
Is there a detailed step-by-step guuide to installing and configuing a basic internet / intranet server. Primarily providing, HTTP, FTP, Windows File, TELNET, possibley mail services for my home / small business. I found 1 guide but it was a bit vague. Any help is really appreciated!

#2
I need to know what is the best partition / file structure for a server that will utilize some form of quota control. My reading shows me a few differnet suggestions. Who can reccomend the right, safe, secure breakdown for the directory / space configuration allotments or percentages perffered. Although I can say I will likey be using a 40 gig drive for my install.
 

/    
/boot
/var
/usr
/etc

adn what ever else should be considered.

Thanks in advance!

---

### Post by bluefrog on 2005-12-09
/       5 Gb
/var  5 Gb (http, mail... depending on how you configure your mail server)
swap 2xRAM
/home  the rest (will hold users' data and eventually mail depending on how you configure your mail server)

You will find people saying 5 is too much other not enough and so on....

have a look as well at
[http://www.howtoforge.com/taxonomy_menu/1/4](http://www.howtoforge.com/taxonomy_menu/1/4)

james

---

### Post by Koybe on 2005-12-09
Pay attention that you can't put /etc on a separate partition. It must be in /.

Anyway a separate boot partition for kernel testing could ba a good idea. Juste use something like 100-200 Mb. It'll be enough.

Swap shoudn't be two time ram if you memory is important. For example, 1Gb of would make 2 Gb of swap which is really too much. I personnaly think 512 Mb is sufficient in most of the case. You can go up to 1Gb if you want.

/var parition should be important as bluefrog told you. On a server this is the place for all de system varaible. So it depends mostly on which service your server will provide (Will you http have a database?). Mail, log, databases, www, dns and so on in there. Yep go on for 5Gb.

/usr partition... Yes why not, but (in my mind) it's not very useful to have it on another partition. Especially for a server.

If you're planning to use file sharing, with user authentication or access to personal folders, put /home on a separate partion and give it space matching your needs.

/ will be enough with 5Gb as he said.

You can have in mind making a small /tmp partition (1-2Gb) to separate it from the main system.

This is just my point of view... you can go on many discussions ont this point. ;)

Good luck.

---

### Post by alexxtasi on 2008-01-10
hi there (linux newby here...)
some years later!!!
if anyone still read this post....
is there a recommendation for the partition structure for a machine:
ubuntu server 7.10 as file server only (planning some simple samba) on a  6Gb hard disk?!!!!! (using external hard disks for storage...)
Or it's just too small for ever a samba server?
i was thinking of this structure

/           -> 1Gb
/swap  -> 512 Mb
/home  -> the rest...

is / too small?
should i create any /tmp or /var or its too much for just a samba?
any recomentations?

---

