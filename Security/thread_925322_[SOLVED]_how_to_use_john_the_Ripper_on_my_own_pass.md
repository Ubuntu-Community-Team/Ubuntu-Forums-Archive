---
title: "[SOLVED] how to use john the Ripper on my own password"
date: 2008-09-20
forum: Security
---

### Post by bigdee973 on 2008-09-20
okay i have john the ripper installed through the synaptic package manager...[i.e. sudo apt-get install john] now i want to try to crack my own username password for ubuntu on my machine. can someone tell me step by step how to crack my own password? i need to know for security purposes of my own.

---

### Post by kevdog on 2008-09-20
Do to these forums' policies, I don't think this question can be answered here!  I would recommend someone closing this thread before trouble starts.

---

### Post by cariboo on 2008-09-20
There are legitimate reasons for using john. I used to service computers for a living, I have lost count of the times I've had to reset the admin password in WiXP, and have had to crack the root password on a linux installation several times.

Have look at this page for a john tutorial:

 [http://www.osix.net/modules/article/?id=455](http://www.osix.net/modules/article/?id=455)

Also in a terminal:

```
man john
```

John is slow because it uses a brute force attack, so it may take quite a while.

Jim

---

### Post by Dr Small on 2008-09-20
> **kevdog said:**
> Do to these forums' policies, I don't think this question can be answered here!  I would recommend someone closing this thread before trouble starts.
I didn't think there was anything illegal about using John or using it to crack my own password that existed on my own computer that I had root access to. This, I would not think, to be against Forum Policy, but someone please correct me if I am wrong.

To the OP, a simple way to crack your own password would be to copy the line from /etc/shadow that pertains to your account. Paste this line in a new file, and for example, we'll call it 'passwd'. Now, simply run:
```
john passwd
```

John will begin bruteforcing the password through all it's dictionary files, and after that has completed with out success, it will begin what is called 'Incremental' mode. From there, it is basically a guessing game to see if John can crack it.

You can stop john at any time, and then restore the session by running:
```
john -restore
```

Dr Small

---

### Post by Sef on 2008-09-20
> Do to these forums' policies, I don't think this question can be answered here! I would recommend someone closing this thread before trouble starts.


If it is for their own machine, it would be ok.

---

### Post by lovinglinux on 2008-09-20
> **Sef said:**
> If it is for their own machine, it would be ok.

What about the "Social engineering" thing explained in the Ubuntu Security sticky? 

It wouldn't be illegal to crack the password of your own machine, but (not judging the thread starter) anyone could post messages here saying that this is for personal use. So, as far as I see from similar threads, I think this should be locked/deleted.

Just my 2 cents...

---

### Post by Dr Small on 2008-09-20
> **lovinglinux said:**
> What about the "Social engineering" thing explained in the Ubuntu Security sticky? 

It wouldn't be illegal to crack the password of your own machine, but (not judging the thread starter) anyone could post messages here saying that this is for personal use. So, as far as I see from similar threads, I think this should be locked/deleted.

Just my 2 cents...
Explaining how to use John is not a crime, whether or not the person is using a social engineering attack against us, or not. We can only go by what the OP said, not by what we preceive (of what we can not know).

If a person started a thread saying "Can u help me crack passwords with john?? i am on my friendz compz nad want to crack his passwd and be ubber 1337!", then we would ultimately lock this thread.

Otherwise, I see no harm in it.

---

### Post by lovinglinux on 2008-09-20
> **Dr Small said:**
> Explaining how to use John is not a crime, whether or not the person is using a social engineering attack against us, or not. We can only go by what the OP said, not by what we preceive (of what we can not know).

If a person started a thread saying "Can u help me crack passwords with john?? i am on my friendz compz nad want to crack his passwd and be ubber 1337!", then we would ultimately lock this thread.

Otherwise, I see no harm in it.

Thanks for the explanation.

---

### Post by tarun.winlin on 2008-09-21
> **dr small said:**
> explaining how to use john is not a crime, whether or not the person is using a social engineering attack against us, or not. We can only go by what the op said, not by what we preceive (of what we can not know).

If a person started a thread saying "can u help me crack passwords with john?? I am on my friendz compz nad want to crack his passwd and be ubber 1337!", then we would ultimately lock this thread.

Otherwise, i see no harm in it.

+1

---

### Post by bigdee973 on 2008-09-22
thanks for the policies,  its good that we have policies like this because i for one am not trying to hack or do anything illegal i need to know how to use john 1) for figuring out how well this thing is going to be able to hack into my own account and if it does fix it until ultimately john or any other hacking program cannot figure out my password and 2) if i ultimately forget a password, lock myself out OR some other malicious person locks me out i.e. changes my password as a prank while im using the potty i could at least attempt to find out the password with this tool. its for my own good not for breaching others security.

