---
title: "Let's hack the Zune!"
date: 2009-07-10
forum: The Cafe
---

### Post by gymophett on 2009-07-10
As you know, still, no-one has been able to sync the Zune without using a VirtualBox. It's time to finally hack this thing. Even if it uses a Window's computer, it would be better to use it one time than everytime you sync. I'm tired of syncing my Zune via Window's computer. We can do this! I hook my Zune up, and it recognizes and mounts it. I can browse through whats on them, but can't listen or sync it. So everyone post ideas, and things to try until we get it right.. 
:guitar:

---

### Post by dragos240 on 2009-07-10
Now you're thinking with portals!

---

### Post by calrogman on 2009-07-10
> **dragos240 said:**
> Now you're thinking with portals!

[SIZE="1"]
This was a triumph.
I'm making a note here: HUGE SUCCESS.
It's hard to overstate my satisfaction.

Aperture Science:
We do what we must because we can.
For the good of all of us
Except the ones who are dead.

But there's no sense crying over every mistake
You just keep on trying till you run out of cake
And the science gets done and you make a neat gun
For the people who are still alive.

I'm not even angry.
I'm being so sincere right now.
Even though you broke my heart and killed me.
And tore me to pieces.
And threw every piece into a fire.
As they burned it hurt because
I was so happy for you.

Now these points of data make a beautiful line
And we're out of beta we're releasing on time.
So I'm GLaD I got burned think of all the things we learned
For the people who are still alive.

Go ahead and leave me.
I think I prefer to stay inside.
Maybe you'll find someone else to help you.
Maybe Black Mesa -
THAT WAS A JOKE. HA HA, FAT CHANCE.
Anyway, this cake is great:
It's so delicious and moist.

Look at me still talking when there's science to do.
When I look out there it makes me GLaD I'm not you.
I've experiments to run there is research to be done
On the people who are still alive

And believe me I am still alive.
I'm doing science and I'm still alive.
I feel FANTASTIC and I'm still alive.
While you're dying I'll be still alive.
And when you're dead I will be still alive.

Still alive
Still alive
[/SIZE]

---

### Post by andrew_D14 on 2009-07-10
if i knew anything about hacking i would totally do this because i haven't been able to upload anything on my zune ever since i switched to linux

---

### Post by phrostbyte on 2009-07-10
Try to get in touch with this project:

[http://libmtp.sourceforge.net/]("http://libmtp.sourceforge.net/")

---

### Post by Bungo Pony on 2009-07-10
You could always rip the guts out of your Zune and replace it with one of those handheld Tetris games :)

---

### Post by gymophett on 2009-07-11
Hmm. This is still as far as I can get.
Screenshot attached.. Hmm. I still haven't got to a point where it ask for some secret handshake... Odd.

---

### Post by Rainstride on 2009-07-11
its not compatible with the MTP plugin in rhythmbox?

---

### Post by gymophett on 2009-07-11
> **Rainstride said:**
> its not compatible with the MTP plugin in rhythmbox?

No, this Microsoft product is like on... LOCKDOWN. Why couldn't they make it hackable for us?!? :(

---

### Post by dragos240 on 2009-07-11
Because they're microsoft, remember?

---

### Post by gymophett on 2009-07-11
> **dragos240 said:**
> Because they're microsoft, remember?

Yes, but their OS is COMPLETELY hackable. Yet the Zune has yet to be hacked.

---

### Post by tacantara on 2009-07-11
Then maybe Microsoft should get away from the NT kernel and build an OS based on Zune

:lolflag:

I'd love to hack the Zune and make it work on Ubuntu, but I'm not that computer savvy. Not yet, at least.

---

### Post by gymophett on 2009-07-11
I am somewhat computer savvy. In 1st grade I taught my Computer Lab teachers how to use computers correctly. xD

---

### Post by Ranko95 on 2009-07-11
could you do it like an ipod touch? sync wirelessly with amorok or something?
just thinking out loud here.

---

### Post by Warpnow on 2009-07-11
Microsoft developed their own version of MTP that is zune-exclusive. I think they call it MTPz or something.

