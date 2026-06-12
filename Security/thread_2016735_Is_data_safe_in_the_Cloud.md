---
title: "Is data safe in the Cloud?"
date: 2012-07-04
forum: Security
---

### Post by youknowme on 2012-07-04
Excuse my ignorance. I do not know anything about the cloud other than that data is stored on some remote server somewhere which apparently implements bullet proof security measures.

I am not pointing at Ubuntu specifically - just all clouds generally.

I instinctively have a great distrust of this new trend - not based upon fact, just a gut feeling. Do you understand what i mean?

---

### Post by deadflowr on 2012-07-04
In general, the cloud is reasonably safe. All the cloud is is massive data storage servers, any reputable cloud service provider will be storing the data encryptly. But like any server or computer system, they are prone to neverending onslaughts of attacks and so forth. Whether or not the cloud service can handle that is one thing, diciphering the encrypted content is another. For me, I'm more concerned with how well a service backs up the data, in case the storage drives fail.

---

### Post by thnewguy on 2012-07-04
When people refer to the cloud they usually mean data or services on servers they do not control. This can be useful, certainly, when used properly. Your e-mail, for example, is probably handled by a remote server. Chances are you have a blog or website which is run on someone else's server. It's convenient. These could loosely be considered cloud services.

However, two things the cloud are not are secure and "bullet proof". You should work under the assumption that anything stored in a cloud or services run in a cloud could disappear at any time or could be hacked at any time.

Look at MegaUpload, Amazon's cloud service, Microsoft's cloud service, etc. All of them have had major downtime this year due to software bugs or legal issues.

Your distrust is very valid, cloud storage is not designed to be secure nor reliable, it's designed to be convenient as long as both you and the service provider can maintain Internet connections. My advice is to make use of cloud storage if you have a use for it, but make sure your data is also backed up somewhere else, somewhere you control. Also, don't save anything to the cloud of a sensitive nature (tax returns, contracts, financial data) unless it is encrypted.

---

### Post by Hungry Man on 2012-07-04
That really depends.

On the one hand a large company can afford to have administrators who are paid to look through logs and check IDS and IPS denials etc, which can stop attacks.

On the other hand you also have the issue of those administrators often having access to the files.

My suggestion is that you encrypt everything locally and *then* upload it. This way the attacker can't get in even if they control the server.

---

### Post by msammels on 2012-07-04
To be fair, the cloud can be useful. Technically, email is in the cloud. I mean, I wouldn't trust my personal documents there, or important ones without a backup, but it is a solid idea.

---

### Post by ottosykora on 2012-07-05
I have come over one storage service which seems very secure.
[www.wuala.com](www.wuala.com)

The special thing is, that with wuala, all data is encrypted on your own computer before travelling to the server. No passwords or keys are sent over the net, all is done locally. So even the operators of the servers are not able to access the data.
The data is then stored in secured servers in a raid, so even when some of the servers fails , your data can be recovered and retrieved.

Small minus: they can not offer web interface as other such services do, as this would mean transfer of password over net. Java applet will be downloaded and used instead to do all the local encryption / decryption work.

---

### Post by cintiaarosales on 2012-08-09
Hey youknowme,
I understand what you mean, it’s legitimate to have some doubts regarding how secure are the networks we use. For many people, even us techy-geeky types, the “cloud” is still somewhat of an abstract idea and people tend to be apprehensive about stuff they don’t totally understand. Add to that the increase of cyber attacks of various magnitudes and your distrust is completely understandable. On the other hand, as some guys mentioned before me, the convenience of access, the ease of sharing and collaborating, and the possible financial savings on hardware and software make utilizing cloud services worthwhile in my opinion. Also, I recently saw an infographic (I think on CIO.com) with an interesting statistic that most American companies trust and use cloud services and 85% of IT experts trust cloud service providers with regard to security.
If you’d like to read some more - here’s a nice [post](http://xeround.com/blog/2012/08/43-free-cloud-resources-for-application-developers) I found with a big list of free cloud services for application developers, just to give you an idea of the big variety of tools available on the cloud (more than just simple data storage...). Of course each of these tools may have its own security concerns, but not all of them will store your most valuable or sensitive data. In the end you’ll find the balance between the convenience of the cloud, how much you’d like to use and the amount of security risk you’re willing to trade off. 
Cheers :) Cintia

