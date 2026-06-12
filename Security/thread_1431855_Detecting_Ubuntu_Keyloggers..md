---
title: "Detecting Ubuntu Keyloggers."
date: 2010-03-17
forum: Security
---

### Post by zozza on 2010-03-17
One of the attractions for me of Ubuntu was its lack of susceptibility to virus and malware. attacks.  I was interested to learn that keyloggers are available for Ubuntu like logkeys.  

When I downloaded it and tested it with Clam AV it was not detected.  

I wonder why this is or if there is a "better" AV / anti-spyware / anti-malware tool out there?

---

### Post by Grenage on 2010-03-17
I guess it depends on what the software makers consider spyware.  While I don't write software, I would guess that a basic key logger you install yourself is not classed as a malicious program.

After installing, does it work when another user is logged in?
If so, did you have to install it using root privileges?

---

### Post by bodhi.zazen on 2010-03-17
> **zozza said:**
> One of the attractions for me of Ubuntu was its lack of susceptibility to virus and malware. attacks.  I was interested to learn that keyloggers are available for Ubuntu like logkeys.  

When I downloaded it and tested it with Clam AV it was not detected.  

I wonder why this is or if there is a "better" AV / anti-spyware / anti-malware tool out there?

There are no known key loggers "in the wild"

You would need to download, install, and configure one yourself.

---

### Post by gnupipe on 2010-03-17
> **bodhi.zazen said:**
> there are no known key loggers "in the wild"

you would need to download, install, and configure one yourself.

+1

---

### Post by OpSecShellshock on 2010-03-17
Keyloggers in and of themselves are not necessarily malware. It's only when they can be automatically and silently installed, run without the system owner's knowledge, and then send the logged data offsite that they become malicious. Beyond that, in order for it to have any value your computer would either have to be directly accessible from the open web (which doesn't require a keylogger in most cases) or it would have to capture login data for sites you access through the browser (which is easier to get by phishing).

A keylogger is basically just not going to get installed automatically, and it wouldn't be able to set itself up to run when your system starts up anyway. Just be careful where you install software from.

---

### Post by HermanAB on 2010-03-18
It is usually easy to detect malware.  Run tcpdump and look at the data on the network interface - there should not be any.  Now type something on the keyboard - there still should not be any.

---

### Post by zozza on 2010-03-19
> A keylogger is basically just not going to get installed automatically, and it wouldn't be able to set itself up to run when your system starts up anyway. Just be careful where you install software from.

Forgive my ignorance but I do not understand this.  There are plenty of programs that run on startup.  Why not a keylogger? 

Perhaps I am thinking with an XP mindset.  I suppose that to install the keylogger I (or anyone) would need to run sudo and obviously I am only going to do that if I trust the software. 

But what happens if:

a) someone send me the keylogger program and tells me it's something else (not me obviously, but someone naive) so it is installed?

b) I am using a cybercafe and the keylogger is installed?

---

### Post by rookcifer on 2010-03-19
> **zozza said:**
> 

a) someone send me the keylogger program and tells me it's something else (not me obviously, but someone naive) so it is installed?

Then you're screwed.

> b) I am using a cybercafe and the keylogger is installed?

Physical access = pwnage.  So, if you are using someone else's machine, you should *never* assume you are secure in anything you do.

Bottom line: don't worry about keyloggers.  They require root access to be installed, so as long as you never provide root access to an untrusted program, you will never have to worry about a keylogger.

---

### Post by bodhi.zazen on 2010-03-19
I agree with rookcifer.

This is not Windows and one can not have key loggers installed as easily.

You should be worried about how a key logger was installed in the first place as this implies either social engineering or some type of a crack, so this thread covers what you need to know about security.

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

Second there are several types of key loggers, some are physical, and thus detected by physical inspection of the box.

If you system has been cracked you are in trouble, and the only things that may help would be apparmor or selinux.

If you are on an untursted network or computer there is not really much you can do. You could tunnel your traffic over VPA or ssh, etc, but again you would be better off assuming you are being watched on such a system or (public) network.

---

### Post by Ijan on 2010-03-19
I think zozza's question is legit and relevant.

