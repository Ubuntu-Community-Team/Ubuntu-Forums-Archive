---
title: "Securing Firefox"
date: 2007-07-15
forum: Server Platforms
---

### Post by weth on 2007-07-15
What steps have you taken to secure your Firefox browser?

---

### Post by M$LOL on 2007-07-15
All you need to do is Install NoScript, Adblock Plus and McAfee Site Advisor, disable cookies (I manually add sites I want to allow) and keep it updated ;)

---

### Post by weth on 2007-07-15
thanks, M$LOL :)

---

### Post by RoyalShrubber on 2007-07-15
AFAIK Feisty doesn't support Systrace (that's what I would do on BSD), maybe you can try installing SELinux or AppArmor :) 
What's funny though is that default installation of IE on Vista (protected mode) is safer than default installation of Firefox on Ubuntu. ;)

---

### Post by M$LOL on 2007-07-16
Explain how that's the case.

---

### Post by p_quarles on 2007-07-16
> **RoyalShrubber said:**
> AFAIK Feisty doesn't support Systrace (that's what I would do on BSD), maybe you can try installing SELinux or AppArmor :) 
What's funny though is that default installation of IE on Vista (protected mode) is safer than default installation of Firefox on Ubuntu. ;)
Because of disabled ActiveX controls and UAC? "Safe," maybe, but definitely irritating to use. 

Safer than FF on Ubuntu, though, I have to disagree. Even without Noscript, you're not going to get scripts trying to log in as root and installing keyloggers. The scale of Microsoft's security problems, and the speed at which they get patched, prevents it from ever being all that safe.

---

### Post by weth on 2007-07-16
Well, how do I deactivate ActiveX?

---

### Post by p_quarles on 2007-07-16
You don't, unless you're using Windows. It doesn't exist in Linux.

---

### Post by weth on 2007-07-17
Well, I was wondering today: 
" why do most URL's have www at the beginning and some don't?"

---

### Post by netkid91 on 2007-07-17
Uhmm, that was random.  But that's an easy question, the www is just a legacy thing, honestly, theses days you don't need the www anymore.

---

### Post by weth on 2007-07-17
I though the presence or absence of "www" denoted some kind of special, different kind of sites...ok, but when I sometimes omit the "www" the browser can't find the location!
has it got something to do with DNS?

---

### Post by netkid91 on 2007-07-17
Yup, it has something to do with DNS.  That something is: the person(s) that set up the site didn't add a DNS entry for the site without the www.  That's it

---

### Post by RoyalShrubber on 2007-07-19
> **p_quarles said:**
> Because of disabled ActiveX controls and UAC? "Safe," maybe, but definitely irritating to use. 

Safer than FF on Ubuntu, though, I have to disagree. Even without Noscript, you're not going to get scripts trying to log in as root and installing keyloggers. The scale of Microsoft's security problems, and the speed at which they get patched, prevents it from ever being all that safe.

Sure firefox is a priori safer - because why? - being foss??

Why don't you go on Secunia page and see for yourself that IE and firefox got roughly the same amout of exploit when comparing IE7 and FF2. Though it's true that IE6 was a mess (that's why I used Opera before IE7 came out). 

While FF2 has slightly less bugs (than IE7) Ubuntu makes sure they'll propagate with potentially greater destruction. 
IE7 on Vista runs in protected mode with limited context upon which hacked IE can influence - IE is jailed in Vista. While you can easily protect FF in many unixes, by default in Ubuntu FF can do a lot more damage than IE7 in Vista with default setup. Looks like that is compromise for not having 'inconvenience' named UAC. :S

---

### Post by p_quarles on 2007-07-19
It would be a bit more helpful if you would explain exactly what kind of "potentially greater destruction" is invited by using Firefox in Ubuntu.

That said, two points:
1) Firefox is vulnerable, sure, but Ubuntu doesn't run it as a root application (by default, at least, and only stupid people would alter that). MSIE7 actually does run under the administrator's account (again, by default, but only smart people would change it in this case). If someone were to figure out how to compromise UAC, it would immediately present a threat to every Vista system in existence. If someone figures out how to crack my password, it presents a threat to me. 

