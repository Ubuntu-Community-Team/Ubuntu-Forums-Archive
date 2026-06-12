---
title: "What's the coolest thing you do in Linux that you couldn't do in Windows?"
date: 2014-11-11
forum: Ubuntu, Linux and OS Chat
---

### Post by SagaciousKJB on 2014-11-11
Windows users feel free to chime in if you feel that you actually CAN do these things...

Use a combination of ssh, nfs, bash and ffmpeg to transcode video files downloaded on my laptop using my desktop computer as the encoding machine, but sending the output automatically back into the same folder as the video I'm transcoding on my laptop.  The whole thing is ran by a script I just right-click and run on the original file.

Can you do THAT in Windows?

---

### Post by sudodus on 2014-11-11
I think the coolest thing is running live and installed systems from USB pendrives. Such portable systems work beautifully with Linux. There are Windows PE (preinstallation environment) systems, but they are very limited, and work only as rescue systems.

---

### Post by TheFu on 2014-11-11
> **SagaciousKJB said:**
> Windows users feel free to chime in if you feel that you actually CAN do these things...

Use a combination of ssh, nfs, bash and ffmpeg to transcode video files downloaded on my laptop using my desktop computer as the encoding machine, but sending the output automatically back into the same folder as the video I'm transcoding on my laptop.  The whole thing is ran by a script I just right-click and run on the original file.

Can you do THAT in Windows?

So ... yes you can, but it isn't as easy. I use a mix of Linux/Windows here. Strawberry Perl is the glue. The only reason I use Windows is for video editing (and quicken).

I routinely 
* queue up batch processing using task-spooler (queue management is amazing)
* access GUI programs running on other machines using X/Windows on the LAN
* access remote desktops over ssh with NX-base x2go (both secure AND much, much, much faster than either RDP or VNC) from around the world
* XBMC - 'nuff said
* ssh around the world to manage servers and routers configured for clients
* Ansible to automate systems management - if you have 4-40,000 systems, you NEED to use ansible.
* read scheduled, daily emails created by my systems for log summaries, system status, backup completions/failures, etc... 

And don't forget how easy it is to maintain the complete OS and all installed applications weekly by running 2 simple commands:
* sudo aptitude update
* sudo aptitude dist-upgrade
THAT is the real reason I prefer Linux over Windows ... those 2 commands.

All with 100% free, libre, software that has source code available. THAT is the amazing part.

---

### Post by treb0r on 2014-11-11
For me, the greatest benefit of GNU/Linux over Windows is access to tools.

On Windows, if you need to accomplish something you usually need to go off and find/buy/download software to do it. On GNU/Linux, you will usually find that the tools you need are already installed. If not, the amazing array of software available through the Advanced Package Tool (APT) will give you what you need.

It's a common complaint from new users of Ubuntu that one needs to learn the command line to really get to grips with the system. The truth is that the command line can reward you with the power to get most things done in return for just a little bit of reading, learning and research.

---

### Post by wyliecoyoteuk on 2014-11-11
Install and configure a basic server in less than 30 minutes.

Run Mythbuntu from a cheap 8GB SSD, with /var /home and swap on a spinner.

---

### Post by mastablasta on 2014-11-11
and you can't get most things done using command line in Windows?

I remember when I was in primary school we didn't have money for a proper PC, but my mother got us one really old they threw out in their office. with a Z-80 CPU, 2 floppies, no proper graphics - it used modified DOS 4 i think and it wasn't that much modified. with an old  DOS book in hand I started with CLI interface. I knew quite a lot and could do many things. 

now I dont' have time to learn so much anymore. if I am lucky I get about 30 minutes of peace a day. either learn or surf the net or check email. all in those 30 min. during weekend it's a bit better maybe an hour or two. still too little time to learn CLI so I depend on GUI and like KDE since they have many things in GUI and usually interfaces are good and most things self explanatory. so I don't need to learn or teach too much.

I am tinkering with file server and I am forced to learn - usually I can do it only during weekend. if the there is time.

