---
title: "Do Not Use the Firefox bundled with Ubuntu LTS 24.04 (explained)"
date: 2024-05-02
forum: Security
---

### Post by vbgf3 on 2024-05-02
a. It is written in the old style unix coding practice. It relies on an army of helpers in /bin, especially on initialization. Although the included Apparmor profile lists them out, thus identifying them and constrains the app bundle. It does not help that an attacker has access to this army of utilities, significantly easing her attack.


b. A snap or flatpak or docker just bundles the correct libraries and correct utilities an app requires. It protects the Integrity of the app itself. And the virtualization of a snap makes it impossible to modify that bundle. But who says the attacker has to modify the bundle? Firefox has a big @{HOME}/snap/firefox directory where it stores it's scripts and settings. My red team has demonstrated that they can gain persistance there and setup monitoring.


c. There exists a directory named StartupCache inside Firefox's settings directory. In there is a bin cache file that supposedly stores multiple startup scripts, ready to be extracted and run. This arrangement cannot be protected by Apparmor, which relies on having discrete script files and program files which Apparmor can either allow or disallow. Having them all stored in a single bin cache is just un-securable.


Lets face it, you are at risk when you use the Ubuntu bundled Firefox even with it's bundled Apparmor profile. The attack technique demonstrated is probably not unique; other seasoned attackers would have arrived at the same approach. Use a properly defined Apprmor profile for your browser and make sure it constrains any program/script execution inside the browser's own settings directory, where an attacker will probably first land.

---

### Post by TheFu on 2024-05-02
No program, especially modern browsers, running on a computer is safe.  Data can always become corrupted whether it be cached or created locally or copied in.  We trust that the snap/deb/flatpak/PPA is provided by trustworthy people who aren't trying to screw everyone.  Sometimes that fails.

The snap subsystem limits access to other parts of the file system for write access.  There are other constraint systems available as well.

The Linux kernel is written using "old style unix coding practices", so by that reasoning, nobody should run Linux.  But MS-Windows is written using MS-DOS style coding practices, so we cannot trust it either.  Keep that line of thought and soon, you'll be living in a cave afraid to leave.

Did you report the issue to the Mozilla bug and security team?  What was their response?

---

### Post by vbgf3 on 2024-05-03
The "old style unix coding practice' I should have explained more on. I was referring to the way the main Firefox app relies on system bins as helpers to perform a core function - like initializing the settings directory. A modern day app would have done this within the app itself, without the need for external utilities.The included bins in that Apparmor profile was VERY generous; I doubt every single one of the mentioned bins is needed. You should know the way unix things are traditionally cobbled together. That way of doing things requires a long list of bundled things to be included in an Apparmor profile.Which aids an attacker.It simply gives the attacker more tools to use. 

I am aware that a browser has tons of features and moving parts, the display engine, the jscript interpreters and other language and protocol requirements. And they keep adding more. They fix one CVE in one release and another one arrives. My job is to protect the user as best I can. And I call out bad practices that don't fit modern protection mech like Apparmor.

I must admit I haven't looked into the full protection capabilities of snap. Maybe Firefox is well protected by snap. I will investigate.

---

### Post by TheFu on 2024-05-03
> **vbgf3 said:**
> The "old style unix coding practice' I should have explained more on. I was referring to the way the main Firefox app relies on system bins as helpers to perform a core function - like initializing the settings directory. A modern day app would have done this within the app itself, without the need for external utilities.The included bins in that Apparmor profile was VERY generous; I doubt every single one of the mentioned bins is needed. You should know the way unix things are traditionally cobbled together. That way of doing things requires a long list of bundled things to be included in an Apparmor profile.Which aids an attacker.It simply gives the attacker more tools to use. 

I am aware that a browser has tons of features and moving parts, the display engine, the jscript interpreters and other language and protocol requirements. And they keep adding more. They fix one CVE in one release and another one arrives. My job is to protect the user as best I can. And I call out bad practices that don't fit modern protection mech like Apparmor.

I must admit I haven't looked into the full protection capabilities of snap. Maybe Firefox is well protected by snap. I will investigate.

I prefer firejail over snaps. With firejail, I have control over the constraints, unlike with snaps.
I still use startup files with my programs to set environment variables needed for the code.  Sometimes I use that start script to figure out the location the program is being run, though getting that 100% correct is more complex than it should be when there are hardlinks, softlinks and starting apps can use all sorts of convoluted relative paths.  Figuring out which directory a program is being run from with 90% accuracy iis really easy.  But the last 10% of possible cases is really ugly.   This assumes the program even needs to know which directory it is being run from.  Instead, I'll often just make a config file hierarchy be used, shifting the responsibility to the user.

