---
title: "How do I know if my computer has been affected by java script?"
date: 2012-01-18
forum: Security
---

### Post by arroy_0209 on 2012-01-18
Although I try to be safe by using add ons like no script and adblockplus, with firefox, at times I have to let no script allow some websites which may run java script to get full information on the page. In case some website does that, what security issues may arise? How do I know that my operating system (Ubuntu 10.04 LTS) had been affected due to running java script without my notice?

Also, are there other problems which might be created by malicious websites?

---

### Post by haqking on 2012-01-18
> **arroy_0209 said:**
> Although I try to be safe by using add ons like no script and adblockplus, with firefox, at times I have to let no script allow some websites which may run java script to get full information on the page. In case some website does that, what security issues may arise? How do I know that my operating system (Ubuntu 10.04 LTS) had been affected due to running java script without my notice?

Also, are there other problems which might be created by malicious websites?

To infinity and beyond.

too many possibilities to list, not all javascript is bad, infact you need it for 9/10 sites to be most effective.

Whether you come across a malicious one and what the script may contain could be  a multitude of things.

if you have no issues dont worry about it too much

regularly check your logs

Cheers

---

### Post by arroy_0209 on 2012-01-19
Thanks. However I need a bit more info. 

First, which log file should I look for? There are so many different files. I guess /var/log/syslogs would obviously include such info. 

Second, which keyword(s) should I match using grep command to detect such problem?

---

### Post by mikewhatever on 2012-01-19
You'll have to learn intrusion detection. It's not exactly trivial, so start getting familiar with the logs, networking, intrusion detection tools, etc.

---

### Post by haqking on 2012-01-19
> **arroy_0209 said:**
> Thanks. However I need a bit more info. 

First, which log file should I look for? There are so many different files. I guess /var/log/syslogs would obviously include such info. 

Second, which keyword(s) should I match using grep command to detect such problem?

> **mikewhatever said:**
> You'll have to learn intrusion detection. It's not exactly trivial, so start getting familiar with the logs, networking, intrusion detection tools, etc.

Well intrusion detection is a full time science, however yes the basics are handy.

however that presupposes you are looking for an intrusion attempt and not all malicious javascript is based around an intrusion attempt or culminates in one, so the malicious script may have run but doesnt mean someone intruded in on your system.

@the OP, all you mentioned was a malicious javascript.

There are hundreds and thousands of possible permutations of script which could be gleemed as malicious, so performing a grep is no use unless you are looking for something specific, what that would be depends on what you think may have occured.

As for which logs, again it depends on what the malicious script performed.

---

### Post by cariboo on 2012-01-20
@arroy_0209 I'd like to know, what system behavior you are experiencing, that prompted your question.

---

### Post by arroy_0209 on 2012-01-20
Thanks for all the replies.

In response to cariboo907: I am not experiencing any system abnormality, just trying to broaden my knowledge about security and also to be capable of configuring no-script. Almost every security discussion for beginners teaches to restrict running java script by website (by means of add ons like no-script). In reality this makes one safe but one also loses functionality of the website. Now as a user how do I decide when to let no-script allow the website and when not to? I am asking only to get a clear answer to this.

Here is one example: consider this blog : [motls.blogspot.com]("http://motls.blogspot.com") If you load with default setting of no-script, at the bottom of browser you may find: scripts partially allowed 3/24, <SCRIPTS> :186, <OBJECT>: 2.  The no-script options will ask permission to allow various websites, at least temporally. Now there is one such: js-kit.com which must be allowed, otherwise the displayed equations (written in latex) in the blog will not be visible.(Also the blogspot.com has to be kept in whitelist) Now how do I trust js-kit.com? It may help me by displaying equations but the site can harm my system since it can run java script. I get confused at times. What should I do in such cases?

---

### Post by haqking on 2012-01-20
> **arroy_0209 said:**
> Thanks for all the replies.

In response to cariboo907: I am not experiencing any system abnormality, just trying to broaden my knowledge about security and also to be capable of configuring no-script. Almost every security discussion for beginners teaches to restrict running java script by website (by means of add ons like no-script). In reality this makes one safe but one also loses functionality of the website. Now as a user how do I decide when to let no-script allow the website and when not to? I am asking only to get a clear answer to this.

Here is one example: consider this blog : [motls.blogspot.com]("http://motls.blogspot.com") If you load with default setting of no-script, at the bottom of browser you may find: scripts partially allowed 3/24, <SCRIPTS> :186, <OBJECT>: 2.  The no-script options will ask permission to allow various websites, at least temporally. Now there is one such: js-kit.com which must be allowed, otherwise the displayed equations (written in latex) in the blog will not be visible.(Also the blogspot.com has to be kept in whitelist) Now how do I trust js-kit.com? It may help me by displaying equations but the site can harm my system since it can run java script. I get confused at times. What should I do in such cases?


