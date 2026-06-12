---
title: "Just got hacked?"
date: 2012-08-31
forum: Security
---

### Post by holyman842 on 2012-08-31
Hi everyone,
            I am using Ubuntu 12.04. I work as an online app developer for google via odesk. Yesterday, I was working as usual. I was using Google Chrome; I was also listening to music on audacious, my ntfs drive 'songs' was mounted and home folder was opened and finally the Odesk team app was running.
            I am using MTS MBLAZE 3.1 MBPS wireless broadband. I just left the computer for about an hour, paused my work and went for breakfast. All the applications I mentioned above were running and internet was connected.
            When I came back the computer was on stand by (that's normal) but VLC, Firefox, Ubuntu help was opened and all of my drives were mounted and on stand by net got disconnected. No one at my home touched my pc. I was beyond shocked. From that monent on, I rebooted my pc and started win 7. I just didn't feel secure.
            Any ideas on what happened and what should I do?
Regards,
Arindom Das

---

### Post by mdurham on 2012-08-31
Your cat or dog danced on your keyboard/mouse

---

### Post by DaCast on 2012-08-31
I'm security conscious, so when I'm not literally in front of my PC, I make sure to disconnect from the net, unless I'm transferring files or something. It's a bit tedious, but so far, it has worked.

---

### Post by Ubun2to on 2012-08-31
Do you have the built in firewall on? I usually make sure it is turned on after I boot (the GUI interface package is gufw). The only incoming connections I allow are Skype and the scanner I have on my printer.
Also, did you have any remote desktop connection software open? That is one way to get into a computer when nobody is around.

---

### Post by melrokz on 2012-08-31
Well, 99.9% you didn't get hacked. Ubuntu is pretty secure. I've been using Ubuntu since 2008, no major issues. It's either your pets or someone else. Try locking your screen next time you leave your computer, with Ctrl + Alt + L.

---

### Post by mastablasta on 2012-08-31
you can check the system logs for any activity. indeed a valid question is if oyu have a firewall (on router or on the OS)?
 
also i hope your wireles sis propperly secured (strong password and best possible encryption)

---

### Post by Habitual on 2012-08-31
"...wireless broadband..."

nuff said.

---

### Post by 3rdalbum on 2012-08-31
> **Habitual said:**
> "...wireless broadband..."

nuff said.

Huh? That explains the disconnection from the internet when they got back. It doesn't explain the other programs open.

It's wireless broadband, not public wifi. You know, mobile phone internet.

Remote Desktop access may be turned on without requiring a password or local confirmation - that's definitely not the default, maybe you changed it? Otherwise, Ubuntu does not listen to any incoming ports by default, regardless of whether you have a firewall or not.

---

### Post by nativehound on 2012-08-31
First check system monitor to see if vino-server is running.
Then I would check the auth.log for anything that sticks out of the norm.

```
sudo tail -n 30 /var/log/auth.log
```

Then make sure RD is off.

```
gsettings set org.gnome.Vino enabled false
```


gl

---

### Post by holyman842 on 2012-08-31
Well, first of all, I do not own a cat or dog so that is out of the question. Second, I am talking about my ASUS EEEPC 1015PX. I closed the laptop lid when I went.
My system is pretty basic. I have a dial up wireless broadband. I plug in the modem. Click on "MTS MBLAZE Connection" on nm-applet and it gets connected.
Also my work demands that I stay online during work hours so that is why I could not disconnect the internet.
Also, I brag to my friends saying that my ubuntu netbook is better than their windows counterparts. I thought that the built in ubuntu firewall(I have never seen that option:lolflag:) is better than windows firewall. I never configured firewall on ubuntu or on windows.
Also, I never used remote desktop so I have no idea on what to do with it. Nevertheless, I will search and see if it is enabled or not.
I didn't lock my pc when I got up. I guess I got careless, also my password is very basic. That can also be a reason.
Also I will be replying on the vino server soon.
Thanks for the support.
Arindom

---

### Post by holyman842 on 2012-09-01
Hello,
I just ran the following command. Hope this helps.


 ```
sudo tail -n 30 /var/log/auth.log
[sudo] password for arindom: 
Sep  1 18:48:06 arindom-1015PX sudo:  arindom : TTY=unknown ; PWD=/home/arindom ; USER=root ; COMMAND=/usr/lib/jupiter/scripts/vga-out mon silent
Sep  1 18:48:06 arindom-1015PX sudo: pam_unix(sudo:session): session opened for user root by (uid=1000)
Sep  1 18:48:06 arindom-1015PX sudo:  arindom : TTY=unknown ; PWD=/home/arindom ; USER=root ; COMMAND=/usr/lib/jupiter/scripts/rotate restore silent LVDS1
Sep  1 18:48:06 arindom-1015PX sudo:  arindom : TTY=unknown ; PWD=/home/arindom ; USER=root ; COMMAND=/usr/lib/jupiter/scripts/resolutions restore LVDS1
Sep  1 18:48:06 arindom-1015PX sudo: pam_unix(sudo:session): session opened for user root by (uid=1000)
Sep  1 18:48:06 arindom-1015PX sudo: pam_unix(sudo:session): session opened for user root by (uid=1000)
Sep  1 18:48:06 arindom-1015PX sudo: pam_unix(sudo:session): session closed for user root
Sep  1 18:48:07  sudo: last message repeated 3 times
Sep  1 18:48:07 arindom-1015PX polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session1 (system bus name :1.35 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_IN)
Sep  1 18:48:07 arindom-1015PX sudo: pam_unix(sudo:session): session closed for user root
Sep  1 18:48:08 arindom-1015PX sudo:  arindom : TTY=unknown ; PWD=/home/arindom ; USER=root ; COMMAND=/usr/lib/jupiter/scripts/cpu-control vendor
Sep  1 18:48:08 arindom-1015PX sudo: pam_unix(sudo:session): session opened for user root by (uid=1000)
Sep  1 18:48:08 arindom-1015PX sudo: pam_unix(sudo:session): session closed for user root
Sep  1 18:48:08 arindom-1015PX sudo:  arindom : TTY=unknown ; PWD=/home/arindom ; USER=root ; COMMAND=/usr/lib/jupiter/scripts/resolutions modes 
Sep  1 18:48:08 arindom-1015PX sudo: pam_unix(sudo:session): session opened for user root by (uid=1000)
Sep  1 18:48:08 arindom-1015PX sudo:  arindom : TTY=unknown ; PWD=/home/arindom ; USER=root ; COMMAND=/usr/lib/jupiter/scripts/rotate normal 
Sep  1 18:48:08 arindom-1015PX sudo: pam_unix(sudo:session): session opened for user root by (uid=1000)
Sep  1 18:48:08 arindom-1015PX su[2504]: Successful su for root by root
Sep  1 18:48:08 arindom-1015PX su[2504]: + ??? root:root
Sep  1 18:48:08 arindom-1015PX su[2504]: pam_unix(su:session): session opened for user root by (uid=0)
Sep  1 18:48:09 arindom-1015PX su[2566]: Successful su for root by root
Sep  1 18:48:09 arindom-1015PX su[2566]: + ??? root:root
Sep  1 18:48:09 arindom-1015PX su[2566]: pam_unix(su:session): session opened for user root by (uid=0)
Sep  1 18:48:10 arindom-1015PX su[2504]: pam_unix(su:session): session closed for user root
Sep  1 18:48:10 arindom-1015PX su[2566]: pam_unix(su:session): session closed for user root
Sep  1 18:48:11 arindom-1015PX sudo: pam_unix(sudo:session): session closed for user root
Sep  1 18:48:11 arindom-1015PX sudo: pam_unix(sudo:session): session closed for user root
Sep  1 18:48:17 arindom-1015PX dbus[793]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.49" (uid=1000 pid=2695 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.14" (uid=0 pid=1593 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Sep  1 18:48:19 arindom-1015PX dbus[793]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.53" (uid=1000 pid=2763 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.14" (uid=0 pid=1593 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Sep  1 18:52:00 arindom-1015PX sudo:  arindom : TTY=pts/0 ; PWD=/home/arindom ; USER=root ; COMMAND=/usr/bin/tail -n 30 /var/log/auth.log
```

Also I turned off RD as asked. Now how should I know if any keyloggers are on my system?

---

### Post by holyman842 on 2012-09-02
Hello,
      Can someone please reply to this thread. I did as I was told. Please reply soon.
Arindom

---

### Post by sffvba[e0rt on 2012-09-02
*Thread moved to **Security Discussions**.*


404

---

### Post by Ms. Daisy on 2012-09-02
You posted your auth log above. Can you give a timeline associated with it? Were all those sudo sessions during the time you were away from the computer or did you do some of them?

---

### Post by holyman842 on 2012-09-03
Hi,
   Thank you for the reply. I am sure that I was way during that time. Only the last line of the command was done by me..

Sep 1 18:52:00 arindom-1015PX sudo: arindom : TTY=pts/0 ; PWD=/home/arindom ; USER=root ; COMMAND=/usr/bin/tail -n 30 /var/log/auth.log
I don't know what tty=unknown means but I am sure if I use it it shows tty=something!! not unknown. This just confirms I was hacked but as far as I know, hackers are supposed to leave undetected not leave a host of applications running..
I hope that you guys can help me & the others who might be worried about security.
Regards,
Arindom

---

### Post by Ms. Daisy on 2012-09-03
The auth log that you posted happened on September 1 between 18:48:06 and 18:52:00 when you ran the command that nativehound suggested.  You started this thread 3 days ago, so one can assume that the concerning events happened August 31.  You need to look at the logs **from the time period where you think something happened**.

---

### Post by holyman842 on 2012-09-03
Hi Ms Daisy,
            Thank you for your reply. But unfortunately I am not an expert on security so I do not really understand the logs. Also I have run ubuntu just once after that because I am not sure about the security of the system.
            I am sorry that I cannot be of much help but the fact I do not know anything at all about the commands that were run after 18:48. I do not run too many commands instead I rely on GUI.

---

### Post by Ms. Daisy on 2012-09-03
Let's start with "the security of the system."  I recommend you read [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) , which was specifically designed for new users to help them understand security as it relates to Ubuntu.

Now on to the logs.  Basically Ubuntu logs everything one way or another.  When you booted up Ubuntu, the system automatically added lines and lines into the logs.  Not everything logged is malicious. Most of it is actually rather useful if you know how to read it.  You can start here to begin understanding the logs.  [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

If you really want to determine if someone did something nasty on your Ubuntu box, then here's a quick primer on log auditing: [https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned](https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned) . 

I'm still not entirely clear where exactly you left your laptop when you think it got compromised.  Did you leave it in a semi-public place?  If you cannot physically secure your computer, then it doesn't matter what kind of security configurations you have installed.  Don't let a bad guy sit down at the keyboard and you're off to a good start.

---

### Post by holyman842 on 2012-09-04
Hello again Ms Daisy,
                     I was at my home when I left my laptop. I closed the lid of my laptop when I left. I already mentioned the applications that I was running and as I said earlier no one touched my pc when I was away. I will go through the logs again and will try to increase security. Can you please tell me, how to find out if any key loggers have been installed on my system?

---

### Post by Ms. Daisy on 2012-09-04
You can have a look at this support thread, which asked the same thing:
 
[http://askubuntu.com/questions/169887/how-can-i-detect-a-keylogger-on-my-system](http://askubuntu.com/questions/169887/how-can-i-detect-a-keylogger-on-my-system)

---

### Post by holyman842 on 2012-09-04
Thank you for pointing me to that thread.
Regards,
Arindom

---

### Post by OrangeCrate on 2012-09-04
Ms. Daisy has been spot on in her attempt to help you, and I don't want to suggest anything that would dilute what she's attempting to do as she walks you through all of this, but, I will offer another alternative for you to think about, if you can't come to a reasonable outcome with the direction you're going here.

Personally, even if I could positively confirm the presence of a key logger, and some how repair the current installation, I'd never trust that installation again. Fortunately with Linux, is pretty easy to fix anything, by simply backing up your Home folder (everything except those items with a "." in front of them, since you're looking for a clean install), and then reinstall. Change your boot login password during installation, and then change all of your passwords when you're up and running.

If there's an inherent problem with this strategy that I'm not aware of, someone post a reply...

---

### Post by holyman842 on 2012-09-04
OrangeCrate,
            Thank you for your suggestion. Your solutions ounds fairly easy to me as I was also thinking of the same thing. I will provide a strong password this time and also install firestarter but before that I will try solving this issue with Ms Daisy's method. As you said I will never be able to trust this installation but I should know what to do in case this happens again.
Thanks,
Arindom

---

### Post by tubbygweilo on 2012-09-04
OrangeCrate

> Personally, even if I could positively confirm the presence of a key logger, and some how repair the current installation, I'd never trust that installation again. Fortunately with Linux, is pretty easy to fix anything, by simply backing up your Home folder (everything except those items with a "." in front of them, since you're looking for a clean install), and then reinstall. Change your boot login password during installation, and then change all of your passwords when you're up and running.

If using encryption then the .gnupg directory could be backed up unless one has an up to date copy on say dvd or such held offline otherwise your secret key may well be lots.

All the best.

---

### Post by koenn on 2012-09-04
I agree with those that say 'if you don't trust your system, reinstall it'. 

To put things in perspective a bit :

> but VLC, Firefox, Ubuntu help was opened and all of my drives were mounted and on stand by net got disconnected. No one at my home touched my pc
the Occam's razor explanation for this is that someone found the session you left open and started a handful of programs, right there from your keyboard. And they're afraid to tell you (or they're pulling your leg)
Remote sessions, even remote GUI Desktop sessions, would run parallel to your session and any activity (open programs, ...) would be limited to the session where it started. Those programs wouldn't show up on 'your' screen unless they were started from your session.  "Taking over" someones destop on a linux is, as opposed to a Windows desktop, not the default approach, although there are some rdp programs that make it possible (vino maybe ?  VNC ? ...) . 


Then your logs.
Lots of the "root" sessions lest only 1 or 2 seconds, these are most likely scheduled jobs for all sorts of perfectly normal sysadmin tasks. 
The ones that could be worrying are the "su" sessions, since they indicated someone starting a root shell, while the actual commands that were run in that shell won't show up in auth.log. 
Of course, maybe you ran those yourself - that's impossible to tell from the logs. You could run 'history' in a root shell to trace some of it. 
It's also obvious from the logs that these su sessions were started from your own account, so either by you, or by someone else logged on with your account and password. 

I don't know how to interpret the ' polkitd(authority=local): Registered Authentication Agent for unix-session: ' entries. 



> Also, I brag to my friends saying that my ubuntu netbook is better than their windows counterparts.
What probably happened is what I said earlier (Occam's razor), or that someone remotely took over your session by knowing/guessing your password (but : unlikely if you were not running some windows-style rdp software). If it's any consolation, I'd say your behavior makes your Windows sessions just as likely to be compromised as your Ubuntu sessions.

---

### Post by holyman842 on 2012-09-04
> **koenn said:**
> What probably happened is what I said earlier (Occam's razor), or that someone remotely took over your session by knowing/guessing your password (but : unlikely if you were not running some windows-style rdp software). If it's any consolation, I'd say your behavior makes your Windows sessions just as likely to be compromised as your Ubuntu sessions.

As I said earlier, I was at my home when I left the laptop. So I am pretty sure no one came and started all those applications. Also, it is very possible to guess of brute force my password because my password is a four letter dictionary keyword. But as I said earlier this will change soon enough. Right now, I do not have the equipment for performing a fresh installation of ubuntu since I am  out of town. Also, I use samba, openvpn and odesk team app(which is like google talk). So most probably I can guess that someone hacked into my system by guessing/brute-forcing  my password.
As for windows, I have tightened my security on it and I am using windows now since I am unsure of Ubuntu. After a fresh install I will start using ubuntu again.
Thank you,
Arindom

---

### Post by Ubun2to on 2012-09-05
> **OrangeCrate said:**
> If there's an inherent problem with this strategy that I'm not aware of, someone post a reply...

Do you mean like mining the Home folder? (Hiding viruses as hidden files in the Home folder directories-like putting down land mines.)
I could see that happening, but just activate the viewing of hidden files by CTRL + H, and make sure that all the files you get are legit (I don't mean go through and read each document and watch every video, I just mean don't grab ones like .credit-report.doc.deb or free-candy.exe, the ones you know are not legit).

---

### Post by The Cog on 2012-09-05
> **koenn said:**
> Remote sessions, even remote GUI Desktop sessions, would run parallel to your session and any activity (open programs, ...) would be limited to the session where it started. Those programs wouldn't show up on 'your' screen unless they were started from your session.  
But if the computer is configured to allow VNC connections, then the remote user will see (and drive) the current desktop session. What's more, last time I looked, the option to allow remote desktop access had an option to "allow internet access" which if checked, would actively use UPnP to configure incoming port forwarding for VNC through the router. I think that VNC access either from the internet or from the local wireless network is probably the most likely explanation.

---

### Post by OrangeCrate on 2012-09-05
> **holyman842 said:**
> As I said earlier, I was at my home when I left the laptop. So I am pretty sure no one came and started all those applications. Also, it is very possible to guess of brute force my password because my password is a four letter dictionary keyword. But as I said earlier this will change soon enough. Right now, I do not have the equipment for performing a fresh installation of ubuntu since I am  out of town. Also, I use samba, openvpn and odesk team app(which is like google talk). So most probably I can guess that someone hacked into my system by guessing/brute-forcing  my password.
[B]As for windows, I have tightened my security on it and I am using windows now since I am unsure of Ubuntu. After a fresh install I will start using ubuntu again.
Thank you,[/B]
Arindom

Good plan, that's what I would do too.

For general security guidelines, this is a good read, and a great site, if you haven't been there before:

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

And instructions on helping to secure Windows by using a standard user account, can be found here:

[http://www.unixwiz.net/techtips/win7-limited-user.html](http://www.unixwiz.net/techtips/win7-limited-user.html)

Good luck!

:)

---

### Post by koenn on 2012-09-05
> **The Cog said:**
> But if the computer is configured to allow VNC  ... 

You seem to have somehow managed to not see the sentence following the ones you quoted, the one where I say " [...] there are some rdp programs that make [interacting with an existing session] possible (vino maybe ? VNC ? ...)".

---

### Post by Ubun2to on 2012-09-06
> **holyman842 said:**
> Also, it is very possible to guess of brute force my password because my password is a four letter dictionary keyword.

Wow. My previous Admin account password was:
!!(e(rE@/\/\$@/\/|)\/\/!(hE$
I just adapted that from iicecreamsandwiches, by adding in obscure numbers and symbols.

---

### Post by critin on 2012-09-09
Something that I immediately thought of when I read these lines.

> I work as an online app developer> my work demands that I stay online during work hours so that is why I could not disconnect the internet.> I brag to my friends saying that my ubuntu netbook is better than their windows counterparts.Bragging to non-linux users can bring out the competition to prove you wrong.  You work in the field so someone will know how to get in.  They know the computer is on, and they may  even know when you go to lunch.  

They will think this is funny but show much concern for you.  Watch the coworkers faces when you speak to them of this.  

Someone probably showed you how any system is only as secure as its owner.
It was a windows user.  

lol, don't brag...especially to one who knows the ins and outs of a computer.

---

### Post by d3v1150m471c on 2012-09-10
> Also, it is very possible to guess of brute force my password because my password is a four letter dictionary keyword.

um, probably you should change the passwords for your online accounts...im guessing they're all the same four letter word.

---

### Post by mr-woof on 2012-09-10
have you still got the installation? Try running:

sudo netstat –tanp

This command will show you what programs/services are running and listening for incoming connections. 

Post the results if you still have the installation.

---

### Post by mike acker on 2012-09-11
> **holyman842 said:**
> OrangeCrate,
{snip}I will provide a strong password this time and also install firestarter{snip}
Thanks,
Arindom

strong password, yep, good idea. too many people get hacked simply because they didn't change the default password supplied at installation.

we normally do not log in as root in Ubuntu, rather using sudo to carry out changes to root specs.

but sudo requires your admin password. Google "common passwords",-- and "be advised"

ps

I just ran a [https://www.grc.com/intro.htm ]("https://www.grc.com/intro.htm")Gibson Research "Shields Up" test on my U-box (12.04) -- which is "just out of the box" -- and it passed, flying colors -- file sharing and port stealth tests

i would go into the suspect system and ,using TERMINAL, check
gsettings get org.gnome.Vino enabled

I tried this on my Out of the box 12.04 and the following value was returned
FALSE

i would not be surprised to find RD enabled if you are in a corporate environment
~~
this is an excellent thread; i hope we are able to pursue this to resolution.

---

### Post by CharlesA on 2012-09-11
FWIW, the "Shields up" test is pointless, it will only scan your router if you are behind one and Ubuntu ships with no open ports by default, so that's fine.

A "stealth" port is just a marketing term to sell security software. There is no difference between "stealth" and closed ports.

If you are in the corporate environment, there are better ways to connect to a *nix box than using VNC.

---

