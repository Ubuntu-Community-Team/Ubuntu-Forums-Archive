---
title: "Install Internet Explorer"
date: 2010-11-22
forum: Wine
---

### Post by Githan13 on 2010-11-22
Hi,
Im very new to Linux and Ubuntu.
Anybody can guide me to install Internet Explorer in Ubuntu 10.04. Im try to install IEs4Linux-2.99.0 but get this error message:

"Downloading everything we need
  Downloading from microsoft.com:
   0%   IE7-WindowsXP-x86-enu.exe
  Downloading from Evolt Browser Archive:
   0%   ie55sp2_9x.zip!! Could not find a suitable Evolt mirror"

The process while installing. 

Please guide me if there is any other way to install Internet Explorer in Ubuntu. I really need it. Thank you.

---

### Post by WienerWuerstel on 2010-11-22
You can install the Internet Explorer with [PlayOnLinux]("http://www.playonlinux.com/en/").

---

### Post by handy on 2010-11-22
You can install it with winetricks also:

[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

---

### Post by emoguitarist06 on 2010-11-22
> **handy said:**
> You can install it with winetricks also:

[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

I just installed ie8 using winetricks but IE just kept freezing. I then installed ie6 & ie6_full but again IE still wouldn't work. I finally have ie7 working however is there a way to have flash/java to work as well?
I ran winetricks flash and it says it installed successfully but ie7 still isn't using flash

---

### Post by handy on 2010-11-23
> **emoguitarist06 said:**
> I just installed ie8 using winetricks but IE just kept freezing. I then installed ie6 & ie6_full but again IE still wouldn't work. I finally have ie7 working however is there a way to have flash/java to work as well?
I ran winetricks flash and it says it installed successfully but ie7 still isn't using flash

I can't help you as I don't need to use any of the IEs.

I made the post in an effort to help the OP as they may not have known about winetricks being new to Linux & all. I hoped that winetricks would provide an easy solution to the problem...

---

### Post by tjwilli on 2010-11-23
Check out the Wine Application database for Internet Explorer
The recommended Wine supported version is IE6

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=469]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=469")

Also check out the Wine FAQ

[http://wiki.winehq.org/FAQ#head-69ca5e820c6eef64196e1830bf7f09521c2a4843]("http://wiki.winehq.org/FAQ#head-69ca5e820c6eef64196e1830bf7f09521c2a4843")

---

### Post by bobwyajnr on 2010-11-24
> **Githan13 said:**
> 
Please guide me if there is any other way to install Internet Explorer in Ubuntu. I really need it. Thank you.

I am not sure exactly why you would need IE to work in Ubuntu... you haven't said. IE 6 is supported but badly. Basically Internet Explorer has too many hooks back into the Windows OS (which are not supported when running it in Wine). IE 7 and IE 8 support is even worse/less developed.

A native web browser (like Opera, Firefox, SeaMonkey, Chrome, Konquerer, etc.) is always going to give you a far better experience as an end user. Perhaps in the bad ole' days when IE had a monopoly it was a necessary evil but in recent times most webpages don't need activeX or other MS concoctions...

I'm afraid to say if you really can't live without Internet Explorer, in Ubuntu, the only option really is a virtualised MS OS (installed in VirtualBox, VMWare, etc). [ReactOS]("http://www.reactos.org/en/index.html") isn't mature enough (even for a Virtual environment) yet.

Bob

---

### Post by ivanovnegro on 2010-11-24
> **bobwyajnr said:**
> I am not sure exactly why you would need IE to work in Ubuntu... you haven't said. IE 6 is supported but badly. Basically Internet Explorer has too many hooks back into the Windows OS (which are not supported when running it in Wine). IE 7 and IE 8 support is even worse/less developed.

A native web browser (like Opera, Firefox, SeaMonkey, Chrome, Konquerer, etc.) is always going to give you a far better experience as an end user. Perhaps in the bad ole' days when IE had a monopoly it was a necessary evil but in recent times most webpages don't need activeX or other MS concoctions...

I'm afraid to say if you really can't live without Internet Explorer, in Ubuntu, the only option really is a virtualised MS OS (installed in VirtualBox, VMWare, etc). [ReactOS]("http://www.reactos.org/en/index.html") isn't mature enough (even for a Virtual environment) yet.

Bob

Definitely, why you need the Internet Explorer, you are on Linux, man.
Try one of the mentioned browsers, they are far better as the one of MS.
I used to use Firefox also in my Windows time, the best browser for me.

---

### Post by emoguitarist06 on 2010-11-24
**I 100% Agree that Internet Explorer SUCKS!!** As I am 100% Ubuntu my self 
**[COLOR="Red"]BUT[/COLOR]** Unfortuantely there is a **[COLOR="red"]NEED [/COLOR]**for IE

myitlab.com a website used by my school requires IE! Even in their support/faq they recommend virtualizing Windows in either MAC/Linux to run IE since they're site uses Active X

minuteman a website for National Guard Tuition Assistance Requires IE

Usually it's a government or educational site that requires IE

---

### Post by tjwilli on 2010-11-24
I wish IE6 were better supported in Wine. There are still some sites that just don't work right with other browsers. (Are you listening BSA?) I try to stay in Linux/Firefox whenever I can, but sometimes I just have to boot into XP via VirtualBox so I can use IE. (At least I don't have to boot into my Visa partition.) 

I'm active in Scouting, and the some of the pages at scoutnet.scouting.org work in Firefox, but forget about Internet Advancement or Internet Charter Renewal. There are some functions that are IE specific.  Very frustrating.

---

### Post by handy on 2010-11-24
> **emoguitarist06 said:**
> **I 100% Agree that Internet Explorer SUCKS!!** As I am 100% Ubuntu my self 
**[COLOR="Red"]BUT[/COLOR]** Unfortuantely there is a **[COLOR="red"]NEED [/COLOR]**for IE

myitlab.com a website used by my school requires IE! Even in their support/faq they recommend virtualizing Windows in either MAC/Linux to run IE since they're site uses Active X

minuteman a website for National Guard Tuition Assistance Requires IE

Usually it's a government or educational site that requires IE

> **tjwilli said:**
> I wish IE6 were better supported in Wine. There are still some sites that just don't work right with other browsers. (Are you listening BSA?) I try to stay in Linux/Firefox whenever I can, but sometimes I just have to boot into XP via VirtualBox so I can use IE. (At least I don't have to boot into my Visa partition.) 

