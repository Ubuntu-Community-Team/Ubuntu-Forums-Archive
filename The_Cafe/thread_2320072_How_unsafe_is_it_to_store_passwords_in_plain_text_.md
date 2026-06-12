---
title: "How unsafe is it to store passwords in plain text files?"
date: 2016-04-10
forum: The Cafe
---

### Post by user1397 on 2016-04-10
Note: I am talking about for a regular Joe desktop user, not a sysadmin or something else.  A friend of mine says he keeps all his major passwords in a single plain text file locally on his computer.  

I personally feel like that isn't a good idea, because if a hacker gains access to his computer and finds the file then he knows all of his passwords.  Then again, if the user doesn't do anything odd on the internet, and just does some mild browsing, word processing, and email, how risky is this?  Suppose this person has a typical home setup; something like a modem --> WiFi router (built-in firewall) with WPA2 password --> OS firewall and if Windows then proper antivirus software installed, etc.  

Alternatively, what would you suggest for average users who need to keep up with many passwords?  Just have them all hand written?  Only store them on removable media and disconnect them immediately after using them?  Use a single password service like LastPass?  Just let the web browser save all your passwords for you?

EDIT: Didn't know about this, looks really cool: [https://en.wikipedia.org/wiki/FIDO_Alliance](https://en.wikipedia.org/wiki/FIDO_Alliance)  Hope it gets implemented sooner than later.

---

### Post by grahammechanical on 2016-04-10
Here is an illustration.

The security services enter my house and take away my computer. They are looking for subversive documents. But I fooled them. I do not keep subversive documents on the computer. No. I keep them in a brief case. Oh, they took the briefcase away as well. I am not so smart. Then again I am not that stupid either. I keep any subversive thoughts in my head.

With passwords it is different. People can gain access to computers without entering the house if the computer is connected to the internet. With passwords stored in a note book (paper kind of note book) they will need access to the house and to know what they are looking for.

But the game changes yet again if I keep the note book in the laptop case with the laptop. Likewise, keep credit cards in a wallet and keep a list of pin numbers in the wallet for convenience then when the wallet is stolen the thieves have everything they need. 

Having passwords in a text file is not much different from having the passwords written on a sticky note stuck to the screen. And that has been done by some supposedly intelligent people.

Regards

---

### Post by buzzingrobot on 2016-04-10
> **ubuntuman001 said:**
> 
...what would you suggest for average users who need to keep up with many passwords? 

Many people seem to like password managers, which create, then encrypt and store, long and complex passwords.  I've seen some that automatically insert passwords when needed, and others that rely on a user copying and pasting.  The downside:  It's a single point of failure.

I'd argue the three most important things anyone can do re: passwords are:

1.  Use long and complex passwords. This will not protect you from stolen unencrypted or decrypted passwords, but the longer the password the longer it takes for a brute force attack to come up with it, hopefully long enough to fend off the attack.

2.  Use a unique password for any site, etc., where something you value is at risk.  E.g., your bank, Amazon, etc. 

3.  Use two-factor authentication when it is available.  

I tend to use the same password at sites like this -- forums, mailing lists, etc. -- because the worst that could happen is someone might post under my username. For the "at risk" sites I use mnemonics and a memorized algorithm of sorts to generate and remember unique passwords for each that are quite long.

Storing clear text passwords on a device is, for most people, going to be more risky that keeping them, instead, on a piece of paper.  If your device is compromised, you will not know those passwords have been stolen until someone uses them and you happen to notice the damage.  On the other hand, most of us are likely to store that piece of paper somewhere where we'd notice its loss more quickly.

---

### Post by coldraven on 2016-04-10
A long time ago i used to keep all my passwords in a file called README. My logic was that no one actually ever reads the READMEs :)
Now I keep important ones in my head, they are all quite long and have a mixture of characters.

Your friend would be better off if he kept them in a book* on his shelf. As mentioned above, you would know if you had been burgled but you won't know that you have been hacked.

*something so boring that nobody would look at it, charity shops have lots of them.

---

### Post by Bucky Ball on 2016-04-10
I keep my passwords in a plain text document on a backup drive which is only switched on and connected for backups. I print this out, stick it in a secret spot and add to it by hand, then update the digital version once in awhile.

Don't think I'd be keeping that file on the hard drive on my regular day to day laptop or desktop.

---

### Post by sammiev on 2016-04-10
I have been using KeePass2 ( encrypt and store ) for a few years now. Keeping a USB stick updated as there is just too many computers in my hands.

---

### Post by montag dp on 2016-04-10
If you're going to keep them in a plain text file, you might as well encrypt the file. That's basically all that the password managers do anyway, but with a more friendly user interface.

---

### Post by kurt18947 on 2016-04-10
> **montag dp said:**
> If you're going to keep them in a plain text file, you might as well encrypt the file. That's basically all that the password managers do anyway, but with a more friendly user interface.

That seems like a reasonable tack to take. Encrypted readme.odt document:D.  For sites where $$$ or legal damage could occur due to being compromised,  you could have a small separate *buntu install that's ONLY used for those activities. That way any nasties picked up from social or fluff sites shouldn't find anything lucrative or damaging on a daily use partition. Presumably sites with sensitive contents are more security conscious  than  the likes of Facebook, Twitter or sites that host cat videos.

---

### Post by mikodo on 2016-04-10
Plain text file works for me. Then, encrypt it with GPG symmetrical. I also keep a second copy of the data in KeepassX. Use 26 mixed character passwords I memorized to access them.

External backups. 

