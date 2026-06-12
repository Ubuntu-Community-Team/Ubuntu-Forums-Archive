---
title: "virus in ubuntu"
date: 2010-09-13
forum: Security
---

### Post by ashwani17 on 2010-09-13
Friends... I have DEll vostro 1400 n series..i used to have two os one is windows 7 and other one is ubuntu...couple of days ago i have sort of virus in Ubuntu...
1. My keyboard acting strangely ..
2. volume level goes up and down on its own...i dont have any control over it
3. Whenever i typed something..something else get typed..like long persistent 'c' stroke
4.Mouse dont work.It highlights the clicked icon.
5.Whenever i login ...my system works perfectly for few 20 minutes...afterwards it just act the way i mentioned before..i guess after few specific key strokes this virus got activated.
6.To get rid of it i removed windows and my entire data...now i am on ubuntu only...but still the problem persist.
7.I have password on bios sometime i can't even login to my sytem..as that keystroke never matches..then i remove the battery to login..

Guys please help..i losing hope now...

---

### Post by hariks0 on 2010-09-13
Obviously, some of your modifier keys [Ctrl,Alt,Shift,Super] are stuck. May be some other alphanumeric key. Just replace the keyboard to confirm. If this is the case, you have to ensure that all keys are free and not stuck.

---

### Post by DeMus on 2010-09-13
> **ashwani17 said:**
> Friends... I have DEll vostro 1400 n series..i used to have two os one is windows 7 and other one is ubuntu...couple of days ago i have sort of virus in Ubuntu...
1. My keyboard acting strangely ..
2. volume level goes up and down on its own...i dont have any control over it
3. Whenever i typed something..something else get typed..like long persistent 'c' stroke
4.Mouse dont work.It highlights the clicked icon.
5.Whenever i login ...my system works perfectly for few 20 minutes...afterwards it just act the way i mentioned before..i guess after few specific key strokes this virus got activated.
6.To get rid of it i removed windows and my entire data...now i am on ubuntu only...but still the problem persist.
7.I have password on bios sometime i can't even login to my sytem..as that keystroke never matches..then i remove the battery to login..

Guys please help..i losing hope now...

Did you have the same problems in Windows before you uninstalled it, or maybe not the same but similar problems?
If so, it might be a hardware failure of some kind. Maybe the keyboard where a key is "hanging" (making contact all the time)

---

### Post by wainbee on 2010-09-13
I have seen a similar problem where the peripheral devices (mouse, keyboard, external Soundblaster card, printer) were connected through a 7 port USB hub with a defective chip-set.  Anything that acts up after a delay sounds like a thermal hardware problem and not a virus.

---

### Post by 3Miro on 2010-09-13
This is mostly mouse and keyboard issues, try external mouse and keyboard to see if the problem is with the hardware itself.

Also, put a sensor applet to one of your Gnome bars to check if you are having a temperature issues.

You can start the computer from a live CD and see if it will do the same thing. If a LiveCD works fine, then you might have a settings problem.

If the bios is giving you hard time, this is not Ubuntu related. BIOS is active long before anything from Ubuntu has a chance to load. The bad news is that BIOS problems means hardware problems.

---

### Post by ashwani17 on 2010-09-14
well...i am using usb mouse and keyboard..but still this problem persist...i am sure enough this is not a hardware problem..
Yeah i do have, this problem in windows too..thats why i unistalled it..
I google it to death..virus do come in linux...but can be checked by some checkflags..and all.
i guess this is a boot sector virus..
so  give me some more solution

---

### Post by hariks0 on 2010-09-14
[LIST=1]
[*]Try live CDs and you can rest assured that there is no virus if the problem persists.
[*]Try with another Keyboard/mouse to see if solves the issue.
[*]Remove any hardware you have installed recently
[*]Post the results here ;)
[/LIST]

---

### Post by dragilla on 2010-09-16
This is wierd. I have Dell E6410 and now I'm experiencing something similar. This happens only when the system comes back from sleep (suspend).
The mouse goes crazy, I can't point it to login button, it seems it clicks while moving. When I finally manage to log in then everyting goes wild :)

