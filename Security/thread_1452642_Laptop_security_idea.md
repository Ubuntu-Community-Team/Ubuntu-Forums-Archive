---
title: "Laptop security idea"
date: 2010-04-12
forum: Security
---

### Post by schmidtbag on 2010-04-12
I'm sure some of you know that if your laptop comes with a built-in webcam, you can use it to take a picture of someone as your computer boots up and sends the image to a server.  But, finding a reliable service or having a server to upload the images to can be a problem for some people - especially if the thief is not near an internet connection.

In my opinion, having a computer with a login password may be useful to prevent someone from logging in and taking information easily, but with a few hacks they'll get in eventually and be able to take all your information, in which encryption is useless.

So, lets just say you are the only user of your laptop, and you have a working built-in webcam.  If you were to have your computer log in automatically, my idea is the webcam would take a picture of you and with facial recognition it would automatically shut down if it didn't see you as the current user.  Use this with a tracking system and you may be able to find your laptop without any harm being done to it.

Unfortunately I don't do much programming, so I can't develop something like this.  I hope someone reading this post can develop it, or knows someone who can.

---

### Post by marin123 on 2010-04-12
maybe you could buy more expensive laptop and have fingerprint recognition on it?
i dont have camera or fingerprint on my laptop, so i dont have much experience with this, but it seems like a good idea...
i dont know what do you mean by tracking your computer? gps or ip address? maybe you can just keep an eye on it ;)

---

### Post by xhalarin on 2010-04-12
The solution that you propose would only have limited usefulness (possibly not worth the effort to develop).  If you are interested in keeping un-knowledgeable friends and family off the computer, it could work (might as well just user login id/pwd in this case though).  However any semi-skilled linux user could by-pass such a program with a little time and physical access to the PC.

If you are truly interested in keeping  your data out of the hands of others, the best option is full disk encryption whereby a password is required **at boot** before the hard drive will be unencrypted.  There are programs available that can do this; it is not provided out of the box.

The other school of thought is for those who would like to recover their PC if it is ever stolen.  There are programs out there that will use the camera or other information available to the PC and "phone home" if the PC is ever stolen and proper credentials are not met.  Thus you could identify by IP address, screen-shots taken by the camera, etc if the PC is stolen and then turned on and plugged into the Internet.  Again, these mechanisms are somewhat easily bypassed by a skilled user, but do give you a chance of recovering stolen equipment.

The only way that your solution could work is if it was built into the firmware/pc itself.  Such mechanisms do exist and are not out of the realm of possibility, but you would have to be in pretty tight with the hardware vendor to make it happen.  As an example, Dell has a TPM platform that ties together biometrics with the BIOS and software within the OS also to allow you to boot the PC and subsequently into Windows via biometric scanning.

Pretty cool stuff and it's something that I'm sure we'll be seeing a lot more of in the future.  You might want to patent your idea and begin negotiations with the hardware vendors :)

---

### Post by schmidtbag on 2010-04-12
@xhalarin
I see what you mean but i wasn't really referring to my idea as being the only form of security, because you're right, it is kinda useless by itself.  But, like I said before, if you were to do a tracking system, screenshot, and mugshot and THEN shut down the computer, you'd decrease the chances of someone getting into your stuff and you'll be able to find them as they attempt to figure out how to stop it.

keep in mind that most people don't use linux.  If someone steals a computer, i'm sure its the last thing they expect to encounter.  therefore, while being unprepared, having a combination of security measures will greatly annoy a thief.  As I see it, if i can't get my laptop back, i'd prefer it to be useless to whoever stole it.  Currently on my laptop I put a password on BIOS, there is no CD drive, and the bootloader is configured to only boot my pci-e based SSD.  This way, someone can't easily install their own OS.

I do currently use an IP tracking system, and I use a fingerprint reader to access certain things, but if my laptop were to be stolen, I'd like to annoy and frustrate the thief as much as possible.

---

### Post by CharlesA on 2010-04-12
I've said it before: physical access = root access.

