---
title: "Saucy Authentication Problem"
date: 2013-05-01
forum: Ubuntu Development Version
---

### Post by kuvanito on 2013-05-01
I am testing Saucy and have a problem with Gdebi Authentication
There is a new Keyring Policy in effect with Saucy and it will not recognise my password
This is all too new for me and have never seen this new window
Here is a pic of it,read the white out options on the pic.

---

### Post by mc4man on 2013-05-01
That's the root auth window, no use to you. 
run 
```
gksu-properties
```
& change mode to sudo

---

### Post by kuvanito on 2013-05-01
thanks mc4man,all solved now.

---

### Post by mc4man on 2013-05-01
It's an issue that raring released with - 
gksu isn't default installed so when it is, (gdebi uses gksu), it installs with su mode which doesn't work out in Ubuntu
(Some 32 bit users report it installs with sudo, certainly not the case on 64 bit

---

### Post by kevpan815 on 2013-05-01
> **mc4man said:**
> It's an issue that raring released with - 
gksu isn't default installed so when it is, (gdebi uses gksu), it installs with su mode which doesn't work out in Ubuntu
(Some 32 bit users report it installs with sudo, certainly not the case on 64 bit

Mc4man, be advised that I am reporting each of your Posts that continue to mention Raring in this Ubuntu + 1 Sub-Forum. This Sub-Forum has now been Renamed Ubuntu + 1, the 13.10 Tool Chain is UP, and 13.10 Nightly Builds are Available (even if they are NOT working for everyone, including yours truly), check and see what Cariboo907 said regarding further discussion of 13.04 if you don't believe me, Just FYI.

---

### Post by QDR06VV9 on 2013-05-01
> **mc4man said:**
> That's the root auth window, no use to you. 
run 
```
gksu-properties
```
& change mode to sudo

+1 Thanks Bud!

---

### Post by kevpan815 on 2013-05-01
> **runrickus said:**
> +1 Thanks Bud!

As far as I am aware, that is a Raring Problem, NOT a Saucy Problem! For example: The tty1 Login Screen (Control + Alt + F1) is broken in 13.04. It works just fine in 13.10, however, as long as you use your Computer's Name as the User Name (in my case i use kevpan815) and NOT the actual name of the user himself or herself. Then you use Password of the User who set up the Computer, and tty1 works just fine.

---

### Post by cariboo on 2013-05-02
Problems that are carried over from the released version should be discussed here. We are still in the very early stages of development, and as such most of what we are using is still raring.

---

### Post by Elfy on 2013-05-02
> **kevpan815 said:**
> As far as I am aware, that is a Raring Problem, NOT a Saucy Problem! For example: The tty1 Login Screen (Control + Alt + F1) is broken in 13.04. It works just fine in 13.10, however, as long as you use your Computer's Name as the User Name (in my case i use kevpan815) and NOT the actual name of the user himself or herself. Then you use Password of the User who set up the Computer, and tty1 works just fine.

> **cariboo907 said:**
> Problems that are carried over from the released version should be discussed here. We are still in the very early stages of development, and as such most of what we are using is still raring.

The idea being that after smug smaug is released, rabid rabbits issues might well be relevant, same when terrible twosome replaces smug smaug and unbelievable unicorn replaces that ;)

The problem we had between rabid rabbit being released and the forum name changing was people NOT testing assuming it was a specific support forum.

---

### Post by kevpan815 on 2013-05-02
> **cariboo907 said:**
> Problems that are carried over from the released version should be discussed here. We are still in the very early stages of development, and as such most of what we are using is still raring.

Cariboo907, I was simply stating that I am able to Login to tty1 Command Line Screen in Saucy, however I am NOT able to log into tty1 Command Line Screen in Raring, so I was just saying that this is supposed to be fixed in Saucy.

---

### Post by Elfy on 2013-05-02
> **kevpan815 said:**
> Cariboo907, I was simply stating that I am able to Login to tty1 Command Line Screen in Saucy, however I am NOT able to log into tty1 Command Line Screen in Raring, so I was just saying that this is supposed to be fixed in Saucy.

> **kevpan815 said:**
> Mc4man, be advised that I am reporting each of your Posts that continue to mention Raring in this Ubuntu + 1 Sub-Forum. This Sub-Forum has now been Renamed Ubuntu + 1, the 13.10 Tool Chain is UP, and 13.10 Nightly Builds are Available (even if they are NOT working for everyone, including yours truly), check and see what Cariboo907 said regarding further discussion of 13.04 if you don't believe me, Just FYI.

We're replying to this - or I suspect so. I know I was.

---

### Post by kevpan815 on 2013-05-02
> **Elfy said:**
> The idea being that after smug smaug is released, rabid rabbits issues might well be relevant, same when terrible twosome replaces smug smaug and unbelievable unicorn replaces that ;)