The strange solution I found is leaving a message to myself (before logging in). This stops the mouse from going crazy and I can normally log in and everything is working fine. 

This really seems like a virus.
I have a pass for bios as well.

---

### Post by r+9 on 2010-09-16
a boot sector virus would not survive all the installs you have done, and I doubt it would cross from windows to linux environment.
If it was any kind of malware that survived all that you have done it'd be in the bios.  Those are pretty rare, but I don't know much about them.

Logically you've got a hardware problem.  It's more likely your computer is haunted than it is infected with malware.

---

### Post by The Flying Penguin on 2010-09-16
I had the same problem with passwords not matching up on my laptop. Turns out num lock was turned on. Also, make sure the function key isn't stuck (if you have one) or any other keys for that matter. It would be no surprise your mouse messes up too if you have buttons stuck.

I don't think its a virus. If it was a Linux virus, it shouldn't affect your BIOS. Did you have this problem in Wndows?

Try the live cd as recommended. That would be a good place to start.

---

### Post by kaldor on 2010-09-16
It's not a virus. You have hardware issues. If you removed Windows and put Ubuntu on, it's definately a hardware issue. Something is not working right.

A virus wouldn't cross over to Ubuntu and randomly make keys not work and mice fail, etc.

---

### Post by uRock on 2010-09-16
Moved to Security Discussions

---

### Post by ashwani17 on 2010-09-16
What i have done to resolve  it is refreshing my bios version to new bios...
u can download it from ur lappy's vendor site..I have google it and find out that boot sector virus can be removed by bios refreshing or update...It resloved the problem up to some extent..
"It's not a hardware fault"

---

### Post by rookcifer on 2010-09-16
> **ashwani17 said:**
> What i have done to resolve  it is refreshing my bios version to new bios...
u can download it from ur lappy's vendor site..I have google it and find out that boot sector virus can be removed by bios refreshing or update...It resloved the problem up to some extent..
"It's not a hardware fault"

For the 10th time it is not a virus.  You have a hardware issue somewhere.  Either the keyboard, mouse, or perhaps the I/O on the motherboard.

---

### Post by supershin on 2010-09-16
How bout running a memory test on RAM? Corrupted memory causing the fuss?

---

### Post by uRock on 2010-09-17
Go into the menus to System> Administration> System Testing. Let it do its thing and see what it says.

---

### Post by Velnias on 2010-09-17
> **uRock said:**
> Moved to Security Discussions

Reading SecurityDiscussions makes people feel like Ubuntu is less secure than Windows - see all this "security issues".
Maybe its time to create separate forums like "Panic Broadway" "ID-10t cases" "PEBKAC and PICNIC"...

---

### Post by OpSecShellshock on 2010-09-17
> **Velnias said:**
> Reading SecurityDiscussions makes people feel like Ubuntu is less secure than Windows - see all this "security issues".
Maybe its time to create separate forums like "Panic Broadway" "ID-10t cases" "PEBKAC and PICNIC"...

There are several reasons for that, but most of them have nothing to do with the security of the OS itself. Somewhere along the line, this idea has developed in the computer user culture that all unexpected activity is the result of malware. This is largely not helped by malware researchers who (for many reasons, some of them even good) will write articles about various things they find, but won't get into the details of exactly what to look for and what it does, where it comes from. They also tend not to distinguish well between exploit code and second-stage payloads, or to really make clear that automated tools throw out a lot of false positives.

I can't really blame users for this. A lot of documentation in security software is written for people who already know what the limitations are.

In this specific case, I don't see anything that resembles any malware I've ever known of, much less the modern for-profit malware. There would be no point in corrupting the MBR just make the mouse pointer act up.

---

### Post by ashwani17 on 2010-09-22
> **uRock said:**
> Go into the menus to System> Administration> System Testing. Let it do its thing and see what it says.

I can send u log file's..can u analyse them..its hard for me...as now with time proplem keep on persistently increasing...Now volume's goes up and down..some lapy goes to sleep mode on its own, yesterday i was watching movie this thing stopped it in bw arbitrarily. a hardware problem should show some definite pattern...u people need to understand the problem......

---

