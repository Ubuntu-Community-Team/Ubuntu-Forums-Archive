---
title: "Basic Security Wiki (I can't leave &quot;good enough&quot; alone...)"
date: 2012-12-23
forum: Security
---

### Post by Ms. Daisy on 2012-12-23
Since Dangertux's server fell over and his helpful tutorials no longer have the screenshots available, I took it upon myself to copy his firewall tutorial into a wiki.  It is located here:

[https://wiki.ubuntu.com/BasicSecurity/Firewall](https://wiki.ubuntu.com/BasicSecurity/Firewall)

I haven't gotten around to adding the screen shots of GUFW yet but I plan to (unless someone else feels like it, in which case feel free !)

I also added the missing photos into [https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned](https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned) 

Enjoy

---

### Post by CharlesA on 2012-12-25
Awesome! Thanks for your continued work with this. :)

---

### Post by Pjotr123 on 2012-12-25
Why the need for those extra firewall rules? In  my opinion the default set of rules is quite sensible and should suffice for 90 % of the users.... :)

So for most users, merely switching on ufw should be quite enough:
```
sudo ufw enable
```

...and that's all. :)

---

### Post by bodhi.zazen on 2012-12-25
> **Pjotr123 said:**
> Why the need for those extra firewall rules? In  my opinion the default set of rules is quite sensible and should suffice for 90 % of the users.... :)

So for most users, merely switching on ufw should be quite enough:
```
sudo ufw enable
```

...and that's all. :)

I agree. But for those who wish to look deeper or those who want additional security the wiki page is a great asset.

Keep in mind, this is posted in the security section not general help, so most people here are looking for a little extra.

---

### Post by Pjotr123 on 2012-12-25
> **bodhi.zazen said:**
> I agree. But for those who wish to look deeper or those who want additional security the wiki page is a great asset.

Keep in mind, this is posted in the security section not general help, so most people here are looking for a little extra.
OK... I understand, and that makes sense. :)

But the main page of that wiki says this:
> This guide is intended for the typical, average home user that is in the process of learning how to use Ubuntu. So if you just surf the net, play games (on-line & off-line), do on-line banking, education...then you are the intended audience.

Source: [https://wiki.ubuntu.com/BasicSecurity/](https://wiki.ubuntu.com/BasicSecurity/)

Maybe that text should be altered?

---

### Post by samiux on 2012-12-25
I agreed with Pjotr123.

After reading the article, my first impression is that this article will put you into the trouble if you are not familiar with networking and TCP/IP.

For example, if you are using GMail, you may be in trouble as she uses different ports other than the article stated.

In my option, this kind of article is not recommanded.

Samiux

---

### Post by haqking on 2012-12-25
> **samiux said:**
> I agreed with Pjotr123.

After reading the article, my first impression is that this article will put you into the trouble if you are not familiar with networking and TCP/IP.

For example, if you are using GMail, you may be in trouble as she uses different ports other than the article stated.

In my option, this kind of article is not recommanded.

Samiux

Gmail ports are listed at the end as not everyone uses gmail.

it is a wiki, anyone can edit it if you feel it needs something.

---

### Post by samiux on 2012-12-25
After reading the article "DidIJustGetOwned", I am feeling that I am reading a joke.

First of all, rkhunter and chkrootkit are useless as they will make you very busy in the confirming the false postitive when your packages are just updated.

Clean (believed to be) logs cannot proof that nobody else has gain access your system from the outside world.  It is because almost all attackers are using Tor or proxy as well as they will also spoof their IP addresses.  In addition, they may also delete their footprints. 

No attacker will create an unauthorized connection.  They will use authorized connection instead.  You cannot find the difference between malicious or not malicious.

The last thing is that what the attacker want to do after your system is compromised?  Think about it!

Samiux

---

### Post by CharlesA on 2012-12-25
> **samiux said:**
> After reading the article "DidIJustGetOwned", I am feeling that I am reading a joke.

Congrats? It was written with the help of a few InfoSec people, namely Haqking and Dangertux.

It is on the wiki for people to improve it if they want.

---

### Post by haqking on 2012-12-25
> **samiux said:**
> After reading the article "DidIJustGetOwned", I am feeling that I am reading a joke.

First of all, rkhunter and chkrootkit are useless as they will make you very busy in the confirming the false postitive when your packages are just updated.

Clean (believed to be) logs cannot proof that nobody else has gain access your system from the outside world.  It is because almost all attackers are using Tor or proxy as well as they will also spoof their IP addresses.  In addition, they may also delete their footprints. 

No attacker will create an unauthorized connection.  They will use authorized connection instead.  You cannot find the difference between malicious or not malicious.

The last thing is that what the attacker want to do after your system is compromised?  Think about it!

Samiux


I didnt actually contribute anything to the DidIJutsgetowned wiki.

However from it:

> This section will cover the basics of log auditing so that you can begin  to understand which log output is concerning and which is probably  harmless.

It is a basic summary to assist those entering a little deeper into securing their system giving an overall feel for what to look for.

In reference to your post, not all attackers are skilled and not all attackers cover their tracks, infact it is all to often uneducated or unskilled attackers and skiddies attack or try to attack systems and leave a wealth of information behind, this wiki covers the basics of what to look for.

It is not meant as a in-depth covering tracks wiki nor a in depth log auditing or forensic wiki.

Feel free to add to it where you think applicable bearing in mind what i have just said in keeping in line with not overcomplicating things or taking things to a Penetration test or Security Audit level, it is not meant as an Offensive Security Course ;-)

