---
title: "Second opinion on this please"
date: 2007-07-16
forum: The Cafe
---

### Post by euler_fan on 2007-07-16
NOTE: Sorry if this is more a "Servers and Security" thing, but the "before you post" there said they were pretty much servers only. If it should be there, please move it there. END NOTE

Should I be worried about this . . . 

The long and short of it is that the other day I had Firestarter in the system tray and it was reporting a number of hits from various IP addresses against port 5900. They were coming in once every 5-20 minutes (about 40 hits total though the afternoon). I was noticing some hits against SAMBA on port 137 most times I sent an email through my school's servers and a second one on port (based on what was returned from looking up the host names of the ip addresses reported).  This behavior from the school's servers has continued, but the hits against VNC have stopped (or at least, they are not appearing in the log file as shown by Firestarter over the next several days).

I don't use VNC, Firestarter has been told to configure my firewall to log everything and let nothing in and drop all rejected packets silently. I run Thunderbird and connect to my school's servers using regular imap/smtp on the default ports.

So, I sent my logs and a summary of what I know and my setup (basically what I have written above) to my school's tech people (I was curious about the SAMBA thing anyway) and their response is that (1) their servers should not be pinging port 137 for any reason they can think of. (2) I'm probably acting as a relay for spam, and (3) I should probably re-image my hard drive.

My uni is pretty much a Windows only world, no support outside of their IT program (at as far as I know only the graduate level no less) for *nix/Solaris and little enough for Mac.

I was thinking about burning a Knoppix disk or using my Fesity live CD to go in on a live CD and clamscan and rootkit scan my machine to see if there's anything there.

Rkhunter (as of time of posting) says to check these out . . .
/etc/.pwd.lock
/etc/.java /dev/.static
/dev/.udev
/dev/.initramfs
/dev/.initramfs-tools 

chkrootkit found this
Searching for suspicious files and dirs, it may take a while... 
/usr/lib/firefox/.autoreg
/usr/lib/jvm/.java-gcj.jinfo
/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/.systemPrefs
/usr/lib/jvm/.java-1.5.0-sun.jinfo
/usr/lib/j2se/1.4/jre/.systemPrefs
/usr/lib/j2se/1.4/jre/.systemPrefs/.systemRootModFile
/usr/lib/j2se/1.4/jre/.systemPrefs/.system.lock
/lib/modules/2.6.17-11-386/volatile/.mounted
/usr/lib/j2se/1.4/jre/.systemPrefs

OBSD rk v1... /usr/lib/security
/usr/lib/security/classpath.security

I am more than willing to post them all as attachments upon request.

Since it looks like there might be one, does anyone have a suggestion about how to remove it?

Thanks much.

Euler_fan

Their response is below:
******************************************
It is our opinion that your computer could likely be compromised, and
could possibly be being used as a relay server (probably for spam).

