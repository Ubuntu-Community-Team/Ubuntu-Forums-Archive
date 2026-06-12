---
title: "Server is functioning great!"
date: 2009-08-20
forum: The Cafe
---

### Post by dragos240 on 2009-08-20
Yay! I got my arch netbook to work as a 3 in 1 server! A webserver (apache), a FTP server (pure-ftpd), and a SSH server (openSSH). For (almost) 2 days nonstop, see mah uptime ^.^:
18:23:18 up 1 day, 10:02,  2 users,  load average: 0.00, 0.01, 0.00

But now, I need a cooling unit. I already found a good one :)

Just felt the need to brag :) :lolflag:

---

### Post by kg84 on 2009-08-20
> **dragos240 said:**
> Yay! I got my arch netbook to work as a 3 in 1 server! A webserver (apache), a FTP server (pure-ftpd), and a SSH server (openSSH). For (almost) 2 days nonstop, see mah uptime ^.^:
18:23:18 up 1 day, 10:02,  2 users,  load average: 0.00, 0.01, 0.00

But now, I need a cooling unit. I already found a good one :)

Just felt the need to brag :) :lolflag:

Nice job - always good when things work :)

IP please / SSH login???  :lolflag:

---

### Post by Tibuda on 2009-08-20
Why FTP if you have SSH?

---

### Post by MaxIBoy on 2009-08-20
Current uptime of my server is 36 days. If it wasn't for a series of power outages we had, it would have been 101 days. But the all-time record on that particular box was 130 days.

---

### Post by dragos240 on 2009-08-20
> **danielrmt said:**
> Why FTP if you have SSH?

Why not ;)

---

### Post by Bachstelze on 2009-08-20
> **danielrmt said:**
> Why FTP if you have SSH?

In order not to give shell access to everyone that's going to transfer files to the server?

---

### Post by dragos240 on 2009-08-20
> **kg84 said:**
> IP please / SSH login???  :lolflag:
24.34.53.70
port 22
user: ubuntuforums
pass: ubuntu

---

### Post by Bachstelze on 2009-08-20
> **dragos240 said:**
> 24.34.53.70
port 22
user: ubuntuforums
pass: ubuntu

/facepalm

I hope you have upgraded your kernel...

---

### Post by dragos240 on 2009-08-20
Latest ver.
That's why I do:
# pacman -Syu

---

### Post by dragos240 on 2009-08-20
And don't worry, they don't have root access.

Yes, THIS is what happens when you give the ubuntuforums root access to your server:
[IMG]http://icanhascheezburger.files.wordpress.com/2008/12/funny-pictures-squirrels-have-discovered-coffee.jpg[/IMG]

And if you give a particular imageboard that well..........
[IMG]http://stopsocialism.files.wordpress.com/2009/04/nuclear-explosion-1.jpg[/IMG]

---

### Post by avahi on 2009-08-20
Forkbomb.

LY fail.

---

### Post by wojox on 2009-08-20
Don't you like powerpill?

Who's Harley?

---

### Post by schauerlich on 2009-08-20
Hey, put it back! And, first, lrn2limit processes.

---

### Post by dragos240 on 2009-08-20
> **wojox said:**
> 

Who's Harley?

The admin.

---

### Post by avahi on 2009-08-20
> **EDavidBurg said:**
> Hey, put it back! And, first, lrn2limit processes.

He was too stupid to block forkbombs. I totally just trashed that server.

---

### Post by Yes on 2009-08-20
Hehe and while you're at it could you install vim?  It's a pain leaving you messages with nano.

---

### Post by JillSwift on 2009-08-20
> **avahi said:**
> He was too stupid to block forkbombs. I totally just trashed that server.
Calling people "stupid" is not acceptable behavior.

He's learning, encourage him.

---

### Post by dragos240 on 2009-08-20
Vim is installed. But use vi. Trust me, it's vim.

---

