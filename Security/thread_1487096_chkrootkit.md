---
title: "chkrootkit"
date: 2010-05-18
forum: Security
---

### Post by joeman225 on 2010-05-18
Hi all,

I've recently installed rkhunter and chkrootkit, but I have no idea how to use them. Can someone direct me to a well known thread with some simple instruction on how to use them to scan my computer?

Thanks

---

### Post by iponeverything on 2010-05-18
They are not hard, but be aware that you will get false positives. Do google search on your positives and they will be easy to identify and it will save you from posting back in bit of a panic like so many other have.

---

### Post by bodhi.zazen on 2010-05-18
> **joeman225 said:**
> Hi all,

I've recently installed rkhunter and chkrootkit, but I have no idea how to use them. Can someone direct me to a well known thread with some simple instruction on how to use them to scan my computer?

Thanks

This information is linked in the security sticky at the top of these forums.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

[http://ubuntuforums.org/showthread.php?t=1477662](http://ubuntuforums.org/showthread.php?t=1477662)

[http://ubuntuforums.org/showpost.php?p=9265639&postcount=7](http://ubuntuforums.org/showpost.php?p=9265639&postcount=7)
[http://ubuntuforums.org/showpost.php?p=9265649&postcount=8](http://ubuntuforums.org/showpost.php?p=9265649&postcount=8)

---

### Post by joeman225 on 2010-05-19
> **bodhi.zazen said:**
> This information is linked in the security sticky at the top of these forums.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

[http://ubuntuforums.org/showthread.php?t=1477662](http://ubuntuforums.org/showthread.php?t=1477662)

[http://ubuntuforums.org/showpost.php?p=9265639&postcount=7](http://ubuntuforums.org/showpost.php?p=9265639&postcount=7)
[http://ubuntuforums.org/showpost.php?p=9265649&postcount=8](http://ubuntuforums.org/showpost.php?p=9265649&postcount=8)


Thank you so much for the links. For the 3rd link, do i just go to Applications--> Accessories----> Terminal and enter: "sudo chkrootkit"  to start a complete search?

Does the chkrootkit program automatically clean up infections for you? What do you do if infected files are found?

---

### Post by HermanAB on 2010-05-19
Hmm, you are wasting your time.  These things are quite useless.

---

### Post by Rubi1200 on 2010-05-19
> **HermanAB said:**
> Hmm, you are wasting your time.  These things are quite useless.

With all due respect, I am not sure if useless is the right way to describe these tools. 

What I would say is that they are definately not for beginners and that there are other, perhaps better, methods of ensuring that your system is as secure as possible thereby negating the need to use them in the first place.

---

### Post by HermanAB on 2010-05-19
Yeah well, I've been running UNIX systems since about 1985 on thousands of machines and have never encountered a real life rootkit.  Some other crapware yes, but no rootkits.

The best way to detect clandestine activity is by monitoring the log files and network traffic.

---

### Post by bodhi.zazen on 2010-05-19
> **joeman225 said:**
> Thank you so much for the links. For the 3rd link, do i just go to Applications--> Accessories----> Terminal and enter: "sudo chkrootkit"  to start a complete search?

Does the chkrootkit program automatically clean up infections for you? What do you do if infected files are found?

Please read the documentation on chkrootkit.

> **HermanAB said:**
> Hmm, you are wasting your time.  These things are quite useless.

As Herman points out, Linux is not windows and you are better off reading the security sticky.

If you are unwilling to read man pages and find the command line intimidating i suggest you are better off relaxing. Linux is much more secure and scanning for viruses, rootkits, spyware etc is not the place to start with security.

Read the stickies I already gave you.

> **Rubi1200 said:**
> With all due respect, I am not sure if useless is the right way to describe these tools. 

What I would say is that they are definately not for beginners and that there are other, perhaps better, methods of ensuring that your system is as secure as possible thereby negating the need to use them in the first place.

It has a role, just not the role users migrating from Windows envision.

While these tools are essential, or at least many many people are convinced they are, in Windows, in general these tools play a very minor role in Linux security.

In reality, IMO, as long as someone has hardened his or her system, they play a minor role in Windows as well. The problem is most people do not harden Windows, thus they get these things, and they need to be cleaned.

The saying "An ounce pf prevention is worth a pound of cure" applies here, and Linux has a few pounds of prevention ...

---

### Post by Rubi1200 on 2010-05-19
> **HermanAB said:**
> Yeah well, I've been running UNIX systems since about 1985 on thousands of machines and have never encountered a real life rootkit.  Some other crapware yes, but no rootkits.

The best way to detect clandestine activity is by monitoring the log files and network traffic.

I do not doubt your experience or knowledge, and I agree with you about checking log files and network traffic.

As bodhi.zazen points out:
> While these tools are essential, or at least many many people are convinced they are, in Windows, in general these tools play a very minor role in Linux security. 

I was only trying to make this point to the OP.

---

### Post by joeman225 on 2010-05-20
> **HermanAB said:**
> Hmm, you are wasting your time.  These things are quite useless.


@ HermanAB - I'm going to be completely honest... I don't really need this kind of feedback, I don't think its helpful and its a bit insulting.  I'm seeing these kinds of 'answers' alot on the ubuntu forums. I asked a questioned, and really do appreciate answers to the question. But I didn't ask to be judged or asked for your opinion on whether my question was valid or not.



@bodhi.zazen - I appreciate your help bodhi.zazen.

---

### Post by bodhi.zazen on 2010-05-20
> **joeman225 said:**
> @ HermanAB - I'm going to be completely honest... I don't really need this kind of feedback, I don't think its helpful and its a bit insulting.  I'm seeing these kinds of 'answers' alot on the ubuntu forums. I asked a questioned, and really do appreciate answers to the question. But I didn't ask to be judged or asked for your opinion on whether my question was valid or not.



@bodhi.zazen - I appreciate your help bodhi.zazen.

You are most welcome

Honestly, this question is asked frequently and as difficult as it may be to hear, there are no shortcuts with security, you need to read, read, read and diligently monitor these tools.

Everyone uses their systems differently, Desktop vs Server, but even on Desktops , firefox vs Chromium ?, Mono or no ? , Java or icedtea ? Flash or no flash ? etc, etc, etc.

So at the end of the day, these tools can point you to things you should look into, but only you can validate the findings. Honestly, this is true of similar tools in Windows as well.

With that said, HermanAB has given you some of the best advice and I do not think his intention was to be dismissive.

If you are interested , take a look at some of the other tools at your disposal, snort, wireshark, OSSEC, and OpenVAS to mention a few.

You probably will not understand them at first, but once you learn these tools they will server you better then chkrootkit, IMO at least.

Also take a look at tiger.

On the other side of the coin, if these tools seem too advanced or too difficult to learn, again I suggest you relax and enjoy Linux.  rootkits exist but they are extremely rare (this is not Windows).

The vast majority of security issues seen on these forums are :

1. Physical access. Look at all the threads here that boil down to someone with physical access reading unauthorized files or passwords. This it probably #1.

2. Weak passwords. 

3. As a result of #2, people then install VNS (desktop sharing) or less commonly SSH then share the connection over the internet. If you use these two services, learn to secure them BEFORE you connect to the internet.

4. Social engineering. Do not run scripts or commands or install applications from untrusted software.

Hard to think of an issue on these forums not covered by one (or more) of the above examples.

Rootkits come second, after an intruder gains access and much damage / problems can occur without root access, so, relying on rootkit detection for intrusion detection is not a great idea. Keep in mind, these tools scan only for known rootkits. And modern cracker is going to check his or her rootkit aginst these tools BEFORE deploying it, which is why we like to emphasize PREVENTION and tools such as apparmor or selinux.

---

