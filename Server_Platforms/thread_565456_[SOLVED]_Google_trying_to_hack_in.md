---
title: "[SOLVED] Google trying to hack in???"
date: 2007-10-02
forum: Server Platforms
---

### Post by NaSiO6 on 2007-10-02
ok... this might sound very stupid... but please bear with me..

i installed firestarter on my system some days back.

today i got a 'blocked connections' event in it.
the port was some obscure no. from some ip, from some unknown application. and when i 'looked up' the host name, it showed me kr-in-f165.google.com

i personally think this is very weird and i dont think google has any business to open a 40000+ port.i dont have any sort of google applications(google gadgets for linux??) on my system.

pidgin for chatting..yeah...

so...do you guys think that someone(my linux geek friend) is trying something on me?

ultra superdy duperdy n00b

---

### Post by MJN on 2007-10-02
Have you got the firewall logs?

---

### Post by netlogic on 2007-10-03
Are you running Apache? What do you mean by 40000+? Google tried to open that many ports or they were probing port 40,000.  Where is your DNS pointed at? Are you running your own DNS server? Do you think you are running any services that might contact Google?
If you type, "host kr-in-f165.google.com" does it say 66.102.11.165? If yes, you are not being hacked. It is probably an application you are using or it could be their webots looking for websites to index. Many things on the net are noise. Nothing to be paranoid about. I doubt Google wants to bother hacking home users. It is very illogical. Also, there are people out there do the googlewatch. It is just noise on the net.

---

### Post by Oen386 on 2007-10-03
"pidgin for chatting..yeah..."

Are you using that for Gtalk?

---

### Post by nowshining on 2007-10-05
google is just scanning for people torrenting and is also owns level3 (which i use by the way as my isp as they own juno) and I got those all the time. :) they are in use by the USA government u know which is hiding with their ip to again track unlawful citizens, not just for torrenting also for those sharing other bad files, etc..

---

### Post by netlogic on 2007-10-05
> **nowshining said:**
> google is just scanning for people torrenting and is also owns level3 (which i use by the way as my isp as they own juno) and I got those all the time. :) they are in use by the USA government u know which is hiding with their ip to again track unlawful citizens, not just for torrenting also for those sharing other bad files, etc..

i am sorry.  where did you get your information? lol. i am sorry i find it a bit funny.

---

### Post by nowshining on 2007-10-05
I got it from thinking, reading, and UNDERSTANDING google itself. :) it came from various sources and more of it being that I am smart enough to interprit what is going on, well i'm not the only one, I also watch the words they say and they words they write up on the net, I read and understand what they are doing, it also is google bots surfing the net u know ;) 

if u want download bluetack.co.uk lists and google will be in there in one of the torrent lists which should give a clue about also the MPAA and RIAA using them. Peerguardian put those things together in one list tho with the GOV.

As for the level3 part, u see level3 owns juno internet service, which i read and can also agree with due to I am using one of Level3s beginning gateway to the net, compared to Juno's default one and can still surf the net. Also when I did use windows and peerguardian when the firewall I used was off (i used comodo firewall which is good) juno would and still does send igmp pings constantly to me, etc.. and well  a lot of those peerguardian would say came from google and it happenend no matter what ip i was at which would be the clue. Google does own a stake in a lot of things u do know that right. :)

---

### Post by netlogic on 2007-10-05
I think you are being very paranoid. I don't think that is happening. If that is true, most security firms probably examine the situation long time ago. Also, I doubt they want to jeopardize their public relations. Unless, you have complete evidence with documentations, it is highly unlikely that is happening. Webots scan for http servers and only index the public read only files. That isn't intrusion. That is like someone is taking a pictures front of your house. What others are watching google is about how long they maintain their history search files of their users. Others are watching google to see if they are keeping up with their promises.
Google isn't hacking anyone.

---

### Post by MJN on 2007-10-05
nowshiing, I've got some tin-foil if you'd like some? ;)
 
Mathew

---

### Post by steve.horsley on 2007-10-06
Hey, you have to be really careful with that tin foil stuff. If you get the shape wrong, it forms a resonant cavity that actually concentrates and magnifies the waves inside. You should really coat the inside with some non-corrosive electrolytic fluid to damp the resonsnce. 

But the black helicopters have agents who are always on the lookout for anyone buying electrolyte.

---

### Post by netlogic on 2007-10-06
Don't tell me, you guys are one of those weirdos who tin-foils the entire car and go war driving... better off with a concentrate motorized antenna with GPS. Look for the thunderstorm and yell and sing along to the 80s songs about the electricity isn't so tragic. When the signals formed resonance besides sounds?

---

### Post by ice60 on 2007-10-06
firefox contacts google to update the phishing stuff every 30 mins i think, but i thought it used a ssl connection for that so maybe this isn't the same thing :confused:

you can try doing this to disable it

type about:config in to the address bar
then paste this into the filter bar that's just below the tabs
browser.safebrowsing.enabled

then double click it so it goes to false

that might help, i'm just copying and pasting stuff from a post i did a year a go when firefox added that 'feature'

EDIT just to show what i'm on about this is a link about it -
[http://kb.mozillazine.org/Browser.safebrowsing.provider.*.keyURL](http://kb.mozillazine.org/Browser.safebrowsing.provider.*.keyURL)

---

### Post by NaSiO6 on 2007-10-19
> **netlogic said:**
> 
If you type, "host kr-in-f165.google.com" does it say 66.102.11.165? If yes, you are not being hacked. It is probably an application you are using or it could be their webots looking for websites to index. Many things on the net are noise. Nothing to be paranoid about. I doubt Google wants to bother hacking home users. It is very illogical. Also, there are people out there do the googlewatch. It is just noise on the net.

yup it did show that ip, stupid me....
:)

---

