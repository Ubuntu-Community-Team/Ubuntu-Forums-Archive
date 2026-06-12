---
title: "Cross Platform Trojan - Should Linux users be worried?"
date: 2012-07-12
forum: Security
---

### Post by Shadius on 2012-07-12
Hey everybody! :)

I came across this [article]("http://www.zdnet.com/cross-platform-trojan-checks-your-os-attacks-windows-mac-linux-7000000656/") about a cross-platform trojan that checks what OS a user has then downloads the malware depending on what OS it detects. Should this be a concern for us Ubuntu/Linux users?

---

### Post by Hungry Man on 2012-07-12
It uses the Social Engineering Toolkit and it's based no a Jar file. Jar files are Java and can run on any OS that has a Java Virtual Machine (OpenJDK, Oracle JDK, etc) so that's why it runs on Linux.

As you may have guessed the Social Engineering Toolkit (SET) tries to trick you into running the file. If you don't run it you're fine.

You can also run Java in an AppArmor profile, which I suggest. This way even if you run the .jar it will be limited to the AA profile.

---

### Post by Shadius on 2012-07-12
Interesting. What is AppArmor? Also, how can I check if Java is installed on my system? I think I installed Java on my system when I was on the NVIDIA site.

---

### Post by Hungry Man on 2012-07-12
You can check if you have Java installed here:
[https://www.java.com/en/download/installed.jsp](https://www.java.com/en/download/installed.jsp)

I wrote about AppArmor here:
[https://insanitybit.wordpress.com/2012/05/29/apparmor-how-to/](https://insanitybit.wordpress.com/2012/05/29/apparmor-how-to/)

---

### Post by Shadius on 2012-07-12
> **Hungry Man said:**
> You can check if you have Java installed here:
[https://www.java.com/en/download/installed.jsp](https://www.java.com/en/download/installed.jsp)

I wrote about AppArmor here:
[https://insanitybit.wordpress.com/2012/05/29/apparmor-how-to/](https://insanitybit.wordpress.com/2012/05/29/apparmor-how-to/)

Thanks. It appears that I have Version 7 Update 3 and an update to Version 7 Update 5 is available. Do you recommend I update? I don't even know what Java is used for. Do I even need this?

---

### Post by samiux on 2012-07-13
> **Shadius said:**
> Hey everybody! :)

I came across this [article]("http://www.zdnet.com/cross-platform-trojan-checks-your-os-attacks-windows-mac-linux-7000000656/") about a cross-platform trojan that checks what OS a user has then downloads the malware depending on what OS it detects. Should this be a concern for us Ubuntu/Linux users?

[The demo is here.]("http://www.youtube.com/watch?feature=player_embedded&v=Q3DQ_WdnqVE")

Samiux

---

### Post by ranger1021994 on 2012-07-13
No..because he main filesystem is under root control so even if the malware tries to modify the system partition,ubuntu will prompt the user to authenticate the action.
Update to latest versions of Java since they may contain various bugfixes and security enhancements
:smile:

---

### Post by Hungry Man on 2012-07-13
> **Shadius said:**
> Thanks. It appears that I have Version 7 Update 3 and an update to Version 7 Update 5 is available. Do you recommend I update? I don't even know what Java is used for. Do I even need this?

If you don't know what Java is for I suggest you remove it. It's basically a giant gaping security hole.

---

### Post by samiux on 2012-07-13
> **ranger1021994 said:**
> No..because he main filesystem is under root control so even if the malware tries to modify the system partition,ubuntu will prompt the user to authenticate the action.
Update to latest versions of Java since they may contain various bugfixes and security enhancements
:smile:

[Local Privilege Escalation]("http://www.youtube.com/watch?v=Ia6OJAP-KS0") can get the root privilege.

Samiux

---

### Post by OpSecShellshock on 2012-07-13
If you don't need Java, just get rid of it. If there's something you do need it for (since a lot of other things apparently get developed using it as a framework), then at the very least disable it in the web browser.

In this specific case you will most likely be prompted to allow the malicious application to run. Just not doing that should work. 

Now the plain fact is, SE gets everyone eventually. Even professionals who are constantly anticipating it. Someone will find that perfect thing to entice folks into clicking what they shouldn't. So the fundamentals still apply: only enable the things you need, maintain your backups, and be ready to rebuild when there's trouble.

---

### Post by Hungry Man on 2012-07-13
> Now the plain fact is, SE gets everyone eventually. 
I could not agree more.

---

### Post by rookcifer on 2012-07-14
> **samiux said:**
> [The demo is here.]("http://www.youtube.com/watch?feature=player_embedded&v=Q3DQ_WdnqVE")

Samiux

I watched the video and went to the link where the malware was hosted.  I got no Java pop-up, so I suppose the site has been cleaned.

---

### Post by mike acker on 2012-07-14
> **ranger1021994 said:**
> No..because he main filesystem is under root control so even if the malware tries to modify the system partition,ubuntu will prompt the user to authenticate the action.
Update to latest versions of Java since they may contain various bugfixes and security enhancements
:smile:

I agree with this but with two notes
1. You should log on as an ordinary user except when you are servicing your system.  
2. the JAVA your browser is running can only update what your ordinary user can update so you might consider setting up a specially restricted user just for browsing.  Or set up a "BANKER" user that you only log onto when you visit sensitive sites.

Linux is so refreshing!!

---