---

### Post by samiux on 2012-12-26
> **haqking said:**
> In reference to your post, not all attackers are skilled and not all attackers cover their tracks, infact it is all to often uneducated or unskilled attackers and skiddies attack or try to attack systems and leave a wealth of information behind, this wiki covers the basics of what to look for.

I don't really believed that you will build a fortress to protect you from being attacked by a group of untrained enemies.  [-X

Samiux

---

### Post by bodhi.zazen on 2012-12-26
> **samiux said:**
> I don't really believed that you will build a fortress to protect you from being attacked by a group of untrained enemies.  [-X

Samiux

Well, there are several factors at work.

First you need to match your security efforts against the value of your target (assets), personal tolerance (paranoia), and ease of use.

Second, don't underestimate the damage a "script kiddie" can do. And yes they can get away with a ton if the system admin does not read the logs.

Third, IMO, Linux users have grown slack on security. It seems many users can not be bothered to read the logs. You need to understand what is normal behavior before you go looking for intruders.

In the situation of an intruder, the one with the most knowledge will have the upper hand. Education really is the best defense.

Keep in mind, the wiki is community maintained, and if you feel you can improve it, step up and contribute.

If you are unwilling to contribute, you come across as whining or argumentative and your comments here are dismissed before you even post them.

---

### Post by CharlesA on 2012-12-26
> **bodhi.zazen said:**
> 
Third, IMO, Linux users have grown slack on security. It seems many users can not be bothered to read the logs. You need to understand what is normal behavior before you go looking for intruders.

Agreed. This is why I installed logwatch (and skim thru auth.log ever once in a while). Having a summary report emailed to you helps a lot imho.

---

### Post by Hungry Man on 2012-12-26
The nice thing about a wiki is that everyone can contribute.

---

### Post by Soul-Sing on 2012-12-26
> If you are unwilling to contribute, you come across as whining or argumentative and your comments here are dismissed before you even post them.

Dear, please be argumentative (critical/rational) and "whining". Security is all about the whole community, not only for a selective contributing group, narrowing security discussions for "the Haves-only."
On the other hand being critical, specify exactly where the/your critic lays. Be aware if your not an expert your very fast empty handed in a security discours, because it becomes very fast complicated, technical, and often even obscure.

---

### Post by samiux on 2012-12-26
> **bodhi.zazen said:**
> Well, there are several factors at work.

First you need to match your security efforts against the value of your target (assets), personal tolerance (paranoia), and ease of use.

Second, don't underestimate the damage a "script kiddie" can do. And yes they can get away with a ton if the system admin does not read the logs.