---

### Post by gymophett on 2009-07-11
> could you do it like an ipod touch? sync wirelessly with amorok or something?
just thinking out loud here.
That is something to think about, as Zunes have wireless sync also.

> **Warpnow said:**
> Microsoft developed their own version of MTP that is zune-exclusive. I think they call it MTPz or something.

I didn't know that! Thanks! This will come in tons of handy!

---

### Post by Gizenshya on 2009-07-11
well, just thinking out loud, I would think it would be easier to trick it into thinking you were on a win box, instead of hacking the zune itself.

try to find out the dlls or what other files (registry accesses, etc.) "occur" when you're connecting.  Something in there locks it, or unlocks it.

---

### Post by gymophett on 2009-07-11
> **Gizenshya said:**
> well, just thinking out loud, I would think it would be easier to trick it into thinking you were on a win box, instead of hacking the zune itself.

try to find out the dlls or what other files (registry accesses, etc.) "occur" when you're connecting.  Something in there locks it, or unlocks it.

You read my mind! That's what I was thinking too. It would require Wine, but thats fine. I found a ZuneMTPZ.dll! 
[http://www.corruptedfilerepair.com/File-Information/ZuneMTPZ.dll-Zune-Microsoft-Corporation.asp](http://www.corruptedfilerepair.com/File-Information/ZuneMTPZ.dll-Zune-Microsoft-Corporation.asp)
We can somehow put that to use. There is something called ZAlternator also, which enables the Zune to be synced using WMP11, and WMP11 works with Wine..
But you have to have the Zune software to use ZAlternator. Does WINE have registry files? If so, we may be able to get it to work as a flash drive.

EDIT: I just found WINE has registry files! You can go in there and change it to make Zune think it's a flash drive. But... how can I access the Zune via Wine?

EDIT: [http://www.zuneboards.com/forums/tutorials/16833-sync-your-zune-using-mediamonkey-zalternator.html](http://www.zuneboards.com/forums/tutorials/16833-sync-your-zune-using-mediamonkey-zalternator.html)

I am downloading Zune software, I am going to try and replace .dll files, etc and see if it may work.

---

### Post by phrostbyte on 2009-07-11
The secret handshake typically works something like this:

------------------------------
Hi. I am device X, there is some data.

Hi. I am the device X's driver, I shall take your data and encrypt it. Here is the encrypted data.

Thank you, I will decrypt it and confirm that is the same I sent you.
------------------------------

So what you need to find is the encryption algorithm they are using (probably AES), and what their encryption key is. Finding this information is impossible with just a USB sniffer, you'd have to find the code that does this in the actual Zune software (the part of the software that actually communicates with the Zune device, ie the driver). This can be tricky, because that part of the code which does the handshaking might be intentionally obfuscated.

---

### Post by Gizenshya on 2009-07-11
Question: why does such a handshake even exist?  They don't want to sell Zunes or something?

---

### Post by HappyFeet on 2009-07-12
> **Gizenshya said:**
> Question: why does such a handshake even exist?  They don't want to sell Zunes or something?

They just want people that have zune's and install linux, to go- "what? my zune won't work in linux? I'm going back to windows"

I'm glad Sony is OS indifferent. My PSP syncs wonderfully.

---

### Post by gymophett on 2009-07-12
> **phrostbyte said:**
> The secret handshake typically works something like this:

------------------------------
Hi. I am device X, there is some data.

Hi. I am the device X's driver, I shall take your data and encrypt it. Here is the encrypted data.

Thank you, I will decrypt it and confirm that is the same I sent you.
------------------------------

So what you need to find is the encryption algorithm they are using (probably AES), and what their encryption key is. Finding this information is impossible with just a USB sniffer, you'd have to find the code that does this in the actual Zune software (the part of the software that actually communicates with the Zune device, ie the driver). This can be tricky, because that part of the code which does the handshaking might be intentionally obfuscated.

You seem to know more than I do. I have a Zune and Zune software on an XP box I have. Any clue on how to do this?

---

### Post by bigbrovar on 2009-07-12
friends dont let friends buy Zune

---

### Post by 3rdalbum on 2009-07-12
> **Gizenshya said:**
> Question: why does such a handshake even exist?  They don't want to sell Zunes or something?

Zunes can wirelessly receive songs from other Zune owners, that automatically self-destruct after a day or so. The last thing Microsoft wants you to do is connect your Zune to unapproved software that can extract other people's songs.

---

### Post by phrostbyte on 2009-07-12
> **Gizenshya said:**
> Question: why does such a handshake even exist?  They don't want to sell Zunes or something?

Because they want to control you. It's really as simple as that.

---

### Post by phrostbyte on 2009-07-12
> **gymophett said:**
> You seem to know more than I do. I have a Zune and Zune software on an XP box I have. Any clue on how to do this?

I know some stuff about this but I am by no means a professional at reverse engineering.

Do you per chance know any programming? You probably will have to learn x86 assembly. You can disassemble the DLLs in question.

Use this tool (NASM)
[www.nasm.us](www.nasm.us)

You can use a debugger on the DLL to set break points in interesting locations or to use a watch list if certain value changes:
(WinDbg ironically made by Microsoft)
microsoft.com/whdc/devtools/debugging/default.mspx

Using disassembler and debugger it should be able to pinpoint generally where the hand shake occurs in the code. But it might be very hard.

---

### Post by gymophett on 2009-09-12
> **phrostbyte said:**
> I know some stuff about this but I am by no means a professional at reverse engineering.

Do you per chance know any programming? You probably will have to learn x86 assembly. You can disassemble the DLLs in question.

Use this tool (NASM)
[www.nasm.us](www.nasm.us)

You can use a debugger on the DLL to set break points in interesting locations or to use a watch list if certain value changes:
(WinDbg ironically made by Microsoft)
microsoft.com/whdc/devtools/debugging/default.mspx

Using disassembler and debugger it should be able to pinpoint generally where the hand shake occurs in the code. But it might be very hard.

Can someone try this? I feel quite dumb, as I don't know how to do it. But this is very helpful.

---

### Post by Katalog on 2009-09-12
My solution was as follows:
1) Sell 8GB Zune
2) Use money to purchase 8GB Sansa Fuse + 8GB Micro SDHC card
3) Live happily ever after :)

