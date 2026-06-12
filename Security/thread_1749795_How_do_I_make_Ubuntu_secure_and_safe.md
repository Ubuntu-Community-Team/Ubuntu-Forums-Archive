---
title: "How do I make Ubuntu secure and safe?"
date: 2011-05-04
forum: Security
---

### Post by 0Io1 on 2011-05-04
I understand Ubuntu is safe out of the box, being extremely limited and unlikely to get any virus, spyware, adware, worms, etc.

But what can I do myself, to make it more secure and safe? Do I do nothing? Do I need to install a firewall? Virus scanner? Anything?

Thanks.

---

### Post by collisionystm on 2011-05-04
> **0Io1 said:**
> I understand Ubuntu is safe out of the box, being extremely limited and unlikely to get any virus, spyware, adware, worms, etc.

But what can I do myself, to make it more secure and safe? Do I do nothing? Do I need to install a firewall? Virus scanner? Anything?

Thanks.

Install a firewall. Open software center, install gufw. Run gufw and set to enable.

---

### Post by collisionystm on 2011-05-04
For antivirus, there is clamav, avast and eset-nod 32. < --- my favorite.

---

### Post by Rasa1111 on 2011-05-04
You're actually very safe as it is.
But if you'd feel better with a firewall on,
you can just turn on the one that comes with Ubuntu.

After using windows for soo long, (been on ubuntu for a year)
I still feel safer with my firewall on, even though i know I dont need it, and even though many pros tell me I don't even have to bother with it. I still keep it on. lol

If you want a simple GUI to configure your firewall, install "gufw"
You can find it in software center, or synaptic. (just type GUFW in the search bar)

Or you can simply put 
> **sudo ufw enable**in a terminal to turn the firewall on. 

Here is some documentation on it..
[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

If you install GUFW, you can find it under System>Admin>Firewall Config. once installed.
 Then just open it, Click the "enabled" box, and it's on.

I have not used any other kind of security software for the 1year+5months Ive used Ubuntu..
and have never seen my computers run better! :)


 if you want a simple virus scanner, you can install "ClamTK".
Which will scan any files you tell it to, for viruses. 
Mostly for sharing files with windows PC's. 

 But to answer your Q: simply..
No you don't *need* to do anything, except use common sense and don;t run sketchy , random commands or packages from the web. :)

Hope this helps.

---

### Post by HermanAB on 2011-05-05
Hmm, well, if you still have to ask, then it is likely best that you do nothing...

Eventually, in a few months, you will catch on to things and will have read a lot of howtos and man pages and you will know what to do.

---

### Post by wilee-nilee on 2011-05-05
> **collisionystm said:**
> For antivirus, there is **eset-nod 32**. < --- my favorite.

Is there a free version.

---

### Post by collisionystm on 2011-05-05
There used to be a beta version that was free... let me look for you.

As for these comments about not needing a firewall, please ignore them. You DO need a firewall. Unless you want some clown to ssh to your computer... Like I said, install GUFW or FIRESTARTER.

By Default Ubuntu allows all traffic in and out. This is NOT SAFE.

Hence the use of a firewall. I do not understand why Ubuntu does not come with one Default. Linux Mint and Fedora do.

---

### Post by spynappels on 2011-05-05
> **collisionystm said:**
> There used to be a beta version that was free... let me look for you.

As for these comments about not needing a firewall, please ignore them. You DO need a firewall. Unless you want some clown to ssh to your computer... Like I said, install GUFW or FIRESTARTER.

By Default Ubuntu allows all traffic in and out. This is NOT SAFE.

Hence the use of a firewall. I do not understand why Ubuntu does not come with one Default. Linux Mint and Fedora do.

Because Ubuntu Desktop does not come with any listening services by default, so there is no inbound traffic other than that requested by the OS/User. If any listening services are started, then yes, a firewall is a good idea. 

Some clown can only ssh to your computer if you have the ssh server daemon running, which Ubuntu desktop does not have BY DEFAULT.

Oh, and Firestarter is no longer being maintained, so it may be better to stick with UFW/GUFW or using IPTables directly if you do want to run a firewall.

---

### Post by Baumbart on 2011-05-05
> **0Io1 said:**
> But what can I do myself, to make it more secure and safe? Do I do nothing? Do I need to install a firewall? Virus scanner? Anything?