---

### Post by pfeiffep on 2014-11-11
Re-use older hardware to run up-to-date operating system software saving money and not filling the landfills.):P

---

### Post by cariboo on 2014-11-11
Surf the internet while installing Ubuntu or one of the derivatives.

---

### Post by Daveski17 on 2014-11-11
The coolest thing I can do with my laptop, now running Linux instead of Windows, is the fact that I can surf the Internet within 40 seconds of switching it on. Previously it would take ages to page enough RAM to use properly.

The second coolest thing is that I don't have to worry about an anti-virus program accidentally borking my system.

---

### Post by thiebaude on 2014-11-11
Oh, and can you imagine updating your computer before you log in

---

### Post by oldos2er on 2014-11-11
Considering that the last version of Windows I used was 3.1, damn near everything!  :)

---

### Post by PaulInBHC on 2014-11-11
Use it after installing a new motherboard. Windows is asking me to activate it again.

---

### Post by DeadManDying on 2014-11-11
Don't get me started on pen drives. Lol. Well other than that. There's a certain freedom to Linux that other os'es lack. The freedom to use whatever programs you wish. if you want to use a different DE or WM. Go for it. Use Wayland? Why not. And also having a package manager makes things easy to update. On top of all this. I don't have to pay a damn cent. And I'm one stingy man. Lol

---

### Post by mastablasta on 2014-11-12
> **PaulInBHC said:**
> Use it after installing a new motherboard. Windows is asking me to activate it again.

so what? you click activate and move on...

---

### Post by PaulInBHC on 2014-11-12
> **mastablasta said:**
> so what? you click activate and move on...

Wouldn't that be nice.

I have the paid for upgrade from XP. No media. You must call MS and key in numbers to receive a new code number. Yeah it's not a big deal if it works but I shouldn't have to do it. My old code should work.

---

### Post by TheFu on 2014-11-12
> **PaulInBHC said:**
> Use it after installing a new motherboard. Windows is asking me to activate it again.

Every time I attempt to move a Windows install to a different machine (moving the HDD), the boot fails with a BSOD.  This is a retail version of Win7.  So - MS has a solution for this that works (3) times only.  sysprep.  It is better than nothing, but wipes many important settings - like the last time it disabled NTP for some odd reason.  For about a week, the system clock was off 6 hrs and I didn't know why because all the settings for NTP to my internal server were correct ... the service was disabled.

I cannot remember the number of times I've moved a HDD between machines with Linux and it just booted with my normal environment.  Happy.  Once moved from a pentium4 to a core i7 - worked fine.

---

### Post by jay65 on 2014-11-13
1. Hot corner. Windows is too static.
2. Font rendering. CJK font is much more beautiful on linux.
I was impressive with these features on mac but I found linux is more natural.

---

### Post by monkeybrain20122 on 2014-11-13
Make full installls of several Linux distros on an external hd and boot off different machines. When I visit my folks in a different contentinent I just bring it and boot off my dad's laptop instead of bringing my own and sync it with mine when I come back :)

---

### Post by Mike_Walsh on 2014-11-13
> **sudodus said:**
> I think the coolest thing is running live and installed systems from USB pendrives. Such portable systems work beautifully with Linux. There are Windows PE (preinstallation environment) systems, but they are very limited, and work only as rescue systems.

A BIG +1..!

Couldn't agree more. The beauty of it is that I can take my favourite distros with me ANYWHERE there's a 'puter to plug into! I currently have 4 full installations on a bunch of 32 GB SanDisk Cruzer flashdrives I bought a coupla months ago; Ubuntu, Xubuntu, Puppy Linux 'Tahrpup' 6.0.....and Sabayon (which I'm sorta 'playing around' with at the mo...)!

[I]
Originally posted by** pfeiffep**:-
[/I]> [COLOR=#000000]Re-use older hardware to run up-to-date operating system software saving money and not filling the landfills.[/COLOR][IMG]http://ubuntuforums.org/images/smilies/smiley-faces-80.gif[/IMG]

I'm pretty much the same; I have a passion for getting old 'tech' up-&-running again.....and keeping it that way!

Regards,

Mike. ;)

