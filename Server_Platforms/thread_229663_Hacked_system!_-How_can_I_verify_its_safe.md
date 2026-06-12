---
title: "Hacked system!? -How can I verify its safe?"
date: 2006-08-04
forum: Server Platforms
---

### Post by bge on 2006-08-04
When I came home today I found that my desktop picture had been changed to one with the text "UR COMPUTER HAS BIN HAKKED". First of all i find that bad spellning. What I am worried about now is if the system security has been permanently compromised or if this just something trivial that isn't a real threat to my system?

At first glance my system seems unchanged (besides the desktop backgound), no new user has been added, all my files seem to be ok. 

I have ssh access turned on but changed the port to 5656. Before I did that I used to get dictionary attacts but afterwards no. 

The system has also been restarted two times for no appearant reason. To me this indicates that something is wrong. 

I don't understand everything in auth.log, but I can see that there has been no dictionary attacs prior to the restarting and it seems no incomming connections. The wallpaper file was created the 3rd of august 22.15 and has the name Firefox_wallpaper.png. I also found a textfile in my trash that says "Du har blivit hackad!!!!!!!!!!!" (Swedish for you have been hacked). Created 21:58. I post here a part of around that time of auth.log, maybe you can figure something out of it.

```

2006-08-03 00.17.01	localhost	CRON[30691]	(pam_unix) session closed for user root

2006-08-03 00.17.01	localhost	CRON[30691]	(pam_unix) session opened for user root by (uid=0)

2006-08-03 01.17.01	localhost	CRON[579]	(pam_unix) session opened for user root by (uid=0)

2006-08-03 01.17.02	localhost	CRON[579]	(pam_unix) session closed for user root

2006-08-03 02.17.01	localhost	CRON[2955]	(pam_unix) session opened for user root by (uid=0)

2006-08-03 02.17.02	localhost	CRON[2955]	(pam_unix) session closed for user root

2006-08-03 03.17.01	localhost	CRON[5298]	(pam_unix) session closed for user root

2006-08-03 03.17.01	localhost	CRON[5298]	(pam_unix) session opened for user root by (uid=0)

2006-08-03 03.50.08	localhost	smbd[6627]	(pam_unix) session opened for user henrik by (uid=0)

2006-08-03 04.17.01	localhost	CRON[7707]	(pam_unix) session closed for user root

2006-08-03 04.17.01	localhost	CRON[7707]	(pam_unix) session opened for user root by (uid=0)

2006-08-03 04.17.05	localhost	smbd[6627]	(pam_unix) session closed for user henrik

2006-08-03 05.17.01	localhost	CRON[10044]	(pam_unix) session closed for user root

2006-08-03 05.17.01	localhost	CRON[10044]	(pam_unix) session opened for user root by (uid=0)

2006-08-03 06.17.01	localhost	CRON[12372]	(pam_unix) session opened for user root by (uid=0)

2006-08-03 06.17.02	localhost	CRON[12372]	(pam_unix) session closed for user root

2006-08-03 06.25.01	localhost	CRON[12687]	(pam_unix) session closed for user root

2006-08-03 06.25.01	localhost	CRON[12687]	(pam_unix) session opened for user root by (uid=0)

2006-08-03 07.17.01	localhost	CRON[14812]	(pam_unix) session closed for user root

2006-08-03 07.17.01	localhost	CRON[14812]	(pam_unix) session opened for user root by (uid=0)

2006-08-03 07.30.01	localhost	CRON[15317]	(pam_unix) session closed for user root

2006-08-03 07.30.01	localhost	CRON[15317]	(pam_unix) session opened for user root by (uid=0)

2006-08-03 08.17.01	localhost	CRON[17411]	(pam_unix) session closed for user root

2006-08-03 08.17.01	localhost	CRON[17411]	(pam_unix) session opened for user root by (uid=0)

2006-08-03 09.17.01	localhost	CRON[19737]	(pam_unix) session closed for user root

2006-08-03 09.17.01	localhost	CRON[19737]	(pam_unix) session opened for user root by (uid=0)

2006-08-03 10.17.01	localhost	CRON[22078]	(pam_unix) session closed for user root

2006-08-03 10.17.01	localhost	CRON[22078]	(pam_unix) session opened for user root by (uid=0)

2006-08-03 10.47.22	localhost	smbd[23251]	(pam_unix) session opened for user henrik by (uid=0)

2006-08-03 11.17.01	localhost	CRON[24388]	(pam_unix) session closed for user root

2006-08-03 11.17.01	localhost	CRON[24388]	(pam_unix) session opened for user root by (uid=0)

2006-08-03 12.17.01	localhost	CRON[26709]	(pam_unix) session closed for user root

2006-08-03 12.17.01	localhost	CRON[26709]	(pam_unix) session opened for user root by (uid=0)

2006-08-03 13.17.01	localhost	CRON[29071]	(pam_unix) session closed for user root

2006-08-03 13.17.01	localhost	CRON[29071]	(pam_unix) session opened for user root by (uid=0)

2006-08-03 14.06.53	localhost	smbd[23251]	(pam_unix) session closed for user henrik

2006-08-03 14.17.01	localhost	CRON[31515]	(pam_unix) session closed for user root

2006-08-03 14.17.01	localhost	CRON[31515]	(pam_unix) session opened for user root by (uid=0)

2006-08-03 15.17.02	localhost	CRON[1408]	(pam_unix) session closed for user root

2006-08-03 15.17.02	localhost	CRON[1408]	(pam_unix) session opened for user root by (uid=0)

2006-08-03 16.17.01	localhost	CRON[3832]	(pam_unix) session opened for user root by (uid=0)

2006-08-03 16.17.02	localhost	CRON[3832]	(pam_unix) session closed for user root

2006-08-03 17.17.01	localhost	CRON[6172]	(pam_unix) session opened for user root by (uid=0)

2006-08-03 17.17.02	localhost	CRON[6172]	(pam_unix) session closed for user root

2006-08-03 18.17.01	localhost	CRON[8467]	(pam_unix) session opened for user root by (uid=0)

2006-08-03 18.17.02	localhost	CRON[8467]	(pam_unix) session closed for user root

2006-08-03 19.17.01	localhost	CRON[10752]	(pam_unix) session closed for user root

2006-08-03 19.17.01	localhost	CRON[10752]	(pam_unix) session opened for user root by (uid=0)

2006-08-03 19.41.55	localhost	sudo	(pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=henrik

2006-08-03 19.42.58	localhost	gdm[5078]	(pam_unix) session closed for user henrik

2006-08-03 19.43.06	localhost	afpd[17511]	(pam_unix) session closed for user henrik

2006-08-03 19.43.07	localhost	sshd[5816]	Received signal 15; terminating.

2006-08-03 19.45.13	localhost	gdm[5079]	(pam_unix) session opened for user henrik by (uid=0)

2006-08-03 19.45.42	localhost	sshd[5831]	Server listening on :: port 5656.

2006-08-03 19.45.43	localhost	sudo	  henrik : TTY=unknown ; PWD=/home/henrik ; USER=root ; COMMAND=/usr/bin/update-manager

2006-08-03 20.02.46	localhost	sudo	(pam_unix) authentication failure; logname= uid=0 euid=0 tty=pts/0 ruser= rhost=  user=henrik

2006-08-03 20.02.53	localhost	sudo	  henrik : TTY=pts/0 ; PWD=/home/henrik ; USER=root ; COMMAND=/usr/bin/apt-get distupgrade

2006-08-03 20.03.01	localhost	sudo	  henrik : TTY=pts/0 ; PWD=/home/henrik ; USER=root ; COMMAND=/usr/bin/apt-get dist-upgrade

2006-08-03 20.03.34	localhost	sudo	  henrik : TTY=unknown ; PWD=/home/henrik ; USER=root ; COMMAND=/usr/sbin/synaptic

2006-08-03 20.17.01	localhost	CRON[9205]	(pam_unix) session closed for user root

2006-08-03 20.17.01	localhost	CRON[9205]	(pam_unix) session opened for user root by (uid=0)

2006-08-03 20.53.25	localhost	smbd[9858]	(pam_unix) session opened for user henrik by (uid=0)

2006-08-03 21.17.01	localhost	CRON[10503]	(pam_unix) session closed for user root

2006-08-03 21.17.01	localhost	CRON[10503]	(pam_unix) session opened for user root by (uid=0)

2006-08-03 21.25.34	localhost	smbd[9858]	(pam_unix) session closed for user henrik

2006-08-03 21.25.39	localhost	afpd[10638]	(pam_unix) session opened for user henrik by (uid=0)

2006-08-03 22.17.01	localhost	CRON[11542]	(pam_unix) session closed for user root

2006-08-03 22.17.01	localhost	CRON[11542]	(pam_unix) session opened for user root by (uid=0)

2006-08-03 22.27.47	localhost	sshd[11786]	Failed password for root from 127.0.0.1 port 58305 ssh2

2006-08-03 22.27.51	localhost	sshd[11786]	(pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=localhost.localdomain  user=root

2006-08-03 22.27.53	localhost	sshd[11786]	Failed password for root from 127.0.0.1 port 58305 ssh2

2006-08-03 23.10.18	localhost	smbd[12520]	(pam_unix) session opened for user henrik by (uid=0)

2006-08-03 23.17.01	localhost	CRON[12658]	(pam_unix) session closed for user root

2006-08-03 23.17.01	localhost	CRON[12658]	(pam_unix) session opened for user root by (uid=0)

2006-08-04 00.17.01	localhost	CRON[13687]	(pam_unix) session closed for user root

2006-08-04 00.17.01	localhost	CRON[13687]	(pam_unix) session opened for user root by (uid=0)

2006-08-04 00.24.35	localhost	gdm[5079]	(pam_unix) session closed for user henrik

2006-08-04 00.24.41	localhost	smbd[12520]	(pam_unix) session closed for user henrik

2006-08-04 00.24.43	localhost	afpd[10638]	(pam_unix) session closed for user henrik

2006-08-04 00.24.43	localhost	sshd[5831]	Received signal 15; terminating.

2006-08-04 08.48.04	localhost	sshd[5697]	Server listening on :: port 5656.

2006-08-04 08.48.30	localhost	gdm[5088]	(pam_unix) session opened for user henrik by (uid=0)

2006-08-04 08.53.19	localhost	afpd[6319]	(pam_unix) session opened for user henrik by (uid=0)

2006-08-04 08.56.00	localhost	sudo	  henrik : TTY=unknown ; PWD=/home/henrik ; USER=root ; COMMAND=/usr/bin/update-manager

2006-08-04 09.11.14	localhost	gdm[5088]	(pam_unix) session closed for user henrik

2006-08-04 09.11.22	localhost	afpd[6319]	(pam_unix) session closed for user henrik

2006-08-04 09.11.22	localhost	sshd[5697]	Received signal 15; terminating.

2006-08-04 09.13.16	localhost	gdm[5080]	(pam_unix) session opened for user henrik by (uid=0)

2006-08-04 09.13.57	localhost	sshd[5853]	Server listening on :: port 5656.

2006-08-04 09.17.01	localhost	CRON[6466]	(pam_unix) session closed for user root

2006-08-04 09.17.01	localhost	CRON[6466]	(pam_unix) session opened for user root by (uid=0)

2006-08-04 10.17.02	localhost	CRON[8393]	(pam_unix) session closed for user root

2006-08-04 10.17.02	localhost	CRON[8393]	(pam_unix) session opened for user root by (uid=0)

2006-08-04 11.17.01	localhost	CRON[10310]	(pam_unix) session opened for user root by (uid=0)

2006-08-04 11.17.02	localhost	CRON[10310]	(pam_unix) session closed for user root

2006-08-04 12.17.01	localhost	CRON[12320]	(pam_unix) session opened for user root by (uid=0)

2006-08-04 12.17.02	localhost	CRON[12320]	(pam_unix) session closed for user root

2006-08-04 13.17.02	localhost	CRON[14229]	(pam_unix) session closed for user root

2006-08-04 13.17.02	localhost	CRON[14229]	(pam_unix) session opened for user root by (uid=0)

2006-08-04 14.17.01	localhost	CRON[16192]	(pam_unix) session opened for user root by (uid=0)

2006-08-04 14.17.02	localhost	CRON[16192]	(pam_unix) session closed for user root

2006-08-04 15.09.04	localhost	sudo	(pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=henrik

2006-08-04 15.17.01	localhost	CRON[18331]	(pam_unix) session opened for user root by (uid=0)

2006-08-04 15.17.02	localhost	CRON[18331]	(pam_unix) session closed for user root

2006-08-04 16.17.01	localhost	CRON[20338]	(pam_unix) session opened for user root by (uid=0)

2006-08-04 16.17.02	localhost	CRON[20338]	(pam_unix) session closed for user root

2006-08-04 17.17.01	localhost	CRON[22350]	(pam_unix) session opened for user root by (uid=0)

2006-08-04 17.17.02	localhost	CRON[22350]	(pam_unix) session closed for user root

2006-08-04 18.17.02	localhost	CRON[24452]	(pam_unix) session closed for user root

2006-08-04 18.17.02	localhost	CRON[24452]	(pam_unix) session opened for user root by (uid=0)

2006-08-04 19.17.01	localhost	CRON[26523]	(pam_unix) session opened for user root by (uid=0)

2006-08-04 19.17.02	localhost	CRON[26523]	(pam_unix) session closed for user root

2006-08-04 20.17.01	localhost	CRON[28366]	(pam_unix) session closed for user root

2006-08-04 20.17.01	localhost	CRON[28366]	(pam_unix) session opened for user root by (uid=0)

```