AFAIK a good part of Windows anti-malware products detect and inform the user even of professionally and possibly legally installed monitoring software to give just one example.

As there are multiple examples of educational or professional institutions illegally monitoring private activities of students or employees (and even monitoring non private activities is subject to legislation in most countries thankfully) and the pure knowledge of being monitored is legal on the other hand in most countries I think the capability to detect keyloggers is quite a sensible demand.

As it is not very realistic to expect any privacy on cyber-café-boxes you may expect *some* privacy using e. g. a computer you keep in shared student's dorm and a malware scanner is a - while very far from perfect - sensible tool to acquire such as Linux boxes are not harder to exploit than Windows ones once you have physical access.

---

### Post by bodhi.zazen on 2010-03-19
> **Ijan said:**
> I think zozza's question is legit and relevant.

No body indicated the question illegitimate, and I appreciate your concerns.

But if you are on an untrusted network that in itself answers the question.

There is a huge difference between government, commercial (employers), public/shared, and private boxes / networks.

If you do not own the hardware or control the network I would assume it is insecure and that you are being monitored, especially when private or sensitive information is concerned. In that event, most people advise you use ssh or VPN, but unless you have inspected the (external and internal) hardware you can not know if there is a key logger on the system, let alone the network. An untrusted network could easily have a packet sniffer an many types.

So although the concern is valid, it is going to be difficult, at best, to determine if there is a key logger or network monitoring present. It comes down to who is better at such things, you or the network administrator, as well as how paranoid are you, and how sensitive is the data.

---

### Post by Ijan on 2010-03-19
Thanks for your answer bodhi.zazen!

As I got it, zozza's original question was if there was a malware scanner accessible for Linux that is able to detect keyloggers like logkeys.

Some answers were:
> There are no known key loggers "in the wild" [...]
> A keylogger is basically just not going to get installed automatically, and it wouldn't be able to set itself up to run
When zozza voices the fear to be social eningeered into installing a keylogger some answers are:
> This is not Windows and one can not have key loggers installed as easily.
> Then you're screwed.[...but then...]Bottom line: don't worry about keyloggers.
This does not sound like direct answers to me but more as if zozza's question was considered irrelevant somehow. I didn't find the social engineering proposition very imaginary though and being interested in the original answer and the possible consequences too, I tried to add the case of a dorm room mate with a boot-disk or a local admin violating legal limits to the possible scenarios.

I also can't see how a discussion of the security of network traffic would make the original question irrelevant as malevolent colleges, classmates or admins most certainly would not install keyloggers over remote network exploits. You can be pretty safe in public networks otherwise if you use trustable software and encrypted protocols - as long as nobody installed a keylogger on your system.

When you say:
> So although the concern is valid, it is going to be difficult, at best, to determine if there is a key logger or network monitoring present. It comes down to who is better at such things, you or the network administrator, as well as how paranoid are you, and how sensitive is the data.
I would agree but add that anti-malware-scanners - though far from perfect - are IMHO a proven real-life-approach to such incertainities which leads me back to zozza's original question. 

Should maybe somebody have taken the time to add the small bunch of Linux-keyloggers to the clamAV thread database or is it because of other reasons more sensible as it is? What are the alternatives or are there any at all if you are using Linux?

---

### Post by Grenage on 2010-03-19
Out of curiosity (I have never tried), do windows anti-malware/spyware/virus scanners actually pick up basic keyloggers?  If I were to write a WSH script, for example, would it really flag it as a threat?

---

### Post by Ijan on 2010-03-19
Interesting question. The macro recorders or hot-key-listeners I've used didn't trigger anti-malware-soft, known keyloggers did and as soon as a keyboard-listening script was tied to IRC or something with remote access it did. That doesn't make it too clear still if the keylogging was a criterion. Additionally I don't like bloat so doing only on-demand scans I can't say anything regarding behavioural analysis.

If you get an answer at some other place like a malware related forum or such feel free to post it here as well.

---

### Post by OpSecShellshock on 2010-03-19
> **Grenage said:**
> Out of curiosity (I have never tried), do windows anti-malware/spyware/virus scanners actually pick up basic keyloggers?  If I were to write a WSH script, for example, would it really flag it as a threat?

