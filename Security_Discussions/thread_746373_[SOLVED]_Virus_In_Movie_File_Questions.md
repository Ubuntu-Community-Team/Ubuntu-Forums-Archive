---
title: "[SOLVED] Virus In Movie File Questions"
date: 2008-04-05
forum: Security Discussions
---

### Post by adrian007 on 2008-04-05
Hi Everyone.

My friend downloads videos via a bit torrent client and he downloaded movie and his computer has been acting weird ever since. I am trying to tell him that it can't be a virus as there are no or very little viruses for Linux and to mess up your computer you would have to be running as root. My friend is a very basic computer user and i don't think he would do that.

So i want to reassure him that it is not a virus and i want to double check on the forum.

By the way he uses Ubuntu 7.10

P.S. Can you get viruses in movie or audio files if viruses for Linux started appearing(because i heard that viruses can only come in .deb and .tar.gz and those sorts of files)

Thanks

---

### Post by Vadi on 2008-04-05
I'm really doubtful of that. What is the weird behavior he's been having? I suspect it's some other issue.

---

### Post by Chayak on 2008-04-05
I'm very doubtful that it is a malware problem.  My current job is reverse engineering malware and doing behavioral analysis on samples, most of which don't show up on any virus scanners.  I've seen some cool exploits on the windows side of things using wmv's licensing mechinism.  You don't have to really worry about that with linux as 99.999% of the malware I see is for windows machines.  Yes you do have the occasional linux rootkit but those are for use after you've broken into a system and give yourself and easy way back in.  I'm not saying it's impossibly just very very very unlikely that your friend ran a movie file and the exploit was magically specified for an ubuntu machine and has some kernel exploit to get itself root access and infect the system.  It's a very very difficult thing to write an exploit for linux as all those patches that microsoft loves to point out rapidly fix vulnerabilities in software that could be exploited so any malware for linux would be very short lived even if it did manage to work at all.  There's a reason we use linux as malware analysis stations running windows VMs that we can revert back to a clean state to look at the next sample with.  I have so much malware stored on my system that a virus scanner would have an epileptic fit should I ever back up to a windows machine, if it detects some of them at all.

Though to make a long story short no... you're more likely to get bitten by a random aids infected monkey than get malware on linux by playing a movie file.

Oh and tell your friend that we get most of our unknown malware samples that's not detected by any of the commercial AV scanners.  Bot herders love to custom compile their malware and attach it to some warez program or keygen so they can bot all the 133t kiddies that blindly trust their AV scanner.

If something is malware it'll mostly likely come in compiled binary format perhaps as software or maybe a kernel module.  The moral of the story is download your software from trusted sources and check the MD5 hashes or signatures.

---

### Post by Tomatz on 2008-04-05
There are some videos (shared via bittorrent) that require you to download a virus ridden media player to view the content (dom player). I expect that is what he has done :)

---

### Post by netlogic on 2008-04-05
Movie files are not executable like MS office docs. Answer to your question is NO. You can't get a virus from a movie file. You can get a virus from randomly downloading a movie player for Windows.

---

### Post by adrian007 on 2008-04-06
> **Tomatz said:**
> There are some videos (shared via bittorrent) that require you to download a virus ridden media player to view the content (dom player). I expect that is what he has done :)

Thank you. Yes i think this is the cause as the last time i went to his house he had a weird movie player icon on his desktop which wasn't there before and it was one week ago. This is most likely what happened. 

He is unlucky as you guys said it is a 99.99% chance. Oh well it has to happen to someone

Thank You Everyone:)

---

### Post by cdenley on 2008-04-07
> 
He is unlucky as you guys said it is a 99.99% chance


99.99% chance playing the video didn't install a virus. The chances of problems with his system being caused by software installed from an untrusted source is much more likely. He's not unlucky, just gullible.

---

### Post by nicedude on 2008-04-19
Your friend fell for the old you have to download our player or codec to watch this file trick. As I have like 4000 movies in divx or xvid format and have never seen or heard of an attack that works in these types of files. the other guys here are right that it's basically impossible to infect an AVI file. If you did you could sell the code to the MPAA & RIAA for a million bucks, since it could make them effective LOL.  

PS any super geniuses here don't try and do it I need my movie fix :-)

---