Third, IMO, Linux users have grown slack on security. It seems many users can not be bothered to read the logs. You need to understand what is normal behavior before you go looking for intruders.

In the situation of an intruder, the one with the most knowledge will have the upper hand. Education really is the best defense.

Keep in mind, the wiki is community maintained, and if you feel you can improve it, step up and contribute.

If you are unwilling to contribute, you come across as whining or argumentative and your comments here are dismissed before you even post them.

Sorry for my English as English is not my native speaking language.

I have already mentioned in this thread about the out-dated information in the said article, such as rkhunter and chkrootkit, connections and logs checking.  (To CharlesA : the logwatch cannot give you a full picture of your server in the past.  Some useful information are omitted.)

In addition, I have already posted another thread about the security products are suck at [here]("http://ubuntuforums.org/showthread.php?t=2095870").  I think you need to spend some time to watch at least the first two videos in order to get more up-to-date information about the infosec field.

If you don't think it is a kind of contribution, I have nothing to say.  I am feeling that this forum cannot accept any other opinions that do not fix into yours mind.  I am very very disappointed!

Infosec is a kind of art and skill.  It is improving and changing as well as adopting to the new technologies.  Therefore, in my own opinion, this kind of articles will mislead other readers especially when the articles are failed to update.  In fact, there are many Ubuntu wiki articles are out-dated in the wild.

I agreed that script kiddies are harmful as we cannot predict what will they do on our systems.  However, there are many different levels of script kiddies.  Some of them may know how to hide themself and prevent from being caught.  As we know that there are many systems have been compromised but there are a few attackers being caught.  You will know that those level of the said script kiddies have been upgraded for a long time ago.

In the net, almost everyone said that Ubuntu is great for newcomers or newbies.  Therefore, I disagreed that Ubuntu or Linux users are brilliant or security alert than the other operating system users.  Nowadays, Linux is not very hard to learn.  It is very similar to learn to use a Mac OSX and Windows 7 or 8.

Finally, I agreed that education is the best defense.  However, I do not agree that such articles are a kind of education.  The best education is to learn HOW and WHAT the attackers thinking and HOW and WHAT they do to compromise a system.  Then, you will know HOW and WHAT to protect and check your systems.

Last word, attackers are very clever or you can say that they are clever than us.  They will use their creative mind to turn the impossible to possible.  Don't think that Linux is very hard to compromise.  In my option, it is very easy to compromise as similar as Windows box and Mac.

Thanks for reading.

Samiux

---

### Post by haqking on 2012-12-27
> **samiux said:**
> Sorry for my English as English is not my native speaking language.

I have already mentioned in this thread about the out-dated information in the said article, such as rkhunter and chkrootkit, connections and logs checking.  (To CharlesA : the logwatch cannot give you a full picture of your server in the past.  Some useful information are omitted.)

In addition, I have already posted another thread about the security products are suck at [here]("http://ubuntuforums.org/showthread.php?t=2095870").  I think you need to spend some time to watch at least the first two videos in order to get more up-to-date information about the infosec field.

If you don't think it is a kind of contribution, I have nothing to say.  I am feeling that this forum cannot accept any other opinions that do not fix into yours mind.  I am very very disappointed!

Infosec is a kind of art and skill.  It is improving and changing as well as adopting to the new technologies.  Therefore, in my own opinion, this kind of articles will mislead other readers especially when the articles are failed to update.  In fact, there are many Ubuntu wiki articles are out-dated in the wild.

I agreed that script kiddies are harmful as we cannot predict what will they do on our systems.  However, there are many different levels of script kiddies.  Some of them may know how to hide themself and prevent from being caught.  As we know that there are many systems have been compromised but there are a few attackers being caught.  You will know that those level of the said script kiddies have been upgraded for a long time ago.

In the net, almost everyone said that Ubuntu is great for newcomers or newbies.  Therefore, I disagreed that Ubuntu or Linux users are brilliant or security alert than the other operating system users.  Nowadays, Linux is not very hard to learn.  It is very similar to learn to use a Mac OSX and Windows 7 or 8.