Sometimes they are able to find the ones they know about. If you wrote one up and got somebody to install it, AV vendors would likely only learn about it from user-submitted samples. Then they'd add it to a signature update. So it's just like anything else: if they know what they're looking for, then they might find it, if it's there.

---

### Post by bodhi.zazen on 2010-03-19
> **Ijan said:**
> This does not sound like direct answers to me but more as if zozza's question was considered irrelevant somehow. I didn't find the social engineering proposition very imaginary though and being interested in the original answer and the possible consequences too, I tried to add the case of a dorm room mate with a boot-disk or a local admin violating legal limits to the possible scenarios.

I think the answers are very direct.

This is not windows, key loggers do not "just appear" in Linux, they come from somewhere.

The direct answer to the question is that key loggers are almost unheard of in Linux so much so that I am not aware of any scanner.

In addition, there are many types of key loggers. I am not sure all of them can be detected in any OS.

FYI, the discussion of physical access and network security was directly asked by the OP:

> **zozza said:**
> But what happens if:

a) someone send me the keylogger program and tells me it's something else (not me obviously, but someone naive) so it is installed?

b) I am using a cybercafe and the keylogger is installed?

Although I am sometimes guilty of the same thing (not reading the entire thread), I am not sure if you have read this thread.

---

### Post by Ijan on 2010-03-19
@Grenage/OpSecShellshock: I superficially checked a few forum entries at sourceforge et. al. and seemingly you get quite a fair rate of heuristic-based hits at multi-engine tests if you code something keylogging in a scripting language.
[edit]
Ok - correction, I did a few scans myself at virustotal and there are actually little to no hits if you take less popular loggers from sourceforge.
[/edit]

---

### Post by Grenage on 2010-03-19
Thank you for the input; I suspected it might be a case of known loggers being matched.  Windows and most programs running are logging key strokes (feel free to correct me), so I imagine it would be a very hard task to spot one and say "that's malicious".

---

### Post by Ijan on 2010-03-19
Yep seems so, note I edited to sort of the opposite above after doing a few scans myself...

There's a lot of know how at anti-/malware forums about getting stuff through scanners, they should know if any sorts of keyboard access are considered suspicious.

---

### Post by Ijan on 2010-03-19
Hi bodhi.zazen,
sorry for the delayed answer. Though I have indeed read the whole thread I'm sorry if I may have misread parts of it.

I understood that a user was concerned about keyloggers and was getting the answer that keyloggers are no actual thread under Linux.

I would agree to that as far as remotely exploitable security vulnerabilities are concerned and as far as you take into account the relatively low number of Linux desktop systems and consequently the even lower if not zero popularity of Linux-malware targeting desktop users.   

I may have misread some parts of the answers that sounded to me as if such concerns were principally pointless just because "this is not Windows".

Compromising a system via social engineering or a live CD does not seem any harder to me on a Linux system than on a Windows system. Am I wrong about that?

Surely given the relatively low percentage of computer users familiar with Linux the statistical chance to be attacked might be negligible so I admit my further inquiry may appear a bit academic.

However I personally hope that having a low market share will not always be the easy excuse for Linux and apart from that I would have liked to know how to address the concerns voiced by zozza and seconded by me for purely technical interest.

What I had hoped for was comments if a "better" malware scanner that could be upgraded to detecting keyloggers as supposed by zozza was regarded potentially doable or if other approaches would be considered more appropriate beeing aware that attacks involving physical access and social engineering are a difficult matter. Only to express my further interest I brought up my original question again and not to dispute anything mentioned above in any way.

Sorry for obviously beeing unclear!

---

### Post by OpSecShellshock on 2010-03-20
Yeah, sorry if I came across as dismissive. I tend to get the impression that people are most concerned about remote, automated installations of malicious code. The risk of that is somewhat lower on Linux desktop systems. I say "somewhat" because most remote code execution is going to take place within the browser. When that happens, it's going to be just as successful on a Linux system as it is on Windows. The difference is in what happens afterwards (as in, where it can go from there on the rest of the disk).

