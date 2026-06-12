---
title: "Someone's been at my computer, how do i find out for sure?"
date: 2008-07-19
forum: Security
---

### Post by Bruno12 on 2008-07-19
so if you password has been deactivated, and your log directories /var/log have been deleted, and the .bash_history has been deleted, I mean properly deleted by someone malicious or a total amateur, this is saying to me someone has been on my computer? There's no evidence of the last files i looked at, wiped. I am suspicious already, but how can i find out when someone logged into my computer, and what else can i check that they might not have got to? I'm guessing someone must have had physical access to my machine to do this, i've read there are no linux viruses which could do anything like this, and no way a hacker could access my machine any other way...so help me find out who the culprit is please.

---

### Post by zipperback on 2008-07-19
For starters you could check to see if there is a root kit installed.

sudo apt-get install chkrootkit


However given the information that you provided, I would say that your box has been compromised, and is not secure.

Backup any important data, and then do a brand new installation of Ubuntu on your system,

Do NOT use the same username and/or password on the fresh install.

Also change all your email account passwords and other account passwords you might have as well.

Also, Setup a proper firewall.

- zipperback
:popcorn:

---

### Post by hyper_ch on 2008-07-19
if you suspect anyone has been in your machine, then there's only one thing you can do:

NEW INSTALL

you'll never be sure if there is something left inside. And maybe also use full disk encryption ;)

---

### Post by Yannick Le Saint kyncani on 2008-07-19
Yep :

- Boot live cd, remove any $HOME/.* files/directories as they may contain backdoors.

- Reinstall a fresh ubuntu without internet access, so that known security holes won't be exploited until you've updated.

- Setup a firewall, because a door should always be closed unless there is a reason to leave it opened.

- Connect to internet, *update*.

Now make sure you keep a firewall up and running and most important, keep your system up-to-date and use open-source only software (flashplugin-nonfree, I'm looking at you).

Keep backups, and also consider running an encrypted filesystem.

PS: and don't use third-party software or repositories. Only use ubuntu's ones, that way, if a backdoor is implemented and discoverd in a software available in official repos, you will hear and know about it.

---

### Post by Flyingjester on 2008-07-19
> **zipperback said:**
> for Starters You Could Check To See If There Is A Root Kit Installed.

Sudo Apt-get Install Chkrootkit


However Given The Information That You Provided, I Would Say That Your Box Has Been Compromised, And Is Not Secure.

Backup Any Important Data, And Then Do A Brand New Installation Of Ubuntu On Your System,

Do Not Use The Same Username And/or Password On The Fresh Install.

Also Change All Your Email Account Passwords And Other Account Passwords You Might Have As Well.

Also, Setup A Proper Firewall.

- Zipperback
:popcorn:

+1

---

### Post by hyper_ch on 2008-07-19
firewall is not necessary by default... and the TO suspect someone had physical access... so a firewall won't help there

Besides, a firewall is already installed, called  iptables, and it is just not configured to block anything as there are no services running by default...

---

### Post by mikewhatever on 2008-07-19
> ...so help me find out who the culprit is please.

Finger prints? But seriously, there is no way you can find that out. Backup and reinstall.

---

### Post by Yannick Le Saint kyncani on 2008-07-19
> **hyper_ch said:**
> firewall is not necessary by default...

I think the question should not be "is a firewall useful or necessary" but "is there any reason to leave any port opened".
While you're at it, why don't you provide a root account without password ? If there is no connecting from outside, there is no need to disable the root account or use a password to protect it, right ?

There is no need to leave any port opened, so the default configuration should be to close everything.

---

### Post by hyper_ch on 2008-07-19
> **Yannick Le Saint kyncani said:**
> I think the question should not be "is a firewall useful or necessary" but "is there any reason to leave any port opened".
A firewall is useful under certain circumstances but still might not be necessary ;)

Why close all ports if nothing is running on it? A

> **Yannick Le Saint kyncani said:**
> While you're at it, why don't you provide a root account without password ? If there is no connecting from outside, there is no need to disable the root account or use a password to protect it, right ?
Actually, by default the root account on ubuntu has no password ;) but you seem not to understand what a root password would be useful for besides connections from outside ;) I only say PEBCAK

> **Yannick Le Saint kyncani said:**
> There is no need to leave any port opened, so the default configuration should be to close everything.
there is no need to close everything... we're not on windows here where one needs to close everything down so the nag- and ad- and malware can't phone home ;)

---

### Post by Yannick Le Saint kyncani on 2008-07-19
> **hyper_ch said:**
> Why close all ports if nothing is running on it? [snip] there is no need to close everything... we're not on windows here where one needs to close everything down so the nag- and ad- and malware can't phone home ;)

