---
title: "Samba security"
date: 2011-09-10
forum: Security
---

### Post by Advait on 2011-09-10
Hi All,

Any one ever hear of a Windows virus within Ubuntu using Samba to jump over and infect the Windows partition? Say I have a USB stick infected with some Windows malware. Then I insert this stick into an Ubuntu machine. Could the Windows malware use Samba as a way to infect Windows? Just curious.

Thanks!

Tom the Hyper-vigilant

---

### Post by haqking on 2011-09-10
> **Advait said:**
> Hi All,

Any one ever hear of a Windows virus within Ubuntu using Samba to jump over and infect the Windows partition? Say I have a USB stick infected with some Windows malware. Then I insert this stick into an Ubuntu machine. Could the Windows malware use Samba as a way to infect Windows? Just curious.

Thanks!

Tom the Hyper-vigilant

In short yes.

If you use or share files with Windows then a AV scanner is recommended such as ClamAV, this is the only reason why AV scanners are used in Linux to be honest.

Linux does not suffer from Viruses like other OS, there are no known viruses in the wild, the main reason using AV on linux is to scan incase you share files with windows users.

It can still suffer from trojans, rootkits etc, but that comes down to vigilence and making sure you stick to the security model and not disabling passwords or enabling root etc.

Common sense, dont tell your system you want it to do something unless you are sure etc. Linux assumes you know what you are doing ;-)

In browsers you can still suffer from XSS or CSFR, other script related issues so use things like NoScript plugin for firefox, Ad-block etc.

See here for Anti-Virus information:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

See below for Bodhi.Zazen's overview of Linux Security

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

So yes if you use or share Windows files then use a scanner to help protect the windows users and files

---

### Post by Advait on 2011-09-10
Hi,

Thanks for the info. I have Avast AV installed and I use it to scan all USB sticks before I use them in Windows. That is a habit now and I will make it a stronger habit based on your feedback. Thanks!

I presume ClamAV and Avast for Ubuntu are about the same in effectiveness. Let me know if one has a reputation for being a lot better than the other. Maybe I should use both? I also presume they won't conflict if I have both installed. Let me know if they do conflict.

I also have No-Script and Cert Patrol installed in my Ubuntu FireFox. I'm a huge fan of No-Script.

I have also read thru Bodhi.Zazen's overview of Linux Security. Good stuff!

Thanks!

Tom

---

### Post by haqking on 2011-09-10
> **Advait said:**
> Hi,

Thanks for the info. I have Avast AV installed and I use it to scan all USB sticks before I use them in Windows. That is a habit now and I will make it a stronger habit based on your feedback. Thanks!

I presume ClamAV and Avast for Ubuntu are about the same in effectiveness. Let me know if one has a reputation for being a lot better than the other. Maybe I should use both? I also presume they won't conflict if I have both installed. Let me know if they do conflict.

I also have No-Script and Cert Patrol installed in my Ubuntu FireFox. I'm a huge fan of No-Script.

I have also read thru Bodhi.Zazen's overview of Linux Security. Good stuff!

Thanks!

Tom

All scanners are pretty much the same really. comes down to the regularity of definitions updates more than anything, some are more resource hungry than others and some have more features.

Avast should do the trick, as long as your samba shares are set to be scanned and not just your USB sticks ;-)

---

### Post by Advait on 2011-09-10
I think my Samba is set to share ALL the files in my Windows "My Docs" directory (which includes all my docs, pics, audio and video files). You're saying I should scan all these files? Essentially all my user files in Windows? Just want to make sure I understand.

On my Windows side I currently do weekly full disk scans using MS Security Essentials and Eeye "Blink". Both are highly rated scanners. You think I should also scan them using Ubuntu Avast?

Thanks!

Tom

---

### Post by haqking on 2011-09-10
> **Advait said:**
> I think my Samba is set to share ALL the files in my Windows "My Docs" directory (which includes all my docs, pics, audio and video files). You're saying I should scan all these files? Essentially all my user files in Windows? Just want to make sure I understand.

On my Windows side I currently do weekly full disk scans using MS Security Essentials and Eeye "Blink". Both are highly rated scanners. You think I should also scan them using Ubuntu Avast?

