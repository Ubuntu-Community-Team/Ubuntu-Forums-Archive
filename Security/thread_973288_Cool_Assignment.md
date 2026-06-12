---
title: "Cool Assignment"
date: 2008-11-06
forum: Security
---

### Post by skarecrowster on 2008-11-06
Hey Guys, i'm a 2nd yr security student at Uni and have just been given an assignment, in which i have to hide 3 pieces of data on a 128Mb flash drive, using any methods i see fit... I'm not here for the solutions, as i have already come up with some seriously devious methods... But i'd like to get some suggestions if possible...

submission is next friday morning, where we will be given someone else's Flash drive, and given 1 hour to find the 3 pieces of info using forensic tools, such as FTK and Encase..

The 3 pieces of data are, a password 8 characters long, a Jpeg of a car, and a phrase, of 10 words.. No Encryption is to be used, and the characters of the password and phrase must not be split up in any way

Be the master criminal, how would you hide it ??

(We can use Linux & Windows)

---

### Post by Brandel Valico on 2008-11-06
I'd find a picture of a car with a billboard in the background. On which I would place the 10 word phrase. 

I'd also superimpose as a reflection of sorts the password onto the car shell within the image.

As for the picture of the car I'd hide it under a bunch of easy/not so easy to crack encryption. Then spend the rest of my time making a vast network of dead ends and loop backs for the person trying to bust my flash drive. 

For a quick 10 minutes of work I got this as an example

[Hidden]("http://home.comcast.net/~BrandelValico/Images/hidden.jpg")

In the example the 10 word phrase is "The Signs Are All Around You. The Day Draws Near"

The 8 digit password I hid on the billboard also. It's "1001868" oops thats only 7 digits. Ah well you get the idea anyway. 

I then placed the billboard onto an image that showed a car.

---

### Post by Diggs808 on 2008-11-06
What about encoding the phrase and password into the photo code itself?  Also, you could then place the photo on the flash drive as some sort of code rather than a jpeg itself.  

Just an idea...

---

### Post by Gamma746 on 2008-11-07
I'd use steganography (Maybe Steghide? [http://steghide.sourceforge.net/](http://steghide.sourceforge.net/)) to hide the data in several photos (I'm assuming that this is allowed)  While you're at it, hide a bunch of other, useless stuff in other photos; try to fill up the drive.

Then use dd to copy zeros to the first 512 bytes of the drive, thus wrecking the partition table.  You should run ```
sudo dd if=/dev/zero of=/dev/foo bs=512 count=1
```  Make sure you replace foo with the right drive, otherwise you could wreck your PC.

---

### Post by daleus on 2008-11-07
Dump a whole bunch of .mp3 files on the drive and hide the image of the car inside one of them.

The password, set it in the track number tag of a different, random mp3.

and the phrase can go in the comment field of another mp3's ID tag.

Unless they go and read the contents of each .mp3 and know what they are looking for, they'll probably overlook it.

I think the best way to complete this task is exploit the human, not trying to hide from security tools.

---

### Post by Nepherte on 2008-11-07
Just encrypt the data, replace some unimportant binary data from a jpeg with the encrypted data. Or if you want to make it thougher, spread the  data over the photo instead of adding the data as a whole. Nobody will ever find it :)

---

### Post by stinger30au on 2008-11-07
save the text you need for the password in the actual file of the picture

you will need some kind of disk editor and edit the data of the photo and place it in there.

when you view the photo you will see maybe a small glitch in the photo but if oyu make the photo of something messy to start with, you will not see the glitch

---

### Post by daleus on 2008-11-07
He said no encryption, and your all coming out with it.

Think on your feet!, Tools for finding hidden data can't find anything if the data wasn't hidden in the first place!

---

### Post by bodhi.zazen on 2008-11-08
> **skarecrowster said:**
> Hey Guys, i'm a 2nd yr security student at Uni and have just been given an assignment, in which i have to hide 3 pieces of data on a 128Mb flash drive, using any methods i see fit... I'm not here for the solutions, as i have already come up with some seriously devious methods... But i'd like to get some suggestions if possible...

submission is next friday morning, where we will be given someone else's Flash drive, and given 1 hour to find the 3 pieces of info using forensic tools, such as FTK and Encase..

The 3 pieces of data are, a password 8 characters long, a Jpeg of a car, and a phrase, of 10 words.. No Encryption is to be used, and the characters of the password and phrase must not be split up in any way

Be the master criminal, how would you hide it ??

(We can use Linux & Windows)

This is an interesting assignment, however, this is an assignment for you to work through and we discourage this type of thread on these forums.

---