From [http://en.wikipedia.org/wiki/Firewall](http://en.wikipedia.org/wiki/Firewall) :

Without proper configuration, a firewall can often become worthless. Standard security practices dictate a "default-deny" firewall ruleset, in which the only network connections which are allowed are the ones that have been explicitly allowed. Unfortunately, such a configuration requires detailed understanding of the network applications and endpoints required for the organization's day-to-day operation. Many businesses lack such understanding, and therefore implement a "default-allow" ruleset, in which all traffic is allowed unless it has been specifically blocked. This configuration makes inadvertent network connections and system compromise much more likely.


You should not even wonder why adding an extra level of security. Basic security practice dictates that everything should be denied unless stated otherwise.

Obviously, allowing anything and everything does make things simpler, I can understand that.

---

### Post by hyper_ch on 2008-07-19
If you have no services running, what does a firewall add in terms of security? Nothing ;)

But then I have to agree on something:
> **Yannick Le Saint kyncani said:**
> Without proper configuration, a firewall can often become worthless.
denying all traffic by default is no proper configuration either hence your suggestion makes it also worthless ;)

---

### Post by Yannick Le Saint kyncani on 2008-07-19
> **hyper_ch said:**
> If you have no services running, what does a firewall add in terms of security? Nothing ;)

Even without any services running, a firewall does add in term of security :

- In a workplace, it's another way to ensure no one opens a service, thus breaking security policies without explicit consent by the network/unix admin.

- For a home user, when you install a package, it will pull in dependencies and one of them may be a server. Setting up a firewall prevents unexpected surprises where you're running, say, samba, on the internet.

So, even if you don't have a service running, its port should be closed. And even if a service is running and its port is blocked by a firewall, its configuration should prevent any access from unauthorized network. For security purposes, paranoia should be the norm.

> **hyper_ch said:**
> denying all traffic by default is no proper configuration either hence your suggestion makes it also worthless ;)

You should read again, the article never said anything like "denying all traffic by default is no proper configuration". In fact, it's stating the complete opposite, and it's a perfect configuration.

What it says is :
> Many businesses lack such understanding, and therefore implement a "default-allow" ruleset

Essentially, it's saying that even some businesses allow everything in by default because it's simpler when by security, everything should be denied by default and allowed after careful consideration on a case by case basis.

---

### Post by Dr Small on 2008-07-19
> **Yannick Le Saint kyncani said:**
> 
- For a home user, when you install a package, it will pull in dependencies and one of them may be a server. Setting up a firewall prevents unexpected surprises where you're running, say, samba, on the internet.

So, even if you don't have a service running, its port should be closed. And even if a service is running and its port is blocked by a firewall, its configuration should prevent any access from unauthorized network. For security purposes, paranoia should be the norm.


Actually, iptables is installed on Ubuntu by default, but there are no rules applied. If,(and using your example), you install a package and it's dependency is perhaps Apache, having a firewall does not prevent unauthorized access. Since there is no rules, there are no rules to DENY traffic to this port. Thus, the port is open.

All ports are open by default, just no services listening behind them. When you install services, the ports still remain open, unless you have applied rules to iptables. Having a firewall does not guarantee that when services are installed, ports are closed.

Dr Small

---

### Post by Shippou on 2008-07-19
Honestly, this is the first time I have encountered such problems. 

And this is somewhat related to this thread: [http://ubuntuforums.org/showthread.php?t=863912](http://ubuntuforums.org/showthread.php?t=863912)

Thanks for Bruno12 for starting this thread.

---

### Post by hyper_ch on 2008-07-20
> **Yannick Le Saint kyncani said:**
> - In a workplace, it's another way to ensure no one opens a service, thus breaking security policies without explicit consent by the network/unix admin.
In a workplace John Doe does not have the right to install anything... hence - so basically a firewall does not add any security either if the admins do their job ;)

> **Yannick Le Saint kyncani said:**
> 
Well, you should know what you install.. and in that case you did install a service... an honestly, most people that install a service want ti to be accessible from the outside... so, I'd like to know what package that an average home user would secretly also install a service? That would be very interesting to know.

[QUOTE=Yannick Le Saint kyncani;5419521]So, even if you don't have a service running, its port should be closed.
There's absolutely no point in that.

> **Yannick Le Saint kyncani said:**
> And even if a service is running and its port is blocked by a firewall, its configuration should prevent any access from unauthorized network.
Why do you install then a service? If the port is blocked by everything there is no point in installing a service...

