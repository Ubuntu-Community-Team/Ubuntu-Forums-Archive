---
title: "ADvise on cross-platform app needed"
date: 2011-08-17
forum: The Cafe
---

### Post by Zlatan on 2011-08-17
Hello, I want to distribute some cross-platform customized scheduler with couple of inputs when set up- application. I want it to work in linux, Mac, Windows, Android, iOS- to be REALLY cross-platform. And to be easily synced with Google Calendar and similar.
What language should be this app written on? Should it be JAVA?
Please advise, thank you

---

### Post by aeiah on 2011-08-17
probably java. you won't be able to just compile for every platform without changing anything, but you'll be able to easily keep most of your methods.

---

### Post by RichardLinx on 2011-08-17
Do you know Java?

---

### Post by Zlatan on 2011-08-18
> **RichardLinx said:**
> Do you know Java?

I am not any kind of developer but I have connections and ability to hire;) Why?

---

### Post by 3rdalbum on 2011-08-18
Java is completely useless on iOS, and you'd need to heavily modify the program to make it run on Android. You couldn't use Swing for the UI.

The only language that's cross-platform enough for your purposes is AJAX (which is a combination of HTML, Javascript and a server backend using PHP, ASP or something else).

---

### Post by forrestcupp on 2011-08-18
You're going to have to write different clients for different devices. Android uses Java and the Android SDK, iOS uses Objective C, and the desktop OSs can use whatever you want (I think Objective C is only for Apple products). You'll probably be able to reuse most of your code logic, but you'll have to actually write at least 3 different sets of code.

Using the right libraries, you can write cross-platform code for Linux, Windows, and Mac, but when you throw in different portable devices, you'll have to write separate clients for them.

---

### Post by fouserge on 2011-08-18
I would go with developing a web-application as some one noted above using AJAX/HTML/Javascript and a server scripting language such as PHP or even Java.

Then after you have created this which will run on all OSes with a web-browser. You can try to make native apps for Android/iOS that can integrate well with it.

You then may or may not really even need to integrate with Google Calender. But if you want you could even look into using Google App environment. Which again you can use Java to create a web app that runs on a Google or your own independent server and will share user data with Google and all apps made by Google. Meaning you can also get access to users info from other apps like Calender (sharing back and forth).

---

### Post by forrestcupp on 2011-08-18
> **fouserge said:**
> 
Then after you have created this which will run on all OSes with a web-browser. You can try to make native apps for Android/iOS that can integrate well with it.

Just make sure you don't stop with the web browser app and think that's good enough. Having to access things through a web browser on an Android or iOS device sucks. I'd be much more likely to use something that has a native app.

---

### Post by GeneralZod on 2011-08-18
Qt & C++ can be used on all four platforms, though Android and iOS are community-supported and may not yet be entirely complete (for example, iOS QWidget support is mentioned as being untested, though as the developers mention, QML may be a better match for handset-sized devices, anyway).

