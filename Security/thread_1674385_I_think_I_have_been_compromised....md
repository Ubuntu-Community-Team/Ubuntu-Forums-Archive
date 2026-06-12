---
title: "I think I have been compromised..."
date: 2011-01-23
forum: Security
---

### Post by psifunk on 2011-01-23
I do not now how I managed to do it but firefox seems to insist loading a website called Joss & Main for every address that I give it. I am using opera now and it works fine. 

Description of the problem:
Whatever site I try it loads the same website. The webpage firefox is displaying is this one [http://www.jossandmain.com/](http://www.jossandmain.com/) although I had never seen it before or know what this is. Firefox does not display an address in the address bar, I found this web address through google and it looks exactly the same. It actually displays the address of whatever other site I was trying to get to although it is loading this one. 

My knowledge is limited so I simply reinstalled firefox and did all the updates. I also tried firestarter to see if it would detect anything but nothing. Any ideas?

ubuntu 9.10 on asus eee 1005

---

### Post by wojox on 2011-01-23
It sounds like there is something in your DB is corrupt. Download [this Script]("http://www.webgapps.org/firefox/database-optimization") and run it. You need sqlite3 installed as well.

---

### Post by matt_symes on 2011-01-23
Hi

You could close Firefox, rename your hidden Firefox folder in your home directory and restart Firefox.

If that fixes the issue then there is something going on with your renamed Firefox profile.

Have you checked through the settings in Firefox ?

EDIT: Nice script Wojox. I have not seen that before.

Kind regards

---

### Post by Ryan Dwyer on 2011-01-25
Sounds to me like your DNS server has been compromised. If you get the same behaviour with another browser, try changing your DNS server address to Google's public DNS or OpenDNS.

---

### Post by psifunk on 2011-01-25
Thanks for all the advice. So the results are

I tried the script from the first response from wojox, it said it found no problem, optimized the database and the problem persisted.

So I tried what matt_symes suggested and renamed the folder ~/.mozilla to whatever. [U]Firefox works fine now i suppose in the default configuration. So firefox works again that's ok for me. 
[/U]
Before this can be marked as solved :

Should I pursue this any longer trying to figure out if there is a security breach? What should I do with the old configuration folder, delete it? And lastly I am not sure if it is still necessary to follow the advice about changing DNS server from the last response. 

Thanks people!

---

### Post by matt_symes on 2011-01-25
Hi

> Should I pursue this any longer trying to figure out if there is a security breach? 

I don't use this but it has been mentioned a number of times by posters on this site. Might be worth investigating.

[https://addons.mozilla.org/en-US/firefox/addon/noscript/](https://addons.mozilla.org/en-US/firefox/addon/noscript/)

> What should I do with the old configuration folder, delete it? 

Depends if you want to keep any bookmarks etc. You could try coping them back to your new folder.

What is have done is installed a little add-on called xmarks. This allows you to store your bookmarks in the cloud by syncing them. Then if you get compromised, you can get your bookmarks back. It also allows you to access your bookmarks from anywhere. If you are interested [http://www.xmarks.com/](http://www.xmarks.com/)

It's a free service. I should say i have no association with them.

> And lastly I am not sure if it is still necessary to follow the advice about changing DNS server from the last response. 

Although a good suggestion, in this case it is not your DNS server that is causing the problem so leave as be.

Kind regards

---

### Post by psifunk on 2011-01-25
Thanks again matt,  I do need my bookmarks so if you hadn't pointed it out I am sure I would have realized it right after I pressed enter for delete.

I will also give a try to xmarks it sounds useful. I already had noscript working on firefox before the problem happened but it did not give any warning.

---