> **Yannick Le Saint kyncani said:**
> You should read again, the article never said anything like "denying all traffic by default is no proper configuration".
It does... denying all traffic is no proper configuration ;) If you deny all traffic, why are you hooked up to the net anyway?


> **Yannick Le Saint kyncani said:**
> Essentially, it's saying that even some businesses allow everything in by default because it's simpler when by security, everything should be denied by default and allowed after careful consideration on a case by case basis.
So, this article is aimed at businesses? Who wrote that article? Does it aim at businesses with sys admins and an IT department? Does it consider what different OSes run on the lan? From how the article is written I'd rather tend to think it's about small businesses with no it departments and where mostly Windows is used...

> **Shippou said:**
> And this is somewhat related to this thread: [http://ubuntuforums.org/showthread.php?t=863912](http://ubuntuforums.org/showthread.php?t=863912)
I don't think it's related.

---

### Post by brian_p on 2008-07-20
I find this

> **Dr Small said:**
> 

All ports are open by default, just no services listening behind them. When you install services, the ports still remain open, . . . .


and this

> **Yannick Le Saint kyncani said:**
> 

So, even if you don't have a service running, its port should be closed.

confusing; maybe others do too.

A closed port is a port which does not have a service listening on it. With nothing listening there is nothing open and nothing to close.

---

### Post by Dr Small on 2008-07-20
> **brian_p said:**
> 
A closed port is a port which does not have a service listening on it. With nothing listening there is nothing open and nothing to close.

Technically, the port is open, since there are no iptable rules telling the port to DENY traffic. If I have all of my iptable rules cleared (like I do on my system, anyhow), when I start SSH, the port automatically opens because the service is listening behind this port, and there were no rules to tell it to DENY traffic on this port.

So from the technical point of view, when you install Ubuntu, you have no firewall rules, and all ports are wide open. As you install services, these ports begin to have services listening behind them.

The whole point to this matter is, having the firewall installed to it's default configuration, when a person installs a services, the firewall does *not* close the port. The port is open.

Dr Small

---

### Post by brian_p on 2008-07-20
> **Dr Small said:**
> Technically, the port is open, since there are no iptable rules telling the port to DENY traffic.

A port which is not serving is closed. The state of any iptables rules is not relevant because the machine will respond like this:

[INDENT]telnet 88.255.xxx.xxx 25
Trying 88.255.xxx.xxx...
telnet: Unable to connect to remote host: Connection refused[/INDENT]

You cannot get any more closed than that!
 
> So from the technical point of view, when you install Ubuntu, you have no firewall rules, and all ports are wide open.

All ports on a default install are firmly closed to the outside world. They will respond as above.

> As you install services, these ports begin to have services listening behind them.

Now some ports are open. They will respond like this:

[INDENT]telnet 88.255.xxx.xxx 80
Trying 88.255.xxx.xxx...
Connected to 88.255.xxx.xxx.
Escape character is '^]'.[/INDENT]

> The whole point to this matter is, having the firewall installed to it's default configuration, when a person installs a services, the firewall does *not* close the port. The port is open.

If you are saying

```
sudo ufw enable
```

doesn't close any ports, I'd agree. But if you maintain

[INDENT]no service + no iptables rule = open port[/INDENT]

then it is obvious I disagree.

---

### Post by bcl1713 on 2008-07-20
Wow this thread got lost quick.. Poster said he was pretty sure the person had physical access.  This eliminates the firewall argument that is now spanning two pages all together.

---

### Post by Yannick Le Saint kyncani on 2008-07-20
Yeah, unfortunately, if he had physical access, could remove /var/log, which means root privileges, and has removed command history, there is not much to identify the culprit.

Except maybe fingerprints, as suggested, or torture, but it's forbidden, or having security cameras all over the place o.O , but that would just be crazy :lolflag:

---

### Post by hyper_ch on 2008-07-20
encryption is the only way to protect yourself against physical access...

---

### Post by Gizkaguy on 2008-07-21
Backup your data and do a fresh install. Check your logs frequently, and update your firewall.

---

### Post by damis648 on 2008-07-21
What I would do is change my password and make sure automatic login is off (assuming they had physical access). I would also remove the recovery option from your menu.lst because the password can be changed this way. (You can access it by adding "single" to the kernel line).

---

### Post by tact on 2008-07-21
> **hyper_ch said:**
> encryption is the only way to protect yourself against physical access...

*BZZZZT*  Wrong answer   :)

Its not new news but watch the video anyway for a graphic demo how easy it is to get encryption keys for several popular whole disk encryption packages including truecrypt and dm-crypt.

