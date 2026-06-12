---
title: "Networking with mixed systems (LinuxMint, Ubuntu, Windows and Mac OS)"
date: 2009-01-02
forum: Server Platforms
---

### Post by voltopian on 2009-01-02
Mornin' everybody, 

I recently learned that we have 5 PCs at home and 3 Printers (1 one those don't work, guess who's? Right, mine!) and I thought: "Well, that's kinda retarded! We print like 5 pages each per year, we don't need that many printers! Which got me thinking: They got Network Printers at my school and it works there. Should be easy!" Then I saw the fatal flaws in my logic:

We have 5 PCs, all of them either in a) different rooms (smallest of the problem I guess) b) on different levels (count 3 on the first floor, 2 in the cellar) and c) all of them have a different kind of OS on their system. While I am the only one who is using any form of Linux (One of Ubuntu's daughters Mint at the moment on my desktop PC, Ubuntu 8.04 on my Notebook), the others have 3 kinds of MS Windows (Vista, XP and 98 I think) and once even MAC OS ( or "the apple thingemajing", as I like to call it). The good part is that as far as I know we are all connected through the same router (standing on entrance level). Of course through network sockets on each floor which end in the router, but same thing... right  

My question now is: Could it still work? Do I need an extra server? I have an old DELL PC (with Windows installed right now) with Network card and everything which was High-End 4 years ago, would that do? And what else do I need? Any sort of hardware? Is it as much effort as I'm fearing? And would it be possible to add additional Units (let's say Notebooks running Ubuntu ;) ) if I wanted too? Could the Ubuntu Server edition do the job?

Thanks for the help, I hope you can help me

---

### Post by cariboo on 2009-01-02
The answer to all your questions is yes. The only thing that might take a littel work is getting the Mac to talk to the network if you arte using a version older than OSX. In order for oder Macs to communicate with Linux you will have to install and setup [AppleTalk]("http:///help.ubuntu.com/community/AppleTalk"). Connecting from the Windows computers is just a matter of setting up [Samba]("http://ubuntuforums.org/showthread.php?t=806699"). The only limitation as far as network size is the number of network ports you've got.

Jim

---

### Post by voltopian on 2009-01-02
First of all, thanks for the help again, I know that the Ubuntu Community is awesome *slime slime* ;)

I found something called "printer configuration" under System-Administration-Printing and it has such nice options as "connect to server" and "show printers shared by other system". However I have no idea if that helps or what kind of server I should connect to. I am assuming that a cups server is a printing server (no idea what the cu stands for though). 

I installed Samba (actually it allready was installed, but I didn't know that). And I couldn't edit the file yet because I am for the next two days home alone, which is the only way I could get this done. I also have no idea what to write into the file at SERVERSTRING .The IP of the server?
And WORKGROUP is a tough on too, but at least I just have to check at one PC for that.

What it does have is something called "Network Servers". If you click on it, you have the choice between "USERXY-Desktop" and the curiously named "Windows Network". 

And do you mean by all questions yes that I need a server AND can use the Dell PC or that I don't need a server but I could use the DELL one?

As you see, I'm not new to Linux, but to Networking in general. So I want to be very careful and not screw up my or worse the family's Internet Connection just so I can use the printer without having to burn CDs for .doc files. I also am a burned child in that matter, because friends of mine had a LAN party (4 PCs plus mine) in my room and I had to reinstall my OS to get my internet going again afterwards because they had to screw around with the Network Settings.

---

### Post by volkswagner on 2009-01-03
I think you should decide on convenience and performance.  Food for thought.

[LIST]
[*]Which PC can be left on all the time, or can utilize WakeOnLAN?
[*]Which printer has drivers for Linux, Windows, and MacOS?
[*]Can you send a document to the printer without waking someone?
[*]Don't choose a host (server) PC that will be leaving the home soon or often.
[/LIST]

You should be able to follow directions for the particular printer, from the manufactures documentation.

---

### Post by voltopian on 2009-01-03
So, I got it now. It actually WORKS. I'm suprised that we (me and you guys ;)) did get it done, I used the HP Printer in the cellar and had a few problems talking to the mac, but after getting the hang of it, my DELL Server worked for everybody and even has the option of filesharing intergrated in the mix, which wasn't even part of my plan. 

So it works, we can get rid of 2 printers no one uses anyway now. Thank you guys again, if I didn't get this done, my parents would've probably put me up for adoption, even at my age, just to set an example :D .

---

