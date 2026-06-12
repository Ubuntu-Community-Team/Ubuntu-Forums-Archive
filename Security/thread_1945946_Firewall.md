---
title: "Firewall"
date: 2012-03-23
forum: Security
---

### Post by 3dmatrix on 2012-03-23
How can a non-adminstrative user check if the firewal is working on the system or not ?
I have firestarter installed on the system but if i have doubts i have to login to the adminstative rights user to check. Is there any better way ?

---

### Post by Kevin McCready on 2012-03-23
Have a look at

[https://help.ubuntu.com/community/IptablesHowTo]("https://help.ubuntu.com/community/IptablesHowTo")

---

### Post by uRock on 2012-03-23
Moved to *Security Discussions*.

Once in a while I scan my ubuntu machines with Zenmap, which is in the repos. I have full confidence in the default settings of IPTables. I use GUFW to make changes to my firewall. I am not sure if Firestarter allows it, but GUFW has a setting to log denied traffic, which can be checked using the Log File Viewer.

---

### Post by jerome1232 on 2012-03-24
Firestarter hasn't been updated since 2005, you might want to look into a better frontend to iptables. A lot of people seem to like GUFW but there are others.

---

### Post by 3dmatrix on 2012-03-24
I earlier used Guarddog but now it seems it is not available in repo.
I felt more comfortable using that and do not understand much abt GUFW.
Is there any other good front end ?

But even in that case what is the easiest way to quickly check if the firewall is working in the background or not ?

What is Wireshark used for ?

---

### Post by agillator on 2012-03-24
If you have a recent kernel (i.e. 2.4.x or 2.6.x) you have a packet filtering (firewall) ruleset working. The easiest way to see what it is doing is by listing its rules. Use the command: sudo iptables -L -v -n. If it only shows three chains with each having a policy of 'ACCEPT' it is really doing nothing. If it lists a bunch of chains and rules, then it is working. What it is doing is a different story. Something like gufw makes this easier, but even gufw does not cover all the possibilities. However, if you wish to customize your firewall and do not want to go to the trouble of learning to use iptables directly, gufw is worth the effort to learn. It seems to be the most popular front end and is a quick way to get the basic firewall (ruleset) established and then customize it. gufw will tell you if it is 'running', as you asked. If you want to do it manually with probably a dozen or so commands on the command line, one way: get your ip address, ping that address to make sure it is allowed, save the current configuration, clear all chains, set the default policies to DROP, ping your ip address (which should fail), restore your original configuration. Of course you are giving Murphy an excellent opportunity to intervene, but . . . . Hope that helps a bit. If you nedd/want the specific commands, just ask.

---

### Post by Ms. Daisy on 2012-03-25
> **3dmatrix said:**
> But even in that case what is the easiest way  to quickly check if the firewall is working in the background or not  ? Depends on which firewall you're using.  If it's ufw/gufw you  would use
```
sudo ufw status
```
If you're using iptables, it's working by default unless you disable it (like agillator said)

For firestarter you would have to look at the firestarter documentation (I've never used it).

Either  way, you can check the firewall status from a guest or other user  account with limited privileges as long as the user knows the sudo  password.

> **3dmatrix said:**
> What is Wireshark used for  ? It is for monitoring network traffic, but it doesn't allow you  to control the traffic like a firewall does.  [http://www.wireshark.org/about.html](http://www.wireshark.org/about.html)

---

### Post by haqking on 2012-03-25
why not just put yourself in the sudo group.

thats why sudo and su exists to do as another user or do as superuser.

---

### Post by 3dmatrix on 2012-03-25
Tried using gufw but cud not make out much :)
felt there was nothing to do in it !

---

### Post by collisionystm on 2012-03-25
> **3dmatrix said:**
> How can a non-adminstrative user check if the firewal is working on the system or not ?
I have firestarter installed on the system but if i have doubts i have to login to the adminstative rights user to check. Is there any better way ?


As stated use GUFW.

You can also just open a terminal and type

sudo ufw status

---

### Post by haqking on 2012-03-25
you need to remove firestarter if you are to do anything with UFW/GUFW as they conflict.

but i still dont understand the whole logging in as another user thing, just use sudo

Cheers

---

### Post by sammiev on 2012-03-25
> **haqking said:**
> you need to remove firestarter if you are to do anything with UFW/GUFW as they conflict.

+1 firestarter is gone and UFW/GUFW is the way at this time.

---

### Post by 3dmatrix on 2012-03-25
I found a lot of tut regarding GUFW but i am not able to make out one very simple feature that i get in firestarter.

In firestarter there is one feature where i can make it restrictive by default and then allow only a few services. How can i do that in GUFW ? i.e. if i wish to restrict everything apart from say HTTP.

---

### Post by 3dmatrix on 2012-03-25
> **haqking said:**
> you need to remove firestarter if you are to do anything with UFW/GUFW as they conflict.

but i still dont understand the whole logging in as another user thing, just use sudo

Cheers

sudo doesnt works in case of restricted user

---

### Post by haqking on 2012-03-25
> **3dmatrix said:**
> I found a lot of tut regarding GUFW but i am not able to make out one very simple feature that i get in firestarter.

In firestarter there is one feature where i can make it restrictive by default and then allow only a few services. How can i do that in GUFW ? i.e. if i wish to restrict everything apart from say HTTP.

```
sudo ufw default deny
```

make sure you remove firestarter before using UFW.

see here for a good tutorial on UFW/GUFW and IPTables

[Dangertux Firewall Guide]("http://ubuntuforums.org/showthread.php?t=1876124")

---

### Post by haqking on 2012-03-25
> **3dmatrix said:**
> sudo doesnt works in case of restricted user

my point was that you are logging on as a restricted user and you have admin access as you said you can login with a admin account.

The point of sudo is to be able to perform admin action as another user such as restricted user.

su to another account or root if enabled

sudo do admin action as admin user if in sudo group

---

### Post by 3dmatrix on 2012-03-25
> **haqking said:**
> ```
sudo ufw default deny
```

make sure you remove firestarter before using UFW.

see here for a good tutorial on UFW/GUFW and IPTables

[Dangertux Firewall Guide]("http://ubuntuforums.org/showthread.php?t=1876124")

That seems to be a nice link. Thanx !

---

### Post by 3dmatrix on 2012-04-01
> **haqking said:**
> ```
sudo ufw default deny
```

make sure you remove firestarter before using UFW.

see here for a good tutorial on UFW/GUFW and IPTables

[Dangertux Firewall Guide]("http://ubuntuforums.org/showthread.php?t=1876124")

I have disabled Firestarter and enabled GUFW. Kindly see attachment. But i have not added any rules to GUFW and i can still access internet. How is that possible ? I do not understand this application ! I thought all data transaction should get restricted if there are no rules added to the firewall. Plz advise.

.

---

### Post by jerome1232 on 2012-04-01
you need to remove, delete firestarter.

Both Firestarter and Gufw are gui frontends to iptables, it's possible your firestarter 'disabled' setting is overriding ufw's settings.

To see what iptables says

```
sudo iptables -L
```

---

### Post by 3dmatrix on 2012-04-04
> **jerome1232 said:**
> you need to remove, delete firestarter.

Both Firestarter and Gufw are gui frontends to iptables, it's possible your firestarter 'disabled' setting is overriding ufw's settings.

To see what iptables says

```
sudo iptables -L
```

I am sorry but it is getting a lil difficult for me to understand using GUFW.
May be its a bit too simple.

sudo iptables -L is showing if the firewall is working or not.

I used the 'sudo ufw default deny' command and ofcourse all network transaction stopped.
But after that when i allow HTTP (outgoing / service) it still did not allow browsing.
Where am i going wrong ?

---

### Post by OpSecShellshock on 2012-04-04
> **3dmatrix said:**
> I am sorry but it is getting a lil difficult for me to understand using GUFW.
May be its a bit too simple.

sudo iptables -L is showing if the firewall is working or not.

I used the 'sudo ufw default deny' command and ofcourse all network transaction stopped.
But after that when i allow HTTP (outgoing / service) it still did not allow browsing.
Where am i going wrong ?

You'll need to allow DNS going out in order to resolve domains you want to browse to.

---

### Post by 3dmatrix on 2012-04-04
> **OpSecShellshock said:**
> You'll need to allow DNS going out in order to resolve domains you want to browse to.

But i cant see any option for DNS !

---

### Post by jerome1232 on 2012-04-04
You need to allow port 53 out

---

### Post by 3dmatrix on 2012-04-05
> **jerome1232 said:**
> You need to allow port 53 out
What is that Port for ?
Do i have to go to Simple or Advance Tab ?
Do i need to mention any protocol / service ?
If so which one ?

---

### Post by 3dmatrix on 2012-04-05
> **jerome1232 said:**
> You need to allow port 53 out
What is that Port for ?
Do i have to go to Simple or Advance Tab ?
Do i need to mention any protocol / service ?
If so which one ?

---

### Post by OpSecShellshock on 2012-04-05
You may need to check the "extended options" box. Go over to the Simple tab. Select Allow, Out, UDP, Port, and in the text box put in 53. When added, that rule will allow DNS.

---

### Post by haqking on 2012-04-05
See link for a good guide on firewalls in Linux and will solve your issues.  I posted it in previous post aswell and answers your questions.

[Dangertux Firewall Guide]("http://ubuntuforums.org/showthread.php?t=1876124")

Peace

---

### Post by 3dmatrix on 2012-04-07
Thanx! I hav started using GUFW.
Is there any good site or application to check the security of the firewall ?
I checked on Shield's up and it showed most of the ports as closed instead of Stealth.
In fact a few are even Open.
I specifically, added a rule to close that port, but it still shows it open.
Is it showing the status of my comp or that of the proxy that i am behind ?

---

### Post by sammiev on 2012-04-07
> **3dmatrix said:**
> Thanx! I hav started using GUFW.
Is there any good site or application to check the security of the firewall ?
I checked on Shield's up and it showed most of the ports as closed instead of Stealth.
In fact a few are even Open.
I specifically, added a rule to close that port, but it still shows it open.
Is it showing the status of my comp or that of the proxy that i am behind ?

I use GUFW as well and a VPN but with Shield's up I show Stealth on all ports with VPN or not. It can be something with your router.

---

### Post by BigCityCat on 2012-04-07
I remember when I first started using Linux about 7 years ago and I used to read posts from people that used to ask when they were going to remove Firestarter from the repositories. 7 Years ago.):P