---

### Post by mJayk on 2014-11-13
Work

---

### Post by tonstwo on 2014-11-14
Not install an antivirus and still be sure that my computer isn't infected.
Drop down terminals. MPD and NCMPCPP.

---

### Post by TheFu on 2014-11-14
> **tonstwo said:**
> Not install an antivirus and still be sure that my computer isn't infected.
Drop down terminals. MPD and NCMPCPP.

Just be aware that running Linux is NOT a 100%, never-have-to-worry, answer for a secure system.

My fully patched, Ubuntu 14.04.1 netbook was hacked a few weeks ago while accessing a wired ethernet port in a hotel during a conference.  The passwd file and group files were completely replaced ... so they pwned the box - no question.

It was a technology conference.
I had wiped the box before attending and have wiped it since returning - standard procedure for travel computers.  If I travel to hostile countries, the hardware is sold on ebay on return home.  Best to have a $200 system for stuff like that.  Oh - and it never left my site and I was NOT staying at the conference hotel. The hack occurred AT THE CONFERENCE.

There is nothing that is 100%.

---

### Post by tonstwo on 2014-11-14
> **TheFu said:**
> Just be aware that running Linux is NOT a 100%, never-have-to-worry, answer for a secure system.

My fully patched, Ubuntu 14.04.1 netbook was hacked a few weeks ago while accessing a wired ethernet port in a hotel during a conference.  The passwd file and group files were completely replaced ... so they pwned the box - no question.

It was a technology conference.
I had wiped the box before attending and have wiped it since returning - standard procedure for travel computers.  If I travel to hostile countries, the hardware is sold on ebay on return home.  Best to have a $200 system for stuff like that.  Oh - and it never left my site and I was NOT staying at the conference hotel. The hack occurred AT THE CONFERENCE.

There is nothing that is 100%.

Nice, I didn't know about that standard procedure.

---

### Post by TheFu on 2014-11-14
> **tonstwo said:**
> Nice, I didn't know about that standard procedure.

It is only a standard procedure if you do it always.  If your company sends people to not-so-friendly countries where corruption and/or corporate theft is common, this is the best practice.  The computers don't have any sensitive data and is basically a remote desktop access tool - nothing more. Of course, the remote access needs to be highly secured with 2FA too.

