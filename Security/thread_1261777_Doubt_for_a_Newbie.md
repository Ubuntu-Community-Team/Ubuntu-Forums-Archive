---
title: "Doubt for a Newbie"
date: 2009-09-09
forum: Security
---

### Post by chandru155 on 2009-09-09
Hi,
   1. I am not running any servers or anything. But in the process list, i saw one process "SSH_AGENT" why its running? I did Ubuntu update only. I didnt install any server. 
   2. I use torrent. While using it, i open tcp and udp ports for torrent(ktorrent). If any hacker using that opened port can hack my system? Is that possible? If so, how tough he can hack? But my IP is dynamic. Even if he hack, can he hack after restart(also closing the opened port) my system?(Also the modem, which will change my IP)
   3. How do i know that someone is trying to hack my system or hacked my sytem? Is there any log from that i can know? i always enable my ufw firewall and open ports only while downloading via torrent(Ktorrent)
   3. Does the antivirus of Ubuntu(ClamAv or Avast) will detect all of the windows Virus?( i am going to scan the files and softwares of windows to check whether they contain virus or not)

---

### Post by Baneblade on 2009-09-09
On SSh agent (from the man page)
> ssh-agent is a program to hold private keys used for public key authentication (RSA, DSA).  The idea is that ssh-agent is started in the beginning of an X-session or a login session, and all other windows or programs are started as clients to the ssh-agent program.  Through use of environment variables the agent can be located and automatically used for  authentication when logging in to other machines using ssh(1).


As for the rest... are you serious?

---

### Post by minerbog on 2009-09-09
Firstly I think your should calm down. By default Ubuntu is still far more secure than windows will ever be :). Tho I agree not perfect.

1. What process list did you look at? SSH-AGENT runs along side openSSH and other remote shell clients. Generally not harmful.

2. Not sure what your saying here?? As long as you only open the port for outbound traffic nothing can come inbound on that port.

3.Hacking is the wrong word to use here. But any way, most unautherised entries will require a rootkit of some kind. I suggest you install either 'chkrootkit' and/or 'rkhunter' from the apt packages.  However if a system is already infected these are less useful.

4.Windows virus are nothing more than files to a liunx machine. The only problem comes when you are transfering back and forth to a win machine.

Hope this helps :)

---

### Post by barnex on 2009-09-09
As long as you have a strong password, I really see no need to worry.

---

### Post by bodhi.zazen on 2009-09-09
I suggest you read the stickies.

Start with : [Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

And if you like go through the intrusion detection post (which is what you are asking) and the Apparmor post as well.

They are stickies for a reason :p

---

