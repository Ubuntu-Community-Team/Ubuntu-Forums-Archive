---
title: "TOR and Viruses"
date: 2010-03-03
forum: Security
---

### Post by Richiegs on 2010-03-03
I am using Ubuntu 9.10 in my computer. Yesterday, I tried to connect to the Internet using Tor. After that I ran Virus Scanner, I was surprised that it detected 3 viruses such as A0013641.exe and A0015759.exe.

I wonder if my computer got these viruses through Tor because I was connected to Russia, Germany and Denmark?

Thanks

---

### Post by Soul-Sing on 2010-03-03
Do you use Wine?

---

### Post by cdenley on 2010-03-03
Simply connecting to the TOR network will not result in viruses. What you do using the tor network very well may, though.

---

### Post by Sef on 2010-03-03
> After that I ran Virus Scanner, I was surprised that it detected 3  viruses such as A0013641.exe and A0015759.exe.Windows malware will not affect your Linux System.

---

### Post by Objekt on 2010-03-03
Ubuntu 9.10 comes with a virus scanner?

---

### Post by handy on 2010-03-03
See post # 4.

Done finished.

Unless of course you are serving files to windows machines. Under such circumstances you need to be checking the data for viruses on behalf of your clients, not for the benefit of your own Linux system.

---

### Post by Richiegs on 2010-03-03
> **leoquant said:**
> Do you use Wine?

No, I don't use Wine.

---

### Post by Richiegs on 2010-03-03
> **cdenley said:**
> Simply connecting to the TOR network will not result in viruses. What you do using the tor network very well may, though.

I was surfing the web like I always do, except I wanted to try out Tor.

---

### Post by Richiegs on 2010-03-03
I connected to Yahoo in Russia when I used Tor. Is it possible my computer picked up the viruses there?

---

### Post by Richiegs on 2010-03-03
How come Virus Scanner did not stop the viruses from infecting my computer? I only found out the presence of viruses when I scanned the hard drive.

---

### Post by handy on 2010-03-03
If you have any viruses on your computer, then they must be attached to windows file format files.

Your Linux system is safe no matter what.

I expect that you don't even have windows viruses, it is just another software anti-virus program malfunction.

---

### Post by Ijan on 2010-03-03
Richilegs: People will have an easier time helping you if you provide:
* What OS were you using browsing the web through the TOR-network? Do you use other OSs next to it?
* What browser?
* What virus scanner?
* Where were the suspicious files found?
> I wonder if my computer got these viruses through Tor because I was connected to Russia, Germany and Denmark?
Generally spreaking, that is unlikely. Viruses usually do attack software more widely used as TOR.

---

### Post by cdenley on 2010-03-03
> **Richiegs said:**
> I connected to Yahoo in Russia when I used Tor. Is it possible my computer picked up the viruses there?

If there is a vulnerability in your browser (or a browser plugin), then it is possible for a malicious site to load a windows virus on your system, but it wouldn't execute. In that scenario, it would also be possible to load linux malware, but linux is rarely targeted with browser exploits. If your tor exit node was operated by someone with malicious intent, it would be possible to inject a malicous script into a website you visit. If you have all security updates installed, then a browser exploit is very unlikely. If you use noscript, then even more unlikely.

---

### Post by Richiegs on 2010-03-03
> **Ijan said:**
> Richilegs: People will have an easier time helping you if you provide:
* What OS were you using browsing the web through the TOR-network? Do you use other OSs next to it?
* What browser?
* What virus scanner?
* Where were the suspicious files found?

Generally spreaking, that is unlikely. Viruses usually do attack software more widely used as TOR.

I was using Ubuntu 9.10 Which was installed in Windows XP.
I used Firefox 3.5.8.
Virus Scanner is Clam TK.

---

### Post by Richiegs on 2010-03-03
Is it possible that my computer picked up those viruses from Google Chrome instead of Firefox? I used both Firefox and Google Chrome at the same time

---

### Post by handy on 2010-03-03
If I thought that I might have picked up a virus, the last place I would come for help is a/this forum.

All an immature computer user is going to get is confused.

The more help the poor person gets, the more anxiety he gets.

As disparity rules here.

---

### Post by Soul-Sing on 2010-03-03
TOR and "virusses"/exe files doesn't make sense on Ubuntu/Linux.( you could alway's download some exe'files via TOR though, but thats not what your doing I presume)
If you are keen on security, TOR has nothing to do with security imo. So I should drop it if you think TOR would secure your computer.( At its very best TOR provides you a layer to protect your privacy.)

Install Hijackthis on your Windows partition, and take a look if these exe's are present in the logs.
And run a antivirusscanner on your wind. partition.

---

