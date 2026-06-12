---
title: "HDD with LUKS ext4 &amp; ntfs"
date: 2020-04-21
forum: Security
---

### Post by aljames2 on 2020-04-21
Can LUKS be used to protect a HDD that has both ext4 and a ntfs partition or would LUKS only provide the passphrase protection against the ext4 partition?

---

### Post by TheFu on 2020-04-21
> **aljames2 said:**
> Can LUKS be used to protect a HDD that has both ext4 and a ntfs partition or would LUKS only provide the passphrase protection against the ext4 partition?

Typically, LUKS would be on a partition, then a file system would be created inside the LUKS container?

I’m struggling to understand the purpose of NTFS in the config you ask about.  Why?

The only reason I’d use NTFS is if the storage will be physically connected to a Windows system, but Windows doesn't support LUKS, so that would be useless.  Another reason would be to connect to specialized devices - perhaps a video recorder - which won't support LUKS either.

All other reasons would use samba to access the storage, so NTFS should be avoided.

Actually, to make access to multiple storage areas inside a single LUKS container, I’d use LVM with different LVs.  You can put any file system onto an LV that you want.  But ... why NTFS?

---

### Post by EuclideanCoffee on 2020-04-21
I think it's possible if you put the NTFS into a LVM.

[https://ubuntuforums.org/showthread.php?t=146002](https://ubuntuforums.org/showthread.php?t=146002)

If you can do this, I think you can encrypt the LVM container.

I imagine this would all need to be done manually, as the LUKS encryption option in the installer doesn't provide you an easy way to do this automatically.

[https://help.ubuntu.com/community/ManualFullSystemEncryption](https://help.ubuntu.com/community/ManualFullSystemEncryption)

---

### Post by aljames2 on 2020-04-21
I do know how to set up LVs in a LUKS container.  My thought was to try it but perhaps it would be easier to use a separate HDD for the windows junk.  My daughter in college is still bound to Windows and I was trying to think what could work.  I currently have everything (Linux stuff & some Windows stuff) backup up multiple times on a backup server accross multiple HDDs using LVM+ext4.  I am thinking about mobility in this case for the Windows stuff.  Would veracrypt be a viable way to encrypt a separate ntfs drive?  Perhaps better, I could just do a SAMBA share for her to pull from.

---

### Post by EuclideanCoffee on 2020-04-21
Ok, sorry. There's a lot to parse here. When you said HDD I'm thinking of any storage media on HDD, so I didn't think it matters what experience you have since the process is invariably the same on Ubuntu.

You certainly have a lot of options available to you... but when you say NTFS and Windows, I don't immediately think they must be the same. Nor do I understand how you wish for them to relate immediately.

If you want LUKS on an external drive for Windows, you will need a way to unlock it. This is a separate question. Is this your question? Or did you want a networked solution, which also works and may be more secure in this picture. Please let me know.

---

### Post by TheFu on 2020-04-22
> **aljames2 said:**
> I do know how to set up LVs in a LUKS container.  My thought was to try it but perhaps it would be easier to use a separate HDD for the windows junk.  My daughter in college is still bound to Windows and I was trying to think what could work.  I currently have everything (Linux stuff & some Windows stuff) backup up multiple times on a backup server accross multiple HDDs using LVM+ext4.  I am thinking about mobility in this case for the Windows stuff.  Would veracrypt be a viable way to encrypt a separate ntfs drive?  Perhaps better, I could just do a SAMBA share for her to pull from.

So, NTFS only should be used when the disk will physically be connected to a Windows system.  Over the network, she should use Samba or SFTP or rsync or scp or ..... nextcloud or owncloud or magic-wormhole or .....20 other methods.

Windows doesn't understand LVM or LUKS, so there's no way for a Windows system to peal the onion of LUKS --> LVM ---> NTFS to get at any data. So, only a Linux system would be able to do that, and Linux doesn't need NTFS for Windows systems to have access.

Samba should only be used when on the same LAN.  There are slow methods to allow Samba to be used through a VPN, but those a really poor.  
sftp, scp have great client programs for every OS that has a network. Windows has WinSCP or FileZilla.  I use WinSCP.  Set her up with an ssh-key inside WinSCP so she can access your/her storage remotely.  Heck, you could probably setup a daily backup solution using rsync over ssh too.  I've not been impressed with rsync from Windows, but it has been a very long time since I did that.  The "server" side just needs to have ssh open and you could limit her access to just sftp and only the files she wants/needs.  openssh-server is the only packge to be installed.  If she was using Linux, setting this up is trivial, would take under 5 minutes.  For Windows, I would start by checking WinSCP and Putty help files.  I know that putty has a pscp.exe program which is scp.  

As for how to encrypt Windows, perhaps asking that on a Windows-centric forum would be smarter?  I think all portable devices, computers AND storage must be encrypted.

Some thoughts .... 

And before she leaves, test that everything works with her laptop from outside your house.  Perhaps there's free wifi at the local cafe or library?  The college network will not allow inbound connections, but it will allow outbound ones like ssh.

While you're at it, you might want to give her a remote desktop back to your home using x2go.  x2go uses the same ssh port, so there's nothing more to open to the outside world.  When her Windows computer gets hacked, and it will, she'll still be able to have a desktop somewhere else to do papers, spreadsheets, etc. Send her off with Windows, but also a flash drive with Lubuntu setup to connect to your house with ssh-keys and x2go configured and perhaps an rsync script to do backups of the data in her Windows drive?

---

### Post by aljames2 on 2020-04-22
Thank you both!  This does answer everything :).  I have used many of the tools on the network but nothing remote outside the home.  I need to figure out the ssh back into the home part and set my router to forward a non-standard ssh port.  I don't own a domain yet so I need to do that.  Once I get this networking part set, I should be good because I understand how some of these tools work.  

My OP thoughts with the portable spinning 3.5 HDD in an enclosure was to facilitate pulling stuff off her laptop by USB and also transferring what I have backed up that she needs to her laptop...very inefficient is see.  I'm a Linux freshman (figuratively "freshman", not actually) so I admit somewhat embarrassing to have had these thoughts.

Very cool idea using the Lubuntu flash as a backup system for mitigation on the laptop, nice.  I hadn't thought of the remote desktop either, she'll have her own room next semester and the space for it.

---

### Post by TheFu on 2020-04-22
You don't need a domain if you don't want one.  Many routers support free dynamic DNS services - like from No-ip. There are 20 other services. Check ddclient for what linux supports.

if you make ssh available from the internet, be certain to lock down access to only internet address that actually  need access.  Running fail2ban to protect the ssh server is a good idea too.  That's 2 firewall levels.  **Never allow password-based authentication over the internet.**

---

### Post by EuclideanCoffee on 2020-04-22
Please be very careful when you run ssh from a router. Please use a non-standard port and block all incoming traffic besides that port. After this, please layer your firewall, so your port forwarding only goes to the desktop and not your consumer grade equipment. Opening your router to the public increases your risk layer, opening you to attacks. Hackers love consumer routers because it's easier to hide on your equipment. Be safe!

---

### Post by aljames2 on 2020-04-22
Locally I use ssh with keys and no password auth.  What about using keys + passphrase?  I've read best to still only use keys.  I have fail2ban running out of the box, no customization.

My router is one I built, running pfSense on this [https://www.asrock.com/mb/Intel/J3355M/](https://www.asrock.com/mb/Intel/J3355M/)
With a 4 port intel ethernet card.  1 port is my WAN and I use 2 other ports for two separate networks (IoT crap, separate from trusted devices).  It currently is set to not allow any incoming.  With all this though, remote access is still new to me.  I'll think through the security stuff and try to set it up carefully.

Thanks again

---

### Post by EuclideanCoffee on 2020-04-22
Key is better than password. If you enable password and key, it's simply stronger authentication.

fail2ban will stop a bruteforce, but it's not the best out of the box. I typically increase ban time and lower amount of times someone can guess to stop ddos.

I also have a script that finds banned IPs and then deny host access via ufw or iptables.

Self-made routers do not guarantee more security. It is the same problem as creating your own encryption. It makes security weaker.

---

### Post by TheFu on 2020-04-26
> **aljames2 said:**
> Locally I use ssh with keys and no password auth.  What about using keys + passphrase?  I've read best to still only use keys.  I have fail2ban running out of the box, no customization.

My router is one I built, running pfSense on this [https://www.asrock.com/mb/Intel/J3355M/](https://www.asrock.com/mb/Intel/J3355M/)
With a 4 port intel ethernet card.  1 port is my WAN and I use 2 other ports for two separate networks (IoT crap, separate from trusted devices).  It currently is set to not allow any incoming.  With all this though, remote access is still new to me.  I'll think through the security stuff and try to set it up carefully.

Thanks again

ssh keys are created with passphrases.  There are 2 times when a passphrase shouldn't be provided to unlock the ssh-key:
[LIST=1]
[*]It was unlocked earlier and added to the ssh-agent. The timeout hasn't occured yet.
[*]For tasks that run unattended, like backups.
[/LIST]
ssh-agent has a timeout period which controls how long any ssh-key is kept open. This agent can also communicate between systems that a key has been unlocked, so the next system sees that too.

ssh-keys without a passphrase need to be limited to specific access locations. This is one of the reasons that backups should be "pulled", so the private key only exists on a backup server that isn't connected to the internet.  That ssh-key should be limited to backup-related tasks.  The .ssh/ settings on the remote host can control that.

To allow ssh passwords on the LAN or from other, specific IPs, use something like this at the end of the /etc/ssh/sshd_config:

```
# Change to no to disable tunnelled clear text passwords
PasswordAuthentication no
Match Address 172.22.22.0/24,172.21.22.0/24
      PasswordAuthentication yes

```
Any IP not from those 2 subnets, cannot use a password.
The "Match" can be for addresses, users, systems. It is very powerful for sshd configs.

Always remember that the overriding goal is to limit who can access which network and physical services to only those who actually have a need.  The WAN router should prevent most of the world from even seeing that any port running sshd is open.  Security needs to be layered.

As for which routers are more secure, that depends on the person responsible for management.
A 5 yr old consumer router that was patched every quarter until the vendor stopped support is less secure, probably, than a home configured PC running a router config that gets patched every week.  Now, grandma shouldn't have a home-configured router that she maintains unless she loves doing that AND is capable of doing it well.  Similarly, an IT pro who doesn't patch any router firmware, but can setup automatic security updates for a home-configured Ubuntu system and followed instructions correctly to make it into a router would be much more secure.

Secure is dependent on many factors that nobody here can fully outline. Much of security is showing up, doing normal things, reviewing logs, having alarms for odd situations and limiting access to almost the entire world.

---

