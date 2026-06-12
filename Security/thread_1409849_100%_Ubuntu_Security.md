---
title: "100% Ubuntu Security"
date: 2010-02-18
forum: Security
---

### Post by linuxyogi on 2010-02-18
Guys, I know most of you will start by saying that securing one's PC 100% is neither practical nor possible. 

I have installed firestarter firewall.
Did not open any ports (inbound).
The "Allow connections from hosts" is also empty.
I never connect to any other PC remotely.
My PC is not connected to a Local Area Network.
ICMP filtering is enabled.
I connect to the Internet via an ADSL modem with its inbuilt dialer configured & its own firewall active. 
I update Ubuntu regularly (Both "Security" & "recommended" updates).

Now, what I am trying to know is 

1) Is the above mentioned configuration enough?
2)If not, what else do I need to do.

---

### Post by wilee-nilee on 2010-02-18
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by OrangeCrate on 2010-02-18
Adding...

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by Dayofswords on 2010-02-18
to make a computer 100% secure is practical and possible, a few easy steps

[LIST=1]
[*]unplug your computer from the internet
[*]unplug your computers power cord
[*]remove hard drive
[*]hammer and drill hard drive
[*]light the hard drive on fire
[/LIST]

easy and simple, yes?

---

### Post by donato roque on 2010-02-18
Perhaps reading the [Ubuntu Forum Security Sticky page]("http://ubuntuforums.org/showthread.php?t=510812") can help you in your journey using Ubuntu.

---

### Post by lisati on 2010-02-18
> **Dayofswords said:**
> to make a computer 100% secure is practical and possible, a few easy steps

[LIST=1]
[*]unplug your computer from the internet
[*]unplug your computers power cord
[*]remove hard drive
[*]hammer and drill hard drive
[*]light the hard drive on fire
[/LIST]

easy and simple, yes?

6. Dig hole in garden.
7. If it's a laptop, remove the battery & switch off the wifi adapter
8. Place computer and parts that have been removed in the hole
9. Mix some concrete/cement and pour into hole
10. Enjoy the time spent in the garden
...
:)

---

### Post by linuxyogi on 2010-02-18
> **OrangeCrate said:**
> Adding...

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

> **wilee-nilee said:**
> [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
> **donato roque said:**
> Perhaps reading the [Ubuntu Forum Security Sticky page]("http://ubuntuforums.org/showthread.php?t=510812") can help you in your journey using Ubuntu.

Thanks guys. I have visited those links you guys have suggested. I guess I have already implemented almost all the procedures mentioned there. It was just a matter of reassurance. Thanks a lot.

---

### Post by giammy on 2010-02-18
> **linuxyogi said:**
> Guys, I know most of you will start by saying that securing one's PC 100% is neither practical nor possible. 

...

1) Is the above mentioned configuration enough?
2)If not, what else do I need to do.

Hi,

in my opinion it's reasonably secure: the other main problem could come in
if you browse internet and connect to unsafe sites: it up to your judgment
to avoid this problem!

bye
giammy

---

### Post by linuxyogi on 2010-02-18
> **giammy said:**
> Hi,

in my opinion it's reasonably secure: the other main problem could come in
if you browse internet and connect to unsafe sites: it up to your judgment
to avoid this problem!

bye
giammy

Thanks for your reply. Please tell me what do mean by "unsafe sites". Are you talking about sites containing viruses? If so, I thought linux is almost virus & spyware free. Please reply.

---

### Post by giammy on 2010-02-18
> **linuxyogi said:**
> Thanks for you reply. Please tell me what do mean by "unsafe sites". Are you talking about sites containing viruses? If so, I thought linux is almost virus & spyware free. Please reply.

Yes, I mean virus or any other thing you can download: tipically Linux is virus-proof,
but if you download a very interesting application from a site you do not
trust, and that application ask to be installed as root, and you do it, you can 
install some malaware. Just an example: as I said, you configuration is
secure in my opinion!

bye
giammy

---

### Post by Enigmapond on 2010-02-18
> **lisati said:**
> 6. Dig hole in garden.
7. If it's a laptop, remove the battery & switch off the wifi adapter
8. Place computer and parts that have been removed in the hole
9. Mix some concrete/cement and pour into hole
10. Enjoy the time spent in the garden
...
:)

[SIZE=7]LOL!!! Dead On!

[SIZE=2]Firestarter is a dead programme. There is no more support for that. If you need GUI for the iptables install gufw.[/SIZE]
[/SIZE]

---

### Post by linuxyogi on 2010-02-18
> **giammy said:**
> Yes, I mean virus or any other thing you can download: tipically Linux is virus-proof,
but if you download a very interesting application from a site you do not
trust, and that application ask to be installed as root, and you do it, you can 
install some malaware. Just an example: as I said, you configuration is
secure in my opinion!

bye
giammy
Thanks again. Bye.

---

