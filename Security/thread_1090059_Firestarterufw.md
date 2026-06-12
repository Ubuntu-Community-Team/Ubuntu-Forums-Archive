---
title: "Firestarter/ufw"
date: 2009-03-07
forum: Security
---

### Post by joshaman on 2009-03-07
Does ufw use the settings I set in Firestarter when Firestarter itself is not running?

/Josh

---

### Post by bapoumba on 2009-03-08
test

---

### Post by lovinglinux on 2009-03-08
No. firestarter and ufw are firewall managers, which means they are not actually the firewall. When you configure an option on those managers, they introduce rules to the real firewall controller which is iptables. Usually when you start firewall managers like firestarter, they clean up the iptables rules. So if you start ufw after firestarter, it will override firestarter rules with it's own rules.

But, if you use only firestarter fr example, then your firewall rules will work even if you close the GUI.

You should use one or the other. If you use both, there is a huge chance that you experience conflicts.

---

### Post by Nepherte on 2009-03-08
No.

---

### Post by joshaman on 2009-03-08
Oh, my mistake - I was under the impression that ufw was the core firewall.  Still you answered the question I intended to ask.

Do you know of a firewall tool that allows specific port configuration for individual programs?

---

### Post by scottuss on 2009-03-08
Yes, Firestarter will allow you to specify different rules for outgoing connections. I think that's what you wanted isn't it?

Just look on the policy tab and check that out.

---

### Post by lovinglinux on 2009-03-08
> **scottuss said:**
> Yes, Firestarter will allow you to specify different rules for outgoing connections. I think that's what you wanted isn't it?

Just look on the policy tab and check that out.

No. What he wants is not just port rules, but port+application rules like several firewall applications for Windows work, which iptables is not capable (as far as I know).

[TuxGuardian]("http://tuxguardian.sourceforge.net/") can limit network access based on application, but it's last update was april 8th 2006. Not recommended.

I think ufw will support this kind of feature in the future.

---

### Post by wangsuda on 2009-03-08
> **lovinglinux said:**
> 

I think ufw will support this kind of feature in the future.UFW supports it now.

---

### Post by joshaman on 2009-03-08
I did that.  Maybe you can help me - I want to allow outgoing traffic for only Firefox 3.0.7 on ports 443 and 80.  

I tried entering what I thought was the host of the executable however no dice.

edit: whoops, late post - so iptables is not capable?  I checked ufw and it seemed to allow rules for specific programs (e.g. Transmission) yet I think the rule was universally applied.  I could be wrong.

---

### Post by lovinglinux on 2009-03-08
> **wangsuda said:**
> UFW supports it now.

So they already providing this feature. Good to know.

Anyone has tried it? Does it work as expected?

---

### Post by wangsuda on 2009-03-08
> **lovinglinux said:**
> So they already providing this feature. Good to know.

Anyone has tried it? Does it work as expected?

I don't know, as I block everything. Sorry I cannot be more help.

---

### Post by scottuss on 2009-03-08
Oh right. I'm not really sure why a home user would want this. Surely if you don't want a program to access the Internet, don't use it :S

It's not like Linux apps are like Windows ones, i.e calling home every 2 minutes for no reason.

---

### Post by joshaman on 2009-03-08
> **scottuss said:**
> Oh right. I'm not really sure why a home user would want this. Surely if you don't want a program to access the Internet, don't use it :S

It's not like Linux apps are like Windows ones, i.e calling home every 2 minutes for no reason.Opinions like this are really turning me off to Linux.  Almost every answer I search for is questioned in the form of semantics.

---

### Post by scottuss on 2009-03-08
> **joshaman said:**
> Opinions like this are really turning me off to Linux.  Almost every answer I search for is questioned in the form of semantics.

Fair enough, but perhaps if you bring too much of a Windows mind set to Linux this is where problems arise. I admit that I do not know the exact context of your situation, but I was merely stating that unless you have some specific reason to limit the applications in this way, you don't need to do it. And if you do think you need to, I would expect you know how to do it. I don't want to sound elitist, but sometimes you don't actually need to do what you think you may.

This is particularly true when migrating from Windows to Linux. Such examples are anti-virus, malware tools, firewalls etc etc. I only say what I do to help, believe it or not!

---

