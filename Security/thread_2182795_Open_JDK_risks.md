---
title: "Open JDK risks"
date: 2013-10-22
forum: Security
---

### Post by MacDuff on 2013-10-22
I have been helping people make the switch to Linux.  
One of the questions I get asked, because the security risks of Java have gotten a lot of news coverage this year is "Does Java pose a risk to my files on Linux like it does to Windows files?"

My reply has been that "Open Source JDK used on Linux systems should be pretty safe because, like other open source applications, the source code gets examined by many people and anything that appears to be a risk is addressed quickly."

Of course most of the people I help have no idea what "open source" means and to them Java is Java but they take my word for it.

I am wondering if my assurances are valid or if OpenJDK poses a similar risk to Oracle Java and if I should discourage them from installing OpenJDK?

What do you other people who have more knowledge about Java have to say about this?

Thanks

---

### Post by sandyd on 2013-10-22
> **MacDuff said:**
> I have been helping people make the switch to Linux.  
One of the questions I get asked, because the security risks of Java have gotten a lot of news coverage this year is "Does Java pose a risk to my files on Linux like it does to Windows files?"

My reply has been that "Open Source JDK used on Linux systems should be pretty safe because, like other open source applications, the source code gets examined by many people and anything that appears to be a risk is addressed quickly."

Of course most of the people I help have no idea what "open source" means and to them Java is Java but they take my word for it.

I am wondering if my assurances are valid or if OpenJDK poses a similar risk to Oracle Java and if I should discourage them from installing OpenJDK?

What do you other people who have more knowledge about Java have to say about this?

Thanks

moved to security discussions

