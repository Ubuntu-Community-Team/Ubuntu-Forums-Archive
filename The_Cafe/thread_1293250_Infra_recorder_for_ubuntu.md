---
title: "Infra recorder for ubuntu?"
date: 2009-10-16
forum: The Cafe
---

### Post by sudoer541 on 2009-10-16
[Infra recorder]("http://en.wikipedia.org/wiki/Infra_Recorder") is open source, why it isn't available for ubuntu?

---

### Post by Grant A. on 2009-10-16
Why would you want it? Ubuntu has a CD burning software installed by default. It's called Brasero.

I guess if you did want it on Linux, you could try some hacking. After all, that's the beauty of Open Source, is it not? :)

---

### Post by Sam on 2009-10-16
> **sudoer541 said:**
> [Infra recorder]("http://en.wikipedia.org/wiki/Infra_Recorder") is open source, why it isn't available for ubuntu?

Open source &#8800; cross platform

---

### Post by NoaHall on 2009-10-16
> **Sam said:**
> Open source &#8800; cross platform

Ah, but Open Source = Open Source = Code anyone can freely use and edit = a lot easier for someone to transfer to another OS.

---

### Post by Vostrocity on 2009-10-16
Infra was my disc burner of choice back in the Windows days. I haven't tried Brasero yet on Linux but I have no doubt it's just fine. Disc burners are just disc burners, you can't really go wrong. People always complain when an open-source software isn't on Linux, but open-source software can be completely developed and run on a closed-source OS, Paint.NET for example.

---

### Post by sudoer541 on 2009-10-16
to: UF staff

would you please move this thread to the [packaging and compiling section]("http://ubuntuforums.org/forumdisplay.php?f=44")? I just realized that some people can package it! 

Merci:)

---

### Post by HappyFeet on 2009-10-16
I got it to install via wine, but it said I did not have a cd burner. Close though.

---

### Post by doorknob60 on 2009-10-16
Well, nobody's bothered to port it since programs like K3B and Brasero are just as good or better. K3B is great :)

---

### Post by Xbehave on 2009-10-16
Because it does not run on linux! The APIs for burning discs are soo different under linux than under windows that a port would be a pretty major rewrite, and tools like k3b already exist that interact with the linux API.

---

### Post by SunnyRabbiera on 2009-10-17
we got plenty of apps for disk burning, why not use them?

---

### Post by ad_267 on 2009-10-17
> **sudoer541 said:**
> to: UF staff

would you please move this thread to the [packaging and compiling section]("http://ubuntuforums.org/forumdisplay.php?f=44")? I just realized that some people can package it! 

Merci:)

No, people can't package it.

Just because there's source code doesn't mean it can easily be ported to Linux. If that was the case then there would be a lot more commercial software available for Linux. It's likely that Infra Recorder depends on a lot of Windows specific libraries.

---

### Post by ZuLuuuuuu on 2009-10-17
> **Grant A. said:**
> Why would you want it? Ubuntu has a CD burning software installed by default. It's called Brasero.

So, there is an app that you like and everybody should like IT, and not another app? Brasero is a very good application and I like it, too but it does not mean everybody should use it.

I like InfraRecorder very much too and use it when I'm under Windows. But it is coded using Windows API, as far as I know, even for the GUI part -not mentioning about disc burning part which is different for sure and would most probably be harder to port-. So, porting it to Linux means an almost complete rewrite and you have to look for alternatives in this case like Brasero or K3B.

I think, sometimes it is good for a program to be platform dependent. For example, InfraRecorder or Brasero might have been not as good or as stable as they currently are if they would have tried to be cross-platform which would require an enormous additional work.

---

### Post by koleoptero on 2009-10-17
K3b can make infra recorder look like a retarded distant cousin. More effort should go towards developing existing disk burning solutions than porting more from windows to linux.

---

### Post by sudoer541 on 2009-10-17
Non of the other burning software work well. I only found the demo of Nero-Linux 4 doing a good job. I guess I am gonna buy it when its available on the software store. 
I have one question, if I have the windows version of Nero along with my product key, will the product key work on the Linux version of Nero as well?

---

### Post by Xbehave on 2009-10-19
> **sudoer541 said:**
> Non of the other burning software work well. I only found the demo of Nero-Linux 4 doing a good job. I guess I am gonna buy it when its available on the software store. 
I have one question, if I have the windows version of Nero along with my product key, will the product key work on the Linux version of Nero as well?
I really suggest you get the alternatives fixed, k3b, etc work for most people and when they work, most people think they are damn good tools. The  burning API is completely different in linux so if infra recorder ever does get ported it will use the same tools wodim, etc, as k3b so if k3b doesn't work neither will infra recorder. What is your particular problem?

---

### Post by koenn on 2009-10-19
> **sudoer541 said:**
> Non of the other burning software work well. I only found the demo of Nero-Linux 4 doing a good job. I guess I am gonna buy it when its available on the software store. 
I have one question, if I have the windows version of Nero along with my product key, will the product key work on the Linux version of Nero as well?
You'll have yo check that with the vendor, or read the license, terms and conditions, etc.

or use free sofware and be done with all that hassle :)

---