### Post by slooksterpsv on 2010-09-22
> **ashwani17 said:**
> I can send u log file's..can u analyse them..its hard for me...as now with time proplem keep on persistently increasing...Now volume's goes up and down..some lapy goes to sleep mode on its own, yesterday i was watching movie this thing stopped it in bw arbitrarily. a hardware problem should show some definite pattern...u people need to understand the problem......

Hardware is usually least from having a pattern, cause the errors, flaws, bugs, etc. are usually random - as your issue describes - malware, would be more consistent. It sounds like you may have a crossed connection somewhere on the hardware itself (faulty board is my guess). 

Where it happens in Windows and Linux proves it's not an issue with Viruses or Spyware, it proves its hardware related. Check your computer manufacturers website and see if they have a BIOS update specific to this issue. 

If not, you may need to contact your manufacturer and send in the computer to have them fix it where this is a hardware problem - again I think this is a faulty motherboard issue personally.

---

### Post by rookcifer on 2010-09-23
> **OpSecShellshock said:**
> Somewhere along the line, this idea has developed in the computer user culture that all unexpected activity is the result of malware. 

From 20+ years of Microsoft OS's perhaps?  Users, as you say, are trained to believe everything is malware.  In Windows, they are usually correct.

---

### Post by n~kf)}BW% on 2010-09-24
Nobody would make a virus that is cross platform, spreading deeply in your system, moving from OS to OS, and then make funny things with your keyboard/mouse :)

Calm down, we all think it's a hardware problem. Do you still have warranty? Perhaps you should search for similar problems on your type of computer. I'm sure someone has experienced same kind of a defect.

---

### Post by fly-by-night on 2010-09-25
Does the volume go up and down without any interaction from you?  In other words you did not touch the keyboard or moved the mouse.  

If it is during normal typing and mousing then it appear to be keyboard/mouse related issue as some suggested.  It was also suggested you try a different KB/mouse, but did you first double check the laptop keyboard for stuck buttons. **Open a text editor and press every button on the laptop keyboard and combinations to cover fn/alt/ctrl/shift/caps_lock/tab also**.  Check if the output is what's expected.

---

### Post by krupintupple on 2010-09-26
to the OP, I could've swore I had a virus too, until I realized that I had, on a dual-boot system, failed to properly configure a file for the graphic driver in both OS's. another time reseating the RAM fixed the problem.

if anything a virus is far more consistent than a hardware problem. i don't think anyone's attacking you, but you should at least do what this forum is requesting of you, if only to prove to them that it is a virus ;)

---

### Post by Aetixintro on 2010-09-30
Just to come clear on the denial of viruses and spyware in Ubuntu/Linux: here is the wikipedia article, [link]("http://en.wikipedia.org/wiki/Linux_malware") (ofcourse, you can probably be in denial of that too!!)

But I see the article as expert, and there are good advise therein! Use it well!

(I see the moron flat comments on Ubuntu/Linux to be very destructive and I believe we are hurt by being aloof with our 1-3% following (Ubuntu/Linux).)

---

### Post by CharlesA on 2010-09-30
> **Aetixintro said:**
> Just to come clear on the denial of viruses and spyware in Ubuntu/Linux: here is the wikipedia article, [link]("http://en.wikipedia.org/wiki/Linux_malware") (ofcourse, you can probably be in denial of that too!!)

But I see the article as expert, and there are good advise therein! Use it well!

(I see the moron flat comments on Ubuntu/Linux to be very destructive and I believe we are hurt by being aloof with our 1-3% following (Ubuntu/Linux).)

Yes there are viruses/malware for Linux, however they are mostly proof of concept.

There are none in the "wild," so there is nothing to worry about.

---

### Post by uRock on 2010-09-30
> **CharlesA said:**
> Yes there are viruses/malware for Linux, however they are mostly proof of concept.

There are none in the "wild," so there is nothing to worry about.
I agree. There are socially engineered malwares floating around, but those require people to install from sites, such as gnome-look and other sites that provide untrusted code. Those can't install themselves, so I am not worried about them.

---

### Post by Ahava591 on 2010-09-30
> **Aetixintro said:**
> Just to come clear on the denial of viruses and spyware in Ubuntu/Linux: here is the wikipedia article, [link]("http://en.wikipedia.org/wiki/Linux_malware") (ofcourse, you can probably be in denial of that too!!)

