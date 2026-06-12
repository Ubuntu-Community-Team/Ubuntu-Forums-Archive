---
title: "&quot;Locking&quot; my hard drive"
date: 2010-02-13
forum: Security
---

### Post by wersdaluv on 2010-02-13
I have a 500 gb external hard drive with tons of personal files on it. Other people at home just grab my hard drive whenever they need to transfer files. I feel so disrespected. I also want to protect myself from actually losing my hard drive to a stranger who will compromise my data.

I'm thinking of encrypting, but I'm currently too busy to explore (the options seem to be hard to use) and it seems to be too much to encrypt a 500gb hard drive

What are my options in "locking" my hard drive. I don't mind if it's going to be readable only on Ubuntu. That could actually be a plus :)

---

### Post by tubbygweilo on 2010-02-13
> I'm thinking of encrypting, but I'm currently too busy to explore (the options seem to be hard to use) and it seems to be too much to encrypt a 500gb hard drive
wersdaluv,
What value do you place upon your data?
How much time will it take to replace if your disk fails?
How much time will it take to restore your reputation if your innermost secrets are exposed to the world?
How much of your data is really secret or can not be easily replaced?

May I suggest that you audit your data held on the external drive so that you have an idea as to the amount held, which data is secret and needs to be kept from the eyes of others and the state of backed up data. It is only after an audit can the magnitude of the task be seen and the correct tools and procedures selected to solve your problem.

---

### Post by wersdaluv on 2010-02-13
> **tubbygweilo said:**
> wersdaluv,
What value do you place upon your data?
How much time will it take to replace if your disk fails?
How much time will it take to restore your reputation if your innermost secrets are exposed to the world?
How much of your data is really secret or can not be easily replaced?

May I suggest that you audit your data held on the external drive so that you have an idea as to the amount held, which data is secret and needs to be kept from the eyes of others and the state of backed up data. It is only after an audit can the magnitude of the task be seen and the correct tools and procedures selected to solve your problem.
Hello tubbygweilo.

I'm fine with the kind of security that can't be bypassed by the average computer user. My data isn't really top secret. I just don't want people to easily open all the files I archive whenever they have access to my hardware.

---

### Post by tubbygweilo on 2010-02-13
If you still wish to share the disk with others then encrypt your groups of folders/files with [truecrypt]("http://www.truecrypt.org/docs/") as this will keep all you encrypt private and allow others to use the space you have not encrypted.

---

### Post by Ceiber Boy on 2010-02-14
Truecrypt

---

### Post by cariboo on 2010-02-14
Lock it in a drawer when you aren't using it.

---

### Post by ubudog on 2010-02-14
+1 for truecrypt

---

### Post by ubudog on 2010-02-14
> **cariboo907 said:**
> Lock it in a drawer when you aren't using it.

The drawer could easily be busted open by a thief.

---

### Post by cariboo on 2010-02-14
The op is worried about other family members/house mates using the drive to transfer files, as well as theft. If the drive is locked away in a drawer, it is out of sight, out of mind.

---

### Post by ubudog on 2010-02-14
> **cariboo907 said:**
> The op is worried about other family members/house mates using the drive to transfer files, as well as theft. If the drive is locked away in a drawer, it is out of sight, out of mind.

True.

---

### Post by Lucky. on 2010-02-14
Ditto, Truecrypt is great - you can encrypt the entire drive, rendering it useless when somebody plugs it into their computer.  It probably won't even show up as a drive when they plug it in.

---

### Post by Sylslay on 2010-02-15
make ext4 partition and is only for linux system.
No way to read it from <snip>, 
onlu ext4 can be read from <snip>

---

### Post by Giant Speck on 2010-02-15
> **Sylslay said:**
> make ext4 partition and is only for linux system.
No way to read it from <snip>, 
onlu ext4 can be read from <snip>

You realize your post contradicts itself, right?

---

### Post by Grenage on 2010-02-15
> **Sylslay said:**
> make ext4 partition and is only for linux system

"This disk cannot be read, would you like it format it now?"

"Yes"

> **Sylslay said:**
> <snip>

You 1337 h4x0r, j00 ;)

---

### Post by elevatorgod_1 on 2010-02-15
> **wersdaluv said:**
> I have a 500 gb external hard drive with tons of personal files on it. Other people at home just grab my hard drive whenever they need to transfer files. I feel so disrespected. I also want to protect myself from actually losing my hard drive to a stranger who will compromise my data.

I'm thinking of encrypting, but I'm currently too busy to explore (the options seem to be hard to use) and it seems to be too much to encrypt a 500gb hard drive

What are my options in "locking" my hard drive. I don't mind if it's going to be readable only on Ubuntu. That could actually be a plus :)
**ScramDisk 4 Linux maybe of some help :-)**

SD4L is a suite of Linux tools including a graphical user interface which allow the creation of, and access to ScramDisk as well as TrueCrypt encrypted container files. In particular, SD4L provides a Linux driver which enables mounting of containers.```
http://sourceforge.net/projects/sd4l/
```

---

### Post by 26venger on 2010-02-15
truecrypt +1

---

### Post by wersdaluv on 2010-02-15
Now, I'm considering truecrypt through ScramDisk, locking it in my drawer, and ext4. Cool options, folks.

Keep 'em coming! :)

---

### Post by HermanAB on 2010-02-16
Here is a LUKS howto and wizards that could make the encrypted HD Windoze compatible:
[http://www.aeronetworks.ca/luks-usb-howto.html](http://www.aeronetworks.ca/luks-usb-howto.html)
[http://www.aeronetworks.ca/LUKS-Mount-FreeOTFE.pdf](http://www.aeronetworks.ca/LUKS-Mount-FreeOTFE.pdf)

---

### Post by airtonix on 2010-02-19
> **wersdaluv said:**
> Now, I'm considering truecrypt through ScramDisk, locking it in my drawer, and ext4. Cool options, folks.

Keep 'em coming! :)
you can also get a hole saw and drill two holes in your draw basin then use a kensington cable to secure the drive to the drawer...

cable would be long enough that you can plug a USB cable to the computer to the drive.

i would also suggest purchasing twelve steel containers, each one smaller than the last and lock the drive in the smallest....Russian doll style.

also I like to keep a trained brown snake in a perspex container and i put my Kensington locked Russian doll boxes (containing my pron on the drive) in there with jack the brown snake.

you could also submerge the Russian doll steel boxes beneath a foot of gravel so the perspex container looks like a normal snake house.

:)

---

### Post by Grenage on 2010-02-19
Lol.

---

### Post by wersdaluv on 2010-02-19
Can't install ScramDisk 4 Linux :(

I get ```
Error: Dependency is not satisfiable: linux-image-2.6.28-18-generic
```

---

