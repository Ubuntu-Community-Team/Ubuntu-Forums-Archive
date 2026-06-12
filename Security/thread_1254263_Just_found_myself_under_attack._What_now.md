---
title: "Just found myself under attack. What now?"
date: 2009-08-31
forum: Security
---

### Post by lunarul on 2009-08-31
My programs were runing slow, so I checked the system monitor to see if there's some process draining my CPU... What I found was a very large number of processes, all called "ssh". The `Command Line` column was not very helpful "./ssh 270", but it was enough to know that I had a replacement "ssh" executable somewhere. Found the file in "/var/tmp/b-G-d" along with many other files, most of them being lists of common username/password combinations (most likely for a brute force attack on my system). Another file contained the text:
"Powered by stealth
Copyright by #Chance""
I immediatly deleted the whole folder and killed all remaining "ssh" processes.

My problem is: what now? How could someone create files on my system remotely? I checked what else there was in "/var/tmp" and everything there was suspicious. How can I stop this from happening again?
Was my system easy to break in just because of my poor password? ("12345", but changed it immediately after this event with a strong password). Or should I expect this to happen again in the future, regardless of password strength?

---

### Post by wojox on 2009-08-31
Look in 

```
/var/log/auth.log
```

See what it says. You'll probably need a reinstall. You're not sure what they put in there.

---

### Post by lunarul on 2009-08-31
Checked "auth.log" and found a lot of failed login attempts from a remote IP two days ago. There are no failed login attempts today, except after I changed the password. This worries me, since it seems to indicate that my password was indeed found and used.
That's all I could get from the log, as I'm not very experienced with this stuff. I attached the full log for others to study, and maybe give me a more clear picture of what's going on.

---

### Post by XCan on 2009-08-31
I would guess that you indeed got bruted. Your password is way too easy, and it seems you have a fairly common username as well. Tip for future, change your ssh port, and get a strong password. Then you can install some script like fail-2-ban etc if you feel it is necessary, or configure your firewall.

---

### Post by lunarul on 2009-08-31
Is there any way to find out if my system was compromised or not? I changed my password and my ssh port, but was it too late?

---

### Post by mechdave on 2009-08-31
I would suggest pass all relevant data on to the computer crime division of your police force. Image your whole machine and if possible isolate it from the network and then get the crime boys to forensically look at it. Do a fresh install on another machine until such time until the police have finished their investigations. It is vitally important you don't destroy the data on your machine. People with this kind of motivation deserve to rot in a jail cell...

---

### Post by dmizer on 2009-08-31
I don't know about handing things over to the police as I seriously doubt anything will be done, especially considering your auth log doesn't show that the bot made any successful logins. Even so I would certainly consider your computer 100% compromised. You should make a backup of all your log files and your important data and do a fresh install.

Next time, disable password ssh access and use strong RSA encrypted keypairs according to this howto: [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#Disable%20Password%20Authentication](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#Disable%20Password%20Authentication) and [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by SlugSlug on 2009-08-31
you should also install denyhosts

---

### Post by lunarul on 2009-08-31
I was afraid of that... On the other hand, I was planning to do a fresh install anyway (system not running very smoothly after the 9.04 update)

I doubt the police in my country would have any idea what to do with a computer :)

---

### Post by dmizer on 2009-08-31
> **SlugSlug said:**
> you should also install denyhosts

This is only a mild deterrent, as all you need to do is work the bot through a proxy. I can't stress this enough: if your box has an external connection to the world, you MUST use secure and encrypted protocols.

Disabling password login makes deny hosts fairly needless.

---

### Post by mechdave on 2009-08-31
I always change the ssh port to a number higher than 5000, if you can change it to a port number not assigned by iana even better. Also if you are going to access it from a certain network restrict the ssh daemon to only allow connections from that network or better that subnet of the network. Another one is to disable root login completely from ssh and as dmizer said, use strong RSA key pairs and run any bots through a proxy. This will help minimise any security flaw exposure. If you are running any other internet facing programs make sure you research the security flaws and settings before going live.

We can't stop the naughty people, but we certainly can make it much harder for them to compromise our systems.

The above will usually thwart any script kiddie out there with a book on UNIX and a idle mind as far as ssh is concerned :)

Take your box down and re install it, maybe just to be sure even zero the hard drives with random data if you want.

---