I do know that I have made atleast one huge mistake, I used the same password for my user and the root account. (It is changed now however)
But the password I used was strong, of this type X9R%4Zkj. (Mixed cases, with numbers and non alphabetic characters). Could auth.log have been edited afterward, using the root account? And of course, I don't run around sharing my password. 

I use firestarter as a firewall and it is set to allow all connections from 192.168.0.1 to 192.168.0.255 (my laptop connected to eth0 and internet on eth1) and connections on port 5656 (custom ssh), 5900 (VNC) and 18464 (custom bittorrent). I very rarely have the VNC-server up and running. For bittorrent i use Azureus. I use file sharing between my laptop and my ubuntu machine with SAMBA and AFP (netatalk). 

Whats important for me to know now is, what did i do wrong so that I woun't do the same misstake again? And will I have to completely reinstall Ubuntu to have a safe system?

---

### Post by kerry_s on 2006-08-04
Wow! This is the first time i have ever seen that a Ubuntu system got hacked. I Would back up the important stuff and reinstall right away so you don't have to worry about something hidden. I would suggest you read up on tightening down your servers that your running and perhaps cut it down to the bare minumum, instead of the 3-4 you have running. In fact since your only using it to connect to the laptop you should only set that one to have access and deny any external queries. I'm sorry i can't help futher as i have little experince with the exact setup, in my house we never network the computer's just in case 1 gets compromised and only 1 computer has access to the router all other internal/external addresse's are blocked. Also switch your wires around on the router to give them new ips instead of using the same one that was hacked or set a static one.

