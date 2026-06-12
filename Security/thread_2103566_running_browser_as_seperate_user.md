---
title: "running browser as seperate user"
date: 2013-01-10
forum: Security
---

### Post by lou21 on 2013-01-10
Hey all,  I was wondering whether any security can be gained by running the brower as a seperate user?  E.g. something like adding a new account in a new group and then using su to run the browser?  Thoughts all?  If this is actually a good idea then can anyone suggest a reasonably detailed method for setting it up.

---

### Post by snowpine on 2013-01-10
This functionality is built in to Firefox in the form of "profiles":

[http://support.mozilla.org/en-US/kb/profiles-where-firefox-stores-user-data](http://support.mozilla.org/en-US/kb/profiles-where-firefox-stores-user-data)

If you are using Firefox as Profile A then it will not have access to the passwords, cookies, bookmarks, etc. of Profile B. :)

---

### Post by Lfekey2 on 2013-01-10
Hungry Man wrote a great post on his blog.
[http://www.insanitybit.com/2012/08/01/creating-a-new-user-account-for-pidgin/](http://www.insanitybit.com/2012/08/01/creating-a-new-user-account-for-pidgin/)
The example is pidgin, but browser also apply to this.

---

### Post by Hungry Man on 2013-01-10
As Lfekey2 notes, I've written this up for Pidgin. Replacing Pidgin with your browser will have the same effects.

Users are separated from each other in terms of file access and their ability to communicate with other processes in separate user IDs. By running your program as another user you gain some security.

There are downsides. When you download something from your browser it'll be in the other users home directory. You can fix this with setfacl but I haven't gotten around to learning how to do this.

---

### Post by unspawn on 2013-01-10
> **Hungry Man said:**
> By running your program as another user you gain some security.
If you would collate a top ten list of ITW browser or related attacks Linux users face, what security would you actually gain from using a separate Id?

---

### Post by lykwydchykyn on 2013-01-10
Doesn't apparmor already limit what firefox can access on your system?

---

### Post by Hungry Man on 2013-01-10
Apparmor does restrict the browser. It's two different methods with somewhat different results.

@unspawn,

Linux desktop users rarely face threats. I'd say Java exploits are the most likely attack vector for a Linux user. In the case of a Java exploit running the browser and plugin as a separate user will mean that only that UID is compromised.

---

### Post by lou21 on 2013-01-10
> **snowpine said:**
> This functionality is built in to Firefox in the form of &quot;profiles&quot;:

[http://support.mozilla.org/en-US/kb/profiles-where-firefox-stores-user-data](http://support.mozilla.org/en-US/kb/profiles-where-firefox-stores-user-data)

If you are using Firefox as Profile A then it will not have access to the passwords, cookies, bookmarks, etc. of Profile B. :)

 This is not what I was asking about at all.

---

### Post by lou21 on 2013-01-10
> **Hungry Man said:**
> Apparmor does restrict the browser. It's two different methods with somewhat different results.

@unspawn,

Linux desktop users rarely face threats. I'd say Java exploits are the most likely attack vector for a Linux user. In the case of a Java exploit running the browser and plugin as a separate user will mean that only that UID is compromised.

 So this method would prevent the browser from doing any damage/making any changes to the users home folder?

---

### Post by Hungry Man on 2013-01-10
Yes. It gets its own separate home folder. It can't read or write to the users home folder.

---

### Post by lou21 on 2013-01-11
> **Hungry Man said:**
> Yes. It gets its own separate home folder. It can't read or write to the users home folder.

 So if one were to keep any executables or scripts (e.g. self made ones) in their home folder then this would actually add considerable security...

---

### Post by unspawn on 2013-01-11
> **Hungry Man said:**
> I'd say Java exploits are the most likely attack vector for a Linux user. In the case of a Java exploit running the browser and plugin as a separate user will mean that only that UID is compromised.
If Java is the most likely attack vector *then shouldn't the first measure be to disable the Java plugin and webstart until it's actually needed*? Phrased differently: who would the measure realistically benefit? By guesstimate I'd say that of people who have Java installed about .001 per cent actually *need* it and even then it doesn't always have 'net capabilities either: for example OpenOffice.org or LibreOffice may suggest Java as a dependency but IIRC it's only needed for specific math stuff?

---

### Post by mike acker on 2013-01-11
> **snowpine said:**
> This functionality is built in to Firefox in the form of "profiles":

[http://support.mozilla.org/en-US/kb/profiles-where-firefox-stores-user-data](http://support.mozilla.org/en-US/kb/profiles-where-firefox-stores-user-data)

If you are using Firefox as Profile A then it will not have access to the passwords, cookies, bookmarks, etc. of Profile B. :)

...the more advanced question we have is: what can a browser access in our computer ??

e.g. could a Java Script launched by a WebPage inventory my /home/documents/correspondence directory and send copies of my memos to [EMAIL="Hacker6@Ukrane.rus"]Hacker6@Ukrane.rus[/EMAIL] ??

I am running Firefox in the AppArmor proficle distributed by Cannonical but I need to learn more about the syntaxt of AppArmor in order to audit the given profile .   we have trolls "out there" who threaten people with the cost of defending litigation as a means of extortion ...

---

### Post by lou21 on 2013-01-11
> **mike acker said:**
> ...the more advanced question we have is: what can a browser access in our computer ??

e.g. could a Java Script launched by a WebPage inventory my /home/documents/correspondence directory and send copies of my memos to [EMAIL="Hacker6@Ukrane.rus"]Hacker6@Ukrane.rus[/EMAIL] ??

I am running Firefox in the AppArmor proficle distributed by Cannonical but I need to learn more about the syntaxt of AppArmor in order to audit the given profile .   we have trolls &quot;out there&quot; who threaten people with the cost of defending litigation as a means of extortion ...

 Does anyone know the answer to this? This is an important question (yes I know that Java Script should be disabled by default but sometime it needs to be on and we all know that even reputable websites get attacked sometimes).

---

### Post by snowpine on 2013-01-11
> **lou21 said:**
> This is not what I was asking about at all.

Understood; I was merely trying to suggest a simpler method that should be "secure enough" for most users, as well as to let you know that Mozilla developers are concerned about these issues and working to make Firefox as safe & secure as possible. :)

