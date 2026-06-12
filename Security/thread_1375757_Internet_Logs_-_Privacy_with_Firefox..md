---
title: "Internet Logs - Privacy with Firefox."
date: 2010-01-08
forum: Security
---

### Post by zozza on 2010-01-08
These files seem to contain browsing history:

~/.mozilla/firefox/xxxxx.default/cookies.sqlite ~/.mozilla/firefox/xxxxx.default/formhistory.sqlite ~/.mozilla/firefox/xxxxx.default/downloads.sqlite ~/.mozilla/firefox/xxxxx.default/places.sqlite ~/.mozilla/firefox/xxxxx.default/places.sqlite-journal 

~/.mozilla/firefox/xxxxx.default/Cache/

Therefore I have cleared these files using an erasing program.

I am wondering if there are other locations where such log files are stored for Internet browsing. 

I have looked in the /var/log directory and cannot see anything - for example doing a grep on http:// after browsing in Firefox does not reveal anything obvious. 

Thanks.

---

### Post by cdenley on 2010-01-08
Your user doesn't have permission to write outside the home directory. Everything written by firefox should be in the profile within ~/.mozilla/firefox. If you want to clear private data, thats what Tools>Clear Recent History is for. If you're really paranoid about forensic recovery, don't write it to a magnetic media.

---

### Post by bodhi.zazen on 2010-01-08
Adjust your privacy settings in firefox preferences.

> **cdenley said:**
> Your user doesn't have permission to write outside the home directory. Everything written by firefox should be in the profile within ~/.mozilla/firefox. If you want to clear private data, thats what Tools>Clear Recent History is for. If you're really paranoid about forensic recovery, don't write it to a magnetic media.

Or start a private session ...

Tools -> Start private browsing

[http://support.mozilla.com/en-US/kb/Private+Browsing](http://support.mozilla.com/en-US/kb/Private+Browsing)

Of course private browsing is not "perfect" either ;)

Or use a live CD ...

---

### Post by zozza on 2010-01-10
Thanks for these responses and for the advice about private browsing.  

I don't have a problem with having a history, cookies, etc, because I can wipe it. 

However, under XP there were various privacy issues, such as the information contained in index.dat and I was wondering if Ubuntu had places (e.g. in /var/log) where browsing information was retained.

---

### Post by rookcifer on 2010-01-10
> **zozza said:**
> Thanks for these responses and for the advice about private browsing.  

I don't have a problem with having a history, cookies, etc, because I can wipe it. 

However, under XP there were various privacy issues, such as the information contained in index.dat and I was wondering if Ubuntu had places (e.g. in /var/log) where browsing information was retained.

Another, more drastic, alternative to using private browsing is to deny write access to the directories where the browser history/cache is saved.

---

### Post by OpSecShellshock on 2010-01-10
You should also install the Firefox addon called BetterPrivacy so you can delete Flash cookies and DOM objects (basically these are long-term storage objects that don't reside in the places that Firefox cleans on its own).

Understand that private browsing and object deletion only gets rid of these things on your local machine. Beyond your home premise, your control over the visibility of your browsing pretty much stops unless you use a VPN/Proxy/Onion routing service.

---

### Post by mkvnmtr on 2010-01-10
You do not need an addon to delete flash cookies. You can go to the Adobe flash settings management page and do it yourself. You should do it because at default it allows sites to store stuff o your computer and track your web use. Just google it and you will find the page and if you enable script the controller is on the page. It seems to work for all the browsers on a system that use flash but since I have 5 systems on this computer I had to do it for each one. That makes me think that each flash down load can be identified.

---

