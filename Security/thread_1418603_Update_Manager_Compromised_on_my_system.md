---
title: "Update Manager Compromised on my system?"
date: 2010-02-28
forum: Security
---

### Post by angeleum on 2010-02-28
My family has a dangerous person with sophisticated computer knowledge (and friends with such knowledge) stalking family members... really. Therefore we use very long, random passwords, etc., and my system is locked in a special room.

Six days ago Update Manager offered some shady updates to me... _updates_ of programs _not_ on my system... rpm, alien, g++, m4, lsb-cxx (along with other parts of lsb), a slew of BSD stuff and low-level mail daemons... I could go on, but you get the drift. I tried to post a detailed list with other info, but the forum dumped my message saying I was no longer logged in. I was out of time, so I dropped it.

The curious thing was several things (lsb for instance) where I already had parts installed were offered for update with the _same_ version already installed.

I found this highly suspicious and refused permission.

Two days ago, Update Manager dropped these items (finally) but now wants to update sudo, which may be legitimate. I'm getting ready to wipe my system and re-install from a secure disk and don't want to take the chance.

Checking my logs and running chkrootkit didn't reveal anything suspicious to me, but I'm not among most knowledgeable at that level.

So my question to the forum: how was this done, or is it possible? How do I guard against it in the future? Finally, am I being paranoid enough? :???:

---

### Post by johngreth on 2010-02-28
To the best of my knowledge, the update manager does not use a secure encrypted connection. Even if it did, if a skilled hacker is able to intercept and change Internet data coming to and from your house, they could potentially put anything into your updates using a [Man-In-The-Middle Attack]("http://en.wikipedia.org/wiki/Man-in-the-middle_attack"). This isn't common and would be very difficult, but not impossible for someone that is very knowledgeable and is out to get you.

There really was an update recently for sudo, but that doesn't mean that someone with the powers listed above didn't mess with it.

If the attacker is using updates to get into your computer, doing a fresh install wont protect against it, but it could remove any security hazards already installed on your computer. I also suggest wiping the drive with [dban]("http://www.dban.org/") before the fresh install to make sure that nothing is hiding in unallocated space.

The most important thing for you to do is to call the police and report the stalker. Also, keep a well documented list of any suspicious behavior and any related events. Keep this document safe, not on a computer, but on paper, and keep it in a secret place in your house. A stalker's most valued thing is information, and if he/she gets this list, they may be able to use the information against you.

> Finally, am I being paranoid enough?

The likely hood that someone is using updates to attack your computer is slim, but if they are really out to get you and have lots of money and connections and resources (Gang?), then you can't be too careful.

---

### Post by RJARRRPCGP on 2010-02-28
I felt the same way, when I went to a message board and saw my web browser (on the bottom left) telling me it was trying to connect to a domain name that looked suspicious. Then I reformatted and reinstalled the OS.

Turns out that I was a victim of a code injection attack. 

A phpBB 2 message board had a code injection attack. Code was injected into a phpBB message board to connect to a malicious URL when anyone visited.

---

### Post by cariboo on 2010-02-28
> **angeleum said:**
> My family has a dangerous person with sophisticated computer knowledge (and friends with such knowledge) stalking family members... really. Therefore we use very long, random passwords, etc., and my system is locked in a special room.

Six days ago Update Manager offered some shady updates to me... _updates_ of programs _not_ on my system... rpm, alien, g++, m4, lsb-cxx (along with other parts of lsb), a slew of BSD stuff and low-level mail daemons... I could go on, but you get the drift. I tried to post a detailed list with other info, but the forum dumped my message saying I was no longer logged in. I was out of time, so I dropped it.

The curious thing was several things (lsb for instance) where I already had parts installed were offered for update with the _same_ version already installed.

I found this highly suspicious and refused permission.

Two days ago, Update Manager dropped these items (finally) but now wants to update sudo, which may be legitimate. I'm getting ready to wipe my system and re-install from a secure disk and don't want to take the chance.

Checking my logs and running chkrootkit didn't reveal anything suspicious to me, but I'm not among most knowledgeable at that level.

So my question to the forum: how was this done, or is it possible? How do I guard against it in the future? Finally, am I being paranoid enough? :???:

Yes you are being paranoid. You more than likely have Chrome installed, alien, rpm, et all were installed as dependencies by a Chrome update, that has since been fixed 

I would suggest you search the forums first if you feel you are getting dogey updates. I personally started a thread [here]("http://ubuntuforums.org/showthread.php?t=1410411&highlight=cariboo907") on the same subject,

As for the sudo update, have a look [here]("http://www.ubuntu.com/usn/USN-905-1") for more info.

---

### Post by Agent ME on 2010-02-28
> **johngreth said:**
> To the best of my knowledge, the update manager does not use a secure encrypted connection. Even if it did, if a skilled hacker is able to intercept and change Internet data coming to and from your house, they could potentially put anything into your updates using a [Man-In-The-Middle Attack]("http://en.wikipedia.org/wiki/Man-in-the-middle_attack"). This isn't common and would be very difficult, but not impossible for someone that is very knowledgeable and is out to get you.
The packages in the Ubuntu software repository are all digitally signed by keys trusted by every Ubuntu system. If someone tried to use a man-in-the-middle attack to change the packages being downloaded, Ubuntu would give errors.

---

### Post by johngreth on 2010-02-28
> The packages in the Ubuntu software repository are all digitally signed by keys trusted by every Ubuntu system. If someone tried to use a man-in-the-middle attack to change the packages being downloaded, Ubuntu would give errors.

I didn't think of that. Good call. So it's not possible to tamper with updates...

---

### Post by angeleum on 2010-02-28
> **cariboo907 said:**
> Yes you are being paranoid. You more than likely have Chrome installed, alien, rpm, et all were installed as dependencies by a Chrome update, that has since been fixed 

I would suggest you search the forums first if you feel you are getting dogey updates. I personally started a thread [here]("http://ubuntuforums.org/showthread.php?t=1410411&highlight=cariboo907") on the same subject,

As for the sudo update, have a look [here]("http://www.ubuntu.com/usn/USN-905-1") for more info.

Thanks very much, and to others replying to my message. A stalker does make you paranoid, particularly one with gang affiliations as this one has. I can't describe how much this has messed up members of my family. The police encourage you to be paranoid and we already have some police security for the person most directly affected. I am not free to discuss more than that.

To the extent I jumped off the pier, I apologize to the forum and am somewhat relieved by the fast replies. I do have Chrome installed.

In my own defense, I checked to see if any of these were installed; I didn't assume. Synaptic didn't see them, and though that is not definitive, it was the best I could think of at that moment.  I also searched the forum first before posting, but sometimes that's an art not a science. I missed your references and am glad to have them.

---

