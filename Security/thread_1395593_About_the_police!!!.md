---
title: "About the police!!!"
date: 2010-02-01
forum: Security
---

### Post by westony on 2010-02-01
I wanted to ask are the police able to get in my PC behind my back and wouldn't even know about their visit /like Windows, after they gave their source code to the police/ and do I am able to stop them seeing my PC ?!

Thanks in advance!

---

### Post by lisati on 2010-02-01
If you're worried about people getting into your computer from the internet, you might want to check out [this web site]("https://www.grc.com/x/ne.dll?bh0bkyd2"), which does some tests of and reports back to you what it finds.

---

### Post by westony on 2010-02-01
> **lisati said:**
> If you're worried about people getting into your computer from the internet, you might want to check out [this web site]("https://www.grc.com/x/ne.dll?bh0bkyd2"), which does some tests of and reports back to you what it finds.
I cant understand this web that you gave it to me ...

well i am worried about are the police have source code for getting in my pc ?! or i can block them!

---

### Post by lisati on 2010-02-01
> **westony said:**
> I cant understand this web that you gave it to me ...

well i am worried about are the police have source code for getting in my pc ?! or i can block them!

The police probably don't have source code to get into your computer. Some information on computer security when using Ubuntu can be found here: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by westony on 2010-02-01
thank you! :)

---

### Post by schauerlich on 2010-02-01
In before mercy lock.

---

### Post by mikewhatever on 2010-02-01
> **westony said:**
> I wanted to ask are the police able to get in my PC behind my back and wouldn't even know about their visit /like Windows, after they gave their source code to the police/ and do I am able to stop them seeing my PC ?!

Thanks in advance!

Yeah, they can, and there is nothing you can do about it. The big brother is always watching, so don't do anything stupid.

---

### Post by adam814 on 2010-02-01
There's a much better chance law enforcement has the source code for Linux than Windows.  That's kind of the point of open-source software.  You can get it too.

I honestly doubt they'd waste their time "getting into your computer using the source code."  Even assuming the best-case that they've convinced enough kernel developers to hide a rootkit for them in the Linux kernel they'd have to train officers to use it.  It's probably easier to get a search warrant and confiscate your computer than bother with it.

The best advice I could give is to be aware of the laws in your particular jurisdiction and don't do anything illegal.

---

### Post by westony on 2010-02-01
well is there someway to prevent getting in my pc ?!

---

### Post by JoeWheeler on 2010-02-01
Yes don't do anything illegal and they won't want to get in your pc!

In terms of hackers/viruses just don't do any stupid downloads and be wary of email attachments

---

### Post by bodhi.zazen on 2010-02-01
What do you mean by "Getting in" ??

If someone has physical access they have full access to your machine.

The only prevention you can try is encryption, but that will only protect your data.

In terms of remote access, if you are running a server, they learn to secure it.

Start with the security sticky at the top of these forums.

---

### Post by jflaker on 2010-02-01
> **westony said:**
> I wanted to ask are the police able to get in my PC behind my back and wouldn't even know about their visit /like Windows, after they gave their source code to the police/ and do I am able to stop them seeing my PC ?!

Thanks in advance!

Generally, if you are connected directly to your broadband modem, your system if 100% accessible from the internet and WILL be subject to hacking.  If you are behind a router, it is not impossible, but VERY unlikely your system can be accessed from the outside.

One thing to note is that in order for you computer to be covertly accessed, you computer must be listening on a tcp/ip port....This port is opened by a process...know your processes.  

The other thing that is possible is that your computer has malware which MAY include the ability to capture keystrokes and other information and report them to a remote server.  This would require that a process run in the background either continually or via a scheduled job *(cron).  

Know your processes and what they are doing....if you are unfamiliar with a process, you can likely kill it without issue.  

If you are still suspicious about what your system is doing behind your back, you can save your data *(don't forget your hidden folders) and reload your computer so that you are 100% sure things that are running are what should be running.

As for physical access *(at least in the USA)....If police were going to physically access your system, they would first need a search warrant and if they have a search warrant...they are likely going to seize your system for analysis.  

If you have done nothing wrong, police will not be wasting their time.

---

### Post by -__- on 2010-02-02
> **westony said:**
> I wanted to ask are the police able to get in my PC behind my back and wouldn't even know about their visit /like Windows, after they gave their source code to the police/ and do I am able to stop them seeing my PC ?!

Thanks in advance!

creepy.

---

### Post by NickJones on 2010-02-02
Yes. They can. But chances are if you are downloading kiddie porn, hacking into root nameservers, or doing any really bad stuff like that, the police will come to your house and take your PC. All Internet traffic can be easily viewed via your ISP, and if you do get your computer taken from you by the police chances are your data will be *easily* accessible.
If you are downloading torrented movies, don't worry, the chance of you getting prosecuted is so small it's not funny, if you are doing really illegal stuff, then don't do it :D
Nick

---

### Post by diablo69er on 2010-02-02
Speaking of torrents...I've gotten 3 letters so far, one from the RIAA, FOX, and whoever made Mr and Mrs Smith years ago.  Anywho for the most part it's just scare tactics.  Not to mention they can't prove your the one downloading anything.  A IP doesn't mean jack **** as far as a court case is concerned.  I say this because it's not uncommon for hackers to compromise a system and use it as a seed box or something similar.

Now back on topic with the police.  Depending on which agency is after you..  Either way I use to have my pc encrypted at boot, as well as the home directory being encrypted.  All my email messages were encyrpted, but that's really pushing it.  The average user really doesn't need to go that far.

Might I suggest trucrypt ;)

---

### Post by westony on 2010-02-02
The thing i ask is. How to prevent OUT SIDE GETTING IN TO MY FILES WITHOUT MY KNOWN/get in HIDE/

---

### Post by bodhi.zazen on 2010-02-02
> **westony said:**
> The thing i ask is. How to prevent OUT SIDE GETTING IN TO MY FILES WITHOUT MY KNOWN/get in HIDE/


As long as your computer is turned on and connected to the internet there is a chance somebody can access your files. This is true of any operationg system.

For the vast majority of Desktop users, just do two things:

1. Get a router. Do not connect your computer directly to the internet.

2. Use strong passwords.

For extra credit, be sure to secure physical access. For most home users, desktops aer a non-issue. If you use a Laptop I suggest you encrypt the entire system.

If you run servers, such as samba or apache, or if you want to go beyond that you will need to read and learn how to harden your OS.

See:

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

[Securing Debian Manual]("http://www.debian.org/doc/manuals/securing-debian-howto/") 

The arguments that closed source is more or less secure then open source is a recurring discussion with opinions on both sides. In practice, as a recent pwn to own, of 3 computers, Windows, OSX, and Ubuntu, after 3 days, only the Ubuntu box was uncracked.

[http://dvlabs.tippingpoint.com/blog/2008/03/28/pwn-to-own-final-day-and-wrap-up](http://dvlabs.tippingpoint.com/blog/2008/03/28/pwn-to-own-final-day-and-wrap-up)

> So at the end of the last day of the contest, only the Sony VAIO laptop  running Ubuntu was left standing. The concern the government or police are after you is tin foil hat conspiracy theory stuff or illegal activity, neither of which is supported here.

Please see: [http://zapatopi.net/afdb.html](http://zapatopi.net/afdb.html)


Otherwise this thread is closed. If you have a specific question, please ask.

---

