---
title: "Software center"
date: 2013-08-19
forum: Ubuntu, Linux and OS Chat
---

### Post by mJayk on 2013-08-19
Haya using 13.04 64 bit and its really really nice fast snappy and intuitive I've actually managed to remove my windows partition. I don't often used the software center but when I do I notice it seams really slow and sluggish (search loading pages etc). Any one else have this or is it just me. If so why?

Cheers

Matt

---

### Post by ian-weisser on 2013-08-19
Initial sluggishness is because it's loading the entire package cache. Big text database that has outgrown it's originally conceived scale.
Subsequent sluggishness (for me) is due to network activity - loading images and reviews.

---

### Post by lukeiamyourfather on 2013-08-19
If you know what you want you can just install it from a terminal very quickly, list multiple packages if you want more than one thing.

```
sudo apt-get install vlc htop p7zip
```

More on that can be found below. Much more efficient than using the "Software Center" in my opinion.

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

---

### Post by stalkingwolf on 2013-08-19
I have always found software center to be slow.  I much prefer synaptic.

---

### Post by buzzingrobot on 2013-08-19
Software Center certainly needs a rewrite.  It's often annoyingly sluggish.

There is no "software center" that the software called "Software Center" has exclusive rights to access. Synaptic, apt-get, etc., all pull from the same "repositories". if you manually add/delete a repository correctly, or use a program to do that, the change is reflected to all tools that manage software installation.

Synaptic is quite good, but without the pictures or the reviews.

---

### Post by ibjsb4 on 2013-08-19
[Synaptic]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9") is faster and quite versatile.

---

### Post by monkeybrain20122 on 2013-08-19
> **lukeiamyourfather said:**
> If you know what you want you can just install it from a terminal very quickly, list multiple packages if you want more than one thing.

```
sudo apt-get install vlc htop p7zip
```

More on that can be found below. Much more efficient than using the "Software Center" in my opinion.

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

Just one command is enough

```
sudo apt-get install synaptic
```

Problem with the command line only "much more efficient way" you recommend is that you have to know exactly the name of the package. I have seen people getting into problems by copying and pasting a bunch of sudo apt-get install because package names have changed, usually small variations like a version number of a suffix, but that is enough to frustrate many new users. synaptic also allow you do browse by categories when you don't know exactly what to install. It has all the advantages of the USC but a lot faster and allows much more fine grained control.

---

### Post by lukeiamyourfather on 2013-08-20
Sort of, you can use this command too.

```
apt-cache search player
```

It'll search packages based on the words given, then you can get package specific information with this command.

```
apt-cache show vlc
```

Synaptic works too. It's doing the exact same tasks in the background.

---

### Post by mJayk on 2013-08-21
I understand other installation methods as I said I dont use the software center alot I was just wondering if other users experience the slugishness.

Cheers
m

---