### Post by handy on 2010-03-03
> **leoquant said:**
> ...
And run a antivirusscanner on your wind. partition.

I just read your post (& agree completely) when I got to the line quoted above, my mind did a flip of the w in wind, (must be a strange form of dyslexia?) I nearly fell off my chair! :lolflag:

Perhaps I have a virus? ;)

---

### Post by NiGhtMarEs0nWax on 2010-03-04
use a software desktop based firewall with tor even if you are behind a router. .exe are windows executable, they may be infected but they wont run on Linux.

---

### Post by rookcifer on 2010-03-04
> **leoquant said:**
> ( At its very best TOR provides you a layer to protect your privacy.)


Tor does not provide privacy, nor does it claim that it does.  It provides anonymity.  There *is* a difference.

---

### Post by akand074 on 2010-03-04
> **Objekt said:**
> Ubuntu 9.10 comes with a virus scanner?

Ubuntu 9.10 does not come with a virus scanner because Ubuntu (any linux OS at that matter) can not be effected by a virus because they are generally all written for windows and also, you need to be superuser to install anything or do any administrative changes to your computer. So you do not have to worry about viruses at all on your linux system. Don't know about wine but you can easily just remove it with the viruses.

---

### Post by Richiegs on 2010-03-04
> **rookcifer said:**
> Tor does not provide privacy, nor does it claim that it does.  It provides anonymity.  There *is* a difference.

Since Tor provides anonymity, does it mean it is difficult for other people to trace the original source/IP address?

Which software provides the best level of anonymity for Ubunutu?

Thanks

---

### Post by Soul-Sing on 2010-03-04
> **rookcifer said:**
> Tor does not provide privacy, nor does it claim that it does.  It provides anonymity.  There *is* a difference.

I disagree, imho anonymity via TOR is a myth.

---

### Post by cdenley on 2010-03-04
> **leoquant said:**
> I disagree, imho anonymity via TOR is a myth.

What do you mean by that? Connecting to servers through TOR makes it (basically) impossible for anyone with access to that server or unencrypted traffic destined for that server to determine the originating IP. There may be other ways to determine the user's identity if the user doesn't follow the necessary precautions, but that doesn't make anonymity a myth.

---

### Post by Soul-Sing on 2010-03-04
> **cdenley said:**
> What do you mean by that? Connecting to servers through TOR makes it (basically) impossible for anyone with access to that server or unencrypted traffic destined for that server to determine the originating IP. There may be other ways to determine the user's identity if the user doesn't follow the necessary precautions, but that doesn't make anonymity a myth.

I did said anonomity via TOR is a myth, not anonymity in itself.
Although anonymity on the internet in general is a very relative term.
Anonymity is a system, almost a "regime" of measures and restrictions imposed by the user himself.

---

### Post by cdenley on 2010-03-04
> **leoquant said:**
> I did said anonomity via TOR is a myth, not anonymity in itself.
Although anonymity on the internet in general is a very relative term.
Anonymity is a system, almost a "regime" of measures and restrictions imposed by the user himself.

So you agree that TOR can be an important tool for achieving anonymity?

---

### Post by Soul-Sing on 2010-03-04
> **cdenley said:**
> So you agree that TOR can be an important tool for achieving anonymity?

A layer, just a layer as in onions :)

---

### Post by cdenley on 2010-03-04
> **leoquant said:**
> A layer, just a layer as in onions :)

The most important layer, in my opinion. A bit more than a "myth".

---

### Post by TurnOfTide on 2010-03-05
It's because Russians are mad l33t at puting viruses on computers.

---

### Post by Ijan on 2010-03-05
> **rookcifer said:**
> Tor does not provide privacy, nor does it claim that it does.  It provides anonymity.  There *is* a difference.

If your are interested in the Tor projects view on the semantics of those terms you can watch 0:09h-0:10h (or more) of [this](http://mirror.fem-net.de/CCC/26C3/mp4/26c3-3554-de-tor_and_censorship_lessons_learned.mp4), it's the av-recording of [this talk](http://events.ccc.de/congress/2009/Fahrplan/events/3554.en.html).

---

### Post by huangweiqiu on 2010-03-06
> **NiGhtMarEs0nWax said:**
> use a software desktop based firewall with tor even if you are behind a router. .exe are windows executable, they may be infected but they wont run on Linux.
I agree,He installed Ubuntu on Windows,the virus scanned out were Window's that will not hurt Linux

---

### Post by lisati on 2010-03-06
> **Richiegs said:**
> How come Virus Scanner did not stop the viruses from infecting my computer? I only found out the presence of viruses when I scanned the hard drive.

A scanner isn't usually designed to **prevent** the arrival of malware on your system. At best, all you can count on is that it *_might_* **discover** the presence of something potentially nasty and alert you to it, so you can do something about it. As Handy and others have pointed out (see [here]("http://ubuntuforums.org/showpost.php?p=8910083&postcount=6")), the need for such a scanner on Ubuntu is usually more of a courtesy to Windows users with whom you might interact.

On a side note, not completely relevant to this discussion: my web server sometimes has visits from Russian search engines. Occasionally I notice one where the "user agent" identification seems to suggest a 16-bit version of Windows. I find this mildly amusing. :)