I will agree that programs which require a specific PWD can be bad. Best to code in a way that the PWD doesn't matter.

---

### Post by vbgf3 on 2024-05-03
Hi,

I don't understand why you said "[COLOR=#000000]Figuring out which directory a program is being run from with 90% accuracy iis really easy. But the last 10% of possible cases is really ugly. "

[/COLOR]I use strace to build my Apparmor rules. First I strace the program doing the things I do. Then I remove the lines that mentions 'file not found' or something like that - programs are built to function in different distros. Then I grep out the lines that start with 'openat' which gives the lines of things the app tries to use. From that, extract the stuff in between quotes. There then you have all the things the app uses.

Then I build the Apparmor profile with sed.
I append mr to lines that mention libraries, and I append r to all other lines. 
I have a small paragraph of things usually required like /proc/*/stat and others, which were generalized from strace outputs prior.
Add the path of where the app is and you're basically done.

This approach failed with the latest ver 125 of Chrome which failed to utilize my YubiKey PassKey. But I noticed that Firefox is able to. So I included some of what the Firefox profile have which I don't have - which are basically dbus things and a few /dev things. The end result worked and I am too lazy to figure out what was truely missing using the approach which I used successfully previously.

I am not a wiz with regular expressions, used by grep and sed. When I fail, I use Google's Gemini AI to construct the lines I need. (Caution: the AI requires precise descriptions of what you want). Out of practice programmer - new tools. :)

I agree that profiles built without explicit paths are better. But then, I intend the profile to be used only with a particular distro. Not universally re-usable code, but it suffices. The technique is fast.

Are you a contributing developer for firejail ?

---

### Post by TheFu on 2024-05-03
> **vbgf3 said:**
> Hi,

I don't understand why you said "Figuring out which directory a program is being run from with 90% accuracy iis really easy. But the last 10% of possible cases is really ugly. "

I was a developer for 20+ yrs.  You and I are coming at this from completely different perspectives.  The OS/shell can report on where a program is run from, but it isn't always correct using the most common tools, like **whence** or parsing $0 aka arg[0].  That's the 90% solution that is usually good enough, but not always.  For example, if a program comes with these directories:
```
ProgramA
&#9500;&#9472;&#9472; bin
&#9500;&#9472;&#9472; doc
&#9500;&#9472;&#9472; etc
&#9500;&#9472;&#9472; lib
&#9492;&#9472;&#9472; man

```
and the program and/or startup script is in the bin/ directory, it makes sense to assume that configuration files would be in etc/, help pages would be in doc/ and libraries would be in lib/, right?  So we'd look at $0 to get the location of the program and strip off the bin/programa part hoping to be left with the location of ProgramA directories.  But depending on how programA was started, that value may be less useful and end with libraries, documentation and config files inaccessible.  This is why a program start script will often have an environment variable, say JAVA_HOME, to answer the question definitively.

Anyway, probably not what you assumed I meant.

<snip>

> **vbgf3 said:**
> 
I agree that profiles built without explicit paths are better. But then, I intend the profile to be used only with a particular distro. Not universally re-usable code, but it suffices. The technique is fast.

Are you a contributing developer for firejail ?

No, I'm just a happy user of firejail. There are some other, similar, tools that could be better for different situations.  As you know, security is hard. There are often edge conditions that few people understand that someone just happy to have a working program, much less one that is secure too, would be hard to know and understand.  It is significantly more difficult when doing cross-platform coding.  In my prime, my team supported 13 platforms.  We counted MS-Windows as 1, though there were 4 very different releases at the time.  I suppose we could have claimed 17 platforms then. ;)

---

### Post by currentshaft on 2024-05-07
an

---

### Post by 909mjolnir on 2024-05-25
Thanks for your commentary.  
Personally, I find the web browser makers to be very offensive and gutsy with that they tend to do us in terms of security holes.  
The only thing I like about Firefox is the about:config when I turn some stuff off|on and reduce max connections.  Athought, Chrome has many of the same plusses and minusses.  I'm not sure what to do about all this.  

It's so hard.  Just this year I finally figured out that I get hacked a lot more when I use wifi instead of ethernet.

---