### Post by Bachstelze on 2009-08-20
Just FYI, avahi has been banned.

---

### Post by dragos240 on 2009-08-20
> **avahi said:**
> He was too stupid to block forkbombs. I totally just trashed that server.

Darn..... Why didn't I think of that. Ah well. I'll restart it in the morning. Please don't call me stupid.

---

### Post by dragos240 on 2009-08-20
> **HymnToLife said:**
> Just FYI, avahi has been banned.

Thank you.

EDIT:
Did I just ban the user? I let him into my server, he crashed it, and now he's banned? I feel bad.

---

### Post by JillSwift on 2009-08-20
> **dragos240 said:**
> Thank you.

EDIT:
Did I just ban the user? I let him into my server, he crashed it, and now he's banned? I feel bad.
Don't blame yourself for other's choices.

---

### Post by dragos240 on 2009-08-20
Well. Anyways, I am off to find out ways to prevent fork bombs. :D

Even though it's down, it's great that it works!

---

### Post by K.Y.A on 2009-08-20
Lol it is down... That sucks, I was going to leave you messages.....

You can use "echo" to create text files, correct? Or is it "cat"?

---

### Post by dragos240 on 2009-08-20
I created a masterpiece:

@users          hard    nproc           50

Ta da!

---

### Post by dragos240 on 2009-08-20
> **K.Y.A said:**
> Lol it is down... That sucks, I was going to leave you messages.....

You can use "echo" to create text files, correct? Or is it "cat"?

Yeah, avahi bombed it. But he's banned now. But when it's back up, use vi or nano.

---

### Post by JillSwift on 2009-08-20
> **K.Y.A said:**
> Lol it is down... That sucks, I was going to leave you messages.....

You can use "echo" to create text files, correct? Or is it "cat"?

[SIZE=5]Echo [/SIZE][SIZE=3]echo [/SIZE]echo.

```
echo "your message" > the_file
```

---

### Post by Axon5 on 2009-08-20
> **dragos240 said:**
> Well. Anyways, I am off to find out ways to prevent fork bombs. :D

Even though it's down, it's great that it works!

Aw man that sucks.
Probably better that you learned that now instead of when you're running a production server :)

I wonder if there's a way to block all commands except "vi" for that one account.

Edit: WOO FIRST POST

---

### Post by K.Y.A on 2009-08-20
Oh, nano is installed? Good.

I use Nano all the time. Nano Rules!

Also: Only 50 processes? Lets say you get 200 visitors to your webserver....
BOOM!:lolflag:


I usually block it around 250 processes.

---

### Post by bobyo134 on 2009-08-20
well that is just great man , more power to ya , my old server is a dell with a 733mhz cpu from 1996 , ran amazing as a web server , but my new server is a hp dl380 g3 with dual xeon dual core @ 3.2ghz , 4 gigs of ecc ram and dual 36gb scsi drives in raid 1 , the saddest part is i think debain ran faster on the old one then ubuntu server on the new one

---

### Post by K.Y.A on 2009-08-20
I love Debian...

```
winrid@winrid-desktop:~$ server
root@192.168.1.125's password: 
Last login: Sat Jan  8 13:42:20 2000 from computer2007.hsd1.pa.comcast.net
Linux debian 2.6.18-6-686 #1 SMP Tue May 5 00:40:20 UTC 2009 i686

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
debian:~# uptime
 22:16:45 up 9 days,  3:15,  1 user,  load average: 0.16, 0.13, 0.10
debian:~# 

```

And no, I am NOT giving away my ip address...

---

### Post by dragos240 on 2009-08-20
> **Axon5 said:**
> Aw man that sucks.
Probably better that you learned that now instead of when you're running a production server :)

I wonder if there's a way to block all commands except "vi" for that one account.

Edit: WOO FIRST POST

Axon5? Are you avahi? You joined today........ and have no posts.....

---

