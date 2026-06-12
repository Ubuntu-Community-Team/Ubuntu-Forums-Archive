---
title: "[UK] Watch Channel 4 &quot;4od&quot; programmes WITHOUT ads!"
date: 2010-10-18
forum: The Cafe
---

### Post by youbuntu on 2010-10-18
Here is something I picked up from Google (and TESTED myself, I better say!), and wanted to share. This is how you cut out all those annoying (and time sucking) channel 4 TV ads when streaming through 4od:

1/ Goto [http://channel4.com/4od](http://channel4.com/4od) and click ANYTHING to watch, so long as you watch the ads that appear before the start of the programme.

2/ Let the programme run a few seconds, then close the browser (tested on Firefox).

[COLOR=Red]3/ Do not clear the browser cache, otherwise you will need to re-do steps 1 & 2[/COLOR]

4/ Finally, do:

```
sudo nano /etc/hosts
```and put the following lines into your "hosts" file:

```
# hopefully kill off STUUUPID 4od ads
127.0.0.1       s0.2mdn.net
127.0.0.1       realmedia.channel4.com
127.0.0.1       webstat.channel4.com

```

Save & exit nano.

5/ Finally, what I did was to disconnect from my wi-fi, and then I did:

```
sudo ifconfig eth1 down [RETURN]
sudo ifconfig eth1 up [RETURN]

```I then reconnected to my wi-fi, went back to 4od and BAZINGA! NO ADS TO INTERRUPT TV!!

If you clear the cache, you need to repeat steps 1 & 2, as channel 4 store something which allows you on with blocked domains - don't ask me what it is.

---

### Post by benerivo on 2010-10-18
I run privoxy and have just started to use 4oD today. It didn't show any ads either before or 'halfway through' the programme. Tested on today's Deal or No Deal, and last Christmas' Trigger Happy tv episodes.

---

### Post by cra1g321 on 2010-10-19
i use adblock in firefox which seems to block the ads. Alot easier too

---

### Post by guildofghostwriters on 2010-10-19
+1 for adblock. Watched 4od for years without realising it had ads because of adblock.

---

### Post by youbuntu on 2010-10-19
I hate to tell you this, but ad block DOES NOT work! I still get annoying Channel 4 ads, showing me previews of other Channel 4 shows. Am I doing something wrong?

:confused:

[EDIT] My bad - it does work - I was just too impatient to tweak it :$

---

### Post by cra1g321 on 2010-10-19
i always choose the 'easylist' adblock list

---

### Post by Lordpsymon on 2011-10-02
Excuse the necrophilia of threads, but I just tested your method in Chrome and it worked. Thanks!

---

### Post by mr-woof on 2011-10-02
I've always used adblock and didn't realise it took out all the ads on channel 4 on demand, until I reinstalled 10.04 netbook edition back on my eee without all the Firefox Addons. 

It's back on there now :)

---

### Post by sffvba[e0rt on 2011-10-02
Back to sleep thread...


404

---

