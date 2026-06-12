---
title: "Are apparmor profiles available for rhythmbox or Totem?"
date: 2012-04-30
forum: Security
---

### Post by newhere_m on 2012-04-30
I am looking for apparmor profiles for Rhythmbox and Totem (movie player) for Ubuntu 10.04. If these are available, can anybody please inform me the location? (I have found some such profiles but these were meant for older Ubuntu versions and probably not up-to-date.)

---

### Post by rookcifer on 2012-04-30
You can roll your own.  Or I can make one and try to link it, but it may or may not work exactly right (depending on which directory your music is in).

EDIT:  Just made one for Rhythmbox.  I tested it and it seems to work for almost everything.  I am assuming that your music folder (where your MP3's are stored) is somewhere in your /home directory.  If you want to edit the music files (that is write to them) from within rhythmbox you may have to give your music directory write access (by appending "w" to the profile).  Other than that it seems fully functional.

Drop the profile into /etc/apparmor.d and name it "usr.bin.rhythmbox".  Then set it to enforce mode and restart rhythmbox.

```
# Last Modified: Mon Apr 30 11:58:21 2012
#include <tunables/global>

/usr/bin/rhythmbox {
  #include <abstractions/audio>
  #include <abstractions/base>
  #include <abstractions/dbus-session>
  #include <abstractions/evince>
  #include <abstractions/nameservice>
  #include <abstractions/python>


  
  /dev/sr0 rw,
  /etc/apt/apt.conf.d/ r,
  /etc/apt/apt.conf.d/* r,
  /etc/lsb-release r,

  /home/*/** r,
  /home/*/.cache/dconf/user rw,
  /home/*/.cache/rhythmbox/** rwk,
  /home/*/.local/share/rhythmbox/** rwk,
  /home/*/.local/share/webkit/icondatabase/* rwk,
  /home/*/.pulse-cookie rwk,
  /home/*/.config/ibus/bus/ rw,
    
  /proc/*/auxv r,
  /proc/*/cmdline r,
  /proc/*/mounts r,
  /sys/bus/ r,
  /sys/bus/usb/devices/ r,
  /sys/class/ r,
  /sys/class/usb/ r,
  /sys/devices/** r,
  owner /tmp/** lk,
  /tmp/** mrw,
  /usr/bin/gst-install rix,
  /usr/bin/rhythmbox mr,
  /usr/lib{,32,64}/** mrw,
  /usr/lib/rhythmbox/rhythmbox-metadata rix,
  owner /{run,dev}/shm/pulse-shm* k,
  /{run,dev}/shm/pulse-shm* rw,

}
```

If you notice something doesn't work (like a plugin) then you may have to look at your logs (/var/log/syslog) and see what it is denying and then make changes accordingly.

---

### Post by Hungry Man on 2012-04-30
Shouldn't be hard to make a profile for those programs. They pretty much just need read access to a few areas in your home directory, you could pretty much do

/home/*/** r, and it would only take about 5 minutes to make the rest of the profile.

---

### Post by rookcifer on 2012-04-30
> **Hungry Man said:**
> Shouldn't be hard to make a profile for those programs. They pretty much just need read access to a few areas in your home directory, you could pretty much do

/home/*/** r, and it would only take about 5 minutes to make the rest of the profile.

Well they need more than read access to /home as you can see from the above profile.  But, yeah, it's not really hard to make one, you just need to understand what each entry is doing and why.

---

### Post by Hungry Man on 2012-04-30
Yeah, it should need read access to its own folders, probably some theme areas, and then a few more, which will take only a few minutes to get through aa-logprof.

---

### Post by newhere_m on 2012-04-30
Thanks for your replies.
I am willing to learn how to write apparmor profiles. Can anybody please tell me which particular material will be helpful for people like me? 

I confess, I do not understand internal processes which take place related to apparmor. e.g., why in the given profile, there are exactly six particular #include<abstractions/...>? How is python related in the process?  How does one figure out that exactly the following directories are to be considered first [[FONT=monospace]/dev/sr0, /etc/apt/apt.conf.d., ..., /etc/lsb-release]? [FONT=Verdana]By the way, I am unable to locate[/FONT] /dev/sr0 and /etc/lsb-release.[/FONT] Similarely, exactly how does one figure out which directories among many of the /proc/* and /sys/*, /usr/* are to be considered and the required permissions to be given? The job is non-trivial for me and I certainly can not do it in five minutes.

---

### Post by rookcifer on 2012-04-30
> **Hungry Man said:**
> Yeah, it should need read access to its own folders, probably some theme areas, and then a few more, which will take only a few minutes to get through aa-logprof.

It needs write and lock access to various directories as well.  That is where care should be taken.

> Thanks for your replies.
I am willing to learn how to write apparmor profiles. Can anybody please tell me which particular material will be helpful for people like me? 

There's a sticky at the top of the forums that explains the process.  

> I confess, I do not understand internal processes which take place related to apparmor. e.g., why in the given profile, there are exactly six particular #include<abstractions/...>? 

Abstractions are like mini-profiles that are there because many programs use the same directories and processes.  So instead of writing it out for each profile, they put them in an abstraction so all programs can use it.

> How is python related in the process? How does one figure out that exactly the following directories are to be considered first [/dev/sr0, /etc/apt/apt.conf.d., ..., /etc/lsb-release]? By the way, I am unable to locate /dev/sr0 and /etc/lsb-release. 


Python is there because Rhythmbox uses python, so it needs access to the python libs.  /dev/sr0 is my CD-ROM drive.  It may be different on your system.  Not sure why you don't have an lsb-release.

> Similarely, exactly how does one figure out which directories among many of the /proc/* and /sys/*, /usr/* are to be considered and the required permissions to be given? The job is non-trivial for me and I certainly can not do it in five minutes.

Generally it does no harm to allow *read* access to /proc.

---

### Post by 0011235813 on 2012-05-01
My question is; why exactly would one need an apparmor profile for Rhythmbox and Totem? It's not like a music or a video file could compromise anything in your system; after all, it's just a media file! Not an executable one! The only thing I can thing of to sandbox (besides browsers and system services) is LibeOffice, because certain  document files (ones that were invented by a company starting with "M" who uses a technology called ] ActiveX) that **might** affect LO.

---

### Post by Hungry Man on 2012-05-01
> My question is; why exactly would one need an apparmor profile for Rhythmbox and Totem? It's not like a music or a video file could compromise anything in your system
Of course it could.

I can think of three scenarios.

1) Malicious video file used to exploit the program. (Images can do this, but it's rare because of how they're stored, still entirely possible.)

2) Malicious file tries to get it to download a codec.

3) MITM attack (or malicious compromised server) tries to drop malicious package that would otherwise be marked for rhythmbox.

Not sure how viable #2 is on Linux. #3 Requires a method to hijack the session, someone on your network, and some flaw in the delivery system (which has happened before.)

I don't think any of these are very likely (I can actually think of a fourth (other program is initially exploited, loads up rhythmbox for local exploit.) ) But it doesn't hurt anything to set up a profile.

---

### Post by 0011235813 on 2012-05-02
> **Hungry Man said:**
> Of course it could.

I can think of three scenarios.

1) Malicious video file used to exploit the program. (Images can do this, but it's rare because of how they're stored, still entirely possible.)

2) Malicious file tries to get it to download a codec.

3) MITM attack (or malicious compromised server) tries to drop malicious package that would otherwise be marked for rhythmbox.

Not sure how viable #2 is on Linux. #3 Requires a method to hijack the session, someone on your network, and some flaw in the delivery system (which has happened before.)

I don't think any of these are very likely (I can actually think of a fourth (other program is initially exploited, loads up rhythmbox for local exploit.) ) But it doesn't hurt anything to set up a profile.
In any case, the Rhythmbox profile didn't work I got a message error stating there was a missing last line. Still, I'm curious as to how a media file could affect security? That is, besides any of the stuff made by Microsoft, as I know Windows Media Player does use exploitable ActiveX for some of its "features". Which I'm not sure would affect Totem or LO, they don't have AX right? A media file is just a file container with a video stream and an audio stream from what I know, and maybe some files that are used to make Chapters in DVDs etc.

EDIT:
I just found this profile for totem:
```

#include <tunables/global>  /usr/bin/totem flags=(complain) {   #include <abstractions/base>     /dev/shm/ r,   owner /dev/shm/pulse-shm-1579451937 r,   owner /dev/shm/pulse-shm-2903800023 r,   owner /dev/shm/pulse-shm-2933723921 rw,   owner /dev/shm/pulse-shm-4283548248 r,   /etc/fonts/** r,   /etc/gtk-2.0/gdk-pixbuf.loaders r,   /etc/gtk-2.0/gtkrc r,   /etc/pango/pango.modules r,   /etc/pulse/client.conf r,   owner /home/*/.ICEauthority r,   owner /home/*/.config/gtk-2.0/gtkfilechooser.ini r,   owner /home/*/.config/gtk-2.0/gtkfilechooser.ini.6XUP7U w,   owner /home/*/.config/totem/state.ini r,   owner /home/*/.config/user-dirs.dirs r,  }