### Post by lovinglinux on 2009-03-08
> **joshaman said:**
> Opinions like this are really turning me off to Linux.  Almost every answer I search for is questioned in the form of semantics.

He has a point. When I switched from to Linux, about 6 months ago, I was very uncomfortable with the lack o application based firewalls in Ubuntu. I was a Comodo firewall user before, so I had a lot of control over which, how and when applications could connect to network. But this was necessary because I used to install a lot of applications from any kind of source. The Linux mindset is different and I am very comfortable with it now.

---

### Post by hyper_ch on 2009-03-08
in most cases you don't need to alter the firewall in your linux install. if you're behind a NAT router then disable UPnP and set restrictions there.

---

### Post by scottuss on 2009-03-08
> **hyper_ch said:**
> in most cases you don't need to alter the firewall in your linux install. if you're behind a NAT router then disable UPnP and set restrictions there.


Exactly! :D

---

### Post by joshaman on 2009-03-08
I suppose you're right, scottuss.  I'm gonna stick with Firestarter and forget outbound application filtering.

---

### Post by joshaman on 2009-03-08
Removed

---

### Post by hyper_ch on 2009-03-08
have a look at your router config

---

### Post by joshaman on 2009-03-08
> **hyper_ch said:**
> have a look at your router config
I figured there was a software method.

---

### Post by scottuss on 2009-03-08
> **joshaman said:**
> I figured there was a software method.


If log into your router, depending on what brand you have there will be an option to disable it. On my Netgear one it has it's own option near the bottom of the menu on the left hand side. On my Belkin it is under System Settings, again near the bottom of the menu. Of course, yours may be different depending on brand / firmware.

---

### Post by joshaman on 2009-03-08
Right - I know where it is.  I like to keep it enabled for some of my other computers.

---

### Post by bodhi.zazen on 2009-03-09
> **scottuss said:**
> Fair enough, but perhaps if you bring too much of a Windows mind set to Linux this is where problems arise. I admit that I do not know the exact context of your situation, but I was merely stating that unless you have some specific reason to limit the applications in this way, you don't need to do it. And if you do think you need to, I would expect you know how to do it. I don't want to sound elitist, but sometimes you don't actually need to do what you think you may.

This is particularly true when migrating from Windows to Linux. Such examples are anti-virus, malware tools, firewalls etc etc. I only say what I do to help, believe it or not!

Well said =D>

@joshaman The question is what do you want to use a firewall for exactly ?

If you are new to Linux I suggest you take a look at this thread :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

Back on topic, with your firewall rules, you want to block the destination port (port 80 is on the server, on the client it will be a higher pseudorandom port).

---

### Post by scottuss on 2009-03-09
> **joshaman said:**
> Right - I know where it is.  I like to keep it enabled for some of my other computers.

Oh sorry I thought you wanted to disable it? Upnp runs as a service only on Windows, so there is no need to disable anything like that on Linux. 

Also, remember that having upnp enabled on your router is a security issue if Windows boxes are connected to it. Just a thought...

---

### Post by joshaman on 2009-03-09
> **scottuss said:**
> Upnp runs as a service only on Windows, so there is no need to disable anything like that on Linux.Oh I see, thanks.

---

### Post by joshaman on 2009-03-09
> **bodhi.zazen said:**
> @joshaman The question is what do you want to use a firewall for exactly ?Well I'd like to monitor all inbound/outbound activity by use of a firewall similar to Comodo or ZoneAlarm.  This way I would be alerted to any activity, whatsoever, in real-time, and could choose to allow or disallow it, while creating a custom policy for each application.  But I learned there's no current software for Linux that can do this.  I realize now that Linux is mostly malware-free, however I still like this method of controlling connectivity.  It keeps me aware of my programs and all connections, regardless of malware.  However I can accept that I can't do this, and don't really mind allowing all outbound activity and blocking all inbound activity.
> If you are new to Linux I suggest you take a look at this thread :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")thanks, i read the Spyware and Firewall parts when I first installed Ubuntu, but I'll have to read it completely later.> Back on topic, with your firewall rules, you want to block the destination port (port 80 is on the server, on the client it will be a higher pseudorandom port).I don't understand, can you explain?

---

### Post by hyper_ch on 2009-03-09
why would you need that? There's not much reason for a tool like zonealarm. Things on linux don't call home.