---

### Post by slimdog360 on 2006-08-05
do you have a friend or family member who has access to your computer. Also if the password was like that Im guessing you wrote it down somewhere, in which case I would say that its likely it was a friend or family member who done it.
In anycase maybe you could try a different firewall, I use guarddog, but dont ask me the difference or if one is better than the other. I just like the way guarddog can be configured more than firestarter.

---

### Post by Bossieman on 2006-08-05
Is this for real? 
:confused:

Cant you just change the passwords instead of having to reinstall everything?

---

### Post by bge on 2006-08-07
Thank you for your answers.

I just whish this wasn’t for real, it would have saved me a lot of worry. 

No one has access to the computer besides me. I live in an apartment by myself, and those that visit me are not that nosy about my computers ;) So I’m ruling out that some one has done it at the computer, no one has broken into my apartment. The password is written down and kept in a place were it has remained untouched. 

I am sharing my internet connection through my PC, I was thinking about instead of doing that buying a router (one with a built in firewall). Could that increase the security or will it not make a difference? I still want to continue to run both the AFP and the SMB-servers. AFP gets much better transfer rates but will not share NTFS-partitions. 

Since there seems to be no way to verify if the system is safe, I will reinstall Ubuntu, install guarddog, change the passwords (different for user and root), change the ssh port to something even more obscure and hope that my system doesn’t happened again. I have not given up on Ubuntu yet.