But seriously, my hat will certainly be off to whoever manages to breech that firmware, because from what I understand it's a different animal and even more restictive and complicated than the standard WMA DRM firmware on other players. Would be cool if someone could finally crack this. My son has an 80GB Zune, and that is one of the few things that keeps him from going to Linux. What would be even cooler is if it some day there were a Rockbox firmware for it (must have OGG and FLAC support, otherwise it is dead to me!).

---

### Post by DanielHylton13 on 2009-11-15
[COLOR=Black][SIZE=2][FONT=Garamond]***I'm going to work on this handshake. Maybe I can crack the code. I'll keep you updated on how it's going.***[/FONT][/SIZE][/COLOR]

---

### Post by Chronon on 2009-11-15
> **Katalog said:**
> My solution was as follows:
1) Sell 8GB Zune
2) Use money to purchase 8GB Sansa Fuse + 8GB Micro SDHC card
3) Live happily ever after :)

But seriously, my hat will certainly be off to whoever manages to breech that firmware, because from what I understand it's a different animal and even more restictive and complicated than the standard WMA DRM firmware on other players. Would be cool if someone could finally crack this. My son has an 80GB Zune, and that is one of the few things that keeps him from going to Linux. What would be even cooler is if it some day there were a Rockbox firmware for it (must have OGG and FLAC support, otherwise it is dead to me!).

If somebody figures out how to run unsigned code on this thing (or figures out how to properly sign it) then there might be a shot at Rockbox.  Unfortunately, I am not aware of any progress on this front.  Also, I don't think any of the existing devs have one of these players.

On a brighter note nobody was able to run any code on the 2nd generation iPod Nano until recently.  Somebody figured out an exploit and there's now a Rockbox port that runs (though not to the level of fully supported targets).

---

