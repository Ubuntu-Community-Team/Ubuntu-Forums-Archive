---
title: "Pidgin 2.5.5 Released!"
date: 2009-03-02
forum: The Cafe
---

### Post by Kosimo on 2009-03-02
Guys, Pidgin Folks has just released a new version!
2.5.5

Here the changelog> 
```
   libpurple:
   * Fix a crash when removing an account with an unknown protocol id.
   * Beta support for SSL connections for AIM and ICQ accounts.  To
     enable, check the "Use SSL" option from the Advanced tab when
     editing your AIM or ICQ account. (Paul Aurich)
   * Fix a memory leak in SILC. (Luke Petre)
   * Fix some string handling in the SIMPLE prpl, which fixes some buddy name
     handling and other issues. (Paul Aurich, Marcus Sundberg)
   * Implement support for resolving DNS via the SOCKS4 proxy (SOCKS4a).
 .
   ICQ:
   * Fix retrieval of status messages from users of ICQ 6.x, Miranda, and
     other libpurple clients. (Daniel Ljungborg)
   * Change client ID to match ICQ Basic 14.34.3096.  This fixes publishing
     of buddy icons and available messages.
   * Properly publish status messages for statuses other than Available.
     ICQ 6.x users can now see these status messages. (Daniel Ljungborg)
   * Fix receipt of messages from the mobile client Slick. (David Jedelsky)
 .
   MSN:
   * Fix transfer of buddy icons, custom smileys, and files from the
     latest Windows Live Messenger 9 official client. (Thomas
     Gibson-Robinson)
   * Large (multi-part) messages are now correctly re-combined.
   * Federated/Yahoo! buddies should now stop creating sync issues at
     every signin.  You may need to remove duplicates in the Address
     Book.  See the FAQ for more information.  Thanks to Jason Lingohr
     for lots of debugging and testing.
   * Messages from Yahoo! buddies are no longer silently dropped.
   * We now save and use the CacheKey for ABCH SOAP requests.
   * Don't try to parse Personal Status Messages or Current Media if they
     don't exist.
   * Convert from ISO-8859-1 encoding to UTF-8 when no charset is specified
     on incoming messages.  This should fix some issues with messages from
     older clients.
   * Force sending the font "Segoe UI" if outgoing formatting doesn't specify
     a font already.
   * Queue callbacks when token updates are in progress to prevent two token
     update attempts from trampling each other.
   * Fixed a crash on Windows when removing a buddy's alias.
   * Update the Address Book when buddies' friendly names change.  This
     prevents seeing an outdated alias or not seeing an alias at all for
     buddies who are offline when you sign in.
   * Update tokens for FindMembership and ABFindAll SOAP requests.
   * We no longer try to send empty messages.  This could happen when a
     message contained only formatting and that formatting was not supported
     on MSN.
   * Buddies on both the Allow and Block list are now automatically
     removed from the Allow list.  Users with this problem will now no
     longer receive an ADL 241 error.  The problematic buddy should now
     appear on the buddy list and can be removed or unblocked as desired.
 .
   XMPP:
   * Resources using __HOSTNAME__ substitution will now grab only the short
     hostname instead of the FQDN on systems which put the FQDN in the
     hostname. (Mat&#283;j Cepl)
   * No longer send a 'to' attribute on an outgoing stanza when we haven't
     received one.  This fixes a registration bug as described in ticket
     #6635.
 .
   Pidgin:
   * Tooltip windows now appear below the mouse cursor. (Kosta Arvanitis)
   * Tooltip windows now disappear on keypress events. (Kosta Arvanitis)
   * Tooltip windows no longer linger when scrolling the buddy list. (Kosta
     Arvanitis)
 .
   Finch:
   * Allow rebinding keys to change the focused widget (details in the
     man-page, look for GntBox::binding)

```

Note the amount of fixes on MSN network!

Get an easy deb from getdeb.net 
[http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin)

Or download the source code from pidgin.im

---

### Post by kahlil88 on 2009-03-02
It's about freaking time! But the actual Pidgin site still says the latest version is 2.5.4 and the 2.5.5 roadmap isn't complete...

---

### Post by Depressed Man on 2009-03-02
The official Pidgin website is ..

[www.pidgin.im](www.pidgin.im)

not pidgin.net