iOS: [http://labs.qt.nokia.com/2011/08/09/update-on-uikit-lighthouse-platform/](http://labs.qt.nokia.com/2011/08/09/update-on-uikit-lighthouse-platform/)

Android: [http://sourceforge.net/p/necessitas/home/necessitas/](http://sourceforge.net/p/necessitas/home/necessitas/)

Qt includes QtNetwork for network-handling, though I don't know how well supported it (currently) is for e.g. iOS.

---

### Post by sanderd17 on 2011-08-18
Most programming languages like Java and objective C provide you some tools to make your own customised borwser. Your app probably doesn't need an address bar or forward/backward buttons.

So if you have this, and you have your web code, than you have something that looks like a native app but isn't one.

What you could do too is make a different interface for all platforms, but keep the same libraries. I know for example that Navit is written in C, but there are GUIs for Android and iOS too. This will only work when your libraries are the most important part of your app. Otherwise it's not worth to separate them

---

### Post by zekopeko on 2011-08-18
Mono is the only platform (sans HTML,JS,CSS) that I know of which works on all those systems. The UI will have to be different but the core logic would be shared by all of them.

The problem is that products for iOS and Android are not free of charge (something like $400).

---

### Post by Thewhistlingwind on 2011-08-18
I would have said python or java, but when you throw stuff like mobile into the mix, your going to need at least two codebases. 

Java should work (With some modifications maybe.) on Windows, Mac, and Linux. (And anything which supports a java VM.) Java will need modifications to work on android I'm sure, and iOS doesn't use java.

You may want to revise your strategy.

Also, to the person posting above, wheres the fee to publish on android market? i can't find it on their website.

---

### Post by sanderd17 on 2011-08-18
> **Thewhistlingwind said:**
> 

Also, to the person posting above, wheres the fee to publish on android market? i can't find it on their website.

A one time $25 subscription fee: [https://market.android.com/publish/signup](https://market.android.com/publish/signup) + 30% of the price of the apps you sell.

iOS and win7 are a lot more expensive. But Google can't force that price because you can install applications from other places than the market.

---

### Post by fouserge on 2011-08-18
> **Thewhistlingwind said:**
> 
Also, to the person posting above, wheres the fee to publish on android market? i can't find it on their website.

Publishing to the Android Market costs a one time fee of US$25 and to Apple it is I believe US$99 a year.

[https://market.android.com/publish](https://market.android.com/publish)

and don't remember where Apple tells their pricing.

---

### Post by juancarlospaco on 2011-08-18
**html5**

---

### Post by forrestcupp on 2011-08-18
> **GeneralZod said:**
> Qt & C++ can be used on all four platforms, though Android and iOS are community-supported and may not yet be entirely complete (for example, iOS QWidget support is mentioned as being untested, though as the developers mention, QML may be a better match for handset-sized devices, anyway).

iOS: [http://labs.qt.nokia.com/2011/08/09/update-on-uikit-lighthouse-platform/](http://labs.qt.nokia.com/2011/08/09/update-on-uikit-lighthouse-platform/)

Android: [http://sourceforge.net/p/necessitas/home/necessitas/](http://sourceforge.net/p/necessitas/home/necessitas/)

Qt includes QtNetwork for network-handling, though I don't know how well supported it (currently) is for e.g. iOS.I wonder if an app programmed that way for Android and iOS will run as fast and smoothly as programming it natively. I also wonder if the widgets look native. If it doesn't look native, I wouldn't want it, but if it does, this could be interesting.

> **sanderd17 said:**
> 
iOS and win7 are a lot more expensive. But Google can't force that price because you can install applications from other places than the market.True, but your odds are *a lot* better that more people will find your app if it's in the market.

---

### Post by Matpen on 2011-11-04
Qt is, in my opinion, the way to go. Runs on a vast variety of platforms, included the ones you mentioned. Also, it is the only way to get binaries that run natively on the platform. Compared to Java, python and others that run intermediate code on a virtual machine you get much more performance.

---

### Post by sanderd17 on 2011-11-05
> **Matpen said:**
> Qt is, in my opinion, the way to go. Runs on a vast variety of platforms, included the ones you mentioned. Also, it is the only way to get binaries that run natively on the platform. Compared to Java, python and others that run intermediate code on a virtual machine you get much more performance.

You do know this post is rather old. 

Qt can work on all popular desktop platforms, but if you want to run it on a phone platform, you might be lucky you can re-use the libraries (in Android), but you will certainly have to re-code a graphical interface for that platform.

---

### Post by Zlatan on 2011-11-06
> **sanderd17 said:**
> You do know this post is rather old. 

Qt can work on all popular desktop platforms, but if you want to run it on a phone platform, you might be lucky you can re-use the libraries (in Android), but you will certainly have to re-code a graphical interface for that platform.

Hi, post idea is delayed but still interesting:) No problem with posting ideas;)

---

### Post by kvvv on 2011-11-06
html5 css javascript.

Not sure how well that would work on iOS though.

---

