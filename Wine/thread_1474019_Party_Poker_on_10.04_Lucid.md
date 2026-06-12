---
title: "Party Poker on 10.04 Lucid"
date: 2010-05-05
forum: Wine
---

### Post by standingwave on 2010-05-05
I had [Party Poker]("http://www.partypoker.com/") working under 9.04 and 9.10 but no joy so far with 10.04.

I downloaded the setup .exe and  made it executable. Opened it with wine windows program loader and followed the  install wizard prompts. I end up with four blank instances of wine internet explorer but  this was normal behavior and I would just delete these later.

Then it downloads/installs the application and then just vanishes... and then it sends firefox to this page which is blank for me:[ http://www.partypoker.com/installstart.htm]("http://www.partypoker.com/installstart.htm")

Now, I don't remember how it worked before but from the description of that url, it sounds kind of important. :p Made sure scripts were allowed and cookies enabled but it's just blank. Then I tried it with  Google Chrome (chromium) with the same results.

There's nothing in the wine menu but if I look in the program files,  there's a folder with a couple of executables. I try running them and get the following error:

```
Archive:  /home/xxx/.wine/dosdevices/c:/Program Files/PartyGaming.Net/PartyGamingNet.exe
[/home/xxx/.wine/dosdevices/c:/Program Files/PartyGaming.Net/PartyGamingNet.exe]
End-of-central-directory signature not found.  Either this file is not a zipfile, or it constitutes one disk of a multi-part archive.  In the latter case the central directory and zipfile comment will be found on the last disk(s) of this archive.
note:  /home/xxx/.wine/dosdevices/c:/Program Files/PartyGaming.Net/PartyGamingNet.exe may be a plain executable, not an archive zipinfo: cannot find zipfile directory in one of /home/xxx/.wine/dosdevices/c:/Program Files/PartyGaming.Net/PartyGamingNet.exe or /home/xxx/.wine/dosdevices/c:/Program Files/PartyGaming.Net/PartyGamingNet.exe.zip, and cannot find /home/xxx/.wine/dosdevices/c:/Program Files/PartyGaming.Net/PartyGamingNet.exe.ZIP, period.
```

Obviously it sounds like something is incomplete and I suspect it has something to do with that installstart url.

Now, one thing that is different is that this is my first foray into 64 bit Ubuntu. Is it possible that this is a 32/64 problem? I've understand that  PokerStars works so I think I would rather register with them before going back to 32 bit. 

Thanks in advance.

---

### Post by BULAAAN on 2010-05-07
I have exactly the same problem. I would also appriciate a resolve to this problem. At least how could we play directly on the browser through [PartyPokerAnywhere](http://www.partypoker.com/anywhere/) ? I click "Instant Play" button, I get the loading message, and nothing happens no matter how much I wait.

---

### Post by standingwave on 2010-05-07
> **BULAAAN said:**
> I have exactly the same problem. I would also appriciate a resolve to this problem. At least how could we play directly on the browser through [PartyPokerAnywhere]("http://www.partypoker.com/anywhere/") ? I click "Instant Play" button, I get the loading message, and nothing happens no matter how much I wait.Yeah, I tried that too. Are you 64 or 32 bit and what were you with Karmic?

I guess I might try to see if I can get pokerstars going this weekend.

---

### Post by BULAAAN on 2010-05-08
Sry for not giving the info in my first post. I have 32bit. FullTiltPoker works fine, but I need to get PartyPoker working T_T

---

### Post by standingwave on 2010-05-08
> **BULAAAN said:**
> I have 32bit. FullTiltPoker works fine, but I need to get PartyPoker working T_TThanks. Well, that answers my 32/64 question. So I won't be dropping back to 32 bit for this.

---

### Post by BULAAAN on 2010-05-08
I managed to get PartyPokerAnywhere working but it realy sucks. Any wone knows how to properly install PartyPoker on ubuntu 10.04 to work ?

To play from PartyPokerAnywhere install these packets .

**sudo apt-get install nautilus-open-terminal  gnome-exe-thumbnailer default-jre icedtea6-plugin**

---

