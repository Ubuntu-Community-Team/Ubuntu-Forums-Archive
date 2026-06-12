---
title: "Anyone know how to lock or encrypt an ext hdd?"
date: 2010-07-27
forum: Security
---

### Post by bocaccio on 2010-07-27
I have a ext hdd..seagate go. And my 14 yr old son likes to get into it without asking me; of course i dont care when he asks but i don't really want him to get in there and erase anything. I am about to leave for training for 18 weeks with the military. Is there a way i can "secure" the drive for the amount of time that I can't take it with me?

---

### Post by earthpigg on 2010-07-27
[http://www.truecrypt.org/](http://www.truecrypt.org/)

---

### Post by FuturePilot on 2010-07-27
It will involve a reformat but use Disk Utility to reformat it and you can choose to encrypt the drive.

---

### Post by earthpigg on 2010-07-27
> **FuturePilot said:**
> It will involve a reformat but use Disk Utility to reformat it and you can choose to encrypt the drive.

if the external hard drive is less than half full, he should be able to create an encrypted folder on the hard drive, copy everything into the encrypted folder, and delete the original unencrypted data.

the kid, if he is smart enough, will still be able to use tools like photorec to recover the data.

if your 14 year old is as computer savvy as a lot of folks around here and predisposed to time consuming independent research and problem solving, then hiding the data from him will be a lot more involved:

1) back up all the data from the external hard drive.
2) [dban]("http://en.wikipedia.org/wiki/DBAN") the external hard drive. this will eradicate the data from the external hard drive in such a way that it will be impossible to recover.
3) use [truecrypt]("http://en.wikipedia.org/wiki/Truecrypt") to create an encrypted partition on the external hard drive.
4) restore the data from the backup onto the external hard drive's encrypted partition.
5) dban whatever hard drive you backed the data up onto. this, again, will completely eradicate all data on that hard drive. if you had Ubuntu or Windows installed on that hard drive, you will obviously need to reinstall it.


That is what you ought to do if are concerned that your son is some kind of terrorist hacker mastermind and the external hard drive contains nuclear launch codes.

if he is just a typical hormonal 14 year old boy, not a mastermind, and you are trying to keep your porn from him...

1) create an encrypted folder on the hard drive using truecrypt.
2) move all the data onto that encrypted folder.
3) done.

using that 3 step process, it is still [completely possible]("http://www.cgsecurity.org/wiki/PhotoRec") for someone to get his/her hands on the data - not the encrypted data, but the data that was 'deleted' after you moved it onto the encrypted folder. neither windows, os x, or ubuntu's file managers *actually* 'delete' anything when you press 'delete'. it just marks certain areas of the hard drive as 'available to be overwritten' by other data.... and also available to be "recovered".

i said it was possible for 'someone' to get his/her hands on the data. that doesn't mean it is possible for *your son* to get his hands on it. that requires a judgment call on your part about how tech-savvy and determined your son is. unless your son is like i was at 14 and already getting into trouble for bypassing his school's computer security to play pranks, 3 step will almost certainly be fine.



disclaimer: i think what i said is true about the 3 step process. i know that when we normally 'move' something from one folder to another on the same partition, we merely change the information in the filesystem that defines where it resides in the filesystem. i am *assuming* that moving the data into an *encrypted* folder would be more akin to copying data and then deleting it - if that assumption is true, then i believe my entire post to be true an accurate. if that assumption is untrue, someone please correct me.

---

### Post by cariboo on 2010-07-27
This is a support question, it doesn't belong in the Cafe. Moved.

---

### Post by OpSecShellshock on 2010-07-27
Well really, if your primary concern is making sure he doesn't delete anything, you could just make it read-only for his user account. If there are things you don't want him to see, you could follow the encryption instructions above, or physically remove it and lock it up. Really depends on the specific risks you want to mitigate.

---

### Post by bocaccio on 2010-07-28
> **OpSecShellshock said:**
> Well really, if your primary concern is making sure he doesn't delete anything, you could just make it read-only for his user account. If there are things you don't want him to see, you could follow the encryption instructions above, or physically remove it and lock it up. Really depends on the specific risks you want to mitigate.


I could make it read only but it is suppose to stay in the case that i have it in and he's not suppose to be "**playing**" with it. There is no accounts on it.

