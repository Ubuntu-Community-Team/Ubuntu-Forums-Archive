---
title: "Linux/Android/Mac differences in file distribution, sandboxing &amp; other access rules?"
date: 2013-07-02
forum: Security
---

### Post by gotnexusbluz on 2013-07-02
We all know what a liability the Windows registry is to Windows, and we all know that Apple keeps it's core code a secret and it's doors closed to most innovative developers. I also know the obvious argument that it's the most popular systems (not desktop Linux) which get attacked. As it happens, Android, and even the locked-down Apple systems got attacked, so I want to know what really separates their security systems (other than user popularity and company policies) from Linux. Are there really functional differences that protect Ubuntu Linux against recent embarrassments to Android and Apple, or is Ubuntu destined to create it's worst security liability for itself by becoming too popular? So I began my quest to answer these questions when I went looking for the information on the differences between Linux and it's derivative Android, but all I could find discussions on were the drivers and interpreters which separate phones from desktop computers! What I am interested in understanding better are the differences in which applications communicate with different OSs. How are files distributed differently on Linux, Android, and Apple's OSs, are there significant differences in how applications are sandboxed, and what other OS rules and what other factors distinguish (or extinguish) these different systems? I'd be so happy if somebody could shed some light on these questions!

Thanks!

---

### Post by Hungry Man on 2013-07-04
Actually Android uses the Linux security system for one layer - applications are separated by certificate into separate users, and interactions are handled through API access on the Java layer (Android permissions).

No, if anything Ubuntu is in a far worse state than Android.

OSX and Ubuntu run most users programs in a single account, that way they can all access each other, and their files. Android runs all programs in separate accounts. This makes sense for these devices, on Ubuntu you want your Pidgin to be able to open Chrome, etc. On Android you need a separate system (intents) to handle IPC between user accounts safely, and this doesn't exist on other platforms to that extent.

So Android actually does a lot more isolation.

If you have other questions feel free to ask/ if I wasn't clear.

---

### Post by gotnexusbluz on 2013-07-05
> **Hungry Man said:**
> Actually Android uses the Linux security system for one layer - applications are separated by certificate into separate users, and interactions are handled through API access on the Java layer (Android permissions).

No, if anything Ubuntu is in a far worse state than Android.

OSX and Ubuntu run most users programs in a single account, that way they can all access each other, and their files. Android runs all programs in separate accounts. This makes sense for these devices, on Ubuntu you want your Pidgin to be able to open Chrome, etc. On Android you need a separate system (intents) to handle IPC between user accounts safely, and this doesn't exist on other platforms to that extent.

So Android actually does a lot more isolation.

Wow, that's surprising! Is it a temporary account that's assigned when an app launches, or is it a permanent account for each installed app?
Would it be impractical to make PC Linux systems more like Android in that way?

Am I correct (understanding that Android actually has better security measures than Ubuntu) that the main reason why Android is the only Linux(oid) system to be attacked is that it's used enough to make it a target? 

Also, I should have asked specifically about the I-OS as well. It's been said that the Iphone OS has far more effective sandboxing of Apple apps than Android, making it more difficult for Iphone and Ipad users to customize their devices (I know it's not that difficult with Android). Is this difference because of a different operational strategy, or is it because non-open-source system code is unavailable to developers who Apple doesn't like? I find it curious not to have heard of I-OS attacks when Android is getting slammed, if the motivation of system use really trumps most technical barriers for the malware producers.   

Thanks for trying to shed light on the subject!

> **Hungry Man said:**
> 
If you have other questions feel free to ask/ if I wasn't clear.

---

### Post by Hungry Man on 2013-07-05
It is a permanent user account for each app certificate.

> [COLOR=#000000]Would it be impractical to make PC Linux systems more like Android in that way?[/COLOR]

Somewhat. For one thing not all programs are digitally signed. For another, programs assume they can all interact with each other, and you'd need to build a framework around that. But it wouldn't be terribly difficult.

> [COLOR=#000000]Am I correct (understanding that Android actually has better security measures than Ubuntu) that the main reason why Android is the only Linux(oid) system to be attacked is that it's used enough to make it a target? [/COLOR]

Yes. Though it's important to note that Linux is attacked plenty, just usually servers, not desktops.

> [COLOR=#000000]It's been said that the Iphone OS has far more effective sandboxing of Apple apps than Android[/COLOR]
I'm less familiar with iOS but I don't believe so.

> [COLOR=#000000]making it more difficult for Iphone and Ipad users to customize their devices (I know it's not that difficult with Android)[/COLOR]
That's more of their walled garden thing and their resistance to allow users to modify things. Not to mention the fact that it's all closed source.

Most attacks on android are through social engineering, they trick you into installing an app that makes you pay to send SMS, etc. This has less to do with whether the operating systems are super resilient to exploitation and more to do with how they handle alerting users to dangerous permissions. iOS filters all apps on its store, so attackers have to try to trick an iOS guy into letting them on - difficult. With android there's less of that, and attackers use that to their advantage. In later versions dangerous permissions are alerted better to the user, and limited further, so malware is less effective.

---

### Post by gotnexusbluz on 2013-07-07
Thanks! 

 By "mostly servers", I guess you mean network servers for businesses not connected to Ubuntu servers, from which I get my programs?

---

### Post by Hungry Man on 2013-07-07
Yep, that's correct.

---

