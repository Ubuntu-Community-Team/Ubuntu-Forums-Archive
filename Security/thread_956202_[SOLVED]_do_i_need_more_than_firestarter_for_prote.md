---
title: "[SOLVED] do i need more than firestarter for protection?"
date: 2008-10-23
forum: Security
---

### Post by natedogg23 on 2008-10-23
i just started using it a few days ago and was downloading before i had it. should i do something to clear out anything that mite be messing with my pc from weeks ago other than clear private data from the browser? ive only had the net for less than2 months and have had ubuntu the whole time

---

### Post by hyper_ch on 2008-10-23
do you need firestarter at all? In most cases you don't...

---

### Post by taqkavar on 2008-10-23
Strong passwords and good permissions if there are users other than you? Are you a server or something? if it is a personal desktop behind a router you don't need anything. If you are not behind a router, use good passwords. other than that, no need for anything.

---

### Post by sethvath on 2008-10-23
Who and what do you want to protect against? If its the snooping arms of Homeland Security a firewall is not enough to keep them out. 

Most viruses and malware? Ubuntu is safe against them without a firewall.

---

### Post by Sef on 2008-10-23
Ubuntu comes with a firewall installed by default.  It is called IP Tables, which is a command line firewall.  Firestarter is simply a GUI (mouse driven) front end for it.

---

### Post by mcduck on 2008-10-23
> **Sef said:**
> Ubuntu comes with a firewall installed by default.  It is called IP Tables, which is a command line firewall.  Firestarter is simply a GUI (mouse driven) front end for it.

..and that firewall does absolutely nothing by default. You still need to give it some rules to work with, either by hand, by UFW,  or by installing some other configuration tool.

Not that most people would really need to enable the firewall. With no programs listening to incoming traffic there's no need to run a firewall.

---