---

### Post by Hungry Man on 2012-08-09
When you move your data to someone elses server the data is now their problem. That can be a good thing. As a user you and I can't afford to pay an Administrator to stare at server logs all day. We also don't run systems with extremely stripped down operating systems hardened against attack.

The servers have many defenses in place. They have people watching them, people watching the network, and they're hardened.

Or at least ideally that's the case.

If you're worried about the cloud there's one simple solution - before moving a file onto the cloud encrypt it locally. The whole point of encryption is that you can take data and put it anywhere and no one but you can use it.

---

### Post by gordintoronto on 2012-08-09
If I'm working on a document which will eventually be published for all the world to see, it's convenient to dump a copy into my Dropbox in case my hard drive fails.

If I want to make a backup of my tax return, I will use 7-Zip with a huge long encryption key, and dump a copy of that file into my Dropbox. (Or Ubuntu One, or Skydrive, or whatever.) Or, more likely, I will write it to an optical disc along with other private files.

---

### Post by Jive Turkey on 2012-08-10
CLOUD - _C_ouldn't _L_ocate _O_ur _U_sers' _D_ata

With strong encryption your data can be protected from theft.  With redundant multiple location backups it can be protected from loss.

---

### Post by wacky_sung on 2012-08-10
Nothing is unbreakable but with additional using encryption make it harder to crack.

---

### Post by Ms. Daisy on 2012-08-11
Definitely NOT bullet-proof.  

That was said previously but it's worth stating again.  It would be foolish to assume that all the cloud data storage services are going to do everything you would do to protect your data.  

Each cloud service was created independently from any other, so each cloud will have its own security model.  I recommend you look at comparisons of **cloud data storage services **to see what they offer and what they don't.