---

### Post by bigdee973 on 2008-09-22
> **Dr Small said:**
> I didn't think there was anything illegal about using John or using it to crack my own password that existed on my own computer that I had root access to. This, I would not think, to be against Forum Policy, but someone please correct me if I am wrong.

To the OP, a simple way to crack your own password would be to copy the line from /etc/shadow that pertains to your account. Paste this line in a new file, and for example, we'll call it 'passwd'. Now, simply run:
```
john passwd
```

John will begin bruteforcing the password through all it's dictionary files, and after that has completed with out success, it will begin what is called 'Incremental' mode. From there, it is basically a guessing game to see if John can crack it.

You can stop john at any time, and then restore the session by running:
```
john -restore
```

Dr Small

cool thanks,but u mentioned a line? what line extactly r u talking about there are several in the file...is it the line that has my username with it?  if i just copy and paste everything from the shadow file onto a new text file would i still be able to crack it?

---

### Post by blazercist on 2008-09-22
only problem is that u need root priveleges to read /etc/shadow so the whole thing becomes redundant as a practical experiment.

---

### Post by bigdee973 on 2008-09-22
> **blazercist said:**
> only problem is that u need root priveleges to read /etc/shadow so the whole thing becomes redundant as a practical experiment.

i do have root access and root privileges i just want to crack my own password to see if it can get read by john the ripper

---

### Post by bigdee973 on 2008-09-22
also how can i go about seeing john getting my password for my user in my windows XP partition? i have root access to windows partition and i want to see if john can get my password for me.  this is for MY windows XP for MY account and My username.  this is not for security breaching others rather its for determining if my system is secure enough and in case i lose my password i could be able to get access to it.

---

### Post by cariboo on 2008-09-22
All you have to do is have access to the computer and use the software here:

[http://home.eunet.no/pnordahl/ntpasswd/](http://home.eunet.no/pnordahl/ntpasswd/)

No need to try and crack you windows password. I've have used utilities like this for years to reset admin and other user passwords.

Jim

---

### Post by Dr Small on 2008-09-22
> **bigdee973 said:**
> cool thanks,but u mentioned a line? what line extactly r u talking about there are several in the file...is it the line that has my username with it?  if i just copy and paste everything from the shadow file onto a new text file would i still be able to crack it?
Yes, just copy the entire line. John was invented to read the entire /etc/shadow file anyhow, but that takes a long time if you have alot of users. Thence the reason I suggested just copying the line pertaining to your username.

Dr Small

---

### Post by blazercist on 2008-09-23
for windows you can use samdump to dump the windows password hash file.

---

### Post by bigdee973 on 2008-09-27
yeah thanks guys i know at least now how to recover my password but now how can i go about starting to 'HACK' my own password for windows through JOHN...because if my password could be picked up with this software than thats an invasion of privacy and i need to see how one can thwart my system. i just need to know if john can crack it. thats basically all

---

### Post by blazercist on 2008-09-27
again, you can use SAMDUMP in windows to dump the windows password hash file which is similar to /etc/shadow file in linux.  from there the steps are the same.

---

### Post by bigdee973 on 2008-09-27
ok cool

---

### Post by poloko1 on 2009-10-05
im got task involving using john the ripper as my final project in computer security subject..this post realy help thought..but for now, im still stuck in cracking other pc password...my project should be 2 linux pc and 'A'pc should crack 'B'pc pasword..anyone got an idea?

i tried 'scp root@192.168.10.1:/etc/shadow'

output=no password hashes loaded...

one more,im only using local network

---

### Post by Moyamo on 2010-07-12
i tried using john and i get this 
```
No password hashes loaded

```

---

### Post by cariboo on 2010-07-12
A quick google search would have found [this]("http://ubuntuforums.org/showpost.php?p=9370013&postcount=2").

---

