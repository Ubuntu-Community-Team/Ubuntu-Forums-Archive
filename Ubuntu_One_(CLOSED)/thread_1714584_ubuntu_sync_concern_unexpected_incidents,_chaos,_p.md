---
title: "ubuntu sync concern: unexpected incidents, chaos, please help?"
date: 2011-03-25
forum: Ubuntu One (CLOSED)
---

### Post by goscuter1 on 2011-03-25
As I've been having some issues with Windows and my drivers (RAID and virtual drives setup **not by me**), I low-level formatted all my hard drives (DBAN and KillDisk), every byte zero'd out completely, rewrote the MBRs, flashed the BIOS's, then formatted all hard drives with ubuntu and simultaneously installed ubuntu on both my desktop and laptop - with the intent of (hopefully) never thinking about Windows or Microsoft again. 

All was going fine (*as expected*, rather) for an hour or two until I connected to ubuntu One. And a whole lot of unexpected stuff started happening. First, literally just after I connected to ubuntu One, I get this message after two hours online:

> 'Your current network has a .local domain, which is not recommended and incompatible with the Avahi network service discovery. The service has been disabled.'

I don't want a .local domain. Actually, I don't really want any domain, homegroup or network at all. I didn't think I had one, I was hoping I didn't, and I'm pretty sure I didn't until I connected to ubuntu One and Avahi service shuts down after picking a .local domain up. 

Then I suddenly noticed a Windows network on my laptop:

[IMG]http://i.imgur.com/0d9Z9.png[/IMG]

I admit I may have shrieked. Why do I have this? I'm SO SO sure I do not want this. I've searched on Google and found a bunch of people with this question on the ubuntu forums, and the threads were unanswered, which concerned me - not sure how validly... 

When I enter ~$ sudo net rpc share, I get this:

> Connection to localhost failed (Error NT_STATUS_CONNECTION_REFUSED)

-$ sudo net usershare gives me:

> net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


I don't know if that's good or bad, but I had hoped never to have to ask the question. I want nothing to do with Windows NT. And frankly, I'm tired of being told to contact my system administrator - which has been the experience of my last 6 weeks, since strange stuff started happening, and why I never want to THINK of Windows or Microsoft again. 

Then, and I had been quite pleased that ubuntu wasn't picking up proprietary drivers on my system after my mass formatting, suddenly after connecting to ubuntu One, I get notifications I have proprietary drivers ;( - all my problems started when a Dell technician installed 2005-2009 unsupported, non-existent, outdated drivers and firmware when installing a brand new hard drive (cause that makes so much more sense than going to Dell.com and entering service code, and pressing Enter). Dell refuse to comment. :confused: 

But anyway, **after two hours online** (surely this is relevant?) - only after I login to ubuntu One, suddenly I get a recommendation to download a whole stack of security updates for ubuntu. I do so, but it struck me as incredibly strange, even concerning, the timing...

I had spent two hours setting all my laptop's Gnome preferences, and had it just as I liked it prior to connecting to ubuntu One, which I hoped would allow me to sync all my preferences to my desktop. 

But when I connected to ubuntu One, my screen started filling up with files from ubuntu One. Where did these files come from, they had all been deleted, somewhat permanently obliterated (or so I thought). I thought ubuntu One was a sync service, like Dropbox, no? Unless I'm being retarded, where were my files sync'd from? They had all been low-level formatted into oblivion. And yet, I'm staring at all these old files sitting on my screen now. 

There's a lot of other unexpected stuff occurring, for example I had spent a lot of time setting all my Chrome extensions / add-on preferences. ubuntu One zapped them all, when I opened up Chrome, it opened up to a completely fresh page asking me to sign in and whether I wanted to sync. It installed the old Chrome files from...well, nowhere. 

If I type netstat into the terminal, the amount of activity...it blasts though pages and pages and pages. I'm pretty sure I don't like this massive level of activity, surely this isn't normal? I have 50Mbps/20 VDSL, and it feels like I'm on a 56k modem in 1998.

There are just pages and pages of Connected Streams, stuff like:

@/tmp/dbus-kW0CD6Z5qL
/tmp/orbit-root/linc-98c-0-672f27c7aa530
/var/run/dbus/system_bus_socket
@/tmp/.X11-unix/X0
@/dbus-vfs-daemon/socket-lYgIaH2a
/var/run/acpid.socket
@/tmp/gdm-session-nhkpeqye

Just a tiny example...I try Googling this stuff but I just go around in circles, as I spend half an hour reading a page I really can't understand. Which sends me on wild goose-chases to deadends.

Every file I create now has .u1conflict appended to the file name. Please note I have ONE computer in the world that is connected to ubuntu One - according to the help files, it seems this should *not* be happening? 

And the 2nd most concerning thing, is this Unknown File System which suddenly appeared. If this is normal, why is everything Unknown about it - and why is it 5GB large, with 270,000 items? But mostly, why is it completely Unknown (the reason I am never using Windows again, is very similar - unknowns that no one can explain, but everyone just shrugs or goes silent on forums) - and why did it occur only *after* I signed into ubuntu One? (which I expected should have been completely empty, as all files were deleted everywhere)

[IMG]http://i.imgur.com/ilyIZ.png[/IMG]

Sorry for the length of this post, and please bear with me if some of this is normal. I have such simple requirements, unbelievably simple requirements, yet everything seems so complex ;(

The most concerning thing, and this hasn't happened on the fresh installs yet (but it's happened 100 times on Windows 7 Ultimate last 2 months, and happened on ubuntu earlier this month), but without doing a single thing regarding security settings, I'll suddenly discover I've lost my privileges. And no one can explain why, whenever it happens.

[IMG]http://i.imgur.com/jpB9e.png[/IMG]

I have no idea how stupid any of this might be, or how normal it all is. Apologies if so, but this all creeps me out. I was forced to try ubuntu under duress, but I was pleasantly surprised - and I'm sure I will be again, once things make sense again. 

Getting rid of anything and everything "virtual" will make me feel a whole lot better...

~$ sudo xinput --list

> &#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PIXART USB OPTICAL MOUSE                	id=10	[slave  pointer  (2)]
&#9116;   &#8627; DualPoint Stick                         	id=12	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint TouchPad        	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_0.3M           	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=14	[slave  keyboard (3)]


ugh. This really creeps me out...

**Thanks in advance for any answers / solutions!**

---

### Post by goscuter1 on 2011-03-25
> **goscuter1 said:**
> But anyway, **after two hours online** (surely this is relevant?) - only after I login to ubuntu One, suddenly I get a recommendation to download a whole stack of security updates for ubuntu. I do so, but it struck me as incredibly strange, even concerning, the timing...


I just ran sudo apt-get update/upgrade and either ubuntu came out with a massive amount of upgrades in the last 20 hours, or I'm pretty sure when I connected to ubuntu One last night, I was sent backwards. 

Happy to post the logfiles if anyone feels they would be helpful. 

I also noticed 3 old devices listed in ubuntu One, which kind of explains where the sync may have been coming from. Perhaps I was dull to assume they'd be obliterated like the hard drives they were syncing from, but it's still a Security issue no? There are are many dull people like me!

I've still got an Unknown Filesystem as root. And a Windows Network I can't access (which I hope is a good thing, but I fear the reverse from my offline netstat) which I never installed from a Samba I apparently never had. And a .local domain I don't want, from an ISP who's going out of their way to act suspiciously - so lots of questions still, happy to pay for EXPERT assistance (it seems Services are just for business networks :(). I have $ that is legal tender. I almost certain I need professional help sigh...

---