2) I didn't say that Firefox was safer than IE7; I said that Firefox in Ubuntu is more reliably safe. 

If you can point to some non-default things that Ubuntu users could do to make it (even) safer, though, please do (that being the thread topic and all).

---

### Post by Matakoo on 2007-07-19
> **p_quarles said:**
> 
If you can point to some non-default things that Ubuntu users could do to make it (even) safer, though, please do (that being the thread topic and all).

One thing, slightly paranoid and somewhat complex, would be to use a chroot jail. AKA "Where Microsoft got the idea of running IE7 in its own sandbox in Vista". 

Then again, I'm not sure what MS did what that idea in Vista but there's something not quite right about it. Or maybe it was my, now wiped, installation of Vista that was acting up. I didn't do a thorough check on what it might have been, but IE was stubborn as a mule and refused to run in its own sandbox.

---

### Post by p_quarles on 2007-07-19
I had to look that up, but you're right: that would definitely do the trick. 

I'll stick with NoScript and Flashblock for security in FF, but that will definitely go on my to-do list for securing my server. Thanks.

---

### Post by RoyalShrubber on 2007-07-20
> **p_quarles said:**
> It would be a bit more helpful if you would explain exactly what kind of "potentially greater destruction" is invited by using Firefox in Ubuntu.

That said, two points:
1) Firefox is vulnerable, sure, but Ubuntu doesn't run it as a root application (by default, at least, and only stupid people would alter that). MSIE7 actually does run under the administrator's account (again, by default, but only smart people would change it in this case). If someone were to figure out how to compromise UAC, it would immediately present a threat to every Vista system in existence. If someone figures out how to crack my password, it presents a threat to me. 

2) I didn't say that Firefox was safer than IE7; I said that Firefox in Ubuntu is more reliably safe. 

If you can point to some non-default things that Ubuntu users could do to make it (even) safer, though, please do (that being the thread topic and all).

1) Well, it's false assumption and quite stupid one too, that if you don't run application in root it's 'safe'. But it's not. While it's true that normally nonroot application could not break the system - it could totally destroy all user's documents. So if you don't take extra measures with setting file flags (ie. not having everything 777) and running ff with different user, ff can potentially corrupt those files. And I would much rather have broken system than my my files lost. ;-)
Also in Vista as far as I know IE runs in unprivileged mode, where it can access only few folders, but with ability to increase permissions with UAC. While it's true there is possibility someone can break UAC - it's imo harder, because fair amount of it runs in kernel. The same would be breaking ff and getting root under linux - you 'just' have to break kernel :P.

2) As someone suggested, you can chroot it, but that is usually very hard with bigger applications. AFAIK selinux isn't available for ubuntu, however you can download AppArmor, but you have to patch your kernel. :S
Anyway, here's the link [https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor). You effectively have to jail ff to only few folders. I hope however that it gives you 'UAC' if you want to go outside - you see UAC is not that wrong ;)

---

### Post by Adnarim on 2007-07-20
Well why flashblock? If noscript does this too ?

My Plugins for safer and anonymous surfing:
* noscript (restricts js,java,flash,adobe,... with whitelisting)
* cookiesafe (restricts cookies with whitelisting)
* refcontrol (restricts referres with whitelisting)
* modify headers (changes user-agent)
* RIP
* AdblockPlus
* foxyproxy

+privoxy+tor

---

### Post by weth on 2007-07-20
Thank you all for the pointers :)

FF gets a bit sluggish having all these addons installed but it's at least safer, so that's a fair tradeoff.

---

### Post by Matakoo on 2007-07-20
> **RoyalShrubber said:**
> 1) Well, it's false assumption and quite stupid one too, that if you don't run application in root it's 'safe'. But it's not. While it's true that normally nonroot application could not break the system - it could totally destroy all user's documents. So if you don't take extra measures with setting file flags (ie. not having everything 777) and running ff with different user, ff can potentially corrupt those files. And I would much rather have broken system than my my files lost. ;-) 

