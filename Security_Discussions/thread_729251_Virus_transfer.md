---
title: "Virus transfer ?"
date: 2008-03-19
forum: Security Discussions
---

### Post by Hagar55 on 2008-03-19
Can I transfer a virus to my Xp partition by using my linux install (seperate partition) ?

I don't copy files from one OS to the other but can a virus transfer itself from an ext3 partition to an NTFS  one ?

---

### Post by p_quarles on 2008-03-19
Moved to Security Discussions. 

No, not unless you did so intentionally.

---

### Post by hyper_ch on 2008-03-20
maybe if you have ext2/3 drivers installed in windows and access that ext2/3 drives it might be possible - I think.

---

### Post by p_quarles on 2008-03-20
> **hyper_ch said:**
> maybe if you have ext2/3 drivers installed in windows and access that ext2/3 drives it might be possible - I think.
Well, again, you would have to do this deliberately. It's certainly *possible*, but it's not something that's going to happen in the background without the user doing anything.

---

### Post by hyper_ch on 2008-03-20
reading/opening an infected file on a ext2/3 through fs-driver should suffice...

---

### Post by Hagar55 on 2008-03-20
So yes it could happen...shame now I'll have to install a virusscanner in my linux boot....

---

### Post by hyper_ch on 2008-03-20
why? Install one in windows... when you then access the linux file in windows it should be triggered

---

### Post by mcduck on 2008-03-20
> **Hagar55 said:**
> So yes it could happen...shame now I'll have to install a virusscanner in my linux boot....

No, it can't. As the virus doesn't run in Linux, it can't move to another partition (or do anything else) by itself.

The only way it would move from one partition to other (while you are running Linux) is if you move it yourself.

---

### Post by p_quarles on 2008-03-20
> **mcduck said:**
> No, it can't. As the virus doesn't run in Linux, it can't move to another partition (or do anything else) by itself.

The only way it would move from one partition to other (while you are running Linux) is if you move it yourself.
+1

Yes, it's possible to transfer a virus from an ext3 partition to an NTFS partition. Again, for this to happen, you would have to be either extremely careless or actively trying to harm your own system. 

If you're worried about this, it's a much better idea to operate your Windows installation as non-administrative user. Much like the separation of privileges you have in Linux, this makes it much more difficult for viruses to install themselves invisibly.

---

### Post by hyper_ch on 2008-03-20
*wrong thread*

---

### Post by Herman on 2008-03-21
Most viruses and malware in Windows computers come in email or as voluntary or involuntary downloads from web sites.

I don't think anyone would be likely to be transferring email files between Linux and Windows because you can't read Linux email files in Windows, or Windows email files in Linux.
If someone used Ubuntu to take a backup from Windows and store it, that might re-infect the Windows operating system if the email was restored again from a backup but that could happen from any backup no matter where it was stored.

If you downloaded an infected file such as an .exe file for a game from a website in Linux and copied it into your Windows file system and clicked on it to install the game it would probably infect Windows alright.
On the other hand, if you downloaded an .exe file for Windows using Linux you would be a lot safer if you're smart. You could download the .exe file and scan it with AVG in Linux or any other virus scanner you can install in Ubuntu. You could also copy it into a shared data partition first instead of directly into Windows. Then you could boot Windows and scan the shared data partition with your antivirus in Windows before you copy the file into Windows and install it.
Therefore, I would say that by using Linux you would be increasing the safety and security of your Windows installation.

---

### Post by ameba on 2008-03-21
Interesting stuff..

---

### Post by Hagar55 on 2008-03-22
thanks for the answers :)

---

### Post by bhavi on 2008-03-22
> **Hagar55 said:**
> Can I transfer a virus to my Xp partition by using my linux install (seperate partition) ?

I don't copy files from one OS to the other but can a virus transfer itself from an ext3 partition to an NTFS  one ?

Yes its possible the other way around while running wine (windows emulator)..

For security issues on wine..

ou probably should be behind a router with firewall or install something like firestarter.

Ubuntu comes with a firewall installed: IPTables. Firestarter is just a GUI front end for it.

Now the next common question that people ask is there a way to "stealth/hack" your ports via IPTables config files without installing Firestarter as a GUI?