### Post by Axon5 on 2009-08-20
> **bobyo134 said:**
> well that is just great man , more power to ya , my old server is a dell with a 733mhz cpu from 1996 , ran amazing as a web server , but my new server is a hp dl380 g3 with dual xeon dual core @ 3.2ghz , 4 gigs of ecc ram and dual 36gb scsi drives in raid 1 , the saddest part is i think debain ran faster on the old one then ubuntu server on the new one

FreeBSD is the fastest server OS, but it can be hard to configure.
But congrats :P

---

### Post by K.Y.A on 2009-08-20
> **dragos240 said:**
> Axon5? Are you avahi? You joined today........ and have no posts.....

We all have secrets :)


Don't exploit them, and you'll have less enemies... :)

---

### Post by Axon5 on 2009-08-20
> **K.Y.A said:**
> We all have secrets :)


Don't exploit them, and you'll have less enemies... :)

PM me some more IP addresses, I'll forkbomb them, then I'll be like him :)

EDIT: Kidding.

---

### Post by K.Y.A on 2009-08-20
> **Axon5 said:**
> PM me some more IP addresses, I'll forkbomb them, then I'll be like him :)

You do realize you just admitted you where avahi?

Oh well...:popcorn:

---

### Post by dragos240 on 2009-08-20
We'll have a mod compare your IP address history. Just to be safe.

---

### Post by Axon5 on 2009-08-20
> **dragos240 said:**
> We'll have a mod compare your IP address history. Just to be safe.

Surething.

---

### Post by Bachstelze on 2009-08-20
> **dragos240 said:**
> We'll have a mod compare your IP address history. Just to be safe.

Not the same.

---

### Post by K.Y.A on 2009-08-20
For future reference, if bobyo134, or anyone of that matter posts my ip address they will be banned. 

Courtesy of UF staff.

---

### Post by K.Y.A on 2009-08-20
> **HymnToLife said:**
> Not the same.

PROXY! w00t. :lolflag:

---

### Post by Bachstelze on 2009-08-20
> **K.Y.A said:**
> PROXY! w00t. :lolflag:

Er, actually, never mind. I didn't look deep enough.

---

### Post by dragos240 on 2009-08-20
> **HymnToLife said:**
> Not the same.

Thanks. He's safe then.

Or using a proxy. Ban evasion!

---

### Post by K.Y.A on 2009-08-20
> **HymnToLife said:**
> Er, actually, never mind. I didn't look deep enough.

I'm eager to know. What did you find?

I've been here for a while, so don't suspect me just for being interested. :P

---

### Post by dragos240 on 2009-08-20
> **K.Y.A said:**
> I'm eager to know. What did you find?

I've been here for a while, so don't suspect me just for being interested. :P

I don't think you are.

---

### Post by Bachstelze on 2009-08-20
> **K.Y.A said:**
> I'm eager to know. What did you find?

I've been here for a while, so don't suspect me just for being interested. :P

That avahi and Axon5 were two reincarnations of an ancient troll that hails from a place called linsux.org.

---

### Post by K.Y.A on 2009-08-20
> **bobyo134 said:**
> k.y.a. ip address is 24.3.74.20 port 22 , i did not post this lol

Lame. Not my IP. Execute the ip in firefox, it takes you to some odd site...

---

### Post by K.Y.A on 2009-08-20
> **hymntolife said:**
> that avahi and axon5 were two reincarnations of an ancient troll that hails from a place called linsux.org.

[size=4]evil![/size]

---

### Post by K.Y.A on 2009-08-20
> **dragos240 said:**
> I don't think you are.

I think ReactOS does. 

(lol)

---

### Post by Bachstelze on 2009-08-20
> **K.Y.A said:**
> Lame. Not my IP. Execute the ip in firefox, it takes you to some odd site...

So? The fact that the website is odd doesn't mean you can't be the one hosting it. :D

---

### Post by bobyo134 on 2009-08-20
no thats just his old old site , belive me i live right next to him lol

---

