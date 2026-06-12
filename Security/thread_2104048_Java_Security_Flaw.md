---
title: "Java Security Flaw"
date: 2013-01-11
forum: Security
---

### Post by MooPi on 2013-01-11
Considering the latest Java exploit, does it affect openjdk-6-jre ?
I suspect not but i'm still concerned enough to enquire.

---

### Post by Hungry Man on 2013-01-11
Maybe not 6, but almost certainly 7.

---

### Post by MoebusNet on 2013-01-11
I just read about Java's security flaws at:

[http://www.mercurynews.com/business/ci_22357009/?source=inthenews](http://www.mercurynews.com/business/ci_22357009/?source=inthenews)

I have disabled the IcedTea-Web Plugin 1.2-2ubuntu1.3 in Firefox until I get more details. Is this going to be enough until Ubuntu addresses this situation?

---

### Post by AllenGG on 2013-01-11
Looking here: [http://krebsonsecurity.com/2012/08/java-exploit-leveraged-two-flaws/](http://krebsonsecurity.com/2012/08/java-exploit-leveraged-two-flaws/)

Sounds like Ubuntu "10" could be at risk.  NOTE, I did discover 3 viruses, via Clamscan, nestled in a TMP cache. Caused no problems. 
Now, the questions is: can we stop the intrusions ?+++More, Jan 16th+
[B][SIZE=3]
Disabled Java and all the parts in Firefox.
Tools>Add-ons then "search" > "Java" 
then "disable" all that are enabled.[/SIZE][/B]

---

### Post by Hungry Man on 2013-01-11
If you disable the plugin the exploit won't work.

If you enable it on an exploit page you will likely be exploited, regardless of whether it's OpenJDK or Oracle's JDK. This may only effect versions 7.X.

If you would like advanced protection against Java exploits I highly suggest you use an Apparmor profile. I've written one here. Feel free to customize it to your liking.

[http://www.insanitybit.com/2012/08/27/apparmor-and-java/](http://www.insanitybit.com/2012/08/27/apparmor-and-java/)

---

### Post by pqwoerituytrueiwoq on 2013-01-11
> In addition, Mountain  View-based Mozilla said in a blog post that it has begun blocking Java  on its Firefox browser unless someone clicks on a feature to activate  the software. The click-to-play feature "allows users to enable the Java  plugin on a per-site basis if they absolutely need the Java plugin for  the site," the blog said.
finally, that was long overdue

i never install java/icedtea cause there are holes every time you turn around

---

### Post by cariboo on 2013-01-12
Merged two similar threads.

---

### Post by samiux on 2013-01-12
First of all, we should understand how the vulnerability to be exploited.  

This [video]("http://www.youtube.com/watch?v=JRGoIXbw9yA") will show you that various browsers and various operating systems, including Linux will be affected.

The captioned video is just an example but the malicious hackers will not simply do this.  They will hide the suspicious prompts as far as possible.  However, you will know the result of the exploit.


**Edit :** [CVE-2013-0422]("http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2013-0422")

Samiux

---

### Post by MooPi on 2013-01-12
Looks like openjdk-6-jre is not listed as versions affected according to the National Vulnerability Database. One big sigh of relief !

---

### Post by samiux on 2013-01-13
> **MooPi said:**
> Looks like openjdk-6-jre is not listed as versions affected according to the National Vulnerability Database. One big sigh of relief !

According to the information at the [wiki]("http://en.wikipedia.org/wiki/OpenJDK") and my knowledge, OpenJDK is based on Sun/Oracle Java JDK source code.  In addition to the information at [here]("http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2013-0422"), the version of Oracle Java or OpenJDK 1.7 in Java 7 Update 10 or later may be also in question.  Even OpenJDK 1.7.0.50 in Ubuntu 12.10 may be fell into the gap too.

In my opinion, Java (Oracle and open source) is not safe at the moment.

Samiux

---

### Post by Penny N. Nickels on 2013-01-13
I currently have the Java 7 Update 10. Would taking a step backwards & installing Java 6 Update (I forgot the number) allow me to use Java again? I currently have the Java  disabled in FF. 

():P I've not posted here in a while, but I have been here on occasion, searching for answers.)

(I have Ubuntu 12.10 LTS)

---

### Post by Pjotr123 on 2013-01-13
> **samiux said:**
> 
In my opinion, Java (Oracle and open source) is not safe at the moment.

Correct. I always advise to disable the Java or IcedTea plugin in the browser by default. Only enable it for the duration that you really need it, on some trusted website.

The fix may arrive shortly:
[http://www.reuters.com/article/2013/01/13/us-usa-java-security-idUSBRE90B0EX20130113](http://www.reuters.com/article/2013/01/13/us-usa-java-security-idUSBRE90B0EX20130113)

But even when we have this fix, Java will remain a security concern. Has been so for many years... :-(

---

### Post by samiux on 2013-01-13
According to the latest [release note]("http://www.oracle.com/technetwork/java/javase/7u11-relnotes-1896856.html") of Java, the bug does not really fixed yet.  It only increase the security level from medium to high.

I think there may be a way to bypass this setting.

By the way, the Firefox seems to disabled the Java plugin automatically.  However, the other browsers do not.

Samiux

---

### Post by haqking on 2013-01-13
All this worry about plugins and the like.

Browse the web the RMS way

> **Re: Real men don't attack straw men**

 [Posted December 19, 2007 by corbet]                                

 
   **From**:     	      Richard Stallman <rms-AT-gnu.org> **To**:     	      "Edd Barrett" <vext01-AT-gmail.com> **Subject**:     	      Re: Real men don't attack straw men **Date**:     	      Sat, 15 Dec 2007 16:37:06 -0500 **Message-ID**:     	      <E1J3eh0-000571-LM@fencepost.gnu.org> **Cc**:     	      misc-AT-openbsd.org **Archive-link**:     	      [Article]("http://article.gmane.org/gmane.os.openbsd.misc/134979"),         [Thread]("http://thread.gmane.org/gmane.os.openbsd.misc/134979")          For personal reasons, I do not browse the web from my computer.  (I also have not net connection much of the time.)  To look at page I send mail to a demon which runs wget and mails the page back to me. It is very efficient use of my time, but it is slow in real time.    

;-)

---

### Post by samiux on 2013-01-13
> **haqking said:**
> All this worry about plugins and the like.

Browse the web the RMS way



;-)

We cannot fallback to the year of 2007.  

Today, almost every website is interactive.  The use of Java applet is common for modern websites.  We, users, cannot control the use of Java applet or not.  

When we need the services that provided by the websites and they implemented the Java applet, we should install the Java JRE/JDK accordingly.  There is no other alternative choice.

Samiux

---

### Post by haqking on 2013-01-13
> **samiux said:**
> We cannot fallback to the year of 2007.  

Today, almost every website is interactive.  The use of Java applet is common for modern websites.  We, users, cannot control the use of Java applet or not.  

When we need the services that provided by the websites and they implemented the Java applet, we should install the Java JRE/JDK accordingly.  There is no other alternative choice.

Samiux

it was a joke.

---

### Post by pqwoerituytrueiwoq on 2013-01-13
> **samiux said:**
> We cannot fallback to the year of 2007.  

Today, almost every website is interactive.  The use of Java applet is common for modern websites.  We, users, cannot control the use of Java applet or not.  

When we need the services that provided by the websites and they implemented the Java applet, we should install the Java JRE/JDK accordingly.  There is no other alternative choice.

Samiux
name 3 sites that use java, java testing (eg, java * test) sites do not count (javascript != java)
i think java needs to die more than flash does, it is like every few weeks there is a big security issue with java and the last one that happened with flash only affected IE anyway, and that was quite a while ago

---

### Post by cariboo on 2013-01-13
> **haqking said:**
> All this worry about plugins and the like.

Browse the web the RMS way



;-)

Now we know why it took him more than 3 months to complain about the shopping lens. :-D

---

### Post by QIII on 2013-01-13
Is it a good idea to use Java 6?

Is it a good idea to use smokeless tobacco rather than smoking cigarettes?  Java 6 has its own well-known vulnerabilities and is due to reach end of life shortly.

Will OpenJDK 7 provide you any better safety?

In short, no.

Most people do not understand the relationship between OpenJDK 7 and Oracle Java.  Oracle is a prime mover in the development of OpenJDK 7.  

Why?  Because Oracle has made OpenJDK 7 the open source reference implementation for Java.  What that means is that all implementations of Java, including Oracle Java 7, must comply with the standards set in OpenJDK 7.  Oracle, however, sheepishly admits that they aren't there "yet".

What this means is that you can bet that any vulnerability in Oracle Java 7 is also present in OpenJDK 7.  Furthermore, updates to OpenJDK 7 take longer to be published than Oracle Java 7 (and that is dog slow already.)

I think this is the fourth security flaw in Java since October, 2012, where the browser plugin opens the door to nefarious agents who want to have their way with your computer.  Oracle is playing Whack-A-Mole with security.  They no sooner fix one thing than another hole is exposed.

---

### Post by Hungry Man on 2013-01-13
Java is now click to play by default, as of the last patch. You can expect attackers to start looking for new programs to attack in the next year or so.

---

### Post by drawkcab on 2013-01-13
> **Hungry Man said:**
> Java is now click to play by default, as of the last patch. You can expect attackers to start looking for new programs to attack in the next year or so.

In Firefox thanks to Mozilla.  If you're running some other browser, then, as I understand it, look out!

A patch has been issued but the analysts are already saying that it overlooks several key flaws.

---

### Post by Hungry Man on 2013-01-14
To clarify, both Chrome and Firefox have Java as click to play. But now, as of this last patch, Java won't run unsigned code at all without user interaction.

---

### Post by samiux on 2013-01-14
> **pqwoerituytrueiwoq said:**
> name 3 sites that use java, java testing (eg, java * test) sites do not count (javascript != java)
i think java needs to die more than flash does, it is like every few weeks there is a big security issue with java and the last one that happened with flash only affected IE anyway, and that was quite a while ago

Interesting indeed.  Maybe Java applet is not common in your country but it is not indicated that it is not common in other countries.  For example, it is very common in my country.

Therefore, we, users, cannot take control of it.

Samiux

---

### Post by samiux on 2013-01-14
> **Hungry Man said:**
> To clarify, both Chrome and Firefox have Java as click to play. But now, as of this last patch, Java won't run unsigned code at all without user interaction.

With reference to this [video]("http://http://www.youtube.com/watch?v=JRGoIXbw9yA"), even the users ignore/reject to run the applet, the box maybe compromised.  This is just an example.

I tested the Firefox 18.0 with Java JRE 1.7 Update 10 on Windows 7 and Ubuntu 12.10, the Firefox disabled the Java plugin automatically.  The exploit cannot be done.  However, IE does run the exploit successuflly.

Samiux

---

### Post by samiux on 2013-01-14
Tested Java JRE/JDK 7 Update 11 today.  

Users will be asked if they accepted an unsigned or self-signed applet to run or not.  If users accpeted to run the malicious applet, the users' boxes can be compromised.  It is much similar to Microsoft Windows UAC settings.  In addition, the available (known) exploits are blocked by this update upon my limited tests.

Furthermore, the fix is for the users who installed the Java JRE/JDK 7 Update 11 only.  How about the Java JRE/JDK 6, 5.0 and 1.4.2 users?  What if their old systems (or application systems) do support JRE/JDK 7?  What if users must use older version of JRE/JDK?

Samiux

---

### Post by Cavsfan on 2013-01-14
If you don't mind typing commands or copying and pasting into a terminal. Check the links in my signature.
They will provide Java 7 version 11 for Firefox. I don't program so I don't use the JDK nor do I have it installed.
But, I am pretty sure this version is safe. It was just released yesterday. 
The instructions for installing in the [COLOR=Blue]Manually update java[/COLOR] link have been updated to 11 so you'll just have to copy and paste.
This method also removes the IcedTea Java-plug-in.

I finished updating Lucid, Precise, Quantal and Raring without any issue and fairly quickly but, I have done this many times.

---

### Post by youngunix on 2013-01-14
I see that a lot people talking about openjdk (linux) and java 7 being exploited and such. I check my ubuntu 12.04 and it seems I'm running [COLOR=Red]**Oracle Java 8! **[COLOR=Black]Now that's weird since no one has mentioned it anywhere, should I worry?[/COLOR][/COLOR]

---

### Post by Hungry Man on 2013-01-14
Java 8 is currently in beta, and therefor is likely not being patched the way stable versions are. I would suggest you move to 7, or secure Java in other ways.

---

### Post by youngunix on 2013-01-14
> **Hungry Man said:**
> Java 8 is currently in beta, and therefor is likely not being patched the way stable versions are. I would suggest you move to 7, or secure Java in other ways.

thanks for the reply, I just purged it from the system to avoid any drive by. I recommend this approach for now till java get patched.

---

### Post by Ms. Daisy on 2013-01-15
> **cariboo907 said:**
> Now we know why it took him more than 3 months to complain about the shopping lens. :-D

LOL

I wouldn't assume that Java 6 or openjdk are safe from these exploits. Treat all versions/ flavors of Java the same. Unplug them from the browser except where absolutely necessary.

---

### Post by Cavsfan on 2013-01-15
I just found this article that says version 7 update 11's security patch fixes nothing.

[http://betanews.com/2013/01/14/java-7-update-11-security-patch-fixes-nothing/](http://betanews.com/2013/01/14/java-7-update-11-security-patch-fixes-nothing/)

They suggest you disable it.

---

### Post by samiux on 2013-01-15
> **Cavsfan said:**
> I just found this article that says version 7 update 11's security patch fixes nothing.

[http://betanews.com/2013/01/14/java-7-update-11-security-patch-fixes-nothing/](http://betanews.com/2013/01/14/java-7-update-11-security-patch-fixes-nothing/)

They suggest you disable it.

Don't worry.  I confirmed the captioned website said was incorrect.  I have tested Windows 7 with IE 9 and confirmed that Java 7 Update 11 does fix the current problem (known and available exploit).

However, it does not said that the 6.0, 5.0 and 1.4.2 are fixed without this update.

Samiux

---

### Post by Cavsfan on 2013-01-15
> **samiux said:**
> Don't worry.  I confirmed the captioned website said was incorrect.  I have tested Windows 7 with IE 9 and confirmed that Java 7 Update 11 does fix the current problem (known and available exploit).

However, it does not said that the 6.0, 5.0 and 1.4.2 are fixed without this update.

Samiux

Good to know. On my windows 7 install I checked and it had update 7 version 9 both 32 bit and 64 bit.
It was more of a hassle on windows to get 7.11 installed than it was on Ubuntu. 

I guess we will see that popup whenever java is accessed and we can either deny or allow.

---

### Post by samiux on 2013-01-15
> **Cavsfan said:**
> Good to know. On my windows 7 install I checked and it had update 7 version 9 both 32 bit and 64 bit.
It was more of a hassle on windows to get 7.11 installed than it was on Ubuntu. 

I guess we will see that popup whenever java is accessed and we can either deny or allow.

Yes, Java 7 Update 11 is set the security level from medium to high.  unsigned and self-signed applets are asked for confirmation to run or not.  It is much like Microsoft Windows' UAC.  They shift the responsiblity to the users this way, too sad.

Samiux

---

### Post by oblidor on 2013-01-15
> **haqking said:**
> All this worry about plugins and the like.

Browse the web the RMS way



;-)

Yea, well it doesn't pay the bills though.

---

### Post by RoadRunnr on 2013-01-16
7u11 was released 3 days ago and Ubuntu is still shipping 7u9.

Does that mean that Ubuntu doesn't care about the safety of its user base?

---

### Post by samiux on 2013-01-16
> **RoadRunnr said:**
> 7u11 was released 3 days ago and Ubuntu is still shipping 7u9.

Does that mean that Ubuntu doesn't care about the safety of its user base?

May be the Official think that Ubuntu comes with Firefox by default and the latest version of Firefox (version 18.0) will disable the vulnerability Java plugin by default.  They may think that the users of Ubuntu are not in risk at all, my opinion only.

Samiux

---

### Post by Hungry Man on 2013-01-16
No, that's just the downside to Apt. You get slow patching all the time, it's a terrible side effect of a potentially great system.

That said, use the WebUpd8 PPA for Oracle's Java. OpenJDK patches slower.

And update 11 is vulnerable to a new exploit being sold, should already be in the wild, and will be distributed widely soon.

---

### Post by Cavsfan on 2013-01-16
> **RoadRunnr said:**
> 7u11 was released 3 days ago and Ubuntu is still shipping 7u9.

Does that mean that Ubuntu doesn't care about the safety of its user base?

[[COLOR=blue]_Install Java version 7 update 11 here._[/COLOR]]("https://sites.google.com/site/easylinuxtipsproject/java")

---

### Post by QIII on 2013-01-16
Oracle will no sooner fix a known vulnerability than another will be exposed.  Whack-a-Mole.  Soon it will be more than one mole at a time.

---

### Post by Cavsfan on 2013-01-16
I updated the java on my Windows 7 install to 7.11 both 32 bit and 64 bit yesterday. Today I checked for a later version of the Nvidia Driver.
There was a way to check the one on my system to what is available. It was a java applet and asked permission. Knowing I'm going to trust Nvidia pretty much I allowed it.

But, I did appreciate the popup.

I had a 306.xx version installed and version 310.90 was available. I downloaded it.
But, on windows, which is susceptible to viruses, I always scan the downloaded file with my antivirus program before installing it.

That is at least one good thing I see out of 7.11: it pops up a box and directly asks you if you want to proceed.

---

### Post by QIII on 2013-01-16
> **RoadRunnr said:**
> 7u11 was released 3 days ago and Ubuntu is still shipping 7u9.

Does that mean that Ubuntu doesn't care about the safety of its user base?

No.  It means that just like Windows the distribution's features are frozen and the iso is static, so you have to do updates as soon as it is installed.

---

### Post by Cavsfan on 2013-01-16
> **QIII said:**
> No.  It means that just like Windows the distribution's features are frozen and the iso is static, so you have to do updates as soon as it is installed.

Right. Windows 7 didn't even jump up and tell me to upgrade to 7.11. When I checked I had 7.9 installed.

I think I keep Ubuntu more up to date than I do my Windows 7 install. But, I am on this more too. :)

---

### Post by samiux on 2013-01-16
Oracle has released the Java 7 Update 11 and claimed that the vulnerabilities have been fixed.  However, the 0day vulnerability has not been fixed according to some information.  Please read [this link]("http://krebsonsecurity.com/2013/01/new-java-exploit-fetches-5000-per-buyer/") for more details.

For Windows, Mac OSX and Linux users who has been updated to Java 7 Update 11 or not yet applied the patch, please disable the plugin from your browser.  If any website that requires the Java plugin, you must disable the plugin after use.

For Ubuntu users who has been updated to Java 7 Update 11, you can apply the Apparmor to increase the security of the Firefox.  For the users that do not apply the patch, Firefox will disable the plugin by default.  For implement of Apparmor for Firefox, please read [this link]("http://samiux.blogspot.com/2012/09/howto-apparmor-for-firefox-on-ubuntu.html").

Samiux

---

### Post by Ms. Daisy on 2013-01-16
Apparmor won't help - a "feature" of java is that it allows remote code execution inside of java. Will apparmor stop java from executing java? :/

---

### Post by samiux on 2013-01-16
> **Ms. Daisy said:**
> Apparmor won't help - a "feature" of java is that it allows remote code execution inside of java. Will apparmor stop java from executing java? :/

After the Apparmor for Firefox is enforced, I issued the following command and it displayed the result as the following :

```
sudo aa-status
```

```
apparmor module is loaded.
21 profiles are loaded.
21 profiles are in enforce mode.
   /sbin/dhclient
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-previewer//launchpad_integration
   /usr/bin/evince-previewer//sanitized_helper
   /usr/bin/evince-thumbnailer
   /usr/bin/evince-thumbnailer//sanitized_helper
   /usr/bin/evince//launchpad_integration
   /usr/bin/evince//sanitized_helper
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/firefox/firefox{,*[^s][^h]}
   /usr/lib/firefox/firefox{,*[^s][^h]}//browser_java
   /usr/lib/firefox/firefox{,*[^s][^h]}//browser_openjdk
   /usr/lib/firefox/firefox{,*[^s][^h]}//sanitized_helper
   /usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper
   /usr/lib/telepathy/mission-control-5
   /usr/lib/telepathy/telepathy-*
   /usr/sbin/cupsd
   /usr/sbin/tcpdump
0 profiles are in complain mode.
2 processes have profiles defined.
2 processes are in enforce mode.
   /usr/lib/telepathy/mission-control-5 (1992) 
   /usr/sbin/cupsd (801) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.
```

Then, I further checked the following file :

```
sudo nano /etc/apparmor.d/abstractions/ubuntu-browsers.d/java
```

I find out that almost all the components of the Java is allowed to read only but except the binary of Java itself.

To confirm if the Apparmor for Firefox is workable for the vulnerability, I need to set up a lab to test.  You will be informed as soon as possible.

Samiux

---

### Post by Hungry Man on 2013-01-16
> Apparmor won't help - a "feature" of java is that it allows remote code execution inside of java. Will apparmor stop java from executing java? :/
It won't prevent the RCE but it will:

1) Prevent writing/executing the payload
2) Restrict the JRE/ attacker to the profile.

