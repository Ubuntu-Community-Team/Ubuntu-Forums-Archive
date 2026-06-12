---
title: "Password while mounting disks in Lucid!"
date: 2010-05-09
forum: Security
---

### Post by anirban.sg84 on 2010-05-09
Hi guys,
    In Ubuntu Lucid 10.04, when I click a disk in the left panel of Nautilus for the first time, the disks are getting mounted without asking a root password. This was not in the case for the previous versions of Ubuntu. Please suggest how can I turn this feature on in Lucid.

---

### Post by anirban.sg84 on 2010-05-10
Solved by myself.  Just went to System->Users and groups->Advanced Settings->User Privileges tab.

---

### Post by foresthill on 2010-05-10
Yes, but what did you change? I looked in there and didn't see anything that I felt confident would fix the problem.

I have a quad boot system, and was shocked when I installed 10.4 Lucid and saw that the files from my other 3 OS'es were left wide open like that. 

I can't believe people aren't yelling and screaming about this glaring vulnerability, unless they just haven't noticed it yet. What was the rationale for doing this, or was it just an oversight?

---

### Post by bodhi.zazen on 2010-05-10
> **foresthill said:**
> Yes, but what did you change? I looked in there and didn't see anything that I felt confident would fix the problem.

I have a quad boot system, and was shocked when I installed 10.4 Lucid and saw that the files from my other 3 OS'es were left wide open like that. 

I can't believe people aren't yelling and screaming about this glaring vulnerability, unless they just haven't noticed it yet. What was the rationale for doing this, or was it just an oversight?

Physical access = root access

If you need to protect data from physical access you need encryption.

---

### Post by foresthill on 2010-05-10
> Physical access = root access

Yes, I was aware of that. 

I'm more concerned with making it more difficult for someone who gains access to my system while I'm on the internet to go snooping around and possibly altering system files on my other partitions. 

Maybe I'm mistaken, but i thought one of the basic tenets of computer security was to throw every possible roadblock in the way of someone trying to do something like that. And i fail to see how removing password protection on something this important makes users anything other than less safe.

That's why I asked how I can restore the password protection as it existed on previous versions. Anyone?

---

### Post by rookcifer on 2010-05-10
You can't satisfy all of the people all of the time I suppose.  Typically people come here wanting to know how to disable passwords and lessen security, not the other way around!  Oh well, such is life. :)

---

### Post by sgosnell on 2010-05-10
System/Administration/Users&Groups/Advanced Settings/User Privileges tab.  Uncheck the box for "Access external storage devices automatically".  You can always unmount any partitions on the current drive you don't want to access.

---

### Post by sisco311 on 2010-05-10
> **foresthill said:**
> Yes, I was aware of that. 

I'm more concerned with making it more difficult for someone who gains access to my system while I'm on the internet to go snooping around and possibly altering system files on my other partitions. 




If one can gain access to your system over the internet, then focus on that, that's your real issue.

---

### Post by foresthill on 2010-05-10
> **sgosnell said:**
> System/Administration/Users&Groups/Advanced Settings/User Privileges tab.  Uncheck the box for "Access external storage devices automatically".  You can always unmount any partitions on the current drive you don't want to access.

Thanks, I appreciate the help on this, as well as the other responses. I didn't mean to start an argument or anything. 

Unfortunately, the only problem is that this solution did not work, all partitions are still accessible.

Does anyone know the answer to this rather simple question? I guess it's back to Google for me. Thanks again to everyone.

---

### Post by sgosnell on 2010-05-11
Well, yes, all partitions are accessible.  They're accessible with any OS.  I'm not sure I understand your concerns.

---

### Post by numerosix on 2010-05-11
Here it's solved your request :guitar:

[http://ubuntuforums.org/showthread.php?t=1467629](http://ubuntuforums.org/showthread.php?t=1467629)

---

### Post by foresthill on 2010-05-11
EXCELLENT!!! 

It worked!!! Thank you, thank you, thank you!!!

Thanks also for restoring my faith in this forum, and though I realize I'm a complete fool for wanting to do this silly thing at all, it's nice to finally find a solution to a problem.

And it's also nice to confirm my long-held belief that in Linux, anything is customizable. And when that vulnerability that no one thought was possible is taken advantage of by the black hats, I will be the only one whose data is safe! :biggrin:

---

### Post by numerosix on 2010-05-12
Don't mention it!! I've been looking for the solution since I upgraded to 10.04 ... so finally,  I did find it .

Remembering that someone was trying to find it too I decided to post the solution here.

Greetings from Spain.

---

