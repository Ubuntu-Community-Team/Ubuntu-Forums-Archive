---
title: "I need Anti- Virus for Ubuntu 11.10 (64-bit)"
date: 2011-12-04
forum: Security
---

### Post by Calculon64 on 2011-12-04
I need Anti- Virus for Ubuntu 11.10 (64-bit)

Yes I have read and heard many times how safe Linux is ... blah, blah, blah.  I don't really care how safe it is because I already know.  My problem is that I have Ubuntu 11.10 (64-bit) installed on a secondary PC on my work network.  I want to play it safe and need real time protection and not some virus scanner I have to launch manually.  I want something I can install and have running all the time.  Not something running on the background that I cannot see.  I want something that displays an icon near the time and date on the task bar.  I want to show that I have anti-virus on this thing and not a make believe half excuse of anti-virus app.

Please advice.

---

### Post by bluexrider on 2011-12-04
there are a few clamAV, avast, BitDefender or AVG

> **Calculon64 said:**
> I need Anti- Virus for Ubuntu 11.10 (64-bit)

Yes I have read and heard many times how safe Linux is ... blah, blah, blah.  I don't really care how safe it is because I already know.  My problem is that I have Ubuntu 11.10 (64-bit) installed on a secondary PC on my work network.  I want to play it safe and need real time protection and not some virus scanner I have to launch manually.  I want something I can install and have running all the time.  Not something running on the background that I cannot see.  I want something that displays an icon near the time and date on the task bar.  I want to show that I have anti-virus on this thing and not a make believe half excuse of anti-virus app.

Please advice.

---

### Post by OpSecShellshock on 2011-12-04
Short answer is the thing you are looking for doesn't exist. There are no heuristic AV scanners that would alert/block based on behavior or otherwise constantly run and detect malware at the time of access. The AV software listed above (and any others available as far as I know) will need to be run manually, will probably throw out mostly false positives if anything, and will just be scanning for Windows malware anyway.

---

### Post by sammiev on 2011-12-04
[BitDefender]("https://help.ubuntu.com/community/BitDefender") can manually scan all recent files in usually less than a min if scanning once a day. OpSecShellshock gave it to you just like what it is. [Avast]("http://www.avast.com/linux-home-edition") is much the same as I play with both of them. clamAV is great at given you false positives.

---

### Post by Dangertux on 2011-12-04
> **OpSecShellshock said:**
> Short answer is the thing you are looking for doesn't exist. There are no heuristic AV scanners that would alert/block based on behavior or otherwise constantly run and detect malware at the time of access. The AV software listed above (and any others available as far as I know) will need to be run manually, will probably throw out mostly false positives if anything, and will just be scanning for Windows malware anyway.


This is correct. There really is nothing like this on Linux (for free)

