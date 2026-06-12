---
title: "How to investigate whether your passphrase has been cracked"
date: 2012-06-28
forum: Security
---

### Post by yeehi on 2012-06-28
Is there a webpage you can go to where you can check if your password is in a crackers dictionary or has had the hash etc cracked? I would like to be able to do this without actually transmitting the password to the website, where it might be collected and added to a dictionary!

The sort of technology I am thinking of would be something like the [godaddy]("http://www.godaddy.com/domains/searchresults.aspx?ci=57076&isc=gfnf4me15") domain registration page, where, as you type in a domain name, it starts informing you of whether the name is available before you even hit the enter key.

---

### Post by tubbygweilo on 2012-06-28
If you feel that you may well be a target of such password cracking then create a long one and change it often. Although I know nothing about cracking passwords I think the bit of technology you are searching for may be a [Rainbow Table]("http://en.wikipedia.org/wiki/Rainbow_table") but then do you know which tables the crackers are using?

Can you describe why you think you may be a subject of a cracking attempt? You never know but their may well be other ways to protect you.

---

### Post by yeehi on 2012-06-28
Hi, tubbygweilo!

I think everybody should be concerned whether they are the subject of a cracking attempt. Ethical hackers have access to the same dictionaries / rainbow tables as cracers do. Perhaps an ethical hacker has created a website where you can check if your passphrase is in the public domain.

---

### Post by tubbygweilo on 2012-06-28
> Perhaps an ethical hacker has created a website where you can check if your passphrase is in the public domain.

Perhaps a bad guy posing as an ethical hacker has created a website where you can check if your passphrase is in the public domain then you have given them the keys to your system.

Just use a long, hard and changing password - keep the keys to your system in your own pocket.

---

### Post by CharlesA on 2012-06-28
> **tubbygweilo said:**
> 
Just use a long, hard and changing password - keep the keys to your system in your own pocket.

This. Use a password manager to keep track of them, if need be.

---

### Post by SEWilco on 2012-06-28
Type in your passphrase here or on any random web site.
Assume that it might now be used, so change it.

---

### Post by Cheesemill on 2012-06-28
> **yeehi said:**
> Is there a webpage you can go to where you can check if your password is in a crackers dictionary or has had the hash etc cracked?

No.

Anyone who is a serious cracker or a security expert routinely create there own custom dictionary files, there is no way of knowing what they all contain.

I'm sure that [haqking]("http://ubuntuforums.org/member.php?u=1317912") probably has it in one of his dictionaries though :)

Take a look at this thread:
[http://ubuntuforums.org/showthread.php?t=2006385](http://ubuntuforums.org/showthread.php?t=2006385)

Simply put, the more characters in your password, the less likely it is to be cracked.
[http://xkcd.com/936/](http://xkcd.com/936/)

---

### Post by wacky_sung on 2012-06-30
> **Cheesemill said:**
> No.

Anyone who is a serious cracker or a security expert routinely create there own custom dictionary files, there is no way of knowing what they all contain.

I'm sure that [haqking]("http://ubuntuforums.org/member.php?u=1317912") probably has it in one of his dictionaries though :)

Take a look at this thread:
[http://ubuntuforums.org/showthread.php?t=2006385](http://ubuntuforums.org/showthread.php?t=2006385)

Simply put, the more characters in your password, the less likely it is to be cracked.
[http://xkcd.com/936/](http://xkcd.com/936/)

Dictionary attacks is kinda old fashion way of attack to crack a password with 10 characters or less. It is almost near impossible to crack a 21 characters or longer with meeting all requirements of creating a good password. Rainbow tables is good for fast password crack but it will be a pain to have huge disk space to break a 21 characters or longer. Cracker mainly use crack to break the salt/hash or md5sum to get the password. I bet the most effective ways of all is the man in the middle attacks and keylogger is best way that went underhand to steal password than those cracking methods.:lolflag::lolflag::lolflag::lolflag:

---

### Post by dodo3773 on 2012-06-30
> **yeehi said:**
> Is there a webpage you can go to where you can check if your password is in a crackers dictionary or has had the hash etc cracked? I would like to be able to do this without actually transmitting the password to the website, where it might be collected and added to a dictionary!


Not that I am aware of. I do not believe something like this exists. At least not for you to use as you wish. I understand what you are saying but I think you are doing it a little backwards. There are websites that you can use to try to crack hashsums. So create a hashsum from your password and try to crack that. If the hash exists (not your password in plaintext) in the database then yeah it might be more vulnerable. Although, you are probably wasting your time. Just use keepassx and generate long random passwords. A different one for every site. Just make sure to backup your keepassx database in case the original gets corrupted.

---

