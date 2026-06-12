---
title: "Truecrypt help"
date: 2010-07-17
forum: Security
---

### Post by danielwinter on 2010-07-17
Hi there!

I've got a huge question and i don't know where to ask.. I hope anyone of you might help me!

I've encrypted a Partition using truecrypt, borrowed the harddisk to a friend and now i don't know it anymore..
to be exactly: i know 22 of the 26 characters, but 4 in the middle are... "gone" :)

There's some incredibly important data for me on that drive, so i need to recover my password. I have already created a passwordlist with the possible solutions (around 400 000 passwords), and now i need to "give it" to truecrypt in some way.

I've already downloaded CrackTC (which opens a txt with passwords in it and tries everyone of them), but i can't get it working!
it seems like it was for an older version of Truecrypt.

I've tested it with:
TC 6.2
TC 6.2 commandline version (currently trying on that)
TC 5.1

no solution.
Now i thought i might have to get onto the sourcecode of this little programm (written in Java).
If i compile it and try to start it it begins with the first password (at least it looks like it would), but then theres nothing left..

my commands look like that:

> daniel@daniel-laptop:~$ sudo -i
root@daniel-laptop:~# cd ..
root@daniel-laptop:/# cd home/daniel/TC/CrackTC/bin2
root@daniel-laptop:/home/daniel/TC/CrackTC/bin2# java CrackTC /dev/sdb2 pwd.txt

I'll add the java files via attachment, one is "my version", the other is the original by "lolox".

is anyone able to help me? :(

PS: Yes, I've tried to search for solutions in my own, and i've tried to write it on my own but my java skills aren't that good :)
PPS: If the topic is in the wrong section, please move it!

---

### Post by wacky_sung on 2010-07-17
Good luck in your quest trying to crack a 26 characters password using brute force / dictionary attack.

FYI it may take years or you gonna create a huge password list which can be gigabyte size.

---

### Post by danielwinter on 2010-07-17
> **wacky_sung said:**
> Good luck in your quest trying to crack a 26 characters password using brute force / dictionary attack.

FYI it may take years or you gonna create a huge password list which can be gigabyte size.

as i said i know 22 of the 26 characters. just 4 positions are wrong, therefore i just have to crack a 4 characters password.. that should be possible. the password list (which i already created) hast 28Mb btw.

$$$$$$$$$$$$@@@@$$$$$$$$$$

$ = Characters i know
@ = characters i forgot.

therefore it shouldn't be impossible :) it might take a week or so but i'm ready to wait for that..

---

### Post by Agent ME on 2010-07-17
Here's a general outline of a good plan, but I don't know the specifics of the truecrypt program; as long as it has some command line interface that you can specify a possible mount password on, this will be possible. It just needs the right command substituted in instead of "truecrypt-mount-something".

EDIT: I looked up online a bit and I think I've got the right command in. It just needs to be pointed to the truecrypt file.

crack.sh
```
#!/bin/sh

while read line
do
  if truecrypt my-truecrypt-container --password "charactersIknow${line}moreIknow"
  then
    echo "Success, using $line"
    exit 0
  fi
done
echo "Failed."
exit 1
```

passes.txt (for example: )
```
aaaa
aaab
aaac
...
zxbc
zxbd
zxbe
...
zzzz
```

in a terminal
```
chmod +x crack.sh
sudo ./crack.sh <passes.txt
```

---

### Post by jflaker on 2010-07-17
> **danielwinter said:**
> Hi there!

I've got a huge question and i don't know where to ask.. I hope anyone of you might help me!

I've encrypted a Partition using truecrypt, borrowed the harddisk to a friend and now i don't know it anymore..
to be exactly: i know 22 of the 26 characters, but 4 in the middle are... "gone" :)  ...SNIPPED


The whole premise of an encrypted disk or volume is so that even if you know a part of the password, you will be out of luck.  The longer the password, the better chances it won't be cracked.

There is a recent story of the FBI recently trying to decrypt a disk likely to hold information about a crime...but to no avail 3 years later.....

The only thing you can do, is try to bruteforce the missing characters, but if those are not correct, you will not get in.

Encryption is meant to be secure.  There is nothing in the sourcecode to help you decrypt, to be honest...

---

### Post by Agent ME on 2010-07-18
He's only missing 4 characters; assuming he knows which specific 4 characters are missing and that they're alphabetic, that's only 456,976 (26^4) possibilities. If one combination could be checked per second for example, then it should only take around 63 hours to crack.

---

### Post by awi on 2010-07-18
What I see is you are asking for help to crack a 4 character password, all the story you create around it it's only a matter of imagination in order to obtain some help. Who can garantee that this file your are trying to break it's actually yours?

---

### Post by Agent ME on 2010-07-18
If he has that much of the password of a truecrypt volume that isn't his then it's the owner's fault.

I updated my script so it should work. Tell me how well it works; it may need " --password-tries 0" added to the line that calls truecrypt if it decides to try to ask you the password instead.

