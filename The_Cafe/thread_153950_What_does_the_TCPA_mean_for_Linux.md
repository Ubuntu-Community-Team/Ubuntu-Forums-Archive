---
title: "What does the TCPA mean for Linux?"
date: 2006-04-02
forum: The Cafe
---

### Post by Talruk6 on 2006-04-02
What does the TCPA mean for Linux?  I'd think people would be nervous, and I'm confused on why nobody is worried at all.  

The TCPA means Trusted Computing Platform Alliance.  Some links on it are:

[https://www.trustedcomputinggroup.org/home](https://www.trustedcomputinggroup.org/home)
[http://www.againsttcpa.com/index.shtml](http://www.againsttcpa.com/index.shtml)

The jist of it seems to be that processors wouldn't work with open source, and there is a lobbying force to make it illegal, carrying a 5 year jail sentence.  I'm going to be embaressed if I've been had...

---

### Post by GeneralZod on 2006-04-02
Recent Linux kernels provided support for the TPM (Trusted Platform Module) that is the key part of TCPA.  The TPM can be disabled completely in the BIOS.  The only direct danger to Free Software users (that I can see) is that ISPs might make it impossible to connect to the Internet unless you are running Trusted Software (which is unlikely to include Linux in all of its myriad forms) on Trusted Hardware (something which is effectively impossible to spoof), but there are a great many legal and technical hurdles to jump before this becomes a reality, and I doubt ISP's would be interested in pursuing this anyway as it would simply be of no use to them.

I don't want Trusted Computing to become prevalent (especially amongst home users, where the potential for abuse far, far outweighs any meagre benefits it would bring), but I think it's unlikely to cause any real damage.  we'll have to wait and see, though, and keep a wary eye on things.

---

### Post by BWF89 on 2006-04-02
[QUOTE=GeneralZod]The only direct danger to Free Software users (that I can see) is that ISPs might make it impossible to connect to the Internet unless you are running Trusted Software (which is unlikely to include Linux in all of its myriad forms)[/QUOTE]
How could they stop Linux users from connecting to the internet since the majority of servers run on Linux.

---

### Post by crazy_fox on 2006-04-02
Because if these linux servers are to become TCPA compatible, then, they will be using the list of permitted software which will not contain some linux distros.

I am against it in anyway. Its gonna give control of every single computer to large companies. But i find it rather hard for them to implement it.

---

### Post by Kvark on 2006-04-02
I think the only bad implementation that will become common in democratic countries is that some online games will require players to use only approved programs to avoid cheating and some online media services do the same to avoid recording of media streams. Dictatorships on the other hand could use it to check so home computers use only the software the regime has approved for home use before giving internet access. TPM only keeps track of the programs that you have used since you turned on the computer so you can still have anything installed, you'll just have to reboot to reset the TPM chip before playing if you have used something that wasn't approved.

Linux software will probably be approved by services/games that has a Linux port. The big problem I see is that any change in a program no matter how small results in a completely different hash. I think that means that even if Firefox is approved by an online service you still can't use any other version of it then the one Mozilla provides. Unless the service goes through the endless hassle of approving every version that every distro provides and even then you still can't use something you modified and compiled yourself. Effectively turning all software into closed source for those who want use a service that requires TPM.

---

### Post by Arktis on 2006-04-02
Yes, TCPA is what I like to call "totally gay, dude" (no offense meant to actual homosexuals out there ;) ).  The scary part is that this particular model of lockdown has been planed in some form or another for YEARS.  TCPA is just the latest version of it.  People should read up on the history of this stuff.  It's an interesting subject to say the least.  Now where did I put my tinfoil hat...?

[http://en.wikipedia.org/wiki/Trusted_Computing_Platform_Alliance](http://en.wikipedia.org/wiki/Trusted_Computing_Platform_Alliance)
Edit: It really is a very short entry!  We should do our part by adding potentially misleading content!  (j/k)

---

### Post by stoeptegel on 2006-04-22
There's a nice about TCPA movie (mov) on legaltorrents.com about this.
Direct link:
[http://www.legaltorrents.com/bit/trusted-computing.torrent](http://www.legaltorrents.com/bit/trusted-computing.torrent)

---

### Post by Rizado on 2006-05-30
Read [this](http://www.cl.cam.ac.uk/%7Erja14/tcpa-faq.html)

---

### Post by 23meg on 2006-05-30
For Linux, the kernel, it means just another technology to be supported, which can be used for all purposes ranging from private data security to proprietary lockdown. It already *is* supported.

For the world of Free Software it means a threat from the big boys to lock the uninformed and ignorant masses down to proprietary media, software and a paradigm of ownership where the user never absolutely owns anything. 

For the whole world of computing it's a poor scheme that will probably end up failing totally except in a few narrow niches. If it goes so far as to try to shut open source out of the net (it's often argued that this is its hidden agenda) or undermine the GPL as Ross Anderson argues, it will get the answer it deserves mainly in the form of boycotts, which is the kind of language the big boys understand.

---

### Post by G Morgan on 2006-05-30
[QUOTE=23meg]For Linux, the kernel, it means just another technology to be supported, which can be used for all purposes ranging from private data security to proprietary lockdown. 

For the world of Free Software it means a threat from the big boys to lock the uninformed and ignorant masses down to proprietary media, software and a paradigm of ownership where the user never absolutely owns anything. 

For the whole world of computing it's a poor scheme that will probably end up failing totally except in a few narrow niches. If it goes so far as to try to shut open source out of the net (it's often argued that this is its hidden agenda) or undermine the GPL as Ross Anderson argues, it will get the answer it deserves mainly in the form of boycotts, which is the kind of language the big boys understand.[/QUOTE]

Because all those Linux users will be a huge loss to the profits of most companies. The problem with TC is like Linux most don't realise it exists. Unlike Linux currently it will impact most peoples lifes directly. When people start to see this happening they will be up in arms about it. Then we will see some movement to change it. I find it interesting that no political parties seem to be against it. Ok in Britain both major parties are idiots but I'd at least expect the LD's to complain (to be honest the LD's seem to have lost all hope, most British people seem to want to be told what to do at the moment).

---

### Post by Kilz on 2006-05-30
I truly believe that tcpa will be the axe that kills the goose that lays the golden eggs. If people cant do things with their computer, what is the purpose of owning one? This seems to be more a plan that hardware manufacturers have to implement. Don't they see that people are simply not going to buy more computers if the computer limits them?

---

### Post by G Morgan on 2006-05-30
I think there will be a market for non-TC technology in the long term. A company is bound to see the potential for non 1984 computers and will respond accordingly.

---

### Post by Miguel on 2006-07-04
Hi guys,

I have a little question. Intel Macs have TMP chips, right? According to what I've read, these chips are some Infineon made ones. The thing is, I don't want to buy a computer that maybe doesn't trust me. I want no TC or TPM or Palladium on my machine. 

Will I be able to enjoy an Intel Merom with Santa Rosa  platform laptop without these creepy things? I am starting to get worried

---

### Post by G Morgan on 2006-07-04
[QUOTE=Miguel]Hi guys,

I have a little question. Intel Macs have TMP chips, right? According to what I've read, these chips are some Infineon made ones. The thing is, I don't want to buy a computer that maybe doesn't trust me. I want no TC or TPM or Palladium on my machine. 

Will I be able to enjoy an Intel Merom with Santa Rosa  platform laptop without these creepy things? I am starting to get worried[/QUOTE]

I think treacherous computing can be disabled in the bios. Whether you'll be able to get a TC enabled OS to work then is another thing.

---

### Post by Miguel on 2006-07-05
Mmm... I don't think the OS will be a big issue. I mean, one of the reasons to use linux is to avoid using a treacherous OS. Anyway, I'd still feel better if newer processors didn't have those treacherous platform thigs.

---

### Post by G Morgan on 2006-07-05
[QUOTE=Miguel]Mmm... I don't think the OS will be a big issue. I mean, one of the reasons to use linux is to avoid using a treacherous OS. Anyway, I'd still feel better if newer processors didn't have those treacherous platform thigs.[/QUOTE]

Linux was the first platform to support a TPM IIRC. The big worry is that ISP's could ban computers without an active TPM.

---

### Post by ubuntu_demon on 2006-07-05
[QUOTE=stoeptegel]There's a nice about TCPA movie (mov) on legaltorrents.com about this.
Direct link:
[http://www.legaltorrents.com/bit/trusted-computing.torrent](http://www.legaltorrents.com/bit/trusted-computing.torrent)[/QUOTE]
That movie is great! It's definetely suitable to show to a non-geek and he would understand.

---

### Post by Miguel on 2006-07-05
[QUOTE=G Morgan]Linux was the first platform to support a TPM IIRC. The big worry is that ISP's could ban computers without an active TPM.[/QUOTE]

Are you telling me that I will have to either have a look at the kernel source or trust it blinded? No annonymous user for me, then. This really pisses me off. I can't believe I haven't heard the FSF or Stallman himself complaining about this. Or maybe I am being a little too paranoid. I've spent too long in the US, I guess.

A computer is a machine that adds 1's and 0's. I just want it to add numbers at *my* will.

---

### Post by ubuntu_demon on 2006-07-05
I posted an entrty on my blog about this thread and about the "Trusted Computing" movie.

[http://ubuntudemon.wordpress.com/2006/07/05/trusted-computing-a-must-see-short-movie](http://ubuntudemon.wordpress.com/2006/07/05/trusted-computing-a-must-see-short-movie)

---

### Post by Ptero-4 on 2006-07-14
This is really freaky. Even Apple fell to this. This can only be one thing folk, we're closing in for the apocalipsis.

---

### Post by ultim8k on 2007-06-22
Here is Stallman's article about TCPA:

[http://www.gnu.org/philosophy/can-you-trust.html]("http://www.gnu.org/philosophy/can-you-trust.html") ;)

**And remember that there is always a hope when you believe it!**

---

### Post by Tundro Walker on 2007-06-22
Let me lay out an analogy before I explain my stance on this...

I live in Texas, USA.  We have tons of illegal immigrants who have come over from Mexico to work, get some money, etc, etc.  The analogy isn't about the immigrants more so about Company's that choose to target their marketing and business towards them.  In the past 5 years, I've noticed huge surges in Hispanic marketing campaigns.  Even the company I work for has ramped up its Hispanic marketing.  Folks would like to say that this marketing is targeted at the legal Hispanic citizens, but let's be honest; the illegal immigrant population is a huge market to tap, and so a lot of the marketing is directed at them.  To companies, it doesn't matter that the people are here legally or illegally...they're money is just as good either way.

Ok (before an immigration flame war starts), my point is, if companies would go so far as to expand their market by targeting illegal immigrants for  potential business, why would other companies LIMIT their market / business by agreeing to TCPA?!  Business is Business, and it makes no fiscal sense to LIMIT your market.  You're in business to make money, and by denying service to a group of folks because they don't want to use some TCPA crap just means you're not getting them as customers.  Which means there's a void of customers out there needing some kind of service fulfilled.  Which means SOME OTHER COMPANY will pop up to fill the void, taking your potential customers because some genius at your company wanted to tie your hands with this TCPA crap.

From a business stand-point, it doesn't make sense.  From a personal stand-point, it doesn't make sense either, because people don't want their hardware to dictate what they can and can't do with their software, or vice-versa.  It's easier to give freedom then to take it away, and if TCPA is all about taking away freedoms, then folks won't go willingly.  And, any software / hardware that implements it won't work unless ALL software and hardware implements it.  Otherwise, as long as people have a choice, there will always be some who choose to use non-TCPA software / hardware.  If an ISP decides to block you because of that, then another ISP will give you service...picking up the slack that that one ISP is so stupid to deny.

---