---

### Post by bocaccio on 2010-07-28
> **earthpigg said:**
> if the external hard drive is less than half full, he should be able to create an encrypted folder on the hard drive, copy everything into the encrypted folder, and delete the original unencrypted data.

the kid, if he is smart enough, will still be able to use tools like photorec to recover the data.

if your 14 year old is as computer savvy as a lot of folks around here and predisposed to time consuming independent research and problem solving, then hiding the data from him will be a lot more involved:

1) back up all the data from the external hard drive.
2) [dban]("http://en.wikipedia.org/wiki/DBAN") the external hard drive. this will eradicate the data from the external hard drive in such a way that it will be impossible to recover.
3) use [truecrypt]("http://en.wikipedia.org/wiki/Truecrypt") to create an encrypted partition on the external hard drive.
4) restore the data from the backup onto the external hard drive's encrypted partition.
5) dban whatever hard drive you backed the data up onto. this, again, will completely eradicate all data on that hard drive. if you had Ubuntu or Windows installed on that hard drive, you will obviously need to reinstall it.


That is what you ought to do if are concerned that your son is some kind of terrorist hacker mastermind and the external hard drive contains nuclear launch codes.

if he is just a typical hormonal 14 year old boy, not a mastermind, and you are trying to keep your porn from him...

1) create an encrypted folder on the hard drive using truecrypt.
2) move all the data onto that encrypted folder.
3) done.

using that 3 step process, it is still [completely possible]("http://www.cgsecurity.org/wiki/PhotoRec") for someone to get his/her hands on the data - not the encrypted data, but the data that was 'deleted' after you moved it onto the encrypted folder. neither windows, os x, or ubuntu's file managers *actually* 'delete' anything when you press 'delete'. it just marks certain areas of the hard drive as 'available to be overwritten' by other data.... and also available to be "recovered".

i said it was possible for 'someone' to get his/her hands on the data. that doesn't mean it is possible for *your son* to get his hands on it. that requires a judgment call on your part about how tech-savvy and determined your son is. unless your son is like i was at 14 and already getting into trouble for bypassing his school's computer security to play pranks, 3 step will almost certainly be fine.



disclaimer: i think what i said is true about the 3 step process. i know that when we normally 'move' something from one folder to another on the same partition, we merely change the information in the filesystem that defines where it resides in the filesystem. i am *assuming* that moving the data into an *encrypted* folder would be more akin to copying data and then deleting it - if that assumption is true, then i believe my entire post to be true an accurate. if that assumption is untrue, someone please correct me.
I think i have all the answers i need right here. Are you watching me or something? Me hiding porn from my 14yr old son? just kidding. 
You should be teaching my classes. I am on 2/3 of my Core Classes in my Bachelors Degree for Computer Forensics. Getting into a lot of the Legal side of it and the steps you take when you get on the scene..stuff like that.

---

### Post by earthpigg on 2010-07-28
> **bocaccio said:**
> I think i have all the answers i need right here. Are you watching me or something? Me hiding porn from my 14yr old son? just kidding. 
You should be teaching my classes. I am on 2/3 of my Core Classes in my Bachelors Degree for Computer Forensics. Getting into a lot of the Legal side of it and the steps you take when you get on the scene..stuff like that.

Hardly, I'll be starting my second semester of community college in a few weeks. :P

What little I do know, I learned from an old A+ cert book, wikipedia, ubuntuforums.org, and google.

Before anyone goes out and wastes money on a brand new A+ certification study book, I'll point out that the hardware section is the only section of any potential value to a GNU/Linux user. Most Unix/Linux books/documentation (and even relevant wikipedia articles) assume you know a whole bunch about hardware already, while a typical A+ study guide assumes you know nothing. Few people in the GNU/Linux world are impressed by anyone going to the trouble to actually get that certification. 

Pick up a used one at random from the local Used Book Store, flip to the hardware section to see if it is to your liking, and use google/wiki to fill in the gaps caused by the book's age. 

I learned a lot from reading the hardware part of the book, but was fairly appalled at what was written in the rest. (example: apparently, the only two types of operating systems in the world are "Novell" operating systems and "Microsoft" operating systems. Wait, which Linux vendor was it that signed a far-reaching contract with Microsoft a few years back? hrmmm....).

---

