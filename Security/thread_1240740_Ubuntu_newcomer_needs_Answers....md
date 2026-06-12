---
title: "Ubuntu newcomer needs Answers..."
date: 2009-08-15
forum: Security
---

### Post by thegutterpoet on 2009-08-15
I have finally moved over from Win XP to a linux OS, the ubuntu 9.0.4 offering, to be exact. Everything looks and runs so smoothly, and I am mightily impressed.

Now I have all the basics working, I am focusing on Security...

Do I need to download and install a firewall and anti virus???
if so, which are recommended...for a man whose coding skills stretch only as far as copy, paste and edit.

I do plan on using the bit torrent program, so its best for me to have something secure...but truly, i have no idea how secure the basic ubuntu installation is in its naked form? how easy it is to hack?? to infect???

any help is greatly appreciated...

(and PS...is there a MSN clone which looks and behaves similar to MSN Messenger?)

---

### Post by Nburnes on 2009-08-15
Firewall is already installed and I don't see any reason to get AV unless you are sending or forwarding messages to Windows machines.

---

### Post by thegutterpoet on 2009-08-15
Thanks for clearing that up mate, and NO, I have no plans of engaging Windows Machines as you warned...

---

### Post by alenis on 2009-08-15
Firewall (iptables) is already installed but it seems to me that the default configuration allows for all traffic. However, if you don't run servers on your box, this should not be a problem. To configure it you may use a GUI as Firestarter.
I would install NoScript in Firefox to prevent damages from malicious javascripts.

---

### Post by sasho_zl on 2009-08-15
There is a BIG sticky thread on the top of the security discussions. Read it.
And also if you haven't downloaded the "Ubuntu Pocket Guide" yet, I suggest you do - [http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)
because it has a lot of good explanations about how Linux works in general including security.

---

### Post by rookcifer on 2009-08-15
> **weedguru said:**
> Do I need to download and install a firewall and anti virus???

As for AV -- absolutely not.  The words "anti-virus" can now safely be deleted from your vocabulary.

As for a firewall, it is probably a good idea to utilize UFW if you are not behind a router.  If you are behind a router, then I suggest you turn off the Ubuntu firewall as it will be superfluous. 

> I do plan on using the bit torrent program, so its best for me to have something secure...but truly, i have no idea how secure the basic ubuntu installation is in its naked form? how easy it is to hack?? to infect???

Use transmission as your client and, if you are really paranoid, give it an apparmor profile.  See the apparmor sticky for more info.  A couple of guys on here have already made transmission profiles and have made them available.

> (and PS...is there a MSN clone which looks and behaves similar to MSN Messenger?)

Pidgin, which comes with Ubuntu, can do all of the major IM protocols -- AIM, Yahoo, MSN, Jabber, etc..  Give it a try first, and if it doesn't do what you want, then I believe there is a MSN clone available in the repos.

---

### Post by Whiffle on 2009-08-15
Actually Ubuntu has iptables (the firewall) installed by default, but it is not configured, so it doesn't actually do anything. 

But, Ubuntu doesn't open any ports to the outside world by default, so a firewall would be redundant.

---

### Post by scorp123 on 2009-08-15
> **weedguru said:**
> i have no idea how secure the basic ubuntu installation is in its naked form? Very secure.

> **weedguru said:**
>  how easy it is to hack?? Very hard. 

Unless you start running server programs and open those to the outside world ... Web servers maybe? OpenSSH-server maybe? A mail server maybe? As soon as you start doing such things then you *might* be at risk of inviting potential intruders, especially if you don't really know what you are doing ... But that's another topic (e.g. server security).

But "out of the box" Ubuntu does not run any such program so a wannabe intruder has absolutely _NOTHING_ he could hope to connect against over the network. In such a case you won't even need a firewall. What is a firewall supposed to protect if no networked service is even running?

> **weedguru said:**
> to infect??? Extremely hard if not impossible. Linux's internal organisation is entirely different from Windows. The standard strategies of viruses (e.g. go and infect the first binary you encounter, go on and spread from there ...) fail here because on a Linux file system all the program binaries are stowed away in separate directories (such as "/usr" ) and your normal user account does not even have any write permissions there ... So a virus would "starve" because it has nothing it can infect. 

This does not mean though that Linux is "100% safe from all evil". What is a security problem here are human hackers and crackers who sometimes manage to hijack Linux servers. But again ... server security is a different topic.

> **weedguru said:**
> is there a MSN clone which looks and behaves similar to MSN Messenger?aMSN.

---

### Post by lisati on 2009-08-15
Have a look here: [http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

---

### Post by cprofitt on 2009-08-16
You can enable the firewall very easily...

sudo ufw default deny
sudo ufw enable

If you need more you can take a look at the help article I contributed too - [here]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw")

---

### Post by craig10x on 2009-08-16
> **cprofitt said:**
> You can enable the firewall very easily...

sudo ufw default deny
sudo ufw enable

If you need more you can take a look at the help article I contributed too - [here]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw")

Or, you can simply go to add/remove programs and add "gufw" which adds the the gui interface to your applications list on top,  for the ubuntu firewall.... ;)

And you will be able to turn it on and also do more selective "configuring" if you wish....
That's the way i did it....i just turned it on and didn't do anything extra to it.....

---

### Post by HermanAB on 2009-08-16
Howdy,

Note that the UFW firewall isn't really needed unless you are running servers that outsiders can connect to and even then, is not much use.  

There is nothing magic about a Linux firewall and generally you don't need it.  I have run my email and web servers on the wild wild web for years, without any firewall rules.  Linux firewalls typically have oodles of special rules that address network stack bugs that were resolved many years ago already and which are now quite unnecessary.  That is why Ubuntu ships with the packet filter disabled.

A firewall is mainly a Windows thing, because MS runs many undocumented and poorly implemented services by default.

---

### Post by scorp123 on 2009-08-16
> **HermanAB said:**
>  A firewall is mainly a Windows thing, because MS runs many undocumented and poorly implemented services by default. Exactly. Any Windows installation by default has tons of networked services open that by todays standards are so totally not needed. But instead of getting rid of those stupid services and _really_ fixing Windows, Microsoft "educated" its users that they "absolutely" need a firewall "or else .... "

"I need a firewall or else my PC will crash and burn" ... that's Windows thinking. One can safely let go of that.

---