---

### Post by danielwinter on 2010-07-19
> **awi said:**
> Who can garantee that this file your are trying to break it's actually yours?

quite impossible to garantee that, but as anyone else said it might be the owner's fault if i got 22 of the 26 characters that password contains ;)
why I am missing these 4?
the first 18 characters were from a password I used for about 4 years, the other characters were generated by a password genearator, that's why i lost them.



And thanks to AgentME, I'll give it a try when I'm at home.

---

### Post by alphaamanitin on 2010-07-19
> **danielwinter said:**
> Hi there!

I've got a huge question and i don't know where to ask.. I hope anyone of you might help me!

I've encrypted a Partition using truecrypt, borrowed the harddisk to a friend and now i don't know it anymore..
to be exactly: i know 22 of the 26 characters, but 4 in the middle are... "gone" :)


You say you lent the hard disk to a friend and now you don't know the four in the middle.  I find is odd that you forgot only 4 of the 26 character passphrase (and not because I think you are lying about being the owner, I will explain shortly).  I assume you tried what you originally thought was the full 26 character passphrase when you tried to mount if for the first time, that it failed to mount, and that you assumed you forgot those 4 characters correct? 

So here is why I find it odd.  Do you have any idea what your frind did to the drive while (s)he had it?  Did (s)he try writing anyting on the drive?  Is it a full disk encryption?  I ask because if your friend did attempt to right anything to that drive and damaged part of the headers (one in the very front of the TC volume and a back up at the very rear), you are screwed.  If both headers have been damaged and you do not have a back up the drive will not mount even if you supply the correct passphrase.  And no-you cannot recreate the headers.  

Assuming your story is true, it is your drive, and you let some one borrow it, I find it more likely that the headers have been damaged than you managing to forget only 4 out of 26 characters.  

If it is not true and you are cracking into some one else's drive, have fun.  I cannot provide help- not for any moral ground but because my kung fu is not that good.  

If you want to check your headers I suggest you join the TrueCrypt forum-though it requires a .edu or some other private email provider.  Then find and ask Dan about it-he appears to have amazing knowledge of TrueCrypt and to be very helpful.

AlphaA

---

### Post by awi on 2010-07-20
> **danielwinter said:**
> quite impossible to garantee that, but as anyone else said it might be the owner's fault if i got 22 of the 26 characters that password contains ;)
why I am missing these 4?
the first 18 characters were from a password I used for about 4 years, the other characters were generated by a password genearator, that's why i lost them.



And thanks to AgentME, I'll give it a try when I'm at home.

This is interesting, if you used the same password for 4 years, why use a password generator for only 4 characters that you might "forget"? 
I can say that you are lying about de 22, and it's my word against yours. 
My statement is as true as yours. It's "quite impossible to guarantee" who's telling the truth.

---

### Post by alphaamanitin on 2010-07-20
> **awi said:**
> This is interesting, if you used the same password for 4 years, why use a password generator for only 4 characters that you might "forget"? 
I can say that you are lying about de 22, and it's my word against yours. 
My statement is as true as yours. It's "quite impossible to guarantee" who's telling the truth.


I can think of many reasons to use a password generator for the last 8 (not the last 4).  My number one reason would be to introduce more entropy into my standard password.  Even though I like the password for things like my email, I may want a more robust password for my TrueCrypt volume.  I am not taking any one persons side on whether or not he is lying, only pointing out that there is an innocent explanation for any oddity you might find with his story.  At least with his story up to date.  

So I say this, I see no reason not to believe him right now, 22 of 26 characters and their positions sounds like a lot to get from a person and be missing 4.  I myself just installed a program that I had written down the product key for, but sloppy hand writing and months of not using it made me have to guess 3 of the positions until I got it right.  Also, even if he is lying we are not doing any real harm.  There are a number of other places to seek help; some of which would have absolutely no problem helping even if you announced that it was a stolen drive.  In this instance I chose to believe him.

I would like an update on his progress though.  Seems to me some one that actually owned the device and was able to access it again because of help would be very grateful...  Of course he may not have accessed it yet.  

AlphaA

---

### Post by Sporkman on 2010-07-21
> **Agent ME said:**
> He's only missing 4 characters; assuming he knows which specific 4 characters are missing and that they're alphabetic, that's only 456,976 (26^4) possibilities. If one combination could be checked per second for example, then it should only take around 63 hours to crack.

Actually, it's Y^4, where Y is the number of candidate characters. There could be more than 26, for instance if you include upper & lower case, plus numerals, you have 62 possibilities...

EDIT: Sorry, I didn't notice the "alphabetic" - that makes it 52 possibilities.

---

### Post by danielwinter on 2010-07-23
Hey there!
Sorry, I did not have any time to answer in these days.


To answer a few questions:



