---
title: "Linux Security In doubt???"
date: 2005-01-09
forum: Server Platforms
---

### Post by LongTooth on 2005-01-09
From Osnews.com,  [http://osnews.com/comment.php?news_id=9352](http://osnews.com/comment.php?news_id=9352)  .  Can the heavy thinkers of this forum let us light weights know how this will affect us and what to do about it? 

Thanks

---

### Post by daniels on 2005-01-09
There are updates available for Ubuntu kernels, I believe (or there will be very, very soon).  What it means is that anyone who already has access to your machine as a normal user can get root access, and control your machine.

---

### Post by Shaggy on 2005-01-09
Heard about it earlier and I couldn't get the exploit to compile to test out my system.  Haven't tried it again lately.  There are patches available for it already.

But you know what they say, remote user exploit + local user exploit = Owned.

For those interested full write up is here [http://isec.pl/vulnerabilities/isec-0021-uselib.txt](http://isec.pl/vulnerabilities/isec-0021-uselib.txt)

---

### Post by tiiim on 2005-01-09
[QUOTE=Shaggy]Heard about it earlier and I couldn't get the exploit to compile to test out my system.  Haven't tried it again lately.  There are patches available for it already.

But you know what they say, remote user exploit + local user exploit = Owned.

For those interested full write up is here [http://isec.pl/vulnerabilities/isec-0021-uselib.txt](http://isec.pl/vulnerabilities/isec-0021-uselib.txt)[/QUOTE]
 Ubuntu though is meant to be a bit more safer on this side of the problem though but just update your comp asap.

---

### Post by scp on 2005-01-09
Don't let vulnerabilities discourage you from using a GNU/Linux system. Every operating system has it's problems, but GNU/Linux distributions are definately not the most insecure operating systems out there. See the link below:
[http://www.schneier.com/blog/archives/2005/01/linux_security_1.html](http://www.schneier.com/blog/archives/2005/01/linux_security_1.html)

Personally, I would like to see more initiatives to make Ubuntu MORE "secure by default" (I am not just talking about having zero services in "LISTEN" mode in the default install.) I would gladly give up some of my own time to see this happen. Inspiration: [http://www.openwall.com](http://www.openwall.com) , [http://www.openbsd.org/security.html](http://www.openbsd.org/security.html) , [http://www.grsecurity.net](http://www.grsecurity.net) , [http://www.bastille-linux.org](http://www.bastille-linux.org) , [http://www.nsa.gov/selinux/](http://www.nsa.gov/selinux/) .

If there are initiatives like this for Ubuntu and I am just missing the boat, please point me in the right direction. Remember, I am referring to being secure out of the box, not "You can enable universe and install XYZ to make you more secure."

---

### Post by Shaggy on 2005-01-13
Just a question, has anyone even been able to get the code given to compile even?

---

### Post by jdong on 2005-01-13
You need to google for modify_ldt_ldt_s and get the definition of the structure.

I've never gotten the exploit to work with Ubuntu. Either the thing segfaults, or it just start hogging memory until the out-of-memory killer destroys it.

---

### Post by jdodson on 2005-01-13
[QUOTE=scp]Don't let vulnerabilities discourage you from using a GNU/Linux system. Every operating system has it's problems, but GNU/Linux distributions are definately not the most insecure operating systems out there. See the link below:
[http://www.schneier.com/blog/archives/2005/01/linux_security_1.html](http://www.schneier.com/blog/archives/2005/01/linux_security_1.html)

Personally, I would like to see more initiatives to make Ubuntu MORE "secure by default" (I am not just talking about having zero services in "LISTEN" mode in the default install.) I would gladly give up some of my own time to see this happen. Inspiration: [http://www.openwall.com](http://www.openwall.com) , [http://www.openbsd.org/security.html](http://www.openbsd.org/security.html) , [http://www.grsecurity.net](http://www.grsecurity.net) , [http://www.bastille-linux.org](http://www.bastille-linux.org) , [http://www.nsa.gov/selinux/](http://www.nsa.gov/selinux/) .

If there are initiatives like this for Ubuntu and I am just missing the boat, please point me in the right direction. Remember, I am referring to being secure out of the box, not "You can enable universe and install XYZ to make you more secure."[/QUOTE]


opening no ports by default means most users by default wouldnt need bastile or any of the firewall packages you mention.

if you open a port you need to know what you are doing, so firewalling is good and i think it is fine that you have to install them from universe.  then again firewalling has been available in the kernel for quite awhile, however not turned on by deafult :-D 

however, selinux is different and worth looking at for inclusion in ubuntu sometime down the line imo.

---

### Post by jdong on 2005-01-13
I would also like to see some sort of proactive buffer overflow prevention patch making it into Hoary's default kernel -- such as PAX. From my testing, PAX squashes most buffer overflow attacks flawlessly. A DSLReports user showed that PAX squashes the local root compromise by killing it.

I'd also like to see grsecurity+PAX+(selinux) hardened kernels for Hoary -- perfect for servers. grsecurity's hardened /proc prevents this local root exploit from starting (slabinfo read access denied)

---

### Post by scp on 2005-01-13
That's more of what I was talking about.

I should have made myself more clear. There is more to security than "network security." Just because your machine does not listen on any TCP or UDP ports does not mean it is 100% "secure." 

Here's a better wish list:
* Buffer overflow and stack smashing prevention (like what OpenBSD does with W^X, ProPolice, StackGap.. etc.)
* Encrypted Virtual Memory 
* Enhancements like those from Openwall: [http://www.openwall.com/linux/README.shtml](http://www.openwall.com/linux/README.shtml) 
* Integrated Crypto (IPSEC clients, encrypted file-systems, etc.)

And to make sure there isn't confusion, let me say, I AM NOT SAYING JUST IMPLEMENT FIREWALL TECHNOLOGIES.

---

### Post by daniels on 2005-01-14
We're looking closely at PaX/SSP and are doing a trial run through the archive with it; what exactly do you mean by 'Enhanced Virtual Memory', though?

---

### Post by jdong on 2005-01-14
[QUOTE=daniels]We're looking closely at PaX/SSP and are doing a trial run through the archive with it; what exactly do you mean by 'Enhanced Virtual Memory', though?[/QUOTE]

*whispers* psst, it says *encrypted* virtual memory...

---

### Post by scp on 2005-01-14
See:
[http://www.openbsd.org/papers/swapencrypt.ps](http://www.openbsd.org/papers/swapencrypt.ps)
[http://www.kernelthread.com/publications/security/smemory.html](http://www.kernelthread.com/publications/security/smemory.html)

---

### Post by machiner on 2005-01-14
This thread makes me druel with anticipation.

---

### Post by scp on 2005-01-14
You want this, too, I take it?  :lol: 

To me:
"It Just Makes Sense(tm)"

---

### Post by daniels on 2005-01-15
Ah, encrypted swap.  But what's the point?  If swap is to be encrypted, then the key needs to be stored in RAM somewhere, which means that anyone who can get to swap, can get to the key.  Which kind of defeats the point, and just makes swap *really* *really* slow.

---

### Post by scp on 2005-01-15
daniels, 

Your questions are answered in the whitepaper that I posted. Here it is again:
[http://www.openbsd.org/papers/swapencrypt.ps](http://www.openbsd.org/papers/swapencrypt.ps)

Please read it.

Here is some more info on the subject, but keys are static (read: recoverable) in this scenario and that is not ideal, but just some food for thought and is better than nothing:
[http://mail.nl.linux.org/linux-crypto/2001-08/msg00056.html](http://mail.nl.linux.org/linux-crypto/2001-08/msg00056.html)

---

### Post by scp on 2005-01-19
Did this thread die?

---

### Post by J. S. Jackson on 2005-01-19
[BestCrypt](http://www.jetico.com) has incorporated this feature into their windows setup.  Not sure if it applies to the LInux version as well.

I've heard that [TrueCrypt](http://truecrypt.sourceforge.net/) (open source) will also eventually incorporate this functionality.

---

### Post by jdong on 2005-01-19
Linux has cryptoloop that can do loopback encryption -- I'm sure you can hack it to do swap. Probably will be the slowest thing alive.

---

### Post by ubuntu UsER on 2005-01-20
Linux is still more safe than Windows  :D 
[http://www.vnunet.com/news/1160588](http://www.vnunet.com/news/1160588)  =D>

---

