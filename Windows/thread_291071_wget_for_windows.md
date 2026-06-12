---
title: "wget for windows"
date: 2006-11-02
forum: Windows
---

### Post by imrumpf on 2006-11-02
Here is a little somthing I found the other day. I never saw this mentioned on any linux forum so I decided to include it! :D

Basically all this is, is a windows version of a linux command called "wget". yeah yeah so what you ask...well here is a scanario...

I work for microsoft (ironic i know) and do tech support for IE7.You would have no idea how many times a person will install it, it messes up, you try to remove it only to find out there are missing files, and then you cannot access the internet at all! Of course there is nothing else I can do, so since we are in a pickle, the call gets escalated and the customer gets a call back by somebody else the next day.

Now imagine this little utility was installed...imagine the possibilities! like for example, you cannot use IE7 (it opens and then closes right away) because the ieproxy.dll file is missing, and the only way to get it is thru the installer file. Wait...IE doesn't work? you're royally screwed (unless you use firefox :D). Not so anymore...just type in the following in the command prompt:

```
wget http://switch.atdmt.com/action/IE_7_Windows_XP_SP2_B
```

Boom! The offical IE7 installer file is downloaded and ready to use!

The site where I got it from can be found [here]("http://users.ugent.be/%7Ebpuype/wget/").

For sake of easyness, i packaged wget it into a self-extracting file so it will automatically extract "wget.exe" into the "C:\Windows\system32" folder. If you have windows on a different drive letter, please extract the file manually and move it yourself.

I swear..sometimes linux is years ahead of windows...if M$ had this built into their OS, my life as a tech support agent would be 100% easier, espescially since I troubleshoot IE..

What do you think of it all?

---

### Post by Phantom784 on 2006-11-05
Cool, but it won't help you out with tech support unless microsoft decides to pre-install it on all computers.  If ie7 is broken, you can't download that program either.

---

### Post by imrumpf on 2006-11-05
like i said in my first post, i stated " Now imagine this little utility was installed". I know it is not and i think Microsoft has a ways to go before they even begin to match the power of the linux kernel.  one more reason to love Ubuntu :)

---

### Post by Dr. C on 2006-11-07
How would this work with Windows Genuine Advantage, validation etc?

---

### Post by imrumpf on 2006-11-08
as far as downloading files, there is no effect whatsoever. Using the link provided in my first post, you can download the IE7 installation file with no problems in wget. as long as you have a direct http link to a file, wget can retrieve it, much like in linux.


IE7 actually has a validation check built-in, so if you want to bypass WGA to install this software, you will need to find a hacked illigal version on bittorrent, IRC, or wherever else you find your files.

hope that cleared some confusion up.

---

### Post by K.Mandla on 2006-11-08
Thanks for the tip. I've been wanting something like this for Windows for quite a while. Cheers!

---

### Post by oso yogui on 2008-10-08
Hi I having problems to download RSS pages with Wget, when I try to download , appears the following message:


" Connecting to 209.88.15.139:80... connected!
Proxy request sent, awaiting response... 302 Object Moved
Location: [http://www.portafolio.com.co/atom-resumen.xml](http://www.portafolio.com.co/atom-resumen.xml) [following]
[http://www.portafolio.com.co/atom-resumen.xml:](http://www.portafolio.com.co/atom-resumen.xml:) Redirection to itself "

what should I do? or maybe Im doing something wrong, here is my commands :

 wget  -O C:\Inetpub\wwwroot\rss\economia2.xml  [http://www.portafolio.com.co/atom-resumen.xml](http://www.portafolio.com.co/atom-resumen.xml)

---

### Post by Steve1961 on 2008-10-08
As well as wget you can also get other little gems such as dig, which is much better than nslookup.  That said, if forced to use windows it's probably a good idea to just install cygwin so you can have openssh, nano, dig, wget and a whole rack of other stuff.

---

