---
title: "Chrome security/privacy questions"
date: 2013-08-09
forum: Security
---

### Post by Buntu Bunny on 2013-08-09
This morning I read ["Memo from 2008: Chrome stores passwords in plain text (*gasp*)"]("http://www.psychocats.net/ubuntucat/chrome-passwords-plain-text/") over at [Ubuntucat.]("http://www.psychocats.net/ubuntucat/") The title obviously caught my attention in light of what recently happened here at the Ubuntu Forums. Even with some question as to the authenticity of this claim, I nonetheless went to take a look at my Chrome settings. I looked at "manage saved passwords."

Mostly those passwords are for Gmail and various Blogger blogs, and in fact, blogging at Google is about the only thing I use Chrome for anymore. Because of Google's tracking policies, I have Google Disconnect enabled on Firefox, but Disconnect causes Google Blogs to display improperly, so I leave Disconnect disabled on Chrome and use it for blog visiting only. If there's a workaround for this, I'd love to know and ditch Chrome altogether.

Also, in Chrome settings, would it cause problems to uncheck "Continue running background apps when Google Chrome is closed" under system settings?

Lastly, is Chromium more secure than Chrome in regards to how it handles passwords?

---

### Post by Frogs Hair on 2013-08-09
I use Iron which has the same settings as Chromium and Chrome. Iron has to be updated manually because there is no tracking . Iron has the sign in _option,_ but option is the key word . I have never saved passwords in any browser so I'm used to a little extra work. :o  

> [COLOR=#000000]Also, in Chrome settings, would it cause problems to uncheck "Continue running background apps when Google Chrome is closed" under system settings?[/COLOR]

I have always disabled this option since discovering it without noticing any difference at all.

---

### Post by Buntu Bunny on 2013-08-09
> **Frogs Hair said:**
> I use Iron which has the same settings as Chromium and Chrome. 

Thanks Frogs Hair. I installed Iron and honestly can't tell much difference from Chrome

> Iron has to be updated manually because there is no tracking.

How do I update it manually? Something like sudo apt-get update Iron && sudo apt-get upgrade Iron?

> I have always disabled this option since discovering it without noticing any difference at all.

Again, thank you. :)

---