FYI, to all concerned, there's a new Java exploit that will exploit Java update 11 (the latest) in the wild already.

---

### Post by Ms. Daisy on 2013-01-16
What im saying is the only way to fully protect from java exploits is to configure apparmor so that java cannot behave like java. The malicious code runs basically like native java. Hence apparmor would have to disable java completely. I'd love to hear that im wrong...

---

### Post by QIII on 2013-01-16
> **Hungry Man said:**
> It won't prevent the RCE but it will:

1) Prevent writing/executing the payload
2) Restrict the JRE/ attacker to the profile.

FYI, to all concerned, there's a new Java exploit that will exploit Java update 11 (the latest) in the wild already.

Java 7u12 will likely be breached within 48 hours.

The US Department of Homeland Security still recommends disabling the browser plugin.  Some reports I have read indicate this will take two years of concerted effort to rectify, during which time the bad guys will get ready to pounce again.

---

### Post by oldos2er on 2013-01-16
> **QIII said:**
> Will OpenJDK 7 provide you any better safety?

In short, no.


This is a point I've been wondering about, being very java-ignorant. I'm trusting your opinion on this, QIII.

---

### Post by Cavsfan on 2013-01-16
> **QIII said:**
> Java 7u12 will likely be breached within 48 hours.

The US Department of Homeland Security still recommends disabling the browser plugin.  Some reports I have read indicate this will take two years of concerted effort to rectify, during which time the bad guys will get ready to pounce again.

