---
title: "Did I get hacked?"
date: 2011-12-18
forum: Security
---

### Post by waterbob on 2011-12-18
Hi, let me explain my problem. 6 months ago I connected my Ubuntu laptop to a wireless network with an infected Windows computer (it had a remote access virus) also connected, anyway I wondering could my Ubuntu laptop have been hacked?

Also, I installed Ubuntu on the infected computer now.

---

### Post by 2F4U on 2011-12-18
How comes you think you have been hacked? Did you exchange data with the infected computer, are you running services which provide access from the outside world? Ubuntu, by default, is pretty secure, since there are no services running with an interface to the outside, i. e. no open ports. Only exception, as far as I know, is CUPS, which listens to the local network only.
Six month is a long time, so many of the log files on your computer are probably no longer available. Else you can look into /var/log/auth.log to see if anybody tried to remotely log in to your machine.

---

### Post by waterbob on 2011-12-18
> **2F4U said:**
> How comes you think you have been hacked? Did you exchange data with the infected computer, are you running services which provide access from the outside world? Ubuntu, by default, is pretty secure, since there are no services running with an interface to the outside, i. e. no open ports. Only exception, as far as I know, is CUPS, which listens to the local network only.
Six month is a long time, so many of the log files on your computer are probably no longer available. Else you can look into /var/log/auth.log to see if anybody tried to remotely log in to your machine.
I am just concerned I might have been hacked as I have banking data on my Laptop.

The only entries on the log are 2 Dec 18th entries.

Have you heard of any Ubuntu user getting hacked by connecting to a wireless network with an infected windows computer on it?

---

### Post by 2F4U on 2011-12-18
No, I haven't heard of this. This doesn't mean that Linux or Ubuntu can't be hacked, any OS can be hacked. But Linux, through its privilege model, makes it much harder for hackers or malicious software, to cause harm to the computer.
If someone tries to get into your machine, he has to first guess an existing user account and then he has to guess the right password. If you are not using trivial usernames and passwords, breaking into the machine would require many attempts and these would be recognized and logged by the system. If you can't find such entries, you probably don't have a problem.
Anyways, if you are often connecting to insecure networks, it may be a good idea to use a firewall.

---

### Post by waterbob on 2011-12-18
> **2F4U said:**
> No, I haven't heard of this. This doesn't mean that Linux or Ubuntu can't be hacked, any OS can be hacked. But Linux, through its privilege model, makes it much harder for hackers or malicious software, to cause harm to the computer.
If someone tries to get into your machine, he has to first guess an existing user account and then he has to guess the right password. If you are not using trivial usernames and passwords, breaking into the machine would require many attempts and these would be recognized and logged by the system. If you can't find such entries, you probably don't have a problem.
Anyways, if you are often connecting to insecure networks, it may be a good idea to use a firewall.
Well how do I know if I have been hacked? Is there any file or log I could check?

I do use a pretty weak password <snip> is that bad?

---

### Post by Ms. Daisy on 2011-12-18
> **waterbob said:**
> Well how do I know if I have been hacked? Is there any file or log I could check?

I do use a pretty weak password <snip> is that bad?
It's a bad idea to talk about your passwords on a public forum.  But yeah, that's not a great one either.

Read the wiki in my signature, it has tons of information written especially for someone like you. It should answer all your questions.

---

### Post by Dangertux on 2011-12-18
It's possible however it's unlikely. You can read the section in the Wiki Ms. Daisy posted about different log files to check and the types of things to look for. If you need clarification on anything post the log file in question and we can help you determine if the activity is anomalous.

Hope this helps.

---

### Post by waterbob on 2011-12-19
So what log do I check? I am confused.

---

### Post by Dangertux on 2011-12-19
I would go with squid logs, as well as your access.log for apache.

---

### Post by waterbob on 2011-12-19
> **Dangertux said:**
> I would go with squid logs, as well as your access.log for apache.
And how do I access that?

