---
title: "Creating a server (not for home use)"
date: 2008-10-11
forum: Server Platforms
---

### Post by chenguo4 on 2008-10-11
I'm looking to host some files for a cancer research lab, and I was wondering if this would be possible:

Basically, I want to take an old computer, put in a new hard drive (or possibly just an external for simplicity's sake), put Linux on it and use it as a file server.

The thing is, when I Google "Linux file server," all the results that show up seem to be for home networks only. I want to be able to access the files from any network. 

So if this is indeed possible, can anyone link me to a resource (or a few resources) that can tell me how to do this? Thanks in advance.

---

### Post by bluefrog on 2008-10-11
home network or any network, it is the same.

you might need to implement vpn for anybody to access securely your files from anywhere.
[http://www.howtoforge.com/](http://www.howtoforge.com/)

---

### Post by volkswagner on 2008-10-11
The question you need to answer is how will the files be accessed.  As stated earlier you can use VPN, FTP, web pages, etc.  Will users be adding files or only viewing them?  Is the material sensitive, how secure does it need to be?

Cheers

---

### Post by chenguo4 on 2008-10-11
As for security, it's a small concern. I was thinking a password would do.

I'd like users to be able to upload files too, that means it's an FTP right?

Also I did more researching, and would a LAMP system be what I'm looking for? Or do I not really need all that if I'm just implementing a database for people to download and upload documents and not an actual website?

By the way, if size of database factors into this somehow, I'm thinking the absolute max I'd need is about 500gb, and likely much much less than that will be used. The files will mostly be office documents, pdfs, and images.

Thanks in advance guys.

---

### Post by cariboo on 2008-10-11
You would probably be better off to install the lamp server for what you need. The Howtoforge link was posted above.

> As for security, it's a small concern. I was thinking a password would do.

If there are more people than just your self using the system, security is important. You say this is for a cancer research lab. If you feel that the files loaded on the server have no value the go ahead and set it up with minimal security. Security should be just as high a priority as setting the server up. Security not only includes protecting the files from other users but also make sure you have at least a couple of current backups with at least one off site at all times.

Jim

---

### Post by nlinecomputers on 2008-10-11
> **chenguo4 said:**
> As for security, it's a small concern. I was thinking a password would do.



Uh No.  If this is for Medical research and patient records are involved then depending on what country you are in quite a bit of security concerns are in play.  In the USA HIPAA regulations need to be setup if any patient records are stored on this server.

---

### Post by chenguo4 on 2008-10-12
Well, there's no patient records, it's just statisfics. I'm not sure about how secure these files are supposed to be. I'm doing this for my mom, so I'll ask her and google around.

Thanks for all the help guys. I'm reading the howto right now.

---

### Post by chenguo4 on 2008-10-12
Well, there's no patient records, it's just statisfics. I'm not sure about how secure these files are supposed to be. I'm doing this for my mom, so I'll ask her and google around.

Thanks for all the help guys. I'm reading the howto right now.

---

