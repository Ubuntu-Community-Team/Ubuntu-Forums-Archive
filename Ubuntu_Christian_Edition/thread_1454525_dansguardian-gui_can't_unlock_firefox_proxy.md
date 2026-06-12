---
title: "dansguardian-gui can't unlock firefox proxy"
date: 2010-04-14
forum: Ubuntu Christian Edition
---

### Post by marllowe on 2010-04-14
Hello,

I use dansguardian-gui and I press 'Lock Firefox Proxy'.
Now I want to unlock it - but I can't...
I press 'Unlock Firefox proxy', restart browser and it doesn't work...
I look this setting in configuration file in Firefox, but I didn't find.

Could you tell me how could I unlock this ?
Firefox 3.5.8
Ubuntu 9.10
Dansguardian-gui_2.4

Regards,
Artur

---

### Post by david_kt on 2010-04-14
> **marllowe said:**
> Hello,

I use dansguardian-gui and I press 'Lock Firefox Proxy'.
Now I want to unlock it - but I can't...
I press 'Unlock Firefox proxy', restart browser and it doesn't work...
I look this setting in configuration file in Firefox, but I didn't find.

Could you tell me how could I unlock this ?
Firefox 3.5.8
Ubuntu 9.10
Dansguardian-gui_2.4

Regards,
Artur

Open terminal and run:
```

gksudo gedit /usr/lib/firefox-3.5.8/firefox.cfg
```

delete all lines containing 

lockPref("network.proxy.type",0);

Restart firefox.

DK

---

### Post by marllowe on 2010-04-15
Thank you for answer :-)
I've found this solution after I send post.
I remove lockPref("network.proxy.type",0); in /etc/firefox-3.5/pref/firefox.js
Everything works fine.
I use privoxy instead tinyproxy and dansguardian works!
Regards,
Artur

---

### Post by warroomcbw on 2010-04-19
Need some help.....
64bit version.  We have a young man who is getting around Dangaurdian.  Going to sites that he shouldn't by being clever with the search words.  I am wondering how to protect him more.  I've got the settings set for the youngest setting level now.  We only use it to bring worship and praise into a prayer room.  Proxy isn't locked.  Everything else is.  Am I doing something wrong?  Dansguardian is blocking sites.  It is working.  But I need it to work just a bit better.  So what can I do to improve things?

The 32 bit version at home seems to work much better.

Any help would be appreciated.

cbw

---

### Post by david_kt on 2010-04-19
> **warroomcbw said:**
> Need some help.....
64bit version.  We have a young man who is getting around Dangaurdian.  Going to sites that he shouldn't by being clever with the search words.  I am wondering how to protect him more.  I've got the settings set for the youngest setting level now.  We only use it to bring worship and praise into a prayer room.  Proxy isn't locked.  Everything else is.  Am I doing something wrong?  Dansguardian is blocking sites.  It is working.  But I need it to work just a bit better.  So what can I do to improve things?

The 32 bit version at home seems to work much better.

Any help would be appreciated.

cbw

1. Lock proxy
2. Check the words he is using, add to blacklist (banned phrases)
3. Add undesireable site to banned URLS or banned sites

DK

---

### Post by warroomcbw on 2010-04-26
> **david_kt said:**
> 1. Lock proxy
2. Check the words he is using, add to blacklist (banned phrases)
3. Add undesireable site to banned URLS or banned sites

DK

Still can't seem to lock proxy.  This is a 64 bit machine running 9.10.

DG seems to work ok.  Seems to block about everything now that I added...including ubuntu forums.  But that is ok if protects people.  Again, we only use this to stream in the prayer room when we are not doing live prayer/praise/worship.

---

### Post by david_kt on 2010-04-26
> **warroomcbw said:**
> Still can't seem to lock proxy.  This is a 64 bit machine running 9.10.



I will check, it might be some problem either with the indication or the script to lock. Could you help me to check the firefox proxy, is it lock or not actually?

DK

---

### Post by warroomcbw on 2010-04-26
I'm not at the church right now,I was earlier. How would I do that exactly?  Maybe I should brush up on DG howtos?  I will help anyway I can, but you might have to tell me how.  I am trying to get Ubuntu CE on all the computers.  It's hard when your leaders say "we would have to retrain everone and that would be too much trouble".  To me as an Audio guy. Ubuntu is way better than anything....I do quite a lot with it.  Anyway, thanks a bunch for any help.  I can't say thanks enough.