If you don't trust the repositories then audit the source code yourself and compile it yourself. If you trust the repositories then there's nothing in there that would trigger ZoneAlarm or Comodo under normal circumstances.

---

### Post by joshaman on 2009-03-09
> **hyper_ch said:**
> why would you need that? There's not much reason for a tool like zonealarm. Things on linux don't call home.

If you don't trust the repositories then audit the source code yourself and compile it yourself. If you trust the repositories then there's nothing in there that would trigger ZoneAlarm or Comodo under normal circumstances.omg...  options are options for a reason.  they're optional.  don't be so close-minded.

---

### Post by hyper_ch on 2009-03-09
> **joshaman said:**
> omg...  options are options for a reason.  they're optional.  don't be so close-minded.
don't be so close-minded in your windows thinking ;)
you know, it's not that nobody in linux ever thought "hey, we need a nice cute firewall tool like windows with flashy buttons and lots and lots of warn messages so the end-user thinks he's safe"... did you consider that you are safe without that?

---

### Post by joshaman on 2009-03-09
> **hyper_ch said:**
> don't be so close-minded in your windows thinking ;)
you know, it's not that nobody in linux ever thought "hey, we need a nice cute firewall tool like windows with flashy buttons and lots and lots of warn messages so the end-user thinks he's safe"... did you consider that you are safe without that?Pick a number :):