Here's why we think you may be compromised:
-Our mail servers do not connect via a SMB share (in fact no known mail
servers use SMB connections for mail traffic).  The traffic you are
seeing through port 137 on your machine does not correspond with any of
our conventions for mail at UST.  Port 137 is used for NetBIOS traffic,
and you would normally see these types of log entries when you connect
to your "My Storage" drive (it is possible, but not likely, that using
Outlook Web Access might also generate these log entries.   The fact
that you're using Thunderbird would seem to preclude this as an option).
The fact that you are also getting so much traffic through port 5900
from non-UST IP addresses also indicates that your machine is being
scanned for vulnerabilities (or is already compromised).

My best advice to you would be to re-image your machine, and establish
stronger security protocols for your administrative accounts (i.e.
strong password, fewer accounts with admin access, etc...).  If you are
using VNC for any particular reason, it is strongly recommend that you
configure it to not use ports 5900, 5800, 5850, or 5901 for connections
(these are the default ports for VNC and are frequent targets for hack
attempts).  It is also our recommendation to be certain you are using
the most current, upgraded version of VNC and always be sure you are
using an encrypted VNC session.

Before you try re-imaging your machine or using your firewall to close
all of your ports, please keep in mind that there is also a possibility
that these log entries are completely innocuous.  Please consult Google,
or your hardware and software vendors for additional information.  And
if you have further problems, please be advised that you may need to
seek a professional repair service.
*************************************************

---

### Post by kidders on 2007-07-17
Hi there,

> **euler_fan said:**
> I had Firestarter in the system tray and it was reporting a number of hits from various IP addresses against port 5900. They were coming in once every 5-20 minutes (about 40 hits total though the afternoon). I was noticing some hits against SAMBA on port 137There's nothing insidious about this much, per se. Depending on where they are, computers can get battered with all sorts of unsolicited traffic, generated by people/programs/viruses curious about what services you might be running. The key word in that sentence though is "unsolicited". If your PC is doing something to attract the unexpected traffic (which is easy enough to determine), you should take it off your network immediately. It's quite conceivable, for instance, that Samba (or something Samba-like) is inviting the NetBIOS queries you've noticed, by advertising itself on your LAN.

I don't want to ramble too much, but my first instincts might be...
[LIST]
[*]Play around with **netstat** to get a feel for what sorts of connections your box is establishing, and any servers it might be running.
[*]I find **iftop** (sort of like **top** for NICs) a convenient little tool for identifying odd network activity.
[*]**Wireshark** (aka **Ethereal**) is a much more full-on tool, but can tell you literally all there is to know about what your computer & those around it are up to.[/LIST]If you're somehow acting as a spam relay, for instance, it should take all of 30 seconds to establish that, by taking a look at some of your *outgoing* traffic, rather than incoming stuff, as you've been doing. Also, do bear in mind that just as you can curtail the kinds of network packets your box will let in, you can easily impose restrictions on outgoing data as well.

> **euler_fan said:**
> Rkhunter (as of time of posting) says to check these out . . .
/etc/.pwd.lock
/etc/.java /dev/.static
/dev/.udev
/dev/.initramfs
/dev/.initramfs-tools 

chkrootkit found this
Searching for suspicious files and dirs, it may take a while...Again, there is very little inherently suspicious about these observations. Without knowing more about *why* these files were flagged, it's hard to be too concerned. Certainly, if you adhere to all the usual "common sense" security practices, it's very unlikely something like a rootkit could make it onto your machine. Doing any of the following, for instance, (aside from being a little foolish) would give you cause for concern now that strange things seem to be happening...
[LIST]
[*]Having ever launched a web browser as root.
[*]Logging into a graphical environment as root.
[*]Running shell scripts as root without inspecting them first.
[*]Ever having **chmod 777**-ed something outside of your own /home directory.
[*]And so on...[/LIST]As you can probably tell, I'm just writing out a list of very unwise things a person might do, that explicitly defeat Linux's security model.


Two general observations ...

**- I -**
Most attempts I've seen to do things like hijack a Linux box have been incredibly crude, and totally reliant on a user doing something no Linux user should ever do. It's certainly possible that you might have fallen victim to something more sophisticated ... but not very probable, imo.

**- II -**
By far the most common targets for malicious modification are generic system utilities like **ls**, **ps**, **[**, and so on ... the kind of thing that cannot help but be executed thousands of times over in a single day. None of the files you listed fall into that category. For instance...
[LIST]
[*] /etc/.pwd.lock [SIZE=1][COLOR=Red][ Is your scan simply flagging all zero-length "dot" files? ][/COLOR][/SIZE]
[*] /etc/.java /dev/.static [SIZE=1][COLOR=Red][ Are "dot" directories seen as somehow suspicious? ][/COLOR][/SIZE][/LIST]
I hope this is of some help.

---

### Post by euler_fan on 2007-07-18
Well, thanks.

I tried looking at some of that, but between Firestarter's outgoing traffic summary being next to nill and iftop saying there is nothing happening I think there is likely nothing going on.

I guess this is where I ask if there is a good "applied linux security for dummies" style book out there . . . something doesn't assume I know much (which is pretty much me) but which is going to build a good, solid foundation for the security side of administering my own box, but not some tome for professional sys admins either.

---

### Post by kidders on 2007-07-18
Hmmmm... I'm really the wrong person to ask about that. You see, I've never been a big fan of using books as a way to learn computing, but I guess that's just down to how individual people prefer to do their learning hehe. :-( I am, however, a member of the Unanswered Posts Team, so I'll flag your thread for some suggestions on good books.

I've learned my Linux skills mostly on a sort of a need-to-know basis. Taking a look around your machine can be a surprisingly enlightening experience ... for instance, exploring the contents of /bin, /usr/bin, /usr/local/bin and asking "What's that, and why is it there?" seems to suit the way my brain absorbs information. "Better" information sources might include:[LIST]
[*]The man pages belonging to individual system tools. Many Linux systems accumulate 100s of megabytes of reference documentation!
[*]Wikis and HOWTOs from other Linux distros. I find Gentoo's and Red Hat's user documentation quite useful, for an alternative perspective on certain things, despite not being strictly applicable to Debian-style systems, such as Ubuntu.
[*]With particular reference to networking, I would again suggest playing with Wireshark. Since you're in a school, I would recommend keeping it quiet though (hehe), since the use of packet sniffers can make sysadmins nervous.
[*]Also, the contents of places like /dev, /proc and /sys (ie filesystem-based interfaces to your kernel & hardware) can be a useful gateway to finding out more about how Linux works.[/LIST]I seem to have been a little *too* successful in talking you out of your concern over a security problem with your system. The main thing is that **you** feel satisfied there's nothing to worry about. With a username like euler_fan, I'm guessing you might like to be sure hehe...[LIST]
[*]Make sure you're aware of the various tools Linux has that let you explore running processes & system activity. As a basic starting point, take a peek at the output of **ps aux | less** ... or maybe the contents of /var/log, to get a feel for what your box is up to.
[*]You might be interested in exploring intrusion detection. Based on the premise that undetected meddling in your Linux box *is* possible, it focuses on detecting it after the fact, by monitoring system logs for suspicious combinations of entries, or keeping tabs on the md5sums of critical system files. Try **apt-cache search intrusion** if you're stuck for a place to start.
[*]Remember to focus on what sort of traffic is *leaving* your box, moreso than entering it. Linux is pretty good at putting up with a battering from a hostile network, but you may still want to see, with your own eyes, that it's not responding to incoming traffic in a way you wouldn't want.[/LIST]It's worth noting that, out of the box, Ubuntu (afaik) doesn't respond at all to *any* unsolicited incoming network packets. Just in case you weren't sure, I thought I'd mention that. From there, cardinal security rule is to absolutely never grant something (or some*one*) any more access privileges than it needs to function properly. In general terms, adhering to that policy makes it very difficult for anyone to do something they're not supposed to, by ensuring that collections of minor chinks in your armor don't combine to create an exploitable security hole.

Sorry I haven't been able to answer your question directly. :-( Hopefully, someone else from my team will post here shortly, with some practical advice on good books.

---

### Post by euler_fan on 2007-07-18
I appreciate that very much.

I'll definitely take your advice to look around . . .  and I have been already a little bit.

The thing with me and books is that I find myself meandering to one simply to get most of my simpler questions answered so I can move on to more interesting ones or actually figuring out what needs to be done, etc.

Thanks again,

euler_fan

---

### Post by HermanAB on 2007-07-18
Well, now that you know that Firestarter works, you can turn the reporting off and relax.  Let it do its job in peace and quiet.
:)

Cheers,

Herman

---

