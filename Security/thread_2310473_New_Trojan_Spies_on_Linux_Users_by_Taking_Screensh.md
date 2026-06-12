---
title: "New Trojan Spies on Linux Users by Taking Screenshots and Recording Audio"
date: 2016-01-19
forum: Security
---

### Post by Daveski17 on 2016-01-19
'Dr.Web, a Russian antivirus maker, has detected a new threat against Linux users, the Linux.Ekocms.1 trojan, which includes special features that allow it to take screengrabs and record audio.' ~ *Softpedia*

[http://news.softpedia.com/news/new-trojan-spies-on-linux-users-by-taking-screenshots-and-recording-audio-499113.shtml](http://news.softpedia.com/news/new-trojan-spies-on-linux-users-by-taking-screenshots-and-recording-audio-499113.shtml)

---

### Post by slickymaster on 2016-01-19
The danger of this threat is high, Dr. Web researchers could have disclosed how this malware infects Linux computers.

---

### Post by Daveski17 on 2016-01-19
'According to Dr.Web, this particular trojan is part of the spyware family and was specially crafted to take a screenshot of the user's desktop every 30 seconds.

In most cases, screenshot files are always saved to the same two folders, but if the folders don't exist, the trojan will create its own when needed.

If you don't have an antivirus solution installed on your Linux PC, you can check for Linux.Ekocms by inspecting the following two folders and seeing if you find any screengrabs:

- $HOME/$DATA/.mozilla/firefox/profiled

- $HOME/$DATA/.dropbox/DropboxCache

By default, the trojan saves all files in JPEG format with a name that contains the timestamp of when the screenshot was taken. If there's an error while saving the file, the trojan will use the BPM image format.'

How do I find these folders on my computer?

- $HOME/$DATA/.mozilla/firefox/profiled

- $HOME/$DATA/.dropbox/DropboxCache

---

### Post by maxinstuff2 on 2016-01-19
Well, this is concerning to say the least.

No info on where it's coming from yet...... interesting.

I am reading that it uploads the screenies to a FIXED address, hardcoded in the app. Again, no details are shared - what IP address, what ports, what protocol is it using? Is it the attackers "home" server or is this a hijacked machine?

I want details :)

---

### Post by Daveski17 on 2016-01-19
Hmmm ... yeah, spill the beans Dr Web! ;)

---

### Post by maxinstuff2 on 2016-01-19
> **Daveski17 said:**
> Hmmm ... yeah, spill the beans Dr Web! ;)

Oh - to actually answer your question - the folders mentioned sound like they are the ones in your home directory. 

