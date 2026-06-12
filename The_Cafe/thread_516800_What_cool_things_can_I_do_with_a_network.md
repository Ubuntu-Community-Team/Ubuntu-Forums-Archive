---
title: "What cool things can I do with a network"
date: 2007-08-03
forum: The Cafe
---

### Post by jgrabham on 2007-08-03
I now finally have a network up and running.

Are there any cool things I can do with it?

I have a couple of laptops (running xp), the PC in my sig, and soon a dell dimension 5000 (with xp)

---

### Post by koenn on 2007-08-03
you can rename one of the pc's "pong", and ping pong

---

### Post by jgrabham on 2007-08-03
> **koenn said:**
> you can rename one of the pc's "pong", and ping pong

Whats worse is I actually laughed at that

---

### Post by Depressed Man on 2007-08-03
I use my network to stream music and share files between them. You can also play LAN games or VPN into computers to use them or change them from afar. So if I had a stereo system hooked up to my desktop my laptop could start some music on my desktop.

---

### Post by jgrabham on 2007-08-03
Thinking of messing about with a hosting a web page, but dont know what to write the page about!

---

### Post by wesley_of_course on 2007-08-03
Shot in the dark here , but how about all the cool things you can do when you get your network up and runn'in ?  I'd subscribe .

---

### Post by xpod on 2007-08-03
Well i dont know if you can call them cool but i`d get an nfs server set up for sharing your files between the 2 then i`d install the openssh server on the secondry machine so i could control it from the main one:)

Something like that anyway.
My son uses a completely seperate internet connection to our main one so using nfs for file-sharing is no good whatsoever.I had to install the ssh server for that on his pc and you can have all sorts of fun and games with that thing/

Having the ssh server on his machine(with the relevant precautions of course)means i can log into his machine anytime i feel like it just to see whats been going on or run to his app`s and of course share files.

It`s also great at bedtime when i cant get him off the bloody thing of course.....

> sudo goodnight son

Of course running any type of server has potential secirity risks so it is a good idea to read up on all the added precautions you can take.
ssh is great fun though....until they all suss you out:-\"

I`ve never done anything like what you want with web pages etc....i actually have 55Mb of free space from my isp but would`nt have the slightest idea what to do with it or how to do it.
I had began reading up on html and web pages etc about this time last year but something else caught my attention:mrgreen:

EDIT...OH XP...i never seen that...lol
Samba then mabey

---

### Post by Depressed Man on 2007-08-03
Blogs are always good (though finding readership may be hard). But if you write just to write then that's ok. You don't always need an audience. :)

---

### Post by init1 on 2007-08-03
Remote desktop connection. I think you can do that in winxp. If you install Linux you can do ssh. That would be cool. .

---

### Post by esaym on 2007-08-03
Get an old computer and install smoothwall on it and use it as the gateway/firewall

---

### Post by Sporkman on 2007-08-03
I have the computers back up their files to each others' harddrives every night via cron jobs.

---

### Post by Cordate on 2007-08-03
You could set up a cron job and regularly back up important files from one computer to another. 

Edit: Dang it, Sporkman beat me to it :)

---

### Post by Sporkman on 2007-08-03
> **Cordate said:**
> Edit: Dang it, Sporkman beat me to it :)

:p

---

### Post by Turboaaa2001 on 2007-08-03
With my network I have a Samba file server that my wife and I use to share files. I have all my program .exe files there along with my word documents and music. That way No matter what computer I'm on I can access my files without guessing which machine it's on.

The other thing is the most obvious. Sharing a printer. The ironic thing is that printer sharing was the first use of networks, but people today forget to do that. I had to help a customer today because they thought printer sharing was impossible!!!:confused:

Anyway I think it really depends on your needs. When I built my huge network with a Linksys router, a Cisco 2600XL 24 port Switch, and 5 computers I had to do the same thing you are. I  ended up at first finding different projects on the web and trying them out for fun. I then found use for every machine I have.

My latest project is to create a parallel cluster so that I can use 2 computers with a Celeron 2GHZ, 1 computer with a Celeron D 2GHZ, and a 4U Compaq Rack Server with 2 PIII Xeon 900MHZ processors as one big computer through the use of a virtual machine. I hope to run the BOINC software over it but the biggest problem is the overhead.:(

---

### Post by Depressed Man on 2007-08-03
Haha you learn something everyday (I didn't realize that networking was orginally for printers). Speaking of that I should get my USB printer shared so I don't have to keep disconnecting it from my desktop and hooking it up to my laptop just to print.

OH! And VPN. Does anyone have a good guide of how to setup VPNing from Ubuntu to Windows XP? Or Vista to XP for that matter? And Vista to Ubuntu lol.

---

### Post by koenn on 2007-08-04
It all depends on what *you* find cool, or what you are interested it. 
As others pointed out, you can do all sorts of networking stuff : share files and printers, make backups back and forth, run a time server to keep the system clocks on all computerts synchronised across your network, run network services (dhcp, dns,web proxy,  ...) just to see how it's done and make network administration easier, experiment with remote desktops, run a wiki, build a firewall, set up a streaming audio / video server, set up a mail server so you can send mail from one machine to the other without going through your internet mail account, set up your own local chat/instant messaging system  ...

setup some infrastructure for multi-player games - have a LAN party

read up on vulnerabilities, find exploits, and try them against the machines on your network. Figure out what sorts of remote control you can get over other machines on your network.  Use this to cheat in the multi-player games.

---

