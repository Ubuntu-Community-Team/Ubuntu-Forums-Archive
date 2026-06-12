---
title: "Is getting rid of the Think Point virus with ubuntu possible?"
date: 2010-11-08
forum: Security
---

### Post by Michael577 on 2010-11-08
Hey everyone, this kid in my school told me that his computer was infected with a virus and I told him that I was going to bring The live CD of Ubuntu tomorrow.He told me what the virus was, I later looked up the virus and well... You know that fake anti-virus program called Think Point? Well I was wondering if it's possible to remove that program/virus that's installed on a windows machine with a Live CD/USB of Ubuntu? With Avast or some anti-spy-ware/virus installed? Please respond quickly because I need this all set for tomorrow. And Yes I found alternatives without Ubuntu, but I told the kind that I was going to give him the disk with instructions to remove it. thanks to who responds. 

BTW, currently the kids family has NO ANTI-VIRUS AND FIREWALL INSTALLED!!:shock: So it's obvious how the computer got infected.

---

### Post by epz on 2010-11-08
yea it is, you just need an antivirus with updated virus signature, first try clamav (available in repos) them you may want to try avast.

All you have to do is find where the system mounts the Windows partition (i think /media, not sure try to find out) and i think for clamav the cli needs  clamscan /media/pathtowindows, may want to try with sudo, not sure you may benefit on windows but on Linux checks more files (which are normally protected)

ps: i have no idea of what think point is so yea be sure it's a virus first lol

---

### Post by WeAreLinux on 2010-11-08
> BTW, currently the kids family has NO ANTI-VIRUS AND FIREWALL INSTALLED!!

Personally, I would seek help from one of the many malware removal forums. With no security on the machine, who knows what else is currently installed. Even better, I would do a full reformat but that's not an option for everybody. This isn't the forum for that though.

With Ubuntu Live CD, yes it's possible if the AV programs have added the threat to it's definitions. No program can detect 100% of threats.

You could also try AVG's Rescue CD @ [http://www.avg.com/us-en/avg-rescue-cd](http://www.avg.com/us-en/avg-rescue-cd)