### Post by K.Y.A on 2009-08-20
> **hymntolife said:**
> so? The fact that the website is odd doesn't mean you can't be the one hosting it. :d

lol....

---

### Post by dragos240 on 2009-08-20
> **HymnToLife said:**
> That avahi and Axon5 were two reincarnations of an ancient troll that hails from a place called linsux.org.

I knew it!

---

### Post by K.Y.A on 2009-08-20
> **HymnToLife said:**
> So? The fact that the website is odd doesn't mean you can't be the one hosting it. :D

Goto the IP now. Physical proof it is not mine.

---

### Post by dragos240 on 2009-08-20
> **K.Y.A said:**
> Goto the IP now. Physical proof it is not mine.

Lulz.

---

### Post by Giant Speck on 2009-08-20
> **HymnToLife said:**
> That avahi and Axon5 were two reincarnations of an ancient troll that hails from a place called linsux.org.

I'm very curious to know who that actually is.  Linsux does not condone trolling.

---

### Post by K.Y.A on 2009-08-20
> **dragos240 said:**
> Lulz.

Check the site now...
Some mysterious person updated it to make fun of bobyo!

I traced the IP to nigeria!

[http://www.winrid.co.nr/](http://www.winrid.co.nr/)

More proof. Because, as you can see to the left, my location is "Behind my stapler".

---

### Post by Bachstelze on 2009-08-20
> **Giant Speck said:**
> I'm very curious to know who that actually is.  Linsux does not condone trolling.

His last incarnation was Captain Awesome 995. My knowledge does not go further, though, I only followed the whole Linsux thing distantly.

---

### Post by dragos240 on 2009-08-20
> **K.Y.A said:**
> Check the site now...
Some mysterious person updated it to make fun of bobyo!

I traced the IP to nigeria!

[http://www.winrid.co.nr/](http://www.winrid.co.nr/)

More proof. Because, as you can see to the left, my location is "Behind my stapler".

>.<

---

### Post by Bachstelze on 2009-08-20
> **K.Y.A said:**
> 
I traced the IP to nigeria!

[http://www.winrid.co.nr/](http://www.winrid.co.nr/)

Haha, yeah.

```
firas@itsuki ~ % geoiplookup 24.3.74.20
GeoIP Country Edition: US, United States

```

You cannot hide!

---

### Post by K.Y.A on 2009-08-20
> **hymntolife said:**
> haha, yeah.

```
firas@itsuki ~ % geoiplookup 24.3.74.20
geoip country edition: Us, united states

```you cannot hide!


lies!

---

### Post by chris200x9 on 2009-08-20
is it up again? I get ```
 ssh: connect to host 24.34.53.70 port 22: Network is unreachable

```

---

### Post by schauerlich on 2009-08-20
> **HymnToLife said:**
> His last incarnation was Captain Awesome 995. My knowledge does not go further, though, I only followed the whole Linsux thing distantly.

Linsux does not condone messing with people's computers. I've PM'd the admin with links following this in case he finds it necessary to take action.

---

### Post by dragos240 on 2009-08-20
> **K.Y.A said:**
> lies!

I tried it too:

~$ geoiplookup 24.3.74.20
GeoIP Country Edition: US, United States

---

### Post by Giant Speck on 2009-08-20
> **HymnToLife said:**
> His last incarnation was Captain Awesome 995. My knowledge does not go further, though, I only followed the whole Linsux thing distantly.

Wow.  I'll let the moderators at Linsux know.

EDIT:  Eric beat me to it.

---

### Post by K.Y.A on 2009-08-20
> **dragos240 said:**
> I tried it too:

~$ geoiplookup 24.3.74.20
GeoIP Country Edition: US, United States

Oh, well the app I used is a bit buggy:

~$nigerianiptracert 24.3.74.20
Nigeria Country Edition: NG, Nigeria.

---

### Post by JillSwift on 2009-08-20
> **dragos240 said:**
> I tried it too:

~$ geoiplookup 24.3.74.20
GeoIP Country Edition: US, United States

Me too!

```
me@my_computer$geoiplookup 24.3.74.20
For the fifth time, dammit! You don't have geoiplookup installed!
Install it or just stop annoying me!
```

---

### Post by K.Y.A on 2009-08-20
Let's get back on topic...

**servers!!!**

---

### Post by Bachstelze on 2009-08-20
> **K.Y.A said:**
> Let's get back on topic...

**servers!!!**

My servers are alive and well, thank you.

```
firas@itsuki ~ % uname -a
FreeBSD itsuki.fkraiem.org 7.2-RELEASE-p2 FreeBSD 7.2-RELEASE-p2 #0: Thu Jun 25 21:36:31 CEST 2009     root@itsuki.fkraiem.org:/usr/obj/usr/src/sys/ITSUKI  amd64
firas@itsuki ~ % uptime
 3:24am  up 9 days, 13:55, 6 users, load averages: 0.23, 0.17, 0.07

```

```
firas@iori ~ % uname -a
Linux iori.fkraiem.org 2.6.30-1-amd64 #1 SMP Sat Aug 15 18:09:19 UTC 2009 x86_64 GNU/Linux
firas@iori ~ % uptime
 03:24:55 up 5 days,  1:26,  7 users,  load average: 4.82, 3.53, 3.06

```

Whoever manages to guess my IPs wons an internets.*

[SIZE="1"]* While supplies last[/SIZE]

---

### Post by K.Y.A on 2009-08-20
Just to get even with bobyo134, his ip is:
[SIZE=3]72.77.64.75

[SIZE=2]And, his site is [www.moonshelpsite.co.nr](www.moonshelpsite.co.nr)[/SIZE]
[/SIZE]

---

### Post by Frak on 2009-08-20
> **Giant Speck said:**
> I'm very curious to know who that actually is.  Linsux does not condone trolling.
Aye. They only support logical rebuttles, not poser "OMG UR A NOOB" trolling.

/offtopic

I just recently got my CF server up and going. I eventually ended back up on Ubu-Serv running two virtual hosts (one stock ColdFusion, other Railo). Been using it to run load tests, mostly. Railo seems to be smoking the stock ColdFusion installation on my hardware. Quad-Core Opteron 2.4GHz w/ 12GB of FB-DIMM w/ repo-Java in case anybody is wondering.

---

### Post by dragos240 on 2009-08-20
/me wants to learn how to get an ip address :D

---

### Post by Bachstelze on 2009-08-20
> **dragos240 said:**
> /me wants to learn how to get an ip address :D

```
firas@itsuki ~ % host itsuki.fkraiem.org
itsuki.fkraiem.org has address 91.121.117.123
itsuki.fkraiem.org has IPv6 address 2001:41d0:1:ac7b::1
itsuki.fkraiem.org mail is handled by 10 itsuki.fkraiem.org.

```

Like this?

---

### Post by bobyo134 on 2009-08-20
just to tell u thats not my ip that my servers run on , or i even use , next thats my old website , my new one is not up yet

---

### Post by dragos240 on 2009-08-20
> **HymnToLife said:**
> ```
firas@itsuki ~ % host itsuki.fkraiem.org
itsuki.fkraiem.org has address 91.121.117.123
itsuki.fkraiem.org has IPv6 address 2001:41d0:1:ac7b::1
itsuki.fkraiem.org mail is handled by 10 itsuki.fkraiem.org.

```Like this?

Nah. On an internet forum :)

---

### Post by Bachstelze on 2009-08-20
> **dragos240 said:**
> Nah. On an internet forum :)

Become staff. :p

---

### Post by Frak on 2009-08-20
> **dragos240 said:**
> Nah. On an internet forum :)
It's a forum feature for nominated users.

