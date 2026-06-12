---
title: "What do I need to know about this Java issue everyone's talking about?"
date: 2013-01-16
forum: Security
---

### Post by MyTinFoilHat on 2013-01-16
I've been reading this thread about Java Security:
[http://ubuntuforums.org/showthread.php?p=12459242#post12459242](http://ubuntuforums.org/showthread.php?p=12459242#post12459242)

Honestly, it's a little over my head. (I have been focused on reading the stickies in the Security Threads to learn more about security. Problem is, I'm just not "there" yet, skills- or experience-wise)... I also didn't want to be 'that guy' that interrupts the flow of a good thread with a noob question - which is why I'm posting here.

I realize there's a series of exploits in Java. I just don't want to be doubly 'at risk' due to my lack of knowledge.
 
I'm not sure what I can/should do about this that continues to insure my safety/security. I see some discussing the idea that (paraphrasing), if you're using the latest Firefox (18), there are "no worries", or there are other discussions surrounding the use of AppArmor (again, I'm not "there" yet, skillwise). There's a lot of cross-talk from people that have (clearly) a lot of knowledge.

I'm not ashamed to admit this, but the extent of my know-how right now is limited to having "Enable Javascript" UNchecked. 

Can anyone throw a few other pointers my way?
Also, I see I have updates for OpenJDK 7u9-2.3.4... (I've seen discussions mentioning how the issues facing Java likely made their way into OpenJDK)... Should I update these then seek further updates?

It's a little frustrating not knowing what to do. ...And, yes, I don't mind if you explain it as though I'm 5.

Thanks.

---

### Post by MadmanRB on 2013-01-16
Yes please update openjdk, as this exploit will probably work in even the open source version of java that Ubuntu uses.
Free or open java issues effect us all.

---

### Post by 3rdalbum on 2013-01-17
Java and JavaScript are two completely different things. You can keep JavaScript enabled.

To fix the Java issue: it is really easy. Simply remove Java using your package manager.

Attempting to work around the current Java problem will do you no good against the next Java problem in a month or two. Removing Java will render your computer safe against Java flaws.

---

### Post by MyTinFoilHat on 2013-01-17
> **3rdalbum said:**
> Java and JavaScript are two completely different things. You can keep JavaScript enabled.

To fix the Java issue: it is really easy. Simply remove Java using your package manager.

Attempting to work around the current Java problem will do you no good against the next Java problem in a month or two. Removing Java will render your computer safe against Java flaws.

Aah! Got it. Thank you for explaining.
Should I do this in addition to what MadmanRB suggested above (updating openJDK)?
Is there a lot of "loss of functionality" when I do remove Java? Sorry, that's probably a stupid question.

---

### Post by kunai on 2013-01-17
> **MyTinFoilHat said:**
> Aah! Got it. Thank you for explaining.
Should I do this in addition to what MadmanRB suggested above (updating openJDK)?
Is there a lot of "loss of functionality" when I do remove Java? Sorry, that's probably a stupid question.

There will be some loss of functionality in Java-enabled websites, and if you use Java-based development tools like NetBeans, you won't be able to use them anymore. But not a lot of websites use Java anymore -- most have switched to Flash, and even Flash is going away in favor of HTML5. So unless you use NetBeans, I don't think you have anything to worry about.

---

### Post by slickymaster on 2013-01-17
According to an official announcement from Homeland Security, the day before yesterday > *Unless it is absolutely necessary to run Java in web browsers, disable it ... even after updating to 7u11. This will help mitigate other Java vulnerabilities that may be discovered in the future.*

[Java Still Insecure Warns Homeland Security]("http://i-programmer.info/news/149-security/5332-java-still-insecure-warns-hoemland-security.html")

---

### Post by QIII on 2013-01-17
Oracle is vainly patching cracks in the asphalt in an intersection built on a rapidly growing sink hole.

The whole thing needs to be redesigned and completely reconstructed.

---

### Post by bjje on 2013-01-17
ImageJ needs java and loads it when you install.  Is there any way to just have java used for allowed apps?

---

### Post by brusegadi on 2013-01-17
Also, I think if you did not install the restricted extras you wont have java. So, if you are only using the restricted-addons (but not the entire restricted extras package) you should be fine.

---

### Post by slickymaster on 2013-01-17
> **QIII said:**
> Oracle is vainly patching cracks in the asphalt in an intersection built on a rapidly growing sink hole.

The whole thing needs to be redesigned and completely reconstructed.

You couldn't be more right. That's what should be Oracle priority right now, instead of a damage control approach.

---

### Post by d4m1r on 2013-01-17
> **slickymaster said:**
> According to an official announcement from Homeland Security, the day before yesterday 

[Java Still Insecure Warns Homeland Security]("http://i-programmer.info/news/149-security/5332-java-still-insecure-warns-hoemland-security.html")

Wrong, but then again, not like I would ever trust Homeland Security....If you update your Java, you will be fine...At least until a new exploit is found. Java is an often used mechanic on many websites so certain functionality will not work if it can't detect Java (because you disabled it).

> **QIII said:**
> Oracle is vainly patching cracks in the asphalt in an intersection built on a rapidly growing sink hole.

The whole thing needs to be redesigned and completely reconstructed.

Despite my comments above, I agree. It is becoming the new flash....Then again, so many devices run it, it was bound to become a target and I doubt it is going anywhere anytime soon....

---

### Post by MyTinFoilHat on 2013-01-17
> **QIII said:**
> Oracle is vainly patching cracks in the asphalt in an intersection built on a rapidly growing sink hole.

The whole thing needs to be redesigned and completely reconstructed.

That's the impression I've gotten -even if I didn't know what to do about it from the start.

---

### Post by MyTinFoilHat on 2013-01-17
Thank you to everyone who responded!

So, I should do the software update for OpenJDK, then remove Java via Synaptic? Is that right?

---

### Post by HunterDX77M on 2013-01-18
First off, I know nothing about security so I don't know anything about the nature of this security risk that everyone is talking about. **My question is as Ubuntu users, is there something specific we should do prevent any damage to our computers?** :confused:

I've Googled around and everyone's knee-jerk response has been to *remove Java*. Okay. What parts? The runtime environment? The JDK? What versions should we have to worry about (6 or 7)? What about those that are writing programs in Java?

Please explain this to me as if I were 5 years old. I'd really appreciate it. (Any terminal commands would also be helpful!) :D

Thanks in advance!

---

### Post by Sdrabor on 2013-01-18
FWIW, I know that these specific vulerabilities are limited to Java 7.  I don't know what other people have been doing, but for me I'm not using the Oracle version of Java anyway on Ubuntu, so I'm not too worried about it.  On my Windows boxes I've simply installed the latest versions of Java 6, and planning on staying there until Oracle gets their act together with 7.

---

### Post by MoebusNet on 2013-01-18
As I understand it, Java and Javascript are 2 completely different applications; the only similarity is the *Java* in the names. The average desktop user really has no need for Java and can safely remove it with the GUI software management application of your desktop. If you really need it in the future, you can always reinstall it.

The Firefox plug-in to use Java applets on webpages can be disabled using Tools>Plugins>Disable (in my case the IcedTea-Web1.2 plugin).

A more complete discussion is here:

[http://ubuntuforums.org/showthread.php?t=2104048](http://ubuntuforums.org/showthread.php?t=2104048)

---

### Post by OrangeCrate on 2013-01-18
And another thread is here:

[http://ubuntuforums.org/showthread.php?t=2105734&highlight=java+security](http://ubuntuforums.org/showthread.php?t=2105734&highlight=java+security)


Edit:

Um, wait a sec, I think a couple have already been merged. Soon to become a "mega" thread, I would expect.

---

### Post by nothingspecial on 2013-01-18
*Thread moved to **Security Discussions**.*

and Merged.

---

### Post by BBQdave on 2013-01-18
> **HunterDX77M said:**
> I've Googled around and everyone's knee-jerk response has been to *remove Java*.

The exploit is java **applets** in **web browsers**. Mostly focused on older implementations on some web sites.

If you like, you can *disable* java **applets** in your web browser* :)*

---

### Post by Soul-Sing on 2013-01-18
disable the webbrowser plugin, via add-ons, etc.
The amercican govern. has calls for these measures.
Java is also the base of the popular game Minecraft,
(Whats in a name.)and few webpages.

To secure javascript, which has its own security difficulties, use no-script.

---

### Post by Ender Shadow on 2013-01-18
I would like to remove Java, but like Soul-Sing said, Minecraft uses Java as it's game engine. Hopefully this issue with Java will convince Mojang to use something other than Java.

---

### Post by Hungry Man on 2013-01-18
Mojang won't stop using Java. But I suggest you disable the Java web plugin in your browser.

---

### Post by Ms. Daisy on 2013-01-18
> **HunterDX77M said:**
> **My question is as Ubuntu users, is there something specific we should do prevent any damage to our computers?** :confused:There's no good answer unless you don't need Java, in which case it's simple: totally uninstall Java and the browser plugins.  Then run away screaming.

If you need Java then unplug it from the browsers and only enable it when you absolutely need it.

---

### Post by MyTinFoilHat on 2013-01-19
> **Ms. Daisy said:**
> There's no good answer unless you don't need Java, in which case it's simple: totally uninstall Java and the browser plugins.  Then run away screaming.

If you need Java then unplug it from the browsers and only enable it when you absolutely need it.

 This (along with a few other responses) really clarified things for me. I'm sure you can appreciate that someone less familiar, who understands there's a potential security issue related to a java-something, wants to minimize their risk of exposure.  For now, I've removed (and purged) Java via Synaptic and disabled Firefox's java capabilities. Unforunately, doing that seems to goof up my ability to create new posts on (for example) Identi.ca. ...Nothing that can't be worked around, I suppose.  TYVM!

---

### Post by Soul-Sing on 2013-01-20
Then use Quickjava. A firefox add-on. You'r able to block/unblock java and javascript with a click.

---

### Post by palloy on 2013-01-22
My situation is similar to the original questioner.
Update was saying it wanted to update OpenJDK, so I went into Software Centre and removed it. It is now not flagged as installed. I unchecked the updates, and re-checked for updates, and they were still required.  Rebooted. Update still wants to update openJDK. Software Centre says I haven't got it installed.

What next ?

---

### Post by Ms. Daisy on 2013-01-23
If you want it entirely removed from your computer then type
```
sudo apt-get remove --purge openJDK
```

---

### Post by palloy on 2013-01-23
That gave: "E: Unable to locate package openJDK", but it must have cleaned up some loose ends because Update is now clear. Thanks.

---

