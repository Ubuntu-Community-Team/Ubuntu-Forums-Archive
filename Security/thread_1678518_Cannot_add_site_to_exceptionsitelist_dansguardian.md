---
title: "Cannot add site to exceptionsitelist dansguardian"
date: 2011-01-30
forum: Security
---

### Post by toolmania1 on 2011-01-30
I am trying to add any web site into the exceptionsitelist for dansguardian, but I get cannot edit the exceptionsitelist file located at:

/etc/dansguardian/lists

So, I tried to chmod 777 exceptionsitelist 

I was told that:

chmod:  changing permissions of 'exceptionsitelist': Operation not permitted

Am I trying to add a site as a whitelisted site the correct way?

If not, how do I do this?

Please provide details on if this is done in a gui?  ( I don't have a gui or know where it is located at least )
What is the gui called?
Where is it located ( under which mean like administration or preferences etc. ) ?

If there is no gui, am I looking in the correct folder for trying to add a web site for whitelist?
Am I trying to whitelist correctly by adding a web site to the exceptionsitelist folder?

I want to bypass everything dansguardian does.  I read about greylist.  I do not want to do that.  

Do I have to add this web site into other files besides exceptionsitelist?  If so, which ones?

Thanks in advance

---

### Post by toolmania1 on 2011-01-30
Oh, I am using Provioxy as my proxy also.

---

### Post by toolmania1 on 2011-01-30
[http://www.art.ubuntuforums.org/showthread.php?t=1658669](http://www.art.ubuntuforums.org/showthread.php?t=1658669)

I followed a lot on this page from Bodhi

---

### Post by toolmania1 on 2011-01-30
I did just find a way around.  I turned my proxy off so that I am using no proxy.  This obviously provides no protection, but now I can edit the web pages I need to and then turn it back on.  

I would still like to know how to update this though.

---