---

### Post by Randomskk on 2006-08-08
Changing the SSH port to something obscure really won't do very much for you. It's simple to find the SSH port using a tool such as nmap, and if your system was compromised with it already on an obscure port then changing it again won't help.
Instead, look seriously into using SSH key files, disabling passwords, only allowing certain IPs to connect to SSH, not allowing root login, and ONLY allowing your user to login (su / sudo to root).
Make sure SSH is up to date, and unless you need it to be open to the world, keep it open to your local network only.

---

### Post by RavenOfOdin on 2006-08-09
> 
UR COMPUTER HAS BIN HAKKED


From ONLY this. . .

The party that is responsible sounds like a 12 year old who spends all his time on stupid little cracking sites submitting replies to message boards like "OMG I 0WN J00 MU4H4H4H4." 

:D

---

### Post by zhenya on 2006-08-09
Wow!  I'm surprised to hear this, as it sounds like you have been fairly vigilant, and have a system set up very similar to my own.  Are you certain that your password was not compromised via some other manner?  ie. you haven't used it for any other sites or logins, or it was perhaps intercepted via an unsecured remote vnc connection?

The only thing I can add that you might want to do to make things even more secure in the future is set up Denyhosts so that anybody attempting to attack your ssh port will be given limited opportunities.

---

