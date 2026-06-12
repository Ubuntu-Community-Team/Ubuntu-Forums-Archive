---
title: "Big Thumbs Down for Zeitgeist"
date: 2016-05-25
forum: Security
---

### Post by yoshii on 2016-05-25
Has anybody experienced any wierd issues with Zeitgeist?

I don't want to (yet) get into the deep details of what happened to my Ubuntu Studio setup.  
I was able to extinguish the problem, but pretty much the whole hack/spyware subarea that got created on my system without my permission was reliant upon Zeitgeist for it's persistent existence.  And it was involved with making visible backup copies, without my permission, of files I had recently deleted.  

I know Zeitgeist may have normal regular uses, but on my system, it was being used against me, the admin and Digital Audio Workstation owner.  
In my opinion, it really has no business being on Ubuntu Studio and is just extra bloat, like Samba, for those of us who never use Samba services or programs.  

Does anybody else have any experience with Zeitgeist being used as a vector for spyware/unauthorized installs/copies/system modifications?

---

### Post by bashiergui on 2016-05-25
The beauty of linux is you can customize it however you like. Many people remove zeitgeist. Here's a tutorial how:
[http://linuxaria.com/howto/how-to-remove-zeitgeist-in-ubuntu-and-why](http://linuxaria.com/howto/how-to-remove-zeitgeist-in-ubuntu-and-why)

 I haven't heard of any malicious uses of zeitgeist.

---

### Post by ventrical on 2016-05-27
It was annoyance when they used it in Unity/Precise and onwards.. but nothing here..

---

### Post by yoshii on 2016-05-28
Thanks guys.  

Actually I recently noticed that Zeitgeist seems to have been phased out of Ubuntu Studio v16.04 LTS even though it was a part of v14.04.3 LTS.  
I just recently installed Ubuntu Studio v16.04 LTS so it's actually not even a problem anymore.  

I used CatFish to search the filesystem for any file traces of it, and except for some language files and a single Zeitgeist-Explorer.PNG image, it's all gone.  
So I delete those too so now there's no traces of it.

---

### Post by Habitual on 2016-06-02
IME, it was great, until it broke.

---

### Post by yoshii on 2016-06-02
how did it break?

---

### Post by mc4man on 2016-06-02
> **yoshi2 said:**
>  the whole hack/spyware subarea that got created on my system without my permission was reliant upon Zeitgeist for it's persistent existence.  And it was involved with making visible backup copies, without my permission, of files I had recently deleted.  
Does anybody else have any experience with Zeitgeist being used as a vector for spyware/unauthorized installs/copies/system modifications?
Sounds quite unlikely, care to offer some proof.

---

### Post by Habitual on 2016-06-02
> **yoshi2 said:**
> how did it break?
Well, I only have the highlight reel for details now.
It was OpenSUSE 11.x and Xfce and some darned widget. 
It used to catalogue opened files on the system and this widget presented it nicely.
One day it didn't.

I never gave it much notice whether it worked or not after that...

---

### Post by yoshii on 2016-06-03
[i]I can't offer any proof anymore (but I would if I could)...  

I got fed up with trying to delete/remove the folder that was logging and copying my files; the folder kept getting reinstalled.  It was probably somebody's customized version of zeitgeist and not the basic version installed by default into older versions of Ubuntu Studio.  Also, I forget where I saw it now, but part of the ownership details of the malware-used folder were displayed not in English (my native language), but in something that looked like Chinese or some other Asian language, even though I set up the entire computer to use US English as the global default.  And I may have even used BleachBit to remove the unneeded language packs.  

It's not entirely far-fetched.  I had somebody break into my apartment about 4 times earlier this year and noticeably tampered with two out of three computers.  
And if you study computer security websites regularly, you realise that there's tons of different types of attacks and variations and custom-designed attacks.  

Since I didn't want to deal with an infected and compromised system, I checked the status of my backups (on DVD-ROM) and just erased the entire hard drive and installed a completely different version of Linux (which coincidentally had no traces of Zeitgeist).  I test drove that Linux version for a while until I realised that I didn't like it as much as Ubuntu Studio.  

So then I erased that and installed Ubuntu Studio again, but this time using the most recent .ISO (which doesn't install Zeitgeist either).  
I think I also changed my password during this phase and at earlier stages.  

I haven't had any issues since then.  

I didn't lose any intellectual property so I didn't archive the details of the breach/issue.  
But I didn't imagine it.  

On a different laptop system, I manually deleted all traces of Zeitgeist and although I get some warning messages from within aptitude about the missing zeitgeist stuff, everything works as intended and I've had no issues on that system.  

Not everything that is real can be easily documented for proof.  Since I didn't install or initiate the use of Zeitgeist, I can't recreate the situation either.  It wasn't me who did it.  
I happen to live in an apartment complex where there are a significant number of people who are on probation for breaking the law and they have to do community service.  So there's already some suspects around for whoever broke into my apartment.  I changed the locks of course.  And one of the tampered-with (used) laptops I erased and took to a computer recycling place.  I told them about what had happened with it, so they would be warned.  And they said they'd recycle it responsibly.  [/i]
[b]
Anyways, thanks Habitual for the reply about OpenSUSE and Xfce and the widget and whatnot.  
[/b]

---

### Post by Habitual on 2016-06-13
> **yoshi2 said:**
> [I]
So then I erased that and installed Ubuntu Studio again, but this time using the most recent .ISO (which doesn't install Zeitgeist either).  
I think I also changed my password during this phase and at earlier stages.  

I haven't had any issues since then.[/I]
Good bit of work you did, so congrats. New sources and new passwords all the way around!

---

### Post by yoshii on 2016-06-14
Thanks :)

---

### Post by xen3 on 2016-06-17
So you are saying that your system got infected by malware and it used Zeitgeist to track what files you had recently used, in order to copy those?

Zeitgeist from what I see merely stores frequency information about files and documents. And programs.

You could call it a frequency database. I can imagine some malware would or could try to use it, particularly for documents, but in general I don't know what for; if you want data, and if you know that data is going to be stored in some default location, you won't need anything additional like that program.

Zeitgeist has a good sound to me but I thought it would be a local versioning system :p.

Does anyone know of a local versioning system? Perhaps, like, something like OneDrive, but something that keeps a good version history, is remotely accessible, and runs a local daemon that does an upload on every save? I think the [SparkleShare]("http://www.sparkleshare.org") tool does exactly that, but it doesn't seem exactly brilliant (the way it was intended).

Also

> **mc4man said:**
> Sounds quite unlikely, care to offer some proof.

Seems rather inappropriate considering that this is not a thread meant for establishing undeniable truths, nor is it some scientific forum for truth validation. It seems to imply that the one asking the "proof" (you really mean: evidence) has some kind of right or entitlement of being "convinced" when another person's "believing" is not a requirement at all.

All in all I don't see why anyone would need to prove anything.

Then you can say "Then I won't believe it" and then it would be like "Okay, no problem there?" and the sky would not tumble and the earth would not shake.

Hope you get what I'm trying to say. True/untrue doesn't give more information.

All in all the effort in seeing whether something is true for you is on behalf of the beholder.

---

