---
title: "Does running Firefox as a different (non privileged) user provide better security?"
date: 2010-09-25
forum: Security
---

### Post by DodgeV83 on 2010-09-25
So I've finally figured out how to run Firefox as another user without errors.  I created a non-privileged user called "ff", then ran this command from the terminal:

```
gksu -u ff firefox
```

This seems to be the closest Ubuntu can get to Fedora's [Sandbox Mode]("http://danwalsh.livejournal.com/31146.html"), but still providing the full functionality of resizing the window, full flash without slowdown...etc.

Is my thinking on this wrong?  I've always read that even if you get a virus in Linux, it won't matter because it will only be able to touch your personal /home files.  Someone inevitably argues that their own personal /home files are the only important files on their computer!

By running Firefox as the "ff" user, I have confirmed that my personal /home files cannot be accessed from the Firefox session.  Am I missing something, or is this an effective sandbox?

---

### Post by sanderd17 on 2010-09-25
if there's al leak in firefox, it wont be able to affect you if you use a non-privileged user. But if you can still download a virus to your computer like that. Off cource the virus needs to be executed afterwards with your own user account. This is unlikely to happen by accident and very difficult (if not impossible) to code. But if you donwload and execute a trojan, you'll be infected without a doubt.

---

### Post by DodgeV83 on 2010-09-25
> **sanderd17 said:**
> if there's al leak in firefox, it wont be able to affect you if you use a non-privileged user. But if you can still download a virus to your computer like that. Off cource the virus needs to be executed afterwards with your own user account. This is unlikely to happen by accident and very difficult (if not impossible) to code. But if you donwload and execute a trojan, you'll be infected without a doubt.

Yea I understand that, if I download a file it doesn't matter where the file came from, if I run it and give it my password I'm toast.  I'm more worried about drive-by javascript vulnerabilities, or something else which requires 0 user intervention.

I recently got a virus on my Windows box simply by visiting a webpage.  No clicking no downloading at all.  I actually walked away from my computer before the page finished loading, and by the time I returned I had already been infected with Antivirus 2010.  It was asking me for admin permissions, and instead of saying no (expecting something would run anyway) I did a hard-boot of my machine and brought Windows back up, but to no avail.  I was infected.

Even though Linux is much much less vulnerable to these type of attacks by default, I would still like an extra layer of protection.  I think that running Firefox in this fashion would sandbox me from such attacks.  Even if one occurs, I can easily remove the "ff" user and create a new one.

Is my thinking accurate?

---