The Hard drive is 1,5tb in total, the encrypted part is a 1,1tb partition, the rest is a normal FAT32 partition, this is where my friend picked upped the data he wanted. So he didn't need to know the password.




Why I used a password generator for the last characters?
Let me explain that a little bit..
My password consists of several combinations:

password for my internet connection + a little insider between friends and me + the generated part.

all in all:
puxjxlvblub4ever@ "thepartIdon'tknowanymore" bMT24

i generated the last part because the first part is quite easy to decrypt, just a password my ISP gave me, plus words that might exist in a dictionary. I remember the last characters because I built a little "learn sentence" ("by my thing.. don't know how i got to that :) ), and the last number is my birthday. So... quite logical that i might remember these lines, eh?

the part i don't know exists of numbers and characters in upper case, so just 26 characters plus 10 numbers. ;-) (I dont remember the characters anymore but I remember pressing the shift key to long, forcing me to re-enter the password)


But anyways, I understand that you might think that I lie, at least I might do the same if I was on your side. It's your decision wether to trust me or not. I'm not angry if you don't, but I would be great if someone could help me :-)
The tips until today were nice, but I didn't manage to get it working :/


I hope I was able to answer a few of your questions, belonging the source of the reason cracking my own password ^^

---

### Post by alphaamanitin on 2010-07-23
> **danielwinter said:**
> 
The Hard drive is 1,5tb in total, the encrypted part is a 1,1tb partition, the rest is a normal FAT32 partition, this is where my friend picked upped the data he wanted. So he didn't need to know the password. 


Are you sure about the partitioning and that there is no possibility of damaging the header?  Anyway, I am sure a google search would also provide you with lots of programs.  This makes me think that next time I make a passphrase I might also generate a md5 hash of it and use it to check passwords if I forget them.  Of course the md5 is not exactly secure for real security purposes.  

AlphaA

---

### Post by rookcifer on 2010-07-23
> **alphaamanitin said:**
> Are you sure about the partitioning and that there is no possibility of damaging the header?  Anyway, I am sure a google search would also provide you with lots of programs.  This makes me think that next time I make a passphrase I might also generate a md5 hash of it and use it to check passwords if I forget them.  Of course the md5 is not exactly secure for real security purposes.  

AlphaA

Then don't use MD5.  There are plenty of other secure hashing functions.

---

### Post by danielwinter on 2010-07-23
As I imagine there will be lots of other users who have the same problem as I did, I'd like to publish an early try of getting into the drive:

Some genius guy called "IsNull" has coded a program which tries to bruteforce truecrypt files (and even partitions), while it's not using truecrypt directly. It even supports keyfiles! At the moment it's Windows only, but he's trying to write it down in C# so it might be available on other operating systems.

I'm running it on my drive now, with my generated list, looking forward to get onto my drive. I'll inform you if it worked.

here the link to the program:
[http://securityvision.ch/index.php?option=com_content&view=frontpage&Itemid=55](http://securityvision.ch/index.php?option=com_content&view=frontpage&Itemid=55)

I found it in the TrueCrypt forum after searching for days.. it might work this time.. we'll see.


&#8364;dit:
it even saves the last position on the wordlist, so you can pause it and start on another days or something like that! :)

Log so far:
> Hi Daniel :)
___________________________________________________________________
Starting Crack Operation:
Truecrypt: C:\Program Files (x86)\TrueCrypt\TrueCrypt.exe
Wordlist: C:\Users\Daniel\Documents\1.9b\passwrds_upper_case.txt
Target: \Device\Harddisk6\Partition2
Letter: W
Gattering Informations...

Wordlist has ''1679616'' entries.
WL md5: 14513f506ed94a453e0ec75508a4dd46

No previous crack-progress found with this Wordlist. Begin by Pos 1.

---

### Post by AlastairG on 2011-10-12
Someone at work uses TrueCrypt and forgot their password for an encrypted volume and they rely on muscle memory combinations for passwords alternating between permutations of strings for example,  the strings "123", "abc", "!@#" could yield them a password of "abc!@#123" or 26 other variations. I made a PHP script (web developer \\:D/) and used cURL and bash to get his 100.000 possibilities into a password list.

Apparently after some changes to TrueCrypt (command line-only) over the years, AgentME's script no longer works but I modified it to work again (as of 2011). I have no prior shell-scripting experience so this isn't wonderful but at least it works!

```

#!/bin/sh
while read line
do
  if truecrypt my-volume.tc --filesystem=none -m '' --password="$line" -k '' --protect-hidden=no && echo "$line"
  then
    echo "Success!"
    exit 0
  fi
done
echo "Failed."
exit 1

```**sudo sh crack.sh <passwords.lst**

I couldn't get it to show the original password but it will mount and then kill the script so the important thing is that you can get your files out of the volume.

Due to the speed of attempts, this is probably only useful for people that have a reasonable idea of what their password might be. For malicious usage, one'd hope their victim used 'password123' or 'admin'. :p

---