Cheese Whiz!  I like the popup though and if we are going to leave it enabled, which I plan to do. I guess we should pay close attention to what that popup is asking before allowing it to run.

---

### Post by Hungry Man on 2013-01-16
@QIII,

Yes, it is estimated two years. We'll see how they react when it starts getting widely distributed, which will happen in the next day or so.

@Ms. Daisy,

> What im saying is the only way to fully protect from java exploits is to configure apparmor so that java cannot behave like java. The malicious code runs basically like native java. Hence apparmor would have to disable java completely. I'd love to hear that im wrong...
Not really. Java applications needs access to the home directory. They need very little access otherwise, only to Java programs.

The way most exploits work is to drop a second payload and execute it. Apparmor kills that immediately.

Obviously that's a pseudomitigation and trivial to bypass. So what else does AppArmor provide?

As an attacker who exploits a typical Java JRE we have access to the full user directory - home, interacting with other processes, reading the filesystem for sensitive info (for monetization or local exploitation), writing new executable files, persistence, etc.

As an attacker who exploits a JRE running with a strict apparmor profile we can read/write to some Java files, read a few more files, and interact with no other processes. Significantly more secure, not easy to monetize at all.

So while the Java code runs perfectly fine (of course, you need Java to run for Java to run, as you say) it's not able to do anything malicious.

