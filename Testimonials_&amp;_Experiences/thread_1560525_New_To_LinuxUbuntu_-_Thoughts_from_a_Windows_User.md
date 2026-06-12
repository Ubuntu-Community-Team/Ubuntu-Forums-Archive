---
title: "New To Linux/Ubuntu - Thoughts from a Windows User"
date: 2010-08-25
forum: Testimonials &amp; Experiences
---

### Post by ColdSun on 2010-08-25
Hello,

I've been using Windows since before even Windows 3.0.  I've been through just about every version of Windows you can imagine in my adult life so far.  I've made a career out of programming for the Windows OS (WinForms, WPF, ASP.NET, Silverlight, VB, C#, and so on).  I have a pretty successful career in a nameless top company.

All that said, I have never used Linux before.  I was always too busy learning my next Windows thing.  My first real install of Linux was the version of Ubuntu currently available, I believe it is Lucid Lynx?  I consider myself a pretty smart fellow, but what was I thinking?  I have been doing myself a disservice by not getting into Linux sooner.

First, I was impressed by the ease of installation and compatibility along the Windows OS.  The small size and speed while retaining the visual quality I expect from Windows was shocking.  The number of applications available, and the quality of many of them, was astounding.  One thing I noticed about many Linux applications is that they have all the features I am looking for and are visually built with a sensible user interface.  Extra waste/garbage features I would never use are left out.  Awesome.

If I could run all my Windows applications I use for work on this OS, I would.  It is smart, fast, and fun.  I toyed with several of the many distributions for Linux, but I kept coming back to Ubuntu.  I think the Linux Mint distro is very good too.

The thing that brought me into the fold here was my netbook.  I've been using Windows 7 on it since I purchased it.  I have an ASUS 1005PEB Pinetree chipset with 2GB RAM and a 250GB hard drive.  I'm posting this very message on the netbook.  Windows doesn't exist here, as I use this device for surfing, reading, videos, and music.  I have compiz enabled with advanced effects and I have no slowdown whatsoever.

So another Linux fan is born.  Time for me learn application development for Linux. :)

---

### Post by Ms_Angel_D on 2010-08-25
Thanks for your feedback, I've moved your thread to Testimonials & Experiences.

---

### Post by ColdSun on 2010-08-25
> **Ms_Angel_D said:**
> Thanks for your feedback, I've moved your thread to Testimonials & Experiences.

Sorry to put it in the wrong place. :)  I should have looked harder at the forum list.

EDIT:  There is one thing I don't like, and seems to exist in almost all these distros I've tried.  The password security stuff is overboard.  I'm on my netbook or my home PC.  I should be able to turn that nonsense off and on as I need it with a simple single password request.  I absolutely hate the User Access Control (UAC) that popped up in Windows Vista, was sorta improved in Windows 7.  I turn UAC off all the time.  I can turn it on when I have guests, but even UAC doesn't ask me to type my password all the time.  Blech.  Being a newbie, does someone know an easy way to turn off the security feature that does this?

---

### Post by mastablasta on 2010-08-25
It doesnt' ask for password all the time. It only asks you when you install somehting that affects the whole system.
 
Let's say a malicous program would want to install it self. well it can't not here. not unless you type in the password and giving him permission to install. 
 
Once you install everything you need you will only need to type in the password for updates.
 
oh and i think you are confusing this password with file encryption. you files can still easilly be accessed even if you have this password for you account. this passowrd is basically just to protect you from malicious programmes.
 
In windows (especially older version) the programmes can run themselves or they get into some auto exec or start up folders. well here they can't, not unless you provide them the password.

---

### Post by linux-hack on 2010-08-25
> **ColdSun said:**
> 
So another Linux fan is born.  Time for me learn application development for Linux. :)

Welcome to the linux world ;)

---

### Post by malspa on 2010-08-25
> **ColdSun said:**
> The password security stuff is overboard.

Seems to be a common sentiment among folks new to Linux, although I can't remember ever feeling that way.  I feel like it's just part of what makes Linux so much more secure than Windows.

---

### Post by Dayofswords on 2010-08-25
> **malspa said:**
> Seems to be a common sentiment among folks new to Linux, although I can't remember ever feeling that way.  I feel like it's just part of what makes Linux so much more secure than Windows.

yeah, unlike in windows i have actually stop working on things that affect the OS when the prompted comes up, like "should i really run this with root privileges, the ultimate power of the OS?"

---

### Post by Jay Car on 2010-08-25
> **ColdSun said:**
>  There is one thing I don't like, and seems to exist in almost all these distros I've tried.  The password security stuff is overboard.  I'm on my netbook or my home PC.  I should be able to turn that nonsense off and on as I need it with a simple single password request. [...] Being a newbie, does someone know an easy way to turn off the security feature that does this?

