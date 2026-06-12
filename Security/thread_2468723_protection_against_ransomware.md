---
title: "protection against ransomware"
date: 2021-11-09
forum: Security
---

### Post by Tom_ZeCat on 2021-11-09
I've been surprised by recent reports of ransomware that specifically targets Linux computers.  (See article at end of post.)  I would think that Linux PCs would be far less vulnerable to ransomware because it would have to trick you into typing in your password to allow it to install.  Is this correct?  Linux-targeted ransomware cannot install unless the user permits it via typing in his password.  Correct?  I would thus think a huge protection against it would be to know your software sources.  Install from the official repository, of possible.  If not possible, at least know who your source is.  

Another thing I'm doing is this.  I keep a backup of all important files to a thumb drive that I don't keep plugged into my computer or anywhere else on the network.  I don't even save my work to the internal hard drive.  I have one thumb drive that I save my work to and keep plugged in.  Then I use FreeFileSync periodically to back that thumb drive up to another one.  That backup thumb drive only gets plugged in when I need to backup my main one.  Otherwise, it stays safely in a special pouch away from the computer.  

It does seem unlikely that I'll get attacked by ransomware.  However, if I did, I could boot straight to Geparted on a DVD or thumb drive and then wipe the hard drive.  Then I could install Kubuntu from scratch.  If my files were encrypted on my main thumb drive, I could just format it and get my files back from my backup thumb drive.  

This is what I know to do to protect against ransomware.  If anyone knows of anything else I should do, please speak up.  I used to work in a computer place that fixed Windows machines infected by ransomware.  This type of malware is something I find particularly disgusting, not that any malware is good.  I remember the frustration of customers and how violated they felt by these criminals.  We were almost always able to save their machines, granted that was some years back.  I hear ransomware nowadays has gotten even worse.  

If there's anything else I should do besides  what I'm already doing, I'm all ears.  Maybe I should also do an occasional Clam scan for malware?  I do have WINE installed on this PC, but I only run two Windows programs that way.  I run a language dictionary named Ultralingua 6.  I've been running that same version for years, and I trust the original source I bought it from years ago.  I also run Treepad Business Edition.  That's a note-taking program that I purchased from the legitimate source.  It runs pretty well under WINE, though I don't use it anymore.  I also run a few more programs under Windows 7 in VirtualBox.  I know what you're thinking.  Windows 7 isn't supported anymore with any security updates.  However, I've got it locked down to not update, and I've blocked it from even accessing the Internet.  I run a few old Windows programs under it whose sources I trust, as I bought them legitimately.  I only run them occasionally, and neither these Windows apps nor Windows 7 are ever permitted to access the Internet.  

I therefore think I'm protected pretty well.  I use safe software sources.  Most Kubuntu installs happen via the repositories, Snap, and Flathub.  I do have a couple programs that I install via deb files.  They're both proprietary applications that I bought from the legitimate seller.  One is a screenwriting word processor named Fade In.  The other is SoftMaker Office, which is an office suite made in Germany, and also purchased legitimately from them.  I also use the donation-installer provided by the people who make FreeFileSync.  Basically, if you make a donation to them, you get their donation install file that auto updates when a new version comes out.  

I don't download or run any deb or other install files whose source I don't know, and I don't use any PPAs whose origin I don't know.  

I've got Clam installed, but honestly I don't use it much.  I welcome any other comments on keeping safe from ransomware, either in your *buntu OS itself, in WINE, or in VirtualBox, or any other system you might run on a Linux PC.  