You should keep an eye on your ports to the internet and the software listening there.
Maybe you want to isolate programs with internet-connection into a user-sub-group (although that's a bit tricky).

The less software you install, the better. There are some things you'll need but in terms of security, sowtware is never a solution but **always a compromise between security and comfort**.

Never act on what some people in a forum recommend. Of course that includes my own recommendations as well.
Instead inform yourself from the many great sources and resources out there.
For example the Ubuntu-Wiki or the Electronic Frontier Foundation, just to name two of them.

Read all you can grab about a software you use! Especially the terms and conditions.

---

### Post by bodhi.zazen on 2011-05-05
> **0Io1 said:**
> How do I make Ubuntu secure and safe?

Out of the box, Ubuntu is safe and secure.

If you wish to harden the OS, start with the security sticky.

The (short) list would be:

1. Enable your firewall,. Not necessary if you are behind a router (UPnP should be disabled on your router).

```
sudo ufw enable
```

2. Enable apparmor (see the apparmor sticky).

3. Secure your browser (noscript).

4. Do not use VNC.

5. Do not install software (from outside the repositories) you do not trust.

6. Do now fall victim to social engineering or Phishing.

---

### Post by 0Io1 on 2011-05-05
> **collisionystm said:**
> Install a firewall. Open software center, install gufw. Run gufw and set to enable.

I can't seem to keep the firewall enabled. I press enable, it works, but when I restart the computer, I have to enable it again.

How do I keep it enabled?

---

### Post by Soul-Sing on 2011-05-05
> **0Io1 said:**
> I can't seem to keep the firewall enabled. I press enable, it works, but when I restart the computer, I have to enable it again.

How do I keep it enabled?

try
```
sudo ufw status
```
what is the outcome?

when accessing gufw you have to open the prog with sudo/passwd.
if it still disabled
: ```
sudo apt-get purge gufw
```
  ```
sudo apt-get install gufw 
```
enable it, reboot, and open gufw again.

---

### Post by bodhi.zazen on 2011-05-05
> **0Io1 said:**
> I can't seem to keep the firewall enabled. I press enable, it works, but when I restart the computer, I have to enable it again.

How do I keep it enabled?

Do you have another firewall tool installed (such as firestarter) ?

---

### Post by 0Io1 on 2011-05-05
> **bodhi.zazen said:**
> Do you have another firewall tool installed (such as firestarter) ?

Yes.

---

### Post by bodhi.zazen on 2011-05-05
> **0Io1 said:**
> Yes.

Well that is the problem then. These graphical tools are all designed to configure iptables and when you have more then one they conflict. Choose one and remove (purge) the other(s).

```
sudo apt-get purge firestarter
```

Then ufw / gufw will work.

As a side note, I hope you understand, this is not windows and by default there are no significant open ports, so, unlike windows, there is nothing to firewall.

For the vas majority of desktop users you do not need a firewall, and the vast majority of the time if you so desire there is a one time command to run a terminal:

```
sudo ufw enable
```

That is all that is required, no need for gufw.

---

### Post by Rasa1111 on 2011-05-05
yeah don't use firestarter.
it's not even maintained anymore. 

it'd be best to just remove it and use Ubuntus built in firewall.
(as a few of us have mentioned)

And please ignore [this post]("http://ubuntuforums.org/showpost.php?p=10772515&postcount=7")

Bodhi.Zazen knows what he's talking about. 
and knows it well. ;)

---

### Post by PeaceOcean on 2011-05-07
First of all, I am a newbie. do not laugh at me. I turned on the ufw/iptable by punching "$ sudo ufw enable". And then I did "$ sudo ufw default deny". from "$ sudo ufw status verbose", I can see 
"Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip".

I am wondering what exactly the "deny" influences and what exactly it means. when doing internet browsing, the TCP/UDP/HTTP have outgoing packets to the remote servers. However, my computer also receives incoming traffic from those web servers. Why my computer can still doing internet browsing? are there any more steps I need to do for this security set up? clamav is necessary?

thx

---

### Post by bodhi.zazen on 2011-05-08
1. There are no known active viruses for Linux, so nothing to scan for.

2. The answer to your question about your firewall requires you understand TCP/IP protocols.

The default settings are:

1. The firewall allows all outgoing traffic.

2. The firewall blocks all incoming NEW traffic.

3. The firewall allows all incoming ESTABLISHED traffic. This is the response to any requests you made to any (web) servers.

By default there are no listening servers of any significance, so there is nothing to firewall.

It sounds as if you are new to Ubuntu from windows.

Linux security is NOT the same as windows ;)

Read the security sticky ;)

---

### Post by Lars Noodén on 2011-05-08
> **bodhi.zazen said:**
> 
2. The answer to your question about your firewall requires you understand TCP/IP protocols.