But I see the article as expert, and there are good advise therein! Use it well!

(I see the moron flat comments on Ubuntu/Linux to be very destructive and I believe we are hurt by being aloof with our 1-3% following (Ubuntu/Linux).)

I don't recall any denials of the existence of *nix malware, proof-of-concept or otherwise, in my time with Linux gurus.
-The thing is that it is largely proof-of-concept and what malware there is that is coded specifically for *nix tends to be targeted at servers. There is very little of it, (something on the order of 1,000 to 1,200 specific pieces of malware are the usual numbers tossed around,) and it is almost invariably dependent upon root access.   

I believe that in the past and for the foreseeable future the greatest threat to us comes from users not properly configuring their firewalls and not helping to maintain code and repositories, (either by actually auditing the code or reporting bugs, preferably both.)    



As for the OP, I too believe that your problem is one of hardware. It really does seem like faulty hardware, maybe the motherboard as has been suggested.  If you choose to believe that our response is a conspiracy to harm your computer, to harm you, or to cover up harm that has been done to you by somebody else, that is entirely up to you. 

I believe there is a hardware problem. I do not believe there is any evidence whatsoever of malware causing the behavior you have told us about.  Please continue to research your problem as you see fit; please let us know what you find so that in the future we can use your knowledge, I hope with you among us, to help others.

---

### Post by Supergoo on 2010-09-30
Hardware Problem as far as virus and Malware for Ubuntu I am sure nothing is 100%, I have heard about proof of concept but have not heard of any in the wild, even if there was if you use common sense and use the repos and stay away from untrusted code, keep the system updated , I think most people will be safe

---

### Post by Aetixintro on 2010-10-01
I mean, how much of the code is really trusted? I can just mention all the plugins for Firefox. You can also add **numerous** programs from any repository outside the standard Ubuntu-source repository. In addition to this comes all the programs you install from the internet. I think, undeniably, that viruses and Malware affect Ubuntu/Linux to the same degree that it does to the Windows (only that we are smaller). Of course, you have the trick with the Root which is really nice! And we have the transparency of good, simple firewall programs, controlling both outgoing and incoming. But still, how many of you have established user accounts on your systems? As with Windows, I think only the fewest have done this.

---

### Post by uRock on 2010-10-01
That is the good part about ubuntu. You do not have to make another account. An administrative account in Windows has the power to install/remove software without a password, but ubuntu doesn't allow that unless you have activated the root account and start signing in to it, which is asking for trouble.

I don't install any third party software in ubuntu unless I am confident in their code. Most of the malware I have seen in ubuntu gets installed via downloading and installing screen savers. I have turned down installing a few really nice programs because they weren't in the repos.

---

### Post by bodhi.zazen on 2010-10-01
> **Aetixintro said:**
> Just to come clear on the denial of viruses and spyware in Ubuntu/Linux: here is the wikipedia article, [link]("http://en.wikipedia.org/wiki/Linux_malware") (ofcourse, you can probably be in denial of that too!!)

But I see the article as expert, and there are good advise therein! Use it well!

(I see the moron flat comments on Ubuntu/Linux to be very destructive and I believe we are hurt by being aloof with our 1-3% following (Ubuntu/Linux).)

There are no denials, what I think you do not understand is how various OS handle these things.

With Linux, the code is patched, and your system is not vulnerable to known linux viruses.

With Windows, the code is closed and remains unpatched. You then rely on third party applications to identify and remove viruses after the fact. Since the code remains unpatched , small changes in the virus code = "new virus" although they often exploit the same unpatched code.

The point is, Linux security and Windows security have some things in common, and also some major differences.

Because Linux patches code, there is, IMO, no need for virus scanning. IMO you can not "protect" windows by running antiviurs in Linux, although if you wish to scan shared files go for it.

---

### Post by SeijiSensei on 2010-10-01
> **Aetixintro said:**
> I think, undeniably, that viruses and Malware affect Ubuntu/Linux to the same degree that it does to the Windows (only that we are smaller).

