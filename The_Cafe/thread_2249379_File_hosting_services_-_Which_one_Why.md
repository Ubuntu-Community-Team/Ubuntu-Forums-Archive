---
title: "File hosting services - Which one? Why?"
date: 2014-10-21
forum: The Cafe
---

### Post by chaaderf on 2014-10-21
I searched a bit about this topic, but I was not able to find any good one. In case there is a thread about this, feel free to point me to the thread. So here we go.

I've heard that many people use some kind of service to host files e.g. dropbox, etc. But my knowledge of all this kind of stuff is *very* low. Just a while ago I find that in some cases it could be a good thing to have one, mainly for backups. But. At this point I'd like to hear your comments and opinions. So some questions:

Which one is good for you and why?
What is the most important features you appreciate in such cloud based service?
Is there some service that is easy for beginners like me? A free one, perhaps?
Anything else what should be taken into account while choosing the hosting service?

Thank you!

---

### Post by DogMatix on 2014-10-21
[Dropbox]("https://www.dropbox.com/") is still my prefered option even though it's free plan is only 2GB. It's reliable and has Linux, WIN and Mac OS clients. Its grown in popularity meaning that often people I work with use it, which means, I can set up shared folders with clients or colleauges to share and provide project files quickly and easily. I can also link to files in the Public Folder so non-dropbox users can accesss files.

I also use [Copy]("https://www.copy.com/home/") which has a 15GB free plan. However, I find updating files slower than Dropbox and I have had issues with the 'undelete' feature eating up my storage space. One thing I will mention is the excellent and prompt customer support I received in fixing this issue. Linux, WIN and Mac OS X clients are available.

Another sychronising file storage I use is [Hubic]("https://hubic.com/en/"). They provide a generous 25GB for free. There is a Linux client although it is in Beta testing. There is a deb file available for Ubuntu to simplify matters, but, there is no GUI to aid setup so you will have to use a Terminal. This hasn't proved an issue though and if you follow the instructions provided carefully. The customer support for Hubic isn't quite as crash-hot as it could be.

---

### Post by PondPuppy on 2014-10-21
I use CloudMe, a service based in Sweden. There are concerns about data security. But I hardly store anything online, and anything important I store I encrypt first, so it's mostly moot. 

The Register tends to be a bit hysterical in outlook sometimes, but here's a link anyway. Enjoy.

