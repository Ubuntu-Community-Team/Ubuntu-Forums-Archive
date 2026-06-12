---
title: "My friend has a virus, what should I do?"
date: 2009-05-17
forum: The Cafe
---

### Post by hyperdude111 on 2009-05-17
I was on pidgen using msn then i received a message from a friend which was rather out of context to our normal conversations

> First:
damn, saw naked pics of yours or maybe the one in pic is similar to you :D  .... crazy lol    [http://my-secret-gallery-download.com/pic_gallery.html](http://my-secret-gallery-download.com/pic_gallery.html)

Then:
phewww +o( unbelivable, is that you??? who ever is it...is really similar to you lol ...     [http://my-secret-gallery-download.com/pic_gallery.html](http://my-secret-gallery-download.com/pic_gallery.html)


He then signed out, not leaving me a chance to reply.

I had used this friends laptop before, and knew he was using vista and my first thaught was......... virus.

So being on linux and not afraid of the casual windows exe i went to the webpage which said:

> PARTY PICTURES

Click on the image to download the party pictures gallery...

(Click Open or Run when prompted.)

A donwload thencame up asking me to download a ".scr" file. I searched .scr file and found this page [http://www.fileinfo.com/extension/scr](http://www.fileinfo.com/extension/scr) which worryingly quotes:

> Generic executable script created or used by a number of possible programs; when opened, the script typically runs a series of commands in the order they are listed in the script; most script files are editable text documents.

-----------
What should i do?

---

### Post by Jim! on 2009-05-17
Your friend likely got a virus while looking at pornographic material. Of course, I'm sure it's all just a big mistake!

Sorry! I just realized I didn't even answer your actual question! If your friend has a virus and you're able to get access to his computer (ie. If he lives relatively close to you) then you should offer to fix his computer, assuming you know how to that is. If you don't then a quick, informative thread on a Windows discussion forum should be all the assistance you need. :)

---

### Post by Screwdriver0815 on 2009-05-17
did you download the file? Have you opened it? If not: just delete it. If yes... I don't know. Do you have strange behaviour in the system?

what else can you do... maybe tell your friend that his machine is a virus-slingshot? ;) and that he should do something against this, which means: he should not visit porn-sites anymore :D

I just saw that .scr files are not executed by Linux... but you should check anything anyway if you have opened the file - just to be sure

---

### Post by Sef on 2009-05-17
.exe files don't work on Ubuntu nor nonWindows oses.   I would let your friend know, so he can delete it.

---

### Post by hyperdude111 on 2009-05-17
I didn't download it, however i think it is only executable in mac and windows. 

I could download it in a virtual machine, open it in a text editor to see what it is meant to do.

I could execute it in a winxp virtual machine and monitor its effects.
__

This friend is not very technical, using itunes is pain for him. So not sure how to tell him to remove it.

---

### Post by Jim! on 2009-05-17
Does he have up-to-date virus prevention software installed? I'm sure he'd be able to nab the virus using AVG and (not guarenteed) he may be able to track the virus down with the Windows 'search' function and just manually delete it. I can remember that working with one virus for me a long time ago. 

Wow, it's weird talking about this sort of issue on Windows - I haven't used it in so many years!

---

### Post by Kareeser on 2009-05-17
You should advise that he remove the virus. When I faced this problem with a client of mine, I just ran the two "MSN Virus Remover" programs, and booted up into a Live CD environment, ran ClamAV, and removed everything I found by hand.

---

### Post by whoop on 2009-05-17
> **hyperdude111 said:**
> I didn't download it, however i think it is only executable in mac and windows. 

I could download it in a virtual machine, open it in a text editor to see what it is meant to do.

I could execute it in a winxp virtual machine and monitor its effects.
__

This friend is not very technical, using itunes is pain for him. So not sure how to tell him to remove it.
I just downloaded it. It's a windows only binary:
```

4d 5a 90 00 03 00 00 00 04 00 00 00 ff ff 00 00 b8
00 00 00 00 00 00 00 40

```

It looks like it was created using some malware construction kit, cause it seems to contain some generic malware code. It's not worth dissecting. If you want to be a good person you can send it to an antivirus company as a suspicious file as it will not be detected by allot of virus scanners yet, I think.

---

### Post by Screwdriver0815 on 2009-05-17
this is how I would try to get rid of the virus (from remembering how I did it in the past in Xp):

scan the system with antivir (or another good virus scanner)

scan the system with AdAware

test if the virus comes up again. If not: everything is fine.

If yes:

go to [http://www.hijackthis.de/en](http://www.hijackthis.de/en) and download the hijackthis program. BTW: this program scans the system for all processes being executed. 

run the hijackthis tool and copy-paste the resuting logfile into the analyze box on [http://www.hijackthis.de/en](http://www.hijackthis.de/en) , start the analyse and kill all processes in connection with the virus. 
BUT: the hijackthis program also lists processes as evil which have nothing to do with the virus itself and which are maybe wanted on the system! So he has to know what he is doing!

then delete the crap from the registry. To do this, go to start -> execute and type in regedit and go to the HKEY_LOCAL_MACHINE, HKEY_CURRENT_USER, HKEY_USERS

and search for entries which have the same name as the virus scanners have put out for the virus. Then delete this. BUT: if he deletes something different (not evil) then he does extra harm to the system. So he has to know what he is doing!

The reason for doing this in the registry is: even when the virusscanner deletes the virus, it comes up again and again because mostly the viruses install themselves in the registry and take advantage of this stupid registry-system in windows.

This is how I did it in Xp, maybe in Vista this is different :confused:

---

### Post by michaeldt on 2009-05-17
Or maybe his msn account has been hacked? 

The reason I suggest this is that if his PC is on, I would assume he'd be signed into msn. But if his msn signed on, sent the message and then signed off, it sounds more like someone who has a lot of hacked msn accounts and then has a script which signs them on, sends the same message to all the contacts and signs off.

Of course, it might be due to a keylogger or something similar which got his account hacked in the first place but there we go.

---

### Post by Corelogik on 2009-05-17
> **hyperdude111 said:**
> I didn't download it, however i think it is only executable in mac and windows. 


.scr is NOT a Mac executable. Running OS X (10.4.11) PPC G5. .scr is a Windows file normally associated with screen savers.

I tried to quote the output from a text file conversion. Wouldn't let me, so I broke the plain text into 2 files and attached them.

---

### Post by HavocXphere on 2009-05-17
.scr is a renamed .exe...nothing else. You can rename any exe, put it in the windows folder and then its selectable as a screensaver.

The message you got is definitely a virus...I remember reading reports with that exact same BS about pics that look like you. Can't remember the name of the virus though.
EDIT: Make that malware...not sure whether its a virus or bot or what.

If you want to help him sort this out, load up a copy of windows in a VM, download procmon from sysinternals (its on the MS site). Then run the exe/scr in the VM and use procmon to record what it does.

---

### Post by steev182 on 2009-05-17
It looks like his account has been hacked, get him to change his msn password, then see if the false messages stop. I've this exact behaviour before from users at work and once their passwords get changed they are as right as rain.

---

### Post by Saint Angeles on 2009-05-17
chicken noodle soup
7-up
day-quil

and plenty of bed rest.

---

### Post by dragos240 on 2009-05-17
I would recommend installing linux to him :)

---

### Post by Eclipse. on 2009-05-17
Its a bot, your friend has signed up for something he shouldn't have.

Tell him to change his password and it will stop.

---

### Post by pwnst*r on 2009-05-17
what should you do?  teach him better surfing habits.

---

### Post by hyperdude111 on 2009-05-17
Im getting woried now, 
Another one of my friends sent me a message with this link [http://imagetalez.com/?user=ubuntuf&image=DSC00678.JPG](http://imagetalez.com/?user=ubuntuf&image=DSC00678.JPG) (Where it says ubnutu it originally said my name, i just changed that.

After reading their terms and conditions this line stood out 
>  We may temporarily access your MSN account to do a combination of the following: 1. Send Instant Messages to your friends promoting this site. 2. Introduce new entertaining sites to your friends via Instant Messages.  

Wow these things spread

---

### Post by michaeldt on 2009-05-17
> **hyperdude111 said:**
> Im getting woried now, 
Another one of my friends sent me a message with this link [http://imagetalez.com/?user=ubuntuf&image=DSC00678.JPG](http://imagetalez.com/?user=ubuntuf&image=DSC00678.JPG) (Where it says ubnutu it originally said my name, i just changed that.

After reading their terms and conditions this line stood out 


Wow these things spread

Time to educate your friends.....

---

### Post by sim-value on 2009-05-17
about a third of my MSN contacts have this .. well well ...

---

### Post by ugm6hr on 2009-05-17
Indeed, there seems to have been a flurry of malicious emails and IMs from MSN users.

I've had at least 3 friends affected.

---

### Post by sanderella on 2009-05-17
When I read this question, my first thought was a biological virus infecting his body. I forgot about computer viruses. Comes of using 'buntu for 5 years....what's a virus?????:KS

---

### Post by Dr. C on 2009-05-17
> **Sef said:**
> .exe files don't work on Ubuntu nor nonWindows oses.   I would let your friend know, so he can delete it.

With respect this is incorrect. .exe files can work in Ubuntu and in other GNU / Linux distributions if one has Wine / Crossover or the propriety Cedga / WineX installed. They may in some cases also work on DOS (FreeDOS, MS DOS etc), OS/2, ReactOS, Mac OS X, among other non Windows OSes.

While there was a study where it was attempted to infect GNU / Linux with Windows viruses without success, it is a few years old and the Wine project has made great progress since then. 

A blanket statement that Windows malware does not work on GNU / Linux can lead to a dangerous false sense of security.

---