Even if they didn't want your data, they would probably just wipe the drive. There are ways around BIOS passwords.

---

### Post by tubbygweilo on 2010-04-12
> I've said it before: physical access = root access.
Says it all.

If a thief can not at once make use of a stolen laptop then I expect it will be discarded without too much thought, after all she would not like to be associated with stolen goods any longer than is absolutely necessary.

---

### Post by Sir Jasper on 2010-04-12
Hi,

[http://preyproject.com/](http://preyproject.com/) might be of interest to Linux and Windows laptop owners?

My regards

---

### Post by Agent ME on 2010-04-12
If someone has stolen your laptop and brought it somewhere else, and you have a program that takes a picture to send it - what internet connection is it going to use? They can't log in to choose a wireless network to connect to.

---

### Post by texaswriter on 2010-04-12
oh whatever, automatic picture taking every time you load.... and automatically uploaded to server... dang, would have to brush my hair before i turn on computer in the morning... oh yeah, and put clothes on... how 'bout naw :lolflag:

---

### Post by schmidtbag on 2010-04-12
> **Agent ME said:**
> If someone has stolen your laptop and brought it somewhere else, and you have a program that takes a picture to send it - what internet connection is it going to use? They can't log in to choose a wireless network to connect to.

thats exactly the point of what my topic is about - if you can't track them, you can at least annoy them

---

### Post by aysiu on 2010-04-12
It's theoretically possible but highly unlikely.

It has worked when the stars are aligned, though:
[http://www.cjreport.com/news/3712/laptop-thief-caught-on-webcam-by-owner.html](http://www.cjreport.com/news/3712/laptop-thief-caught-on-webcam-by-owner.html)

Best thing to do is to physically secure the laptop. If someone steals your laptop it's usually for the hardware, not for your info.

---

### Post by dgw on 2010-04-13
> **schmidtbag said:**
> In my opinion, having a computer with a login password may be useful to prevent someone from logging in and taking information easily, but with a few hacks they'll get in eventually and be able to take all your information, in which encryption is useless.
Someone with physical access can easily circumvent a login password. They can't get past encryption though. Use full-disk encryption and the thief's only option will be to reinstall the OS. 

I have a program called Motion installed on one of my computers (running Ubuntu 9.10), which records only when it detects motion. I put a launcher on my panel so I can start it with one click (with a 30 second delay so that it doesn't record me leaving), and I have it email me still images immediately if it detects motion(configured in the conf file for Motion, and with a short bash script). If someone breaks into my room when I'm not here, I'll have pics of them doing it, even if they steal the computer that's taking the images. It was easy to set up.

---

### Post by Agent ME on 2010-04-13
> **dgw said:**
> I have a program called Motion installed on one of my computers (running Ubuntu 9.10), which records only when it detects motion. I put a launcher on my panel so I can start it with one click (with a 30 second delay so that it doesn't record me leaving), and I have it email me still images immediately if it detects motion(configured in the conf file for Motion, and with a short bash script). If someone breaks into my room when I'm not here, I'll have pics of them doing it, even if they steal the computer that's taking the images. It was easy to set up.
This is a much better idea than hoping that a thief will boot your computer to linux later and somehow have an internet connection then. With many cellphone services, you can even email the picture to an address associated with your phone (for Verizon, it's ##########@vzwpix.com) which will send the picture to the phone immediately as a picture message.

---

### Post by xhalarin on 2010-04-13
I agree, Motion is a good idea.  I've always wanted a program like that, but hadn't come across a good one.  I'll have to look that up.  Thanks.

---

### Post by Jive Turkey on 2010-04-14
> **CharlesA said:**
> I've said it before: physical access = root access.

Even if they didn't want your data, they would probably just wipe the drive. There are ways around BIOS passwords.

Thieves are not generally the most sophisticated people around however.  Often they are just out to sell the thing for drug money ASAP so they might just fire it up and log on to ebay or craigslist or something.

---

