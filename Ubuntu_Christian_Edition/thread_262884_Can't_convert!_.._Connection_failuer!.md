---
title: "Can't convert! .. Connection failuer!"
date: 2006-09-22
forum: Ubuntu Christian Edition
---

### Post by Isoss on 2006-09-22
Hello
I downloaded the convert me script and when I tried running the script I get this error: 
```
Ubuntu CE Convert Me Script WILL NOT run because a connection to the server could not be made. 
Try again later. Your default sources.list will now be restored.
```
I checked the .start file and found that it's trying to run 
```
wget --tries=2 --timeout=20 http://www.whatwouldjesusdownload.com/.online.key
```

I thought it might be because I am behind a proxy server so I ran ```
export http_proxy=http://proxy:port
``` and could wget the Public Key Block!
I tried again to run convert me to no avail! same error! 
I noticed that it trys to replace me sources.list with ./sources/sources.list but when I opened the ./sources folder I found it empty!! 

Anything wrong? 

Any help will be appriciated

Thanks

---

### Post by Isoss on 2006-09-22
about the sources.list, I just noticed in the ./start script that the scources.list is actually being moved from ./sources to /etc/apt/ folder using! but why is that? why not copy?

I hope someone has a solution to my connection problem! still having it although I am pretty sure my network configurations are correct cuz I can connect to the internet and run apt-get update and everything!

Thanks

---

### Post by mysticrider92 on 2006-09-22
How did you get the script? If you downloaded it from [here]("http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/convert-to-latest-version-of-ubuntu.html"), it should work fine.

Your computer shouldn't need an internet connection to install the convert me script once you download it.

For the sources.list file check /etc/apt/sources.list.

I hope that helps.

---

### Post by mhancoc7 on 2006-09-22
Yes you will need a internet connection to run the convert_me script. The convert_me script also uses the mv command instead of the cp command. This was due to some permission issues. The next version will eliminate that issue. So for now you can only run the script once then toss it. Sounds like you probably ran it a second time. In your /etc/apt folder you should see at least one dated backup of your sources.list file. This was created by the convert_me script. You simply need to rename it to sources.list to restore your sources. Also you will need to extract the script fresh and run it. If you have an internet connection it should work fine. It is simply a front end for apt-get with a few other modifications to add icons and such.

Please let me know if you have any trouble.

God Bless, Jereme

---

### Post by Isoss on 2006-09-22
I still dunno what was going wrong, but I tossed the script, and untarred it again and then I ran sudo su to go as root and ran ./start in terminal and it worked! Now I have CE ... thanks and I like it .. :)

---

### Post by mhancoc7 on 2006-09-22
> **Isoss said:**
> I still dunno what was going wrong, but I tossed the script, and untarred it again and then I ran sudo su to go as root and ran ./start in terminal and it worked! Now I have CE ... thanks and I like it .. :)

Great! I am glad to hear that you got it going. I hope you enjoy it and sorry for your trouble with the script.

God Bless, Jereme

---

### Post by Isoss on 2006-09-23
no problem ... I know some bash .. but not all people do so I guess the script should be developed fast so those who live beind proxy servers can servive ;)

---