### Post by cdenley on 2010-02-18
Linux is not immune to malware, but it is rare that it is targeted. No OS is immune to malware. Someone can always create an application that does malicious things. It is just a matter of tricking you into running it. Also, browser vulnerabilities or browser plug-in vulnerabilities (flash) are something you should be concerned about when browsing the internet. This is why I suggest using noscript.

---

### Post by linuxyogi on 2010-02-18
> **cdenley said:**
> Linux is not immune to malware, but it is rare that it is targeted. No OS is immune to malware. Someone can always create an application that does malicious things. It is just a matter of tricking you into running it. Also, browser vulnerabilities or browser plug-in vulnerabilities (flash) are something you should be concerned about when browsing the internet. This is why I suggest using noscript.
I install softwares mostly fron Ubuntu repositories & a few others by downloading them. Here are some of the softwares that downloaded ------

Opera Web Browser 
Truecrypt
Sun VirtualBox
Google Chrome
Savage 2 (GAME)

You talked about browser vulnerabilities (flash). Now, flash is installed. I need flash to view Youtube videos. What about flash ? Please explain.

No Script is installed.

---

### Post by linuxyogi on 2010-02-18
> **Enigmapond said:**
> [SIZE=7]LOL!!! Dead On!

[SIZE=2]Firestarter is a dead programme. There is no more support for that. If you need GUI for the iptables install gufw.[/SIZE]
[/SIZE]

Thanks. Installing gufw..........

---

### Post by scottuss on 2010-02-18
Look, you're pretty safe. Just use common sense: only install software from the repositories and don't give your password to anything that you downloaded from the 'net unless you trust it.

Also, download and install updates where available and you'll be fine.

Being alert (and slightly paranoid!) is OK, but you can take it too far. Just use common sense and you'll be fine.

---

### Post by cdenley on 2010-02-18
> **linuxyogi said:**
> 
You talked about browser vulnerabilities (flash). Now, flash is installed. I need flash to view Youtube videos. What about flash ? Please explain.


Well, I think most vulnerabilities for Adobe Flash are cross-platform. If there were a vulnerability that allowed execution of arbitrary code, and you visited a page which displayed a malicious flash animation, malware could be executed on your system with the privileges of the user firefox is executing as. I think enabling the apparmor profile for firefox would limit the damage that can be done in such a scenario. With noscript, you can prevent flash animations from loading unless it is a site you trust (youtube). Any time your computer processes any data from the internet, there is potential that some vulnerability can be exploited. The most common example would be a flash animation or javascript embedded in a website.

---

### Post by linuxyogi on 2010-02-18
> **cdenley said:**
> Well, I think most vulnerabilities for Adobe Flash are cross-platform. If there were a vulnerability that allowed execution of arbitrary code, and you visited a page which displayed a malicious flash animation, malware could be executed on your system with the privileges of the user firefox is executing as. I think enabling the apparmor profile for firefox would limit the damage that can be done in such a scenario. With noscript, you can prevent flash animations from loading unless it is a site you trust (youtube). Any time your computer processes any data from the internet, there is potential that some vulnerability can be exploited. The most common example would be a flash animation or javascript embedded in a website.

Just one last thing ---- noscript to my knowledge is only available for firefox. Whats the solution for Opera & Google Chrome ?

---

### Post by linuxyogi on 2010-02-18
> **scottuss said:**
> Look, you're pretty safe. Just use common sense: only install software from the repositories and don't give your password to anything that you downloaded from the 'net unless you trust it.

Also, download and install updates where available and you'll be fine.

Being alert (and slightly paranoid!) is OK, but you can take it too far. Just use common sense and you'll be fine.

Thanks.

---

### Post by cdenley on 2010-02-18
> **linuxyogi said:**
> Just one last thing ---- noscript to my knowledge is only available for firefox. Whats the solution for Opera & Google Chrome ?