### Post by lunarul on 2009-08-31
I generally only keep 5-digit ports open. SSH was the only one I kept on standard port. Thinking about it, I realized that I don't even need to access my computer remotely through SSH, so I now closed the port completely... The only ports open in my router now are for bit-torrent and I don't think there's any way to gain access to a computer through that protocol.

---

### Post by kevdog on 2009-08-31
Or if you really wanted to get creative you could install a port knocker such as fwknop.  [http://www.cipherdyne.org/](http://www.cipherdyne.org/)

But regardless -- dmizer's advice is well heeded.  Secure your box to the outside world and use encrypted protocols always when available.

---

### Post by zipperback on 2009-08-31
If you suspect your system was compromised, backup your critical data files and immediately do a full system wipe and reinstall. Be sure that that you also keep your system fully updated at all times.

Change ALL your account passwords including gmail, hotmail, yahoo, etc.. etc.. etc..

Also be sure you've setup your firewall to use very strict rules.

- zipperback
:popcorn:

---

### Post by phillw on 2009-08-31
> **dmizer said:**
> This is only a mild deterrent, as all you need to do is work the bot through a proxy. I can't stress this enough: if your box has an external connection to the world, you MUST use secure and encrypted protocols.

Disabling password login makes deny hosts fairly needless.


it is a seperate thread,but related.

[http://ubuntuforums.org/showthread.php?t=1253944](http://ubuntuforums.org/showthread.php?t=1253944)

Either I have been hacked, or the remote server has.

---

### Post by bodhi.zazen on 2009-08-31
> **lunarul said:**
> My programs were runing slow, so I checked the system monitor to see if there's some process draining my CPU... What I found was a very large number of processes, all called "ssh". The `Command Line` column was not very helpful "./ssh 270", but it was enough to know that I had a replacement "ssh" executable somewhere. Found the file in "/var/tmp/b-G-d" along with many other files, most of them being lists of common username/password combinations (most likely for a brute force attack on my system). Another file contained the text:
"Powered by stealth
Copyright by #Chance""
I immediatly deleted the whole folder and killed all remaining "ssh" processes.

My problem is: what now? How could someone create files on my system remotely? I checked what else there was in "/var/tmp" and everything there was suspicious. How can I stop this from happening again?
Was my system easy to break in just because of my poor password? ("12345", but changed it immediately after this event with a strong password). Or should I expect this to happen again in the future, regardless of password strength?

Password strength is your weak link in this example.

Secure your ssh server - Use ssh keys, disable password log in, and use either iptables or denyhosts/fail2ban.

See :
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by koenn on 2009-08-31
> **lunarul said:**
> Is there any way to find out if my system was compromised or not? I changed my password and my ssh port, but was it too late?


strange quastion. Didn't you already say:
> **lunarul said:**
> ...  it was enough to know that I had a replacement "ssh" executable somewhere. Found the file in "/var/tmp/b-G-d" along with many other files,...
How could someone create files on my system remotely?

If someone can remotely create files on your system, and (apparently) run them, consider your system compromised.

---

### Post by rookcifer on 2009-08-31
> **lunarul said:**
> My programs were runing slow, so I checked the system monitor to see if there's some process draining my CPU... What I found was a very large number of processes, all called "ssh". The `Command Line` column was not very helpful "./ssh 270", but it was enough to know that I had a replacement "ssh" executable somewhere. Found the file in "/var/tmp/b-G-d" along with many other files, most of them being lists of common username/password combinations (most likely for a brute force attack on my system). Another file contained the text:
"Powered by stealth
Copyright by #Chance""
I immediatly deleted the whole folder and killed all remaining "ssh" processes.

My problem is: what now? How could someone create files on my system remotely? I checked what else there was in "/var/tmp" and everything there was suspicious. How can I stop this from happening again?
Was my system easy to break in just because of my poor password? ("12345", but changed it immediately after this event with a strong password). Or should I expect this to happen again in the future, regardless of password strength?

Back up important files, wipe your disk with a liveCD using the following command as root:

```
shred -vfz -n 1 /dev/sda
```

Then reinstall the OS.  The reason why you want to reinstall is because even if you think your machine is clean, there could always be a rootkit and chances are you would never find it (chkrootkit and rootkithunter and far from perfect and should never be relied upon).

Then learn how to secure ssh.  It's easy to do and will save you major headaches in the future.

---

