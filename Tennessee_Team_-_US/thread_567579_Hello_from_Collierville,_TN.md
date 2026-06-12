---
title: "Hello from Collierville, TN"
date: 2007-10-04
forum: Tennessee Team - US
---

### Post by klhoard on 2007-10-04
It looks like I'm holding up the west end of the state. . . I installed Ubuntu (dual boot w/XP) about two weeks ago and am slowly but surely working my way thru the rough spots.  
.
.
I'm pretty much a noob to Linux, but was hoping that I could ask my questions here and get some help.  
.
.
So far I've been able to learn some rudimentary command line stuff and  work my way thru installing the printer driver for my Dell A920 (Lexmark Z600) printer.  My next challenge is to get the four XP machines in my house to print thru the network so I don't have to boot back to XP in the afternoon when everyone gets home and starts homework.  I can see all of the XP machines in the File Browser, but the XP machines can't see me.  
.
.
I was also thinking of making a reference book for myself as I work my way thru the command line stuff. . . I'm looking to print out a one page info sheet on each command as I'm learning.  Perhaps using MAN command and re-directing to the printer?  However, if there is already a .PDF file that has all of the commands neatly formatted, I would rather use that.  Any suggestions?
.
.
Thanks in advance for any help!!
.
.

---

### Post by saxonjf on 2007-10-04
If you find a cheat sheet out like that for the Command Line, post it.  I would be interested myself.

MrMosier is going to be the most likely to help.  I know nothing about networking.

---

### Post by klhoard on 2007-10-05
.
.
I was able to pipe the MAN output for the LPR command to a text file and clean up the formatting in OpenOffice to a single page without much effort.  One shot with the 3-hole punch and I'm making my own reference manual from a leftover school binder!
.
.
If other people are interested, I would be happy to e-mail the files or post them somewhere so you can make your own manual. 
.
.

---

### Post by MrMosier on 2007-10-11
I liked this cheat sheet for unix commands. By the by, I use a static IP for my linux box to make file/printer sharing easier (I only have to point XP to 192.168.10.100 and install the printer - the IP will be whatever you assign your machine). One question I forgot to ask you...can your XP machines see each other?

[http://fosswire.com/wp-content/uploads/2007/08/fwunixref.pdf](http://fosswire.com/wp-content/uploads/2007/08/fwunixref.pdf)

---

### Post by klhoard on 2007-10-13
Mr. Mosier,

Yes, I finally got the networking thing worked out. . . one thing that Linux seems to be doing for me is making me learn more about the computer!!  I dug into the networking section of the book and figured out the difference between DHCP and Static IP - yeah, me!!   Now I'm working on learning Python.  
.
.
Funny you mentioned the .100 address, that is what I set the new printer (HP photo wireless) up as a static address.  I let all of the XP machines do their thing on the network and I do mine.  I installed Samba so the XP machines can see my Linux box, but I can't share files on the network since I can't figure out how to set a user name and password.  No real burning need to share folders with the family yet so I think I'll just leave that security hole plugged.
.
.
That cheat sheet is great!!  Thanks!!  Saved me alot of work!!
.
.

---

### Post by w4ett on 2007-10-13
> **saxonjf said:**
> If you find a cheat sheet out like that for the Command Line, post it.  I would be interested myself.

MrMosier is going to be the most likely to help.  I know nothing about networking.

Here is a culling from the official Ubuntu Handbook:

[http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9030259&pageNumber=1](http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9030259&pageNumber=1)

---

### Post by MrMosier on 2007-10-16
You can setup a username and password in order to access shares (this is the easiest way in my opinion), or you can setup totally anonymous shares using Samba (so a search on the forums for "samba" "feisty" or something along those lines).I have a common username that all of my machines use (so that I can connect to any of them if I need to and share files with all of them).

...And the best thing is, once you figure this out, you have learned all about setting up a home network with file and printer sharing!

***HINT HINT*** Look for a "Shared Folders" entry in the "System" menu under "Administration." If you just want simple network shares of your Linux box, this should work well for you. If you want to access XP shares use the "Connect to Server" entry under the "Places" menu (selecting "Windows share" and BE SURE TO PUT IN A USERNAME:)).

---