Finally, I agreed that education is the best defense.  However, I do not agree that such articles are a kind of education.  The best education is to learn HOW and WHAT the attackers thinking and HOW and WHAT they do to compromise a system.  Then, you will know HOW and WHAT to protect and check your systems.

Last word, attackers are very clever or you can say that they are clever than us.  They will use their creative mind to turn the impossible to possible.  Don't think that Linux is very hard to compromise.  In my option, it is very easy to compromise as similar as Windows box and Mac.

Thanks for reading.

Samiux

I think you are missing the point here in the thread and the wikis.  It is a **BASIC** wiki introducing new Ubuntu users to security, it is not meant as a offensive/defensive or forensic wiki.  It is merely offering some additional information for those new to Linux usually who have come to it through Ubuntu.  There is nothing in-depth to it nor meant to be.

I am a penetration tester and been in IT and Infosec for 20+ years and could spend the next 4 weeks writing a wiki about Linux Security but that is not the goal or aims of this wiki.

I am well aware that Linux can be compromised as easily as Windows and other OS, which is the point of the wiki also, to gently nudge those new users who do have a  interest in security towards taking proactive steps in begining to secure their systems and not be too nonchalant about it following the general view that "Linux is secure" because it is not, those who read the wiki will either take advice or not, brush it off maybe or get more insterested and follow the links and begin to educate themselves leading to a more "secure" system.

So once again it is a BASIC guide, rather than denigrate its contents then contribute instead, that being said if you do choose to contribute please dont over complicate it as the intent is for a basic overview for the new Ubuntu user, if we add too much there will end up being a ton of threads about the BASIC security wiki going over peoples heads.

I would also like to point out that by your own admission on your blog, it wasnt too long ago that you didnt know what a Penetration Test/er was and was new to Infosec and Backtrack, and though i congratulate on you taking some certs and getting yourself into the Industry, it doesn't mean you are an "expert" or in a position to argue about the content of a wiki to which you don't seem to want to contribute too but would rather spend the time writing a post about it being a "joke".

if you wish to contribute excellent, please do so but keep it simple and within the realms of a new Ubuntu user.

Happy hacking.

---

### Post by samiux on 2012-12-27
> **haqking said:**
> I think you are missing the point here in the thread and the wikis.  It is a **BASIC** wiki introducing new Ubuntu users to security, it is not meant as a offensive/defensive or forensic wiki.  It is merely offering some additional information for those new to Linux usually who have come to it through Ubuntu.  There is nothing in-depth to it nor meant to be.

I am a penetration tester and been in IT and Infosec for 20+ years and could spend the next 4 weeks writing a wiki about Linux Security but that is not the goal or aims of this wiki.

I am well aware that Linux can be compromised as easily as Windows and other OS, which is the point of the wiki also, to gently nudge those new users who do have a  interest in security towards taking proactive steps in begining to secure their systems and not be too nonchalant about it following the general view that "Linux is secure" because it is not, those who read the wiki will either take advice or not, brush it off maybe or get more insterested and follow the links and begin to educate themselves leading to a more "secure" system.

So once again it is a BASIC guide, rather than denigrate its contents then contribute instead, that being said if you do choose to contribute please dont over complicate it as the intent is for a basic overview for the new Ubuntu user, if we add too much there will end up being a ton of threads about the BASIC security wiki going over peoples heads.

I would also like to point out that by your own admission on your blog, it wasnt too long ago that you didnt know what a Penetration Test/er was and was new to Infosec and Backtrack, and though i congratulate on you taking some certs and getting yourself into the Industry, it doesn't mean you are an "expert" or in a position to argue about the content of a wiki to which you don't seem to want to contribute too but would rather spend the time writing a post about it being a "joke".

if you wish to contribute excellent, please do so but keep it simple and within the realms of a new Ubuntu user.

Happy hacking.

I admit that I am not an expert and I am a newbie only, but this article is just like a joke and misleading anyway.  Even an newbie knows that.