Do you have any proof for this other than your "undeniable" belief?  I've run Linux on Internet-facing servers and LAN desktops for fifteen years.  My only experience with malware was an exploit against Apache 1.1 for which a patch was available that I hadn't installed.  My servers get battered every day without incident.

There are many technical reasons why malware has little traction in the Linux world; it's not simply a function of market share.  The Wiki article you cite lists many of those reasons.  Perhaps you should read it again.

Remember, too, that the antivirus companies like Symantec have a financial incentive to make people worry about whether their computers might be vulnerable.  In any security situation, fear sells.  So I wouldn't trust those companies and their representatives to provide unbiased evaluations of Linux true vulnerabilities.  

I make sure that my Internet-facing devices have strong firewalls and up-to-date daemons.  Other than that none of my Linux computers have ever run any kind of anti-malware software.  I do run mail servers that scan incoming messages for viruses, but that's because I'm delivering those messages to networks full of Windows machines.

---

### Post by Ahava591 on 2010-10-01
> **Aetixintro said:**
> I mean, how much of the code is really trusted? I can just mention all the plugins for Firefox. You can also add **numerous** programs from any repository outside the standard Ubuntu-source repository. In addition to this comes all the programs you install from the internet. I think, undeniably, that viruses and Malware affect Ubuntu/Linux to the same degree that it does to the Windows (only that we are smaller). Of course, you have the trick with the Root which is really nice! And we have the transparency of good, simple firewall programs, controlling both outgoing and incoming. But still, how many of you have established user accounts on your systems? As with Windows, I think only the fewest have done this.

I trust the code. I also choose to use, with my own computer, only software that is well-maintained and well-respected with a history of performing, ahem, well. I trust the people who write and maintain this code, some of whom I know in real life, some who are only screen-names. I trust them because they trust me; this is a community. This is a society which has chosen to take hold of our computing. We have the choice, whether by reason of morality, finances or aesthetics to protect one another by protecting the software we use.

We can learn to help one another whenever and wherever it is possible for each individual member of this community. We can learn to be good, decent human beings. We can recognize that by strengthening others in this community, we will in turn be strengthened.

Choosing to download code from outside the official repos is your choice. It is a choice that must be maintained, and that I will fight in politics, in economics and in blood to have. I believe that you have the right to use the software you wish to use even if using that software exposes you to harm. I believe that you have the responsibility to understand what you use; and I believe that you have the responsibility to decide not to contribute to the problem of malicious software.


What I do not think you understand is that the problem you have mentioned, namely that of software which is not created, maintained and audited by such a group of people as ours', software such as that which can be found on the Internet, (e.g., outside trusted repositories,) is not a flaw in the Linux operating system.

*It is not the fault of Linux that **you** choose to use software which cannot be maintained and audited with open-source code, to carelessly use root access, to fail to maintain a reliable, thorough firewall. *

I have not had personal experience with any Linux distribution that gives the default user root access. You mention "user accounts."
--Is it not the case that the default user is usually not granted root access, you have to specifically, deliberately create an account for the root user?

---

### Post by Aetixintro on 2010-10-01
It should be clear that with it's little following, people choose to **_pay_** to get a better alternative than Ubuntu/Linux. At least this goes for the desktop/OS related. So why is this?

Why this is so is because people are tired of dealing with a lot of hassle that lies with the current Ubuntu/Linux systems. They pay for their Apple and Microsoft systems and they work right from the start, seldom with significant problems.

Clearly, there are problems and this is not only faulty code, but also malware and virus.

I once read Linux was the _MOST_ hacked system in the world. So I take this approach, rather than thinking I live in wonderland, in self-delusions, I'd like to press the issues and generate discussion on how to deal with it. Popularity is indeed an indicator of performance. Like in beauty contests, you are simply out if you choose that repulsive/ugly looking girl.

If the system is a hassle to many people, why would one bother to deny vulnerabilities to viruses and malware as well? There is no reason and we should prepare well for it to **NOT** happen to the extent that Ubuntu/Linux maintains its rise to stardom, making the world symmetric! Cheers! :)

---

### Post by rookcifer on 2010-10-01
> **Aetixintro said:**
> It should be clear that with it's little following, people choose to **_pay_** to get a better alternative than Ubuntu/Linux. At least this goes for the desktop/OS related. So why is this?

