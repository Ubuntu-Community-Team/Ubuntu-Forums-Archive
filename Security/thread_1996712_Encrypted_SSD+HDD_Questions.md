---
title: "Encrypted SSD+HDD Questions"
date: 2012-06-04
forum: Security
---

### Post by kid1000002000 on 2012-06-04
Hi all. I purchased a new laptop and have a few questions on the best way to do the following. Thanks for bearing with me as I try to learn all of this.

I have a 70gb SDD that I will be putting into the laptop to run Ubuntu  12.04 from. I will replace the CD/DVD bay with a caddy for  installing the remaining 500gb HDD. The 500gb will be partitioned in 1/2  to hold Windows 7 and contain symbolic links from Ubuntu for storing [COLOR=DarkGreen]/tmp,  Desktop, Documents, Music, Video, and Downloads.[/COLOR]

I require my data to be secure. Thus, I would like to encrypt  information while making maximum use of the limited life an SSD will  provide (e.g., TRIM support). I'll probably follow [these]("http://worldsmostsecret.blogspot.com/2012/04/how-to-activate-trim-on-luks-encrypted.html")  instructions (enable TRIM on the encrypted SSD), as I am not so  concerned with someone knowing where my files are, just protecting them  from access by theft.

How can I make the best of this? See the following questions.

[LIST=1]
[*]When installing Ubuntu for the first time to the SSD, should I tell it to encrypt my entire home directory?
[LIST=1]
[*]If I do, once symbolic links are created to the HDD for my big directories, will those folders be encrypted as well? Could doing this affect  my ability to recover these files later on?
[*]If I do not, how should I encrypt the directories mentioned,  have the directories mount automatically, and protect them from an  intruder also mounting them automatically? (The laptop will not  automatically login, but is this sufficient protection?)
[/LIST]
 
[*]Would it be smarter to remap the entire encrypted home directory to  the HDD, or will this have considerable performance issues with  applications loading, effectively defeating the purpose of a SDD?
[*]Will enabling TRIM on an encrypted SSD (see [link]("http://worldsmostsecret.blogspot.com/2012/04/how-to-activate-trim-on-luks-encrypted.html")) still prevent wear out if I use your suggestions from these other questions?
[*][COLOR=DimGray]The laptop has 8gb of RAM. Which drive would be best for SWAP, and what do I need to do to ensure that the swap partition will stay encrypted, as I am not doing a cookie-cutter encrypted install here? 
*EDIT: Found the answer to SWAP. I want it []("http://ubuntuforums.org/showthread.php?t=1976464")**[on the HDD]("http://ubuntuforums.org/showthread.php?t=1976464").*[/COLOR]
[/LIST]
Thank you for your help. I truly appreciate it.

---

### Post by gordintoronto on 2012-06-04
I'm a big fan of simplicity. That would mean putting /home on the HDD. Generally, applications are not installed in /home, although configuration parameters are. I don't see any need to encrypt the root folder (/),

Use a good password! More than eight characters, upper and lower case plus numbers and other symbols.

I'm not sure what you would need to run to have the swap used, other than Hibernate.

---

### Post by thnewguy on 2012-06-04
1: In your sepcific case, it does not sound like there is any point to encrypting a home folder on the SSD. If possible, try creating a home partition on the hard drive and encrypting that.

If you create symbolic links to another location inside your encrypted home folder, the location linked to will not be encrypted.

2: Yes, definitely set up your home partition on the HDD and encrypt it there. This will not affect the speed of applications loading as they will be on the SSD, not in your home directory. Some of your documents may load a little slower, but unless your documents are quite large, it shouldn't be an issue.

3: SSDs wear out so slowly these days, accepting millions of writes, it really should not be an issue if the SSD is fairly new. Concerns about SSDs wearing out are a bit outdated at this point.

---

