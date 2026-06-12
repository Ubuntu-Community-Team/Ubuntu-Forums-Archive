---
title: "Security Aspects of Linux and Windows"
date: 2010-09-30
forum: Security
---

### Post by GiuHei3u on 2010-09-30
Hello. I have read that Linux does not have the security issues like Windows and their constant security updates does. The idea of not having ports on Linux is a big difference. Is this to say that Linux would not be a good system for online bill paying and other aspects of banking? If one can still do this increasing activity in today's world with Linux than what does Linux have that allows great security that creates problems with a Window operating system?

Thanks.

---

### Post by marin123 on 2010-09-30
in linux you are using limited user rights, while in windows you are administrator all the time. they are trying to fix it with win 7, but its very easy for everyone to get administrator privileges. in ubuntu its a bit different because you have to type admin password each time you try to make changes to the system. and ubuntu wont run .exe files unless you assign them to wine. and one more thing: ubuntu uses open source apps, so no need for crack, keygen and stuff like that...

---

### Post by endotherm on 2010-09-30
this is a very advanced very technical question (at least if you want a real answer) so lets just start by saying that I will not touch my bank online UNLESS i am using linux. with windows, there is just no way to know that your session is private. 

as for your assertion about ports, ubuntu has ports (all Internet capable devices use TCP and UDP ports; just the way the internet works) but all of ubuntu's are closed by default, whereas there are some ports open by default on windows systems that make it susceptible to some attacks right out of the box. with linux, you have to specifically state that you want to install and use a network service, so you know it's running and you can secure it as is appropriate for that service. 

Linux is very partitioned, and each wall between processes or services acts as a security layer. one process can't read the data of another process for instance. Linux is made of many small parts each of which is designed to stand alone, so each peice takes it's own security seriously. as a result you end up with many many tiny barriers that build together into a very secure structure.

---

### Post by srhart on 2010-09-30
The safest way I can think of to access your bank using a 'standard' pc would be to download a 'live cd' version of Linux e.g. Ubuntu desktop. When you want to access your bank, boot that CD, access the bank and perform your transactions then shutdown the machine when finished. That way you are definitely using a modern updated 'clean' operating system and browser.

Simon
-----
[http://www.L3n.co.uk](http://www.L3n.co.uk) L3n Voice and Data Network Solutions - Contact L3n for voice and data network design, supply, installation and support - 24/7 cover available - based in Cambridge UK

---

### Post by oldos2er on 2010-09-30
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by uRock on 2010-09-30
Moved to Security Discussions sub-forum.

---

### Post by LMB on 2010-09-30
> **gumshoegrant said:**
> Hello. I have read that Linux does not have the security issues like Windows and their constant security updates does. The idea of not having ports on Linux is a big difference. Is this to say that Linux would not be a good system for online bill paying and other aspects of banking? If one can still do this increasing activity in today's world with Linux than what does Linux have that allows great security that creates problems with a Window operating system?

Thanks.

I'm sure that others have covered the usual file permissions, root account, lack of viruses etc, so I'd like to mention something else: 

One of the answers is a bit different and more difficult learning curve. Windows brings about everything in front of the user, which makes a false impression that certain things are as easy as for example sharing a folder in a safe networking environment. 

Well, certain things are easy, but others require some knowledge, and I've already learned well that if something is difficult on Linux, it's not because it's "stupid", or "user unfriendly", but because it just couldn't have been made simpler. One just has to spend that hour reading the paper, otherwise one will create a monster. That policy forces a certain quality of service, which is only optional on Windows. One swears that "that goddamn NFS does not work yet", but once things are up and running, one enjoys **years** of trouble-free operation. Partially because kids will not break into non-windows networks, they lack the knowledge. 

Yes, another point is *security by obscurity*, which, contrary to a popular belief, works very well. I have a few Linux computers set up all over my campus, and people stay away from them as soon as they see "it's something strange". Of course those students who aren't afraid get good job offers ;).

---

### Post by Ahava591 on 2010-10-01
> **LMB said:**
> I'm sure that others have covered the usual file permissions, root account, lack of viruses etc, so I'd like to mention something else: 

One of the answers is a bit different and more difficult learning curve. Windows brings about everything in front of the user, which makes a false impression that certain things are as easy as for example sharing a folder in a safe networking environment. 

Well, certain things are easy, but others require some knowledge, and I've already learned well that if something is difficult on Linux, it's not because it's &quot;stupid&quot;, or &quot;user unfriendly&quot;, but because it just couldn't have been made simpler. One just has to spend that hour reading the paper, otherwise one will create a monster. That policy forces a certain quality of service, which is only optional on Windows. One swears that &quot;that goddamn NFS does not work yet&quot;, but once things are up and running, one enjoys **years** of trouble-free operation. Partially because kids will not break into non-windows networks, they lack the knowledge. 

Yes, another point is *security by obscurity*, which, contrary to a popular belief, works very well. I have a few Linux computers set up all over my campus, and people stay away from them as soon as they see &quot;it's something strange&quot;. Of course those students who aren't afraid get good job offers ;).

 Oy. Vey.

