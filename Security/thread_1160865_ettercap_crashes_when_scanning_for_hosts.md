---
title: "ettercap crashes when scanning for hosts"
date: 2009-05-16
forum: Security
---

### Post by Hilko on 2009-05-16
Hello, when I launch the ettercap GUI from the menu or from the terminal with this command i get an error:

```
:~$ sudo ettercap -G

ettercap NG-0.7.3 copyright 2001-2004 ALoR & NaGA

Dissector "dns" not supported (etter.conf line 70)
Ooops ! This shouldn't happen...
Segmentation Fault...

```

But the GUI starts. Then i do 'Start Unified Sniffing' and after that I try to scan for hosts. The moment I select 'scan for hosts' from the menu. Ettercap just quits.

Can anyone help me with this ? Please ?

-----------
I'm running Ubuntu 9.04 for 64bit

---

### Post by Hilko on 2009-05-18
Has anyone seen this problem before ?

---

### Post by The Tronyx on 2009-05-18
Ettercap is an older program that hasn't been updated in around...4 years, so there may some issues.  If you don't see it resolved here you could try the ettercap forums (which haven't had a post in around a month) or simply e-mailing the original developers directly.

I should preface this by saying that I am not really sure if I can solve your problem but what happens if you scan for hosts first then do unified sniffing?

Cheers.

---

### Post by Hilko on 2009-05-20
Thanks for your reply. I cannot scan for hosts. I have to start unified sniffing first before the menu 'hosts' appears.

---

### Post by SilvaRizla on 2009-07-01
I have this problem, the only thing I can see atm is there isn't and etter.conf file so I'm doing some more digging.

---

### Post by SmarterThanMyPhone on 2009-07-02
you need to specify the interface in the etter.conf file, you could also try; 
ettercap -i [interface] -C
Thats how I run it works for me.
hth

---

### Post by uncr347ivenam3 on 2009-07-14
```
User@Host:~$ sudo ettercap -i wlan0 -C
[sudo] password for User: 

ettercap NG-0.7.3 copyright 2001-2004 ALoR & NaGA

Dissector "dns" not supported (etter.conf line 70)
Ooops ! This shouldn't happen...
Segmentation Fault...

Please recompile in debug mode, reproduce the bug and send a bugreport

User@Host:~$
```

---

### Post by Hilko on 2009-07-15
Problem solved: [URL="https://launchpad.net/~timothy-redaelli/+archive/ppa"]https://launchpad.net/~timothy-redaelli/+archive/ppa
[/URL]
Uninstall your current ettercap version and download and install the recompiled .debs from above (I think you will only need ettercap-common and ettercap-gui not the other one). Also, if you are running it from terminal don't forget to run it as super user - "sudo ettercap -G"

---

### Post by maransor on 2009-07-23
I got the same problem and i don't know how to solve it

Code:
 	:~$ sudo ettercap -G

ettercap NG-0.7.3 copyright 2001-2004 ALoR & NaGA

Dissector "dns" not supported (etter.conf line 70)
Ooops ! This shouldn't happen...
Segmentation Fault..

---

### Post by uncr347ivenam3 on 2009-07-26
The solution that Hilko gave seems to have fixed the problem for me.  At least, no segfault when scanning for hosts.

---

### Post by TooCrooked on 2009-08-02
this kinda worked for me... i had the issue where ettercap would just close. when i ran it from the command line, i got that whole "[COLOR=Red]Dissector "dns" not supported (etter.conf line 70)[/COLOR]" thing, but i didnt get any other lines under it. ettercap would then open, but i couldnt do the unified sniffing.

when i ran the command with the -i option, i could select unified sniffing, but when i tried to scan for hosts, it would crash and the terminal would say something about needing to recompile.

i eventually uninstalled it from the package manager and then i began to do the whole thing with getting the new debs noted in the post above... when i did finally get to installing the debs, i got an error (that i paraphrase) complaining that the package already existed. given that, i installed that package and tried again.

it didnt work. it still crashed out when i selected the interface. however, when i tried to see what would happen if i used the -i option, i was able to scan for hosts successfully.

so basically an uninstall/reinstall worked. on item to note, which probably has reall no bearing on this, is that i first installed ettercap through the commandline...

---

### Post by go_beep_yourself on 2009-08-03
I installed the debs posted and now ettercap seems to work if ran with the ncurses interface, not the gui.

---

### Post by SilvaRizla on 2009-08-07
Thanks for taking the credit on this one Hilko ;)

I need to check with everyone else here that when on this package, when you scan for hosts, they are all detected and not just the router, I seem to be having a problem

---