---

### Post by dragos240 on 2009-08-20
Well yeah.......

---

### Post by dragos240 on 2009-08-20
> **Amberjhons said:**
> Just enjoy yourself.:)
Hello! Whats up? You are 4 days old, you are safe!

---

### Post by PurposeOfReason on 2009-08-20
I'd change the default port for ssh of you're going to get a lot of bots trying to get in.

---

### Post by Tamalin on 2009-08-20
I visited [www.winrid.co.nr](www.winrid.co.nr).

All I have to say is, "What the heck?  Who spent their time doing *this*?"

---

### Post by bobyo134 on 2009-08-20
that would de devon aka k.y.a. or linuxisevolution , it was a site he made when he was 13 has was just learing html , his new site is [www.directoryadmin.info](www.directoryadmin.info) and [www.thelinuxhowto.co.nr](www.thelinuxhowto.co.nr)

---

### Post by Tamalin on 2009-08-20
> **bobyo134 said:**
> that would de devon aka k.y.a. or linuxisevolution , it was a site he made when he was 13 has was just learing html , his new site is [www.directoryadmin.info](www.directoryadmin.info) and [www.thelinuxhowto.co.nr](www.thelinuxhowto.co.nr)

Yeah, well he posted this on his site...

> I am banned on my main account linuxisevolution.