1. You're saying I'm safe without those flashy buttons and warning messages?  But I thought those flashy programs know exactly how to keep my computer safe! 8-[ 

2. You're really getting off-topic.  And you're exaggerating.  You're also implying that I'm too dumb to think for myself.  I assure you, you're wrong. ;)

---

### Post by bodhi.zazen on 2009-03-09
both #1 and #2 , we want you to think outside the old box.

Security is a complex subject, even on Windows. So much so people buy things that tell them they are safe.

We are trying to encourage you to look under the hood of you new OS and see for yourself you are safe. Just keep reading and learning.

---

### Post by joshaman on 2009-03-09
> **bodhi.zazen said:**
> both #1 and #2 , we want you to think outside the old box.

Security is a complex subject, even on Windows. So much so people buy things that tell them they are safe.

We are trying to encourage you to look under the hood of you new OS and see for yourself you are safe. Just keep reading and learning.OK.

I guess I am being a bit close-minded.  apologies.

---

### Post by Turpin on 2010-01-18
{Sigh} I want to block specific applications.  Do we have such a firewall available for Linux yet? I use Wine.  I like some software. I want the ability to block specific apps.  There is my statement.  Resistence is futile.  All I want is a valid suggestion of software that will work for this, not to carry on this debate.  You're a community.  Okay, I'm also part of that community I suppose.  But more importantly, I'm an individual.  I want certain things.  My reasons are my own, but c'mon, who doesn't want full easy control of individual applications?  And why is there an argument against wanting such a thing???  I'm talking about easy complete control and monitoring of all network traffic based on addresses, IPs, incoming, outgoing, APPLICATIONS..  Yeah.  Why not?  Because we're as a community watching every application supported by Linux for weird behavior?  Okay. I get that.  I want to run OTHER things.  But besides that fact, I want the ability to limit whatever however whyever I may want to limit it on MY COMPUTER (you can do what you like on yours). Nay, I require it.  And I view the intentions of anyone who tries to talk myself or others out of that point of view with EXTREME SUSPICION. Why would anyone not want us to have this power and control over what information leaves our own computers and reports out to who-knows-where with who-knows-what encrypted information packets? I think I've repeated myself enough here.  If someone still doesn't get it, ... A wise man once said "I'm into freedom of speech, and freedom of choice. I'm the kinda guy that likes to sit in a greasy spoon and wonder, "Gee, should I have the T-bone steak or the jumbo rack of barbecue ribs with the side-order of gravy fries?" I want high cholesterol! I wanna eat bacon, and butter, and buckets of cheese, okay?! I wanna smoke a Cuban cigar the size of Cincinnati in the non-smoking section! I wanna run naked through the street, with green Jell-O all over my body, reading Playboy magazine. Why? Because I suddenly may feel the need to, okay, pal?" Okay, maybe he wasn't that wise...  Actually he was more of an anarchist...  Oh well. My point is, there are those who let their operating system decide for them what they are allowed and not allowed to do, and then there is me.  Hello. And I want to control which applications connect out and in what way, and with a certain ease of control I used to have with Sygate Personal Firewall.  And here we go...  I already feel the argument coming, Yes I know, Sygate was a discontinued product, and yes I know there is traffic in Windows going on that no firewall will inform us of or filter fully and accurately.  Open source and the inherent verifiability is why I use Linux.  But I want to use software, such as games.  Windows games.  Certain windows games that aren't on Linux.  Because I like them. Because they appeal to me in ways that other Windows games and games on Linux don't.  Because I grew up in....  My reasons are my own, okay? Okay.
Do we have such a firewall available for Linux yet?  The closest I've found is linux-firewall.org, a closed-source which I haven't gotten to run right on anything past hardy for some reason.

---

### Post by wangsuda on 2010-01-18
> **Turpin said:**
> {Sigh} I want to block specific applications.  I use Wine.  I like some software. I want it.  There is my statement.  Resistence is futile.  All I want is a valid suggestion of software that will work for this, not to carry on this debate.  You're a community.  Okay, I'm also part of that community I suppose.  But more importantly, I'm an individual.  I want certain things.  My reasons are my own, but c'mon, who doesn't want full easy control of individual applications?  And why is there an argument against wanting such a thing???  I'm talking about easy complete control and monitoring of all network traffic based on addresses, IPs, incoming, outgoing, APPLICATIONS..  Yeah.  Why not?  Because we're as a community watching every application supported by Linux for weird behavior?  Okay. I get that.  I want to run OTHER things.  But besides that fact, I want the ability to limit whatever however whyever I may want to limit it on MY COMPUTER (you can do what you like on yours). Nay, I require it.  I think I've repeated myself enough here.  If someone still doesn't get it, ... A wise man once said "I like to read. I'm into freedom of speech, and freedom of choice. I'm the kinda guy that likes to sit in a greasy spoon and wonder, "Gee, should I have the T-bone steak or the jumbo rack of barbecue ribs with the side-order of gravy fries?" I want high cholesterol! I wanna eat bacon, and butter, and buckets of cheese, okay?! I wanna smoke a Cuban cigar the size of Cincinnati in the non-smoking section! I wanna run naked through the street, with green Jell-O all over my body, reading Playboy magazine. Why? Because I suddenly may feel the need to, okay, pal?"

You want all that? OK, this is simple. Download Gufw 9.10.4 from Synaptic and configure it for the IPs, programs, and whatnot you want to allow and disallow. It's that easy.

---

### Post by Turpin on 2010-01-18
Very cool.  I'm impressed to see the application-specific rule ability in there.  It must be a new feature because the last time I looked at that about a year ago I don't remember reading any serious talk of putting that feature in gufw. So far I haven't found how to add applications to the list, which right now for me only seems to have Transmission listed, but if it's figure-out-able, I'll figure it out.  Thanks for pointing that out.  I'm so happy I think I might run through the street naked.  :D

---

### Post by bodhi.zazen on 2010-01-18
> **Turpin said:**
> {Sigh} I want to block specific applications.  Do we have such a firewall available for Linux yet? 


No this is NOT POSSIBLE EASILY with Linux.

UFW / GUFW may use names of servers, such as apache, but iptables is port specific.

So you can block a specific application that uses a specific port, such as MSN.

But you can not block port 80 for firefox but allow Opera to connect to port 80.

[http://www.linux.com/archive/feature/121374](http://www.linux.com/archive/feature/121374)

[http://l7-filter.sourceforge.net/](http://l7-filter.sourceforge.net/)

---

### Post by pakki on 2010-04-16
GUFW sucks for those who are addicted o win firewall applications 
solution is 
[http://linux-firewall.org/linux-firewall.org_i386.deb](http://linux-firewall.org/linux-firewall.org_i386.deb)

---

### Post by Helkaluin on 2010-04-16
> **pakki said:**
> GUFW sucks for those who are addicted o win firewall applications 
solution is 
[http://linux-firewall.org/linux-firewall.org_i386.deb](http://linux-firewall.org/linux-firewall.org_i386.deb)

Is it just me or do I read from the lfwsetup file in the package that it mess with your sudoer file?

Looks dodgy to me...

---

### Post by bodhi.zazen on 2010-04-16
> **pakki said:**
> GUFW sucks for those who are addicted o win firewall applications 
solution is 
[http://linux-firewall.org/linux-firewall.org_i386.deb](http://linux-firewall.org/linux-firewall.org_i386.deb)

Thank you for the link, looks interesting.

FYI, these are different tools for different tasks, GUFW manages iptables, the application you linked is at an application level.

The default equivalent in Ubuntu is apparmor.

---

### Post by bodhi.zazen on 2010-04-16
> **pakki said:**
> GUFW sucks for those who are addicted o win firewall applications 
solution is 
[http://linux-firewall.org/linux-firewall.org_i386.deb](http://linux-firewall.org/linux-firewall.org_i386.deb)

Out of interest I tried the application. It looks interesting, but is not working on lucid.

The main panel opens , but there are no programs listed in the programs tab and no way to add a program (the add program buttons are missing).

The project looks promising, will watch to see if they fix the issues and / or release a 64 bit version.

---

### Post by cariboo on 2010-04-16
From the looks of it, lfwsetup, does try to change your /etc/sudoers file:

```
#!/usr/bin/perl
if(open(FILE,"</etc/sudoers"))
{
   foreach(<FILE>)
   {
      if ($_ =~ /linux-firewall/)
      {
         $gefunden="ja";
      }
   }
   close FILE;
   unless($gefunden eq "ja")
   {
      if(open(FILE,">>/etc/sudoers"))
      {
         print FILE "\nALL ALL= NOPASSWD: /usr/bin/linux-firewall.org\n";
         close FILE;
      }
      else
      {
         print "Could not write to the file\n";
      }
   }
}
else
{
   print "Could not read the file\n";
}
```

This thing has my spidey senses tingling, it really doesn't have a license, just that you aren't allowed to copy it. Plus the author really has no presence on google.

---

### Post by uRock on 2010-04-16
> **cariboo907 said:**
> From the looks of it, lfwsetup, does try to change your /etc/sudoers file:
I don't like the thought of something making those changes. Between UFW, Ninja, and AppArmor, I think my system is plenty safe from those folks on the other side of my router.

---

### Post by bodhi.zazen on 2010-04-17
> **cariboo907 said:**
> From the looks of it, lfwsetup, does try to change your /etc/sudoers file:

```
#!/usr/bin/perl
if(open(FILE,"</etc/sudoers"))
{
   foreach(<FILE>)
   {
      if ($_ =~ /linux-firewall/)
      {
         $gefunden="ja";
      }
   }
   close FILE;
   unless($gefunden eq "ja")
   {
      if(open(FILE,">>/etc/sudoers"))
      {
         print FILE "\nALL ALL= NOPASSWD: /usr/bin/linux-firewall.org\n";
         close FILE;
      }
      else
      {
         print "Could not write to the file\n";
      }
   }
}
else
{
   print "Could not read the file\n";
}
```This thing has my spidey senses tingling, it really doesn't have a license, just that you aren't allowed to copy it. Plus the author really has no presence on google.

The name of the application sets off my spider sense "linux-firwall.org"

Hard to say which is worse, "firewall", which it is not, or ".org" in the name of an application ?

:lolflag:

I tried it in a VM and the idea will certainly be popular with some.

+1 on ufw + apparmor + ninja

---

### Post by OpSecShellshock on 2010-04-17
I wonder if it might not be a good idea for someone to edit all the links to the application so they don't point directly to the .deb? It seems to me that there are a lot of new users lately, many coming off of a long Windows history and thinking they need a firewall with a comfortable interface and which tells them when connection attempts are being prevented (which I'd argue provides no benefit to the end user, but it takes time to adjust).

However, rather than linking to the site where they can read up on the application, the links in this thread go right to the installation file which, as noted above, alters the sudoers file during installation and presumably runs with administrative privileges immediately at startup. Considering that many new users will look for "security" applications to install first, and then will seek to inform themselves about what the security concerns really are only after that's done, they might just go ahead and install it as soon as it comes up.

---

### Post by Helkaluin on 2010-04-17
I don't quite understand. The .desktop launchers seem to include sudo in their exec lines, and so the author for some reason entered them into sudoers without password.

But the 'linux-firewall.org' seems only to be a Gambas GUI. What lies behind is the lfwdaemon.

What's ironic is that the 'linux-firewall.org' and 'lfwloader' clearly prints 'freeware'.

```
# Gambas Project File 2.0
Title=lfwloader
Startup=MMain
Version=0.0.31
TabSize=2
ExecPath=/home/rmg/firewall2/pakete/usr/bin/lfwloader.gambas
Maintainer=Ren  -Maxime Gracien
Vendor=Ren  -Maxime Gracien
Address=rm@gracien.de
License=Freeware
```

Meh. 3rd-party, no source (well, at least nowhere to be found on their website), and modifies your sudoers. Better not touch it.

---

### Post by ubutu on 2010-04-25
> **bodhi.zazen said:**
> No this is NOT POSSIBLE EASILY with Linux.

UFW / GUFW may use names of servers, such as apache, but iptables is port specific.

So you can block a specific application that uses a specific port, such as MSN.

But you can not block port 80 for firefox but allow Opera to connect to port 80.
[]("http://l7-filter.sourceforge.net/")

Then anyone can write a script then convince me to run it as root (Since I don't know much about linux, quite easy), the script then connects via port 80 to the internet and does whatever it wants.
 I've read there's no such thing as malware on linux, then what do I call a script written by a malicious coder?

---

### Post by uRock on 2010-04-25
> **ubutu said:**
> Then anyone can write a script then convince me to run it as root (Since I don't know much about linux, quite easy), the script then connects via port 80 to the internet and does whatever it wants.
 I've read there's no such thing as malware on linux, then what do I call a script written by a malicious coder?

Call it "operator error," because you shouldn't run code if you do not know what it does. In these forums most people write a description of what the command does and if someone else sees it and reports it as being harmful, then the moderators will remove it. If you are not sure that someone's commands are legit, then ask for a GUI way or an explanation of the commands. Again, people here will report bad commands if they are seen.

---

### Post by bodhi.zazen on 2010-04-25
> **ubutu said:**
> Then anyone can write a script then convince me to run it as root (Since I don't know much about linux, quite easy), the script then connects via port 80 to the internet and does whatever it wants.

That is true of any OS.

> I've read there's no such thing as malware on linux, then what do I call a script written by a malicious coder?

First nobody claimed there was no such thing as malware on Linux.

I can think of a few terms, self destructive ? social engineering perhaps would be the best general term.

---

### Post by ubutu on 2010-04-25
Ok. 
How to configure ubuntu to first verify with me before allowing OUTBOUND/inbound traffic of any application on the system?

---

### Post by bodhi.zazen on 2010-04-25
> **ubutu said:**
> Ok. 
How to configure ubuntu to first verify with me before allowing OUTBOUND/inbound traffic of any application on the system?

Linux does not do allow / deny network traffic per application.

---

### Post by Byb on 2010-04-26
> **ubutu said:**
> Ok. 
How to configure ubuntu to first verify with me before allowing OUTBOUND/inbound traffic of any application on the system?
Just unplug the network cable after dl'ing the ISO :P
I seem to joke but I agree with you. I'd say it differntly than the one who wanna run naked in the street, but the result is the same: for the ones that not only are concerned by security AND aren't able to decrypt sources (in this case, no need to evoque the ability to write their own, neither compile anything), a pop-up/warning/self-learning app-aware firewall would be ... say a step in feeling secure. Any other advises are from the ones who fluently speak binany language AND have a realtime updated security database in their head filled with app-srcport-destip-dstport records.
The problem for a mid way is that allowing say firefox for outbound ports would be a silly huge burden that will drive users to Allow-All just before the end of their first browsing hour.
In fact the problem is confidence: maybe there would be a RSOD (red screen of death) warning notifying that installing a out-of-std-depos will break your ubuntu warraty... if ubuntu went in your box with a 100% security warranty label (hope that kind of foolish things won't never exist, but I can hear that more and more people nowadays think they can wish them and don't care/see they ask for totalitarism at the same time) ...and not "as-is" as it is.
Even embedded security features in firefox (antifishing) or plugins rely on the confidence you grant to the one that coded them.

Although, what to do with this security basis sentence: everything not-allowed is forbidden? Just hear it and forget it: there is no place in this binary alternative for un-knowledge, when this last is **required** to human beings. Even for me it's hard to say and moreover harder to admit, but I think it's true.

Another problem is the time.... ???? : what you now flag as safe, will it always remain so, when you have forgot this rule in your firewall conf, say just in one or two monthes (just to be friendly, but I could have say one or two minutes) ?  

:popcorn:

---