### Post by metRo_ on 2010-05-31
> metRo_ •  
Not allowed here
Sorry, you don't have permission to access this page.

You are logged in as metRo_.


Can you send me the files?

---

### Post by acidblue on 2010-07-17
I get the same thing.
"don't have permissions"
Any chance us mere mortals can get access to the files?

---

### Post by piyush.neo on 2010-08-03
hey i have similar problem 
```

[piyush@localhost ~]$ sudo ettercap-gtk

ettercap NG-0.7.3 copyright 2001-2004 ALoR & NaGA


(<unknown>:2315): GLib-GObject-WARNING **: gsignal.c:3079: signal name `depressed' is invalid for instance `0x9f9ee00'

(<unknown>:2315): Gtk-WARNING **: Invalid text buffer iterator: either the iterator is uninitialized, or the characters/pixbufs/widgets in the buffer have been modified since the iterator was created.
You must use marks, character numbers, or line numbers to preserve a position across buffer modifications.
You can apply tags and insert marks without invalidating your iterators,
but any mutation that affects 'indexable' buffer contents (contents that can be referred to by character offset)
will invalidate all outstanding iterators
Ooops ! This shouldn't happen...
Segmentation Fault...



```
and i also can't access those file..
Any solutions...

---

### Post by monty47 on 2010-08-21
You can get the files here ; [https://launchpad.net/~timothy-redaelli/+archive/drizzt/+packages](https://launchpad.net/~timothy-redaelli/+archive/drizzt/+packages) (thanks to Thimothy)
I have another problem though, ettercap isn't showing http sniffed password, can you tell me if it is the case for you with this version?
thanks a lot

---

### Post by vinigfer on 2010-12-16
Thanks Monty47 and Thimothy! Those link and packages were helpfull. How about sending the update of ettercap to the ubuntu and debian repositories so that other people could benefit from them? Just a sugestion.

Regards

---

### Post by Phantom3D on 2011-01-13
When I run scan for hosts it still crashes here..
And running the -C interface seems fine at the start, but it bugges after scanning for hosts. Getting weird symbols all over the terminal.

I downloaded the common and GTK *.deb files...

Any news on this?

---

### Post by cariboo on 2011-01-13
How are you installing etherape? I Installed it using synaptic, and it works out of the box on my highly experimental Natty/gnome 3 install.

---

### Post by Phantom3D on 2011-01-13
I did it from Ubuntu Software Center, and now also from the downloaded *.deb files..

---

### Post by cariboo on 2011-01-13
I would suggest you try System->Administration->Synaptic Package Manager, search for etherape, then highlight it and click the properties button, then the dependencies tab to see if you have all the dependencies installed.

---

### Post by fredo994 on 2011-01-16
It works perfectly but I haven`t been able to arp poison host in my lan natwork does someone have any suggestions or tutorials to do that

---

### Post by buckbugs on 2011-10-06
> **monty47 said:**
> You can get the files here ; [https://launchpad.net/~timothy-redaelli/+archive/drizzt/+packages](https://launchpad.net/~timothy-redaelli/+archive/drizzt/+packages) (thanks to Thimothy)
I have another problem though, ettercap isn't showing http sniffed password, can you tell me if it is the case for you with this version?
thanks a lot

it wasn't work on my notebook
upgrading to ettercap 1:0.7.3-2ubuntu1 but the same error still occur. 

#Dissector "dns" not supported (etter.conf line 70)

really appreciate if anybody can help on this

---

### Post by randomfuoco on 2012-04-02
Hi I realize this is an old topic but it's the closes thing I found to helping me so far. I am very new with ubuntu and confused as to what I do with the packages on launchpad. Which ones am I supposed to download? Is one for 64 and another 32 bit? 

I think I'm 32 bit but I don't really know. If someone could help guide me through what I'm supposed to do I would greatly appreciate it.

Linux version 2.6.35-32-generic (buildd@palmer) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #64-Ubuntu SMP Mon Jan 2 23:31:33 UTC 2012

---

### Post by phoenixflames on 2012-04-15
> **randomfuoco said:**
> Hi I realize this is an old topic but it's the closes thing I found to helping me so far. I am very new with ubuntu and confused as to what I do with the packages on launchpad. Which ones am I supposed to download? Is one for 64 and another 32 bit? 

I think I'm 32 bit but I don't really know. If someone could help guide me through what I'm supposed to do I would greatly appreciate it.

Linux version 2.6.35-32-generic (buildd@palmer) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #64-Ubuntu SMP Mon Jan 2 23:31:33 UTC 2012


To check if you are 32 or 64 bit use this:
```
uname -m
```

Generally, 32 bit will work on either or, so it doesn't matter.

---