---

### Post by 3dmatrix on 2012-04-07
> **sammiev said:**
> I use GUFW as well and a VPN but with Shield's up I show Stealth on all ports with VPN or not. It can be something with your router.

Well, its not 'MY' router. I use the connection provided by the  Univ and have to log in to their proxy server to access net.

So that info provided by Shields Up is of my comp or my proxy or my router ?
And how can i check MY comp ?

---

### Post by sammiev on 2012-04-07
> **3dmatrix said:**
> Well, its not 'MY' router. I use the connection provided by the  Univ and have to log in to their proxy server to access net.

So that info provided by Shields Up is of my comp or my proxy or my router ?
And how can i check MY comp ?

The info provided by Shields Up will be from the Univ or proxy and not likely from your computer.

---

### Post by 3dmatrix on 2012-04-08
> **sammiev said:**
> The info provided by Shields Up will be from the Univ or proxy and not likely from your computer.

So is there any way to check up MY comp's security status ?

---

### Post by haqking on 2012-04-08
> **3dmatrix said:**
> So is there any way to check up MY comp's security status ?

nmap

---

### Post by 3dmatrix on 2012-04-08
> **haqking said:**
> nmap

What is that Buddy :) Google says its Network Mapper but i am not sure abt the correct command (and options) and how to decipher the result. Read it also has some gui.