---

### Post by Kosimo on 2009-03-02
> **Depressed Man said:**
> The official Pidgin website is ..

[www.pidgin.im](www.pidgin.im)

not pidgin.net

My mistake, Thanks for the heads up!

---

### Post by Polygon on 2009-03-03
for some reason getdeb has an extra package this time around (libpurple-bin)

but whatever, nothing a dpkg -i *.deb can't fix =)

---

### Post by Rokurosv on 2009-03-03
I guess it still doesn't support webcams, too bad. I think Pidgin is an excelent IM client, my bro is using it on his XP cause he hated how bloated the new Live Messenger was.

---

### Post by YoungQuiz on 2009-03-03
is there a .deb for this?

im not to good with manual installs, although i could do it with some good instructions

---

### Post by kevin11951 on 2009-03-03
> **YoungQuiz said:**
> is there a .deb for this?

im not to good with manual installs, although i could do it with some good instructions

the getdeb link, links to a pack of debs.

---

### Post by Kosimo on 2009-03-03
Strange....
Pidgin's webpage still doesn't says anything about 2.5.5... Where did this guys from getdeb get the source code?

---

### Post by Johnsie on 2009-03-03
Still no multimedia??? Seriously, using Pidgin is like going back to the 90's!

---

### Post by cb951303 on 2009-03-03
> **Johnsie said:**
> Still no multimedia??? Seriously, using Pidgin is like going back to the 90's!

I doubt there were any multi-protocol chat clients back then :P

seriously though, modernity of an IM client is not related to video/audio chat capability.

---

### Post by Johnsie on 2009-03-03
Trillian may not have been 1990's but it was released in 2000 and IMO is much better than gaim/pidgin.

---

### Post by cb951303 on 2009-03-03
> **Johnsie said:**
> Trillian may not have been 1990's but it was released in 2000 and IMO is much better than gaim/pidgin.

not open source, not multi-platform. so far so bad :) And the one time I tried it on windows, it was a resource hog.

---

### Post by andrewabc on 2009-03-03
> **Johnsie said:**
> Trillian may not have been 1990's but it was released in 2000 and IMO is much better than gaim/pidgin.

If you are on Windows, Miranda IM is better than trillian. Opensource, most protocols supported, and thousands of plugins to make the IM do exactly what you want.

I'm guessing this new version of pigdin still does not fix msn HTTP connecting through port 80. It never has worked. Other ubuntu IM do work, but they are terribly designed and crash often.

---

### Post by ArtF10 on 2009-03-03
> **Johnsie said:**
> ....using Pidgin is like going back to the 90's!

which wasn't such a long time ago.

---

### Post by kimda on 2009-03-03
I see they havent fixed the file sharing problem yet. I wish I could run Pidgin but when I send files its like dialup speeds at only 6kb/sec or something like that. Now I run aMSN instead which is in my opinion ugly as hell but at least I can send files at a decent speed.

---

### Post by Kosimo on 2009-03-03
> **kimda said:**
> I see they havent fixed the file sharing problem yet. I wish I could run Pidgin but when I send files its like dialup speeds at only 6kb/sec or something like that. Now I run aMSN instead which is in my opinion ugly as hell but at least I can send files at a decent speed.

Totally agree...
Pidgin uses HTTP connections when sending files, instead of the current P2P connections used in Windows Live messengers or other programs... They are working on implement this since forever... Someday we'll have it..

aMSN is extremely ugly...

---

### Post by racoq on 2009-03-03
> **Kosimo said:**
> Totally agree...
aMSN is extremely ugly...

But still... is the most featured, live messenger client on Linux.

