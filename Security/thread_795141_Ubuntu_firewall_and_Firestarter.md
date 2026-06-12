---
title: "Ubuntu firewall and Firestarter?"
date: 2008-05-15
forum: Security
---

### Post by MilesRdz on 2008-05-15
Sup guys!
Does the Ubuntu firewall get disabled when I run the Firestarter firewall? I wouldn't want any conflicts between these two programs.

---

### Post by Nepherte on 2008-05-15
Firestarter is not the firewall itself but merely a gui for firewall in linux called IPTables. So there is no conflict at all

---

### Post by hyper_ch on 2008-05-16
are you sure you actually need any of this?

---

### Post by MilesRdz on 2008-05-19
> **hyper_ch said:**
> are you sure you actually need any of this?

No. :)

---

### Post by hyper_ch on 2008-05-19
then I wouldn't bother installing either oen ;)

---

### Post by MilesRdz on 2008-05-19
> **hyper_ch said:**
> then I wouldn't bother installing either oen ;)

I was curious. ;)

---

### Post by kamaji792 on 2008-05-25
I have a server version of hardy.  Out of the box when I list the iptables setup I get:
```
$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```
I am not entirely sure but I believe that is saying it will accept a connection from anyone/anywhere.  It may be because it is the server version but you could see what you get when you type:
```
sudo iptables -L
```
in a terminal.

I have played around with **ufw** (Uncomplicated FireWall), which is installed on Hardy but not enabled.  It is a command line interface to iptables.

Try:
[help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)
for a ufw tutorial.