[http://www.google.com/support/forum/p/Chrome/thread?tid=080661c4f58af5c8&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=080661c4f58af5c8&hl=en)

---

### Post by Soul-Sing on 2010-02-18
> **linuxyogi said:**
> Just one last thing ---- noscript to my knowledge is only available for firefox. Whats the solution for Opera & Google Chrome ?

no-script will be soon available for chrome.

---

### Post by Soul-Sing on 2010-02-18
ps. how to secure explore/seatch the ww web: [http://ubuntuforums.org/showthread.php?t=1389589](http://ubuntuforums.org/showthread.php?t=1389589)

---

### Post by 2hot6ft2 on 2010-02-18
Don't download any untrusted .exe files from the net they will run in wine and can infect wine inside linux.
By untrusted I mean torrents, anything that is not from a reputable established and trusted source, i.e. bootleg software.

If it's for windows I just leave it for windows and if I could remove notepad from wine I would since it's the only thing in there and I don't use it.

Yeah, I could remove wine but I'm not sure how it would affect an upgrade. You also have that choice of removing wine. If you're really concerned about security you may want to do just that.

Point in fact "qaz".
[http://ubuntuforums.org/showthread.php?t=1409646](http://ubuntuforums.org/showthread.php?t=1409646)
[http://www.glocksoft.com/trojan_list/Qaz.htm](http://www.glocksoft.com/trojan_list/Qaz.htm)
[http://www.pchell.com/virus/qaz.shtml](http://www.pchell.com/virus/qaz.shtml)

---

### Post by cariboo on 2010-02-18
I think the majority of us don't have wine installed, it's only a small subset of computer users that are Windows gamers, that install wine.

---

### Post by rookcifer on 2010-02-18
> **linuxyogi said:**
> Just one last thing ---- noscript to my knowledge is only available for firefox. Whats the solution for Opera & Google Chrome ?

Chrome doesn't need NoScript since it runs from a sandbox in the first place.  The same goes for Firefox if you enable the AppArmor profile.

---

### Post by 2hot6ft2 on 2010-02-18
> **cariboo907 said:**
> I think the majority of us don't have wine installed, it's only a small subset of computer users that are Windows gamers, that install wine.
That's all I needed to hear. It's gone now. I run Ultimate Edition so it it's installed by default along with a bunch of other stuff I never use and have to get rid of but it has some things I really like.

---

### Post by cdenley on 2010-02-18
> **rookcifer said:**
> Chrome doesn't need NoScript since it runs from a sandbox in the first place.  The same goes for Firefox if you enable the AppArmor profile.

Chrome's sandboxing is a substitute for an apparmor profile, but not noscript. Noscript is also good for protecting privacy by blocking third party scripts and ads, but more importantly it prevents untrusted scripts from running at all. Sandboxing them should limit the damage, but even then they could still potentially do something malicious.

---

### Post by uRock on 2010-02-18
Check this out to see just how well UFW works. [http://ubuntuforums.org/showthread.php?t=1408074](http://ubuntuforums.org/showthread.php?t=1408074)  And those results don't include the added security of being behind a router.

---

### Post by linuxyogi on 2010-02-18
> **2hot6ft2 said:**
> Don't download any untrusted .exe files from the net they will run in wine and can infect wine inside linux. 


I don't have wine installed. But tell me something -------

In win I have seen computers getting virus infected by just visiting a website. You realize that your PC is infected only after the virus starts to show its symptoms. Firstly most win users always use their administrator account to do day to day tasks including Internet surfing & so the infection becomes system wide. Users don't even realize when & how the malware got installed. These are not the cases where the user is "tricked" to install some software. Just visiting a web page is enough to get infected. 

Are there malicious .deb files or .sh files out there in the www ? I know even if they exist that won't be able install themselves without my knowledge. I am talking about a scenario where the malicious .deb or .sh tries to install itself automatically just like those .exe files.
 
> **rookcifer said:**
> Chrome doesn't need NoScript since it runs from a sandbox in the first place.  The same goes for Firefox if you enable the AppArmor profile.

What is a sandbox?

Is there a way I can configure apparmor graphically ? I used Fedora 8 for some months, they have provided a gui for SElinux.

---

### Post by ismaelito on 2010-02-19
[B]
[/B]

[B]What is an AppArmor profile? and How does AppArmor work? , is it installed by defaults in Ubuntu 9.10?, Thanks.
[/B]

---

### Post by halovivek on 2010-02-19
> **lisati said:**
> 6. Dig hole in garden.
7. If it's a laptop, remove the battery & switch off the wifi adapter
8. Place computer and parts that have been removed in the hole
9. Mix some concrete/cement and pour into hole
10. Enjoy the time spent in the garden
...
:)

adding some more ...
1. If possible. nuke the hard drive..

---

### Post by rnerwein on 2010-02-19
> **Dayofswords said:**
> to make a computer 100% secure is practical and possible, a few easy steps

[LIST=1]
[*]unplug your computer from the internet
[*]unplug your computers power cord
[*]remove hard drive
[*]hammer and drill hard drive
[*]light the hard drive on fire
[/LIST]

easy and simple, yes?

that's full +1 
i think too that's the only way it will work every thing else is
security by obscurity
ciao

---

### Post by cdenley on 2010-02-19
> **linuxyogi said:**
> 
What is a sandbox?


A sandbox is a method of restricting what a process can do, in case that process is exploited and tricked into performing some malicious actions it wasn't meant to perform.

---

### Post by cdenley on 2010-02-19
> **ismaelito said:**
> [B]
[/B]

[B]What is an AppArmor profile? and How does AppArmor work? , is it installed by defaults in Ubuntu 9.10?, Thanks.
[/B]

An AppArmor profile is a configuration which sandboxes an application on your system. AppArmor is installed in ubuntu by default with a few different profiles, but the one for firefox is disabled by default.

---

### Post by linuxyogi on 2010-02-19
> **cdenley said:**
> An AppArmor profile is a configuration which sandboxes an application on your system. AppArmor is installed in ubuntu by default with a few different profiles, but the one for firefox is disabled by default.

Is there a GUI available to configure apparmor profiles ?

(Like there is GUI to configure SElinux)

---

### Post by cdenley on 2010-02-19
> **linuxyogi said:**
> Is there a GUI available to configure apparmor profiles ?

(Like there is GUI to configure SElinux)

Not that I know of.

---

### Post by uRock on 2010-02-19
For some great profiles go to Bohdi's site @ [http://bodhizazen.net/aa-profiles/](http://bodhizazen.net/aa-profiles/) and also read his thread here [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

---

### Post by linuxyogi on 2010-02-19
> **iRock said:**
> For some great profiles go to Bohdi's site @ [http://bodhizazen.net/aa-profiles/](http://bodhizazen.net/aa-profiles/) and also read his thread here [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

Thanks but I am afraid I have to skip this. This is too difficult for me. I guess SElinux is less difficult to configure because of its user friendly GUI. Selinux in Ubuntu is this possible? I have seen Selinux in synaptic. Again, thanks a lot.

---

### Post by uRock on 2010-02-19
I don't know if it can be or not. I copied and pasted the profiles on the link and I understand that it can be a bit much work. After running mapping tools against UFW, I feel safe. I also use NoScript and such for FF.

---

### Post by ismaelito on 2010-02-19
> **iRock said:**
> For some great profiles go to Bohdi's site @ [http://bodhizazen.net/aa-profiles/](http://bodhizazen.net/aa-profiles/) and also read his thread here [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

I read the article, unfortunately i have found it very complicated, I have downloaded this profile:
Bodhi.Zazen's current firefox 3.6 profile, in which directory should i save it?

Thanks,everything is new for me in Ubuntu:confused:,but i really like it.

---

### Post by cdenley on 2010-02-19
> **ismaelito said:**
> I read the article, unfortunately i have found it very complicated, I have downloaded this profile:
Bodhi.Zazen's current firefox 3.6 profile, in which directory should i save it?

Thanks,everything is new for me in Ubuntu:confused:,but i really like it.

In ubuntu 9.10, no need to download anything.
```

sudo aa-enforce /etc/apparmor.d/usr.bin.firefox-3.5

```
[https://help.ubuntu.com/community/AppArmor#How can I enable AppArmor for Firefox?](https://help.ubuntu.com/community/AppArmor#How can I enable AppArmor for Firefox?)

---

### Post by uRock on 2010-02-19
> **cdenley said:**
> In ubuntu 9.10, no need to download anything.
```

sudo aa-enforce /etc/apparmor.d/usr.bin.firefox-3.5

```
[https://help.ubuntu.com/community/AppArmor#How can I enable AppArmor for Firefox?](https://help.ubuntu.com/community/AppArmor#How can I enable AppArmor for Firefox?)

Bodhi's profile has a few rules added. 

ismaelito, please read through the UF link I gave in the same post as Bodhi's site. It explains where the files go.

---

### Post by rookcifer on 2010-02-19
> **ismaelito said:**
> [B]
[/B]

[B]What is an AppArmor profile? and How does AppArmor work? , is it installed by defaults in Ubuntu 9.10?, Thanks.
[/B]

AppArmor is a security mechanism that is patched into the Linux kernel by Ubuntu, OpenSuSE, Mandriva and some other distros.  It acts as a sandbox, or more technically, it acts as a Mandatory Access Control mechanism.  (SELinux is also a MAC, but is a bit more complex).  What this means is that a policy (or profile) is created for an application and that application cannot do anything not allowed in the profile, even if exploited (there are occasional ways to defeat a MAC via kernel level exploits, but that's beyond the scope of the discussion here).

AppArmor, imo, is much easier to use than SELinux.  In fact, this is the reason it was developed in the first place -- to be a replacement for the overly complex syntax of SELinux.  It's true that SELinux can do more than AppArmor (such as RBAC and MLS), but that is overkill for a desktop machine that is not on a network.

All you have to do to enable the Firefox profile is 

```
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox*
```

Then run firefox for a while and occasionally run 
```

sudo aa-logprof
```

to check for denials.  If Firefox loses functionality then aa-logprof should allow you to inspect what AppArmor is blocking and why.  You can then adjust it accordingly. If you know anything at all about how the Linux filesystem and other such security basics, AppArmor will be easy to learn.

---

### Post by ismaelito on 2010-02-19
This Forum is awesome:D, Thank you very much for your help. I 'll try your advices.

---

### Post by bodhi.zazen on 2010-02-19
> **ismaelito said:**
> I read the article, unfortunately i have found it very complicated, I have downloaded this profile:
Bodhi.Zazen's current firefox 3.6 profile, in which directory should i save it?

Thanks,everything is new for me in Ubuntu:confused:,but i really like it.

Just be aware , my ff 3.6 profile is with downloading the binary from mozilla and placing it in /usr/local

You can still use the profile, but you may need to adjust a few paths if you put firefox elsewhere.

If you are using the default 3.5.x user my 3.5 profile.

My profile is a bit restrictive in your Home directory, you may only download to ~/Download and ~/Documents .

If you want an intro to aa, take a look at this thread :

			 			[Introduction to AppArmor]("http://ubuntuforums.org/showthread.php?t=1008906")

---

### Post by linuxyogi on 2010-02-19
Got my PC checked at GRC.com.

STEALTH! STEALTH!

No More Fear !!!

Thanks to all those who tried to help.
[SIZE="5"]:D[/SIZE]

---

### Post by uRock on 2010-02-19
If you want to test your system and have 2 PCs, you can install and run Zenmap. Being that I got superb readings with just UFW enabled, I am sure yours will be fine. Since my most recent reinstall I haven't messed with AppArmor. I have been too busy with homework.

---

### Post by linuxyogi on 2010-02-19
> **bodhi.zazen said:**
> Just be aware , my ff 3.6 profile is with downloading the binary from mozilla and placing it in /usr/local

You can still use the profile, but you may need to adjust a few paths if you put firefox elsewhere.

If you are using the default 3.5.x user my 3.5 profile.

My profile is a bit restrictive in your Home directory, you may only download to ~/Download and ~/Documents .

If you want an intro to aa, take a look at this thread :

			 			[Introduction to AppArmor]("http://ubuntuforums.org/showthread.php?t=1008906")

Hi, is there a aa profile for Opera ?  
Opera is my favorite web browser. 
How secure do you think Opera is ?
Please reply.

---

### Post by linuxyogi on 2010-02-19
> **iRock said:**
> If you want to test your system and have 2 PCs, you can install and run Zenmap. Being that I got superb readings with just UFW enabled, I am sure yours will be fine. Since my most recent reinstall I haven't messed with AppArmor. I have been too busy with homework.

I don't have 2 PCs. 

As suggested -----------

> **cdenley said:**
> In ubuntu 9.10, no need to download anything.
```

sudo aa-enforce /etc/apparmor.d/usr.bin.firefox-3.5

```
[https://help.ubuntu.com/community/AppArmor#How can I enable AppArmor for Firefox?](https://help.ubuntu.com/community/AppArmor#How can I enable AppArmor for Firefox?)

"sudo aa-enforce /etc/apparmor.d/usr.bin.firefox-3.5"

This is the only thing I did besides installing gufw.

---

### Post by uRock on 2010-02-19
> **linuxyogi said:**
> I don't have 2 PCs. 

As suggested -----------

"sudo aa-enforce /etc/apparmor.d/usr.bin.firefox-3.5"

This is the only thing I did besides installing gufw.

Your system should be good to go then. There is always a way in, but IP tables makes it really hard to find unless you are using wireless.

---

### Post by dogdo on 2010-02-19
> **iRock said:**
> Your system should be good to go then. There is always a way in, but IP tables makes it really hard to find unless you are using wireless.

Im using wireless at home-explain that last comment...

---

### Post by HermanAB on 2010-02-19
"there is always a way in"
Not true.

By default Ubuntu runs *NO* listening services.  A default Ubuntu install is secure.

---

### Post by uRock on 2010-02-19
> **dogdo said:**
> Im using wireless at home-explain that last comment...

There is a lot to explain behind that little statement. There are intrusion tools that work well at first sniffing wireless packets to get simple things like WEP passwords to be able to connect to routers or with a little work they can take over a TCP connection and hack their way in. Go to your Synaptic and search out Zenmap, NMAP, and Aircrack-ng for starters. Zenmap is a GUI for NMAP and aircrack is self explanatory. I am taking a Network Intrusion Detection class and have a lot to learn yet, but if you want to learn more check out [Back|Track Linux]("http://www.backtrack-linux.org/"). It is an OS built for penetration testing. I don't recommend installing this OS but it is good to look into.

---

### Post by uRock on 2010-02-19
> **HermanAB said:**
> "there is always a way in"
Not true.

By default Ubuntu runs *NO* listening services.  A default Ubuntu install is secure.

True until you make a connection and the hacker uses that moment to move in. I ran Zenmap on a new install and it brought up open ports. Once ufw is enabled they disappear. If you can ping it, you can connect to it.

---

### Post by d3v1150m471c on 2010-02-19
I have iptables set to drop all incoming packets w/ssh disabled. psad and denyhosts are also installed. Not much of anything is getting through that.

---

### Post by uRock on 2010-02-19
> **d3v1150m471c said:**
> I have iptables set to drop all incoming packets w/ssh disabled. psad and denyhosts are also installed. Not much of anything is getting through that.

Installing psad as we speak, thanks. Denyhosts looks like it takes knowing how to configure it to make it work.

---

### Post by ismaelito on 2010-02-20
> **bodhi.zazen said:**
> Just be aware , my ff 3.6 profile is with downloading the binary from mozilla and placing it in /usr/local

You can still use the profile, but you may need to adjust a few paths if you put firefox elsewhere.

If you are using the default 3.5.x user my 3.5 profile.

My profile is a bit restrictive in your Home directory, you may only download to ~/Download and ~/Documents .

If you want an intro to aa, take a look at this thread :

                         [Introduction to AppArmor]("http://ubuntuforums.org/showthread.php?t=1008906")

Thanks for your answer, 
Actually, i have just downloaded your ff 3.6 profile, and placed in Documents, i want only use appArmor profiles by default.

So, i follow the easy way , i used this command :

```
sudo apt-get install apparmor-profiles
```

After, because i 'am using FF 3.6, i used this second command  according to[ rookcifer]("http://ubuntuforums.org/member.php?u=487698"):

```
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox*
```

And i restarted ff 3.6. 

And i run 

```
sudo aa-logprof
```

And
```
sudo genprof firefox
```am i doing something wrong?

---

### Post by rookcifer on 2010-02-20
> **ismaelito said:**
> 
And i restarted ff 3.6. 

And i run 

```
sudo aa-logprof
```

And
```
sudo genprof firefox
```am i doing something wrong?

The aa-logprof command is only used for auditing and for adjusting the profile if you lose some functionality.  So, if you notice Firefox is not behaving like it should be, you can run aa-logprof to see what error messages there are, and then it will allow you to interactively adjust the profile to correct the issue.

---

### Post by ismaelito on 2010-02-20
> **rookcifer said:**
> The aa-logprof command is only used for auditing and for adjusting the profile if you lose some functionality.  So, if you notice Firefox is not behaving like it should be, you can run aa-logprof to see what error messages there are, and then it will allow you to interactively adjust the profile to correct the issue.

Thanks for your answer, right now Firefox is behaving well, no problem at all.
Just one more question, i am really fan of Opera, but since i started to use Ubuntu, and i read a lot of information in this forum about Firefox, i realised that most people are using Firefox, so i switched to firefox. What i don't know if Firefox is more secure than Opera.
Anyway, I 'am using 
Firefox 3.6+Wot+adblock+OpenDns(+filters)+apparmor + UFW firewall+ Firewall of the router. Am i now safe?

---

### Post by cariboo on 2010-02-20
If you like wearing a belt and suspenders, you're safe. I personally wouldn't bother with a firewall on the computer if you are behind a router.

---

### Post by bodhi.zazen on 2010-02-21
Safe is a relative term, :lolflag:

Start firefox and run :

```
sudo aa-status
```

You should see your firefox listed as a process in enforce mode.

You can test the firefox profile easily, try to save something somewhere you should no and see if anything is logged in /var/log/messages .

---

### Post by ismaelito on 2010-02-21
> **bodhi.zazen said:**
> Safe is a relative term, :lolflag:

Start firefox and run :

```
sudo aa-status
```You should see your firefox listed as a process in enforce mode.

You can test the firefox profile easily, try to save something somewhere you should no and see if anything is logged in /var/log/messages .

Thanks :popcorn:

I run  ```
sudo aa-status
```

And i have the following:
sudo aa-status

apparmor module is loaded.
34 profiles are loaded.
15 profiles are in enforce mode.
   /usr/share/gdm/guest-session/Xsession
   /usr/bin/freshclam
   /usr/sbin/avahi-daemon
   /sbin/dhclient3
   /usr/lib/firefox-3.5.*/firefox
   /usr/sbin/mysqld-akonadi
   /usr/bin/evince-thumbnailer
   /usr/lib/firefox-3.6.2pre/firefox-*bin
   /usr/sbin/cupsd
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
   /usr/bin/evince-previewer
   /usr/sbin/tcpdump
   /usr/lib/cups/backend/cups-pdf
   /usr/bin/evince
19 profiles are in complain mode.
   /usr/lib/dovecot/imap-login
   /bin/ping
   /sbin/klogd
   /sbin/syslogd
   /sbin/syslog-ng
   /usr/lib/dovecot/imap
   /usr/sbin/traceroute
   /usr/sbin/mdnsd
   /usr/sbin/identd
   /usr/lib/dovecot/managesieve-login
   /usr/sbin/dnsmasq
   /usr/sbin/nmbd
   /usr/lib/dovecot/dovecot-auth
   /usr/lib/dovecot/pop3-login
   /usr/sbin/smbd
   /usr/lib/dovecot/deliver
   /usr/sbin/nscd
   /usr/sbin/dovecot
   /usr/lib/dovecot/pop3
5 processes have profiles defined.
5 processes are in enforce mode :
   /usr/sbin/avahi-daemon (536) 
   /sbin/dhclient3 (1848) 
   /usr/sbin/cupsd (1567) 
   /usr/bin/freshclam (1523) 
   /usr/sbin/avahi-daemon (557) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.

---

### Post by bodhi.zazen on 2010-02-21
I can see firefox listed, but it does not appear you are running firefox, as firefox is not listed in the 

"5 processes are in enforce mode :"

So either you did not start firefox first as I advised you or firefox in not confined. If firefox is not confined you will need to look at the profiles to determine why not.

---

### Post by uRock on 2010-02-21
> **cariboo907 said:**
> If you like wearing a belt and suspenders, you're safe. I personally wouldn't bother with a firewall on the computer if you are behind a router.

Suspenders? I personally don't worry about my firewall. Though I do like running the pen tools against the firewalls to see if they really block anything.

---

### Post by ismaelito on 2010-02-21
> **bodhi.zazen said:**
> I can see firefox listed, but it does not appear you are running firefox, as firefox is not listed in the 

"5 processes are in enforce mode :"

So either you did not start firefox first as I advised you or firefox in not confined. If firefox is not confined you will need to look at the profiles to determine why not.

I started firefox before to run : sudo aa-status :confused: , so firefox is not confined, what do i have to do ? Thanks

---

### Post by bodhi.zazen on 2010-02-21
> **ismaelito said:**
> I started firefox before to run : sudo aa-status :confused: , so firefox is not confined, what do i have to do ? Thanks

Depends on what version of firefox you are using, how you installed it, and how your profile is written.

You stated earlier you are using firefox 3.6 ? Well, you do not have a profile for firefox 3.6. (firefox-3.6.2pre != firefox 3.6).

---

### Post by ismaelito on 2010-02-21
> **bodhi.zazen said:**
> Depends on what version of firefox you are using, how you installed it, and how your profile is written.

You stated earlier you are using firefox 3.6 ? Well, you do not have a profile for firefox 3.6. (firefox-3.6.2pre != firefox 3.6).

I'am using Firefox 3.6, i installed following Ubuntuzilla, and after i ran


```
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox*
```.

Now i have a problem, i can't start firefox:confused:, i am using Opera.
Oh my God:(

---

### Post by bodhi.zazen on 2010-02-21
> **ismaelito said:**
> I'am using Firefox 3.6, i installed following Ubuntuzilla, and after i ran


```
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox*
```.

Now i have a problem, i can't start firefox:confused:, i am using Opera.
Oh my God:(

It works !! :twisted: :lolflag:
 
 You have not posted sufficient information to fix your problem though.
 
 You need to read the apparmor thread :
 
 [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)
 
 and read your logs and or use aa-logprof.

I would also point out that debugging your ff 3.6 profile is now almost 70 posts deep in a thread titled "100% Ubuntu Security". 

If you are using my profile, as I said earlier, I installed firefox 3.6 by doenloading the binary from mozilla and installing it in /usr/local/firefox.

You will need to adjust the profile accordingly, or install firefox as I did.

---

### Post by ismaelito on 2010-02-21
> **bodhi.zazen said:**
> It works !! :twisted: :lolflag:
 
 You have not posted sufficient information to fix your problem though.
 
 You need to read the apparmor thread :
 
 [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)
 
 and read your logs and or use aa-logprof.

I would also point out that debugging your ff 3.6 profile is now almost 70 posts deep in a thread titled "100% Ubuntu Security". 

If you are using my profile, as I said earlier, I installed firefox 3.6 by doenloading the binary from mozilla and installing it in /usr/local/firefox.

You will need to adjust the profile accordingly, or install firefox as I did.

Thanks for your time and your help, i really appreciate it.
I gave up:(, i run 
```
sudo /etc/init.d/apparmor stop
```
Now Firefox is working, i don't need Apparmor any more.

---

### Post by rookcifer on 2010-02-21
> **ismaelito said:**
> Thanks for your time and your help, i really appreciate it.
I gave up:(, i run 
```
sudo /etc/init.d/apparmor stop
```
Now Firefox is working, i don't need Apparmor any more.

LOL, you don't need to shut AppArmor down entirely.  Just put the Firefox profile back in complain mode:
```

sudo aa-complain firefox-3.*

```

Then restart AppArmor

```
sudo /etc/init.d/apparmor restart
```

Now, why don't you post your Firefox profile here?  Go to /etc/apparmor.d, find the firefox profile and post it here.

---

### Post by bodhi.zazen on 2010-02-21
> **rookcifer said:**
> Now, why don't you post your Firefox profile here?  Go to /etc/apparmor.d, find the firefox profile and post it here.

Along with your path to firefox 3.6 and error messages when you run firefox in complain mode ...

---

### Post by ismaelito on 2010-02-22
Hello,
I got a lot of problems with firefox and Apparmor,i couldn't start it anymore, so i decided to uninstall it completely.
Now, i am using Opera, and sometimes Epiphany(excellent browser),How do i apply the Apparmor profiles to theses browsers?
Thanks.

---

### Post by uRock on 2010-02-22
```
sudo complain firefox
``` should shut off the AppArmor profile for Firefox.

---

### Post by bodhi.zazen on 2010-02-22
> **ismaelito said:**
> Hello,
I got a lot of problems with firefox and Apparmor,i couldn't start it anymore, so i decided to uninstall it completely.
Now, i am using Opera, and sometimes Epiphany(excellent browser),How do i apply the Apparmor profiles to theses browsers?
Thanks.

No offense, but if you wish to use apparmor you are going to need to do some reading and learn to use apparmor.  You need to know a little about your file system and what "normal" or expected behavior is of the application you are trying to confine.

You basically have 3 problems.

1. IMO your biggest problem is you do not willing to learn apparmor. by that I mean, it does not work the way you expect, and so you giv eup and move to another application or disable apparmor altogether.

[[all variants] Introduction to AppArmor - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1008906") 

Now if you have a specific question on what you read, feel free to ask.

If you do not want to take the time to learn apparmor and read and debug the errors/denial in the logs I suggest you do not use it at all.

2. Your second problem is Firefox, or any browsser really, is not a good application to start with. This is because everyone uses the browser for different things and very diverse things such as sound, flash, opeing documents, pdf, etc etc. So copying somebody else's profile is unlilkely to be overly helpful.

3. You are not using the default version of firefox that comes with Ubuntu. If you used the default version of firefox you can use the default apparmor profile. If you do not use the default version of firefox, you will need to write a profile for the version of firefox you are using.

IMO if you can not modify a profile for firefox you are going to struggle to write a profile form scratch for an alternate browser. As far as I know there are no drop in apparmor profiles for other browsers.

If you want to secure your system I suggest you go back to the basics:

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

I think better questions are:

What makes you feel you "need" apparmor ?

Are you willing to spend the time and effort it takes to learn apparmor ?

If so, we can help, but you will need to read and ask specific questions.

---

### Post by ismaelito on 2010-02-23
> **bodhi.zazen said:**
> No offense, but if you wish to use apparmor you are going to need to do some reading and learn to use apparmor.  You need to know a little about your file system and what "normal" or expected behavior is of the application you are trying to confine.

You basically have 3 problems.

1. IMO your biggest problem is you do not willing to learn apparmor. by that I mean, it does not work the way you expect, and so you giv eup and move to another application or disable apparmor altogether.

[[all variants] Introduction to AppArmor - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1008906") 

Now if you have a specific question on what you read, feel free to ask.

If you do not want to take the time to learn apparmor and read and debug the errors/denial in the logs I suggest you do not use it at all.

2. Your second problem is Firefox, or any browsser really, is not a good application to start with. This is because everyone uses the browser for different things and very diverse things such as sound, flash, opeing documents, pdf, etc etc. So copying somebody else's profile is unlilkely to be overly helpful.

3. You are not using the default version of firefox that comes with Ubuntu. If you used the default version of firefox you can use the default apparmor profile. If you do not use the default version of firefox, you will need to write a profile for the version of firefox you are using.

IMO if you can not modify a profile for firefox you are going to struggle to write a profile form scratch for an alternate browser. As far as I know there are no drop in apparmor profiles for other browsers.

If you want to secure your system I suggest you go back to the basics:

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

I think better questions are:

What makes you feel you "need" apparmor ?

Are you willing to spend the time and effort it takes to learn apparmor ?

If so, we can help, but you will need to read and ask specific questions.

Since i am new with Ubuntu, i have found everything a little complicated, so i am sorry if i  annoy you. 
To be honest, i read [Introduction to AppArmor]("http://ubuntuforums.org/showthread.php?t=1008906") more than three times, but i haven't understood, or i haven't figured out how to apply it, i should  struggle more to assimilate How it functions.
But, right now i keep using Opera because i prefer it than Firefox, so i don´t need apparmor.
Thanks for your time.

---

### Post by bodhi.zazen on 2010-02-23
> **ismaelito said:**
> ... so i don´t need apparmor.
Thanks for your time.

I am not annoyed, I am trying to point you in a more productive direction, point out to you what running apparmor will require. If you are happy with your results, then all is good.

I think that is the best option for now. Linux is not windows and, IMO, a default installation of Ubuntu is more secure then a default windows installation.

As you learn how your system works you may wish to look at SELinux and apparmor.

The advantage of selinux, it has been in existance longer and there are more "profiles" if you will. The disadvantage are the selinux syntax is more difficult to learn and difficult to modify.

The advantage of apparmor is it is easier to learn, not that it is easy as you can see. The disadvantage, there are not yet default profiles of each and every network aware application. The profile for firefox is relatively new and hopefully there will soon be a profile for all apps, such as opera.

As I tried to point out, part of your problem is that you did not stay with the defaults. If you stay with the default version of firefox, the default firefox apparmor profile works just fine, you simply enable it.

Your problems with apparmor stem from the fact that you installed a newer version of firefox and you do not yet understand your system enough to write a custom apparmor profile. As I indicated, firefox is not the best application to start with. Although It is needed, teh firefox apparmor profile is complex, and thus not a good first application to start with. If you want to learn apparmor start with a simpler application, such as pidgin or xchat.

---

### Post by linuxyogi on 2010-02-23
How to enable apparmor for pidgin? I am using Pidgin ver. 2.6.5.

---

### Post by uRock on 2010-02-23
> **linuxyogi said:**
> How to enable apparmor for pidgin? I am using Pidgin ver. 2.6.5.

Bodhi has a profile here for Pidgin [here]("http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.10/"). However, the explanation of how to create a profile can be found [here]("http://ubuntuforums.org/showthread.php?t=1008906").

---

