---
title: "Chkrootkit found &quot;suspicious&quot; files, and other fun stuff!"
date: 2012-03-03
forum: Security
---

### Post by delta410 on 2012-03-03
Chkrootkit found a few files on my system which it labeled suspicious. Here's what I got:

> suspicious files and directories were found:  
/usr/lib/xulrunner-1.9.2.27/.autoreg /usr/lib/jvm/.java-6-openjdk.jinfo /usr/lib/pymodules/python2.6/PyQt4/uic/widget-plugins/.noinit /usr/lib/pymodules/python2.6/.path
I think I clipped off the first part of the message when I copied and pasted the text from the terminal.

Are these false positives? If not, how do I clean them?

Also, how do I get Firestarter to start up automatically, the way Avast or Zone Alarm would in (if you'll pardon the expression) Windows? I'm pretty diligent about starting it before I do anything else, but I've forgotten to start it on more than one occasion. And since I'm giving my admin password to start it, does that log me in as "root" (please don't laugh. I'm fairly new at this)?

Lastly, I clicked on a URL in what looked like an e-mail from a friend in my Gmail account (guess the web-scum hijacked his address). I was in Firefox and the URL took me to one of those dodgy sites which sells dodgy products and when you try to leave, flashes a pop-up saying "are you sure you want to navigate away from this page and miss out on some great deals?" or something like that. I just pulled the plug on my machine when that happened. It subsequently rebooted without incident, but i'm wondering if that web site has left behind any surprises.

---

### Post by claracc on 2012-03-04
As far as I know, they are false positives (chkrootkit and rkhunter give a lot of them), I wouldn't remove any of indicated files ( firefox related, java openjdk or phyton). I recommend you to read the security stickyes in this subforum. Note the one about firewall and host-based intrusion detection systems.

As for firestarter, I think this is an old firewall project. I use ufw and its gui app gufw to manage it. You can activate it in the gufw screen and it runs when starting the system.

---

### Post by Ms. Daisy on 2012-03-04
I'm no expert but it looks like you got something very similar to this guy which was a false positive:

[http://ubuntuforums.org/showthread.php?t=1840388](http://ubuntuforums.org/showthread.php?t=1840388)

[USELESS_OPINION] There are a whole lot of threads like that one, and they leave me wondering if chkrootkit is honestly useful [/USELESS_OPINION]

Firestarter is no longer supported. You could use ufw or gufw in the software center. It would be easier to find support for a supported application. In fact there's a good ufw discussion in the stickys of this forum. But if you switch to ufw make sure to remove Firestarter- they apparently conflict.

As far as surprises from the dodgy website, you can look here for a nice tutorial to figure out if you've been compromised.
[https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned](https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned)

You said you're new at this, so you may also want to take a quick look at the other links in my signature which were designed for new users.

---

### Post by Dangertux on 2012-03-04
Youre fine those are among the typical false positives that rkhunter abd chlrootkit normally throw out

---

### Post by emiller12345 on 2012-03-04
I think chkrootkit will report any filename that is in your /usr/ directory and has a filename that begins with a "." as being suspicious (because technically these files are hidden).

---

### Post by unspawn on 2012-03-07
> **Ms. Daisy said:**
> [USELESS_OPINION] There are a whole lot of threads like that one, and they leave me wondering if chkrootkit is honestly useful [/USELESS_OPINION]
It's not a useless opinion. The problem is a lot of people (and tutorials and HOWTOs) forget to mention is these are after-the-fact tools: they try to detect anomalies but they don't enhance security. *The emphasis should be on hardening and regularly updating and auditing*. (It would be good if "DidIJustGetOwned" mentioned that too IMHO.) Even then there's a lot of Linux users that just don't care or don't (want to) understand what files like README or FAQ are for...

---

### Post by Ms. Daisy on 2012-03-07
> **unspawn said:**
> It's not a useless opinion. The problem is a lot of people (and tutorials and HOWTOs) forget to mention is these are after-the-fact tools: they try to detect anomalies but they don't enhance security. *The emphasis should be on hardening and regularly updating and auditing*. (It would be good if "DidIJustGetOwned" mentioned that too IMHO.) Even then there's a lot of Linux users that just don't care or don't (want to) understand what files like README or FAQ are for...
IMO the "DidIJustGetOwned" wiki addresses this already in the **rkhunter and chkrootkit** section.  That wiki is specifically designed to help people after the fact & be an introduction to auditing.  The [Basic Security wiki]("https://wiki.ubuntu.com/BasicSecurity") is designed to enhance security by hardening and regularly updating the desktop.
[QUOTE=DidIJustGetOwned wiki]rkhunter and chkrootkit are two applications that are  designed to aid in the detection of a compromised system. They function  by doing two things. First they check the integrity of commonly hooked  system files. These files are often backdoored by an attacker in order  to gain special access or glean credentials from a compromised system.  An example of a frequently backdoored command in the Linux world is /bin/su.  

It  is important to understand that rkhunter and chkrootkit function best  if they are given a benchmark standard. Meaning that you run them  following your initial installation so that they may get a "base line"  for what your system should look like. That way if changes are made,  they will be able to detect the changes as potentially unauthorized.  Note, sometimes updates may throw false positives due to the way these  applications work. [/QUOTE]

As I understand your comment, the wikis exactly address your concerns already. Do you agree?

---

### Post by unspawn on 2012-03-07
> **Ms. Daisy said:**
> IMO the "DidIJustGetOwned" wiki addresses this already in the rkhunter and chkrootkit section. That wiki is specifically designed to help people after the fact & be an introduction to auditing.
If you mean the "don't enhance security" part, yes, but otherwise: no. There's no reference to or emphasis on the (way higher) importance of hardening. At least linking to [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) in the introductory paragraph could be helpful IMHO.


> **Ms. Daisy said:**
> As I understand your comment, the wikis exactly address your concerns already. Do you agree?
No I don't but it will take me more time than I have right now to explain. I do commend you for writing the page though, it certainly is helpful, usable and something I could refer to (even though we have a [README](http://rkhunter.cvs.sourceforge.net/viewvc/rkhunter/rkhunter/files/README), [FAQ](http://rkhunter.cvs.sourceforge.net/viewvc/rkhunter/rkhunter/files/FAQ) and [manual](http://sourceforge.net/apps/trac/rkhunter/wiki/SPRKH)).

---

### Post by Dangertux on 2012-03-07
> **unspawn said:**
> If you mean the "don't enhance security" part, yes, but otherwise: no. There's no reference to or emphasis on the (way higher) importance of hardening. At least linking to [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) in the introductory paragraph could be helpful IMHO.



No I don't but it will take me more time than I have right now to explain. I do commend you for writing the page though, it certainly is helpful, usable and something I could refer to (even though we have a [README]("http://rkhunter.cvs.sourceforge.net/viewvc/rkhunter/rkhunter/files/README"), [FAQ]("http://rkhunter.cvs.sourceforge.net/viewvc/rkhunter/rkhunter/files/FAQ") and [manual]("http://sourceforge.net/apps/trac/rkhunter/wiki/SPRKH")).

As a contributor to the afforementioned wiki as well as someone who spends a considerable amount of time addressing security related issues on this forum I can certainly see where you're coming from.

I also completely agree that there are both proactive and reactive solutions, and that tools like AV or chkrootkit / rkhunter / tiger /whatever as whatever other enumerable anti-malware solutions are out there are in fact reactive measures.

Meaning that they are reacting to a compromise after the fact, otherwise known as post-mortem on a system.

You are also correct in your assumption that considerably less effort should be put into scanning as is put into the actual hardening or application of the previously mentioned proactive measures.

Examples of which would be aggressive firewalling, implementation of mandatory access controls, application whitelisting, aggressive access control schema , etc...

That being said -- there are two problems with hardening guides (despite the fact I've written a few). One, it's nearly impossible to address every single use case, and you're basically watering yourself down to best practices. In which case most of Ubuntu's standard documentation meets those requirements. The second, is it is also impossible (at least as a singular or small group effort) to address every conceivable service, application and vulnerability that any given user could introduce into their environment and write an appropriate set of hardening instructions. That is why it's often best to give this type of advice on the fly, or on a by request basis.

Example being : 

I'm running a development webserver on apache, it's internet accessible and I'll be testing my home grown web applications. In conjunction I'll also be using a glassfish java servlet.

Great... So the recommendations are pretty clear here.

- Apparmor / whitelisting for the glassfish application and it's associated java applets
- Aggressive permissions schema, authentication based ACL (preferably token based)
- Agressive firewall measures 
- Congifuration hardening, both for apache and glassfish as well as the reverse proxy that would probably be running in that set up. 
- And of course a web application and or dbms firewall. (Mod-security, greensql or if you want to buy an appliance etc..)


However, that's a very finite scenario and one I'd wager most people on this forum aren't running. So truthfully, documentation is good, but it can't cover every single usage  or purpose each person will have.

That's why we have forums ;-)

---

### Post by Ms. Daisy on 2012-03-07
> **unspawn said:**
> 
No I don't but it will take me more time than I have right now to explain. I do commend you for writing the page though, it certainly is helpful, usable and something I could refer to (even though we have a [README]("http://rkhunter.cvs.sourceforge.net/viewvc/rkhunter/rkhunter/files/README"), [FAQ]("http://rkhunter.cvs.sourceforge.net/viewvc/rkhunter/rkhunter/files/FAQ") and [manual]("http://sourceforge.net/apps/trac/rkhunter/wiki/SPRKH")).
(FWIW I'd say I was the editor of the "did i get owned" page. Dangertux wrote it.) I hope you will explain when you do have more time.

---

### Post by Ms. Daisy on 2012-03-07
> **unspawn said:**
> At least linking to [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) in the introductory paragraph could be helpful IMHO. 
I see your point. [https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned](https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned) now links back to basic security.

---

### Post by delta410 on 2012-03-12
First, thank you all for responding. I very much appreciate your help.

Second, manually going through log files as described on the Did I Just Get Owned page to detect anomalies won't work for me. My eyes glaze over when I'm looking at line after line of log output. That's just the way my brain is wired. 

In other words, I need a GUI-based solution that works automatically, like Norton or Comodo does in Windows. But without the bloatiness, the unasked-for apps and the adware!

Also, how does one configure gufw to run when the system boots up? There seems to be no such option in any of the menus.

---

### Post by Ms. Daisy on 2012-03-12
> Also, how does one configure gufw to run when the system boots up? There seems to be no such option in any of the menus.
gufw is just the GUI for ufw.  You launch gufw from the dash (if you're running 11.04 or 11.10). Just type in "firewall" or "gufw" and it will pop up.  You can add the icon to your launcher to find it easier.  But as long as ufw is enabled, then your firewall will start upon boot.

I don't know about an automated log reader.  You could probably grep for stuff in terminal, but that's about as far away from a GUI as it gets.

---

