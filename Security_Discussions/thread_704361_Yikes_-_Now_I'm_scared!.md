---
title: "Yikes - Now I'm scared!"
date: 2008-02-22
forum: Security Discussions
---

### Post by whitefort on 2008-02-22
Perhaps this should be in the 'Beginner' section, but it IS a security question.  For nearly a year I've been running my wireless network without any encryption.  i figured this was OK, as I live out in the sticks, and I would probably notice if someone was sitting my garden with a laptop.

But today, just playing around, I installed Wireshark, and was a bit shocked to see that the hypothetical person in the garden would be able to read my emails using Wireshark.

So, I set up WEP encryption on my network.

However, when I run wireshark and send an email, I can still read part of the message, and worse, my POP password is right there on view.

Does this mean I haven't set WEP up properly?  Or do I need to look for another way to hide the details of emails sent over the wireless network?

I really don't like the idea that I could be sending an email from a wireless location and some eavesdropper could be getting the email address and password!!

Thanks!

---

### Post by The Cog on 2008-02-22
Are you running wireshark on the same PC as you are sending the mail from? That doesn't prove anything because wireshark will be seeing the packets before they get encrypted.

A proper wireless sniffer on a different PC would prove the point. I don't know the names of any such sniffers though.

---

### Post by astrotech226 on 2008-02-22
Also, don't try to use another wireless device to do the sniffing that has the WEP key in use.  Any encrypted traffic will be decrypted before wireshark sees it, making it also appear unencrypted.

---

### Post by fs3rp4 on 2008-02-22
And running WEP is amost nothing. See:
[http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy](http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy)

Try WPA. Your AP probaly have it:
[http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access](http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access)

