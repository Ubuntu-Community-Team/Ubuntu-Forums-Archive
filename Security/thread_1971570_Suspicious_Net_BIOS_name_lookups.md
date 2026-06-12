---
title: "Suspicious Net BIOS name lookups"
date: 2012-05-02
forum: Security
---

### Post by Jonathan L on 2012-05-02
Dear All

I was solving a networking problem on an isolated test network with tcpdump and am seeing very suspcious-looking Net BIOS name requests for domains entirely unrelated to me.  There's one Windows XP machine, recently switched on, which is sending them.

These are the names[INDENT]HEROLADAAW.BIZ
MUSI-C-LIPS.COM
REPKAMOUSE.NET
RULESSELUR.COM
[/INDENT]Output from tcpdump -vvv shows they're all of this form:

```
>>> NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
TrnID=0x8D25
OpCode=0
NmFlags=0x11
Rcode=0
QueryCount=1
AnswerCount=0
AuthorityCount=0
AddressRecCount=0
QuestionRecords:
Name=RULESSELUR.COM  NameType=0x00 (Workstation)
QuestionType=0x20
QuestionClass=0x1
```It's the only Windows machine on the network; there's no Samba; there's no route out.

Opinions welcomed.

Many thanks,
Jonathan.

EDIT: Run for about an hour, list of names now
GAMEVID.COM
HEROLADAAW.BIZ
MUSI-C-LIPS.COM
REPKAMOUSE.NET
RULESSELUR.COM
SPORT-TUBE.COM
SR4.ZAPSERV.COM
SU3.MCAFEE.COM
TUBEFASTER.COM
VOLKAHATAB.CC
[WWW.GOOGLE.COM](WWW.GOOGLE.COM)
[WWW.MADRIX.COM](WWW.MADRIX.COM)

---

### Post by CharlesA on 2012-05-02
Sounds like the box is trying to connect to some dodgy sites.

Have you run a malware scanner on it?

---

### Post by Jonathan L on 2012-05-03
Hi Charles

> Sounds like the box is trying to connect to some dodgy sites.
Have you run a malware scanner on it?

It's got some McAfee software on it, but reporting nothing.  I have the machine off at the moment; I'd like to boot in Ubuntu and scan from there -- can you recommend something to scan it with?

Thanks,
Jonathan.

PS. It's Windows XP, no data I care about.  Just running a Windows-only app I need for a few days.

---

### Post by matt_symes on 2012-05-03
Hi

I have looked on the wot ([http://www.mywot.com/](http://www.mywot.com/)) website and all those sites have been rated as malware sites by people.

The computer is infected. No two ways about it.

I would use Bit-defender ([http://download.bitdefender.com/rescue_cd/](http://download.bitdefender.com/rescue_cd/)) and/or Malware bytes.

Avast also have a Linux edition ([http://www.avast.com/products#tab2](http://www.avast.com/products#tab2)).

If you boot into safe mode, do you also get the netbios packets ? If not then use the excellent sysinternals suite and autoruns to disable all start up applications, programs, services etc for that user.

You can then use a binary search to see what is causing the problem. This assumes there is no root kit on the system.

I would also suggest creating a new user from safe mode command line. Log in as that user and see if you still get the same NetBIOS packets. This will help to identify a system or user profile settings compromise.

These steps are generally my starting point when removing a virus.

There is also Hirens boot CD. [http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd).

You can also check out UBCD (ultimate boot CD).

The safest way is to reinstall of course.

Kind regards

---

### Post by Jonathan L on 2012-05-03
Matt

Thanks for knowing where to check and kind of you to check for me.

> all those sites have been rated as malware sites ... The computer is infected. No two ways about it.

Oh how tedious! One forgets so quickly how fragile are the defenses of these poor wee beasties, and how much care and worry they require: this particular computer has had a single careful user (me) and certainly no click-happy fool seduced by the offer of a free smiley or ringtone.

Thanks all for advice: box will be in solitary, then shot.  Task will be attempted in Wine.

Kind regards,
Jonathan.

---

### Post by Jonathan L on 2012-05-04
Postscript: Booted "Safe Mode", logged in as Adminstrator, still looking for netbios resolution of the dodgy sites.  Rebooted, safe mode, administrator and installed free Windows Avast (watch for cheeky "Please Install Chrome"), ran boot-time scan, found approx 12 virus/trojan etc).  Now boots without looking for the dodgy sites ... but enthusiastically looking for "avast.com" for its updates.  Will keep it in disjoint network before wiping clean.

---

### Post by CharlesA on 2012-05-04
> **Jonathan L said:**
> Postscript: Booted "Safe Mode", logged in as Adminstrator, still looking for netbios resolution of the dodgy sites.  Rebooted, safe mode, administrator and installed free Windows Avast (watch for cheeky "Please Install Chrome"), ran boot-time scan, found approx 12 virus/trojan etc).  Now boots without looking for the dodgy sites ... but enthusiastically looking for "avast.com" for its updates.  Will keep it in disjoint network before wiping clean.

Yuck!

Which trojan/viruses did it find?

---

### Post by Jonathan L on 2012-05-05
> Which trojan/viruses did it find?

A nasty salad of Pdfka, Malob-by Crypt, Trojan-Gen, Malware-Gen, about 12 infected files.

In passing, Avast's download was a big single file, which I pulled down to a different machine and copied over, to keep the infected machine quarantined from the internet.  AVG's download, on the other hand, was simply and installer which immediately wanted to connect to the internet to pull the rest of it.  Thanks Matt for tip re Avast.

Thanks all.
Jonathan.

---

