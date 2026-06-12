---
title: "The Truth about Linux?"
date: 2006-05-11
forum: The Cafe
---

### Post by Darklighter137 on 2006-05-11
Hello,

I am looking into giving my mom and dad the gift of Linux.  I keep telling them all about the benefits, but I have recently realized that I don't *know* for certain how Linux really handles security.  Could someone please address these points for me?

[LIST=1]
[*]Are there truly no viruses at all?  On some game development forums, people complained that their Linux machines needed to be repaired because of viruses.
[*]What needs to be done to maintain a computer with Linux whose users do little more than play cards, mahjong, and visit contest sites?
[*]We have dial-up here...  If I connect to the internet, am I going to suffer some manner of attack before I can install all of the security updates?
[*]As soon as I get my Windows machine re-ghosted, I suffer attacks from remote computers (trojan horses and things like that).  Will that affect a Linux machine (please note that I am sure my Win install wasn't corrupt at the time these things happened?
[*]What kinds of security threats does Linux really suffer?
[*]Finally, does Kbuntu come with drivers for Winmodems out of the box (I know Ubuntu doesn't)?
[/LIST] 

Thanks! =)

---

### Post by ComplexNumber on 2006-05-11
1) every OS has viruses. anyone who tells you that linux has no viruses whatsoever is misinformed. there are very few. plus the fact that unix systems have greater control over security than certain propriatory operating systems that you may be used to, in addition to the fact that its market share isn't that great at the moment compared to windows. however, because of the greater control and protection in the area of securtiy means that if both windows and linux had exactly 50%:50% market share and there were exactly 50%:50% viruses that were of similar nature for windows and linux, linux would still be by far the least vulnerable to being compromised. 

2) not a lot, if anything at all. less than you need with windows. with windows, its best to defrag every now and again, but this is not necessary in linux. there are defraggers available for linux though for those who demand absolute optimum performance (not that it makes much of a difference anyway). there is also no need to buy anti-malware packages and to run the software every few days or so. at least a firewall such as Firestarter would be ample for linux. never do without a firewall on any system. 

3) there were several tests done several months ago comparing unpatched systemsusing  windows 2003 server, windows XP, redhat linux , and suse linux. it was found that windows systems managed to last 1 hour and about 15 seconds before they were compromised. neither of the unpatched linux versions were compromised in the 6 months that the tests were conducted for.

4) no. there's no connection between the 2.

5) same as any other system. whilst there aren't that many virus/trojands/worms in the wild, there will always be hackers who will try any system by trying to see if there are any open or closed ports. thats why a firewall and a router that has every port _stealthed_ is important. if you have closed ports, it means that they can't get in at the moment, but they know you're there.

6) don't know. maybe someone else can help you there.

---

### Post by xXx 0wn3d xXx on 2006-05-11
[QUOTE=Darklighter137]Hello,

I am looking into giving my mom and dad the gift of Linux.  I keep telling them all about the benefits, but I have recently realized that I don't *know* for certain how Linux really handles security.  Could someone please address these points for me?

[LIST=1]
[*]Are there truly no viruses at all?  On some game development forums, people complained that their Linux machines needed to be repaired because of viruses.

There are about 40 viruses for Linux but none of them are severe or do any damage. If a situation ever arose there would most likely be a patch in 1-2 days.

[*]What needs to be done to maintain a computer with Linux whose users do little more than play cards, mahjong, and visit contest sites?

Not really anything but check for updates and install them.

[*]We have dial-up here...  If I connect to the internet, am I going to suffer some manner of attack before I can install all of the security updates?

I highly doubt it. Linux and Ubuntu in general is very secure.