Java code running isn't scary - or not super scary - it's what it does after it runs we worry about.

---

### Post by offgridguy on 2013-01-16
This link deals with Java security flaw and windows.

[http://ask-leo.com/should_i_disable_java_and_if_so_how.html?awt_l=H3ACU&awt_m=K429IRa4eZdfbL](http://ask-leo.com/should_i_disable_java_and_if_so_how.html?awt_l=H3ACU&awt_m=K429IRa4eZdfbL)

---

### Post by samiux on 2013-01-16
Hi all,

After hours of testing with limited available Java plugins and reading the following information, I am sure that Firefox 18 with Java 6 Update 38 and Java 7 Update 10 are not affected by the vulnerability even you do not implemented the Apparmor for Firefox.  It is because Firefox 17 or above disabled the vulnerability Java plugins.

However, I have no available exploit to test Firefox 18 with Java 7 Update 11.  Therefore, I strongly recommend anyone who has updated to Java 7 Update 11 need to aware of executing any Java Applet on his/her Firefox 18.  

Or, you simply to uninstall/disable the Java 7 Update 11 or disable it after use.  Meanwhile, I strongly believe that Apparmor for Firefox can protect your box from being compromised by this vulnerability; however, I have no evidence at the moment.

The following information is quoted from [Add-ons Blocklist of Firefox]("https://addons.mozilla.org/en-US/firefox/blocked/") :

```
**Why was it blocked?**
    The Java plugin is causing significant security problems. All users are 
    strongly recommended to keep the plugin disabled unless necessary.

**Who is affected?**
    All users who have these versions of the plugin installed in Firefox 17 
    and above.

**What does this mean?**
    The problematic add-on or plugin will be automatically disabled and no 
    longer usable.

```

_The reference links :_

All users who have the Java Plugin 6 Update 31 through 38 installed in Firefox 17 and above.

[Java Plugin 6 updates 31 through 38 (click-to-play), Linux]("https://addons.mozilla.org/en-US/firefox/blocked/p190")

[Java Plugin 6 updates 38 and lower (click-to-play), Mac OS X]("https://addons.mozilla.org/en-US/firefox/blocked/p188")

[Java Plugin 6 updates 31 through 38 (click-to-play), Windows]("https://addons.mozilla.org/en-US/firefox/blocked/p186")


All users who have the Java Plugin 7 Update 10 and lower installed in Firefox 17 and above.

[Java Plugin 7 update 10 and lower (click-to-play), Linux]("https://addons.mozilla.org/en-US/firefox/blocked/p184")

[Java Plugin 7 update 10 and lower (click-to-play), Windows]("https://addons.mozilla.org/en-US/firefox/blocked/p182")

[Java Plugin 7 update 10 and lower (click-to-play), Mac OS X]("https://addons.mozilla.org/en-US/firefox/blocked/p180")

Samiux

---

### Post by samiux on 2013-01-17
Please read this [link]("http://immunityproducts.blogspot.hk/2013/01/confirmed-java-only-fixed-one-of-two.html") if you concern about the Java's latest update.

Samiux

---

### Post by bcschmerker on 2013-01-25
I found this Thread after reading of a potential design flaw in the Java® Runtime Environment from as far back as Release 1.4; it was apparently uncorrected by both Sun Microsystems® and Oracle® in all of Java® SE 5 (all known Updates), 6 (through Update 39), and 7 (through Update 11) and may affect their OpenJDK and IcedTea counterparts as well.  I removed Java® SE 6 Update 38 from my Asus® CM1630-06 (which runs Microsoft® Windows® 7.0.8001) and am awaiting information on a fix for the in-development (as of January 2013) Java® SE 8.  (An attempt to uninstall OpenJDK 6 would break the Metapackage ubuntu-desktop in 12.04.1-LTS.)

What source procedure in OpenJDK holds this design flaw and therefore must be fixed to resolve this issue?

---

### Post by AllenGG on 2013-01-25
Looks like  ORACLE has just released another  "PATCH"
Here:    [go ]("http://ubuntuforums.org/ww.oracle.com/technetwork/topics/security/alert-cve-2013-0422-1896849.html"),  but not likely will show up in "Synaptic"  for some time.

Use Synaptic to check your package list,  and you will see "Iced Tea" often referred to.

Note what happens when you use Synaptic to uninstall parts of Opewnjdk,  It appears to install other packages, strange.

Did you check your virus problems with Clamscan ?

---

