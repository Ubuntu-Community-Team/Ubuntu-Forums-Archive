---
title: "Windows 7 - can't get rid of &quot;conduit&quot;"
date: 2014-03-04
forum: Windows
---

### Post by squakie on 2014-03-04
My brother in-law's Windows 7 laptop seems to have installed the conduit search engine with one of his downloads.  I've read where it can end up allowing a backdoor for someone to load a trojan, etc., in to the computer.  The hard disk on his laptop is constantly being hit, quite strongly, even when the laptop is doing nothing.  I found 2 programs running in task manager that had "conduit" in the description - I killed those, the disk activity stopped and the laptop started responding again.

I did some reasearch on the net, then tried to follow some advice I found.  First I removed the program via the normal Windows 7 programs and features option in control panel.  Next I went to the browser and removed any reference to conduit (like the default page, etc.), then did the reset they mentioned.  I ran superantispyware and malwarebytes but neither found anything except a few tracking cookies - I let them delete them.  I then checked the registry for the entries the instructions said to find and remove - couldn't find them.  Yet everytime the PC starts up, conduit shows up again, the disk is hit like crazy, and the laptop is either super SLOW or completely unresponsive.

I *think* something got in and might possibly be allowing someone or something to look all over in the laptop and potentially send data or even allow remoted access to the laptop.  I did turn off remote access itself in Windows, but it still keeps going.

I'm kind of at the end of my rope and my little Windows knowledge at this point.  My brother in-law just gets so frustrated he gets really cranky and gets mad, but won't listen when I tell him to stop and let me do something (kill the conduit processes) to allow him to work better on it.

If anyone has any ideas on how to walk me through this it would be greatly appreciated!

Thanks!

---

### Post by monkeybrain20122 on 2014-03-04
Can't help you here, just note that one guy I installed lubuntu for actually got the conduit through browsing some site (he said he suspected it was a sport streaming site..). It hijacked FF and it always opened to the same site which I can't remember what it was now.  about://config was full of conduit entries. But that was all it did apparently, after nuking ~/ .mozilla everything was back to normal. Didn't find anything suspicious or abnormal like you reported here.

Edited: Just to clarify, he got it on lubuntu, not Windows.

---

### Post by orb9220 on 2014-03-04
More to it than that since it's considered malware.
A [simple google search]("https://www.google.com/search?as_qdr=y&q=conduit+search+engine") shows there is many steps involved.
.

---

### Post by karol3 on 2014-03-04
Hi, Squaquie.
I have removed twice conduit form my Laptop.
You have to be patient and do a bit long work.
What you have done is correct. But let's check this:
- Check each browser on PC: starting page (in Google, may be a bit hidden), addons, so forth.
- When conduit is running check which processes are running in task manager. You may find someone related to it. Do not remember now.
- Look into Windows services: you may find some of them related to Conduit and also to the other applications.
- Install crap cleaner and let it delete every garbage in the computer. If you prefer, you can do a backup of the registry before deleting all the rubbish from there.
- initiate regedit.exe and go manually through the registry, looking for "conduit" first, and the other app then. delete each entry related to them, also folders.
Google for this and, may be, you will be able to find more details.
Hope the best for you and success on your work!

---

### Post by xicarusx on 2014-03-04
[http://malwaretips.com/blogs/conduit-search-removal/](http://malwaretips.com/blogs/conduit-search-removal/)

Once you get it removed have the person get Malwarebytes. I own a computer repair business and it is one of my go to tools for avoiding malware. Just make sure to enable blocking PUPs (potentially unwated programs).

---

### Post by squakie on 2014-03-07
> **orb9220 said:**
> More to it than that since it's considered malware.
A [simple google search]("https://www.google.com/search?as_qdr=y&q=conduit+search+engine") shows there is many steps involved.
.
That's why I followed what I did on the net:  remove the program first, then scan, then remove the registry keys, then scan with malwarebytes and superantispyware.  The trouble I think is that none of the mentioned registry keys are being found, so it's imbedded somewhere else.

Thanks ! ;)
Dave

---

### Post by squakie on 2014-03-07
Thanks to everyone!  I've been a busy on something else and hadn't gotten back to check this thread in a while.  I guess I need to check a different thread from the one I was following on the net. ;)

Thanks again! ;)
Dave

---

### Post by monkeybrain20122 on 2014-03-09
Just restore it to factory condition when all else fails. I don't know why you would bother if your brother in law is mad and cranky and won't listen to you. He is the one who get his pc infected in the first place, probably from viewing porn :)

---

### Post by squakie on 2014-03-11
> **monkeybrain20122 said:**
> Just restore it to factory condition when all else fails. I don't know why you would bother if your brother in law is mad and cranky and won't listen to you. He is the one who get his pc infected in the first place, probably from viewing porn :)

That would not be beyond the realm of possibility ;)

I talked to him yesterday about doing a restore as I had followed several web threads about removing it but it appears to be in too deep.  Not that Conduit itself is bad, it's just that it opens a door for some really bad things.  So, sometime in the next week or so I get to restore it back to how it was delivered.  Since he won't be using Juno now, it will help not having "garbage" code (sorry Juno) installed.  Easier to maintain.

He and my Dad are what I like to term "everything is good" thinkers.  They think if they have anti-virus and anti-spam software installed that it just "magically" does it's thing.  Have the time they don't have their PC's on long enough to even run a quick scan, let alone a full scan.  Updates to the def's??  "We don't need no stinkin' updates" ;)

My Dad (in his 80's) bought a new laptop last year and said he had the place he bought it from install everything so he was safe.  He asked me to look it over - I figured "ain't my job" anymore, so I just told him "sure".  Well, wouldn't you know, he picked something up AGAIN and has been mad becauise I told him "sure".  At least they are only 250 miles away now.  I used to have to try to debug and tell them what to do over the phone when they were 2000 miles away - that was never fun.  Always go things fixed, but never fun! ;)

So, back to the subject at hand - yep, going to do a restore to factory defaults.  That should solve the problem (at least I *hope* that might get rid of things like a boot virus if that's where it hooked in).

Thanks everyone!

---

### Post by mastablasta on 2014-03-12
how about using a rescue cd like bit defender (it's linux with XFCE and bitdefnder antivirus scaner)? would it help?

also i found that something like processhacker or similar tools to be more informative and telling you what file is actually running the process and where is it running it from. particlualry what started and is running svchost (and connecting to the net) and various similar processes which are nothing unusual if they run but can be abused. a portable version exists for troubleshooting mashcines at relatives :-)

---

### Post by squakie on 2014-03-15
Thanks mastablasta - I've got to remember that one!

I was allowed to just reset to factory defaults and have rebuilding what he wants from there.  Unable to convince him to go to Linux for now ;)  Oh well....

---