[*]As soon as I get my Windows machine re-ghosted, I suffer attacks from remote computers (trojan horses and things like that).  Will that affect a Linux machine (please note that I am sure my Win install wasn't corrupt at the time these things happened?

Ubuntu has a built in firewall called iptables that is very powerful so no. And even of they got past-what would they do ?

[*]What kinds of security threats does Linux really suffer?

There are a few vunerabilties but all vunerabilties are patched very quickly. Don't run as root user all the time, use sudo.

[*]Finally, does Kbuntu come with drivers for Winmodems out of the box (I know Ubuntu doesn't)?

Most likely not since Kubuntu is just Ubuntu with the KDE desktop enviroment.

[/LIST] 

Thanks! =)[/QUOTE]
Hope that helps.

---

### Post by Sef on 2006-05-11
> Are there truly no viruses at all? On some game development forums, people complained that their Linux machines needed to be repaired because of viruses.

About the only viruses for GNU/Llinux are built in the labs for demonstartion purposes.  Apache, Linux based web server, had an attack a few years ago, but the patch had been out for about 6 months before the Slapper worm was released.  

> # What needs to be done to maintain a computer with Linux whose users do little more than play cards, mahjong, and visit contest sites?

Just install Firestarter, a firewall.  It turns on automatically, and runs in the background upon boot.  You don't see on, but it is.

> We have dial-up here... If I connect to the internet, am I going to suffer some manner of attack before I can install all of the security updates?

No.  

> # As soon as I get my Windows machine re-ghosted, I suffer attacks from remote computers (trojan horses and things like that). Will that affect a Linux machine (please note that I am sure my Win install wasn't corrupt at the time these things happened?

Well if the Windows partition becomes corrupted, it could cause problems.  Otherwise Windows is off when you have GNU/Linux running.

> # What kinds of security threats does Linux really suffer?

There are coding errors found, but, in general, they are quickly patched.   As long as you don't go into root, you will be safe.  

> # Finally, does Kbuntu come with drivers for Winmodems out of the box (I know Ubuntu doesn't)?

No. Kubuntu is Ubuntu with a K Desktop Environment (KDE) instead of a Gnome Desktop Environment (Gnome).  The backends are both the same.

---

### Post by GeneralZod on 2006-05-11
> **Darklighter137]
[*]Are there truly no viruses at all?  On some game development forums, people complained that their Linux machines needed to be repaired because of viruses.
[/QUOTE]

No said:**
> 
[*]What needs to be done to maintain a computer with Linux whose users do little more than play cards, mahjong, and visit contest sites?


With Ubuntu, very little.  I'd advise not adding them to the sudo'ers list and, if they are to be downloading stuff they want to keep, I'd advise making local, automated backups of the "valuable" directories such that the backups are read-only and owned by a different user.  If you install something like sshd, use a strong and long password (or maybe even public-key authentication) and disallow root logins.

> 
[*]We have dial-up here...  If I connect to the internet, am I going to suffer some manner of attack before I can install all of the security updates?


No - Ubuntu, unlike Windows, has no services listening by default, so there is nothing to really "attack".  Of course, browsing the web carries some risk if you go to shady sites ;)  You should be absolutely fine doing this.

> 
[*]As soon as I get my Windows machine re-ghosted, I suffer attacks from remote computers (trojan horses and things like that).  Will that affect a Linux machine (please note that I am sure my Win install wasn't corrupt at the time these things happened?


No, again due to the lack of listening services.  If you install sshd, though, you can expect anywhere from a handful to thousands of "attacks" per day.  

> 
[*]What kinds of security threats does Linux really suffer?


Honestly, very few and, as technology progresses (the inclusion of SELinux by default; compiling with stack protection; etc), I anticipate that they will grow fewer.  Of course, there is no defence against an unknowledgeable user with root access :)

> 
[*]Finally, does Kbuntu come with drivers for Winmodems out of the box (I know Ubuntu doesn't)?


Not to my knowledge, no - sorry :)

---

### Post by Sef on 2006-05-11
> 1) every OS has viruses. anyone who tells you that linux has no viruses whatsoever is misinformed. there are very few. plus the fact that unix systems have greater control over security than certain propriatory operating systems that you may be used to, in addition to the fact that its market share isn't that great at the moment compared to windows. however, because of the greater control and protection in the area of securtiy means that if both windows and linux had exactly 50%:50% market share and there were exactly 50%:50% viruses that were of similar nature for windows and linux, linux would still be by far the least vulnerable to being compromised.

GNU/Linux has 2/3 of the webserver market, and there has been two worms in the wild for it.  For Microsoft, the number runs into the thousands.

---