I'm active in Scouting, and the some of the pages at scoutnet.scouting.org work in Firefox, but forget about Internet Advancement or Internet Charter Renewal. There are some functions that are IE specific.  Very frustrating.

You guys should give the [**_User Agent Switcher_**]("https://addons.mozilla.org/en-US/firefox/addon/59/"), Firefox add-on a try, it just might (with a bit of luck) solve your problems.

---

### Post by ivanovnegro on 2010-11-24
> **emoguitarist06 said:**
> **I 100% Agree that Internet Explorer SUCKS!!** As I am 100% Ubuntu my self 
**[COLOR=Red]BUT[/COLOR]** Unfortuantely there is a **[COLOR=red]NEED [/COLOR]**for IE

myitlab.com a website used by my school requires IE! Even in their support/faq they recommend virtualizing Windows in either MAC/Linux to run IE since they're site uses Active X

minuteman a website for National Guard Tuition Assistance Requires IE

Usually it's a government or educational site that requires IE

Now I understand it.
Never could imagine that IE could be important for some people because of your problems, never herad about this.

---

### Post by tjwilli on 2010-11-24
I seem to remember trying that or something like it a while ago. It didn't help in my case, but I'll give it another try.

---

### Post by tjwilli on 2010-11-24
> **handy said:**
> You guys should give the [**_User Agent Switcher_**]("https://addons.mozilla.org/en-US/firefox/addon/59/"), Firefox add-on a try, it just might (with a bit of luck) solve your problems.

I installed it and tried it with setting user agent IE8. When I click on on of the buttons on the web page I get

Error: document.frmRoster.item is not a function
Source File: [https://scoutnet.scouting.org/IADV/ui/IAdvProcess/wbfAdvancementRoster.aspx](https://scoutnet.scouting.org/IADV/ui/IAdvProcess/wbfAdvancementRoster.aspx)
Line: 61

---

### Post by Githan13 on 2010-12-02
> **bobwyajnr said:**
> I am not sure exactly why you would need IE to work in Ubuntu... you haven't said. IE 6 is supported but badly. Basically Internet Explorer has too many hooks back into the Windows OS (which are not supported when running it in Wine). IE 7 and IE 8 support is even worse/less developed.

A native web browser (like Opera, Firefox, SeaMonkey, Chrome, Konquerer, etc.) is always going to give you a far better experience as an end user. Perhaps in the bad ole' days when IE had a monopoly it was a necessary evil but in recent times most webpages don't need activeX or other MS concoctions...

I'm afraid to say if you really can't live without Internet Explorer, in Ubuntu, the only option really is a virtualised MS OS (installed in VirtualBox, VMWare, etc). [ReactOS]("http://www.reactos.org/en/index.html") isn't mature enough (even for a Virtual environment) yet.

Bob

Hi..
Same as [emoguitarist06]("http://ubuntuforums.org/member.php?u=555068"), there is need for IE at my work place. There is a system called HRMIS (Human Resource Management Information System) that need to use IE. It doesnt support any other browser. Yeah, its true that IE sucks.. I had it very much, but there is no other solution for me. Please help.[IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]

---

### Post by vduke on 2011-02-11
Sadly to say, that as a LAMP Developer I still have to test sites in IE for cross browser compatibility testing. And EVEN Worse is this forces me to specifically have a VBox install of WinXP JUST to use IE.  

My opinion... Internet Explorer needs to just Die. It doesn't provide any added value at all. Instead it monopolizes on proprietary plug-ins and active x controls (silverlight for one.. Thank you moonlight project for helping us out with that but, it is still the main reason why streaming netflix video's on ubuntu does NOT work).

If Microsucks would just follow standards (which they NEVER will) instead of trying to create their own the world would be a better place. However, we keep hacking away and making our Free OS better, our OS apps better. Eventually we shall win =P

Until then, Us web developers, online school users, government site users, have to take a walk of shame until a real solution becomes available. And the only real solution in my opinion is for IE to either Die, or conform to the standards and stop making life hard for everyone. 

I have said my piece.

---