[http://citp.princeton.edu/memory/](http://citp.princeton.edu/memory/)

Pay special attention to the part where they power off a laptop, pull out the battery, plug in a specially prepared USB drive, power up the laptop and boot from the USB drive, grab a snapshot of the memory contents and extract disk encryption key....  (source code supplied for all utils needed).

No need even to "freeze" the RAM but that apparently gives you time to go for lunch, have a few beers, order pizza, spend some quality time with your significant other - between powering off the laptop and extracting the keys.  :)

---

### Post by hyper_ch on 2008-07-21
> **tact said:**
> *BZZZZT*  Wrong answer   :)
Not really... you know of any other way? Except putting it into your bank's treasure vault?

> **tact said:**
> [http://citp.princeton.edu/memory/](http://citp.princeton.edu/memory/)
That has been discussed here also a couple of times... while in running state who could get one access or suspect it's encrypted? and while turned off how would that approach you say help?

---

### Post by tact on 2008-07-21
> **hyper_ch said:**
> Not really... you know of any other way? Except putting it into your bank's treasure vault?


That has been discussed here also a couple of times... while in running state who could get one access or suspect it's encrypted? and while turned off how would that approach you say help?

"encryption is the only way to protect yourself against physical access..."
- is your assertion.   

Watch the video - encryption is no protection at all, trivial to get around, for an attacker with physical access.  

Yes - its not a new news story (I said that above too).  But that its been discussed before does not negate the point:   encryption is no protection at all, trivial to get around, for an attacker with physical access.  

So ...  "encryption is the only way to protect yourself against physical access..."   is still a "wrong answer".   *BZZZT*   ;)

That I cannot offer any "right answer" other than locking it in a bank vault - does not negate the point and make the "encryption" answer less wrong.  

Don't get me wrong.  I am not saying that encryption is a waste of time or useless.  It has its uses.   I use it.  I use full disk encryption (dm-crypt) and I have certain files/folders encrypted again ontop of the fully encrypted drive.

I am saying one thing only ...  in response to the statement "encryption is the only way to protect yourself against physical access..."     -  Its not even "a way" to defend against a hands-on physical attack - so it cannot possibly be the ONLY way.

Totally unrelated and nonetheless interesting...  in other news - the "plausible denyability" selling point of truecrypt (encrypted containers hidden inside of encrypted containers....)  has also been compromised.  Schneier has found a way to prove that a hidden encrypted volume exists in certain circumstances.  This does not crack the encryption and reveal the contents.  Just proves that a hidden volume exists thus removing the ability to deny the existance.

---

### Post by hyper_ch on 2008-07-21
> **tact said:**
> Watch the video - encryption is no protection at all, trivial to get around, for an attacker with physical access.
You get it wrong.
If the computer is turned off --> the attacker can't get around but by brute-forcing
If the computer is turned on --> the attacker first would have to assume that it might be encrypted and then he would have to take appropriate measures. If the computer is turned on and a screen saver is running with a password asking, IMHO (at least for the time being) it is much more likely an attacker will just turn computer off and on again --> no chance that he's getting the passsword from dram.
So this leaves, up to now, only the way if the computer is turned on and the attacker knows or assumes it's encrypted --> so far a very unlikely scenario (IMHO)

> **tact said:**
> So ...  "encryption is the only way to protect yourself against physical access..."   is still a "wrong answer".   *BZZZT*   ;)
As pointed out above, it's not ;)

> **tact said:**
> I am saying one thing only ...  in response to the statement "encryption is the only way to protect yourself against physical access..."     -  Its not even "a way" to defend against a hands-on physical attack - so it cannot possibly be the ONLY way.
If you only let your computer run when you're at it - what most people do - it is the only way... however you have other suggestions?

---

### Post by tact on 2008-07-21
> **hyper_ch said:**
> You get it wrong.
If the computer is turned off --> the attacker can't get around but by brute-forcing

You haven't watched the video have you?   It was all about getting around encryption WITHOUT brute-forcing despite the computer being turned off.

Had you watched the video you would have seen an "attacker" with physical access to a computer with whole disk encryption.  You would have seen that "attacker" power off the laptop, plug in a USB drive, power on the laptop and boot from the USB drive... take a memory dump of the DRAM (what was in it BEFORE it was powered off) then sort through and find the key to the disk encryption.

No brute forcing.  No super computer and 20million years.  He found.... the.... KEY in the DRAM of a powered off PC.  And the process is trivially easy.  

So once more for effect: 
- "encryption is the only way to protect yourself against physical access..." [hyper_ch]
- Its not even "a way" to defend against a hands-on physical attack

