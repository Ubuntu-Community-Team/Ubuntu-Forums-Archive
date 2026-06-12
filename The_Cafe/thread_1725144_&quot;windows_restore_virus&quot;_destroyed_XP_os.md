---
title: "&quot;windows restore virus&quot; destroyed XP os"
date: 2011-04-09
forum: The Cafe
---

### Post by sdowney717 on 2011-04-09
At a friends house running XP and IE6. We visited perhaps 6 sites.
google searches
speedtest.net
verizon fios
hulu to download hulu desktop
amazon
ebay
 
somewhere during this time, AVAST notified us of some malware and said it had blocked the infection.

Then this malware started manifesting with multiple popups saying hard drive was failing with bad sectors, system infected etc... lots of scary sounding ominous warnings, 4 or 5 messages and it started running a scanning window.
So Avast let this malware set itself up on the PC.
So we tried to run system restore, said it could not start
We reboot in safe mode to run system restore and it cant start.
The task manager is DISABLED. The desktop icons are gone. screen background is black in normal mode.
So we open windows explorer and none of the files are listed, c: shows a blank
So we open a cmd terminal window and do dir's and comes back empty. We could move into directories and it would show the folder name but no file names. 
So we reboot 4 or 5 times back and forth safe mode and normal and finally this thing has totally taken over the PC. If you halt its scanner, you can not interact with the menus anymore.
All this took about 30 minutes from a fully functioning PC to totally hosed.

So we are going to install Ubuntu and he will run XP in virtualbox.

[http://www.expertsupportnow.com/1034/how-to-remove-windows-restore-virus-malware/](http://www.expertsupportnow.com/1034/how-to-remove-windows-restore-virus-malware/)

This comes in threw an active x control.
I think that IE allowed this onto the PC.

---

### Post by P1C0 on 2011-04-09
> **sdowney717 said:**
> At a friends house running XP and IE6. We visited perhaps 6 sites.
google searches
speedtest.net
verizon fios
hulu to download hulu desktop
amazon
ebay
 
somewhere during this time, AVAST notified us of some malware and said it had blocked the infection.

Then this malware started manifesting with multiple popups saying hard drive was failing with bad sectors, system infected etc... lots of scary sounding ominous warnings, 4 or 5 messages and it started running a scanning window.
So Avast let this malware set itself up on the PC.
So we tried to run system restore, said it could not start
We reboot in safe mode to run system restore and it cant start.
The task manager is DISABLED. The desktop icons are gone. screen background is black in normal mode.
So we open windows explorer and none of the files are listed, c: shows a blank
So we open a cmd terminal window and do dir's and comes back empty. We could move into directories and it would show the folder name but no file names. 
So we reboot 4 or 5 times back and forth safe mode and normal and finally this thing has totally taken over the PC. If you halt its scanner, you can not interact with the menus anymore.
All this took about 30 minutes from a fully functioning PC to totally hosed.

So we are going to install Ubuntu and he will run XP in virtualbox.

[http://www.expertsupportnow.com/1034/how-to-remove-windows-restore-virus-malware/](http://www.expertsupportnow.com/1034/how-to-remove-windows-restore-virus-malware/)

This comes in threw an active x control.
I think that IE allowed this onto the PC.Well, the worst thing you can do after an infection is reboot the pc, because the virus probably has also invited some friends of him that will start on next reboot.

Other than that, Linux is the way to go.

---

### Post by CharlesA on 2011-04-09
Why would you even go on the internet using IE6?

The only thing that browser is good for is updating Windows (to get IE8) and downloading a different browser.

---

### Post by Spr0k3t on 2011-04-09
On a new/load system of XP, the first thing I do is load Firefox from a flash drive and make it the default.  If I don't have the flash drive, I grab the latest release from the ftp public site... never having to open IE once... unless it's to update the systems software.

---

### Post by Timmer1240 on 2011-04-09
This Program is the way to go on a windows machine before I started using Linux I used this on my xp install it saved my skin many times![http://www.sandboxie.com/](http://www.sandboxie.com/)

---

### Post by LowSky on 2011-04-09
there is no way those sites led to a system full of bugs.

---

### Post by CharlesA on 2011-04-09
> **LowSky said:**
> there is no way those sites led to a system full of bugs.
I agree.

The only thing I can think of is that some sites may serve ads that can trick you into installing scareware.

---

### Post by Philsoki on 2011-04-09
> **LowSky said:**
> there is no way those sites led to a system full of bugs.
I don't think the OP is telling the full story. If Windows was that bad it wouldn't be usable, no one would use it.

I installed Windows XP SP3 today and haven't had any trouble. It's beyond me how they were able to get a virus visiting six websites. No offense, the only reason you can get a virus on Windows is if you put it on there yourself. 

It's why Windows users always get viruses, because they run .exe files without thinking.
"Oh hey, this website scanned my computer and it seems I have viruses, but no worries because they've given me a free Antivirus.exe to download - Just double click and install!"

Sorry, but posts like this annoy the hell out of me.

/rant

---

### Post by gsmanners on 2011-04-09
Doesn't SP3 come with IE7 or 8? I can believe IE6 might hose your system.

---

### Post by CharlesA on 2011-04-09
> **gsmanners said:**
> Doesn't SP3 come with IE7 or 8? I can believe IE6 might hose your system.
Not by default.

---

### Post by el_koraco on 2011-04-09
> **Philsoki said:**
> It's why Windows users always get viruses, because they run .exe files without thinking."Oh hey, this website scanned my computer and it seems I have viruses, but no worries because they've given me a free Antivirus.exe to download - Just double click and install!"



not necassarily, with active content, you can get into trouble with virus scanning scam trojans. you don't have to actually download them, you just get a pop up thingy, and when you try to close it the trouble begins. it's not that hard to manually find the infection, but once you start panicing, rebooting, the deamons can give you a lot of headache. 

i think these problems stopped with ie8 and up, but the older versions are just plain dangerous. visiting the web with them is like playing roulette.

---

### Post by sdowney717 on 2011-04-09
actually I dont possibly know the whole story about when or how the PC got infected.
Those sites are the relevant ones sticking in my mind. It is possible we surfed somewhere looking at speedtests or video streaming related to hulu desktop. Or he got it infected earlier. The avast did notify us of an trojan and the notification showed up after we went to amazon. BUT the avast did not work to keep it from getting infected.

I took the drive home and ran avast4linux.
You have to modify a system parameter to make it run.
It ran without the database update, but after the update, avast would not start.
So I followed the recommend to change a line in one of the files and rebooted and it worked fine then.
I selected thorough and check archives.
[http://forum.avast.com/index.php?topic=57812.0](http://forum.avast.com/index.php?topic=57812.0)

It found and I deleted 2 viruses into the virus chest. 
I followed the manual removal for the lnk files
I think the OS will work now.

---

### Post by uRock on 2011-04-09
MS Security Essentials FTW! MaximumPC rates it 8 out of 10.

---

### Post by jerenept on 2011-04-09
> **uRock said:**
> MS Security Essentials FTW! MaximumPC rates it 8 out of 10.

I use NOD32 and ClamSentinel, and, of course, my brain.

---

### Post by CharlesA on 2011-04-09
Antivirus isn't a substitute for smart browsing habits either. :)

---

### Post by uRock on 2011-04-09
> **jerenept said:**
> I use NOD32 and ClamSentinel, and, of course, **my brain**.

Using the bolded practically negates the need of the previous things, but they are good to have for those moments we slip up.

MaximumPC gave ClamWIN(free) a 3 out of 10 rating. Mostly because it is on demand and doesn't proactively scan downloads and is a CPU hog when it is scanning.

---

### Post by jerenept on 2011-04-09
> **uRock said:**
> Using the bolded practically negates the need of the previous things, but they are good to have for those moments we slip up.

MaximumPC gave ClamWIN(free) a 3 out of 10 rating. Mostly because it is on demand and doesn't proactively scan downloads and is a CPU hog when it is scanning.

clamSentinel gives clamwin on-access scanning, or whatever it's called. I use it mainly as a second opinion, though.
Agree with the CPU hogging. :P

---

### Post by Quadunit404 on 2011-04-09
I guess I'll say this right about now:

ESET Smart Security 4 = ftw. It tells me if there are updates available in Windows Update, it kills viruses dead immediately, allows me to terminate downloads if it detects a virus and it continues to protect me even after my license expires. Oh, and it's lightweight too.

---

### Post by tgm4883 on 2011-04-09
> **P1C0 said:**
> Well, the worst thing you can do after an infection is reboot the pc, because the virus probably has also invited some friends of him that will start on next reboot.

Other than that, Linux is the way to go.

That isn't entirely accurate. If a threat (please don't call them viruses unless it actually is one) get onto a system and downloaded other threats as well, it would have no issues starting those threats. It does not need to wait for a reboot.

---

### Post by tgm4883 on 2011-04-09
> **Philsoki said:**
> I don't think the OP is telling the full story. If Windows was that bad it wouldn't be usable, no one would use it.


Windows is that bad, but yea the story likely isn't entirely accurate.

> **Philsoki said:**
> 
I installed Windows XP SP3 today and haven't had any trouble. It's beyond me how they were able to get a virus visiting six websites. **No offense, the only reason you can get a virus on Windows is if you put it on there yourself. **


Not true. There are plenty of ways to get a threat. Read up on worms, security vulnerabilities, and drive by downloads. Conficker did this, as do other threats. No user input necessary.

> **Philsoki said:**
> 
It's why Windows users always get viruses, because they run .exe files without thinking.
"Oh hey, this website scanned my computer and it seems I have viruses, but no worries because they've given me a free Antivirus.exe to download - Just double click and install!"

Sorry, but posts like this annoy the hell out of me.

/rant

Yea the OP didn't get infected by those websites (unless it was a malicious ad on one of those websites). What probably happened is another infected system on that network infected that PC. Which is usually an issue if you don't do Windows security updates or run without a firewall.

---

### Post by espressobeanie on 2011-04-09
Lol. Why are we talking about XP on a Linux site? I'm happy I'm a Penguin.

---

### Post by d3v1150m471c on 2011-04-09
the thing is with internet explorer, and i don't believe this is the case on other browsers, is the use of activex controls. It's entirely possible to control a client computer using javascript. I know, i've done it before playing around with it. Change your browser when in windows. Personally, i'd scrap windows all together but sometimes people need it to run specific software.

---

### Post by uRock on 2011-04-09
> **jerenept said:**
> clamSentinel gives clamwin on-access scanning, or whatever it's called.

Kool!

---

### Post by matty abbo on 2011-04-09
Windows XP SP3 won't allow you to roll back to  IE 6, but if you already have IE 6 installed and go to install SP3, it will leave IE 6 be, and you could always tried booting to ubuntu using the live CD and running anti virus software through ubuntu and then booting back into XP, should work :)

---

### Post by KL_72_TR on 2011-04-09
> **CharlesA said:**
> Why would you even go on the internet using IE6?

The only thing that browser is good for is updating Windows (to get IE8) and downloading a different browser.
I totally agree.

> **Spr0k3t said:**
> On a new/load system of XP, the first thing I do is load Firefox from a flash drive and make it the default.  If I don't have the flash drive, I grab the latest release from the ftp public site... never having to open IE once... unless it's to update the systems software.
Yes. That's what I do to stay out of trouble.
> **Philsoki said:**
>  No offense, the only reason you can get a virus on Windows is if you put it on there yourself. 

It's why Windows users always get viruses, because they run .exe files without thinking.

Sorry, but posts like this annoy the hell out of me.

/rant
Hell...o. Don't underestimate the nature of the beast...

---

### Post by earthpigg on 2011-04-09
are we really having an argument about which antivirus is the best?

here, ill throw my $0.02 in:

whichever one spends the most resources on incentivising malware creation. for many reasons, that will be the best one.

---

### Post by uRock on 2011-04-09
> **earthpigg said:**
> are we really having an argument about which antivirus is the best?
No.

---

### Post by disabledaccount on 2011-04-09
> **sdowney717 said:**
> At a friends house running XP and IE6. We visited perhaps 6 sites.
google searches
speedtest.net
verizon fios
hulu to download hulu desktop
amazon
ebay
 
somewhere during this time, AVAST notified us of some malware and said it had blocked the infection.

Then this malware started manifesting with multiple popups saying hard drive was failing with bad sectors, system infected etc... lots of scary sounding ominous warnings, 4 or 5 messages and it started running a scanning window.
So Avast let this malware set itself up on the PC.
So we tried to run system restore, said it could not start
We reboot in safe mode to run system restore and it cant start.
The task manager is DISABLED. The desktop icons are gone. screen background is black in normal mode.
So we open windows explorer and none of the files are listed, c: shows a blank
So we open a cmd terminal window and do dir's and comes back empty. We could move into directories and it would show the folder name but no file names. 
So we reboot 4 or 5 times back and forth safe mode and normal and finally this thing has totally taken over the PC. If you halt its scanner, you can not interact with the menus anymore.
All this took about 30 minutes from a fully functioning PC to totally hosed.

What can i say - don't even try to use xp without combofix and hijackthis (or similar software). There is no good antivirus for some speciall malware/trojans - some of them could even disable AV services - you are lucky, because it was "light" virus - thats all.

---

### Post by barthus on 2011-04-09
> **sdowney717 said:**
> At a friends house running XP and IE6. We visited perhaps 6 sites.
google searches
speedtest.net
verizon fios
hulu to download hulu desktop
amazon
ebay
 
somewhere during this time, AVAST notified us of some malware and said it had blocked the infection

... and so on



I find this quite amusing, really!

Sometimes I understand that we need to keep the overall worldwide market share of Linux  below 5%! Because then, we must not fear all this idiotic nonesense ... .

Tell your friend to change to Linux. But tell only him about this. :)

---

### Post by Spr0k3t on 2011-04-09
From that list, it's hard to believe... but it is possible, depending on the searches done.  To disinfect use this:

Safemode:
 - Hitman Pro 3.5
 - Malwarebytes

Notsosafemode:
 - Hitman Pro 3.5 (again)
 - Malwarebytes (again)
 - SuperAntiSpyware
 - TrojanRemover
 - Any AntiVirus full system scan.

Should be done at that point.  Usually I catch most everything out there, on a random occasion it's not possible to fix networking issues and requires a complete rebuild.  An alternate permanent fix is to install Linux and ditch Microsoft.

---

### Post by youbuntu on 2011-04-09
I have a friend who runs a PC shop. He repairs PCs daily, and yet INSISTS on using Internet Explorer, and never anything else, on ALL his PCs... :? (yes, he does know better, however, but insists he will not switch).

Suffice to say, said friend is the subject of much teasing and ridicule. Also, said friend does _everything_ with his mouse, and I mean EVERYTHING, telling me he "can't be bothered" to learn KB shortcuts, and admits he knows none.

How I laugh at him (to his face) and how he seems not to care (good for him :)). Oh the truth of "ignorance is bliss"...

---

### Post by Johnsie on 2011-04-09
+1 for Microsoft security essentials. It's a great free product.

I also use Winpatrol. It's a little bit sensitive but I think it's better to be safe than sorry.

Hijackthis is also an highly important tool and malwarebytes is pretty effective.

The first thing you should do when you install windows is disable system restore, get Security Essentials and install IE7 or above. Do the Windows Update and then you will be alot safer to visit non-microsoft sites.

It is safer to use Desktop Linux but I'm not going to get on the Linux high-horse.  There are alot of serious vulnerabilities in Linux. It's just that less people are targeting those vulnerabilities. It makes more sense to target the most used platform (Windows). It's also important to remember that most servers that are hacked are actually Linux servers. Criminals are willling to target Linux servers more than desktops because webservers are the best way to spread the malware.

If you're interested in Linux security I would suggest reading the following site:
[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn) 

As I said, the vulnerabilities exist, but aren't exploited much

---

### Post by NCLI on 2011-04-09
> **Johnsie said:**
> +1 for Microsoft security essentials. It's a great free product.

I also use Winpatrol. It's a little bit sensitive but I think it's better to be safe than sorry.

Hijackthis is also an highly important tool and malwarebytes is pretty effective.

I'm not going to get on the Linux high-horse though. It is safer to use Desktop Linux. That doesn't mean there are less vulnerabilities in Linux. It's just that less people are targeting those vulnerabilities. It makes more sense to target the most used platform. It's also important to remember that most servers that are hacked are actually Linux servers. Criminals are willling to target Linux servers more than desktops because webservers are the best way to spread the malware.

If you're interested in Linux security I would suggest reading the following site:
[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn) 

As I said, the vulnerabilities exist, but aren't exploited much
Do you realise what the big, hugely important difference between the vulnerabilities listed there is, compared to the vulnerabilities listed similarly by Microsoft?

These are always fixed within a few days. 

If you read through the list, you'll notice that most, if not all of them(I couldn't be bothered to read the entire thing) have been resolved by a simple update.