### Post by bryncoles on 2008-10-23
ubuntu comes with a firewall as standard (if you're on hardy heron). its not ip tables - they're (as i understand it) the things the firewall governs. the firewall is called... UFW - 'uncomplicated firewall'. 

UFW, or firestarter, are used to set the rules (in ip tables) which govern what and how you can access the internet. out of the box, tehres nothing which is trying to access the internet, so as far as i understand it, there are no ip tables rule set up, both nothing listening or ignoring any ports anyway. you'll want to start p[laying with firewalls when you start playing with torrents, servers and so forth (i think). 

im no expert though, so read more on security here:

[http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)
[http://ubuntuforums.org/showthread.php?t=671604](http://ubuntuforums.org/showthread.php?t=671604)
[http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741)

---

### Post by hyper_ch on 2008-10-23
> **mcduck said:**
> You still need to give it some rules to work with,
It works perfectly in its default state on Ubuntu and doing exactely what it should - letting pass everything ;)

> **mcduck said:**
> Not that most people would really need to enable the firewall. With no programs listening to incoming traffic there's no need to run a firewall.
+1

> **bryncoles said:**
> ubuntu comes with a firewall as standard (if you're on hardy heron). its not ip tables - they're (as i understand it) the things the firewall governs. the firewall is called... UFW - 'uncomplicated firewall'.
Nope, the "firewall" is iptables. UFW just alters how iptables works. So ufw is nothing but a simple configuration tool for iptables.

---

### Post by eragon100 on 2008-10-23
If you want an easy firewall with a GUI, i recommend you install GUFW.

Latest version can be obtained from getdeb.net:

[http://www.getdeb.net/app/gufw](http://www.getdeb.net/app/gufw)

You probably don't need a firewall tough. :wink:

---

### Post by hyper_ch on 2008-10-23
gufw is no firewall!

---

### Post by muteXe on 2008-10-23
> **eragon100 said:**
> If you want an easy firewall with a GUI, i recommend you install GUFW.

Latest version can be obtained from getdeb.net:

[http://www.getdeb.net/app/gufw](http://www.getdeb.net/app/gufw)

You probably don't need a firewall tough. :wink:

wtf?  It's a firewall manager not a firewall.

---

### Post by iKonaK on 2008-10-23
hello, i had this question myself a while ago, here's some tips:
1. install firestarter, open it and go trough the menu
2. test your pc @ [http://www.pcflank.com](http://www.pcflank.com)
3. install [no script ]("https://addons.mozilla.org/en-US/firefox/addon/722")
4. install [addblock plus]("https://addons.mozilla.org/en-US/firefox/addon/1865")
5. install [refcontrol ]("https://addons.mozilla.org/en-US/firefox/addon/953")
6. install [cookie safe ]("https://addons.mozilla.org/en-US/firefox/addon/2497")
-assuming you're using firefox...

no , you might not need all this but take a look on them and decide for yourself ;)

---

### Post by eragon100 on 2008-10-23
> **muteXe said:**
> wtf?  It's a firewall manager not a firewall.

True, but it is a frontend for iptables, which comes with ubuntu by default. So it will work without problem.

---

### Post by the8thstar on 2008-10-23
> **eragon100 said:**
> If you want an easy firewall with a GUI, i recommend you install GUFW.

Latest version can be obtained from getdeb.net:

[http://www.getdeb.net/app/gufw](http://www.getdeb.net/app/gufw)

You probably don't need a firewall tough. :wink:

*gufw* is in the repos.

---

### Post by eragon100 on 2008-10-23
> **the8thstar said:**
> *gufw* is in the repos.

Yes, but that's not the latest version, is it?

---

### Post by sethvath on 2008-10-23
> **hyper_ch said:**
> 

Nope, the "firewall" is iptables. UFW just alters how iptables works. So ufw is nothing but a simple configuration tool for iptables.

To the 3 people arguing about schematics of which is a firewall and what not:

iptables - firewall
ufw - command based firewall manager
gufw - gui front-end to ufw

---

### Post by the8thstar on 2008-10-23
> **eragon100 said:**
> Yes, but that's not the latest version, is it?

Hmm, I have Gufw 0.20.4 here. You?

---

### Post by hyper_ch on 2008-10-23
> **sethvath said:**
> To the 3 people arguing about schematics of which is a firewall and what not:

iptables - firewall
ufw - command based firewall manager
gufw - gui front-end to ufw

I know what it is but a lot of people don't :)

---

### Post by the.phantom on 2008-10-23
i run two rootkit hunters to get that warm and fuzzy feeling

a while ago someone posted how to do it and this is what i did


install chroot and rt hunter.............................

sudo aptitude install chkrootkit rkhunter


 to run chroot................................

sudo chkrootkit


to update and run rt hunter.................

sudo rkhunter --update && sudo rkhunter -c -sk

---

### Post by bodhi.zazen on 2008-10-23
> **natedogg23 said:**
> i just started using it a few days ago and was downloading before i had it. should i do something to clear out anything that mite be messing with my pc from weeks ago other than clear private data from the browser? ive only had the net for less than2 months and have had ubuntu the whole time

The bottom line, only you can determine your security needs.

I suggest you start with these links :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

[[all variants] Intrusion Detection - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=919472") 

If you are running a desktop behind a router you are probably just fine. If you are running a public server you should learn to secure it. Securing your server is more then running firestarter.

I suggest you do not run firestarter as it is outdated, no longer maintained, and a security risk (it runs as root).

+1 UFW. If you must have a gui check out GUFW. Both applications configure iptables which is the actual firewall.

---

### Post by kevdog on 2008-10-23
I had no idea firestarter ran as root (I don't use it).  But wouldn't ufw have to run as root also? I mean the netfilter svc runs as root (its part of the kernel), and to modify the iptables you need to be root?  I don't seem to get the difference.

---

### Post by bodhi.zazen on 2008-10-23
> **kevdog said:**
> I had no idea firestarter ran as root (I don't use it).  But wouldn't ufw have to run as root also? I mean the netfilter svc runs as root (its part of the kernel), and to modify the iptables you need to be root?  I don't seem to get the difference.

Yes, I should have been more clear. Firestarter runs as root and has a security hole that allows escalation of privileges ie root access to crackers.

gufw and ufw do not have the same security hole as firestarter.

---

### Post by natedogg23 on 2008-10-23
im not a server or anything. just a guy who didnt have the net for 8 yrs and wants to make sure i dont mess thing thing up by not having something running that i should when downloading watching streams or just surfing. i take it all i need to do is nothing. thank u all i appreciate any advice im only in my 6th week or so of ubuntu and the internet

---

### Post by kevdog on 2008-10-23
Interesting

When was the Firestarter security hole found?  Seems like this should be more widely advertised on this forum since this seems to be the most predominate method of interacting with the iptable/netfilter firewall.

---

### Post by nubdora on 2008-10-23
> **kevdog said:**
> Interesting

When was the Firestarter security hole found?  Seems like this should be more widely advertised on this forum since this seems to be the most predominate method of interacting with the iptable/netfilter firewall.

The main reason it is predominant on these forums is because many websites, other forums, and technical books suggest Firestarter as a good IP Tables Config for beginner's in relation to new Ubuntu users. With pulled support, the service running as root, and other known security problems, Firestarter is not an ideal IP Tables config for beginner's - for any one. Yet, it still receives praises and positive criticism. Conspiracy? I wonder.

---

### Post by bodhi.zazen on 2008-10-23
> **nubdora said:**
> The main reason it is predominant on these forums is because many websites, other forums, and technical books suggest Firestarter as a good IP Tables Config for beginner's in relation to new Ubuntu users. With pulled support, the service running as root, and other known security problems, Firestarter is not an ideal IP Tables config for beginner's - for any one. Yet, it still receives praises and positive criticism. Conspiracy? I wonder.

+10

Not a conspiracy but really a lack of a good GUI for iptables. I know there are some guis, but nothing "simple" that harnesses the power of iptables (including NAT configuration, logging, blocking after so many log in attempts ...).

UFW is a step in the right direction, but new users are reluctant to use the command line, no matter how easy it may be. Hopefully GUFW will be a better solution.

Both UFW and GUFW fail, IMO, in that they do not yet allow easy access to the full power of IPTables.

Plus there are a number of ardent firestarter supporters ...

---

### Post by OrangeCrate on 2008-10-23
> **bodhi.zazen said:**
> Yes, I should have been more clear. Firestarter runs as root and **has a security hole that allows escalation of privileges ie root access to crackers**.

gufw and ufw do not have the same security hole as firestarter.

Cite a source please?

And, didn't we already have a conversation regarding Firestarter in this thread?

[http://ubuntuforums.org/showthread.php?t=914869&page=2](http://ubuntuforums.org/showthread.php?t=914869&page=2)

As of right now, I haven't changed my position, but, I'd be happy to, if you can put some meat into your comment above...

---

### Post by OrangeCrate on 2008-10-23
> **kevdog said:**
> Interesting

When was the Firestarter security hole found?  Seems like this should be more widely advertised on this forum since this seems to be the most predominate method of interacting with the iptable/netfilter firewall.

Agreed.

Nor do I find any information about it in the Ubuntu documentation, which was updated of 10/7/08.

[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

---

### Post by bodhi.zazen on 2008-10-23
> **OrangeCrate said:**
> Cite a source please?

And, didn't we already have a conversation regarding Firestarter in this thread?

[http://ubuntuforums.org/showthread.php?t=914869&page=2](http://ubuntuforums.org/showthread.php?t=914869&page=2)

As of right now, I haven't changed my position, but, I'd be happy to, if you can put some meat into your comment above...

Do a google search and you will find many references. As I have said, you are free to use firestarter if you wish, but it is outdated and falling out of favor.

---

### Post by OrangeCrate on 2008-10-23
> **bodhi.zazen said:**
> D**o a google search and you will find many references.** As I have said, you are free to use firestarter if you wish, but it is outdated and falling out of favor.

All right, I've done several search strings on Google, that relate to your statement, and frankly, I'm not finding anything other than you, trashing Firestarter.

Can you specifically cite a source to back-up your statement, or not?

> Firestarter runs as root and **has a security hole that allows escalation of privileges ie root access to crackers**.

I've supplied sources to back up my statements, including Ubuntu documentation, so I'm comfortable with my position. However, as stated in both threads, I'd be happy to change my mind, if you can supply tangible evidence that I am wrong in my opinion, which I detailed in the other thread.

---

### Post by OrangeCrate on 2008-10-23
> **bodhi.zazen said:**
> The bottom line, only you can determine your security needs.

I suggest you start with these links :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

[[all variants] Intrusion Detection - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=919472") 

If you are running a desktop behind a router you are probably just fine. If you are running a public server you should learn to secure it. Securing your server is more then running firestarter.

**I suggest you do not run firestarter as it is outdated, no longer maintained, and a security risk **(it runs as root).

**+1 UFW. If you must have a gui check out GUFW. Both applications configure iptables which is the actual firewall.**

Firestarter's documentation was last updated on 12/18/07, the site is copyrighted through 2007, and all of the contact links are live to the developer, and the the company. So, if it quacks like a duck...

[http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)

Personally I think there are very valid reasons why people continue to recommend Firestarter, why it's in our repositories, and why there's formal Ubuntu documentation on the package.

It is obvious, that you're a big fan of UFW, but I would hope, since Linux is all about choices, that you would accurately represent alternatives to your personal choice.

Again, though I personally don't have it installed myself - I don't run a server, I'm quite satisfied with recommending Firestarter to security conscious users, particularly, those fresh from Windows, that would simply want a configured firewall, and are uncomfortable with the command line.

Firestarter is nothing more, that a simple GUI, with simple instructions to configure iptables. It's a finished product, that requires little updating to be effective.

However, as I've stated several times, when I'm shown that it is no longer a viable option, I'll drop it like a hot potato. But so far, with all due respect to your multiple comments to the contrary, I haven't seen any reason to do that.

---

### Post by kevdog on 2008-10-24
I'm in no position to demand an explanation from anyone on this matter.  I'm a neophyte in configuring iptables, and I don't even use firestarter.  I did take up this challenge and did a search for possible security risks when using firestarter

I used only google and google groups as my starting references.  I searched under the terms "firestarter security risk", "firestarter risks", "firestarter security", "firestarter hole", "firestarter security hole".  Needless to say I only found to posts on the debian archive forum that tangentially touched on a security risk.  This is a summary from 2005:
[http://groups.google.com/group/linux.debian.maint.firewall/browse_thread/thread/4b48b9a4151f5101/460c5091db9ed14e?hl=en&lnk=st&q=firestarter+risk#460c5091db9ed14e](http://groups.google.com/group/linux.debian.maint.firewall/browse_thread/thread/4b48b9a4151f5101/460c5091db9ed14e?hl=en&lnk=st&q=firestarter+risk#460c5091db9ed14e)

Again, I am no proponent of firestarter.  Interaction with firestarter DOES require admin privileges -- kind of a clumsy interface.  I can't speak of ufw/gufw, however I do wish this project great success.  This is definitely an area that has great possibility for advancement.

---

### Post by OrangeCrate on 2008-10-24
^,

Thanks for doing that. That's pretty much the same results I got, though your link didn't even show up in my searches.

I don't  currently use Firestarter either, but I do recommend it. In the past, I have had it installed several times, and I'm quite familiar with it's setup, and usage.

In another life, I was a bit of a Guru on Windows security, and I'm continually coaching  users from that community, who either want to convert to Linux, or at least try it. As you would expect, the subjects of firewalls, antivirus programs, and spyware scanners come up often.

Edit:

BTW, I was editing, for effect, on the post right above yours, when you posted. You might want to give it a reread...

---

### Post by nubdora on 2008-10-24
Because a site is online does not mean it nor the content it pertains to is maintained. In the world of technology, especially computer security, I would not use an application, in most circumstances, that looks like it has not been updated for a year. Copyright lengths are difficult to determine since some have a set number of years while many are renewed every year. Also, using the 2.6 kernel as an argument is not a strong one since the 2.6 kernel was released December 17, 2003.

---

### Post by OrangeCrate on 2008-10-24
> **nubdora said:**
> Because a site is online does not mean it nor the content it pertains to is maintained. In the world of technology, especially computer security, I would not use an application, in most circumstances, that looks like it has not been updated for a year. Copyright lengths are difficult to determine since some have a set number of years while many are renewed every year. **Also, using the 2.6 kernel as an argument is not a strong one since the 2.6 kernel was released December 17, 2003.**

You're absolutely correct regarding the age of the kernel. A lapse of memory on my part, and I've removed that comment. Thanks.

---

### Post by hyper_ch on 2008-10-24
OrangeCrate:

And for what reasons do you recommend firestarter at all? why do you think it's even needed to alter default iptables rules?

---

### Post by OrangeCrate on 2008-10-24
> **hyper_ch said:**
> OrangeCrate:

And for what reasons do you recommend firestarter at all? why do you think it's even needed to alter default iptables rules?

I don't recommend one, because as we both know, it's not needed.

But, new converts, particularly those who know a great deal about Windows security, are a tough sell. Some don't seem to understand that if they're not running stealth on all ports, they're not vulnerable.

So, if they want to stealth all their ports, and not respond to someone pinging them, and they want to sit and watch hits from the big bad world, on some kind of detector, I really don't care, and I suggest that if they want to configure iptables, so they can do all of that, Firestarter would be a good option.

And I don't find anything on the web, that tells me that my recommendation is wrong. What I am, is a bit tired of random, negative comments regarding the effectiveness of Firestarter, or any other program for that matter, that aren't backed up with facts.

---

### Post by lovinglinux on 2008-10-24
> **bodhi.zazen said:**
> Yes, I should have been more clear. Firestarter runs as root and has a security hole that allows escalation of privileges ie root access to crackers.

gufw and ufw do not have the same security hole as firestarter.

I would like to understand this better. I'm starting to use command-line to add some iptables rules, but I still use Firestarter to generate a basic configuration, with all ports closed and limited outbound traffic. I don't run Firestarter gui anymore. Whenever I need to reset the iptables to my basic configuration I stop and start Firestarter from command-line. Whenever I need to open a port or allow specific outbound traffic I do it with iptables commands. 

As far as I understand, when you run "firestarter --start" it just insert the iptables rules and there is nothing else running in the background right? So, if I'm not running Firestarter gui could my system be affected by those security holes? The problem with Firestarter is related to the gui running as root or the rules it creates in the iptables that are weak?

I don't like ufw/gufw because it doesn't allow to change outbound traffic, while Firestarter does. Besides, ufw creates some additional iptables chains that I don't know how to modify with command-line. So, I'm stuck with Firestarter until I learn how to create all rules I need with command-line.

---

### Post by hyper_ch on 2008-10-24
> **OrangeCrate said:**
> So, if they want to stealth all their ports, and not respond to someone pinging them, and they want to sit and watch hits from the big bad world, on some kind of detector, I really don't care, and I suggest that if they want to configure iptables, so they can do all of that, Firestarter would be a good option.

They want security and they think they must run a firewall and stealth everything... by recommending firestarter or ufw you just "cure symptoms" and not the underlaying problem of having "the wrong idea on security".

That why I ask as to way they want to "install a firewall".

---

### Post by bodhi.zazen on 2008-10-24
> **lovinglinux said:**
> I would like to understand this better. I'm starting to use command-line to add some iptables rules, but I still use Firestarter to generate a basic configuration, with all ports closed and limited outbound traffic. I don't run Firestarter gui anymore. Whenever I need to reset the iptables to my basic configuration I stop and start Firestarter from command-line. Whenever I need to open a port or allow specific outbound traffic I do it with iptables commands. 

As far as I understand, when you run "firestarter --start" it just insert the iptables rules and there is nothing else running in the background right? So, if I'm not running Firestarter gui could my system be affected by those security holes? The problem with Firestarter is related to the gui running as root or the rules it creates in the iptables that are weak?

I don't like ufw/gufw because it doesn't allow to change outbound traffic, while Firestarter does. Besides, ufw creates some additional iptables chains that I don't know how to modify with command-line. So, I'm stuck with Firestarter until I learn how to create all rules I need with command-line.

Yes, that is the problem with firestarter, running the gui, worse if running it all the time.

In my experience Firestarter often fails as you start to build complex rule sets and are using NAT.

The "nice" thing about UFW , IMO, on the command line, is that you will start to understand how iptables works.

I think you would like the commands "iptables-save" and "iptables-restore"

What you do is set up your rules and then :

```
sudo bash -c " iptables-save > /root/firewall.rules"
```

Then to restore those rules

```
sudo bash -c "iptables-restore < /root/firewall.rules"
```

---

### Post by lovinglinux on 2008-10-24
> **bodhi.zazen said:**
> Yes, that is the problem with firestarter, running the gui, worse if running it all the time.

In my experience Firestarter often fails as you start to build complex rule sets and are using NAT.[/code]

I have no server running, my desktop is wired to the router and I have a notebook connected by wireless. That is my local network. So I guess those issues won't be a problem, right?

> **bodhi.zazen said:**
> The "nice" thing about UFW , IMO, on the command line, is that you will start to understand how iptables works.

Can you make outbound traffic restrictive like Firestarter? This sounds useless, but I like to have full control of my network traffic.

> **bodhi.zazen said:**
> I think you would like the commands "iptables-save" and "iptables-restore"

What you do is set up your rules and then :

```
sudo bash -c " iptables-save > /root/firewall.rules"
```

Then to restore those rules

```
sudo bash -c "iptables-restore < /root/firewall.rules"
```

So, let's assume I have created my own rules or replicated all rules created by Firestarter. If I use those commands above I can uninstall Firestarter and just modify rules that I need temporarily,[[COLOR="Red"] for example to open a port or change outbound policy[/COLOR]]("http://ubuntuforums.org/showthread.php?p=6027716#post6027716")? If I don't use iptables-save after adding new rules, when I restart I will allways get my basic rules back right?

---