For more informations about wireless security:
[http://en.wikipedia.org/wiki/Wireless_security](http://en.wikipedia.org/wiki/Wireless_security)

---

### Post by whitefort on 2008-02-22
Thanks for the replies, guys.

Well, I told you I was a beginner!  Yes, I was stupidly doing the sniffing from a friendly computer.

Still, I have to say that I was really shocked at how much an unencrypted wireless setup gives away.  I knew there was a danger of someone stealing internet access, but not that they could see so much of what was going on.

Also, I'll have a look at WPA - thanks again!

---

### Post by kaens on 2008-02-22
> **whitefort said:**
> Thanks for the replies, guys.

Well, I told you I was a beginner!  Yes, I was stupidly doing the sniffing from a friendly computer.

Still, I have to say that I was really shocked at how much an unencrypted wireless setup gives away.  I knew there was a danger of someone stealing internet access, but not that they could see so much of what was going on.

Also, I'll have a look at WPA - thanks again!

Don't feel stupid - everyone is a beginner at some point. The important thing is that you noticed, and decided to learn.

Also, WPA not WEP if you're concerned about privacy. Do some experiments with cracking your own encryption while not logged on to your wireless. Read up on it, and play around . . . it's possible to crack WEP in a matter of minutes in the best case (from the cracker's standpoint) scenario. WPA not so much.

---

### Post by wirelessmonkey on 2008-02-22
WPA is not a balm, make sure and use strong passwords!!!  In my test environ, I can crack any  generic named 8-10 char password nearly as quickly as a modern router w/ WEP.  Give your network a unique name and use password > 10 characters, with symbols and different cases.

---

### Post by osx424242 on 2008-02-23
Also, WEP/WPA only encrypts the messages sent over the air between your computer and your wireless router or access point.  That unencrypted e-mail password still travels through a few other computers on its way to your e-mail server.

Open up a terminal window and type:
```
traceroute mail.google.com
```
You'll get a list of all the servers between you and gmail.  You can repeat this for other servers you use (mail.yahoo.com, your work, ubuntuforums.org, etc.).  To get to ubuntuforums.org, this message is going through servers that are named Seattle, Denver, Chicago, Washington (assuming DC?), Paris, and London before I hit canonical.com (and traceroute bombs out on the last 10ish entries).

Whenever possible, use secure logins ([https://mail.google.com/](https://mail.google.com/) instead of [http://mail.google.com/](http://mail.google.com/)) and verify that your browser location bar changes color (usually from white to yellow) or shows you an icon or something to indicate you're on a 'secure' web site.  Using https sites encrypts all the data between your computer and their server.

Obviously there's a lot more info out there once you know the right words to Google :)

---

### Post by FakeOutdoorsman on 2008-02-23
You can encrypt the data between you and the mail server (secure pop, SMTP-AUTH and TLS).  Both incoming and outgoing can and should be encrypted.   As for the client side, most good e-mail programs such as Claws-Mail and Thunderbird can handle this.

---

### Post by jba6511 on 2008-02-25
no body has mentioned it but you can also turn off the broadcasting of your ssid and enable mac filtering. Although a determined malicious user can still get around this (obscurity instead of security), it might deter the average script kiddie.

---

### Post by whitefort on 2008-02-26
Once again, thanks for the replies, everyone.  Much appreciated.

Just a couple of follow-up questions, if anyone has time for a quick reply.

First, encrypting data between me and the mail server.  
I understand that Thunderbird can handle this (though I've not yet researched how to set it up), but I'm wondering how this would get decrypted when it reaches the server at my ISP.   Perhaps this question is itself a demonstration of how clueless I am at this!

Also, if my SSID is just a name I've chosen to give my home network, what's the real advantage of hiding it?  I'm presuming that a potential snooper will still see there's a wireless network there, even if he doesn't get the actual name - why is the name an advantage to him?

All of this is still a bit academic for me, as I live in a location where my nearest neighbour is several fields away, but I AM hoping to learn enough to convince various family members that using unsecured WiFi in a built-up area is crazy.

And at the risk of trying your patience...  I'm also trying to teach family members the importance of good passwords (even on my own home PCs).

I've downloaded 'John' planning to run it on my machines and expose any inadequate passwords - but I have no idea how to get it to work.  The Man page seems to suggest I just point it at my passwd file, but that doesn't seem to do anything

When I run:
me@MyPC  sudo john /usr/bin/passwd

I just get:
Loaded 0 passwords, exiting...

Is this because passwd is already encrypted or something?  Should I be pointing John at some other file in Ubuntu?

Thanks again, everyone.

---

### Post by astrotech226 on 2008-02-26
> **whitefort said:**
> 
When I run:
me@MyPC  sudo john /usr/bin/passwd

I just get:
Loaded 0 passwords, exiting...

Is this because passwd is already encrypted or something?  Should I be pointing John at some other file in Ubuntu?

The passwd file is located at /etc/passwd, but the encrypted passwords are in /etc/shadow.  So try this:

```
sudo john /etc/shadow
```

---

### Post by chewearn on 2008-02-26
For the really paranoid (like myself :biggrin:), I use this password generator for my WPA2 network:
[https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm)

You can also look around grc.com for interesting articles on internet security.

---

### Post by jba6511 on 2008-02-26
the ssid is just a name you choose. If its hidden (invisible) than it will not show up on the list of available wireless networks. However, tools such as Kismet will reveal that there is a hidden wireless network and the bssid associated. By also enabling MAC filtering, only those PC's with the MAC addresses you approve will be able to connect. Once again, this can be overcome by using a tool such as macchanger to change the attackers MAC address to one on the approved list. These methods just make it a little more difficult for an attacker. The best advice would be to pick a strong WPA2 Personal password that contains a combination of letters, number and symbols that is not based on a dictionary word (use a phrase you can remember. For ex. Just Sit Right Back and You Will Hear a Tale... would be J$rB&ywH@T), enable MAC filtering, use a hidden ssid, encrypt sensitive emails (PGP, etc) and encrypt communications. If you are really paranoid, download BackTrack 3 from [www.remote-exploit.com](www.remote-exploit.com) and follow some of the tutorials on their forums to see if you can get into your own network with these measures in place.

edit: with John I believe you have to obtain the /etc/shadow and /etc/passwd files on newer linux systems and then use the unshadow function before you can launch a dictionary or hybrid attack on the passwords. Double check though as I am still learning myself.

---

### Post by osx424242 on 2008-02-28
> **whitefort said:**
> First, encrypting data between me and the mail server.  
I understand that Thunderbird can handle this (though I've not yet researched how to set it up), but I'm wondering how this would get decrypted when it reaches the server at my ISP.   Perhaps this question is itself a demonstration of how clueless I am at this!
Like all analogies, this is suspect, but: imagine buying a safe.  You get two keys for it.  You fly down to Florida (if you live in Florida, then s/Florida/Seattle/g :)) and give one of the keys to your buddy.  Then you fly home.  You write a letter and put it into the safe, and send the safe to your buddy via UPS.  If you hadn't put the letter into the safe, any of a few dozen people between you and your buddy could have opened the letter, read it, and resealed the envelope.  Because the letter is in a safe, you are reasonably confident that no one has read it.  When your buddy is done reading the letter, they write a reply, put it back into the safe, and send the safe back to you.
Okay we're using the Internet so everything is faster and cheaper than mailing a heavy safe cross-country, but the principal still applies: except here, the ISP's mail server is "your buddy" and "the Internet between you and your ISP's mail server" is UPS.  If you are connected to a secure server ([https://.](https://.)...) then you are using your safe.  If you are not ([http://.](http://.)...) then you are just sending your letter out without securing it in any way.
It's more detailed than that, of course, but this is a start....

> Also, if my SSID is just a name I've chosen to give my home network, what's the real advantage of hiding it?  I'm presuming that a potential snooper will still see there's a wireless network there, even if he doesn't get the actual name - why is the name an advantage to him?
As others have said: it doesn't stop a dedicated attacker, just slows them down a little.  The biggest thing to take home is that it makes your wireless connection (from your computer to your wireless router) more difficult to attack than other vectors.  You know the story about the two guys on safari, they stop to cool their feet in a lake, a lion comes out of the bushes, and one of them starts lacing up his boots? His safari partner asks him why he's bothering, since he can't outrace a lion, and he replies, "I don't have to be faster than the lion, I just have to be faster than you."  If you make your WLAN harder to crack than anyone else's WLAN than someone who just wants to crack a WLAN won't attack you.  If you make your WLANL harder to crack than any other aspect of your online communications, than someone who wants your info won't attack your WLAN (they'll just attack some other weak point of your communication path).

> All of this is still a bit academic for me, as I live in a location where my nearest neighbour is several fields away, but I AM hoping to learn enough to convince various family members that using unsecured WiFi in a built-up area is crazy.
Agreed: securing your WiFi is academic.  Securing your WiFi access point-to-the-rest-of-the-Internet is much more important _for_you_.

For your family members:
- someone could drive by, or hang out in a nearby apartment, and take their passwords or credit card numbers
- someone could use their internet access with no malicious intent towards your family, but download something illegal: the courts are still unclear on this: your family members _could_ be held liable (e.g. the RIAA could sue your family members for allowing someone else to use their internet to download mp3s).  This is pretty speculative... but is it worth the potential legal hassles?  Especially since it just takes an hour or so (or less!) to secure your wireless network?

> And at the risk of trying your patience...  I'm also trying to teach family members the importance of good passwords (even on my own home PCs).
Good luck :)

---

### Post by whitefort on 2008-02-28
Thanks again, everyone - this has all been incredibly useful, and reinforces my conviction that this forum is one of the most friendly and helpful on the internet!

I've got john running.  In fact it's now been running for 2 days non-stop, and still hasn't cracked any passwords, so maybe they weren't quite so easy as I suspected.

I'm visiting family tomorrow, and I'll be taking my (ubuntu!) laptop with wireshark and a few other bits and pieces, just to give them a scare and persuade them that yes, it IS SO worth the 'hassle' of securing their network!

Many thanks!

---

### Post by wieman01 on 2008-02-28
For WEP security, also see my own thread (signature). Plus I want to add that secure email communication can be achieve using Enigmal or GPG. But the recipient must have it enabled as well (public key vs. private key encryption). If you want to know more about it, see this:

[http://enigmail.mozdev.org/home/index.php]("http://enigmail.mozdev.org/home/index.php")

To reemphasize, MAC filtering and hidden SSID are not security feature and are not part of the 802.11i  specification. For MAC cloning you don't even know a tool. This is enough:
> ifconfig eth0 down hw ether 00:00:00:00:00:01
ifconfig eth0 up
Hidden SSID's make your system even less secure, in particular if you are a laptop user (roaming):

[http://blogs.technet.com/steriley/archive/2007/10/16/myth-vs-reality-wireless-ssids.aspx]("http://blogs.technet.com/steriley/archive/2007/10/16/myth-vs-reality-wireless-ssids.aspx")

WPA2 with AES and a long password with special characters is the best protection you can get for wireless networks.

Hope this helps a bit.

---

### Post by whitefort on 2008-02-28
> **wieman01 said:**
> secure email communication can be achieve using Enigmal or GPG. But the recipient must have it enabled as well 

I've been playing around with GPG and Enigmail for a while now. I started getting interested in this stuff after reading Stephan Levy's book, CRYPTO.

Again, it's a bit academic, since I can't persuade any of my friends to install the software!!! (though I do like the idea of digitally signing my emails).

I've also been playing around with Encfs, and have found it really useful.  I don't have any secret files that would be of interest to spies, law enforcement or shadowy government agencies(!!!), but I do have some private stuff that I wouldn't want a family member to read if I had an unfortunate accident or something, and if they inherited my computers.  Encfs is so incredibly simple to use and hassle free, but it offers more than enough protection for my private stuff, at least from family and friends even more clueless than myself!

Thanks again.  I'm going to have to make notes from this thread and put them in my 'useful stuff' notebook!

---

### Post by astrotech226 on 2008-02-28
> **wieman01 said:**
> 
Hidden SSID's make your system even less secure, in particular if you are a laptop user (roaming):

[http://blogs.technet.com/steriley/archive/2007/10/16/myth-vs-reality-wireless-ssids.aspx]("http://blogs.technet.com/steriley/archive/2007/10/16/myth-vs-reality-wireless-ssids.aspx")


I'd like to learn more about this part in particular and didn't really see this in the link provided.  Can you explain why this is or have a link to somewhere that does?

Thanks!

---

### Post by wieman01 on 2008-02-28
> **whitefort said:**
> I've been playing around with GPG and Enigmail for a while now. I started getting interested in this stuff after reading Stephan Levy's book, CRYPTO.

Again, it's a bit academic, since I can't persuade any of my friends to install the software!!! (though I do like the idea of digitally signing my emails).

I've also been playing around with Encfs, and have found it really useful.  I don't have any secret files that would be of interest to spies, law enforcement or shadowy government agencies(!!!), but I do have some private stuff that I wouldn't want a family member to read if I had an unfortunate accident or something, and if they inherited my computers.  Encfs is so incredibly simple to use and hassle free, but it offers more than enough protection for my private stuff, at least from family and friends even more clueless than myself!

Thanks again.  I'm going to have to make notes from this thread and put them in my 'useful stuff' notebook!
The best data / file system encryption software is - in my opinion - Truecrypt. I have used it for years and it gets better and better. Check it out:

[http://www.truecrypt.org/]("http://www.truecrypt.org/")

---

### Post by wieman01 on 2008-02-28
> **astrotech226 said:**
> I'd like to learn more about this part in particular and didn't really see this in the link provided.  Can you explain why this is or have a link to somewhere that does?

Thanks!
I need to check that once again. Need to find a new source. Let me do some research and get back to you.

---

### Post by whitefort on 2008-03-01
> **wieman01 said:**
> The best data / file system encryption software is - in my opinion - Truecrypt.

I've just been reading their website, and it looks quite impressive - it seems almost identical to a commercial program I used to use on my Windows machine.

On balance, I still think encfs is more appropriate to my needs, as I don't have to set the size of the encrypted area - with Encfs, this increases/decreases in a dynamic way, and I kinda prefer that.  However, I may give Truecrypt a go on my last remaining Windows computer.

Thanks!

---

### Post by wieman01 on 2008-03-01
> **whitefort said:**
> On balance, I still think encfs is more appropriate to my needs, as I don't have to set the size of the encrypted area - with Encfs, this increases/decreases in a dynamic way, and I kinda prefer that. 
That's indeed a very good feature. Thank you for highlighting that... Perhaps encfs is an option for me as well.

---

### Post by whitefort on 2008-03-01
I've just installed Truecrypt on my Windows machine and set it up.  

I have to say, the wizard makes it all very simple and painless.  I DO like Encfs, but I wouldn't ever have figured out how to set it up if it hadn't been for the step-by-step instructions in the 'Hacking Ubuntu' book.

Also, in setting up Truecrypt, I noticed something about an option for dynamic file size (unless I misunderstood it - I must check the docs!).  It seemed to be saying that you could have the dynamic file size, and that if you did so, the file size you set up will be regarded as a maximum.   This would work for me very well, so you might have converted me from Encfs to Truecrypt!

Thanks!

---

### Post by wieman01 on 2008-03-01
> **whitefort said:**
> I've just installed Truecrypt on my Windows machine and set it up.  

I have to say, the wizard makes it all very simple and painless.  I DO like Encfs, but I wouldn't ever have figured out how to set it up if it hadn't been for the step-by-step instructions in the 'Hacking Ubuntu' book.

Also, in setting up Truecrypt, I noticed something about an option for dynamic file size (unless I misunderstood it - I must check the docs!).  It seemed to be saying that you could have the dynamic file size, and that if you did so, the file size you set up will be regarded as a maximum.   This would work for me very well, so you might have converted me from Encfs to Truecrypt!

Thanks!
Oh, that's new to me as well. :-)

---

### Post by whitefort on 2008-03-01
> **wieman01 said:**
> Oh, that's new to me as well. :-)

I've done a bit more digging.

Truecrypt does dynamic volumes... sort of...

From the user guide:

"Dynamic TrueCrypt container is a pre-allocated NTFS sparse file whose physical size (actual disk
space used) grows as new data is added to it. Note that the physical size of the container (actual
disk space that the container uses) will not decrease when files are deleted on the TrueCrypt
volume. The physical size of the container can only increase up to the maximum value that is
specified by the user during the volume creation process. After the maximum specified size is
reached, the physical size of the container will remain constant.
Note that sparse files can only be created in the NTFS file system. If you are creating a container
in the FAT file system, the option Dynamic will be disabled (“grayed out”)"


So, the volume only grows dynamically and never shrinks again.  Which, it seems to me, kinda defeats the purpose.  Having said that, I REALLY like Truecrypt, and I'll be putting  it on my desktop machines.  On my laptop, where space is at more of a premium, I'll stick with Encfs for now.

Thanks again, everyone - this has all been very helpful.

---

### Post by whitefort on 2008-03-02
Ok - just another quick note for any fellow encryption newbies who are interested in this stuff...

After a weekend of comparing Encfs and Truecrypt, I think I have to declare myself officially converted to Truecrypt.

It's MUCH easier to set up (a wizard walks you through it - what could be easier?!).  With Encfs, I had to follow a lot of quite involved steps to get everything working. (when I say, 'involved', I stress again that I'm a beginner at this stuff.  Everyone else might find it dead easy!)

I like it that with Encfs, you don't have to decide how much disk space to allocate in advance, so your filesize is dynamic, growing and shrinking as you add/delete items from your encrypted folder - but actually it only does this because it creates a plain ol' folder but encrypts each individual item inside it.

This is fine for my purposes, but the ultra-security conscious user might worry about it, as the files are individual and obviously still there, even if encrypted.  With Truecrypt, they're all tucked away into the one file, which can even be hidden altogether.

I'm sure both systems have other pros and cons, but the fact that Truecrypt will also run on Windows machines is a big plus for me (I still have one Windows machine).

So, thanks for letting me know about Truecrypt!!!

---

### Post by wieman01 on 2008-03-02
Kudos to you for sharing this with us. :-) Very interesting read. Thank you.

---

### Post by P235 on 2008-03-05
All this endorsement to Truecrypt merits a visit and a try on my part.  Though I do imagine myself wandering through the fog that borders caution and paranoia, Truecrypt's reported ease of use will likely make this a worthwhile experience.  I'm not wearing an aluminium cap yet.  :)

---

### Post by wieman01 on 2008-03-05
But please read this to ensure you know what encryption can do and what its shortcomings are:

[http://citp.princeton.edu/memory/]("http://citp.princeton.edu/memory/")

---

### Post by P235 on 2008-03-06
Thanks for the link wieman, it is very interesting.

---

### Post by whitefort on 2008-03-10
For anyone who's interested, there's a downloadable podcast review of Truecrypt [COLOR="Navy"][HERE]("http://www.grc.com/securitynow.htm")[/COLOR]

They give it an astonishingly good review. The only 'negative' thing they have to say is that it's this version is still quite new, but for the rest of the hour (more or less) they just rave about how good it is, and express amazement at its features (Like how Windows stuff runs much faster on a Truecrypt encrypted drive than it does in a normal Windows setup).



Watching my spy movies, and thinking about this encryption stuff, I got to thinking.  Wouldn't it be really cool if they made it so you could give a file a sort of double-layer.  I mean, the same file would have TWO passwords.  One would be the 'real' password and open up the inner sanctum, but the other would be the password you'd give the enemy agents after they'd tortured you for a while - this would APPARENTLY open the file, but would really only open a secondary area, where you'd taken the precaution of storing innocent stuff or misinformation...

I know... I watch WAY too many spy movies....:)

---

### Post by chewearn on 2008-03-10
> **whitefort said:**
> 
Watching my spy movies, and thinking about this encryption stuff, I got to thinking.  Wouldn't it be really cool if they made it so you could give a file a sort of double-layer.  I mean, the same file would have TWO passwords.  One would be the 'real' password and open up the inner sanctum, but the other would be the password you'd give the enemy agents after they'd tortured you for a while - this would APPARENTLY open the file, but would really only open a secondary area, where you'd taken the precaution of storing innocent stuff or misinformation...

I know... I watch WAY too many spy movies....:)

Isn't this already a feature with Truecrypt?  You can create hidden volume: [http://www.truecrypt.org/docs/?s=hidden-volume](http://www.truecrypt.org/docs/?s=hidden-volume)

---

### Post by whitefort on 2008-03-15
> **AstalaVista said:**
> Isn't this already a feature with Truecrypt?  You can create hidden volume: [http://www.truecrypt.org/docs/?s=hidden-volume](http://www.truecrypt.org/docs/?s=hidden-volume)

Oh wow... That is just so cool!  I've finally got round to trying it out, and it's amazing.  I hadn't realised that the same file could have different passwords, and depending on which you give, you get a different folder.  I've just set it up on a pen drive, and it works perfectly. 

Is there anything these guys DIDN'T think of?

Thanks for directing my attention to this.  Now I need to go and read the manual (what a concept!) to see what else it can do.

---