---

### Post by Silvereyes on 2010-03-07
I had a quick scan through the OP's previous posts and he (she?) seems to have something of an obsession with keylogging, viruses, anonymity etc.

Naturally this suggests Dodgy Porn and Pirated Windows Software :tongue:

---

### Post by Richiegs on 2010-03-07
> **Silvereyes said:**
> I had a quick scan through the OP's previous posts and he (she?) seems to have something of an obsession with keylogging, viruses, anonymity etc.

Naturally this suggests Dodgy Porn and Pirated Windows Software :tongue:

Dodgy Porn and Pirated Windows Software? Of course not! The reason I am interested in keylogging, viruses, anonymity is because I am afraid of identity theft and I want to find ways to prevent being the next victim.

---

### Post by OpSecShellshock on 2010-03-07
To be honest, the biggest risk of ID theft comes from third parties whom you've given personal information to willingly. If their systems and data get compromised, it doesn't matter what you've done on your local machine. Also, notification laws in the event of breaches vary from place to place, and they may not have to even tell you about it. The best form of protection is the exercise of caution with regard to whom you provide such information to and careful reading of privacy policies.

Also, it's good practice to either not put info about your hobbies, life, relatives, etc. on the social web or to use false info when creating accounts that ask you to set up "security questions." And then remember the false info, of course.

---

### Post by Richiegs on 2010-03-08
[QUOTE=OpSecShellshock;8930619]To be honest, the biggest risk of ID theft comes from third parties whom you've given personal information to willingly. If their systems and data get compromised, it doesn't matter what you've done on your local machine. Also, notification laws in the event of breaches vary from place to place, and they may not have to even tell you about it. The best form of protection is the exercise of caution with regard to whom you provide such information to and careful reading of privacy policies.

This may be true. But I remembered receiving fake emails asking me to VERIFY my username and password in a bank account. These happened immediately after I just had accessed to that bank account online. I wonder how did they find out I had an account in  THAT BANK? These have happened four times to me already.

---

### Post by DawieS on 2010-03-08
> **Richiegs said:**
> These happened immediately after I just had accessed to that bank account online. I wonder how did they find out I had an account in  THAT BANK? These have happened four times to me already.
This is why I have Firestarter open at all times while I am on the Internet. It has a panel showing me ALL the active connections.

My Firefox home-page is a blank screen, thus ensuring that NO connections are made when I first open Firefox, fresh without cookies or cache which may carry some form of spy-ware. There are lots of spy-bots on the Internet, that hook on to traffic to and from certain targeted websites.

These spy-bots are then able to breach your router firewall, and then create an unwanted connection to a third website, that you cannot get rid of, unless you close Firefox. If you continue with that session, logging into your bank account, it is possible for this third website to eavesdrop on all your actions for that session.

I then first block these websites, using either Adblock Plus or Firestarter, and exit Firefox without logging into my bank account. It is important to adjust the Privacy settings of Firefox to delete just about everything on exit (except the browsing/download history, and saved passwords, that should be protected with a master password).

If you log into your bank account, it is important to check that the connection is secure, and that it is the ONLY connection.

Nowadays I even block all the various Google addresses, preventing them to surf the Internet along with me. Even if I gave them permission to spy on me, I would expect of them to pay for the bandwidth used, not me.

I learned this the hard way and was forced to start using these techniques, due to bandwidth theft. At first I could not understand how the thievery was able to continue, even after changing all the passwords at my ISP and the router.

---

### Post by Ijan on 2010-03-08
> **Richiegs said:**
> 
This may be true. But I remembered receiving fake emails asking me to VERIFY my username and password in a bank account. These happened immediately after I just had accessed to that bank account online. I wonder how did they find out I had an account in  THAT BANK? These have happened four times to me already.

This does not sound very comforting. Sure it wasn't coincidence? If you regularly access your bank account online 4 times a day and that same email address of yours has been correlated to your bank e. g. via shopping in lots of places in the past, there's a chance your connection or local computer does not have to be compromised for this happening.

I say this because online fraud is still kind of a quite automated mass business that only very seldomly involves sophisticated personalized attacks.