---

### Post by Hungry Man on 2013-01-11
There's no way for Javascript to access those files unless the browser provides an interface to do so. If it does provide that interface you can bet that it's handled in some way that wouldn't allow arbitrary access.




@Unspawn,

> If Java is the most likely attack vector then shouldn't the first measure be to disable the Java plugin and webstart until it's actually needed? Phrased differently: who would the measure realistically benefit? By guesstimate I'd say that of people who have Java installed about .001 per cent actually need it and even then it doesn't always have 'net capabilities either: for example OpenOffice.org or LibreOffice may suggest Java as a dependency but IIRC it's only needed for specific math stuff?[

You can disable the web plugin, sure. But then there'll be that day where you need to enable it for whatever site, and that's a pain.

You can use Click To Play (that's how I do it) but uneducated users click "Yes" to anything, they've been trained to do so. The most obvious evidence of this is the proliferation of software that's packaged with other software ie: ask toolbar, babylon, etc.

So a solution like AppArmor, which works whether the code is run or not, is ideal for Java.

Beyond that, for people in many countries Java is a requirement for accessing government/ bank websites.

@Lou21,

> So if one were to keep any executables or scripts (e.g. self made ones) in their home folder then this would actually add considerable security...
Sort of. If an attacker has gained control over Firefox they'll be able to read/write to whichever Home directory Firefox has access to. If this is the case they could simply drop/write their own scripts and execute them. 

A more significant benefit is that a process of UID X can't interact with a process of UID Y. It can't read its address space, or ptrace it, or do much at all to it. Essentially you isolate Firefox from other UIDs. The added benefit of it getting its own Home directory is less significant.

---

### Post by vasa1 on 2013-01-11
> **unspawn said:**
> ... LibreOffice may suggest Java as a dependency but IIRC it's only needed for specific math stuff?
Don't mean to "derail" this thread but ... [http://www.libreoffice.org/get-help/faq/general-faq/does-libreoffice-require-java/](http://www.libreoffice.org/get-help/faq/general-faq/does-libreoffice-require-java/)

---

### Post by lou21 on 2013-01-11
> **snowpine said:**
> Understood; I was merely trying to suggest a simpler method that should be &quot;secure enough&quot; for most users, as well as to let you know that Mozilla developers are concerned about these issues and working to make Firefox as safe & secure as possible. :)

 In that case thank you for posting.

---

### Post by lou21 on 2013-01-11
> **Hungry Man said:**
> There's no way for Javascript to access those files unless the browser provides an interface to do so. If it does provide that interface you can bet that it's handled in some way that wouldn't allow arbitrary access.




@Unspawn,


You can disable the web plugin, sure. But then there'll be that day where you need to enable it for whatever site, and that's a pain.

You can use Click To Play (that's how I do it) but uneducated users click &quot;Yes&quot; to anything, they've been trained to do so. The most obvious evidence of this is the proliferation of software that's packaged with other software ie: ask toolbar, babylon, etc.

So a solution like AppArmor, which works whether the code is run or not, is ideal for Java.

Beyond that, for people in many countries Java is a requirement for accessing government/ bank websites.

@Lou21,


Sort of. If an attacker has gained control over Firefox they'll be able to read/write to whichever Home directory Firefox has access to. If this is the case they could simply drop/write their own scripts and execute them. 

A more significant benefit is that a process of UID X can't interact with a process of UID Y. It can't read its address space, or ptrace it, or do much at all to it. Essentially you isolate Firefox from other UIDs. The added benefit of it getting its own Home directory is less significant.

 Interesting. Thank you.

---

### Post by vasa1 on 2013-01-11
> **Hungry Man said:**
> ...
Beyond that, for people in many countries Java is a requirement for accessing government/ bank websites.
...
The sad thing is that many of these Java-loving banks also love another operating system as is implied here: [How do I install 'proper' anti-virus protection for Online Banking satisfying its Terms of Use?]("http://askubuntu.com/q/236891/25656")

The other point which may already have been mentioned is that many of these exploits, Java or not, are "social" with a high degree of PEBKAC.

---

### Post by unspawn on 2013-01-12
> **Hungry Man said:**
> You can disable the web plugin, sure. But then there'll be that day where you need to enable it for whatever site, and that's a pain. (..) Beyond that, for people in many countries Java is a requirement for accessing government/ bank websites.
No, for me it isn't, I know where I need to have Java enabled. Looking purely at minimizing risks doesn't white listing allow for *way less exposure* compared to a reactive, after-the-fact black listing approach? And configuring a browser plug-in to allow Java for a specific site may be inconvenient but it's only once per site.


> **Hungry Man said:**
> (..) uneducated users click "Yes" to anything, (..)So a solution like AppArmor, which works whether the code is run or not, is ideal for Java.
OK, so then the list of realistic first measures to take could become:
- enable the AppArmor Java profile regardless,
- enable Java for only specific sites,
- and be educated wrt "browsing hygiene",
...and not necessarily running the browser under another UID? Sure it may mitigate some aspects but I still doubt it could prevent any problems caused by browsers themselves, plugins let alone social engineering. 

IMHO reality shows the only boundary is the economics of malware as current Java-based malware shows its clients do not consider it economical to target a platform with aprox. two per cent market share. Mitigation-wise the often-used counter argument of Linux diversity does not apply when talking about write-once-run-everywhere malware anyway but also because it draws away attention from the *capabilities* malware like Jacksbot seem to possess. To put it more simply: are Java security model problems caused by the *OS* Java runs on or by *Java itself*?..

---

### Post by Hungry Man on 2013-01-12
> No, for me it isn't, I know where I need to have Java enabled. Looking purely at minimizing risks doesn't white listing allow for way less exposure compared to a reactive, after-the-fact black listing approach? And configuring a browser plug-in to allow Java for a specific site may be inconvenient but it's only once per site.
If whitelisting works for you, by all means, go for it. I use click to play myself. I just mean that it isn't a great solution generically, for the average user.

> OK, so then the list of realistic first measures to take could become:
- enable the AppArmor Java profile regardless,
- enable Java for only specific sites,
- and be educated wrt "browsing hygiene",
...and not necessarily running the browser under another UID? Sure it may mitigate some aspects but I still doubt it could prevent any problems caused by browsers themselves, plugins let alone social engineering. 

Yes, I would suggest all of those things. Running the browser in a separate UID provides benefits, but running in an apparmor profile is a much stricter set of restrictions. You could, of course, do both. 


> IMHO reality shows the only boundary is the economics of malware as current Java-based malware shows its clients do not consider it economical to target a platform with aprox. two per cent market share. Mitigation-wise the often-used counter argument of Linux diversity does not apply when talking about write-once-run-everywhere malware anyway but also because it draws away attention from the capabilities malware like Jacksbot seem to possess. To put it more simply: are Java security model problems caused by the OS Java runs on or by Java itself?..
That's a simple question with a somewhat more complicated answer. The answer is that it's both.

Java, and its developers, are responsible for these vulnerabilities to the extent that they wrote the code, etc. But an operating system is responsible for providing an adequate security model. Java has its own sandboxing, outside of the operating system model, and it's proven to be incredibly weak. Java doesn't make use of any OS provided access control.

These vulnerabilities exist on all operating systems, so it's not as if Linux is doing something wrong here that others are doing right.

---

### Post by unspawn on 2013-01-12
> **Hungry Man said:**
> Java, and its developers, are responsible for these vulnerabilities to the extent that they wrote the code, etc. But an operating system is responsible for providing an adequate security model. Java has its own sandboxing, outside of the operating system model, and it's proven to be incredibly weak. Java doesn't make use of any OS provided access control.
And that indeed is the core problem: DAC is too coarse, MAC does help but in the end there currently is no OS equivalent way to define fine-grained 
"deny this applet to load another applet"-type of controls. Back to the "*whether any security can be gained by running the brower as a seperate user*" question this thread started with, analysis is IMHO best done the other way around (mapping measures to risks) and measures should be chosen based on an *understanding* of threats and applied in order of *effectiveness*.

*BTW +1 for proper attribution in your web log post.

---