Won't stop everything but, I need to keep it simple.

---

### Post by PJs Ronin on 2016-04-11
Plain text files?   Depends how paranoid you choose to be (I'm one of the tin hat brigade).   I use LastPass to help out, but primarily I use:
[ATTACH=CONFIG]268298[/ATTACH]

---

### Post by mastablasta on 2016-04-11
keepass 2 does it for me. it generates complex passwords and you can copy&paste from it.

it is a bit more secure than text files. at least it if someone steals it should give me some time to change the passwords before they crack the master. and that is if I knew they stole it.

email is how people get it computer these days. also "mild browsing" what is that? respectable sites have been known to be filled with ads running malware under it.

---

### Post by malspa on 2016-04-11
> **PJs Ronin said:**
> Plain text files?   Depends how paranoid you choose to be (I'm one of the tin hat brigade).   I use LastPass to help out, but primarily I use:
[ATTACH=CONFIG]268298[/ATTACH]

Lol. Index cards, that's exactly what I've been using. But I think I might start storing passwords in a plain text file on a flash drive.

---

### Post by Irihapeti on 2016-04-11
Index cards? I thought the ultimate was a post-it note on your monitor...

---

### Post by Bucky Ball on 2016-04-11
May as well use a post-it note on your monitor. PJ, I thought you said you were paranoid, yet you leave all your passwords written on bits of card next to your computer! A theif doesn't need to steal your computer. They can simply take the box of index cards, get onto your bank account when they get home and buy themselves a better computer than they could have stolen from you! :|

---

### Post by sammiev on 2016-04-11
> **Irihapeti said:**
> Index cards? I thought the ultimate was a post-it note on your monitor...

I feel so much better now! ;)

---

### Post by allformsofpandas on 2016-04-11
How about a file with 000 permissions?

---

### Post by oldos2er on 2016-04-11
KeePassX.

---

### Post by PJs Ronin on 2016-04-11
Looks like my index cards peaked some discussion, excellent.   To those who wondered, after I took the image of my "password logging system" the index card box was returned to my kitchen, adjacent to a row of spices and oils.

My time in Defence (spelling is correct) taught me that security comprises both value and intent.   Sure, passwords are a high(er) value item as they could provide access to your personal assets, but the 'intent' factor tends to be missing from your typical drug starved home invader.   These erstwhile folks head straight for a couple of key places (bed side tables, ladies underwear drawers (??), freezer section of fridges, etc) during a break-in looking for cash and high value electronics.   A recipe card box flies under their radar.

---

### Post by mikodo on 2016-04-11
Really, if one is intently trying to be safe, one wouldn't have any passwords stored in the systems. Better to have them stored away from it in a safe place and a duplicate off-site. Our systems can be compromised too easily. I am surprised no-one but PJ has brought that up. I agree that would be best. I'm not holding myself up though, it is more of a do as I say, not as I do. I am getting too old to use the elaborate encryption schemes that would probably only lock *me* out now.

Speaking of security against house break-ins, I agree also, it is is usually addicted criminals looking for cash and expensive electronic equipment. In ladies underwear drawers though? Who keeps cash in them or, expensive electronics? None of my wives have ... or ... never mind, scratch that.

---

### Post by mastablasta on 2016-04-13
> **mikodo said:**
>  Who keeps cash in them or, expensive electronics?

many people keep cash in closets, drawers. not long ago there was a post from local facebook user. while his partner talked with the old lady about table cloths he went to "the bathroom". the video shows a thief casually going to the bedroom with a bored look on his face he goes through closets and a few drawers. collects the cash and goes out. it all happens in less than 2 minutes. this wasn't the first time the robbed the old lady and her family members, suspecting something, set up a video cam.

---

### Post by andrea105 on 2016-04-13
tried to encrypt the file with gpg?
It shall made hard to steal your passwords.

This is a useful link about this on askubuntu: [http://askubuntu.com/a/27806](http://askubuntu.com/a/27806)

---

### Post by deadflowr on 2016-04-13
Does NetworkManager still store passwords in plain text?
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1060907](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1060907)

No wifi for me, so can't tell...

---

### Post by oygle on 2016-04-14
Currently have all passwords stored in a html file. It's easy to view, edit and copy/paste passwords. If I move them to a KeePassx database that needs a master key to open, how can I ensure that **ONLY** KeePassx accesses the database ??

I saw one post in this thread that suggested changing the perms to 000. But won't that stop me from accessing it. lol

---

### Post by utnubu4 on 2016-04-15
Passwords are very important.. even to the average Joe. We use passwords to secure sensitive data, how would you feel if someone gained access to your bank information? 

I would suggest creating your own hex written down on paper, then convert your passwords into your own hex code. Once you have your passwords converted into your own hex, go ahead and store them in your computer, I would suggest an encrypted folder.

Don't forget to keep the written down hex code very safe.

---

### Post by mikodo on 2016-05-01
> **utnubu4 said:**
> 

I would suggest creating your own hex written down on paper, then convert your passwords into your own hex code. Once you have your passwords converted into your own hex, go ahead and store them in your computer, I would suggest an encrypted folder.

Don't forget to keep the written down hex code very safe.
I wish I knew how to do that.

---

### Post by HermanAB on 2016-05-03
This is a very disconcerting thread.

Please tell your friend to install KeepassX on all his devices, put the password file in a central location such as Dropbox and then he can access them from anywhere all the time.

---

### Post by haplorrhine on 2016-05-06
You could always invent your own reversible algorithm to transform the passwords into something unrecognisable.

---