To get an overview of TCP/IP, see in RFC 793 the [list of connection states](http://tools.ietf.org/html/rfc793#section-3.2) and Figure 6 below the states.

---

### Post by farmerjohn73 on 2011-05-10
Hi all,

I have avg installed, does it protect me from viruses and malware properly?

Nod32 is not free, I couldnt install avast, the installation was painful but gui didnt work.  I didn't find any other free antimalwares which are good.

I will study the apparmour sticky and configure it.

---

### Post by bodhi.zazen on 2011-05-10
> **farmerjohn73 said:**
> Hi all,

I have avg installed, does it protect me from viruses and malware properly?

Nod32 is not free, I couldnt install avast, the installation was painful but gui didnt work.  I didn't find any other free antimalwares which are good.

I will study the apparmour sticky and configure it.

As there are no known active viruses for Linux, antivirus is not needed for the average Desktop user. What makes you think you need antivirus ?

Linux is not windows and you should start by reading the security sticky.

---

### Post by Ghost|BTFH on 2011-05-10
Best ways to secure Ubuntu after installation.

Step 1: Learn the golden rule not to install anything from outside the repositories.

Step 2: Re-read step 1 until it sinks in.

Step 3: You may wish to also tattoo step 1 onto your forehead, in reverse, so you can read it easily in the mirror.

Step 4: Once step 1 is secured, install the addon - Adblock Plus in Firefox.  Select EasyList after restarting Firefox.

Step 5: Enjoy a pretty secure system.

Cheers,
Ghost|BTFH

---

### Post by farmerjohn73 on 2011-05-12
> **bodhi.zazen said:**
> As there are no known active viruses for Linux, antivirus is not needed for the average Desktop user. What makes you think you need antivirus ?

Linux is not windows and you should start by reading the security sticky.

I am dumb noob to ubuntu. When I executed this on command line:

sudo /etc/init.d/apparmor status

I got this :

apparmor module is loaded.
10 profiles are loaded.
10 profiles are in enforce mode.
   /sbin/dhclient3
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-thumbnailer
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/sbin/cupsd
   /usr/sbin/tcpdump
   /usr/share/gdm/guest-session/Xsession
0 profiles are in complain mode.
2 processes have profiles defined.
2 processes are in enforce mode :
   /sbin/dhclient3 (1486) 
   /usr/sbin/cupsd (1265) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.
-----
     These seem to be default profiles, Are they enough for an average internet browser like me?  I read the sticky on apparmor but I can't make any profiles myself 'coz I don't know the coding.  As I am a dumb noob,  I can't make and add profiles.

I am a little afraid coz, recently my wordpress login has been compromised by a hacker and I never accessed that from windows.

What should I do?  But I love this OS.

Thanks a lot.

---

### Post by 3602 on 2011-05-12
Ubuntu-Tweak PPAs are fine...

---

### Post by Larkspur on 2011-05-12
> **farmerjohn73 said:**
> Are they enough for an average internet  browser like me?  I read the sticky on apparmor but I can't make any  profiles myself 'coz I don't know the coding.  As I am a dumb noob,  I  can't make and add profiles.

I am a little afraid coz, recently my wordpress login has been compromised by a hacker and I never accessed that from windows.

What should I do?  But I love this OS.

Thanks a lot.


If you use Firefox, you should enter this into the terminal:

```
sudo aa-enforce firefox
```Though aa-status doesn't list it - for some reason - there is a profile  for firefox already installed.  You can get more if you install the  apparmor-profiles package through synaptic, including one for  Chrom(ium).  I'd also recommend that you install the apparmor-notify  package, since it lets you know when a program with an enforced profile  has tried to do something the profile forbids.  You don't have to, you  can check the logs (kernel I think) in Log File Viewer.

(Don't worry if you get a message: it's not necessarily a sign of  anything untoward.  The profiles included with apparmor try to balance  safety with allowing most users to use a program the way they want, but  the profile writers can't cater for everyone.  A refusal message from  apparmor generally means you're using the program in an unexpected way).

I agree with you that apparmor is very off-putting: the basics of  language itself is not too hard if you're used to using the terminal  (all a profile boils down to is defining a path or location and telling  apparmor what the program being profiled is allowed to do there) but  using it to its fullest depends on a deep knowledge of what the various  parts of Ubuntu do, whether and how they can be exploited (i.e. there's  no point writing a profile that, by giving a certain permission in a  certain folder, allows the program to run unconfined) what alternatives  there are and so on.  Also, you need to be something of a programmer to  "debug" a profile (since a single profile actually includes many  others).  Then again, it's designed for server admins, not the likes of  us.  The default profiles are perfectly good in most situations.

