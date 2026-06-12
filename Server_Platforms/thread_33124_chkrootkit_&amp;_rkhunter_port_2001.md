---
title: "chkrootkit &amp; rkhunter: port 2001"
date: 2005-05-09
forum: Server Platforms
---

### Post by beeldings on 2005-05-09
After running chkrootkit and rkhunter on a fresh install of Warty upgraded to Hoary, it appears as if there is some possible malicious activity on my computer. chkrootkit reports that I might be infected with the Scalper worm and it also reports that "bindshell" is infected on ports 1524, 4000, and 31337. I promptly blocked those ports in Firestarter,

After my chkrootkit test, I decided to go for a second opinion and ran rkhunter on my system. rkhunter reported unsafe file ownership of /home/spikentm/.gnupg/gpg.conf. During the filesystem scan, I received the following notice:

```

* Filesystem checks
   Checking /dev for suspicious files...                      [ OK ]
   Scanning for hidden files...                               [ Warning! ]
---------------
 /dev/.udev.tdb
/dev/.udevdb /etc/.pwd.lock
---------------
Please inspect:  /dev/.udevdb (directory)

```

During the network scan of rkhunter, I received notice that port 2001 is possibly infected with the Scalper Rootkit. I find this to be alarming as chkrootkit also reported that I might be infected with Scalper.

I have read that sometimes a utility such as chkrootkit or rkhunter can cause false alarms. But I am concerned over the fact that both programs reported a possible infection from the Scalper worm and the Scalper Rootkit, and that both programs listed port 2001 as being infected.

What I would like to know is how and if I really am infected with the Scalper variants. I personally think it's highly unlikely that I am infected as I obtain and update most of my software and system-critical files with apt-get from the command-line, with the exception of the four extensions for Firefox that I downloaded from the Firefox web site and rkhunter itself (which I downloaded from the official rkhunter web site). Prior to installing Warty from the pressed CD I received a few months back, I wiped my hard drive with the Gutmann process using dban (Darik's Boot and Nuke) just to make sure nothing nasty could have hampered the installation.

If you read my "Keeping Your Privacy Private" thread on the Community forum, then you know I'm very paranoid when it comes to computer security. If you could provide any information as to my recent rootkit scans, I would appreciate it very much. On another note, does anyone know how I can permanently disable FTP, telnet, and SSH access to my computer? I have those protocols disabled in Firestarter under my Outbound Traffic policy and those ports are being monitored with portsentry. Do you have any other tips or applications I can use to further lockdown my Linux box?

---

### Post by Seth on 2005-05-09
[http://www.f-secure.com/v-descs/scalper.shtml](http://www.f-secure.com/v-descs/scalper.shtml)

> The worm does not modify the system configuration, and it is visible in the system process list as a process ".a".

Scalper can be removed from the system by deleting file "/tmp/.a" and terminating the worm process with command "killall -9 .a". 

---

### Post by beeldings on 2005-05-09
Thanks for the info, Seth. It appears as if both programs issued a false alarm and that I am not infected with the Scalper worm, because the file mentioned in your quote does not exist in my temporary directory and the "killall" command was unable to terminate any process under that name.

---

