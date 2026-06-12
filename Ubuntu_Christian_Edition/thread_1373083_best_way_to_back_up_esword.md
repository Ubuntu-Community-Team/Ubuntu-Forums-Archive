---
title: "best way to back up esword"
date: 2010-01-05
forum: Ubuntu Christian Edition
---

### Post by stlsaint on 2010-01-05
i have notes/study sheets etc in e-sword but i dont know whats the best solution for backing up e-sword so i can fresh install or upgrade.

---

### Post by jonathonblake on 2010-01-05
> **stlsaint said:**
> i have notes/study sheets etc in e-sword but i dont know whats the best solution for backing up e-sword so i can fresh install or upgrade.

Burn everything to DVD, or CD.
As an alternative, buy a 64 GB card, and keep your e-Sword resource collection on it.

jonathon

---

### Post by Pepe Lebuntu on 2010-01-05
What I've done to keep a regular backup of my study notes is change the destination my Wine "My Documents" to a "Documents" Folder under my Dropbox folder. If you're using Ubuntu One, that would work just as well.

You just need to go to Applications>Wine>Configure Wine, then the Desktop Integration tab, then change where your My Documents links to, from home/user/Documents to home/user/Dropbox/Documents (or home/user/UbuntuOne/Documents or whatever...). 

Once you've done that, E-Sword should create an E-Sword Folder in that Dropbox Folder. Then move your notes etc over to that new E-Sword Folder. There are several big advantages to this. One is that every time you make a change to your notes, they are automatically backed up immediately, without you even thinking about it. The other cool thing is that, if you use multiple computers (work and home, etc), and you have Dropbox set up on them all, your notes will be available on all of them (this is one of the major advantages Dropbox has over UbuntuOne, as it is crossplatform - my work computer uses XP). This is UBER-useful!

---

### Post by ChrisNZ on 2010-08-01
On a similar note, study notes that were created in an older version and then Linux upgraded. Backup was done, however E-sword was fresh installed due to 'circumstances'. Now I want to find my notes and make them accessible for the new e-sword version! So do i try to move them to where ever the new version is installed or can i import them somehow?

I have tried to search the forums but just too many threads...

Thanks in advance.

---

### Post by jonathonblake on 2010-08-01
> **ChrisNZ said:**
> Now I want to find my notes and make them accessible for the new e-sword version!

I'm going to answer this in several different sections

*[COLOR="DarkRed"]Notes are from e-Sword 8.x, or earlier:[/COLOR]*
*[COLOR="Red"]Using e-Sword 7.x:[/COLOR]*

No conversion needed.  

Study Note files (.not) get dumped into the e-Sword program directory.
Topical Files (.top) get dumped into the e-Sword program directory.

*[COLOR="Red"]Using e-Sword 8.x:[/COLOR]*

No conversion needed.  

Study Note files (.not) get dumped into the e-Sword user directory.
Topical Files (.top) get dumped into the e-Sword program directory.

*[COLOR="Red"]Using e-Sword 9.x:[/COLOR]*

These will need to be converted.

a) I am not aware of any publicly distributed tools that run as native linux programs, that will perform this conversion.

b) The e-Sword Converter program, available from [http://e-sword.net/extras.html](http://e-sword.net/extras.html), will convert topical files.
This will run under WINE on Ubuntu 9.10.

Start the program, then select the specific file.
Note:  This program will convert one file at a time:
Note:  This program will not see, much less be able to navigate into directories that begin with a dot, or other non-alphanumerical character;

c) To convert both study note and topical files (and any other non-password protected resources) then the following may work:

Note:  This procedure might backfire.   Backup your e-Sword resources before doing this.   Backup _everything_ in the .wine directory that you don't want to have to spend time/effort/energy recreating.

In [COLOR="Green"]user.reg[/COLOR], locate the line:
[COLOR="Green"]"Convert User Files"="True"[/COLOR]
Chance "True" to "False".

[COLOR="Green"]gedit ~/.wine/user.reg[/COLOR] is the command line I use.

d) GoodOlClint's Convertor will convert files en masse.  It requires .NET 3.0 framework to be installed.

e) BeST 2.x will convert files individually.  It requires .NET 2.0 framework to be installed.

*[COLOR="DarkRed"]Notes are from e-Sword 9.x:[/COLOR]*

[COLOR="Red"]*Using e-Sword 8.x, or earlier:[/COLOR]*

These files need to be converted.  I'm not aware of any tools that run on Linux, either using WINE, or as native applications, that will perform this conversion.

BeST 2.x requires .NET 2.0 network to be installed.  This is the only tool I am aware of, that can perform this conversion.

*[COLOR="Red"]Using e-Sword 9.x:[/COLOR]*

No conversion needed.  

I am not aware of any publicly distributed tools that run as native linux programs, that will perform this conversion.

Study Note files (.notx) get dumped into the e-Sword user directory.
Topical Files (.topx) get dumped into the e-Sword program directory.

---

