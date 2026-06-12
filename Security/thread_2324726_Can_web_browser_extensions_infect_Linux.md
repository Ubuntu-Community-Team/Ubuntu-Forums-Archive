---
title: "Can web browser extensions infect Linux?"
date: 2016-05-16
forum: Security
---

### Post by cortana2 on 2016-05-16
So,  as a long term Linux user I should probably already know the answer to  this, but I installed a couple of addons in Firefox and Chrome. I was  wondering if it was possible that assuming 1 of those addons were  malicious, could it infect my linux distro?


  Assuming one of the addons were malicious, could it access my  /home/username? Could it steal passwords I input on Palemoon (my browser  of choice)?


  Thanks!

---

### Post by TheFu on 2016-05-16
Welcome to the forums.

yes. Anything is possible.  There is no silver bullet for security. Sorry.  Firefox has design issues which impact the security for all addons on all platforms. They share the same namespace across all JS addons. That means that any addon has access to any other addon's data. [http://www.ghacks.net/2016/04/06/firefox-cross-extension-vulnerability-discovered/](http://www.ghacks.net/2016/04/06/firefox-cross-extension-vulnerability-discovered/)   Any program running under a userid could be malicious and read the memory for other programs running under that same userid, unless limits are put in place like SE-Linux can provide.  NoScript has the FF issue and it has been seen in the wild.

Security of chrome is also a challenge. Chrome is made by the largest advertising company on Earth. Providing direct access to everything done inside the browser is an issue for me, but not everyone is as paranoid as me.

Never heard of Palemoon, but storing passwords inside the same process as that which accesses dangerous internet sites/services has been proven to be a bad idea. Whether this specific setup has already be compromised or not is a different question.  

I use KeePassX in a separate process. The DB is encrypted in memory, but if someone looked through the code, they could probably attack that.  I know that KeePass v2.x on Windows was successfully attacked.  On Windows, I use KeePass v1 still, about once a month. Don't really use Windows with anything on the internet.  I'm hoping that because most people use a different version of the code, that the crackers won't bother. This is the same reason why OSX is effectively more secure than Windows.  It certainly isn't because Apple patches known issues quickly (they don't for everything).

---

### Post by blaze24-matrix on 2016-05-16
Yes, it is possible. Some of the addons can track your activity and send report's to the owner's. I suggest you to use No Script extension to be safe, or remove them all.

---

### Post by Habitual on 2016-05-16
In a word, flash

---

