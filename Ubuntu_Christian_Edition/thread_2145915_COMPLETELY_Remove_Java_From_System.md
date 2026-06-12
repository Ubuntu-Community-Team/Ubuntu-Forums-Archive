---
title: "COMPLETELY Remove Java From System"
date: 2013-05-16
forum: Ubuntu Christian Edition
---

### Post by parkernathan on 2013-05-16
How can I **completely** remove Java from a UCE system? I need to completely remove it from a system for security reasons.

Thanks!

---

### Post by tgalati4 on 2013-05-16
Open a terminal:

```
dpkg --list | grep Java
dpkg --list | grep Java > list_of_java_packages.txt
```

That will give you a starting point.   I would expect some breakage because Java is extensively embedded throughout the Ubuntu operating system.

---

### Post by QIII on 2013-05-16
May I ask what security reasons?

---

### Post by parkernathan on 2013-05-16
> **tgalati4 said:**
> Open a terminal:

```
dpkg --list | grep Java
dpkg --list | grep Java > list_of_java_packages.txt
```

That will give you a starting point.   I would expect some breakage because Java is extensively embedded throughout the Ubuntu operating system.

OK great then just remove the ones I need through the Software Center or Terminal?

---

### Post by parkernathan on 2013-05-16
> **QIII said:**
> May I ask what security reasons?

I've been seeing bad reports of vulnerabilities with Java, so I try to stay away from it as much as possible. I'm sure the media is overhyped, but unless I install apps that are critically in need of Java, I'd rather remove it until I need it. Just one less thing to have to worry about.

---

### Post by tgalati4 on 2013-05-20
I use *noscript* as an add-on in Firefox and that allows to you selectively turn on Javascript for websites that you need to have access to.  That will give you perhaps 80% of the security that you need from web-browsing, Java exploits.  Another 10% improvement will come from keeping Java updated as vulnerabilities get patched and pushed to your computer through normal updates.  Simply removing all Java packages will probably cause you more grief than you expect, since a lot of applications rely on Java to function properly.

The only way to guarantee security on your system is to disconnect it from the internet.  But if you remain connected to the internet, and you use the Web on a daily basis, then Java is required for the correct operation of many, many websites.  It is a compromise and one has to weigh the risks.

---

### Post by QIII on 2013-05-20
I don't think it's necessary to remove Java completely.

The recent exploits you have read about, which are terrible and Oracle probably needs to do a ground-up refactoring of the entire stack, depend on gaining access via the Java browser plugin, which can be disabled.

You may have desktop applications that depend on Oracle Java 7 or OpenJDK 7, in which case you might run into difficulties.  Perhaps not.  I'd say it's a fair bet you would, though.

As far as the web goes, there are fewer and fewer sites that use Java, and that has decreased sharply since the latest round of exploits.  Just disable the browser unless you need it for a trusted site and then disable it again when you are done.

By the way, javascript is not Java.  ;)

---

### Post by parkernathan on 2013-05-22
Hi everyone,

Yeah, for the record, JavaScript and Java are two totally different things. Most websites these days rely on JavaScript for something to work, whereas while some web apps relied on Java to work in the past, fewer websites use Java nowadays.

As for JavaScript, I've used noscript before, but it was a pain to use. I felt like I couldn't even breathe on the web at all. Usually I haven't experienced any major security vulnerabilities with JavaScript. That's not to say that none exist (I'm sure they do), but JavaScript isn't a large enough threat to me to entirely block it. I'd rather just keep my browser updated with the latest security updates.

As for Java, in the past I used a good bit of Linux apps that required Java, but lately it hasn't been the case. The majority of the apps I run are native code or removing Java doesn't break anything critical in the apps I'd need to use on a daily basis. In the past, this wasn't the case, but nowadays, it seems I can get by without Java on a day-to-day workflow. While the security vulnerabilities surrounding Java are probably overhyped, since I'm not really using it right now, I'd rather just remove it so it's one less vulnerability to have to worry about. If I get to the point where an app I use on a regular basis requires Java, I can re-install Java and go back to keeping it updated regularly with security updates.

Ever since Oracle took over Java, they've really made a mess of things, just like Abode and the acquisition of Macromedia.

Speaking of Adobe, I'm using a slightly similar route with Flash. Abode is slowing phasing out future major releases of Flash for FireFox, so I'm probably just going to pull Flash from FireFox and use the built-in Flash plugin inside Chrome instead. There are some websites I need to access Flash in, but I'd rather use Chrome for those (since they update Flash automatically), and just use FireFox for the regular sites I browse (since more and more are going HTML5).

Coupled with Linux's already secure underpinnings, dansguardian, and ClamAV on board, I should have a "pretty secure" system. Nothing's totally immune, but it's as good as I can probably get.

---

### Post by jonathonblake on 2013-05-24
> **tgalati4 said:**
> I use *noscript* as an add-on in Firefox and that allows to you selectively turn on Javascript for websites that you need to have access to.

Java and Javascript are two very different languages, with very different security flaws.

>   That will give you perhaps 80% of the security that you need from web-browsing, Java exploits. 

NoScript will not block the most effective Java exploits. 

jonathon

---

### Post by jonathonblake on 2013-05-24
> **parkernathan said:**
> Coupled with Linux's already secure underpinnings, dansguardian, and ClamAV on board, I should have a "pretty secure" system. Nothing's totally immune, but it's as good as I can probably get.

The most common exploits that work rely on social engineering.   

jonathon

---

