---
title: "World of Warcraft gets stuck at connecting to server"
date: 2011-04-21
forum: Wine
---

### Post by Shmantiv_Radio on 2011-04-21
It won't go any further and Google hasn't really helped much.

Terminal output is this, whatever it means.

```
smapt3@smapt3-N130:~$ '/home/smapt3/Downloads/WOW-4.0.0.12911-enGB-Trial.exe' 
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (15000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 15000
fixme:ntdll:NtPowerInformation semi-stub: SystemPowerCapabilities
fixme:font:CreateScalableFontResourceW (0,L"C:\\users\\Public\\Application Data\\Blizzard Entertainment\\FrizQuadrata.fon",L"C:\\users\\Public\\Application Data\\Blizzard Entertainment\\FrizQuadrata.ttf",(null)): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x171650,0x1715c0): stub

```

Thanks in advance if anyone knows how to fix :)

P.s. The Wine iexplorer browser works fine, as does all the other net stuff, so I don't think it's a connection/driver issue.

---

### Post by Tweak42 on 2011-04-21
Has the game connected, logged in and worked before?  Or is this a first time install?

---

### Post by Chen78 on 2013-02-20
i have the same problem
fresh install

any ideas?

---

### Post by Thee on 2013-02-20
Do you have winetricks installed?

---

### Post by SkipHuffman on 2013-05-10
I seem to be having the same problem   I have Ubuntu 12.04 installed on my wife's HP mini along with wine 1.5   WoW launcher starts and connects to the servers for updates.  But when we try to log into the game we get an Error #105 and "Server Disconnected".  I do understand that this typically means that there is a problem with the Auth server on Blizzard's side, but it has been going on for three days now, while I can  connect on my laptop (Mint Maya, same Wine version) either with her WoW account, or my own.

Would really like to get her system working so we can play together, instead of her borrowing my laptop.

I have used the winetricks tool and so far it hasn't made any difference.

---

### Post by Lightning Dragon on 2013-05-10
Hi, 

Have you considered reading the HOWTO thread for World of Warcraft located in the Gaming sub-forum for answers to your problem? If not, the link is in my signature. If you post there, you have a higher chance of getting your problem resolved. :)

---

### Post by SkipHuffman on 2013-05-11
Hey,thanks!

---

### Post by SkipHuffman on 2013-05-11
[COLOR=#000000]Thanks, but pointing me to a thread that has been growing for most of a decade, with thousands of posts is not terribly helpful. I am sure that thread is very useful for the people who are researching and figuring out things. But it would be very useful if someone were to pull together a FAQ for users of recent builds of Linux, WoW and Wine.[/COLOR]

---

### Post by Lightning Dragon on 2013-05-11
Hi,

Unfortunately gathering all the information from that massive thread to build a FAQ would require a lot of time from people, especially if only one person were to do it. The purpose of linking you to the thread was that you could either ask there for a solution to your problem (another is having the same issue) or search the thread manually or automatically for a solution to your problem. I have found additional links for you to take a look at, as well;

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
[http://howto.cnet.com/8301-11310_39-10418439-285/running-world-of-warcraft-in-ubuntu-linux/](http://howto.cnet.com/8301-11310_39-10418439-285/running-world-of-warcraft-in-ubuntu-linux/)
[http://us.battle.net/wow/en/forum/topic/1020822642](http://us.battle.net/wow/en/forum/topic/1020822642)
[http://us.battle.net/wow/en/forum/topic/7200180928](http://us.battle.net/wow/en/forum/topic/7200180928)
[http://kastang.com/blog/2010/08/installing-and-configuring-wow-on-linux/](http://kastang.com/blog/2010/08/installing-and-configuring-wow-on-linux/)
[http://sergioandresmeneses.wordpress.com/2012/11/28/playing-world-of-warcraft-with-ubuntu/](http://sergioandresmeneses.wordpress.com/2012/11/28/playing-world-of-warcraft-with-ubuntu/) (< carries even more tutorial links at the end)
[http://askubuntu.com/questions/226809/how-to-install-run-world-of-warcraft-on-ubuntu-12-04-1](http://askubuntu.com/questions/226809/how-to-install-run-world-of-warcraft-on-ubuntu-12-04-1)
[http://ubuntuforums.org/showthread.php?t=2049114](http://ubuntuforums.org/showthread.php?t=2049114)
[http://www.youtube.com/watch?v=WwkP0ynts6c](http://www.youtube.com/watch?v=WwkP0ynts6c)
[http://askubuntu.com/questions/10779/how-to-install-world-of-warcraft](http://askubuntu.com/questions/10779/how-to-install-world-of-warcraft)

The above links and the HOWTO thread have pulled together all the help on the internet one can find for their problems. If I find anything else, I will update or let you know. :)

---