### Post by Virogenesis on 2006-05-11
[QUOTE=Darklighter137]
[*]Are there truly no viruses at all?  On some game development forums, people complained that their Linux machines needed to be repaired because of viruses.[/QUOTE]About 12 and most of those where made in labs.
[QUOTE=Darklighter137]
[*]What needs to be done to maintain a computer with Linux whose users do little more than play cards, mahjong, and visit contest sites?.[/QUOTE]
Nothing really, no registry to mess about with, don't really need to run anti virus software you might want to just incase you do infect your boss's\school's system.
You don't really need to defrag.

[QUOTE=Darklighter137]
[*]We have dial-up here...  If I connect to the internet, am I going to suffer some manner of attack before I can install all of the security updates?
[/QUOTE]Doubtful just use a secure password like you should do anyway.
[QUOTE=Darklighter137]
[*]As soon as I get my Windows machine re-ghosted, I suffer attacks from remote computers (trojan horses and things like that).  Will that affect a Linux machine (please note that I am sure my Win install wasn't corrupt at the time these things happened?[/QUOTE] You should be more secure from the word go ubuntu and many other distros don't have ports open like windows does.
[QUOTE=Darklighter137]
[*]What kinds of security threats does Linux really suffer?
[/QUOTE] They get rooted if you have ssh running and use a crap password. and 
[QUOTE=Darklighter137]
[*]Finally, does Kbuntu come with drivers for Winmodems out of the box (I know Ubuntu doesn't)?
[/QUOTE] Ermm ubuntu is the same as kubuntu but basically with a different front end.
My suggestion would be to switch to a external modem you should be able to pick one up for cheap off of ebay.

---

### Post by ComplexNumber on 2006-05-11
[quote=Sef]GNU/Linux has 2/3 of the webserver market, and there has been two worms in the wild for it.  For Microsoft, the number runs into the thousands.[/quote] i'm not disputing that. i'm just giving him a realistic viewpoint. i don't think its a good idea to say to people "don't worry. linux has no viruses". its always good to be aware of what might be, so that people can keep things in perspective and be realistic

---

### Post by Darklighter137 on 2006-05-11
Hi!  Thanks so much guys!  But, could you please tell me what this "sshd" thing is that someone mentioned? =)

---

### Post by sinkxdie on 2006-05-11
What would a linux virus be able to do actually?
Unless you've enabled root login or something, the system completely boarded up from permanent damaging.

---

### Post by GeneralZod on 2006-05-11
[QUOTE=Darklighter137]Hi!  Thanks so much guys!  But, could you please tell me what this "sshd" thing is that someone mentioned? =)[/QUOTE]

If you don't know what it is, you don't need to worry about it ;)

sshd is a Secure SHell server Daemon, and allows you to log in to your computer remotely:

[http://en.wikipedia.org/wiki/Secure_shell](http://en.wikipedia.org/wiki/Secure_shell)

---

### Post by ComplexNumber on 2006-05-11
[quote=Darklighter137]Hi!  Thanks so much guys!  But, could you please tell me what this "sshd" thing is that someone mentioned? =)[/quote]
[this]("http://en.wikipedia.org/wiki/Ssh") will explain it.

---

### Post by Virogenesis on 2006-05-11
[QUOTE=Darklighter137]Hi!  Thanks so much guys!  But, could you please tell me what this "sshd" thing is that someone mentioned? =)[/QUOTE]
sshd stands for secure shell daemon, it allows you to log into the computer remotely from anywhere in the world, ssh isn't turnt on by default so you don't need to worry.
Also a user is locked into their own directory so they cannot delete other users files or write to the system this makes it harder for viruses to spread around the system.

---

### Post by Darklighter137 on 2006-05-11
Thanks, guys! ^_^

---

### Post by skippy81 on 2006-05-11
OK I agree fully with all the positive points made about linux.  However I do feel that a few points need to be made.  

1) I can't see anyone being able to use linux for longer than a couple of weeks without having to use the shell prompt.

2) You will have compatibilty problems with some websites (not many though). Upload scripts sometimes dont work well with linux.  

3) You will have to get the hardware spot on if you want your folks to have an easy time with linux.

Dont get me wrong, I love the shell prompt and having a powerful OS.  I think that the virus/hacking risk on linux is incredibly low, providing you get a distro which doesnt run tons of services as standard.

---

