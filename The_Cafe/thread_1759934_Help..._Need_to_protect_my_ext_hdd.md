---
title: "Help... Need to protect my ext hdd"
date: 2011-05-16
forum: The Cafe
---

### Post by aschwerin.moses on 2011-05-16
Hi all....

I have checked for few options but none seem convincing to me.

So. I have a 1TB hard drive with all my stuff in it. Now the problem is that my friends/roommates use it to access movies, music, etc. I dont have a problem with sharing it with them, however they do not know how to keep their laptop's free from Virus.

One of my friends did a mistake by giving his 1TB hdd to a friend (girl-no offense). He gets the hdd back but to only discover 5631 virus. Yes, he remembers the number because it took him a lot of time and effort to clean it without formatting the hdd.

I dont want this to happen. I want to protect my HDD and im here so that you guys can give me few options.

My options were as follows. 
- Install ubuntu in the external hdd, convert the entire hdd into ext4. The only way to access the files is to boot to ubuntu..... Now im not sure if this hdd can be used on multiple laptops. Will that mess the drivers?
- Use an encryption software to encrypt the hdd. But if one connects the hdd to virus filled system and access the files, the virus should infect the files.

well.. i cannot think of anything more... please guide me.

Regards,
Moses...

---

### Post by tmette on 2011-05-16
> **aschwerin.moses said:**
> Hi all....

I have checked for few options but none seem convincing to me.

So. I have a 1TB hard drive with all my stuff in it. Now the problem is that my friends/roommates use it to access movies, music, etc. I dont have a problem with sharing it with them, however they do not know how to keep their laptop's free from Virus.

One of my friends did a mistake by giving his 1TB hdd to a friend (girl-no offense). He gets the hdd back but to only discover 5631 virus. Yes, he remembers the number because it took him a lot of time and effort to clean it without formatting the hdd.

I dont want this to happen. I want to protect my HDD and im here so that you guys can give me few options.

My options were as follows. 
- Install ubuntu in the external hdd, convert the entire hdd into ext4. The only way to access the files is to boot to ubuntu..... Now im not sure if this hdd can be used on multiple laptops. Will that mess the drivers?
- Use an encryption software to encrypt the hdd. But if one connects the hdd to virus filled system and access the files, the virus should infect the files.

well.. i cannot think of anything more... please guide me.

Regards,
Moses...

I think putting Ubuntu on it is a pretty good idea.  This way they can still access their own HDDs from it and transfer data.  However if they still put an infected file on there, it will still be infected.  It just won't do anything to the Ubuntu OS.  If you transfer that infected file back over to a Windows PC, It will still infect the computer.

---

### Post by aschwerin.moses on 2011-05-16
Yes. I think that is the best options. But can one connect the hdd to multiple laptops and boot to ubuntu?.. what will not mess the drivers?

---

### Post by madjr on 2011-05-16
so i believe this is more to protect your friends computers from getting infected?

since you already have ubuntu , your own computer is protected.

---

### Post by madjr on 2011-05-16
> **aschwerin.moses said:**
> Yes. I think that is the best options. But can one connect the hdd to multiple laptops and boot to ubuntu?.. what will not mess the drivers?

should be similar to a bootable live usb/cd i believe.

if live cds work on their system, then there should be no probs.

---

### Post by tmette on 2011-05-16
Well, I never would have thought about the drivers issue.  They may run into a few issues such as possible wireless connections.  When you install the copy of Ubuntu on the machine, I wouldn't install the "recommended" graphics drivers or anything since they might have ATI where you have Nvidia.

They will probably have enough driver support to transfer/copy files.

---

### Post by aschwerin.moses on 2011-05-16
> **madjr said:**
> should be similar to a bootable live usb i believe.

If i install ubuntu in the hdd, will it work like a live usb?.. 

> **madjr said:**
> so i believe this is more to protect your friends computers from getting infected?

since you already have ubuntu , your own computer is protected. 

no no.. to protect the contents in my hdd. my laptops has windows 7 (office laptop).. so by not letting my hdd get infected with virus im going to keep the contents in the hdd safe and also my windows 7 laptop.


if i install ubuntu in the hdd. it will have the drives of my laptop. now if my friend connects it to his laptop will the drivers not mess the entire OS?

---

### Post by aschwerin.moses on 2011-05-16
> **tmette said:**
> Well, I never would have thought about the drivers issue.  They may run into a few issues such as possible wireless connections.  When you install the copy of Ubuntu on the machine, I wouldn't install the "recommended" graphics drivers or anything since they might have ATI where you have Nvidia.

They will probably have enough driver support to transfer/copy files.

yea. as long as they can copy/paste stuff into it and not use it completely. Well.. do you think it would be safer to create a GUEST user account with less control?

---

### Post by madjr on 2011-05-16
> **aschwerin.moses said:**
> If i install ubuntu in the hdd, will it work like a live usb?.. 

 

no no.. to protect the contents in my hdd. my laptops has windows 7 (office laptop).. so by not letting my hdd get infected with virus im going to keep the contents in the hdd safe and also my windows 7 laptop.