(i'm not counting Mercury IM, since is a far worst memory hog, than Windows Live Messenger itself)

---

### Post by Kosimo on 2009-03-03
> **racoq said:**
> But still... is the most featured, live messenger client on Linux.

(i'm not counting Mercury IM, since is a far worst memory hog, than Windows Live Messenger itself)

Totally.

---

### Post by hatten on 2009-03-03
is it possible to get it with a "simple" command in the terminal?

---

### Post by Kosimo on 2009-03-03
> **hatten said:**
> is it possible to get it with a "simple" command in the terminal?

What you mean? You want to download it using terminal? Actually you can by using *wget*, but is not gonna be a "simple" command as you have to download more than one .deb because at the moment, pidgin's official webpage doesn't offer the source code for 2.5.5, in fact it doesn't say anything about 2.5.5 at all yet.

---

### Post by Muffinabus on 2009-03-03
Installing the .deb's isn't too difficult anyways.

I like the new version though, mostly for the fixed tooltip while scrolling the buddy list, ha.  That really annoyed me.

---

### Post by Polygon on 2009-03-03
> **Johnsie said:**
> Trillian may not have been 1990's but it was released in 2000 and IMO is much better than gaim/pidgin.

last time i used trillian, its user interface was horrid. HORRID.

---

### Post by kevdog on 2009-03-04
For those wanting to compile from source here are some instructions:
[http://ubuntuforums.org/showthread.php?t=975783](http://ubuntuforums.org/showthread.php?t=975783)
I haven't updated for 2.5.5, however I think the average user can figure out the 2.5.5 should be used when 2.5.4 is mentioned!

---

### Post by heartwarmer on 2009-03-06
For me 2.5.5 is no different than 2.5.4, i still cant see icons for buddies
who uses wlm9, and colored nicknames is not colored.

the only thing that changed for me is the fewer crashes :)

---

### Post by Polygon on 2009-03-06
> **heartwarmer said:**
> For me 2.5.5 is no different than 2.5.4, i still cant see icons for buddies
who uses wlm9, and colored nicknames is not colored.

the only thing that changed for me is the fewer crashes :)

pidgin says that they will never EVER support the bbcode style formatting in nicknames. They said they are going to eventually just have pidgin strip the formatting codes so you dont have buddies that are like **NameHere!**

and icons for buddies works for me....

---

### Post by heartwarmer on 2009-03-06
why wont they? can you give me the link to where they said so?

---

### Post by Polygon on 2009-03-06
[http://developer.pidgin.im/ticket/4598](http://developer.pidgin.im/ticket/4598) <== ongoing ticket to remove the formatting from the name

> 
This is not technically part of the MSN protocol. It is part of Messenger Plus!, which hacks on various things like coloured nicks, skins, funky logs, and who knows what else. 


i cant find the original ticket that said they will not implement the msnplus formatting tags into pidgin, if anything there will be a plugin to remove it.

---

### Post by andrewabc on 2009-03-06
> **heartwarmer said:**
> why wont they? can you give me the link to where they said so?

It is not official MSN server stuff, so no reason to implement such a terrible idea. If you want msnplus stuff, then you can use official msn with msnplus. some people actually like having a clean easy to look at interface and don't want the contact list to look like myspace.

---

### Post by Absolom on 2009-03-10
I installed the new 2.5.5 version of pidgin from getdeb and when I turn it on it loads but as soon as msn loads it closes down... if I disable msn my other IMs load no prob then soon as I enable msn it closes down on me...

I prefer using pidgin but untill it lets me use msn I have to rely on kopete

---

### Post by Johnsie on 2009-03-10
Trillian is completely skinnable and supports audio/video as well as alot more plugins.

---

### Post by bash on 2009-03-10
> **Johnsie said:**
> Trillian is completely skinnable ....

For me it is actually a huge plus that Pidgin uses the native look in a GTK+ enviroment and tries to emulate the native look pretty closely in Windows. If you like Skins then that options in Trillian might be nice, but back when I used Trillian 3.x it was impossible to just give it a native Windows look.

> **Johnsie said:**
> ... and supports audio/video ...

True - but at least in the 3.x series it was only voice/video between different Trillian clients and not for example between Trillian and a user of the official MSN messenger. And work is being done concerning voice and video in pidgin: [http://developer.pidgin.im/milestone/Voice%20and%20Video%20Support](http://developer.pidgin.im/milestone/Voice%20and%20Video%20Support)

> **Johnsie said:**
> ... as well as alot more plugins.

I'm curious about this. Can you tell me which plugins (with I assuming you mean protocols) Trillian supports that Pidgin doesn't? I just remember from back in the whole fight to even just get basic Jabber support in the free version of Trillian.

---

### Post by heartwarmer on 2009-03-10
> **Johnsie said:**
> Trillian is completely skinnable and supports audio/video as well as alot more plugins.

I thought trillian didnt have a Linux version, where can i find it?

---

### Post by Thelasko on 2009-03-10
> **ArtF10 said:**
> which wasn't such a long time ago.

It's 2009, it was almost decade ago!  Time really slips by, doesn't it?

After 2010, what will we call the 200Xs?  The noughts, naughts, aughts, oughts, zeros, hundreds... ones?

P.S. [Wikipedia article on the topic.]("http://en.wikipedia.org/wiki/2000%E2%80%932009#Names_of_the_decade")  [1900-1909 was called "The aughts"]("http://en.wikipedia.org/wiki/1900-1909")

---

### Post by screaminj3sus on 2009-03-10
> **bash said:**
> For me it is actually a huge plus that Pidgin uses the native look in a GTK+ enviroment and tries to emulate the native look pretty closely in Windows. If you like Skins then that options in Trillian might be nice, but back when I used Trillian 3.x it was impossible to just give it a native Windows look.



True - but at least in the 3.x series it was only voice/video between different Trillian clients and not for example between Trillian and a user of the official MSN messenger. And work is being done concerning voice and video in pidgin: [http://developer.pidgin.im/milestone/Voice%20and%20Video%20Support](http://developer.pidgin.im/milestone/Voice%20and%20Video%20Support)



I'm curious about this. Can you tell me which plugins (with I assuming you mean protocols) Trillian supports that Pidgin doesn't? I just remember from back in the whole fight to even just get basic Jabber support in the free version of Trillian.

I agree, I'd MUCH rather have native apps so I don't have to freakin skin them to try qand make them look NATIVE. trillian is ugly as hell and the new trillian astra theme is one of the most hideous gaudy things I have ever seen.

And AFAIK there is no linux trillian version, but there is a mac version in the works I believe.

---

### Post by Polygon on 2009-03-10
and as i have already said, even the native windows UI is terrible, every thing is confusing, and it took me like 20 minutes just to figure out how to set up the program.

---

### Post by leandroamparo on 2009-03-13
Hello everybody,
yesterday i installed ubuntu 8.04 i386 on my new laptop (inspiron 1525) and pidgin only upgrades to version 2.5.2. i've tried upgrading to 2.5.5 using those getdeb packages, but i get some dependencies problems relating to packages that are already installed. can anyone help me here?
thanks

---

### Post by Kosimo on 2009-03-13
> **leandroamparo said:**
> Hello everybody,
yesterday i installed ubuntu 8.04 i386 on my new laptop (inspiron 1525) and pidgin only upgrades to version 2.5.2. i've tried upgrading to 2.5.5 using those getdeb packages, but i get some dependencies problems relating to packages that are already installed. can anyone help me here?
thanks

You're having this dependencies problems because you are trying to install "Intrepid Ibex" packages into "Hardy Heron"

Get the right packages for your distro [here: ]("http://www.getdeb.net/release/3962")

---

### Post by VitaLiNux on 2009-03-13
> **Johnsie said:**
> Still no multimedia??? Seriously, using Pidgin is like going back to the 90's!

Hello, 

I don't mean to be rude, but I just can't get why some people blame Open Source development for lacking of some features. They're not trying to reinvent the wheel, but, come on, have you ever heard of "PATENT INFRINGEMENT"? Maybe not, probably. Then I'd understand your "Still no multimedia??? Seriously, using Pidgin is like going back to the 90's!" point.:rolleyes:

---

### Post by gunbladeiv on 2009-03-14
> **VitaLiNux said:**
> Hello, 

I don't mean to be rude, but I just can't get why some people blame Open Source development for lacking of some features. They're not trying to reinvent the wheel, but, come on, have you ever heard of "PATENT INFRINGEMENT"? Maybe not, probably. Then I'd understand your "Still no multimedia??? Seriously, using Pidgin is like going back to the 90's!" point.:rolleyes:

At last, someone comes up with a good point. Try to read before you nag and blame peoples' hard work. Very good point there VitaLiNux

---

### Post by mparker81 on 2009-03-15
> **Kosimo said:**
> You're having this dependencies problems because you are trying to install "Intrepid Ibex" packages into "Hardy Heron"

Get the right packages for your distro [here: ]("http://www.getdeb.net/release/3962")


thanks, that fixed my problem too...   :)

---

### Post by Thelasko on 2009-03-16
> **VitaLiNux said:**
> Hello, 

I don't mean to be rude, but I just can't get why some people blame Open Source development for lacking of some features. They're not trying to reinvent the wheel, but, come on, have you ever heard of "PATENT INFRINGEMENT"? Maybe not, probably. Then I'd understand your "Still no multimedia??? Seriously, using Pidgin is like going back to the 90's!" point.:rolleyes:

Sorry, No

[Many]("http://en.wikipedia.org/wiki/Miranda_IM") [other]("http://en.wikipedia.org/wiki/IChat") [IM clients]("http://en.wikipedia.org/wiki/Kopete") provide these features and haven't been sued for patent infringement.  Patent infringement has nothing to do with it, it's just lazy developers.

---

### Post by Kosimo on 2009-03-16
> **Thelasko said:**
> Sorry, No

[Many]("http://en.wikipedia.org/wiki/Miranda_IM") [other]("http://en.wikipedia.org/wiki/IChat") [IM clients]("http://en.wikipedia.org/wiki/Kopete") provide these features and haven't been sued for patent infringement.  Patent infringement has nothing to do with it, it's just lazy developers.

Wow man... 

Sorry but I don't agree with you [-(
I think that if you're not happy with it, you're free to use something else, but: People who is developing an open source project that is available free of charge can't be called lazy at any time.

---

### Post by Polygon on 2009-03-16
dont call them lazy unless you go join the dev team and figure out how hard it is to reverse engineer something without infringing on any patents.

---

### Post by Thelasko on 2009-03-16
> **Polygon said:**
> dont call them lazy unless you go join the dev team and figure out how hard it is to reverse engineer something without infringing on any patents.

But they don't have to.  Kopete is open source and has already done the reverse engineering.  All the Pidgin developers need to do is [stop wasting time figuring out the best way to resize a window]("http://techreport.com/discussions.x/14659") and implement Kopete's code!

Sorry I'm not PC enough for everyone here, but Pidgin developers are just lazy.  That's all there is to it.

---

### Post by Polygon on 2009-03-16
kopete and pidgin are two different programs. Pidgin uses libpurple, so to implement anything they have to write a module for libpurple, they cant just ctrl+c ctrl+v the kopete code. I have no idea whats taking them so long, but calling them lazy is just immature on your part =) By that argument, the linux/gnome/kde/ whatever developers are lazy by wasting their time on feature X when they could be implementing feature Y

---

### Post by airtonix on 2009-03-16
> **ArtF10 said:**
> which wasn't such a long time ago.
Apparently yesterday was too long ago.

---

### Post by smbm on 2009-03-16
> **Thelasko said:**
> Sorry I'm not PC enough for everyone here, but Pidgin developers are just lazy.  That's all there is to it.

I'm not sure it's being not PC, I think it might just be impoliteness.

---

### Post by meho_r on 2009-03-16
> **Absolom said:**
> I installed the new 2.5.5 version of pidgin from getdeb and when I turn it on it loads but as soon as msn loads it closes down... if I disable msn my other IMs load no prob then soon as I enable msn it closes down on me...

I prefer using pidgin but untill it lets me use msn I have to rely on kopete

Just a thought, in case you're using Music Tracker plugin. I had same problems with Pidgin when Music Tracker is set on "Automatic" in "Player" section. If this is the case, chose one specific player or install msn-pecan, maybe it'll solve the problem.

BTW, msn-pecan seems to be better choice for msn protocol in Pidgin. Not tested with files transfer though.

---

### Post by Mr. Picklesworth on 2009-03-16
> **bash said:**
> For me it is actually a huge plus that Pidgin uses the native look in a GTK+ enviroment and tries to emulate the native look pretty closely in Windows. If you like Skins then that options in Trillian might be nice, but back when I used Trillian 3.x it was impossible to just give it a native Windows look.

Besides, GTK+ *is* skinnable.
Kudos for understanding the benefit of a native toolkit. It's not just about the look, either. Notice how you can roll the mouse wheel over a list of tabs to switch between tabs quickly; how you can expect drag & drop to always work with every text box out there; the way vertical and horizontal scrolling with the scroll wheel always works; and the way right click menus open when the mouse button goes *down* instead of when it goes up (just like any other menu)... that's all thanks to GTK :)
Without a native toolkit like that, the interface loses any chance of consistency, and with that goes usability and productivity. Which makes me sad.

I'll take good user interface over voice chat any day. (Case in point, aMSN). Although as soon as PyMSN supports voice and audio I'm back to Telepathy ;)

