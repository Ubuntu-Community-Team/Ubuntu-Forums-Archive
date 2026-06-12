---
title: "need help configuring torK"
date: 2008-05-19
forum: Security
---

### Post by mamadu bwana on 2008-05-19
I am trying to configure torK on my x386 computer running Ubuntu 8.04 and I am running into some problems.  Could you please point me towards the right solution?

I installed torK, tor and privoxy without any problems.

I used the torK wizard to configure to to run as a client.```


I configured torK to lauch tor when needed (tor is not started at bootup)

When I try to lauch torK from the "press play to get started"  I get this message:

TorK couldn't start your Privacy Proxy!
Message: Nothing.
Reason: This may be because you have configured it to launch at system startup. If that is the case, and you have reason to believe it is configured to listen to Tor, then just click 'No' and take a look at the 'Konqueror' settings in the configuration dialog.
Would you like TorK to try restarting it again?
```

Then I choose 'yes' and I get:

```
Tor Couldn't Bind to One of the Addresses/Ports you configured!
Message: May 19 15:52:14.256 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Reason: Tor is probably already running. If you like, TorK can connect to the already-running instance of Tor and manage that for you instead. (You will have to open the configuration dialog and re-apply any settings you wished to use.)
```
Would you like to do this now?

and when I choose 'yet' I get:
```

TorK has passed an invalid configuration file to Tor!
Message: May 19 15:52:14.256 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
This means: Please report this using 'Help->Report Bug' in the menu. Try to provide as much detail as possible. Thanks!
```

What am I doing wrong?  How do I manually start tor and privoxy and have torK use them?

I know that it is not my hardware or network because I ran torK off a live-CD and everything worked perfectly.

Many thanks in advance for any pointers!

---

### Post by Taris-Quickpaw on 2008-05-25
i'm having the same problem.

---

### Post by crabclaw on 2008-05-29
anyone come up with an answer to this?

---

### Post by zalzala on 2008-08-26
Same problem.

---

### Post by mkrahmeh on 2008-09-14
same problem here..
am behind a proxy with a smart filter feature..something like web sense, which prevents me from reaching websites like youtube.com and certain pages in the sourceforge.com domain...
can these applications help me out in this ?? if so..am having the very same problem as mentioned above..
any suggestions ??

---

### Post by pqrs541 on 2008-09-16
The Weather:[buy wow gold](http://www.mmoinn.com)  It's so dry, the trees are bribing the dogs. It's been hitter?s a goat's butt in a pepper patch.  Wintry roads are said to be "slicker than otter snot. [wow gold](http://wowus.mmoinn.com/index.do?PageModule=OrderForm_new)[wow gold](http://woweu.mmoinn.com/index.do?PageModule=OrderForm_new) [World of warcraft Gold](http://www.mmoinn.com)[wow gold](http://www.mmoinn.com)

---

### Post by Sico2 on 2008-10-07
Got the same on my 8.04. 
Why no one can see the bug in it? Do so little people use TorK?

---

### Post by bolwarra_ on 2008-10-11
You could try first killing the tor process under
System -> Administration -> System Monitor. Then run TorK.

hope this helps...

---

### Post by khaard on 2008-11-19
Here's what I've done to have a running smoothly and shiny Tor, TorK and privoxy :)
Before all that below you'll have to install it. I have choosed the TorK from universe repository, same for privoxy, and noreply.org repository for Tor. Let's add the noreply.org:
```
sudo kate /etc/apt/sources.list
```
and copy/paste there this:
```
deb http://mirror.noreply.org/pub/tor hardy main
deb-src http://mirror.noreply.org/pub/tor hardy main
```
then, of course
```
sudo aptitude update && sudo aptitude install tor tork privoxy
```
When you have all that stuff installed let's do some configuring.

Firstly, edit the privoxy config. It can be done by that:
```
sudo kate /etc/privoxy/config
```
then find a line 
```
#forward-socks4a   /               127.0.0.1:9050 .
```
and uncomment it. DO NOT delete that little dot at the end of the line :) Then restart privoxy.
```
sudo /etc/init.d/privoxy restart
```

Secondly, edit the Tor config. Type in Konsole
```
sudo kate /etc/tor/torrc
```
then find a line
```
#ControlPort 9051
```
and uncomment it. Then restart Tor by typing:
```
sudo /etc/init.d/tor restart
```
Next thing is to configure TorK, but this can be done by a First Run Wizard :)

---

### Post by melqui on 2009-02-05
[FONT="Verdana"][SIZE="1"]That worked beautifully. Thank you khaard![/SIZE][/FONT]

---

### Post by ITCons on 2009-03-28
Thanks for the note khaard. Works beautiful now...

I only noticed on installing the packages that I got an error on Hardy.

Error message:

> W: GPG error: [http://mirror.noreply.org](http://mirror.noreply.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CFF71CB3AFA44BDD
W: You may want to run apt-get update to correct these problems

Solution:

First get the key:

gpg --keyserver hkp://subkeys.pgp.net --recv-keys CFF71CB3AFA44BDD

Then add the key:

gpg --export --armor CFF71CB3AFA44BDD | sudo apt-key add -

then 

apt-get update


Thanks again!

---

### Post by neo01 on 2009-04-09
thank you khaard...

---

### Post by neeteex on 2009-05-07
> **neo01 said:**
> thank you khaard...
+1
and thank you ITCons too... :popcorn:

---