### Post by mannheim on 2006-08-10
Another possibility: perhaps you used some other compromised machine, to log in remotely to your own machine? A keylogger could have grabbed your password in that case, I guess.

When you reinstall the system, I would keep an archive (e.g. on a dvd) of everything that is on the old system, as it is now. Maybe later, you will get an idea of what went wrong, and you can go back and revisit the "scene of the crime".

---

### Post by cleverselfreferentialname on 2006-08-13
> **Randomskk said:**
> Changing the SSH port to something obscure really won't do very much for you. It's simple to find the SSH port using a tool such as nmap, and if your system was compromised with it already on an obscure port then changing it again won't help.
Instead, look seriously into using SSH key files, disabling passwords, only allowing certain IPs to connect to SSH, not allowing root login, and ONLY allowing your user to login (su / sudo to root).
Make sure SSH is up to date, and unless you need it to be open to the world, keep it open to your local network only.

I hang around with a few security literate people, and one labeled my use of a nonstandard SSH port "Security through obscurity" and that it didn't really help me. If someone is using nmap to scan for standard ports on, say, my entire netblock, they wont notice my SSH server on a random port.

If, however, someone did an exhaustive scan of all ports on my machine with the -p option and 0-65535 operand with nmap, they would find it, and I'd be damned if I didn't have a decent password.

To the thread starter, listening on port 5656 might be a bad idea. Some backdoor from a while back listened on the same port, and someone, though this is unlikely, might scan that port across a wide range of IPs in order to find trojanized systems.

