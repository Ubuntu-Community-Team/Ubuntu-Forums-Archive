---
title: "Security of Ubuntu One"
date: 2010-04-10
forum: Ubuntu One (CLOSED)
---

### Post by oOarthurOo on 2010-04-10
Please excuse / merge if this thread is duplicative of many others, I have searched the forums for a discussion of the risks that using Ubuntu One (UO) poses to users but haven't found anything. 

I have a few concerns that I'd like to raise, and maybe get some feedback on. 

**1. UO transmits data between the host computer / servers securely**. 

From the wiki:

> We use both SSL and secure certificates to deliver Ubuntu One services in a secure manner. Secure certificates ensure that you are communicating with Ubuntu One and SSL encrypts the transmission of all subscriber data. This data include files, notes, and all other data backed-up and synchronized through your personal cloud. SSL is good enough for banks so it should be good enough for us. 

This is all well and good, and as expected. But I was wondering about the comment that the interaction between our computers and the host servers is completed via a proprietary method.Perhaps I misunderstood it. Here is the quote from the UO's wiki/technical details

> There is one implementation, which is proprietary. Little is known, but an instance of it runs on an EC2 server at updown.one.ubuntu.com. 

My only question here is if I'm understanding this correctly: UO transmits data securely, but not transparently secure; We're just asked to trust that there are no bugs in the proprietary implementation of some secure transmission "implementation". I'm not a security geek, so I just don't know if I'm reading this correctly. I've nothing specifically against it, though one reason I choose to use FOSS because I believe in an open security model. 

**2. UO stores data on Amazons' S3 servers, unencrypted. **

Again from the UO/wiki/security page:

> We do not store your files encrypted in our data storage since we need them unencrypted in order to send them to the people you choose to share with. If you are really paranoid, you could always store the files already encrypted so Ubuntu One never sees the plain text files. 

It's kind of insulting to say "if you're really paranoid". I mean, you offer easy /home encryption for Mom and Pop with their desktop, then say they might be paranoid about sharing it unencrypted on a server farm accessible by hundreds of strangers at Amazon.

Let's talk about the S3 cloud for a second.

**   a) It's hosted in the U.S.**
This means its subjected to all the laws and regulations of that country, and frankly, those laws don't offer as much privacy regulations and protection as my own country. [[More info on this]("http://www.infoworld.com/d/the-industry-standard/why-privacy-laws-should-make-you-think-twice-about-the-cloud-692")]

Some questions about the cloud raised elsewhere include:

> What if Amazon has a major, prolonged outage? What if they go out of business? What if someone sues them and obtains a blanket subpoena to all data to which Amazon has access?

The last is the most serious to me, because it's actually happened in the US already. Google was actually ordered to turn over search data, though I believe they reached a deal in the end that protected personally identifying information. [[Link]("http://www.nytimes.com/2008/07/04/technology/04youtube.html")]

**    b) It's a publicly accessible server. **
I don't mean this the way you think. I'm not that worried about hackers breaking into Amazon's S3 remotely. I'm concerned about the hundreds of employees with access to it. How much do you think they pay these guys? You think China or a Russian criminal group can't find a person with access who needs an extra $50,000 to harvest some user info? Or what about someone who is fired and is disgruntled, and decides to take a terabyte or two of data on the way out the door. 

This too has happened already, in places more "secure" than Amazon. [[Link]("http://www.wired.com/threatlevel/2010/03/tsa-worker-charged-with-attempted-sabotage/")]

***********************************************

Actually, that's about it. Two concerns. I guess I didn't need the numbers.

In any event. Those two concerns are the reason the first thing I do with my new install is to remove UO. Because I think they're real threats, and there are other methods that we can use to sync and back up our data. I just wish rsync / unison was as easy and amazingly integrated as UO has become. 

Please let me know what your thoughts are on this. I'd be happy to reconsider my "paranoid" position.

---

### Post by oOarthurOo on 2010-04-10
Just want to add another recent example of the trust we put in close source applications, letting a corporation handle the security:

[Bank of America Employee Plants Malware to steal money from clients]("http://gizmodo.com/5514089/bank-of-america-employee-charged-with-planting-malware-on-atms")

Further to point #2.

---

