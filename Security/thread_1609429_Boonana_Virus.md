---
title: "Boonana Virus"
date: 2010-10-30
forum: Security
---

### Post by lamadredelsapo on 2010-10-30
Check out [_this one_]("http://www.tgdaily.com/security-features/52266-video-boonana-pwns-and-owns-three-operating-systems?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+tgdaily_all_sections+%28TG+Daily+-+All+News%29"), it turns out that Ubuntu is also being targeted by viruses...

---

### Post by viralmeme on 2010-10-30
> **lamadredelsapo said:**
> .. it turns out that Ubuntu is also being targeted by viruses...

"*Whether you are running Windows, Mac OS X or Linux on your computer, if you **give permission** for the highly obfuscated **Java app** to **run** then the malware will sneakily download a variety of programs from the internet which it will then **execute on your computer***"

Where do I click to get infected by this Linux virus ?

---

### Post by OpSecShellshock on 2010-10-30
> **viralmeme said:**
> "*Whether you are running Windows, Mac OS X or Linux on your computer, if you **give permission** for the highly obfuscated **Java app** to **run** then the malware will sneakily download a variety of programs from the internet which it will then **execute on your computer***"

Where do I click to get infected by this Linux virus ?

If you follow the link from the nice stranger on the internet, it will take you to a fake video site where there will be a thumbnail image. You click that because that's what the video site says to do in order to view it, and then a message comes up that doesn't even match your window theme, and it asks if you'd like to run the mystery unsigned applet. At the bottom of the page there's a handy guide that says if you get a pop-up message you should click "Run" which, again, must be perfectly harmless. So you click Run and allow the Java applet, and if you've got the lucky vulnerable version of Java then you too can get the big scary Linux malware (until the next time you shut down your system). I know it sounds like a lot of work, but evidently it calls our entire threat model into question. Just goes to show that if you really try hard, you too can get web-based malware.

---

### Post by viralmeme on 2010-10-30
> **OpSecShellshock said:**
> If you follow the link from the nice stranger on the internet ..

I'd much prefer for you to provide me a **direct link**. What exactly does "*downloading files onto your computer which it's then going to run*" mean. Does it run executables that alter system files without prompting for root access, if not then this report is totally bogus. Whay are you posting free adverts for Sophos here ?

---

### Post by OpSecShellshock on 2010-10-30
> **viralmeme said:**
> I'd much prefer for you to provide me a **direct link**. What exactly does "*downloading files onto your computer which it's then going to run*" mean. Does it run executables that alter system files without prompting for root access, if not then this report is totally bogus. Whay are you posting free adverts for Sophos here ?

It means exactly what it says. Consenting to run the Java applet, if you have the vulnerable version, will download and run further scripts. It doesn't do anything that involves privilege elevation. It just drops files into a user's home directory and runs them as the user. When the system is restarted, the malware stops and will not start back up. This is the second thread on the topic in this forum.

It will not run or execute without the user telling it to. Even if it does, it won't install anything outside of the home directory and will not persist across desktop sessions.

Not sure what you meant about Sophos advertisements. I've never used their software, though I do read their analysts' blog from time to time. The Linux version of this particular worm wouldn't be detected by any AV software anyway, but as I said, you'd have to get infected on purpose in order for it to really work.

The reason that not a lot of news reports are going into great detail about this is that, if they did, then it wouldn't sound as scary (because it isn't). They focus on the fact that it affects Linux systems (because Java is cross-platform) and not on what it takes to get it in the first place or how little actual damage it does.

---

### Post by movieman on 2010-10-30
> **OpSecShellshock said:**
> I know it sounds like a lot of work, but evidently it calls our entire threat model into question.

Running random software from the internet can infect your PC, shock! Full story at 11!

Seriously, this is another crappy trojan of the kind that has been around for decades, and it's only a problem because it's written in a managed language rather than native code so it can run on anything that supports Java and has the holes it wants to exploit.

The only real lesson is that Java should always be disabled in the default install of a web-browser; if you really need it you can enable it yourself.

---

### Post by HermanAB on 2010-10-30
Yup, and if you go to mirrors.kernel.org, then you can download this thing called Ooboontoo Linux and if you follow all the instructions carefully then you can completely overwrite your whole compooter system. It is a jungle out there...

---

### Post by mainerror on 2010-10-30
> **movieman said:**
> Running random software from the internet can infect your PC, shock! Full story at 11!

Seriously, this is another crappy trojan of the kind that has been around for decades, and it's only a problem because it's written in a managed language rather than native code so it can run on anything that supports Java and has the holes it wants to exploit.

The only real lesson is that Java should always be disabled in the default install of a web-browser; if you really need it you can enable it yourself.

Actually it only shows that you have to update your software regularly to keep your system secure which is nothing new either.

That hole only exists in older versions of Java. Update regularly, worry less.

---

### Post by movieman on 2010-10-30
> **mainerror said:**
> That hole only exists in older versions of Java. Update regularly, worry less.

But the hole exists in Java, which hardly anyone actually needs in a web browser. I do use it sometimes at work for web-based applications, but I haven't needed to run a Java applet on the web at home for years.

If you don't install the plugin, holes don't matter, because they can't be exploited. The less code you have able to access the web from your browser, the lower the impact of any such holes will be.

---

### Post by ubunterooster on 2010-10-30
This is not a linux virus, or even linux malware. It is _***JAVA***_ malware. Again the problem is not the OS, but rather the plugins

---

### Post by ankspo71 on 2010-10-31
Hi,
This serves as a reminder of why it is important that we do not attempt to login as the root user, or run applications as root (sudo) that don't need to be run as root (especially web browsers and email clients etc). I personally think this virus/malware was worth mentioning here because there are increasing numbers of new/unsuspecting Linux users using Ubuntu, and just as many Ubuntu users using Facebook and Java.

Not only that, but some of the other major Linux distributions still allow logging in as the root user. :confused:

---

### Post by lisati on 2010-10-31
But is it really a virus? Does it reproduce itself?

---

### Post by OpSecShellshock on 2010-10-31
> **lisati said:**
> But is it really a virus? Does it reproduce itself?

I believe that technically it's both a trojan and a worm.

---

### Post by Googleler on 2010-11-01
This type of virus affects the Windows based computer of my sister. I think this is possible just because the Java is not updated. 

If you have the latest version installed, you have no problem with this threat. :)

---

