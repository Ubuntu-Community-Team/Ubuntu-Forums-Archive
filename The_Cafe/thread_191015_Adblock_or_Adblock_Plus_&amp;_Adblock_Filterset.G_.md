---
title: "Adblock or Adblock Plus &amp; Adblock Filterset.G Updater for Opera 9.00 beta 2"
date: 2006-06-07
forum: The Cafe
---

### Post by RAV TUX on 2006-06-07
I have been looking for an extension for Opera 9.00 beta 2 that is comparable to Adblock Plus 0.7.0.1 and Adblock FilterSet.G Updater 0.3.0.4 found on Firefox 1.5.0.4. for both my Ubuntu 6.06 & XPsp2 box

I did find Python Adblocker for Opera but am finding it hard to figure out:
[http://operawiki.info/OperaPythonAdblock](http://operawiki.info/OperaPythonAdblock)

there is also a C++ Adblocker for Opera
[http://operawiki.info/CPlusPlusAdBlock](http://operawiki.info/CPlusPlusAdBlock)

and here is an Opera Adblock thread
[http://my.opera.com/community/forums/topic.dml?id=75874&t=1149653511&page=11#comment1216738](http://my.opera.com/community/forums/topic.dml?id=75874&t=1149653511&page=11#comment1216738)

I was just wondering if anybody here has been successful in implementing Adblock for Opera?

---

### Post by RAV TUX on 2006-06-07
[quote=yozef]I have been looking for an extension for Opera 9.00 beta 2 that is comparable to Adblock Plus 0.7.0.1 and Adblock FilterSet.G Updater 0.3.0.4 found on Firefox 1.5.0.4. for both my Ubuntu 6.06 & XPsp2 box

I did find Python Adblocker for Opera but am finding it hard to figure out:
[http://operawiki.info/OperaPythonAdblock]("http://operawiki.info/OperaPythonAdblock")

there is also a C++ Adblocker for Opera
[http://operawiki.info/CPlusPlusAdBlock]("http://operawiki.info/CPlusPlusAdBlock")

and here is an Opera Adblock thread
[http://my.opera.com/community/forums/topic.dml?id=75874&t=1149653511&page=11#comment1216738]("http://my.opera.com/community/forums/topic.dml?id=75874&t=1149653511&page=11#comment1216738")

I was just wondering if anybody here has been successful in implementing Adblock for Opera?[/quote]

also a 
** Lua Adblocker for Opera **

[http://operawiki.info/OperaLuaAdblock](http://operawiki.info/OperaLuaAdblock)

---

### Post by RAV TUX on 2006-06-07
am I the only one using Opera on Linux?

---

### Post by SlugO on 2006-06-21
I think it's better to just use the built in ad blocker that comes with Opera.
It's not exactly as powerful as FF's Adblock but atleast it's light, you don't need anything extra. And if some ads get past it just click to block em or add new rules.

Here's my urlfilter.ini that works pretty well, just remove the .txt from the end and add it to .opera directory.

---

### Post by RAV TUX on 2006-06-21
[quote=SlugO]I think it's better to just use the built in ad blocker that comes with Opera.
It's not exactly as powerful as FF's Adblock but atleast it's light, you don't need anything extra. And if some ads get past it just click to block em or add new rules.
 
Here's my urlfilter.ini that works pretty well, just remove the .txt from the end and add it to .opera directory.[/quote]
 
Great! Thanks for the advice.

---

### Post by Flavian on 2006-08-14
Thank you very much!
I was searching for a good Adblocker for such a long time!
Since I don't like Firefox at all I was trying hard to find an adblocker to block out all the crap that was presented through that.

My thanks go to you guys...
The ini file works just fine and does everything I need :)

Thanks
Flo

---

### Post by ice60 on 2006-08-14
hi, i'm about %80 sure you can use the Adblock filter set with Privoxy 
```
apt-get install privoxy
```

privoxy by it self will block most things, it's an http proxy.

to configure Opera to use Privoxy all you have to do is go to -
Tools>Preferences>Network>Proxy Servers

then configure it like the screenshot, and that's it - everytime you startup Opera it will use Privoxy.

you can also use an adblocking hosts file

---

### Post by ice60 on 2006-08-14
i just thought i'd let you know that the places to look where to put the adblock filter set would be these -

/etc/privoxy/default.action
/etc/privoxy/config
/etc/privoxy/user.action

this will show if it's running -
ps -e |grep privoxy

and this is how to start and stop it -
sudo /etc/init.d/privoxy start
sudo /etc/init.d/privoxy stop

---

### Post by ice60 on 2006-08-14
i just had alook and maybe you can use the 'filter file'

[http://www.privoxy.org/3.0.3/user-manual/config.html#FILTERFILE](http://www.privoxy.org/3.0.3/user-manual/config.html#FILTERFILE)

> The filter file contains content modification rules that use regular expressions. These rules permit powerful changes on the content of Web pages, e.g., you could disable your favorite JavaScript annoyances, re-write the actual displayed text, or just have some fun replacing "Microsoft" with "MicroSuck" wherever it appears on a Web page.

[http://www.privoxy.org/3.0.3/user-manual/filter-file.html](http://www.privoxy.org/3.0.3/user-manual/filter-file.html)

it should be in /etc/privoxy/ i'm using SUSE atm and it's in a different place on SUSE -
/var/lib/privoxy/etc

BTW, i think it would be great if we could use the filter set even though Privoxy by itself is very good :)

---

### Post by Flavian on 2006-08-14
Privoxy does not work on my PC. Well it did in the past... but it won't work anymore, after I reinstalled it!
It can't find the config file.

Actually it blocked too much on my Pc that's why I deleted it.
I was not very happyx with how to configure it because I couldn't figure out how to :/ was a little bit too difficult for me, so I just searched for an easier to use tool, like admuncher on windows.

Opera with the file posted above seems to fulfill it's purpose :)
Thanks though!
Flo

---

### Post by Erik Trybom on 2006-08-14
My favourite method is to use a user javascript that gets rid of all flash elements until I click them, and then disable GIF animation. This rids me of most *annoying* ads. I don't mind ads all that much, but when they move or sound and bog down my cpu they have to go.

---

### Post by ice60 on 2006-08-15
i just installed TOR, to be anonymous on the internet, and i had another look at Privoxy as they work together, anyway, i think you can just import the adblock filter to the default.action file, this is how the default filter looks
```
#####################################
# Generic block patterns by host:
###########################################
{+block}
ad*.
.*ads.
.ad.
*banner*.
count*.
*counter.
```so if you can just import adblock there it should be easy to setup -
```
sudo apt-get install privoxy
```
just this first time you might have to start it
```
sudo /etc/init.d/privoxy start
```
then 
```
sudo gedit /etc/privoxy/default.action
```
and copy and paste the filter set to the place i showed above. i hope someone tries it out. i have other adblockers already, but i'd switch if it works OK. :)

will it work?

---

### Post by ice60 on 2006-08-15
this bit might have to be changed

########################
# Defaults
########################
-add-header \
-block \
-crunch-outgoing-cookies \
-crunch-incoming-cookies \
-deanimate-gifs{last} \

change the 
-block \

to this
+block \

i'm not sure though.

---

### Post by go_beep_yourself on 2007-11-15
I have a dual boot of ubuntu 7.10 64 bit and wintendo for gaming. I put a lot of open source applications into wintendo such as gnu gpg, firefox, 7-zip, etc. I installed the adblock firefox extension in Firefox. Many advertisements are not being blocked, so I need the Adblock filterg set extension also. However, when I try to install that. I get this error below. Can anyone help?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=50281&stc=1&d=1195147389[/IMG]

---

