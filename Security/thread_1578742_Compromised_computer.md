---
title: "Compromised computer?"
date: 2010-09-20
forum: Security
---

### Post by jgull8502 on 2010-09-20
The other day I was notified by my university that my computer (they assumed I was running Windows) has become compromised by a bot or trojan. I've been running Ubuntu for a few years now, and it seems unlikely to me that I've been infected. 

After a conversation with the university IT security people, all they would tell me is that my computer was trying to connect to some sketchy IP addresses, but they wouldn't elaborate. They did however say that some web ads could trigger this type of issue. Apparently, the only way to be let back on the network is to tell them that I've "rebuilt my computer" (reformatted).

I went through and checked my logs and didn't see anything suspicious. The only thing I remember doing out of the ordinary at the time they reported is installing Exaile and trying to connect to some internet radio stations. Could that have triggered the alert? Is it likely that I've been infected with a bot, and is there any way to check for this at home? 

I also tried some other things I saw in a previous post: rkhunter --check yielded a few warnings mainly regarding pulseaudio and ADBE (presumably Adobe reader) in /dev/shm/; there were no suspicious processes running; and there was no crontab for root.

I could reformat, but its kind of a pain, especially considering my computer seems clean. I could also tell the IT people that I've "rebuilt" to get back on the network to see if it happens again. What do people here suggest?

Thanks!

---

### Post by jhayes on 2010-09-20
ok in am in undergrad for bsit security lemme see what i can do to help.

"The other day I was notified by my university that my computer (they assumed I was running Windows) has become compromised by a bot or trojan. I've been running Ubuntu for a few years now, and it seems unlikely to me that I've been infected."

first i would run 
netstat -tuna
and
lsof -L
to check conenctions, open ports etc.
then run ps aux
to see if any processes are out of order. is sshd when nor intended to run etc.


"After a conversation with the university IT security people, all they would tell me is that my computer was trying to connect to some sketchy IP addresses, but they wouldn't elaborate. They did however say that some web ads could trigger this type of issue. Apparently, the only way to be let back on the network is to tell them that I've "rebuilt my computer" (reformatted)."

look in aide and tripwire and snort. these are intrusion detection and host ids. not a perfect solution but will help monitor.

I went through and checked my logs and didn't see anything suspicious. The only thing I remember doing out of the ordinary at the time they reported is installing Exaile and trying to connect to some internet radio stations. Could that have triggered the alert? Is it likely that I've been infected with a bot, and is there any way to check for this at home?

if you check processes (ps aux) and open ports (netstat) and monitor then for a few days and nothing fun shows up ...

here is a piece of the php i run on my webpage on my server,that you can adapt,

system('./sshuser');
$arraydirty = file("sshdirty");
$arrayclean = array_unique($arraydirty);
foreach ($arrayclean as $value){
echo '<p><font color="red">sshusers = ',$value,"</p>";}
echo "<br /><br />";

the system call, calls this 
netstat -tuna |grep ":22"|grep ESTABLISHED|cut -d ":" -f 2|cut -d " " -f 9 | tr -d '\n'  > some file
but really you can leave the greps and cuts out , make it a cron job run it like every 10 min and write to a file. this will log it for awhile.


I could reformat, but its kind of a pain, especially considering my computer seems clean. I could also tell the IT people that I've "rebuilt" to get back on the network to see if it happens again. What do people here suggest?


with those other things running to monitor for a day or 2 you will know.
i doubt it is a bot net.
most likely an unusual port.

---

### Post by CharlesA on 2010-09-20
Personally I'd just backup my data and wipe the drive. Ubuntu isn't that hard to reinstall.

It may be nothing, but better safe than sorry.

Also, I'd contact the IT department and see if they can tell you which IP and port was being connected to. I doubt they'll tell you, but it's worth a shot.

I've seen cases where something as simple as SSHing into a machine at home is flagged.

---

### Post by rookcifer on 2010-09-21
Ah, the perils of dealing with university IT admins who have never even looked at a UNIX terminal.

---

### Post by perspectoff on 2010-09-21
> **jgull8502 said:**
> The other day I was notified by my university that my computer (they assumed I was running Windows) has become compromised by a bot or trojan. I've been running Ubuntu for a few years now, and it seems unlikely to me that I've been infected. 

After a conversation with the university IT security people, all they would tell me is that my computer was trying to connect to some sketchy IP addresses, but they wouldn't elaborate. They did however say that some web ads could trigger this type of issue. Apparently, the only way to be let back on the network is to tell them that I've "rebuilt my computer" (reformatted).

