---
title: "Obvious question? Why is Linux superior to Windows? Is it?"
date: 2006-12-19
forum: Windows
---

### Post by finferflu on 2006-12-19
I always hear people saying that Windows is bad, poorly designed, and so on, but to be honest, I don't know about it. The only things I've experienced with Windows are the famous blue screens of death, various crashing, viruses, and sometimes a very heavy system.

Well, apart from viruses, I get crashes and heavy load on Ubuntu as well. What I consider very valuable is the continuous development going on, and the wonderful community support. But as for comparison I haven't got proper knowledge to draw a line and say that Ubuntu is a superior OS. Not that I don't believe it, because I really enjoy the Linux world. I enjoy customising my system to my heart's desire, and most of all I enjoy Open Source. 

I am now asking to somebody more expert than me, why, at the end of the day, is Linux considered to be superior to Windows?

My doubts started when a friend of mine, a Linux user, told me that Windows is not bad, it's just the user's incapability that makes it unstable and unsecure. Well, I can't answer to that, because I've never been a Windows geek.

Finally I want to point out that I'm a full Ubuntu user, I have deleted Windows for good and I have no intention to go back, for my main reason to use Linux is because I'm in love with Open Source. Even though Windows would prove to be superior to Linux, I would still stick with Linux, because there's a better philosophy behind it, and I want to see it grow. 

Thanks for your time :)

---

### Post by matthew on 2006-12-19
[http://www.whylinuxisbetter.net/](http://www.whylinuxisbetter.net/)

has some interesting thoughts on the subject.

---

### Post by finferflu on 2006-12-19
Thanks for the link, very interesting and useful, even though is not as technical as I wanted...

---

### Post by milton1 on 2006-12-19
The big reason why linux, and any other unix based os, is better and more stable than windows has to do with the dependancy structure. The statement that instability comes from the user is inaccurate. Windows services have too much cross dependancy. This is why the entire system is likely to need a reboot if one service goes down. It is true that linux will crash on you, but when it happens, it is more likely that you will be able to restart the one service that crashed, leaving the rest of the system fully operational.

As for security, you can certainly set up decent security in windows. however, it is not well set up by default, and setting it up requires some finesse, as well as a willingness to sacrifice some of the system's functionality.

---

### Post by 23meg on 2006-12-19
[QUOTE=milton1]
As for security, you can certainly set up decent security in windows. however, it is not well set up by default, and setting it up requires some finesse, as well as a willingness to sacrifice some of the system's functionality.[/QUOTE]As well as some money.

---

### Post by darrenm on 2006-12-19
> **finferflu said:**
> I always hear people saying that Windows is bad, poorly designed, and so on, but to be honest, I don't know about it. The only things I've experienced with Windows are the famous blue screens of death, various crashing, viruses, and sometimes a very heavy system.

Windows isn't really all that bad in itself. Well it is but not as bad as we would like to believe sometimes. Its like an invention that a really nasty inventor has created. 

> **finferflu said:**
> Well, apart from viruses, I get crashes and heavy load on Ubuntu as well. 

I don't really. Crashes isn't very descriptive, it can mean a whole lot of things. I get some applications that are still in early development cause some troubles which I accept and expect due to them being described as being Alpha or Beta. This is a condition of me using them. Things like Beryl, Deluge etc. Even so the worst that can happen due to the modular make up of Ubuntu is you have to press CTRL-ALT-F1, go to a terminal and kill the process. Nothing ever takes the whole system down. The stable, mature products such as the Linux kernel itself, Apache, BASH etc. are unfeasibly stable.

> **finferflu said:**
> What I consider very valuable is the continuous development going on, and the wonderful community support. 

Yeah Ubuntu seems to have attracted a newer non ex-usenet crowd that are patient with the people they are trying to convert.

> **finferflu said:**
> But as for comparison I haven't got proper knowledge to draw a line and say that Ubuntu is a superior OS. 

It is, it really is, for a whole lot of reasons.

> **finferflu said:**
> Not that I don't believe it, because I really enjoy the Linux world. I enjoy customising my system to my heart's desire, and most of all I enjoy Open Source. 

I am now asking to somebody more expert than me, why, at the end of the day, is Linux considered to be superior to Windows?

I don't profess to be more expert than you but it's something I have experience in - 
For a start I prefer to refer to it as Ubuntu rather than Linux because Linux has become a too generic term for the GNU/Linux range of distributions. Ubuntu to me is the best of the distributions.

Windows is monolithic. Its all intertwined and cobbled together. If something bad happens then you are lucky if you can close the one app without taking the whole system down. Ubuntu is modular. The window manager sits on top of the X window system which sits on top of the shell which sits on top of the kernel (not exactly like that but Im making a point) so if an application does something bad its much more contained.

A big thing to me is that I don't get to see what Windows is doing to my system. I have to trust Microsoft to not let me see what the software I bought from them is doing. But it turns out I haven't actually bought anything. I've bought a license to use the software, which to me is still nothing. With Ubuntu I don't have time to review all the code personally but I have a fairly good idea that if anything was wrong then the power of peer review would get it sorted for me.

> **finferflu said:**
> My doubts started when a friend of mine, a Linux user, told me that Windows is not bad, it's just the user's incapability that makes it unstable and unsecure. Well, I can't answer to that, because I've never been a Windows geek.

To a point yes a user will help to make the system insecure and unstable by downloading and running rubbish off the internet. However even if Ubuntu was at 90% usage then I would be able to download and install rubbish off the internet and it still wouldn't cause the issues that Windows has purely because of the Unix security model. Anything I run only has the same permissions that I do, which is very little unless I'm root. All the people who say that Windows only has all the security problems because its widely used and if Linux was more widely used then it would be the other way round are wrong. Nothing can do anything to my system that I can't do.

> **finferflu said:**
> Finally I want to point out that I'm a full Ubuntu user, I have deleted Windows for good and I have no intention to go back, for my main reason to use Linux is because I'm in love with Open Source. Even though Windows would prove to be superior to Linux, I would still stick with Linux, because there's a better philosophy behind it, and I want to see it grow. 

Thanks for your time :)

Good for you. :)

---

### Post by 3rdalbum on 2006-12-20
Linux/Unix has an incredible scripting language inside it, and a huge number of programs that can be scripted through it; you can link multiple programs together to achieve a result that is larger than the sum of its parts.

I don't think I can talk about GNU/Linux's power in a sufficiently technical way, so I won't try.

As far as crashes go, what you probably see is the X server crashing. I have two computers - one using the ati driver and the other using fglrx. The Fglrx (proprietry ATI driver) machine occasionally crashes, but the one using the open-source driver simply doesn't crash.

Even when the fglrx machine crashes, it's only actually Xorg and client applications that freeze. Emergency kernel key combinations still work, which tells me that Linux itself is still running - it's just that the usual input and output is still being hogged by Xorg and as such, the usual key presses and mouse movements are being swallowed up.

---

