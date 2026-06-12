---
title: "Full Tilt Poker, Poker Stars, Ultimate Bet online poker"
date: 2010-03-22
forum: Wine
---

### Post by drillerccg on 2010-03-22
I finally got all three clients to work under Wine. I'm a newbie to Linux so I will keep it simple for all newbies like myself:

1- I have installed Ubuntu 10.04 LTS beta on a clean hard drive, it's the only OS on this Dell Lattitude 620 notebook. (I could not get Full Tilt to work under Ubuntu 9.10 yesterday. May have been my fault though)

2- click on Applications/Ubuntu Software Center and search for Wine and install the first one that says (dummy package). It now appears that both options are installed on my computer. This is the 1.1.41 version of Wine.

3- Download Full Tilt Poker, Poker Stars, or Ultimate Bet from their website through Firefox and into your download folder. (If you do not have a rakeback.com account, you can sign up using my referal code. You will get 27-30% rake back and I get a referral fee. Erase your cookies first and use this link that has my number: [http://www.rakeback.com/?referrerid=35155](http://www.rakeback.com/?referrerid=35155) not a big deal if you don't):D

4- click on applications/accessories/terminal to start a terminal session. You will see:
yourname@your computer's name:~$ 

5- at the prompt type in: wine  download/name of the file you want to install (fulltiltsetup.exe)

 and then press enter

6- go through the steps and you are done. To launch the programs click applications/wine/programs

I tested all three. Ultimate bet's cashier and some of the windows are web based, they do not work. But you can play all the games, I'd say it has 90% functionality. Full Tilt and Poker Stars worked flawlessly.

Hope this helps. My first post here, so go easy on me.

---

### Post by pkaneski on 2010-05-01
Probably a dumb question but I installed wine and then installed pokerstars and it worked great. Now after I close pokerstars how do I run it again?

---

### Post by Funkey Monkey on 2010-05-01
> **pkaneski said:**
> Probably a dumb question but I installed wine and then installed pokerstars and it worked great. Now after I close pokerstars how do I run it again?

1) Go to Applications > Wine > Programs > Pokerstars

or

2) In the terminal wine ~/.wine/drive_c/Program\ Files/PokerStars/PokerStars.exe

---

### Post by bonds73 on 2010-05-23
I want to start by saying, I'm new to Ubuntu and I'm very impressed, if I didn't need Adobe CS4 I would switch all Windows PC's to Ubuntu but I think the Ubuntu Community is still working to solve that puzzle.

The only other Windows program I wanted (not needed) was poker. I followed the above instructions, initially I still had crashes after about 5 minutes of use. 

So then I went into configure Wine and added Fulltilt to Wine after install. I had to reboot to get it to show up. I then opened up configure wine under applications. Selected FullTiltPoker.exe and below I selected Windows Version Windows 7 as a Wine Configure option. I then took the forum advice and changed Audio driver by also clicking on the Audio Tab in Configure wine and deselected the default and selected EsounD Driver. I couldn't deposit through FullTilt on Ubuntu, but you could probably just go to the actual instadebit website and do it through there *shoulder shrug* I had existing funds so I didn't look too much into it. I played continuously in 3 tournaments for 2.5 hours with out a single crash. It actually worked better than my Windows machine as in Windows Vista when I go to the options menu in Full Tilt it crashes. I also tested multi table and resizing windows, no issues, played 2 tables flawlessly. Tested in both Ring and Tourney games. So the only issue I had was testing the deposit from the program, it did not open browser window.

Thank you for the above advice and hopefully this helps someone.

---

### Post by ricey155 on 2011-02-16
i keep getting the error using 10.10 

keeps telling me wine cannot open as not marked as excutable 

"blocked message: wine start /unix

done a search and a few pokerstar threads just wondered if anyone has had success with 10.10 and pokerstars ??

---

### Post by hatridge on 2011-02-20
> **ricey155 said:**
> i keep getting the error using 10.10 

keeps telling me wine cannot open as not marked as excutable 

"blocked message: wine start /unix

done a search and a few pokerstar threads just wondered if anyone has had success with 10.10 and pokerstars ??

I did a re-install of entire OS . Poker stars worked before through wine. However with the clean install I am having the same issues as the quote above.

---

### Post by hatridge on 2011-02-20
Although I was not successful installing through wine, I was able to install full tilt poker, and poker-stars through "play on Linux" I seen it when I typed wine in the search  bar from Ubuntu Software Center. Thought I'd try it and it worked for me.....

---

### Post by thebighoppa on 2011-03-16
Just downloaded Ubunto today and I am really liking it. I am having some real trouble getting pokerstars downloaded though - I have tried the actions suggested in this thread but no joy so far - any suggestions?

Also I have some software I use at pokerprolabs, will I be able to use this too?  I guess it will take a while to get used and once I figure it out will run like clockwork (me and the OS!).

---

### Post by thebighoppa on 2011-03-16
> **hatridge said:**
> Although I was not successful installing through wine, I was able to install full tilt poker, and poker-stars through "play on Linux" I seen it when I typed wine in the search  bar from Ubuntu Software Center. Thought I'd try it and it worked for me.....

You, my friend, are a legend!  Should have tried your route first!

---

### Post by Nobo115 on 2011-03-31
I haven't tried Poker Stars yet with WineHQ, but I did manage to get Party Poker to work using this guide from linuxconfig.org :):

[http://linuxconfig.org/linux-poker-online-client](http://linuxconfig.org/linux-poker-online-client)

You can also find a bunch of native Linux poker clients through pokerlistings online poker page:

[http://www.pokerlistings.com/online-poker-rooms](http://www.pokerlistings.com/online-poker-rooms)

Note: check the left-hand side for which OS's are supported.

---