My Defcon group had a discussion about how to travel with a computer to China a few years ago. The guy who asked the question said some people in his company wanted to bring their home laptops - think we talked them out of that.  We also talked them out of having any remote access on their cellular devices. 
[http://www.darkreading.com/attacks-breaches/researcher-intercepts-gsm-cell-phones-during-defcon-demo/d/d-id/1134099?](http://www.darkreading.com/attacks-breaches/researcher-intercepts-gsm-cell-phones-during-defcon-demo/d/d-id/1134099?)

It is a scary world out there - "they" are not targeting YOU, they are targeting EVERYONE (most of the time). Of course, if you are a CxO on trave (or lead engineer, product manager, sale VP, ... l, then they ARE targeting YOU, specifically, and they are patient.

DarkHotel: A Sophisticated New Hacking Attack Targets High-Profile Hotel Guests
[http://www.wired.com/2014/11/darkhotel-malware/](http://www.wired.com/2014/11/darkhotel-malware/)

---

### Post by SagaciousKJB on 2014-11-15
Very intresting TheFu, have any theories about how they did this?  I must admit that a lot of the times I adopt a "Nobody is going to try" approach.  But I don't find myself at a lot of tech conferences, in China or even in a demographic where many people are technologically oriented.   More people in my city know how to grow corn than what a korn shell is.

---

### Post by TheFu on 2014-11-15
> **SagaciousKJB said:**
> Very intresting TheFu, have any theories about how they did this?  I must admit that a lot of the times I adopt a "Nobody is going to try" approach.  But I don't find myself at a lot of tech conferences, in China or even in a demographic where many people are technologically oriented.   More people in my city know how to grow corn than what a korn shell is.

They have cars, know how to take trains and buses.
Plus there is this new world-wide network thingy ... that reaches almost everywhere.

---

### Post by rrnbtter on 2014-11-15
Greetings,
Some cool things I do to keep from getting hacked. 
1. run a firewall (it's free).
2. Log into unknown WIFI with an alternate USER account.
3. Use a VM.
4. My favorite. Dual boot a copy of Puppy Linux. I prefer Carolina Puppy, but there are many others. 
5. Encrypt Home Dir ( I like this the least).
6. Use a high quality network password. (see wifi settings under network). 
7. Clone your mac address. (network settings or macchanger)
It goes without saying "the list goes on" and most of these should be usable in Windows.

---

### Post by TheFu on 2014-11-15
> **rrnbtter said:**
> Greetings,
Some cool things I do to keep from getting hacked. 
1. run a firewall (it's free).
2. Log into unknown WIFI with an alternate USER account.
3. Use a VM.
4. My favorite. Dual boot a copy of Puppy Linux. I prefer Carolina Puppy, but there are many others. 
5. Encrypt Home Dir ( I like this the least).
6. Use a high quality network password. (see wifi settings under network). 
7. Clone your mac address. (network settings or macchanger)
It goes without saying "the list goes on" and most of these should be usable in Windows.

rrnbtter - perhaps I'm missing something important, but I don't think most of those things in the list actually help security much (if any).  I understand the firewall and sorta get the encrypted home, but how does the rest actually help secure a laptop on travel at all? Please educate us.

---

### Post by oldrocker99 on 2014-11-15
Not about security, but...
I recently bought a $50 Lenovo 3000 N100 (32-bit dual-core Pentium!) and it would have bogged down just trying to run Windows 7. I put the new Ubuntu MATE 14.04.1 on it, and it runs like the proverbial top. No, it won't run every program well, but it does run everything I want to run (with the usual exception of various Steam games) quite well indeed.

In other words, another old computer brought back to useful life by Linux!\\:D/

---

### Post by bro2 on 2014-11-16
> **TheFu said:**
> rrnbtter - perhaps I'm missing something important, but I don't think most of those things in the list actually help security much (if any).  I understand the firewall and sorta get the encrypted home, but how does the rest actually help secure a laptop on travel at all? Please educate us.

Dual booting seems like a great idea, though, if you don't have to do much post-OS configuration. Just install the distro that you might be taking risks with, then purge it after you're done. Much safer then just using an alternate user account....

---

### Post by TheFu on 2014-11-16
> **bro2 said:**
> Dual booting seems like a great idea, though, if you don't have to do much post-OS configuration. Just install the distro that you might be taking risks with, then purge it after you're done. Much safer then just using an alternate user account....

According to Brian Krebs, of **KrebsOnSecurity** fame, the secure method to perform [safe internet banking is with a liveCD]("http://krebsonsecurity.com/2012/07/banking-on-a-live-cd/") that you boot and use which cannot be altered (read-only media).  Of course, using an ISO inside a VM from a 100% uncorrupted hostOS is another, but most people will not limit the use of the hostOS in a way to prevent it from becoming corrupted (i.e., it will be on a network that has internet access of some sort).  This means that booting off a flash drive and "try ubuntu" is probably as much security as most of us can stand.  I use [TinyCore]("http://distro.ibiblio.org/tinycorelinux/") for my banking and don't save any data between runs. TinyCore has just enough OS to run a browser on a network, but not much more. It loads into RAM at boot, so any hacking caused by visiting my banks is gone at reboot, plus it is tiny, so calling it fast doesn't come close to explaining how fast it is. Everything it does happens instantaneously.

Of course, I don't use it except from trusted networks - never outside those 2 places, period.

BTW - that is something Windows cannot do too. ;)

---

### Post by bonzini on 2014-11-16
Back to the thread topic -

Use the compose key to type accented characters en français y español.

---

