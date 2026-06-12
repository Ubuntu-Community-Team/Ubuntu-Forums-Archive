---
title: "OpenJDK Java 7 Runtime - safe for banking?"
date: 2012-07-13
forum: Security
---

### Post by Kols on 2012-07-13
Hey!

I hope this is the correct forum - let me know if it isn't.


I need java for my internet bank, so I just installed OpenJDK.

In windows, I've always used Sun, cause that's the easiest choise, I suppose. As I haven't been robbed yet, I'm presuming that Sun is a safe java-applet when using bank-services on the internet.

Now I'm wondering - is OpenJDK as safe, or safer, to use with banking? 
I'm relatively new to Linux, so opensource is still a bit blurry to me; therefore I'm prone to thinking "opensource must mean that it's easier to extract bank-information, and I don't know if I can trust someone other than Sun"

Now, I would appreciate if someone could prove me wrong=P

---

### Post by ottosykora on 2012-07-13
well I would rather see it so that the java you have installed, it is somthing like an other oprearting system. It is kind of virtual machine. It self it does not do anythning, but sit here and wait for some program written for this machine.

So the work is done by the program written for the java virtual machine. This is then the applet which you will download from the bank website etc.

How this applet is written and what quality we dont know, but I would assume that a bank did quite a degree of consulting on that subject before releasing an applet.
Those applet do often all the cryptography jobs, they create the session keys, sign the messages with the private key, encrypt all to the bank key etc. 

As every system, the java virtual machine can be attacked too, but in this case the integrity of the applet supplied by the bank seems to me much more important.

---

### Post by Hungry Man on 2012-07-13
> 
I'm relatively new to Linux, so opensource is still a bit blurry to me; therefore I'm prone to thinking "opensource must mean that it's easier to extract bank-information, and I don't know if I can trust someone other than Sun"
Well first off the JRE is no longer handled by Sun it's handled by Oracle. You can't trust Oracle for **** because they're one of the worst tech companies that currently exists and I'll resist ranting about that.

Open source vs closed source is a subject that gets repeated a lot. My stance is that open source is always potentially more secure than closed source. I won't elaborate, it'll end up devolving into an ironically really complicated discussion.

I think that the current Oracle JRE is actually based on OpenJDK 7. So they're both pretty much as broken as the other most likely.

If you're using Firefox there's an apparmor profile already built for the plugin. You can enable it with:

