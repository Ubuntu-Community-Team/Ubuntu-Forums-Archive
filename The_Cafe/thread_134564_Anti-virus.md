---
title: "Anti-virus"
date: 2006-02-22
forum: The Cafe
---

### Post by bjweeks on 2006-02-22
I've been thinking about this what is the point of anti-virus? If virus spread by eather a hole in the software or a admin(root) running it, why do we have anti-virus? If you fix the holes and make users non-root (*cough*sudo*cough*) the why the !@#$ is microsoft makeing a anti-virus?

---

### Post by welsh_spud on 2006-02-22
It is easy enough to say 'Fix all the holes' but Windows (and any other OS for that matter) is such a huge database of code to sift through it would take thousands of years to fix every single possible security hole.

Also, just because you don't have root access doesn't mean you can't get a virus. It just means that only your /home/user directory would get trashed, not the entire system under /

---

### Post by nocturn on 2006-02-22
[QUOTE=bjweeks]I've been thinking about this what is the point of anti-virus? If virus spread by eather a hole in the software or a admin(root) running it, why do we have anti-virus? If you fix the holes and make users non-root (*cough*sudo*cough*) the why the !@#$ is microsoft makeing a anti-virus?[/QUOTE]

AV is good as a last line of defense and for determining/cleaning infections.  Most users however seem to think of it as a proactive security measure, which it clearly isn't.

A recent study showed that fast moving virusses had at least 8 hours before the first signatures where out, that could be a lot of owned machines.

Not running as root/admin is good, a firewall is good, stack protection and non-executable memory and partitions are real defenses.

---

### Post by bjweeks on 2006-02-22
> It is easy enough to say 'Fix all the holes' but Windows (and any other OS for that matter) is such a huge database of code to sift through it would take thousands of years to fix every single possible security hole.

Just fix the hole the virus expoilts

---

### Post by Robgould on 2006-02-22
[quote=bjweeks]Just fix the hole the virus expoilts[/quote]
 
You can't fix the hole until you know it is there.  You usually don't know that until it has been exploited.  So now what do you do?  You have potentially millions of copies of this software out there.  How do you let everyone know that they need to update/upgrade?  How do you even know who has the software?  What you are saying is just not feasible.  
 
A good protion of software designers do fix the holes - in future versions after the hole has been found.  That does nothing for the software already out there.  
 
So anti-virus companies are notified, or discover it themselves.  Virus signatures are updated, and systems are protected.  Assuming that is, that people run an anti-virus and keep signatures updated.
 
There really is no other feasible way to limit the damage of a virus that is already out there.
 
If software designers new about the hole, before it was infected, it would not be there to begin with.  They are generally not there on purpose.

---

### Post by dosed150 on 2006-02-22
on this subject how do i install avg on ubuntu?

---

### Post by briancurtin on 2006-02-22
the fact that the original question in this thread even had to be asked, gave me a headache.

---

### Post by KiwiNZ on 2006-02-22
[quote=briancurtin]the fact that the original question in this thread even had to be asked, gave me a headache.[/quote]

It was a reasonable question.

---

### Post by GreyFox503 on 2006-02-22
Why are they making an anti-virus?  I can think of three choices for them.

1)  Put a lot of time and effort into cleaning up their entire operating system.  This would take forever to do thoroughly.

2)  Launch a new anti-virus program that would be much faster to produce, and conveniently gives them a new source of income.  A *subscription* product, no less.  Those are all the rage nowadays.

3)  Do nothing.  Let the current anti-virus market continue, miss opportunity.


Of course, the 2nd option presents a huge conflict of interest.  If a new virus is discovered that exploits a technical flaw, do they fix the flaw first, or release an update to their antivirus?  I would not put it past Microsoft to do this as an incentive for more users to buy their protection.

As far as I can tell, that's what it amounts to.  Now you can pay Microsoft protection money to keep your computer safe, instead of Norton or McAfee.

---

### Post by prizrak on 2006-02-23
> Of course, the 2nd option presents a huge conflict of interest. If a new virus is discovered that exploits a technical flaw, do they fix the flaw first, or release an update to their antivirus? I would not put it past Microsoft to do this as an incentive for more users to buy their protection.
I don't think it has to be an either/or type of deal. It's much easier (and faster) to release a signature file that will stop the virus than it is to code a patch. So the first thing out will be a signature of the virus to stop it's spread while the patch is being created. It's not a bad idea especially since the update mechanisms are already in place making it easier for users. You got MS Update now that will update all of the MS software on your system at the same time (or so they say). I can also see an A/V from MS to be faster than 3rd party ones since they know the OS inside out.

---

### Post by GreyFox503 on 2006-02-23
True.  It probably is much faster to quickly release a virus definition update than to find and fix a section of their code.  Then we trust them to fix the flaw anyways.  Hope they don't give it a low priority.  After all, no rush to fix it, right?  I mean, they already released the virus-definitions to stop it.  Oh, wait, for those using the anti-virus product...

I know that in theory, it's possible that Microsoft will continue their patching schedule unaffected by the anti-virus product in any way.  But they seem so related, I'm just trying to play devil's advocate.  You can tell I don't trust them, because if I did then I would have full confidence that they will continue to patch their flaws.

---

### Post by prizrak on 2006-02-23
[QUOTE=GreyFox503]True.  It probably is much faster to quickly release a virus definition update than to find and fix a section of their code.  Then we trust them to fix the flaw anyways.  Hope they don't give it a low priority.  After all, no rush to fix it, right?  I mean, they already released the virus-definitions to stop it.  Oh, wait, for those using the anti-virus product...

I know that in theory, it's possible that Microsoft will continue their patching schedule unaffected by the anti-virus product in any way.  But they seem so related, I'm just trying to play devil's advocate.  You can tell I don't trust them, because if I did then I would have full confidence that they will continue to patch their flaws.[/QUOTE]
Yeah I can see you have little trust in MS ;) I don't think it would be affected actually as you can expect just about anyone to have an A/V nowadays (ISP's, colleges, companies, etc give them out to customers/employees/students) so they don't HAVE to patch things really. They'd come under alot of heat if they were to stop or significally delay patching. If that were to happen I can see companies running to Linux en masse.

---

### Post by GreyFox503 on 2006-02-23
Um... the beans graphic above my avatar has gone crazy.... and apparently they are not roasted.  These forum guys have lost it.  :)

Sorry, way off-topic.  Continue discussion!

---

