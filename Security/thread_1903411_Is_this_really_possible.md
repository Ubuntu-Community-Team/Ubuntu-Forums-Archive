---
title: "Is this really possible?"
date: 2012-01-02
forum: Security
---

### Post by scruffyeagle on 2012-01-02
I found a video on YouTube titled "Anonymous Hacker Group Fawkes Security' Unveils The 'Legion Exploit Kit'" The dialogue in the video claims that a group of hackers has developed & is distributing an exploit kit that can easily infect Linux systems (as well as Windows). I have 2 question after watching this:

1) Is this is true? Can hackers really use this software to hack into any Linux system they choose? and,

2) If it's true, is there any way to defend against it?

[http://www.youtube.com/watch?feature=endscreen&NR=1&v=9Z3zXIYhpZA](http://www.youtube.com/watch?feature=endscreen&NR=1&v=9Z3zXIYhpZA)

---

### Post by DS McGuire on 2012-01-02
Can somebody give me a transcript or something of that video I can't sit here and listen to that...
Anyway, Anonymous are all talk IMO and with all the eyes on the code on Linux I highly doubt anything like like what you are saying will get through...as for windows I'm not sure :L

---

### Post by Dangertux on 2012-01-02
Hmm... That's propaganda. I'll explain why in a minute. However, to answer your question yes it is possible to compromise a poorly secured Linux system. It's as trivial as compromising any other poorly secured system.

Now on to why it's propaganda, notice how I repeatedly said poorly secured? The reason is, you can't just make some magical software to exploit some vulnerability and it just works on EVERYTHING. No individual or group can just say, oh I'm going to target this person. Whip out a pre-made program and break in just like that *snaps fingers*. The caveat to that being, if said person or organization which was targeted has not performed system updates in a year and is vulnerable to pre-made exploit code. Automation only goes so far in this case. Some leg work will need to be done if they wanted to target a hardened infrastructure, there is no magic bullet exploit, just like there is no magic bullet security solution.

Here's another problem with that cute little message. It's crap, there is absolutely nothing new there.  They talked about a few key points, in their rant let's move through them and discuss what they are actually saying. 

- Exploit Command and Control : They explain a very typical exploit framework that if injected into a compromised site redirects traffic to the appropriate exploit code. This assumes the system is vulnerable, it would be unlikely the C&C server could profile a system in depth enough to confirm that the exploit code would work without opening their own C&C server to a considerable attack.

(for instance using system or passthru to run nessus or nmap against the target)

This has been seen for a while, it wreaks of blackhole to be honest. The little comment about AV was completely pointless.

- IFRAME injection, congratulations this doesn't need discussion, it's been around...Well since IFRAMEs have been around.

- PHP obfuscation, blah boring. Been around for a while as well.

- Javascript packing, again been around. They may have a unique algorithm which will eventually be reverse engineered, as they all are.

- Java application exploitation - it's 2012 guys... And yes this still works.

Now let's talk about this Trojan...

Pretty typical in terms of what trojans do, clearly it's probably polymorphic and self encoding based on the nice description they provided. Most AV vendors have caught on to these techniques recently as they've been beaten to death by TDSS and Zeus at this point.


None of this stuff is special, can linux be compromsied yes... With the caveats above. Is this exploit tool kit anything amazing? No... As always I'm left disappointed in Anon.

---

### Post by Ms. Daisy on 2012-01-02
Yes, any operating system can be cracked.  That point is totally non debatable. 

If you want to secure your system, the best approach is a layered one.  That means you use several security measures and you don't rely on only one.  

The [basic security wiki]("https://wiki.ubuntu.com/BasicSecurity") will get you started on securing Ubuntu if you're a new desktop user.  I also recommend you review the [security sticky]("http://ubuntuforums.org/showthread.php?t=510812").

---

### Post by Dangertux on 2012-01-02
Oh in case I didn't mention it in my last post... That nice little redirect process and payload injection process. NoScript pretty much makes it impossible for it to ever succeed, unless of course you just allow EVERYTHING. Hope this helps.

---

### Post by scruffyeagle on 2012-01-02
> **Dangertux said:**
> Oh in case I didn't mention it in my last post... That nice little redirect process and payload injection process. NoScript pretty much makes it impossible for it to ever succeed, unless of course you just allow EVERYTHING. Hope this helps.

Dangertux: Thank you very much for your detailed replies. I feel less apprehensive about this now. And yes, I use NoScript & never allow everything.

Ms. Daisy: Thank you for your suggestions and links. I'm fairly sure I've read that stuff before, but it seems that I should go back & read it again.

---

### Post by 0011235813 on 2012-01-08
I've heard of theoretical ways to compromise a system by embedding malware on media files, but no actual viruses that actually do that as far as i know... So basically any malware needs to be some type of executable. If JS is disabled, that can't work. Furthermore, let's not forget that a browser exploitation in FF might not work on say, Chromium. So if the user is using a different browser.... 
The only other way would be to make the user install an application, which would be a little hard to do with smart Linux users. 
Same rules still apply, paranoia. Pure paranoia. Even vanilla Linux is secure; never mind any other changes you might make.

---

