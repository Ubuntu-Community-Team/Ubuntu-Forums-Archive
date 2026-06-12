---
title: "virus writing contest for linux....?"
date: 2008-10-01
forum: The Cafe
---

### Post by EnGorDiaz on 2008-10-01
wth...


look at this
[http://linux.slashdot.org/article.pl?sid=01/10/13/1346243&mode=thread](http://linux.slashdot.org/article.pl?sid=01/10/13/1346243&mode=thread)


there is already the possibility of ubuntu being targetted in the linux community bcus debian does take the pie in the linux community 


why even write viruses for something with no restraint?

---

### Post by Ms_Angel_D on 2008-10-01
Because you can't fix the weakness if you don't know that it exists. I think that's the point of the challenge. That being said I'm sure it's difficult to do I mean the guy has been throwing the challenge out there for 2 yrs now and still no one has claimed the Money.

---

### Post by eentonig on 2008-10-01
Basically, it's a challenge to prove how strong Linux is. The mere fact that he can make that challenge and two years later he's still sitting on his money, is a strong prove how secure linux is.

It's actually one of the best ways of testing your security, because when they do succeed in hacking that machine, they will have to reveal how they did it. And thus, allow the community to close that hole in the defenses. Makes definitively sense to me.

---

### Post by EnGorDiaz on 2008-10-01
> **MetalHellsAngel said:**
> Because you can't fix the weakness if you don't know that it exists. I think that's the point of the challenge. That being said I'm sure it's difficult to do I mean the guy has been throwing the challenge out there for 2 yrs now and still no one has claimed the Money.

its wierd bcus these systems are so secure its great you know when i first came to linux i was so surprised by the security

---

### Post by davidryder on 2008-10-01
With the way things are it is going to depend on the user lowering security.

EDIT: It's awesomely impressive that it's been 2 years and no luck. I heart Linux.

---

### Post by Ms_Angel_D on 2008-10-01
[QUOTE=EnGorDiaz]its wierd bcus these systems are so secure its great you know when i first came to linux i was so surprised by the security 	[/QUOTE]

Yeah If your an ingrained Windows User (As I was) It quite strange to come into a system where that's no longer something you have to constantly be concerned with, sometimes I would even say almost boring...lol. However I personally was aware of the more secure environment provided by Linux as My websites are all on linux servers.

---

### Post by EnGorDiaz on 2008-10-01
> **MetalHellsAngel said:**
> Yeah If your an ingrained Windows User (As I was) It quite strange to come into a system where that's no longer something you have to constantly be concerned with, sometimes I would even say almost boring...lol. However I personally was aware of the more secure environment provided by Linux as My websites are all on linux servers.

but windows users find it really comfortable they find it comfortable to be affraid they put there trust into it

imaggine this scenario 

a windows vista lover comes and reads this article what do you thin his/her thougths on this if they were programmer or hacker? (if they exist in windows GUI)


the reason i say if they exist is ive seen alot of try hards on the actual gui itself an they go on hacker forums saying oh i sql injected this site an they really havent done 
anything

then theres another type of would be windows gui hacker

the i can run nmap to pfft user that really says something lulz.

---

### Post by earthpigg on 2008-10-01
> **davidryder said:**
> EDIT: It's awesomely impressive that it's been 2 years and no luck. I heart Linux.

actually, i think it's been longer than that.

[http://linux.slashdot.org/article.pl?sid=01/10/13/1346243]("http://linux.slashdot.org/article.pl?sid=01/10/13/1346243")

> *£10,000 Prize for Linux Virus Challenge Re-Issued *
Posted by CmdrTaco  on Sat Oct 13, **_2001_** 11:45 AM

[http://software.silicon.com/security/0,39024655,11028211,00.htm]("http://software.silicon.com/security/0,39024655,11028211,00.htm")

> *The £10,000 Linux virus challenge*
Published: 12 October **_2001_** 17:40 BST

---

### Post by Twitch6000 on 2008-10-01
> **EnGorDiaz said:**
> wth...


look at this
[http://linux.slashdot.org/article.pl?sid=01/10/13/1346243&mode=thread](http://linux.slashdot.org/article.pl?sid=01/10/13/1346243&mode=thread)


there is already the possibility of ubuntu being targetted in the linux community bcus debian does take the pie in the linux community 


why even write viruses for something with no restraint?

That is kind of old news <.<.

Plus there have been many viruses for Linux written.Infact just for this sort of thing.Bliss is one that comes to mind >.>.

---

### Post by MaxIBoy on 2008-10-01
Ken Thomson himself said that a virus could "reproduce" by injecting its own code into a compiler itself. Compiling a fresh install of the compiler could be made useless. 

After that, it's just a matter of inserting a very small amount of malicious code into anything you compile. It's only a matter of time before you run something with root privileges, and then there goes the neighborhood.

---

### Post by the_darkside_986 on 2008-10-01
Editing the compiler might be difficult if it is read-only to the standard user. But a concern would be having a user writable folder (such as ~/MyPrograms) in one's $PATH. It is too easy to put a fake ls in it and next time Terminal is used, it will execute the malicious ls instead of /usr/bin's ls. Of course, the user's executable path folder might have some ridiculous name that no one would guess but I've seen distros that put a ~/bin folder automatically which is a very bad idea if that is in $PATH.

---

### Post by Dr Small on 2008-10-01
> **the_darkside_986 said:**
> Editing the compiler might be difficult if it is read-only to the standard user. But a concern would be having a user writable folder (such as ~/MyPrograms) in one's $PATH. It is too easy to put a fake ls in it and next time Terminal is used, it will execute the malicious ls instead of /usr/bin's ls. Of course, the user's executable path folder might have some ridiculous name that no one would guess but I've seen distros that put a ~/bin folder automatically which is a very bad idea if that is in $PATH.
I have ~/bin and it is also in my $PATH. It doesn't make Linux less secure, just more convienant than placing all my scripts in /usr/bin. Just remember, someone or something has to gain access to my account before it can go placing a debunk compiler in my ~/bin.

---

### Post by MaxIBoy on 2008-10-01
All you need is an infected .run file. Those will often need root access to run. Simply set it up so that the first time the .run file does something which needs root access, it's legit. So in other words, you'll see something like "cannot write to /usr/local/games: access denied" instead of "cannot write to /usr/lib/gcc/whatever: access denied." So you'll run it again with root privileges, it will inject its stuff into the gcc source, and use your existing gcc install to compile it into an a.out somewhere, then all you need is a simple "mv ~/a.out /usr/bin/gcc" and your computer is infected.

---

### Post by aysiu on 2008-10-01
> **MaxIBoy said:**
> All you need is an infected .run file. Those will often need root access to run. Simply set it up so that the first time the .run file does something which needs root access, it's legit. So in other words, you'll see something like "cannot write to /usr/local/games: access denied" instead of "cannot write to /usr/lib/gcc/whatever: access denied." So you'll run it again with root privileges, it will inject its stuff into the gcc source, and use your existing gcc install to compile it into an a.out somewhere, then all you need is a simple "mv ~/a.out /usr/bin/gcc" and your computer is infected.
Wouldn't it be easier to just make a game.deb file people double-click to install?

---

### Post by MaxIBoy on 2008-10-01
.run, .deb, same thing. Infecting the compiler would be so that any compiled code from now on will have the "installer" for the virus in it. The virus itself would be seperate from it. 

Worst-case scenario: some poor developer builds a Debian package of his project and uploads it to SourceForge. Or worse yet: some poor Linux developer gets every other Linux developer's compiler infected (although less likely because I'm pretty sure Linux devs don't send each other prebuilt packages.)

---

### Post by Dr Small on 2008-10-01
> **MaxIBoy said:**
> .run, .deb, same thing. Infecting the compiler would be so that any compiled code from now on will have the "installer" for the virus in it. The virus itself would be seperate from it. 

Worst-case scenario: some poor developer builds a Debian package of his project and uploads it to SourceForge. Or worse yet: some poor Linux developer gets every other Linux developer's compiler infected (although less likely because I'm pretty sure Linux devs don't send each other prebuilt packages.)
I think this thread should be locked and moved out of sight before anyone gets any ideas! Also, we need to find some way to silence you. What will you accept? Cash?

---

### Post by MaxIBoy on 2008-10-01
Ten thousand pounds' worth in U.S. dollars. :D Actually, I don't know if I'd have the skill to make this, so I'll settle for a nice Voodoo Envy.

---

### Post by EnGorDiaz on 2008-10-02
> **Dr Small said:**
> I think this thread should be locked and moved out of sight before anyone gets any ideas! Also, we need to find some way to silence you. What will you accept? Cash?

i think not

this is kinda an eye opener really

i think we as ubuntu users should all compile something that says a little warning message inside the gdebi to inspect for destruction scripts 

for example my plans are to make ipcop merge with ubuntu using the kernel files and i might make a program to dissalow certain commands or atleast put a warning out there

it would be good it could be great for our systems and we do need a more flex firewall

---

### Post by EnGorDiaz on 2008-10-02
the big thing is ubuntu is the number one in linux we should make it number one with security aswell

---

### Post by MaxIBoy on 2008-10-02
Just realized, you could infect dpkg too.

---

### Post by jrusso2 on 2008-10-02
> **MaxIBoy said:**
> All you need is an infected .run file. Those will often need root access to run. Simply set it up so that the first time the .run file does something which needs root access, it's legit. So in other words, you'll see something like "cannot write to /usr/local/games: access denied" instead of "cannot write to /usr/lib/gcc/whatever: access denied." So you'll run it again with root privileges, it will inject its stuff into the gcc source, and use your existing gcc install to compile it into an a.out somewhere, then all you need is a simple "mv ~/a.out /usr/bin/gcc" and your computer is infected.

That would not be a virus but a trojan.  Of course you can use social engineering to infect Linux with a trojan. Always download from known and trusted sources still apply to any operating system.

---

### Post by MaxIBoy on 2008-10-02
It's a trojan that doesn't rely on social engineering. Just crack open the getdeb repos.


And the infected .run works as advertised (If it's supposed to install ETQW, it will install ETQW normally, but it will also infect your computer.)

---

### Post by jrusso2 on 2008-10-02
> **MaxIBoy said:**
> It's a trojan that doesn't rely on social engineering. Just crack open the getdeb repos.


And the infected .run works as advertised (If it's supposed to install ETQW, it will install ETQW normally, but it will also infect your computer.)

Well if you were to crack getdeb, I am sure they would find out fast and people that check md5sums would not be fooled.

This contest is for a computer virus

A computer virus is a computer program that can copy itself and infect a computer without permission or knowledge of the user.

---

### Post by EnGorDiaz on 2008-10-02
> **MaxIBoy said:**
> It's a trojan that doesn't rely on social engineering. Just crack open the getdeb repos.


And the infected .run works as advertised (If it's supposed to install ETQW, it will install ETQW normally, but it will also infect your computer.)

wow omg this thread is getting abit extreme i think ubuntu and linux should really review there security

unless the developers have other reason to why this cant happen

---

### Post by EnGorDiaz on 2008-10-02
> **jrusso2 said:**
> Well if you were to crack getdeb, I am sure they would find out fast and people that check md5sums would not be fooled.

This contest is for a computer virus

A computer virus is a computer program that can copy itself and infect a computer without permission or knowledge of the user.

yes you are right there will only be a few patchs to stop this also there would be no need to worry about vulnerabilitys

a topic like this was discussed on the solaris forums a guy said i can do that and he infected over 100 solaris computers with a worm....

i thought about this alot thats why im having a dual os set up ipcop on one screen ubuntu on the other

---

### Post by original_jamingrit on 2008-10-02
right, it would have to exploit something in kernel-space directly to actually be a virus.  To use a user-space exploit as a vector would also mean you'd have to get the user to run as root (through social-engineering), or at least run that app with root privileges.  Another possibility is that the "virus" could be a script which internally uses sudo when the user doesn't need a password for sudo.

Both possibilities are negligible for ordinary users that are able to recognize most obvious forms of social engineering.  Strictly speaking, any malware that is not self-replicating (depends on compiler or dpkg for replication) is not a virus, and therefore can be trivially defended against.

---

### Post by rune0077 on 2008-10-02
Here's a short list of known viruses and more that have worked on Linux: [http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses#Threats](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses#Threats)

I doubt many of them were very successfully, and exploits are luckily quickly closed once discovered, but it just goes to show that it is quite possible to write these viruses, as long as there's some kind of security exploit available.

---

### Post by EnGorDiaz on 2008-10-03
> **rune0077 said:**
> Here's a short list of known viruses and more that have worked on Linux: [http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses#Threats](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses#Threats)

I doubt many of them were very successfully, and exploits are luckily quickly closed once discovered, but it just goes to show that it is quite possible to write these viruses, as long as there's some kind of security exploit available.

most of them werent except for lion it was a Ddos attack on apache servers

---

### Post by Ioky on 2008-10-03
Serious, there are many people think, the reason why Linux is so security is because they think, it is much more up to date with patch. And windows can do the same if they are up to date with patch. Come on, stop prove your ignorant. I mean, with the newest windows Vista SP1, it can be hack in two days, at the most of time that is needed. Linux, however would take a longer time. I am not saying Linux cannot be hack, in fact it can, There are many hold from many app, and other stuff that run on Linux. For people who really know Linux, they can fix any problem Linux has as long they do have the skill to do so. But in OS like windows. You simply can't do much about it until M$ take their time to fix it for you, or add something into it to make it work. At the end, you ending up stuff over stuff, to just keep your system save, while the system itself are still weak. (and annoying)

---

### Post by EnGorDiaz on 2008-10-04
> **Ioky said:**
> Serious, there are many people think, the reason why Linux is so security is because they think, it is much more up to date with patch. And windows can do the same if they are up to date with patch. Come on, stop prove your ignorant. I mean, with the newest windows Vista SP1, it can be hack in two days, at the most of time that is needed. Linux, however would take a longer time. I am not saying Linux cannot be hack, in fact it can, There are many hold from many app, and other stuff that run on Linux. For people who really know Linux, they can fix any problem Linux has as long they do have the skill to do so. But in OS like windows. You simply can't do much about it until M$ take their time to fix it for you, or add something into it to make it work. At the end, you ending up stuff over stuff, to just keep your system save, while the system itself are still weak. (and annoying)

good point alot of systems are hackable even systems with an ipcop box no successful attempts so far on ipcop but i think someone actualy can hack it

---