The only sure fire way is to examine the script.

Anything else is trust, and trust is a funny thing, trust is just the belief or hope that nothing will go wrong ;-)

There is no such thing as a sure thing when it comes to computer/online security.

here is a good tutorial on noscript configuration
[http://ubuntuforums.org/showpost.php?p=11451584&postcount=450](http://ubuntuforums.org/showpost.php?p=11451584&postcount=450)

in Security there is a fine line between security, functionality and ease of use, as soon as you move towards one you move further away from the others

---

### Post by cryptotheslow on 2012-01-20
Without examining each and every script before allowing it to run it's impossible to come to a 100% accurate decision. Clearly that is impractical and requires intimate javascript knowledge.

One alternative is to confine what actions your browser can take on your machine using the likes of AppArmor or SELinux. Have a read of bodhi.zazen's apparmor intro sticky thread in this foum section.

Another alternative is to load up a separate installation of your OS in a virtual machine e.g. VirtualBox and use it solely for browsing. It is also relatively trivial to take a snapshot of the virtual machine before browsing then reverting back to that known "clean" snapshot once you're done.

Unfortunately security and convenience are not the best of compadres :)

*Cross-posted with Haqking - sorry for the repetition :) *

---

### Post by Ms. Daisy on 2012-01-20
> **cryptotheslow said:**
>  Another alternative is to load up a separate installation of your OS in a virtual machine e.g. VirtualBox and use it solely for browsing. It is also relatively trivial to take a snapshot of the virtual machine before browsing then reverting back to that known "clean" snapshot once you're done. 
I would add here that if you reverted to a snapshot in a virtual machine, that still wouldn't protect you from browser hijack/ credential theft while you were browsing.

---

### Post by Dangertux on 2012-01-20
Ms. Daisy hit on a really good point here.

There is a very limited amount of information your system will actually log about web/javascript based threats.

For instances things your system will log.

Direct browser compromise (IE: Memory corruption that leads to a compromised service). This wil lbe logged in syslog in ubuntu (other distros call it something else). 

That being said, clickjacking, XSS, session riding and a myriad of other web based nasties can ruin your day (and you credit score) without ever touching your system. These are much harder to spot, and pretty much impossible to spot in logs. Why? Because they're not an actual intrusion into YOUR system. They are gleaning your information from an external website that is flawed.

What you can do is use NoScript effectively here -- that will stop 99% of the issues. Again even if you allow all the scripts running on a page and one is malicious, NoScript _MAY_ still prevent that attack from working (depending on how the attack is designed). 

If you're super paranoid, you can analyse each and every script running on a page. However, due to obfuscation techniques this may be a little bit difficult. Not all obfuscated scripts are malicious, some sites do it to save bandwidth. 

Additionally you can use something like Tamper Data or Web Scarab to go through play by play every single request your browser is making. This would make your browsing experience...Well, very dull.

So my best advice is use common sense and a sensibly configured NoScript addon ;-)

Hope this helps.

---

### Post by cryptotheslow on 2012-01-20
True - I should have been clearer - loading up a vm just helps separate the browser from your main OS it's of no assistance preventing drive-bys in the browser instance itself.

All depends how paranoid you want to be :D

Personally (as far as I know) I've had no problem just using Firefox with NoScript* in block everything unless I say otherwise mode. But then my browsing habits are pretty unadventurous.

*Also Adblock Plus, Better Privacy and Ghostery - but those are for other reasons.

---

### Post by OpSecShellshock on 2012-01-20
> **cryptotheslow said:**
> *Also Adblock Plus, Better Privacy and Ghostery - but those are for other reasons.

Though now that you mention it, Adblock Plus is actually really good in the sense that a lot of malware is delivered by way of malicious ads that have made their way onto third party ad platforms, and ABP also allows for blocking of individual scripts on sites for those patient enough to flip switches and see what happens. That can be useful when you want to allow the scripts that are necessary for the functions you want, but would like to block everything else.

---

### Post by emiller12345 on 2012-01-21
usually when someone has hijacked your browser, they "hook your browser", where they keep a running script looping in the background, repeatedly sending data back to their server and commands to your browser.  You might be able to use a firefox addon like "Live HTTP Headers" to observe if there is data flying around when your not actively using your browser, and its just open.  Some sites legitimately loop data, but it will at least let you see whats going on.

---