---

### Post by leandroamparo on 2009-03-16
> **Kosimo said:**
> You're having this dependencies problems because you are trying to install "Intrepid Ibex" packages into "Hardy Heron"

Get the right packages for your distro [here: ]("http://www.getdeb.net/release/3962")

thanks, but i did download those packages and they did work, but the pacackage manager kept complaining that i had dependencies problems with some packages and whenever i tried to fix it using the synaptic it would uninstall those pidgin packages. but anyway, i've upgraded to intrepid and installed those packages and they worked fine.
thanks for the help.

---

### Post by Absolom on 2009-03-21
> **meho_r said:**
> Just a thought, in case you're using Music Tracker plugin. I had same problems with Pidgin when Music Tracker is set on "Automatic" in "Player" section. If this is the case, chose one specific player or install msn-pecan, maybe it'll solve the problem.

BTW, msn-pecan seems to be better choice for msn protocol in Pidgin. Not tested with files transfer though.

thanks but I don't have music tracker at least I've never intentionally installed  it and I tried pecan already but results were the same ... pidgin worked fine untill I tried putting msn online soon as msn opened pidgin closed down

---

### Post by som24 on 2009-03-26
still waiting for the voice chat option

---

### Post by heartwarmer on 2009-03-27
> **som24 said:**
> still waiting for the voice chat option