Cheers

---

### Post by hyper_ch on 2008-07-21
If you have read the paper you'd have seen even in the abstract that "DRMS used in most modern computr retain their contents for seconds to minutes after power is lost".
Hence if you poweroff the computer a bit longer it is perfectly safe ;)

---

### Post by kevdog on 2008-07-21
Actually a very interesting concept -- however they did state even in the video, that the computer was at risk if stolen in sleep mode state or was powered on.  The only specifically implicated Bit Locker for being vulnerable while the computer was turned off.  

Although I guess whole disk encryption could be relatively termed "protection through obscurity", I find the likelihood of this entire process very remote, however for theoretical discussions its very interesting.

---

### Post by tact on 2008-07-21
> **hyper_ch said:**
> If you have read the paper you'd have seen even in the abstract that "DRMS used in most modern computr retain their contents for seconds to minutes after power is lost".
Hence if you poweroff the computer a bit longer it is perfectly safe ;)

A little impractical...  
-  how many minutes, after powering off your PC,  before you are safe? 
-  most people do leave their PC turned on (perhaps locked) when they go make a coffee or take a toilet stop (at home or office).  Most people don't shut down, wait 1?, 5?, 10? minutes for DRAM to die, then only go pee-pee and have to wait for their machine to reboot when they get back.
-  most people don't know 10 minutes ahead of time when someone might snatch their laptop right from under their nose at Starbucks, and only those with good sources (not open sources) will ever know 10 minutes ahead of time when the FBI might break down their door.

But...  as impractical as it may seem to always be prepared for every possibility your PC may be accessed by someone, and ensure that your PC/laptop has been turned off for at least 10-20 minutes beforehand - I agree with you that whole disk encryption does have its uses.   (Like when the DRAM has been powered off for some time)   :)

However...  I would tend to steer away from giving assurances that encryption is THE answer to unauthorised access....

---

### Post by hyper_ch on 2008-07-21
> **tact said:**
> A little impractical...
That's your opinion...

> **tact said:**
> -  how many minutes, after powering off your PC,  before you are safe?
Have a look at the study ;)

> **tact said:**
> -  most people do leave their PC turned on (perhaps locked) when they go make a coffee or take a toilet stop (at home or office). Most people don't shut down, wait 1?, 5?, 10? minutes for DRAM to die, then only go pee-pee and have to wait for their machine to reboot when they get back.
There are other options as well as shutting down... check the study ;)


> **tact said:**
> -  most people don't know 10 minutes ahead of time when someone might snatch their laptop right from under their nose at Starbucks,
Why do you leave your notebook unattended?

> **tact said:**
> and only those with good sources (not open sources) will ever know 10 minutes ahead of time when the FBI might break down their door.
The FBI does not concern me at all

> **tact said:**
> But...  as impractical as it may seem to always be prepared for every possibility your PC may be accessed by someone, and ensure that your PC/laptop has been turned off for at least 10-20 minutes beforehand - I agree with you that whole disk encryption does have its uses.   (Like when the DRAM has been powered off for some time)   :)
If you're that paranoid at the FBI catchin you then you should be prepared for every possibility ;)

> **tact said:**
> However...  I would tend to steer away from giving assurances that encryption is THE answer to unauthorised access....
I'm open to other suggestions? Under normal circumstances encryption is THE answer to unauthorized access.

---

### Post by smc18 on 2010-02-08
EDIT: WHOA!! Really old POST. I'm sorry.

Video Includes:

1- Running Windows XP
2- Plugged in external HDD with bootable tool installed
3- Removed Battery (Laptop shuts off)
4- Reinsert battery and boot off the external HDD.

My question is, that tool would only work if your BIOS boot order was set to boot to USB-HDD before internal HDD.

In the paper they also mentioned being able to boot from PXE, but still Network boot would still have to be above internal HDD in the boot order.

Excellent tool they made, I just thought I'd point out the above two complications.

So always leave your internal HDD #1 in your BIOS boot order ;)

(On a side note: I wonder if the contents in the RAM would disappear before you could enter BIOS and edit the Boot order)

---

### Post by lisati on 2010-02-08
> **smc18 said:**
> (On a side note: I wonder if the contents in the RAM would disappear before you could enter BIOS and edit the Boot order)
I've had the rare occasion on restarting when Ubuntu goes through its boot up, and a distorted version ot an XP splash screen shows momentarily just before the Ubuntu splash screen appears. Probably something to do with the screen mode changing before Ubuntu has had a chance to update the contents of video RAM. (I vaguely remember seeing a thread somewhere about this confusing a new user.)

---