### Post by hessiess on 2009-11-15
Just dump it and support a company which follows open standards and dousen't tie you to a fundamentally broken OS.

---

### Post by pwnst*r on 2009-11-15
> **hessiess said:**
> Just dump it and support a company which follows open standards and dousen't tie you to a fundamentally broken OS.

blah blah blah

---

### Post by Frak on 2009-11-15
> **pwnst*r said:**
> blah blah blah
True that.

Also, good luck on whoever is trying to find the handshake. Until then, I will be jamming on my Zune HD. Good luck.

---

### Post by pwnst*r on 2009-11-15
> **Frak said:**
> True that.

Also, good luck on whoever is trying to find the handshake. Until then, I will be jamming on my Zune HD. Good luck.

how you liking that HD, Frak?  i may pick one up before my trip Thanksgiving week.  pros, cons?

---

### Post by Frak on 2009-11-15
> **pwnst*r said:**
> how you liking that HD, Frak?  i may pick one up before my trip Thanksgiving week.  pros, cons?
Pros, it's awesome. Cons, it's awesome. In all seriousness:

Pros: Low power screen, great battery life, HD Radio (matters to me), WiFi, Web Browser, this cool tilt thing it does with the background, and Wireless Sync. Oh, and Microsoft has the best support I've ever used. If your Zune malfunctions somehow, they'll provide all the shipping materials and pay the cost of the repair round trip. No cost to you.

Iffy cons: You have to use Microsoft Points to buy music from the market, and it only syncs on Windows. They don't phase me any, since I have a 360 and I have many computers running Windows. In the end, nothing stops you from buying your music from Amazon.

Definite Cons: It's not a phone (I would toss my iPhone for this) and the App store is very young. I should be releasing my own games out soon enough.

EDIT
Pro: The app store isn't managed by idiots (looking at you, iPhone).

EDIT EDIT
Pro: Zune media center > EVERYTHING.

---

### Post by pwnst*r on 2009-11-16
> **Frak said:**
> Pros, it's awesome. Cons, it's awesome. In all seriousness:

Pros: Low power screen, great battery life, HD Radio (matters to me), WiFi, Web Browser, this cool tilt thing it does with the background, and Wireless Sync. Oh, and Microsoft has the best support I've ever used. If your Zune malfunctions somehow, they'll provide all the shipping materials and pay the cost of the repair round trip. No cost to you.

Iffy cons: You have to use Microsoft Points to buy music from the market, and it only syncs on Windows. They don't phase me any, since I have a 360 and I have many computers running Windows. In the end, nothing stops you from buying your music from Amazon.

Definite Cons: It's not a phone (I would toss my iPhone for this) and the App store is very young. I should be releasing my own games out soon enough.

EDIT
Pro: The app store isn't managed by idiots (looking at you, iPhone).

EDIT EDIT
Pro: Zune media center > EVERYTHING.

i hate you, because now i want one even more.  lol @ definite cons, because i too use an iphone and i mostly love it, but that zune HD is sex all around.  and, same as you, i have a 360 and all my pc's/laptops/tablet are dual boot.

audio quality? what headphones are you using?

---

### Post by pwnst*r on 2009-11-16
i just noticed too that there's no line out? :(  i know that the headphone jack on the iphone/ipods aren't as clean as the line out, so will scour the net to see if someone has done an SQ measurement between the two.

---

### Post by Frak on 2009-11-16
> **pwnst*r said:**
> i hate you, because now i want one even more.  lol @ definite cons, because i too use an iphone and i mostly love it, but that zune HD is sex all around.  and, same as you, i have a 360 and all my pc's/laptops/tablet are dual boot.

audio quality? what headphones are you using?
Good and I use [In-Ear Skullcandy]("http://www.skullcandy.com/shop/holua-black-green.html"). I, personally, think the audio quality has gotten better. My Zune 8 from yester-generation was worse against the iPod, but I think the HD has better quality than the iPod now.

---

### Post by pwnst*r on 2009-11-16
> **Frak said:**
> Good and I use [In-Ear Skullcandy]("http://www.skullcandy.com/shop/holua-black-green.html"). I, personally, think the audio quality has gotten better. My Zune 8 from yester-generation was worse against the iPod, but I think the HD has better quality than the iPod now.