---

### Post by marin123 on 2010-10-01
> **LMB said:**
> I'm sure that others have covered the usual file permissions, root account, lack of viruses etc, so I'd like to mention something else: 

One of the answers is a bit different and more difficult learning curve. Windows brings about everything in front of the user, which makes a false impression that certain things are as easy as for example sharing a folder in a safe networking environment. 

Well, certain things are easy, but others require some knowledge, and I've already learned well that if something is difficult on Linux, it's not because it's "stupid", or "user unfriendly", but because it just couldn't have been made simpler. One just has to spend that hour reading the paper, otherwise one will create a monster. That policy forces a certain quality of service, which is only optional on Windows. One swears that "that goddamn NFS does not work yet", but once things are up and running, one enjoys **years** of trouble-free operation. Partially because kids will not break into non-windows networks, they lack the knowledge. 

Yes, another point is *security by obscurity*, which, contrary to a popular belief, works very well. I have a few Linux computers set up all over my campus, and people stay away from them as soon as they see "it's something strange". Of course those students who aren't afraid get good job offers ;).

not only students are running away from "something strange"... people on my college (electronic engineering) think of me as weirdo because i like using linux (ubuntu)... everyone is comfortable with faulty windows installations as long as they can perform their tasks...

---

### Post by rookcifer on 2010-10-01
Windows XP:

Default account is an all-powerful admin account that allows anything that comes in through the browser to do anything it wants to any system file.  A recipe for disaster and is why some studies have shown that the average XP box when first connected to the Internet is infected within about 15 minutes.

Ubuntu/Linux:

Default account has limited privileges (pretty much limited to /home with a few exceptions like /tmp).  This means anything that comes in through the browser (or other network facing apps) cannot do anything to system files.

Windows XP:

Has very few memory protections.  IIRC, there is no DEP/ASLR.  This means exploiting bugs is much easier.

Ubuntu:

Enables NX (DEP) by default and enables ASLR on many binaries.  It also has other protections like stack smashing protections and RELRO, etc.  This makes exploiting known bugs much harder.

Windows XP:

Will allow the execution of any malicious code downloaded without much afterthought.  Of course, SRP can stop this but most people have no idea about what that even is and it's not available on XP Home versions anyway.

Ubuntu:

Does not allow a newly created binary to be executed without first making it executable (thanks to the umask setting).  This means it is almost impossible for something to sneak in and execute itself.  Ubuntu has no "AutoRun" which is the bane of the Windows world.

Windows XP:

Updates only once a month.

Ubuntu:

Security updates are pushed within a couple of days (if not sooner).

These are just a few differences.  