But while thats banned I use EnglishSparrow -just don't tell anyone *;)* 

Not so secret anymore.

---

### Post by Giant Speck on 2009-08-20
> **Tamalin said:**
> Not so secret anymore.

:facepalm:

What an idiot.

---

### Post by Tamalin on 2009-08-20
Sad.  Well, such is the fate of such dissenters.

---

### Post by hanzomon4 on 2009-08-21
Ummm I get No route to host

Am I doing it wrong ```
ssh -p 22 -l ubuntuforums 24.34.53.70
```

---

### Post by avahi returns on 2009-08-21
The only reason avahi was banned is because he was a Linux member.
Good job, you've sunk to Kiwi's level.

---

### Post by schauerlich on 2009-08-21
> **avahi returns said:**
> The only reason avahi was banned is because he was a Linux member.
Good job, you've sunk to Kiwi's level.

No, it was because you forkbombed someone and bragged about it.

---

### Post by CJ Master on 2009-08-21
Very fun topic to read. :D Except his beans don't appear to be burnt...

> **Giant Speck said:**
> I'm very curious to know who that actually is.  Linsux does not condone trolling.

LOL. Are we talking about the same Linsux I visited a couple months ago? Because there was no other way to classify that site except for troll site. Of course, I don't mind, often times I classify Ubuntu forums as a Windows troll site as well. ;)

---

### Post by schauerlich on 2009-08-21
> **CJ Master said:**
> LOL. Are we talking about the same Linsux I visited a couple months ago? Because there was no other way to classify that site except for troll site.

Linsux a few months ago != current linsux. They've been actively trying to clean up the content and discourage stirring up trouble.

---

### Post by CJ Master on 2009-08-21
> **EDavidBurg said:**
> Linsux a few months ago != current linsux. They've been actively trying to clean up the content and discourage stirring up trouble.

I looked over it again. It looks like Linsux with 25% less troll. It's an improvement. :)

---

### Post by schauerlich on 2009-08-21
> **CJ Master said:**
> I looked over it again. It looks like Linsux with 25% less troll. It's an improvement. :)

It's not trolling if everyone is doing it. Then it's just a different kind of community. It's only trolling when it spills over to other sites. See 4chan as a great example. It's said that trolling 4chan is "like pissing in an ocean of piss."

---

### Post by ViperChief on 2009-08-21
> **CJ Master said:**
> I looked over it again. It looks like Linsux with 25% less troll. It's an improvement. :)

You should see it with 100% less troll. I'm the new chief admin. I do not, in any way, advocate trolling. Any trolling by members of the site is on them, not on the site. Look around over there. There's nowhere that the staff advocates causing problems on any site.

