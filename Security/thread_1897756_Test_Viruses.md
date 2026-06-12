---
title: "Test Viruses?"
date: 2011-12-19
forum: Security
---

### Post by elgordodude on 2011-12-19
I'm currently building out a Lubuntu live drive which I use to scan infected Windows machines, so we can skip the whole antivirus isn't necessary conversation. Anyway I've got several antivirals and I've begun benchmarking them, but I'd like to get a better handle of their effectiveness.

I've googled around, but I'm having trouble finding a library of test viruses, and this doesn't seem like a great topic to go traipsing through third party sites with. Anyone here have any experience with this and might be able to suggest a place where I can get a bunch of viruses, or things that look like viruses in a zip file? 

It feels really weird to type that, but in addition to knowing how long these scans take and how many files they scan, I would really like to know how good they are at finding infected files and I can only do that if I know how many infections are on the machine.

So far, my evidence is anecdotal, but AVG seems to be doing the best job at finding infections.

If I can get some decent benchmarks I'll be sure to post them.

---

### Post by Dangertux on 2011-12-19
> **elgordodude said:**
> I'm currently building out a Lubuntu live drive which I use to scan infected Windows machines, so we can skip the whole antivirus isn't necessary conversation. Anyway I've got several antivirals and I've begun benchmarking them, but I'd like to get a better handle of their effectiveness.

I've googled around, but I'm having trouble finding a library of test viruses, and this doesn't seem like a great topic to go traipsing through third party sites with. Anyone here have any experience with this and might be able to suggest a place where I can get a bunch of viruses, or things that look like viruses in a zip file? 

It feels really weird to type that, but in addition to knowing how long these scans take and how many files they scan, I would really like to know how good they are at finding infected files and I can only do that if I know how many infections are on the machine.

So far, my evidence is anecdotal, but AVG seems to be doing the best job at finding infections.

If I can get some decent benchmarks I'll be sure to post them.


Hmm... Interesting goal, but it's going to be a little bit difficult. As far as picking up actual signatured threats. I would just set up a machine that will be the target for the scan with XP SP0 and browse the net with no protection, preferable downloading as many "free" things as possible.

Now if you actually want to test against non-signatured threats with heuristics, this is a little bit easier as most anti-malware will trigger on a jmp call to EIP in a payload, which is thankfully very easy to replicate (some progamming knowledge required). 

This might be a little bit confusing, but I don't really know of any other way you can really test this.

Also -- there is EICAR but it's old as the hills.

---

### Post by yetiman64 on 2011-12-19
eicar.com (.com being a Windows extension NOT a website :-)) is a test file for antiviruses. eicar stands for "European Institute for Computer Antivirus Research" as far as I understand it. I have in the past (Win 98 days) used it by stashing it on the drive somewhere and running the AV scan. I think something like this may be of use to you.

Originally I obtained it through the Window AV package f-prot. You may need to search around for it now. I would likely have a copy here somewhere, but won't post it as I'm very unsure about the legalities of distributing it. Probably best to look in the current f-prot package or checking if EICAR still distribute it.

Edit: Just remembered the "virus" eicar is actually just a string in a text file in f-prot which has to be copied to a blank document and the txt extension changed to .com (for Windows AV resident shield to "jump on it") if you decide to look for it, look for a txt file with the string in.

---

### Post by Dangertux on 2011-12-19
> **yetiman64 said:**
> eicar.com (.com being a Windows extension NOT a website :-)) is a test file for antiviruses. eicar stands for "European Institute for Computer Antivirus Research" as far as I understand it. I have in the past (Win 98 days) used it by stashing it on the drive somewhere and running the AV scan. I think something like this may be of use to you.

Originally I obtained it through the Window AV package f-prot. You may need to search around for it now. I would likely have a copy here somewhere, but won't post it as I'm very unsure about the legalities of distributing it. Probably best to look in the current f-prot package or checking if EICAR still distribute it.

