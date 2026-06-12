---
title: "Why does Windows slow down eventually"
date: 2008-12-15
forum: Windows
---

### Post by upapilot on 2008-12-15
I've experienced that all Windows eventually slow down until their speed is half or quarter their original speed. Why does this happen?

---

### Post by exploder on 2008-12-15
There are several reasons for the slow downs. The more applications that are added and removed the larger the registry becomes. Windows NTFS does not write data to the hard drive in a very efficient manner and creates a need to defragment the drive often. Unnoticed temporary files build up over time and slow down the system. Windows tends to keep many services running in the background that you will probably never need. The firewall and anti virus software needed to try and keep the system secure eat up a lot of resources. These are just some of the reasons that Windows becomes slow over time.

This topic probably should have been posted in the Windows discussions section of the forum.

---

### Post by muxenle on 2008-12-16
> **exploder said:**
> There are several reasons for the slow downs. The more applications that are added and removed the larger the registry becomes. Windows NTFS does not write data to the hard drive in a very efficient manner and creates a need to defragment the drive often. Unnoticed temporary files build up over time and slow down the system. Windows tends to keep many services running in the background that you will probably never need. The firewall and anti virus software needed to try and keep the system secure eat up a lot of resources. These are just some of the reasons that Windows becomes slow over time.

This topic probably should have been posted in the Windows discussions section of the forum.

yep

the best way to stop this is:

use low resource programgs as much as you can
keep your HD clean 
uninstall stuff you don't use
fragment your HD
clean your registry
keep it clear of virus and spy ware

---

### Post by tjandracom on 2008-12-16
[QUOTE="exploder"]The firewall and anti virus software needed to try and keep the system secure eat up a lot of resources. These are just some of the reasons that Windows becomes slow over time.[/QUOTE]

i found that cpu and memory resources are consumed the most by antivirus and its friends. by removing antivirus programs, you can speed up windows a lot. Windows (XP and later) are packaged with built in firewall, and you can use it rather than third party firewall. you can prevent and eliminate virus by implementing security setting similar to linux operating system.
e.g:
- format the system drive using NTFS. remove "Everyone" group access in "c:\", "c:\Program Files", "c:\Windows" and "c:\Windows\System32" and make those folder read-only for group "Users".
- deny "Users" from executing an executable in their "My Documents" folder. "My Documents" is the only folder that an user could write to, but they are denied to execute any programs from inside that. so any accidentaly downloaded virus could not be executed anyway,
- always separate administrator account (you can think it as root in linux) and regular user account. (default Windows is give a regular user an Administrators rights, you must change that).
- only install programs as administrator. and only install programs that you really needed and programs you really sure doesn't contain viruses or other malicious code.
- always login as regular user to do everyday job (especially to connect to the internet and/or open flash-disk or cd-rom).
- turn-off autorun when opening cd-rom or flash-disk.

with that habit, i never get a virus that affect my Windows Systems (for more that 5 years now). sometime user get virus downloaded in their documents folder, but it could be easily deleted.

---

### Post by Cool Javelin on 2008-12-16
I found an issue with Win98, then noticed it in XP. I assume Vista has the same problem, (leave it to windoz to add new features without fixing the old problems first.)

If you rename, delete, or move a lot of files, (I am thinking the number may be as low as 256 files,) windows seems to slow way down. I think this has something to do with the undo list.

If you delete a file, you can pick undo to restore it. The same happens with moving files.

I think if the list gets too long, windoz can't deal with it properly.

I have no proof other then some experimentation. I tried a fresh reboot, then moved several hundred files from one folder to another and then noticed the problem.

I tried without any virus checking or any other program running.

It is the only thing I can think of.

Mark.

---

### Post by jrusso2 on 2008-12-16
> **upapilot said:**
> I've experienced that all Windows eventually slow down until their speed is half or quarter their original speed. Why does this happen?

This does not happen to me, Some of my Windows installs are 9 years old and they are still just as fast.  I keep the registry clean and defraged.  Don't have any virus or spyware or malware,
Use and uninstaller and check the registry to make sure programs are removed completely and use a good defragger.

---

### Post by LarsKongo on 2008-12-16
To reduce the need to defrag very often you can set up a 10GB partition for XP only (30GB for Vista), don't install anything else on it. (I also recommend several partitions for different things.) You can also create a partition for your virtual memory to reduce fragmentation on C: even more. For me it only takes a couple of seconds to defrag my OS partition, and my other 50GB paritions also defrags very fast depending on how much I've used them.

Then just keep your registry and hd clean with CCleaner and defrag once in a while (once a month should be enough). After this your Windows installation should be as fast as the day you installed it, even after 2 years.

---

### Post by HermanAB on 2008-12-16
If you want to see why it is running slow, download PStools from Microsoft. It includes many utilities to see what is running, to find and stop auto-start programs and such crudware. You can also use Hijackthis from Merijn to remove crud.