Why this is so is because people are tired of dealing with a lot of hassle that lies with the current Ubuntu/Linux systems. **They pay for their Apple and Microsoft systems and they work right from the start, seldom with significant problems.**

I stopped reading here and then went into a laughing fit.  Do you know how many people I know personally that ask me to come over and clean up their Windows machines?  Do you know how many viruses I remove?  And these are not warez or porn surfers either.  They are people who get infected even when running up to date AV software.  People who get infected by just surfing CNN.com or their favorite news sites.

On the other hand, do you know how many people I have ever seen on a Linux forum that have asked for help with "cleaning up" malware on their Linux box?  ZERO.

> I once read Linux was the _MOST_ hacked system in the world. 

I once read that the president is an alien from the planet Zoltar.  But, you know, I don't believe everything I read.  Consider the source.

> So I take this approach, rather than thinking I live in wonderland, in self-delusions, I'd like to press the issues and generate discussion on how to deal with it. 

That's fine.  Discussion is good and can lead to a better understanding for all of us.  But no one has ever said that Linux is immune from all threats.  Indeed, if you run a server, you need to keep tabs on your security, not get lazy with updates, use a firewall, chroot Apache, etc.  Servers do get cracked occasionally, but that doesn't translate over into desktop machines.  I have been around these forums for a while and never once have I seen a single account of a desktop machine getting cracked unless the user was really stupid (running VNC or SSH servers with no password and no firewall).  Moreover, I have never seen a SINGLE account of someone with malware.  Sure, there are lots of people who *think* they have malware (due to hardware failures, etc.) but I have never seen a single case that can be confirmed.  

Does this mean it is impossible?  No.  If you voluntarily install a malicious program or run a malicious script, it can "infect" the machine (as was the case with the now infamous gnome-look.org trojan).  The thing is, however, that Linux makes this very hard to do by accident.  The user practically has to infect himself.

> If the system is a hassle to many people, why would one bother to deny vulnerabilities to viruses and malware as well? There is no reason and we should prepare well for it to **NOT** happen to the extent that Ubuntu/Linux maintains its rise to stardom, making the world symmetric! Cheers! :)

In science, it is contingent upon the one making the claims to prove them.  It is not up to us to prove a negative.  So, I say, prove your assertion that Linux is just as malware prone as Windows.  Got any hard data?  Got any university studies?  I will even take anecdotes here.  Do you know anyone who runs Linux that has had a malware problem?  Just one person?

---

### Post by Ahava591 on 2010-10-02
:rolleyes:


Linux probably ***is*** the most hacked system in the world. BSD might come in second, maybe first.
Didn't the thing basically start out as a hack? An almost-clone of MINIX that was designed to behave above the hood like the the *nix variations that came before it with enhanced, original code under the hood?

All the hackers I know of either started out with *nix and moved to BSD or Linux, (or both,) if they're old enough, and the younger ones have worked with BSD and Linux pretty much forever.


Seems like a non-sequitur, this whole hacking subject.

Oh, ahem, I see. I'm embarrassed now. It seems that Aetixintro is unaware of what they are saying.

---

### Post by |{urse on 2010-10-02
Linux "the most hacked system"? Lol I don't know where you're getting your info. I'll give you one silly guess as to what OS really is hacked the most.

Here's a hint: It's the one that you HAVE to install antivirus on.

Try compiling sdbot or rbot and launching it on any *nix variant. Case closed.

---

### Post by uRock on 2010-10-02
Hacked= Made to work with my system and do what I want it to do, the way I want it done.

Cracked= "What just happened," my system has been pwned by someone and now I have to reinstall.

---

### Post by |{urse on 2010-10-02
Yeah according to mitnick the hackers are good guys and the crackers are the bad guys. I've never heard any real hackers call themselves crackers, for obvious reasons. In fact you never really hear it used on irc unless they are referring to cracking a password or removing security features from a closed source program.

---

### Post by uRock on 2010-10-02
Very true, but my phrasing is the only way I can imagine Linux being the "most hacked."

---