The problem we had between rabid rabbit being released and the forum name changing was people NOT testing assuming it was a specific support forum.

This is exactly what I Predicted would happen if we left this Sub-Forum Open and then Re-named it to Ubuntu + 1. People would start replying to old posts about 13.04 that are weeks old, etc. It happens all the time in an Un-Moderated Microsoft google groups News Group that I sometimes pop into to harass all the People still running Windows Vista that post there.

---

### Post by kuvanito on 2013-05-02
dang it!
what did I just created here?
anyways,it is a problem in 13.10 and that is what I am running right now.I am a true tester of Ubuntu and if this is the case then rename this sub-forum Ubuntu-Saucy 13.10,hehehehehe :)
and in all cases THANK YOU mc4man for solving my PROBLEM,jejejejeje

---

### Post by rrnbtter on 2013-05-02
Greetings,
it may be Saucy but it isn't 13.10 by a long shot! Until May 31 it is 13.05. 13.05 is Raring with some upstream code. There isn't even a feature freeze on 13.05. Plus if you check the Changes Digest and the kernel changes log files there are suggestions of continued disfunction in specific libraries.  IMO kevpan815 states the problem and solution. Where it came from and I'm still not sure where it is going. We are actually useing Wheezy 7.0 dressed in a Saucy Salamander suit.

---

### Post by kuvanito on 2013-05-02
> **rrnbtter said:**
>  We are actually useing Wheezy 7.0 dressed in a Saucy Salamander suit.
now that's funny,hehehehehe

---