---

### Post by CharlesA on 2011-12-19
> **waterbob said:**
> And how do I access that?
Logs should be stored in /var/log/

---

### Post by waterbob on 2011-12-19
> **CharlesA said:**
> Logs should be stored in /var/log/
I still don't see it.

---

### Post by CharlesA on 2011-12-19
> **waterbob said:**
> I still don't see it.
What do you see if you run this:

```
ls /var/log
```

I see a bunch of stuff:

```
[COLOR="Blue"]apache2[/COLOR]        btmp             debug.1       dpkg.log       fontconfig.log  lastlog        mysql           pm-powersave.log       syslog.3.gz          user.log.3.gz
apparmor       btmp.1.gz        debug.2.gz    dpkg.log.1     fsck            lpr.log        mysql.err       pm-powersave.log.1     syslog.4.gz          user.log.4.gz
apt            ConsoleKit       debug.3.gz    dpkg.log.2.gz  gdm             mail.err       mysql.log       pm-powersave.log.2.gz  syslog.5.gz          wtmp
auth.log       cups             debug.4.gz    dpkg.log.3.gz  installer       mail.info      mysql.log.1.gz  pm-powersave.log.3.gz  syslog.6.gz          wtmp.1.gz
auth.log.1     daemon.log       dist-upgrade  dpkg.log.4.gz  jockey.log      mail.log       mysql.log.2.gz  pm-powersave.log.4.gz  syslog.7.gz          Xorg.0.log
auth.log.2.gz  daemon.log.1     dmesg         dpkg.log.5.gz  jockey.log.1    mail.warn      mysql.log.3.gz  pycentral.log          udev                 Xorg.0.log.old
auth.log.3.gz  daemon.log.2.gz  dmesg.0       dpkg.log.6.gz  kern.log        messages       mysql.log.4.gz  samba                  ufw.log
auth.log.4.gz  daemon.log.3.gz  dmesg.1.gz    dpkg.log.7.gz  kern.log.1      messages.1     mysql.log.5.gz  speech-dispatcher      unattended-upgrades
boot           daemon.log.4.gz  dmesg.2.gz    dpkg.log.8.gz  kern.log.2.gz   messages.2.gz  mysql.log.6.gz  syslog                 user.log
boot.log       dbconfig-common  dmesg.3.gz    dpkg.log.9.gz  kern.log.3.gz   messages.3.gz  mysql.log.7.gz  syslog.1               user.log.1
bootstrap.log  debug            dmesg.4.gz    faillog        kern.log.4.gz   messages.4.gz  news            syslog.2.gz            user.log.2.gz

```

---

### Post by Ms. Daisy on 2011-12-19
I hope no one minds a brief departure from the subject. CharlesA, how did you preserve the spacing in the output you pasted above? Whenever I paste terminal output, all spacing is lost.

---

### Post by CharlesA on 2011-12-19
> **Ms. Daisy said:**
> I hope no one minds a brief departure from the subject. CharlesA, how did you preserve the spacing in the output you pasted above? Whenever I paste terminal output, all spacing is lost.
I copy/pasted it from Putty and threw it in [noparse]```

```[/noparse] tags.

---

### Post by waterbob on 2011-12-19
> **CharlesA said:**
> What do you see if you run this:

```
ls /var/log
```

I see a bunch of stuff:

```
[COLOR="Blue"]apache2[/COLOR]        btmp             debug.1       dpkg.log       fontconfig.log  lastlog        mysql           pm-powersave.log       syslog.3.gz          user.log.3.gz
apparmor       btmp.1.gz        debug.2.gz    dpkg.log.1     fsck            lpr.log        mysql.err       pm-powersave.log.1     syslog.4.gz          user.log.4.gz
apt            ConsoleKit       debug.3.gz    dpkg.log.2.gz  gdm             mail.err       mysql.log       pm-powersave.log.2.gz  syslog.5.gz          wtmp
auth.log       cups             debug.4.gz    dpkg.log.3.gz  installer       mail.info      mysql.log.1.gz  pm-powersave.log.3.gz  syslog.6.gz          wtmp.1.gz
auth.log.1     daemon.log       dist-upgrade  dpkg.log.4.gz  jockey.log      mail.log       mysql.log.2.gz  pm-powersave.log.4.gz  syslog.7.gz          Xorg.0.log
auth.log.2.gz  daemon.log.1     dmesg         dpkg.log.5.gz  jockey.log.1    mail.warn      mysql.log.3.gz  pycentral.log          udev                 Xorg.0.log.old
auth.log.3.gz  daemon.log.2.gz  dmesg.0       dpkg.log.6.gz  kern.log        messages       mysql.log.4.gz  samba                  ufw.log
auth.log.4.gz  daemon.log.3.gz  dmesg.1.gz    dpkg.log.7.gz  kern.log.1      messages.1     mysql.log.5.gz  speech-dispatcher      unattended-upgrades
boot           daemon.log.4.gz  dmesg.2.gz    dpkg.log.8.gz  kern.log.2.gz   messages.2.gz  mysql.log.6.gz  syslog                 user.log
boot.log       dbconfig-common  dmesg.3.gz    dpkg.log.9.gz  kern.log.3.gz   messages.3.gz  mysql.log.7.gz  syslog.1               user.log.1
bootstrap.log  debug            dmesg.4.gz    faillog        kern.log.4.gz   messages.4.gz  news            syslog.2.gz            user.log.2.gz

```
Should I post what I get when I run ```
ls /var/log
```?

---

### Post by CharlesA on 2011-12-19
Do you get something similar to what mine shows? The access.log should be in /var/log/apache2/

---

### Post by waterbob on 2011-12-19
> **CharlesA said:**
> Do you get something similar to what mine shows? The access.log should be in /var/log/apache2/
I don't have a folder called apache2. :confused:

---

### Post by CharlesA on 2011-12-19
> **waterbob said:**
> I don't have a folder called apache2. :confused:
If you don't have Apache installed, you won't have any logs for it.

---

### Post by lisati on 2011-12-19
It might take a little while to track down anything useful, but it might be worthwhile looking at /var/log/syslog

---

### Post by waterbob on 2011-12-19
> **lisati said:**
> It might take a little while to track down anything useful, but it might be worthwhile looking at /var/log/syslog
What should I look for?

---

### Post by Dangertux on 2011-12-19
Alright , let's try this a different way because we're just going in circles right now. Let me see if I understand the situation correctly. You were running a Windows system in conjunction with a Ubuntu system on a wireless network. The windows machine became compromised and you are trying to find out of that Ubuntu box is also compromised. You are seeing strange activity in logs (where? you said squid but then you said you can't find your squid logs so now I'm confused.) 

Also to help me better answer your query please provide the following information

1 - The reason you think you were compromised a paste of whatever logs lead you to believe that someone is utilizing your system with unauthorized access. (redact any personal information please)

2 - The layout of the network the system is on, in detail. Is there a proxy (how is it configured) are the Windows box and Ubuntu box seperate, dual booted or VM's. Is this a shared network (IE: dorm, public wifi, library, etc) or is it a home network where it is access by only those who are trusted. Is it using strong encryption (WPA/2) or is it using WEP.

3 - Any additional information you might feel is pertinent. Odd occurences (please explain in depth). 

Example :

When I visit google.com from my chromium browser in Ubuntu on my home network I am redirected to freehawaiivacation.ru however if I visit it from my Windows machine using Firefox on the same network I am taken to google.com

Thank you.

---

### Post by waterbob on 2011-12-19
> Alright , let's try this a different way because we're just going in circles right now. Let me see if I understand the situation correctly. You were running a Windows system in conjunction with a Ubuntu system on a wireless network. The windows machine became compromised and you are trying to find out of that Ubuntu box is also compromised. 
Correct.