[http://www.itworld.com/virtualization/229225/cloud-service-rumble-amazon-cloud-drive-vs-icloud-vs-dropbox-vs-google-music-v](http://www.itworld.com/virtualization/229225/cloud-service-rumble-amazon-cloud-drive-vs-icloud-vs-dropbox-vs-google-music-v) (this one includes Ubuntu One)
[http://www.wired.com/gadgetlab/2011/06/cloud-services-compared/](http://www.wired.com/gadgetlab/2011/06/cloud-services-compared/)
[http://www.pcmag.com/article2/0,2817,2288745,00.asp](http://www.pcmag.com/article2/0,2817,2288745,00.asp)
[http://gizmodo.com/5828035/the-best-way-to-store-stuff-in-the-cloud](http://gizmodo.com/5828035/the-best-way-to-store-stuff-in-the-cloud) 

The only way to answer your question is also the most unpopular solution.  You have to read all the documentation (especially the fine print) for each service you're comparing.

---

### Post by Ms. Daisy on 2012-08-11
I found an interesting article on cloud data storage security:

[http://www.schneier.com/blog/archives/2012/08/yet_another_ris.html](http://www.schneier.com/blog/archives/2012/08/yet_another_ris.html)

---

### Post by tubbygweilo on 2012-08-11
Bruce is often worth a browse. 

I would always encrypt data prior to sending it off to a cloud and I would also have the same data on a few clouds if data important enough and cash available. The cloud is not a panacea for all data storage problems but it may well address one or two of your concerns. Remember to bring it back every now and then to see if it is what you expected.

Data storage procedures often takes a bit of thinking about and those solutions using a cloud are no different.

---

### Post by Soul-Sing on 2012-08-12
A network, and the internet is a network, is not, a priori, designed to be safe/secure. The internetprotocol is designed to be in the air, "up". The best place to store sensitive/personal/etc, information is on a disk/hardware imho. (Encrypted)

---

### Post by bouncingwilf on 2012-08-12
Aside from the security implications of storage on the cloud, I also have concerns regarding exclusive _ownership_ of the data. I believe in some circumstances this is not fully explored - itunes types of accounts are effectively cloud services - can you_ insist_ on recovering your own data in all circumstances?

Bouncingwilf

---

### Post by Jay MC on 2012-08-12
In terms of backups, the safest thing is to use multiple places.  Any file that only exists in one place is in danger.  A cloud might fall over, a thumb drive might be lost, a laptop might perish in a fire.

In my case, all my important work is in four places.  On my current laptop; my previous laptop; a thumb drive (sometimes more than one); and Microsoft SkyDrive.  Before SkyDrive I used to send webmail attachments to myself.  All of those locations feel a bit vulnerable for different reasons, but it would be very unlucky for all four to fail me.  Still, don't want to tempt fate, so never say never  :)

In terms of personal data/privacy, my only sensitive private information is on the cloud *and always has been* - insofar as I do online banking.  Even for those who don't check their accounts online, you're relying on someone else to store your private info on their computer network.  I've never kept especially sensitive information on my own device because I've never had a reason to.

---

### Post by andrew3 on 2012-08-15
if you're using "the cloud" (SaaS) then your data is not on your computer. To get your data, you have to:
[LIST]
[*]Accept any new agreements to access your data
[*]Accept that some "cloud" providers (eg. Gmail) automatically access your data and analyse it so they can categorise you (for ads)
[*]Accept that the SaaS provider can make it hard for you to get your data back
[/LIST]From my perspective, there's not much good about that.

---

### Post by Moose on 2012-08-15
The cloud is similar to a file hosting site mixed with a storage warehouse. You can uplad your files and then acess your stuff afterwards via passwords. IMO i don't use the cloud personally and probably won't. BUYING NEW HARDRIVES ALL THA WAAAY!!, no but seriously crazy caps forum screaming aside. I have used the cloud before and it is more trouble than it is worth. Just get a new hardrive for your pc. :}
 
-Anarchy

---

### Post by walker195 on 2012-08-15
they are relatively safe they are great for music and stuff like that but data loss is very possible. in my opinion a external HDD is a good option but its good to put Ubuntu one clouds free 5gb of storage to good use anything important or private though try to keep on a encrypted external HDD just for extra security.

---

### Post by rookcifer on 2012-08-16
The Cloud is great as a storage backup space, but that's all I would use it for.  As Hungry Man said, always encrypt your documents locally before you send them to Dropbox or Ubuntu One or whatever you use.  If you do that then no one on the other end will be able to see your files.

---

### Post by wacky_sung on 2012-08-20
> **rookcifer said:**
> The Cloud is great as a storage backup space, but that's all I would use it for.  As Hungry Man said, always encrypt your documents locally before you send them to Dropbox or Ubuntu One or whatever you use.  If you do that then no one on the other end will be able to see your files.

Actually the theory is 50% correct because the cloud administers are still able to retrieve/review over your files unless your files are also total encrypted over the cloud server require a key/password to retrieve it.

I still believe in this type of setting of cloud service as [Tonido]("http://www.tonido.com/software_what.html").

```
Tonido doesn't upload your data onto external servers, but instead provides direct access to data on your computer.

You have access to 100% of your files from anywhere.
You don't need to upload any files. All your files are directly served from your machine.
Importantly, data stays with you, providing complete privacy and control.
```

---

### Post by movieman on 2012-08-21
> **wacky_sung said:**
> I still believe in this type of setting of cloud service as [Tonido]("http://www.tonido.com/software_what.html").

That means:

1. You give remote users access to a service running on your home system. If it has security holes, they can own your server.
2. If your house burns down, you lose all your data.

The 'cloud' at least ensures you have a backup of your files at an external location so you can recover it if your house does burn down.

Two potential issues I haven't seen mentioned yet:

1. Various countries have rules about what can be done with personal data and how it can be transferred. If you happen to have data in your files which falls under those rules and your 'cloud' provider stores it in one of those countries, you may have just broken the law.
2. Various countries expect 'cloud' providers to hand over user data on request. So it better be well encrypted.

One of the big problems with the 'cloud' is that it pretends to be an amorphous blob that exists in a virtual world, but it's really a bunch of random servers in random countries with random laws. For example, the EU now requires web sites to get permission to store cookies on a user's computer, and since I have no idea where my web site is physically located, I had to stick that on there just in case.

---

### Post by jedispork on 2012-08-22
Is there any serious privacy concerns to storing pictures unencrypted? I keep things like tax documents offline and on a disc.  I didn't get into the whole facebook thing so I have been looking for a easy way to share all my photos and using the cloud service as a additional backup.

---

### Post by Ms. Daisy on 2012-08-23
> **jedispork said:**
> Is there any serious privacy concerns to storing pictures unencrypted? I keep things like tax documents offline and on a disc.  I didn't get into the whole facebook thing so I have been looking for a easy way to share all my photos and using the cloud service as a additional backup.
Not unless they're pictures of highly sensitive things. It would be odd to me if someone encrypted photos of the family vacation.

Services like Snapfish, Flickr & Shutterfly provide "cloud" storage while allowing you to share photos.

---

### Post by Irihapeti on 2012-08-24
There have been concerns about the EXIF data in pictures providing more information than some people would like. E.g. dates, times and location details.

If that is an issue, then it's easy enough to strip out the EXIF data.

Other than that, I don't see a problem.

---

### Post by sdowney717 on 2012-11-23
> **ottosykora said:**
> I have come over one storage service which seems very secure.
[www.wuala.com](www.wuala.com)

The special thing is, that with wuala, all data is encrypted on your own computer before travelling to the server. No passwords or keys are sent over the net, all is done locally. So even the operators of the servers are not able to access the data.
The data is then stored in secured servers in a raid, so even when some of the servers fails , your data can be recovered and retrieved.

Small minus: they can not offer web interface as other such services do, as this would mean transfer of password over net. Java applet will be downloaded and used instead to do all the local encryption / decryption work.

Just signed up for Wuala and it works well enough and can sync files. Your cloud drive shows up in Nautilus.
You get 5gb free. I noticed it is slow. Although I dont yet have enough experience to compare with ubuntu one or isync google drive speedwise.

---

### Post by mike acker on 2012-11-24
> **AnarchyTech said:**
> The cloud is similar to a file hosting site mixed with a storage warehouse. You can {upload} your files and then {access} your stuff afterwards via passwords. IMO i don't use the cloud personally and probably won't. BUYING NEW HARDRIVES ALL THA WAAAY!!, no but seriously crazy caps forum screaming aside. I have used the cloud before and it is more trouble than it is worth. Just get a new hardrive for your pc. :}
 
-Anarchy

+1

if you are running a lap top use an external USB connected HD

---

### Post by leyonchung on 2012-12-17
A cloud service is itself a very big market to explore and the methodology is pretty simple. It is built on a network where people keep and store their important and confidential data on a network which can be accessible anytime and anywhere. ubuntuone is undoubtely a sound option to consider in this case, but if you want some more [cloud data storage]("http://www.cloudreviews.com/blog/cloud-data-storage") options, then i will suggest you to mind checking companies like **SugarSync** and **JustCloud**, because i have had a good experience with them as well.

---

### Post by Simon T on 2012-12-17
You add additional security when you use the cloud by hiding your identity. Even if some were able to view your stored data, it would be difficult to use it if the owner of the information is unknown. Use proxy or VPN to change your IP address is the minimum measure you should take.  And if you use a proxy, you should first check the anonymity level of the proxy before using it. Some proxies only hide your identity partially or not at all.  Here is a web [anonymity level checker]("http://www.idcloak.com/check-anonymity/Check-Anonymity-With-Proxy-Test.html").    

hope this helps. 
Simon T

---

