---
title: "upgrade from 12.10 to 13.10 uses HTTP.   So there is no security ?"
date: 2014-03-05
forum: Security
---

### Post by bob60 on 2014-03-05
Hi,
today I wanted to upgrade to ubuntu 13.10. But due to a wifi connection failure, the process stopped. And what I saw :

[IMG]http://s17.postimg.org/x3q1wkil9/omg_trying_to_upgrade_from_ubuntu_12_10_to_13_10.png[/IMG]

I was very suprised to realize that in order to transfer critical files, the HTTP protocol is used and not the HTTP[COLOR=#ff0000]S[/COLOR] one.

So there is no secured transmission?

What about a man in the middle attack? It'd be easy to replace a critical library without the user notices anything. Isn't it?

---

### Post by mikewhatever on 2014-03-05
...and how would the bogus library pass the checksum?

---

### Post by The Cog on 2014-03-05
All the packages are signed with certificates. The only thing HTTPS would add is a little privacy, which is not really important. I see no need to hide what you are downloading from your ISP.

---

### Post by bashiergui on 2014-03-05
See this thread for a thorough answer. 
[http://ubuntuforums.org/showthread.php?t=2203884](http://ubuntuforums.org/showthread.php?t=2203884)

---

### Post by bob60 on 2014-03-06
thanks a lot for your answers.

@The Cog : yeah you're absolutely right. To use https doesn't really make sense as https is more for confidentiality than integrity.

@bashiergui : thank you very much for your link(s). It's very interesting and I've learnt a lot of things.

But I'm far from beeing sure that I've well understood everything (I'm not super good in english)
Here is what I've understood in all my researches :

Please don't hesitate to note any mistake :)       
thanks in advance

Postulate : repositories are not corrupted
Postulate : I have a fresh install of ubuntu on my computer that is not corrupted
Postulate : I have an internet connection that is untrusted.
In my ubuntu, I guess I have by default the certificates of Ubuntu repositories. (let say there is only one repository and ubuntu needs to download only one file to simplify )
When I try to make an update/upgrade (or even a complete upgrade of my OS like I tried to do)  
1) my ubuntu gets the public key of the repository through the certificate stored on my computer.
2) Then ubuntu download (through http) the file and its corresponding hash value.
3) With the public key ubuntu can check if the hash value is correclty signed by the repository private key. 
4) if this verification is ok, then ubuntu makes a md5sum of the file downloaded and if it matches the signed hash value so that'll be the proof the file is exactly the same as the one in the remote repository and so there is no corruption.       

Am I all right? 
(and sorry for my newbish questions and my english)

---

### Post by The Cog on 2014-03-07
Your English looks perfect to me, and your logic looks very good too. But just to be clear, my understanding is that:
a: The public key for the release file is part of the original Ubuntu install. The installer file can be verified against the MD5 sum published on the Ubuntu download website. 
b: Updating involves downloading a new release file. The release file describes all the package files, including their MD5 sums. It is cryptographically signed, and verified using the above public key.
c: Individual package files are integrity checked after downloading using the MD5 sums in the above release file.

I think the dangerous part is the original installer download. 
Your ISP could create a false Ubuntu site serving fake installer ISOs and a fake md5dum file, and then their own fake repository files for updating with. But that's a lot of fakery work to do.

---

### Post by bob60 on 2014-03-11
Thank you very much The Cog. I really appreciate your reply and all details you gave to me. :-)
Have a nice week ^^

---

