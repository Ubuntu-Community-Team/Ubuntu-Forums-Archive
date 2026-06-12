---
title: "desktop vs server ubuntu, which one?"
date: 2008-10-05
forum: Server Platforms
---

### Post by enzo12345 on 2008-10-05
Hi.

I currently have ubuntu desktop installed on a machine i intend to use for these purposes:

apache, php programs, sql database, ftp server.

specs:
amd athlon 2500+
512mb ddr
128mb ati radeon 9200
2 x 80gb HD's.

Would I gain much of a performance boost if i switched to server edition and used the command line instead of a GUI?

Is using the command line exclusively going to be alot harder?

One reason for the GUI is i need to download a text file from a web server every now and then, but it is not possible with php and cURL as it does not have a direct download link, so i was going to use a macro to control the mouse in the GUI to download this text file.

Does anyone know how I could download this file without the GUI?

Thanks

Enzo

---

### Post by Drezard on 2008-10-05
Cli with server edition will almost always be faster then the Gui with Desktop edition. Im not sure on this hardware whether you would notice the boost or not but give it a shot and see what happens.

In regards to the other problem, google "crontabs" and "wget".

Daniel

---

### Post by Iowan on 2008-10-05
As if you needed another option... installing SSH-server would let you use SSH (or PuTTY) to retrieve the file(s). Although I've never used it, **webmin** is often mentioned as an alternative to a full GUI. Personally, I like the CLI... but it helps to make friends with the **man** command.

---

### Post by lykwydchykyn on 2008-10-05
You could always fire up lynx or w3m or another text-mode browser to download the file.

Honestly, though, on modern hardware if you install xorg and a window manager like jwm or fluxbox, the performance difference is minimal.  If you're going to have a monitor attached to it, might as well have the GUI so you can take advantage of multiple xterms, browsing, etc.  Otherwise it doesn't afford you much advantage unless you've got an actual GUI configuration app that you want to use.

BTW, if this is a dedicated server and you've got an on-board video adapter, I'd yank that ATI card and see if you can trade someone for another stick of RAM.  All that card is going to do is use up more power for nothing.

---

### Post by enzo12345 on 2008-10-07
**Drezard** - crontabs looks like what i need! looked at wget but i think i will have the same problem with cURL (i am trying to download a file with a URL like this: [www.example.com/directory/](www.example.com/directory/) , the file is made by the server on the fly, then the download prompt comes up in my browser).

**Iowan** - I dont own the server i am trying to download from so I dont think i will be able to use SSH to remotely get the file!

**lykwydchykyn** - I am going to try and use a text based browser, then write a script to log in and download the file i need. Is this possible? I need the script to mimic keyboard shortcuts to control the browser though (e.g i need to select the link with the tab key, how do i get a shell script to type tab for me?).

Thanks for your suggestions, they have helped me out alot!

---

### Post by lykwydchykyn on 2008-10-07
I suppose it's possible, though I've never done it.  Maybe you can use a redirect, though I can't be sure it'd work:
```

lynx http://www.example.com << EOF
[tab]
[tab]
[enter]
username
password
[tab]
d
EOF

```
Something like that.  That's just a wild guess.  Regarding how to get things like tab and enter into your script, see this post:
[http://ubuntuforums.org/showthread.php?t=547046](http://ubuntuforums.org/showthread.php?t=547046)

---

### Post by enzo12345 on 2008-10-07
thanks, it works at last! using w3m its better than i thought. cheers

---

### Post by computer_freak_8 on 2008-10-07
Hello,

I too have a question regarding Server vs. Desktop versions.

First off, I know that the GUI can be installed on the Server edition by running "sudo apt-get install ubuntu-desktop". Correct?
Second, the real question: What about the other way around? 

Say I have Ubuntu (Desktop version). I want to get full server capabilities. Is there a command like "sudo apt-get install ubuntu-server" that will make my Desktop-version computer be server-capable?


Thanks so much,
computer_freak_8

---

### Post by Iowan on 2008-10-07
Des Moines, eh? I'm about 2 hours east on I-80.  Most of what makes a server a server can be installed separately (possible exception is optimized kernel).  Check the "Perfect Server" article(s) on howtoforge.com to see how they built their server - they didn't use the easy "Install LAMP server" method I chose.

---

### Post by tspec on 2008-10-08
Performance aside, if I was to choose running the server edition over the desktop edition, it would be more on the basis that the server edition has longer support cycle. That said, I do like having a GUI available if I need it, sometimes it's just easier than piss farting around with the command line but all depends on what I'm doing.

---

### Post by computer_freak_8 on 2008-10-08
> **Iowan said:**
> Des Moines, eh? I'm about 2 hours east on I-80.  Most of what makes a server a server can be installed separately (possible exception is optimized kernel).

First off, cool! Are you a member of the Iowa LoCo team?
Secondly, I understand what you mean about the things that are "what makes a server a server" - I actually went to Ubuntu's website and figured out (through "apt-get" and the first few letters followed by the [Tab] key) the "sudo apt-get install" equivalent of what a command such as "sudo apt-get install ubuntu-server" would do.

Now I'm going to look for threads on meta packages :)


Thank you!
computer_freak_8

---

### Post by AgentZ86 on 2008-10-12
Hi all

I've been using SME server but am considering Ubuntu Server.

I use my server for webmail,ftp,hosting images for ebay, and a few other websites for my freinds,and local print server. And also Horde Group suite which is the webmail program.
I don't have to have horde but something similar would be nice with task lists, notes, share common phone book on the server etc.

I want to setup Ubuntu for this, but I'm haveing some trouble deciding. I"m not to concerned about the gui slowing things down.

My question is, since I know how to get around Ubuntu Desktop and installing things easily with synaptic etc. I'm wanting a GUI for my server.

But I'm not sure if it's better to use Ubuntu Desktop and get the server stuff installed on it, or to install Ubuntu server and install the desktop stuff on it. ?

Please advise which is best for my small server usage

Also will Ubuntu Server prompt me for use as local server or Gateway ?
I need to use as a Gateway

---

### Post by computer_freak_8 on 2008-10-12
AgentZ86 - 
I don't remember my server installation asking me to use as a gateway, but if you look around for IPTABLES tutorials for using it as a gateway, you will find that there are plenty. [This one]("https://help.ubuntu.com/community/Internet/ConnectionSharing") might work for you.

As for installing server packages via desktop edition or installing GUI via server edition, I would recommend installing the server, and then running:
```
sudo apt-get install ubuntu-desktop
```

Otherwise, you will have a very long list of packages to download to get all that the server edition has to offer.


Good luck,
computer_freak_8

---

