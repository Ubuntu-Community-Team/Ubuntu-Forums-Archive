---
title: "Is there UAC (like Vista's) in Linux?"
date: 2008-03-14
forum: Security Discussions
---

### Post by IPEnthusiast on 2008-03-14
The reason for Vista's slow adoption is UAC. The era of ripping off gullible PC users is somewhat ending with the introduction of UAC in Windows Vista.

Is there some similar functionality in Linux?

Thanks.

---

### Post by aysiu on 2008-03-14
What's UAC?

---

### Post by IPEnthusiast on 2008-03-14
UAC is User Account Control. If enabled, among other things, it prevents the injection of rootkits into Vista.

---

### Post by aysiu on 2008-03-14
I don't think there's a way to prevent the injection of rootkits. If someone authorizes the installation of software that also brings a rootkit along with it, the authorization is there.

---

### Post by IPEnthusiast on 2008-03-14
What UAC does is, it alerts the user to any alteration to the OS. Does Linux have some functionality like this?

Thanks.

---

### Post by eragon100 on 2008-03-14
I'm not exactly certain, but yeah, ubuntu also nagges you with irritating popups asking for your password :(

---

### Post by scorp123 on 2008-03-14
> **eragon100 said:**
>  ubuntu also nagges you with irritating popups asking for your password :( Only if you are about to perform an administrative task, such as performing a software installation. This is not even remotely comparable to UAC which nags you all the time about anything.

**_Cancel or Allow?_**
[http://www.youtube.com/watch?v=l-7C-w8jc0w](http://www.youtube.com/watch?v=l-7C-w8jc0w)

---

### Post by scorp123 on 2008-03-14
> **IPEnthusiast said:**
> What UAC does is, it alerts the user to any alteration to the OS. Does Linux have some functionality like this?  _Simple answer: _

It doesn't need to. Unless you don't do silly stuff as almighty super-user "root" there is no way anyone or anything could even come close to alter the operating system in any way.


_More complex answer:_

There are programs such as **"tripwire"**, **"chkrootkit"** and **"rkhunter"** ... If we do a "**apt-cache show rkhunter**" we get this text: ```
...
Description: rootkit, backdoor, sniffer and exploit scanner
 Rootkit Hunter scans your system for known and unknown rootkits,
 backdoors, sniffers and exploits.
 .
 Some of the tests it does:
   - MD5 hash compare
   - Look for default files used by rootkits
   - Wrong file permissions for binaries
   - Look for suspected strings in LKM and KLD modules
   - Look for hidden files
   - Optional scan within plaintext and binary files
 .
 Please note that rkhunter does *not* guarantee your system has
 not been compromised! You should also run additional tests, e.g. using
 chkrootkit and other measures.
 .
  Homepage: http://rkhunter.sourceforge.net 
... 
```

You will get similar texts from the other programs, e.g. **apt-cache show tripwire**: ```
 ... 
Description: file and directory integrity checker
 Tripwire is a tool that aids system administrators and users in
 monitoring a designated set of files for any changes.  Used with
 system files on a regular (e.g., daily) basis, Tripwire can notify
 system administrators of corrupted or tampered files, so damage
 control measures can be taken in a timely manner.
... 
```

**_The point is: _**

[COLOR="Red"]Those programs are not installed on a default Ubuntu desktop.[/COLOR] For a simple reason: **[COLOR="Red"]_You don't need them._[/COLOR]**

**And this is for the same reasons you don't need a virus scanner on Ubuntu or any sort of spyware removal kit:** For as long as you don't give out your login and your password and for as long as you don't do silly things as almighty super-user "root" there is no way in this Universe how anything could alter your OS behind your back.

But why do these programs exist then?

Servers with multiple accounts are a different story, especially if you have servers facing the Internet (e.g. web servers). Then yes, then those programs make sense and as admin I'd at least install "tripwire" on my Ubuntu Server installations so it keeps me informed about any potentially fishy stuff going on, especially if I am the one having all the responsibility.

A customer I do some sysadmin-tasks for from time to time has like **4000 user accounts on the same machine**. Some of those users have "root" access. But not all of those who have it are really supposed to have it. So yes, in such a scenario where I can't be there all the time to keep **4000+ people** under control all the time I'd definitely install something like **"tripwire"**, **"rkhunter"** and other such tools.
[B]
But as home user? Overkill. You really don't need it.[/B]

_So the precise answer to your question would be:_

No it's not there because you don't really need it. But you can have such programs if you really want to.


Hope this helped to clarify things.

---

### Post by HermanAB on 2008-03-15
Linux has something much stronger, called SElinux, which is built into the kernel:
[http://www.nsa.gov/selinux/](http://www.nsa.gov/selinux/)

On Ubuntu however, it is turned off, since it is hard to manage and a desktop system doesn't normally need to be all that paranoid.  However, you can play with it if you want - find a manual, turn it on and have fun.

---

### Post by scorp123 on 2008-03-15
> **HermanAB said:**
> Linux has something much stronger, called SElinux, which is built into the kernel:
[http://www.nsa.gov/selinux/](http://www.nsa.gov/selinux/)

On Ubuntu however, it is turned off, since it is hard to manage and a desktop system doesn't normally need to be all that paranoid.  Yes, I forgot about that one. Thanks for mentioning it. And then there is **Novell's AppArmor** which e.g. gets built into their **SUSE Linux** products (OpenSUSE has it too), and which recently was also added to Ubuntu:

[http://www.novell.com/linux/security/apparmor/](http://www.novell.com/linux/security/apparmor/)
[http://www.novell.com/linux/security/apparmor/selinux_comparison.html](http://www.novell.com/linux/security/apparmor/selinux_comparison.html)

[https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)
[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)
[http://packages.ubuntu.com/gutsy/base/apparmor](http://packages.ubuntu.com/gutsy/base/apparmor)

---

### Post by handydan918 on 2008-03-15
I have a little different perspective on the OPs question. (Does Linux have something similar to UAC?)

Yes. linux is derived from Unix, and Unix has had user access controls (i.e., users vs. root, sudo) since it's inception in the 60's. 
UAC is merely Microsoft's attempt to, once again, "innovate" by adopting existing technology. 
In this case, it's 40 year old technology. Better late than never, I guess. 
This is why M/S has the terrible security rep it has. Windows was never designed ans a multi-user (read: networked) system. Unix was designed with multi-user security in place from the beginning. Compared to the classic Unix permissions model exemplified by Linux, UAC is a nasty, glued-on kludge.

---

### Post by scorp123 on 2008-03-15
> **handydan918 said:**
>  I have a little different perspective on the OPs question. (Does Linux have something similar to UAC?)  I see what you mean. Yes, from the functionality-POV it has already existed for ages. But I understood it more in this sense: "Is there an interactive program that will nag me all the time about anything as soon as something tries to alter my OS?" ... And to that my answer is as stated above.

 > **handydan918 said:**
>  This is why M/S has the terrible security rep it has.  Yes. 
[http://ubuntuforums.org/showpost.php?p=4238468&postcount=18](http://ubuntuforums.org/showpost.php?p=4238468&postcount=18)

> **handydan918 said:**
>  UAC is a nasty, glued-on kludge.  ... But it makes for some good jokes. I just love the [Apple commercial]("http://www.youtube.com/watch?v=l-7C-w8jc0w") where they parody Vista + UAC :)  (I know ... I already posted this ... but I just can't get enough :lolflag: )

---

### Post by Foster Grant on 2008-04-13
UAC is none of that.

According to a Microsoft official, it was designed specifically to annoy users.

[http://arstechnica.com/news.ars/post/20080411-vistas-uac-security-prompt-was-designed-to-annoy-you.html](http://arstechnica.com/news.ars/post/20080411-vistas-uac-security-prompt-was-designed-to-annoy-you.html)

It pops up every time an application tries to elevate priveleges. It's not a security barrier, like a password. It only exists so end users will pressure app vendors into writing software that doesn't elevate priveleges.

Which brings to mind an obvious point: If application developers can be convinced to write software that doesn't elevate priveleges, [so can malware developers](http://arstechnica.com/news.ars/post/20070430-microsofts-guru-malware-and-viruses-will-evolve-on-vista.html).

---

### Post by kutjara on 2008-04-13
> **Foster Grant said:**
> UAC is none of that.

According to a Microsoft official, it was designed specifically to annoy users.

[http://arstechnica.com/news.ars/post/20080411-vistas-uac-security-prompt-was-designed-to-annoy-you.html](http://arstechnica.com/news.ars/post/20080411-vistas-uac-security-prompt-was-designed-to-annoy-you.html)

It pops up every time an application tries to elevate priveleges. It's not a security barrier, like a password. It only exists so end users will pressure app vendors into writing software that doesn't elevate priveleges.

Which brings to mind an obvious point: If application developers can be convinced to write software that doesn't elevate priveleges, [so can malware developers](http://arstechnica.com/news.ars/post/20070430-microsofts-guru-malware-and-viruses-will-evolve-on-vista.html).

That sounds like a bit of revisionist history from MS, trying to cover the fact that UAC has been scorned in the marketplace. When it was launched, UAC was touted as this powerful security tool that would protect users from the big bad world. Now, it's been demoted to just a nuisance aimed at changing software developers' behavior. Yeah, right. Nice try Microsoft.

---

### Post by finferflu on 2008-04-13
<almost off-topic>
This makes me think: what happened to the Windows "just works" approach? Now the responsibility is back on the user, and it's back in terms of knowledge: the user needs to be aware of what's going on, and has the power to allow or stop processes, according to his/her own understanding of it. It seems that RTFM is valid, now as never before for Vista, and the so called ease-of-use, as MS promotes it, reveals its flaws. 
To operate a machine, you need to know *at least* how it works, and Linux was condemned so much because of the need of reading manuals...
</almost off-topic>

---

### Post by mrsteveman1 on 2008-04-13
UAC is a privilege escalation mechanism to interact with the integrity levels in Vista, it isn't the same thing as merely launching a process with a new UID, which is what sudo does.

Integrity levels are a sort of access control built in to the kernel in Vista, the closest thing i can think of in linux is RBAC or SElinux, though those are a bit more fine grained than IL and serve somewhat different purposes. 

For an example of something that uses IL in Vista, IE7 protected mode runs in the low integrity level, so in theory it isn't capable of interacting with anything running in any other integrity level, though i'm not sure how well it holds up to attack.

If the user on a Vista system is not set as an admin, they will also have to enter a password in the UAC prompt, so it is also a security method as well, to prevent random users from changing things. Microsofts reasoning that it annoys users is perfectly valid, most programs shouldn't require such high privilege on a system, and perhaps developers will take notice and stop doing it in the future. 

The same thing is true of Linux and OS X, they both require passwords to change certain things, and rightly so.

---

### Post by IPEnthusiast on 2008-04-13
> **Foster Grant said:**
> UAC is none of that.

According to a Microsoft official, it was designed specifically to annoy users.

[http://arstechnica.com/news.ars/post/20080411-vistas-uac-security-prompt-was-designed-to-annoy-you.html](http://arstechnica.com/news.ars/post/20080411-vistas-uac-security-prompt-was-designed-to-annoy-you.html)

It pops up every time an application tries to elevate priveleges. It's not a security barrier, like a password. It only exists so end users will pressure app vendors into writing software that doesn't elevate priveleges.

Which brings to mind an obvious point: If application developers can be convinced to write software that doesn't elevate priveleges, [so can malware developers](http://arstechnica.com/news.ars/post/20070430-microsofts-guru-malware-and-viruses-will-evolve-on-vista.html).

Well, if an app elevates privileges, it can do things like accessing OS directories, files, etc. and modify them, which is what an app would do to inject a rootkit and UAC would alert the user to that happening.

---

### Post by scorp123 on 2008-04-13
> **IPEnthusiast said:**
>  ... and UAC would alert the user to that happening. Nope it doesn't. UAC only asks you to allow certain priviledges or not ... But it doesn't really tell you what's really going on. Or why else do Vista users still need virus scanners and protection from malware? :)

---

### Post by netlogic on 2008-04-13
> **aysiu said:**
> I don't think there's a way to prevent the injection of rootkits. If someone authorizes the installation of software that also brings a rootkit along with it, the authorization is there.

Agree. If Ms stil believes all software use installer such as msi, setup.exe, and install.exe, they are still stuck with Windows 95. Injecting a dll doesn't always require an administrative level. UAC doesn't work. It was busted during the beta release and after SP1, still busted.

---

### Post by netlogic on 2008-04-13
> **HermanAB said:**
> Linux has something much stronger, called SElinux, which is built into the kernel:
[http://www.nsa.gov/selinux/](http://www.nsa.gov/selinux/)

On Ubuntu however, it is turned off, since it is hard to manage and a desktop system doesn't normally need to be all that paranoid.  However, you can play with it if you want - find a manual, turn it on and have fun.

However, I don't want install, break, and spend 6hrs to fix it.

---

### Post by mrsteveman1 on 2008-04-13
SElinux is great for what it is supposed to be used for, and that is locking down servers etc to a paranoid degree. It is both useless and unnecessary for home machines, because the policy is insane and impossible for anyone to figure out, and i've tried for a long time. 

This is likely why Linus was so opposed to letting SElinux be the only in-kernel security mechanism, it isn't adequate for a lot of purposes and can't be adapted for others. I believe his words were "you security people are insane" :D

Apparmor on the other hand, is excellent in certain home situations, like sandboxing a web browser or apache, which is what lots of people use it for now.

---

### Post by scorp123 on 2008-04-14
> **mrsteveman1 said:**
>  Apparmor on the other hand, is excellent in certain home situations, like sandboxing a web browser or apache, which is what lots of people use it for now. Yes, and it seems AppArmor is establishing itself as a sort-of standard in the corporate world ... I know many places where they use it to lock down their servers, and setting up AppArmor isn't so difficult. There are many good manuals out there. SELinux on the other hand is a PITA.

---

### Post by Duckyspetrie on 2008-04-15
Asking for the root/sudo password when you attempt to install anything is equivalent to Vista's UAC. There are also ways to change the timeout time for asking for your password (either more often or less often). Admittedly, I'm not exactly sure how to do it. Hope this helps. BTW, UAC doesn't prevent the installation of rootkits, it is simply another precautionary measure Microsoft was five years behind in implementing...

---

### Post by IPEnthusiast on 2008-04-15
> **scorp123 said:**
> Nope it doesn't. UAC only asks you to allow certain priviledges or not ... But it doesn't really tell you what's really going on. Or why else do Vista users still need virus scanners and protection from malware? :)

I agree that UAC can tell the user more. And Windows users can use all the help they can get, including UAC, virus scanners, malware protection, etc.

And are you actually claiming that Linux is more user-friendly than Windows? I plan to do some things with Linux, and I'm only brave enough to approach it since I've been developing software for well over a decade. For the average user that visits some websites to buy something, Windows is way more user-friendly than Linux.

And I think Windows is way more programmer-friendly, too.

---

### Post by scorp123 on 2008-04-15
> **IPEnthusiast said:**
>  And are you actually claiming that Linux is more user-friendly than Windows?  That's a "personal taste" thing one can't really argue about. For me it is and I use Linux since 1996. I started with an early release of "SuSE Linux" (now owned by Novell Inc.) and in 2005 switched over to Ubuntu. So for me Linux is also "friendly" because that's the OS I have been using for the past 12 years. Being used to something also plays an important role on how "friendly" something is or isn't.

For many others Linux isn't "friendly" enough and that opinion is just as valid. Everybody should use the OS they are most comfortable with. So for some the right answer to that is Linux. For others it's Windows or Mac OS X ... or something else, e.g. Solaris, FreeBSD, BeOS, OS/2 ... 

> **IPEnthusiast said:**
>  I plan to do some things with Linux, and I'm only brave enough to approach it since I've been developing software for well over a decade.  If you just want to give it a test-ride you could e.g. install it without any risks into a virtual machine, e.g. VMware or VirtualBox or something similar. With that you could test it but would not have to sacrifice any disk space or risk losing your Windows installation by potentially doing something wrong during the installation.

Just bear in mind please: Linux is not Windows, so certain things definitely will be different and may appear to be unusual to you.

> **IPEnthusiast said:**
>  For the average user that visits some websites to buy something, Windows is way more user-friendly than Linux.  And why that? I regularly order stuff online and so far never ever had troubles with anything.

> **IPEnthusiast said:**
>  And I think Windows is way more programmer-friendly, too.  If you know your ways around then every system will be "friendly" to you. It's a matter of being used to it. And given the many thousand of volunteers who program and develop stuff for Linux you can't really argue that Linux is "unfriendly" to programmers. The contrary is the case, people are being encouraged to take the source code and help enhance it.

---

### Post by netlogic on 2008-04-15
na...
I don't think you understand how antivirus and malware detection work. They will not protect you from everything. Some antivirus are mostly focused on signature files.

---

### Post by netlogic on 2008-04-15
This is why Windows suck. In the past week, hackers are taking advantage of Flash vulnerabilities for Windows. Flash bug only affects Windows. Privilege escalation didn't work for Linux or xBSD. Programmers are now putting rootkit through FLASH. Your malware protection apps will not protect you from it, because API is handled by Flash. Malware protection will only pick it up after it is installed, which is the post scan.

[http://www.theregister.co.uk/2008/04/15/pro_tibet_trojan/](http://www.theregister.co.uk/2008/04/15/pro_tibet_trojan/)

Who cares it is a bit more secure. That is like saying it feels better to have sex without a condom. Like I have been saying for last few months, these protection software for Windows isn't full prove. The signature based software will only catch 40%.

---

### Post by netlogic on 2008-04-15
In case someone jumps in and say why I am such a Windows hater. I work with Windows for over a decade now. It is impossible to make them secure or make them reliable. The only reason Windows seems to work flawlessly in a corporate environment is many admins spend a great amount of time in the background trying to prevent bad things from happening. I find Windows to be a pure garbage. They make the OS and ask everyone to fix them, so they can make more money. If they spend more money on developments and R&D instead of their lawyers, they actually might have a better product.

---

### Post by mrsteveman1 on 2008-04-15
A competent antivirus program should be able to detect a compromise regardless of how it happens, because they usually hook into the kernel and intercept syscalls and file accesses.

Of course, most AV are completely INcompetent and thus can't really protect users anyway. If Windows had been protecting its own APIs and services in the first place this mess wouldn't be necessary.

---

### Post by scorp123 on 2008-04-15
> **mrsteveman1 said:**
>  If Windows had been protecting its own APIs and services in the first place this mess wouldn't be necessary. Exactly! #-o

Same with their firewall ... Windows wouldn't need it if it didn't have tons of network daemons running in the background out of the box in the first place. And I am talking their home OS'es here.

---

### Post by IPEnthusiast on 2008-04-17
> **scorp123 said:**
> That's a "personal taste" thing one can't really argue about. For me it is and I use Linux since 1996. I started with an early release of "SuSE Linux" (now owned by Novell Inc.) and in 2005 switched over to Ubuntu. So for me Linux is also "friendly" because that's the OS I have been using for the past 12 years. Being used to something also plays an important role on how "friendly" something is or isn't.

For many others Linux isn't "friendly" enough and that opinion is just as valid. Everybody should use the OS they are most comfortable with. So for some the right answer to that is Linux. For others it's Windows or Mac OS X ... or something else, e.g. Solaris, FreeBSD, BeOS, OS/2 ... 

 If you just want to give it a test-ride you could e.g. install it without any risks into a virtual machine, e.g. VMware or VirtualBox or something similar. With that you could test it but would not have to sacrifice any disk space or risk losing your Windows installation by potentially doing something wrong during the installation.

Just bear in mind please: Linux is not Windows, so certain things definitely will be different and may appear to be unusual to you.

 And why that? I regularly order stuff online and so far never ever had troubles with anything.

 If you know your ways around then every system will be "friendly" to you. It's a matter of being used to it. And given the many thousand of volunteers who program and develop stuff for Linux you can't really argue that Linux is "unfriendly" to programmers. The contrary is the case, people are being encouraged to take the source code and help enhance it.

I'm focusing on developing some business applications these days, so I really don't need access to the OS source code. But, soon in the future, I'll have to do some infrastructure development - and I'll need access to an IPv6 implementation, so I'll probably need an OS that comes with source code. So, I'll probably work with Linux for that.

Is Mac OS X based on some open source OS? If it is, is the Mac OS X source code available to the public?

Thanks.

---

### Post by scorp123 on 2008-04-17
> **IPEnthusiast said:**
>  I'll need access to an IPv6 implementation, so I'll probably need an OS that comes with source code.  Please pay attention to the license the source code is published under! Many companies and programmers fall into this trap ... so please make sure you really understand the licenses the source code is published under and make sure you follow it. Most things related to Linux are published under the GNU General Public License "GPL". In short, you are allowed to take source code from GPL programs and use them in your own programs but as soon as you distribute your derived work the GPL insists you publish the source code too so that the source code may remain open.
 Wikipedia has the details:
[http://en.wikipedia.org/wiki/GNU_General_Public_License](http://en.wikipedia.org/wiki/GNU_General_Public_License)

In contrast to that the BSD License allows you to take their source code and you may do with it as you please for as long as you leave their copyright messages intact ... Wikipedia:
[http://en.wikipedia.org/wiki/BSD_licenses](http://en.wikipedia.org/wiki/BSD_licenses)

> **IPEnthusiast said:**
>  Is Mac OS X based on some open source OS? If it is, is the Mac OS X source code available to the public?   The lower layers of Mac OS X are known as the "Darwin" operating system. See here:
[http://en.wikipedia.org/wiki/Darwin_%28operating_system%29](http://en.wikipedia.org/wiki/Darwin_%28operating_system%29)

Darwin and its source code are available under Apple's Public Source License. See here:
[http://en.wikipedia.org/wiki/Apple_Public_Source_License](http://en.wikipedia.org/wiki/Apple_Public_Source_License)

The higher layers however (e.g. the GUI of Mac OS X) are closed-source and the property of Apple Inc.

---