[https://www.forbes.com/sites/daveywinder/2020/11/08/new-ransomware-threat-jumps-from-windows-to-linux-what-you-need-to-know/?sh=d9ad85b32657](https://www.forbes.com/sites/daveywinder/2020/11/08/new-ransomware-threat-jumps-from-windows-to-linux-what-you-need-to-know/?sh=d9ad85b32657)

---

### Post by TheFu on 2021-11-09
TL;DR sorry. Busy night.

Daily, versioned, "pulled" backups is the solution to all ransomware attacks.  
That means having a backup server that isn't accessible to the attackers. 
The server "pulls" the backups. They cannot be pushed.
The client cannot have direct access to the backup storage. Definitely no NFS or CIFS or Samba should be used.
The backup server "pull" should use a root-equiv account, not the end user's account and that connection should be locked down so it can only be used for backup processing and only from the backup server, no other locations.
AV software is a boondoggle and might be 50% effective.  Use your brain instead.  There are contracts which blindly mandate the use of AV - my professional E&O insurance mandated a few things that makes perfect sense in the Windows world, but doesn't make much sense for Unix or Linux systems. Still, we followed their rules, since insurance is useless if they refuse to pay over failure to comply with the rules.

Thumb drives probably aren't the best backup storage. They are best for sneakernet needs. Flash storage tends to fail with little to zero warning. Beware.

BTW, I consider myself a Neb guy, though I haven't been back since a few visits during college. Some family still lives in Omaha, but we tend to see each other in other locations.

---

### Post by LokiScarlet on 2021-11-24
You're pretty much covered. Linux malware is typically spread by the human factor. Attackers of Windows use vulnerabilities to get in. Attackers of Linux use vulnerabilities just to run, and still need a human to deliver the trojan.
Don't use any, and I mean any, resident AV software if you don't have to. A simple virus scanner like Clam is fine, but don't fall for the commercial ones, as resident antivirus software can be exploited to potentially become a zero-click backdoor or may come with backdoors. If you want to be safe from other people's human vector as well, you could build from source anything you get from outside the included repository, but that's kinda overkill.

With all the extremes out of the way, the best advice anyone can give is don't hire idiots. Also, like TheFu said, backups should be pulled from your server by a backup server, rather than pushed onto a drive or pushed onto a backup server, but I'll go into detail of one way I know to do that:

SSH is capable of not only providing a secured shell for which it's named, but also SFTP. So what you'd want to do, is create a user on the server you want to protect, that can access everything you want to back up. You set up SSH to use a private/public key pair for this user and disable the use of a password. Install the private key on the backup server and the public key on the server that needs protected. Then, you make a script on the backup server to copy the files using the scp command. "scp -rp <user>@<server address>:<files path> <folder to copy to>", like ```
scp -rp backup@10.0.6.66:/home/dracula/important-files/* "/var/backups/10.0.6.66/$(date +'%Y%m%d')/dracula/important-files/"
``` where p is optional if you don't care about preserving metadata like permissions, dates, etc. Then, having written your script with whatever amount of lines of scp commands you need, just schedule it in cron or whatnot.
But if you don't have a backup server, at least you have all your other bases covered.

---

### Post by mcyber4 on 2021-11-28
If you look at the complexity of a modern UEFI Rootkit malware, setting up a keysniffer is only the first and easiest part to get the root password.

I think we need a fully supported and up to date built in  antivirus, -malware alike Windows 11. Sure I could buy Eset but...

---

### Post by TheFu on 2021-11-28
> **mcyber4 said:**
> If you look at the complexity of a modern UEFI Rootkit malware, setting up a keysniffer is only the first and easiest part to get the root password.

I think we need a fully supported and up to date built in  antivirus, -malware alike Windows 11. Sure I could buy Eset but...

Systems like Ubuntu don't have a root password unless someone is violating the default setup.
If someone has physical access to any computing device - game over.  Just assume that.  We can make it very difficult by booting from alternate media that doesn't leave our control, by using strong full-disk encryption, and by staying patched.  Those techniques should address all but the most capable, determined, attackers.

AV is only about 50% effective.  Run 5 brands of AV and we get to somewhere between 80-90% effective.  A smart user defeats attacks all the time through behavior and actually reading warning messages. The hard thing is that 1 in 10,000 times a smart user makes a mistake, that's all that is needed for attacks to effective.  

The 'zero-click' attacks are outside normal user's control, assuming the devices are fully patched.

The solution for ransomware is automatic, daily, versioned, "pulled" backups, with enough versions so that we can locate and determine the attack vector. The backup area cannot be shared storage that clients can access. I suppose read-only access would be ok, but that isn't how we do it until the user asks to restore a file.  Then we mount the backup area read-only to their workstation. I used to think that 6 months was sufficient length of time for backups, before a friend had a valid attack that actually planted the malware over 9 months earlier inside their business.  That's a determined attacker.

Of course, if there is any doubt that a system is compromised, nuke it from orbit. That's the only way to be sure.

---

### Post by mcyber4 on 2021-11-29
Yea sudo is the command, haven't use Ubuntu since I was hit by a UEFI Rootkit 3 years ago. Nuke from orbit is not enough...I had to buy a new motherboard from a DIFFERENT vendor! I don't know where/how it originated but it infected many files I had on Ubuntu, Win10, Android and MacOS.

---

### Post by TheFu on 2021-11-29
> **mcyber4 said:**
> Yea sudo is the command, haven't use Ubuntu since I was hit by a UEFI Rootkit 3 years ago. Nuke from orbit is not enough...I had to buy a new motherboard from a DIFFERENT vendor! I don't know where/how it originated but it infected many files I had on Ubuntu, Win10, Android and MacOS.

If there is malware in the hardware, there isn't much any OS can do. Supply chain attacks tend to be extremely targeted to avoid detection, since mass deployments always have someone noticing issues, eventually.

If it was me planning an attack, I'd mess with the SSD firmware and perhaps have a little tiny SOC connected to the LAN port.  I own a SOC that is about the size of my thumb and USB powered. It could easily be smaller. It is a complete ARM Linux computer. I suspect they just tool a Pi-Zero-W and made it smaller.

But for the 99.9% of us, HW attacks just don't happen, so daily, automatic, versioned, "pull'd" backups is the solution. Just retain enough versions to outlast any delay the malware C&C might use.  That could be a few days, weeks, months.  I'm always amazed that people don't have versioned backups. It isn't like doing it is THAT hard, especially for personal data.

For a single user, getting their HOME: [Https://ubuntuforums.org/showthread.php?t=2465035&p=14049979#post14049979](Https://ubuntuforums.org/showthread.php?t=2465035&p=14049979#post14049979)
```
  /usr/bin/rdiff-backup --exclude-special-files  $HOME /mnt/backup/
 /usr/bin/rdiff-backup --remove-older-than 90d --force /mnt/backup/
```
are the commands to have 90 days retained - if you run the task daily.  Typically a backup is just 2 minutes. It depends on the amount of changed data and whether any system data is gathered to be included in the backups.  This is the minimal level of backups that everyone should be doing, IMHO. It is simple and gets YOUR most important data.  Just adding in the list of manually installed packages to the backup data would make restoring to new hardware (total loss) possible and not catastrophic for most end-users.

The flaw with the commands above are that the backup storage is directly connected to the same system. That's a liability for malware attacks, but still far better than nothing.  For non-servers, in home environments, that's probably 80% of what a good backup needs to do.

---