VNC is vulnerable since it only permits passwords up to eight characters. Instead, get an SSH client (I think portaputty does this, and is usable in Windows from USB) that supports X forwarding, configure it to authenticate with a key you have on a USB drive as well as with a password (though I've yet to do that on my system). I don't remember if putty supports compressing SSH traffic, but do it if possible, it will make it a lot faster than VNC.

---

### Post by cleverselfreferentialname on 2006-08-13
I don't remember Azureus being vulnerable or seeing any security advisories, but it would be prudent to upgrade to the newest version once you reinstall. 

And please do reinstall.

I mean, you might not NEED to, it might be an open and shut rootkit removal, but I use Linux for the peace of mind, of not knowing that Georgie Boy and his buddies in the big three letter agencies can't get in too easily, because the system (uhm...the linux system. Not the one with Georgie Boy) wants you to understand how it works.

An ideal ssh config might look like the following. Well, I might be biased, since this is mine.

```

Port 54201
Protocol 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
UsePrivilegeSeparation yes
SyslogFacility AUTH
LogLevel INFO
LoginGraceTime 120
PermitRootLogin no
StrictModes yes
RSAAuthentication yes
PubkeyAuthentication yes
IgnoreRhosts yes
RhostsRSAAuthentication no
HostbasedAuthentication no
PermitEmptyPasswords no
ChallengeResponseAuthentication no
PasswordAuthentication yes
X11Forwarding yes
X11DisplayOffset 10
PrintMotd yes
PrintLastLog yes
KeepAlive yes
Banner /etc/issue.net
AcceptEnv LANG LC_*
Subsystem sftp /usr/lib/openssh/sftp-server
UsePAM yes
AllowGroups sshusers

```

Most notably, I created the group sshusers with 'sudo addgroup sshusers'. Edit the group membership in /etc/group.

iptables (firestarter is a frontend to this) can be configured to allow connections from the local network with this command ```
iptables -A INPUT -s 192.168.0.0/24 -d private_ip_of_ssh_box -p tcp --dport 54201 -j ACCEPT
``` or from the interweb in general (if you choose to replace VNC with X over SSH) with this ```
iptables -A INPUT -d private_ip_of_ssh_box -p tcp --dport 54201 -j ACCEPT
```

Either way, if you're still feeling paranoid (a possibility, since I always am) I'm sure if you contact me over AOL IM or via PM that I could get some of my comrades to audit it for you.

---

### Post by Phantom784 on 2006-08-13
I'm guessing it was from a key logger on a machine you used to log into your linux box.  I'd defiently re-install to be safe, especially since your root kit detector turned up hidden processes.  For protection in the future, you should disable ssh password access and use a key to login.  Sticky PuTTY (google it if u don't know what it is) and a password protected keypair on a usb drive/whatever portable storage is best for you.  The password on the private key should be different than your Ubunutu password (which you should never reuse anywhere; if you did before, this is another way this may have happened).  You then stick the public key in your authorized_hosts file/folder (i foget which).  Sorry I don't have all the detailed technical directions on how to do this stuff; I'd have to look it up myself.  This way still isn't perfectly secure, since a compromised machine could have a program to copy your private key off the usb drive and then use the password from the keylogger to decrypt it.  It will still save you from a less intelligent trojan that only logs keystrokes.  To be extra secure, change your keypair from time to time.

Kind off topic here, but does anyone know of a progrem/kernel plugin/patch/whatever it would be that will keep a port (such as 22) hidden until it sees attempts to connect to certian predefined ports in a predefinded order?  This would save you from nmaping.

---

### Post by shu on 2006-08-15
Sorry to hear that. I guess, since you didn't use any system integrity programs before attack, you need to reinstall now.

For future:
1. Use firewall (I know you did)
2. Do not allow any incoming connection except ssh 
3. Do not allow root logins via ssh
4. Use strong password for your account and root account (different ones)
5. Use key-based login via ssh and always check if key of the machine your connecting to is your machine key (man-in-the-middle)
6. Do not use VPN, use FreeNX over ssh instead.
7. Use some log watcher to scan ssh logs and prevent brute force attacks.

---

### Post by Sam on 2006-08-18
You can install **logwatch** which parses some logfiles (sshd, httpd, ...) for everything unusual then sends a report by mail daily.

Example of report:
>  --------------------- SSHD Begin ------------------------ 

 
 Login attempted when not in AllowUsers list:
    bin : 2 Time(s)
    cyrus : 2 Time(s)
    daemon : 2 Time(s)
    ftp : 2 Time(s)
    games : 2 Time(s)
    lp : 2 Time(s)
    mail : 2 Time(s)
    mysql : 2 Time(s)
    named : 2 Time(s)
    news : 2 Time(s)
    nobody : 2 Time(s)
    postfix : 2 Time(s)
    sshd : 2 Time(s)
    uucp : 2 Time(s)
    wwwrun : 2 Time(s)
 
 Users logging in through sshd:
    root:
       xxx.xxx.xxx.xxx (somehost.com): 8 times
 
 ---------------------- SSHD End ------------------------- 

---

### Post by Pumm4 on 2006-08-19
Hello **bge** I hope everything is allright now. This may sound strange to you but... never write down your passwords and sensitive data that is used on your system. What if someone breaks in the house when you are not home and finds that list of valuable information. Try to remember those, something that is easy to remember and hard to guess. This is only a tip ;)
> **shu said:**
> 
4. Use strong password for your account and root account (different ones)
Number 4. is a must. But remember - Do **_NOT_** make your password a dictionary word or common name with numbers and symbols merely substituting for similar looking alphabetic characters.

> 7. Use some log watcher to scan ssh logs and prevent brute force attacks. To fool the brute-force attcks use psw's like:" ***** ***** **" meaning use spaces between "words and/or numbers and/or symbols"- but never in the begenning or end.

Try to read as much as you can about software that can help you minimaze these "attacks" and maxsimize your system security.

**Software Tools:**[LIST]
[*][Argus]("http://qosient.com/argus/") - IP network transaction auditing tool. This daemon promiscuously reads network datagrams from a specified interface, and generates network traffic status records 
[Argus 2]("http://argus.tcp4me.com/")
[*][COPS]("ftp://ftp.cerias.purdue.edu/pub/tools/unix/scanners/cops/") - UNIX security checks.
[*][deslogin]("ftp://ftp.uu.net/pub/security/des") - remote login
[*][Freedom Internet Privacy Suite for Linux]("http://www.freedom.net/products/bundles/privacy_bundle.html") - Commercial products for internet surfers. (Also free downloads)
[*][freestone]("http://ftp.nluug.nl/security/coast/firewalls/freestone/freestone/") - firewall from sosCorp.com
[*][ipfilter]("http://cheops.anu.edu.au/%7Eavalon/ip-filter.html") - packet filter
[*][Kerberos]("http://web.mit.edu/kerberos/www/") - authentication
[*][Port Sentry, Log Check, Host Sentry]("http://www.psionic.com/")
[*][rsaeuro]("ftp://ftp.ox.ac.uk/pub/crypto/misc") - cryptographic toolkit
[*][Pretty Good Privacy (PGP)]("http://www.pgp.com/")
[*][Rkdet]("http://vancouver-webpages.com/rkdet/") - root kit detector daemon. Intended to catch someone installing a rootkit or running a packet sniffer.
[*][satan]("http://www.fish.com/satan/") - Security Administrator Tool for Analyzing Networks
[*][SARA]("http://www-arc.com/sara/sara.html") - Security Auditor's Research Assistant - network security vulnerability scanner.
[*][SAINT]("http://www.wwdsi.com/products/saint_engine.html") - Finds computers on the network, port scans and does a vulnerability check and outputs a report. - Commercial product.
[*]Secure connections **SSH** (shell) and **SSL** (socket layer):[LIST]
[*][ssh.com]("http://www.ssh.com/products/ssh/") - Secure shell
[*][OpenSSH]("http://www.openssh.org/") - Open Source version - Requires :[LIST]
[*][OpenSSL]("http://www.openssl.org/") - Secure Socket Layer
[*][zlib]("http://www.gzip.org/zlib.tar.gz") - data compression library[/LIST] 
[*][SSH]("http://www.cs.hut.fi/ssh/") - Comercial versions SSH1 and SSH2
[*][SSH]("http://www.zedz.net/") -                   [[Download]]("ftp://ftp.zedz.net/pub/crypto/redhat/i386/")                   - Ver. 1 (RPMs: ssh, ssh-server, ssh-clients, ssh-extras)
[*][SSL]("ftp://ftp.tu-chemnitz.de/pub/Local/informatik/sec_tel_ftp/") - Encrypted telnet
[*][ SSH FAQ]("http://www.onsight.com/faq/ssh/ssh-faq.html") - Frequently Asked Questions
[*][Secure Shell Working Group]("http://www.ietf.org/html.charters/secsh-charter.html")
[*]MS/Windows clients:[LIST]
[*][PuTTY]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/download.html") - Telnet, SSH, SCP, SFTP client
[*][WinSCP]("http://winscp.vse.cz/eng/") - scp (secure copy) client.
[*][Shaolin Secure FTP]("http://www.shaolinsecureftp.com/")
[*][Tera Term]("http://hp.vector.co.jp/authors/VA002416/teraterm.html")
[*][TTSSH: An SSH Extension to Teraterm]("http://www.zip.com.au/%7Eroca/ttssh.html")[/LIST] [/LIST] 
[*][TAMU]("http://www.net.tamu.edu/network/public.html#Security") - Texas A&M University developed tools[LIST]
[*][Drawbridge]("http://www.net.tamu.edu/drawbridge/index.html") - Firewall package (Free BSD)
[*][Tiger]("http://www.net.tamu.edu/network/tools/tiger.html") - Scan a Unix system looking for security problems (Similar to COPS) -          [Tiger Analytical Research Assistant (TARA Pro)]("http://www-arc.com/tara/") - Commercial support
[*][Netlog]("http://www.net.tamu.edu/network/tools/netlog.html") - TCP and UDP suspicious traffic logging system[/LIST] 
[*][TCP wrapers]("ftp://ftp.porcupine.org/pub/security/") - Wietse Venema
[*][tripwire]("http://sourceforge.net/projects/tripwire/") - File system data integrity checking tool
[*][InterSect Alliance]("http://www.intersectalliance.com/") - Intrusiuon analysis. Identifies malicious or unauthorized access attempts.
[*][CryptoHeaven]("http://www.cryptoheaven.com/") - Secure online storage, file sharing and distribution, email, instant messaging. Free Linux client but it is a commercial for fee service. (less than 2MB storage is free)[/LIST]Wireless:[LIST]
[*][AirSnort]("http://airsnort.sourceforge.net/") - wireless LAN (WLAN) tool that recovers encryption keys.
[*][WEPCrack]("http://sourceforge.net/projects/wepcrack")
[*]Also see: [YoLinux Wireless security links]("http://www.yolinux.com/TUTORIALS/LinuxTutorialWireless.html#SECURITY")[/LIST]**Security Audit Tools:**[LIST]
[*][Nessus]("http://www.yolinux.com/TUTORIALS/LinuxTutorialInternetSecurity.html#NESSUS") - Remote security scanner. Checks service exploits and vulnerablilities.
[*][Chkrootkit]("http://www.yolinux.com/TUTORIALS/LinuxTutorialInternetSecurity.html#CHKROOTKIT") - Scan system for trojans, worms and exploits.
[*][Linuxforce: AdminForce CGI Auto Audit]("http://www.linuxforce.net/") - CGI script analyzer to find security deficiencies.[/LIST]Have Phun

---

### Post by Gouki on 2006-08-20
You can also check for [Rootkits](http://howtoforge.com/scan_linux_for_rootkits). It's never a bad idea.

---