[http://www.theregister.co.uk/2014/10/21/skyhigh_data_protection_risks_survey/](http://www.theregister.co.uk/2014/10/21/skyhigh_data_protection_risks_survey/)

---

### Post by speedwell68 on 2014-10-22
AFAIK Dropbox now offer 50GB free.  I find it to be a pretty good solution.  It works on anything with a web browser.

---

### Post by ibjsb4 on 2014-10-22
> **speedwell68 said:**
> AFAIK Dropbox now offer 50GB free.  I find it to be a pretty good solution.  It works on anything with a web browser.
Must be for new accounts only, I'm not getting the option.

Edit
Here's a comparison of a few.
[http://www.cnet.com/news/is-dropbox-cloud-storage-too-expensive/](http://www.cnet.com/news/is-dropbox-cloud-storage-too-expensive/)

---

### Post by kc1di on 2014-10-22
Hi I use spider oak - I use dropbox some , but spider oak encrypts all your uploads and is believed to be more secure if that is a concern for you.

---

### Post by mastablasta on 2014-10-22
Mega doesn't have any clients but it is encrpyted and has 25 Gb.

Google drive (Google) and One drive (Microsoft) both not encrypted (user side) but offer quite a bit of free space. depends what you need these for.


anyway main issue is why do you want to use them? what do you need them for?

Spideroak is encrypted (I mean user side) but a bit slow. still it is good enough for occasional backup of some important things you want encrypted. has a GUI and is easy to set up. 3 GB free

Dropbox has only 2 GB free. and osme other limits. but might be good enough for start

you can also set one up yourself. :P (see--> owncloud)

---

### Post by chaaderf on 2014-10-22
Thank you for replays so far!

As I mentioned, I'll probably create an account to some cloud service for backups, but I'm not sure, do I really need it. But all this info has been very illustrative and I appreciate it very much. 

The encrypting thing... If a service doesn't do it, should I do it on someway? I think, I've read something about it, but indeed, I'm not sure is it needed or how to do the encryption even though there should be tools (in *buntu variants) for it too. And further, if I'd encrypt the files myself, what would be a suitable method? One quide I read, said that AES-256 in GnuPG would be enough.

As for the OwnCloud, yes, it is very compelling option. However, I don't have any device that I'd run as a server... But I afraid, once I get one, it may be my choise. :D

---

### Post by DogMatix on 2014-10-22
> **mastablasta said:**
> Mega doesn't have any clients but it is encrpyted and has 25 Gb.



Hi Mastablasta

I think Mega has updated its free quota and available software.

[Mega]("https://mega.co.nz/") now offers Linux/Mac/Win clients and has 50GB of storage that is encrypted end to end which is a good thing for those of us who upload national secrets or personally sensitive files to the cloud. You can also share encrypted folders with other users. The only draw back is a 12TB bandwidth cap (on the free account) and if you forget your password you lose access to your uploaded files.

---

### Post by mastablasta on 2014-10-23
> **chaaderf said:**
> Thank you for replays so far!

As I mentioned, I'll probably create an account to some cloud service for backups, but I'm not sure, do I really need it. But all this info has been very illustrative and I appreciate it very much. 

The encrypting thing... If a service doesn't do it, should I do it on someway? I think, I've read something about it, but indeed, I'm not sure is it needed or how to do the encryption even though there should be tools (in *buntu variants) for it too. And further, if I'd encrypt the files myself, what would be a suitable method? One quide I read, said that AES-256 in GnuPG would be enough.


sure you can do the encryption. most if not all of the services have it but they also have the keys. the proper way to do it is that user has one key, server has one key. server can't unlock access to files without the user key and password. at the same time server key keeps the data locked. you know kind of like the bank safe deposit box. they have one key you have the other. while they keep the safe and they have master key to the vault, they do not have access to what is inside the safe deposit box. so if bad people get access to the boxes they still need your key to open them (unless the use brute force which in computer and with good keys would take at least a couple of thousand years if not milions)

if you encrypt the data yourself and then send them to server it would be ok. 

> 
As for the OwnCloud, yes, it is very compelling option. However, I don't have any device that I'd run as a server... But I afraid, once I get one, it may be my choise. :D

you need descent internet connection, preferably static IP, and hardware. hardware can be old PC or something that uses low power (Atom board PC, intel Celeron U series PC) proper server (The HP micro N54L Gen 7 if you can still find it is an excellent home server - they are selling them very cheap nowadays), or you can buy proprietary NAS device (something like Synology NAS, WD my cloud - cheapest ones cost about 110 EUR without hard disks). proprietary devices do not have owncloud (mostly) yet they have their own cloud version, can encrypt files... usually the cheap ones are not great on specs (but they are low on power usage) , but more expencive ones can be expencive. all of them are quite easy to use with a nice GUI.

If you are the only user doing the backup (I mean only one computer) then it is better/easier to setup external disk and set automatic backups to it (let's say you use something like Luckybackup, backintime or similar). you can access it safely from internet using SSH (or rather sFTP) protocol and can use a file browser such as Filezilla or if you use windows WinSCP will also do it fine.

cloud are more ment to share your work but of course you can also use them as backup.

for example I have my website setup to backup automatically to dropbox - the website doesn't really have any important data/I mean all that data is published on the web anyway (aside form passwords), so if someone broke in to dropbox they wouldn't get much... :-)

I also use them to share funny pictures from games with my bro.

> **DogMatix said:**
>  which is a good thing for those of us who upload national secrets or personally sensitive files to the cloud. .
shh don't tell them that...

I need to check them out again. I only signed up to it and uploaded one file, but then haven't had the pleasure of using them. I am in the process of setting up owncloud, so I might not need it. but then again you never know when it might come in handy.

---

### Post by ukripper on 2014-10-24
I use Amazon's AWS. Currently on free 1 year subscription. When time arrives end of next year will see what offers are available however I'm very happy with the service

So far AWS has never gone down for me running django/nginx projects on them without any issues.

---