.

---

### Post by haqking on 2012-04-08
> **3dmatrix said:**
> What is that Buddy :) Google says its Network Mapper but i am not sure abt the correct command (and options) and how to decipher the result. Read it also has some gui.


.

[www.nmap.org](www.nmap.org)

there are hundreds of switches

it is a port scanner to scan your machine (though it is much more).

the simplest use of it would be

```
nmap ip.ip.ip.ip
```

where ip.ip.ip.ip is your ip address or just ```
nmap localhost
``` if doing it from same machine

a TCP connect scan which is really the most basic and stable of scans does a 3 way handshake

```
nmap -sT -p- -PN ip.ip.ip.ip
```

if you dont specify as in first command then nmap by default does a SYN scan and is popular due to speed and less noise generated on the wire.

read up on nmap.org or i will be here all day with various switches ;-)

Peace

---

### Post by Soul-Sing on 2012-04-08
PORT   STATE SERVICE VERSION
53/tcp open  domain  dnsmasq 2.59

thats new for me on 12.04......(dnsmasq thing)

---

### Post by haqking on 2012-04-08
> **leoquant said:**
> PORT   STATE SERVICE VERSION
53/tcp open  domain  dnsmasq 2.59

thats new for me on 12.04......(dnsmasq thing)

dnsmasq is a forwarder (and DHCP/TFTP server) for small home networks.

how does this relate to the questions ?

peace

---

### Post by Soul-Sing on 2012-04-08
> So is there any way to check up MY comp's security status ?

answer: > use nmap, via localhost

i post the outcome from my machine......