### Post by Hungry Man on 2013-08-10
I wouldn't use Iron.
[http://www.insanitybit.com/2012/06/23/srware-iron-browser-a-real-private-alternative-to-chrome-21/](http://www.insanitybit.com/2012/06/23/srware-iron-browser-a-real-private-alternative-to-chrome-21/)

---

### Post by CharlesA on 2013-08-10
> **Hungry Man said:**
> I wouldn't use Iron.
[http://www.insanitybit.com/2012/06/23/srware-iron-browser-a-real-private-alternative-to-chrome-21/](http://www.insanitybit.com/2012/06/23/srware-iron-browser-a-real-private-alternative-to-chrome-21/)

Totally. Owned.

---

### Post by Hungry Man on 2013-08-10
Also any browser that can autofill passwords stores them in the clear, even Firefox with a master password. The difference is that if you haven't entered in that MP yet they're encrypted - but once you do they aren't. There's further validation with MP but an attacker with physical access can dump the memory of any user they have access to so yeah, it'll keep your friends out, but that's all.

I suggest using Chrome with LastPass.

---

### Post by Mr.Dunham on 2013-08-10
> **Buntu Bunny said:**
> The title obviously caught my attention in light of what recently happened here at the Ubuntu Forums.
Well, the key here is that we should get used to take care of our sensitive stuff like passwords and other personal/private information always, as a healthy habit, not because of some forum being hacked.

> **Frogs Hair said:**
> I have never saved passwords in any browser so I'm used to a little extra work.
Same here. One of the first things I always do is to uncheck the "Save passwords" option on any browser, here in my own Xubuntu system and also in the several Windoze computers I use at my workplace. To me it's just common sense. Anyone is entitled to handle this stuff the way they want, just be aware that always there's extra work to be done; if you uncheck the *save password* option, you'll have to type them in again; and if you check the "save" option, you'll need to take an extra care.

---

### Post by vasa1 on 2013-08-10
> **Hungry Man said:**
> I wouldn't use Iron.
[http://www.insanitybit.com/2012/06/23/srware-iron-browser-a-real-private-alternative-to-chrome-21/](http://www.insanitybit.com/2012/06/23/srware-iron-browser-a-real-private-alternative-to-chrome-21/)

+1.

> Iron has to be updated manually because there is no tracking.  doesn't make sense to me. What about other software that doesn't need to be "updated manually"? All spyware?

Anyway, using Iron doesn't eliminate the password issue that OP has.

---

### Post by CharlesA on 2013-08-10
> **Hungry Man said:**
> Also any browser that can autofill passwords stores them in the clear, even Firefox with a master password. The difference is that if you haven't entered in that MP yet they're encrypted - but once you do they aren't. There's further validation with MP but an attacker with physical access can dump the memory of any user they have access to so yeah, it'll keep your friends out, but that's all.

I suggest using Chrome with LastPass.

Agreed. I use KeePass myself, but LastPass is good to.

> **Mr.Dunham said:**
> Same here. One of the first things I always do is to uncheck the "Save passwords" option on any browser, here in my own Xubuntu system and also in the several Windoze computers I use at my workplace. To me it's just common sense. Anyone is entitled to handle this stuff the way they want, just be aware that always there's extra work to be done; if you uncheck the *save password* option, you'll have to type them in again; and if you check the "save" option, you'll need to take an extra care.

I think I only use the save password thing for one site and it is because I use a certain browser only for that site due to some issues it has with FF and Chrome.

---

### Post by Hungry Man on 2013-08-10
Keypass is very good. It has some significant advantages over LastPass, like the ability to use any amount of PBKDF2 rounds for your password hashing (LastPass limits you to a very adequate 256,000 rounds). I like LastPass for the syncing and two factor authentication, but both are really good programs.

---

### Post by Buntu Bunny on 2013-08-10
> **CharlesA said:**
> .... I use a certain browser only for that site due to some issues it has with FF and Chrome.

Well, this is the problem that prompted me to ask the question in the first place; I need a browser only for reading Google's Blogger blogs, because if I disable Google tracking then the blogs are not rendered properly. I use FF for everything else. I like Opera but it's slow on my system, even in turbo.

I appreciate all the comments. I took a look at KeePass yesterday, and I'll look at it again today.

---

### Post by Frogs Hair on 2013-08-11
> How do I update it manually? Something like sudo apt-get update Iron && sudo apt-get upgrade Iron? There is no sever connection to Iron repos by design and they are not using Chrome 21 . Iron does not track your ip or location when it is downloaded like Chrome.  I also installed keePassX today   

[URL="http://www.srware.net/en/software_srware_iron_download.php"]
[/URL][http://www.srware.net/en/software_srware_iron_chrome_vs_iron.php](http://www.srware.net/en/software_srware_iron_chrome_vs_iron.php)

---

### Post by Buntu Bunny on 2013-08-11
> **Frogs Hair said:**
> There is no sever connection to Iron repos by design and they are not using Chrome 21 . Iron does not track your ip or location when it is downloaded like Chrome. 

So upgrading is simply installing the newest version(?)

>  I also installed keePassX today   

I'm taking a look at that too.

---

### Post by Frogs Hair on 2013-08-11
> So upgrading is simply installing the newest version(?)

Yes. I use a Chromium based  browser as a secondary browser and have used Chrome also . I am certainly not fanatical about Iron. I am testing the chromium based Opera 15 , but there are no Linux builds yet.  Opera won't be connected to Google  services via sign in or to the Chrome web store. Opera Next is not a Chrome clone and has it's own add-on and theme page. Opera turbo has been renamed and added also.

---

### Post by Buntu Bunny on 2013-08-11
> **Frogs Hair said:**
> Yes. I use a Chromium based  browser as a secondary browser and have used Chrome also . I am certainly not fanatical about Iron. I am testing the chromium based Opera 15 , but there are no Linux builds yet.  Opera won't be connected to Google  services via sign in or to the Chrome web store. Opera Next is not a Chrome clone and has it's own add-on and theme page. Opera turbo has been renamed and added also.

I've always liked Opera, but didn't realize they'd developed a Chromium based version. That's interesting news. Hopefully it will become available for Linux soon.

---

### Post by Frogs Hair on 2013-08-12
After experimenting with KeePassx and the  Lastpass extension for FF and Chrome  I find the LP to be the most convenient so far.

---

### Post by bapoumba on 2013-08-12
I never store passwords in browser, but use KeePassX. I store the db in dropbox, so I can access from the 3 different computers I regularly use, plus phone and tablet. It can use both a master password and a specific file to be present on the device to open the db which is encrypted.

---

### Post by Buntu Bunny on 2013-08-12
> **Frogs Hair said:**
> After experimenting with KeePassx and the  Lastpass extension for FF and Chrome  I find the LP to be the most convenient so far.

Thanks Frogs Hair! How is it different than using FF's master password?

> **bapoumba said:**
> I never store passwords in browser, but use KeePassX. I store the db in dropbox, so I can access from the 3 different computers I regularly use, plus phone and tablet. It can use both a master password and a specific file to be present on the device to open the db which is encrypted.

DB??? 

I have two computers so this is an idea for me.

---

### Post by Frogs Hair on 2013-08-13
> [COLOR=#000000]Thanks Frogs Hair! How is it different than using FF's master password?[/COLOR] They have a cloud based data base so it is similar to what  [COLOR=#000000]bapoumba is doing with KeePassX & Dropbox.  [/COLOR]Best to read their info. [https://lastpass.com/features_free.php](https://lastpass.com/features_free.php)

The extensions work well for me due to my Win 7 dual boot ,so I don't have to worry about having the same software for both operating systems. I just added the extension in the Win 7 browser and logged in.

---

### Post by bapoumba on 2013-08-13
Yes, thanks Frogs Hair. db is for database, the file that stores sites url, login and passwords as well as other text files if you wish. The database is encrypted and the application has a password generator. To open the database, a master password is required. You can make it additionally require a file to open the db.
[https://www.keepassx.org/](https://www.keepassx.org/)

---

### Post by Buntu Bunny on 2013-08-13
> **Frogs Hair said:**
> Best to read their info. [https://lastpass.com/features_free.php](https://lastpass.com/features_free.php)

Thank you. I've learned quite a bit from this discussion and appreciate the help.

---

### Post by Welly Wu on 2013-09-01
I switched from using LastPass Premium with two Yubico Yubikeys to KeePassX and KeePass 2 with the Google Chrome ChromeIPass and Mozilla Firefox KeeFox plug-ins. You can enable two-factor authentication using KeePass 2 and Mono using the optkeyprov plug-in or you can generate a secure keyfile and require it to open or unlock your KeePass 2 encrypted database. This is what I have chosen to do myself. LastPass is good if you prefer convenience and you don't mind paying the low $12.00 USD annual subscription fee. I don't trust LastPass because they were attacked and they did not come clean with details about the security breach. KeePass 2 has a lot of resources at their website at [http://www.keepass.info](http://www.keepass.info) for you to browse and learn more about. It's a fully function and more secure alternative to LastPass in my experience and opinion. I now prefer it to the built-in password managers for Google Chrome or Mozilla Firefox or any other web browser. I also set my PKBDF2 key transformations to 512,000.00 for extra security against brute force dictionary attacks in KeePass 2. This is a free, libre, open source alternative that has proven to be the best in my experience and opinion.

---

### Post by Welly Wu on 2013-09-02
If you are wary about the AES cipher, then you can download Bruce Schneier's TwoFish cipher from the keepass.info website and type in sudo cp TwoFishCipher.plgx to /usr/lib/keepass2/plugins. Be sure to do a sudo mkdir /usr/lib/keepass2/plugins sub-folder prior to copying the file to this directory. Restart KeePass 2 and let it compile the plug-ins.

AES is partially broken, but it is still computationally unfeasible to break it completely. TwoFish is completely unbroken. It is not even close to being partially broken yet and it is nearly as fast as AES and it gets Intel's AES-NI support for CPU hardware accelerated encryption and decryption. TrueCrypt and KeePassX and KeePass 2 support these technologies.

---

### Post by Welly Wu on 2013-09-02
[http://www.differencebetween.net/technology/difference-between-aes-and-twofish/](http://www.differencebetween.net/technology/difference-between-aes-and-twofish/)

---