Thanks!

Tom

Scan any files the go to or come from windows, doesnt matter if they come from windows with a virus but if you are then gonna pass it back or onwards then scan them.

in short, scan all files from or to windows

---

### Post by Advait on 2011-09-10
I'm guessing that 99.99% Windows malware does not have code that would allow it to use Samba to jump over to the Windows side. Is this true? I'm guessing the malware authors would have to specifically include code that would allow it to use Samba to jump to Windows. And I'm guessing zero malware authors care about this (very very tiny?) attack vector into Windows. Just want to check my assumptions. I'm an uber newbie. Thanks!

Also, I've turned off ALL my Ubuntu auto-run settings.

Tom (paranoid? perhaps...)

---

### Post by haqking on 2011-09-10
> **Advait said:**
> I'm guessing that 99.99% Windows malware does not have code that would allow it to use Samba to jump over to the Windows side. Is this true? I'm guessing the malware authors would have to specifically include code that would allow it to use Samba to jump to Windows. And I'm guessing zero malware authors care about this (very very tiny?) attack vector into Windows. Just want to check my assumptions. I'm an uber newbie. Thanks!

Also, I've turned off ALL my Ubuntu auto-run settings.

Tom (paranoid? perhaps...)


Viruses do not jump anywhere on there own, they are propogated by execution of the infected file or through file transer and distribution.

You are using samba which is to allow file transfer/sharing of windows files.

So scan all files that come or go to windows

---

### Post by Advait on 2011-09-10
All my Windows files get well scanned by the 2 AV tools, so I think they're safe. In general, I trade very few files back and forth between Ubuntu and Windows. But I'll start scanning them. Sounds like always scanning USB sticks is my main line of defense. Thanks!

---

### Post by haqking on 2011-09-10
> **Advait said:**
> All my Windows files get well scanned by the 2 AV tools, so I think they're safe. In general, I trade very few files back and forth between Ubuntu and Windows. But I'll start scanning them. Sounds like always scanning USB sticks is my main line of defense. Thanks!


No problem, the best defence is a good offence and the best approach to security is to treat it as a process not a product and use it in layered approach (as you say, 2 levels of AV)

You are welcome, if you feel this is solved please remember to use thread tools to mark it solved so to assist others in there search for solutions.

Cheers and have a great day.

---

### Post by Advait on 2011-09-10
Is it safe to say that almost zero Windows malware has code that would *automatically* detect Samba on an Ubuntu machine and use that to jump to Windows with no user interaction? I'm guessing, that under normal conditions, malware on Ubuntu couldn't do this without triggering an admin authentication dialog box. Thanks!

---

### Post by haqking on 2011-09-10
> **Advait said:**
> Is it safe to say that almost zero Windows malware has code that would *automatically* detect Samba on an Ubuntu machine and use that to jump to Windows with no user interaction? I'm guessing, that under normal conditions, malware on Ubuntu couldn't do this without triggering an admin authentication dialog box. Thanks!


See post #8

Like i said just scan all from and to windows then even if it could it wouldnt matter cos you are scanning all from and to.

The virus wont effect linux

---

### Post by Advait on 2011-09-10
> **haqking said:**
> See post #8
Like i said just scan all from and to windows then even if it could it wouldnt matter cos you are scanning all from and to. The virus wont effect linux

OK, thanks. Good advice. I wish I had the skills to write a little program that would automatically virus scan all files that move to and from Windows, and automatically scan any inserted USB drive. But, alas, I have no programming experience. When I get time I can research and see if ClamAV can be programmed or scripted to do that.

Cheers!

---

### Post by haqking on 2011-09-10
> **Advait said:**
> OK, thanks. Good advice. I wish I had the skills to write a little program that would automatically virus scan all files that move to and from Windows, and automatically scan any inserted USB drive. But, alas, I have no programming experience. When I get time I can research and see if ClamAV can be programmed or scripted to do that.

Cheers!


no need.

your AV software will scan what folders you ask it to.

When folders change if viruses are detected the AV software will flag them.

Any new folders added (like USB) should be done transparently depending on configuration.

If they required you to manual scan everything then AV wouldnt work

---