---

### Post by haqking on 2012-04-08
> **leoquant said:**
> answer: 

i post the outcome from my machine......

oh gotcha 

peace

---

### Post by jerome1232 on 2012-04-08
Scanning it from localhost is going to show all sorts of things that are only listening for connections from localhost, most likely your firewall will not be set to block connections from localhost to localhost (and if it is, your in for a headache) so scanning from localhost won't give you good results, your going to see things that are open but not listening to any other computer.

As much as I dislike shields up, it's testing what everything else on the Internet is going to be thinking your connections are coming from, whether that be your router or our proxy if your behind a proxy. Unless specifically set to do so, new-inbound connections sent to your router or proxy will never make it to your machine.

If you want to see the affects of your firewall, scan it [the machine whose firewall you are configuring] from another host on the local network.

---

### Post by haqking on 2012-04-08
> **jerome1232 said:**
> Scanning it from localhost is going to show all sorts of things that are only listening for connections from localhost, most likely your firewall will not be set to block connections from localhost to localhost (and if it is, your in for a headache) so scanning from localhost won't give you good results, your going to see things that are open but not listening to any other computer.

As much as I dislike shields up, it's testing what everything else on the Internet is going to be thinking your connections are coming from, whether that be your router or our proxy if your behind a proxy. Unless specifically set to do so, new-inbound connections sent to your router or proxy will never make it to your machine.

If you want to see the affects of your firewall, scan it [the machine whose firewall you are configuring] from another host on the local network.

I agree i should of mentioned that, though alot of people dont have more than one machine which is why i said localhost, but yes scanning yourself from yourself is not ideal.

The trouble is with shields up (apart from steve gibson) is it is likely scanning the internet facing device which is most commonly these days to be a home router and not the machine itself.

Of course after that is all said and done, to the OP dont assume that a firewall blocking connections or having closed ports is the be all and end all, you also need tight outbound rules to control outbound traffic to prevent arbitrary port binding and remote code exploitation which can result in callbacks.

Peace

---

### Post by 3dmatrix on 2012-04-08
Oh ! So how do i go abt it :) you mean i need to ask / use any of my neighbour to use nmap my IP ? Which seems a lil diff thing to do !

---

### Post by haqking on 2012-04-08
> **3dmatrix said:**
> So shud i use the "nmap localhost" command ?

well as said you can, but it is not a true response and may overwhelm with additional information not needed.

The best way is to direct it at your machine from another one.

But the point is as long as you have followed the guides in setting up your firewall you should be good, no connected system is 100% secure.

If you have followed the instructions then there should be no obvious gaping holes.

Also though i mentioned nmap, if you dont know how to use it the output probably wont make any sense either ;-)  I only mentioned it in direct response to your question about alternative method to test for open ports.

Peace

---

### Post by 3dmatrix on 2012-04-08
> **3dmatrix said:**
> Oh ! So how do i go abt it :) you mean i need to ask / use any of my neighbour to use nmap my IP ? Which seems a lil diff thing to do !

Yes I underatand what you mean ! But the point is i really do not understand what i have been doing with this new firewall :) so feel a lil unconfident.

---

### Post by haqking on 2012-04-08
> **3dmatrix said:**
> Yes I underatand what you mean ! But the point is i really do not understand what i have been doing with this new firewall :) so feel a lil unconfident.

well no getting your neighbour to do it wont have any effect as they are not on your LAN, unless of course they are ?

If they scan your public facing IP they are scanning your router and not your machine.

A firewall is one of many steps to take to help secure your system.

If you have followed the guide linked above a few times then all should be good.

A firewall is not the be all and end all of system security only one cog in the machine

The rest is down to safe good habits such as running NOScript in browsers, Apparmor for profiling applications.

Dont download files you dont trust or from sources you dont know or trust etc etc.

If you dont understand what you have been doing then i suggest a good starting point is to read the [Ubuntu Security Wiki]("https://wiki.ubuntu.com/BasicSecurity") and remember that security is a process not a product.

Peace

---

### Post by 3dmatrix on 2012-04-08
> **haqking said:**
> well no getting your neighbour to do it wont have any effect as they are not on your LAN, unless of course they are ?

If they scan your public facing IP they are scanning your router and not your machine.

A firewall is one of many steps to take to help secure your system.

If you have followed the guide linked above a few times then all should be good.

A firewall is not the be all and end all of system security only one cog in the machine

The rest is down to safe good habits such as running NOScript in browsers, Apparmor for profiling applications.