its comming very soon,planned on April 1st -> [[COLOR="Red"]roadmap[/COLOR]](http://developer.pidgin.im/roadmap)

---

### Post by JackieChan on 2009-03-27
> **heartwarmer said:**
> its comming very soon,planned on April 1st -> [[COLOR="Red"]roadmap[/COLOR]](http://developer.pidgin.im/roadmap)
This isn't some cruel April Fools joke is it? :(

---

### Post by heartwarmer on 2009-03-27
> **JackieChan said:**
> This isn't some cruel April Fools joke is it? :(

hahahaha, i hope not,but even if they finish it in this date, i think they will
wait until 2.6 to launch it. at least thats what i think :)

---

### Post by enterman on 2009-04-07
Ok, for whatever reason no matter what Pidgin crashes for me in Ubuntu 8.10 whenever I try to talk to anyone in either Gtalk or MSN. It simply freezes and I have to force it to close. Anyone have any idea? It wasn't doing this until the last kernel update a month or 2 ago...

---

### Post by Kosimo on 2009-04-07
I would recommend you guys to stop installing debs and use the "now official" Pidgin PPA. Go to pidgin's wepbage and follow the instructions. Finally they remember us!

---

### Post by enterman on 2009-04-07
> **Kosimo said:**
> I would recommend you guys to stop installing debs and use the "now official" Pidgin PPA. Go to pidgin's wepbage and follow the instructions. Finally they remember us!
thats what I installed with and it still crashes ><

---

### Post by vitotol on 2009-04-09
hey guys, i followed the instructions from [http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/) to set up the ppa.

now i have problem with the update manager, i get this error
'E:Malformed line 1 in source list /etc/apt/sources.list.d/pidgin-ppa.list (dist parse), E:The list of sources could not be read.'

i guess i had to remove some spaces...:icon_frown:

how can i fix this???

EDIT:
ok, i fixed it, i removed the pidgin file from /etc/apt/sources.list.d

---

### Post by etnlIcarus on 2009-04-09
> **Kosimo said:**
> I would recommend you guys to stop installing debs and use the "now official" Pidgin PPA. Go to pidgin's wepbage and follow the instructions. Finally they remember us!

The PPA builds were buggy as hell for me. I went back to the old version in the ubuntu repos.

---

### Post by Kosimo on 2009-04-09
> **etnlIcarus said:**
> The PPA builds were buggy as hell for me. I went back to the old version in the ubuntu repos.

For me everything is working perfectly using their PPA

---

### Post by Eisenwinter on 2009-04-09
Pidgin 2.5.5 kept crashing all the time for me too.

Eventually I switched to Bitlbee, won't use Pidgin again :P

---