Otherwise, it depends. A lot is theoretically possible. To find out what is likely you should provide further information. Were you using Linux or Windows? Were you using Tor? Do you connect via WLAN/WiFi etc.? Have other people acess to your LAN or are there other computers running. Did you have other Websites open while using your online banking (see above)? Did you access the bank's login page directly or via links etc.?

Also you might want to open another thread only on this topic as this one probably got a bit too wound to attract enough people to go through the time consuming process of a free personal security audit with you just for fun.

---

### Post by Richiegs on 2010-03-08
I am sure it wasn't coincidence because in one of those events I had just opened an account online just 3 days before. I was lucky because I had a zero balance.

Were you using Linux or Windows? Windows
Were you using Tor? No
Do you connect via WLAN/WiFi etc.? DSL
Did you access the bank's login page directly or via links etc.? Directly

---

### Post by Ijan on 2010-03-08
Ok, if you were using Windows it's a completely different thing. In that case malware is the most likely explanation. Not that Linux had the security magic, there are just tons of malware out there for Windows that nobody took the time to write for Linux systems.

The first thing was to virusscan your whole system (=all drives) from a clean boot environment. I think Avira has free ready made live-CDs ([link](http://www.free-av.com/en/tools/12/avira_antivir_rescue_system.html)) but there are others and I'd use at least a second engine and of course up to date signatures. Using a clean boot environment is important if your PC is probably already infected.

---

### Post by Richiegs on 2010-03-08
Thanks for your reply. That is why I switch to Linux because my Windows PC frequently was infected with viruses. Since I am now using Linux, is this malware in Windows still working?

---

### Post by Ijan on 2010-03-08
> **Richiegs said:**
> Since I am now using Linux, is this malware in Windows still working?

What do you mean by "in Windows"?

---

### Post by Richiegs on 2010-03-08
> **Ijan said:**
> What do you mean by "in Windows"?

Yes, in Windows. Will the malware self-activate in Windows even I am using Linux now?

---

### Post by Ijan on 2010-03-08
I meant your system configuration. What did you do with the potentially infected Windowsbox/-partition?

If is resides unbooted on some hd, the malware potentially present won't be activated. Malware needs to configure the running system to load and execute it. If you boot an infected Windows on the same box as your Linux it might potentially be able to access the Linux partition but it won't most probably not be able to "infect" the system as malware is mostly platform specific. If you never booted the potentially infected Windows or even deleted it since the malware is most certainliy gone.

If you access your mail account from a backdoored System and do not change the password afterwards, accessing it via Linux will not make you safer as your password is still potenitally in posession of an untrusted 3rd party.

You will get more and better answersy BTW if you attach basic information to your questions so that people do not have to guess.

---

### Post by Richiegs on 2010-03-08
My PC is a 5-year-old Windows XP and I have many anti-virus softwares for Windows such as AVG, Avast. So I probably already deleted the malware. Nevertheless, I installed Ubuntu within Windows using Wubi. I just wonder if I use Linux to access my files in Windows (/Host), will the malware in Windows self-activate? I know it is better to have 2 separate partitions for Linux and Windows, but I need to access my files in Windows. Thanks for your reply

---

### Post by gradinaruvasile on 2010-03-08
Linux can natively read/write to the Windows partition... And Windows has third party tools to access Linux partitions (at least the ext3 partitions).

As Ijan said, even if you copy a virus to the Windows partition it wont execute at startup, only if you launch Windows then execute the virused executable. 

A Windows (and programs in general) virus cannot be executed in Linux environment.

Offtopic a bit: I am not talking about Wine here, the virus cannot auto-execute code if not launched explicitly by the user via Wine - and in this case it is confined to Wine and that isnt running all time and it lacks many Windows specific stuff, meaning it will be crippled anyway.

---

### Post by Ijan on 2010-03-08
You could access Windows partitions also if you installed Linux/Ubuntu onto a separate partition. But Wubi isn't bad anyway.

Generally speaking your Linux-system is save of the Windwos malware with 99% certainty. This does none the less not cover the risk of already stolen passwords or possibly manipulated userscripts or app-configurations you copied from Windows into your Linux-apps but if you configured your Linux Browser IM etc. by hand your are probably also safe from this way of cross platform infection.

[edit]
Oh, I missed gradinaruvasile, sorry. Didn't relaod.
[/edit]

---

### Post by OpSecShellshock on 2010-03-08
If your browser session with your bank had been intercepted by malware, they wouldn't have needed to phish for your login details. They'd just grab them. It's more likely that someone got into your email account, saw some legitimate communication from the bank, but didn't have the credentials. That can happen if (for one example) your email address was scraped from a site where you'd entered it into some field and then whoever obtained it just ran it through a cracking program with a list of others. It's also possible that the email provider was breached. In any case, the most important thing is that you didn't fall for the phish, and it doesn't look like you did.

---

