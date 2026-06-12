---
title: "Suppressing Requests for Password"
date: 2010-07-11
forum: Security
---

### Post by novicee on 2010-07-11
**11 July 2010**

I use Ubuntu 10.04 and I want to be able to move around the system without having to frequently enter my password. 

For example, when waking up the system from a power save state or when accessing Synaptic Package Manager I do not want to be asked to enter my password.

There is nothing on my system that matters if its security is breached.

Is there a way to turn off these requests for a password?

---

### Post by kukker32 on 2010-07-11
it's made for security reasons, im not sure you can do anything about it.. i have tried without succes.

but!
If people can be victim to social engineering, it doesn’t matter how well the system’s security is constructed.

the password is to prevent stuff like this to happen ->
If you install a malicious deb you don’t need to ask for the password. The deb itself can run whatever it wants while it is being installed. It can disable services, replace them, and also do a simple rm -Rf /.
You don’t have to install some random deb you find on the web, that is why there are repositories and digital signatures. password requests and so on.

---

### Post by kukker32 on 2010-07-11
BTW i found this
[http://www.ubuntugeek.com/how-to-disable-password-prompts-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-password-prompts-in-ubuntu.html)

I can't find out how to solve that out, but maybe it's just me...

---

### Post by new_tolinux on 2010-07-11
Afaik there should be something possible by editing the sudoers file.

More info here: [http://www.sudo.ws/sudo/sudoers.man.html](http://www.sudo.ws/sudo/sudoers.man.html)
Another page: [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers) (maybe outdated, I only see 8.04 and 8.10 described)

---

### Post by celldweller1591 on 2010-07-11
Its all about file permissions that adds to linux security and it lacks in windows. Thats why malware are easy to make any significant dangerous changes to system files resulting in data theft and crashes, broken boot-loaders..etc ! Ubuntu escalates ur rights to root for some time after typing root password and after that specific period, they come back to normal. I would like to keep it that way :)

---

### Post by Rubi1200 on 2010-07-11
I hope you learn something from these links.

[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by novicee on 2010-07-11
**12 July 2010**
 
Thanks for the replies.
 
I will follow up the links provided.
 
If I find out how to turn off the password requests I will report back.
 
I am aware of the security benefits of the password requests but they are a nuisance when security is not important.

---

### Post by cariboo on 2010-07-11
Password aren't there to protect from physical access, they are there to protect you while you are on a network, be it local or the internet.

If someone has physical access to your computer all the passwords in the world aren't going to protect you.

---

### Post by novicee on 2010-08-21
**21 Aug 10**

This is a belated report back. I finally got the time to follow up  the links suggested in posts on this topic. The instructions at the link given by kukker32 on 11 July, did the job: 

[http://www.ubuntugeek.com/how-to-disable-password-prompts-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-password-prompts-in-ubuntu.html)


There were a lot of posts at this link about the wisdom of suppressing the password prompt however I was only interested in how it could be done and not whether it should be done.

---

### Post by xircon on 2010-08-21
Thank you!  Entering a password on a system used by multiple people is sensible, but on my laptop sat behind my router it can get very boring!(and as irritating as User Access Control:lolflag:).

Do I care if I get hacked? No, I rebuild my system every time I break it (which is often!), it is a big boys toy, everything important is stored safely on DropBox and a usb HD (belt & braces).

---

### Post by wacky_sung on 2010-08-21
> **xircon said:**
> Thank you!  Entering a password on a system used by multiple people is sensible, but on my laptop sat behind my router it can get very boring!(and as irritating as User Access Control:lolflag:).

Do I care if I get hacked? No, I rebuild my system every time I break it (which is often!), it is a big boys toy, everything important is stored safely on DropBox and a usb HD (belt & braces).

Well,i got the same kinda Don't Care attitude more a decade back before i got my hacked and my personal data got stolen.

If you think you got nothing important to steal,then you are wrong because your system can be used as zombie for botnet or hosting illegal files.
Beside that,you think all your vital files in a DROPBOX is safe.In fact you raise the interest of the cracker to break it. 

Apart from that,it take me years to learn to secure window OS and i have not formatted / rescue my [WinXP]("http://en.wikipedia.org/wiki/Windows_XP") for a decade with all my hardening.That does not mean it is crack proof but least it make it very tough fo a real intrusion as a normal home user.

Nothing is hackproof till you power off your system as hack can be done through internet / locally.

---

### Post by xircon on 2010-08-21
When I say important, I don't mean vital, just stuff I keep there in case my computer goes **** up:

-All my own programs (Free Pascal and VFP)
-My CV.
-My band's recordings.

Hack away, no personal info, no bank info.

---

### Post by Rinzwind on 2010-08-21
Not to be mean to others but you can adjust the time for sudo to re-ask for a password.
You can do that with sudo -v

If given the -v (validate) option, sudo will update the
user's timestamp, prompting for the user's password if
necessary. This extends the sudo timeout for another 15
minutes (or whatever the timeout is set to in sudoers) but
does not run a command.



You can also adjust /etc/sudoers and
- extend the time of 15 minutes
- add a user that does not require a password.

HOW? Not gonna tell :+

To anyone else but topicstarter: do not do this.
Ubuntu and other OS'es with sudo are set like this for a reason and the reason being: less security opens you up for malicious attacks and we do not need a 2nd OS that acts like Windows where anyone can look and adjust your data even if you put up the blindfolds.

---

### Post by xircon on 2010-08-21
Agreed - I know the risks and am willing to take them.

---

### Post by OpSecShellshock on 2010-08-21
Honestly, I do think that we're still at a point where the risk of accidental user-initiated system damage is greater than the risk of malicious outsider-initiated compromise. I still wouldn't recommend bypassing the privilege escalation process for most folks, though, because the difference between accidents and intrusions can largely be considered academic--that is, people will think they've been "hacked" when they've actually just done something wrong (or failed to do something necessary), and the solution (reinstall) is largely the same either way.

If users know what they're doing and either there's nothing at stake or they've accepted the risks, well, party on I guess. I've personally never seen password entry as much of an inconvenience. I definitely wouldn't recommend circumventing it for anyone who doesn't feel comfortable with assessing risk on the fly.

---

### Post by bodhi.zazen on 2010-08-21
I think we are discussing "gnome keyring"

If you google search there are several methods of disabling this "feature"

One is here :

[http://essayboard.com/2009/06/24/gnomes-keyring-tip-how-to-disable-keyring-or-remove-password-file/](http://essayboard.com/2009/06/24/gnomes-keyring-tip-how-to-disable-keyring-or-remove-password-file/)

IMO disabling gnome keyring is not a security hole, personally I do not use it at all.

---