I went through and checked my logs and didn't see anything suspicious. The only thing I remember doing out of the ordinary at the time they reported is installing Exaile and trying to connect to some internet radio stations. Could that have triggered the alert? Is it likely that I've been infected with a bot, and is there any way to check for this at home? 

I also tried some other things I saw in a previous post: rkhunter --check yielded a few warnings mainly regarding pulseaudio and ADBE (presumably Adobe reader) in /dev/shm/; there were no suspicious processes running; and there was no crontab for root.

I could reformat, but its kind of a pain, especially considering my computer seems clean. I could also tell the IT people that I've "rebuilt" to get back on the network to see if it happens again. What do people here suggest?

Thanks!

A little hard story to believe. There are so many cross-scripts on web pages that send your computer connecting to IP addresses all over the world that it is impossible for any IT security wannabe at a university to determine if it was legit or not.

On the other hand, if you have hundreds of Gb transferring consistently to a site in Russia or Yugoslavia, or something, they might suspect you of file-trading. (A lot of file-sharing sites are located overseas.)

Perhaps your university is currently on a crusade against file-sharing or something. In that case you better not be, because they could snort your traffic and make a case against you. Possibly they are being polite, but possibly they are threatening you in a sidehand fashion.

There is a lot of legit non-copyrighted content that can be streamed from overseas sites, and it is always a long and difficult court case to prove illegal file-trading. Still, universities can easily be pressured into pressuring the most egregious offenders, and there is little question that historically much illegal file-trading has emanated from universities.

I also don't understand why you say they told you they suspected a Windows computer if you are using Linux. All monitors identify the operating system correctly. Something is wrong with the story.

I also don't buy it about an unknown bot. Sounds awful like an "OJ Simpson defense", where he checked for the "true killer" on the golf course.

But another thought occurs to me. Is your Internet connection secure? It is often easy to connect to some Internet connection at a university, kind of like war-driving. Could someone else be using your connection surreptitiously?

---

### Post by Ahava591 on 2010-09-21
The entire exchange between the IT people and you seems suspect. 

I would ask that they provide you with more information, including what exactly they think you've been doing, or what they think somebody else has been doing without you knowing.

It just sounds like either a scam or a complete moron thought he was going to be a cowboy that day.

Let us know how it goes, and good luck.

---

### Post by OpSecShellshock on 2010-09-21
With rampant script injections, malicious banner ads, and really effective BhSEO, there are hordes of users connecting to suspicious IP addresses and domains all the time. However, it doesn't always mean that whatever script it was actually worked. In the OP's case, I can almost guarantee that it didn't. But since a lot of these scripts direct browsers to exploit kits, it gets really noisy pretty quickly as they cycle through any number of Windows, Flash, Acrobat, Java, and browser exploits. In other words, if the university's IT staff is just running a query of university IP addresses that connected to a list of known-or-suspected malicious external IP addresses with no contextual data, they're going to get a whole lot of false positives. I really suspect that when they refuse to give you details it's because they don't have them.

It's a shame for a university not to have a dedicated security staff to watch these things more closely and put them in context.

---

### Post by jgull8502 on 2010-09-21
Yeah, the whole thing sounded a bit suspicious to me as well, but I figured I'd ask around here to get a second opinion. My university is very strict on file sharing, and as such I would never do it at work. 

I'll notify them that everything's been taken care of, and I'll try prodding them for more details while I'm at it, including whether it's happened again between the day they logged me and the day they shut me off; I assume it hasn't. 

Thanks all!

---

### Post by jgull8502 on 2010-09-21
I talked to the security people again and they did tell me the name of what they claim I was infected with: bredolab. I'm fairly sure I'm not / can't be infected with this, am I right? I check anyway (especially because I have wine installed) and I didn't find any of the relevant dll or exe files on the computer. 

Maybe the virus tried to get itself onto my computer and that's what they detected.

---

### Post by HermanAB on 2010-09-21
Hmm, bredolab is a Windows trojan.  Tell IT that you run Linux and cannot run Windows malware, so whatever Windows problem they saw, must have been a mistake or a transient problem.

Relax and enjoy your Linux system.

---

### Post by rookcifer on 2010-09-21
> **jgull8502 said:**
> I talked to the security people again and they did tell me the name of what they claim I was infected with: bredolab. I'm fairly sure I'm not / can't be infected with this, am I right? I check anyway (especially because I have wine installed) and I didn't find any of the relevant dll or exe files on the computer. 

Maybe the virus tried to get itself onto my computer and that's what they detected.

Tell them to either learn something about Linux or to find a new job.  They're incompetent, plain and simple.  But, hey, that's what we get for living in a Windows world.

---

