---
title: "My 3 week battle with spyware / trojan"
date: 2008-02-08
forum: Windows
---

### Post by Bungo Pony on 2008-02-08
I'm getting to the point where I'm ready to completely ditch Windows until April when Hardy is released, and completely re-do my OS installations. I'm slowly doing a complete migration to Linux, but I'm not entirely ready yet.

For the last 3 weeks, I've been battling a piece of spyware, or a trojan. I don't know which. I've run multiple scanners and removal tools. One will say I have Virtumonde, one will say I have Zlob, and some will say I have both. The only thing these scanners are pointing me to are registry entries and .dll files, which I've removed manually numerous times. The removal tools don't work. I'm convinced there's an .exe somewhere on my system, and nothing is finding it.

What this thing does: it gives me fake error messages galore, slows down my system, and creates two fake icons on my desktop called "Windows Update" and "Help & Support". The icons are shortcuts to some website (I can't remember where, I'm currently at work).

Has anybody dealt with this piece of crap before?

---

### Post by slipperhead on 2008-02-08
i had something similar a while ago and i have to say i gave up trying to clean it and just reformatted.

not very helpful i know :(

---

### Post by bossa on 2008-02-08
Sorry to hear of your problems. Maybe these will help

[http://www.bleepingcomputer.com/forums/topic18610.html]("http://www.bleepingcomputer.com/forums/topic18610.html")

[http://www.lavasoft.com/support/securitycenter/virtumonde_remover.php](http://www.lavasoft.com/support/securitycenter/virtumonde_remover.php)

[http://www.auditmypc.com/virtumonde-remove.asp](http://www.auditmypc.com/virtumonde-remove.asp)


Switch to Linux soon :)

---

### Post by Bungo Pony on 2008-02-08
I've tried all three of those :(

My Linux switch is progressively getting better, and I'm staying booted into Ubuntu more. I'm stumped as to how I got the Windows infection since I'm in Ubuntu 75% of the time. I'll be putting even more effort into a complete switch after Hardy, since I'll be keeping it for the two years before the next LTS version comes out.

I'm running some of my most important Windows software in Wine, and I have yet to try running more.

---

### Post by tadcan on 2008-02-08
[www.spybot.com](www.spybot.com) might help

I had the same problem on my mums PC. I Installed [http://www.kaspersky.com/](http://www.kaspersky.com/) which did the job. It is heavy on system resources. If that doesn't work then I'd save my files and do a clean install.

---

### Post by dca on 2008-02-08
You can d/l & install a free trial of Prevx... 
 
[http://www.prevx.com/](http://www.prevx.com/)
 
It's worked well in the past for companies I consult for that either have corp accounts w/ McAfee or Symantec.  Sometimes something new or big hits and it takes too long for them to find a fix...  This Prevx always seems on the ball and fixes it before the big guys.
 
I liked the option about getting rid of Windows better...

---

### Post by Bungo Pony on 2008-02-08
> **dca said:**
> 
I liked the option about getting rid of Windows better...

Trust me, I do too, but I don't have the time to learn everything at once. Everything is being learned a little bit at a time, and the results are showing :)

I'll give spybot and prevx a shot. I think spybot helped with the last stupid Trojan I had.

I've re-installed Windows about 3 or 4 times on this machine in the last year because of it getting buggered up with garbage, and I've re-installed Ubuntu only when a new version came out. Says something, doesn't it? ;)

---

### Post by aysiu on 2008-02-08
In my experience, it's nigh-impossible to get rid of spyware in Windows without doing a complete reinstallation. That's what I would do. We're still two months away from Hardy's release.

So reinstall Windows and *do not* run as administrator. Create a limited user account in Windows and always run as the limited user. If you need to install something, use the *Run as* context menu to run the setup.exe as the administrative account.

---

### Post by kevstar31 on 2008-02-08
Have you tried [hitman pro]("http://www.hitmanpro.nl/hitmanpro/"), it uses multiple anti-spyware products to clean your system.
if you still have trobles with spyware you can use [hijackthis]("http://http://www.spywareinfo.com/~merijn/programs.php") to allow us to have an idea of what programs are not being detected.

---

### Post by randy78 on 2008-02-09
A friend had a bad infestation a couple of months back so here's what I did.

I downloaded a free tool called Autoruns (just Google it)
I fired up Autoruns, noticed the locations where the viruses were executing from  since they were stealthing themselves by hiding (even with Show Hidden Files on), and then I booted up a Gutsy Live CD and took care of business.

A HijackThis log would help immensely, and as Aysiu said, the best thing for you to do would be to completely re-install your OS (Hopefully with Ubuntu).

You don't know if they planted a Rootkit into your MBR or if they are using one of the new stealth Keyloggers that go virtually undetected.

You absolutely MUST be more pro-active in your defenses and maybe this experience will show you how rotten Windoze really is.

Good Luck, you're going to need it ;)

---

### Post by smoker on 2008-02-09
why waste any more time trying to clean windows!

install ubuntu, and if you really need windows, install it on virtualbox, that way you can take a 'snapshot', use whatever window apps you need, and if it gets infected again, use the snapshot to take it back to a clean system.

best of luck

---

### Post by seanc7 on 2008-02-09
I suspect there is a rootkit at work hiding some of the parts of the virus/spyware.

Try using one of the rootkit scanners:

[http://www.techsupportalert.com/best_46_free_utilities.htm#7](http://www.techsupportalert.com/best_46_free_utilities.htm#7)

But with rootkits, the only sure way to eliminate one is to do a complete format using a different boot media (ie: like the old DOS boot diskettes were, but now any Linux Live CD distro would do.)

First backup your data under Windows. Then boot with the Live CD and do a format of the hard drive. I don't know the terminal commands, you'd have to Google them.

Hopefully this helps.

---

### Post by ikt on 2008-02-10
> **aysiu said:**
> In my experience, it's nigh-impossible to get rid of spyware in Windows without doing a complete reinstallation.

In my experience it's extremely easy to remove a majority of spyware in windows without doing a complete reinstallation.

It's even easier to just plain not get spyware if people switch on their brains while using the internets as well.

---

### Post by rune0077 on 2008-02-10
Have to agree with above poster. Keeping Windows clean is not that big of a deal, if you're careful and use the right software. *Always* use a spyware detector. Spybot is free and pretty decent, spysweeper costs money but is better (according to pcworld, it's the one you want). Better yet, use them both. And *always* use a virus detector. It's resource demanding to run two spyware detectors and a virus scanner, I know, but it's how you have to do it. 

Windows is only insecure if you leave your door right open and invite every stranger who comes along inside.

---

### Post by aysiu on 2008-02-10
> **ikt said:**
> In my experience it's extremely easy to remove a majority of spyware in windows without doing a complete reinstallation.

It's even easier to just plain not get spyware if people switch on their brains while using the internets as well. Why don't you insult the OP a little more? Did you read the subject title? *My **3-week** battle with spyware / trojan*. So you're implying the OP is an idiot for not being able to remove the spyware easily (in less than 3 weeks) and an idiot for getting it in the first place. Nice. Since I can't be objective in the matter (you've almost indirectly insulted me too), I'll leave it up to another moderator to decide whether your insult was indirect enough to not warrant an infraction. Your wording may have somehow saved you.

> **rune0077 said:**
> Have to agree with above poster. Keeping Windows clean is not that big of a deal, if you're careful and use the right software. *Always* use a spyware detector. Spybot is free and pretty decent, spysweeper costs money but is better (according to pcworld, it's the one you want). Better yet, use them both. And *always* use a virus detector. It's resource demanding to run two spyware detectors and a virus scanner, I know, but it's how you have to do it.  And, as I've said before, in my experience, running those things does essentially nothing. Everyone I know who's gotten infected with some type of malware has been running all those services.

> Windows is only insecure if you leave your door right open and invite every stranger who comes along inside. This, however, I can fully agree with. The people who tend to get malware also tend to be those who will click on just about anything.... *and* run Windows as administrator all the time.

---

### Post by rune0077 on 2008-02-10
> **aysiu said:**
> 
 And, as I've said before, in my experience, running those things does essentially nothing. Everyone I know who's gotten infected with some type of malware has been running all those services.


Maybe it's been a long time since you've tried them. I remember the first time I tried out spybot, the thing didn't seem to do squad. But have to say, these buggers are getting better all the time (so is the malware, I know). Spysweeper caught a lot of stupid stuff for me when I was running Vista, and what got through got necked up by either Spybot or Windows Defende (yeah, I had three spyware detectors, I'm paranoid). Spybot also has the enormously useful feature of actually alerting you *every single time* a program wants to make changes to your registry, together with the option to not allow those changes. That one's a godsend for any Windows user, since it prevents a lot of weird stuff from happening, and not just when it comes to spyware.

---

### Post by aysiu on 2008-02-10
> **rune0077 said:**
> Maybe it's been a long time since you've tried them. Not really. I'm talking about co-workers and friends who *still* run them now and *still* get malware now.

---

### Post by Bungo Pony on 2008-02-10
> if you still have trobles with spyware you can use hijackthis to allow us to have an idea of what programs are not being detected.

Believe it or not, whatever has infected my machine has prevented HJT from running.

But it seems that I've somewhat neutralized it a bit. There's still some problems, but it's not nagging me with fake errors anymore. It's a good thing I do all my transactions that need security in Linux. I know not to trust Windows.

> why waste any more time trying to clean windows!
install ubuntu, 

I've been running Ubuntu since last March. Transition has been a bit slow, but this whole spyware/trojan issue has really sped up my adaptation of Ubuntu. The biggest problem I've had so far was getting a decent Wav -> MP3 converter. I got EAC running in Wine with an external LAME encoder working well. Oh yeah, and please don't tell me to try xxxx for an MP3 encoder, because I've tried pretty much all of them. The only one that actually worked for me was SoundConverter, but it lacks the option to customize the bitrates to my liking.

> First backup your data under Windows. Then boot with the Live CD and do a format of the hard drive. 

I use Gparted for all my hard drive needs :)

> In my experience it's extremely easy to remove a majority of spyware in windows without doing a complete reinstallation.

That has also been my experience.... until now.

I've helped people remove malware from their PCs over the phone. I'm not afraid of going into the registry. I usually use anoter OS to delete infections, rename files, or overwrite the files with crap. Ubuntu has been extremely helpful in this area.

Again, things are better (for now), but there's still a few problems to work out. I'm really not up for a Windows reinstallation right now, but it's been motivation to adapt to Ubuntu even moreso.

---

### Post by ikt on 2008-02-10
> **aysiu said:**
> So you're implying the OP is an idiot for not being able to remove the spyware easily (in less than 3 weeks) and an idiot for getting it in the first place. Nice.

[http://www.google.com.au/search?q=define%3A+idiot&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com.au/search?q=define%3A+idiot&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

Definitions of  idiot on the Web:

    * a person of subnormal intelligence 

I'm not implying anything like that at all, and I have no idea how you even got that idea. 

> The people who tend to get malware also tend to be those who will click on just about anything.... and run Windows as administrator all the time.

What you just said, is all that I'm saying.

The most effective form of anti-virus and anti-spyware is knowledge. And to me if it takes the OP 3 weeks to remove some basic malware + and the fact he got it in the first place, suggests a little more knowledge may be the thing that helps him/her from ever getting malware again.

I can suggest some stuff right now:

- Use Firefox or Opera instead of Internet Explorer:

[http://en.www.mozilla.com/en/firefox/?from=getfirefox](http://en.www.mozilla.com/en/firefox/?from=getfirefox)
[http://www.opera.com/](http://www.opera.com/)

- When installing programs go over all the options carefully, and don't click next and hope for the best, for it is a fact that programs like Flash and Yahoo Messenger will try and install extra items which you didn't originally intend to install.

- [http://www.f-secure.com/weblog/](http://www.f-secure.com/weblog/) - is a great blog with lots of information on new threats, good to know what our common enemy is up to.

I hope the OP can fix his issue soon :)

Just quickly here are the pages with all the information on the malware:

Virtumonde:
[http://www.symantec.com/security_response/writeup.jsp?docid=2003-120914-4108-99&tabid=2](http://www.symantec.com/security_response/writeup.jsp?docid=2003-120914-4108-99&tabid=2)

Zlob:
[http://www.symantec.com/security_response/writeup.jsp?docid=2005-042316-2917-99&tabid=2](http://www.symantec.com/security_response/writeup.jsp?docid=2005-042316-2917-99&tabid=2)

---

### Post by rune0077 on 2008-02-10
> **Bungo Pony said:**
> 
I've been running Ubuntu since last March. Transition has been a bit slow, but this whole spyware/trojan issue has really sped up my adaptation of Ubuntu..

My secret conspiracy theory: the massive spyware/virus software that is threatening Windows-users is actually all engineered by a small group of Linux enthusiasts, who, aspiring for OS world domination, is trying to drive users away from Windows and switch to Linux. :)

---

### Post by tadcan on 2008-02-11
A random guess. Have you tried this for converting songs to different file types.
 [http://www.nch.com.au/switch/plus.html](http://www.nch.com.au/switch/plus.html)

If you have physical backups of the songs you may have to rip them from scratch in Ubuntu.

---

### Post by gsiliceo on 2008-02-12
I do this and not a single spyware have beaten this metod:
Start in safe mode with console only(so i does not start iexplore hijacked)

hit ctrl+alt+del, and from the file menu(i think, its the first one)

run, autoruns(google it)

Unthick everything thats not signed from a vendor(a couple of windows files are not signed but are safe to remove in most cases)
Some legit programs are unsigned, if you don't know, unthick them and when you reboot normally if you see something missing, reinstall it.

After that run a battery of spywares, antivirus, everything you can throw at it to remove the evil(not active) files.
Works everytime

---

### Post by Bungo Pony on 2008-02-13
> **tadcan said:**
> A random guess. Have you tried this for converting songs to different file types.
 [http://www.nch.com.au/switch/plus.html](http://www.nch.com.au/switch/plus.html)

If you have physical backups of the songs you may have to rip them from scratch in Ubuntu.

I haven't tried that, but I'm quite happy with EAC for ripping and conversion. It does a fine job at both.

I'll try the autorun when I get a bit of time to screw around with Windows (again). People complain about how much time it takes to get things running in Ubuntu. It's NOTHING compared to fixing Windows!

I'm gonna try and get a slightly older version of Nero Vision to work in Wine. That's pretty much the only thing I use Windows for now.

---

