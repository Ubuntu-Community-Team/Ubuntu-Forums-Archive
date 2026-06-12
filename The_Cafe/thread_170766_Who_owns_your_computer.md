---
title: "Who owns your computer?"
date: 2006-05-05
forum: The Cafe
---

### Post by Sef on 2006-05-05
This is from wired.com magazine.  It's rather interesting on ownership of computers: who really own them: you or some company or more than one.

[http://www.wired.com/news/columns/1,70802-0.html]("http://www.wired.com/news/columns/1,70802-0.html")

---

### Post by Sye d'Burns on 2006-05-05
Yeah, I posted a link to this article yesterday. I thought it was a fairly concise reasoning of the growing perils one takes running a windows box these days.
 
 More accurately, I think it's the growing perils of running programs without knowing, or having the ability to know, what's in them, regardless of platform.

---

### Post by BoyOfDestiny on 2006-05-05
[QUOTE=Sye d'Burns]Yeah, I posted a link to this article yesterday. I thought it was a fairly concise reasoning of the growing perils one takes running a windows box these days.
 
 More accurately, I think it's the growing perils of running programs without knowing, or having the ability to know, what's in them, regardless of platform.[/QUOTE]


I'll be honest, I didn't read the article... I've been aware of these perils for years, which encouraged me to move toward Linux. When the sony root kit came out (rather news of it), although unaffected, I got a new hard drive, moved my data, and wiped windows for good. Ubuntu only :)

---

### Post by Sye d'Burns on 2006-05-05
I'm pretty sure that most people who are here are aware of the perils. Wired has a much wider audience which perhaps aren't quite as informed. I think the author  did a pretty good job laying out how technology is making an ownership grab at home computers and did it in such a way that even people who can barely operate a windows machine could understand.
 
  An excerpt:
 
> 
Now, things are not so simple. There are all sorts of interests vying for control of your computer. There are media companies that want to control what you can do with the music and videos they sell you. There are companies that use software as a conduit to collect marketing information, deliver advertising or do whatever it is their real owners require. And there are software companies that are trying to make money by pleasing not only their customers, but other companies they ally themselves with. All these companies want to own your computer.


   Some examples:
        [LIST]
[*]Entertainment software: In October 2005, it emerged that [Sony had distributed a rootkit]("http://www.wired.com/news/politics/privacy/0,69601-0.html") with several music CDs -- the same kind of software that crackers use to own people's computers. This rootkit secretly installed itself when the music CD was played on a computer. Its purpose was to prevent people from doing things with the music that Sony didn't approve of: It was a DRM system. If the exact same piece of software had been installed secretly by a hacker, this would have been an illegal act. But Sony believed that it had legitimate reasons for wanting to own its customers’ machines.
[*]Antivirus: You might have expected your antivirus software to detect Sony's rootkit. After all, that's why you bought it. But initially, the security programs sold by Symantec and others did not detect it, because Sony had asked them not to. You might have thought that the software you bought was working for you, but you would have been wrong.
[*]Internet services: Hotmail allows you to blacklist certain e-mail addresses, so that mail from them automatically goes into your spam trap. Have you ever tried blocking all that incessant marketing e-mail from Microsoft? You can't.
[*]Application software: Internet Explorer users might have expected the program to incorporate easy-to-use cookie handling and pop-up blockers. After all, other browsers do, and users have found them useful in defending against internet annoyances. But Microsoft isn't just selling software to you; it sells internet advertising as well. It isn't in the company's best interest to offer users features that would adversely affect its business partners.
[*]Spyware: Spyware is nothing but someone else trying to own your computer. These programs eavesdrop on your behavior and report back to their real owners -- sometimes without your knowledge or consent -- about your behavior.
[*]Internet security: It recently [came out]("http://www.zdnet.com.au/news/security/soa/Vista_firewall_shackled_due_to_customer_demand_Microsoft/0,2000061744,39252954,00.htm") that the firewall in Microsoft Vista will ship with half its protections turned off. Microsoft claims that large enterprise users demanded this default configuration, but that makes no sense. It's far more likely that Microsoft just doesn't want adware -- and DRM spyware -- blocked by default.
[*]Update: Automatic update features are another way software companies try to own your computer. While they can be useful for improving security, they also require you to trust your software vendor not to disable your computer for nonpayment, breach of contract or other presumed infractions.[/LIST]

Articles such as this could be a great boon to FOSS.

---

### Post by kanem on 2006-05-05
When I first started reading it I was thinking how I'm glad I don't have to worry about that stuff and that **I** own my computer.

But then I realized that I really don't. Ubuntu does. Oh well, at least I trust them. Hmm, this could be an argument as to why Ubuntu should stay completely Free. As soon as closed-source apps get in the distro, someone (not us, nor Ubuntu) owns part of our computers.

Also, from the article:> Using the hacker sense of the term, your computer is "owned" by other people.
I think the proper term is Pwnz0red.;)

---

### Post by RavenOfOdin on 2006-05-05
I've been aware of this for quite a while.  The issue with TCPA/TCG was what motivated me to dump Windows completely.

---

### Post by Kvark on 2006-05-05
[QUOTE=kanem]But then I realized that I really don't. Ubuntu does.[/QUOTE]
I think that is false. Find a situation where you want the opposite of what Ubuntu wants and the software is deliberately designed to prevent you from doing what Ubuntu doesn't want you to do. If you can't find such a situation then it is you and not Ubuntu that owns your computer.

---

### Post by yabbadabbadont on 2006-05-05
[QUOTE=Kvark]I think that is false. Find a situation where you want the opposite of what Ubuntu wants and the software is deliberately designed to prevent you from doing what Ubuntu doesn't want you to do. If you can't find such a situation then it is you and not Ubuntu that owns your computer.[/QUOTE]

It used to be, at least in Breezy, the you could not remove the bluetooth software packages without your kernel being uninstalled too.  I think that fits as a valid example.  Note, however, that this behavior doesn't appear to happen in Dapper.  Perhaps they listened to user feedback.  Which is a *lot* different than in the Winblows world.

---

### Post by Kvark on 2006-05-05
[QUOTE=yabbadabbadont]It used to be, at least in Breezy, the you could not remove the bluetooth software packages without your kernel being uninstalled too.  I think that fits as a valid example.  Note, however, that this behavior doesn't appear to happen in Dapper.  Perhaps they listened to user feedback.  Which is a *lot* different than in the Winblows world.[/QUOTE]
Yeah if that is on purpose and not an uninentional bug then that is compareable to Windows taking steps to avoid users uninstalling Explorer. With Windows/Explorer it is easy to see the motives behind the evil plot. But here I don't understand why Ubuntu would deliberately force you to keep their bluetooth software. What are Ubuntu's motives behind this act?

---

### Post by yabbadabbadont on 2006-05-05
I think it was intentional, but with good intentions.  The kernel modules included bluetooth support.  Bluetooth modules need bluetooth software to do anything.  Hey, let's make the the bluetooth software packages a dependency of the kernel modules package...  something like that I would guess.

Or

I could be completely wrong (wouldn't be the first time) and it was a simple mistake that was eventually discovered and corrected.  Either way, the bahavior isn't there any more, so good for them.

---

### Post by janz84 on 2006-05-05
bluetooth support erks me since

---

### Post by Engnome on 2006-05-05
Im very scared by TCPA and all that. Read this: [http://www.gnu.org/philosophy/can-you-trust.html](http://www.gnu.org/philosophy/can-you-trust.html)  some time ago and now I know, "Im always gonna be in charge on whats going on in my computer"  If someone ever (in the future) sends me one of those "encrypted mails they are gonna have to send them again. Not gonna start som prop. software to read them.

---

### Post by Kernel Sanders on 2006-05-05
Its this that will be the greatest help to converting people to Linux IMHO.

---

### Post by Sef on 2006-05-05
> Yeah, I posted a link to this article yesterday. I thought it was a fairly concise reasoning of the growing perils one takes running a windows box these days.


Sorry, I didn't see it.  Otherwise, I would have just commeted under your thread.

---

### Post by kanem on 2006-05-06
[QUOTE=Kvark]I think that is false. Find a situation where you want the opposite of what Ubuntu wants and the software is deliberately designed to prevent you from doing what Ubuntu doesn't want you to do. If you can't find such a situation then it is you and not Ubuntu that owns your computer.[/QUOTE]
That's easy. It happens every time I want to use apt-get and Ubuntu's repositories to get a new version of a program but would have to upgrade my whole system to get it. It happens every time a program in their repository is compiled with different options than what I want.

But that's not even what I meant. What I meant was that we accept binary code from Ubuntu that could have anything in it. If, for example, the devs went psycho and decided to put malware in some app, they could do it. And we wouldn't even know about it for a long time. There could be code in all our machines that will turn them all into spambots 56 days from now. Luckily there's no reason to think that would ever happen. 

In this age of rapid updates and fast development schedules we all have to trust someone. Unless you audit every piece of code that runs on your computer, someone has the ability to screw you. It's all about who you trust. People who trust MS or Sony or other random apps they get from the net get screwed often. People who only trust their GNU/Linux distros may never get screwed. But just because your distro would never intentionally screw you doesn't mean that they don't 0wn your computer.

---

### Post by helpme on 2006-05-06
[QUOTE=kanem]That's easy. It happens every time I want to use apt-get and Ubuntu's repositories to get a new version of a program but would have to upgrade my whole system to get it. It happens every time a program in their repository is compiled with different options than what I want.
[/quote]
I'm sorry, but technical limitations of something are hardly comparable, let alone equal to Sony installing a rootkit on your computer.

[QUOTE=kanem]
But that's not even what I meant. What I meant was that we accept binary code from Ubuntu that could have anything in it. 
[/quote]
Ehm, you can easily build everything from source yourself, if you so desire. Also, of course every system has a certain potentila of being exploited, however, that's a very, very, very, very, very far cry from your system actually being exploited and that's what the article is talking about.

---

### Post by kanem on 2006-05-06
[QUOTE=helpme]I'm sorry, but technical limitations of something are hardly comparable, let alone equal to Sony installing a rootkit on your computer.[/QUOTE]
I wasn't comparing to Sony. Someone asked for an example of Ubuntu, by design, limiting what I can do with my computer. I answered. Also, it's not a technical limitation. Some other distros allow me to do those things I mentioned. But again, this has nothing to do with my point about Ubuntu 0wning my computer.

[QUOTE=helpme]
Ehm, you can easily build everything from source yourself, if you so desire. Also, of course every system has a certain potentila of being exploited, however, that's a very, very, very, very, very far cry from your system actually being exploited and that's what the article is talking about.[/QUOTE]Yes, that's actually what I say later in the post about auditing every piece of code that runs on your machine. If you build everything from source, and make sure that the source code is safe, then you can be sure that you are the master of your machine. Otherwise, you are not.

My point is that someone, not you, controls your computer. And it doesn't matter if they will never use that control for malicious ends. They still control it.  In none of my posts did I imply that this is paramount to some kind of spyware or exploitation. But it's still someone else determining the fate of your computer.

And let me be clear that I'm not complaining about this situation. I trust Ubuntu and don't have time to review code before compiling it just to make sure it's safe.

---

### Post by Kvark on 2006-05-06
[QUOTE=kanem]That's easy. It happens every time I want to use apt-get and Ubuntu's repositories to get a new version of a program but would have to upgrade my whole system to get it. It happens every time a program in their repository is compiled with different options than what I want.[/QUOTE]
Yeah, that is a big downside with getting all your programs from Ubuntu. I wish there was a way to use apt-get or something equally easy to get all programs directly from their original developers.

[QUOTE=kanem]But that's not even what I meant. What I meant was that we accept binary code from Ubuntu that could have anything in it. If, for example, the devs went psycho and decided to put malware in some app, they could do it. And we wouldn't even know about it for a long time. There could be code in all our machines that will turn them all into spambots 56 days from now. Luckily there's no reason to think that would ever happen. 

In this age of rapid updates and fast development schedules we all have to trust someone. Unless you audit every piece of code that runs on your computer, someone has the ability to screw you. It's all about who you trust. People who trust MS or Sony or other random apps they get from the net get screwed often. People who only trust their GNU/Linux distros may never get screwed. But just because your distro would never intentionally screw you doesn't mean that they don't 0wn your computer.[/QUOTE]
If the fact that you trust Ubuntu means Ubuntu owns your computer then you never own anything. The food producers could poison the food they sell to you and you wouldn't know until it's too late. All the electronics and machinery you buy from your toaster to your car could have hidden microphones or whatever and you wouldn't know. Your home could have spy equipment hidden in the walls from before you moved in. Your pets could have been injected with tracking chips before you got them. It's even possible to hide tracking chips in money so you can't tell it's there, which they do during bank transports in to trace robbers remotely. By this logic nobody has any property at all.

I think a more sane way to see it is that they own your computer only if they actually do actively control and restrict what you can do with the computer to suit their plans instead of yours. In your apt-get example I don't think it is an active plan to gain control over what you do with your computer. It is not like the Ubuntu devs added a "feature" with the sole purpose of prevening you from running the latest Firefox. If that was the case then they would have added something to prevent you from installing software from sources other then the official repos. Like a check to make sure you can run only software that Ubuntu has released a signed checksum of. Then they would own or at least control your computer.

---

### Post by kanem on 2006-05-06
[QUOTE=Kvark]stuff...[/QUOTE]
Yeah, I agree. Maybe I was a bit too liberal with my usage of the word 0wned.

---

### Post by giaguara on 2006-05-06
Nice article, thanks for linking it.
However ... my husband owns my computer ;) the one that I use with Kubuntu. I wanted something to play with, while I couldn't decide which laptop I would want to buy for myself.

---

### Post by Lovechild on 2006-05-06
[QUOTE=yabbadabbadont]It used to be, at least in Breezy, the you could not remove the bluetooth software packages without your kernel being uninstalled too.  I think that fits as a valid example.  Note, however, that this behavior doesn't appear to happen in Dapper.  Perhaps they listened to user feedback.  Which is a *lot* different than in the Winblows world.[/QUOTE]

That's a bullshit argument and here's why:

Ubuntu does in NO way stop you from issuing a simple set of commands to rebuild and tailormake your system to your needs, they even make it easy and provide you with instructions, sourcecode and tools. Microsoft on the other hand does none of these so comparing the two is hardly honest and well thought out.

Besides that is likely to be a bug, report it or don't complain. That's how feedback works, not moaning on an enduser forum.

---

### Post by yabbadabbadont on 2006-05-06
[QUOTE=Lovechild]That's a bullshit argument and here's why:

Ubuntu does in NO way stop you from issuing a simple set of commands to rebuild and tailormake your system to your needs, they even make it easy and provide you with instructions, sourcecode and tools. Microsoft on the other hand does none of these so comparing the two is hardly honest and well thought out.

Besides that is likely to be a bug, report it or don't complain. That's how feedback works, not moaning on an enduser forum.[/QUOTE]

Hmmm, where in my post did I ever say that you were prevented from rebuilding everything from source to get it the way you would like?  So let me be more specific, *by default* if you tried to remove that package using the *recommended* tools, that was the behavior you would see.  And, although you didn't include it in your quote, I also went on to say that I could be completely wrong and that it was a bug that has since been fixed.  (which it apparently was and has been)

---

### Post by Zombie process on 2006-05-06
Well, as long as you trust their binaries and updates, Ubuntu and the free projects that it depends on (I doubt every single line of code in Universe is carefully audited by hand :P ), have the power to do you or your system some damage. 

But that is a far cry from owning your computer and restricting your rights the way closed source companies often do:

If some app will not uninstall without uninstalling the kernel, you install your own (self-compiled, non-apted package) kernel and then uninstall both the default kernel and the offending package. 

If something happens that makes you not longer trust the default apt-get repositories, you can always remove them and use some other servers (your own?, Debian perhaps?)

If you would like to install a package without some optional dependencies that apt-get thinks you can't live without you can get the original sources and compile it with the options you like. ¿Can you compile Windows Media Player 10 without support for wma, wmv and DRM for example? 

If the developers decided to include something nasty in their code, you can use freedom 1 and strip the offending 'feature' or pay/wait for someone to do it for you. 

Even if an update of ubuntu erased your whole hard drive, as long as you have backups, you could restore and access your data in the conditions you wanted. The format is open so you can use a different app to read it if the original one becomes unavailable. You can change to a different software application / Operative System without fear to lose or get locked out of your data or files. 

Compare that to documents and media that you can only read with one application: one that you have no control over, one that you have no idea how it really works, one that may contact his creator before deciding whether to allow you (or not) to access your OWN data. Enter the world of Microsoft Word and .doc (for just one example). 

Note: Yes, I am aware that OpenOffice.org can read .doc, but that is the result of reverse engineering and was never what MS intended. Also... ¿have you tried using openoffice to read DRMed .docs? 

Now try playing wmv files or DVDs in the US using your favorite free software app without becoming a criminal in the process.

The difference is that while trusting Ubuntu or other free software company may get you screwed once. Trusting closed software will normally result in you getting AND REMAINING screwed until you are willing to do something drastic and lose the advantages of the software you bought and/or used time learning and maybe lose also some or all of the data YOU created or had rightful access to.

---

