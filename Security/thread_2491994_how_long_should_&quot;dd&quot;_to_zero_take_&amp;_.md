---
title: "how long should &quot;dd&quot; to zero take? &amp; how reliable for securing HDD?"
date: 2023-10-27
forum: Security
---

### Post by anotherChris on 2023-10-27
I sent an old Dell Inspiron 15 3000 series laptop to a recycling agency ([https://www.renet.jp](https://www.renet.jp)).  Initially, I had planned to remove the hard drive and use it as an backup external drive.  However, when the guy came to pick up my laptop, I couldn't get any of the screws to loosen. (I also couldn't re-install Linux for reasons.)  I ended up using the "dd" command to try to overwrite the hard drive.  Specifically, I used...
```
dd if=/dev/zero of=/dev/sda
```
I was surprised, because I expected this command to take a while to execute, but it executed very quickly.  Maybe 10 seconds or less.   I thought maybe it had not worked.  However, when I tried to re-start the laptop, it wouldn't boot because no bootable device was found.

My questions are:
[LIST=1]
[*]About how long should that "dd" command take to execute and overwrite my hard drive with zeroes?
[*]Assuming that the "dd" command worked correctly, how recoverable is the data on that hard drive that I ended up sending to recycling?   Can knowledgeable people likely boot the computer somehow?  Is it easy to strip files off of?   (I didn't have any financial information on there, but I was signed in to Gmail, Amazon, etc, so if somebody could boot the drive, they could access all that stuff.)
[/LIST]

Thanks.

---

### Post by sudodus on 2023-10-27
It takes several hours to wipe a hard disk drive with dd (of course depending on write speed and size of the drive). Increasing the the block size (from default 512 bytes to 4096 bytes (4 kiB) makes a big difference in speed. In some cases it is worthwhile to increase it further to 1 MiB, so use an option (on the command line after dd)
```

bs=4096
# or
bs=1M

```
But often there is a better and faster method to

[SIZE=3]wipe an internal drive: Use **[FONT=Courier New]hdparm[/FONT]**[/SIZE]

to create a new mapping between the logical and physical addresses. See [this link](https://ubuntuforums.org/showthread.php?t=2124829&p=12555068#post12555068). The link is old, the usage of hdparm might be slightly modified, so please read the manual [FONT=Courier New]**man hdparm**[/FONT]. 

Warning: If I remember correctly, [SIZE=3]do not use **[FONT=Courier New]hdparm[/FONT]** via USB[/SIZE]. It may brick the drive.

[hr][/hr]
Finally, *no*, I think you did not wipe the whole drive, only a small fraction of it near the head end. It makes it difficult but still possible to retrieve the data stored on the drive.

---

### Post by TheFu on 2023-10-27
If the people you worry about are 10 yr old kids, using /dev/zero will likely be fine. If they are from a govt and that govt wants to retrieve the data, no less than 5 random passes would be my suggestion. DoD standards require at least 10 random passes.

Could you be confusing HDD and SSD devices?  SSDs are over 25x faster than HDDs.  Compare 32,000 Mbps to 1200 Mbps.

+1 for using a larger blocksize if using dd.  The main issue with dd is that when it hits the first block failure, it stops.  There are other tools that will continue past back blocks and write to all that it can on a device.  ddrescue is one.

---

### Post by anotherChris on 2023-10-28
> **sudodus said:**
> It takes several hours to wipe a hard disk drive with dd .....Finally, *no*, I think you did not wipe the whole drive, only a small fraction of it near the head end. It makes it difficult but still possible to retrieve the data stored on the drive.

Hmmm... I was guessing the same thing... that perhaps I only overwrote the boot partition of the drive, which would be small but prevent the computer from being able to boot normally, but which would not actually delete the majority of information on the disk... thank you.  Unfortunately, because of the situation with a scheduled pick-up, I, unwisely, sent off the laptop.  I had deleted many files on the hard drive already.  However, I did not delete browser history and was signed in to services like Gmail and Amazon.    How would you rate my risk (i.e., how hard would it be to get data off the drive.. i.e., are there methods that could easily be done on any drive that would recover data...)?    And other than changing passwords for services like Gmail, would you do anything in particular?    (For example, do I need to change my wi-fi router password?)   Thanks.

---

### Post by anotherChris on 2023-10-28
> **TheFu said:**
> If the people you worry about are 10 yr old kids, using /dev/zero will likely be fine. If they are from a govt and that govt wants to retrieve the data, no less than 5 random passes would be my suggestion. DoD standards require at least 10 random passes.

Could you be confusing HDD and SSD devices?  SSDs are over 25x faster than HDDs.  Compare 32,000 Mbps to 1200 Mbps.

+1 for using a larger blocksize if using dd.  The main issue with dd is that when it hits the first block failure, it stops.  There are other tools that will continue past back blocks and write to all that it can on a device.  ddrescue is one.

I got this laptop as a hand-me-down from someone, so I don't know, but I assume it had an HDD because it was quite old (~12+ years?).   I don't know what this [www.renet.jp](www.renet.jp) service does with old stuff.  They advertise that they employ handicapped people to take apart and recycle computers, but I don't really know.  I am not concerned about a government, but I am concerned because the [www.renet.jp](www.renet.jp) website makes a big point of telling people to wipe their hard drives and even offers a paid service to do it for you.   Perhaps they "recycle" computers by re-selling them to people in less-developed nations or something, in which case identity theft could be a problem.   Other than changing my passwords for various services I was signed in to, do you have specific ideas about something I should do at this point?  Thanks.

---

### Post by sudodus on 2023-10-28
> **anotherChris said:**
> ...   How would you rate my risk (i.e., how hard would it be to get data off the drive.. i.e., are there methods that could easily be done on any drive that would recover data...)?    And other than changing passwords for services like Gmail, would you do anything in particular?    (For example, do I need to change my wi-fi router password?)   Thanks.

I am not an expert, so I cannot rate your risk. Probably the people who repair your computer don't spend time trying to extract passwords from their customers, but you cannot be sure about that. So I think it is a good idea to change important passwords.

---

### Post by TheFu on 2023-10-28
> **anotherChris said:**
> I got this laptop as a hand-me-down from someone, so I don't know, but I assume it had an HDD because it was quite old (~12+ years?).   I don't know what this [www.renet.jp](www.renet.jp) service does with old stuff.  They advertise that they employ handicapped people to take apart and recycle computers, but I don't really know.  I am not concerned about a government, but I am concerned because the [www.renet.jp](www.renet.jp) website makes a big point of telling people to wipe their hard drives and even offers a paid service to do it for you.   Perhaps they "recycle" computers by re-selling them to people in less-developed nations or something, in which case identity theft could be a problem.   Other than changing my passwords for various services I was signed in to, do you have specific ideas about something I should do at this point?  Thanks.

I think you are screwed if someone wants to do you harm. You leaped before you looked, I'm sad to say.

A friend had two smartphones stolen during a trip to Europe in the same week. Both were unlocked and he didn't have any password/encryption on the devices.  He changed all his logins that were on the device, but there's lots of other data there as well.  The phone data was cloned and wiped clean ... then sent two different ways.

Phone A was sent to central Africa and resold in a very poor country.
Phone B was sent to Indonesia and resold.
The two countries involved aren't part of the group of countries where stolen devices are blocked which includes Europe and nearly all the Americas + Japan, Korea, Taiwan.  We both worked in telecom and had coworkers who could trace where the phones finally showed up in the world about 2 months.

As for the data, it was sold to organized criminals.  Within 1 hour of the phones being stolen, he'd sent a remote wipe request.  It failed. They knew enough to never power on the phone where it could contact any cell network and receive instructions.  

All his business contacts, friends and family were contacted and phished for over a year. They would email, text, and voice call trying to get them to pay for bail, buy a gift card, and one person was actually threatened.  The closer friends had more information in the phone, so they got the worst hassles.  He used gmail for his private email. Even without access to Google's servers, all those contacts and notes were accessible on the phone.  With a laptop, I can only imagine how much more data it will hold than a phone.

Why do you care about browser history?  Does that really matter?  It might be slightly embarrassing, but it isn't like you setup automatic logins, right?    Whenever I'm doing something of any sensitivity level, I run my browsers inside a firejail container so they aren't allowed to save anything local.   I use a different system for online banking, never my main system. That other system uses a read-only version of Linux and doesn't have a HDD connected, so nothing can ever be stored to be compromised.

Perhaps it isn't too late to pay the recycler to wipe the drive?  If it is an SSD, there's no way to fully wipe the data on it.  I've seen articles that claim being able to restore data for over 50 layers of writes from some SSDs.  My answer for SSDs that die is to physically destroy the device, break every component to tiny pieces and split up where those pieces end up in garbage around the city.  Using thermite has always been on my list. I need to order some and dig a hole to fully destroy some old HDDs after drilling through them 4+ huge holes.  I never give way or sell a computer with one of my SSDs or HDDs included. The risks are just too great in my estimation.

Of course, you could get lucky and have the drive end up with a family that just wanted a computer for their 8 yr old to play educational games on.  They will never look for or see the old data ... until they recycle it in 10 yrs and the next person decides to look for interesting data on the HDD.  Some of your data will likely still be there.

---

### Post by anotherChris on 2023-10-28
> **TheFu said:**
> With a laptop, I can only imagine how much more data it will hold than a phone.

Why do you care about browser history?

I'm not sure, but I would assume the laptop actually has less data than a phone, as my contact lists, etc are not embedded in the computer anywhere.  I have already done "Sign Out of All Devices" for important websites and changed passwords.  And, yes, I was automatically signed in on numerous sites, which is why I care about browser history.   I agree about breaking up hard drives, and I have removed them from all other devices I have recycled or thrown away.  Just, this one, for some reason, I couldn't unscrew the case.

---

### Post by TheFu on 2023-10-28
> **anotherChris said:**
> I'm not sure, but I would assume the laptop actually has less data than a phone, as my contact lists, etc are not embedded in the computer anywhere.  I have already done "Sign Out of All Devices" for important websites and changed passwords.  And, yes, I was automatically signed in on numerous sites, which is why I care about browser history.   I agree about breaking up hard drives, and I have removed them from all other devices I have recycled or thrown away.  Just, this one, for some reason, I couldn't unscrew the case.

I hope you at least booted from a flash drive and deleted all the file systems and partition table before sending off the system. After all, it is unlikely to get a Linux OS if given to someone else.  

They might just split out the components and ship them to somewhere in SE Asia to be disassembled for the metals and then have the rest junked.  I've seen where a news team followed "junked" computer components from the US on a ship to Indonesia and found huge piles of the stuff. Lots of locals would bring a cart to that location fill it up and cart it back to their workshop to take apart. If new enough, the parts would be reused. If now, the more expensive metals would be captured and sold.  The most common stuff - plastics, glass, and iron-based things would end up in a trash hill.

---