True. It is safer to run as non-root, but not safe. Nothing is totally safe. But there are a couple of things to do to make FF safer (and some of them applies to Firefox on windows too).

1. The chroot jail I already mentioned
2. Running FF as another user (iow, setting up a firefox user and group)
3. Set the file permissions on your own files to, for example, 0660
4. Set up a special partition for FF cache and other data and mount it noexec,nosuid (alternatively, mount /home that way). That would make firefox incapable of running malicious software (like say a shell-script).

> **RoyalShrubber said:**
> Also in Vista as far as I know IE runs in unprivileged mode, where it can access only few folders, but with ability to increase permissions with UAC. While it's true there is possibility someone can break UAC - it's imo harder, because fair amount of it runs in kernel. The same would be breaking ff and getting root under linux - you 'just' have to break kernel :P.

There is a difference though. The kernel can obviously not be turned off. UAC can. And in my experience, most Vista users do just that - even those who should know better. I can't say I can blame them either, since it's a royal pain in the ***. The biggest problem with UAC is that it turns up so often that, when still turned on, people don't bother to read the dialogue. They just click okay (or type the password and click ok, depending on how it's set up) to go away. IMO, UAC do not promote better security. Other things in Vista do, and UAC would had it been better implemented. 

> **RoyalShrubber said:**
>  2) As someone suggested, you can chroot it, but that is usually very hard with bigger applications. 

That depends. To get firefox's basic functionality in a chroot jail is not for a Linux newbie, I grant you that. It's not terribly complicated if you have some experience though. The biggest problem is that you'll have to copy quite a few extra applications and libraries into the jail if you want to enhance firefox with, for example, the acrobat plugin.

> **RoyalShrubber said:**
> [AFAIK selinux isn't available for ubuntu, however you can download AppArmor, but you have to patch your kernel. :S]

SELinux is installed by default. Or rather, the shared libraries are. The tools for creating policies are not, but available through apt-get. AppArmor is available too, in the universe section (and you don't need to patch the kernel, you need to compile a kernel module). See [http://outflux.net/blog/archives/2007/04/02/apparmor-now-in-feisty/](http://outflux.net/blog/archives/2007/04/02/apparmor-now-in-feisty/)

---

### Post by RoyalShrubber on 2007-07-20
> **Matakoo said:**
> There is a difference though. The kernel can obviously not be turned off. UAC can. And in my experience, most Vista users do just that - even those who should know better. I can't say I can blame them either, since it's a royal pain in the ***. The biggest problem with UAC is that it turns up so often that, when still turned on, people don't bother to read the dialogue. They just click okay (or type the password and click ok, depending on how it's set up) to go away. IMO, UAC do not promote better security. Other things in Vista do, and UAC would had it been better implemented. 


I don't think UAC is too annoying and I've been using Vista since January. ;) 
Also if users disable it then they cannot blame MS for breaking their computer. :)

---

### Post by Matakoo on 2007-07-20
> **RoyalShrubber said:**
> I don't think UAC is too annoying and I've been using Vista since January. ;) 
Also if users disable it then they cannot blame MS for breaking their computer. :)

No, they can't. It's their own fault after all. Still, just the fact that it can be disabled tells me that it is probably only a matter of time before UAC is compromised. 

For people who know what they're doing, UAC is just another layer of protection and a rather thin one at that (maybe with the exception of IE7's sandbox). In most cases, it can be compared to the "Are you sure you really want to delete that file Yes|No" dialog. It wasn't designed to protect the system from malware or viruses. It was designed to protect the system (and the user) from the user so, for example, the user does not disable the firewall or something equally stupid by mistake or because they think they know what they're doing. And don't take my word for it. It's what Microsoft says.

It is quite easy to have a windows system where the user does not have administrative rights without UAC enabled, provided you know what you're doing. If you don't know what you're doing, it is a good thing to have.