[http://www.mcafee.com/us/products/virusscan-enterprise-for-linux.aspx](http://www.mcafee.com/us/products/virusscan-enterprise-for-linux.aspx)

That's a decent choice if you're willing to shell out big bucks. It provides on-access (active) heuristic and definition based scanning for both Linux and Windows malware. It also supports Ubuntu. The catch it costs $154 because you have to buy 5 licenses as a minimum.

---

### Post by dd76 on 2011-12-06
Also I believe ESET has a linux version now.  I use it on my Windows partition and it is fantastic very lightweight and effective.  The initial cost for a 3 computer License is priced similar to Norton but after the first subscription they give an excellent discount.  Though in truth I haven't had a problem with my setup (2 windows machines and a dual boot win7/ubuntu) so I don't worry, though a healthy dose of paranoia is perfectly normal (remember it only takes being right once to make it all worth it)

---

### Post by Lars Noodén on 2011-12-06
> **Dangertux said:**
> This is correct. There really is nothing like this on Linux (for free)

[http://www.mcafee.com/us/products/virusscan-enterprise-for-linux.aspx](http://www.mcafee.com/us/products/virusscan-enterprise-for-linux.aspx)

That's a decent choice if you're willing to shell out big bucks. It provides on-access (active) heuristic and definition based scanning for both Linux and Windows malware. It also supports Ubuntu. The catch it costs $154 because you have to buy 5 licenses as a minimum.

Could five people go in on a set of licenses or do they all have to be for the same owner?

---

### Post by OpSecShellshock on 2011-12-06
> **Lars Noodén said:**
> Could five people go in on a set of licenses or do they all have to be for the same owner?

Well it should theoretically be possible to set up a five-person "enterprise." However are we sure this product doesn't mostly exist as a solution to an unchecked box on a compliance sheet somewhere?

---

### Post by collisionystm on 2011-12-06
> **Calculon64 said:**
> I need Anti- Virus for Ubuntu 11.10 (64-bit)

Yes I have read and heard many times how safe Linux is ... blah, blah, blah.  I don't really care how safe it is because I already know.  My problem is that I have Ubuntu 11.10 (64-bit) installed on a secondary PC on my work network.  I want to play it safe and need real time protection and not some virus scanner I have to launch manually.  I want something I can install and have running all the time.  Not something running on the background that I cannot see.  I want something that displays an icon near the time and date on the task bar.  I want to show that I have anti-virus on this thing and not a make believe half excuse of anti-virus app.

Please advice.


[http://www.eset.eu/products/nod32-for-linux](http://www.eset.eu/products/nod32-for-linux)

---

### Post by DodgeV83 on 2011-12-07
> **Calculon64 said:**
> I need Anti- Virus for Ubuntu 11.10 (64-bit)

Yes I have read and heard many times how safe Linux is ... blah, blah, blah.  I don't really care how safe it is because I already know.  My problem is that I have Ubuntu 11.10 (64-bit) installed on a secondary PC on my work network.  I want to play it safe and need real time protection and not some virus scanner I have to launch manually.  I want something I can install and have running all the time.  Not something running on the background that I cannot see.  I want something that displays an icon near the time and date on the task bar.  I want to show that I have anti-virus on this thing and not a make believe half excuse of anti-virus app.

Please advice.

Taken from the [Security sticky]("http://ubuntuforums.org/showthread.php?t=510812"):


**[SIZE="3"]Viruses[/SIZE]**

The fact of the matter is: viruses/worms take advantage of flaws or holes in the code. At this time of this writing, there are no significant Linux viruses "in the wild". Linux boxes are no less targets than any other OS, many of the large (ie valuable) Internet sites run on *nix so there is no lack of motivation to crack into *nix.

Do not believe the suggestion that the Linux community is complacent or "behind the times" in terms of viruses, or any other security issue. Linux developers have not "ignored" viruses, rather the OS is built to be highly resistant to them and since the code is "Open" there are literally thousands of eyes watching ...

This is an example of what it would take to install malware on an Ubuntu box:

Install [evilmalware]("http://www.gnu.org/fun/jokes/evilmalware.html")

(Don't worry, that link will NOT install anything )

**For the most part, Linux anti-virus programs scan for Windows viruses which do not run on Linux.** There are increasing reports, however, that Windows malware may run in wine, as such I added a section reviewing what I feel you should know about security if you choose to install and run wine (see below).

Please understand, anti-virus programs, and in fact most HIDS, are "reactive" in that they can only protect you from known viruses. They can only protect you against malware after it is developed and incroporated into HIDS, not before. Furthermore the "fix" will be to close any hole(s) in the code, these fixes will be available through security updates (which are more frequent in Linux then your previous OS if you are coming from Windows).

Reasons AGAINST antivirus on Ubuntu:
[LIST=1]
[*]They scan primarily for Windows viruses.
[*]    There is a high rate of false positives.
[*]    Isolation/inoculation is poor.
[*]    And currently there are no known active Linux viruses (so there is essentially nothing to detect).
[/LIST]


Reasons FOR antivirus on Ubuntu:

[LIST=1]
[*]You are running a file or mail server with Windows clients.
[*]    You wish to scan files before transferring them, by email, flash drive, etc., to a Windows machine.
[/LIST]


Running antivirus can make some sense if you are intending to "protect" Windows users, however, IMO, for a variety of reasons, it is best if Windows users learn to protect themselves.

Note: There have been many documented cases in Windows and Linux that a buffer overflow in an antivirus product has been an attack vector!

If you would like to run an antivirus program on Ubuntu you have several choices :

    Antivirus
    ClamAV
    [http://www.avast.com/eng/avast-for-l...rkstation.html](http://www.avast.com/eng/avast-for-l...rkstation.html)
    [http://www.pandasoftware.com/download/linux.htm](http://www.pandasoftware.com/download/linux.htm)
    [http://www.centralcommand.com/linux_server.html](http://www.centralcommand.com/linux_server.html)
    [http://www.f-prot.com/products/home_use/linux/](http://www.f-prot.com/products/home_use/linux/)

---

### Post by Dangertux on 2011-12-07
> **OpSecShellshock said:**
> Well it should theoretically be possible to set up a five-person "enterprise." However are we sure this product doesn't mostly exist as a solution to an unchecked box on a compliance sheet somewhere?

Haha you're partially right as to its existence. Though at this point isn't any AV pretty much a check the box. 

On the topic Ive done a little bit of testing against that product and it's pretty much on par with it's Windows counterparts more or less. To Lars I think as long as you come up with the money I don't think it matters what machines the licenses go to. They don't ask for incorporation documents when you purchase so.. Take it for what you will

---