> You are seeing strange activity in logs (where? you said squid but then you said you can't find your squid logs so now I'm confused.) 
No, I never said I was seeing strange activities in the logs, someone told me to post them and I can't find the right ones.

> 2 - The layout of the network the system is on, in detail. Is there a proxy (how is it configured) are the Windows box and Ubuntu box seperate, dual booted or VM's. Is this a shared network (IE: dorm, public wifi, library, etc) or is it a home network where it is access by only those who are trusted. Is it using strong encryption (WPA/2) or is it using WEP.
I use Ubuntu and I connected to a wireless network for 6 months which had a separate computer that ran windows and it was infected with malware, and that computer now runs ubuntu as well. It is a secured home wireless network with wpa protection. And no proxy.

> 3 - Any additional information you might feel is pertinent. Odd occurrences (please explain in depth). 

Example :

When I visit google.com from my chromium browser in Ubuntu on my home network I am redirected to freehawaiivacation.ru however if I visit it from my Windows machine using Firefox on the same network I am taken to google.com

Thank you.
No strange occurrences that I am aware of, but then again I am pretty new to ubuntu and I am not sure I would know a strange occurrences when I see one. But no redirects or anything.

---

### Post by Dangertux on 2011-12-19
> **waterbob said:**
> Correct.


No, I never said I was seeing strange activities in the logs, someone told me to post them and I can't find the right ones.


I use Ubuntu and I connected to a wireless network for 6 months which had a separate computer that ran windows and it was infected with malware, and that computer now runs ubuntu as well. It is a secured home wireless network with wpa protection. And no proxy.


No strange occurrences that I am aware of, but then again I am pretty new to ubuntu and I am not sure I would know a strange occurrences when I see one. But no redirects or anything.


All right, outstanding. We're in a much better spot now at least I am, I was rather confused lol :-P

Now... If you completely trashed Windows and are now using Ubuntu on the once infected machine it is highly unlikely that an infection remains. Since you are not noticing anomalous behavior, it's likely that everything is just fine.

The set up of your network looks pretty solid from what you've described, and I have no reason that I would outright say that you are currently still compromised.

If you are concerned about malware there are several anti-malware scanners for Ubuntu that do a decent job at detecting Windows malware. I would recommend Avast, though I hear bit defender is pretty good as well. 

As it stands right now though -- I would say you have nothing to worry about, as it is unlikely that the malware that was installed under windows was designed to be able to migrate to Ubuntu, or that it even had the opportunity. While this is theoretically possible it is HIGHLY unlikely, and would be a VERY targeted attack.

I hope this helps.

---

### Post by waterbob on 2011-12-20
> **Dangertux said:**
> All right, outstanding. We're in a much better spot now at least I am, I was rather confused lol :-P

Now... If you completely trashed Windows and are now using Ubuntu on the once infected machine it is highly unlikely that an infection remains. Since you are not noticing anomalous behavior, it's likely that everything is just fine.

The set up of your network looks pretty solid from what you've described, and I have no reason that I would outright say that you are currently still compromised.

If you are concerned about malware there are several anti-malware scanners for Ubuntu that do a decent job at detecting Windows malware. I would recommend Avast, though I hear bit defender is pretty good as well. 

As it stands right now though -- I would say you have nothing to worry about, as it is unlikely that the malware that was installed under windows was designed to be able to migrate to Ubuntu, or that it even had the opportunity. While this is theoretically possible it is HIGHLY unlikely, and would be a VERY targeted attack.

I hope this helps.
I don't think I have malware (I already scanned) but I am concerned the hacker might have created a backdoor on my ubuntu laptop and has access to it now. How would I tell if this happened?

---

### Post by spynappels on 2011-12-20
> **waterbob said:**
> I don't think I have malware (I already scanned) but I am concerned the hacker might have created a backdoor on my ubuntu laptop and has access to it now. How would I tell if this happened?

