---
title: "Any recommended cloud backup services?"
date: 2016-04-28
forum: The Cafe
---

### Post by AbleTassie on 2016-04-28
I am using Ubuntu 14.04 LTS (Lubuntu). I want to backup personal files for free and will encrypt anything I think is all that sensitive. I don't have a lot of large files like photos or games or music. Mainly text and pdf documents. But I could probably use most or all of the free 15 GB that Google drive offers.

As I said, Google Drive allows 15 GB for free. I tried Google Drive the other day and thought I had backed up many files by selectively uploading them. But I checked Google Drive again today and it was empty. So I guess I was not really using it correctly. Now today I cannot even really see how to upload files to Google Drive anymore at least not very efficiently. I'm not sure Google Drive works very well for Lubuntu.

QUESTIONS: Does anybody have a suggestion(s) for a cloud back up service that is free and would probably work for me?

Thanks,

A.

---

### Post by UbuntuAddict99 on 2016-04-28
Hello AbleTassie,

Now i see what you mean getting a decent Cloud Storage provider is a bit hard nowadays everyone is giving the same deal but in my PERSONAL experience.
Microsoft's One Drive is by far the best just for having a Microsoft E-mail (Outlook, Hotmail, Live.) You automatically receive 15 Gigabytes free.
Plus if you use Microsoft Office it is perfect for your Documents that you said you need to backup. Now as for encryption. I have YET, to test it but try compressing your documents with a password i recommend 7Zip for the BEST possible compression rate.

And then uploading them to a cloud storage provider. Now i know this is a Linux forum but i have no regrets stating that Microsoft has a pretty decent Cloud Storage solution. but at the end of the day it is always up to you for what Cloud Storage provider you will use hope i have given some help.

Happy Linuxing.

---

### Post by AbleTassie on 2016-04-28
Thank you UbuntuAddict,

Can I use Lubuntu with Microsoft's cloud service? 

I rarely use Microsoft Office anymore, mostly Libre Office.

A.

---

### Post by UbuntuAddict99 on 2016-04-28
Yes, you can as long as you go to [www.onedrive.com](www.onedrive.com) to access your Cloud Storage there is a port for One Drive for Linux but it is unsupported or in Beta. iIcannot remember correctly but it is on Github.

Happy Linuxing.

---

### Post by DuckHook on 2016-04-29
*Your thread has been moved to **The Cafe** as the forum more suited to your issue.*

You will probably get more answers here. :)

---

### Post by Dragonbite on 2016-04-29
If you are looking for online access, I and up splitting between Google Drive and OneDrive and Dropbox but nothing is ideal.  I use Google Drive for Google Docs (free), Photos (free if you size it right) and OneDrive for my "professional" and volunteer organization related stuff.  SpiderOak is another one, and it includes encrypting without keeping the keys from the start, and is Linux-friendly.

I don't know if they will run it again, but about a year ago Bing was running a reward (you get "Bing points" for searching with Bing) for 100GB of OneDrive space for free for 2 years.  I haven't seen that available lately but I'm still using the extra 100 GB.  I don't rely on it, though, because once the free period is over, I am NOT paying for it.

If you are looking just to have a backup and it doesn't need to be accessible to the Internet, or you are savvy enough about networking and the like you can set up your own ownCloud server!

Setting up ownCloud is very simple.  I don't have mine Internet-facing, just using it as an internal file synchronization server (with web access).