```
What do you think of it?

---

### Post by Hungry Man on 2012-05-02
Anything's exploitable. If there is parsing involved a buffer overflow is possible, especially if it's handled using unsafe string methods in C. If it's not validating input properly you could probably heap overflow, depending on how music is played (which I don't know.)

It allows for some kind of input - ie: the music file. That's pretty much all an attacker needs to be able to exploit it, assuming there are vulnerabilities in that area to exploit.

Not sure about that profile. I've never used any music programs on Ubuntu.

---

### Post by 0011235813 on 2012-05-02
> **Hungry Man said:**
> Anything's exploitable. If there is parsing involved a buffer overflow is possible, especially if it's handled using unsafe string methods in C. If it's not validating input properly you could probably heap overflow, depending on how music is played (which I don't know.)

It allows for some kind of input - ie: the music file. That's pretty much all an attacker needs to be able to exploit it, assuming there are vulnerabilities in that area to exploit.

Not sure about that profile. I've never used any music programs on Ubuntu.
Hang on here, I'm getting confused. Anything **executable** is exploitable, let's clarify this OK? You're talking about C in media files? Uhm... What? Why would there be any executable binaries or scripts in a media file? And if there was a media file (like .wmv) that had some sort of executable code in it, wouldn't ASLR (**A**ddress **S**pace **L**ayout **R**andomization) and DEP (**D**ata **E**xecution **P**revention- which is both software and hardware based) prevent buffer overflow (i.e crashing) techniques from being very effective??! I'm a bit confused by what you're trying to say. Does anyone know of any media files that can actually infect Rhythmbox or Banshee?

---

### Post by Hungry Man on 2012-05-02
I'm not saying there are any scripts or binaries in the media file. I'm saying there's data in the media file and the program that interprets it is written in C/C++ (Im' assuming.) What does this mean? You create dynamic buffers on the heap to store data and you're going to probably be parsing quite a lot of things that the user inputs (track data, album art, the media itself.)

You're also misunderstanding what DEP and ASLR do. I'm not trying to argue here. ASLR and DEP don't prevent buffer overflows. I can overflow a buffer with DEP on or off, it doesn't matter. What DEP would stop is the end of that overflow from being executable (hopefully) and ASLR would prevent me from being able to run the code from other areas of the address space without prior knowledge to where those areas are.

Again, you don't need some executable data in the media file.

You have two scenarios:
1) Strcopy the name/album/whatever and overflow it like that. This is easy, bounds checking isn't done in a lot of C string functions so you can drop a double where an int should be and suddenly you've overrun. There can probably be ways around safecopies idk enough about that. Not a hacker. Barely a programmer. There are other unsafe calls like strcopy that'll be easily overflowed though.

2) Heap overflow. Pretty much the same as above, you just need to get the wrong kind of information into the dynamically loaded memory. When a program needs to load up a variable amount of information it creates a pointer array with a variable size. This is pretty safe usually (I would assume. And it has performance benefits) because it can adjust itself to large files. I don't know the details on how someone would overflow on this, I assume if you create an int array (or char or whatever) and drop in a double or float it'll probably be much too large.

What happens after that? Well, if my media file is 100 bytes and the buffer is 4 bytes I now control 96 bytes of information to do with as I please. Did I need executable data in my media file? No. All I needed was the user to click the file and the media player to try to load it up.

DEP and ASLR would, of course, make things much harder from there (they wouldn't prevent the exploit.) I don't think it really makes sense to go into how to bypass those two for the sake of this conversation.

This attack is likely not that practical (it's aimed at a very tiny userbase of people who run a specific program on an OS tha tholds a low percentage, and it's likely that they use safe copies. There are other mitigation techniques implemented that drive up the cost) and you're never going to find it in the wild. You asked for scenarios, so there it is.

---

### Post by rookcifer on 2012-05-02
> **0011235813 said:**
> In any case, the Rhythmbox profile didn't work I got a message error stating there was a missing last line. 

Yeah, sorry.  I fixed it.  The profile posted should now work.

---

### Post by 0011235813 on 2012-05-02
> **Hungry Man said:**
> I'm not saying there are any scripts or binaries in the media file. I'm saying there's data in the media file and the program that interprets it is written in C/C++ (Im' assuming.) What does this mean? You create dynamic buffers on the heap to store data and you're going to probably be parsing quite a lot of things that the user inputs (track data, album art, the media itself.)

You're also misunderstanding what DEP and ASLR do. I'm not trying to argue here. ASLR and DEP don't prevent buffer overflows. I can overflow a buffer with DEP on or off, it doesn't matter. What DEP would stop is the end of that overflow from being executable (hopefully) and ASLR would prevent me from being able to run the code from other areas of the address space without prior knowledge to where those areas are.

Again, you don't need some executable data in the media file.

You have two scenarios:
1) Strcopy the name/album/whatever and overflow it like that. This is easy, bounds checking isn't done in a lot of C string functions so you can drop a double where an int should be and suddenly you've overrun. There can probably be ways around safecopies idk enough about that. Not a hacker. Barely a programmer.

2) Heap overflow with dynamic buffers. Pretty much the same as above, you just need to get the wrong kind of information into there. When a program needs to load up a variable amount of information it creates a pointer array with a variable size. This is pretty safe usually (I would assume. And it has performance benefits) because it can adjust itself to large files. I don't know the details on how someone would overflow on this, I assume if you create an int array (or char or whatever) and drop in a double or float it'll probably be much too large.

What happens after that? Well, if my media file is 100 bytes and the buffer is 4 bytes I now control 96 bytes of information to do with as I please. Did I need executable data in my media file? No. All I needed was the user to click the file and the media player to try to load it up.

DEP and ASLR would, of course, make things much harder from there (they wouldn't prevent the exploit.) I don't think it really makes sense to go into how to bypass those two for the sake of this conversation.

This attack is likely not that practical (it's aimed at a very tiny userbase of people who run a specific program on an OS tha tholds a low percentage, and it's likely that they use safe copies. There are other mitigation techniques implemented that drive up the cost) and you're never going to find it in the wild. You asked for scenarios, so there it is.
I apologise if I didn't make myself clear, I didn't ASLR and DEP would prevent buffer overflows per say, just that it would make it very difficult for a hacker to gain access to the OS if they did try the crash method, so to speak. 

What you seem to be saying is that there is a very small chance you might infect something by making a badly packaged media file. What is the point of trying to protect yourself against a threat that is currently only theoretical? 

One more question; Linux doesn't give files executable permissions by default, how does one execute a non-executable file? From what I can understand (which is, not a whole lot) a computer file stored on a drive is at the lowest level, a bunch of 0s and 1s (binary- although I suppose it could be single in analogue computers or threes {trinaries?} in future computers) and this includes plain text (which is human readable and is what a compiler uses to make machine executable) and the OS basically just treats them in different ways (a program would make API calls for example). But media files still require another executable to be "displayed" so to speak of. I suppose if the program treated the media files as if it were "executable" (that is, can run calculations in the transistors/cells {in biological computers} of the CPU or GPU[via something like OpenGL]) and can make different data at the end of it (I'm putting it simply here). But media players shouldn't treat media files like executables unless the darn thing requires it (in things like the not-so-venerable ActiveX). Am I getting this right?

---

### Post by Hungry Man on 2012-05-02
All threats are theoretical until they're not. Maybe this will never be exploited and maybe it will be. If I were to bet, I'd bet that it never gets exploited. But setting up an apparmor profile takes all of 5 minutes... so I don't see any issue with a user doing so.

I'm not sure how media programs work. ASLR and DEP don't apply to all programs. EX: Java with a JIT compiler by necessity creates executable code, which means that it's vulnerable to a whole set of other attacks and needs to make use of a whole set of other mitigations. Worth noting since, again, I have close to no idea how th emusic program works.

> One more question; Linux doesn't give files executable permissions by default, how does one execute a non-executable file? F
You don't. If my malicious payload is a music file I never execute that file. The user simply double clicks it and what executes is the program (totem? I'll call lit totem.) So I, the hacker, get you to download the music file (or I use an exploit in your browser or plugin to drop it, whatever) and then you the user open the file. The file doesn't need exec permissions. I can open a text file without executing it, right? What executes is "notepad.exe" or gedit or whatever and it's notepad.exe that I'm exploiting.

At no point is the media player "Executing" the file. Even if the file were marked executable it wouldn't matter, there's no code in there. There's no script saying "do X if Y" - it's simply data. Or rather, there's virtually no code. I'll have "datadatadatadata*endofbuffer*code" in my media file. So, it wouuld be like a song with code attached at the end... sorta.

So (in one scenario, the second listed) the music player loads up the media file (in the other it would copy or read data from the file, any data will do such as the artist title etc.) The file is too large and overruns the buffer. What's left is a hanging piece of code (that I'd appended) now in the address space. Without DEP I'm able to do whatever I want with this code, I can execute it right then and there. With DEP I have to jump through a hurdle (not a hard one.)

---

### Post by 0011235813 on 2012-05-02
> **Hungry Man said:**
> All threats are theoretical until they're not. Maybe this will never be exploited and maybe it will be. If I were to bet, I'd bet that it never gets exploited. But setting up an apparmor profile takes all of 5 minutes... so I don't see any issue with a user doing so.

I'm not sure how media programs work. ASLR and DEP don't apply to all programs. EX: Java with a JIT compiler by necessity creates executable code, which means that it's vulnerable to a whole set of other attacks and needs to make use of a whole set of other mitigations. Worth noting since, again, I have close to no idea how th emusic program works.


You don't. If my malicious payload is a music file I never execute that file. The user simply double clicks it and what executes is the program (totem? I'll call lit totem.) So I, the hacker, get you to download the music file (or I use an exploit in your browser or plugin to drop it, whatever) and then you the user open the file. The file doesn't need exec permissions. I can open a text file without executing it, right? What executes is "notepad.exe" or gedit or whatever and it's notepad.exe that I'm exploiting.

At no point is the media player "Executing" the file. Even if the file were marked executable it wouldn't matter, there's no code in there. There's no script saying "do X if Y" - it's simply data. Or rather, there's virtually no code. I'll have "datadatadatadata*endofbuffer*code" in my media file. So, it wouuld be like a song with code attached at the end... sorta.

So (in one scenario, the second listed) the music player loads up the media file (in the other it would copy or read data from the file, any data will do such as the artist title etc.) The file is too large and overruns the buffer. What's left is a hanging piece of code (that I'd appended) now in the address space. Without DEP I'm able to do whatever I want with this code, I can execute it right then and there. With DEP I have to jump through a hurdle (not a hard one.)
I think it all comes down to what is defined by executable. I think that in the strict sense of the word, what you're describing isn't "executable" as such, more like... It *tells* the program to do something that would be considered *malicious* by the programmer/hacker and the user. 
But yeah, I think I understand what you're saying.

---

### Post by Hungry Man on 2012-05-02
My media file does not have its own address space, a heap, a stack, libraries, or function calls. That's all I mean. Instead it is a piece of **data** that is read by a program. 

In the end my media file does lead to me executing code though. It's all semantics. 

The point I'm trying to get across is that you can take pretty much any kind of program and if it takes some kind of input you can probably exploit that.

---

### Post by 0011235813 on 2012-05-02
> **rookcifer said:**
> Yeah, sorry.  I fixed it.  The profile posted should now work.
I'm afraid not. When I turn off rhythmbox, enforce the profile and reload it into the kernel module (following bodhi.zazen's instructions) Rhythmbox refuses to start. 

PS: I just thought of a metaphor that would describe the deadly media file virus. Basically, it's like; if I told you to take of your left arm, and you (the media player) did so, that would basically be an infection. So it's not being executed (I'm not making API calls to your neurological brain to cut-of-left-arm) but I'm telling the conscious brain (media player) to do something. Which of course, would require you to be insane (vulnerability within the media player) to happen.

---

### Post by rookcifer on 2012-05-02
> **Hungry Man said:**
> You don't. If my malicious payload is a music file I never execute that file. The user simply double clicks it and what executes is the program (totem? I'll call lit totem.) So I, the hacker, get you to download the music file (or I use an exploit in your browser or plugin to drop it, whatever) and then you the user open the file. The file doesn't need exec permissions. I can open a text file without executing it, right? What executes is "notepad.exe" or gedit or whatever and it's notepad.exe that I'm exploiting.

At no point is the media player "Executing" the file. Even if the file were marked executable it wouldn't matter, there's no code in there. There's no script saying "do X if Y" - it's simply data. Or rather, there's virtually no code. I'll have "datadatadatadata*endofbuffer*code" in my media file. So, it wouuld be like a song with code attached at the end... sorta.


This would be sort of like the Flashback trojan that hit OSX recently.  OSX, like Linux, uses a default umask of 022.  What this means is that newly created files are not executable by default.  However, in the case of Flashback, the user had his browser exploited via a Java flaw, then redirected to a malicious site.  At this site, a trojan was downloaded and automatically placed into the users /home folder.  This file should not be executable, yet somehow it was.  

I guess I just don't understand the Flashback trojan because no one that I have seen has really described (as the lowest levels) how it works.  So, because of this, I am kinda confused how it bypassed the no-executable bit.

---

### Post by Hungry Man on 2012-05-02
Run aa-logprof and see what's missing.

It's less that I'm getting the program to do what I want and more that I'm making use of the programs executable address space. But that's pretty much the general idea.

---

### Post by Hungry Man on 2012-05-02
> **rookcifer said:**
> This would be sort of like the Flashback trojan that hit OSX recently.  OSX, like Linux, uses a default umask of 022.  What this means is that newly created files are not executable by default.  However, in the case of Flashback, the user had his browser exploited via a Java flaw, then redirected to a malicious site.  At this site, a trojan was downloaded and automatically placed into the users /home folder.  This file should not be executable, yet somehow it was.  

I guess I just don't understand the Flashback trojan because no one that I have seen has really described (as the lowest levels) how it works.  So, because of this, I am kinda confused how it bypassed the no-executable bit.
Java doesn't support ASLR and it **barely** supports DEP. DEP separates data from code, exec from no-exec. Java just marks everything "exec" so it doesn't matter.

That said, even with proper DEP it's trivial to bypass without ASLR. OSX has awful ASLR anyways.

Because Java is a JIT compiler everything it does is marked executable. So if you exploit Java you're free to use any part of its address space.

I don't know the details of the exploit. If you exploit Java and download the payload you can just use Java to then run the payload without user permission.

---

### Post by jerome1232 on 2012-05-02
> **rookcifer said:**
> This would be sort of like the Flashback trojan that hit OSX recently.  OSX, like Linux, uses a default umask of 022.  What this means is that newly created files are not executable by default.  However, in the case of Flashback, the user had his browser exploited via a Java flaw, then redirected to a malicious site.  At this site, a trojan was downloaded and automatically placed into the users /home folder.  This file should not be executable, yet somehow it was.  


Installers for OSX generally come as disc images, double clicking mounts the disk image which autoruns and will have it's own preset permissions. The user doesn't have to mark anything as executable this way.

Trojans will be trojans, they generally exploit the user not the system.

---

### Post by Hungry Man on 2012-05-02
True. But in the case of Flashback it was definitely a case of exploiting the system.

---

### Post by 0011235813 on 2012-05-02
> **rookcifer said:**
> This would be sort of like the Flashback trojan that hit OSX recently.  OSX, like Linux, uses a default umask of 022.  What this means is that newly created files are not executable by default.  However, in the case of Flashback, the user had his browser exploited via a Java flaw, then redirected to a malicious site.  At this site, a trojan was downloaded and automatically placed into the users /home folder.  This file should not be executable, yet somehow it was.  

I guess I just don't understand the Flashback trojan because no one that I have seen has really described (as the lowest levels) how it works.  So, because of this, I am kinda confused how it bypassed the no-executable bit.
From what I gather, plugins like Java (Java has nothing to do with Flash exploits by the way, that's a misleading name it has- along with all the other misleading FUD articles on the 'net like a certain "Ed" likes to troll about) cannot make file operations within the users directories (besides /tmp). Now of course, it can compromise the browsers itself (which can make *some* file operations in the user its running as- depending on your AA profile) but that doesn't make any sense. Why? Because the Flashback **trojan** (emphasis on the word Trojan) is browser independent so what this really is, is a phishing scam. That is, unless the plugin itself didn't get sandboxed properly, which is the fault of Mac OSX and not the fault of Java really.

---

### Post by jerome1232 on 2012-05-02
> **Hungry Man said:**
> True. But in the case of Flashback it was definitely a case of exploiting the system.

Do you have a source, everything I can find about this trojan claims it posed as a legitimate installer for flash. Requiring the user to download and run it and give it sudo permission to then install it's malicious code.

If my information is correct this is a classic case of exploiting... or tricking the user, not exploiting the system. Could happen just as easily with a deb, rpm, or binary on a Linux system.

---

### Post by rookcifer on 2012-05-02
> **jerome1232 said:**
> Installers for OSX generally come as disc images, double clicking mounts the disk image which autoruns and will have it's own preset permissions. The user doesn't have to mark anything as executable this way.

Trojans will be trojans, they generally exploit the user not the system.

The later versions of Flashback did not require any user interaction at all.  It was a drive-by download.  If you visited a site with a browser that had outdated Java, the trojan would somehow download itself and then execute itself.  How it does this I do not know.  I figured the fact that it didn't have execute rights would stop it, but this doesn't appear to be the case.  Again, I am trying to figure out how exactly it bypassed that.  None of the blogs out there have explained it.

---

### Post by Hungry Man on 2012-05-02
Flashback has been around for a while. It used to pose as a Flashplayer installer, which required the user to give it permission. Now it exploits the Java vulnerability and does not require permission. If your Java is patched it falls back to its old method ie: tricking the user.

> 
If my information is correct this is a classic case of exploiting... or tricking the user, not exploiting the system. Could happen just as easily with a deb, rpm, or binary on a Linux system.
In the case of the old "social engineering" method, it could happen either way. Just like installing any program. The difference being that Linux users tend to get their packages from "trusted" repositories instead of the internet, and all updates for programs like Flash and Java are handled automatically by the OS. This means that it should, theoretically, be more difficult to trick a user into downloading a fake update/program because they get their programs/ updates through the OS.

---

### Post by jerome1232 on 2012-05-02
Thanks, that makes a lot more sense. I guess that's enough derailing the topic. :D

---

### Post by rookcifer on 2012-05-02
> **Hungry Man said:**
> Now it exploits the Java vulnerability and does not require permission. If your Java is patched it falls back to its old method ie: tricking the user.

How does the Java exploit give it permission to execute?  It is my understanding that the Java exploit allows the trojan to download to the machine without user interaction.  After that this trojan then downloads a malicious payload from a botnet that then executes itself and performs further actions.

So, I guess I am wondering how does it bypass the umask setting of 022?  Should it not be impossible for this newly created file to execute?  Or does the Java exploit somehow allow it to bypass this?

---

### Post by Hungry Man on 2012-05-02
I don't know enough about how OSX/BSD permissions work. I would think it's as simple as Windows - you can download and execute any .exe or .msi or whatever.

If the exploit gives them root it can do whatever. If the permissions allow the program to manipulate files that it owns' permissions it can change the payload how it likes. It could mmap() or virtualalloc() it and get it to execute that way.

Not really sure how it did it or how the best way to go about doing it would be.

---

### Post by rookcifer on 2012-05-02
> **Hungry Man said:**
> I don't know enough about how OSX/BSD permissions work. I would think it's as simple as Windows - you can download and execute any .exe or .msi or whatever.

Yeah, from reading I found out that OSX uses the default umask of 022, which is the same as most Linux distros.  This means new files should not be executable.

> If the exploit gives them root it can do whatever. If the permissions allow the program to manipulate files that it owns' permissions it can change the payload how it likes. It could mmap() or virtualalloc() it and get it to execute that way.

Yeah this malware didn't need root -- it worked directly within the user's directory.  So, I was just wondering how it overcame the umask setting.  Only thing I can figure is that since it exploited the browser, it may have gained the permissions that way (i.e, it assumes the same permissions the browser has automatically, which probably allows it to execute).  Though this is just a guess.

---

### Post by Hungry Man on 2012-05-02
It wouldn't get the browsers permissions, it's just a plugin and it has its own separate permissions.

---