cool, just making sure you're not using the stock headphones :D  thx for the other info man.

---

### Post by Frak on 2009-11-16
> **pwnst*r said:**
> cool, just making sure you're not using the stock headphones :D

Music is SERIOUS BUSINESS.

---

### Post by squidmaster on 2009-11-16
the zune media center is one of the nicest ones I've used. Very sexy! If only I had a zune I'd actually (somehow) use it. 

Wine?

---

### Post by pwnst*r on 2009-11-16
> **Frak said:**
> Music is SERIOUS BUSINESS.

agreed.

---

### Post by denago on 2009-11-16
Here's how I'd start trying to crack it.

[LIST=1]
[*]Start up [Snoopy](http://www.wingmanteam.com/usbsnoopy/)
[*]Plug in your zune
[*]Save the data snoopy collects
[*]find the handshake exchange and try to write your own program to repeat it and see what you get.
[/LIST]

Good luck if you're serious about cracking it, I'm sure it won't be an easy task...

---

### Post by Frak on 2009-11-16
> **denago said:**
> Here's how I'd start trying to crack it.

[LIST=1]
[*]Start up [Snoopy](http://www.wingmanteam.com/usbsnoopy/)
[*]Plug in your zune
[*]Save the data snoopy collects
[*]find the handshake exchange and try to write your own program to repeat it and see what you get.
[/LIST]

Good luck if you're serious about cracking it, I'm sure it won't be an easy task...
That wouldn't work since all the negotiation is done on the device, not the host. In pretty basic terms, it sends a "yes that was correct" or "no that was incorrect".

---

### Post by denago on 2009-11-18
> **Frak said:**
> That wouldn't work since all the negotiation is done on the device, not the host. In pretty basic terms, it sends a "yes that was correct" or "no that was incorrect".

The host still has to communicate with the device.  The device can't magically know that the correct program is trying to access it without the progam doing something to let it know that it is.

---

### Post by Frak on 2009-11-18
> **denago said:**
> The host still has to communicate with the device.  The device can't magically know that the correct program is trying to access it without the progam doing something to let it know that it is.
As stated above, and as far as I can understand, the device negotiates by the host sending an encrypted string to the device. The device doesn't care whether it's being accessed by Zune/XNA Studio/etc., it just cares that the correct handshake is sent to it.

---

### Post by denago on 2009-11-18
Doing a quick search it looks like the zune software sends a certificate to the zune, which in turn sends some data to the software.  So no, according to folks actively trying to crack it, it's not all performed "on the zune".

---

### Post by Frak on 2009-11-18
> **denago said:**
> Doing a quick search it looks like the zune software sends a certificate to the zune, which in turn sends some data to the software.  So no, according to folks actively trying to crack it, it's not all performed "on the zune".
Would you please link to these folks actively trying to crack it. I'm curious as to their current developments.

---

### Post by Tipped OuT on 2009-11-18
Isn't hacking illegal?

---

### Post by Rainstride on 2009-11-18
> **Tipped OuT said:**
> Isn't hacking illegal?

no. only if you are trying to get into a computer that's not yours.

---

### Post by Tipped OuT on 2009-11-18
> **Rainstride said:**
> no. only if you are trying to get into a computer that's not yours.

I would think hacking Mac OS X operating system to run on PC's would be illegal.

Correct me if I'm wrong please.

---

### Post by Frak on 2009-11-18
> **Tipped OuT said:**
> I would think hacking Mac OS X operating system to run on PC's would be illegal.

Correct me if I'm wrong please.
You would be correct.

---

### Post by PhoenixMaster00 on 2009-11-18
> **Frak said:**
> Pros, it's awesome. Cons, it's awesome. In all seriousness:

Pros: Low power screen, great battery life, HD Radio (matters to me), WiFi, Web Browser, this cool tilt thing it does with the background, and Wireless Sync. Oh, and Microsoft has the best support I've ever used. If your Zune malfunctions somehow, they'll provide all the shipping materials and pay the cost of the repair round trip. No cost to you.

Iffy cons: You have to use Microsoft Points to buy music from the market, and it only syncs on Windows. They don't phase me any, since I have a 360 and I have many computers running Windows. In the end, nothing stops you from buying your music from Amazon.

Definite Cons: It's not a phone (I would toss my iPhone for this) and the App store is very young. I should be releasing my own games out soon enough.

EDIT
Pro: The app store isn't managed by idiots (looking at you, iPhone).

EDIT EDIT
Pro: Zune media center > EVERYTHING.

I heard a reviewer say there were a few adverts on the Zune HD when you load some programs is that true and if so is it annoyin? 

Apart from that i would love to get it since it looks like a great device and i cant be bothered to wait for the Creative Zii

---

### Post by Frak on 2009-11-18
> **PhoenixMaster00 said:**
> I heard a reviewer say there were a few adverts on the Zune HD when you load some programs is that true and if so is it annoyin? 

Apart from that i would love to get it since it looks like a great device and i cant be bothered to wait for the Creative Zii
Some apps, yes, and pretty much every Microsoft game. I don't blame them, since the games were created by a 3rd party studio that wants brand recognition. You wait for a total of one or two seconds to watch a "Created by: Studio Name" go by the screen. During that time, the Zune HD is loading the program into RAM. I think weather does. I'm not sure because I haven't tried it.

---

### Post by PhoenixMaster00 on 2009-11-18
> **Frak said:**
> Some apps, yes, and pretty much every Microsoft game. I don't blame them, since the games were created by a 3rd party studio that wants brand recognition. You wait for a total of one or two seconds to watch a "Created by: Studio Name" go by the screen. During that time, the Zune HD is loading the program into RAM. I think weather does. I'm not sure because I haven't tried it.

Yeah its not the actual ads that would bother me i just dont want to have to be bombarded with them when all i want to do is play some music or quickly plays some games for a bit.

---

### Post by Frak on 2009-11-18
> **PhoenixMaster00 said:**
> Yeah its not the actual ads that would bother me i just dont want to have to be bombarded with them when all i want to do is play some music or quickly plays some games for a bit.
Yeah, you'll be fine.

---

### Post by pwnst*r on 2009-11-18
> **Rainstride said:**
> no. only if you are trying to get into a computer that's not yours.

wrong XD

---

### Post by atirox on 2009-11-19
Actually, hacking is legal. Its what you do with the knowledge you gain from hacking that isnt. There are generally three types of hackers. White hat, Grey hat, and Black hat. White hat hackers are the ones who share any knowledge gained for the betterment of others. Grey hat hackers are ones who may not share the knowledge with others, but dont use it to do something bad to others. Finally, you have the Black hat hackers. These are the ones who take the knowledge they learn, and use it for evil purposes that harm others. 

Thats hackers in a nutshell.

---

### Post by telly220 on 2009-12-11
Here are my thoughts on how to approach this:
I suspect that once the Zune gets the right "secret handshake" its file system becomes writeable. I have heard (unverified) that there is a workaround that involves starting up the Zune software and the terminating it after the Zune gives the "connected" screen. If this is true it would back up my suspicion. A good first step would be to use a USB packet sniffer to see whether the bytes sent between the Zune device and the host software are the same every time the Zune connects. Does each Zune have its own static key, or is a random string generated and then decrypted/encrypted or whatever back and forth until the device and host have verified each other? The answers to these questions will lay the groundwork for future efforts (and someone out there already knows).
 
I'm very interested to hear if anyone has made any progress on this or knows of any groups who are pursuing this seriously. 
 
I've got SnoopyPro, and know a little C/C++. I'm learning USB protocol and Linux-USB, but have a ways to go with that. I've captured the dialogue between host and device upon connection, but haven't gotten to the point where I can decode it. I don't have a lot of free time, but I'm going to work on this a little and I'm willing to share what I learn or work with anyone who is interested.

---

### Post by DeadSuperHero on 2009-12-11
Here's a thought: Zune has an app store. Why not write an app for the Zune that supports a different syncing protocol, like the open source MTP implementation or something? Then you'd bypass the encryption entirely. (in theory)

---

### Post by telly220 on 2009-12-11
Oh yeah, actually something like that had crossed my mind. I did write "hello world" for my Zune when I first got it, but I didn't want to go to the trouble of learning C# and the whole XNA framework so I never went anywhere with it. This might be a valid approach. Does anyone know if XNA supports writing to the whole Zune filesystem, or are there restrictions?

---

### Post by Frak on 2009-12-11
> **Mr. Psychopath said:**
> Here's a thought: Zune has an app store. Why not write an app for the Zune that supports a different syncing protocol, like the open source MTP implementation or something? Then you'd bypass the encryption entirely. (in theory)

> **telly220 said:**
> Oh yeah, actually something like that had crossed my mind. I did write "hello world" for my Zune when I first got it, but I didn't want to go to the trouble of learning C# and the whole XNA framework so I never went anywhere with it. This might be a valid approach. Does anyone know if XNA supports writing to the whole Zune filesystem, or are there restrictions?

Well, unfortunately, the Zune only allows Zune-to-Zune communications. Microsoft has effectively phased out any other way to connect remotely. The only way to make connections to the internet is to have your application be vetted by Microsoft. Only Microsoft has the ability to create applications that can connect remotely, such as the portable browser.

Microsoft foresaw people trying to bypass the Zune method of syncing.

Also, as for the second quote, I believe it gives you access to the registry to write temporary values, but not direct I/O access.

Soooo.... :(

---

### Post by sandyd on 2009-12-11
[http://www.zuneboards.com/forums/zune-hacks-mods/2772-zune-linux-progress-2.html](http://www.zuneboards.com/forums/zune-hacks-mods/2772-zune-linux-progress-2.html)

---

### Post by sandyd on 2009-12-11
> **Frak said:**
> Well, unfortunately, the Zune only allows Zune-to-Zune communications. Microsoft has effectively phased out any other way to connect remotely. The only way to make connections to the internet is to have your application be vetted by Microsoft. Only Microsoft has the ability to create applications that can connect remotely, such as the portable browser.

Microsoft foresaw people trying to bypass the Zune method of syncing.

Also, as for the second quote, I believe it gives you access to the registry to write temporary values, but not direct I/O access.

Soooo.... :(
if you hack the firmware, its possible.
but due to copyright/modification restrictions of the zune, im not obviously going to post this here.

---

### Post by Frak on 2009-12-11
> **carlee said:**
> if you hack the firmware, its possible.

I would say "Thank you captain obvious", but that would be rude. So I'll say this:

Thank you for the handy information :)

---

### Post by Gizenshya on 2009-12-11
I remember this post!

instead of managing with the firmware, how about basically writing another OS for it?

or hacking out the problematic handshake components?

or would those be catch 22's...?

is there a firmware update program for linux?

---

### Post by sandyd on 2009-12-11
> **Gizenshya said:**
> I remember this post!

instead of managing with the firmware, how about basically writing another OS for it?

or hacking out the problematic handshake components?

or would those be catch 22's...?

is there a firmware update program for linux?
go on and have a try downloasd one of these and get started ;)
[http://www.zuneboards.com/forums/firmware-downloads-163/](http://www.zuneboards.com/forums/firmware-downloads-163/)

---

### Post by phrostbyte on 2009-12-12
If someone is willing to donate a Zune to me, I might be able to enable it's use on Linux. I have some experience with that sort of thing. No guarantees though, sorry. :)

---

### Post by telmac on 2009-12-12
I'm really not good with this stuff, but why don't you try syncing it, then copying the sogs into that folder. I really what I just said may be really n00bish. Sorry if it is.

---

### Post by Frak on 2009-12-12
> **phrostbyte said:**
> If someone is willing to donate a Zune to me, I might be able to enable it's use on Linux. I have some experience with that sort of thing. No guarantees though, sorry. :)
I can only get it working through disabling the firmware handshake. I'm not sure how to crack the firmware handshake.

---

### Post by Chronon on 2009-12-12
> **Gizenshya said:**
> I remember this post!

instead of managing with the firmware, how about basically writing another OS for it?

or hacking out the problematic handshake components?

or would those be catch 22's...?

is there a firmware update program for linux?

The replacement OS needs to be digitally signed so that the processor accepts it.  The signature check is implemented in the Freescale processor, I believe, so I don't see a way around it.

---

### Post by lashepherd on 2010-01-27
Has there been any progress on the effort?  I sure hope so.  Thanks.

---

### Post by oiler920 on 2010-01-31
No progress, unfortunately. Despite the outcry of new Zune HD users, no one [who is capable of doing so] is willing to try and crack MTPZ, the Zune's proprietary MTP authentication extension. As far as I know.

---

### Post by ad_267 on 2010-01-31
Or we could stop purchasing products that we know don't work well with Linux, from companies who don't care about interoperability and standards.

---

### Post by lashepherd on 2010-02-16
> **ad_267 said:**
> Or we could stop purchasing products that we know don't work well with Linux, from companies who don't care about interoperability and standards.

That's a novel approach and one I plan on trying _when_ my Zune craps out on me.

Now, if I could only find a way to take the Zune music with me to my nonproprietary player. :P

---

### Post by gymophett on 2010-02-16
> **lashepherd said:**
> That's a novel approach and one I plan on trying _when_ my Zune craps out on me.

Now, if I could only find a way to take the Zune music with me to my nonproprietary player. :P

My Zune got stolen, and I'm glad. Now I have an excuse to get one that works in Linux natively.

---

### Post by Chronon on 2010-02-16
> **oiler920 said:**
> No progress, unfortunately. Despite the outcry of new Zune HD users, no one [who is capable of doing so] is willing to try and crack MTPZ, the Zune's proprietary MTP authentication extension. As far as I know.

MTP is just a transfer protocol.  MTPZ is just an extension of that with DRM.  This has more to do with DRM applied to files transferred via the Zune's WiFi (or USB possibly) than with the signature check which prevents 3rd party code from being executed.

---

### Post by phrostbyte on 2010-02-16
> **gymophett said:**
> My Zune got stolen, and I'm glad. Now I have an excuse to get one that works in Linux natively.

I have a $10 Sandisk player I've had for years that works brilliantly with Linux, easy to recharge and use, with built in FM also. I also have an iPod Touch somewhere hasn't been touched in nearly a year. :)

---

### Post by Chronon on 2010-04-19
The thread is old, but deserves to be bumped because apparently some folks have found a way through.
[http://www.zuneboards.com/?p=vB50442](http://www.zuneboards.com/?p=vB50442)
[http://zunedevwiki.org/wiki/getting_started/developer/start](http://zunedevwiki.org/wiki/getting_started/developer/start)

Now that they are able to execute 3rd party code, this opens the door to homebrew applications as well as complete replacement firmwares (Rockbox anyone?).

---

### Post by ctrlmd on 2010-04-19
i thought this could help maybe 
[http://www.neowin.net/news/zunes-hacked-opened-for-homebrew-development](http://www.neowin.net/news/zunes-hacked-opened-for-homebrew-development)

---

### Post by Letrazzrot on 2010-04-19
About a week ago I would have been interested in these latest developments.  I may even have had the motivation to look into that new SDK.  Alas, my Zune software decided to stop working suddenly on my XP machine (which I hardly ever use).  To add insult to injury, hooking up the Zune to the computer while trying to open the software mysteriously deleted every single track of music off the player, with no warning or noticeable reason.

So I threw it in the trash (I know, probably a little extreme), and bought a Sandisk.  Working good so far, and can use with Linux directly.

Of course, other user experiences may vary...

---

### Post by tgalati4 on 2010-04-19
Do they still make them in brown?

---

### Post by Frak on 2010-04-19
> **tgalati4 said:**
> Do they still make them in brown?
Haven't for a long time.

---

### Post by tgalati4 on 2010-04-20
Which was the last time I looked at a Zune.

Why would anyone want to lock themselves into such a closed system?

---