### Post by rookcifer on 2010-10-02
> **Ahava591 said:**
> :rolleyes:


Linux probably ***is*** the most hacked system in the world. BSD might come in second, maybe first.
Didn't the thing basically start out as a hack? An almost-clone of MINIX that was designed to behave above the hood like the the *nix variations that came before it with enhanced, original code under the hood?

It wasn't really a clone of Minix.  I don't know where that urban legend began but Minix and Linux are nothing alike in their design.  Minix is a microkernel, Linux is not.  I suppose this belief arose from the fact that Linus Torvalds used Minix to develop Linux on, but he didn't really copy much of the design of Minix itself. 

Keep in mind that this was the early 90's when BSD was undergoing a court case with AT&T about using their Unix code in BSD.  Therefore, BSD was practically dead at that time because they had to rewrite the whole thing and omit any AT&T code.  Also, Minix was restricted in its licensing, so Torvalds set out and created his own Unix-like OS.

---

### Post by |{urse on 2010-10-02
Oh yes. Now i get why you said that lol.
By the way this fix would more than likely cure the OP's "virus".

[http://ubuntuforums.org/showthread.php?t=1164008](http://ubuntuforums.org/showthread.php?t=1164008)

That fix will need to be modified for grub2. I believe that's been covered in this thread.

[http://ubuntuforums.org/showthread.php?t=1326115](http://ubuntuforums.org/showthread.php?t=1326115)

---

### Post by Ahava591 on 2010-10-02
> **rookcifer said:**
> It wasn't really a clone of Minix.  I don't know where that urban legend began but Minix and Linux are nothing alike in their design.  Minix is a microkernel, Linux is not.  I suppose this belief arose from the fact that Linus Torvalds used Minix to develop Linux on, but he didn't really copy much of the design of Minix itself. 

Keep in mind that this was the early 90's when BSD was undergoing a court case with AT&T about using their Unix code in BSD.  Therefore, BSD was practically dead at that time because they had to rewrite the whole thing and omit any AT&T code.  Also, Minix was restricted in its licensing, so Torvalds set out and created his own Unix-like OS.

I said "almost-clone," because I couldn't think of a better way to put it. I didn't state they were the same design; in fact, I specifically wrote that under the hood Linux was original with respect to MINIX and Unix. However, the fact remains that Linux uses the same concepts from Unix in particular. "Everything is a file," the directory system, all of that.  Even the command line shells have been imported from the *nix variants that came before Linux. Bash existed in Unix, for example.  I probably could have put it better than I did, but I stand by my arguments, the concepts.   As for the apparent "hacking," problem, I was ridiculing the named poster for misusing the term "hacking." As for actual hacking, I also stand by my argument that Linux and BSD are still huge centers of it, probably the communities with the largest number of hackers. If you feel otherwise, please explain your position to me.

---

### Post by Ahava591 on 2010-10-02
> **|{urse said:**
> Linux &quot;the most hacked system&quot;? Lol I don't know where you're getting your info. I'll give you one silly guess as to what OS really is hacked the most.

Here's a hint: It's the one that you HAVE to install antivirus on.

Try compiling sdbot or rbot and launching it on any *nix variant. Case closed.

 See my post above this one explaining the terminology in question.

---

### Post by |{urse on 2010-10-02
Oh no, I understood what you meant 

You said linux is the most hacked system. <-- zero merit to this statement.
THEN you assert that it is the system that hackers (bad ones) use. <-- completely changed the statement, not just the terminology.

Aaaand that's why i can't stop laughing at your absurd assertions.

---

### Post by Ahava591 on 2010-10-02
> **|{urse said:**
> Oh no, I understood what you meant 

You said linux is the most hacked system. <-- zero merit to this statement.
THEN you assert that it is the system that hackers (bad ones) use. <-- completely changed the statement, not just the terminology.

Aaaand that's why i can't stop laughing at your absurd assertions.

Try grasping the English language before you attempt to communicate in it. 

No. I have never stated that "bad ones," use anything. I never said this in any way, shape or form. I can't stop laughing at how stupid you appear to be. I never changed any statement or any terminology.



Malware, malicious commands, etc. are all CRACKING. NOT HACKING. THEY HAVE NEVER BEEN HACKING. THEY WILL NEVER BE CONSIDERED HACKING. 


And I quote myself:
*As for the apparent "hacking," problem, I was ridiculing the named  poster for misusing the term "hacking." As for actual hacking, I also  stand by my argument that Linux and BSD are still huge centers of it,  probably the communities with the largest number of hackers. If you feel  otherwise, please explain your position to me.*


The poster in question, Aetixintro, used the term "hacking," to describe CRACKING, and, confusing the terms CRACKING and HACKING described Linux as being the most "hacked," system. This person had completely screwed up their terminology while simultaneously using said terminology to state a truth about Linux.
They believe that Linux is "the most cracked OS," which it is not, but instead of saying that Linux is "cracked," (which it is not,) they used the term "hacked."

Get it? Are you grasping the fundamental concepts of the English language yet?

I then made fun of Aetixintro by stating the obvious truth that Linux IS IN FACT AN OFTEN HACKED SYSTEM. HACKERS USE IT. HACKERS MODIFY IT TO SUIT THEIR NEEDS AND TO ENTERTAIN THEMSELVES.

---

### Post by lisati on 2010-10-02
I blame the media for some of the confusion between the terms "hacking" and "cracking"........ :D 

And how much of what is attributed to the bad guys is better attributable to PEBKAC errors?

---

### Post by nlsthzn on 2010-10-02
I find it fascinating how many people come to a forum (any forum) seeking assistance with a problem only to already have there minds made up what the problem and subsequent solution is and then refuting any and all assistance/comments/solutions that doesn't fit there paradigm...

Absurdity!

---

### Post by |{urse on 2010-10-02
Personally I just think it's great that both Ahava591 and myself can't stop laughing. 

I shall endeavor to grasp the English language as soon as I finish learning my 8th programming language. Perhaps, while I'm meeting you halfway you could stop using the term "hack" in a good way. No-one calls users "hackers" in a positive way anymore. By the way, 1997 called.. It wants it's lame jargon that no-one uses anymore back.

---

### Post by Ahava591 on 2010-10-02
> **|{urse said:**
> Personally I just think it's great that both Ahava591 and myself can't stop laughing. 

I shall endeavor to grasp the English language as soon as I finish learning my 8th programming language. Perhaps, while I'm meeting you halfway you could stop using the term "hack" in a good way. No-one calls users "hackers" in a positive way anymore. By the way, 1997 called.. It wants it's lame jargon that no-one uses anymore back.

 Good for you with your multitude of languages. 
Keeping in mind that I have never bragged as you have just done about programming, I must wonder just how well you know any of them. 
-Remember, too, when you read this and feel the inclination to tell me about all of your years of experience and how many companies you have worked for and all the software you have contributed to the community before, likely, asking me "just what languages do you know?" that I'm not the one bragging about it and jumping on the intellectual high horse with lies and misunderstanding of what somebody has said, stumbling over the most basic sarcasm.


Why should I quit using the term, "hack," "in a good way,"? You may not call people hackers as a compliment anymore; do not speak for me or anybody else. 

Just because you are too trendy to deign to use "lame jargon," does not make you an authority on what is a valid statement. 
Scurry back to your IT department now with your seven-going-on-eight programming languages and tune into CNN every time they report every bored fourteen year old or career criminal or Chinese attack on their flavor of the month target as "hacking."


P.S.
On second thought, do dress me down with your very great knowledge so that, in humor, as was my original reply to Aetixintro which first seems to have started our little pissing contest, I may acknowledge you as a true hacker.

---

### Post by |{urse on 2010-10-02
You really spent a long time on that post. I can tell from the ridiculous amount of text. Unfortunately I wont be reading it. All the best!

---

### Post by Ahava591 on 2010-10-02
:popcorn:

---

### Post by |{urse on 2010-10-02
Kind of rude of me to leave things like that. I really am still quite confused though. Let's say I wrote a little html parser + a cgi script with socket::inet that would guarantee I would always have the last word on ubuntu forums, would that be considered cracking or hacking?

---

### Post by cariboo on 2010-10-02
This thread seems to have degenerated into name calling. There is no need to Keep it open. Closed.

---

