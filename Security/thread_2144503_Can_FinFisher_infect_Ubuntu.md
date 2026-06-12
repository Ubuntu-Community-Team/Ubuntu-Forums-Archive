---
title: "Can FinFisher infect Ubuntu?"
date: 2013-05-12
forum: Security
---

### Post by D7Gd on 2013-05-12
[https://en.wikipedia.org/wiki/FinFisher](https://en.wikipedia.org/wiki/FinFisher)
[https://wikileaks.org/spyfiles/files/0/310_ELAMAN-IT_INTRUSION_FINFISHER_INTRODUCTION_V02-08.pdf](https://wikileaks.org/spyfiles/files/0/310_ELAMAN-IT_INTRUSION_FINFISHER_INTRODUCTION_V02-08.pdf)
[https://wikileaks.org/spyfiles/list/company-name/gamma.html](https://wikileaks.org/spyfiles/list/company-name/gamma.html)

It is important for activists and dissidents to know how to defend against such attacks.

How can a person protect oneself from FinFisher?

Is Ubuntu safe from such attacks? The Wikileaks documents mention that it can infect GNU/Linux systems as well as Windows and Mac OS.

One of the components of FinFisher is the FinFly transparent HTTP proxy that can fake signatures and also inject malicious code into programs and other files. Are there any methods to defend against those kinds of attacks?

---

### Post by stmiller on 2013-05-12
'Infect' is an odd way to think of this one. It is more of a targeted trojan for government computer systems that have been Windows.

In short I would not worry about it,

---

### Post by oldos2er on 2013-05-12
Moved to Security Discussions.

---

### Post by D7Gd on 2013-05-13
> **stmiller said:**
> 'Infect' is an odd way to think of this one. It is more of a targeted trojan for government computer systems that have been Windows.

If they target a system running Ubuntu, can they get root access to it? For example by using the FinFly HTTP transparent proxy?

If so, is there any way to detect them and protect yourself if you are targeted by FinFisher?

---

### Post by cariboo on 2013-05-14
If you are running a default Ubuntu install, the root account is disabled, so no worries there. The user is the biggest security problem, make sure you set a strong password, and practice safe computing.

---

### Post by nexus604 on 2013-05-25
would love to hear more on how to handle this rogue.

---

### Post by cariboo on 2013-05-25
> **nexus604 said:**
> would love to hear more on how to handle this rogue.

Seeing as it doesn't affect Linux based systems, you may need to go elsewhere to find an answer to your question

---

### Post by paulxx on 2013-05-26
I think d7gd makes a valid point.

There was a report on the BBC news yesterday about this Finfisher "product" being sold to governments to spy on those who oppose the government. The report said it had been found on computers and smartphones without the owners permission. The report did not say whether it was linux/android or others.

I think it is something that Linux Ubuntu users should take seriously. At the very least we need an open and honest discussion about it to allay any fears.

paul

---

### Post by paulxx on 2013-05-26
There is some interesting information on wikipedia about this issue.

Here's a paragraph from wikipedia/finfisher which should concern anyone using **Mozilla Firefox**:

[B]"Firefox Masquerading

FinFisher is capable of masquerading as other more legitimate programs, such as Mozilla Firefox. On April 30, 2013, Mozilla announced[20] that they had sent Gamma a cease-and-desist letter for trademark infringement. Gamma had created an espionage program that was entitled firefox.exe and even provided a version number and trademark claims to appear to be legitimate Firefox software." 

[/B](btw, Gamma is the company that owns Finfisher)

I'd be interested to hear the views of anyone with some expertise/knowledge of security matters concerning Linux/Ubuntu[B].

[/B]paul

---

### Post by Lars Noodén on 2013-05-26
> **paulxx said:**
> There was a report on the BBC news yesterday about this Finfisher "product" being sold to governments to spy on those who oppose the government. The report said it had been found on computers and smartphones without the owners permission. The report did not say whether it was linux/android or others.

Over the years I have noticed that the news almost makes a point of avoiding mention of systems that are immune. Whether because MS will cut them off from future press conferences or other reasons I do not not.  I just see the behavior.  

About FinFisher, there is little to no technical coverage, but one site does give a clue that it is Windows only
[https://blog.mozilla.org/blog/2013/04/30/protecting-our-brand-from-a-global-spyware-provider/](https://blog.mozilla.org/blog/2013/04/30/protecting-our-brand-from-a-global-spyware-provider/)

Maybe if you try it it might run under WINE but otherwise you'll have to run Windows in a VM for it to work.

---

### Post by paulxx on 2013-05-26
Thanks Lars,
That's reassuring.
paul

---

### Post by HermanAB on 2013-05-27
In general, Windows malware doesn't work on Linux, not even on Wine.  These things invariably exploits a very specific hole in a Windows system, which doesn't exist in Linux.

That being said, it is possible to exploit a badly configured Linux system.  If you use a kewl 4 letter password and installed VNC, FTP, Apache and other servers, then your system can possibly be hacked.

If you use a default Ubuntu installation and you set a 12 character password, then not.

So it is completely up to you, how hackable your system is.

---

### Post by jonnyboysmithy on 2013-05-29
There is always the posibility that there are unknown zero day exploits that someone could discover and develop exploit tools for.
Unlikely, but yes it could happen. And if it does happen it will be big news.

---

### Post by linuxtechguy on 2013-05-29
> **cariboo907 said:**
> If you are running a default Ubuntu install, the root account is disabled, so no worries there. The user is the biggest security problem, make sure you set a strong password, and practice safe computing.

No the problem is that root is disabled and you rely on sudo being secure. It is better to get rid of sudo alltogether and rely on having a strong root password and a strong user password. I cant stand sudo and is the first thing I always remove.

---

### Post by cariboo on 2013-05-30
I can't see sudo as being any less secure than root, with the same strong password. The big problem is using the root account improperly. The Debian way of doing things, is to have you create a root account along with a regular user account. You then use that normal user account, until you need to do something as an administrator.

To use the root account you then need to switch user:

```
su root
```

type your root password, and then type the command you want to use. Then when you are finished your administration task, switch back to your normal user. The one problem I see for those that have problems with passwords, is that they need to remember 2 passwords.

The Ubuntu way of doing things has you create just a user account, then when you need to do any system administration, you just type:

```
sudo <command>
```

and enter your password, or if it is a graphical program, press Alt-F2 and type:

```
gksu <command>
```

enter your password, and the program starts.

One thing I have to note, is that we all run as root when first using a Linux distribution other than Ubuntu, but as you gain experience, especially after making enough mistakes to destroy our running distribution several times, most of us opt for safety, instead of convenience.

---

### Post by Hungry Man on 2013-06-01
> **HermanAB said:**
> In general, Windows malware doesn't work on Linux, not even on Wine.  These things invariably exploits a very specific hole in a Windows system, which doesn't exist in Linux.

That being said, it is possible to exploit a badly configured Linux system.  If you use a kewl 4 letter password and installed VNC, FTP, Apache and other servers, then your system can possibly be hacked.

If you use a default Ubuntu installation and you set a 12 character password, then not.

So it is completely up to you, how hackable your system is.
Not really. By default Ubuntu isn't very secure at all. It's maybe on par with Windows 7, depending on the software you use. It takes some effort to make it secure, especially if we're talking about government malware like mentioned in the first post.

The password doesn't factor into it much.

---

### Post by monkeybrain2012 on 2013-06-01
> **cariboo907 said:**
> 

One thing I have to note, is that we all run as root when first using a Linux distribution other than Ubuntu, but as you gain experience, especially after making enough mistakes to destroy our running distribution several times, most of us opt for safety, instead of convenience.

Yeah, even when using other distros I prefer to use sudo which escalates adminstrative privilege for just the current commands. I am nervous about running a session as root. I haven't looked into the details but it seems that if there is a root there are certain things even sudoers don't have the permisison to do, it will only work by becoming root (su to root) I have encountered that quite often in Fedora.

---

### Post by cariboo on 2013-06-02
> **monkeybrain2012 said:**
> Yeah, even when using other distros I prefer to use sudo which escalates adminstrative privilege for just the current commands. I am nervous about running a session as root. I haven't looked into the details but it seems that if there is a root there are certain things even sudoers don't have the permisison to do, it will only work by becoming root (su to root) I have encountered that quite often in Fedora.

I have yet to find a task that:

```
sudo -i
```

will not take care of. I'm sure there are some corner cases that I haven't run into, that you actually need to be root to accomplish.

---

### Post by Lars Noodén on 2013-06-02
> **cariboo907 said:**
> I have yet to find a task that:

```
sudo -i
```

will not take care of. I'm sure there are some corner cases that I haven't run into, that you actually need to be root to accomplish.

One of the bigger advantages of sudo comes with multi-user systems.  With sudo it's possible to give permission to just specific tools and tasks.

---

### Post by monkeybrain2012 on 2013-06-02
> **cariboo907 said:**
> I have yet to find a task that:

```
sudo -i
```

will not take care of. I'm sure there are some corner cases that I haven't run into, that you actually need to be root to accomplish.

Like cd into /root . I use checkinstalll to compile programs in Fedora too. Unlike in Ubuntu, sudo checkinstall doesn't automatically install the package, instead it creates a .rpm inside a subfolder of  /root created by rpmbuild . But if I try to install the package with "sudo rpm -i pathtorpm" it will say permission denied and even just cd-ing into the the root directory is not permitted (I don't understand why sudo checkinstall is allowed to dump a package there in the first place) , however, if I actually become root (su) then it is ok.

---

### Post by cariboo on 2013-06-02
On Ubuntu:

```
sudo -i
```

puts you in /root, so this may be something in the way Fedora is setup. I haven't used checkinstall for years, and rarely compile from source as using ppas to get the latest and greatest always seems to work for me, others experiences may be different.

---

### Post by monkeybrain2012 on 2013-06-02
> **cariboo907 said:**
> On Ubuntu:

 I haven't used checkinstall for years, and rarely compile from source as using ppas to get the latest and greatest always seems to work for me, others experiences may be different.

ppa is a Ubuntu phenomenon, ;)  Fedora's official updates are in general very much ahead of Ubuntu's in terms of being bleeeding edge , there are also third party repos for other things. It can deliver the bleeding edge much better than Ubuntu and quite stable too. But there is a catch, that is, you will get the latest and greatest only if the binary  package is available but sometimes they are not so you have to compile. It seems that many more applications are readily availiable in .deb than in .rpm (and suse's .rpm may not install in Fedora and vice versa)

---