The other thing is, people have this idea that the most successful Windows malware isn't itself mostly installed by users following social engineering. Fact is, though, that that's exactly how the most destructive ones get on there. Malicious web scripts play a part in the social engineering aspect (think of the fraudulent AV messages that people are constantly seeing), but the really destructive payloads come about when users download and install them.

---

### Post by HermanAB on 2010-03-20
"Out of curiosity (I have never tried), do windows anti-malware/spyware/virus scanners actually pick up basic keyloggers? If I were to write a WSH script, for example, would it really flag it as a threat?"

My little sniffers used to recover ISP passwords when I have to fix someone's email are regularly flagged as malware by McAffee and the like.  However, Cygwin tcpdump and ngrep always get through unmolested.

---

### Post by rookcifer on 2010-03-20
> **Ijan said:**
> 
As it is not very realistic to expect any privacy on cyber-café-boxes you may expect *some* privacy using e. g. a computer you keep in shared student's dorm and a malware scanner is a - while very far from perfect - sensible tool to acquire such as Linux boxes are not harder to exploit than Windows ones once you have physical access.

You see, as I said before, physical access = pwnage.  If your roommate can boot into a liveCD, he has root to your box.  And if he has root, all the anti-malware scanners in the world will not matter because he can merely tamper with the kernel so that his keylogger is hidden, or he can tamper with the malware scanner itself.

---

### Post by merck on 2010-03-21
Hey guys!
This is pretty much a discussion my roommate and I have been having over the past few days. We were curious how a keylogger could be detected and (more importantly) removed form an ubuntu machine. This is more of an academic discussion so we are assuming that there is a keylogger on the machine. Both of us have some experience with linux, but neither of us are guru. Any help or advice would be great!
Oh, and reformatting the hard drive is cheating.

---

### Post by Ijan on 2010-03-21
^
Hm, as pointed out above a software could have all sorts of legit reasons for listening to the keyboard. Without knowing too much about the system architecture used in Linux to access keyboard input this might however come in the way of any method trying to recognize any generic patterns.

One could still try to list all processes accessing keyboard input and try to sort out by hand if there are any unwanted among them.

Another approach would be research into which of the known keyloggers seem to support illegitimate uses by advertising stealthiness and such and scan for them.

Both would of course - to argree with rookcifer there - be effective only in the case of the most unsophisticated sorts of keyloggers that don't bring any of the numerous disguise techniques like e. g. the manipulation of system files.

---

### Post by OpSecShellshock on 2010-03-21
I'd start by looking over everything that the user installed from somewhere other than the official repositories. I'd be inclined to pay special attention to anything that was installed by a means other than aptitude, synaptic, or dpkg (so mostly something that was compiled just prior to installation, probably--something done using make install). Basically, I think it would probably have to come in the form of an application where there was a tutorial for long-hand manual installation that was geared toward people who don't usually do that. So I'd just suggest removing all of those right away.

My reasoning for that is that if it sits entirely in user space it either won't work or will be too obvious. Plus, the user level doesn't own the keyboard or the processes by which input is accepted. So it would have to be at a higher level of permissions, probably.

I suppose you could also sniff traffic. Odds are it would be sent over https, but even if you can't read the packets you can see something happening. All you have to do is close all network-accessing applications/processes that you know about, and then check on what's still connecting. It might take a while depending on how it's been set to run, but as long as you're willing to wait, capture the traffic, and look for process names you don't recognize, then it should eventually get spotted. If you're behind a hardware router, just shut off all outgoing connections from there. That way the computer will still try to connect, but won't succeed. Then check for errors about not being able to find the destination. That should yield both the process name and the host it's trying to contact.

---

### Post by phibxr on 2010-03-21
> **rookcifer said:**
> You see, as I said before, physical access = pwnage.  If your roommate can boot into a liveCD, he has root to your box.  And if he has root, all the anti-malware scanners in the world will not matter because he can merely tamper with the kernel so that his keylogger is hidden, or he can tamper with the malware scanner itself.

Actually, if your roommate has physical access to your computer, he might as well install a hardware keylogger and be done with it.

No anti-spyware software is ever going to be able to pipe into the wirings of your keyboard and ask if something has read the signals along the way to your computer until "trusted computing" is a real fact - and by then we're most likely screwed either way. :)

---