It is a common misconception that Linux is only safe because it is small. Do you really think criminals aren't interested in all the huge linux servers out there? Of course3 they are, but where Microsoft usually just ignores vulnerabilities if it finds them itself, Linux is open-source, so any vulnerabilities are simply reported to the relevant bug trackers, a patch is developed and, within a few days, it is released, solving the problem.

Microsoft usually only fixes vulnerabilities if there are real attacks in the wild, otherwise, it just issues security notifications with workarounds for the problem.

Don't believe me? Then try comparing [this]("http://secunia.com/advisories/product/27467/") to [this]("http://secunia.com/advisories/product/30524/").

I'll sum it up for you:
[QUOTE=Microsoft Windows 7]Vendor, Links, and Unpatched Vulnerabilities

Vendor 	Microsoft

Product Link 	View Here (Link to external site)

Affected By 	59 Secunia advisories
96 Vulnerabilities

Monitor Product 	Receive alerts for this product

Unpatched 	10% (6 of 59 Secunia advisories)

Most Critical Unpatched
The most severe unpatched Secunia advisory affecting Microsoft Windows 7, with all vendor patches applied, is rated Highly critical[/QUOTE]
[QUOTE=Ubuntu 10.04]Vendor, Links, and Unpatched Vulnerabilities

Vendor 	Canonical Ltd.

Product Link 	View Here (Link to external site)

Affected By 	137 Secunia advisories
706 Vulnerabilities

Monitor Product 	Receive alerts for this product

Unpatched 	0% (0 of 137 Secunia advisories)

Most Critical Unpatched
There are no unpatched Secunia advisories affecting this product, when all vendor patches are applied.[/QUOTE]
Also of note is that Secunia knows about way more bugs in Ubuntu 10.04 than in Windows 7. This is due to it being open source, meaning that more bugs are reported, making a zero-day attack less likely.

---

### Post by Philsoki on 2011-04-09
> **KL_72_TR said:**
> 
Hell...o. Don't underestimate the nature of the beast...
I know, it totally came out of no-where, almost like I was a Windows fanboy or something.:P

> Not true. There are plenty of ways to get a threat. Read up on worms,  security vulnerabilities, and drive by downloads. Conficker did this, as  do other threats. No user input necessary.
I really don't need to read up on those things... I'll bet I can use Windows an entire year for just as many things as I use a Linux machine for and not have any (viruses) issues. Starting... Yesterday:[IMG]http://min.us/jmTvge.bmp[/IMG]


Do you see what you've done?! Now I feel compelled to use Windows to prove its not as bad everyone says it is.

---

### Post by tgm4883 on 2011-04-09
> **Philsoki said:**
> I know, it totally came out of no-where, almost like I was a Windows fanboy or something.:P


I really don't need to read up on those things... I'll bet I can use Windows an entire year for just as many things as I use a Linux machine for and not have any (viruses) issues. Starting... Yesterday:[IMG]http://min.us/jmTvge.bmp[/IMG]


Do you see what you've done?! Now I feel compelled to use Windows to prove its not as bad everyone says it is.

Yes you can use XP just fine and not have any issues, if you know what you are doing. You also probably

1) Run everything as a limited user
2) Use some form of firewall
3) Run antivirus
4) Are up to date on security patches

Your sample size will be 1, which means in the world of scientific experiments it is meaningless. Guess what, when I ran Windows I didn't have threats either, but that doesn't mean that XP is secure by any means. I deal with customer's corporate environments every day, some of which are locked down pretty tight. Even some of those end up with some nasty outbreaks.

---

### Post by Philsoki on 2011-04-09
> **tgm4883 said:**
> Yes you can use XP just fine and not have any issues, if you know what you are doing. You also probably

1) Run everything as a limited user
2) Use some form of firewall
3) Run antivirus
4) Are up to date on security patches

Your sample size will be 1, which means in the world of scientific experiments it is meaningless. Guess what, when I ran Windows I didn't have threats either, but that doesn't mean that XP is secure by any means. I deal with customer's corporate environments every day, some of which are locked down pretty tight. Even some of those end up with some nasty outbreaks.
I like you, you're knowledgeable.

---

### Post by Spr0k3t on 2011-04-09
Don't forget, you can run almost any Windows environment without the risk of getting attacked... even without an anti-virus app.  I ran an XP system like that for two years without virus problems.  The key, as mentioned already in this thread, use your brain and you'll be fine.

---

### Post by wolfen69 on 2011-04-09
> **Spr0k3t said:**
> I ran an XP system like that for two years without virus problems.  The key, as mentioned already in this thread, **use your brain and you'll be fine.**

In other words, surf at only THE most safe sites known, DO NOT go on a surfing spree when you are bored, and last but not least, DO NOT download any porn. But hey, who actually likes to have fun with their computers? I couldn't imagine the average user doing any of the above. ;-)

---

### Post by Philsoki on 2011-04-09
> **wolfen69 said:**
> In other words, surf at only THE most safe sites known, DO NOT go on a surfing spree when you are bored, and last but not least, DO NOT download any porn. But hey, who actually likes to have fun with their computers? I couldn't imagine the average user doing any of the above. ;-)
A joke? I showed uTorrent in the screenshot for a reason... I'll visit all the sites I want (And have been) without issues.

---