Being a penetration tester or attacker, if s/he have a creative mind and skill, s/he can master the stuff without problem.  I think it is not related to experience or not.  Meanwhile, there are many useful and skillful articles in the net about that.  However, some said experienced infosec experts may do something stupid as there are many fake experienced experts in the wild.

For example, a kid (says 10 or so) can compromise a big corp or government systems with ease and the kid have very little experience in this field.  The kid only have 10 or so years of living experience in the world.  How about the experience in the infosec?  So, experience will make you proud but not the essential indeed.

In my own opinion, there is no BASIC or ADVANCED security information.  We need to deliver the true and technical information.  When an newbie read a lot of true and technical information, s/he will be not an newbie anymore.  If he read a lot of "BASIC" information, s/he will be an newbie forever.  There is no excess true and technical information.  Live is hard!

Samiux

---

### Post by haqking on 2012-12-27
> **samiux said:**
> I admit that I am not an expert and I am a newbie only, but this article is just like a joke and misleading anyway.  Even an newbie knows that.

Being a penetration tester or attacker, if s/he have a creative mind and skill, s/he can master the stuff without problem.  I think it is not related to experience or not.  Meanwhile, there are many useful and skillful articles in the net about that.  However, some said experienced infosec experts may do something stupid as there are many fake experienced experts in the wild.

For example, a kid (says 10 or so) can compromise a big corp or government systems with ease and the kid have very little experience in this field.  The kid only have 10 or so years of living experience in the world.  How about the experience in the infosec?  So, experience will make you proud but not the essential indeed.

In my own opinion, there is no BASIC or ADVANCED security information.  We need to deliver the true and technical information.  When an newbie read a lot of true and technical information, s/he will be not an newbie anymore.  If he read a lot of "BASIC" information, s/he will be an newbie forever.  There is no excess true and technical information.  Live is hard!

Samiux

So are you saying there shouldnt be a wiki on the basics of where to begin in being proactive about securing your Linux system?

And there shouldnt be a wiki on where to begin with checking logs ?

Because it is all out there already if people want to learn ?

I disagree, but we are all welcome to our opinions.

The wiki is community based and can be edited, and people can choose to read it or not, there have also been already been numerous thanks from new users who found it useful.

---

### Post by Pjotr123 on 2012-12-27
> **haqking said:**
> So are you saying there shouldnt be a wiki on the basics of where to begin in being proactive about securing your Linux system?

The "basic" wiki says fine and interesting things (kudo's for your efforts!), but in my opinion it goes beyond the needs of Linux beginners who just want to have a safe desktop for general use....

For those ordinary desktop users, a few simple rules are enough, I think:
1. immediately install security updates when you're notified;
2. do not install antivirus, as you *really* don't need it in Linux;
3. enable the firewall (sudo ufw enable) without further tweaks;
4. stick to the official repo's as much as possible, and only deviate from them when strictly necessary and with much caution;
5. keep Java disabled by default, and only enable it when needed;
6. tweak Wine a bit to make it more secure;
7. and most important of all: use your common sense. The biggest security threat is generally found between keyboard and chair. :biggrin:

If only we could hammer that simple message between the ears of Linux beginners, a lot of harm would be prevented.... :p

In my opinion, the "basic" wiki currently contains a lot of advanced tweaking for people with enhanced security needs, who need a much higher level of security than the ordinary home user....

---

### Post by samiux on 2012-12-27
> **haqking said:**
> So are you saying there shouldnt be a wiki on the basics of where to begin in being proactive about securing your Linux system?

And there shouldnt be a wiki on where to begin with checking logs ?

Because it is all out there already if people want to learn ?

I disagree, but we are all welcome to our opinions.

The wiki is community based and can be edited, and people can choose to read it or not, there have also been already been numerous thanks from new users who found it useful.

I am doubt that does an newcomer of Ubuntu/Linux (as you said) understand what the system logs said when s/he is reading.  They even do not know how to read a normal system logs.  But you ask them to read, nonsense.  

Linux SysAdmin always ask others to read logs but do not teach them how to identify the malicious activities.  What does it look like?  What does it mean?  It is because they do not know too, I guess.

Sometimes, system logs cannot provide you useful information as the malicious activities may be same as the legal one.

Meanwhile, the said article is giving out a misleading information to newcomers (as you said).  They may treat this as a bible.  So, I suggest not to write this kind of article anymore.

The wiki should be covered all true and technical as well as up-to-date information about the infosec but not only the "BASIC".  Please DO NOT classify your readers as NEWBIES or NEWCOMERS.  As I said, when they read/know more, they are no more newbies or newcomers.

Samiux

---

### Post by Pjotr123 on 2012-12-27
> **samiux said:**
> Please DO NOT classify your readers as NEWBIES or NEWCOMERS.

I disagree strongly. A clear message with a few simple security rules for beginners, is very, very useful. Because most of them won't take the trouble to read long, in-depth articles. TL;DNR. 

We must take human nature as it is... :)