Now, admittedly, Windows 7 is much better than XP.  Seven has DEP/ASLR and the default account, while an administrator, is protected a bit by UAC.  It also has integrity levels which help protect the browser and a few other apps (otherwise known as protected mode).  Further, creating a true user account is much easier and apps run much more smoothly than they did on XP.  On XP running from a limited account is nearly impossible. But even with Win 7's improvements, I will still take the security of Linux.  For one, with Linux, the kernel offers several advanced security features (known as MAC's) that Windows simply doesn't offer.  The Win 7 "Integrity levels" tried to provide this ability but they are very lacking since they are not really configurable and very limited in scope as to what they protect.

---

### Post by canthus13 on 2010-10-02
> **gumshoegrant said:**
> Hello. I have read that Linux does not have the security issues like Windows and their constant security updates does. The idea of not having ports on Linux is a big difference. Is this to say that Linux would not be a good system for online bill paying and other aspects of banking? If one can still do this increasing activity in today's world with Linux than what does Linux have that allows great security that creates problems with a Window operating system?

Thanks.

  
  I see a lot of people touting the security of linux, while forgetting one major thing: Regardless of the OS you choose, you have to pay attention and be suspicious when it comes to sensitive information. No matter what OS you have, it's only as good as the operator.  When it comes to online banking, it's just as easy to use a man-in-the-middle attack to steal your credentials with linux as it is with windows.  Always make sure that you are connected to the secure site SECURELY. that means https:// in front of the url.  Even then, you're still vulnerable to attack. If you know what you're looking for, you may be able to tell that it is happening by the appearance of a pop-up to confirm an SSL certificate.  Still, there are dozens of other ways they can get your information from you.
  My point is, don't be lulled into a false sense of security just because you're using linux. But don't take this as a deterrent, either. You're taking huge steps in the right direction by using a much more secure OS, but always remember that the weakest security link is YOU. Stick with software from the repositories to avoid malware, pay attention to what you're doing, and if something doesn't look right, investigate - you might be right.

--Me

---

### Post by lisati on 2010-10-02
Another thing to watch for is [phishing]("http://lisati.homelinux.com/wiki/index.php/Phishing"), a form of social engineering. Even when the scammers manage to produce a email that convinces you to click on a link that takes you to a realistic copy of your bank's web site, there are usually clues. For example, if you normally go to the website _[noparse]http://yourbank.com[/noparse]_ the link will probably be to something like _[noparse]http://somewhere.else/yourbank.com[/noparse]_ - if you're alert. you'll notice that something's wrong, regardless of which OS you're using.

---

### Post by wacky_sung on 2010-10-02
> **lisati said:**
> Another thing to watch for is [phishing]("http://lisati.homelinux.com/wiki/index.php/Phishing"), a form of social engineering. Even when the scammers manage to produce a email that convinces you to click on a link that takes you to a realistic copy of your bank's web site, there are usually clues. For example, if you normally go to the website _[noparse]http://yourbank.com[/noparse]_ the link will probably be to something like _[noparse]http://somewhere.else/yourbank.com[/noparse]_ - if you're alert. you'll notice that something's wrong, regardless of which OS you're using.

Below are a few good sites or toolbar in which can help you to determine a phishing sites.

[http://www.siteadvisor.com/sites/wordslife.com](http://www.siteadvisor.com/sites/wordslife.com)
[http://www.phishtank.com/](http://www.phishtank.com/)
[http://toolbar.netcraft.com/](http://toolbar.netcraft.com/)

---

### Post by bodhi.zazen on 2010-10-03
This is a very broad question. The question of the security of the OS , ie Linux vs Windows, is best answered by the sticky at the top of these forums.

Every OS has potential security issues and by default Ubuntu is, IMO, more secure then Windows. You may get differing opinions on that, I suggest you research the topic yourself.

"Online banking" is a different issue. You are no longer talking about simply an OS, but bring in everything from networking protocols to the server your bank is using to Phishing to Javascript to flash cookies to who knows what.

If you plan to do "internet banking" you need to consider all these things and IMO you need to understand:

1. Phishing.

2. https

3. How to secure your browser. At a minimum you  should use NoScript.

See : [How to Secure Firefox - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=671604")

Much of the advice on Internet banking is independent of the OS you run and more dependent on your understanding of Phishing and https (ie your behaviour).

---