Cheers,

Herman

---

### Post by MisfitI38 on 2008-12-16
> **jrusso2 said:**
> This does not happen to me, Some of my Windows installs are 9 years old and they are still just as fast.  I keep the registry clean and defraged.  Don't have any virus or spyware or malware,
Use and uninstaller and check the registry to make sure programs are removed completely and use a good defragger.

Thumbs up.
Windows XP slows down for one reason: PEBKAC
Poor computing habits is >95% of all Windows XP issues. Vista is another story.

---

### Post by BGFG on 2008-12-16
To keep windows fast you need :

Good disk and cleanup utilities - Defraggler and CrapCleaner 
Lean Antivirus and firewall - Avira, Avast, kerioSunbelt Free Firewall
To protect yourself from malware - SandboxIE
To replace big suites with Lighter Functional apps - ImgBurn, CDBurnXp, utorrent, GOM Player, Media Player Classic etc...

But mostly disk, registry and temp file maintenance.

---

### Post by fistfullofroses on 2008-12-18
+1 for tjandracom's suggestions. 

Security is one of the main reasons Windows slows down. People purchase a Windows machine and then proceed to load it down with security software. Much of the security issues in Windows are due to people leaving the system the exact way it was by default. Simply changing permissions can make the world of difference. Secondly, if people defrag their HDs, run a registry checker now and then, and uninstall all unused programs speed and response time can improve.  Most of the time, if you are not using IE, limewire, and Outlook, half of all of the viruses (if not more) for Windows will not find their ways to your machine. Beyond that, be intelligent. Porn sites are the number one source of malware. Avoid them. Also avoid serial and registration key sites. If you must get illegal software and/or porn, use bittorrent instead.

---

### Post by mikjp on 2008-12-20
Viruses, too many apps loading at the boot, registry becomes cluttered, hard disk fragmented...

---

### Post by Kernel Sanders on 2008-12-20
> **upapilot said:**
> I've experienced that all Windows eventually slow down until their speed is half or quarter their original speed. Why does this happen?

Vista doesn't. Had my install going since February 2007, still as snappy as the day I installed it. One of the major pluses of Vista tbh.

---

### Post by scorp123 on 2008-12-21
> **Kernel Sanders said:**
> Vista doesn't....  Yeah right, it's already slow as a snail to begin with :D

I have Vista pre-installed on my new Quad-Core System with 8 GB RAM..... It definitely _is_ the slowest OS I have seen in a long time. And I have seen many :D

---

### Post by fistfullofroses on 2008-12-22
Vista is a half baked release of Windows 7, like seriously, Microsoft just wasn't done with it yet, but the public wanted something new... so Microsoft delivered it. It is awful. There are very few redeeming qualities to the OS, but that is true of every single Microsoft Windows release. There were NO winxp fanboys until Vista was released. There were NO win2k fanboys until winxp was released. There were NO win3x fanboys until win95 was released.

---

### Post by AlfieSR on 2008-12-22
I just store everything except the stuff I need incase of a virus on HDD.
It's FAT32, so it only needs defragmenting about once every 3 months.

---

### Post by scorp123 on 2008-12-22
> **AlfieSR said:**
> ... so it only needs defragmenting about once every 3 months. Defragmenting? What's that????? :lolflag:

;)

---

### Post by WaeV on 2008-12-22
> **AlfieSR said:**
> I just store everything except the stuff I need incase of a virus on HDD.
It's FAT32, so it only needs defragmenting about once every 3 months.

Wait, FAT32 needs less defragmenting than NTFS?

---

### Post by RS3York on 2008-12-23
> **fistfullofroses said:**
> +1 for tjandracom's suggestions. 

Security is one of the main reasons Windows slows down. People purchase a Windows machine and then proceed to load it down with security software. Much of the security issues in Windows are due to people leaving the system the exact way it was by default. Simply changing permissions can make the world of difference. Secondly, if people defrag their HDs, run a registry checker now and then, and uninstall all unused programs speed and response time can improve.  Most of the time, if you are not using IE, limewire, and Outlook, half of all of the viruses (if not more) for Windows will not find their ways to your machine. Beyond that, be intelligent. Porn sites are the number one source of malware. Avoid them. Also avoid serial and registration key sites. **If you must get illegal software and/or porn, use bittorrent instead.**

:lolflag:

I think this post is full of good advice but that last sentence is comedy gold.  *Must* get illegal software or porn?  Under what circumstances would someone be forced to get illegal software or porn?  I could understand academic research or criminal investigations...but for the average Ubuntu user?

---

### Post by scorp123 on 2008-12-23
> **RS3York said:**
> Under what circumstances would someone be forced to get illegal software or porn? "Inner urges" maybe? :twisted:

---

### Post by Rotaj on 2008-12-23
> **AlfieSR said:**
> I just store everything except the stuff I need incase of a virus on HDD.
It's FAT32, so it only needs defragmenting about once every 3 months.