EDIT: Personally, I see trolling as extremely childish. I prefer mature dialogue and think that we can get our point across in a much better way.

---

### Post by t0p on 2009-08-21
> **hanzomon4 said:**
> Ummm I get No route to host

Am I doing it wrong ```
ssh -p 22 -l ubuntuforums 24.34.53.70
```

The server is down because avahi forkbombed it.  Do try and pay attention! :p

---

### Post by dragos240 on 2009-08-21
Hi everyone! The SSH server is now back up, and users are limited to running 30 applications, to prevent a fork bomb. Enjoy! Nano AND vim are installed. 'vi' is vim, vim is not working. Please enjoy.

---

### Post by pwnst*r on 2009-08-21
> **dragos240 said:**
> 24.34.53.70
port 22
user: ubuntuforums
pass: ubuntu

this bears repeating.

---

### Post by dragos240 on 2009-08-21
> **pwnst*r said:**
> this bears repeating.

I don't understand..... Does the server not work?:confused:

---

### Post by plurt on 2009-08-21
It works, should it be tested for security? :)

---

### Post by dragos240 on 2009-08-21
I got that handled. It's secure, I need one more thing. But it's okay, i'm leaving it up for fun :p

---

### Post by plurt on 2009-08-21
seems down again though

---

### Post by Joeb454 on 2009-08-21
> **MaxIBoy said:**
> Current uptime of my server is 36 days. If it wasn't for a series of power outages we had, it would have been 101 days. But the all-time record on that particular box was 130 days.

Mine was around 136 days, then I decided that I should probably apply the kernel updates I'd been getting ;)

---

### Post by dragos240 on 2009-08-21
> **plurt said:**
> seems down again though


Really? I can login just fine? Hold on, I'm going to see if it's down to everyone else.

---

### Post by Kingsley on 2009-08-21
lol I'm going to class. That was fun, guys.

---

### Post by dragos240 on 2009-08-21
Nope, seems to be up, and ports 80, 21, and 22 are open.

---

### Post by CJ Master on 2009-08-21
> **ViperChief said:**
> You should see it with 100% less troll. I'm the new chief admin. I do not, in any way, advocate trolling. Any trolling by members of the site is on them, not on the site. Look around over there. There's nowhere that the staff advocates causing problems on any site.

EDIT: Personally, I see trolling as extremely childish. I prefer mature dialogue and think that we can get our point across in a much better way.

The site is named Linsux for goodness sakes. It's hard to get a mature community around that.

But still, I'm glad that it's maturing. Some of the stuff over there two months ago was... you know.

"It's not trolling if everyone is doing it. Then it's just a different kind of community. It's only trolling when it spills over to other sites. See 4chan as a great example. It's said that trolling 4chan is 'like pissing in an ocean of piss.'"

Can't argue with that. :P

Anyway, don't want to divert the topic more then it is.

---

### Post by Yes on 2009-08-21
> **dragos240 said:**
> Nope, seems to be up, and ports 80, 21, and 22 are open.

You sure?  I can't connect at all.

---

### Post by dragos240 on 2009-08-21
Now you can't, see, I am having permission problems, and I can't even login, it's reinstall time.

---

### Post by MaxIBoy on 2009-08-21
Ah, come on, reinstalling is cheating.

---

### Post by mr-woof on 2009-08-21
sounds like someone has taken it over, if you can't login anymore

---

### Post by hessiess on 2009-08-21
> **dragos240 said:**
> Now you can't, see, I am having permission problems, and I can't even login, it's reinstall time.

you should have imaged the drive before experimenting with it;)

---

### Post by Nepherte on 2009-08-21
> **dragos240 said:**
> Now you can't, see, I am having permission problems, and I can't even login, it's reinstall time.
That's where live cds come in handy.

---

### Post by dragos240 on 2009-08-21
> **mr-woof said:**
> sounds like someone has taken it over, if you can't login anymore

Nope, it was me messing up my system. 100% me.

---