answer is: When you install Ubuntu, iptables is there, but it allows all traffic by default.

I can bet you that on a default install when you run the command

sudo iptables -nL the result you get is

Chain INPUT (policy ACCEPT)
target prot opt source destination

Chain FORWARD (policy ACCEPT)
target prot opt source destination

Chain OUTPUT (policy ACCEPT)
target prot opt source destination

=all traffic allowed ;-)

When you start using p2p applications you become extremely visible and you get all kinds of unwanted connection attempts. If your PC is sat there online with an (possibly unsupported and untrusted) application listening on multiple (or even unknown random) ports you really should have some control over the traffic. So you can learn iptables or use a gui frontend, hence my suggestion to use Firestarter or similar. For a desktop user a nice gui interface fits the Ubuntu philosophy much better than expecting users to correctly set iptables rules by hand and it's very easy and quick to set up. If you don't have iptables configured one way or the other your security policy comes down to only using invulnerable applications (no, I can't think of any either) and unbreakably strong passwords.

Now from ext3 to ntfs:

Viruses arent easy to program in linux because of Ubuntu/Linux has very CLEAR defenitions of groups and users, file ownerships and permissions.. So In ubuntu/linux if at all a virus is there it can affect only the user who ran the program.. And because of the file ownerships and permissions the USER will have a control over the system unlike in windows where the OS has control over the machine.. This makes Virus development in linux difficult to say the least..

Finally I think it wont....

---

### Post by Herman on 2008-03-22
Yes, that is absolutely right, IPtables does come unconfigured by default.
However, a fresh Ubuntu installation is quite secure because no ports are open.

Some people connect to the internet by wireless networking or by dial-up, and others by Cable broadband or ADSL or other kinds of connections. Those types of connections have potential security issues. 
If you connect through a router, it already has a pretty good firewall in it. Most broadband modems have another firewall in them too, so there is already some protection for a computer that's inside the average home or office LAN, behind a router and an ADSL modem-router.

If you have a LAN, you can run a port scan from another computer in the network, and you will not detect an open port in a fresh installation of Ubuntu.
Ubuntu comes with its own port scanner, go 'System', 'Administration','Network Tools', and click the 'Port Scan' tab. You need to know the IP address for the computer you wish to scan, and you can find that by running 'ifconfig' in the PC you want to run a security test on. You should find out that no ports are open, so the Ubuntu PC is invisible in a network.

Certainly if we install 'services' like file sharing, we will necessarily open ports. I agree, and it is then necessary to configure the firewall. 
Firestarter is my favourite too, I think it's a excellent frontend for IPtables, and more than that, it provides a way to monitor 'hits' as well. I use Firestarter too if I decide to open ports.

If we install a service like an SSH (Secure Shell) Server, which opens port 22, we can still be fairly secure providing we are sensible about how we set up SSH, it has it's own security measures built into it.

File sharing services, to me, seem to present us with a bit of a conundrum. Someone who installs a file sharing service is inviting strangers into their computer. Surely anyone installing a file sharing service must understand that. In that case, how can a firewall protect you? Are you going to us the firewall to let people in? Or lock them out? If you lock them out then you can't use file sharing. If you let them in you can use file sharing but your firewall isn't protecting you. 
I don't think file sharing services are compatible with security.

One way to do things might be to have two operating systems installed, if you really want to indulge in file sharing, make one operating system your open one and keep all your files in it that you wish to present to the public, and don't worry about security. 
Make a separate installation let that one remain secure, don't install any services in it, and keep your personal files in that system. Just make sure it isn't mounted by the other one.
Or use two different computers.

IPtables and Friestarter are great though, when you want to open you computer and share files with only people you know, such as member of your family, close friends, or business associates.
If you use a secure server like SSH, it's easy to configure Firestarter to further enhance the already secure SSH server. You can set Firestarter to allow access only to a port of your choice, and only to packets from IP addresses you set. 

I don't think there's any need for new Ubuntu users to be frightened by the fact that 'Ubuntu has no firewall', or that 'IPtables is unconfigured'.
Ubuntu is quite secure by default.
Either the user is aware of security and wants a secure computer or the opposite.

Regards, Herman :)

---