Dont download files you dont trust or from sources you dont know or trust etc etc.

If you dont understand what you have been doing then i suggest a good starting point is to read the [Ubuntu Security Wiki]("https://wiki.ubuntu.com/BasicSecurity") and remember that security is a process not a product.

Peace

Very well written :) I would try and follow. 
Would like to know if my neighbour is connected to the same router/using the same proxy (as is the case inside univ) then can i consider him/her to be on the same Lan ?

.

---

### Post by haqking on 2012-04-08
> **3dmatrix said:**
> Very well written :) I would try and follow. 
Would like to know if my neighbour is connected to the same router/using the same proxy (as is the case inside univ) then can i consider him/her to be on the same Lan ?

.

so when you say your neigbour you mean someone else sharing the same connection as you ? someone else on the University LAN ?

It depends on the infrastructure, i expect so but couldnt tell you for certainty.

However that being said running Nmap or other such tools on the University LAN which you do not own likely contravenes the acceptable use policy of the network.

Though port scanning is not in itself illegal (usually) it will certainly be judged based on the AUP of the University network, also port scanning if not done properly can generate alot of noise on the wire, enough sometimes to be considered a DoS attack so be warned.

---

### Post by 3dmatrix on 2012-04-10
Thanx a lot for all the info. I wish to ask some similar security related question, esp regarding what you said.

"The rest is down to safe good habits such as running NOScript in browsers, Apparmor for profiling applications.

Dont download files you dont trust or from sources you dont know or trust etc etc."

(1) If i do not run scripts in the browser then there are a lot of websites which i cannot use. In that case i usually try and use multiple browsers. With script enabled on one, for those websites that force us to use scripts, and disabled on the rest. In that case, if the script enabled browser gets 'infected' can it cause a security threat for the entire system and the other browsers also or it 'leaks' info ONLY from the browser which is script enabled ?

(2) Regarding software sources : i often come across instructions on forums and tutorials abt using deb files from sources that 'seems to be safe' like

[https://launchpad.net/~gnome3-team/+archive/gnome3/+files/gnome-shell-extensions-user-theme_3.2.0-0ubuntu1~oneiric1_all.deb](https://launchpad.net/~gnome3-team/+archive/gnome3/+files/gnome-shell-extensions-user-theme_3.2.0-0ubuntu1~oneiric1_all.deb)

Or adding repository PPA eg.

sudo apt-add-repository ppa:satyajit-happy/themes

How do we know which PPA / synaptic source is safe ?

I would like to try out different new things on linux, it helps in learning more abt Linux environment but without compromising on security.

Plz advise :)

.

---

### Post by jerome1232 on 2012-04-10
> **3dmatrix said:**
> 
Or adding repository PPA eg.

sudo apt-add-repository ppa:satyajit-happy/themes

How do we know which PPA / synaptic source is safe ?


When you add from PPA's you are trusting the maintainer of the ppa to not hand you malicious .debs and to keep their gpg key to themselves so that they are the only ones who can modify the packages etc...

---

### Post by 3dmatrix on 2012-04-10
> **jerome1232 said:**
> When you add from PPA's you are trusting the maintainer of the ppa to not hand you malicious .debs and to keep their gpg key to themselves so that they are the only ones who can modify the packages etc...

Is there any way to figure out if the 'owner' is authorised by Ubuntu or not ?

---

### Post by jerome1232 on 2012-04-10
Yes, AFAIK, none of them are, Ubuntu doesn't guarantee package integrity from PPA's.

It depends on how paranoid you are, I would trust most ppa's that are popular without a second thought. But some people are more paranoid than I. Now if I was managing a server I'd be a whole lot more cautious about adding ppa's than I am on my desktop machine, more from a "I don't want to break things with new, shiny, untested software" than a "I don't want to get owned by a trojan or virus" line of thought.

Hopefully my ranting is more clear than mud.:KS

---

### Post by 3dmatrix on 2012-04-10
*** So no PPA for me :) ***

> (1) If i do not run scripts in the browser then there are a lot of websites which i cannot use. In that case i usually try and use multiple browsers. With script enabled on one, for those websites that force us to use scripts, and disabled on the rest. In that case, if the script enabled browser gets 'infected' can it cause a security threat for the entire system and the other browsers also or it 'leaks' info ONLY from the browser which is script enabled ?

(2) Regarding software sources : i often come across instructions on forums and tutorials abt using deb files from sources that 'seems to be safe' like

