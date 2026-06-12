---
title: "I've been hacked"
date: 2013-09-26
forum: Security
---

### Post by Mahyar on 2013-09-26
Hi everyone,

My server has been hacked.

I noticed that I couldn't access its files remotely, so had a closer look. There were no files in my home folder.

I looked at the log of commands, and this is what I found.

sudo su
pwd
ls -a
w
id
uname -a
wget <some file>
unzip root.txt.zip
perl root.txt
ls
id
rm -rf*
exit -0

Does anyone have any advice? How did they get my password after inputting 'sudo su'? Should I reinstall the OS? Is there anything I can do to safeguard against this in the future? Is this a bot or human?

I know it's too late this time, but I don't want this to happen again, to me or anyone.

All comments appreciated.

Thanks

---

### Post by hakermania on 2013-09-26
I am very sorry that this happened to you. I hope you had everything backed up. This is the worst type of hackers: Logging in, deleting as many things as they can and then they log off. Probably without any good reason.

I guess that you took the commands from ~/.bash_history file? Weird that the hacker did not logged in twice to wipe out the file so as to hide the commands from you.
Please mention that for root the commands are saved under /root/.bash_history, so if the "sudo su" command was successful any commands run by the su session will be under /root/.bash_history

But, from my point of view, the first "sudo su" was unsuccessful (maybe the user he was logged in from could not become root using this way) so he downloaded an exploit using wget and tried to run it so as to gain root privileges. If he had been successful I think that he would wipe out the whole filesystem, not just the home folder of yours. That makes me believe that his try to gain root privileges was unsuccessful.

As to what gave him access to your server, who knows? There are way too many ways to attempt to access a server, from SQL injection, brute force attacks, XSS and the list goes on. I don't know many things about server configuration etc but I guess that there will be somewhere a log which may say something interesting.

---

### Post by Mahyar on 2013-09-26
Thanks for your advice. I think you're right.

I need to boost security.

---

### Post by nerdtron on 2013-09-26
Make the server offline immediately. If you have backup on your data, reinstall everything so that you can make the server online again with minimal downtime.
I always enable the firewall and only allow ssh by default on all server deployments. You can change the port of the ssh and disable root login and then use a secure password. It can be enough on a not so popular/not busy web server.

---

### Post by ian-weisser on 2013-09-26
Nerdtron is right:
- Take your server offline *immediately*
- Complete reinstall. You don't know what other surprises are lurking.
- Restore data from pre-hack backups. Do not try to preserve the data on your compromised system.

Use ssh keys instead of passwords on an internet-facing server.

See [https://help.ubuntu.com/12.04/serverguide/security.html](https://help.ubuntu.com/12.04/serverguide/security.html)

---

### Post by scbingham on 2013-09-26
Also, don't use the ssh default external port 22 on your router for port forwarding, use something higher than 9000.

My server was continually bombarded with access attempts & I realised it was probably just a matter of time before someone got in.

Since I changed it to a port above 9000, all went quiet. I also installed denyhosts, there are other programs too.

---

### Post by tripp98 on 2013-09-26
Also give them something to do.  Install a honeypot and forward 22 to it.  Its designed to capture what the hackers try to do.

---

### Post by Gyokuro on 2013-09-26
> **ian-weisser said:**
> Nerdtron is right:
- Take your server offline *immediately*
- Complete reinstall. You don't know what other surprises are lurking.
- Restore data from backups. Do not try to preserve the data on your compromised system.

Use ssh keys instead of passwords on an internet-facing server.

See [https://help.ubuntu.com/12.04/serverguide/security.html](https://help.ubuntu.com/12.04/serverguide/security.html)

First two points are ok but with the third one I have a problem: how does the OP knows that his/her backups are not altered and after a clean install those modifications get back on the system?? The best would be to make a copy of the hacked system which can be usefull for computer forensic and install a clean system in a controlled environment and after updates to use something like AIDE ([http://www.securitytube.net/video/4963](http://www.securitytube.net/video/4963)) and keep the log files at a place which are not reachable from the Internet (on usb stick in a safe). Maybe this is useful.

---

### Post by ian-weisser on 2013-09-26
> **Gyokuro said:**
>  how does the OP knows that his/her backups are not altered and after a clean install those modifications get back on the system??
Good point. Clarified above to restore data from pre-hack backups.

---

### Post by unspawn on 2013-09-27
> **Mahyar said:**
> There were no files in my home folder. (..) Should I reinstall the OS?
If there were no files left in your home directory but the rest of the files are there then their attempt to gain root may have not met with success.
This should not automagically mean you're safe: only the result from *investigating the cause and assessing damages* should count.
Let us know if you would like to do that.


> **Mahyar said:**
> Is there anything I can do to safeguard against this in the future?
To start with:
- Read your distributions documentation,
- Read your distributions security documentation,
- Install only the software you need -=[ now ]=-,
- Update software when updates are released,
- Disable services that are unused or easy to gain entry with,
- Restrict access to services wherever possible,
- Don't use simple passwords,
- Use pubkey auth only for SSH access,
- Enable proactive measures where possible,
 - Ensure you regularly audit your machine.

---

### Post by Mahyar on 2013-09-27
Thanks everyone for your wise words. Although I've used Linux since Ubuntu 6.06, I'm still pretty naive about network security. Hopefully this thread will help others before this happens to them.

For the record, I have re-installed from a pre-hack back-up.

unspawn: what are these services that are easy to gain entry with?

---

### Post by Gyokuro on 2013-09-27
Hi

Sorry to step in - everything which is accessible from outside and which is unpatched or due to wrong system administration is a security thread. You have to check what else you have to enable and only enable services/servers which you really need for outsite services/server communication and enable apparmor (minimal setup/system). In case there is no apparmor profile I can only suggest that you study apparmor documentation and create yourself a profile for the offered service/server in case there is non available. However study the provided apparmor profiles too as there is room for improvements (for my taste some of them are relaxed)  - you know your system and what is needed - tailor a strict profile.

---

### Post by unspawn on 2013-09-27
> **Mahyar said:**
> what are these services that are easy to gain entry with?
That depends on what's exposed, what authentication and what vulnerabilities are involved. Historically that means any R* services, for Desktop systems Vino and equivalents were mentioned quite a lot in this forum, these days commonly SSH with easy-to-guess passwords instead of pubkey auth and whatever runs in the web stack. For example running vulnerable outdated versions of forum or web log software, plugins, themes and such. While the web server user has less privileges than root it can store files, maybe run cron jobs, send email and such. That may not mean much at first sight, the majority of easy-to-expoit situations are only abused for sending spam or running a bot, but leaving events undetected or not correcting them timely allows an attacker to gain a foothold and seek to compromise the system more thoroughly and at a leisurely pace. The problem with that is not only a local security risk but also an increased threat for adjacent systems: which basically means us as we're all connected via the 'net. Loading a backup still requires you to change passwords / pass phrases and assess the system for loopholes.

Two things you should learn from your mishap are that *security is a continuous process requiring a layered approach* and that *Linux may be free to use but using it is not free of responsibilities*.

---

### Post by Wiking on 2013-09-28
> **tripp98 said:**
> Also give them something to do.  Install a honeypot and forward 22 to it.  Its designed to capture what the hackers try to do.

Care to mention any honeypots?

---

### Post by CCgirl6690 on 2013-09-30
poor thing LoL

---

### Post by tripp98 on 2013-10-05
[http://www.tracking-hackers.com/solutions/](http://www.tracking-hackers.com/solutions/)

i have used honeyd.  its fun watching what people try to do.  
it logs everything they type.

---