Oh, I an I have heard Mega ([https://mega.nz]("https://mega.nz")) offers 50 GB of cloud space, but the sync client is Windows-only.

---

### Post by mcduck on 2016-04-29
I'm using HubiC, pretty good this far, not as full-featured as Google Drive but they have clients for Windows, Mac, Linux, Android & iOS. Free account gives you 25GB of space. I'm using a 120€/year account which gives me pretty decent 10TB of cloud space.... (also that one is on discount now for 50€/year).

Then again, it's probably only great if you are from Europe, as their servers are in France.

I can't remember if they have any built-in backup features, I'm just using Deja Dup to do it (and Duplicity on the Windows side of my laptop).

---

### Post by jay_bowles2 on 2016-04-29
I quite like Mega [https://mega.nz/](https://mega.nz/) which is based in New Zealand. I believe they still offer 50Gb of free cloud storage... worth a look? They seem to respect privacy as well :)

---

### Post by AbleTassie on 2016-04-29
Thanks to everybody, I will look carefully at each suggestion.

Able

---

### Post by fyfe54 on 2016-04-30
I use Mega and the Linux sync works.   Check here for downloads:  [https://mega.nz/#sync](https://mega.nz/#sync)

---

### Post by O)9(yo&amp;# on 2016-05-01
I use Box.com. Not a lot of space (10GB) , but it does have an audio player, which means I can use it to showcase my music. So far, I haven't used up anywhere near the 10 GB, so it works out for me. But then I'm a simple man.

---

### Post by Cammy_White on 2016-05-01
I personally use MEGA for backups, you get 50 GB free.
The only thing is that MEGA has a lot of glitches sometimes and also is associated with piracy.

However it offers more than any other provider so yeah also I don't host anything illegal with it.

---

### Post by Dragonbite on 2016-05-02
I can't use Mega... I already have 60+ GB stored on my ownCloud.  Darn digital pictures, takes a lot of space...

---

### Post by AbleTassie on 2016-05-04
Thanks to everybody. I will wait a while longer then mark this thread as SOLVED.

A.

---

### Post by Habitual on 2016-05-04
What ever service you choose, please consider encryption or compression with a password before you upload.
Point is, don't rely on some software, or service to supply Security.

---

### Post by mastablasta on 2016-05-05
why does it have to be "cloud"? 

what about if you setup your own cloud?  

and if you don't want to fiddle too much with this just get an external hard drive. you can also get a networked drive for 130 USD or something like that.

---

### Post by Dragonbite on 2016-05-05
I got a GoFlex network drive from Costco the other day and the handy thing is that it can make itself Internet-facing or not at your choice.  Combined with NoIp or DynDNS and you wouldn't have to worry about finding your home's IP address.

Come to think about it, I just had a thought of putting my goflex at my parent's house and set up a routine that backs up from my ownCloud server to that overnight (when I know my parents aren't using the Internet). That way it is out of the house, and not costing me cloud storage prices.

I mean, can probably set one up w/Ubuntu but this is already built-in and easier...

Hmm....

---

### Post by AbleTassie on 2016-05-06
Hi Habitual,

Thanks. I've been looking into compression software with a password.

Mastablasta,

Thanks, I am worried about mechanical failure, so I don't want to rely on a peripheral hard drive. I have an older mechanical peripheral hard drive that is 160GB; it is not a SSD. My financial situation is such that I do not want to spend a lot of money right now. 

Hi Dragonbite,

Thanks, the GoFlex drive is a Seagate, correct? I assume it is not a SSD, correct? Interesting idea about how to use it at your parents house; I do not have another place to put it other than my residence.

Thanks again,

A.

---

### Post by mastablasta on 2016-05-08
> **AbleTassie said:**
> 
Mastablasta,

Thanks, I am worried about mechanical failure, so I don't want to rely on a peripheral hard drive. I have an older mechanical peripheral hard drive that is 160GB; it is not a SSD. My financial situation is such that I do not want to spend a lot of money right now. 


that's understandable. well as others have said Mega has 50GB (encrypted).

still when financial situation does improve i suggest you look into those networked drives. 

another cheaper option would be just to use an external USB drive. they go for about 50 EUR for 500GB here. this is ofcourse if you do not need some natural disater proteciton. in that case cloud is better.  you could also add an internal drive and use it only for backup.

cloud is usually also used to access data from any place with internet. so it's a bit more than just simple backup. cheapest owncloud can be contructed using raspberry pi, but liek i said they also have networked drivers now and soon after that cheapest NAS units with 2 RAID1 drives start.

but from what i undertsand now you just want a backup of your data. get an external drive and setup a script or use a GUI (maybe something like Areca, luckybackup, dejadup...) to do autobackups. if this is some static data (eg. photos, videos that do not change) then just use a script that will copy files from a certain folder onto an external drive. 

it all depends what kind of backups (file types -static, dynamic?), if you need data versioned or not, if you need natural disaster protection, does it have to be encrypted etc. and also how you intend to recover. 

i stored some important document scans on SpiderOak. this could be used in case of any natural disater. while i do not have such protection for my photos or videos. they analogue ones are on paper in a drawer and digital ones are on 2 different hard disks. all in the same room. there is just too many of them to be able to afford a cloud for all. we are at arround 100 GB and still increasing.

---

### Post by Dragonbite on 2016-05-09
> **AbleTassie said:**
> 
Hi Dragonbite,

Thanks, the GoFlex drive is a Seagate, correct? I assume it is not a SSD, correct? Interesting idea about how to use it at your parents house; I do not have another place to put it other than my residence.

Thanks again,

A.
No, it isn't an SSD. 

Mine is a 2 TB I got a few years ago from Costco.  They now have up to 4 TB sizes.

I am not 100% happy with the built-in OS, but it works. I would rather have more control over everything but the OS does allow me to do what I want.

I understand about wanting to be cautious about mechanical failure.  I did have 1 time I had to send it back under Warranty and they sent me a new drive. That's why I am trying to look at redundancy (backing up the ownCloud server for instance).

The thing that scares me about real-time synchronization (cloud or even ownCloud) is Ransomeware.  If your system gets infected and it propagates to the synchronized location (where ever it is) then as that as a backup is no good.  I think the only protection from this is point-in-time backups.

Since Ubuntu is so easy to install (I have a USB stick I keep updated with currently used releases) if I am caught with ransomeware I can wipe off the entire drive, reinstall via USB and copy my files from backup and only lose some of my most recent data, but not everything.

Cloud is good for catastrophic events (house burns down) but unless you run your own server, you are at the mercy of the service provider.  I know the precursor to Mega (Mega Upload?) had the legal issue about copyrights(?) and everybody lost the ability to connect for like a week before they started opening select "clean" accounts.

It depends on your technical capabilities I guess, using Amazon Web Services could set up a cloud-based FTP location to store files.  I don't know the cost but it may be on as "as you use" basis (more data for more money) and with the benefit of virtually no upper limit (except your wallet).  Dropbox uses AWS for its site and users' files.

---

### Post by kevdog on 2016-05-10
Does anyone have experience with cloud backup site that allows either ssh/sftp -- I've kind of narrowed by suggestive offsite backup to have capabilities to accept either an obnam or borg backup -- both encrypt backups, make use of hard links to avoid deduplication, and allow for mounting of remote encrypted directory via fuse module.  I don't have any system right now that can no straight ZFS snapshot backups, but that would be another option if I had the capability.  Both obnam and borg can encrypt -- obnam via GPG with keys and borg via a password I believe doing AES encryption.  The only other such backup utility that could do this I think is duplicity however I've read every few months the entire archive needs to be re-uploaded -- which is obviously a major negative if the backup is several GB in size.

---

### Post by mastablasta on 2016-05-10
> **Dragonbite said:**
> 
The thing that scares me about real-time synchronization (cloud or even ownCloud) is Ransomeware.  If your system gets infected and it propagates to the synchronized location (where ever it is) then as that as a backup is no good.  I think the only protection from this is point-in-time backups.

owncloud has versioning of files available. 

[https://doc.owncloud.org/server/8.2/user_manual/files/version_control.html](https://doc.owncloud.org/server/8.2/user_manual/files/version_control.html)

but it (Owncloud) is not really meant as a backup i believe. it is more aimed at sharing your things with others and collaborative work.

---

### Post by mastablasta on 2016-05-10
> **kevdog said:**
> Does anyone have experience with cloud backup site that allows either ssh/sftp 

every hosted server or VPS Will get you that. 

you then only need a program that will transfer the data automatically over ssh. have you checked Duplicati and duplicati 2.0? What about Areca? or rdiff-backup?

---

### Post by AbleTassie on 2016-05-19
Thanks to everybody. I am going to mark thread a SOLVED. 

A.

Edit: well I thought I could mark it as SOLVED, but it does not  appear that I can do that for some reason.

---

### Post by QIII on 2016-05-19
You can't mark it solved because it's in the Cafe.

---

### Post by LK_gandalf_ on 2016-11-20
I was also curious about Mega, it seems too good to be true....50gb free and tons of clinets for linux and windows? Is there a catch? What about privacy?

---

### Post by C.S.Cameron on 2016-11-20
I use, (but not often), Box.
They gave me something like 50GB or 75GB free to start.
Not had any problems so far, (knock on wood).

---

### Post by 7dEfOk4AgU on 2016-11-20
> **LK_gandalf_ said:**
> I was also curious about Mega, it seems too good to be true....50gb free and tons of clinets for linux and windows? Is there a catch? What about privacy?

I would not go near Mega at all

---

### Post by mastablasta on 2016-11-21
> **LK_gandalf_ said:**
> I was also curious about Mega, it seems too good to be true....50gb free and tons of clinets for linux and windows? Is there a catch? What about privacy?

it's like with other file sharing/cloud sides. you do not know exactly what happens there in the background. but Mega has your data encrypted. if there are any backdoors we do not know. but supposedly there aren't.

the founder made it cause they took down his previous site megaupload which was not encrypted so it got hacked and taken down by FBI. anyway he vowed to restart it and make it fully encrypted. as i understand the onwership of mega transfered to another entity (company?!), but encryption is an important part of their marketing.

[https://en.wikipedia.org/wiki/Mega_(service)](https://en.wikipedia.org/wiki/Mega_(service))
> Mega most notably advertises its feature that all files are encrypted locally before they are uploaded[SUP][[SIZE=2][3][/SIZE]]("https://en.wikipedia.org/wiki/Mega_(service)#cite_note-3")[/SUP] and 50 [GB]("https://en.wikipedia.org/wiki/Gigabyte") of storage space are available for free[SUP][[SIZE=2][4][/SIZE]]("https://en.wikipedia.org/wiki/Mega_(service)#cite_note-free_space-4")[/SUP] and up to 4 [TB]("https://en.wikipedia.org/wiki/Terabyte") for paid accounts.[SUP][/SUP]
> 

[h=2]Data encryption[[edit]("https://en.wikipedia.org/w/index.php?title=Mega_(service)&action=edit&section=2")][/h]



Dotcom has said that data on the Mega service will be encrypted [client-side]("https://en.wikipedia.org/wiki/Client-side_encryption") using the [AES]("https://en.wikipedia.org/wiki/Advanced_Encryption_Standard") algorithm. Since Mega does not know the encryption keys to uploaded files, they cannot decrypt and view the content. Therefore, they cannot be responsible for the contents of uploaded files.[SUP][[SIZE=2][36][/SIZE]]("https://en.wikipedia.org/wiki/Mega_(service)#cite_note-36")[/SUP] Dotcom stated that encrypting files allows them to work with a larger number of data hosting companies around the world, decreasing the likelihood of a Megaupload-style seizure of servers by one government. He mentioned in an interview with [Ars Technica]("https://en.wikipedia.org/wiki/Ars_Technica") that "Each file will be kept with at least two different hosters [sic], [in] at least two different locations," and "That&#8217;s a great added benefit for us because you can work with the smallest, most unreliable [hosting] companies. It doesn&#8217;t matter because they can&#8217;t do anything with that data."[SUP][[SIZE=2][37][/SIZE]]("https://en.wikipedia.org/wiki/Mega_(service)#cite_note-ars_interview-37")[/SUP]
In the first few weeks after the Mega launch, various security problems were found that researchers said an attacker could use to gain access to a logged-in user's files.[SUP][[SIZE=2][38][/SIZE]]("https://en.wikipedia.org/wiki/Mega_(service)#cite_note-SO_attackers-38")[/SUP][SUP][[SIZE=2][39][/SIZE]]("https://en.wikipedia.org/wiki/Mega_(service)#cite_note-mega_blog_3-39")[/SUP][SUP][[SIZE=2][40][/SIZE]]("https://en.wikipedia.org/wiki/Mega_(service)#cite_note-mega_blog_4-40")[/SUP] In response, Mega started a vulnerability reward program which offers a reward of up to &#8364;10,000 for reporting security problems to Mega.[SUP][[SIZE=2][41][/SIZE]]("https://en.wikipedia.org/wiki/Mega_(service)#cite_note-mega_blog_6-41")[/SUP]
The Mega team indicated that some companies, such as film studios, will have direct access to remove files if they discover the encryption keys online and determine that the content infringes their copyright. Dotcom added that if such companies want to use that tool they would have to agree, prior to receiving access, not to sue Mega or hold the site accountable for the actions of its users.[SUP][[SIZE=2][42[/SIZE]]("https://en.wikipedia.org/wiki/Mega_(service)#cite_note-cnet_rises-42")[/SUP]


---

### Post by Dragonbite on 2016-11-21
I've got 1.5 TB available for me on my ownCloud.

---

### Post by kennster2 on 2016-12-07
I would say dropbox has done a pretty good job for me.

---

