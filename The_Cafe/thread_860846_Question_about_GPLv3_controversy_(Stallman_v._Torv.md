---
title: "Question about GPLv3 controversy (Stallman v. Torvalds?)"
date: 2008-07-16
forum: The Cafe
---

### Post by erans on 2008-07-16
I've been reading some articles about the history of Linux and I came across a few by Dan Lyons (the fake Steve jobs) talking about Richard Stallman's plan for a GPLv3. 

In it, he writes: > HP has asked Stallman to eliminate a clause that would prevent companies that distribute GPLv3 programs from bringing patent infringement claims against those programs in the future. Stallman has refused to remove the clause.

And Linus Torvalds, who created Linux 15 years ago while he was a college student, doesn't like another GPLv3 clause that would prohibit companies from using GPLv3 code to create digital rights management (DRM) schemes. Torvalds says he won't adopt the new license and will stick with GPLv2 instead.

I'm new to the whole free software thing, so I don't really understand the controversy here (especially the first paragraph in that quote). Also, what are DRM schemes? Copyrighting programs that use open-source code? Like Red Hat Enterprise? 

I wasn't sure where to put this thread. Seems like it should fit in "Beginner Talk." 

Thanks in advance! I'm very interested in this subject now. Link to the Lyons article here: [http://www.forbes.com/technology/2006/08/31/stallman-linux-opensource_cz_dl_0831stallman.html](http://www.forbes.com/technology/2006/08/31/stallman-linux-opensource_cz_dl_0831stallman.html)

This one is also good: [http://members.forbes.com/forbes/2006/1030/104.html?token=MjMgU2VwIDIwMDcgMDE6NTk6MDMgKzAwMDA%253D](http://members.forbes.com/forbes/2006/1030/104.html?token=MjMgU2VwIDIwMDcgMDE6NTk6MDMgKzAwMDA%253D)

---

### Post by nanotube on 2008-07-16
there's a lot to be said on this topic... but as in most cases, wikipedia will give you a good start.

---

### Post by erans on 2008-07-16
I'm especially confused about this statement: "a clause that would prevent companies that distribute GPLv3 programs from bringing patent infringement claims against those programs in the future."

I really don't have any idea what that means. Bringing up lawsuits against programs that you're distributing yourself?

---

### Post by erans on 2008-07-16
I found the actual clause. It says: >     [Y]ou may not initiate litigation (including a cross-claim or counterclaim in a lawsuit) alleging that any patent claim is infringed by making, using, selling, offering for sale, or importing the Program or any portion of it.

Is this saying that if you release something under the GPLv3 and someone ELSE takes it and starts selling it/manipulating it or portions of it, you can't initiate a lawsuit against them?

---

### Post by samjh on 2008-07-16
> **erans said:**
> I found the actual clause. It says: 

...

Is this saying that if you release something under the GPLv3 and someone ELSE takes it and starts selling it/manipulating it or portions of it, you can't initiate a lawsuit against them?

Be careful not to interpret it outside of context.

Here's the full paragraph:
[quote=GPLv3 Section 10 para 3]You may not impose any further restrictions on the exercise of the rights granted or affirmed under this License. For example, you may not impose a license fee, royalty, or other charge for exercise of rights granted under this License, and you may not initiate litigation (including a cross-claim or counterclaim in a lawsuit) alleging that any patent claim is infringed by making, using, selling, offering for sale, or importing the Program or any portion of it.[/quote]

What it means is that you can't sue someone who is/was making, using, selling, offering for sale, or importing (this requires clarification: international trade "import" or programming "import"?) the Program (here the Program means software licensed under GPLv3) for patent infringement.

So, it's not protection against ALL lawsuits.  Just patent infringement allegations.

---

### Post by saulgoode on 2008-07-16
> **erans said:**
> Also, what are DRM schemes?

As an example, a company produces a computer and sells it loaded with GPLed software. They provide the source code for the software, thereby complying with the GPL (version 2 anyway); however, they put in their computer a hardware chip which performs a checksum-type hash of the program memory and disable operation if the calculated checksum does not match one that was stored in the hardware chip when the computer was manufactured. This allows the computer manufacturer to prevent you from modifying the GPLed program and running it on "their" computer. 

GPL version 3 is designed to prohibit the preceding scenario. Linus Torvalds has suggested that the above described situation is still in the spirit of the ["tit-for-tat"]("http://en.wikipedia.org/wiki/Tit-for-tat") philosophy which attracted him to GPLv2. The company does, after all, provide any improvements they made back to the community; and a user can use those changes *on a different machine*. 

The authors of the GPLv3 believe that such hardware lock-in goes against the philosophy of Free Software where the user should have control of his computer and therefore they stipulate that when distributing GPLv3 code: "*the Corresponding Source conveyed under this section must be accompanied by the Installation Information*", with "Installation Information" being any activation keys or methods which might otherwise lock out the user.

---

### Post by Canis familiaris on 2008-07-16
> **saulgoode said:**
> As an example, a company produces a computer and sells it loaded with GPLed software. They provide the source code for the software, thereby complying with the GPL (version 2 anyway); however, they put in their computer a hardware chip which performs a checksum-type hash of the program memory and disable operation if the calculated checksum does not match one that was stored in the hardware chip when the computer was manufactured. This allows the computer manufacturer to prevent you from modifying the GPLed program and running it on "their" computer. 

GPL version 3 is designed to prohibit the preceding scenario. Linus Torvalds has suggested that the above described situation is still in the spirit of the ["tit-for-tat"]("http://en.wikipedia.org/wiki/Tit-for-tat") philosophy which attracted him to GPLv2. The company does, after all, provide any improvements they made back to the community; and a user can use those changes *on a different machine*. 

The authors of the GPLv3 believe that such hardware lock-in goes against the philosophy of Free Software where the user should have control of his computer and therefore they stipulate that when distributing GPLv3 code: "*the Corresponding Source conveyed under this section must be accompanied by the Installation Information*", with "Installation Information" being any activation keys or methods which might otherwise lock out the user.

So why does Linus disagree?

---

### Post by wrtpeeps on 2008-07-16
> **erans said:**
> I'm especially confused about this statement: "a clause that would prevent companies that distribute GPLv3 programs from bringing patent infringement claims against those programs in the future."

I really don't have any idea what that means. Bringing up lawsuits against programs that you're distributing yourself?

Basically, they can't patent GPL programs.

---

### Post by ukripper on 2008-07-16
> **wrtpeeps said:**
> Basically, they can't patent GPL programs.

i think that is the whole point of GPL!

---

### Post by samjh on 2008-07-16
Again, be careful not to interpret without context.

Bear in mind that the GPLv3 is only binding on the licensee, just like any EULA.

> You may not impose any further restrictions on the exercise of the rights granted or affirmed under this License. For example, you may not impose a license fee, royalty, or other charge for exercise of rights granted under this License, and you may not initiate litigation (including a cross-claim or counterclaim in a lawsuit) alleging that any patent claim is infringed by making, using, selling, offering for sale, or importing the Program or any portion of it.

To explain that portion, here's a scenario:

1. Acme Software Inc is a software producer and distributor.

2. One of Acme Software Inc' products is Acme Office, distributed under GPLv3.

3. Acme Office unfortunately appears to infringe on some patents owned by Megasoft Corporation.

4. Megasoft Corporation is/was never a licensee of Acme Office.

Megasoft Corporation **can** file a lawsuit against Acme Software Inc about alleged patent infringements in Acme Office!

However, if #4 was different, so that Megasoft is actually a Acme Office licensee, then Megasoft **cannot** sue.

For issues related to patents, read section 11 of the GPLv3 text.  The section is nicely summarised by the first three paragraphs:
> A &#8220;contributor&#8221; is a copyright holder who authorizes use under this License of the Program or a work on which the Program is based. The work thus licensed is called the contributor's &#8220;contributor version&#8221;.

A contributor's &#8220;essential patent claims&#8221; are all patent claims owned or controlled by the contributor, whether already acquired or hereafter acquired, that would be infringed by some manner, permitted by this License, of making, using, or selling its contributor version, but do not include claims that would be infringed only as a consequence of further modification of the contributor version. For purposes of this definition, &#8220;control&#8221; includes the right to grant patent sublicenses in a manner consistent with the requirements of this License.

Each contributor grants you a non-exclusive, worldwide, royalty-free patent license under the contributor's essential patent claims, to make, use, sell, offer for sale, import and otherwise run, modify and propagate the contents of its contributor version.This part basically means that if a patent holder authorises or uses their patented ideas in a GPLv3 licensed program, then the patent holder cannot enforce their patent rights with respect to the program.

GPLv2 does not include such protection.  It only says that a distributor can't distribute a GPLv2 program and satisfy its patent obligations regarding said program simultaneously.  GPLv3 protects against the threat of lawsuits themselves.

---

### Post by zmjjmz on 2008-07-16
Yeah, the no DRM clause was in there to prevent "TiVO-isation", where it runs a Linux kernel and is OSS, but any attempts to mod it result in a brick.

---

### Post by Cannaregio on 2008-07-16
> **Anurag_panda said:**
> So why does Linux disagree?

"Linux" doesn't disagree at all. In fact "Linux" as an operating system _does not exist_ and what we all use should always be called [COLOR="Blue"]GNU/Linux[/COLOR]. 

In this case is just [COLOR="#0000ff"]Linus Torvalds[/COLOR] that disagrees, the guy that gave us a working kernel, but at the same time kidnapped (and damaged) the whole GNU project philosophy with his own name.

So let him disagree, I personally stick with [Richard]("http://en.wikipedia.org/wiki/Richard_Stallman"). Always have.

You'r touching deep historical-loaded facts and questions here :-)

---

### Post by Canis familiaris on 2008-07-16
> **Cannaregio said:**
> "Linux" doesn't disagree at all. In fact "Linux" as an operating system _does not exist_ and what we all use should always be called [COLOR="Blue"]GNU/Linux[/COLOR]. 


It was a typo. I meant Linus.

---

### Post by ukripper on 2008-07-16
[QUOTE=]Cannaregio;5396171

 the guy that gave us a working kernel, but at the same time kidnapped(and damaged) the whole GNU project philosophy with his own name.

[/QUOTE]

kidnapped?? hmmmm...Bit harsh don't you agree?

---

### Post by Canis familiaris on 2008-07-16
> **Cannaregio said:**
> 
In this case is just [COLOR="#0000ff"]Linus Torvalds[/COLOR] that disagrees, the guy that gave us a working kernel, but at the same time kidnapped (and damaged) the whole GNU project philosophy with his own name.

I thought he accelerated the GNU project. GNU wouldn't have been so far if there had been no Kernel. Their kernel GNU/HURD is still not ready. It has really been a long time.
Personally I'm neither the fan of RMS or Linus. I like Mark Shuttleworth.

---

### Post by bigbearomaha on 2008-07-16
Linus didn't hijack anything. It's the nature in people to shorten terms and names, making them catchy and easy to remember.

This nonsense with Linus vs stallman and all the other hyperbole in the opensource world of distro vs distro and fan boi mentalities is what is really damaging.

You can call it GNU/Linux, you can just call it Linux, it's not meant to be a 'slight' to Stallman, who by the way isn't the grand poohbah of opensource any more than Linus is.

It boils down to Stallman is very idealistic, and in an idealistic world, there would be viable and legitimate 'free' software to perform just as well or better than commercial closed software.  It's something worth pursuing to get people to 'think' open.

In the meantime, people and systems do not change overnight and the current proprietary system was not instilled overnight either.

It will require transitory software and time for people to see the impact and benefits of free software.   Where free software has not made any visible gains yet,  people who are in need of that type of software will use what they need to use to get a task or job done.  That is just a rule of productivity.

If people in GNU camp are so determined, they might try to kindle interest in programmers and coders to create viable 'user' apps like greeting card apps and such.  You and I might not use them them or think them trivial, but the fact remains that a huge majority of 'everyday' computer users do use those types of apps on a regular basis.

Big Bear

---

### Post by original_jamingrit on 2008-07-16
for a little bit of background on the DRM part: ['Flame Linus to a crisp!'](http://marc.info/?l=linux-kernel&m=105115686114064&w=2)

While he's not promoting or advocating DRM, he does have a rather passive stance on it.  It goes back to the freedom debate:  If the GPLv3 restricts people's freedom to restrict other people's freedom, is the GPLv3 really free?  I would argue that the GPLv3 is not free in this sense, but that's okay, because it's intended to preserve *everybody's* freedom, and not just vendor freedom.  As far as I'm concerned, I'm happy with the Linux kernel being GPLv2, and I'm happy with other things being GPLv3.  It's just that Linus and the Linux devs kind of take it from granted that they won't get any useful bug reports from users of a tainted (ie; tainted with proprietary modules) Linux.

As for the clause against suing for patents thing, that's just common sense.  Stallman should have no reason at all for removing it.

---

### Post by saulgoode on 2008-07-16
> **original_jamingrit said:**
> It goes back to the freedom debate:  If the GPLv3 restricts people's freedom to restrict other people's freedom, is the GPLv3 really free?  I would argue that the GPLv3 is not free in this sense, but that's okay, because it's intended to preserve *everybody's* freedom, and not just vendor freedom.
The flaw with your logic is that the GPL does not restrict anyone's freedom. Distribution of copyrighted software is restricted *by copyright law*. The GPL places conditions under which such distribution is permitted; **it** does not restrict distribution, it only serves to permit it.

---

### Post by the_darkside_986 on 2008-07-16
The GPLv3 clause about patent protection was a response to the Novell-Microsoft deal about patent licenses, so that any patent protection purchased by Novell has to apply to all users of the GPL3 licensed software, not just Novell customers. 

And GPLv3 _does_ restrict some freedom--that is--the "freedom" of oppressive software vendors to restrict the users in different ways, but that's not really a valid freedom I suppose.  But DRM in the kernel would be like any other unclean module, if the user wants to sign away their freedom, that's their business as long as it is purely optional and not the default on distros such as Ubuntu. I have little concern about efforts of Hollywood to "protect" their manufactured garbage they call entertainment but when it starts threatening my computer usage freedom then I will be very defensive.

---

### Post by original_jamingrit on 2008-07-16
> **saulgoode said:**
> The flaw with your logic is that the GPL does not restrict anyone's freedom. Distribution of copyrighted software is restricted *by copyright law*...

Sorry, I guess I did word that kind of awkwardly.  What I meant was this:  **If** the GPL offered total freedom, then it would be offering vendors the freedom to place restrictions on the freedom of other people.  The GPL **does not** do this, and was made for the general purpose of not allowing this sort of thing, just as the_darkside_986 pointed out.  The GPL is a copy-left, but it is not a copy-wrong ;-) (which is to say, it's intended to be different from a normal copyright license, but it isn't the opposite of copyright).  Otherwise, the GPL would serve no purpose at all.

---

### Post by Foster Grant on 2008-07-16
> **Cannaregio said:**
> "Linux" doesn't disagree at all. In fact "Linux" as an operating system _does not exist_ and what we all use should always be called [COLOR="Blue"]GNU/Linux[/COLOR]. 

In this case is just [COLOR="#0000ff"]Linus Torvalds[/COLOR] that disagrees, the guy that gave us a working kernel, but at the same time kidnapped (and damaged) the whole GNU project philosophy with his own name.

So let him disagree, I personally stick with [Richard]("http://en.wikipedia.org/wiki/Richard_Stallman"). Always have.

You'r touching deep historical-loaded facts and questions here :-)

So are you, inaccurately.

Linus Torvalds didn't even come up with the name Linux; he favored the name "Freax"(freak/free/X) for his school project. His friend Ari Lemmke, then the server administrator at Helsinki University of Technology, didn't like "Freax" and came up with "Linux" on his own. Linus only trademarked it after an attorney named William R. Della Croce Jr. engaged in trademark-squatting, trying to extort money from Linux companies. At first glance, this appears to be Mr. Della Croce's only contribution to Linux, open source, computer science or indeed the world at large. (Don't believe me? Ask [Google](http://www.google.com/search?q=William+R.+Della+Croce&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a).)

(Linus didn't even come up with what is popularly known [Linus' Law](http://en.wikipedia.org/wiki/Linus%27s_law). [Eric S. Raymond](http://en.wikipedia.org/wiki/Eric_S._Raymond) did that, and he's been a much better philosopher advocate for open source than RMS has.)

GNU had already put its name on an operating system kernel: GNU Hurd, a stalled project with a string of bad kernel choices (they're on their fourth kernel now and would have gotten nowhere if the Debian team hadn't helped out). It's only been relatively recently that any GNU Hurd kernel has run at all.

If you think "GNU" should be stuffed on the front, you should also have to include Python, Minix, Xfree386, TeX, KDE, GNOME,  Perl, Apache and a thousand million other projects on the front; they deserve as much credit as GNU, if not more. It becomes slightly unwieldy after a while.

Perhaps Jim Gettys, the founder of the X windowing system, put it best: "There are lots of people on this bus; I don't hear a clamor of support that GNU is more essential than many of the other components; can't take a wheel away, and end up with a functional vehicle, or an engine, or the seats. I recommend you be happy we have a bus."

It's a very nice bus. Perhaps we can all stop fighting over it?

---

### Post by saulgoode on 2008-07-16
> **Foster Grant said:**
> [Eric S. Raymond](http://en.wikipedia.org/wiki/Eric_S._Raymond) did that, and he's been a much better philosopher advocate for open source than RMS has.
That's because RMS doesn't advocate *Open Source*, he advocates Free Software. :razz:

---

### Post by Foster Grant on 2008-07-16
> **saulgoode said:**
> That's because RMS doesn't advocate *Open Source*, he advocates Free Software. :razz:

It's nice to have a bearded utopian around, but we got a lot further with reasonable pragmatism.

And ESR is right: You should be able to make money on your creation if that's what you choose. Stallman leaves the impression that he would have all programmers working for free.

[http://www.linuxtoday.com/news_story.php3?ltsn=2001-08-17-016-20-OP-CY](http://www.linuxtoday.com/news_story.php3?ltsn=2001-08-17-016-20-OP-CY)

> I'm not going to make any claims about "freedom" here. I'm just talking about flerbage. But if you the reader agree with me that more flerbage is a good thing and less flerbage is a bad thing, then there are some questions we may want to ask Bradley Kuhn and Richard Stallman.

Here's the first and most important one: **if you two could get a law passed making proprietary licenses illegal, would you do it?**

If their answer is "no", then the dispute with Tim is over. Because that will mean they do recognize a right for developers to choose licenses as they will without being killed, jailed, or threatened for choosing the "wrong" one.

If their answer is "yes", then there are many, many other moral questions we could ask them -- and should, if only so that we can get some idea if they're too dangerous to have as neighbors.

---

### Post by saulgoode on 2008-07-16
> Here's the first and most important one: if you two could get a law passed making proprietary licenses illegal, would you do it?

This question shows Mr Raymond's utter lack of understanding of copyright privilege and licensing thereof. It would be ludicrous to enact a law providing a privilege to someone and then pass a second law to outlaw that privilege. Anyone with a lick of sense would realize that you'd merely repeal the first law.

---

### Post by toupeiro on 2008-07-17
> **saulgoode said:**
> This question shows Mr Raymond's utter lack of understanding of copyright privilege and licensing thereof. It would be ludicrous to enact a law providing a privilege to someone and then pass a second law to outlaw that privilege. Anyone with a lick of sense would realize that you'd merely repeal the first law.

You haven't reviewed many state and federal laws, have you? :lolflag:

this is done quite a bit to one level or another.

---

