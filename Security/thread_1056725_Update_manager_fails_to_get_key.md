---
title: "Update manager fails to get key"
date: 2009-02-01
forum: Security
---

### Post by reldon on 2009-02-01
My update program gives the following error when trying to update

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8B9FBE5158B3AFA9

how can I fix this?..

---

### Post by hyper_ch on 2009-02-01
get the public key

---

### Post by Dr Small on 2009-02-01
By the way, [here it is](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x8B9FBE5158B3AFA9).

---

### Post by reldon on 2009-02-12
sorry for being gone so long.  ice storms can wreak havoc on a persons weeks.

Would you guys be so kind as to tell me how to install this key?  I appreciate your posting it for me to get but without the knowledge of where and how to properly put it in my system having the key is only one small part of my bigger problem.

thanks..

rel

---

### Post by hyper_ch on 2009-02-12
have you tried to find an answer on how to add those keys yourself yet?

---

### Post by NE Key on 2009-02-12
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

Look at the link. It describes how the key is inserted.

---

### Post by reldon on 2009-02-12
I wouldn't be here if I hadn't exhausted all the sources I have tried.  Do you have any productive, positive, suggestions or do you only wish to imply I am an idiot, which I already know when it comes to Ubuntu.

---

### Post by reldon on 2009-02-12
Re: NE Key

Your post gave me a little more to go on.  The post by Dr Small supposedly has a link to the key but I cannot save it in any manner that lets me add it via the method from the website your link takes me to.  Is there a special filename I should use to paste the key information into?

---

### Post by reldon on 2009-02-12
Thank you NE Key !!!

You're post with the link gave me enough to finally figure out how to get that darn key installed.  After some additional machinations I have finally been able to update my programs!!!

This post can now be listed as solved...

Thanks again..   :-)

---

### Post by bryncoles on 2009-02-13
interesting... i get this error message, though i gather its not a bug, its something to do with keys being updated and verified. 

i followed the link given above to the public key, saves it as a text file, double-clicked it (which unexpectedly gave me a 'successfully imported' message), but i still get the error. 

what did i miss...? (and ps: sorry for jumping on the thread....:))

*edit*

never mind, i was being dense. re-read the provided links and realised id done things stupidly! got it sorted now *blushes*

---

### Post by cryptovenom on 2009-02-13
I got the same error massage also. 

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220

---

### Post by agtsmth on 2009-02-13
The key you are referring to is associated with ubuntu tweak.

---

### Post by forger on 2009-02-14
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by ITC on 2009-02-14
> **cryptovenom said:**
> I got the same error massage also. 

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220

To import the key for Ubuntu-Tweak you use:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FE85409EEAB40ECCB65740816AF0E1940624A220
```

[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)

---