[http://www.howtogeek.com/howto/14434/scan-a-windows-pc-for-viruses-from-a-ubuntu-live-cd/](http://www.howtogeek.com/howto/14434/scan-a-windows-pc-for-viruses-from-a-ubuntu-live-cd/)
[http://ubuntuforums.org/showthread.php?t=1028934](http://ubuntuforums.org/showthread.php?t=1028934)
[http://ubuntuforums.org/showthread.php?t=1516513](http://ubuntuforums.org/showthread.php?t=1516513)

---

### Post by slooksterpsv on 2010-11-09
Avira has an amazing antivirus engine and is ranked top against competitors like AVG, MSE, McAfee, Norton, etc. Actually the Premium version ranks 98.6% at #1 according to [http://av-comparatives.org/](http://av-comparatives.org/)

Here's where you can download a "rescue" cd (Linux based) to run a scan and clean out what you can: 
[http://www.avira.com/en/support-download](http://www.avira.com/en/support-download)

Theres an ISO and an EXE - EXE will burn it for you, ISO you need an ISO Burning app like k3b, Brasero, ISORecorder, etc.

---

### Post by wilee-nilee on 2010-11-09
Good luck if they have been running it in admin with no firewall or AV software there is more then one virus there.

You may get some cleaned up if it is bad but you may have a unusable computer. Under those circumstances I would tell them a reinstall is in order, you will never know whats in there. there are rootkits that are undetectable.

I wouldn't touch that with a ten foot pole but with a install disc I would.

---

### Post by OpSecShellshock on 2010-11-09
Anything short of reinstalling the OS is a waste of time. If they're going to insist on installing that one, they're going to need to add the necessary protections prior to surfing the web--and I'd hasten to add that I mean any part of the web, not just the places you'd expect.

---

### Post by wojox on 2010-11-09
Use [Trinity Rescue Kit | CPR for your computer]("http://trinityhome.org/Home/index.php?content=TRINITY_RESCUE_KIT____CPR_FOR_YOUR_COMPUTER&front_id=12&lang=en&locale=en")

---

### Post by Grenage on 2010-11-09
I'm going to risk the flaming, and disagree; you don't usually need to format a computer due to a bit of rough software.  Just because a machine has one piece of malware, it doesn't mean it's eternally doomed, evil, unstable, unusable or likely to murder your family.

I second the Avira rescue CD; Windows-based scans such as MalwareBytes!, Spybot, and Avast or Microsoft Security Essentials would also be ideal.  Windows firewall would be a bonus, especially if they don't have a gateway router with one.

---

### Post by Kinstonian on 2010-11-09
> **Grenage said:**
> I'm going to risk the flaming, and disagree; you don't usually need to format a computer due to a bit of rough software.  Just because a machine has one piece of malware, it doesn't mean it's eternally doomed, evil, unstable, unusable or likely to murder your family.

I second the Avira rescue CD; Windows-based scans such as MalwareBytes!, Spybot, and Avast or Microsoft Security Essentials would also be ideal.  Windows firewall would be a bonus, especially if they don't have a gateway router with one.

There is a lot more to recovering from an incident than running anti-malware software.  You can avoid a reinstall if you know what you're doing and analyze various timelines of system activity, web browsing history, registry, log analysis, memory analysis, reverse engineer malware, etc., followed by increased monitoring of the system after recovery.  Only then would it be relatively safe to avoid a reinstall.

However, as you can probably see, it's easier for home users to recover from a serious compromise by reinstalling the OS after figuring out how the attacker got access.

---

### Post by |{urse on 2010-11-09
boot to safe mode (if u can) (hit f8 before the windows boot logo)
*if you cant get to a desktop you will need to perform a repair install of the operating system*
run combofix, get it here [http://www.bleepingcomputer.com/download/anti-virus/combofix](http://www.bleepingcomputer.com/download/anti-virus/combofix)
remove avast, install avira
scan with avira
install malwarebytes anti-malware
scan with malwarebytes
press windows key + r
type *msconfig* in the run box
check selective startup
click the far right tab labeled "startup"
remove any suspicious startup entries (uncheck them)
reboot when prompted to do so after clicking Ok
download dial-a-fix [http://djlizard.net.nyud.net:8080/software/Dial-a-fix-v0.60.0.24.zip](http://djlizard.net.nyud.net:8080/software/Dial-a-fix-v0.60.0.24.zip)
extract dial-a-fix and run with defaults checked

This is my standard removal and repair procedure for any smitfraud based infection. This will remove the ThinkPoint virus and the rootkits and other unpleasant things it installs, Enjoy. 

To do all this from a linux livecd is possible but you would have to manually edit the hive and that would take 92387394739287yrs.

---

### Post by wilee-nilee on 2010-11-09
> **Kinstonian said:**
> There is a lot more to recovering from an incident than running anti-malware software.  You can avoid a reinstall if you know what you're doing and analyze various timelines of system activity, web browsing history, registry, log analysis, memory analysis, reverse engineer malware, etc., followed by increased monitoring of the system after recovery.  Only then would it be relatively safe to avoid a reinstall.

However, as you can probably see, it's easier for home users to recover from a serious compromise by reinstalling the OS after figuring out how the attacker got access.

I have to ask here if the OP has to ask the forum for help on just how to use the Ubuntu disc do they possess the toolset to do this?

I have friends who do this for a living, they all would recovery the important information and reinstall and set them up with a limited account and good free av software. The amount of time at the rate of charge ($) is the key here.

Any of you who are trying to say oh you can do this or that you don't have to reinstall are not paying attention here. As I said there are rootkits that can not be detected. Yes if your a computer forensic person you could find them probably and get it cleaned up but that is a high skill level of understanding the MS OS, Do we see that here with the OP.

A computer run in admin with MS with no firewall and av software is about as exposed as you can get, short of actually wanting a problem.

[http://www.myantispyware.com/2010/10/18/how-to-remove-thinkpoint-uninstall-instructions/](http://www.myantispyware.com/2010/10/18/how-to-remove-thinkpoint-uninstall-instructions/)

---

### Post by Grenage on 2010-11-09
> **wilee-nilee said:**
> Any of you who are trying to say oh you can do this or that you don't have to reinstall are not paying attention here. As I said there are rootkits that can not be detected. Yes if your a computer forensic person you could find them probably and get it cleaned up but that is a high skill level of understanding the MS OS, Do we see that here with the OP.

You could therefore assume that most computers have a root kit on them - bit they can be found with relative ease; rootkits are also *not* the kind of thing you catch via a virus.

Some computers are worth reformatting, it's just quicker than a clean. Of course, if the user is going to use it with lax security again, it's a futile venture and a waste of time.  Still, we try.

---

### Post by wilee-nilee on 2010-11-09
> **Grenage said:**
> You could therefore assume that most computers have a root kit on them - bit they can be found with relative ease; rootkits are also *not* the kind of thing you catch via a virus.

Some computers are worth reformatting, it's just quicker than a clean. Of course, if the user is going to use it with lax security again, it's a futile venture and a waste of time.  Still, we try.

Duh;) you know what happens when you assume. A root kit needs root access; a MS admin account is root access.

I would agree if they are not going to lock it down correctly it is a waste of time and promotes them to continue a slapshod setup.

A MS OS can be set up to be as safe as Linux or any other open source OS, but it has a huge bullseye on the operating system. You also have to be aware of social engineering which is how the track point gets loaded. look at my link as to what it does, it is a fake AV that is a HUGE red flag.

The best security just to start with a MS user can use is a limited account, all versions from XP and on will allow you to run admin functions from the limited with a right click run as. It is hypothesized that a limited account will wipe away about 90% of the danger to begin with.

---

### Post by uRock on 2010-11-09
[Malwarebytes]("http://www.malwarebytes.org/mbam.php") and [MS Security Essentials]("http://www.microsoft.com/security_essentials/") FTW!

They both work great and they are both free.

---

### Post by Grenage on 2010-11-09
> **wilee-nilee said:**
> The best security just to start with a MS user can use is a limited account, all versions from XP and on will allow you to run admin functions from the limited with a right click run as. It is hypothesized that a limited account will wipe away about 90% of the danger to begin with.

Yup, with that I cannot argue. :)

---

### Post by wilee-nilee on 2010-11-09
> **uRock said:**
> [Malwarebytes]("http://www.malwarebytes.org/mbam.php") and [MS Security Essentials]("http://www.microsoft.com/security_essentials/") FTW!

They both work great and they are both free.

superantispyware is a good one as well, it will run circles around malwarebytes which is a pretty good malware finder itself.
[http://www.superantispyware.com/](http://www.superantispyware.com/)

---

### Post by |{urse on 2010-11-09
> **wilee-nilee said:**
> I have to ask here if the OP has to ask the forum for help on just how to use the Ubuntu disc do they possess the toolset to do this?

I have friends who do this for a living, they all would recovery the important information and reinstall and set them up with a limited account and good free av software. The amount of time at the rate of charge ($) is the key here.

Any of you who are trying to say oh you can do this or that you don't have to reinstall are not paying attention here. As I said there are rootkits that can not be detected. Yes if your a computer forensic person you could find them probably and get it cleaned up but that is a high skill level of understanding the MS OS, Do we see that here with the OP.

A computer run in admin with MS with no firewall and av software is about as exposed as you can get, short of actually wanting a problem.

[http://www.myantispyware.com/2010/10/18/how-to-remove-thinkpoint-uninstall-instructions/](http://www.myantispyware.com/2010/10/18/how-to-remove-thinkpoint-uninstall-instructions/)

This no longer works without running combofix first unfortunately. If you follow those steps without it you'll end up with that lovely thinkpoint screen on reboot again. Also this is for removal of the smitfraud variant but there is no mention of repair. I'd recommend an sfc /scannow  for the windoze savvy or dial-a-fix for the beginner afterwords.

---

### Post by |{urse on 2010-11-09
> **Grenage said:**
> Yup, with that I cannot argue. :)
+1 on that.

---

### Post by wilee-nilee on 2010-11-09
> **|{urse said:**
> This no longer works without running combofix first unfortunately. If you follow those steps without it you'll end up with that lovely thinkpoint screen on reboot again. Also this is for removal of the smitfraud variant but there is no mention of repair. I'd recommend an sfc /scannow  for the windoze savvy or dial-a-fix for the beginner afterwords.

I only included that not as a fix but as a a little information on the nature of this virus. My opinion has already been stated.;)

---

### Post by tgalati4 on 2010-11-09
I had luck cleaning a system with a similar virus using an ubuntu live CD and installing and running bit defender.

---

### Post by uRock on 2010-11-09
> **tgalati4 said:**
> I had luck cleaning a system with a similar virus using an ubuntu live CD and installing and running bit defender.

Yup, the good thing about bitdefender is that it is free for Linux desktop users.

---

### Post by wilee-nilee on 2010-11-09
> **uRock said:**
> Yup, the good thing about bitdefender is that it is free for Linux desktop users.

This is what I use, it has multiple different av available, I also use superantispyware and avast live in my actual setups.
[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/)
All of the av will download the latest definitions, although I could not get avira or avg to work the load would not boot.

If a person has computer that doesn't boot a thumb this will allow you to do so.
[http://www.plop.at/](http://www.plop.at/)

---

### Post by WeAreLinux on 2010-11-09
Just wanted to add, when using Malwarebytes Anti-Malware don't purchase the real-time scanner. It's not that great.

---

### Post by |{urse on 2010-11-09
> **wilee-nilee said:**
> I only included that not as a fix but as a a little information on the nature of this virus. My opinion has already been stated.;)

Oh, gotcha. BTW I agree personally. Reinstall windows. However for a customer who wouldnt notice the many holes left by such a virus, I'd remove/repair. Really it comes down to how valuable the compromised data is. Sorry didn't mean to tit the wrong tat.

---

### Post by wilee-nilee on 2010-11-09
> **|{urse said:**
> Oh, gotcha. BTW I agree personally. Reinstall windows. However for a customer who wouldn't notice the many holes left by such a virus, I'd remove/repair. Really it comes down to how valuable the compromised data is. Sorry didn't mean to tit the wrong tat.

I think we have to take the context of this situation in perspective. To me it looks like another student who uses open source and has acquaintance that has this problem.

If it was a professional service situation would they be coming onto the forum to get information?

Personally as I said I wouldn't touch it under this situation without a reinstall. I have fixed my friends computers free of charge that run MS, but I tell them that we have to be ready for a reinstall possibility. So we back up everything, then go after the critters. Now in every case with my friends in spite of my telling them in the first place how to make their computers safer they ignored this advice. Consequently I would find in the numbers around 200-300 nasty-ware hits and 1-3 root kits that were actually detectable. In these cases after cleaning it all up the OS was toast. Not even able to be overwritten with a standard XP disc that will reinstall leaving your extras in place. All of these people were running XP in admin mode.

So I fresh installed, sanitized their back up and set them up correctly and they have no problems now.

---

### Post by |{urse on 2010-11-10
> If it was a professional service situation would they be coming onto the forum to get information?

Nope, but thats what they'll get from me. Not just a quick google and opinions but specific solutions derived from personal and professional experience.  

>  I have fixed my friends computers free of charge that run MS

Please understand me when I say I'm not trying to flamebait you but I did pc repair for a living until I pursued a career in web design and landed a job as a govmt subcontractor doing more interesting linuxy things. 9o percent of the time I can get everything back up to snuff even on the worst system within a few hours. It's still easier and faster to reinstall.

I have tried everything I know of to accomplish what the OP proposed including writing a script in combination with sysresccd to clean the user profile hive (complete failure by the way).  ^^ If anyone knows of, or can write a win UPH cleaner for linux then we can make a livecd distro that completely removes all smitfraud variants and the sidebyside errors or "holes" if you will. I have everything needed already looped to /mnt/dsk just need the uph cleaner and there it will stay until I find something that works.

---

### Post by wilee-nilee on 2010-11-11
n

---