### Post by ComplexNumber on 2006-05-11
>  1) I can't see anyone being able to use linux for longer than a couple of weeks without having to use the shell prompt.
i can't see anyone using windows for longer than a couple of weeks without banging their heads against the computer screen and giving up in dispair. at least linux has a painless and workable solution  ;)

---

### Post by Carrots171 on 2006-05-12
[QUOTE=skippy81]1) I can't see anyone being able to use linux for longer than a couple of weeks without having to use the shell prompt.[/QUOTE]

I don't have to use the shell every few weeks to get stuff done. Yes, with Ubuntu you do have to use the terminal to configure some things. But in SuSE or MEPIS, there is a graphical tool/program for just about everything. And once the initial setup of the computer is finished, I don't see why you would have to use the shell. Right now the only reason I would use the shell on my computer is because I need to install a downloaded .deb file. But in Dapper, you can install downloaded .deb files graphically! =D>

Linux doesn't support all hardware, and I wish that more hardware vendors supported Linux, but I don't think that the hardware has to be "on the spot" for things to be easy, either.

---

### Post by Gustav on 2006-05-12
[QUOTE=skippy81]1) I can't see anyone being able to use linux for longer than a couple of weeks without having to use the shell prompt.[/QUOTE]
I have never had the *need* to use the shell prompt since I updated to breezy about half a year ago. (and you really don't need it for that either if your graphics configuration doesn't brake as it did for me)

I use the shell prompt at least a couple of times per day but thats either because it's faster (and more fun) than the gui or because I install some package that I don't really need (mostly a newer rhythmbox or some game) (and you can easely make this doable with a gui (and it is from the start in Dapper)).

---

### Post by aysiu on 2006-05-12
[QUOTE=skippy81]
1) I can't see anyone being able to use linux for longer than a couple of weeks without having to use the shell prompt.[/QUOTE] I think I used Mepis for an entire month last year without ever touching the command-line. Not having to touch the shell was a big thing for me as a Linux newcomer--one of the main reasons I stayed away from Ubuntu at the time.

Now that I have Ubuntu installed and configured, though, I do not *need* to touch the command-line at all. I use the command-line because I want to, but all of the tasks I do can be done through GUI as well.

---

### Post by prizrak on 2006-05-12
[QUOTE=sinkxdie]What would a linux virus be able to do actually?
Unless you've enabled root login or something, the system completely boarded up from permanent damaging.[/QUOTE]
It would have the same rights as the user who executed it, which means that even if your install survives your files could easily be trashed and if you have network shares it could easily propogate to your other machines. Just because it won't overwrite system files it doesn't mean that it's harmless ;)

---

### Post by IYY on 2006-05-12
>    1. Are there truly no viruses at all? On some game development forums, people complained that their Linux machines needed to be repaired because of viruses.

Of course there are viruses. I mean, if you define a virus as any malicious program, I could give you a virus shell script right now:

```
sudo nohup rm -rf /
```

If you execute this code, you will erase your entire system, silently. But you'd have to run this code. It won't magically appear on your system and be executed. So, as long as you download your programs from a trustworthy source (sourceforge, the repositories), you have pretty much no chance of getting a virus.

>    2. What needs to be done to ain a computer with Linux whose users do little more than play cards, mahjong, and visit contest sites?

Just install these games and download the java and flash plugins for firefox.

> 
   3. We have dial-up here... If I connect to the internet, am I going to suffer some manner of attack before I can install all of the security updates?

No. This is not Windows, such things don't happen. Ubuntu's quick release cycle will also protect you here (your system can't be older than a few months, so it is secure enough even without updates).

>    4. As soon as I get my Windows machine re-ghosted, I suffer attacks from remote computers (trojan horses and things like that). Will that affect a Linux machine (please note that I am sure my Win install wasn't corrupt at the time these things happened?

That is a known problem with Windows, and it doesn't happen on Linux (unless you install something like an SSH server and have very weak passwords, like 'guest'). 

>    5. What kinds of security threats does Linux really suffer?

I think the biggest problem is hackers trying to get in through SSH, FTP or Telnet by using common username/password combinations. Of course, if you don't have these servers installed, you're safe.

>    6. Finally, does Kbuntu come with drivers for Winmodems out of the box (I know Ubuntu doesn't)?

No, but it's fairly easy to install.

---

