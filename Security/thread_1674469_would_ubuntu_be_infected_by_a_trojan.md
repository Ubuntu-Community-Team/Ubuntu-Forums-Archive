---
title: "would ubuntu be infected by a trojan ?"
date: 2011-01-23
forum: Security
---

### Post by neil_1 on 2011-01-23
was doing some searching to see which whould suite me , ubuntu and kubuntu and came across this weird site where they make trojans for windows and kubuntu =/
my q :
would ubuntu get infected by a trojan made for kubntu ?

---

### Post by matt_symes on 2011-01-23
Hi

Can you provide a link to the site ?

Kind regards

---

### Post by DeviantGuy on 2011-01-23
Yeah, the website link would be ideal to get. 
Even though I'm rather new (Going on to Intermediate) to Ubuntu. I really don't think so. But if this website starts to make trojans for Ubuntu. You may want to contact Cancordal, Or the community, Or fix it yourself.

---

### Post by neil_1 on 2011-01-24
@matt_symes
here
[http://albertopajuelo.blogspot.com/2010/12/demonio-troyano-opensource-en-c-y-qt4.html](http://albertopajuelo.blogspot.com/2010/12/demonio-troyano-opensource-en-c-y-qt4.html)
 
Dependencies:
Qt-4.7 or higher 
pic of it running with kubuntu
[http://3.bp.blogspot.com/_r4nGutBkNys/TSnS-SsPqnI/AAAAAAAAAAw/PlEy2FAtdBI/s1600/linuxaxp.jpeg](http://3.bp.blogspot.com/_r4nGutBkNys/TSnS-SsPqnI/AAAAAAAAAAw/PlEy2FAtdBI/s1600/linuxaxp.jpeg)

---

### Post by OpSecShellshock on 2011-01-24
Well, if you install a trojan, then yes, it will affect your system. I don't think there's any way that it would install without intervention of the user. A lot of things written with KDE desktops in mind run OK under a Gnome desktop, but it would depend on the specific code probably.

---

### Post by neil_1 on 2011-01-24
> **OpSecShellshock said:**
> Well, if you install a trojan, then yes, it will affect your system. I don't think there's any way that it would install without intervention of the user. 
intervention of a user ?
means it will have to run as sudo to infect us ?

---

### Post by Dr Small on 2011-01-24
> **neil_1 said:**
> intervention of a user ?
means it will have to run as sudo to infect us ?
Meaning, it will not work or act by itself, (example, browsing a website) but requires **you** the user to install it or run it.

---

### Post by neil_1 on 2011-01-24
> **Dr Small said:**
> Meaning, it will not work or act by itself, (example, browsing a website) but requires **you** the user to install it or run it.
so if we click on it (even by mistake) it wont run like how it does on windows ?

---

### Post by laithbsoul on 2011-01-24
not to mention most viruses for Linux require you to compile them

---

### Post by Dr Small on 2011-01-24
> **neil_1 said:**
> so if we click on it (even by mistake) it wont run like how it does on windows ?
The worst a trojan/virus can do (if you should accidentally run something without root privileges) is total your user account; not the whole system. Now, if it requires sudo (root) privileges to run, and you enter the password, it could be a simple trojan and wipe your entire disk. But, that would be your fault for entering the sudo password.

Security lies within the user of who runs the system. Think smart, live safe.

---

### Post by cariboo on 2011-01-24
It's good to see you again Dr Small.

---

### Post by Dr Small on 2011-01-24
> **cariboo907 said:**
> It's good to see you again Dr Small.
It's nice to see you again too :)

---

### Post by leorolla on 2011-01-24
> **neil_1 said:**
> so if we click on it (even by mistake) it wont run like how it does on windows ?

> **Dr Small said:**
> The worst a trojan/virus can do (if you should accidentally run something without root privileges) is total your user account; not the whole system. Now, if it requires sudo (root) privileges to run, and you enter the password, it could be a simple trojan and wipe your entire disk. But, that would be your fault for entering the sudo password.

Well, if you think of a personal computer for a single user...

A trojan making damage confined to user's home is in some cases just as bad as hurting the rest of the system. Not hurting /etc or /bin doesn't mean it is not dangerous, and doesn't make a trojan less trojan. Just like a Windows trojan will not hurt your hardware but still is considered very bad, yet if such trojan doesn't even touch /system it can make damage to user's data and it is still a trojan.

So, neil_1's question may sound naïve but he went right to the point, what he asks makes perfect sense.

Ubuntu is safe because it prevents the user from doing this. It surrounds human behavior by adequate protection. If the user downloads a file and double-click on it, by default the file is **not** executed. This is what prevents dumb Ubuntu users from running trojans.

If the user intentionally changes its permissions so that it can be executed, then I suppose such user should be aware of what he is doing. People downloading and e-mailing executable files is simply ridiculous, it's part of a culture based on ignorance, predominant in other OS's.* If you e-mail a file together with instructions on how to change its permissions so that the recipient can watch a nice video, and you have enough many stupid friends to follow your instructions, and your friends have enough many stupid friends themselves, then in this case you would indeed have a trojan that is capable of surviving Ubuntu's ecosystem. I'm not aware of such a trojan, it's far from current reality. In summary, don't worry, you're fine.

(*) In years I have never downloaded executables. Actually, when I installed the dropbox .deb file, yes, it did download a binary and did change its  permissions, that was the only exception but I don't believe it had a trojan.

If you have multiple users...

Yes, your 5-year-old son is allowed to download, compile, and run whatever he wants, including the worst trojan available out there, if he is interested in this subject ans wants to play with theoretical viruses. In this case all the damage will be confined to his home folder, unless he has the root password or he boots your system from a LiveCD/USB. As long as you don't care about his home folder, don't worry, you're fine.

---

### Post by koenn on 2011-01-24
> **neil_1 said:**
> 
pic of it running with kubuntu
[http://3.bp.blogspot.com/_r4nGutBkNys/TSnS-SsPqnI/AAAAAAAAAAw/PlEy2FAtdBI/s1600/linuxaxp.jpeg](http://3.bp.blogspot.com/_r4nGutBkNys/TSnS-SsPqnI/AAAAAAAAAAw/PlEy2FAtdBI/s1600/linuxaxp.jpeg)
I don't read spanish so I can't comment on the article itself, and meybe I missed something, but ...
are you sure that's kubuntu ? 
If so, i't like to know which versions of kubuntu have paths like "c:/Documents and Settings/albetro" and since when linux has support for drive letters.

---

### Post by paju1986 on 2011-01-24
Hi, I'm the original author of this RAT, sorry for my bad english but I'm spanish.
This pic is the Client in Kubuntu 10.10 connected to a server in a Windows XP host.
I did those screenshot because I was doing some probes between OSs.

My trojan doesn't need root privilegies since it doesn't try to modify any of the root filessytem, but it need to execution permissions in order to run on Kubuntu.

---

### Post by bodhi.zazen on 2011-01-24
> **koenn said:**
> I don't read spanish so I can't comment on the article itself, and meybe I missed something, but ...
are you sure that's kubuntu ? 
If so, i't like to know which versions of kubuntu have paths like "c:/Documents and Settings/albetro" and since when linux has support for drive letters.

Just with wine (only time I can think of) 

There are (rare) reports of windows malware running in wine.

;)

---

### Post by neil_1 on 2011-01-24
thanks leorolla for the explanation :)
> **leorolla said:**
> Yes, your 5-year-old son ...
im 13 :O
> **paju1986 said:**
> My trojan doesn't need root privilegies since it doesn't try to modify any of the root filessytem, but it need to execution permissions in order to run on Kubuntu.
huh ? :S

---

### Post by OpSecShellshock on 2011-01-25
What the author of the code was saying there is that the trojan can run under regular user permissions because it does not attempt to alter any system files (which actually makes discovery and cleanup easier), but that it still needs to be made executable manually by the user in order to run on Kubuntu because by default it would not be executable.

---

### Post by koenn on 2011-01-25
> **paju1986 said:**
> 
This pic is the Client in Kubuntu 10.10 connected to a server in a Windows XP host.
I did those screenshot because I was doing some probes between OSs.


so, it's a client-server thingy ?


what does it do ?

---

### Post by DZ* on 2011-01-25
> **Dr Small said:**
> The worst a trojan/virus can do (if you should accidentally run something without root privileges) is total your user account; not the whole system. Now, if it requires sudo (root) privileges to run, and you enter the password, it could be a simple trojan and wipe your entire disk. But, that would be your fault for entering the sudo password.

You could have entered sudo password just before to run something from the menu that requires authorization (like gparted) or used F2-gksudo (i.e. created an authorization window for a process with no TTY)

Then a malicious program can reuse that authorization. I actually went into trouble to check if it works on Ubuntu, by writing a script that sits there and wakes up once in a while to check for sudo authorization, and yes it does work. Of course, there is a simple solution not to use an account with admin privileges for anything except administration, but the way Ubuntu installation is setup, most single user installs end up with a single account that is also an admin account.

---