### Post by schauerlich on 2009-08-21
> **dragos240 said:**
> Nope, it was me messing up my system. 100% me.

Except for the forkbomb.

---

### Post by dragos240 on 2009-08-21
> **Nepherte said:**
> That's where live cds come in handy.

That's where live flash drives come in handy. Netbook server :p

---

### Post by dragos240 on 2009-08-21
> **EDavidBurg said:**
> Except for the forkbomb.


Well yes, that wasn't me, but it wasn't the thing that messed up my system.

---

### Post by Giant Speck on 2009-08-21
> **CJ Master said:**
> The site is named Linsux for goodness sakes. It's hard to get a mature community around that.

But still, I'm glad that it's maturing. Some of the stuff over there two months ago was... you know.

"It's not trolling if everyone is doing it. Then it's just a different kind of community. It's only trolling when it spills over to other sites. See 4chan as a great example. It's said that trolling 4chan is 'like pissing in an ocean of piss.'"

Can't argue with that. :P

Anyway, don't want to divert the topic more then it is.

The main core of the Linsux userbase (ViperChief, timestandstill, Sir Sane, EDavidburg, myself, and others)* is made up of former or current Linux users.  We have not and will not ever troll another website.  We can beyotch and moan sometimes about how we may lament certain online communities, but that behavior is generally confined to within our own website.  Linsux has its own rules, but it does not condone violating the rules of other online communities. That would be immature and a waste of our time.

It's the people who join Linsux thinking that trolling is what Linsux is all about who are causing the problems, and that is extremely evident in this very thread.

[SIZE=1] *If I did not mention your name, I apologize.  I've been very busy today.[/SIZE]

---

### Post by schauerlich on 2009-08-21
> **Giant Speck said:**
> It's the people who join Linsux thinking that trolling is what Linsux is all about who are causing the problems, and that is extremely evident in this very thread.

+1

Back on topic: Is there an ETA for the server being back up?

---

### Post by dragos240 on 2009-08-21
> **EDavidBurg said:**
> +1

Back on topic: Is there an ETA for the server being back up?

Perhaps a few days..... maybe about 9:00 EST Tuesday? Although I'm not sure. I am doing a reinstall of arch, so it may take a while, I have compiled a list of applications, that I use daily, and ones needed for the server, I will backup my current files, which I can do, and I can do a reinstall. Although, I probably will get it up and running sooner than the ETA. But in the time being:

No server for you!

---

### Post by Tamalin on 2009-08-21
> **avahi returns said:**
> The only reason avahi was banned is because he was a Linux member.
Good job, you've sunk to Kiwi's level.

Welcome back avahi, but no more forkbombing.  And may I ask, what is Kiwi?

---

### Post by dragos240 on 2009-08-21
Lol I dunno? KiwiNZ?

---

### Post by -grubby on 2009-08-21
> **Giant Speck said:**
> 
[SIZE=1] *If I did not mention your name, I apologize.  I've been very busy today.[/SIZE]

/me is offended

---

### Post by Frak on 2009-08-21
> **Joeb454 said:**
> Mine was around 136 days, then I decided that I should probably apply the kernel updates I'd been getting ;)
[http://www.ksplice.com/](http://www.ksplice.com/)

---

### Post by dragos240 on 2009-08-21
> **Frak said:**
> [http://www.ksplice.com/](http://www.ksplice.com/)

OMGBBQLOLLMAOROFL that's awesome!

---

### Post by Frak on 2009-08-21
We use that where I work. I'm paid by contract, but some other techs there are only paid as long as the server stays on-line. While updates that actually change the kernel (as in change the way it handles data, such as a full-blown kernel upgrade, such as 2.4 to 2.6) aren't supported, minor and major security updates are supported, which make up 85% - 90% of the updates we receive anyways.

Oh, and we run Red Hat and Ubuntu on our web and application servers. We run Windows Server 2008 on our client network (it also operates as a bridge).

---