I could not get ufw to work with my samba the way I wanted it so I have started playing with iptables direct.  The best introduction I have found is:
[help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

If you want a GUI front end to iptables then almost everyone appears to use **Firestarter**.

Enjoy

---

### Post by mbaker824 on 2008-05-25
> **MilesRdz said:**
> Sup guys!
Does the Ubuntu firewall get disabled when I run the Firestarter firewall? I wouldn't want any conflicts between these two programs.

Almost any "firewall" software you'll find for Linux is just a front-end for netfilter, which is built in to almost all newer Linux distributions. iptables, by the way, is the userspace configuration program for netfilter.

I disagree with the assertion someone implied here that you don't need to worry about a firewall.  Linux machines definitely can be (and are) attacked, and protecting your machine with a simple firewall is prudent.

You don't have to install any additional software to set up a Linux firewall, although if you do it manually you'll have to dig into the details of netfilter and iptables.  If you prefer to do it the easy way, Firestarter and Guarddog are good front-ends, although Firestarter is probably a bit simpler.

Good luck,
Mark

---

### Post by mbaker824 on 2008-05-25
> **kamaji792 said:**
> I have a server version of hardy.  Out of the box when I list the iptables setup I get:
```
$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```
I am not entirely sure but I believe that is saying it will accept a connection from anyone/anywhere.  It may be because it is the server version but you could see what you get when you type:
```
sudo iptables -L
```
in a terminal.

That is indeed what 'iptables -L' is telling you here.  The INPUT chain is empty (as are FORWARD and OUTPUT, but they have nothing to do with inbound traffic destined for the local machine) and its default policy is ACCEPT, so any inbound packets will be accepted.

Mark

---

### Post by hyper_ch on 2008-05-26
> **mbaker824 said:**
> I disagree with the assertion someone implied here that you don't need to worry about a firewall.  Linux machines definitely can be (and are) attacked, and protecting your machine with a simple firewall is prudent.

Ok, on a normal home desktop installation, what services are listening that need to be protected by a firwall?
Let me guess: 0

Why is a firwall important on Windows? Because there also outgoing traffic needs to be filtered. All that spyware and stuff the gets installed among "legal" software. You don't have this in Linux...

So, why do you need a firewall?

---

### Post by mbaker824 on 2008-05-26
> **hyper_ch said:**
> Ok, on a normal home desktop installation, what services are listening that need to be protected by a firwall?
Let me guess: 0

Why is a firwall important on Windows? Because there also outgoing traffic needs to be filtered. All that spyware and stuff the gets installed among "legal" software. You don't have this in Linux...

So, why do you need a firewall?

Do you believe attacking a listening service is the only mode of attack available?  Do you believe there are no keystroke loggers and rootkits for Linux?

Mark

---

### Post by hyper_ch on 2008-05-26
> **mbaker824 said:**
> Do you believe attacking a listening service is the only mode of attack available?  Do you believe there are no keystroke loggers and rootkits for Linux?

Mark

And how is a firewall to help against that?

---

### Post by mbaker824 on 2008-05-26
> **hyper_ch said:**
> And how is a firewall to help against that?

You yourself said:
> Why is a firwall important on Windows? Because there also outgoing traffic needs to be filtered. All that spyware and stuff the gets installed among "legal" software. You don't have this in Linux...

You don't?  Keystroke loggers and rootkits certainly qualify as "spyware and stuff", so it would seem Linux systems need the same kind of protection.

I'm not the only one who thinks so, and to support my argument, here's something from Ed Skoudis in *Counter Hack Reloaded*:
> ...it's very helpful to have a basic knowledge of the Linux and UNIX operating systems **because they are so popular as target platforms and as operating systems from which to launch attacks**.  (emphasis mine)

Linux systems do get compromised, in a wide variety of ways, and I believe using a firewall of some kind is a prudent step toward securing a Linux machine.  

If you don't want to use a firewall on your Linux system, by all means do as you please; but I see little point in continuing this discussion.  Let's agree to disagree and keep trying to help other users as best we can.

Mark

---

### Post by michaelzap on 2008-05-26
I have a question related to the original post...

I recently upgraded from Gutsy to Hardy. In Gutsy I was using Firestarter with no problems, and the same seems to be true now in Hardy. Is there any reason that I should be using ufw instead (and if so, how)?

I'm going to do a fresh Hardy install on a new drive soon just to start over with an encrypted file system, so I also wonder if Firestarter will still be part of my installation in that case.

---

### Post by scorp123 on 2008-05-26
> **mbaker824 said:**
>  Do you believe attacking a listening service is the only mode of attack available?  If it ain't listening, then there is simply nothing that would accept incoming connections, and hence: nothing to attack.

> **mbaker824 said:**
>  Do you believe there are no keystroke loggers and rootkits for Linux?  For most of them you'd already need to be "root" in the first place to install them, e.g. you'd need to exploit a server somehow. As non-root you could only hope to exploit a single user's stupidity by e.g. sending them scripts and programs they don't understand via e-mail and hope they will be daft enough to execute them. Maybe you get lucky and you hit the one account with "sudo" priviledges. But all this talk of rootkits and keyloggers is highly exaggerated. As home user you are highly unlikely to ever run across one of those things.

---

### Post by scorp123 on 2008-05-26
> **mbaker824 said:**
>  Keystroke loggers and rootkits certainly qualify as "spyware and stuff", so it would seem Linux systems need the same kind of protection.  You're mixing apples and oranges here. Firewalls protect against network threats ... if you configure them right. Keyloggers? Root Kits? Different beasts altogether and firewalls don't protect against those.

> **mbaker824 said:**
>  Linux systems do get compromised, in a wide variety of ways, and I believe using a firewall of some kind is a prudent step toward securing a Linux machine.   That guy was clearly talking about **servers** IMHO ... Yes, badly maintained servers where no admin bothered to install any patches for way too long are popular targets. And they are far far more interesting. But again: A firewall is no cure against that. Take a DNS or a Mail server as example: Firewall or no firewall, but you have to let those services through anyway (what's the purpose of a mail server if you block the relevant ports with firewalls???). Chances are that on a badly maintained server where the lazy admin doesn't do a proper job you will encounter old and hackable versions of sendmail (= mail daemon) or bind (= DNS server daemon), and voila: You can be hacked. Firewall or no firewall.

This is extremely different from Windows where you have tons of highly unsafe, stupid and silly network protocols accepting connections from *anywhere* ... But typical Microsoft: Instead of shutting those silly services down or getting rid of them altogether they came up with this joke of "firewall" they ship with since XP .... and now everybody thinks that they absolutely "need" a firewall no matter what.

Trust me, things are very different here. If --different than Windows-- you are not running any network service whatsoever as is the case with Ubuntu "out of the box" you absolutely don't need any firewall whatsoever, for there simply is no protocol, no daemon, no service and no process a wannabe attacker could remotely connect to and hope to exploit.

Servers are a different story again: As soon as you dabble around with stuff such as SSH, Apache, SAMBA and other network services you have to think about these things, e.g. limit the range of IP addresses that may connect to your machine. Yes, that's what a firewall can be used for and where it indeed offers protection, e.g. shutting out those parts of the Internet you don't want to have any business with.

> **mbaker824 said:**
>  If you don't want to use a firewall on your Linux system, by all means do as you please If you know what you do and why you do it, fine. Just don't do things because you are relying on false information that gives you a false sense of safety. See my examples above: Even with a firewall you might still be attackable depending on what you configured. Having a firewall is no guarantee whatsoever. As I said: Know what you do and why you do it and you will be fine ;)

---

### Post by kamaji792 on 2008-05-31
> **michaelzap said:**
> I have a question related to the original post...

I recently upgraded from Gutsy to Hardy. In Gutsy I was using Firestarter with no problems, and the same seems to be true now in Hardy. Is there any reason that I should be using ufw instead (and if so, how)?


The immediate thought is if it ain't broke don't fix it.

**ufw** and **firestarter** so the same job.  They are both front ends for **iptables**.  ufw uses a command line interface where as firestarter uses a GUI (Graphical User Interface like Gnone or KDE).  If you are getting on fine with firestarter then stick with it.  Only play with ufw if you only have a command line interface.

All the best

---

### Post by michaelzap on 2008-05-31
> **kamaji792 said:**
> The immediate thought is if it ain't broke don't fix it.

**ufw** and **firestarter** so the same job.  They are both front ends for **iptables**.  ufw uses a command line interface where as firestarter uses a GUI (Graphical User Interface like Gnone or KDE).  If you are getting on fine with firestarter then stick with it.  Only play with ufw if you only have a command line interface.

All the best

Thanks for the reply. I actually decided to start fresh with a new Hardy installation (mostly because I wanted to encrypt the drive, and this gave me the opportunity to play around with some new software on my old installation without worrying that I might mess anything up). I installed Firestarter again and it (like pretty much everything else) is working perfectly and with no complications.

---

### Post by tebbens on 2008-05-31
> **hyper_ch said:**
> Ok, on a normal home desktop installation, what services are listening that need to be protected by a firwall?
Let me guess: 0

Why is a firwall important on Windows? Because there also outgoing traffic needs to be filtered. All that spyware and stuff the gets installed among "legal" software. You don't have this in Linux...

So, why do you need a firewall?

I always leave the front door to my house wide open...my car also.
I have very little to steal, besides, what are the chances someone
would come snooping around ???

---

### Post by brian_p on 2008-05-31
> **tebbens said:**
> I always leave the front door to my house wide open...my car also.
I have very little to steal, besides, what are the chances someone
would come snooping around ???

The first sentence of post #15 deserves your attention.

---

### Post by scorp123 on 2008-06-01
> **tebbens said:**
> I always leave the front door to my house wide open...my car also. I have very little to steal, besides, what are the chances someone would come snooping around ??? What you describe here: That's Windows! And Microsoft put this miserable little fence in front of the open door and they call it "Firewall".

On Ubuntu there isn't even a door (= no open ports!) "out of the box" in the first place. ;)

---

### Post by tebbens on 2008-06-01
> **scorp123 said:**
> What you describe here: That's Windows! And Microsoft put this miserable little fence in front of the open door and they call it "Firewall".

On Ubuntu there isn't even a door (= no open ports!) "out of the box" in the first place. ;)

I still think a firewall should be setup by default.
Any user (novice or expert) could easily install something
that opens up a port/ports, without knowing or even be notified
that a Firewall is not in place.

Atleast ask during the install...
Do you want the firewall turned on ??

---

### Post by scorp123 on 2008-06-01
> **tebbens said:**
> At least ask during the install...
Do you want the firewall turned on ?? Yes, I'd agree to that.

---

### Post by hyper_ch on 2008-06-01
firewall is always turned on... except if you remove iptables from the kernel (is that possible?)

---

### Post by kevdog on 2008-06-01
Just to clarify some misconceptions that the default stance of the iptables is not DROP!

---

### Post by tebbens on 2008-06-01
> **hyper_ch said:**
> firewall is always turned on... except if you remove iptables from the kernel (is that possible?)

After a new install the Ubuntu firewall is installed, not active or "on".

---

### Post by scorp123 on 2008-06-01
> **hyper_ch said:**
> firewall is always turned on...  Nope, it's not. We have had this discussion before I think. Please type this into a terminal: ```
sudo iptables -L
```  ... You will most likely get this as result: ```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
``` Voila, no active firewall whatsoever.


Or please try this command: ```
sudo lsmod | grep ip
``` ... You will get a result which looks something like this: ```
ipv6                  273892  26 
snd_cmipci             37024  1 
snd_opl3_lib           11520  1 snd_cmipci
snd_mpu401_uart         9600  2 snd_cmipci,snd_mpu401
snd_pcm                80388  4 saa7134_alsa,snd_cmipci,snd_usb_audio,snd_pcm_oss
snd                    54660  17 saa7134_alsa,snd_cmipci,snd_opl3_lib,snd_mpu401,snd_mpu401_uart,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_hwdep,snd_seq,snd_timer,snd_seq_device
gameport               16776  2 snd_cmipci,analog
``` .... No sign whatsoever of a firewall.

On the system I just used the "iptables" command I have two entries which hint at the possibility of activating the firewall: ```
iptable_filter          3968  0 
ip_tables              13924  1 iptable_filter
x_tables               16260  1 ip_tables
``` ... But again, the absence of all other modules tells me that there is no firewall active here!

Now for comparison the output from a system which does have an active firewall:

```
~ > sudo lsmod | grep ip
iptable_nat            16900  0 
nf_nat                 30636  1 iptable_nat
nf_conntrack_ipv4      29456  2 iptable_nat
nf_conntrack           83548  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nfnetlink              15432  3 nf_nat,nf_conntrack_ipv4,nf_conntrack
ip_tables              31080  1 iptable_nat
x_tables               30600  2 iptable_nat,ip_tables
ipv6                  360168  34 
chipreg                11904  2 jedec_probe,cfi_probe 
``` See all those  modules, e.g. for NAT, for IP connection tracking, and so on? Yes, this is an active firewall here.

But this is not what you get "out of the box" and hence your statement is again not correct.

Yes, the basis for activating a firewall (the "infrastructure" if you want to call it so) is there. But it's not activated at all, it does nothing at all and the above shell commandos should be proof enough to show this.


> **hyper_ch said:**
>  except if you remove iptables from the kernel (is that possible?)  Of course you can remove it. Just untick the firewall features when you configure your kernel and that's it. Not hard at all to do. And even if you leave it in: See above. The groundwork for a firewall is there, yes. But "out of the box" it is neither active nor will it do *anything* at all to protect you from unwanted network traffic.

The question in the previous posting is thus valid: A user should be asked if they want to activate the firewall and have all incoming network traffic filtered by default. Because right now it's not doing anything like that.

---

### Post by Monicker on 2008-06-01
> **scorp123 said:**
> ```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
``` Voila, no active firewall whatsoever.




I don't agree with that statement.  Iptables is used to administer the kernel level packet filtering (netfilter).  Iptables and netfilter are obviously active, yet set to a default policy of accepting all traffic.  A firewall is not a firewall just by virtue of being set to block traffic.  If anything I would call it an "unconfigured" firewall, since firewalls start with either a policy of default allow or default deny.  Any additional configuration is up to the person who maintains the firewall.

Change the command to 

```
sudo iptables -L -v
```

..and you will see that the kernel packet filter is still inspecting the network traffic, since it will give you the number of packets for each default chain.  Just because it has not been configured to do more than its default policy does not make it not a firewall.

---

### Post by kevdog on 2008-06-01
Im not sure what the right answer is frankly, however aren't you two splitting hairs?

Whether the iptables is inactive by default, or active but not set to block anything -- in the end -- the result is the same.  In order to take advantage of the built-in firewall, the ruleset must be fed into iptables at every boot (whether through importing a ruleset, or by adding additional rules either manually or through a frontend).  Only then is the firewall truly active.

---

### Post by scorp123 on 2008-06-01
> **Monicker said:**
>  I don't agree with that statement ... Iptables and netfilter are obviously active, yet set to a default policy of accepting all traffic.  OK, let me fine-tune my statement: "active firewall" in the sense that it would filter network traffic and not "active" in the sense of "being present". That's how I used it I think ("active" == "filtering traffic") and in this sense my statements should be correct.

> **Monicker said:**
>  A firewall is not a firewall just by virtue of being set to block traffic. If anything I would call it an "unconfigured" firewall  I agree to that. You see, there already was a lengthy thread where hyper_ch and me disagreed what the difference between "unconfigured" and "default configuration" is when it comes to "iptables". I guess I am on the same page as you: "iptables" is 'out of the box' unconfigured, yes. Here is the thread I am referring to:
[http://ubuntuforums.org/showthread.php?t=640752](http://ubuntuforums.org/showthread.php?t=640752)

> **Monicker said:**
>  since firewalls start with either a policy of default allow or default deny.  Any additional configuration is up to the person who maintains the firewall.  Yes, absolutely.

> **Monicker said:**
>  Just because it has not been configured to do more than its default policy does not make it not a firewall.  Technically you are right, yes. But please see above, when I wrote "active firewall" I meant it in the sense "this firewall is filtering stuff" and not "firewall technology is always present" -- yes, it's present, but from a packet filtering point of view not "active" in the sense that it would keep any traffic away. If anything it's completely "passive" in its default setting.

And this is also what is often misunderstood by newcomers: They're told "Ubuntu is safe out of the box". Yes, this is more or less true if we compare this with e.g. Windows out of the box. And then they are told "You don't need to download a firewall, Linux already has a built-in firewall". This is also true. But here's the catch: Many people connect the two and thus misunderstand the message as being "Ubuntu is safe out of the box because there is a built-in firewall" ... And this is obviously *WRONG*. Ubuntu's safety "out of the box" comes from the fact that per default there are no TCP or UDP ports listening for outside traffic, and not because the firewall would do any magical work in its default setting --- and semantics aside, I think we both agree that the default setting of "iptables" on Ubuntu is not filtering anything (regardless if I call that stuff "active firewall" vs. "passive firewall") and letting all traffic through.

So to get back to the topic I'd say tebben's posting a little bit further up is not such a bad idea: The users should be asked if they want the firewall "active" (= in the sense that it filters traffic) and the installer should then create a default rule set which would e.g. let all outgoing traffic out but block all unwanted incoming traffic. 

Other distros such as OpenSUSE are already doing this for quite some time now. Per default the SUSE installer will activate the firewall and only offer to activate SSH. Here is a screenshot:

[IMG]http://www.novell.com/coolsolutions/img/16249-3.jpg[/IMG]

IMHO this is not such a bad idea at all. Users who know what they are doing can still click on that button to disable the firewall but for the average home user who doesn't want to risk anything such an option would definitely be nice, IMHO.

---

### Post by Monicker on 2008-06-01
> **scorp123 said:**
> 

So to get back to the topic I'd say tebben's posting a little bit further up is not such a bad idea: The users should be asked if they want the firewall "active" (= in the sense that it filters traffic) and the installer should then create a default rule set which would e.g. let all outgoing traffic out but block all unwanted incoming traffic. 

Other distros such as OpenSUSE are already doing this for quite some time now. Per default the SUSE installer will activate the firewall and only offer to activate SSH. Here is a screenshot:

<snip>

IMHO this is not such a bad idea at all. Users who know what they are doing can still click on that button to disable the firewall but for the average home user who doesn't want to risk anything such an option would definitely be nice, IMHO.

Understood.  I agree that most newcomers do not understand when and why they might want to have an active firewall.  Judging from some of the forum posts, many are dabbling with things such as apache, mysql, and other services, which may or may not be exposed directly to the internet.  Even with port forwarding, you should be aware of the security implications of allowing ANY service to be accessed on your machine.  I have seen logs of some compromised web servers, and it can be quite an adventure when someone discovers a shortcoming in your security.  On the other hand, people should not be so scared that they lock things down so tight that they can't communicate at all on the network - which I have also seen in these forums.  :)  I guess its still a matter of finding a good way of educating people about these issues.

I would have no problem with being prompted to activate a firewall during the install.  Redhat Enterprise/Fedora have done that for some time now.

---

### Post by scorp123 on 2008-06-01
> **Monicker said:**
>  Understood.  I agree that most newcomers do not understand when and why they might want to have an active firewall.  Exactly!

> **Monicker said:**
>  Judging from some of the forum posts, many are dabbling with things such as apache, mysql, and other services, which may or may not be exposed directly to the internet.  Even with port forwarding, you should be aware of the security implications of allowing ANY service to be accessed on your machine. Absolutely! In in that light I think it is somewhat dangerous if they believe the misinformation "Don't worry, there is a firewall in the background 'out of the box' and it will protect you" when in fact it doesn't. Yes, there is firewall-technology, it's already there. But you have to configure it and tell it what you want it to do because otherwise it will do nothing whatsoever. But very often I see this mantra "there already is a firewall, so don't worry" repeated all over these forums and IMHO such misinformation needs to be countered. There already is one OS with a miserable track record when it comes to security, we don't need Ubuntu or any other Linux distro to become another copy of that. So IMHO it's important to clearly spread the info what the firewall --as of now-- does 'out of the box' and what it doesn't because there are still too many misunderstandings about this.

> **Monicker said:**
>  I guess its still a matter of finding a good way of educating people about these issues.  Exactly.

> **Monicker said:**
>  I would have no problem with being prompted to activate a firewall during the install.  Redhat Enterprise/Fedora have done that for some time now.  Absolutely! Same with SUSE or OpenSUSE as they are called now. Same with Mandrake / Mandriva as far as I remember. All these distros will offer to activate a default rule-set and if the user doesn't change those options the built-in firewall indeed becomes "active" in every sense and will indeed start to intercept traffic. I therefore wonder why Canonical didn't include this option on their desktop releases too.

---

### Post by kevdog on 2008-06-01
Thats a great idea guys -- why doesn't someone submit for Ibex that the default iptables configuration to reject all ports except for ssh and incoming ping requests.  I would be happy out of the box with this setup.

---

### Post by tebbens on 2008-06-01
> **kevdog said:**
> Thats a great idea guys -- why doesn't someone submit for Ibex that the default iptables configuration to reject all ports except for ssh and incoming ping requests.  I would be happy out of the box with this setup.

I've been using Fedora for some time now, and just installed
Ubuntu 8.04. I was VERY surprised to see the default install
has the Firewall off.

At the VERY least, ask during the install !!!
I would suggest asking something like this...

Would you like the Firewall turned on or off ?

[ ] Turn ON the Firewall
...[ ] Allow SSH
...[ ] Allow PING

[ ] Turn OFF the Firewall

Include a small explanation/warning of what each does.

Matthew

---

### Post by hyper_ch on 2008-06-02
> **kevdog said:**
> Thats a great idea guys -- why doesn't someone submit for Ibex that the default iptables configuration to reject all ports except for ssh and incoming ping requests.  I would be happy out of the box with this setup.

Why? Most people are behind a router anyway nowadays. So no direct connection to the net. Hence you rather configure the firewall at the router and not on your lan.

---

### Post by brian_p on 2008-06-02
> **scorp123 said:**
>  Absolutely! In in that light I think it is somewhat dangerous if they believe the misinformation "Don't worry, there is a firewall in the background 'out of the box' and it will protect you" when in fact it doesn't. Yes, there is firewall-technology, it's already there. But you have to configure it and tell it what you want it to do because otherwise it will do nothing whatsoever. But very often I see this mantra "there already is a firewall, so don't worry" repeated all over these forums and IMHO such misinformation needs to be countered.

How about the misinformation that a single Ubuntu box needs a firewall, either in its default state or running a few services?

> There already is one OS with a miserable track record when it comes to security, we don't need Ubuntu or any other Linux distro to become another copy of that. So IMHO it's important to clearly spread the info what the firewall --as of now-- does 'out of the box' and what it doesn't because there are still too many misunderstandings about this.

Controlling what services are running on Windows is far from an easy task so a firewall is probably a necessity. It saves having to think and gets round deficiencies in the design of the OS. Discovering what runs on Linux is easy and installed services have sane defaults. Why copy the Windows model?

---

### Post by brian_p on 2008-06-02
> **tebbens said:**
> I've been using Fedora for some time now, and just installed
Ubuntu 8.04. I was VERY surprised to see the default install
has the Firewall off.

Is there something unsafe about the default install? If not, why be surprised?

> At the VERY least, ask during the install !!!
I would suggest asking something like this...

Would you like the Firewall turned on or off ?

[ ] Turn ON the Firewall
...[ ] Allow SSH
...[ ] Allow PING

[ ] Turn OFF the Firewall

At least you do not regard ssh or ping as unsafe services to run. That's good.

> Include a small explanation/warning of what each does.

Would this do?

Turn OFF the Firewall: By default no services are running. No connections can be made to your machine. It is completely secure.

Turn ON the Firewall: No connections can be made to the non-existent services. Your machine is now doubly completely secure.

---

### Post by hyper_ch on 2008-06-02
the firewall on windows has also another effect that is not (yet) in existance on a linux box.

In windows if you install software, mainly from "shady" sources or also commercial software then you are likely to install malware, adware, spyware, ... that data is then being transmitted back to the creators. So, a firewall on windows not only has the job to inspect incoming traffic but also a large extend to inspect outgoing traffic.

This is not the case (yet) on linux.

---

### Post by scorp123 on 2008-06-02
> **hyper_ch said:**
> Why? Most people are behind a router anyway nowadays. So no direct connection to the net. Hence you rather configure the firewall at the router and not on your lan. That depends on the country I guess. There are many many countries and places out there where people are still on dial-up or where the modems are still connected directly to the PC and where the modem is really just that: a modem, e.g. no routing and no firewall capability whatsoever. So for such people offering an option to have a default firewall ruleset would be a nice idea I guess.

---

### Post by scorp123 on 2008-06-02
> **brian_p said:**
>  How about the misinformation that a single Ubuntu box needs a firewall, either in its default state or running a few services?  I never said that. Ultimately it's up to the user to know if they need a firewall or not. But from the "newbie point of view" it probably wouldn't be such a bad idea. As I wrote above, if the system asks you "Turn on a firewall?" or if the installer presented an option as SUSE's installer does you can still turn it off if you think you don't need a firewall, either because you know what you do or because your router already does all the firewall work for you.

> **brian_p said:**
>  Controlling what services are running on Windows is far from an easy task so a firewall is probably a necessity. It saves having to think and gets round deficiencies in the design of the OS.  Absolutely.

> **brian_p said:**
>  Discovering what runs on Linux is easy and installed services have sane defaults.  Yes, if you know how and if you know what you do. But honestly, browsing throught these forums I can also see too many newbies tinkering with things such as Apache, PHP, MySQL and so on. Of course they have every right in the Universe to tinker with these things, but in that light I think that the default setting of Ubuntu's firewall (= everything is let through and nothing is blocked) isn't such a good move. Because the misinformation "There is already a firewall, you are safe" got stuck in so many places and in so many heads (I don't mean this as an insult or as an accusation!) I fear that whenever something bad happens they will blame it on Ubuntu, Linux and the "not working firewall" ... Which of course would work perfectly, if only they had taken care to configure it.

> **brian_p said:**
>  Why copy the Windows model?  In my opinion we are getting more and more ex-Windows users who are used to this "modus operandi", e.g. they hear that there is a firewall in Linux and thus they presume automatically that it is active (= in the sense: filtering unwanted traffic) and "protecting them". You can't re-educate millions of people, but you could indeed change the firewall's behaviour so that it would indeed protect people. At least on the Ubuntu "Desktop" releases. On the server releases however the firewall IMHO should remain off as it is now.

---

### Post by scorp123 on 2008-06-02
> **hyper_ch said:**
>  In windows if you install software, mainly from "shady" sources or also commercial software then you are likely to install malware, adware, spyware, ... that data is then being transmitted back to the creators. So, a firewall on windows not only has the job to inspect incoming traffic but also a large extend to inspect outgoing traffic.

This is not the case (yet) on linux. I agree 100% here. But I wonder if we aren't steering into this direction as well ... ? Stuff like "Automatix" gets used a lot (despite the warnings not to use it), and people often tend to add third-party repos .... So the scene for "shady sources" is already set, IMHO.

---

### Post by HunterThomson on 2008-06-02
> **hyper_ch said:**
> then I wouldn't bother installing either oen ;)

What is your IP address? You seem to be vary sure of your security:)

---

### Post by scorp123 on 2008-06-02
> **HunterThomson said:**
> What is your IP address? You seem to be vary sure of your security:) If he isn't running any services and if he is using a router with firewall functionality as he suggested in his other posting then he indeed has nothing to fear (At least not from anyone here I guess? :) ) and he therefore really doesn't need to run a firewall on his Ubuntu installation. ;)

---

### Post by HunterThomson on 2008-06-02
> **scorp123 said:**
> If he isn't running any services and if he is using a router with firewall functionality as he suggested in his other posting then he indeed has nothing to fear (At least not from anyone here I guess? :) ) and he therefore really doesn't need to run a firewall on his Ubuntu installation. ;)

Well I'll tell him if he is running any services:) In any case he just seem to tell everyone not to use a firewall. This is not really a good idea. He doesn't even now if there computer is a laptop or not  half the time. He also doesn't know if the person knows how to set up a firewall on there router properly and if there asking about firestater they probaly don't. If it is not set up well then having a soft firewall on there computer is not a bad idea.

---

### Post by scorp123 on 2008-06-02
> **HunterThomson said:**
>  Well I'll tell him if he is running any services :)  And what if he setup a honeypot? ;)

> **HunterThomson said:**
>  He doesn't even now if there computer is a laptop or not  half the time. I don't use a firewall on my laptop. Only services listening are SSH (port 22) and CUPS (631). "denyhosts" takes care of clowns trying to login on my laptop when I am on the road. E-Mail traffic is always encrypted ... but then again no firewall would protect you if you are daft enough to use unencrypted POP3 or IMAP transmissions on a public WiFi network. So I don't see hyper's suggestions as being that 'bad'. And let's admit it: From a purely technical point of view his statements are true: if you are not running any services whatsoever then there is no point in running a firewall.

It's just that IMHO as soon as someone installs a service --be that SSH, MySQL, Apache, whatever-- this equation changes and a firewall then would indeed be useful for the average user.

> **HunterThomson said:**
>  He also doesn't know if the person knows how to set up a firewall on there router properly and if there asking about firestater they probaly don't.  Hmmm, maybe.

> **HunterThomson said:**
>  If it is not set up well then having a soft firewall on there computer is not a bad idea.  Well, a soft firewall on your own computer won't help one little bit if you lack any basic understanding of how and what a firewall is supposed to do ;)

In that regard I'd still say it would be a good idea if the Ubuntu installer asked the user if he wants a firewall or not. Other distros do that too and I don't see why this should be wrong. Users who don't want or don't need a firewall can still answer "No" (I do just the same when I myself configure a SUSE box ...)

---

### Post by brian_p on 2008-06-02
> **hyper_ch said:**
> the firewall on windows has also another effect that is not (yet) in existance on a linux box.

In windows if you install software, mainly from "shady" sources or also commercial software then you are likely to install malware, adware, spyware, ... that data is then being transmitted back to the creators. So, a firewall on windows not only has the job to inspect incoming traffic but also ona large extend to inspect outgoing traffic.

This is not the case (yet) on linux.

Convincing a Windows user with a router that a firewall is not required for incoming traffic is very fraught. For outgoing packets you may as well not even try! Attempting to explore the fundamental reasons why a firewall is necessary is not seen as helpful because indoctrination for that OS is continual, extensive and successful. If we ever get to that point with Linux it would be a shame.

---

### Post by scorp123 on 2008-06-02
> **brian_p said:**
>  ... If we ever get to that point with Linux it would be a shame. Yes, I can see your point. Really. But please see my posting #40 above. Quoting myself here: > ... But honestly, browsing throught these forums I can also see too many newbies tinkering with things such as Apache, PHP, MySQL and so on .... I fear that whenever something bad happens they will blame it on Ubuntu, Linux and the "not working firewall" ... Which of course would work perfectly, if only they had taken care to configure it. See what I mean? Now, wouldn't this too be a shame if Ubuntu (or Linux in general) somehow received a bad reputation of having a "not working firewall" (which is BS of course)? So having an option in Ubuntu's installer to activate a default firewall ruleset (or leave it inactive) would IMHO help to get this issue solved before it even becomes one. Users who 'feel naked' without a firewall can turn it on; users who know that they don't need one can leave it off and get the current behaviour.

---

### Post by hyper_ch on 2008-06-02
It would be a shame to "enable" it upon installation because most people changing from Windows to Linux will "enable" it just because they are used to being required to have one on Windows.

It's much better to educate them that there are cases in which they don't need to alter anything.

---

### Post by scorp123 on 2008-06-02
> **hyper_ch said:**
>  It would be a shame to "enable" it upon installation because most people changing from Windows to Linux will "enable" it just because they are used to being required to have one on Windows.  Yes, I know.

> **hyper_ch said:**
>  It's much better to educate them that there are cases in which they don't need to alter anything.  ... long way to go then ... :)

---

### Post by hyper_ch on 2008-06-02
If you treat them like stupids they will remain stupid/ignorant ;)

&#8220;Give a man a fish; you have fed him for today.  Teach a man to fish; and you have fed him for a lifetime&#8221;

---

### Post by Monicker on 2008-06-02
> **brian_p said:**
> 
Turn OFF the Firewall: By default no services are running. No connections can be made to your machine. It is completely secure.

Turn ON the Firewall: No connections can be made to the non-existent services. Your machine is now doubly completely secure.

I understand where you are coming from with those remarks.  However, what about later when the user decides to actually open up and port forward services, when they don't understand how to secure those same services?  How long will a default secure configuration actually stay that way?

There was a thread in "Server Platforms", I believe, where someone had their mysql server accessible to the entire internet, and then were surprised to find that somebody was trying to brute force the mysql root account.

How do we educate people to be more aware of securing any services they decide to open up?  Even if they do have an active firewall running, they will most likely just punch a hole in it when they discover it is blocking a service they opened up.

In a sense some of this arguing about using or not using a firewall seems pointless if people are not informed about the risks of what they might decide to do.  An active firewall can be just as insecure as none at all once people start adjusting it.  Most of them, whether they are linux or windows users, have no idea about securing open services on their machine.

---

### Post by brian_p on 2008-06-02
> **scorp123 said:**
> Yes, I can see your point. Really. But please see my posting #40 above.

I was just about to reply to that post. Hopefully I can do it justice here.

> 
 Quoting myself here:[quote]

... But honestly, browsing throught these forums I can also see too many newbies tinkering with things such as Apache, PHP, MySQL and so on .... I fear that whenever something bad happens they will blame it on Ubuntu, Linux and the "not working firewall" ... Which of course would work perfectly, if only they had taken care to configure it.




[/quote]
> 
  See what I mean? Now, wouldn't this too be a shame if Ubuntu (or Linux in general) somehow received a bad reputation of having a "not working firewall" (which is BS of course)? So having an option in Ubuntu's installer to activate a default firewall ruleset (or leave it inactive) would IMHO help to get this issue solved before it even becomes one. Users who 'feel naked' without a firewall can turn it on; users who know that they don't need one can leave it off and get the current behaviour.

Your point about what could be perceived as a non-working firewall is a reasonable one. Individual reactions would depend to some extent on expectations and on understanding what a firewall does and under what circumstances it becomes useful. As for adverse comment against Ubuntu I'd much prefer to see a robust promotion of its strengths rather than provide a palliative. Emphasise that services are installed with safe defaults which are under constant review. Point to config files/documentation which must be read. Explain the importance of regular upgrades to software.

My initial reaction to a SUSE type installer question about installing a firewall is that many will say 'yes' because they know it is a good thing or it can't do any harm. They'll do it even if they do not intend to run any services. I've seen advice similar to this given in these forums.

My second reaction is that running a service is good and nowhere near the level of dangerous activity it is sometimes made out to be. Proviso: newbie territory is being left behind and there is a lot of essential reading to be done. I cannot see what a firewall (installed with a default ruleset or not) has to contribute. For a network of machines, perhaps. For a single machine, no.

A third thought is the default ruleset. I assume it would reject all attempted connections? Then alter a rule or two to allow services to operate? That doesn't seem safer than what we have at present and it offends my sense of elegence.

---

### Post by hyper_ch on 2008-06-02
> **Monicker said:**
> I understand where you are coming from with those remarks.  However, what about later when the user decides to actually open up and port forward services, when they don't understand how to secure those same services?  How long will a default secure configuration actually stay that way?
Well, if they decide later on to, hmmm let's say install apache, then they will sort of use default configuration. In that case they will open port 80 and probably leave it plain open with no advanced rules and stuff...

So, I wonder where is the difference then to have no filtering in iptables compared to a plain open port 80?

I mean you don't install services and then let nobody connect to them, right?

> **Monicker said:**
> There was a thread in "Server Platforms", I believe, where someone had their mysql server accessible to the entire internet, and then were surprised to find that somebody was trying to brute force the mysql root account.
Mysql might be an exception as you can limit it to local use only, however for most services you want to connect to from other places... hence firewall will need to be open for that... either in general or then just to specific IPs (which can lead to that you don't have access at some other time because you are not on an authorized IP...)

> **Monicker said:**
> In a sense some of this arguing about using or not using a firewall seems pointless if people are not informed about the risks of what they might decide to do.  An active firewall can be just as insecure as none at all once people start adjusting it.  Most of them, whether they are linux or windows users, have no idea about securing open services on their machine.
That's true and that's where you need to educate/inform them... so far people want to install a firewall because it is a "must" on windows. They have an idea of what a firewall is (on windows) but they don't have one on linux. So tell them pro and cons... where security issues are and then let them decide.

---

### Post by brian_p on 2008-06-02
> **Monicker said:**
> I understand where you are coming from with those remarks.  However, what about later when the user decides to actually open up and port forward services, when they don't understand how to secure those same services?  How long will a default secure configuration actually stay that way?

There was a thread in "Server Platforms", I believe, where someone had their mysql server accessible to the entire internet, and then were surprised to find that somebody was trying to brute force the mysql root account.

How do we educate people to be more aware of securing any services they decide to open up?  Even if they do have an active firewall running, they will most likely just punch a hole in it when they discover it is blocking a service they opened up.

In a sense some of this arguing about using or not using a firewall seems pointless if people are not informed about the risks of what they might decide to do.  An active firewall can be just as insecure as none at all once people start adjusting it.  Most of them, whether they are linux or windows users, have no idea about securing open services on their machine.

You state the problem succinctly. A lot depends on the quality of the documentation and its layout. I'm not suggesting it is incomplete but often there are things one is searching for which take some finding. Confining a service to the local net is sometimes obvious from what is in the configuration file, sometimes it is not. Resorting to a search engine is something I've had to do quite a few times.

The fact is you are not doing newbie things when configuring a service and if anything it is surprising how mistakes can be made without incurring expensive repercussions. Most services are complex and become more so when attempting something which is not run of the mill, so a user has to have a good idea of where she is going and how to get there before setting out.

README.Debian is sometimes a good source of information; sometimes not; a lot depends on the who is doing the packaging. There are times when I think more could be done there but there is, of course, the opportunity to file bug reports offering patches for the documentation.

---

### Post by tebbens on 2008-06-02
What exactly is the problem with asking during the install ?

If you don't ask during the install then you have people installing services without any notification that the Firewall is OFF.

After a service is installed I don't see any pop-ups in Ubuntu that say..
You now started opening up ports, you might want to consider turning ON the Firewall.

---

### Post by hyper_ch on 2008-06-02
if you enable the firewall upon installation and install a service and you ask here why it doesn't work and that linux is stupid and that you're going back to windoze.

---

### Post by tebbens on 2008-06-02
> **hyper_ch said:**
> if you enable the firewall upon installation and install a service and you ask here why it doesn't work and that linux is stupid and that you're going back to windoze.

Better safe upfront then sorry later.
I'd rather see questions like that then an insecure server.

Besides, my question was....
What exactly is the problem with ASKING during the install ???

---

### Post by scorp123 on 2008-06-02
> **tebbens said:**
>  What exactly is the problem with ASKING during the install ??? I am curious too :)  All other distros seem to do that as well (for years in the case of SUSE) and last time I checked this didn't water down their "Linuxness" so far ;)

---

### Post by HunterThomson on 2008-06-03
OK OK......#-o

I Spent far too much time on window$.....

I am use to installing a program like windows media player or playing a Sony RootKit CD that sent off data to whoever... or programs or MP3's with spyware  trying to send off info to whoever. ZeroDay exploits everyday. A load of services open form the first time I turn on the computer.... So, ya I guess there is a good chance you don't need a firewall. I am still full of window$ paranoia. Excuses my ignorance. I was wrong and I have a lot to learn.#-o

---

### Post by brian_p on 2008-06-03
> **tebbens said:**
> Better safe upfront then sorry later.
I'd rather see questions like that then an insecure server.

All installed services are safe in their default states so you won't see an insecure server. That makes the question redundant.

> Besides, my question was....
What exactly is the problem with ASKING during the install ???

It serves no purpose.

---

### Post by hyper_ch on 2008-06-03
> **brian_p said:**
> It serves no purpose.

In fact, according to the help requests here, it creates more problems than it solves.

---

### Post by brian_p on 2008-06-03
> **scorp123 said:**
> I am curious too :)  All other distros seem to do that as well (for years in the case of SUSE) and last time I checked this didn't water down their "Linuxness" so far ;)

The rationale behind why a distribution does this is not readily found from a quick search. In Ubuntu's case the default install has no services so a firewall has no purpose. One could guess that asking a question about installing one would be unnecessary and merely burden a newcomer with something they do not need. Those who have a hankering after such things can always play with iptables later.

---

### Post by HunterThomson on 2008-06-03
So what should I worried about? I mean Ubuntu is not bullet proof... Right? How could my desktop become compermized?

---

### Post by scorp123 on 2008-06-03
> **HunterThomson said:**
> compermized? "compromised" you mean ;)

There are various ways but as home user you are rather unlikely to encounter them. Different story if you run servers that are accessible 24x7 from the Internet ...

But as home user ... don't ever run commands as "root" (e.g. via "sudo") unless you really really really have to, make sure you keep your system updated, make sure you only install stuff from the official repos (no downloading of *.deb or *.tar.gz from any dubious sites ... those packages there might be manipulated ... and then you're not any better off than on Windows!), make sure you *think* before installing network services and related packages such as Apache, MySQL, and so on .... And you should be pretty much safe.

I say "should" ... There never ever can be a 100% guarantee. It's a fact of life. :)

---

### Post by stmurray on 2008-06-03
I keep reading in posts that Ubuntu does not have any services open, any ports open, etc.  On my installation, Hardy has at least 2 open UDP ports-- avahi and dhclient3:

udp        0      0 0.0.0.0:68            0.0.0.0:*                           4484/dhclient3  
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           5905/avahi-daemon:

I believe Avahi is installed by default and if you use dhcp, dhclient 3 must be enabled.  So, to say that a default installation of Ubuntu has no services or open ports is not really true.

 (If I am mistaken, can someone straighten me out?)


Therefore, even though I am behind a firewall, I run firestarter on my PC, because the benefits (more protection) outweigh the drawbacks (a little processing overhead, installation and configuration time, etc).

---

### Post by scorp123 on 2008-06-03
> **stmurray said:**
>  So, to say that a default installation of Ubuntu has no services or open ports is not really true. Good point :)

Also, if you have a printer, chances are you got CUPS and thus port 631 open too.

---

### Post by tebbens on 2008-06-04
> **brian_p said:**
> All installed services are safe in their default states so you won't see an insecure server. That makes the question redundant.

It serves no purpose.

It does serve a purpose !
It allows the installer to decide upfront if they want a firewall. One of the most important features of the system.

If security is soo good on Ubuntu why is there not even a notification during the os install and install of any services that the "Firewall is OFF, you may want to turn it on !".

---

### Post by hyper_ch on 2008-06-04
> **tebbens said:**
> One of the most important features of the system.
I don't think it's one of the most important features of the system. What makes you think so?

> **tebbens said:**
> If security is soo good on Ubuntu why is there not even a notification during the os install and install of any services that the "Firewall is OFF, you may want to turn it on !".
Because security is so good that it's not needed ;)

---

### Post by brian_p on 2008-06-04
> **stmurray said:**
> I believe Avahi is installed by default and if you use dhcp, dhclient 3 must be enabled.  So, to say that a default installation of Ubuntu has no services or open ports is not really true.

 (If I am mistaken, can someone straighten me out?)

You're not mistaken. The dhcp client has always been around but it would seem avahi (zeroconf) is a relatively recent introduction to a default install because it is an 'exciting technology'.

dhcpclient is probably listening for a response to a request and, being a mature application, should be secure. You'll have to judge for yourself whether avahi is of any concern. I don't use it and have never bothered to read about it until your post, for which I must thank you because it provided me with an incentive to improve my knowledge. Extensive discussion is on the ubuntu-devel mailing list. Two links which may be of interest:

[http://0pointer.de/blog/projects/zeroconf-ubuntu](http://0pointer.de/blog/projects/zeroconf-ubuntu)

[https://lists.ubuntu.com/archives/ubuntu-devel/2006-July/019680.html](https://lists.ubuntu.com/archives/ubuntu-devel/2006-July/019680.html)

> Therefore, even though I am behind a firewall, I run firestarter on my PC, because the benefits (more protection) outweigh the drawbacks (a little processing overhead, installation and configuration time, etc).

It doesn't take more than a few seconds to remove and purge avahi.

---

### Post by brian_p on 2008-06-04
> **scorp123 said:**
> Also, if you have a printer, chances are you got CUPS and thus port 631 open too.

I think it only listens to localhost.

---

### Post by kevdog on 2008-06-04
The whole point of this firewall argument is pointless.  Obviously its not needed out of the box since there are no listening processes.  However, I would also think it is foolish to not expect the end user not to install at least one listening server on the computer, ie ssh, ftp, http, etc.  Maybe a good idea would be to start a poll somewhere to actually discern this information, however I would bet at least more users than not have at least one listening process.

I would also hedge that most users with these listening processes have done nothing to harden the default installation.  I ran an ssh server for years before actually realizing its probably not a good idea to run a service wide open on port 22 (luckily I had disabled passwords).  I only started becoming nervous after one day learning what the system logs were, looking at them, and then seeing the thousands of hits there were attempting to gain access to port 22.  

I think a firewall is one potential solution however not the only viable solution.  I wouldn't mind if the firewall were activated by default, however I would say at the minimum during installation, that at least the user be informed that the firewall is not turned on and not active by default.  It could then refer the user to a reference page about how to enable and configure iptables whether manually or through a third part program such as Firestarter, Guarddog, etc. (Heck most users think Firestarter is the firewall -- iptables what are those??  Even one user asked if he could use something else than iptables because he didn't like that -- Obviously a lot of misconceptions floating around).  Id like to see specific tutorials explicitly summarizing how one can harden their default ssh installation and http installations.  I see a lot of ideas discussed, and I would really like to see an exhaustive list.  Most threads start out general, however quickly focus on one method, based on one particular poster's opinion.  It would be nice to see a short explanation of all possible methods.  

My 2 cents.

---

### Post by tebbens on 2008-06-04
> **kevdog said:**
> The whole point of this firewall argument is pointless.  Obviously its not needed out of the box since there are no listening processes.  However, I would also think it is foolish to not expect the end user not to install at least one listening server on the computer, ie ssh, ftp, http, etc.  Maybe a good idea would be to start a poll somewhere to actually discern this information, however I would bet at least more users than not have at least one listening process.

Starting a Poll sounds good, does anyone here have permissions to start it ?
I would suggest asking 2 questions...

1. Were you aware that Ubuntu is installed with the Firewall OFF?
2. After installing Ubuntu have you installed any services like SSH, FTP, HTTP, ...etc ?

---

### Post by brian_p on 2008-06-04
> **kevdog said:**
> The whole point of this firewall argument is pointless.  Obviously its not needed out of the box since there are no listening processes.

Post #65?

>  However, I would also think it is foolish to not expect the end user not to install at least one listening server on the computer, ie ssh, ftp, http, etc.  Maybe a good idea would be to start a poll somewhere to actually discern this information, however I would bet at least more users than not have at least one listening process.

If they have installed a server it is doing what it is designed to do - listen and serve. A firewall is unlikely to make doing this job more efficient or safe.

> I would also hedge that most users with these listening processes have done nothing to harden the default installation.  I ran an ssh server for years before actually realizing its probably not a good idea to run a service wide open on port 22 (luckily I had disabled passwords).  I only started becoming nervous after one day learning what the system logs were, looking at them, and then seeing the thousands of hits there were attempting to gain access to port 22.

452 attempted connections in May here. My sshd rejected them and gave a little smile each time it did so. It knows that they arise from automated scripts which have zero chance of coming up with a username/password combination which it recognises. I bet yours would have a quiet snigger to itself as well.

> I think a firewall is one potential solution however not the only viable solution.

My machines operate quite happily without a firewall. So, as you say, using one is not the only viable solution.

---

### Post by hyper_ch on 2008-06-04
What is more "dangerous":

Running "no" firewall and knowing yourself what runs on your server/computer

or

Running "a" firewall but have no clue what it does and how it affects services?

---

### Post by kevdog on 2008-06-04
> **hyper_ch said:**
> What is more "dangerous":

Running "no" firewall and knowing yourself what runs on your server/computer

or

Running "a" firewall but have no clue what it does and how it affects services?

Hmmm, I not getting in a flameware, but lets look at the corollary here:


"Which is more "secure":
Running a firewall AND knowing what runs on your server/computer?

Seems to me, that if you install a listening process/server, you know what runs on your server. However I'm curious to know how many people understand the implications of this?  Just knowing that something is running on your computer is menial, to understand the implications of running the server (both pros/cons) is really the question that needs to be answered.  I'm fairly certain that alerting users that no firewall is active during the default install is not impositional or over-reaching.  Just really an FYI -- since you must admit many users are unclear about this topic.  Just as in Fedora, I think that running a firewall out of the box is a good idea (just so everyone understands my position), however I'm willing to compromise and state that informing users about the status of the firewall at the time of installation is probably reasonable.

---

### Post by tebbens on 2008-06-04
> **brian_p said:**
> Post #65?



If they have installed a server it is doing what it is designed to do - listen and serve. A firewall is unlikely to make doing this job more efficient or safe.



452 attempted connections in May here. My sshd rejected them and gave a little smile each time it did so. It knows that they arise from automated scripts which have zero chance of coming up with a username/password combination which it recognises. I bet yours would have a quiet snigger to itself as well.



My machines operate quite happily without a firewall. So, as you say, using one is not the only viable solution.

This means nothing because you know how to harden and keep secure the services you operate.
Most people do not, and are not notified by Ubuntu during the os install or service install that
the Firewall is OFF.

---

### Post by kevdog on 2008-06-04
Ok, rather than throwing darts back and forth, I made and submitted part #1 of the poll questions and suggested above:

[http://ubuntuforums.org/showthread.php?t=818300](http://ubuntuforums.org/showthread.php?t=818300)

I posted the poll in the Community Cafe because I couldn't think of a better place for it.  I thought many of the users that read the Security subforum would be experienced and hence would bias the results.  Polls in the beginner section tend to get buried quickly.  If someone thinks it should be moved to a different subforum, let me know and I will ask a moderator (LaRoza :) ) to move it for me.

---

### Post by scorp123 on 2008-06-04
> **brian_p said:**
> I think it only listens to localhost. If I check on my system e.g. by doing "sudo lsof -n -i -P" I get this:
```
cupsd      5540  root    3u  IPv4 1923683       TCP 127.0.0.1:631 (LISTEN)
cupsd      5540  root    5u  IPv4 1923686       UDP *:631
``` ... so yes, the TCP part is listening only to "localhost" (127.0.0.1), but the UDP part seems to indicate that it's listening on any interface (guessing from the "*:631" part above).

As for the discussion per se ... In all honesty, I can fully understand the argument why a firewall in Ubuntu's default setting isn't needed. But IMHO it wouldn't harm to simply ask the user if he wants one ... all other distros do that too and I don't think it would do too much harm. Users answering "No, I don't need a firewall" will simply get the current behaviour. Voila, and both sides of the argument can have it their way.

Just a suggestion.

---

### Post by tebbens on 2008-06-04
> **kevdog said:**
> Ok, rather than throwing darts back and forth, I made and submitted part #1 of the poll questions and suggested above:

[http://ubuntuforums.org/showthread.php?t=818300](http://ubuntuforums.org/showthread.php?t=818300)

I posted the poll in the Community Cafe because I couldn't think of a better place for it.  I thought many of the users that read the Security subforum would be experienced and hence would bias the results.  Polls in the beginner section tend to get buried quickly.  If someone thinks it should be moved to a different subforum, let me know and I will ask a moderator (LaRoza :) ) to move it for me.

VERY interesting to read the first few posts !
Wouldn't you say Brian_p ??

---

### Post by scorp123 on 2008-06-04
> **brian_p said:**
>  452 attempted connections in May here. My sshd rejected them and gave a little smile each time it did so. It knows that they arise from automated scripts which have zero chance of coming up with a username/password combination which it recognises. I bet yours would have a quiet snigger to itself as well. This only works so well for as long as there is no remote exploit that all of a sudden goes into the open .... And please let's not use the argument "... But what are the chances ...?": the recent "SSL hickup" was undetected for like two years, and had some black hats looked close enough they might have found that they have a high chance of guessing the right keys. So yes, this time nothing happened. But there is no 100% safety. And who knows what could happen the next time such a "hickup" in SSL or SSH related packages is found?

Also ... I notice a certain "arrogance" (please: nobody take this as an insult!) amongst us Linux and UNIX folks. Just because we don't use virus-infested Microsoft OS's anymore doesn't mean we are 100% safe from everything. The elderly amongst us maybe still remember things like **"The Morris Worm"** ... ?  If you don't know what this is you may want to look it up in Wikipedia:

[http://en.wikipedia.org/wiki/Morris_worm](http://en.wikipedia.org/wiki/Morris_worm)

**Yes, it's a virus. Yes, it's a worm.** **[COLOR="Red"]FOR UNIX[/COLOR]** ... It probably would not work anymore on current systems ... But still. Does it really take another "Morris Worm" or something similar until we reconsider our "don't worry we are safe, we don't need firewalls" stance again?

I am sure that back in the day people would not have expected that something such as the "Morris Worm" would be possible and that it would be able to kill so many different UNIX systems. That's why it is called "surprising news".

What if yet another "intellectual experiment" somehow found its way into the wild and then wreaked havoc ... ? I am 100% sure that nobody right now expects such a thing to happen. But that's exactly the point :)

So yes, right now we are "safe". Right now we can leave our SSH servers out in the open. Right now we don't have to worry if some script kiddie tries to attack our port 22 again and again. Right now ... 

But because unexpected things always happen, wouldn't it be wise to add a layer of defense "just to be safe"?  Or at least give the user the choice if he "out of the box" wants such a layer or not (as is the current behaviour)?

Just my 0.02&#8364;  ;)

---

### Post by kevdog on 2008-06-04
Shameless plug here -- but I didnt write the software only the tutorial.  In my opinion, if you want one of the slickest way to dynamically modify your server's firewall (without actually making any modification at the server), check out the port knocker utility:
[http://ubuntuforums.org/showthread.php?t=812573](http://ubuntuforums.org/showthread.php?t=812573)

Although its not practical for everyone, you have to admit it ranks really high on the "cool" factor. :)

---

### Post by brian_p on 2008-06-04
> **tebbens said:**
> This means nothing because you know how to harden and keep secure the services you operate.
Most people do not, and are not notified by Ubuntu during the os install or service install that
the Firewall is OFF.

I don't need to know anything and neither does anyone else. By default all installed services are safe.

I have said this before; if you do not accept it, say why.

---

### Post by brian_p on 2008-06-04
> **tebbens said:**
> VERY interesting to read the first few posts !
Wouldn't you say Brian_p ??

We probably find them interesting for different reasons.

Incidentally: you have never said what this default firewall would look like. Care to give a brief outline?

---

### Post by brian_p on 2008-06-04
> **scorp123 said:**
> yes, the TCP part is listening only to "localhost" (127.0.0.1), but the UDP part seems to indicate that it's listening on any interface (guessing from the "*:631" part above).

I'll have to do a bit of hand waving here because I'm not too familiar with the internals of cups! The udp port has something to do with the way cups advertises and gathers information about printers. Ubuntu has all of that set to 'no'.

> As for the discussion per se ... In all honesty, I can fully understand the argument why a firewall in Ubuntu's default setting isn't needed. But IMHO it wouldn't harm to simply ask the user if he wants one ... all other distros do that too and I don't think it would do too much harm. Users answering "No, I don't need a firewall" will simply get the current behaviour. Voila, and both sides of the argument can have it their way.

Just a suggestion.

Looks good. A decent compromise. But . . . .

A user installs Ubuntu and is really happy with it. It just works. That makes the Ubuntu people also very happy because 'just works' is what they strive for.

In the next version of the OS we have our proposed question about a firewall. Many say 'yes, give me one'. Nobody here has said what the default iptables rule would be so let's have all ports, tcp and udp, blocked. We'll forget about what that might do for avahi and dns.

The user now installs chrony or mtr. Both use udp ports. Possibly at random, I'm unsure. Neither 'just work'. Result: unhappy user and unhappy developers.

---

### Post by brian_p on 2008-06-04
> **scorp123 said:**
> This only works so well for as long as there is no remote exploit that all of a sudden goes into the open .... And please let's not use the argument "... But what are the chances ...?": the recent "SSL hickup" was undetected for like two years, and had some black hats looked close enough they might have found that they have a high chance of guessing the right keys. So yes, this time nothing happened. But there is no 100% safety. And who knows what could happen the next time such a "hickup" in SSL or SSH related packages is found?

I agree. The run of the mill script kiddie is no danger but if one or more had latched on to the SSL vulnerability it would have far more than a hiccup. However, we could conjecture quite well what would have happened.

Systems would have been breached and possibly ransacked. How long before anyone noticed it? 10 break ins? 20 break ins? Even with my unimportant network email would tell me someone had logged in. Alarm bells! People far more savvy than me would have informed Debian.

The response would have been massive. Within hours servers would have fixed packages. Within a day most users would have installed them. Phew! That was a close one. You would have been ok because these scripts would still have taken some to probe you even with the much reduced key space and they hadn't latched on to you anyway. (Sorry. I couldn't resist the statistical argument. I think it has some merit here).

Casualties? 100? 200?. Unaffected: 100,000,000.

> Also ... I notice a certain "arrogance" (please: nobody take this as an insult!) amongst us Linux and UNIX folks. Just because we don't use virus-infested Microsoft OS's anymore doesn't mean we are 100% safe from everything.

No, we are not 100% safe but a touch of arrogance is not out of place. Complacency and misinformation is the enemy.

> The elderly amongst us maybe still remember things like **"The Morris Worm"** ... ? 

I'm familiar with the Morris worm. Less of the 'elderly', please. A firewall would have been useless against it because it attacked a service. 

> But because unexpected things always happen, wouldn't it be wise to add a layer of defense "just to be safe"?  Or at least give the user the choice if he "out of the box" wants such a layer or not (as is the current behaviour)?

Just my 0.02€  ;)

I really do have trouble with grasping how a firewall acts as a layer and protects a running service. Honest!

Why encourage a user to install a firewall or put the thought in his mind? If he wants one he can install it. Not necessarily for the right reasons but it becomes his choice rather than a shared one he is edged into.

---

### Post by tebbens on 2008-06-04
> **brian_p said:**
> I don't need to know anything and neither does anyone else. By default all installed services are safe.
I have said this before; if you do not accept it, say why.

There is nothing 100% safe, expecially computers!
The default services may not be safe, along with any updates to them.

My main problem is that there is absolutely no notification that the Firewall is off by default during the install. At the very least say something about it. I would rather see an option during the install... Do you want the Firewall ON or OFF ?

---

### Post by stream303 on 2008-06-04
This is more of a usability question rather than a security issue in regards to a firewall:

Assuming you are secure because you haven't opened any ports, isn't it wise to run a firewall (of some sort) to just keep your computer from responding to the general internet "background noise" (pings, probes etc for ports that are closed anyway), or is this urban-legend?

Seems like less annoying packets to deal with..

---

### Post by scorp123 on 2008-06-04
> **brian_p said:**
>  I really do have trouble with grasping how a firewall acts as a layer and protects a running service. A firewall -- or other mechanism such as "hosts.deny" for that matter -- can limit (depends on your configuration, of course) the IP ranges that are able to connect to your service.

I have customers who do this with $$$ commercial products, e.g. their servers are connected to the Internet, but the firewalls and the IDS make sure only legit traffic gets through to the servers. As soon as you try portscans or similar stuff the firewalls will keep you away. Some commercial firewalls such as "CheckPoint" will indeed inspect the package *before* handing them over to the target server, even if the firewall rules say "let this stuff through". This makes it impossible to e.g. hide SSH transmissions in HTTP traffic and vice versa. So there is your firewall which acts as a layer between client and server. 

I am not sure if "iptables" or "Netfilter" as it probably should be called is able to do that too. With add-on packages such as "snort" this should be possible I guess?

It shouldn't be too hard to produce a free + open setup which too keeps an eye open on "unwanted events" (e.g. failed login attempts) or "unwanted traffic" and then triggers a script which will adapt the firewall rules to keep away the IP address that is bugging your system ... before it becomes a nuisance.

So what's this got to do with the thread?

Well, as I said before: I can see the argument against having a default firewall always on (because there is nothing to protect in the first place). But I can also see the worries of those who would prefer to have one out of the box; and you'd have to admit that the Morris worm was quite a bad surprise back in its days, so I can only assume what interesting effects a "Moris II" worm could have if there all of a sudden were one.

So in the light of this .... How about coming up with something truly elegant then that would indeed satisfy both sides of the argument? (I know ... I am being typically Swiss here :-)  )

Someone in this thread has demonstrated (sudo iptables -L -v) that despite there being no active firewall rules, the firewalling parts are present nontheless and even counting the traffic that went in and out. So far so good. But instead of just counting those packets, how about having the software actually inspect them? (or at least parts of them)

Imagine this:
- there are no firewall rules, no filtering is taking place out of the box.
- but the packets are being inspected nontheless (at least partially).
- as soon as this packet inspection engine detects "unwanted" events (e.g. packet storm or aggressive port scan from the same source IP again and again, etc.) it springs to life and dynamically creates a firewall rule to block the origin of those packets.
- same for failed login attempts (this package would have to be aware of e.g. telnet, ftp, ssh, mysql, http, https, and maybe many other services to be of real use): if it detects a certain number of failed logins it springs to life and blocks the source IP address ...
- the user is notified either via a pop-up message or an e-mail to the "root" account (or both?).
- after a certain timeout is reached (e.g. a couple of hours?) the firewall dynamically drops the rules it created again ...

With something like this both sides of the argument here would have their way; plus it would really be a nice solution, wouldn't it?

IMHO the software packages to do all this are already here:
- denyhosts
- fail2ban
- ippl
- scanlogd
- snort
- various packet sniffers that can auto-check packet headers

... one would just need to bring it all together into one nice end-user package.

Of course, there should still be the option to turn all this off so those who don't want it get the current behaviour again (= no firewall filtering taking place).

---

### Post by stmurray on 2008-06-04
> I really do have trouble with grasping how a firewall acts as a layer and protects a running service. Honest!


I agree-- it doesn't.  But it does protect you from future unknown open services.  Two examples of "unlikely" services have appeared already in this thread-- Avahi (enabled by default and opens a UDP service) and cups (opens a UDP service when enabled).  My machine's configuration changes all the time.  I get updates from Update Manager, and I install or enable software.  I don't want to check all the details of each update (or upgrade to a new Ubuntu version) or have to worry about any configuration change that may open a service on my machine that I don't know about. 

I have the firewall running, and I know exactly what services are exposed, no matter what havoc I wreak on my machine's configuration. 

(And if there is ever a 0-day worm that exploits a previously unknown buffer overflow in Avahi or cups, I don't have to worry about that either)

Having said all that, I understand Ubuntu's decision not to enable the firewall, because without knowing how the machine will be used, it would be a burden on new users.  But I also agree that having some kind of notice on installation that there is no firewall enabled and pointing to how-to documentation would be a good idea.

---

### Post by kevdog on 2008-06-04
Poll #2 has been posted in order to determine how many users install server software after the Ubuntu base install:
[http://ubuntuforums.org/showthread.php?t=818989](http://ubuntuforums.org/showthread.php?t=818989)

---

### Post by tebbens on 2008-06-05
> **brian_p said:**
> We probably find them interesting for different reasons.

Incidentally: you have never said what this default firewall would look like. Care to give a brief outline?

I don't think a firewall should be on by default.
What I would like to see is the option to turn it on, or at
least a notice to the installer about fact that the firewall
is off by default.

Clearly, posts and responses to the poll show that something
needs to be done.

---

### Post by brian_p on 2008-06-05
> **stmurray said:**
> (And if there is ever a 0-day worm that exploits a previously unknown buffer overflow in Avahi or cups, I don't have to worry about that either)

The default cupsd.conf is locked down. There is no internet access to it.

avahi listens only on the LAN. Please see

[https://wiki.ubuntu.com/ZeroConfPolicySpec](https://wiki.ubuntu.com/ZeroConfPolicySpec)

No 0-day or any other day worm is possible.

---

### Post by brian_p on 2008-06-05
> **tebbens said:**
>  Clearly, posts and responses to the poll show that something needs to be done.

I'll give a hand with this. There clearly needs to be a some choice in the type of filtering done by the firewall installed and, unless I've missed it, there have been no suggestions as to what a user will get. So, my input:

You have chosen to install a firewall (incoming packets will be filtered). Please select from the following options.

[ ] No filtering (As used and recommended by Linus Torvalds).
[ ] Reject all packets to all ports. (Real fun when you choose to run a service).
[ ] Filtering on during a weekday; off at weekends (Keeps the crackers on the hop).
[ ] Open and close random ports at random times (Useful with ssh. Experimental. Use with caution).

Please feel free to say what you envisage.

---

### Post by stmurray on 2008-06-05
> **brian_p said:**
> The default cupsd.conf is locked down. There is no internet access to it.

I'm not sure what you mean by locked down.  I used cups because per an earlier post in this thread, it is apparently listening on a UDP port.  If it accepts network traffic, then it must parse and process the packet and the data in the packet.  If the code that does that has vulnerabilities, then an attacker could send purposefully mal-crafted packets to exploit the vulnerabilities and possibly run code of their choosing 

> **brian_p said:**
> 
avahi listens only on the LAN. Please see

[https://wiki.ubuntu.com/ZeroConfPolicySpec](https://wiki.ubuntu.com/ZeroConfPolicySpec)

No 0-day or any other day worm is possible.

I'm not sure why that would be the case.  There has to be code parsing at least the source address of the packet in order to verify that it is from the local lan (and drop the packet if it is not).  That code could have vulnerabilities.  And besides, a worm could  come from the local lan.  Many worms/virus have multiple infection vectors (that is, they spread multiple ways, by email, network exploit, Instant Messaging....).  

I have no reason to believe that either cups or avahi have vulnerabilities, and I believe the risk that they do have vulnerabilities is low.  And even if they did, the risk of a worm exploiting the vulnerability before it gets patched is even lower.  I am sure that is why the Ubuntu packagers "allow" them to install and listen on ports, even though most users don't know they do listen on ports.  The trade off is acceptable (that is, the risk of compromise is so low, that the benefit of the service they perform for the user outweigh the risk).  And I agree with that assessment.

---

### Post by brian_p on 2008-06-05
> **stmurray said:**
> I'm not sure what you mean by locked down.  I used cups because per an earlier post in this thread, it is apparently listening on a UDP port.  If it accepts network traffic, then it must parse and process the packet and the data in the packet.  If the code that does that has vulnerabilities, then an attacker could send purposefully mal-crafted packets to exploit the vulnerabilities and possibly run code of their choosing 

There have been exploits along these lines in the past but because Ubuntu's cups listens only to localhost and has browsing off it is not vulnerable. The documentation at [http://localhost:631/](http://localhost:631/) has the details.

> I'm not sure why that would be the case.  There has to be code parsing at least the source address of the packet in order to verify that it is from the local lan (and drop the packet if it is not).  That code could have vulnerabilities.  And besides, a worm could  come from the local lan.  Many worms/virus have multiple infection vectors (that is, they spread multiple ways, by email, network exploit, Instant Messaging....). 

I was concentrating on a remote exploit but, as you correctly point out, the LAN is also a concern. The quick and efficient way with avahi (if you've no use for it) is to turn it off or, better still, use your favourite package manager to remove it from the system. Why get iptables to filter packets for an application which is doing nothing?

> I have no reason to believe that either cups or avahi have vulnerabilities, and I believe the risk that they do have vulnerabilities is low.  And even if they did, the risk of a worm exploiting the vulnerability before it gets patched is even lower.  I am sure that is why the Ubuntu packagers "allow" them to install and listen on ports, even though most users don't know they do listen on ports.  The trade off is acceptable (that is, the risk of compromise is so low, that the benefit of the service they perform for the user outweigh the risk).  And I agree with that assessment.

My attitude is similar to yours. avahi is seen as an important service to have but not at a cost of underplaying or neglecting security aspects.

---

### Post by michaelzap on 2008-06-05
> **brian_p said:**
> 
I was concentrating on a remote exploit but, as you correctly point out, the LAN is also a concern.

Absolutely. People with laptops often connect to unfamiliar networks or hotspots, and that could allow an attacker to start on the same LAN. Or a hacker could crack your WEP key or otherwise gain access to your own LAN.

So while limiting a service to the LAN is important, it certainly is not foolproof.

With a firewall one can limit access to LAN services much more strictly (e.g., only allow your coworker to connect to your shared folder) and you can also use it to monitor the network for suspicious activity.

---

### Post by hyper_ch on 2008-06-06
> **michaelzap said:**
> With a firewall one can limit access to LAN services much more strictly (e.g., only allow your coworker to connect to your shared folder) and you can also use it to monitor the network for suspicious activity.

If you know how... but generally shutting everythign down with a firewall results in the average user that he can't use many of the services he wants to use.

---

### Post by HunterThomson on 2008-06-06
OK what about this....


Lets say the someone is using a "Wireless router's Firewall" As there firewall.... It is set up like this... Right?

Workstation1----->
Workstation2----->   Wireless Router Firewall----> Internet
Attacker--------->

The attacker can attack Workstation1 with no intervention form the Wireless Router's Firewall... Right? So, in this case you would still be best to have a firewall on the workstation... Right?

Workstation1------>
Firewall
Workstation2------>   Wireless Router Fierwall----> Internet
Firewall
Attacker---------->

---

### Post by HunterThomson on 2008-06-06
> **michaelzap said:**
> Absolutely. People with laptops often connect to unfamiliar networks or hotspots, and that could allow an attacker to start on the same LAN. Or a hacker could crack your WEP key or otherwise gain access to your own LAN.

So while limiting a service to the LAN is important, it certainly is not foolproof.

With a firewall one can limit access to LAN services much more strictly (e.g., only allow your coworker to connect to your shared folder) and you can also use it to monitor the network for suspicious activity.

Owe,, I should have read the new posts before I posted... You guys already said that...

---

### Post by hyper_ch on 2008-06-06
if you have nothing running on your workstation you don't need a firewall ;)

Furthermore, if you have a service running you normally want it to be accessible by the outside. So you'll punch a hole into the firewall then.

Those that install apache, mysql and php for local developement should know how to limit that access BUT mostly people want to install P2P and instant messaging stuff for file transfers and for those they deliberately do want to be open.

In most cases a firewall is not needed.

---

### Post by kevdog on 2008-06-06
Just curious based on the logic of this discussion if there is an active firewall on the Ubuntu server edition?  Surely if the release has "server" in the name, they must anticipate people to run listening processes from the machine.  In this scenario, wouldn't a default drop stance be the better setup?  And by the same logic, if someone is smart enough to use the Ubuntu server edition and install a server, they should be smart enough to configure the firewall to allow access to the server.

---

### Post by hyper_ch on 2008-06-06
> **kevdog said:**
> Surely if the release has "server" in the name, they must anticipate people to run listening processes from the machine.  In this scenario, wouldn't a default drop stance be the better setup?/QUOTE]
Doesn't make sense... if they want to run a server then it should by default not be blocked...


[QUOTE=kevdog;5127347]And by the same logic, if someone is smart enough to use the Ubuntu server edition and install a server, they should be smart enough to configure the firewall to allow access to the server.
That is no logic ;) If someone wants to run a server he wants to have daemons that provide services hence serve and not a blackbox where nothing goes in and nothing comes out. They should be able to restrict firewall policies - if needed.

Basically you are saying that all the server software is at danger. Apache for example is fairly secure... if you just run apache I don't see much point for a firewall... and if there is a security issue with apache itself, chance that a firewall will prevent anything is, IMHO, quite small. Apache is a service that is, normally, setup to serve to the whole world.

Firewalls IMHO come only in place you want to restrict to whom you want to serve.

---

### Post by kevdog on 2008-06-06
Hard to say things are secure in light of the entire Debian OpenSSH fiasco recently discovered.  OpenSSH touts itself as one of the most secure programs in the world, and although the exploit wasn't due to the OpenSSH people themselves, obvious there was a security hole for over 2 years.  

You want to run Apache wide open:

iptables -A INPUT -i <interface> -p tcp --dport 80 -j ACCEPT

There done!  How hard was that to set up??  Seriously its harder to configure Apache itself.

As far as the debate at hand, I just don't want to hear the reason that iptables isn't active by default b/c there are no listening processes by default.  That makes no sense if you --- since by this rationale the server edition should have an active iptables ruleset since its intended purpose is to have listening processes.  

And as far as iptables, how hard are they to configure anyway?

---

### Post by hyper_ch on 2008-06-06
> **kevdog said:**
> Hard to say things are secure in light of the entire Debian OpenSSH fiasco recently discovered.  OpenSSH touts itself as one of the most secure programs in the world, and although the exploit wasn't due to the OpenSSH people themselves, obvious there was a security hole for over 2 years.
And how would a firewall have prevented here anything?

> **kevdog said:**
> 
You want to run Apache wide open:

iptables -A INPUT -i <interface> -p tcp --dport 80 -j ACCEPT

There done!  How hard was that to set up??  Seriously its harder to configure Apache itself.
Is there a reason to restrict apache first place? If so, then apache is inherently dangerous and shouldn't be run at all, right? Actually that command is way more difficult than setting up a basic webpage with apache ;)

---

### Post by kevdog on 2008-06-06
> **hyper_ch said:**
> And how would a firewall have prevented here anything?

Would have limited the threat, iptables in combination with port knocker utility with ssh server would have neutralized threat.


> Is there a reason to restrict apache first place? If so, then apache is inherently dangerous and shouldn't be run at all, right? Actually that command is way more difficult than setting up a basic webpage with apache ;)

Since when did I say Apache was dangerous?  Ever try to set HTTPS on Apache?? Not quite so easy.

---

### Post by hyper_ch on 2008-06-06
> **kevdog said:**
> Would have limited the threat, iptables in combination with port knocker utility with ssh server would have neutralized threat.
Are you sure? How?

> **kevdog said:**
> Since when did I say Apache was dangerous?  Ever try to set HTTPS on Apache?? Not quite so easy.
By saying that you first need to punch a hole into the firewall so that apache can operate in its normal behaviour you imply that apache is inherently dangerous... if it was not, there would be no need to firewall it first place ;)

---

### Post by kevdog on 2008-06-06
Security is a multiple layer approach.  To expect Apache to at all times be responsible for its own security would be presumptive.  There have been many exploits of Apache in the past, and will continue to do so.  If you do not acknowledge this fact, then you are turning your back on history.

If you want to turn disable the iptable ruleset:

iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -X

How hard was that?

And back to the original premise, what's wrong with informing the user at installation that the built-in firewall at the time of installation is not configured and hence inactive -- providing no filtering capabilities.  If they need more info on configuring the firewall see [http://.](http://.).....

Seems my original point has been overlooked?!

---

### Post by michaelzap on 2008-06-06
It seems as if the argument against firewalls has turned religious. As if offering to configure one on installation would be tantamount to denying the divinity of Linux. All that's left is to compare firewall boosters to appeasers of Hitler (Godwin!).

A firewall is a multiuse security tool that provides an extra layer of protection. Your argument is essentially that anyone using Ubuntu needs no second layer. What do you have against multiple layers?

There are numerous examples of situations in which a firewall could keep you more secure than not having one. The idea that "most people" don't do these things is a fallacy. Lots of people experiment with all sorts of things on Linux, and a firewall can help to keep them safer.

Example: A new web designer installs a local LAMP server to learn to program PHP. She uses her firewall to limit access to those services to her local machine, since she knows that she's using incorrect permissions and making other mistakes she wouldn't want to be public.

The other argument seems to be that it will add too much complexity for new users. That's what the wiki, forums, and help are for. I heard the same argument against full disk encryption: A lot of users will mess it up and have problems for which they'll unfairly blame Ubuntu, so let's keep that option from them to protect Ubuntu's image.

Firestarter is very easy to use, and P2P folks have been configuring their routers and firewalls since the days of Napster, so I really don't see the big deal.

---

### Post by stmurray on 2008-06-06
> **brian_p said:**
> Why get iptables to filter packets for an application which is doing nothing?


My main reason for using the firewall is because I am always tinkering with my system- installing packages, changing configs, updating packages.  The risk i am trying to mitigate by using the firewall is that I unintentionally open a port on my machine.  The added security outweighs the hassle of the firewall (to me).  Protecting ports that I know are open and don't use (like Avahi) is a secondary benefit.  

> **brian_p said:**
> The quick and efficient way with avahi (if you've no use for it) is to turn it off or, better still, use your favourite package manager to remove it from the system.

I haven't disabled Avahi, but I should, as this story shows: 
IPV6 was enabled on my first Ubuntu installation and when I installed VNC, it automatically opened an IPV6 TCP port .  Using firestarter, I thought I was blocking everything except ssh (tunneling the vnc over that), but I wasn't. (Apparently, none of the iptables front-ends at the time allowed for the IPV6 rules.) As I recall, a post to my question mentioned the IPV6 being enabled was a "bug" at the time, and that Ubuntu by default does not enable IPV6, but I have never verified that.  So the lesson learned is, even though (I believe) Ubuntu does a very good job of balancing the usability and security on it's default installation, don't get smug. If your data and/or computer uptime is important to you, use defense in depth: Don't think you are not at risk, because you run a firewall.  Shut services down if you don't use them.  And don't think you are not at risk because you don't have any ports open-- you may get surprised at what is open on your machine....

---

### Post by hyper_ch on 2008-06-06
> **michaelzap said:**
> It seems as if the argument against firewalls has turned religious. As if offering to configure one on installation would be tantamount to denying the divinity of Linux. All that's left is to compare firewall boosters to appeasers of Hitler (Godwin!).
Why do you religiously preach for something that is not needed by an average user? All that's left is to compare firewall cricits to appeasers of Hitler (Godwin!).

> **michaelzap said:**
> A firewall is a multiuse security tool that provides an extra layer of protection. Your argument is essentially that anyone using Ubuntu needs no second layer. What do you have against multiple layers?
(1) What do you need an extra layer of protection for anyway if you can't be touched first-place?
(2) Where did I say that anyone using Ubuntu does not need a firewall? I say that in most cases you don't neet one.
(3) Multiple layers that are obsolete because they don't provide any extra security make me feel... hmmm... bloat...

> **michaelzap said:**
> There are numerous examples of situations in which a firewall could keep you more secure than not having one.
I notice the word "could". So you don't even know. Please name als those numerous examples of situations... my own list in this regard is very short.

> **michaelzap said:**
> The idea that "most people" don't do these things is a fallacy. Lots of people experiment with all sorts of things on Linux, and a firewall can help to keep them safer.
But what do those most people do? Only a very small number of people I know of have ever installed apache or ssh server or ftp server or or or... but again, I do notice "can" instead of "does".

> **michaelzap said:**
> Example: A new web designer installs a local LAMP server to learn to program PHP. She uses her firewall to limit access to those services to her local machine, since she knows that she's using incorrect permissions and making other mistakes she wouldn't want to be public.
Exactely, because she does install apache and mysql servers she will then secure that. Not that she will secure herself with a firewall because she might install it at some point ;) Thank you :)

> **michaelzap said:**
> The other argument seems to be that it will add too much complexity for new users. That's what the wiki, forums, and help are for.
Have a look at the absolut beginner forums. How many of those read the wiki, forums or google? They have a problem, they post the problem and wait for a solution... no need for them to do any research on their own ;)

> **michaelzap said:**
> I heard the same argument against full disk encryption: A lot of users will mess it up and have problems for which they'll unfairly blame Ubuntu, so let's keep that option from them to protect Ubuntu's image.
I don't get your point here. Please elaborate.

> **michaelzap said:**
> Firestarter is very easy to use, and P2P folks have been configuring their routers and firewalls since the days of Napster, so I really don't see the big deal.
In the days of Napster there have, at least here, not been many home routers around. And todays homerouters have UPnP enabled by default... although on windows you're better of having it disabled... and most people I know will get their router/cable-/dsl-modem from the provider, hook it up and not do anything with it... neither change admin password, ... so I do see a big deal upon a system that's shutdown with a firewall by default.

---

### Post by brian_p on 2008-06-06
> **kevdog said:**
> And back to the original premise, what's wrong with informing the user at installation that the built-in firewall at the time of installation is not configured and hence inactive -- providing no filtering capabilities.  If they need more info on configuring the firewall see [http://.](http://.).....

Seems my original point has been overlooked?!

The original proposals are in posts #22, #33 and #34. They are quite a bit different from what you have above.

A notification, then. Nothing more? Something which informs the user that the system can be configured in a different way? Ok.

Could we also have notices that cups does not discover printers on the network or that an MTA is not installed?

---

### Post by brian_p on 2008-06-06
> **michaelzap said:**
> It seems as if the argument against firewalls has turned religious. As if offering to configure one on installation would be tantamount to denying the divinity of Linux. All that's left is to compare firewall boosters to appeasers of Hitler (Godwin!).

I'd see it primarily as an engineering argument. Why not configure an application at the application level? Most servers offer fine-grained control and tcp wrappers is very useful.

> A firewall is a multiuse security tool that provides an extra layer of protection. Your argument is essentially that anyone using Ubuntu needs no second layer. What do you have against multiple layers?

Multiple layers is a nice security buzz phrase. It would be more convincing to give two or three examples of the extra security a firewall can give.

> 
Example: A new web designer installs a local LAMP server to learn to program PHP. She uses her firewall to limit access to those services to her local machine, since she knows that she's using incorrect permissions and making other mistakes she wouldn't want to be public.

Has this any advantage over the tools provided by the applications? For example, the htaccess stuff. Not that I know much about web servers but that is where I would look for control.

---

### Post by Monicker on 2008-06-06
Not that I am completely against firewalls at the workstation level, but I do think they are best used at the network gateway level.  I think this has been brought up before in this thread.  If you have multiple machines being accessed, without NAT, then a firewall is a good way to filter the traffic to those machines.

The point of the application controls is well taken.  Apache has directives for allowing/denying traffic from specific ip addresses and ranges.  If you are going to learn to use s service, then you should be familiar with all aspects of securing it, and not just relying on a firewall.  Things like buffer overflows, sql injection, assignment of permission should all be taken into account.  Being new and learning is fine, but if you want to develop something that will eventually be exposed to scrutiny outside of the local machine, I think its a given that you can expect that it may be attacked in some fashion.  Why not also learn to make it as secure as you can?

---

### Post by brian_p on 2008-06-06
> **stmurray said:**
>  Shut services down if you don't use them.

Good advice. Where are you up to with avahi?

> And don't think you are not at risk because you don't have any ports open-- you may get surprised at what is open on your machine....

Why are people so afraid of open ports? You can almost hear the gasps of horror and incredulity when someone declares they run a server. Doesn't seem to bother Google; they must have millions.

If the software in Ubuntu listening on those ports was known to be insecure and nothing was done about it the distribution wouldn't last a month. But it isn't and you always keep up-to-date.

---

### Post by tebbens on 2008-06-06
> **brian_p said:**
> Multiple layers is a nice security buzz phrase. It would be more convincing to give two or three examples of the extra security a firewall can give.


Information in the form of logs....this is very important.

Protection against certain types of attacks...
Besides what is listed below, I'm sure there are other types.

# SYN-FLOOD
-N SYN-FLOOD
-A Firewall-INPUT -p tcp -m tcp --syn -j SYN-FLOOD
-A SYN-FLOOD -m limit --limit 1/second --limit-burst 4 -j RETURN
-A SYN-FLOOD -j LOG --log-prefix "IPTABLES SYN-FLOOD: "
-A SYN-FLOOD -j DROP

# SSH-FLOOD
-N SSH-FLOOD
-A Firewall-INPUT -s ! 192.168.1.0/24 -p tcp -m tcp --dport 22 -m state --state NEW -j SSH-FLOOD
-A SSH-FLOOD -m limit --limit 2/minute --limit-burst 2 -j RETURN
-A SSH-FLOOD -j LOG --log-prefix "IPTABLES SSH-FLOOD: "
-A SSH-FLOOD -j DROP

# NEW NOT SYN
-A Firewall-INPUT -p tcp ! --syn -m state --state NEW -j LOG --log-prefix "IPTABLES NEW-NOT-SYN:"
-A Firewall-INPUT -p tcp ! --syn -m state --state NEW -j DROP

# FRAGMENTS
-A Firewall-INPUT -f -j LOG --log-prefix "IPTABLES FRAGMENTS: "
-A Firewall-INPUT -f -j DROP

---

### Post by michaelzap on 2008-06-06
> **hyper_ch said:**
> Why do you religiously preach for something that is not needed by an average user? All that's left is to compare firewall cricits to appeasers of Hitler (Godwin!).
.

I don't see how wanting to offer people the option to install and configure a firewall with information about why they might or might not need it when they install Ubuntu is religiously preaching. If I am expressing any "faith" here, it's that users are smart enough to make their own choices if they're presented with options and information. You seem to want to limit people's choices to what you have decided is necessary and correct, which strikes me as dogmatic.

The Hitler reference is obviously over-the-top and meant to indicate that the conversation has become unproductive.
> **hyper_ch said:**
> 
(1) What do you need an extra layer of protection for anyway if you can't be touched first-place?
(2) Where did I say that anyone using Ubuntu does not need a firewall? I say that in most cases you don't neet one.
(3) Multiple layers that are obsolete because they don't provide any extra security make me feel... hmmm... bloat...

RE #1. Because they could be touched. No OS is invulverable, and many people consider extra protection worthwhile. Just discovering a machine on the network allows you to do a denial-of-service attack against it, for example.

RE #2: Your argument seems to be that "most people" or "the average user" doesn't need a firewall. I don't think that we know that for sure, and I'd prefer to give people the option. A lot of people (myself included) would choose it.

RE #3: A firewall DOES provide extra security if it's configured properly. It is a tool that allows a user to modify their system's network defenses based on their specific needs and situation. So again I can share files only to my coworker's computer and block any other requests, etc.

Bloat?!? We're talking about an OS that comes with Compiz, ferchrissakes. How much memory or CPU does the Firestarter applet use compared to that?

> **hyper_ch said:**
> 

I notice the word "could". So you don't even know. Please name als those numerous examples of situations... my own list in this regard is very short.


A short list is still a list, isn't it? And if you look through my previous posts and those of others you'll see several other examples. If you don't want to consider them as valid because "if people are installing LAMP or Samba they ought to know about firewalls also" then that's up to you.

> **hyper_ch said:**
> 

But what do those most people do? Only a very small number of people I know of have ever installed apache or ssh server or ftp server or or or... but again, I do notice "can" instead of "does".


I guess I know more or different people than you do then.

> **hyper_ch said:**
> 
Exactely, because she does install apache and mysql servers she will then secure that. Not that she will secure herself with a firewall because she might install it at some point ;) Thank you :)


Some people (myself included) know that we're going to experiment with software that might open us up to additional vulnerabilities when we first install Ubuntu, and thus we might appreciate the opportunity to install it at that time (plus it's a good opportunity to educate people about them and how they're used).

> **hyper_ch said:**
> 
Have a look at the absolut beginner forums. How many of those read the wiki, forums or google? They have a problem, they post the problem and wait for a solution... no need for them to do any research on their own ;)


So the best way to not have to deal with users who refuse to educate themselves is to decide for them? Personally I would make the effort to educate them. I think that the majority of beginners appreciate and respond well to that, and you'll never be free of the difficult minority of constant gripers anyway.

> **hyper_ch said:**
> 
I don't get your point here. Please elaborate.


On the Ubuntu Brainstorm site, many people argued against making full-disk encryption an easy and straightforward thing to do in the installer because they said that stupid users would mess it up, have more trouble recovering their system, and then blame Ubuntu for the problem. You seem to be saying the same thing about firewalls. Because (in theory) they could block traffic that novice users won't understand how to unblock, and those people might blame Ubuntu for their difficulties, the option to install a firewall should be something that only those who actively look for it will find.

> **hyper_ch said:**
> 
In the days of Napster there have, at least here, not been many home routers around. And todays homerouters have UPnP enabled by default... although on windows you're better of having it disabled... and most people I know will get their router/cable-/dsl-modem from the provider, hook it up and not do anything with it... neither change admin password, ... so I do see a big deal upon a system that's shutdown with a firewall by default.

Again, you and I know different people. And I haven't seen anyone argue for completely shutting down a system with a firewall by default, so that's not the alternative to not having one. The alternative that I would recommend is giving people the option to install it and some sample configurations to choose from (as some other distros already do).

---

### Post by stmurray on 2008-06-06
> **brian_p said:**
> Why are people so afraid of open ports? You can almost hear the gasps of horror and incredulity when someone declares they run a server. Doesn't seem to bother Google; they must have millions.

If the software in Ubuntu listening on those ports was known to be insecure and nothing was done about it the distribution wouldn't last a month. But it isn't and you always keep up-to-date.

Afraid is a strong word.  Google needs the millions of servers to make the billions of dollars they make.  So, they spend some money to ensure those servers are secure (probably a lot of money, as Google needs people to believe they are secure, to make sure they don't lose users and can make even more money).   Then they accept any residual risk after that.   

For me, I am not afraid of opening ports (I have sshd running on all my machines), it is reducing the risk for things things like this:
[http://secunia.com/advisories/30228/](http://secunia.com/advisories/30228/)  The fixed version of samba hasn't reached the Ubuntu repositories, yet.  Risk is very low of this being exploited before then (The Ubuntu packagers deserve all of our thanks and admiration), but the risk to me is (virtually) non-existent.  I don't need Samba, and therefore don't run Samba and iptables would keep any attack against it from being successful, even it does get enabled.  


(cups was recently patched as well--> [http://www.ubuntu.com/usn/usn-598-1](http://www.ubuntu.com/usn/usn-598-1) came out about 2 weeks after the advisory ->[http://secunia.com/advisories/29431/](http://secunia.com/advisories/29431/).  I call this is a fast turnaround-- again kudos to the packagers!!)

---

### Post by brian_p on 2008-06-06
> **tebbens said:**
> Information in the form of logs....this is very important.

Applications log too.

> Protection against certain types of attacks...
Besides what is listed below, I'm sure there are other types.

[Snip iptables rules]



To me layers mean one thing after another. Portknocking prior to using am MTA is an example of layering. The rules appear to duplicate what can be done with an application (sysctl and denyhosts would do the first two) or do something which is not possible at the application level. Then again, it wouldn't be the first time I've misinterpreted a term.

---

### Post by michaelzap on 2008-06-06
It's important for applications to be secure and properly configured also. But as noted sometimes there will be vulnerabilities in any software, and patches often don't arrive immediately. So that's where an additional layer of protection comes in handy.

It's also useful to be able to deal with application behavior individually but have a central place to determine overall policy for your entire machine.

Installing Firestarter would have practically zero effect on system performance (it's probably lighter on system resources than the Apearance control panel) and give users the ability to use the built-in iptables firewall as a secondary layer of protection. It's not like anti-virus software, for example, which really would slow down your system for no significant purpose. You can always turn it off at the click of a button if you're having trouble getting something to work.

I cheered when the Ubuntu machine was unscathed in the recent Pwn 2 Own contest, and I delight in telling people how much more secure Linux is than Windows, but I'm not going to get so cocky that I let my guard down when it costs me nothing to maintain it up.

---

### Post by brian_p on 2008-06-06
> **Monicker said:**
> Not that I am completely against firewalls at the workstation level, but I do think they are best used at the network gateway level.  I think this has been brought up before in this thread.  If you have multiple machines being accessed, without NAT, then a firewall is a good way to filter the traffic to those machines.

Firewalls for networks by all means. They are ideal, especially if there are untrusted machines on it or complex operations to perform.

> Why not also learn to make it as secure as you can?

It's not that firewalls cannot or should not play a suitable part in contributing to security but it seems to me they are often a first port of call even in the simplest of situations. In most cases there are more fruitful ways of achieving an objective.

---

### Post by HunterThomson on 2008-06-06
I have iptables set up:) I also use ipfilter to block ipranges:) I Block a vary large list of known attacker web sights:) I am not going to change this because I get hits constantly,((by web sights and form IP ranges that after a whois and a google confirm I am vary happy are being blocked))

Form what I understand.... Window$, MacOS, BSD, Linux..... Would all not need a firewall and windows would not need anti-virus and there would be no need for IT security specialists if it all programs and web sights were written correctly. Nothing would be exploitable... However, this is not the world we live in.... There are exploits>>> [http://insecure.org/sploits.html](http://insecure.org/sploits.html) <<< Even your firewall can have exploits:) so lets say you are running SSH and SAMBA and you use only one firewall that sits between your computer/'s and the internet... Someone finds a way to exploit that firewall. ZEROday or it really don't have to be Zeroday it could be day 2,3,4,5,or 13 before a patch is out.... then they can attack SSH and SAMBA no problem:) But, if you also had IP tables set-up on your BOX then they would still be blocked:)

---

### Post by HunterThomson on 2008-06-06
I just got the new "LINUX PRO Magazine" June 2008. This issue is "All About Linux Security." Last months  issue has a vary long section about Linux security too. I hope I find a reason to have fire starter set-up on ones Ubuntu Box as well as a firewall on the router:)((besides the Point I made about a Wireless network leaving your Box open to attack)) I am sure there are. LIKE, there are a lot more options in iptabels then just OPEN Port 21 or Close Port 21..... I thought Firestarter's default workstation configuration was to make all ports "Permissive" not just OPEN ports that need to be used. Iptables can be used to restrict access to services like SSH i.e. Only allow you computer at work to connect to your home computer through SSH. Not just OPEN port 21.

I also use firestarter to block Ping:)

[http://www.phrack.org/issues.html?id=6&issue=49](http://www.phrack.org/issues.html?id=6&issue=49)

I also block timestamping, MS Traceroute, Traceroute, Unreachable, Redirection

---

### Post by kevdog on 2008-06-07
Seems like a lot of people according to this informal poll, do infact run server programs (as opposed to other opinions put forth in this thread):
[http://ubuntuforums.org/showthread.php?t=818989](http://ubuntuforums.org/showthread.php?t=818989)

---

### Post by hyper_ch on 2008-06-07
this does not mean anything...

look at the testimonials section and the polls in there... if you extrapolite the results there it seems that for most ubuntu users ubuntu does not run ;)

---

### Post by kevdog on 2008-06-07
I'm not looking at the testimonials, just the raw poll results.  You don't have to post a response in order to vote in the poll.  For every poll I participate in, I rarely post a comment.  If you would like to post your own poll, I would encourage it, since Im certain mine would not meet true scientific method criteria.  However until I see other results disproving this poll, this is the only hard evidence tending to make me believe more users than not run server software.]

Im not extrapolating with these results -- they are actual results.

---

### Post by hyper_ch on 2008-06-07
no, you think that those 100 people or so how posted there ar representative for the - I don't know how many - ubuntu users there are ;)

---

### Post by kevdog on 2008-06-07
What evidence other than extrapolation and conjecture do you have to dispute these results???  Please lets keep the discussion on point.  I didn't bias my poll one way or another, and I can't control who actually votes in the poll.  You have done nothing other than complaining about my poll to actually take steps to support your position.  Again I don't know what the correct percentages of people are who actually run server vs those who don't, however at least I have taken some steps to discern the difference.  Please develop other methods, or post your own poll so we together can attempt to discover the truth.  Simply posting your own objections to information gathered thus far is not constructive or helpful in any way.

---

### Post by hyper_ch on 2008-06-07
the sample is too small and diversity is not granted to be of statistically importance ;) hence it is not representative and hence conclusions shouldn't been drawn from it.

As I said in my first reply to it, have a look at the polls in the testimonials section... according to those ubuntu does not run for most users ;)

---

### Post by tebbens on 2008-06-07
> **hyper_ch said:**
> no, you think that those 100 people or so how posted there ar representative for the - I don't know how many - ubuntu users there are ;)

For all the "ubuntu users there are", do you think the opposite
is true... that most ubuntu users don't install a server ?

The poll is more proof then anything I've seen posted here so far.

---

### Post by hyper_ch on 2008-06-07
Yes, most ubuntu users don't install a server...

From what I've seen in those forums in general, ubuntu users do not install servers in general ;)

---

### Post by kevdog on 2008-06-07
> **hyper_ch said:**
> the sample is too small and diversity is not granted to be of statistically importance ;) hence it is not representative and hence conclusions shouldn't been drawn from it.

As I said in my first reply to it, have a look at the polls in the testimonials section... according to those ubuntu does not run for most users ;)


Rebutting the veracity of my directed on-topic non-scientific poll using other non-scientific, off-topic polls and generalized observations in other subforums as evidence is frankly ironic.

---

### Post by hyper_ch on 2008-06-07
yes it is... showing you by methods you apply that nobody would be running ubuntu if you take credit for what is ranted there ;)

---

### Post by kevdog on 2008-06-07
> **hyper_ch said:**
> yes it is... showing you by methods you apply that nobody would be running ubuntu if you take credit for what is ranted there ;)

That doesn't make any sense.

---

### Post by tebbens on 2008-06-08
This is getting boring.

Next Topic?  :)

---

### Post by michaelzap on 2008-06-08
Hitler was boring and didn't make any sense either (are you allowed to call Godwin on yourself to end a thread?).

---

### Post by kevdog on 2008-06-08
I've moved on to the next topic, I think my point was made many, many posts ago.

---

