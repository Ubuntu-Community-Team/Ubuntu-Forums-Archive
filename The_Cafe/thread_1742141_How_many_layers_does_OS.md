---
title: "How many layers does OS"
date: 2011-04-28
forum: The Cafe
---

### Post by nec207 on 2011-04-28
So I was reading up how OS works but got confused of how many layers the OS have.
 
 
 I thought a OS has 3 layers?

1. User level
2. System level 
3. Kernel level

---

### Post by Lucradia on 2011-04-28
> **nec207 said:**
> So I was reading up how OS works but got confused of how many layers the OS have.
 
 
 I thought a OS has 3 layers?

1. User level
2. System level 
3. Kernel level

[http://en.wikipedia.org/wiki/Abstraction_layer](http://en.wikipedia.org/wiki/Abstraction_layer)

---

### Post by nec207 on 2011-04-28
> **Lucradia said:**
> [http://en.wikipedia.org/wiki/Abstraction_layer](http://en.wikipedia.org/wiki/Abstraction_layer)
 
 
I never seen any thing shown like that .
 
 
I gusess if want you could add more .
 
 
 1. User level
     programs
     interface
     shell
2. System level 
3. Kernel level

---

### Post by 3Miro on 2011-04-28
This is the best I can come up with. The model is far from perfect, but it is reasonably close.

User
Windows Manager
Desktop Environment (gconf, NetworkManager)
Toolkit (GTK/QT)
Xorg
Various system daemons (i.e. hal, dbus ...)
Kernel
Hardware

The shell, or the User Interface (UI) consists of the top two (panels and windows manager/effects).

The boundaries are sometimes blurry. Toolkits do have components to interface with system processes not just Xorg. Desktop environment can also be split into background daemons (gconf) and foreground panels (gnome-panel). NetworkManager works independent of Xorg, but it is controlled via nm-applet, which is part of the GTK environments ....

---

### Post by RiceMonster on 2011-04-28
What is the "system level"?

---

### Post by lisati on 2011-04-28
A short answer is that it takes as many layers as is necessary. 

At the end of the day, I don't think too much about what happens between me pressing a sequence of keys on my laptop and my posts appearing on Ubuntuforums.org - unless, of course, something goes wrong and I need to switch into troubleshooting mode. :D

---

### Post by nec207 on 2011-04-28
> **RiceMonster said:**
> What is the "system level"?
 
 
OS system files and drivers.
 
 
Mess with this and your OS goes up in snoke.
 
Needs root to acess it not like user level.
 
 
>  
 Toolkits do have components to interface with system processes not just Xorg

 
sorry no idea what are Toolkits or Xorg.
 
Malware really cannot do any thing to the Kernel.

---

### Post by fdrake on 2011-04-28
> **lisati said:**
> A short answer is that it takes as many layers as is necessary. 
good and empiric answer! many developers are still working on to find out how many are necessary on modern os . there are different os that can contain only 2 levels(almost). system level and user level(applications that contain itself a piece of kernel)

---

### Post by 3Miro on 2011-04-28
> **nec207 said:**
> 
sorry no idea what are Toolkits or Xorg.


Google Xorg, GTK and QT.

Xorg is the base for everything graphical in Linux.

Toolkits provide a set of libraries that give basic functionality for creating graphical apps as well as common look and feel. Apps working on the same Toolkit find it easier to work together (like drag-and-drop features).

---

### Post by nec207 on 2011-04-28
> **fdrake said:**
> good and empiric answer! many developers are still working on to find out how many are necessary on modern os . there are different os that can contain only 2 levels(almost). system level and user level(applications that contain itself a piece of kernel)
 
I don't know any OS that  has 2 or 3 .
 
If you talking about malware than yes it be like this .
 
1. User level   ( non root ) ( you movies ,music ,pictures and work )
2. System level  ( root acess)
3. Kernel level.
 
System level ----Kernel level. -- Hardware
 
In windows .
 
1. User level   ( user )
2. System level (  admin) 
3. Kernel level.
 
System level ----Kernel level. -- Hardware
 
So in theory if one makes malware and you click the URL of malware  and you log in as root on Linux or Mac OS X  or admin in windows the malware can go to System level  really easy.

---

### Post by fdrake on 2011-04-28
[http://en.wikipedia.org/wiki/Microkernel](http://en.wikipedia.org/wiki/Microkernel)

i said "almost" 2 levels since the kernel in the machine is so small and limited (almost inexistent) that the application have their on drivers and kernel code to run.

---

### Post by fdrake on 2011-04-28
> **nec207 said:**
> I don't know any OS that  has 2 or 3 .
 
If you talking about malware than yes it be like this .
 
1. User level   ( non root ) ( you movies ,music ,pictures and work )
2. System level  ( root acess)
3. Kernel level.
 
System level ----Kernel level. -- Hardware
 
In windows .
 
1. User level   ( user )
2. System level (  admin) 
3. Kernel level.
 
System level ----Kernel level. -- Hardware
 
So in theory if one makes malware and you click the URL of malware  and you log in as root on Linux or Mac OS X  or admin in windows the malware can go to System level  really easy.

actually system level is not the root or the aministration level but is a set of packages that hold together the system and are a medium between the programs and the kernel. exc. Xsever. desktop, windows manager. ..

---

### Post by nec207 on 2011-04-28
System level has files needed to run the OS and has the drivers. And some programs will load in the system level or have to work with the systel level.
 
The system level deals with the Kernel level and the Kernel level deels with the hardware.
 
I was saying you need root to acess the system level .
 
Your home folder,movies ,music ,pictures and work and running open Office,paint so on does not need root acess has it is your user level.
 
Only when you make changes to OS ,install software , drivers or system uptades will need root acess do to the damage it could do to at the system level.
 
 
The Malware cannot do any thing at the user level but can do alot at the system level.

---

### Post by jeffathehutt on 2011-04-28
> **nec207 said:**
> The Malware cannot do any thing at the user level but can do alot at the system level.

What about malware that deletes all my files?  I can't speak for others, but my data is much more important than the programs I use.  Also, what about a program that a user installs to their home directory?  That program wouldn't be installed system-wide but it could cause a lot of damage.

---

### Post by 3Miro on 2011-04-29
> **jeffathehutt said:**
> What about malware that deletes all my files?  I can't speak for others, but my data is much more important than the programs I use.  Also, what about a program that a user installs to their home directory?  That program wouldn't be installed system-wide but it could cause a lot of damage.

Don't install programs from sources that you don't trust. Be careful who you trust.

A program can come and delete all of your files, but unlike Windows, it will not be able to then clone itself and start attacking other people. The damage from malware is contained to the people that got fooled into installing the malware. Also, it is virtually impossible to just "get something" while browsing.

The main advantage of Linux security is not that it is build very tightly and very restrictively. The main advantage is the open nature of the community allowing for an almost instantaneous response to security threats. This is only possible with open (non proprietary) software.

---

### Post by nec207 on 2011-04-29
> **jeffathehutt said:**
> What about malware that deletes all my files? I can't speak for others, but my data is much more important than the programs I use. Also, what about a program that a user installs to their home directory? That program wouldn't be installed system-wide but it could cause a lot of damage.
 
 
Than get windows it has more gradual permission level than a ON and OFF  like Linux or Mac OS X.
 
In Windows you set up a account for internet use only with like no permission to do any thing on the computer even open programs or read and write to your files.

---

### Post by HoKaze on 2011-04-29
> **nec207 said:**
> Than get windows it has more gradual permission level than a ON and OFF  like Linux or Mac OS X.

That's not true. Almost every UNIX or unix-like OS tends to come with very fine controls over permissions if you choose to use them. For instance, in Linux you can create minimal accounts that can't even access the internet, audio or video if you wish, or set up guest accounts who have their home as a temporary space in ram.
Of course, most people don't go overboard with group restrictions, homes stored in ram or excessive permission control and as such there are only 3 or 4 account levels most people would ever use: root, admin, user and guest.

It's actually considerably more complicated than that with "users" that are actually not users at all such as daemon, gdm, lp, etc but hey, not my area of expertise there. I dare say I've probably gotten a few things wrong in all this but either way, UNIX and unix-like systems are pretty complex when it comes to users and their permissions. To call it a "ON and OFF" system is ridiculous.

---

### Post by nec207 on 2011-04-29
> **HoKaze said:**
> That's not true. Almost every UNIX or unix-like OS tends to come with very fine controls over permissions if you choose to use them. For instance, in Linux you can create minimal accounts that can't even access the internet, audio or video if you wish, or set up guest accounts who have their home as a temporary space in ram.
Of course, most people don't go overboard with group restrictions, homes stored in ram or excessive permission control and as such there are only 3 or 4 account levels most people would ever use: root, admin, user and guest.
 
It's actually considerably more complicated than that with "users" that are actually not users at all such as daemon, gdm, lp, etc but hey, not my area of expertise there. I dare say I've probably gotten a few things wrong in all this but either way, UNIX and unix-like systems are pretty complex when it comes to users and their permissions. To call it a "ON and OFF" system is ridiculous.
 
Find I will take it back on the Linux part.But I think I still right whe it comes to Mac OS X ??
 
No idea what is a guest or daemon on a Linux system.
 
**no permission to do any thing on the computer even open programs or read and write to your files**
 
Is this same wih Linux.

---

### Post by 3Miro on 2011-04-29
> **nec207 said:**
> Find I will take it back on the Linux part.But I think I still right whe it comes to Mac OS X ??
 
No idea what is a guest or daemon on a Linux system.
 
**no permission to do any thing on the computer even open programs or read and write to your files**
 
Is this same wih Linux.

Daemons are system processes that run as a specific user, thus even one of them gets broken into, then this does not give root access. This is a very sharp contrast with say windows XP, where the browser itself was integrated into the kernel and ran with administrative permissions. Thus even small exploits in IE gave hackers full control over windows.

You can do the no-permission thing in Linux, it just probably takes a few steps to setup (I don't think it is a simple click-here GUI interface).

---

### Post by HoKaze on 2011-04-29
> **nec207 said:**
> Find I will take it back on the Linux part.But I think I still right whe it comes to Mac OS X ??
 
No idea what is a guest or daemon on a Linux system.
 
**no permission to do any thing on the computer even open programs or read and write to your files**
 
Is this same wih Linux.

I believe the user "nobody" fulfils this purpose on most unix-like systems, including Linux although you can setup a similar user yourself with a little knowledge. Just checked the user nobody on my system right now and as this user is able to run some programs but doesn't have a home, has no write access anywhere on the system and only has read access of files which have been set so that "everyone" has read permissions.

And it should be true for Mac OS X although I doubt many OS X users even know of such options. As OS X is based partially on aspects of FreeBSD and NetBSD (as well as Nextstep), it is thus a UNIX system and allows for the same degree of control over users as Linux does...although it may be a bit different to setup as the BSD and GNU tools are somewhat different and OS X may have hidden some of these features for the sake of "user friendliness".
I can't say I know much about the OS X side of things, but if the family roots are anything to go by, OS X should work in a similar fashion at least on the command line level of things.

---

### Post by nec207 on 2011-04-30
> **3Miro said:**
> Daemons are system processes that run as a specific user, thus even one of them gets broken into, then this does not give root access. This is a very sharp contrast with say windows XP, where the browser itself was integrated into the kernel and ran with administrative permissions. Thus even small exploits in IE gave hackers full control over windows.QUOTE]
 
You mean user that can only run a specific processes .And a processes cannot acess the system level.
 
[QUOTE]I believe the user "nobody" fulfils this purpose on most unix-like systems, including Linux although you can setup a similar user yourself with a little knowledge. Just checked the user nobody on my system right now and as this user is able to run some programs but doesn't have a home, has no write access anywhere on the system and only has read access of files which have been set so that "everyone" has read permissions.
 
 
That is high security.
 
One other way malware can makes its way on the system is the internet cache folder and browser running code in web site,add or pop up like Java ,sun Java ,scrip ,flash or Java scrip..

---

### Post by Savio2010 on 2011-04-30
Read This PDF file

[http://regmedia.co.uk/2004/10/22/security_report_windows_vs_linux.pdf](http://regmedia.co.uk/2004/10/22/security_report_windows_vs_linux.pdf)

A very good guide.

---

### Post by Spice Weasel on 2011-04-30
Since every OS has users, every OS has security holes. You shouldn't have a false sense of security just because you don't use Windows. Do a search for "debian openssl security" and see just how little it takes for an apparently very secure operating system to become very, very insecure.

---

### Post by Lucradia on 2011-04-30
> **Spice Weasel said:**
> Since every OS has users, every OS has security holes. You shouldn't have a false sense of security just because you don't use Windows. Do a search for "debian openssl security" and see just how little it takes for an apparently very secure operating system to become very, very insecure.

SSL Isn't really needed though.

And you should have said search for "SSL Tunneling", it may be an actual method of getting into an SSL login that you should use, but it's also a bad idea.

---

### Post by nec207 on 2011-04-30
> **Spice Weasel said:**
> Since every OS has users, every OS has security holes. You shouldn't have a false sense of security just because you don't use Windows. Do a search for "debian openssl security" and see just how little it takes for an apparently very secure operating system to become very, very insecure.
 
Tighten up Java,JavaScrip,scrip,flash,sun Java and macros and 90% of most code will not just run in web site ,ads,pop ups or hidden picture that really is not a JPEG.
 
And block HTML in e-mail and do not click spam or junk mail.

---

### Post by 3Miro on 2011-04-30
> You mean user that can only run a specific processes .And a processes cannot acess the system level.

Pretty much yes.

There are two types of attacks, psychological and technological. One targets a weakness of the system, the other targets ignorance of the user. The only way to combat psychological attacks is to restrict the user to the point where they cannot do anything on the system (which cannot be done if this is your own system). However, running the system as "nobody" user will do the trick.

Some people fail to make the distinction between the two and say that "security doesn't matter, since you can fool people to do stupid things on their machines". However, this argument is like saying that "there is no point for Banks to build strong vaults, since people will always fall for Nigerian prince scams".

There is no 100% security on tech attacks, however, in that respect Linux does have huge advantage over most other OS. The open environment allows for very fast response, so a security hole is patched within hours of discovery. This is compared to weeks or even months on Window (that's why you need AV on Windows, the AV companies react much faster and temporarily patch things until MS decides to do something useful for a change, this is also why Linux will never need AV).

Do you want to safely surf the net yourself or are you trying to restrict someone else. If you are going to visit a shady site and you want to be as secure as possible, find some obscure Linux distribution, disconnect all of your HDDs from the Motherboard and then use a liveCD. If the OS doesn't have physical access to any data, it cannot damage/steal the data. You can always clean everything with just a simple reboot.

---

### Post by nec207 on 2011-05-05
I'm not surprised I'm confused the myths floating around on the internet like.
 
 
1.Less than 1% use Linux and 10% use Mac Os X it is not that they are so much better but market share .The Malware makers are going windows where the market shares are.
 
2.Windows have more security but most people don't use it.
 
3.Mac OS X security is not that good , windows is better.
 
Note here is best thing I could find on the internet on OS layer..
 
 
**An OS is very much like cake. Not only does it have layers, but it has frosting that holds the layers together. The tricky thing is the actual OS you're looking at.**
 
**User level runs apps and the UI, including the shell. **
 
**The system level acts as an interface between the user level and the kernel level, and provides the APIs as frosting between it and the user level. Services are in the system level.**
 
**The kernel level access the hardware directly and acts as the CPU traffic director in most contemporary OSes. It manages processes, threads, interaction with the hardware, etc. It talks only to the System level in most cases. Drivers exist at this level.**

---

### Post by Lucradia on 2011-05-06
2% of computers that can connect to the Internet use OtherOS types. (This includes Apple.) Most statistics measure Windows against Windows (IE: Windows XP Vs. Windows Vista Vs. Windows 2000 Vs. Windows Seven Vs. Windows 98 Vs. NT#)

It's a remarkable sight to see how many people still use Windows XP and 2000, and still go on the Internet. But please note, this is limited to computers that connect to the Internet. A lot of people around the UF can tell you they know a lot of places where Linux is used, but not for using the system on the Internet.

And natively, MacOSX has better security than Windows. :| And yes, it's true that Windows has good security, and people don't use it well. IE: They just use Windows Firewall, and don't install anything extra, or just use what came with the computer.

---

### Post by nec207 on 2011-05-06
sorry what do you mean.

---

### Post by nec207 on 2011-06-03
Just looking at the thread over month no reply to my last post.

---

### Post by aaaantoine on 2011-06-03
Obligatory [http://xkcd.com/676/](http://xkcd.com/676/)

---

### Post by nec207 on 2011-06-18
Well other month and still no reply.
 
Anyways here is what I found on Mac OS X the Securing problems talked about here in this thread.
 
[http://www.mactech.com/articles/mactech/Vol.21/21.02/Security/index.html](http://www.mactech.com/articles/mactech/Vol.21/21.02/Security/index.html)
 
 
Have a look at the web site and tell me what you think pro and cons windows or Linux when comes malware.

---