But anyway, the tl;dr version of this is: install apparmor-profiles,  activate the profiles for the programs you use, and you'll be safe.


Now, regarding your problem with your wordpress account: how do you  mean, "compromized"?  To know if Ubuntu was to blame, you'll have to go into  more detail: how did you store your passwords?  How did you enter them?   Did you use computers other than your own to access the account?  Has anyone been present when you accessed the account?  What leads you to believe it was hacked in the first place?

---

### Post by lmn. on 2011-05-12
I have installed;

Firestarter & gufw
Clam
Lynis & Tiger auditing tools


any thoughts on
[http://tanaya.net/BullDog/index.shtml]("http://tanaya.net/BullDog/index.shtml") ??

*[FONT="Courier New"][SIZE="2"]updated: Tuesday, October 18, 2005[/SIZE][/FONT]
it's old that's for sure..

---

### Post by Larkspur on 2011-05-12
> **lmn. said:**
> I have installed;

Firestarter & gufw
Clam
Lynis & Tiger auditing tools


any thoughts on
[http://tanaya.net/BullDog/index.shtml](http://tanaya.net/BullDog/index.shtml) ??

*[FONT=Courier New][SIZE=2]updated: Tuesday, October 18, 2005[/SIZE][/FONT]
it's old that's for sure..

I don't have any opinion on Bulldog, but I'd recommend you uninstall Firestarter; gufw is more simple, adds a bit of "Little Snitch" functionality (you can set it to tell you which programs are accessing the internet) and Firestarter hasn't been updated in a couple of years.  At the very least, pick one firewall: both of them are basically frontends for ufw/iptables, and having two running at the same time can cause conflicts, especially if you start defining rules.

---

### Post by spynappels on 2011-05-12
> **Larkspur said:**
> I don't have any opinion on Bulldog, but I'd recommend you uninstall Firestarter; gufw is more simple, adds a bit of "Little Snitch" functionality (you can set it to tell you which programs are accessing the internet) and Firestarter hasn't been updated in a couple of years.  At the very least, pick one firewall: both of them are basically frontends for ufw/iptables, and having two running at the same time can cause conflicts, especially if you start defining rules.

Definite +1 for the above, you should not use both and of the two, most here would recommend UFW/GUFW for desktop use. Depending on how you installed Firestarter
```
sudo apt-get purge firestarter
```
will get rid of it.

---

### Post by farmerjohn73 on 2011-05-16
> **Larkspur said:**
> If you use Firefox, you should enter this into the terminal:

```
sudo aa-enforce firefox
```Though aa-status doesn't list it - for some reason - there is a profile  for firefox already installed.  You can get more if you install the  apparmor-profiles package through synaptic, including one for  Chrom(ium).  I'd also recommend that you install the apparmor-notify  package, since it lets you know when a program with an enforced profile  has tried to do something the profile forbids.  You don't have to, you  can check the logs (kernel I think) in Log File Viewer.

(Don't worry if you get a message: it's not necessarily a sign of  anything untoward.  The profiles included with apparmor try to balance  safety with allowing most users to use a program the way they want, but  the profile writers can't cater for everyone.  A refusal message from  apparmor generally means you're using the program in an unexpected way).

I agree with you that apparmor is very off-putting: the basics of  language itself is not too hard if you're used to using the terminal  (all a profile boils down to is defining a path or location and telling  apparmor what the program being profiled is allowed to do there) but  using it to its fullest depends on a deep knowledge of what the various  parts of Ubuntu do, whether and how they can be exploited (i.e. there's  no point writing a profile that, by giving a certain permission in a  certain folder, allows the program to run unconfined) what alternatives  there are and so on.  Also, you need to be something of a programmer to  "debug" a profile (since a single profile actually includes many  others).  Then again, it's designed for server admins, not the likes of  us.  The default profiles are perfectly good in most situations.

But anyway, the tl;dr version of this is: install apparmor-profiles,  activate the profiles for the programs you use, and you'll be safe.


Now, regarding your problem with your wordpress account: how do you  mean, "compromized"?  To know if Ubuntu was to blame, you'll have to go into  more detail: how did you store your passwords?  How did you enter them?   Did you use computers other than your own to access the account?  Has anyone been present when you accessed the account?  What leads you to believe it was hacked in the first place?

The hacker logged into my wordpress dashboard and changed one of my pages with his page.  I never logged into my wp dashboard even with my windows partition, nor used any other computer.

I have enforced firefox with the command you showed.  But I could not do that with google chrome.  I installed it with the tar file downloaded from google's site rather than from synaptic package manager.  I wanted to show the path of chrome to apparmor to enforce, but don't know how to do it.

---