---

### Post by haqking on 2012-12-27
> **Pjotr123 said:**
> The "basic" wiki says fine and interesting things (kudo's for your efforts!), but in my opinion it goes beyond the needs of Linux beginners who just want to have a safe desktop for general use....

For those ordinary desktop users, a few simple rules are enough, I think:
1. immediately install security updates when you're notified;
2. do not install antivirus, as you *really* don't need it in Linux;
3. enable the firewall (sudo ufw enable) without further tweaks;
4. stick to the official repo's as much as possible, and only deviate from them when strictly necessary and with much caution;
5. keep Java disabled by default, and only enable it when needed;
6. tweak Wine a bit to make it more secure;
7. and most important of all: use your common sense. The biggest security threat is generally found between keyboard and chair. :biggrin:

If only we could hammer that simple message between the ears of Linux beginners, a lot of harm would be prevented.... :p

In my opinion, the "basic" wiki currently contains a lot of advanced tweaking for people with enhanced security needs, who need a much higher level of security than the ordinary home user....

> **samiux said:**
> I am doubt that does an newcomer of Ubuntu/Linux (as you said) understand what the system logs said when s/he is reading.  They even do not know how to read a normal system logs.  But you ask them to read, nonsense.  

Linux SysAdmin always ask others to read logs but do not teach them how to identify the malicious activities.  What does it look like?  What does it mean?  It is because they do not know too, I guess.

Sometimes, system logs cannot provide you useful information as the malicious activities may be same as the legal one.

Meanwhile, the said article is giving out a misleading information to newcomers (as you said).  They may treat this as a bible.  So, I suggest not to write this kind of article anymore.

The wiki should be covered all true and technical as well as up-to-date information about the infosec but not only the "BASIC".  Please DO NOT classify your readers as NEWBIES or NEWCOMERS.  As I said, when they read/know more, they are no more newbies or newcomers.

Samiux


Feel free to contribute.

---

### Post by samiux on 2012-12-27
> **Pjotr123 said:**
> I disagree strongly. A clear message with a few simple security rules for beginners, is very, very useful. Because most of them won't take the trouble to read long, in-depth articles. TL;DNR. 

We must take human nature as it is... :)

I strongly disagreed.

When they read the said "BASIC" infosec information, they will treat this as bible and sticked to it.  However, it is not enough.  Their systems can still be compromised, I mean desktops and servers for both.

Do you know how many zombies or say botnets out there in the wild?  They are not only Windows boxes but also includes Linux and other systems.  Why this happened?  It is because they read and learn the said "BASIC" security information.  They even do not know that their systems are infected.

Live is hard!  So, you need to read and learn more about true and technical as well as up-to-date information.

Samiux

---

### Post by samiux on 2012-12-27
> **haqking said:**
> Feel free to contribute.

I think discussion is also a kind of contribute.

Samiux

---

### Post by Hungry Man on 2012-12-27
I disagree
 If the argument is that the wiki is only basic and you can still get hacked than, yes, you are entirely correct. But I'm confused as to why that's a problem.