Then again, if the user tries to install a program for example, UAC is going to prove to be of little help in preventing damage to the system. I'm talking home users here, btw. In a corporate setting, the administrator in charge has hopefully locked down the computer further than the defaults. Anyway, most PC users do not know enough to know what can potentially be damaging to their operating system (regardless of what system they're using). UAC will not change that. It will, at best, be just another dialog window to answer before the computer does what the user asked of it. 

It is, IMO, dumb to rely on the user to make informed choices in what is harmful to the OS and what is not. Which, essentially, is what UAC is doing. Is prog_x.msi a program with included advertisment programs or a keylogger? The user, in most cases, does not know, so the chances are rather big that will just go ahead and install anyway no matter if UAC is left enabled or not. And hey, yet another windows box with unwanted software.  

Is it good that UAC exist? Yes. Any extra layer of security can only be a good thing. It is, however, overrated in how much extra security it provides. It is much more important to have working anti-spyware (Windows Defender is decent, but not enough) and anti-virus software with the definitions up-to-date, and a  working firewall. UAC can, in other words, give a false sense of security.

Sorry for the rant.

---

### Post by RoyalShrubber on 2007-07-20
> **Matakoo said:**
> No, they can't. It's their own fault after all. Still, just the fact that it can be disabled tells me that it is probably only a matter of time before UAC is compromised. 

For people who know what they're doing, UAC is just another layer of protection and a rather thin one at that (maybe with the exception of IE7's sandbox). In most cases, it can be compared to the "Are you sure you really want to delete that file Yes|No" dialog. It wasn't designed to protect the system from malware or viruses. It was designed to protect the system (and the user) from the user so, for example, the user does not disable the firewall or something equally stupid by mistake or because they think they know what they're doing. And don't take my word for it. It's what Microsoft says.

It is quite easy to have a windows system where the user does not have administrative rights without UAC enabled, provided you know what you're doing. If you don't know what you're doing, it is a good thing to have.

Then again, if the user tries to install a program for example, UAC is going to prove to be of little help in preventing damage to the system. I'm talking home users here, btw. In a corporate setting, the administrator in charge has hopefully locked down the computer further than the defaults. Anyway, most PC users do not know enough to know what can potentially be damaging to their operating system (regardless of what system they're using). UAC will not change that. It will, at best, be just another dialog window to answer before the computer does what the user asked of it. 

It is, IMO, dumb to rely on the user to make informed choices in what is harmful to the OS and what is not. Which, essentially, is what UAC is doing. Is prog_x.msi a program with included advertisment programs or a keylogger? The user, in most cases, does not know, so the chances are rather big that will just go ahead and install anyway no matter if UAC is left enabled or not. And hey, yet another windows box with unwanted software.  

Is it good that UAC exist? Yes. Any extra layer of security can only be a good thing. It is, however, overrated in how much extra security it provides. It is much more important to have working anti-spyware (Windows Defender is decent, but not enough) and anti-virus software with the definitions up-to-date, and a  working firewall. UAC can, in other words, give a false sense of security.

Sorry for the rant.

