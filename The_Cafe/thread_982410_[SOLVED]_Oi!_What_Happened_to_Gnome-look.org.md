---
title: "[SOLVED] Oi! What Happened to Gnome-look.org??"
date: 2008-11-14
forum: The Cafe
---

### Post by nufros on 2008-11-14
It seemed fine yesterday... now when I go to [http://www.gnome-look.org/]("http://www.gnome-look.org/"), all I get is redirected here [http://www2.searchresultsdirect.com/parking.php4?domain=gnome-look.org&registrar=238091&eq=6f9ee28c3b53cb947e87f56c90d280d3]("http://www2.searchresultsdirect.com/parking.php4?domain=gnome-look.org&registrar=238091&eq=6f9ee28c3b53cb947e87f56c90d280d3")

Anybody know what's up? :confused:

---

### Post by pt123 on 2008-11-14
I was just about to post this too

I am getting the same page too.

[http://kde-look.org/](http://kde-look.org/) is fine

---

### Post by Kingsley on 2008-11-14
It's working now.

---

### Post by SuperSonic4 on 2008-11-14
kde-look was the same a few days ago. I just think it's getting a facelift

---

### Post by damis648 on 2008-11-14
All I am getting is one of those place-holder sites... what is happening? Is this a sign of the apocalypse?!

---

### Post by igknighted on 2008-11-14
> **damis648 said:**
> All I am getting is one of those place-holder sites... what is happening? Is this a sign of the apocalypse?!

KDE-look works fine, but I get the same thing on gnome-look.  Probably a DNS error somewhere.

---

### Post by binbash on 2008-11-14
> **damis648 said:**
> All I am getting is one of those place-holder sites... what is happening? Is this a sign of the apocalypse?!

There is nothing wrong here?

---

### Post by sstecken on 2008-11-14
I just did a fresh install and went to Gnome-look.org after upgrading the default system and loading in some nvidia drivers.

Does anyone else get redirected to:
[http://www2.searchresultsdirect.com/parking.php4?domain=gnome-look.org&registrar=238091&eq=6f9ee28c3b53cb947e87f56c90d280d3](http://www2.searchresultsdirect.com/parking.php4?domain=gnome-look.org&registrar=238091&eq=6f9ee28c3b53cb947e87f56c90d280d3)

Edit:  I can see that the title bar says "Eye candy" but then it immediately redirects. Is it me or were they hijacked?

---

### Post by damis648 on 2008-11-14
Yes, it is very wierd... can we get a thread merge?:
[http://ubuntuforums.org/showthread.php?t=982426](http://ubuntuforums.org/showthread.php?t=982426)

---

### Post by siafok on 2008-11-14
I am suprised too, dont know what is going on.

---

### Post by damis648 on 2008-11-14
> **siafok said:**
> I am suprised too, dont know what is going on.

Scary stuff here.:popcorn:

---

### Post by KillerZ on 2008-11-14
Its working for me. Strange.

---

### Post by scouser73 on 2008-11-14
It's working for me also.

---

### Post by sisco311 on 2008-11-14
it's working for me.

try: [http://87.106.93.206/]("http://87.106.93.206/")

---

### Post by sstecken on 2008-11-14
If you turn on NoScript in Firefox, it doesn't redirect, but the page is definitely messed up.

---

### Post by init1 on 2008-11-14
Working fine here

---

### Post by init1 on 2008-11-14
Yeah, it was working about 2 minutes ago, but now I'm geting that domain place-holder page. Strange.

---

### Post by doorknob60 on 2008-11-14
Works for me (I use OpenDNS, maybe your DNS server isn't as quick updating and they changed servers or something, IDK)

---

### Post by elmer_42 on 2008-11-14
It's not working here, either.

---

### Post by super.rad on 2008-11-14
yeah working fine for me aswell (using openDNS aswell)

---

### Post by init1 on 2008-11-14
It's working now, but it stops working every few minutes.

---

### Post by bswilson on 2008-11-14
Still down for me.  A quick dig query shows that the A record is the same IP address as kde-look.org.

However, if you look at the Authority section, inwx.de is the domain that controls the record.  I don't believe that inwx.de is malicious, but that is a Gernam domain registrar's name, whereas 87.106.93.206 is from Amsterdam. 

Sounds like a DNS screwup somewhere.

```
$ dig www.gnome-look.org A

; <<>> DiG 9.5.0-P2 <<>> www.gnome-look.org A
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 49280
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 3

;; QUESTION SECTION:
;www.gnome-look.org.            IN      A

;; ANSWER SECTION:
www.gnome-look.org.     3600    IN      A       87.106.93.206

;; AUTHORITY SECTION:
gnome-look.org.         86400   IN      NS      ns3.inwx.de.
gnome-look.org.         86400   IN      NS      ns2.inwx.de.
gnome-look.org.         86400   IN      NS      ns.inwx.de.

;; ADDITIONAL SECTION:
ns3.inwx.de.            2453    IN      A       217.20.112.194
ns2.inwx.de.            2453    IN      A       213.239.206.103
ns.inwx.de.             1032    IN      A       217.70.142.66

;; Query time: 152 msec
;; SERVER: 24.25.5.149#53(24.25.5.149)
;; WHEN: Fri Nov 14 18:56:57 2008
;; MSG SIZE  rcvd: 160
```

---

### Post by bswilson on 2008-11-14
I forgot to say, look at the dig information for kde-look.org.  The Authority section is owned by WorldNIC in the US.

```
;; ANSWER SECTION:  
[www.kde-look.org](www.kde-look.org).       7200    IN      A 87.106.65.160                                                                         
;; AUTHORITY SECTION:                                              kde-look.org.           5307    IN      NS      ns9.worldnic.com.  kde-look.org.           5307    IN      NS      ns10.worldnic.com

```

---

### Post by BobCFC on 2008-11-14
Same problem here.

Compiz-themes.org is still up,so is opendesktop.org

---

### Post by gkrules on 2008-11-14
I think the site has been hijacked.
WOT warns that the site is a suspected malware site and will try and put malware/viruses on your computer. 


I don't know why they would do that to a linux website but whatever.

---

### Post by SomeGuyDude on 2008-11-14
Rolling along fine here.

---

### Post by eternalnewbee on 2008-11-14
Not working here.

---

### Post by Meshach on 2008-11-14
Works fine for me...


Clear your cache.



Meshach

---

### Post by mrgnash on 2008-11-14
Getting the redirect here.

---

### Post by yaknowwat on 2008-11-14
[http://www.gnome-look.org](http://www.gnome-look.org)

It doesn't seem to be there does anyone know what happened to it? 
This could be a serious issue.  I was about to look for some themes and noticed it.

---

### Post by yaknowwat on 2008-11-14
How do we get gnome look back?

---

### Post by Mardoct909 on 2008-11-14
Umm... What? Noticed what? Sometimes sites go down. When it happens, you try again tomorrow.

---

### Post by tvtech on 2008-11-14
what do you mean it's gone?  I go there lickity split.  even downloaded a couple desktops while I was at it. perhaps your having an isp problem  you should do a traceroute  and see what's going on.

---

### Post by ciscosurfer on 2008-11-14
> **yaknowwat said:**
> ...It doesn't seem to be there does anyone know what happened to it? This could be a serious issue.You could look into using [OpenDNS]("http://www.opendns.com/").

---

### Post by Frak on 2008-11-14
> **mrgnash said:**
> Getting the redirect here.
Sounds like a poisoned DNS cache on whichever sub-continental hub you happen to be going through.

While chances are low, it could happen :P

---

### Post by tvtech on 2008-11-14
> **ciscosurfer said:**
> You could look into using [OpenDNS]("http://www.opendns.com/").

don't do it!

---

### Post by Meshach on 2008-11-14
> **Frak said:**
> Sounds like a poisoned DNS cache on whichever sub-continental hub you happen to be going through.

While chances are low, it could happen :P


I think that might be it...


For those of you who are getting the redirect, maybe try using the [opendns.com]("http://www.opendns.com") dns servers?



Regards,
Meshach

---

### Post by eternalnewbee on 2008-11-14
> 
Works fine for me...


Clear your cache.

Didn't work.

---

### Post by Mardoct909 on 2008-11-14
It's fine for me. Maybe it's because I have no script.

Just tried without it... Nope, that's not it.

---

### Post by ciscosurfer on 2008-11-14
> **tvtech said:**
> don't do it!Whatever floats your boat ;-)

---

### Post by voteforpedro36 on 2008-11-14
Lol it goes down like once a month, there are so many of these threads around.

---

### Post by Saint Angeles on 2008-11-14
gnome-look is full of jealous artists that like to rate every theme bad, if it's not theirs.

they really need to change that rating system to one that only takes s "good" rating. that way, the best ones will have the best ratings... this whle "lets start at 50%" thing is pretty dumb.

---

### Post by mrgnash on 2008-11-14
> **Saint Angeles said:**
> gnome-look is full of jealous artists that like to rate every theme bad, if it's not theirs.

they really need to change that rating system to one that only takes s "good" rating. that way, the best ones will have the best ratings... this whle "lets start at 50%" thing is pretty dumb.

Nonsense. Good themes generally, but not always, receive good ratings. Most of the antipathy is toward the multitude of OSX/Vista ripoffs which do indeed deserve to be rated poorly.

---

### Post by Tprnyc on 2008-11-14
[http://gnome-look.org](http://gnome-look.org) - sends me to the BS site.

[http://www.gnome-look.org](http://www.gnome-look.org) - sends me to the real site.

:confused:

---

### Post by wolfen69 on 2008-11-15
gnome-look.org doesn't work for me.

---

### Post by Anduu on 2008-11-15
Here's my situation...

Go to gnome-look with Opera it works fine...Use Firefox and get redirected...

Tried clearing cache but no change

Ack! :confused:

---

### Post by Anduu on 2008-11-15
Opera gets me to gnome-look just fine...Firefox gets me redirected.

Tried clearing cache but no dice.

Any ideas?

---

### Post by Mardoct909 on 2008-11-15
Works fine in FF for me.

---

### Post by Anduu on 2008-11-15
This is just plain goofy....Oh well,we'll see where things are at tomorrow.

---

### Post by Kantis on 2008-11-15
Neither Firefox nor Opera works for me, I get the same redirection from both.

---

### Post by armageddon08 on 2008-11-15
Me too :(

---

### Post by perfectska04 on 2008-11-15
> **Tprnyc said:**
> [http://gnome-look.org](http://gnome-look.org) - sends me to the BS site.

[http://www.gnome-look.org](http://www.gnome-look.org) - sends me to the real site.

:confused:

They **both** send me to the BS site. :confused:

---

### Post by Yellow Pasque on 2008-11-15
It looks fine to me in Swiftweasel(FF) 3.03

---

### Post by garfilth on 2008-11-15
Tried in FF, Opera and Epiphany no joy.

Checked the site in site advisor ( the site thats there now ) and they give it a green but one reviewer says Adware, Spyware and Viruses.

very strange. kde-look and xfce-look are fine.

---

### Post by scouser73 on 2008-11-15
I've tried it on Firefox and it works, I'm unsure as to why you are being redirected.

---

### Post by bapoumba on 2008-11-15
I've merged all the gnome-look access issues in this thread.

---

### Post by b0b138 on 2008-11-15
The site seems to be back up.

---

### Post by damis648 on 2008-11-15
> **b0b138 said:**
> The site seems to be back up.

Thats all great and all, but does anyone know actually what happened?

---

### Post by eternalnewbee on 2008-11-15
> The site seems to be back up.
Just a couple of minutes. Then it's **"the smiling ladies' screen of death"**.

---

### Post by hoagie on 2008-11-15
It works fine for me, Im using Firefox.

---

### Post by Martje_001 on 2008-11-15
Defaced maby?

---

### Post by bonzodog on 2008-11-15
I cannot get into gnome-look either, but all other *-look sites are fine. You can use xfce-look for GTK themes, compiz/emerald has its own site, and there is box-look for the box WM users.

---

### Post by init1 on 2008-11-15
It's working (for now)

---

### Post by lukjad on 2008-11-16
> **kingsley said:**
> it's working now.
+1

---

### Post by nufros on 2008-11-16
> **init1 said:**
> It's working (for now)


I marked this thread as [SOLVED] because the problem seems to have sorted itself out... it would be nice to know definitively what happened though... I'm kinda leaning toward dns error

oh well... at least it's back, so now I can continue the never-ending project of customizing my GDE :lolflag:

---

### Post by billmx1313 on 2011-08-08
Its not working!!

---

### Post by lisati on 2011-08-08
I wonder what this thread did to have its sleep disrupted after three years.

---