No one can really say for sure, there are some issues that (have) affected OpenJDK and Oracle Java at the same time. Take for example [http://www.ubuntu.com/usn/usn-1693-1/](http://www.ubuntu.com/usn/usn-1693-1/)

---

### Post by QIII on 2013-10-22
There is something important to understand about the relationship between OpenJDK and Oracle Java:  OpenJDK 7 is the open source reference implementation of Java -- all Java.  Any implementation that calls itself Java, including Oracle Java 7 (per Oracle itself -- Oracle ordained this relationship) must comply with OpenJDK 7 as its standard.  Oracle admits even they themselves are not there yet, but they are the ones who have set that standard.

Many people do not realize that the primary driving force behind OpenJDK 7 in terms of development effort is ... drumroll, please ... Oracle.  They actually have a large team of engineers dedicated to it.

If you ask me, the safe bet is to assume that any vulnerability in Oracle Java 7 is also present in OpenJDK 7, even though that may not always be, in fact, the case in any particular instance.  With regard to OpenJDK 7, I don't think that "open source" implies the same sense of "security" that we expect in many other open source projects.

When all the hoopla was going on last October with Oracle Java 7, Red Hat's labs found that the same sandbox-jumping vulnerability present in Oracle Java 7 was present in OpenJDK 7.

This isn't a Linux thing.  Windows users were vulnerable, too.  In fact, one of last year's exploits determined if the JVM was running in Windows, Apple or Linux and behaved appropriately in each OS to exploit the sandbox jump.

I think the whole JVM ecosystem needs to be reworked from the ground up.

Edit:

Instead of the "open source" argument in this case, I think the better case is made by saying that apparmor can provide a deeper level of protection in Linux.

---

### Post by MacDuff on 2013-10-22
Thanks QIII

I am more knowledgeable on the subject of Java now, and really appreciate your point about apparmor.

So what is your opinion about the risks of someone using a 'buntu to do on-line banking and similar tasks if they have OpenJDK installed (or any other web based Java apps)?

Mac

---

### Post by QIII on 2013-10-22
Frankly, I'm surprised banks still use anything that depends on the Java browser plugins, either Oracle or IcedTea.

I think it is very risky, but it's a fact of life.

---

### Post by MacDuff on 2013-10-23
I too would be surprised if any financial institution would use Java applications but I think what the user was asking, and I did not quote him completely, was "Does having OpenJDK installed on my computer pose any risk to me if I do connect to a bank to do on-line financial transactions?"  This connection would presumably be a secure connection provided by the bank.  

Is it probable that someone using OpenJDK might be exposed to a bad guy/girl using the flaws in Java to remotely implant a key logger or remote desktop viewer or some other tool to obtain access to the users confidential information?

I have not considered this before.   I guess its true that teaching the pupil teaches the teacher.

Mac

---

### Post by CharlesA on 2013-10-23
The applet the bank uses would need to be modified to act as anything other than what it would normally do, no?

---

### Post by MacDuff on 2013-10-23
Thanks for the help folks.    I will assure the newbies that they have nothing to fear from installing OpenJDK on their 'buntu installations, but for reasons other than what I gave them when they first asked.

This is my 10th installation for people new to Linux and all but one have stayed with it,  though not always with the distro that I first recommended/installed.   That is the beauty of freedom.  In all those installations I have only encountered one Windows application that could not be replaced or satisfactorily substituted for on Linux.   We have come a long way in the past 6 years.

---

### Post by kurt18947 on 2013-10-23
Does the bank require Java?  If not, it's pretty easy to disable the browser plugin except when it's needed.  The only time we have needed java is for a chat app.  Personally, I prefer to have a small partition with an install used ONLY for transactions requiring security.  No Flash, no Java, no facebook, etc. etc.

---

### Post by 1clue on 2013-10-23
Speaking as somebody who writes financial software for fortune 500 companies, yes financial software uses Java.  Oracle Financials makes heavy use of it.  Oracle database has Java components.  Lots of other big financial software from other companies uses it.

Be that as it may, most of that Java is on a server somewhere, not on your browser.  IMO Java applets are a bad idea.  Java on a server can be properly protected.

Java is much more pervasive than a lot of people think.  If you own a BluRay player, then you are using Java.  Probably if you have a smart TV or set-top-box, or a smart dvd or smart anything else, it has Java.

Security:  Some of the issues that come up are implementation-specific.  Other issues are problems with the specification.  As with any security vulnerability you need to look at what it is before making judgments.

---

### Post by MacDuff on 2013-10-24
So what I get from this discussion is that it matters not the source of Java (OpenJKD, or download from Java.com)  Once installed, it still poses a threat to a local user's security and therefore should not be installed.   It may be a very long time before Java will be safe to install..... perhaps never because the problems with it are so large that they may never be addressed.

I had been suggesting to other people that Java be turned off and on as required when Internet Browsing but Java still exists in the system even though the Internet interface is turned off.   

What about other Java applications that reside on the computer but do not apparently need an Internet connection?  

The original question about Java came to me from a new user who discovered a Java application called SuperbCalc.  The user does book keeping and apparently would like to use SuperbCalc on his computer because it is a financial "tape" type calculator that records scrolling strings of financial calculations that simplify error checking.  Does this type of application pose a risk?

I am way out of my depth here.

Mac

---

### Post by Paddy Landau on 2013-10-24
> **MacDuff said:**
> … a financial "tape" type calculator that records scrolling strings of financial calculations…
I don't know exactly what your friend wants, but have a look at Speed Crunch (available in the Ubuntu Software Centre).

---

### Post by 1clue on 2013-10-24
When you ask questions on a forum, particularly on a forum which really has nothing to do with the software in question, you get a whole lot of possibly strong but mostly inexpert opinions.

As I mentioned before, Java is used by fortune 500 companies for financial transactions that make your personal checking account look like nothing.  If they thought it wasn't secure enough for this task -- or more accurately, if they thought it couldn't be made to be secure enough when used in conjunction with other measures -- then they wouldn't use it.

Obviously there ARE risks.  Obviously a whole lot of people on this forum are just guys who installed one of the easiest to use distros out there, and that's about the only expertise they have.  Why don't you do some research on the vulnerabilities on your own?  Go to CERT or go to the web site for the particular flavor of Java you're thinking of using.  Either way, you can find "java security vulnerabilities" and get a real list.

---

### Post by MacDuff on 2013-10-24
Paddy: I had suggested Speedcrunch and he tried it but found SuperbCalc and asked about it.  

1clue:  Your point is taken. But understand that I am cutting corners because I am just an unpaid volunteer who is trying to help out potential new Linux users.  Yes, I should do some serious research but there is a limit to the amount of time I can spend helping others.  I though I might get a quick answer through this forum that would save me time.

---

### Post by QIII on 2013-10-24
One of the guys here talking about Java security is a developer and member of the ODN, by the way.  So there are some people who have some expertise as well as strong opinions.  In fact, that expertise may lead to strong opinions.  I develop Java apps for several clients. 

A desktop or enterprise Java application used by a Fortune 500 company is one matter.  Just having Java on the machine and using Java apps is not, in and of itself, a security risk.  Server side Java is extremely useful.  Desktop Java apps are great.

But exposure to the web via the browser plugin most certainly is a security risk as has been demonstrated over and over again.  Red Hat broadcast a message last fall recommending to all of its enterprise users to stop using the browser plugin at all -- remove it if need be -- when the series of no fewer than three escape vulnerabilities were being exploited within three weeks.  I doubt Red Hat was speaking from a dearth of expertise.  And few security experts even now would say that Oracle is anywhere close to having a handle on all the vulnerabilities.

Using the Java browser plugin on the web is risky.  (See post #5 -- I specifically said browser plugin.)  That is a stone cold fact.

Banks are fine in using Java in the enterprise.  A home user is fine using a Java desktop app.  But I think banks, in particular, are terribly irresponsible if they are using applets on their websites and I think uses should be exceptionally wary of using the browser plugin and use something to block java applets unless explicitly allowed by the user -- and that only when need be.

---

### Post by 1clue on 2013-10-24
Didn't mean to ruffle feathers, just pointing out that the average guy on this forum with an opinion about Java is probably spouting hearsay.  I develop on the JVM writing that financial software, so obviously I know that not everybody here is uninformed.

We both agree on the plugin/applet being a bad idea, but with the OP asking about security for apps and other non-applet things, I thought that looking at the actual vulnerabilities might give him an idea what's considered safe and what's not.

---

### Post by MacDuff on 2013-10-24
Good discussion and though there was no definitive answer, it has provided some ideas to pass on to the individual who is concerned.

Thank you all for your replies. 

Mac

---

