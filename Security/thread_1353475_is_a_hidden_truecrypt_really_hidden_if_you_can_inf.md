---
title: "is a hidden truecrypt really hidden if you can infer its existence from file size?"
date: 2009-12-12
forum: Security
---

### Post by fireandspike on 2009-12-12
HI, I was playing about with hidden volumes in true-crypt today in preparation for a new ubuntu install. 

What I'm not sure about is this, if your trying to hide files in a true-crypt volume won't someone be able to infer the inner hidden volumes existence from file size of the outer volume file and the files contained in the outer volume.

for example If my entire true-crypt volume is 100Gb and i have to reveal my outer volume for some reason and he sees that I have 5GB worth of files in my (undisclosed) 10GB outer volume then won't he be able to infer a 90/95GB hidden volume from the total size of the truecrypt outer volume thats 100GB?

---

### Post by BkkBonanza on 2009-12-12
I believe you're confused about how hidden volumes work. There are not two different sizes, only one. If you have a volume of 10GB then when you use one password you get files starting from the bottom of the volume. When you use the hidden volume password you get files starting from the top of the volume. No one can see any indication of where the start or bottom volumes begin/end. Because the free space is random data and the volume data also looks random it is not provable whether the hidden volume is present or not. However, if you add too much data to your visible (bottom) volume then it can overwrite the data stored in the hidden volume, ie. if the bottom fills up too much then it obliterates the top portion.

The purpose of a hidden volume is denialibility. If someone says you have data in the truecrypt volume and forces you to release a password for it they have no way to prove you also have a second password for the hidden part. 

This is all explained on the truecrypt web site.

Of course, you may be saying that since you have a 10GB volume that isn't full it must indicate there is more because otherwise you wouldn't have made it that big. Well, ya, there's always that possibility. But then you either deny it or they start breaking limbs and you have to decide just how much you want to keep it secret... in this sense the fact that hidden volumes are possible guarantees that it's password may also be demanded. However, I think that hidden volumes may be more useful on an encrypted drive where the size is defined by the drive and hence not questionable.

---

### Post by fireandspike on 2009-12-13
> Of course, you may be saying that since you have a 10GB volume that isn't full it must indicate there is more because otherwise you wouldn't have made it that big.Yes that's what I was talking about. I live in a rather unfree country where the very existence of encrypted data is enough to land you in jail if you dont supply the password. There are no laws against self incrimination here. So if I don't encrypt this data (which happens to be legal in most country's but not mine) I get thrown in jail and if I do encrypt it I get thrown in jail for not supplying the password. So I'm screwed either way. 

What I need to do is hide that fact that I even have encrypted data in the first place, this is related to my other thread as well> [http://ubuntuforums.org/showthread.php?t=1353431](http://ubuntuforums.org/showthread.php?t=1353431)

I need a way to make encrypted data look like its not encrypted. In other words to obscure it in something legit. I thought about doing something like this>

encrypt the data
split it up into 10000 different chunks
hide each chunk inside an image file or video at the end of it as junk data so the image/video still works as normal and a person viewing the media file would not notice anything unusual.
Then to get the decrypted file back, read the junk data from each media file, reassemble it in the order known only to me and then decrypt it.

Of course I would have to make sure that ratio of junk data to legit content is not too obvious as with the hidden true-crypt volume. 

I know there are plenty of programs to hide data in images but I'm not sure if there is anything that does it on a large scale in an automated fashion.

Anybody done something like this before?

---

### Post by BkkBonanza on 2009-12-13
You need to read up on tools for "steganography". They do what you need but are hard to use for large data sets. If you just have a relatively small amount of private data and you have a lot of files (jpegs) that you can hide them in then there are tools that can help you. They will spread the data out over a number of jpeg/audio files in such a way that they cannot be detected (or not without knowing they're likely there and having sophistciated tools). Typically, for example, they add small calculable pixel value variations across an image and with the right tool those changes can be detected and retrieved. So you could first encrypt (with gpg) and then use steganography to hide the data in other files.

Another way would be to hide the encrypted (random looking) data in free space on a partition. It would not show up in the filesystem at all. You would not want to use that filesystem much (or at all really) as storing new files could overwrite free space. I don't know of a tool that does that but I'm sure there must be something out there. Or using low level block copying command like dd could likely be used but great care would be needed too.

The hidden volumes in truecrypt are designed for cases where deniability is likely to work. In a harsh regime where they know about truecrypt they would likely just beat you until you gave up denial.

---