sudo aa-enforce /etc/apparmor.d/**java**

and if that doesn't work replace 'java' with 'jdk' or whatever it is.

That should help keep you much safer. If you're using another browser you'll need to generate the profile yourself.

Pretty sure Java 7 still doesn't support TLS 1.1+ either.

Which bank is this out of curiosity?

---

### Post by CharlesA on 2012-07-13
> **Hungry Man said:**
> 
Which bank is this out of curiosity?

I am curious as well. None of the banks I have used have needed Java to access your account. Some have used flash for their homepage, but I don't think any of them have actually used Java.

---

### Post by Hungry Man on 2012-07-13
I've heard of it before. Honestly I'd just like to see it and then email them explaining why they need to not do that.

---

### Post by QIII on 2012-07-13
Yes, some banks do use the Java plugin.

OpenJDK 7 is the open source reference implementation of Oracle Java 7.  If one has security issues, the other is likely to as well.  They both get updated at the same time as issues are discovered.  In fact, yesterday I read about a cross-platform Social Engineering exploit that targets Java.

Despite the fact that OpenJDK 7 is the reference implementation of Oracle Java 7, a good part of the world does not recognize it as "Java".  If the bank's website developers do not understand the relationship and only look for the Oracle Java plugin, you'll find that the applets won't work.

(If you install OpenJDK 7 and go to Oracle's site to check to see if you have Java, Oracle recognizes it, of course!)

If OpenJDK 7's plugin, IcedTea, is not recognized by the bank's website, you will have to install Oracle Java 7 (see the wiki in my signature and look for "Using webupd8.org's strikingly simple method").

Secure is only good until someone finds an exploit.  It's the risk we take.  But you should use the apparmor profile.

---

### Post by ottosykora on 2012-07-15
come on, I use at least two banks who need it myself and I am not someone having 20 bank accounts (as I hardly can keep two above minus)

There is system of identification with simple 509 PKI, but the private key is on a chip card. The process of verification and acces to the card is done by java applet as well as the encryption process, generation of the session key etc.
This is by the way the standard way of internet bank access in countries like Czech Republic.

The other application is for swiss banking.

There are apparently banks in Italy who use similar procedures as well.

So there will many around as this is a way how to maintain only one software for different operating systems.

And yes, so far I did not manage to operate either of them under openJDK, so far only under sun/oracle java.

---

### Post by ottosykora on 2012-07-15
> **Hungry Man said:**
> I've heard of it before. Honestly I'd just like to see it and then email them explaining why they need to not do that.

simple: it is all using an applet which is downloaded at the time of operation and thus little bit more under control of the bank then if there is a software installed on the clients PC.
Software installed on clients PC is considered as weakest point in the whole authetication and is therefore avoided.

The java applet is just sent to client PC run inside the java VM and does all the job and is deleted after.

It is also easy to maintain only one software for different OS.

In some countries the procedure is standardized by the legal requirements for internet transactions.


You can go and ask one of the cert authorities why they do it this way: [http://www.ica.cz/English](http://www.ica.cz/English)
or one of their customers: [http://www.csob.cz/en/Stranky/default.aspx](http://www.csob.cz/en/Stranky/default.aspx)

---

### Post by Hungry Man on 2012-07-15
There are plenty of benefits for programming in JAva like crossplatform code. That doesn't really excuse it. Think of BEAST. Think of MD4 only just being depreciated.

---

### Post by ottosykora on 2012-07-16
well yes, but what alternative has a bank ?

Write windows software which the user has to install on his computer? Probably not good idea.
Use just identification with something like RSA timer? OK, but then for the communication just the standard encryption mechanism provided by the browser? Hmm, possible, but not legal in many countries.

In number of countries I know, the legal requirement is to use x.509 PKI . How to implement that so to keep the secret key not on the PC and same time use it and carry out encryption process without installing software on client computer?

---

### Post by Hungry Man on 2012-07-16
I don't see why anything needs to be installed at all. What exactly are they doing on this site other than banking? Simply allow an HTTPS connection and that's it - the browser handles all of this. As for PKI that's really up to the bank in terms of getting their private key certification for the public key to meet those standards.

---

### Post by ottosykora on 2012-07-16
this is the problem. One can relay on the ssl, but this will not solve the problem of 509 PKI handling. And in many countries I know, the authentication and encryption has be done with full 509 implementation doe to legal directives.
Yes, the operating system like windows or other will handle that, but this is not wanted, as this is bigger risk.
You have to provide software, which can make use of key pair on external media not readable otherwise then by software run at the time of the access. 

This is rather standard procedure, number of specialized companies produce software for such smart card access and operations using the keys stored on not accessible partition on the smart card.

So it is not about the bank getting cert on their key, but it is about each client has a key pair on non accessible media, and this media has to be given a crypto task and perform that task and commuicate then with the outside world.
This is the only legal way in number of countries as they will not accept any sort of 'browser will do' ssl as security feature for bank transactions.
This is mainly because the browser is installed as whole on the clients PC and this is basically considered as unusable.

In fact, the initial communication uses ssl, but then the java applet is downlaoded via this ssl, it does some basic intergity check of the java VM and the software to talk to the smart card is then executed and will do the rest of the communication and crypto tasks.

The java applet is deleted at the and of the session.

There also highly protected secure storage servers, in number of countries which use java applets for the whole cryptography process as this is at the end much more secure then any sort of ssl transmission. Here is however more the point, that the data must not be decrypted at the other and of the line which is not the case in a bank traffic.
 

In fact I do not know any bank around which will relay transactions on ssl as browser function.

Some banks do use the ssl for the traffic, but will use some second path for authetication number of times during the session. They will definitely not relay on authetication message created by the operating system crypto functions.

---

### Post by Hungry Man on 2012-07-16
I've never had City bank try to use Java for any transaction.

---

### Post by ottosykora on 2012-07-16
> **Hungry Man said:**
> I've never had City bank try to use Java for any transaction.

yes, but then you have second communication path, independent on browser, computer and your current internet connection for initial authetication and exchange of basic session key parameters.
Often application via certain cooperating mobile phone providers is used, RSA timer or similar not internet browser based communication needs to be established.

Any procedure using just browser would be highly risky and simply not allowed by the authorities in many countries. Simple browser based authentication was dropped sometimes in the 90ties.

I have one way of using such basic communication for transactions with a bank, but it will allow me only transactions of maximum 100$ and 500$ per month maximal.
The smart card java based system will allow me transactions of 100000$ each up to the full banking limit per month.
From that you can see how the security is probably estimated by the bank and software companies behind the system.

---

### Post by Outtascope on 2012-08-13
Ok, so you are a Java hater, I get it.  But at least have the correct information if you are going to go off about it.

> **Hungry Man said:**
> Open source vs closed source is a subject that gets repeated a lot. My stance is that open source is always potentially more secure than closed source. I won't elaborate, it'll end up devolving into an ironically really complicated discussion.

That could be true if Ubuntu actually kept up to date.  Except that OpenJDK 7 on Ubuntu is currently at Update 3, while Oracle's is at Update 5, released 2 months ago, with 14 security fixes in it.  (of course Ubuntu/Debian has taken to making a bunch of software dependent on OpenJDK rather than make it a recommend, thus forcing users to "roll their own" for these packages, or run a less secure version of Java)



> **Hungry Man said:**
> Pretty sure Java 7 still doesn't support TLS 1.1+ either.

That is ENTIRELY incorrect.   Java 7 currently supports both TLS 1.1 and 1.2, neither of which are supported by Firefox yet despite ancient bugs for them.

---

### Post by Hungry Man on 2012-08-13
I'm not a 'Java' hater. I like the language, I like that it's portable, and I like OOP. In general I dislike the implementation and I think most users shouldn't have it installed as it's one of the most commonly exploited pieces of software.

> That could be true if Ubuntu actually kept up to date. Except that OpenJDK 7 on Ubuntu is currently at Update 3, while Oracle's is at Update 5, released 2 months ago, with 14 security fixes in it. (of course Ubuntu/Debian has taken to making a bunch of software dependent on OpenJDK rather than make it a recommend, thus forcing users to "roll their own" for these packages, or run a less secure version of Java)

Not really what I was talking about but yes, it is behind. This is unfortunately the case with quite a few programs in the software center.

> That is ENTIRELY incorrect. Java 7 currently supports both TLS 1.1 and 1.2, neither of which are supported by Firefox yet despite ancient bugs for them.

Good to know. At least they've done something. I know 7 also depreciated some weaker hash functions as well.

---

### Post by Kols on 2012-12-02
OP here, again! (still using Lubuntu)

Thanks for all the answers. As far as I can read out of it all, OpenJDK seems like a safe enough way to go. 

Now for another question; how to verify that I have the latest version, and how do I, if necessary, update it?

When I finally managed to install OpenJDK, I wasn't skilled in Linux at all - at least now, I've learned a _little_ more. Therefore, I'm not really sure what I did back then. It seems like I have both the version 6 and 7 installed. If someone could explain possible reasons why this is, I'd be glad=P

Now, for the pressing issue. I remember a while back, my bank encouraged all their users to update their java, as there were some new security threats around. As I can't remember how I installed java, I'm not sure if it ever updates automatically through "sudo apt-get update". At least, when I do a "sudo apt-get install openjdk-7-jre" from OpenJDK's pages, my terminal outputs that I already have the newest version. 

Do I?

Should I switch to Oracle instead?=P

Best regards

Ole-Jørgen

---

### Post by CharlesA on 2012-12-02
As long as are you are doing regular updates, you should have the latest version of OpenJDK.

---

### Post by MontrealCorp on 2013-02-13
> **QIII said:**
> Yes, some banks do use the Java plugin.

OpenJDK 7 is the open source reference implementation of Oracle Java 7.  If one has security issues, the other is likely to as well.  They both get updated at the same time as issues are discovered.  In fact, yesterday I read about a cross-platform Social Engineering exploit that targets Java.

Despite the fact that OpenJDK 7 is the reference implementation of Oracle Java 7, a good part of the world does not recognize it as "Java".  If the bank's website developers do not understand the relationship and only look for the Oracle Java plugin, you'll find that the applets won't work.

(If you install OpenJDK 7 and go to Oracle's site to check to see if you have Java, Oracle recognizes it, of course!)

If OpenJDK 7's plugin, IcedTea, is not recognized by the bank's website, you will have to install Oracle Java 7 (see the wiki in my signature and look for "Using webupd8.org's strikingly simple method").

Secure is only good until someone finds an exploit.  It's the risk we take. ** But you should use the apparmor profile**.


i try what humgerman said for this since i use firefox , just isnt working :(

where can i find info on how to use this ?

ty



actually nevermind, ill try find other solution

---

### Post by Ms. Daisy on 2013-02-14
This thread is only six months old but A LOT has changed since then.  If you have the java plugin in your browsers, keep them disabled until you need to do banking. Then disable them as soon as you're done.

If you have both versions, remove 6. I'm on Windows right now so I can't test it, but I believe the code is
```
sudo apt-get remove --purge openjdk-6* && sudo apt-get remove --purge icedtea-6*
```
Then you can make sure you have openjdk 7 by typing 
```
dpkg -l | grep openjdk*
```

---