### Post by joshuahoover on 2010-04-12
> **oOarthurOo said:**
> PMy only question here is if I'm understanding this correctly: UO transmits data securely, but not transparently secure; We're just asked to trust that there are no bugs in the proprietary implementation of some secure transmission "implementation". I'm not a security geek, so I just don't know if I'm reading this correctly. I've nothing specifically against it, though one reason I choose to use FOSS because I believe in an open security model. 

It is true that our server implementation is not open source, but the protocol between the client and our server code is open source: [https://edge.launchpad.net/ubuntuone-storage-protocol](https://edge.launchpad.net/ubuntuone-storage-protocol) 

> It's kind of insulting to say "if you're really paranoid". I mean, you offer easy /home encryption for Mom and Pop with their desktop, then say they might be paranoid about sharing it unencrypted on a server farm accessible by hundreds of strangers at Amazon.

I'll see if we can change that language as I can see how people might find it insulting.

> In any event. Those two concerns are the reason the first thing I do with my new install is to remove UO. Because I think they're real threats, and there are other methods that we can use to sync and back up our data. I just wish rsync / unison was as easy and amazingly integrated as UO has become. 

Please let me know what your thoughts are on this. I'd be happy to reconsider my "paranoid" position.

We respect that some people are not going to be comfortable with the Ubuntu One services or any services that synchronize or store data in a public cloud. We do our best to ensure our users' data is as secure as possible while still providing compelling services. The examples you provided of security breaches are serious and the last thing Canonical wants is to have a similar incident. At the same time, I'm not sure there is anything I write here that will convince you to use Ubuntu One. We don't have plans to open source the server side of our code. We still intend on using Amazon's S3 for the foreseeable future. We will continue to examine our security and privacy policies, processes, and practices and improve them where ever we can. I appreciate your feedback and hope that over time we'll prove to you that Ubuntu One is a service you can trust.

Thank you,

Joshua

---

### Post by oOarthurOo on 2010-04-13
Appreciate the response Joshua. From what I've read md5 hash checks should be possible to prevent data corruption. If that feature isn't already implemented it could be a method to prevent someone from maliciously corrupted your pdf files on the server. Encryption is also an option if you're just using it for backup, which would mitigate pretty much all my 'concerns'. 

It's quite an amazing app and you guys are going a great job on it. Thanks again for the clarifications.

---

### Post by zekopeko on 2010-04-13
> **joshuahoover said:**
> We respect that some people are not going to be comfortable with the Ubuntu One services or any services that synchronize or store data in a public cloud. We do our best to ensure our users' data is as secure as possible while still providing compelling services. The examples you provided of security breaches are serious and the last thing Canonical wants is to have a similar incident. At the same time, I'm not sure there is anything I write here that will convince you to use Ubuntu One. We don't have plans to open source the server side of our code. We still intend on using Amazon's S3 for the foreseeable future. We will continue to examine our security and privacy policies, processes, and practices and improve them where ever we can. I appreciate your feedback and hope that over time we'll prove to you that Ubuntu One is a service you can trust.

Thank you,

Joshua

I'm still not clear why U1 doesn't have encrypted server side storage. I'm pretty sure Dropbox has it.

The "we need to have decrypted data so you can share it" argument is (easily) solvable. Why not have everything encrypted and when the user shares something simply move that to an unencrypted storage?

---

### Post by joshuahoover on 2010-04-14
> **zekopeko said:**
> Why not have everything encrypted and when the user shares something simply move that to an unencrypted storage?

That's definitely an option and one we'll consider as we continue to improve the service.

Thank you,

Joshua

---

### Post by zekopeko on 2010-04-16
Here is Amazons Whitepaper on data security:

[http://awsmedia.s3.amazonaws.com/pdf/AWS_Security_Whitepaper.pdf](http://awsmedia.s3.amazonaws.com/pdf/AWS_Security_Whitepaper.pdf)

---

### Post by firmit on 2010-05-12
Hi all

I do agree that the lack of encryption out of the box with U1, seems rather strange given the option of encrypting your /home drive when installing.

However, solving this is easy. As U1 now offers the user to select the folders in your /home/user to sync, you may easily create one folder which you have your shared stuff in, i.e. /home/user/public, and one for personal stuff - which you have encrypted!

encFS should be able to solve this very easily. Simply sync the encrypted folder! 

I made a post about this a couple of years ago - for paranoid Dropbox users. I think this post is even more valid now:
[ see updated blog post here ]("http://wp.me/pdWhQ-2g")

---