Utter BS. UAC is only link between unprivileged user and privileged user. It operates on the same level as some graphical tools in Unix (like when you run Synaptic it ask you for confirmation - it's unix UAC). You people bow down to sudo and at the same time bash similar technologies on Windows. 

Again, both in Unix and Windows dumb user can download malware - but that has nothing to do with UAC. 

*" Still, just the fact that it can be disabled tells me that it is probably only a matter of time before UAC is compromised."* - you can also disable sudo and run root all the time in unix. You see how ignorant this statement was?

*"In most cases, it can be compared to the "Are you sure you really want to delete that file Yes|No" dialog."*
Yes? UAC is in kernel mode - out of reach to the application - so did you want to make a point?

*" It wasn't designed to protect the system from malware or viruses. It was designed to protect the system (and the user) from the user so, for example, the user does not disable the firewall or something equally stupid by mistake or because they think they know what they're doing."*
It was designed to keep usermode code unpriviliged until special permissions are needed. It's up to user to decide if they really are. If the user is dumb, then they can use limited account without UAC. However it's hard to make users do that or teach them how to use UAC properly (not answering always with 'yes').

---

### Post by weth on 2007-07-21
> **Adnarim said:**
> Well why flashblock? If noscript does this too ?

My Plugins for safer and anonymous surfing:
* noscript (restricts js,java,flash,adobe,... with whitelisting)
* cookiesafe (restricts cookies with whitelisting)
* refcontrol (restricts referres with whitelisting)
* modify headers (changes user-agent)
* RIP
* AdblockPlus
* foxyproxy

+privoxy+tor

Well, I installed Foxyproxy. I was asked two questions along the installation, the answers to which I was not sure of. The first question was "PLease enter the port on which privoxy is listening"...I chose the default -8118. The next question was "Would you like the DNS requests to go through the TOR network" and again, as I was not sure what to say, selected "Yes".
Are these settings ok, or do you think there could be better ones?
Next I had to configure a pattern for the proxy, and I put a "*" in order to get all the url's through the proxy, or at least that is what I thought I was doing. The problem is that when I tried to open sites FF said proxy didn't allow connections. So I removed the patterns in order to be able to browse the internet after all. And now I think the Foxyproxy is not actually working because when I check my ip on the "Show my IP" sites they all show me my IP(well I thought it should be different). Btw I am assigned an IP by DHCP.
I guess my questions may sound not taht clear but that's how my computernetworks literacy is!

So how do I know if the Proxy is working properly with the desired effect?

thank you :)

---

### Post by Adnarim on 2007-07-21
hi weth,
yes it's good to answer the second question with yes because you won't be dns leaking when hostresolution is done!

But you have taken the wrong port, by default it is 9050 and not 8118! Go to the proxy details and switch this to port=9050, hostname=127.0.0.1 and Socks v5 Proxy. 

Next I can recommend installing vidalia to check if everything with tor is right.

The rule you did was right and also I'm doing it this way. Make a new rule, call it all and make it just with a * and set it to whitelist, so all sites will by default be loaded through that proxy.

if it continues to refuse to work ask again :)

two additional tips for tor:
* [http://wiki.noreply.org/noreply/TheOnionRouter/FireFoxTorPerf](http://wiki.noreply.org/noreply/TheOnionRouter/FireFoxTorPerf) (helps with timeouts)
* [https://addons.mozilla.org/en-US/firefox/addon/546](https://addons.mozilla.org/en-US/firefox/addon/546) (for better handling of them)

---

### Post by weth on 2007-07-21
Thank you Adnarim!
I reconfigured Foxyproxy as you advised me and now it is working :)
Vidalia can only be compiled from source, and this is something I have never done before so I'll leave it for some other time.

regards

---

### Post by Adnarim on 2007-07-21
no problem dude ;) but if you want to compile it just test it, I will help you with any problems you get, it's really easy.

---

### Post by weth on 2007-07-22
It seems something is not working properly because while compiling Vidalia from source I receive the following

-------------------------------------
configure: Running qmake...
/usr/bin/uic-qt4 src/gui/mainwindow.ui -o src/gen/ui/ui_mainwindow.h
Could not create output file
make: *** [src/gen/ui/ui_mainwindow.h] Error 1
-------------------------------------

now I have no idea what point I have come to :(


any ideas? Thanks :)

---

### Post by Adnarim on 2007-07-22
have you QT4 installed? Check this with:
> 
$ **qmake -v**
QMake version 2.01a
Using Qt version 4.2.3 in /usr/lib


here I found a little howto which also sais which packages you need to install with apt-get: [http://ubuntuforums.org/showthread.php?t=287349](http://ubuntuforums.org/showthread.php?t=287349)

---

### Post by weth on 2007-07-22
Thank you very much again for your help Adnarim :)

yep, I have the same output for "qmake" but again the same error occurred... but, anyway, having followed the how-to, now everything seems to be working just fine :)

now I am starting to install Snort...

cheers

---

