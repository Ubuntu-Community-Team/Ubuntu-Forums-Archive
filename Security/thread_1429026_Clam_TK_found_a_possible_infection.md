---
title: "Clam TK found a possible infection"
date: 2010-03-13
forum: Security
---

### Post by Chris_cur on 2010-03-13
I just ran into my first possible virus in Ubuntu with Clam TK. It is in my Mozilla Firefox Cache. Status is: "PUA.Script.Packed-1"
What does this mean?
Quarantine or delete this?

---

### Post by Frogs Hair on 2010-03-13
Hi,

PUA : Private Use Area -( Unicode Context ) I don't know if it's a threat.
PUA : Possibly Unwanted Application   Klam states that  it is a false positve.

See [http://clamav.net/sendviruses.cqt](http://clamav.net/sendviruses.cqt)

---

### Post by 2hot6ft2 on 2010-03-13
> **Chris_cur said:**
> I just ran into my first possible virus in Ubuntu with Clam TK. It is in my Mozilla Firefox Cache. Status is: "PUA.Script.Packed-1"
What does this mean?
Quarantine or delete this?
Going to Edit > Preferences > Advanced tab > Network tab
and clicking on Clear Now under Offline Storage in firefox will clear your offline content and should get rid of it. I think that's how you clear the cache.

It's not like it can do anything in ubuntu anyway if it is something you got while browsing the web.

---

### Post by mikewhatever on 2010-03-13
PUA = Potentially Unwanted Application. The name and location you posted indicate it is a script, which has nothing to do with virus infection. Just empty Firefox's cache and it's gone, and if you are worried about scripting, turn off java scripts in Firefox.

---

### Post by MarkC502 on 2010-03-13
Plus it would be a virus targeted towards a Windows box anyway. I am not aware of any Linux based malware definitions in the Clam AV database ( jump in anyone if you know otherwise ). Also the PUA while that is potentialy unwanted Ap, the script packed usually means it was packed using something which causes AV alerts due to the method used to package the software for install. Hundreds of small developers get the laughable "you gave my PC a virus email" simply because they decide to use a packer to build their install.

Rest easy,

Mark

---

### Post by OpSecShellshock on 2010-03-13
Packers get used in a couple of different ways. Some use it everywhere, to obscure their source code and things. This is not necessarily malicious, but it does suggest that not having people be able to read (and presumably copy?) the code is more important to the author than letting end users examine it to see what it does. The other major use is to hide the commands in a web-based script from network based security tools that might otherwise block it before it gets where it's going. That's obviously not something that someone on the up-and-up would do. However, since it is packed, there's no way to determine which type it is, so AV software vendors prefer to err on the side of caution. In this case, if it's malicious it would likely only affect Windows, and at this point won't get out of the cache anyway. If it's not malicious, it was obviously not necessary, either, because you didn't miss out on anything for not running it.

If you want, you can always follow the path and check the file name when these detections come up. There might be some kind of identifier that can tell you where it came from, and you can judge its intentions that way.

---

### Post by Chris_cur on 2010-03-13
Thanks every one! I knew it would probably not effect Ubuntu, I was just so shocked.  Your information was great!

@mikewhatever: I love your Linux is NOT Windows link! I am reading it now. I never bought Legos for the figurative "car inside", or if I did I quickly decided I didn't like the Yugo I bought and built a Ferrari!! mwahahaha

---