[https://launchpad.net/~gnome3-team/+...eiric1_all.deb](https://launchpad.net/~gnome3-team/+...eiric1_all.deb)

Or adding repository PPA eg.

sudo apt-add-repository ppa:satyajit-happy/themes

How do we know which PPA / synaptic source is safe ?

How abt other deb locations ? Is mediabuntu repo maintained by Ubuntu and/or community or 3rd party ?

How abt the browser infection issue ?

.

---

### Post by 3dmatrix on 2012-04-18
> **haqking said:**
> so when you say your neigbour you mean someone else sharing the same connection as you ? someone else on the University LAN ?

It depends on the infrastructure, i expect so but couldnt tell you for certainty.

However that being said running Nmap or other such tools on the University LAN which you do not own likely contravenes the acceptable use policy of the network.

Though port scanning is not in itself illegal (usually) it will certainly be judged based on the AUP of the University network, also port scanning if not done properly can generate alot of noise on the wire, enough sometimes to be considered a DoS attack so be warned.

Wish to ask you somthing a lil different from what we had been talking here.
I wish to install VirtualBox. When i try to do so, i am asked to install fakeroot also. Can fakeroot be a security loophole ? If so what are the precautions that i should take ?

---

### Post by haqking on 2012-04-18
> **3dmatrix said:**
> Wish to ask you somthing a lil different from what we had been talking here.
I wish to install VirtualBox. When i try to do so, i am asked to install fakeroot also. Can fakeroot be a security loophole ? If so what are the precautions that i should take ?

fakeroot just "fakes" UID of 0 for file management, packaging etc.

Ive never seen it required for virtualbox, but cant imagine any major issue.

It is not real "root"

So during Virtualbox instal it tells you this ?

How are you installing virtualbox ?

I would download the .deb from oracle if i was you, also the extensions pack.

Peace

---

### Post by 3dmatrix on 2012-04-18
> **haqking said:**
> 
How are you installing virtualbox ?

Peace

I tried installing it using Synaptic and it said additional packages reqd . . . .  !

---

### Post by haqking on 2012-04-18
> **3dmatrix said:**
> I tried installing it using Synaptic and it said additional packages reqd . . . .  !

download the .deb

[http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html)

get the extensions pack also.

Peace

---

### Post by 3dmatrix on 2012-04-21
> **haqking said:**
> download the .deb

[http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html)

get the extensions pack also.

Peace

Welllll, downloaded it but as you know i am a lil scared abt security issues when its not from Ubuntu Repo :) so not sure what to do next ! I find Oracle similar to Microsoft and so untrustable. They can do anything to mint money.

---

### Post by haqking on 2012-04-21
> **3dmatrix said:**
> Welllll, downloaded it but as you know i am a lil scared abt security issues when its not from Ubuntu Repo :) so not sure what to do next ! I find Oracle similar to Microsoft and so untrustable. They can do anything to mint money.

Yeah Microsoft and Oracle are malicious criminals and Canonical are not ;-)

Take off your tin foil hat and download the .deb.

Who said the repos havent been compromised ?

If you dont want to then dont ;-)

Peace

---

### Post by 3dmatrix on 2012-04-21
> **haqking said:**
> Yeah Microsoft and Oracle are malicious criminals and Canonical are not ;-)

Take off your tin foil hat and download the .deb.

Who said the repos havent been compromised ?

If you dont want to then dont ;-)

Peace

Ok ! I will :)
But how do we switch between the two OS ?

---

### Post by rookcifer on 2012-04-21
> **jerome1232 said:**
> Yes, AFAIK, none of them are, Ubuntu doesn't guarantee package integrity from PPA's.

It depends on how paranoid you are, I would trust most ppa's that are popular without a second thought. But some people are more paranoid than I. Now if I was managing a server I'd be a whole lot more cautious about adding ppa's than I am on my desktop machine, more from a "I don't want to break things with new, shiny, untested software" than a "I don't want to get owned by a trojan or virus" line of thought.

Hopefully my ranting is more clear than mud.:KS

I agree with this assessment.  It all depends on your risk analysis and what you're willing to lose if you make a mistake.  The more vital the system is to you, the more paranoid you should be.  

I would say the vast majority of PPA's out there are put up by people just trying to help the community or those who have written software they don't feel like trying to get put in the official repositories.  So, on a desktop machine of the average user, I think most PPA's (especially the widely used ones) can be used safely and without second thought.

On the other hand, if you run a high value server, you probably don't want to use any PPA's at all.  Any software not in the official repositories that you need, you will probably want to compile from source directly (after you audit the code of course).

---