The need for passwords has never felt intrusive to me, until Lucid came out. Right after a fresh Lucid install, every time the monitor went blank, a password was needed to get back to the desktop. It was very annoying, but it was caused by the default screen-saver settings in Lucid, which were very easy to change.

> Uncheck: "lock screen when screen saver is activated" in the System->Preferences->Screen Saver menu.  

Also, changing the settings to 'automatic Login after suspend' might help too. [[COLOR="RoyalBlue"]This page has the steps to make that change[/COLOR]]("https://help.ubuntu.com/community/AutoLogin") (scroll towards the bottom of the page).

:)

---

### Post by ColdSun on 2010-08-25
Thank you so much for the tips.  Just to be clear, the password thing is not a deal-breaker for me.  I do like the fact that the OS is secure.  I will shut off the screensaver password and change the suspend settings and I think that will make it more than comfortable for me.

I honestly wish I could run this OS 100% of the time and replace Windows.  I can't though, as my job requires otherwise.  At least for now. :)

---

### Post by Jay Car on 2010-08-25
> **ColdSun said:**
> Thank you so much for the tips.  Just to be clear, the password thing is not a deal-breaker for me.  I do like the fact that the OS is secure.  I will shut off the screensaver password and change the suspend settings and I think that will make it more than comfortable for me.

I honestly wish I could run this OS 100% of the time and replace Windows.  I can't though, as my job requires otherwise.  At least for now. :)

ColdSun, I think all of us here understand that sometimes you just need to use Windows. But these days no one has to use Windows **only** any more, which is great. I hope you have as much fun learning your way around Ubuntu as I did. :)

P.S., please mark this as solved if the solution worked for you.

---

### Post by bouncingwilf on 2010-08-25
As a user that absolutely hates systems that are forever asking for confirmation of actions or passwords ( I'm a big boy now and can take responsibility for my actions!) I sympathize with Coldsun and recommend that he does as  I do ( but at his own risk) that is go for pass-wordless login, give a blank password for keyring (and the bloody irritating little app goes away) and use configuration editor to  set the default actions to your preferences. I do however approve of the the sudo philosophy - and if you find that your doing a lot of privileged work in a terminal and sudo expires, I believe I right in saying that the default timeout can be extended. If you set it up right, Linux is a delight to work with!

bouncingwilf

---

### Post by mastablasta on 2010-08-26
> **bouncingwilf said:**
> As a user that absolutely hates systems that are forever asking for confirmation of actions or passwords ( I'm a big boy now and can take responsibility for my actions!) I sympathize with Coldsun and recommend that he does as I do ( but at his own risk) that is go for pass-wordless login, give a blank password for keyring (and the bloody irritating little app goes away) and use configuration editor to set the default actions to your preferences. I do however approve of the the sudo philosophy - and if you find that your doing a lot of privileged work in a terminal and sudo expires, I believe I right in saying that the default timeout can be extended. If you set it up right, Linux is a delight to work with!
 
bouncingwilf
 
 
So a virus/malware would just insert blank password and it's good to go on a rampage in your system. so much for being a big boy... Ever used windows? Did you run it without antivirus? Because antivirus (with firewall) does all the checking there arround the system so you don't /shouldnt' have to worry abotu passwords there. shouldn't... for example if a programm want to access internet (on my WinxP) my firewall will pop up asking me if i know the program. no password here, but i am sure this firewall function could be tuned off. but at least it's something... So if i don't know the programme i look it up or do a scan of it.
 
Again the password is not so much to protect the system form you or you from the system. it's there to protect the system from malicious actions performed by programmes. at least that's how i understand from what i read.

---

### Post by bouncingwilf on 2010-08-26
I stated passwordless login not no password ( except keyring - which only hold my WEP code) I do in fact use a strong password so access to the system (via sudo) is still secure. My home account only contains trivial data, there is no ssh set up, so I believe I can afford to be (reasonably) smug!

---

### Post by Sef on 2010-08-28
> I stated passwordless login not no password ( except keyring - which only hold my WEP code)

If you are using WEP, then you are insecure.  WEP has been so thoroughly hacked that it is useless as security.

---

### Post by Swagman on 2010-08-29
> **Sef said:**
> If you are using WEP, then you are insecure.  WEP has been so thoroughly hacked that it is useless as security.

And yet I have used 64 bit WEP (and still do) since going broadband about 12 years ago without issue.

---

### Post by finny388 on 2010-08-29
Check out monodevelop for a C# API.

Welcome to the freedom of open source :D

---

