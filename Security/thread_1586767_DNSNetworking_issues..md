---
title: "DNS/Networking issues."
date: 2010-10-02
forum: Security
---

### Post by rammbhat on 2010-10-02
Hey guys

Im shocked! I've managed to catch a virus!! :P

I cannot access my net at all from ubuntu.. its really really slow.. both chrome and firefox... when i goto popular sites like google, yahoo etc the page redirects to some generic travel page called google travel and holidays! the url stays the same! Pls help me remove this.. Ive never had to deal with a virus in ubuntu! 

PS: I havent installed anything odd.. Only installed stuff from ubuntu package manager.. i DID plug in a friends pen drive tho :(

---

### Post by paulsp on 2010-10-02
Check your network settings, especially DNS servers (right click on your network connection > Connection Information). What is listed there? Copy the DNS just in case, and then change them to: 8.8.8.8,8.8.4.4. This is Google DNS, just to see if something changes.

---

### Post by Soul-Sing on 2010-10-02
you should give/show "us" the content of your logs.

---

### Post by cprofitt on 2010-10-02
What makes you think you have a virus?

I would boot to the live CD and then see if the problem persists.

---

### Post by rammbhat on 2010-10-02
Im assuming its not a DNS related problem and a virus cos im dual booting and using windows right now, same DNS same settings.. and everythings fine..

---

### Post by cprofitt on 2010-10-02
> **rammbhat said:**
> Im assuming its not a DNS related problem and a virus cos im dual booting and using windows right now, same DNS same settings.. and everythings fine..


Depending on your version of Windows that assumption may not be a good one. Do you have a live CD of the same version of Ubuntu as installed?

---

### Post by uRock on 2010-10-02
Open Network Manager and delete your current profile and create another one. This should fix the problem.

---

### Post by Rubi1200 on 2010-10-02
Also clear out the cache and cookies and install NoScript for Firefox.

---

### Post by rammbhat on 2010-10-02
Heyy looks like u guys were right... I created a new profile and used the google public dns.. problem seems to have resolved! Guess it wasnt a virus afterall! BUt the time taken to ping these DNS are like 289ms on average..my old dns had about 20ms :(

---

### Post by uRock on 2010-10-02
If you can access your router and copy the DNS addresses it uses and input them into the new profile, then that might get you a faster speed, though I think the new profile automatically uses the local ISP's DNS address, but I am not sure, nor am I home to check it out right now.

---

### Post by dwhecht on 2010-10-02
After downloading and installing package manager updates on 10/1/2010, I'm experiencing very poor network speed performance.  I believe I have isolated the problem to the ubuntu upgrade.  I tested the network connection to my apartment by testing another laptop.  Network speeds on it were normal.  I then hooked that second laptop up to the ethernet cable that my ubuntu laptop uses and I had good network speeds with it there too.

The problem also exists with my machine when trying to access my NAS, that is within my LAN.

I booted up, using grub, to kernel -24 b/c this last upgrade had -25 in it.  But I still had the network performance problem.

What specific logs would be helpful to see for this?

Tks,

---

### Post by HermanAB on 2010-10-02
Hmmm...  These "OMFG I got a Linux Virus!!!" thread owners should really go back and change the subject lines.  It just makes them look stupid.

---

### Post by dwhecht on 2010-10-02
Hold on, I'm isolating this to interaction between ubuntu and my new network switch.  I just bypassed my network switch, using my ubuntu system and the network speed was normal again.

More to come...

---

### Post by uRock on 2010-10-02
> **HermanAB said:**
> Hmmm...  These "OMG I got a Linux Virus!!!" thread owners should really go back and change the subject lines.  It just makes them look stupid.
If you report the thread as needing a name change, then we can do it. A poster can't change the title which shows in the sub-forum, iirc.

---

### Post by cprofitt on 2010-10-02
> **HermanAB said:**
> Hmmm...  These "OMFG I got a Linux Virus!!!" thread owners should really go back and change the subject lines.  It just makes them look stupid.

I do not think anyone looks stupid and saying so is very un-Ubuntu like. The forums are meant for help, not showing off your uber-l33t knowledge.

---

### Post by dwhecht on 2010-10-02
> **dwhecht said:**
> Hold on, I'm isolating this to interaction between ubuntu and my new network switch.  I just bypassed my network switch, using my ubuntu system and the network speed was normal again.

More to come...

Oddly enough, my problem has something to do with a new ethernet cable.  Sorry for the noise on the forum.  I figured out my own problem.

Tks,

---

### Post by cprofitt on 2010-10-02
> **dwhecht said:**
> Oddly enough, my problem has something to do with a new ethernet cable.  Sorry for the noise on the forum.  I figured out my own problem.

Tks,

Never apologize for asking for help -- that is what the forums are here for.

---