### Post by Rubi1200 on 2010-09-25
Have you looked into using AppArmor?
[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)
[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

---

### Post by OpSecShellshock on 2010-09-25
Even user accounts that have sudo privileges are still non-privileged until used with sudo to perform an administrative action. Since no one does that with Firefox (because there's no need to and it would be stupid), there's no risk present that would be mitigated by using a different account.

---

### Post by SeijiSensei on 2010-09-25
> **DodgeV83 said:**
> I recently got a virus on my Windows box simply by visiting a webpage.  No clicking no downloading at all.  I actually walked away from my computer before the page finished loading, and by the time I returned I had already been infected with Antivirus 2010.

The phony "antivirus" ploy uses Javascript. I encountered it on my Linux box when I visited the [New York Times]("http://bits.blogs.nytimes.com/2009/09/14/times-site-was-victim-of-a-malicious-ad-swap/") site some months ago.  The Javascript waits for you to close or navigate away from the infected page, then opens a page of its own from a remote web server that purports to be scanning your Windows hard drive.  Looks pretty realistic, too.  

Still it didn't take me more than a second or two to laugh at how it supposedly was finding dozens of infections on my non-existent C: drive.  

You can protect yourself against these ploys by adding the [Noscript]("https://addons.mozilla.org/en-US/firefox/addon/722/") extension to Firefox, but since most popular websites these days are full of JS scripts, it can quickly become rather tedious to review them all and decide which to allow.  [AdBlock Plus]("https://addons.mozilla.org/en-US/firefox/addon/1865/") can also help since it often has dicey sites in its database.  

Antivirus 2010 wouldn't be able to infect your Linux computer no matter how you have browsing configured.  In fact, I know of no exploit that infects Linux machines purely by visiting a site.  Perhaps others have experienced this, and I'm just lucky, but I think there just isn't that much out there that can hurt you without some action on your part.

(Note that I'm not saying Linux viruses can't exist, or that I couldn't accidentally run a script even as an ordinary user that would turn my computer into a spambot.  Hell, I could probably write one of those myself using just bash if I had any interest in doing so.  On the other hand, I've been using Linux for fifteen years on workstations and Internet-facing servers, and the last time I encountered an exploit on one of my boxes was almost a decade ago now, and that was a flaw in the Apache web server.)

---

### Post by bodhi.zazen on 2010-09-25
I do not think you gain much with that.

IMO you should use apparmor and NoScript

See : [How to Secure Firefox - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=671604")

---

### Post by DodgeV83 on 2010-09-26
> **bodhi.zazen said:**
> I do not think you gain much with that.

IMO you should use apparmor and NoScript

See : [How to Secure Firefox - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=671604")

What I'm trying to gain is added protection of my /home files.  My pictures and other priceless data stored in my Documents.  As I understand it, while nothing has yet been found in the wild, a vulnerability in Firefox (or any other program run with user-permissions) would give an attacker access to the /home drive which is currently running Firefox.

If that's /home/ff, I don't care.

If that's /home/DodgeV83, I do.

I think apparmor would give me the same protection, but I've heard that can cause some additional headaches, Firefox refusing to open, Flash not working...etc.  Is anyone here happily running Firefox with AppArmor and not experiencing any issues?

---

### Post by bodhi.zazen on 2010-09-26
> **DodgeV83 said:**
> What I'm trying to gain is added protection of my /home files.  My pictures and other priceless data stored in my Documents.  As I understand it, while nothing has yet been found in the wild, a vulnerability in Firefox (or any other program run with user-permissions) would give an attacker access to the /home drive which is currently running Firefox.

If that's /home/ff, I don't care.

If that's /home/DodgeV83, I do.

I think apparmor would give me the same protection, but I've heard that can cause some additional headaches, Firefox refusing to open, Flash not working...etc.  Is anyone here happily running Firefox with AppArmor and not experiencing any issues?

The default firefox profile seems to work for most, you may need to lock down files in $HOME a bit.

See my firefox profile here :

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.bin.firefox](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.bin.firefox)

If you have problem you will indeed need to learn to debug apparmor.

---

### Post by DodgeV83 on 2010-09-26
> **bodhi.zazen said:**
> The default firefox profile seems to work for most, you may need to lock down files in $HOME a bit.

See my firefox profile here :

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.bin.firefox](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.bin.firefox)

If you have problem you will indeed need to learn to debug apparmor.

What advantages would using AppArmor give me over running as a different user?  I'd prefer not to learn something new for little to no gain :)

---

### Post by bodhi.zazen on 2010-09-26
> **DodgeV83 said:**
> What advantages would using AppArmor give me over running as a different user?

1. Apparmor is much more secure, at least in terms of system files, and likely with your user files as well.

2. A firefox apparmor profile is included by default, you need to enable it.

> I'd prefer not to learn something new for little to no gain :)

/me wonders, if you are not willing to learn or listen to the advice of others, why start a thread ?

---

### Post by wacky_sung on 2010-09-26
> **bodhi.zazen said:**
> 1. Apparmor is much more secure, at least in terms of system files, and likely with your user files as well.

2. A firefox apparmor profile is included by default, you need to enable it.



/me wonders, if you are not willing to learn or listen to the advice of others, why start a thread ?

I just got a good laugh over it and didn't meant to be rude.Probably he just wanna run something that is quick and easy without much learning or configuration.:guitar:

---

### Post by Rubi1200 on 2010-09-26
> What advantages would using AppArmor give me over running as a different  user?  I'd prefer not to learn something new for little to no gainAs they say, no pain, no gain.

See here for some of the advantages:
[http://developer.novell.com/wiki/index.php/Apparmor_FAQ#What_are_the_advantages_of_AppArmor_over_SELinux.3F](http://developer.novell.com/wiki/index.php/Apparmor_FAQ#What_are_the_advantages_of_AppArmor_over_SELinux.3F)

Although this is a comparison, read carefully and you will understand why AppArmor is being recommended.

---

### Post by DodgeV83 on 2010-09-26
Understood.  So I activated the Firefox profile:

```
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox
```

and restarted Firefox (even rebooted), but it doesn't seem to be working.  When I open Firefox I am able to perform a "Save Page As" in locations I shouldn't be able to, like my Desktop or Pictures folder.

The following command says the Firefox process is in enforce mode:

```
sudo apparmor_status
```

Am I simply not understanding how this should work?  Of the following lines, the only directory which is "rw" is /Downloads, why am I still able to write to other places?

```
  # Default profile allows downloads to ~/Downloads and uploads from ~/Public
  owner @{HOME}/ r,
  owner @{HOME}/Public/ r,
  owner @{HOME}/Public/* r,
  owner @{HOME}/Downloads/ r,
  owner @{HOME}/Downloads/* rw,

```

Edit:  I'm using the 10.10 beta, so it may be a bug :(

Edit 2: Making a new thread for the AppArmor issue.  Consider me convinced :)

---

### Post by aysiu on 2010-09-26
> **DodgeV83 said:**
> What I'm trying to gain is added protection of my /home files.  My pictures and other priceless data stored in my Documents.  As I understand it, while nothing has yet been found in the wild, a vulnerability in Firefox (or any other program run with user-permissions) would give an attacker access to the /home drive which is currently running Firefox.

If that's /home/ff, I don't care.

If that's /home/DodgeV83, I do. In that case, I'd recommend buying an external hard drive and regularly backing up /home/DodgeV83 to it using *rsync*.

---

### Post by DodgeV83 on 2010-09-26
So I activated the Firefox profile:

```
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox
```

and restarted Firefox (even rebooted), but it doesn't seem to be working.  When I open Firefox I am able to perform a "Save Page As" in locations I shouldn't be able to, like my Desktop or Pictures folder.

The following command says the Firefox process is in enforce mode:

```
sudo apparmor_status
```

Am I simply not understanding how this should work?  Of the following lines, the only directory which is "rw" is /Downloads, why am I still able to write to other places?

```
  # Default profile allows downloads to ~/Downloads and uploads from ~/Public
  owner @{HOME}/ r,
  owner @{HOME}/Public/ r,
  owner @{HOME}/Public/* r,
  owner @{HOME}/Downloads/ r,
  owner @{HOME}/Downloads/* rw,

```

Note: I'm using the 10.10 beta, so it may be a bug :(

---

### Post by rookcifer on 2010-09-26
Could be a bug.  If the snip from the profile is correct, it should not be allowing anything to write to any /home directory other than /Downloads.  I am on 10.04 here and the default profile is different.  Mine looks like this:

 ```
# allow read and write to all user's files, except explicitly denied ones
  @{HOME}/ r,
  @{HOME}/** r,
  owner @{HOME}/** w,
  owner @{HOME}/Desktop/** r,
```

---

### Post by Rubi1200 on 2010-09-26
To help troubleshoot issues you could/should put the profile in complain mode.

Then open a terminal and run ```
tail -F /var/log/messages
``` and then start Firefox and do normal things like browsing, downloading etc.

You will hopefully be able to then figure out what is going on or post back here with error messages and questions.

---

### Post by cariboo on 2010-09-26
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by OpSecShellshock on 2010-09-26
After you selected the Desktop and/or Pictures folders from the Save Page As menu, did you browse to the folders and see if the files you saved were actually there? It's possible that it just silently failed rather than telling you that Firefox doesn't have access.

---

### Post by DodgeV83 on 2010-09-26
> **cariboo907 said:**
> Please don't create multiple threads on the same subject, I have merged your two threads.

I am no longer interested in running Firefox as a different user.

I am now interested in getting my Firefox AppArmor profile working.  Can you change the thread title to reflect this?  If not just close the thread and I'll open a new one again.

---

### Post by DodgeV83 on 2010-09-26
> **OpSecShellshock said:**
> After you selected the Desktop and/or Pictures folders from the Save Page As menu, did you browse to the folders and see if the files you saved were actually there? It's possible that it just silently failed rather than telling you that Firefox doesn't have access.

Yes, the files were actually created.

---

### Post by cariboo on 2010-09-26
Closed by request, as the op has created a new thread in Maverick Testing and Discussion.

---

### Post by DZ* on 2010-09-27
> **aysiu said:**
> In that case, I'd recommend buying an external hard drive and regularly backing up /home/DodgeV83 to it using *rsync*.

A possibility that sensitive data can be stolen is also a threat. It seems to me that running firefox as a firefox-dedicated user provides a quick but effective protection.

---