### Post by Timmer1240 on 2011-04-09
[http://www.sandboxie.com/](http://www.sandboxie.com/) Surf all the porn sites or whatever darkside of the web you want on a windows machine with this your computer will be safe!

---

### Post by SeijiSensei on 2011-04-10
> **NCLI said:**
> Also of note is that Secunia knows about way more bugs in Ubuntu 10.04 than in Windows 7. This is due to it being open source, meaning that more bugs are reported, making a zero-day attack less likely.

I haven't looked at the Secunia lists lately, but I recall that "Ubuntu" included both the kernel and every other package that's bundled with it.  So security problems in, say, Firefox are attributed to Ubuntu even though it has no direct responsibility for Firefox other than distributing it and its patches.  "Windows," on the other hand, refers to a much more limited collection of software.  Even though there's a version of Firefox for Windows, Microsoft isn't considered responsible for Firefox in the same way Ubuntu is.

This method of counting vulnerabilities is often exploited by Windows apologists who want to make it seem Windows is the more secure OS.  See the comments to [this article](http://www.pcworld.com/businesscenter/article/218083/dont_let_microsoft_trained_brain_syndrome_happen_to_you.html) for an example of this strategem.

---

### Post by NCLI on 2011-04-10
> **SeijiSensei said:**
> I haven't looked at the Secunia lists lately, but I recall that "Ubuntu" included both the kernel and every other package that's bundled with it.  So security problems in, say, Firefox are attributed to Ubuntu even though it has no direct responsibility for Firefox other than distributing it and its patches.  "Windows," on the other hand, refers to a much more limited collection of software.  Even though there's a version of Firefox for Windows, Microsoft isn't considered responsible for Firefox in the same way Ubuntu is.

This method of counting vulnerabilities is often exploited by Windows apologists who want to make it seem Windows is the more secure OS.  See the comments to [this article](http://www.pcworld.com/businesscenter/article/218083/dont_let_microsoft_trained_brain_syndrome_happen_to_you.html) for an example of this strategem.
That just makes it even more incredible that Ubuntu has 0 unfixed vulnerabilities, while Windows has several.

---

### Post by SeijiSensei on 2011-04-10
As I said, I haven't looked at the lists lately to see if that's still true.  They may have "levelled-the-playing-field" in the interim.

---

### Post by Philsoki on 2011-04-10
> This method of counting vulnerabilities is often exploited by Windows  apologists who want to make it seem Windows is the more secure OS.  See  the comments to [this article]("http://www.pcworld.com/businesscenter/article/218083/dont_let_microsoft_trained_brain_syndrome_happen_to_you.html") for an example of this strategem.
"Windows apologists..." :P

I don't think Windows is more secure than Linux, no sir. But I do think its secure enough to be a usable system if you know what you're doing - kind of like Linux. 

I mean, people come on here all the time just to get help with one problem and never come back. Any one of us could say "OK, I'd like to help you. This command will tell me what I need to know, please open a terminal and run:
```
sudo rm -rf
```

You can open a terminal by going to Applications > Accessories > Terminal."

Sure, its not a virus, but it's just as dangerous as one.

---

### Post by NCLI on 2011-04-10
> **Philsoki said:**
> "Windows apologists..." :P

I don't think Windows is more secure than Linux, no sir. But I do think its secure enough to be a usable system if you know what you're doing - kind of like Linux. 

I mean, people come on here all the time just to get help with one problem and never come back. Any one of us could say "OK, I'd like to help you. This command will tell me what I need to know, please open a terminal and run:
```
sudo rm -rf
```

You can open a terminal by going to Applications > Accessories > Terminal."

Sure, its not a virus, but it's just as dangerous as one.
Ah, but you have to run it yourself. Malware on Windows can utilise exploits to execute themselves without user interaction, which is why an anti-malware tool is neccesary to use Windows safely.

If Microsoft would simply fix the flaws the malware exploits within days of them being discovered, and use a safe repository system like Linux has for years, there would be no need for anti-malware tools.

Alas, that apparently isn't going to happen. It seems that Windows 8 will have a safe repository, but that is only half of the equation.

---

### Post by Philsoki on 2011-04-10
> **NCLI said:**
> Ah, but you have to run it yourself. Viruses on Windows can utilise exploits to execute themselves without user interaction.
But how common are viruses like that?

---

### Post by NCLI on 2011-04-10
> **Philsoki said:**
> But how common are viruses like that?
I'd say quite common, since we need anti-malware tools. I don't have any numbers on this, and can't be bothered to google it right now, but I'm sure Symantec will have some statistics on the matter.

If they were unusual, you'd be completely fine with no anti-malware software, as long as you didn't install any dangerus software.

So, here's my challenge: Use a Windows computer just like ypu would use Ubuntu, let's say for three months. Do not install any anti-malware software, do not install a firewall, or do any other security-related modifications. After those three months are over, if the computer still works, install anti-malware software, and see what's there. Most malware is well hidden nowadays.

I very much doubt it would last that long, or at least I'd imagine you would find A LOT of dangerous stuff when you run that scan.

---

### Post by Philsoki on 2011-04-10
> **NCLI said:**
> I'd say quite common, since we need anti-malware tools. I don't have any numbers on this, and can't be bothered to google it right now, but I'm sure Symantec will have some statistics on the matter.
What I mean is... Can you link me to a webpage that will automatically download and install a virus onto my computer?

---

### Post by NCLI on 2011-04-10
> **Philsoki said:**
> What I mean is... Can you link me to a webpage that will automatically download and install a virus onto my computer?
I edited the post quite heavily, you might want to take a look at it again.

And no, I can't. Usually, when these agressive infections are discovered on sites, they are removed.

---

### Post by Philsoki on 2011-04-10
> **NCLI said:**
> So, here's my challenge: Use a Windows computer just like ypu would use Ubuntu, let's say for three months. Do not install any anti-malware software, do not install a firewall, or do any other security-related modifications. After those three months are over, if the computer still works, install anti-malware software, and see what's there. Most malware is well hidden nowadays.

I very much doubt it would last that long, or at least I'd imagine you would find A LOT of dangerous stuff when you run that scan.
That's like saying remove every security feature out of Linux and use it how you normally would for three months. I doubt it would come out too well, just look how many security patches you get with every Debian update.

Edit: And editing your post completely changed the context of mine, so here's yours before the edit for context:
> **NCLI said:**
> Ah, but you have to run it yourself. Malware on Windows can utilise  exploits to execute themselves without user interaction, which is why an  anti-malware tool is neccesary to use Windows safely.

If Microsoft would simply fix the flaws the malware exploits within days  of them being discovered, and use a safe repository system like Linux  has for years, there would be no need for anti-malware tools.

Alas, that apparently isn't going to happen. It seems that Windows 8  will have a safe repository, but that is only half of the equation.

---

### Post by SeijiSensei on 2011-04-10
> **Philsoki said:**
> But how common are viruses like that?

Have you read much about the [Stuxnet]("http://www.zdnet.co.uk/news/security/2010/07/19/windows-systems-at-risk-from-stuxnet-shortcut-malware-40089575/") worm, the one allegedly designed to disable Iran's nuclear weapons program?  The systems running the centrifuges that were the target of the worm were physically disconnected from the main research network and had no contact with the Internet at all.  The worm's developers solved this problem by using the "autorun" feature of Windows.  It turned out that USB sticks were a common method of collecting data from the centrifuges and taking them to the research network for study and reporting.  The sticks would be infected at that point, then they'd transfer their payloads via autorun when inserted back into the centrifuge network.

Autorun has been a common method for delivering malware in other instances.  [British executives traveling to China]("http://www.timesonline.co.uk/tol/news/uk/crime/article7009749.ece") for trade meetings would often receive a USB stick as a gift from their Chinese hosts.  Once inserted into the executive's laptop, the autorun facility would install a variety of malware onto the laptop that would scour the local machine and any visible networks for sensitive documents and ship them over the Internet to China.

A well-known [experiment]("http://www.darkreading.com/security/perimeter-security/208803634/index.html") was based on dropping USB pendrives into the parking lots of businesses.  The drives contained a harmless bit of code that, when executed via autorun, would report on its installation to the experimenters.  Nearly every device reported back.

These autorun infections take place silently when the .lnk file on the drive is run to create an icon on the desktop.

Nowadays we don't have the same frequency of "drive-by" infections that happened with earlier versions of Internet Explorer, so villains have changed their strategy.  The "Antivirus 2010" and "Windows Repair" malware scam the user into believing his or her computer is infected.  These use a simple Javascript program that runs when a browser window is closed.  The unwitting user is shown a screen full of scary reports of the viruses supposedly found with a link to a trojan posing as an antivirus program.  Most of these programs also disable any existing legitimate antivirus programs so they will escape detection.

Of course, there's the perennial email touting nude celebrity photos which is really just a link to an executable designed to install a keylogger or similar malware.  The executables used to be contained as an attachment to the message, but the widespread scanning of email for viruses put a stop to that.  Now there's just a link.  URL-shorteners like bit.ly are a good way to hide such scams.

One popular recent vector are [infected PDF files]("http://searchsecurity.techtarget.com/news/1527652/Email-attachments-unique-attacks-highlight-Internet-espionage-trends") that exploit known holes in Adobe Reader.  So while it's a lot more difficult to get a "drive-by" infection via an ActiveX exploit, it's not that hard to get people to open an [infected PDF document]("http://news.softpedia.com/news/Zero-Day-Adobe-Reader-Exploit-Found-in-the-Wild-129921.shtml") residing on a public website. At first Adobe was unwilling even to admit these vulnerabilities existed.  They've since accelerated their patching efforts as more vulnerabilities were reported.  This case illustrates how closed-source software puts its users at-risk while awaiting a fix from the vendor.  Open-source applications have certainly had their share of vulnerabilities, too, but once discovered they get patched much more quickly, in part because the holes are visible to everyone.

---

### Post by NCLI on 2011-04-10
> **Philsoki said:**
> That's like saying remove every security feature out of Linux and use it how you normally would for three months. I doubt it would come out too well, just look how many security patches you get with every Debian update.
I didn't ask you to turn off Windows Update, which is what your suggestion would equate to. I'm just comparing the out-of-the-box-experience, which is really what should be compared.

> Edit: And editing your post completely changed the context of mine, so here's yours before the edit for context:
Yeah, I know, sorry. I didn't think you'd reply to it so quickly.

---

### Post by Philsoki on 2011-04-10
> **SeijiSensei said:**
> Have you read much about the Stuxnet worm, the one allegedly designed to disable Iran's nuclear weapons program?  The systems running the centrifuges that were the target of the worm were physically disconnected from the main research network and had no contact with the Internet at all.  The worm's developers solved this problem by using the "autorun" feature of Windows.  It turned out that USB sticks were a common method of collecting data from the centrifuges and taking them to the research network for study and reporting.  The sticks would be infected at that point, then they'd transfer their payloads via autorun when inserted back into the centrifuge network.

Autorun has been a common method for delivering malware in other instances.  [British executives traveling to China]("http://www.timesonline.co.uk/tol/news/uk/crime/article7009749.ece") for trade meetings would often receive a USB stick as a gift from their Chinese hosts.  Once inserted into the executive's laptop, the autorun facility would install a variety of malware onto the laptop that would scour the local machine and any visible networks for sensitive documents and ship them over the Internet to China.

A well-known [experiment]("http://www.darkreading.com/security/perimeter-security/208803634/index.html") was based on dropping USB pendrives into the parking lots of businesses.  The drives contained a harmless bit of code that, when executed via autorun, would report on its installation to the experimenters.  Nearly every device reported back.

Nowadays we don't have the same frequency of "drive-by" infections that happened with earlier versions of Internet Explorer, so villains have changed their strategy.  The "Antivirus 2010" and "Windows Repair" malware scam the user into believing his or her computer is infected.  These use a simple Javascript program that runs when a browser window is closed.  The unwitting user is shown a screen full of scary reports of the viruses supposedly found with a link to a trojan posing as an antivirus program.  Most of these programs also disable any existing legitimate antivirus programs so they will escape detection.

Of course, there's the perennial email touting nude celebrity photos which is really just a link to an executable designed to install a keylogger or similar malware.  The executables used to be contained as an attachment to the message, but the widespread scanning of email for viruses put a stop to that.  Now there's just a link.  URL-shorteners like bit.ly are a good way to hide such scams.

One popular recent vector is using [infected PDF files]("http://searchsecurity.techtarget.com/news/1527652/Email-attachments-unique-attacks-highlight-Internet-espionage-trends") to exploit known holes in Adobe Reader.  So while it's a lot more difficult to get a "drive-by" infection via an ActiveX exploit, it's not that hard to get people to open an infected PDF document residing on a public website.
A lot of what you just wrote was related to cases of espionage though... I really don't think I need to worry about secret agents giving me free USB drives.:lolflag:
Reminds me of of this...[IMG]http://imgs.xkcd.com/comics/open_source.png[/IMG]

---

### Post by DrSeemann on 2011-04-10
If Antivirus, Firewall, Anti Malware, were "part of" "Windows Security" they would be included in the software license.

I don't think that windows is **completely useless**, but you will have to spend some money on a decent heavy antivirusspywaremalwarefirewall. And when the moment of switching OS version comes. Well, get a new PC, or die waiting for it to boot.

My 2 cents.

---

### Post by Philsoki on 2011-04-10
> **DrSeemann said:**
> If Antivirus, Firewall, Anti Malware, were "part of" "Windows Security" they would be included in the software license.

I don't think that windows is **completely useless**, but you will have to spend some money on a decent heavy antivirusspywaremalwarefirewall. And when the moment of switching OS version comes. Well, get a new PC, or die waiting for it to boot.

My 2 cents.
[http://en.wikipedia.org/wiki/Microsoft_Security_Essentials](http://en.wikipedia.org/wiki/Microsoft_Security_Essentials) (One of many free security programs for Windows)

Like Linux, there are plenty of free programs available for Windows. Including software for the security issues you listed. And c'mon, Firewall? Even Windows XP comes with a Firewall.;)

---

### Post by NCLI on 2011-04-10
> **Philsoki said:**
> [http://en.wikipedia.org/wiki/Microsoft_Security_Essentials](http://en.wikipedia.org/wiki/Microsoft_Security_Essentials) (One of many free security programs for Windows)

Like Linux, there are plenty of free programs available for Windows. Including software for the security issues you listed. And c'mon, Firewall? Even Windows XP comes with a Firewall.;)
What I meant is that you should not install any security tools that are not included with the system, or automatically installed.

Everything necessary for a secure system should be included with the system.

---

### Post by DrSeemann on 2011-04-10
> **Philsoki said:**
> [http://en.wikipedia.org/wiki/Microsoft_Security_Essentials](http://en.wikipedia.org/wiki/Microsoft_Security_Essentials) (One of many free security programs for Windows)

Like Linux, there are plenty of free programs available for Windows. Including software for the security issues you listed. And c'mon, Firewall? Even Windows XP comes with a Firewall.;)
Well then, do something. Install a complete suite of free anwtivirusfirewallmalwarespyware run it for a while, then install some expensive soft like spywaredoctor and post the results of a test. Oh btw you can rely on Windows Firewall, it works just fine.

---

### Post by Philsoki on 2011-04-10
> **DrSeemann said:**
> Well then, do something. Install a complete suite of free anwtivirusfirewallmalwarespyware run it for a while, then install some expensive soft like spywaredoctor and post the results of a test. Oh btw you can rely on Windows Firewall, it works just fine.
Uh... What?

---

### Post by NCLI on 2011-04-10
> **Philsoki said:**
> Uh... What?

Yeah, he lost me too. O.o

---

### Post by DrSeemann on 2011-04-10
> **NCLI said:**
> Yeah, he lost me too. O.o
What I mean is that when it comes to security mater, using a private OS, you can't trust on "free antivirus" that much.

---

### Post by NCLI on 2011-04-10
> **DrSeemann said:**
> What I mean is that when it comes to security mater, using a private OS, you can't trust on "free antivirus" that much.
Countless tests disagree with you.

---

### Post by SeijiSensei on 2011-04-10
> **Philsoki said:**
> A lot of what you just wrote was related to cases of espionage though... I really don't think I need to worry about secret agents giving me free USB drives.

You missed the point.  USB malware exists because of design decisions in Windows itself.  Windows developers thought it would be a "good thing" if people didn't have to do anything to execute a program on a CD or USB drive because it simplified the user experience.  So they designed a method whereby the operating system automatically runs those programs for you.  

The notion that a program should be able to execute simply because you inserted a device into a drive or USB port is anathema to the way Unix works.  The general philosophy is typically "deny by default" not "enable by default".  That makes *nix systems less "friendly" than Windows systems, if by friendly we mean simplifying the process of running a program contained on a CD or USB drive.  Whether you view the consequences of this decision as "friendly" is another matter entirely.  The cases I describe show how unfriendly that decision can be in practice.

The same logic underpinned the original concept of self-executing ActiveX modules.  Microsoft's enterprise customers wanted a technology that would make it easy to deploy web-based applications to their users' desktops.  Thus was born ActiveX.  It somehow slipped everyone's mind that if an object could be downloaded and executed in the background over the network that creates a vector for delivering both benign and evil applications. 

I trace a lot of these problems back to Windows origin as a single-user operating system.  Windows, like DOS before it, was designed to be run on individual desktops in non-networked environments.  The concept of network threats really didn't have much leverage in a world where network services were largely limited to file and printer sharing via Netware and Netbios.  Computers in the Windows world didn't run "daemons," didn't listen on ports, and generally ignored the other computers on the network around them.  

The Internet broke this model of computing forever. Now every computer was conceivably the peer of both the workstation in the cubicle next door and ones located far across the globe.  Even if the computer were hiding behind a firewall, it was now able to download objects from untrustworthy computers anywhere on the planet.  This was not the world that Windows was designed for, and Microsoft has spent the last twenty years coping with that fact. 

Unix systems, on the other hand, were developed on the assumption of pervasive networking.  They were designed to run daemons and exchange information with other computers.  Programs like sendmail and BIND had already been battered on numerous occasions by the time Windows 95 appeared.  The "[Morris worm]("http://en.wikipedia.org/wiki/Morris_worm")" scared the dickens out of network and system administrators and led to a major round of hardening of services and software.  Windows wasn't touched by any of this at all.

So, for me, what distinguishes these platforms are deep philosophical design issues that reflect the origins of Windows and Unix.  It's hard to talk about this broader perspective when security arguments are largely dominated by fanboyism and based on silly measures like counting "vulnerabilities" as if they were all the same.

---

### Post by Philsoki on 2011-04-10
> You missed the point.  USB malware exists because of design decisions in  Windows itself.  Windows developers thought it would be a "good thing"  if people didn't have to do anything to execute a program on a CD or USB  drive because it simplified the user experience.  So they designed a  method whereby the operating system automatically runs those programs  for you.  
Is this what you mean by the system automatically running a program for me? I just put in this CD now and it didn't run it at all, rather it presented me with a nice interface so that I could choose what I want to do with it next:
[IMG]http://min.us/jkCt3e.bmp[/IMG]

---

### Post by SeijiSensei on 2011-04-10
Yes, except you left out the part about the additional software it might have silently loaded in the background using the [.lnk exploit]("http://blogs.pcmag.com/securitywatch/2010/07/exploit_code_for_windows_lnk_f.php").

You also didn't insert a disk with an executable program on it either it appears.  Try inserting a software installation disc with SETUP.EXE on it. If autorun is not disabled, that program will run when the disk is inserted. 

Finally it turns out [that nice menu can itself be hijacked]("http://en.wikipedia.org/wiki/AutoRun#Issues_and_security") to execute malware even if autorun itself is disabled.

---

### Post by Philsoki on 2011-04-10
> **SeijiSensei said:**
> Yes, except you left out the part about the additional software it might have silently loaded in the background using the .lnk exploit.
I think I'm safe:
```
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Richard>lnk
'lnk' is not recognized as an internal or external command,
operable program or batch file.

C:\Documents and Settings\Richard>search lnk
'search' is not recognized as an internal or external command,
operable program or batch file.

C:\Documents and Settings\Richard>
```;)

Then again, I'd be pretty shocked if the Fedora dev team were trying to infect my Windows install. :D

---

### Post by wolfen69 on 2011-04-10
> **SeijiSensei said:**
> You missed the point.  USB malware exists because of design decisions in Windows itself.  Windows developers thought it would be a "good thing" if people didn't have to do anything to execute a program on a CD or USB drive because it simplified the user experience.  So they designed a method whereby the operating system automatically runs those programs for you.  

The notion that a program should be able to execute simply because you inserted a device into a drive or USB port is anathema to the way Unix works.  The general philosophy is typically "deny by default" not "enable by default".  That makes *nix systems less "friendly" than Windows systems, if by friendly we mean simplifying the process of running a program contained on a CD or USB drive.  Whether you view the consequences of this decision as "friendly" is another matter entirely.  The cases I describe show how unfriendly that decision can be in practice.

The same logic underpinned the original concept of self-executing ActiveX modules.  Microsoft's enterprise customers wanted a technology that would make it easy to deploy web-based applications to their users' desktops.  Thus was born ActiveX.  It somehow slipped everyone's mind that if an object could be downloaded and executed in the background over the network that creates a vector for delivering both benign and evil applications. 

I trace a lot of these problems back to Windows origin as a single-user operating system.  Windows, like DOS before it, was designed to be run on individual desktops in non-networked environments.  The concept of network threats really didn't have much leverage in a world where network services were largely limited to file and printer sharing via Netware and Netbios.  Computers in the Windows world didn't run "daemons," didn't listen on ports, and generally ignored the other computers on the network around them.  

The Internet broke this model of computing forever. Now every computer was conceivably the peer of both the workstation in the cubicle next door and ones located far across the globe.  Even if the computer were hiding behind a firewall, it was now able to download objects from untrustworthy computers anywhere on the planet.  This was not the world that Windows was designed for, and Microsoft has spent the last twenty years coping with that fact. 

Unix systems, on the other hand, were developed on the assumption of pervasive networking.  They were designed to run daemons and exchange information with other computers.  Programs like sendmail and BIND had already been battered on numerous occasions by the time Windows 95 appeared.  The "[Morris worm]("http://en.wikipedia.org/wiki/Morris_worm")" scared the dickens out of network and system administrators and led to a major round of hardening of services and software.  Windows wasn't touched by any of this at all.

So, for me, what distinguishes these platforms are deep philosophical design issues that reflect the origins of Windows and Unix.  It's hard to talk about this broader perspective when security arguments are largely dominated by fanboyism and based on silly measures like counting "vulnerabilities" as if they were all the same.

No they are not all the same, obviously. All I know is, my customers get viruses and I fix. :)

Your use of "deep philosophical design issues" is a good one. Anyway, I'm getting too old to argue about stuff anymore. I enjoyed the read.

---

### Post by SeijiSensei on 2011-04-10
Did you actually read any of the articles I linked to?  It doesn't sound like you did.

---

### Post by Philsoki on 2011-04-10
> **SeijiSensei said:**
> Did you actually read any of the articles I linked to?  It doesn't sound like you did.
No, I didn't. Could you please quote anything relevant from them?

---

### Post by 3rdalbum on 2011-04-10
> **Philsoki said:**
> Is this what you mean by the system automatically running a program for me? I just put in this CD now and it didn't run it at all, rather it presented me with a nice interface so that I could choose what I want to do with it next:
[IMG]http://min.us/jkCt3e.bmp[/IMG]

Click "Always do the selected action" and see how safe your computer stays :-P

---

### Post by Philsoki on 2011-04-10
> **3rdalbum said:**
> Click "Always do the selected action" and see how safe your computer stays :-P
It's all about choice, you see. And to be honest, it would be quite safe if I did. Oh no! My computers printing a virus! Oh no, don't view all those images, they might contain hidden scripts that will hijack my system! Oh no, don't open that folder and *view* my files I might actually double click a virus I downloaded! ;)

---

### Post by tgm4883 on 2011-04-10
> **Philsoki said:**
> What I mean is... Can you link me to a webpage that will automatically download and install a virus onto my computer?

Yes I could, I won't though.

Here are two writeups for one's I've run across in the past.

[http://en.wikipedia.org/wiki/Conficker](http://en.wikipedia.org/wiki/Conficker)
[http://www.symantec.com/security_response/writeup.jsp?docid=2009-050707-0639-99](http://www.symantec.com/security_response/writeup.jsp?docid=2009-050707-0639-99)

---

### Post by Philsoki on 2011-04-10
> **tgm4883 said:**
> Yes I could, I won't though.

Here are two writeups for one's I've run across in the past.

[http://en.wikipedia.org/wiki/Conficker](http://en.wikipedia.org/wiki/Conficker)
[http://www.symantec.com/security_response/writeup.jsp?docid=2009-050707-0639-99](http://www.symantec.com/security_response/writeup.jsp?docid=2009-050707-0639-99)
I don't mind if you want to link me to one via private message. In fact, I invite you to. Don't worry about any potential harm to my computer. All my files are safely backed up, and my Antivirus, Firewall, etc are all up-to-date. Please, go ahead and link me.:)

---

### Post by Johnsie on 2011-04-10
Most servers that get hacked are Linux servers.

---

### Post by my mother's pc on 2011-04-10
> **Johnsie said:**
> Most servers that get hacked are Linux servers.

Not judging by the machines that myself and most of my colleagues have to fix and maintain on an everyday basis. 

What type of server are you referring to (web/print/file etc)? 

Is this from your own experience or that of others (anecdotal)?

Do you have any definative proof of what you say (and no, I don't meant the reports and surveys that are sponsored by Microsoft, Apple or anybody else for that matter)?

It's a slow Sunday and I could do with a good read. 

I am sure it would also make good reference material for the people that I work with.

---

### Post by tgm4883 on 2011-04-10
> **Philsoki said:**
> I don't mind if you want to link me to one via private message. In fact, I invite you to. Don't worry about any potential harm to my computer. All my files are safely backed up, and my Antivirus, Firewall, etc are all up-to-date. Please, go ahead and link me.:)

Sorry won't do it. It's unethical and I'd probably be fired.

---

### Post by Philsoki on 2011-04-10
> **tgm4883 said:**
> Sorry won't do it. It's unethical and I'd probably be fired.
It's not unethical. All my files are backed up, you'd be doing me no harm at all. And why would you be fired for linking me to a virus freely available on malicious sites all over the internet? Why should your employer care what you do in your own time from your personal computer at home?

I'm calling you out. You don't know of a virus that will automatically install itself on my Windows machine while I'm browsing a webpage.

---

### Post by LowSky on 2011-04-10
> **Philsoki said:**
> I'm calling you out. You don't know of a virus that will automatically install itself on my Windows machine while I'm browsing a webpage.
 
Maybe he works for a company that makes viruses that supposedly install themselves just by looking at them


:popcorn:

---

### Post by Johnsie on 2011-04-10
> Do you have any definative proof of what you say (and no, I don't meant the reports and surveys that are sponsored by Microsoft, Apple or anybody else for that matter)?


Sure, here's some government statistics:

[http://www.ic3.gov/media/annualreport/2008_IC3Report.pdf](http://www.ic3.gov/media/annualreport/2008_IC3Report.pdf)


Some trends reports by antihphising.org:
[http://www.antiphishing.org/phishReportsArchive.html](http://www.antiphishing.org/phishReportsArchive.html)

And also some reports by the Computer Security institute:
[http://gocsi.com/members/reports](http://gocsi.com/members/reports)


There's quite alot there, so enjoy the read :-)

Windows desktop users are usually the targets, but Linux servers are often attacked to help spread the malware. This is because most web servers run Linux and the web browsers are the easiest things to exploit on the Windows desktop. That's why most servers that get hacked are Linux ones. There are more of them ;-)

---

### Post by tgm4883 on 2011-04-10
> **Philsoki said:**
> It's not unethical. All my files are backed up, you'd be doing me no harm at all. And why would you be fired for linking me to a virus freely available on malicious sites all over the internet? Why should your employer care what you do in your own time from your personal computer at home?

I'm calling you out. You don't know of a virus that will automatically install itself on my Windows machine while I'm browsing a webpage.

Call me out all you want. I don't need to link you to a page that does that, I linked you to two articles discussing two specific threats that do exactly what I have been saying.

> **LowSky said:**
> Maybe he works for a company that makes viruses that supposedly install themselves just by looking at them


:popcorn:

No, I work for and support an AntiVirus product

---

### Post by SeijiSensei on 2011-04-10
> **Johnsie said:**
> [http://www.ic3.gov/media/annualreport/2008_IC3Report.pdf](http://www.ic3.gov/media/annualreport/2008_IC3Report.pdf)

Searching via Okular, the word "linux" does not appear in that document.

> Some trends reports by antihphising.org:
[http://www.antiphishing.org/phishReportsArchive.html](http://www.antiphishing.org/phishReportsArchive.html)

I read the 2010-Q2 report.  Again, a search of that document fails to find the word "linux."

Also the US is reported as hosting the most phishing sites.  Do you suppose that's because web servers in the US are more likely to be compromised than web servers in other countries, or because the US hosts more web servers overall?

The same argument would apply to Linux.  Even if it's true that there are more compromised Linux web servers than Windows web servers, there are many more Linux servers hosting web sites.  You even say so yourself:

> That's why most servers that get hacked are Linux ones. There are more of them

A more relevant comparison would be the conditional probability of a server being compromised given that it runs Linux versus the same conditional probability given that it runs Windows.  Got any data for that?

> And also some reports by the Computer Security institute:
[http://gocsi.com/members/reports](http://gocsi.com/members/reports)

Searching that site for "linux" brings up one article that has something to do with Twitter.  

Want to try again?

---

### Post by Johnsie on 2011-04-10
Try looking at the graphs or actually reading the article... 'Images' tend not to come up in 'word' searches ;-)

ps. There's no way you could've read the hundreds of articles on those sites in such a short time ;-)

---

### Post by SeijiSensei on 2011-04-10
> **Johnsie said:**
> Try looking at the graphs or actually reading the article... 'Images' tend not to come up in 'word' searches ;-)

ps. There's no way you could've read the hundreds of articles on those sites in such a short time ;-)

Well, I read the entire top report on the anti-phishing site, [http://www.antiphishing.org/reports/apwg_report_q2_2010.pdf](http://www.antiphishing.org/reports/apwg_report_q2_2010.pdf), and Linux doesn't appear in the graphs either.  Since it's the most recent summary report from that project, one would think it would include whatever comparisons of phishing vulnerabilities by OS that organization made.

Rather than trolling, why don't you point to one or more specific document(s) that support your claim?

---

### Post by youbuntu on 2011-04-10
Windows XP _is_ spyware itself. It's hardly going to report itself as malware, is it! :lol:

---

### Post by Quadunit404 on 2011-04-10
> **glossywhite said:**
> Windows XP _is_ spyware itself. It's hardly going to report itself as malware, is it! :lol:

[[citation needed]]

---

### Post by beew on 2011-04-10
> **Philsoki said:**
> I don't think the OP is telling the full story. If Windows was that bad it wouldn't be usable, no one would use it.

I installed Windows XP SP3 today and haven't had any trouble. It's beyond me how they were able to get a virus visiting six websites. No offense, the only reason you can get a virus on Windows is if you put it on there yourself. 

It's why Windows users always get viruses, because they run .exe files without thinking.
"Oh hey, this website scanned my computer and it seems I have viruses, but no worries because they've given me a free Antivirus.exe to download - Just double click and install!"

Sorry, but posts like this annoy the hell out of me.

/rant


Well if you are unlucky enough you can get hosed even by visiting only "safe sites". I am now typing from a HP netbook that I am trying to restore. It belongs to this neighbour who pretty much just uses the computer for Youtube and Livejourna (with Vista). About a week ago her computer was disabled because the LiveJournal site suffered a DDOS attack apparently by the Russians and anyone who logged in at the time (with Windows) was toasted. 

[http://www.gmanews.tv/story/217366/technology/ddos-cyberattack-on-livejournal-enrages-russian-president](http://www.gmanews.tv/story/217366/technology/ddos-cyberattack-on-livejournal-enrages-russian-president)

Now the virus is gone, just need to restore the registry entries so she can actually open a file or program (apparently the malware changed the registry so that whatever she clicked some popup appeared telling her to buy anti-virus. After the malware was removed all the modified registry entries got removed too, leaving no file association at
all)

---

### Post by goscuter1 on 2011-04-11
> **earthpigg said:**
> are we really having an argument about which antivirus is the best?

here, ill throw my $0.02 in:

whichever one spends the most resources on incentivising malware creation. for many reasons, that will be the best one.

Thank you for saving my sanity. I am quite certain if I went 9 pages without someone stating the bleeding obvious, I would have had to stop reading the Internet. 

Anyone who can't seem to draw a connection between Supply and the creation of Demand for a Product...man, yall didn't go to school? What is this, like grade 9 Economics? 

Come on yall, wake up yeah...

---

### Post by goscuter1 on 2011-04-11
> **Originally Posted by Spr0k3t  **
To disinfect use this:
Safemode:
- Malwarebytes

Notsosafemode:
- Malwarebytes 


...on a random occasion it's not possible to fix networking issues and requires a complete rebuild. An alternate permanent fix is to install Linux and ditch Microsoft.

*Quote snipped for brevity.* You're 100% correct about the networking vulnerabilities and 100% correct about them being simply impossible to fix. Once you have unattended installations being deployed...it's game over. Entire systems rebuild is the only solution. I've low-level formatted with DBAN and KillDisk back-to-back, rewrote the MBR, flashed the BIOS, formatted with a Linux rescue CD and installed Ubuntu and Mint. Nup...entirely new systems is your only shot. 

Where I think you (and the entire AV community) are wrong though, is for the widespread love of Malwarebytes. Piece of joke imo, it's never detected anything on my systems - whilst ComboFix and OTL are screaming about detected Rootkits and empty "run once" registry keys. 

This is Malwarebytes for you, cute little silent patched reinstall (the unpatched legit version was useless anyway):

[http://i.imgur.com/A6JDQ.png](http://i.imgur.com/A6JDQ.png)

All the AV 'solutions' (with the sole exception of RegRun, who aren't a 360 degree solution by any means) are the primary writers of the malware code they then sell you the 'solutions' for. I picked up this little BSOD'ing corrupting procexp113.sys file from [http://technet.microsoft.com/en-us/sysinternals](http://technet.microsoft.com/en-us/sysinternals) (who ostensibly have a good name, but I learned there are no good names in the AV industry - and why would there be, it's an industry where "moral hazard" gets redefined) - whichever AV 'solution' detects the most threats, is deemed the 'best'. There's a few ways you can make your 'solution' pretty good at detecting threats....

[http://i.imgur.com/11LtA.jpg](http://i.imgur.com/11LtA.jpg)

> **Originally Posted by SeijiSensei ** 
You missed the point. USB malware exists because of design decisions in Windows itself. Windows developers thought it would be a "good thing" if people didn't have to do anything to execute a program on a CD or USB drive because it simplified the user experience. 

The same logic underpinned the original concept of self-executing ActiveX modules. Microsoft's enterprise customers wanted a technology that would make it easy to deploy web-based applications to their users' desktops. Thus was born ActiveX. It somehow slipped everyone's mind that if an object could be downloaded and executed in the background over the network that creates a vector for delivering both benign and evil applications. 

I trace a lot of these problems back to Windows origin as a single-user operating system. Windows, like DOS before it, was designed to be run on individual desktops in non-networked environments. The concept of network threats really didn't have much leverage in a world where network services were largely limited to file and printer sharing via Netware and Netbios. Computers in the Windows world didn't run "daemons," didn't listen on ports, and generally ignored the other computers on the network around them. 

So, for me, what distinguishes these platforms are deep philosophical design issues that reflect the origins of Windows and Unix. It's hard to talk about this broader perspective when security arguments are largely dominated by fanboyism and based on silly measures like counting "vulnerabilities" as if they were all the same.

This guy is laying down nuggets of purified TRUTH and I've yet to see a single sentence he's written in this thread which hasn't been bang on the money. He's a bit more diplomatic than I'm willing to be, philosophical design issues? hmm I have a less generous take on it all... 

What it really boils down to is SHEER FILTHY GREED combined with that most dangerous of all additives, unfathomable incompetence. 

People have NO IDEA how many exploitabilities are pre-packaged and launched active by default in their home Windows systems. Hacker capabilities increased exponentially with Active Directory. But there's just no f justifiable reason for no-prompt install function - which is really what creates all the problems, SILENT unattended deployment. 

That's not even getting into the smorgasbord of attack vectors, which are SIMPLY UNNECESSARY for home users not running Virtual Drives, not deploying remote system images, who have no real use for Junction points, or sneaky subtle "library" dynamic links or hardlinks, home users who couldn't possibly ever want to upload recovery files hidden / virtual partitions and offline registry hives, or trigger entire system images from hidden, encrypted dynamic disks remotely. Just a few kb of code stored innocuously in some undetectable hidden virtual, encrypted partition or even on your hardware somewhere - it doesn't have to be on your hard drive, everything is SATA now. It's ridiculous. 

Microsoft patches for the IDIOTIC vulnerability which is Active signed content, have been released going as far back as 1999. This should give you a clue about how moronic these people really are. It's quite literally criminal, it's staggering. 

[http://www.microsoft.com/technet/sec.../ms00-042.mspx]("http://www.microsoft.com/technet/sec.../ms00-042.mspx")

> **Why is Microsoft-signed content trusted by default?** 

By design, Microsoft-signed files are trusted by default. At first blush, this would seem appropriate - after all, the user has chosen to install a Microsoft product, so they've already made the decision to trust the content that Microsoft provides. 

The security problem this raises is that there's nothing to prevent other people from hosting Microsoft-signed files (after all, Microsoft-signed files are freely available from various pages on the Microsoft web site) and using them inappropriately.

Yes, Microsoft. The person asking the question would already know that - which is why he's asking the QUESTION YOU DID NOT ANSWER. 

I mean, is this for real? Trusting someone in 1999, doesn't mean you trust them for...ever? No one is this stupid. 

But it's okay, because 11 years ago, they fixed it!

> **What is Microsoft doing about this issue?**

Microsoft has developed a procedure that eliminates the vulnerability.

Um pretty sure the only thing that can eliminate the vulnerability..is ELIMINATING the vulnerability that is silent deployment of Active signed code. 12 years on, more and more patches being released. This is not philosophical differences, this is criminal greed and control causing this. 

But it's okay, because they have System File Checker and WFP. The problem with those two trojan horses is if you're facing unattended installations, WFP is your enemy when any attempt to replace the system files is deemed by WFP to be an unauthorised installation. Cute. I'm an idiot so it took me a fortnight of SFC /scannow cleaning of corrupted files, only for the WFP to silently corrupt them all again with the 'correct' system files...before I finally figured it out. My Genuine Advantage OS was 'corrupting' the unattended silent deployments of OS's I had the nerve to want to replace. WFP put paid to my attempts to hack my own systems!

As for SFC, lol. When command lines don't function...well, it's time for Linux I guess. [SFC /verifyonly - oh.really?]("http://i.imgur.com/0vYYA.png")

When I first reported the issue to the philosophical Microsoft techs, and uploaded the screenshot evidence successfully to the Microsoft secure server, they claimed they didn't receive anything and accused me of making it up, telling me to call the "Cyber Cops" to report this huge crime. lol. This is despite my showing them the evidence that they did receive the images, which were also emailed (of course). [lol_Microsoft]("http://i.imgur.com/P3EJw.png")

> You: DELL installed a brand new HDD a week ago after my BITLOCKER and Dell's TPM conspired to destroy my encrypted hard drive. 
Supervisor_Jaykrishnan: May be then the Hacker has taken over the Bios too
You: Yes, I believe he has, but I can't flash him out. so lol at Microsoft when BITLOCKER is useless, and MS Security Essentials is laughed at by the rootkit, which patches MSSE with a yawn, and Genuine Advantage cannot format the drive. 
You: Can you do....ANYTHING?
Supervisor_Jaykrishnan: Okay I wonder how even after that advanced conspiracy using the High level TPM chips installed your Computer was prone to Hack
Supervisor_Jaykrishnan: (Smiles)
You: are you seriously trying to be...cute? hours after I've shipped you the evidence, and demanded to know how reclaim my systems? 
Supervisor_Jaykrishnan: Okay i think we should put an end to this, if you think the Hacker is way too out of control even after reformatting your HDDs and is able to gain access using advanced conspiracy with the help of BIT Locker and MSSE the only way out is go Bust that Hacker! 
Supervisor_Jaykrishnan: so You should be contacting the Cybercrime department and not Microsoft.
You: Are you freaking serious? Check your email!
Supervisor_Jaykrishnan: You have been saying the same thing and why dont you forward your evidence again?
You: CHECK YOUR EMAIL. Can you read? I UPLOADED THE IMAGES TO MICROSOFT SECURE SERVER - I HAVE SHOWN YOU EVIDENCE OF THAT FACT
You: now stop embarrassing yourself, it's disgraceful. 
Supervisor_Jaykrishnan: Okay this is My official warning - you use profanity again on this chat you will be disconnected. Your case needs immediate attention by Cybercops and not Microsoft Engineers. 
You: You're a f**king disgrace to humanity.
**chat disconnected**

Philosophical differences.

---

### Post by sdowney717 on 2011-04-11
> Well if you are unlucky enough you can get hosed even by visiting only "safe sites". I am now typing from a HP netbook that I am trying to restore. It belongs to this neighbour who pretty much just uses the computer for Youtube and Livejourna (with Vista). About a week ago her computer was disabled because the LiveJournal site suffered a DDOS attack apparently by the Russians and anyone who logged in at the time (with Windows) was toasted.


Honestly, we went no where people would think of as unsafe.
Avast notified us of a threat, I clicked on the threat link URL in the Avast warning popup to read about the threat. Perhaps that is what did it.
The poster who mentioned simply closing the warning malware popup can install malware is right IMO. I do think if he had been using a recent copy of Firefox or Chrome instead of IE6 it might have had a different outcome.

Windows PC and DOS attacks are due to the massive numbers of PC infected machines running BOTNETS, controlled by highly organized criminal types or governments.
The most successful Botnets will be the ones where the owners are unaware that MS windows is infected.
 [http://en.wikipedia.org/wiki/Botnet](http://en.wikipedia.org/wiki/Botnet)

the AV makers are empowered by the MS Window makers and the government spyers want backdoors into the os. And business and governments want to track your every move. The whole computerized industrial complex of security is rigged to force people to keep upgrading, spending money and time or your overcome and drowned by malware. Peoples PC get slowed down by this burden of malware and think they need a faster PC, better and more secure PC and the thing just keeps on rolling.

botnet growth from 2008
[http://cyberinsecure.com/infected-machines-in-botnets-quadrupled-in-last-3-months/](http://cyberinsecure.com/infected-machines-in-botnets-quadrupled-in-last-3-months/)
[http://cyberinsecure.com/malware-infected-computer-botnets-click-fraud-at-record-high/](http://cyberinsecure.com/malware-infected-computer-botnets-click-fraud-at-record-high/)

---

### Post by sdowney717 on 2011-04-11
[http://news.bbc.co.uk/2/hi/business/6298641.stm](http://news.bbc.co.uk/2/hi/business/6298641.stm)
Most vulnerabile OS is MS based windows
Ironic that windows success as a mass consumer OS is so plagued with vulnerabilities that it could ruin internet's future.
 
> Criminals controlling millions of personal computers are threatening the internet's future, experts have warned.

**Up to a quarter of computers on the net** may be used by cyber criminals in so-called botnets, said Vint Cerf, one of the fathers of the internet. 

> The expert panel, among them Michael Dell, founder of Dell computers, and Hamadoun Toure, secretary general of the International Telecommunication Union, agreed that a solution had to be found to ensure the survival of the web.

But its members were unsure about feasible solutions, even though they **identified operating systems and authentication as key issues**. 

> Of the 600 million computers currently on the internet, between 100 and 150 million were already part of these botnets, Mr Cerf said. 

---

### Post by el_koraco on 2011-04-11
> **sdowney717 said:**
> 
Avast notified us of a threat, I clicked on the threat link URL in the Avast warning popup to read about the threat. Perhaps that is what did it.[]("http://cyberinsecure.com/malware-infected-computer-botnets-click-fraud-at-record-high/")


yup, taht's what it was, except for the fact that it wasn't avast informing you, but a trojan. the famous antivirus scam. the next time this happens, don't click on the popup, go to the task manager (crtl alt del), and end the browser process.

---

### Post by ikt on 2011-04-11
> **sdowney717 said:**
> Ironic that windows success as a mass consumer OS is so plagued with vulnerabilities that it could ruin internet's future.

[http://www.zone-h.com/news/id/4737](http://www.zone-h.com/news/id/4737)

---

### Post by Tristam Green on 2011-04-11
[www.bleepingcomputer.com](www.bleepingcomputer.com)


use it for all those rogue antimalware program woes.

---

### Post by sdowney717 on 2011-04-11
> yup, taht's what it was, except for the fact that it wasn't avast informing you, but a trojan. the famous antivirus scam. the next time this happens, don't click on the popup, go to the task manager (crtl alt del), and end the browser process.

interesting idea that the malware perhaps mimicked an Avast warning.
I have seen Avast popup a warning before and I just assumed it was another Avast popup warning. This warning did not sound any audible alarm. but who knows.

The friend who owns this PC is a senior Java developer familiar with UNIX, Linux and windows with 30 years of varied programming experience which started with NASA.  BUT he is also so busy he has little time to put into his own home PC's. I convinced him 3 years ago how Linux for the desktop was a good choice and he is a definite believer today. SO our plan is to install Ubuntu on this PC and run XP in a VM as he has to log into his work based windows system using a specialized Cisco VPN program which does not work in Linux.

His other home PC has run Ubuntu for 2 years and never has much go wrong with it.

---

### Post by el_koraco on 2011-04-11
that particular scam has been in the works for some years now. it's the standard example of exploiting the famous activex controls. i remember having had these issues years ago, when i got xp with IE6 preinstalled. the trojans do look rather similar to the real antivirus programs, and when you're casually browsing the web, feeling secure, because you got yourself some high end antivirus "protection", you don't even question the warning. from then on, things can go belly up rather soon. and no, it doesn't just happen to noobs and grannies.

---

### Post by goscuter1 on 2011-04-16
> **el_koraco said:**
> that particular scam has been in the works for some years now. it's the standard example of exploiting the famous activex controls. i remember having had these issues years ago, when i got xp with IE6 preinstalled. the trojans do look rather similar to the real antivirus programs, and when you're casually browsing the web, feeling secure, because you got yourself some high end antivirus "protection", you don't even question the warning. from then on, things can go belly up rather soon. and no, it doesn't just happen to noobs and grannies.

There's also a MS Hotfix exploitability which I reported to Microsoft and they blew me off. I got sucked in by that one pretty good early on, multiple times, as it just seems so innocuous and slides into your Windows Update gazillion patches and updates after reinstalling Win7. If you're unaware you're running a unattended OS, silently deployed when you believed you were installing from your Genuine Advantage discs, some of the very first Windows Update downloads will be obscure Microsoft Hotfixes from 2007 and whatnot. Why, or how they're used by hackers with my system, I couldn't say. And I couldn't care less. 

All I know is that if Windows Update is downloading a 2007 Hotfix which the accompanying instructions from Microsoft instruct that the hotfix should not be downloaded unless users are having trouble with filtering dll's or Remote Procedure Calls...then I know that it's not legitimate.  

Therefore it's malicious. 

Therefore it's a problem. 

But this industry is full of people who - if they don't know something, or can't explain unexplainable Microsoft-related activity, they'll just shrug as if it's not a problem. They'll ignore the bleeding fact that if something is unexplainable, it's a problem. They'll shrug and say "oh just Microsoft, one of those thigns" and they'll spend weeks trying to find a workaround. Which is a stupidity so generic, I was flabbergasted upon my first exposure to it this industries Windows 'experts' on their forums of collective expert idiots.  

If no one can explain something, or explain it's function, or what caused it...it's not mere incompetence. It's a huge problem which must be DEMANDED by answered by Microsoft and solved. Until then, it's an exploit being used by those who are smarter than Microsoft (which isn't saying much) and smarter than people like me (who herd goats in pleasant Tibetan fields).

---

### Post by goscuter1 on 2011-04-16
But back on Topic =D> how amazing is Ubuntu 11.04. 

I mean, seriously. If it was a girl (even with all it's Beta bugs), I half think I might have a little crush, and may even flirt with it so more - if I can find the courage to man up and get some game.

So sexy. A sexy sexy distribution, in my opinion.

---

### Post by CharlesA on 2011-04-16
> **goscuter1 said:**
> There's also a MS Hotfix exploitability which I reported to Microsoft and they blew me off. I got sucked in by that one pretty good early on, multiple times, as it just seems so innocuous and slides into your Windows Update gazillion patches and updates after reinstalling Win7. If you're unaware you're running a unattended OS, silently deployed when you believed you were installing from your Genuine Advantage discs, some of the very first Windows Update downloads will be obscure Microsoft Hotfixes from 2007 and whatnot. Why, or how they're used by hackers with my system, I couldn't say. And I couldn't care less. 

All I know is that if Windows Update is downloading a 2007 Hotfix which the accompanying instructions from Microsoft instruct that the hotfix should not be downloaded unless users are having trouble with filtering dll's or Remote Procedure Calls...then I know that it's not legitimate.  

Therefore it's malicious. 

Therefore it's a problem.

So your clean install of Windows 7 is compromised by windows update? What hotfix in particular?

---

### Post by el_koraco on 2011-04-16
> **goscuter1 said:**
> But back on Topic =D> how amazing is Ubuntu 11.04. 



Feeling the same way here, but for Kubuntu 11.04.

---

### Post by neu5eeCh on 2011-04-16
> **goscuter1 said:**
> But back on Topic =D> how amazing is Ubuntu 11.04. 

I mean, seriously. If it was a girl (even with all it's Beta bugs), I half think I might have a little crush, and may even flirt with it so more - if I can find the courage to man up and get some game.

So sexy. A sexy sexy distribution, in my opinion.

Yeah, but she's not the girl you used to know. This one won't let you mess with her clothes. She's got her own fashion sense and if you don't like it, take a hike.

---

### Post by el_koraco on 2011-04-16
well, from what i gather, the girl he used to know was inviting her other boyfriends to his house all the time :D

---

### Post by neu5eeCh on 2011-04-16
> **el_koraco said:**
> well, from what i gather, the girl he used to know was inviting her other boyfriends to his house all the time :D

Better than that other minx, the one who charges. :lolflag:

---

### Post by goscuter1 on 2011-04-16
> **CharlesA said:**
> So your clean install of Windows 7 is compromised by windows update? What hotfix in particular?

It was, happened with this Hotfix only once (but the Hotfix issue was occurring with different Hotfix's multiple times during my 40 or so reformat, Genuine Advantage Win7 Ultimate 'clean' installs). This one was on a DBAN'd hard drive, and after a few MSSE (patched of course) instant Windows Update automated installs (since when is MSSE the first Update off the rank, EVER - let alone a patched one which prevented any other AV software from being installed, as the rogue MSSE service was grayed out, and impossible to adjust let alone kill, even when logged in as Super Administrator), I very consciously clicked "NO" when given the option to download Windows Updates during the clean installation. 

I almost fell off my chair when, the second I went online, even though it had been deactivated, Windows Update started automatically downloading Security Updates which seemed harmless enough? (except for the fact that Windows Update was deactivated - and then I Googled the command line). And saw a Hotfix which couldn't be legit for the reason that I not only didn't have any of the 3 problems to which it addressed, I had never heard of WUSA and certainly did not wish to deploy Forefront Endpoint Protection which I'd never heard of, and in all honesty, I'm so dull I didn't even comprehend the nature of the word "deploy" until a month later. No thanks to the industry idiots posing as experts, who kept running me through endless Malwarebytes time-wasting, and declaring my systems clean, even though they were shown a whole stack of evidence suggesting it was anything but.  

This is the 3 Updates installed literally the second I went online, whilst Windows Update was completely deactivated: [http://i.imgur.com/Lm6uo.png](http://i.imgur.com/Lm6uo.png)

I looked in the Event log to try and make sense of it and saw the Hotfix had been installed by a command: [http://i.imgur.com/kMPmj.png](http://i.imgur.com/kMPmj.png)

This is the Google search of the command line in the screenshot above: [http://i.imgur.com/skZ1g.png](http://i.imgur.com/skZ1g.png) So frustrating that if I only knew a tiny bit, and understood the first thing about Windows server deployment (the thought had literally never crossed my mind), I would have recognised from that Google results list that I didn't want my systems to be silently 'protected' without my authorisation using Forefront Endpoint Protection - and I could have saved 2 months tilt right there. But all I knew was that a dozen Google hits was very odd, and forwarded it all to Microsoft asking what to do. And posted on forums, where 'experts' pretending to have a clue, simply ignored it (and the MOUNTAINS of other evidence I submitted) because that's what Windows 'experts' do when they don't know squat. They say it's fine. Or they go silent. It's despicable.  

I first tried to work out what WUSA was and immediately knew it wasn't cool (aside from the fact that I'd never heard of it, and my lifetime experience with cmd was limited to trying to deactivate the rogue MSSE from a SuperUser Administrator elevated prompt):

> 

You can use the following switches together with Wusa.exe:

[LIST]
[*]**/quiet**
Run  Wusa.exe in quiet mode without user interaction. When the tool runs in  quiet mode, it runs without user interaction. The computer restarts if  it is required.

For example, if the Windows6.0-KB934307-x86.msu file is in the   D:\934307 folder, type the following command at a command prompt to install the update package without user interaction: wusa.exe d:\934307\Windows6.0-KB934307-x86.msu /quiet
**Note**  When you use this switch, the Microsoft Software License Terms do not appear.
[/LIST]
\\:D/ Microsoft just helping out the hackers of the world. Ain't no thang. I'm sure some lazy systems administrators are happy also. Good for them!

I knew the Hotfix itself was messed up, as I looked it up and the symptoms weren't remotely relevant:

[http://support.microsoft.com/kb/981889](http://support.microsoft.com/kb/981889)

> This hotfix rollup  package fixes the Windows Filtering Platform (WFP) driver issues that  are described in the following Microsoft Knowledge Base (KB) articles:

[976759]("http://support.microsoft.com/kb/976759")                               WFP drivers may cause a failure to  disconnect the RDP connection to a multiprocessor computer that is  running Windows Vista, Windows Server 2008, windows 7 or Windows Server  2008 R2[INDENT][COLOR=Red]In this scenario, you log on to and log off from the computer by using a  Remote Desktop Protocol (RDP) connection. [/COLOR]However, if you log on to and  log off from the computer many times, the RDP connection may not be  disconnected successfully.  Therefore, when you try to log on to the  computer again , you may receive an error message that resembles the  following:     
Another session is busy disconnecting 


[/INDENT][979278]("http://support.microsoft.com/kb/979278")                               Using two Windows Filtering Platform (WFP)  drivers causes a computer to crash when the computer is running Windows  Vista, Windows 7, or Windows Server 2008[INDENT] [COLOR=Red]You install two third-party Windows Filtering Platform (WFP) callout  drivers.[/COLOR] In this scenario, the computer may crash and you receive a Stop  error message on a blue screen  when you use these drivers. Sometimes,  this issue occurs before you log on to the computer.[/INDENT][979223]("http://support.microsoft.com/kb/979223")                               A nonpaged pool memory leak occurs when you  use a WFP callout driver in Windows Vista, Windows 7, Windows Server  2008, or in Windows Server 2008 R2[INDENT][COLOR=Red]You install an application that uses a Windows Filtering Platform (WFP)  callout driver. [/COLOR]After the application is running for some time, a memory  leak may occur in the nonpaged pool memory. In this situation, you may  experience low performance on the computer.
[/INDENT]**Hotfix information**

  A supported hotfix is available from Microsoft. However,[COLOR=Red] this hotfix is  intended to correct only the problem that is described in this article.  Apply this hotfix only to systems that are experiencing the problem  described in this article.[/COLOR] This hotfix might receive additional testing. [COLOR=Red] Therefore, if you are not severely affected by this problem, we  recommend that you wait for the next software update that contains this  hotfix.[/COLOR]To my layman eyes, this looked pretty much smoking gun stuff. This is a fresh Genuine Advantage installation on a low-level formatted HDD, I looked up Remote Desktop Protocol and didn't like the sound of that. I'd installed nothing but Windows 7 Ultimate so...the next two were negated. 

With the only severe effect being the unauthorised Hotfix download and install whilst Windows Update was deactivated, I decided I had a problem, and went to Microsoft. 

hahahaahha

I provided all this, and MUCH MUCH more to Microsoft. Uploaded to their Secure https support link, and sent by email. 

And I have the screenshot evidence of them claiming they didn't receive it. And calling me a liar, to my face. Which is funny, cause they kept calling me a liar and kept claiming 'technical problems' were preventing their viewing of successfully emailed and uploaded files, the more I sent them successfully, the more they called me a liar and insulted me. 

It was really rather cute, **our psychological differences**, in that regard.* (edit: dammit, I meant **philosophical **differences - I ruined my only decent line, noose. Our psychological differences were pretty notable, as well. Had they not been protected by my computer screen, and the ether, there would be some other notable differences, but alas...)*

> **VTPoet said:**
> Yeah, but she's not the girl you used to know. This one won't let you mess with her clothes. She's got her own fashion sense and if you don't like it, take a hike.

I like her fashion sense, though. She's got causal style - not afraid to let her hair down and coyote dance the bar, but perfectly comfortable in formal dinner wear, turning heads. I'm just afraid she'll tell me to take a hike, cause that's what normally happens....

> **el_koraco said:**
> well, from what i gather, the girl he used to know was inviting her other boyfriends to his house all the time :D

Jesus christ. I'm so tired, I read your post and thought "**WTF which one of my friends is this!!**". Failing to realise you were talking about an Operating System. I've probably given a bit too much info out there. Let's just ignore that....whoa that was a bit spooky. And for the record, only Windows is worse than her, in that regard. ubuntu has some catching up to do, in the indiscretion stakes...

But it's all good. ubuntu 11.04 and I are in <3. She's the one. I hear wedding bells that only the Chrome OS might threaten....

---

### Post by MasterNetra on 2011-04-16
I use comodo Internet Suite (minus geekbuddy at install of course) and my own brain as well plus I go disable things like terminal services (which is just asking to get hacked from),remote registry and remote login, and such things. Restore cd, though, disables services like messenger (which IS NOT instant messenger chat app) as well as some other things by default.
It Usually runs fine. I also frequently run ccleaner too keep registry tidy as well as having disabled system restore which is useless really.

---

### Post by el_koraco on 2011-04-16
> **goscuter1 said:**
> She's the one. I hear wedding bells that only the Chrome OS might threaten....

You do know that Chrome OS is Ubuntu based, right? There's more than one "cloud" OS out there. After you take some time recovering from the Windows ordeal, do take a look at KDE. It's like rediscovering the computing world all over again.

---

### Post by goscuter1 on 2011-04-17
> **MasterNetra said:**
> I use comodo Internet Suite (minus geekbuddy at install of course) and my own brain as well plus I go disable things like terminal services (which is just asking to get hacked from),remote registry and remote login, and such things. Restore cd, though, disables services like messenger (which IS NOT instant messenger chat app) as well as some other things by default.
It Usually runs fine. I also frequently run ccleaner too keep registry tidy as well as having disabled system restore which is useless really.

Your comment about Geekbuddy makes me think I was out of the loop somehow. I paid those jokers. I'm such a sucker for confident, outlandish claims...

[IMG]http://i.imgur.com/EgknT.png[/IMG]


Disabling System Restore (which is a joke as you quite rightly point out) was only realised by me far too late in the carnage to be of much use. I think I had decided to install ubuntu the same day I figured out something about System Restore was suspect. Probably the fact that I couldn't delete some suspiciously dated restore points, even with Super user Administrator elevation. 

But as someone pointed out earlier in the thread, just because Windows is running fine doesn't mean...you know? I am computer illiterate, always have been - I used Windows for 8 years without really ever having a virus issue once (just by not ever opening on idiotic chain mails and whatnot). 

But when you're hit, on one of the new attack vectors....there's no solution. 

New systems. Entirely new systems = **only solution.** Of course I'm talking about non-ridiculous malware coders, not the guys who write Microsoft's Top Virus Threats (lol):

**actual email exchange with MS Tech support**

> [INDENT]GMER 1.0.15.15530 - [http://www.gmer.net]("http://www.gmer.net/")
 Rootkit scan 2011-02-11 11:08:47
 Windows 6.1.7600  
 Running: ghsbq0fs.exe
 
 
 ---- Services - GMER 1.0.15 ----
 
 Service  C:\Windows\servicing\TrustedInstaller.exe (*** hidden *** )  [AUTO] TrustedInstaller   <-- ROOTKIT !!!
 
 ---- EOF - GMER 1.0.15 ----
[/INDENT][FONT=georgia]Microsoft, this is ridiculous. What am I supposed to do here, aside from rant in hypercolour language and swear off Windows for life? [/FONT][COLOR=#1F497D][COLOR=#000000][FONT=georgia,serif]
[/FONT][/COLOR] 
-------------
[/COLOR] [COLOR=Blue]
[/COLOR] [COLOR=Blue]Please run the Malware bytes and also this software: Hijackthis. Let me know the results. Please run Malware bytes in Safe Mode with Networking and then in normal mode run Hijackthis. 

[/COLOR]      [COLOR=Blue]The link for Malware bytes is:  [http://tinyurl.com/23n2bdp](http://tinyurl.com/23n2bdp).
   The link for Hijackthis is: [http://www.trendmicro.com/ftp/products/hijackthis/beta/HijackThis.msi](http://www.trendmicro.com/ftp/products/hijackthis/beta/HijackThis.msi).
   Let me know the results. Turn on your Window Firewall and Defender ON.
[/COLOR] [COLOR=#000000][FONT=georgia,serif]
-----------------

**a day later**

[/FONT][/COLOR][COLOR=#1F497D][COLOR=Blue]Please confirm the scan did work, if so we have some final work to do remaining.[/COLOR]
---------------

[/COLOR][COLOR=#000000][FONT=georgia,serif]Your stupid scan came up clean. Why, did you expect something else? 

Did you think I've been battling a hacker all week who's so stupid he would name his malware stuff like this? 

[/FONT][/COLOR]
[LIST]
[*]                      [Trojan:Java/Jifake.A]("http://www.microsoft.com/security/portal/Threat/Encyclopedia/Entry.aspx?Name=Trojan%3aJava%2fJifake.A")
[*]                     [Trojan:BAT/Delfiles.R]("http://www.microsoft.com/security/portal/Threat/Encyclopedia/Entry.aspx?Name=Trojan%3aBAT%2fDelfiles.R")
[*]                     [Trojan:HTML/Phishbank.U]("http://www.microsoft.com/security/portal/Threat/Encyclopedia/Entry.aspx?Name=Trojan%3aHTML%2fPhishbank.U")
[*]                     [Trojan:Win32/Fakeinstaller.I]("http://www.microsoft.com/security/portal/Threat/Encyclopedia/Entry.aspx?Name=Trojan%3aWin32%2fFakeinstaller.I")
[/LIST]

[COLOR=#000000][FONT=georgia,serif]You mo[FONT=Georgia]rons.[/FONT][/FONT][/COLOR][FONT=Georgia] But I guess I'm lucky I'm not being hit with Phishbank or FakeInstaller!! Those sneaky bastards. Imagine trying to rustle them out of your system...[/FONT]> **el_koraco said:**
> You do know that Chrome OS is Ubuntu based, right? There's more than one "cloud" OS out there. After you take some time recovering from the Windows ordeal, do take a look at KDE. It's like rediscovering the computing world all over again.

I did not know that, but what I do not know is...moderately obese.

What's the other cloud OS's out there? Are any operational already? Obviously I could Google but...you know...you can't trust search engines. 

It's actually kind of amazing that the whole world hasn't moved to the cloud ages ago. It makes no sense to carry around briefcases of cash, when you can 'lug' around a credit card to your cash in the cloud. I have no need to OWN software, or carry it around with me. I heard a half-decent (but not really) argument from a music nut with 6000 MP3s and obscure playing requirements, but I countered with Grooveshark. Basically his argument came down to 3G not being as reliable as he requires for his demanding advanced audio palate or something hilarious. 


KDE is like...I don't know what to make of KDE. We're eying each other off, warily. We might hook up though, at some point (like if and when I can't figure out how to get the fantastic but OMG complicated French docking thing to work on my Gnome desktop. So simple, but I'm so stupid. Also, options - too many options. It's tragic...

---

### Post by el_koraco on 2011-04-17
**[This]("http://distrowatch.com/table.php?distribution=jolios")** is just for starters. It's been gaining popularity, but very slowly. The Ubuntu developer responsible for, among other things, introducing **[two]("http://upstart.ubuntu.com/")** major system **[components]("http://ubuntuforums.org/showthread.php?t=1434502")** to the Unix world, is now employed by Google, working on Chrome OS. Personally, I'm not all that into the cloud paradigm, but that's not too important. 

As for the docking thing: 
Middle clicking an icon on it opens up a second instance of a running program. 
Double clicking on an icon of a program that has two or more windows brings them up in a tiled view. 
To move thing arround in the docking thing you gotta move the icon off it, and then place it where you want to. 
Type compizconfig-settings-manager in the software center and install it. 
Hit the super (meta, 'Windows') key, type ccsm and run it. Go to the Unity plugin, and it's pretty much self explanatory from there. 
When in doubt, ask. :D

---

### Post by goscuter1 on 2011-04-18
> **el_koraco said:**
>  After you take some time recovering from the Windows ordeal, do take a look at KDE. It's like rediscovering the computing world all over again.

lol I got to take a look at KDE without even intending to. I certainly didn't install any KDE, I was busy fighting my feisty (but fiery) sweetheart Gnome 3, trying to get her to stop crashing long enough to lock some window docks in place. 

But someone kindly brought KDE, to me!

[IMG]http://i.imgur.com/kmgaim.png[/IMG]

Also, just out of interest, what is X11. Or should I say, why is it doing that recursion thing that happened in Windows all the time, filling up my hard drives and BSOD'ing my systems...

[IMG]http://i.imgur.com/i95Hfm.png[/IMG]

Man recursion is a bitch. I hated the crap out of it in school, recursion and stupid relativity and migraine headaches. And they're back, to screw with me. 

I always feared this day would come...

---

### Post by el_koraco on 2011-04-19
X11, or X, is the windowing system used by Unix systems. It's comprised of a window manager (or DE) and the X server. The X server is the primitive part, responsible for relaying messages to the kernel, while window managers (such as Compiz), widget toolkits (such as GTK), or desktop environments (such as Gone) do the actual detailing. 

The directory (folder), AFAIK, is not recursive folder, but a symbolic link. I believe that in the old days all the graphical apps were placed in the /usr/bin/X11 direcotry, and non graphical ones in /usr/bin, so some of the lagacy apps still need the path. 

Everytime you open it, you're actually opening the /usr/bin/X11 directory.  

Of course, I'm as far away from being an expert in this as one can possibly imagine.

---

### Post by goscuter1 on 2011-04-19
> **el_koraco said:**
> X11, or X, is the windowing system used by Unix systems. It's comprised of a window manager (or DE) and the X server. The X server is the primitive part, responsible for relaying messages to the kernel, while window managers (such as Compiz), widget toolkits (such as GTK), or desktop environments (such as Gone) do the actual detailing. 

The directory (folder), AFAIK, is not recursive folder, but a symbolic link. I believe that in the old days all the graphical apps were placed in the /usr/bin/X11 direcotry, and non graphical ones in /usr/bin, so some of the lagacy apps still need the path. 

Everytime you open it, you're actually opening the /usr/bin/X11 directory.  

Of course, I'm as far away from being an expert in this as one can possibly imagine.

lol *blush* I really wish I didn't post that particular post. Just for posterity or for interest's sake (not mine so much, I'd just as soon blush and move on), the answers from a launchpad god who's assisting me with my noose:

> **"Eliah Kagan"]The reason for the directory /usr/bin to contain the symbolic link

     X11 -> .

is because there are files inside /usr/bin which were traditionally stored in /usr/bin/X11, which was traditionally a separate directory altogether. For backward compatibility, these files must remain accessible inside /usr/bin/X11 even though they are really inside /usr/bin. This symbolic link makes /usr/bin/X11 another name for /usr/bin.

That this creates recursion is a side-effect said:**
> http://en.wikipedia.org/wiki/Wine_(software[/url])).

This file is provided by the package cabextract, and not by any of the packages specifically associated with KDE4. See [http://packages.ubuntu.com/search?searchon=contents&keywords=cabextract.desktop&mode=exactfilename&suite=maverick&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=cabextract.desktop&mode=exactfilename&suite=maverick&arch=any) and [http://packages.ubuntu.com/maverick/cabextract](http://packages.ubuntu.com/maverick/cabextract). It is provided so that KDE4, and programs that use KDE4 or components of it (which may include programs you currently have), will be able to use cabextract, if and when such programs are installed. 

I see glimpses of what appear to be grounds for a counter-attack argument about "bloatware", but only fools attempt to cover embarrassment by amplifying it. The best way to deal with blushing is to simply forget about it. Clearly I am a genius fool...

---

### Post by BrianTheComputerWizard on 2011-04-20
Tell your friend to use Combofix.  It is free and this is the safest site to get it from, and the one I use:  [http://www.bleepingcomputer.com/combofix/how-to-use-combofix](http://www.bleepingcomputer.com/combofix/how-to-use-combofix)

It is extremely important that he use that site. There are a number of fake combifix sites and you are in deep trouble if you get a hacked version.  Once he has it, tell him to run it in safe mode (good old F8).  This should do a good job getting rid of the initial issues. 

After that it is time for malwarebytes, spybot, and adaware. Then tell him to change to better protection, Norton 360 is what I have been running for years. One of my clients had this hit his machine and his Norton contained most of the damage, allowing me to clean up his machine with much less trouble than usual.

Hope this helps,

Brian

---

### Post by el_koraco on 2011-04-20
> **goscuter1 said:**
> 
I see glimpses of what appear to be grounds for a counter-attack argument about "bloatware", but only fools attempt to cover embarrassment by amplifying it. The best way to deal with blushing is to simply forget about it. Clearly I am a genius fool...

Well, not really. Sure, there are some Linux systems which come preinstalled with all the shared libraries needed for hypothetic use of other packages and those that come rather clean. Say, for instance, Ubuntu comes with the smbclient preinstalled. I myself don't need it, because I'm not sharing files with windows systems over the network, and find NFS to be faster, but removing it is one command away, as is installing it. On the other hand, if you do a minimal install, you'll be able to specify packages to the very last detail.

It's not foolish to freak out, it's foolish not to ask :D

As for security experts and antivirus programs, this is an oldie, but a goodie. 

[http://linuxmafia.com/faq/Essays/security-snake-oil.html]("http://linuxmafia.com/faq/Essays/security-snake-oil.html") 

And escpecially the two essays linked therein: 

[http://www.ranum.com/security/computer_security/editorials/dumb/]("http://www.ranum.com/security/computer_security/editorials/dumb/")
[http://www.ranum.com/security/computer_security/editorials/master-tzu/]("http://www.ranum.com/security/computer_security/editorials/master-tzu/")

---

### Post by goscuter1 on 2011-04-21
> **BrianTheComputerWizard said:**
> Tell your friend to use Combofix. [http://www.bleepingcomputer.com/combofix/how-to-use-combofix](http://www.bleepingcomputer.com/combofix/how-to-use-combofix)

Yep ComboFix and Gmer are brilliant programs. And I wish I didn't have quite the experience / authority to comment on this particular topic. Run everything safe mode also, as per Brian's advice. 

Another program I have a lot of time for is ESET SysInspector - which is awesome for comparing progressive system health statuses. Somewhat ironically, I don't really rate Nod32 Internet Security after watching it's firewall settings being adjusted before my eyes one day. To the best of my limited knowledge, I do not have ESP. Not yet. And if I did, these were not the settings I would use my powers for, I think I'd be going more for something like Drew Barrymore in Firestarter:

[IMG]http://www.peliculasycine.org/images/0034drew_barrymore.jpg[/IMG]

That was a cool kid. Pity she had to grow up and get nasty ugly but...what can do you. 

> After that it is time for malwarebytes, spybot, and adaware. Then tell him to change to better protection, Norton 360 is what I have been running for years. 

With the same level of emphatic agreeance with Brian's initial advice, I strongly disagree with this. And until someone can explain why or how Malwarebytes isn't as redundant a program as they come, and they'd best be prepared with some convincing arguments because I have hundreds of forum threads to submit into evidence as Exhibits a > zzzz that Malwarebytes (whilst honest) is ineffectual. And there is a clue in that, I think, for alert and non-naive readers. 

> One of my clients had this hit his machine and his Norton contained most of the damage, allowing me to clean up his machine with much less trouble than usual.

I'm not saying Norton created the damage. That would be libellous. I have no evidence. I merely have IRREFUTABLE LOGIC on my side. And let's say, hypothetically, they did create the damage. 

Having coded it, would they not be in the best position to 'contain' it? Which would allow you to clean up his machine from Norton damage, a great deal easier than cleaning it from - say - Trend Micro's damage? And would that not lead you and almost everyone to believe Norton was the bomb? 

And if you put yourself in the shoes of an honest anti-malware company, in arguably the 2nd most corrupted industry on the planet (after e-gaming), an industry who's very EXISTENCE thrives on the creation and distribution of the malware they protect you from - lol. I'm not saying such a morally-conflicted company would be justified in their (very commercially correct) logic that, to survive, they must play the game. But then, I don't think such morally-conflicted companies even exist in the first place. Not the commercial guys (and hooey to "free software trials" that are clearly hooks, especially when the hooks are very subtle. 

I'm supposed to be catching up on work, but procrastinating. But Gmer and ComboFix must make literally nothing. They're the most abused and used "freeware" on the planet, I suspect. Which makes their coders admirably inspiring, and allows a level of trust as that moral hazard is not nauseatingly ridiculous (that the idea that morals even come into play, when commercial companies produce hazard). 

Watch out for RootkitUnhooker. They found a lot on my PC and I was really impressed. But then I caught up on the Russian coder public war between them and Greatis Regrun. If the Greatis guy is wrong, I'll eat my hat. His arguments trashing their lame excuses for why their code isn't open source make perfect sense, their responses are death threats. Seems pretty cut/dry to me. That's a Anti malware set of tools I have a lot of time for as well, Greatis RegRun. The broken Russian English is charming as well... 

I think someone mentioned Stuxnet earlier in this thread. Man that is a BITC.H to get rid of. All the big name jokers with their solutions were't doing squat. Finally RegRun's free tool, which Stuxnet put up a godawful fight against, came out on top. :glory

[IMG]http://i.imgur.com/slnVf.png[/IMG]

Good people, the Russians at RegRun. No bloatware also, unlike ubuntu 11.04 ;) 

> **el_koraco said:**
> Sure, there are some Linux systems which come preinstalled with all the shared libraries needed for hypothetic use of other packages and those that come rather clean. Say, for instance, Ubuntu comes with the smbclient preinstalled. I myself don't need it, because I'm not sharing files with windows systems over the network, and find NFS to be faster, but removing it is one command away, as is installing it. On the other hand, if you do a minimal install, you'll be able to specify packages to the very last detail.

Yeah the guy helping me on LaunchPad really helped me see where I was kind of at fault, with my *mild* annoyances that ubuntu wasn't the "*streamlined, purely functional, lightweight Linux distributions*" I'd been hearing about. Effectively, complaining that I'm retarded because my idiot mind didn't make the 'click' that ubuntu (the most user-friendly - and users are morans - and mainstream of all the Linux distributions) probably wasn't the lightweight Linux I expected it to be, and which disappointed me, idiotically. I still think there is dubious logic in the inclusion of anything that could be remotely exploitable, when a simple apt-get could add it if the user needs it...but users be morans, like me, so...I've made *better* arguments, from *stronger* positions, than that one. 

Man I should get back to work. What is wrong with me...holla

Oh, and from what little I saw, JoliCloud is god. We only had a short date, I got to first base (:brag) before my third system went kaput, but there was some sexual chemistry for sure. Wedding invites requiring RSVPs shortly.

---

### Post by el_koraco on 2011-04-21
I think that between iptables (sudo ufw enable) and apparmor, Ubuntu is pretty safe out of the box. I've certainly never had any problems with security, but I use cheap laptops, have no secret files, and the only networking I do is a small home file "server", so I never really needed any high level security. 

As for the levels of "user friendliness" and lock down, when talking about various Linux/*BSD variants, it mostly comes down to the philosophical differences.

---

### Post by goscuter1 on 2011-04-22
> **el_koraco said:**
> I think that between iptables (sudo ufw enable) and apparmor, Ubuntu is pretty safe out of the box. I've certainly never had any problems with security, but I use cheap laptops, have no secret files, and the only networking I do is a small home file "server", so I never really needed any high level security. 

As for the levels of "user friendliness" and lock down, when talking about various Linux/*BSD variants, it mostly comes down to the philosophical differences.

Just wanted to clarify I completely agree, on ubuntu's safeness. *In case I've given the impression I was annoyed at ubuntu for not curing my Windows AIDS. I was, but only irrationally.

---

### Post by P1C0 on 2011-04-22
Holy cow, the same Virus hit a neighbor of mine. He uses Windows XP, firefox and had only browsed into Facebook.
He also uses Avast.

I have tried Dr.Web CureIT and SuperAntiSpyware, and allthought these programs find the "windows restore" virus and delete it, it comes again after a reboot, probably by a backdoor trojan or sth.

---

### Post by el_koraco on 2011-04-22
> **goscuter1 said:**
> Just wanted to clarify I completely agree, on ubuntu's safeness. *In case I've given the impression I was annoyed at ubuntu for not curing my Windows AIDS. I was, but only irrationally.

Well, there is a certain point to the bloat and exploitability argument, but I think the only menaces so far have been "proof on concept" schemes. 

As i said, it comes down to the level of lock-down you wanna have. Extremely high levels of security can be achieved with any Linux distro or BSD variant, although some are more secure in nature than others. But then we would have to go into the SELinux/Apparmor-minimal/full install and similar debates, which are just as tedious as the desktop environment flame wars.

---

### Post by matt_symes on 2011-04-24
@goscuter1

The rest of us use Linux :popcorn:

Only gentle ribbing :D

---