So, your HDD 32GB or less. If not, what was used to partition and format the drive?

---

### Post by MisfitI38 on 2008-12-23
> **fistfullofroses said:**
>  There were NO winxp fanboys until Vista was released...

I disagree. I've been a big fan of XP since SP2. It's a very reliable and predictable OS. Vista just makes me appreciate it that much more..

---

### Post by sportscrazed2 on 2008-12-23
i don't know but my vista partition was running super slow and yesterday i decided to reinstall it and it's almost as fast as xp.  and slightly slower than ubuntu.  i'm not installing anything that i'm not going to use so there's nothing to uninstall so hopefully it doesn't slow down its faster right now than the day i bought the pc

---

### Post by Thelasko on 2008-12-23
> **Kernel Sanders said:**
> Vista doesn't. Had my install going since February 2007, still as snappy as the day I installed it. One of the major pluses of Vista tbh.

Upon reading the title of this thread I thought, "Third party software developers doing things they shouldn't be doing."  Your comment confirms this.

For years third party software has put items in the registry unnecessarily, and forced itself to run on startup when it shouldn't.  The whole point of Vista's UAC, and why it is so hated, is because it forces these software developers to write proper code, and no longer leave your system in shambles.

I've actually been a fan of XP since SP2.  It's flaws were minor in comparison to those of the 9X family.  I think the UAC was a great step forward for Microsoft, but the rest of Vista is a mess.  It seems like Ubuntu is the system Windows is trying to be if Microsoft hadn't gotten greedy.

---

### Post by Kernel Sanders on 2008-12-23
> **scorp123 said:**
> Yeah right, it's already slow as a snail to begin with :D

I have Vista pre-installed on my new Quad-Core System with 8 GB RAM..... It definitely _is_ the slowest OS I have seen in a long time. And I have seen many :D

Then your hardware is broken. Vista flies on my 2ghz dual core with 2 gig of ram with all the bells and whistles.

Vista bashing may sound cool, but it's not valid.

---

### Post by scorp123 on 2008-12-23
> **Kernel Sanders said:**
> Then your hardware is broken. My hardware definitely works tip top and as expected under Linux. What's broken here is this crap OS they call "Vista". But never mind. In case I suddenly need space to try out another Linux or Solaris distribution, I definitely know which partition is going to be dedicated to this purpose .... :twisted:

---

### Post by scorp123 on 2008-12-23
> **Kernel Sanders said:**
> Vista bashing may sound cool, but it's not valid. Besides, I don't need to bash Vista ... videos like this one speak volumes:

[http://prash-babu.blogspot.com/2008/12/ubuntu-vs-windows-xp-vs-windows-vista.html](http://prash-babu.blogspot.com/2008/12/ubuntu-vs-windows-xp-vs-windows-vista.html)

Add to this Vista's poor security record such as the recent "zero day exploit" for Internet Explorer that apparently was spreading like mad, and you get the picture of how I think about anything that has a "Microsoft" logo on it.

I don't need to bash anything. Microsoft's crap quality does the job already for me. :lolflag:

---

### Post by WaeV on 2008-12-23
> I disagree. I've been a big fan of XP since SP2. It's a very reliable and predictable OS. Vista just makes me appreciate it that much more..

I agree.  I took some advice from this thread and deleted 25 GB of crud (old isos mostly), defragged three times until nothing was fragmented, and got a registry cleaner which removed over 1000 errors.  I use the windows standard theme and disabled many of the graphical improvements over 2k (translucent selection rectangle, show standard actions in the side of windows...)

I now run avast antivirus, no firewall (not even windows') and run my registry cleaner once every couple of days.  It's amazing the stuff the registry wil link to.  I found tags referencing install exes I deleted from my desktop months ago.

All in all, my PC is MUCH more responsive and even boots faster.

---

### Post by Open-SuSe-A-Me on 2008-12-24
+1 to everyone.  I do use linux most of the time, but whenever i have to go into XP for something (dual boot) a custom stripped down XP can be rather nice.

Everyone pretty much nailed it: defrag regularly, disable as many unneeded services and autoboot programs as possible, use Avast, Ad-Aware, and a good firewall if you dont use a router.

There is a really good guide on mininova called "hacking windows xp" which gives a ton of speed and customization tips, such as disabing file indexing that windows does any time you touch any file.  This will help more if you have many many files and folders.

---

### Post by mobilediesel on 2008-12-24
> **MisfitI38 said:**
> I disagree. I've been a big fan of XP since SP2. It's a very reliable and predictable OS. Vista just makes me appreciate it that much more..

Totally. SP2 made XP as close to great as it was ever going to be. I don't know what SP3 will do for it since I've discovered Ubuntu before SP3's release.

The main reason I switched to Ubuntu was the news of Microsoft discontinuing support for XP. Not long after that announcement I downloaded and burned Ubuntu 8.04. About a month later Internet Explorer crashed (shock. horror.) and I booted the live CD and told it to use the whole drive. I believe I said something like "DIE WINDOWS DIE!!!"

---

### Post by Battie on 2008-12-24
> **scorp123 said:**
> Besides, I don't need to bash Vista ... videos like this one speak volumes:

[http://prash-babu.blogspot.com/2008/12/ubuntu-vs-windows-xp-vs-windows-vista.html](http://prash-babu.blogspot.com/2008/12/ubuntu-vs-windows-xp-vs-windows-vista.html)

Add to this Vista's poor security record such as the recent "zero day exploit" for Internet Explorer that apparently was spreading like mad, and you get the picture of how I think about anything that has a "Microsoft" logo on it.

I don't need to bash anything. Microsoft's crap quality does the job already for me. :lolflag:

Funny, that zero-day exploit was less dangerous on Vista than XP because of Protected Mode, a feature that is not available on XP's IE7.

Still not good, but Vista won over XP on that one.

(By the way, my old home PC is not even as good as Kernel Sanders's, but I've put Vista on it and it still runs like a dream, Aero and all.)

---

### Post by WaeV on 2008-12-25
> There is a really good guide on mininova called "hacking windows xp" which gives a ton of speed and customization tips, such as disabing file indexing that windows does any time you touch any file. This will help more if you have many many files and folders.

I have a book by that title all about improving performance and customizing looks.  It is a LOT easier to change the boot screen in Ubuntu.

---

### Post by tylerspaska on 2008-12-25
I don't know the answer to the OP's question, but it seems this thread has gone a different direction anyway. 

I use Altiris' Software Virtualization Solution for all my Windows installs. I helps me keep the system as clean as possible no matter how much junk you install and remove over the years. If you use a Windows system regularly I highly recommend looking into it.

---

### Post by scorp123 on 2008-12-25
> **Battie said:**
> Funny, that zero-day exploit was less dangerous on Vista than XP because of Protected Mode Like I care?? Both are crap OS by Microsoft.

> **Battie said:**
>  a feature that is not available on XP's IE7.  Repeating Microsoft's marketing blah blah blah on these forums here will get you nowhere.

> **Battie said:**
>  my old home PC is not even as good as Kernel Sanders's, but I've put Vista on it and it still runs like a dream, Aero and all. I definitely see a difference in performance when I run Vista and when I run Ubuntu, OpenSolaris or anything else on my Quad-Core rig. Vista is slow as a snail compared to the others. If I move a few directories around on Vista it takes ridiculous amounts of time. The same operation on Ubuntu (where I use XFS) and OpenSolaris 2008.11 (where ZFS is used) finishes in just a few seconds. The list goes on and on.

---

### Post by Kernel Sanders on 2008-12-25
> **scorp123 said:**
> My hardware definitely works tip top and as expected under Linux. What's broken here is this crap OS they call "Vista". But never mind. In case I suddenly need space to try out another Linux or Solaris distribution, I definitely know which partition is going to be dedicated to this purpose .... :twisted:

> **scorp123 said:**
> Besides, I don't need to bash Vista ... videos like this one speak volumes:

[http://prash-babu.blogspot.com/2008/12/ubuntu-vs-windows-xp-vs-windows-vista.html](http://prash-babu.blogspot.com/2008/12/ubuntu-vs-windows-xp-vs-windows-vista.html)

Add to this Vista's poor security record such as the recent "zero day exploit" for Internet Explorer that apparently was spreading like mad, and you get the picture of how I think about anything that has a "Microsoft" logo on it.

I don't need to bash anything. Microsoft's crap quality does the job already for me. :lolflag:

Troll post has trolled.

Vista isn't perfect by a long shot, but your comments suggest little more than trolling. I mean Vista has a poor security record? Since when? Actually, I don't know why i'm bothering, you're simply on a anti-vista troll, so discussing the issue would be pointless and a waste of both of our time.

Sorry, but I find the whole "VISTA=FAIL LOL!!!" argument so tedious and boring. There are many people like me that use Vista without issue, and we don't have super computers either. 

So please stop spreading FUD. It doesn't help Linux adoption if that's what your aim was, and actually makes us appear in a more negative light to potential new Linux users, so you really aren't helping.

---

### Post by Irony on 2008-12-25
Windows has always been faster than Linux for me.

I've used windows 95, 98 and XP home. 98 I took over from someone else but I cleaned it up over time and it just got faster. XP I had fresh and its always been fast.

I guess I am just regimented about everything. For example I use custom installs for programs so that I install only what I want. When I uninstall I also check the registry and delete stuff from there. XP has never crashed on me.

I prefer linux because things are more configurable, I like the multiple desktops and middle button clicking - I like that I can use a simple copy command to copy the entire linux operating system to another partition. I like that I can update without having to pay for another operating system.

---

### Post by scorp123 on 2008-12-25
> **Kernel Sanders said:**
> There are many people like me that use Vista without issue, and we don't have super computers either.   Well then, be happy. I don't have a super-computer and Vista simply put stinks sky-high when compared to any of the other OS'es that I use here. Seems our definitions of "works without issue" are different. I can live with that. Can you?

> **Kernel Sanders said:**
>  It doesn't help Linux adoption  I don't care about that either. Telling people what they should use and should not use is wrong. Trying to convert people to anything is wrong, be that their religion or their OS. If someone out of their own free will wants to convert to Linux that's fine. If they have questions - fine: that's what these forums are good for. But if they carry on and use whatever other OS they already have used before that's fine too. Linux isn't for everyone. I can accept that. But you seem to have troubles to accept the fact that there are people like me who have dozens of valid reasons not to use and especially not to like Vista?? Is that your problem?

---

### Post by Battie on 2008-12-25
> **scorp123 said:**
> Like I care?? Both are crap OS by Microsoft.

 Repeating Microsoft's marketing blah blah blah on these forums here will get you nowhere.

 I definitely see a difference in performance when I run Vista and when I run Ubuntu, OpenSolaris or anything else on my Quad-Core rig. Vista is slow as a snail compared to the others. If I move a few directories around on Vista it takes ridiculous amounts of time. The same operation on Ubuntu (where I use XFS) and OpenSolaris 2008.11 (where ZFS is used) finishes in just a few seconds. The list goes on and on.

It's not "marketing blah blah blah," it's just a fact.  XP doesn't have protected mode for IE.

My job revolves around Microsoft products, good, bad, or indifferent.  That means that I have to know what they're about and what they do.  And maybe more importantly, I have to be able to separate fact from FUD for the people I support.  Vista does come with surprises, and if I can't anticipate and overcome them for my customers or have the facts to ease their hesitation, we're all sunk.  There has been so much damage done to Vista's rep by people who, IMHO of course, have no idea what they're really talking about, that it can be a big task to help peope face the inevitable advances of technology within our corporation.

I'm sorry Vista's been a bad experience for you, and it's fine with me if you dislike Vista and don't want to run it.  However, it's not been bad for everyone, and it's been good for many.  Moreover, if you work in the IT field, chances are that you're going to have to deal with MS products, and your bias is not going to carry you far.

---

### Post by scorp123 on 2008-12-25
Someone called me a "troll" a bit further up. LOL. But OK, let's do some trolling then. Let's do a **"Windows vs. Linux"** ... based on security advisories! (supplied by Secunia and publicly available on their website: [www.secunia.com](www.secunia.com))

_**Windows Vista:**_

[IMG]http://secunia.com/advisories/graph/?type=sol&period=all&prod=13223[/IMG]

As Windows Vista was released on January 2007, we're going to look at Ubuntu 7.04, 7.10, 8.04 and 8.10 too (technically all these Ubuntu releases are still available and still being distributed). But let's look at Windows XP first.


_**Windows XP:**_

[IMG]http://secunia.com/advisories/graph/?type=sol&period=all&prod=16[/IMG]


_**Ubuntu Linux 7.04:**_

[IMG]http://secunia.com/advisories/graph/?type=sol&period=all&prod=14068[/IMG]


**_Ubuntu 7.10:_**

[IMG]http://secunia.com/advisories/graph/?type=sol&period=all&prod=16251[/IMG]


**_Ubuntu 8.04:_**

[IMG]http://secunia.com/advisories/graph/?type=sol&period=all&prod=18611[/IMG]


_**Ubuntu 8.10:**_

[IMG]http://secunia.com/advisories/graph/?type=sol&period=all&prod=20299[/IMG]


The forum software is limiting the number of pictures that can be posted, so I can't post everything I wanted to show, e.g. the average criticality of a security issue on Windows vs. Ubuntu Linux ... But even so: the numbers here still are pretty clear I guess? Canonical Ltd. 4 x gets a completely green pie chart: "0% unpatched security issues" in Ubuntu Linux (releases 7.04 up to 8.10) .... Whereas Microsoft still has around 13% of unpatched issues in Vista and XP.

So the next "zero day exploit" is just waiting to happen. So all you Windows users out there: Have fun hunting worms, viruses, trojans and good luck with those patches ... should Microsoft ever be so merciful to release them and even bother to address those issues.

---

### Post by scorp123 on 2008-12-25
> **Battie said:**
> However, it's not been bad for everyone, and it's been good for many.   I am aware of that. It's just that I honestly don't care. There are certain types of flies who *love* to eat all kinds of smelly stuff ... manure, excrements, cadavers, ..... 1 billion flies can't be wrong, right? :lolflag:

You see ... I don't really care what 1 billion flies think about "how good" that smelly food of their's is ... I know it's not for me. Same goes for anything that has a "Microsoft" sticker on it. I don't really care.

> **Battie said:**
>  Moreover, if you work in the IT field ... your bias is not going to carry you far. It has carried me far enough so far :D

---

### Post by Kernel Sanders on 2008-12-25
Your posts are starting to get ridiculous. ALL your doing is bashing Vista with FUD.

For someone who "doesn't care" you're putting an awful lot of effort into anti-vista trolling aren't you?

---

### Post by Maxxtsch on 2008-12-25
You just have to maintain it, I noticed when google toolbar is stuck in there, it bog's it down to almost 1/2 the speed.(in Vista)

---

### Post by Maxxtsch on 2008-12-25
> **Kernel Sanders said:**
> Your posts are starting to get ridiculous. ALL your doing is bashing Vista with FUD.

For someone who "doesn't care" you're putting an awful lot of effort into anti-vista trolling aren't you?

THANK YOU, stop bashing vista

---

### Post by TheUnderTaker on 2008-12-25
Vista is not slow because Microsoft Rushed it. The Kernel In vista is completly redesigned from xps kernel. Microsoft admited it was bloated.

---

### Post by TheUnderTaker on 2008-12-25
I am not bashing vista. It was like this too. Windows 2000 was a new kernel and it was slower than nt 4.0. XP was the refined kernel of windows 2000. 

Nt 4.0= NT kernel 4.0
Windows 2000= Nt kernel 5.0
Windows xp= Nt kernel 5.1
Windows Vista= Nt kernel 6.0
Windows 7= NT kernel 6.1

---

### Post by scorp123 on 2008-12-25
> **Kernel Sanders said:**
> Your posts are starting to get ridiculous. ALL your doing is bashing Vista with FUD. FUD??? Now you're the one being ridiculous. The security holes on Microsoft operating systems are a technical fact. That they remain unpatched for a very long time is a fact too. No FUD here by a wide stretch. Just simple facts. If you can't take it ... fine. :lolflag:

> **Kernel Sanders said:**
> For someone who "doesn't care" you're putting an awful lot of effort into anti-vista trolling aren't you? Even if that were true .... why does it even bother *you*? It's not like you're Bill Gates, or a Microsoft programmer, or working for their marketing division?

Besides: I at least am on a Linux forum ... You won't see me going to Microsoft forums and spread any "You know, actually Linux isn't that bad ... " messages over there. Maybe that would be an idea for you as well?

OP's question was answered as far as I can tell. Unless something interesting pops up here I'd say this is the end of the discussion then. ):P

---

### Post by scorp123 on 2008-12-25
> **TheUnderTaker said:**
>  Microsoft admited it was bloated. I bet Mr./Mrs. (?) Sanders up there will soon accuse you too of "bashing Vista" and of "spreading FUD" ... unless of course you could backup that statement above with sources? :D

---

### Post by WaeV on 2008-12-26
> **tylerspaska said:**
> I don't know the answer to the OP's question, but it seems this thread has gone a different direction anyway. 

I use Altiris' Software Virtualization Solution for all my Windows installs. I helps me keep the system as clean as possible no matter how much junk you install and remove over the years. If you use a Windows system regularly I highly recommend looking into it.

Interesting.  Does this cause any performance losses?  Clearly it would prevent 'registry rot', but when compared side by side with an actual install, does a virtual install go any perceptible amount slower?

---

### Post by TheUnderTaker on 2008-12-26
He also said the kernel is very streamlined in vista which is true IMO.

[http://www.builderau.com.au/news/soa/Microsoft-admits-Windows-is-large-and-bloated-/0,339028227,339283093,00.htm](http://www.builderau.com.au/news/soa/Microsoft-admits-Windows-is-large-and-bloated-/0,339028227,339283093,00.htm)

---

### Post by scorp123 on 2008-12-26
> **TheUnderTaker said:**
>  [http://www.builderau.com.au/news/soa/Microsoft-admits-Windows-is-large-and-bloated-/0,339028227,339283093,00.htm](http://www.builderau.com.au/news/soa/Microsoft-admits-Windows-is-large-and-bloated-/0,339028227,339283093,00.htm)  "Microsoft admits Windows is 'large' and 'bloated' .... "

Interesting read, thanks for that link.

As for Windows being "streamlined" ... Well ... Windows 2008 Server supposedly can be installed in such a way so that you get a "terminal only" system. They call that a "Server Core" installation:
[http://en.wikipedia.org/wiki/Windows_server_2008#Server_Core](http://en.wikipedia.org/wiki/Windows_server_2008#Server_Core)

The most interesting bit from there is this: > "... Iain Anderson, a product manager on the Windows Server team, noted that a primary motivation for producing a Server Core variant of Windows Server 2008 was to reduce the attack surface of the operating system, and that about 70% of the security vulnerabilities in Microsoft Windows from the prior five years would not have affected Server Core."

I can't help but get the impression that they are trying to emulate a typical Linux OS server installation (e.g. no GUI, no browser, everything is done via CLI ...)

But does that make sense? If you had to run a command-line only server you could just as well pick a Linux distribution, IMHO. (that's also an argument I often hear from my customers and why they are reluctant to pay any money for Windows 2008 ... those who use it are happy with what Windows 2003 can do for them; if they want a "terminal only" server they'd rather pick a free Linux distro ...)

It will be interesting to see how widely this will be adopted.

---

### Post by MisfitI38 on 2008-12-27
> **scorp123 said:**
> ..if they want a "terminal only" server they'd rather pick a free Linux distro ...



Free GNU/Linux distros that come with absolutely no warranty?
This might be ok for some firms, but many do not want the accountability put upon themselves. 
It is just good business for many large corporations to pay someone else, like Microsoft, in order to shift that accountability elsewhere. 
This is not an oversimplification.

---

### Post by scorp123 on 2008-12-28
> **MisfitI38 said:**
> Free GNU/Linux distros that come with absolutely no warranty?  I know several customer companies (some large, some small) which are absolutely happy with Debian and variations thereof. I know several cases where they even created their own distribution based on a Debian distro. One such case is publicly known here in Switzerland and therefore I guess it's no problem if I mention them here: 

"GIBB" is the "Gewerblich-Industrielle Berufsschule Bern" (Commercial/Industrial Trade School of Berne):
[http://www.gibb.ch](http://www.gibb.ch)

So if you were to start an apprenticeship in the Bern area you'd most likely attend that school 3x per week in addition to your on-the-job training that you'd receive at your employer. In order to train their IT/CS students "GIBB" have created their own Linux distro based on Knoppix with a licensed copy of VMware as add-on for the virtualisation (the students are then charged a small fee for the licenses that the closed-source components require):

"GIBBix"
[http://www.gibbix.ch/core/?site=content2&menu=31](http://www.gibbix.ch/core/?site=content2&menu=31)

> **MisfitI38 said:**
>  This might be ok for some firms As far as I can tell many firms do this. It's not like 10 years ago when hardly anyone knew Linux. Nowadays there are plenty of IT/CS students out there whom you could hire as relatively cheap Linux admins. 

> **MisfitI38 said:**
>  but many do not want the accountability put upon themselves.  One magic word here: outsourcing to third-world countries. In 2007 my well-paid job as "support specialist" was axed too (I now work for the competition :D ). And according to what I heard from former customers the quality of support given to them now is abysmal and yet they are being charged the same prices. They feel like they're being ripped off. And sooner or later such customers will cancel their support contracts. Why pay any money if the support is so totally abysmal?

I can easily imagine that many companies have had a similar experience. So if thanks to outsourcing the support has gotten so bad that you can't rely on it anymore you could just as well do some "insourcing" and do the support yourself with your own people.

And that's exactly the trend I am seeing with certain customer companies. So in the end it does not matter to them that they can't get support. They have to hire their own people ... and if that's the case they might just as well rely on free Linux distributions such as CentOS and/or Debian so they can at least be sure that they won't have any bad surprises or unexpected license issues there.

But of course, I also know plenty of customers who have support contracts with e.g. Red Hat and Novell ... but as far as I know those companies too will use a free distro if it suits their purposes. I know of at least one case where they use OpenBSD (so that's not even a Linux ...) as a firewall solution because their paranoid admin doesn't trust anything else.

> **MisfitI38 said:**
>  It is just good business for many large corporations to pay someone else, like Microsoft, in order to shift that accountability elsewhere.  What good is this "shifting of accountability elsewhere" when your servers are down? And if the support you have to pay for is so bad that you might just as well cancel it altogether? And voila, all of a sudden the ability to point fingers at someone becomes totally irrelevant, especially during times like these where every single cent counts and where spending or not spending money makes a difference if your company is still in business tomorrow or not. Faced with this those finger-pointing games become irrelevant. And what if the company you paid for support all of a sudden goes out of business tomorrow? Don't tell me "can't happen" ... if you have been watching the news lately you should know very well that it can happen anytime and without prior warning. With this in mind it should easy to see why one might prefer a free distro such as Debian and variations thereof: No vendor lock-in, you're not depending on the mercy of a single company and you're not lost should anyone all of a sudden go out of business.

Finger-pointing is only nice for managers and right now I'd say it's somewhat of a luxury many companies don't want to spend on at the moment.

---

### Post by Kernel Sanders on 2008-12-28
Still trolling then? :(

This thread is about why Windows slows down eventually, (something that was valid for XP but not with Vista.) NOT a "let's bash Vista" thread.

Please let people use whatever operating system they want rather than evangelising. Vista is a good operating system, just like Ubuntu is a good operating system. Bashing either in a thread like this is pointless and comes accross as childish.

Please stop with the windows bashing. You aren't helping.

---

### Post by scorp123 on 2008-12-28
> **Kernel Sanders said:**
> Still trolling then? :( WTF? 

> **Kernel Sanders said:**
> NOT a "let's bash Vista" thread. Your pointless accusations and your inability to grasp a discussion based on simple facts is kinda getting boring.

---

### Post by exploder on 2008-12-28
Things might have gone a bit off topic but I did find scorp123's post interesting. I used to work in IT until the company closed it's doors. scorp123's comments brought up some interesting points and things to consider.I do not consider the post as trolling.

---

### Post by inxygnuu on 2008-12-28
@ OP: spyware, programs, adware and viruses, registry, and a lot of other sh**.

---

### Post by lisati on 2008-12-28
> **BGFG said:**
> To keep windows fast you need :

Good disk and cleanup utilities - Defraggler and CrapCleaner 
Lean Antivirus and firewall - Avira, Avast, kerioSunbelt Free Firewall
To protect yourself from malware - SandboxIE
To replace big suites with Lighter Functional apps - ImgBurn, CDBurnXp, utorrent, GOM Player, Media Player Classic etc...

But mostly disk, registry and temp file maintenance.

A couple of "no frills" crud cleaners that remove *some* temporary files that are missed by Windows "Disk cleanup" utility can be found at [http://geocities.com/rjv_soft/ssc](http://geocities.com/rjv_soft/ssc)

---

### Post by scorp123 on 2008-12-28
> **exploder said:**
> scorp123's comments brought up some interesting points and things to consider.I do not consider the post as trolling. Exactly ... all I said a few postings earlier is that I kinda dislike Vista (that's a matter of personal taste, and tastes are different) and that IMHO it's slower on my system than any of the Linux distros or e.g. OpenSolaris 2008.11 (so this is a personal observation with no claim whatsoever to represent a "universal truth" in any way ...) ... But is that "trolling" or "bashing" ??  I kinda doubt that.

> **exploder said:**
>  I used to work in IT until the company closed it's doors. scorp123's comments brought up some interesting points and things to consider OK, I got a little carried away up there. My point was that companies do not only use free Linux distributions, they sometimes even create their own. The argument "you won't get any support and can't blame anyone else" that MisfitI38 brought up isn't so much of a obstacle any more as it used to be a few years ago. As I see it I was engaging in a normal peaceful discussion with MisfitI38 about the points he/she brought up ... OT maybe as far as this thread is concerned .... but trolling???? bashing???? I kinda fail to see that in my recent few postings ... :confused:

---

### Post by Kernel Sanders on 2008-12-28
Oh for goodness sake. The topic here is "why does Windows slow down eventually". Your response has been to troll the thread with Vista bashing. It's clear for all to see. Here are just the first few of your posts that I could be bothered to C+P:

> **scorp123 said:**
> Yeah right, it's already slow as a snail to begin with :D

I have Vista pre-installed on my new Quad-Core System with 8 GB RAM..... It definitely _is_ the slowest OS I have seen in a long time. And I have seen many :D

> **scorp123 said:**
> Defragmenting? What's that????? :lolflag:

;)

> **scorp123 said:**
> "Inner urges" maybe? :twisted:

> **scorp123 said:**
> What's broken here is this crap OS they call "Vista". But never mind. In case I suddenly need space to try out another Linux or Solaris distribution, I definitely know which partition is going to be dedicated to this purpose .... :twisted:


> **scorp123 said:**
> Besides, I don't need to bash Vista ... videos like this one speak volumes:

[http://prash-babu.blogspot.com/2008/12/ubuntu-vs-windows-xp-vs-windows-vista.html](http://prash-babu.blogspot.com/2008/12/ubuntu-vs-windows-xp-vs-windows-vista.html)

Add to this Vista's poor security record such as the recent "zero day exploit" for Internet Explorer that apparently was spreading like mad, and you get the picture of how I think about anything that has a "Microsoft" logo on it.

I don't need to bash anything. Microsoft's crap quality does the job already for me. :lolflag:

> **scorp123 said:**
> Like I care?? Both are crap OS by Microsoft.

 Repeating Microsoft's marketing blah blah blah on these forums here will get you nowhere.


> **scorp123 said:**
> Vista simply put stinks sky-high when compared to any of the other OS'es that I use here.


> **scorp123 said:**
> I am aware of that. It's just that I honestly don't care. There are certain types of flies who *love* to eat all kinds of smelly stuff ... manure, excrements, cadavers, ..... 1 billion flies can't be wrong, right? :lolflag:

You see ... I don't really care what 1 billion flies think about "how good" that smelly food of their's is ... I know it's not for me. Same goes for anything that has a "Microsoft" sticker on it. I don't really care.

 It has carried me far enough so far

For people like me who had an interest in discussing the OP's issue, all you've done is get in the way and troll. There is absolutely no need of it. Please grow up.

---

### Post by p_quarles on 2008-12-28
> **scorp123 said:**
> op's question was answered as far as i can tell. Unless something interesting pops up here i'd say this is the end of the discussion then. ):p

+1

---