---

### Post by david_kt on 2010-04-27
> **warroomcbw said:**
> I'm not at the church right now,I was earlier. How would I do that exactly?  Maybe I should brush up on DG howtos?  I will help anyway I can, but you might have to tell me how.  I am trying to get Ubuntu CE on all the computers.  It's hard when your leaders say "we would have to retrain everone and that would be too much trouble".  To me as an Audio guy. Ubuntu is way better than anything....I do quite a lot with it.  Anyway, thanks a bunch for any help.  I can't say thanks enough.

No, it is not DG. It is Firefox. Just open firefox and try to change proxy (Edit > Preference > network > Setting )

Lock means you could not change proxy setting. If you could change, means it is unlocked.

It is true we have to retrain everyone, but it is not too much trouble I guess.

DK

---

### Post by marllowe on 2010-04-27
> **warroomcbw said:**
> Need some help.....
Dansguardian is blocking sites.  It is working.  But I need it to work just a bit better.  So what can I do to improve things?


Maybe better idea than locking proxy settings in Firefox is redirect everything from port 80 to Dansguardian. This soution is better - becouse if you install another browser (eg. Opera) - it will be redirected to Dansguardian too.

If you want to do this - paste this in terminal:
> sudo iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner --uid-owner root -j ACCEPT
sudo iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner ! --uid-owner tinyproxy -j REDIRECT --to-port 8080
Make sure everything is working properly.
If everything is o.k. and you want run this commands after boot-up past in terminal:
> sudo iptables-save > /etc/iptables.saveOpen file /etc/rc.local
> sudo gedit /etc/rc.localAbove 'exit 0' paste: iptables-restore /etc/iptables.save

> iptables-restore /etc/iptables.save
exit 0
Save changes. After boot-up you could install any browser you want and it should be filtered by Dansguardian.

---

### Post by warroomcbw on 2010-04-27
I will try that and report back as soon as I can...thanks again.

---

### Post by david_kt on 2010-04-27
> **marllowe said:**
> Maybe better idea than locking proxy settings in Firefox is redirect everything from port 80 to Dansguardian. This soution is better - becouse if you install another browser (eg. Opera) - it will be redirected to Dansguardian too.

If you want to do this - paste this in terminal:
Make sure everything is working properly.
If everything is o.k. and you want run this commands after boot-up past in terminal:
Open file /etc/rc.local
Above 'exit 0' paste: iptables-restore /etc/iptables.save

Save changes. After boot-up you could install any browser you want and it should be filtered by Dansguardian.

No, don't do that. Ubuntu ce already has firewall to redirect all traffic on port 80. The problem is even with this redirection, people could still bypass the filtering using external proxy using different port.

DK

---

### Post by marllowe on 2010-04-28
> **david_kt said:**
> No, don't do that. Ubuntu ce already has firewall to redirect all traffic on port 80. The problem is even with this redirection, people could still bypass the filtering using external proxy using different port.

DK
Sorry for the confusion. I use Ubuntu 9.10 Karmic Koala - not Ubuntu CE - so, I didn't know about this.

---

### Post by david_kt on 2010-04-28
> **marllowe said:**
> Sorry for the confusion. I use Ubuntu 9.10 Karmic Koala - not Ubuntu CE - so, I didn't know about this.

Did you use dansguardian gui?

DK

---

### Post by marllowe on 2010-04-28
> **david_kt said:**
> Did you use dansguardian gui?

DK
Yes, I used dansguardian gui. But I had problem with tinyproxy  (blank page in many sites), so I unistall tinyproxy - and install privoxy - it's fast and simple - I recomment it :-)

---

### Post by warroomcbw on 2010-05-10
> **david_kt said:**
> No, it is not DG. It is Firefox. Just open firefox and try to change proxy (Edit > Preference > network > Setting )

Lock means you could not change proxy setting. If you could change, means it is unlocked.

It is true we have to retrain everyone, but it is not too much trouble I guess.

DK

Settings are locked out.  seems to be working ok

---