if i install ubuntu in the hdd. it will have the drives of my laptop. now if my friend connects it to his laptop will the drivers not mess the entire OS?

then install it as a live-usb with a persistent disk space.

that should work well for most systems.

ps. remember to backup and test this a few times, till you believe everything is working ok.

and in case it doesnt boot for any reason, you can always access the files from any ubuntu install or live-cd

---

### Post by 3Miro on 2011-05-16
Note: Encryption has no effect on protecting stuff from viruses. It only disallows other people from reading the files on it, if your friends have the password and permission to put files on the HDD, then they can put viruses.

---

### Post by Oxwivi on 2011-05-16
Install Ubuntu with ClamAV to protect against Windows viruses.

---

### Post by aschwerin.moses on 2011-05-16
installing ubuntu seems to be the only way. thank you guys.

well, anyone with another idea can please suggest me.

---

### Post by blueturtl on 2011-05-17
How about just formatting the HDD as EXT3/4 and then giving a LiveCD to your friend because "you can't use the disk with Windows anyway"?

Using the LiveCD has the benefit that it should boot on anyone's laptop. An installed system might get quirky if you keep switching the hardware underneath it.

Using a LiveCD allows your friends to transfer files to and from your disk without the risk of viruses (unless they transfer infected files, naturally).

---

### Post by aschwerin.moses on 2011-05-17
> **blueturtl said:**
> How about just formatting the HDD as EXT3/4 and then giving a LiveCD to your friend because "you can't use the disk with Windows anyway"?

Using the LiveCD has the benefit that it should boot on anyone's laptop. An installed system might get quirky if you keep switching the hardware underneath it.

Using a LiveCD allows your friends to transfer files to and from your disk without the risk of viruses (unless they transfer infected files, naturally).

now this is niceeee.. did not think of it.. nice nice nice


Is there anyway I can have the livecd stuff in the same HDD but in a separete folder. Like.. if I open the HDD parent folder.. it should have folders such as

Ubuntu Live CD (this is where the livecd files should be stored)
Music
Movies
Documents
Software
etc....

is this possible?

---

### Post by madjr on 2011-05-17
did you tried the persistent usb?

[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/)

[http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/)


also your friends having ubuntu on their machines as a second OS would be of benefit to them if windows fails.

i for example always download my stuff to ubuntu, then move it into windows (if necessary) after a scan.

i also avoid typing passwords or sensitive data in windows, because of the spyware and keyloggers. I had some of that info stolen with some online accounts and online games... ;/ , then after i use ubuntu, never happened again. Peace of mind is priceless. :)

---

### Post by aschwerin.moses on 2011-05-17
> **madjr said:**
> did you tried the persistent usb?

[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/)

[http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/)


also your friends having ubuntu on their machines as a second OS would be of benefit to them if windows fails.

i for example always download my stuff to ubuntu, then move it into windows after a scan.

i also avoid typing passwords or sensitive data in windows, because of the spyware and keyloggers. I had some of that info stolen with some online accounts and online games... ;/ , then after i use ubuntu, never happened again. I have peace of mind now. :)

Great.. now this is exactly what i was looking for. Never did know about this persistant option. Great feature, just read the links. Need to experiment.

think i got what i was looking for. ubuntuforums rocks as always :guitar:

---

### Post by jhonan on 2011-05-17
I might not be understanding this fully - But if you're using that ext. HDD as a file store, and connecting windows machines to it - it really makes no difference what OS you're running on the ext. HDD.

If you connect an infected windows PC to it, if the virus uploads itself to the ext. HDD it doesn't care what OS it runs - it just sees it as another drive.

If someone else connects to it with a windows PC, and run the .exe (or whatever file contains the virus) then their PC gets infected.

Although, this *would* require a virus which is capable of using an external hdd as an attack vector, with the target clicking on an executable... seems a bit unlikely.

I'd like to know in what way that ext HDD is getting 'infected'

---

### Post by madjr on 2011-05-17
> **aschwerin.moses said:**
> Great.. now this is exactly what i was looking for. Never did know about this persistant option. Great feature, just read the links. Need to experiment.

think i got what i was looking for. ubuntuforums rocks as always :guitar:

yes, both links have very good tips. I would read them both.

glad to help, and anything else just ask. Hope this works well.

---

### Post by madjr on 2011-05-17
> **jhonan said:**
> I might not be understanding this fully - But if you're using that ext. HDD as a file store, and connecting windows machines to it - it really makes no difference what OS you're running on the ext. HDD.

If you connect an infected windows PC to it, if the virus uploads itself to the ext. HDD it doesn't care what OS it runs - it just sees it as another drive.

If someone else connects to it with a windows PC, and run the .exe (or whatever file contains the virus) then their PC gets infected.

Although, this *would* require a virus which is capable of using an external hdd as an attack vector, with the target clicking on an executable... seems a bit unlikely.

I'd like to know in what way that ext HDD is getting 'infected'

well he wont be connecting "windows" machines.

instead he will be using ubuntu off the hard drive , so no auto-viruses will move themselves to that drive.

if you connect any drive into ubuntu you can even view all those virus files (which are invisible in windows file explorer).

he should definitely try it and see if it works for him.

---