### Post by mc4man on 2013-05-02
> **kuvanito said:**
> d
anyways,it is a problem in 13.10 and that is what I am running right now.
Whether the gksu mode is still an issue in 13.10 64 bit installed from a daily is not exactly clear yet (here

To see one would need to boot to, then install from daily, install gksu & then check the mode.
On a quick test here on a 64 bit daily install the mode was set correctly But didn't check quite fully

To get the daily to install I had to use nomodeset, which unlike in the past was then made a default boot up option for the install. So a better test would have been to remove the option, restart, then install gksu 
Whether running under nomodeset has any affect on the install mode of gksu no idea, but did notice that on a live session with nomodeset that nautilus was handling the Desktop. So the 2nd question would be was that nonsense fixed a day late, dollar short or a side effect of nomodeset..?

(at least here am ready to dump gksu completely, the only hang up there is gdebi, have a bug on to convert to pkexec, hopefully they'll do so in a timely fashion. May have a look at if not forthcoming in the next month or so though possibly  a bit more complicated than nautilus or gedit.

[https://bugs.launchpad.net/ubuntu/+source/gdebi/+bug/1173827](https://bugs.launchpad.net/ubuntu/+source/gdebi/+bug/1173827)

---

### Post by kevpan815 on 2013-05-02
> **rrnbtter said:**
> Greetings,
it may be Saucy but it isn't 13.10 by a long shot! Until May 31 it is 13.05. 13.05 is Raring with some upstream code. There isn't even a feature freeze on 13.05. Plus if you check the Changes Digest and the kernel changes log files there are suggestions of continued disfunction in specific libraries.  IMO kevpan815 states the problem and solution. Where it came from and I'm still not sure where it is going. We are actually useing Wheezy 7.0 dressed in a Saucy Salamander suit.

Excuse me sir but I am getting Updates in Saucy Main that I am NOT getting in Raring Main, which I started getting as early as Monday, Chicago Time Zone, before I put in Ventrical's 3 command's, I get about 10 Updates at most, after putting in Ventrical's 3 command's I get over 100 Updates from Saucy Main NOT Saucy Proposed. I should also note that it is finally May 2nd and that by the end of the work day today the Saucy Tool-Chain is supposed to be 100% UP. I should also note that 13.10 Nightly Builds were up on the Ubuntu Cdimage Download Server as of Yesterday Night (Chicago Time Zone). So quit talking out of your hat as you most definitely did NOT check to see if the Nightly Builds were up before posting! The Unity Nightly Builds were definitely up yesterday evening (Chicago Time Zone). Just a big FYI.

---

### Post by kevpan815 on 2013-05-02
The previous poster is incorrect by the way, May 2nd: Saucy Tool Chain Uploaded, if you can NOT read Cariboo907's comments about how May 2nd is the first Official Day of Saucy Salamander Alpha Testing I suggest you Raring Poster's get some Glasses! Just FYI.

---

### Post by kevpan815 on 2013-05-02
P.S. The scheudule says The Split Off takes place today @ 21:00 UTC! It is now 21:24 UTC! All discussions of Raring in this Sub-Forum must now end.

---

### Post by QIII on 2013-05-02
Say, let's report posts that don't seem to fit to the Moderators and let the Moderators take it from there.

Would that work out for everyone?

---

### Post by kevpan815 on 2013-05-02
> **QIII said:**
> Say, let's report posts that don't seem to fit to the Moderators and let the Moderators take it from there.

Would that work out for everyone?

My point is that I have experienced absolutely 0 Problems Logging into Saucy, therefore what you guys are Discussing is a Raring Problem, NOT a Saucy Problem, as I have all ready verified that TTY1 Login works just fine in Saucy, it's ONLY Broke in Raring, NOT Saucy!

---

### Post by rrnbtter on 2013-05-02
Greetings,

> **kevpan815 said:**
> Excuse me sir but I am getting Updates in Saucy Main that I am NOT getting in Raring Main, which I started getting as early as Monday, Chicago Time Zone, before I put in Ventrical's 3 command's, I get about 10 Updates at most, after putting in Ventrical's 3 command's I get over 100 Updates from Saucy Main NOT Saucy Proposed. I should also note that it is finally May 2nd and that by the end of the work day today the Saucy Tool-Chain is supposed to be 100% UP. I should also note that 13.10 Nightly Builds were up on the Ubuntu Cdimage Download Server as of Yesterday Night (Chicago Time Zone). So quit talking out of your hat as you most definitely did NOT check to see if the Nightly Builds were up before posting! The Unity Nightly Builds were definitely up yesterday evening (Chicago Time Zone). Just a big FYI.

Opinions are like belly buttons, everyone has one more than they need.  I never said it wasn't Saucy. I said it wasn't 13.10. In fact it won't even be 13.05 until May 31st. I know whats in the stream because I get the Digest emails. Instead of following fifty opinions I just use the Wiki. [https://launchpad.net/ubuntu/saucy](https://launchpad.net/ubuntu/saucy). It speaks for it's self. I agree that we now have Ubuntu +1 so start testing and quit debating.

---

### Post by lisati on 2013-05-02
Thread closed for cool down and/or review.

---

### Post by Elfy on 2013-05-03
re-opened

---

### Post by kuvanito on 2013-05-05
This is my thread,I created it and it should stay opened but marked as solved!
as of my initial post on this thread this is still a problem in Saucy 13.10
I just installed today's daily build 2013/05/05 of Saucy 64 bits and it came up right away
but as mc4man suggested just open the terminal and copy this:
gksu-properties
then change mode to sudo

Note:05/05/2013 (wohooooo,Cinco de Mayo)

---

### Post by cariboo on 2013-05-05
I marked the thread as solved for you.

---

### Post by kuvanito on 2013-05-05
> **cariboo907 said:**
> I marked the thread as solved for you.

Thank You!

---