You would need to check the auth.log files in /var/log, but taking a step back, this is extremely unlikely.

What would have had to happen is this:

Windows computer becomes infected
Malware on Windows computer scans for other computers on LAN
Malware then carries out a targeted attack on your Linux laptop
Laptop becomes infected/has a backdoor put on it.

While steps 1 and 2 are likely, step 3 is much more unlikely and step 4 is very unlikely indeed on a standard Ubuntu install, due to privilege escalation and lack of listening ports and even simple architecture differences between Linux and Windows.

So I would say that unless you have concrete reasons for thinking the laptop is compromised and not just a vague disquiet, you are fine.

If you feel you simply cannot trust your laptop, the only recourse is a clean install, but based on the info you have given so far, I think this is not necessary.

---

### Post by CharlesA on 2011-12-20
> **spynappels said:**
> 
So I would say that unless you have concrete reasons for thinking the laptop is compromised and not just a vague disquiet, you are fine.

If you feel you simply cannot trust your laptop, the only recourse is a clean install, but based on the info you have given so far, I think this is not necessary.

Indeed. I don't see anything that would warrant a reinstall.

---

### Post by Paddy Landau on 2011-12-20
In full agreement with Dangertux and spynappels, there is nothing to indicate that you have a problem. Don't worry about it.