So in a terminal, navigate to the folder and then list the contents with "ls" command:
```
cd ~/[COLOR=#000000].mozilla/firefox/profiled
ls[/COLOR]
```
[COLOR=#000000]or
```
cd ~/.dropbox/DropboxCache
ls
```
Alternatively you can toggle view of hidden folders (those with the . character) in your home directory in the gui by pressing Ctrl+h.[/COLOR]

---

### Post by mörgæs on 2016-01-20
As always, the best one can do is to set the system to apply security updates automatically. 

It's especially important if the computer is used by someone who is not familiar with IT matters.

---

### Post by Daveski17 on 2016-01-20
> **maxinstuff2 said:**
> Oh - to actually answer your question - the folders mentioned sound like they are the ones in your home directory. 

So in a terminal, navigate to the folder and then list the contents with "ls" command:
```
cd ~/[COLOR=#000000].mozilla/firefox/profiled
ls[/COLOR]
```
[COLOR=#000000]or
```
cd ~/.dropbox/DropboxCache
ls
```
Alternatively you can toggle view of hidden folders (those with the . character) in your home directory in the gui by pressing Ctrl+h.[/COLOR]

OK thanks. I think they can also be accessed in Firefox (Troubleshooting Information - Profile Folder).

> **mörgæs said:**
> As always, the best one can do is to set the system to apply security updates automatically. 

I always keep the system up to date.

> **mörgæs said:**
> It's especially important if the computer is used by someone who is not familiar with IT matters.

Ah, that would be me then. ;)

I know Dr Web aren't saying much but I would like to know how this trojan is contracted onto the system in the first place. The only trojan I ever encountered was in 2008 running Vista. I was in SeaMonkey with no adblocker and had not installed NoScript then and accidentally clicked on a flash ad. I believe it was a buffer overflow attack. Nowadays both on Linux and Windows I have an amount of browser hardening (uBlock Origin, NoScript, Flagfox, WOT).

---

### Post by bashiergui on 2016-01-20
Screenshots every 30 seconds will fill up disk space fast, especially if space is limited. The article didn't say how often it dumps screenshots out to its c2c, but it would have to be at fairly short intervals lest they fill up the victim's disk. 

You could use Tripwire to watch the file locations listed here:
[http://vms.drweb.com/virus/?i=7924647](http://vms.drweb.com/virus/?i=7924647)

Would have been nice if they said what port and service it uses to communicate back. Restrictive firewall rules denying everything except what you need might help unless they're using 443 or 80. Come to think of it, they left a lot of useful information out :-/

---

### Post by maglin2 on 2016-01-20
> **bashiergui said:**
>  Come to think of it, they left a lot of useful information out :-/

They have indeed - conceivably for increased impact. In particular they give no information on how the malware infects machines.

I gather that well over 1E6 new Windows Trojans are identified each year, yet very very many Windows users experience no issues with any of these.

---

### Post by Habitual on 2016-01-20
Searching for [https://duckduckgo.com/?q=Linux.Ekocms](https://duckduckgo.com/?q=Linux.Ekocms)
resembles a DrWeb "Commercial".

---

### Post by mörgæs on 2016-01-20
> **maglin2 said:**
> They have indeed - conceivably for increased impact. In particular they give no information on how the malware infects machines.


This is good practice. Revealing a lot of information before the fix is out gives bad people good ideas.

> **maglin2 said:**
> I gather that well over 1E6 new Windows Trojans are identified each year, yet very very many Windows users experience no issues with any of these.

What is an 'issue' to you? The virus probably does no harm to the computer but identity theft and backmailing are real threats.

---

### Post by maxinstuff2 on 2016-01-20
> **Habitual said:**
> Searching for [https://duckduckgo.com/?q=Linux.Ekocms](https://duckduckgo.com/?q=Linux.Ekocms)
resembles a DrWeb "Commercial".

Yes, this was my feeling also.

"Dr. Web has discovered this crazy new virus!!!!"

> **mörgæs said:**
> This is good practice. Revealing a lot of information before the fix is out gives bad people good ideas.

I have to strongly disagree with this. Keeping the information secret just leaves everyone vulnerable. It's also extremely patronising and self-serving bahaviour on behalf of an anti-virus company. It's as if to say "we can't tell you how it works because that might give naughty people ideas, but download our anti-virus software and we'll protect you!"

---

### Post by CharlesA on 2016-01-20
Smells like an ad to me. There is no reason to not disclose detailed info unless you want people to buy your product to "protect themselves."

:rolleyes:

---

### Post by patrikmellq on 2016-01-21
I open the terminal and try to navigate to ```
cd ~/.mozilla/firefox/profiled
``` but it say no such file or directory exist.
Am i doing something wrong or is that a good thing?

Test Ctrl+h and can see my .mozilla folder and open it and only have extension and firefox folder.

> You could use Tripwire to watch the file locations listed here:
[http://vms.drweb.com/virus/?i=7924647](http://vms.drweb.com/virus/?i=7924647)

I understand that we can add the file path to Tripwire to notice any change, but would it not be to late as the virus make pictures every 30 sec, i mean you need to have a Tripwire installation/configuration where Tripwire send you email alert if something change which might alert our mobile phone with new email. But i have never seen any configuration guide how to do that with Tripwire, send email alerts in present time.
If you know such a guide or howto - then feel free to post a link.

---

### Post by maglin2 on 2016-01-21
> **mörgæs said:**
> This is good practice. Revealing a lot of information before the fix is out gives bad people good ideas.

This may be true for some threats. Assuming this threat is in that category, consider the purpose of trumpeting your discovery of it before it has become wise to reveal the modus operandi/routes to protection. 

I believe it is commercial. Readers cannot assess the risk it poses to them, hence uncertainty and fear are raised. The incentive to buy Dr Web's AV, as the only available fix, is increased.

I am not in any way anti-commerce, but I prefer my commerce to follow a Needs, Features, Benefits sales model, rather than a Fear, Uncertainty, Doubt sales model.

---

### Post by mörgæs on 2016-01-21
Though only little information is relased I am still willing to guess what the virus is about.

A standard Buntu (non-server) is hard to attack from outside because no daemons are listening, unlike Windows. Therefore most attacks are using one of two approaches:

a) Inside-out attack: When the user is tricked to click a certain link or open a certain e-mail attachment, a connection out is made and the attack begins. 
b) Privilege escalation: A standard user account is able to get root access without root password due to a bug.

Thus, if you and your family are the sole users of a computer (non-server) and if all are aware of the danger of 'click here!' e-mails I guess the risk is low. 

Let's see if this is correct when more information surfaces. 


Details of a security bug are always kept low-profile. Even our own Launchpad hides security bugs until a fix is out. 


As for the commercial part of it I think people should embrace that companies (antivirus or whatever) are paying attention to Buntu and see it as a mature platform for a business plan. I would not like a situation where antivirus companies ignored malware research in Buntu.

---

### Post by bashiergui on 2016-01-21
> **patrikmellq said:**
> I understand that we can add the file path to Tripwire to notice any change, but would it not be to late as the virus make pictures every 30 sec, i mean you need to have a Tripwire installation/configuration where Tripwire send you email alert if something change which might alert our mobile phone with new email. But i have never seen any configuration guide how to do that with Tripwire, send email alerts in present time.
If you know such a guide or howto - then feel free to post a link.Being notified when you check tripwire logs is better than not being notified at all. Sure you can set up tripwire to email you
[https://www.digitalocean.com/community/tutorials/how-to-use-tripwire-to-detect-server-intrusions-on-an-ubuntu-vps](https://www.digitalocean.com/community/tutorials/how-to-use-tripwire-to-detect-server-intrusions-on-an-ubuntu-vps)

I'm calling this one FUD too. They publicly released enough details to let the malware author know they found it, so the only people disadvantaged by withholding details are defenders.

---

### Post by patrikmellq on 2016-01-23
Hello, i just want to say that i think is better to install and make configuration with Tripwire database on removable media, then letting Tripwire running 100% from the Ubuntu system when sending emails reports once each day.
Because maybe a hacker can crack or modifies the Tripwire, which is not possible if you have it on removable media. 

I also think i find a guide for how to get Tripwire report in present time if there is a change in system so you can react in real time when intrusion happens.
Following this guide: [http://www.linuxquestions.org/questions/linux-security-4/email-alerts-with-tripwire-883839/](http://www.linuxquestions.org/questions/linux-security-4/email-alerts-with-tripwire-883839/)
That should be better solution as then a hacker or cracker would probably not have time to do anything before you get one email alert on your mobile phone.

---

### Post by bashiergui on 2016-01-23
It is good practice to send logs off to a separate device in real time, then if the attacker changes or deletes them you will see it. However that's massive overkill for a home user. But hey- who am I to judge. My idea of a good time is to stand up Security Onion on my home network just because I can.

---

### Post by haplorrhine on 2016-01-24
> **bashiergui said:**
> Being notified when you check tripwire logs  is better than not being notified at all. Sure you can set up tripwire  to email you
[https://www.digitalocean.com/community/tutorials/how-to-use-tripwire-to-detect-server-intrusions-on-an-ubuntu-vps](https://www.digitalocean.com/community/tutorials/how-to-use-tripwire-to-detect-server-intrusions-on-an-ubuntu-vps)

I'm calling this one FUD too. They publicly released enough details to  let the malware author know they found it, so the only people  disadvantaged by withholding details are defenders.

or AIDE

I learned Tripwire, then learned that AIDE supports newer hash algorithms.

> **Habitual said:**
> Searching for [https://duckduckgo.com/?q=Linux.Ekocms](https://duckduckgo.com/?q=Linux.Ekocms)
resembles a DrWeb "Commercial".

kudos

---