You state they will treat it as if it were all there is to security. I doubt it, but even if they did, if they spend the time setting up Apparmor profiles they'll be quite a lot safer than many users. So while advanced attacks will still work (attackswith second stage kernel exploits) many won't, like a typical java exploit.

I'm on a phone unfortunately so I'm reluctant to spend the time on this. But based on the topics I have seen on more basic security forums including this one the wiki addresses the most commons questions with the most common answers.

The goal is to have those questions answered without a user needing to make a topic.

---

### Post by samiux on 2012-12-27
> **Hungry Man said:**
> I disagree
 If the argument is that the wiki is only basic and you can still get hacked than, yes, you are entirely correct. But I'm confused as to why that's a problem.

I'm on a phone unfortunately so I'm reluctant to spend the time on this. But based on the topics I have seen on more basic security forums including this one the wiki addresses the most commons questions with the most common answers.

The goal is to have those questions answered without a user needing to make a topic.


I have already answered at [#24]("http://ubuntuforums.org/showpost.php?p=12424149&postcount=24").

Samiux

---

### Post by samiux on 2012-12-27
> **Hungry Man said:**
> You state they will treat it as if it were all there is to security. I doubt it, but even if they did, if they spend the time setting up Apparmor profiles they'll be quite a lot safer than many users. So while advanced attacks will still work (attackswith second stage kernel exploits) many won't, like a typical java exploit.

However, the said article is not talking about Apparmor or alike.  Therefore, I said we need true and technical as well as up-to-date infosec information.

Samiux

---

### Post by haqking on 2012-12-27
> **samiux said:**
> However, the said article is not talking about Apparmor or alike.  Therefore, I said we need true and technical as well as up-to-date infosec information.

Samiux

This threads OP is about the Firewall page.

The Basic Security Wiki mentions and links to further about apparmor as found here [https://wiki.ubuntu.com/BasicSecurity#AppArmor](https://wiki.ubuntu.com/BasicSecurity#AppArmor)

Your original post was about the firewall page not covering Gmail ports which it does.

---

### Post by samiux on 2012-12-27
> **haqking said:**
> This threads OP is about the Firewall page.

The Basic Security Wiki mentions and links to further about apparmor as found here [https://wiki.ubuntu.com/BasicSecurity#AppArmor](https://wiki.ubuntu.com/BasicSecurity#AppArmor)

Your original post was about the firewall page not covering Gmail ports which it does.

My discussion is switched to the article "DidIJustGetOwned" since [#8]("http://ubuntuforums.org/showpost.php?p=12421701&postcount=8").

For the post about Firewall, it is just an example to point out that if the newcomers (as you said) do not understand networking and TCP/IP, they will be in trouble.  So, I agreed with Pjotr123 that a simple firewall rules is enough.  It is because there are many opening ports (that you do not know) even you restricted the rules tidy.

For the Apparmor, it is just an example that Hungry Man stated and I refer to it only.

My main discussion is targeted to the article namely "DidIJustGetOwned".

Samiux

---

### Post by haqking on 2012-12-27
> **samiux said:**
> My discussion is switched to the article "DidIJustGetOwned" since [#8]("http://ubuntuforums.org/showpost.php?p=12421701&postcount=8").

For the post about Firewall, it is just an example to point out that if the newcomers (as you said) do not understand networking and TCP/IP, they will be in trouble.  So, I agreed with Pjotr123 that a simple firewall rules is enough.  It is because there are many opening ports (that you do not know) even you restricted the rules tidy.

For the Apparmor, it is just an example that Hungry Man stated and I refer to it only.

My main discussion is targeted to the article namely "DidIJustGetOwned".

Samiux

So you want a section on Apparmor in the DidIJustGetOwned wiki ?

Guess what, you can add it, it is a wiki ;-)

But as already stated it is covered from the Link i posted above

---

### Post by Elfy on 2012-12-27
This is going nowhere fast.

The beginning and end of the wiki is that ANYONE can do it.

Complaining about what others have done is quite frankly just bad manners, if you have that much of an issue - go and edit things - just like the others that have taken time out of their day to do.

Closed.

---