Regarding your very simple password, you may want to check [GRC's Password Haystack]("https://www.grc.com/haystack.htm"). It will help you to choose a strong, secure password.

---

### Post by waterbob on 2011-12-20
Sounds rational enough, but let me ask you this, if I reinstalled ubuntu on my laptop, what is the chance if my laptop *was* infected, it would have spread back to the other laptop with ubuntu?

And what should I look for in the auth log?

---

### Post by CharlesA on 2011-12-20
Changes are low. Windows viruses won't run on a *nix box.

---

### Post by waterbob on 2011-12-20
> **CharlesA said:**
> Changes are low. Windows viruses won't run on a *nix box.
What kind of changes? The entries in it only go back to Dec 18.

And I know windows viruses don't run on linux, but I am concerned a hacker (or cracker/whatever) exploited my laptop and now has access to it.

---

### Post by CharlesA on 2011-12-20
Chances are low, rather. Spelling = fail.

If the machine was compromised a reinstall would wipe any trace of it away.

---

### Post by OpSecShellshock on 2011-12-20
What you would check for in auth.log is access by a user who isn't you, or access by you at a time when you are sure you weren't logged in.

As for the persistence of unauthorized access, it would not survive a clean install if it were the result of some kind of backdoor.

---

### Post by waterbob on 2011-12-20
The log looks very confusing, I guess I will monitor it for a while.

I know it would wipe the backdoor, but what about the other laptop with ubuntu? Could the attacker have access to that as well?

Or would I have to reinstall ubuntu on both of them while both are disconnected from the network?

But back in reality, what are the chances of my laptop being compromised in the first place? e.g 5%, 1%, 0.2%?

---

### Post by OpSecShellshock on 2011-12-20
To be honest, the chances that either of them is compromised are extraordinarily low. Even sharing a network with a Windows computer that is loaded down with modern commercial malware is unlikely to affect the Ubuntu machine in the slightest. If they are both running Ubuntu and there is no evidence that either of them is being used remotely by an unauthorized party then there's really nothing to worry about.

I think doing a clean installation on both would mostly just be for peace of mind, since it would eliminate any chance that whatever might cause unauthorized access would be wiped out. Since that's probably not happening anyway, it may strike some as overkill, but everyone has to choose their own level of concern. Users should do whatever it takes to be comfortable using their systems for their intended purposes.

---

### Post by waterbob on 2011-12-20
> To be honest, the chances that either of them is compromised are extraordinarily low. Even sharing a network with a Windows computer that is loaded down with modern commercial malware is unlikely to affect the Ubuntu machine in the slightest. If they are both running Ubuntu and there is no evidence that either of them is being used remotely by an unauthorized party then there's really nothing to worry about.
This computer had everything from rootkits to trojans, so it was pretty loaded. 

What is considered evidence of ubuntu being compromised?

And do I need a firewall?

---

### Post by OpSecShellshock on 2011-12-20
Rootkits and trojans would not survive a full installation of Ubuntu, and if created for Windows, would not run on it.

When I say evidence of compromise in the context of a desktop system (as opposed to a server, which I presume we aren't talking about) what I mean is evidence that some of your other accounts, say email, banking, and whatever else, have been used by others to either communicate suspiciously with your contacts or steal your money. Those things tend to happen quickly, so you'd know by now.

It is a good idea to have a firewall. There's one built into Ubuntu installations, but I don't believe it's on unless you turn it on. If you have more than one system on your home network, then there is probably a router between your ISP's modem and your computers. These devices usually also function as firewalls.

---

### Post by waterbob on 2011-12-20
> **OpSecShellshock said:**
> Rootkits and trojans would not survive a full installation of Ubuntu, and if created for Windows, would not run on it.

When I say evidence of compromise in the context of a desktop system (as opposed to a server, which I presume we aren't talking about) what I mean is evidence that some of your other accounts, say email, banking, and whatever else, have been used by others to either communicate suspiciously with your contacts or steal your money. Those things tend to happen quickly, so you'd know by now.

It is a good idea to have a firewall. There's one built into Ubuntu installations, but I don't believe it's on unless you turn it on. If you have more than one system on your home network, then there is probably a router between your ISP's modem and your computers. These devices usually also function as firewalls.
So if you were me, would you stop worrying?

---

### Post by OpSecShellshock on 2011-12-20
> **waterbob said:**
> So if you were me, would you stop worrying?

That's what I'd do.

---

### Post by waterbob on 2011-12-20
> **OpSecShellshock said:**
> That's what I'd do.
But how do I turn on the firewall?

And is there any sort of ports that would be open if I was compromised?

---

### Post by Dangertux on 2011-12-20
> **waterbob said:**
> But how do I turn on the firewall?

And is there any sort of ports that would be open if I was compromised?

To enable the firewall simply

```

sudo ufw enable

```For more in depth information about configuring the firewall more securely read here : [http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

As far as ports being opened on a compromised system yes there usually are however they are usually pseudo random and if the system is rootkitted sockets and associated ports may be hidden.

Hope this helps.

---

### Post by Ms. Daisy on 2011-12-20
> **waterbob said:**
> But how do I turn on the firewall?

And is there any sort of ports that would be open if I was compromised?
The firewall is on by default in Ubuntu, it is set to deny all incoming & allow all outgoing traffic.  You need to configure it if you want to restrict traffic.

This thread will show you how to use a firewall.  I was able to follow it as a new user.

[http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

---

### Post by waterbob on 2011-12-21
Hay, on your firewall tutorial I installed gufw but do I have to do all those port steps? Or can I just leave outgoing as "allow"?

---

### Post by OpSecShellshock on 2011-12-21
> **waterbob said:**
> Hay, on your firewall tutorial I installed gufw but do I have to do all those port steps? Or can I just leave outgoing as "allow"?

That will depend on whatever you're most comfortable with. If you are concerned about backdoors establishing connections to other computers then I would go with filtering outbound traffic. In most cases it isn't enough of a risk to most Ubuntu users to be worth it if it's going to be too difficult to manage. I do it just in case my boss decides to keep me on my toes when I'm at home.

---

### Post by waterbob on 2011-12-21
> **OpSecShellshock said:**
> That will depend on whatever you're most comfortable with. If you are concerned about backdoors establishing connections to other computers then I would go with filtering outbound traffic. In most cases it isn't enough of a risk to most Ubuntu users to be worth it if it's going to be too difficult to manage. I do it just in case my boss decides to keep me on my toes when I'm at home.
I don't think I have a rootkit. How would your boss do that?

Is there any easier way of telling if someone has compromised my system? (I am not meaning to be redundant here).

---

### Post by spynappels on 2011-12-21
> **waterbob said:**
> Is there any easier way of telling if someone has compromised my system? (I am not meaning to be redundant here).

I don't want to be too brusque, but you have had multiple people tell you that there is more than overwhelmingly likely no problem, as well as giving you tips to secure and harden your system.

There is no simple way to tell if you have been compromised, although what you have said so far and the balance of probability would say not.

If you feel that there is still ambiguity, then you need to consider whether the hassle of re-installing would set your mind at ease or not, and act accordingly.

The bottom line is, we don't think you have been compromised, but only you can decide whether you trust our judgement/believe us.

Have a nice day.

---

### Post by Dangertux on 2011-12-21
what your boss never sent you payloaded files? Lol lucky it happens a lot on Thursdays... Please don't ask why ;-)

No but seriously you're fine. Yes there are ways of telling if you've been compromised, that being said it's probably not something most would be willing to give a step by step on in a thread especially since in your case it is highly unlikely that anything would be found. 

If you want a deeper understanding of how to determine if a system has been compromised. Start learning more about nix and how it can be compromised. For instance what log files look like from a cmrpomised machine , or what a malicious cron job might look like, and a myriad of other things. 

But really I think you should stop worrying.

---

### Post by waterbob on 2011-12-21
Okay I guess I will stop worrying about it. 

But I have one final question, they changed the internet password (the one used for the modem) on their infected computer, and I am pretty sure the hacker got it, can the hacker see my internet traffic?

Because I couldn't figure out how to change it.

---

### Post by Ms. Daisy on 2011-12-21
Reset the router. See [this tutorial ]("http://compnetworking.about.com/od/wirelesssecurity/tp/wifisecurity.htm")how to do that.

---

### Post by waterbob on 2011-12-21
> **Ms. Daisy said:**
> Reset the router. See [this tutorial ]("http://compnetworking.about.com/od/wirelesssecurity/tp/wifisecurity.htm")how to do that.
I actually did that once before, but I forgot the password and they had to stay on the phone with the isp to get the password back. But I just want to know, can the hacker see my web traffic with the modem passward?

---

### Post by waterbob on 2011-12-21
And I wasn't talking about the router password, I was talking about the modem (from the isp) password.

---

### Post by Paddy Landau on 2011-12-21
> **waterbob said:**
> But I just want to know, can the hacker see my web traffic with the modem passward?
If they've set the router to use their own proxy, yes. They could even stage a man-in-the-middle attack whereby they can see your banking passwords. EDIT: I've just seen your latest post. Probably not, but it won't hurt to change the password to a [strong password]("https://www.grc.com/haystack.htm").

Reset the router, change the default password to a strong password, change the user name if it allows you to, and follow as many of the other steps in the tutorial as you can.

Be sure to use WPA2 for your wireless (if you can), otherwise WPA, with a preference for AES rather than TKIP. Using WEP is pointless, as it can be cracked in seconds.

---

### Post by waterbob on 2011-12-21
> **Paddy Landau said:**
> If they've set the router to use their own proxy, yes. They could even stage a man-in-the-middle attack whereby they can see your banking passwords. EDIT: I've just seen your latest post. Probably not, but it won't hurt to change the password to a [strong password]("https://www.grc.com/haystack.htm").

Reset the router, change the default password to a strong password, change the user name if it allows you to, and follow as many of the other steps in the tutorial as you can.

Be sure to use WPA2 for your wireless (if you can), otherwise WPA, with a preference for AES rather than TKIP. Using WEP is pointless, as it can be cracked in seconds.
Okay, the hacker don't have the router password (I set that one). But the owners of the network don't want me messing with their "internet" anymore. So what could the hacker do with the modem password anyway?

---

### Post by waterbob on 2011-12-21
But just as long as the hacker can't get my email and facebook I am fine.

---

### Post by waterbob on 2011-12-21
And this is my LAST question (I promise). :)

---

### Post by OpSecShellshock on 2011-12-21
> **waterbob said:**
> But just as long as the hacker can't get my email and facebook I am fine.

Oh, if someone wanted either of those they wouldn't bother hacking your systems. They'd just hack you. Uh, but don't freak out. Your logins for those are going to be encrypted between your computer and the sites' servers.

Keep those passwords strong and most importantly, different from each other and all of your other passwords. Also, if you aren't the owner of the network, there's really only so much you can do.

---

### Post by waterbob on 2011-12-21
> **OpSecShellshock said:**
> Oh, if someone wanted either of those they wouldn't bother hacking your systems. They'd just hack you. Uh, but don't freak out. Your logins for those are going to be encrypted between your computer and the sites' servers.

Keep those passwords strong and most importantly, different from each other and all of your other passwords. Also, if you aren't the owner of the network, there's really only so much you can do.
I forgot about encryption. Silly me.

But I keep my passwords on a text file on my computer is this safe? Or incredibly dangerous?

---

### Post by waterbob on 2011-12-21
Also, if the attacker has the password can he see the web traffic? This is all I want to know.

---

### Post by Dangertux on 2011-12-21
Check it out.

The bottom line is if you control any segment in the network then you can sniff the traffic. If it's SSL encrypted then it's a little bit harder. However it can still be done if a man in the middle condition be created with the use of something like SSLstrip. 

Still keep your passwords strong, also if this above condition is created you will likely get a certificate warning, though not necessarily.

If there is a segment of the network you can't control then most of this is out of your hands.

Also -- yes storing passwords in a text file on your computer is a terrible idea. If you need a password management system I suggest something like last pass or keepass though, I don't like them.

Hope this helps.

---

### Post by CharlesA on 2011-12-21
> **Dangertux said:**
> If you need a password management system I suggest something like last pass or keepass though, I don't like them.

Aye. Single point of failure and all that.

---

### Post by Hellweek on 2011-12-21
Wow, this was hard to follow.  It almost sounds like someones chain is being pulled here.

Storing passwords in clear text is never a good idea.  Passwords these days need to be strong mix of letters and numbers with mixed case.  How many of you have noticed that sites have password standards now?

You have had some good advice. Advice many people would have to pay for.  The chances are little to none that your *nix was hit.

It seems that you visit sites that infect computers.  Be aware that the same can happen on you *nix. learn how to protect your system.

---

### Post by waterbob on 2011-12-21
Thanks for your help everyone. :) I guess I am fine tho.

---

### Post by Paddy Landau on 2011-12-22
If this has answered your question, please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") to help other people with your problem.

> **Dangertux said:**
> storing passwords in a text file on your computer is a  terrible idea.Absolutely true. However, I would like to know: where could one store passwords safely? Ideally on the cloud so the passwords are not lost through (say) fire, but then how can you be sure that the cloud is not compromised? This is a tricky question indeed.

---

### Post by Dangertux on 2011-12-22
> **Paddy Landau said:**
> If this has answered your question, please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") to help other people with your problem.

Absolutely true. However, I would like to know: where could one store passwords safely? Ideally on the cloud so the passwords are not lost through (say) fire, but then how can you be sure that the cloud is not compromised? This is a tricky question indeed.

If you're wanting them to survive physically in addition to password management write them down and put them in a safe deposit box in the bank. (If it's that serious)

---

### Post by Paddy Landau on 2011-12-22
> **Dangertux said:**
> If you're wanting them to survive physically in addition to password management write them down and put them in a safe deposit box in the bank. (If it's that serious)
:lol: No, it's not that serious -- no state secrets!

---