Yeah this is it [http://www.eicar.org/86-0-Intended-use.html](http://www.eicar.org/86-0-Intended-use.html)

It's legit to distribute.

---

### Post by yetiman64 on 2011-12-19
> **Dangertux said:**
> Yeah this is it [http://www.eicar.org/86-0-Intended-use.html](http://www.eicar.org/86-0-Intended-use.html)

It's legit to distribute.
Yep that is it, good to hear that, thanks

The string I mention is in the code box further down the page linked, much easier than trying to send as a file for the OP. Cheers.

---

### Post by elgordodude on 2011-12-19
> **Dangertux said:**
>  I would just set up a machine that will be the target for the scan with XP SP0 and browse the net with no protection, preferable downloading as many "free" things as possible.


Thanks for the quick reply, I considered doing this, I have a spare P4 that I'm running the time and file benchmarks against now. The problem is that I want to know how infected the machine is so I know how effective the scan is. If I don't know how many infections there are, I worry that one scan may look good by issuing a bunch of false positives which would be counter-productive.

For the record I have AVG Avast BitDefender Avira Clam and F-Prot installed, suggestions on other scanners are welcome.

---

### Post by Dangertux on 2011-12-19
> **elgordodude said:**
> Thanks for the quick reply, I considered doing this, I have a spare P4 that I'm running the time and file benchmarks against now. The problem is that I want to know how infected the machine is so I know how effective the scan is. If I don't know how many infections there are, I worry that one scan may look good by issuing a bunch of false positives which would be counter-productive.

For the record I have AVG Avast BitDefender Avira Clam and F-Prot installed, suggestions on other scanners are welcome.

Yes that is a valid concern, you might try contacting one of the AV vendors who's products your testing. They may be able to give you something that triggers multiple signatures. However, that might be a little rigged. I don't really think you're going to be able to just request a zip file full of malware though :-/

---

### Post by elgordodude on 2011-12-19
> **Dangertux said:**
> [http://www.eicar.org/86-0-Intended-use.html](http://www.eicar.org/86-0-Intended-use.html)


That is an interesting read, and while I promise my motives are genuine, I'm well aware of what a promise on the internet is worth. I'll give it a shot, but I would suspect that every antiviral engine has already tested against this file. Right? This is dated 2006, I know some linux programs are poorly supported, but 5 years should be plenty of time.

Perhaps I'll go the XP route and see if I can build my own test folder based on multiple scans, it would take some time, but might get me the results I'm looking for.

---

### Post by Dangertux on 2011-12-19
> **elgordodude said:**
> That is an interesting read, and while I promise my motives are genuine, I'm well aware of what a promise on the internet is worth. I'll give it a shot, but I would suspect that every antiviral engine has already tested against this file. Right? This is dated 2006, I know some linux programs are poorly supported, but 5 years should be plenty of time.

Perhaps I'll go the XP route and see if I can build my own test folder based on multiple scans, it would take some time, but might get me the results I'm looking for.


Well in this particularly case I think most people would think "so you want to download a bunch of viruses? okay...." lol

I do see your interest and I'm just not sure that there is really anything already put together for that. I would suggest talking to different malware research firms (try to google some phone numbers) and see if they suggest anything. 

Also -- you are right about that file being signatured.

---

### Post by elgordodude on 2011-12-19
> **Dangertux said:**
> you might try contacting one of the AV vendors who's products your testing. They may be able to give you something that triggers multiple signatures.

In my googling I found the eicar file from kaspersky, and that was about it, so I guess it's time to dust off an XP cd.

---

### Post by elgordodude on 2011-12-19
> **Dangertux said:**
> Well in this particularly case I think most people would think "so you want to download a bunch of viruses? okay...." lol

I do see your interest and I'm just not sure that there is really anything already put together for that. I would suggest talking to different malware research firms (try to google some phone numbers) and see if they suggest anything. 

Also -- you are right about that file being signatured.

I know! As I said in the OP it felt really weird to type that, I sat back for a minute and thought, "Did I really just tell the internet that I want a zip full of malware?" Unfortunately I do, but it's sounding like I'll have to make it, a little dangerous, but I can secure it off the LAN so mostly it's a matter of time.

---

### Post by spynappels on 2011-12-20
I know a lot of A/Vs on Windows allow you to send any infected files to a vault rather than deleting them, this should allow you to build up a nice collection rather quickly...

---

