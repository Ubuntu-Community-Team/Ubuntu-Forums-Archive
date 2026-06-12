---
title: "Networking and being anonymous"
date: 2009-09-27
forum: The Cafe
---

### Post by dhughes on 2009-09-27
OK here's the scoop I'm having a "discussion", we'll say, with someone and I say being 100% anonymous on the Internet is next to impossible, not totally impossible but difficult. That person may even be reading this post who knows.

 There's always a physical path back to you, your system's hardware is unique and can be identified unless you go out of your way to hide that but even then it's not guaranteed you'll fool everyone along the many servers your data flows through.

 I'm sure I could use a LiveCD, spoof my MAC address, use a coffee shop wifi router from outside the coffee shop to avoid any security cameras but there's always a chance you'll be seen and caught.

 I'm not doing this looking for tips I'm just asking opinions if you think it's easy to hide on the Internet/Web without going out of your way to disguise the path back to you.

---

### Post by Mathiasdm on 2009-09-27
> **dhughes said:**
> OK here's the scoop I'm having a "discussion", we'll say, with someone and I say being 100% anonymous on the Internet is next to impossible, not totally impossible but difficult. That person may even be reading this post who knows.

 There's always a physical path back to you, your system's hardware is unique and can be identified unless you go out of your way to hide that but even then it's not guaranteed you'll fool everyone along the many servers your data flows through.

 I'm sure I could use a LiveCD, spoof my MAC address, use a coffee shop wifi router from outside the coffee shop to avoid any security cameras but there's always a chance you'll be seen and caught.

 I'm not doing this looking for tips I'm just asking opinions if you think it's easy to hide on the Internet/Web without going out of your way to disguise the path back to you.
Yes, it's (relatively) easy to hide on the internet. Use something like Tor or I2P :) It would be extremely difficult to trace communications back to you then.

---

### Post by toupeiro on 2009-09-27
There's only one problem with i2p and tor.  They only protect you from the outside in, but your ISP providing your local connection can identify you at a packet level if they really wanted to.  Don't fool yourself,  If someone really wanted to find you, they could.  One way, for example, is your network history is cached on your machine, and even something as simple as a DHCP handshake on a new network could reveal say .. what DNS servers you were using prior to the network session you are on now, which if they were your home ISP's DNS servers, they've closed in and will be knocking on your doors in days, or your ISP has already turned over the enough information to warrant them sitting on your couch when you get home from that coffee shop.  I'm not saying your local starbucks or your ISP **is** snooping at this level, but I am saying they could.

My advice, People aren't going to waste their time looking for you if you aren't doing anything warranting the effort, so the less you convince yourself (or whomever else) that you know about every way to hide, the safer you will be because you probably won't do stupid things if you think you're going to get caught. ;)

---

### Post by pwnst*r on 2009-09-27
tor, although it helps you to be anonymous, you wind up giving up some security.

---

### Post by misfitpierce on 2009-09-27
I think you can try but no matter what if somehow connected to the net you can always be traced by someone with lots of experience or computer skills. You can try and conceal yourself very very well with the right tools and stuff but at some point I believe you can always be traced.

---

### Post by collinp on 2009-09-27
There is no such thing as "Privacy" or "Anonymous" on the Internet.

---

### Post by pwnst*r on 2009-09-27
lol i'd like to know who clicked the first option in the poll.

---

### Post by LookTJ on 2009-09-27
Hmmm....VPN?

EDIT Also, voted "*Difficult, but with experience/planning, yes anonymous"*

---

### Post by pwnst*r on 2009-09-27
_lol

---

### Post by nubimax on 2009-09-27
the only way that I can think of is to buy a used laptop cheap go to a puplic park here in Mexico (most have free wifi) do your dirty business Then ditch the laptop after aclean wipe.
M

---

### Post by Mathiasdm on 2009-09-28
> **toupeiro said:**
> There's only one problem with i2p and tor.  They only protect you from the outside in, but your ISP providing your local connection can identify you at a packet level if they really wanted to.
What exactly are you saying here? I assume with 'identify you at a packet level', you mean you can check what the packets look like and see that you're running Tor or I2P. That's correct. Still, that's not a problem, they still can't see the content of the packet. If one of the next hops in the network is a busy node forwarding to hundreds of other nodes at the same time, it's easy to lose track there :) 

> **toupeiro said:**
> Don't fool yourself,  If someone really wanted to find you, they could.
Probably, yes.
1. If an adversary is powerful enough, they could go around and gather enough information.
2. If you make a stupid mistake revealing your identity, it's game over as well.

> **toupeiro said:**
> One way, for example, is your network history is cached on your machine, and even something as simple as a DHCP handshake on a new network could reveal say .. what DNS servers you were using prior to the network session you are on now, which if they were your home ISP's DNS servers, they've closed in and will be knocking on your doors in days, or your ISP has already turned over the enough information to warrant them sitting on your couch when you get home from that coffee shop.  I'm not saying your local starbucks or your ISP **is** snooping at this level, but I am saying they could.
Everything that's stored on your computer can be hidden by encrypting your hard drive.
If you sent all your sensitive information through Tor or I2P, they won't be closing in on you at all through the DNS servers you're using (all your DNS requests will be sent through the anonymous network).

> **toupeiro said:**
> My advice, People aren't going to waste their time looking for you if you aren't doing anything warranting the effort, so the less you convince yourself (or whomever else) that you know about every way to hide, the safer you will be because you probably won't do stupid things if you think you're going to get caught. ;)
This might be true to some degree, but it's still good to know that it's possible to be anonymous if you want to be (and since I'm talking about running an anonymous network and encrypting your hard drive, it's probably pretty clear that it's not all that easy).

---

### Post by toupeiro on 2009-09-28
> **Mathiasdm said:**
> What exactly are you saying here? I assume with 'identify you at a packet level', you mean you can check what the packets look like and see that you're running Tor or I2P. That's correct. Still, that's not a problem, they still can't see the content of the packet. If one of the next hops in the network is a busy node forwarding to hundreds of other nodes at the same time, it's easy to lose track there :) 

Your packet has a header.  headers can be learned, trended, and eventually identified.  It's not rocket science, its networking.  To your ISP, you're basically on a port, which can be subject to monitoring, QoS, or anything else they want to do based on what they trend. Hell, if I wanted to, I could spend a few hundred buck on a used 5-6 year old Fluke LanMeter and get full layer-7 information on just about anything I could want on a given network I had access to.  To you, I could just be they guy having coffee in the coffee shop next to you and you wouldn't know any better.  



> 
Everything that's stored on your computer can be hidden by encrypting your hard drive.
If you sent all your sensitive information through Tor or I2P, they won't be closing in on you at all through the DNS servers you're using (all your DNS requests will be sent through the anonymous network).

They don't care about your hard drive, or what new DNS server you might be using.  They care about what your OS and Network stack is going to do based on how its configured to participate on your network.  Your IP lease, and all relavent information (including DNS) is going to be rechecked and activated, or released and renewed on your new network...  The first two to three octets of your cached ISP's DNS server can tell me your Country, City, State/Province and Internet Provider.  How much longer do you really think it would take for someone really looking for you to find you?  Say they've already trended your traffic, your upstream partners traffic (which you have no idea whats being sniffed on that end) and with that, they know all they need to know without ever scanning your drive to pick you up from home or work, take all of your toys away, have probable cause to search and inventory (busted) and depending on how much they've gathered, and for how long, prosecute you with enough evidence to stick.

> 
This might be true to some degree, but it's still good to know that it's possible to be anonymous if you want to be (and since I'm talking about running an anonymous network and encrypting your hard drive, it's probably pretty clear that it's not all that easy).

Encrypting hard drives are only relevant if I actually physically steal your hard disk or entire machine.  It's called TPM.  If your hardware environment becomes altered in any way, or your OS associated with TPM/Bitlocked encryption becomes bypassed, I cannot boot your disk, nor can I access it with any sort of live CD or additional hard drive in any way without decrypting it using a very long string.  What goes over a network port while your OS is properly booted has nothing to do with your drive being encrypted.  But you knew that already, just like you know you're **completely** anonymous.  Have a ball, baby! :guitar:

---

### Post by PaulReaver on 2009-09-28
of course you can be traced. its not just ip addresses though.
a lot of what has been posted on forums can be usefull for tracking too.

your in canada for example.

---

### Post by Bodsda on 2009-09-28
> **PaulReaver said:**
> of course you can be traced. its not just ip addresses though.
a lot of what has been posted on forums can be usefull for tracking too.

your in canada for example.

Whilst its probably true, it is hardly a definitive way of finding where someone lives. For example, whoever is trying to find me by looking at my location on my forum profile will realize that they are very very close to finding me, but am I actually there?

---

### Post by Mathiasdm on 2009-09-28
> **toupeiro said:**
> Your packet has a header.  headers can be learned, trended, and eventually identified.  It's not rocket science, its networking.  To your ISP, you're basically on a port, which can be subject to monitoring, QoS, or anything else they want to do based on what they trend.
Yes, I know that... Like said, that's still not useful to them if you use an anonymous network (edit: it does have some use, to find out if you're running Tor, and to find out about the first hop. Still, that's limited.).




> **toupeiro said:**
> They don't care about your hard drive, or what new DNS server you might be using.  They care about what your OS and Network stack is going to do based on how its configured to participate on your network.  the first two to three octets of your cached ISP's DNS server can tell me your Country, City, State/Province and Internet Provider.  How much longer do you really think it would take for someone really looking for you to find you?  Say they've already trended your traffic, your upstream partners traffic (which you have no idea whats being sniffed on that end) and they know all they need to know without ever scanning your drive to pick you up from home or work, take all of your toys away, and depending on how much they've gathered, for how long, prosecute you with enough evidence to stick.
Please find out more about anonymous networks, then come back to post.



> Encrypting hard drives are only relevant if I actually physically steal your hard disk or entire machine.  It's called TPM.  If your hardware environment becomes altered in any way, or your OS associated with TPM/Bitlocked encryption becomes bypassed, I cannot boot your disk, nor can I access it with any sort of live CD or additional hard drive in any way without decrypting it using a very long string.  What goes over a network port while your OS is properly booted has nothing to do with your drive being encrypted.  But you knew that already, just like you know you're **completely** anonymous.  Have a ball, baby! :guitar:
:roll:
Perfect anonymity doesn't exist, but I am still saying it's possible to protect yourself well enough.

---

### Post by PaulReaver on 2009-09-28
> **Bodsda said:**
> Whilst its probably true, it is hardly a definitive way of finding where someone lives. For example, whoever is trying to find me by looking at my location on my forum profile will realize that they are very very close to finding me, but am I actually there?

of course.
your right behind me
look.

---

### Post by starcannon on 2009-09-28
The only thing allowing anyone any level of "anonymity" is time and money. If you are not high enough profile to spend the time and money tracking down, then, with exception to "just for the lulz", no one is going to bother wasting resources on you. Don't hang out in the truly back alley dark corners of the interwebs, or start flirting with minors, and you'll likely never even be a blip on the radar screen of anyone that matters. As far as privacy goes, well, pft, thats an illusion anyway, cover up if you feel a need, but your wife already knows.

---

### Post by toupeiro on 2009-09-28
> Please find out more about anonymous networks, then come back to post.

Please, learn a little more about networking, hopefully before you get arrested for doing something dumb thinking you're anonymous, and save yourself the money.  You can thank me later for the post.



> 
:roll:
Perfect anonymity doesn't exist, but I am still saying it's possible to protect yourself well enough.

Drive encryption != anonymity.  If I wanted your Identity or to find out what you're doing, there are better ways to do it then stealing your Dell.  But by all means, if you really think Tor will protect you,  have a ball!  Maybe you'll get slashdotted. ;)

---

### Post by PaulReaver on 2009-09-28
yes but all you need to trace someone would be a full name and area of birth. 

still using vmware?

---

### Post by Mathiasdm on 2009-09-28
> **toupeiro said:**
> Please, learn a little more about networking, hopefully before you get arrested for doing something dumb thinking you're anonymous, and save yourself the money.  You can thank me later for the post.
1. I talked about 'learning about anonymous networks', because you seem to think your ISP can simply look at your traffic and find out who you're communicating with. In circumstances without anonymous networks, that's true. However, we're not talking about those circumstances now...
2. I know quite a bit about networking, but thanks for the suggestion.
3. I don't intend to do anything illegal. I find anonymity networks interesting as a research topic and as a concept (the idea of anonymity in case one needs it).

> **toupeiro said:**
> Drive encryption != anonymity.  If I wanted your Identity, there are better ways to get it then stealing your Dell.
Which is why I am talking about combining things? Of course encryption != anonymity. It can provide security (by stopping people from accessing data), but not anonymity.

---

### Post by toupeiro on 2009-09-28
> **Mathiasdm said:**
> 1. I talked about 'learning about anonymous networks', because you seem to think your ISP can simply look at your traffic and find out who you're communicating with. In circumstances without anonymous networks, that's true. However, we're not talking about those circumstances now...
2. I know quite a bit about networking, but thanks for the suggestion.
3. I don't intend to do anything illegal. I find anonymity networks interesting as a research topic and as a concept (the idea of anonymity in case one needs it).

I understand its probably late where you are at, so you may be misinterpreting what your reading.  What I am saying here is if your transmitting and receiving over an anonymous network, your ISP is going to know about it, not necessarily exactly what you are transmitting and receiving.  However, If your ISP is doing behavioural trends on its traffic by some agency's request directly, indirectly related, or completely unrelated to you, and monitors how many mb/month of your traffic has been logged while using tor, depending on the circumstances thats enough to warrant probable cause to do further inquiries and take further actions on their own behalf, or whatever agency may have approached them.  If you're doing some malicious, and think you have to be caught in the act to be prosecuted, you're in for a rude awakening.  You said you're not.  I dont care if you are or not, but do what you want. :)

---

### Post by Mathiasdm on 2009-09-28
> **toupeiro said:**
> I understand its probably late where you are at, so you may be misinterpreting what your reading.  What I am saying here is if your transmitting and receiving over an anonymous network, your ISP is going to know about it, not necessarily exactly what you are transmitting and receiving.
That's what I was saying? Okay, maybe we were having a misunderstanding :) 

> **toupeiro said:**
> However, If your ISP is doing behavioural trends on its traffic by some agency's request directly, indirectly related, or completely unrelated to you, and monitors how many mb/month of your traffic has been logged while using tor, depending on the circumstances thats enough to warrant probable cause to do further inquiries and take further actions on their own behalf, or whatever agency may have approached them. If you're doing some malicious, and think you have to be caught in the act to be prosecuted, you're in for a rude awakening.
I agree with that entirely, perhaps the difference is that I was mostly thinking about the 'finding out purely online' cases. You are correct in that an agency will simply continue other actions on their own (though Tor does have a lot of users. Merely using Tor is probably not enough to attract attention.)

> **toupeiro said:**
> You said you're not.  I dont care if you are or not, but do what you want. :)
Of course. You can't trust what someone says online ;-)

---

### Post by eragon100 on 2009-09-28
> **nubimax said:**
> the only way that I can think of is to buy a used laptop cheap go to a puplic park here in Mexico (most have free wifi) do your dirty business Then ditch the laptop after aclean wipe.
M

That would probably work, especially if you use the shred command on the harddrive before ditching it. Nobody, in decades, has been able to retrieve even one byte of data from a "shredded" hard disk drive, and it's a one-line command :guitar:

---

### Post by doas777 on 2009-09-28
it really depends on what you do. no one is going to take tor appart to try to find you for downloading some song that Lily Allen stole first, but they would if you happened to have emailed yourself the norad firing codes. 

theres also an element of luck. you get caught on quite a few cameras daily. how many of them do you think will have the time you were exposed reviewed? is there a guy in the back room looking at just the right monitor at just the right time? 

so I'll say 50/50.

I really wish I2P would take off.

---

### Post by Firestem4 on 2009-09-28
I accidentally voted for "Never Anonymous..." While it is difficult, if you KNOW what you are doing you can become completely anonymous. But it takes specific circumstances...No audit trail (pay for laptop with cash) take it to a public net. Never load any of your files on it...etc etc, do your dirty deed and then dump the laptop.

But if you continually use the same machine(s), even in different locations you will not be completely anonymous.

---

### Post by Firestem4 on 2009-09-28
> **eragon100 said:**
> That would probably work, especially if you use the shred command on the harddrive before ditching it. Nobody, in decades, has been able to retrieve even one byte of data from a "shredded" hard disk drive, and it's a one-line command :guitar:

Also while this may be true it is important to quote to the Shred man page.

> CAUTION: Note that shred relies on a very important assumption: that the file system over&#8208;writes data in place.  This is the traditional way to do things, but many modern file system designs do not satisfy this assumption.  The following are examples of file systems on which shred is not effective, or is not guaranteed to be  effective  in  all  file  system modes: ...


---

### Post by toupeiro on 2009-09-28
> **Mathiasdm said:**
> 

Of course. You can't trust what someone says online ;-)

Sure you can.  Watch.  Give me ssh access to your machine and I'll make it uber secure for you. ;)

---

### Post by Mathiasdm on 2009-09-29
> **toupeiro said:**
> Sure you can.  Watch.  Give me ssh access to your machine and I'll make it uber secure for you. ;)
:lolflag:

---

### Post by markbuntu on 2009-09-29
It is not so difficult to be anonymous and secure, you just can't be doing it from your home.

You can carry your OS on a usb stick, totally encrypted, and no memory of what it did before and you can boot it up on just about any machine. You can use a throw away cell phone to connect it to the internet.

Open wireless sites are abundant and it is easy to fake mac addresses and tor has layers of encryption that hide ip forwarding and pgp can make it very very difficult to crack message content.

Only people who really really are after you would even attempt to track you through all that.

---

### Post by eragon100 on 2009-09-30
> **markbuntu said:**
> It is not so difficult to be anonymous and secure, you just can't be doing it from your home.

You can carry your OS on a usb stick, totally encrypted, and no memory of what it did before and you can boot it up on just about any machine. You can use a throw away cell phone to connect it to the internet.

Open wireless sites are abundant and it is easy to fake mac addresses and tor has layers of encryption that hide ip forwarding and pgp can make it very very difficult to crack message content.

Only people who really really are after you would even attempt to track you through all that.

People who are really, really after you are what we are talking about here, right? Also, keep in mind that the location of mobile phones can be tracked, even if they are off. So, they would at what place you were doing your dirty stuff and at wath time, if they can get a video camera recording for that place and time, you are screwed. So don't use a cellphone :wink:

---

### Post by pwnst*r on 2009-09-30
> **eragon100 said:**
> People who are really, really after you are what we are talking about here, right? Also, keep in mind that the location of mobile phones can be tracked, even if they are off. So, they would at what place you were doing your dirty stuff and at wath time, if they can get a video camera recording for that place and time, you are screwed. So don't use a cellphone :wink:

how are they tracked when they're off?  are they emitting low power signals anyway?  then just remove the battery.

---

### Post by samjh on 2009-09-30
Mobile phones can't be tracked if it's switched off.  The idea about unpowered mobile phones being trackable is CSI television nonsense.  The only exceptional case is a mobile phone with RFID, which is trackable when near an appropriate reader.

Complete permanent anonymity is merely an abstract concept for most people.  For 99% of the population, it's just not feasible to live completely off the grid for prolonged periods of time (eg. over a year).

---

### Post by Khufucius on 2009-11-04
> **eragon100 said:**
> That would probably work, especially if you use the shred command on the harddrive before ditching it. Nobody, in decades, has been able to retrieve even one byte of data from a "shredded" hard disk drive, and it's a one-line command :guitar:

Beware - (some output copied from "$man shred" follows)

"
 CAUTION:  Note  that  shred relies on a very important assumption: that
       the file system overwrites data in place.  This is the traditional  way
       to  do  things, but many modern file system designs do not satisfy this
       assumption.  The following are examples of file systems on which  shred
       is not effective, or is not guaranteed to be effective in all file sys&#8208;
       tem modes:

       * log-structured or journaled file systems, such as those supplied with
       AIX and Solaris (and JFS, ReiserFS, XFS, Ext3, etc.)

       *  file  systems  that  write  redundant data and carry on even if some
       writes fail, such as RAID-based file systems

       * file systems that make snapshots, such  as  Network  Appliance&#8217;s  NFS
       server

       * file systems that cache in temporary locations, such as NFS version 3
       clients

     * compressed file systems

       In the case of ext3 file systems, the  above  disclaimer  applies  (and
       shred  is  thus  of  limited  effectiveness) only in data=journal mode,
       which journals file data in addition to just  metadata.   In  both  the
       data=ordered  (default) and data=writeback modes, shred works as usual.
       Ext3 journaling modes can  be  changed  by  adding  the  data=something
       option  to  the  mount  options  for  a  particular  file system in the
       /etc/fstab file, as documented in the mount man page (man mount).

       In addition, file system backups and remote mirrors may contain  copies
       of the file that cannot be removed, and that will allow a shredded file
       to be recovered later.
"

Just wanted to point that out.

-Khufucius

---

### Post by NCLI on 2009-11-04
How about using OpenDNS along with an encrypted tunnel to a VPN?

---

### Post by t0p on 2009-11-05
> **Khufucius said:**
> Beware - (some output copied from "$man shred" follows)

"
 CAUTION:  Note  that  shred relies on a very important assumption: that
       the file system overwrites data in place.  This is the traditional  way
       to  do  things, but many modern file system designs do not satisfy this
       assumption.  The following are examples of file systems on which  shred
       is not effective, or is not guaranteed to be effective in all file sys&#8208;
       tem modes:

       * log-structured or journaled file systems, such as those supplied with
       AIX and Solaris (and JFS, ReiserFS, XFS, Ext3, etc.)

       *  file  systems  that  write  redundant data and carry on even if some
       writes fail, such as RAID-based file systems

       * file systems that make snapshots, such  as  Network  Appliance’s  NFS
       server

       * file systems that cache in temporary locations, such as NFS version 3
       clients

     * compressed file systems

       In the case of ext3 file systems, the  above  disclaimer  applies  (and
       shred  is  thus  of  limited  effectiveness) only in data=journal mode,
       which journals file data in addition to just  metadata.   In  both  the
       data=ordered  (default) and data=writeback modes, shred works as usual.
       Ext3 journaling modes can  be  changed  by  adding  the  data=something
       option  to  the  mount  options  for  a  particular  file system in the
       /etc/fstab file, as documented in the mount man page (man mount).

       In addition, file system backups and remote mirrors may contain  copies
       of the file that cannot be removed, and that will allow a shredded file
       to be recovered later.
"

Just wanted to point that out.

-Khufucius

Just cut-and-pasting mindlessly from man pages proves nothing but mindlessness.

In the days when ext3 was the norm in ubuntu, the important part of the above was:

> In the case of ext3 file systems, the  above  disclaimer  applies  (and
       shred  is  thus  of  limited  effectiveness) only in data=journal mode,
       which journals file data in addition to just  metadata.   In  both  the
       data=ordered  (default) and data=writeback modes, shred works as usual.

ie, default file system worked with shred just fine.

Now the default is ext4, we need a new man page.

---

### Post by sim-value on 2009-11-05
In real Life we are never Anonymous so why the hell do people Expect this from the Internet ?

Do you always go shopping when there is nobody in the Stores so no one will know what u are buying ?

---

### Post by t0p on 2009-11-05
> **sim-value said:**
> In real Life we are never Anonymous so why the hell do people Expect this from the Internet ?

Do you always go shopping when there is nobody in the Stores so no one will know what u are buying ?

No silly!  I don't mind if people know what I'm buying.

I always go to a store I've never used before, wearing a false moustache, and pay in cash.  I find that's sufficient.  :p

---

### Post by kpholmes on 2009-11-05
what about axxo? 
[http://en.wikipedia.org/wiki/AXXo](http://en.wikipedia.org/wiki/AXXo)


i mean, the studios were going mad about his rips, and you bet they were shovelling **TONS** of money and manpower to find out who this person was.

no one knows if its a guy or girl, young or old, if thats not anonymous, then enough then i dont know what is.

---

### Post by afeasfaerw23231233 on 2009-11-05
It seems that my ISP imposes a transparent proxy to its client.

---

### Post by hobo14 on 2009-11-05
> **Hellow said:**
> There is no such thing as "Privacy" or "Anonymous" on the Internet.

Depends who's looking.  Who am I?  
You don't have authority to force my ISP to hand over data on me, so as far as you're concerned, until I log in here, I become anonymous every time my IP address changes.

It's not easy, it would take effort, but it certainly is possible to be totally and 100% anonymous online.
I'd recommend a bit of wardriving, until you find a network to piggyback on, rather than a coffee shop.


> **sim-value said:**
> Do you always go shopping when there is nobody in the Stores so no one will know what u are buying ?
No, but if I don't see anyone I know, or use a credit card, I'm shopping anonymously. 
Do you present your ID when you walk into a shop?  Would you present it if a shop asked you to?

---

### Post by postaldude on 2009-11-05
100% anonymous? Not a chance. Whatever you do to encrypt or divert your traffic, your IP address is still a necessary component of the packet, which has to be unencrypted, to get the data back to your machine. You can go through as many proxies as you like, but the data, as far as your ISP is concerned, is still there. If someone really wanted to, and had the time, they could trace your activity on the net, get the IP, and the ISP could tell them who it was.
Thankfully, mostly, they don't seem to, unless there's a court order (at least the ones I've heard of), so the chances are fairly low. But it's still possible.

---

### Post by PatrickBoyle on 2009-11-05
99% anonymity can be obtained fairly easily with a moderate knowledge of TCP/IP, and not using an internet connection that is linked to you.

I say 99% in the sense that there is always a risk you will screw up, or that you happen to do something serious enough that the government will funnel enough time, money, and resources into finding you. Even then chances are slim you will be discovered.

This isn't something new. Many many people on the internet do things regularly that would land them in jail for a very long time. A lot of people have huge organizations with a LOT of funding (read: RIAA/MPAA) going after them, and they've managed to stay anonymous for years.

---

### Post by Bezmotivnik on 2009-11-05
> **toupeiro said:**
> But by all means, if you really think Tor will protect you,  have a ball!  
I still don't see how you can crack my content/activity if I'm using Tor.

That I am online (assuming I'm not wardriving with a spoofed MAC) and accessing a Tor server, yes, the ISP network may see that, but I don't see how you can possibly have any more information than that as all traffic is encrypted/reencrypted between nodes in the Tor network.

As I understand it, the only (theoretical) vulnerability with Tor is *traffic analysis at both ends*, which would be impossible for the ISP in the large majority of cases.

---

### Post by Bezmotivnik on 2009-11-05
> **postaldude said:**
> 100% anonymous? Not a chance. Whatever you do to encrypt or divert your traffic, your IP address is still a necessary component of the packet, which has to be unencrypted, to get the data back to your machine. 
Yes, but only at the original Tor node you're accessing.

It sounds to me like in this discussion...

1:  People are using "anonymous" in different senses and

2:  They don't understand how Tor works.

---

### Post by t.rei on 2009-11-05
I wonder how anyone should vote for being anonymous, jet posting in a public forum. Thats just... slacking unless it's a "trowaway" and still...

---

### Post by edin9 on 2009-11-05
> **Mathiasdm said:**
> Yes, it's (relatively) easy to hide on the internet. Use something like Tor or I2P :) It would be extremely difficult to trace communications back to you then.

Tor is easy to track. If you use a private backnet it is much harder to trace.

---

### Post by Bezmotivnik on 2009-11-05
> **edin9 said:**
> Tor is easy to track. 
How?

---

### Post by edin9 on 2009-11-05
> **Bezmotivnik said:**
> How?

Both end analysis, cookie scanning, user agent information, statiscal analysis of behaviour, logger cookies, DPI combined with some of these other things. All sorts of ways.

---

### Post by t0p on 2009-11-05
> **postaldude said:**
> 100% anonymous? Not a chance. Whatever you do to encrypt or divert your traffic, your IP address is still a necessary component of the packet, which has to be unencrypted, to get the data back to your machine. You can go through as many proxies as you like, but the data, as far as your ISP is concerned, is still there. If someone really wanted to, and had the time, they could trace your activity on the net, get the IP, and the ISP could tell them who it was.
Thankfully, mostly, they don't seem to, unless there's a court order (at least the ones I've heard of), so the chances are fairly low. But it's still possible.

Let's say you've got a bunch of 3G phones or USB dongle-modems, unlocked for any network, and a bunch of sim cards. All on pay as you go so no ID needed to buy them.  You use the phone or dongle-modems, swapping devices and sim cards frequently, which changes your ISP and the "identity" with which they can associate any IP address you might be using at any moment, and which also makes behaviour profiling impossible.  You move location frequently, so it's impossible to associate any traffic with any static location.  

That's anonymity.

---

### Post by doas777 on 2009-11-05
> **t0p said:**
> Let's say I've got a bunch of 3G phones or USB dongle-modems, unlocked for any network, and a bunch of sim cards. All on pay as you go so no ID needed to buy them.  You use the phone or dongle-modems, swapping devices and sim cards frequently.  You move location frequently.

That's anonymity.

best idea thus far, but highly impractical.

---

### Post by t0p on 2009-11-05
> **doas777 said:**
> best idea thus far, but highly impractical.

I dispute that.  It isn't "highly impractical".  Sure it's not *easy*.  But if you really need true anonymity, you'll be prepared to do something difficult.  The option I voted for in the poll was "Difficult, but with experience/planning, yes anonymous".  I think my proposal fits that description.

---

### Post by edin9 on 2009-11-05
> **t0p said:**
> Let's say you've got a bunch of 3G phones or USB dongle-modems, unlocked for any network, and a bunch of sim cards. All on pay as you go so no ID needed to buy them.  You use the phone or dongle-modems, swapping devices and sim cards frequently, which changes your ISP and the &quot;identity&quot; with which they can associate any IP address you might be using at any moment, and which also makes behaviour profiling impossible.  You move location frequently, so it's impossible to associate any traffic with any static location.  

That's anonymity.

And use APS over a private network.

---

### Post by Bezmotivnik on 2009-11-05
> **edin9 said:**
> Both end analysis, cookie scanning, user agent information, statiscal analysis of behaviour, logger cookies, DPI combined with some of these other things. All sorts of ways.
Most of these don't apply, and the ones that do certainly aren't "easy" by any stretch of the imagination.

Java/Cookies are (normally) disabled by both a sophisticated user and Privoxy, traffic analysis in a normally active Tor net is virtually impossible and who has real-time access to "both ends" of the entire Internet in the real world?  

Unless you can do real-time decryption of them, all you can trace is undifferentiated encrypted packets in a single hop between two nodes in a very busy Tor net.  

The only "easy" way to do this is to compromise the actual machines identified by tracking their IPs in their initial hookups with the Tor net, not Tor itself.

---

### Post by doas777 on 2009-11-05
> **t0p said:**
> I dispute that.  It isn't "highly impractical".  Sure it's not *easy*.  But if you really need true anonymity, you'll be prepared to do something difficult.  The option I voted for in the poll was "Difficult, but with experience/planning, yes anonymous".  I think my proposal fits that description.


fair enough. would you settle for a little impractical then?

if I have to leave my home to keep mediasentry guessing, then it probably isn't worth the trouble.

---

### Post by edin9 on 2009-11-05
> **Bezmotivnik said:**
> Most of these don't apply, and the ones that do certainly aren't &quot;easy&quot; by any stretch of the imagination.

Java/Cookies are (normally) disabled by both a sophisticated user and Privoxy, traffic analysis in a normally active Tor net is virtually impossible and who has real-time access to &quot;both ends&quot; of the entire Internet in the real world?  

Unless you can do real-time decryption of them, all you can trace is undifferentiated encrypted packets in a single hop between two nodes in a very busy Tor net.  

The only &quot;easy&quot; way to do this is to compromise the actual machines identified by tracking their IPs in their initial hookups with the Tor net, not Tor itself.

It's easy for the people who want to track you. One of the easiest ways it to cross-reference useragent information against site information.

---

### Post by mmix on 2009-11-05
easy.

bind 9 + tor combo.

[https://www.isc.org/products/BIND/](https://www.isc.org/products/BIND/)
[http://www.torproject.org/](http://www.torproject.org/)

---

### Post by Bezmotivnik on 2009-11-05
> **edin9 said:**
> It's easy for the people who want to track you. One of the easiest ways it to cross-reference useragent information against site information.
Doesn't work:

"Set user agent during Tor usage (crucial)

"User agent masking is done with the idea of making all Tor users appear uniform. A recent Firefox 2.0.0.4 Windows build was chosen to mimic for this string and supporting navigator.* properties, and this version will remain the same for all TorButton versions until such time as specific incompatibility issues are demonstrated. Uniformity of this value is obviously very important to anonymity. Note that for this option to have full effectiveness, the user must also allow Hook Dangerous Javascript ensure that the navigator.* properties are reset correctly. The browser does not set some of them via the exposed user agent override preferences."

---

### Post by edin9 on 2009-11-05
The default user agent in Firefox is set to en_US, I should have been more clear, I meant browser info as well. Screen resolution, browser size. Most people who connect to Tor just go with the default setting. If you truly want a chance at anonymity use APS over a private network with P2P packet streaming to an outside network.

---

### Post by Khufucius on 2009-11-05
> **t0p said:**
> Just cut-and-pasting mindlessly from man pages proves nothing but mindlessness.

Nice!!*

So for those running ext3, such as myself, this seems to apply (RE: disk wipes):
[http://ubuntuforums.org/showthread.php?t=31661](http://ubuntuforums.org/showthread.php?t=31661)

Cheers,

-Khufu


*I have **three** beans, tough guy.  I was trying to be helpful.

---

### Post by Bezmotivnik on 2009-11-05
> **edin9 said:**
> The default user agent in Firefox is set to en_US, I should have been more clear, I meant browser info as well. Screen resolution, browser size.

Most people who connect to Tor just go with the default setting. If you truly want a chance at anonymity use APS over a private network with P2P packet streaming to an outside network.

It doesn't apply.  The logging information that shows when using Tor is that of the exit node, not me at my end.  I just tested it.  

[http://ipid.shat.net/](http://ipid.shat.net/)

No identifying info from my machine shows at that end and aside from my IP, little (if any) distinctive info is conveyed to the *entry* node, and that is scrubbed prior to retransmission.

I have all that blocked even with my normal, open use, with NoScript.

Again, you can't hide that you are accessing a Tor net, but telling what you are doing with it is another story.

---

### Post by edin9 on 2009-11-05
> **Bezmotivnik said:**
> It doesn't apply.  The logging information that shows when using Tor is that of the exit node, not me at my end.  I just tested it.  

[http://ipid.shat.net/](http://ipid.shat.net/)

No identifying info from my machine shows at that end and aside from my IP, little (if any) distinctive info is conveyed to the *entry* node, and that in encrypted form, which is scrubbed upon decryption.

Yes it does you don't fully understand the concept of Tor. You just need to use 'outside the box' methods to catch someone who tries to hide. Tor just makes it harder not impossible.

---

### Post by t0p on 2009-11-05
> **edin9 said:**
> The default user agent in Firefox is set to en_US, I should have been more clear, I meant browser info as well. Screen resolution, browser size. Most people who connect to Tor just go with the default setting.

It doesn't matter what "most people" do.  If we're going to assume that the user really really wants/needs true anonymity, it's reasonable to assume he will use Tor in the most effective way possible.

---

### Post by edin9 on 2009-11-05
> **t0p said:**
> It doesn't matter what &quot;most people&quot; do.  If we're going to assume that the user really really wants/needs true anonymity, it's reasonable to assume he will use Tor in the most effective way possible.

If you want true anonymity you don't use Tor, there are far more effective things out there if you know who and where.

---

### Post by Bezmotivnik on 2009-11-05
> **edin9 said:**
> Yes it does you don't fully understand the concept of Tor. 
I think I just don't understand your explanation.

How is this information available at the exit end of the Tor network if it hasn't gone beyond the first hop?

---

### Post by Bezmotivnik on 2009-11-05
> **t0p said:**
> It doesn't matter what "most people" do.  If we're going to assume that the user really really wants/needs true anonymity, it's reasonable to assume he will use Tor in the most effective way possible.
I don't think that's a safe assumption, which is why they made Vidalia, to make the process less onerous.

I am not convinced that the package is foolproof, but I have not seen a good explanation of why it wouldn't be from anyone who has seriously analyzed the package at length.

---

### Post by edin9 on 2009-11-05
> **Bezmotivnik said:**
> I think I just don't understand your explanation.

How is this information available at the exit end of the Tor network if it hasn't gone beyond the first hop?

Tor doesn't hide browser info like your screen resolution, the size of the browser, you may have an application installed that Tor doesn't compensate for, the generic Tor user agent is itself a form of identification, logging cookies can feed back information that betray you, your broswer may have a plugin that uses it's own protocols that doesn't work with Tor, handshake protocols, a LOT of things. Any information I can gain can be used to piece together a picture. These are the some of the methods police/anti-terrorist/etc use against people who try to hide.

---

### Post by Bezmotivnik on 2009-11-05
> **edin9 said:**
> Tor doesn't hide browser info like your screen resolution, the size of the browser you may have an application installed that Tor doesn't compensate for, the generic Tor user agent is itself a form of identification, logging cookies can feed back information that betray you, your broswer may have a plugin that uses it's own protocols that doesn't work with Tor, handshake protocols, a LOT of things. Any information I can gain can be used to piece together a picture. These are the some of the methods police/anti-terrorist/etc use against people who try to hide.
Actually, the main thing they currently do is simply compromise suspect machines, which is more efficient than screwing around with trying to brute-force Tor packets.  There's a particular lead unit that does this at Ft. Meade I was reading about the other day.

But what I don't get is how the specific information to which you refer can occur if cookies, scripts and Flash are blocked at your browser.

I also don't understand -- unless the end site was hostile or compromised -- how any of this would be apparent in encrypted packets, unless it were occurring outside the encryption process, which I do not believe is the case.

---

### Post by edin9 on 2009-11-05
> **Bezmotivnik said:**
> Actually, the main thing they currently do is simply compromise suspect machines, which is more efficient than screwing around with trying to brute-force Tor packets.  There's a particular lead unit that does this at Ft. Meade I was reading about the other day.

But what I don't get is how the specific information to which you refer can occur if cookies, scripts and Flash are blocked at your browser.

I also don't understand -- unless the end site was hostile or compromised -- how any of this would be apparent in encrypted packets, unless it were occurring outside the encryption process, which I do not believe is the case.

I did say some of the ways, and that leads back into application/plugins that betray you. The rest is hard to explain if you don't fully read and understand what I have already said. Not all machines can just be infected, you quite often have to use different/simple methods to narrow down and identify. There are also several upcoming methods that will make tracing someone virtually impossible.

---

### Post by pwnst*r on 2009-11-05
you're either paronoid beyond belief or have something to hide if you're using Tor.  talk about slow as snails

---

### Post by edin9 on 2009-11-05
> **pwnst*r said:**
> you're either paronoid beyond belief or have something to hide if you're using Tor.  talk about slow as snails

Lmfao exactly, Tor is unusable 90% of the time.

---

### Post by hobo14 on 2009-11-05
Tor still doesn't provide you with **true** anonymity, only practical anonymity.
It may make you _almost_ (there is always a chance, however tiny, that the correct traffic will be analysed first, at every node) impossible to find _in practice_, but in theory your IP address can still be found.  

The only way to true anonymity is to use an IP that has no connection to you: ie throwaway mobiles bought without ID, an ISP that destroys all record of who used which IP address, or piggybacking.

---

### Post by JBAlaska on 2009-11-05
Just boils down to who's looking for you, if it's anyone but N$A you can prolly spoof them...But N$A doesn't lease Cray time..They own 2 of them..

Instant HD wipe:
Powerful Degausser mounted on top of your HD (On a UPS in case they cut your power), when the MAN kicks in your door, you flip a switch and ZAP!

Anonymous interweb surfing:
Combo of proxy tunneling and...Wait a sec, figure this stuff out for yourself LOL's

---

### Post by c2006 on 2009-11-05
> **JBAlaska said:**
> Just boils down to who's looking for you, if it's anyone but N$A you can prolly spoof them...But N$A doesn't lease Cray time..They own 2 of them..

Instant HD wipe:
Powerful Degausser mounted on top of your HD (On a UPS in case they cut your power), when the MAN kicks in your door, you flip a switch and ZAP!


Only 99.999% effective. Physical destruction of the drive is the *only* way to be sure. Mount it in a hot-swap bay, remove it, throw it from 20 stories up... It'll die.

> **JBAlaska said:**
> 
Anonymous interweb surfing:
Combo of proxy tunneling and...Wait a sec, figure this stuff out for yourself LOL's

The only way to be truly secure and have any semblance of anonymity is to have nothing plugged in. Including any monitors, as these can be scanned from outside.

---

### Post by JBAlaska on 2009-11-05
> **c2006 said:**
> Only 99.999% effective. Physical destruction of the drive is the *only* way to be sure. Mount it in a hot-swap bay, remove it, throw it from 20 stories up... It'll die.



The only way to be truly secure and have any semblance of anonymity is to have nothing plugged in. Including any monitors, as these can be scanned from outside.

1-Guess I should have posted the Thermite grenade method.

2-Darn, I thought I was Paranoid..Good point though.

---

### Post by hobo14 on 2009-11-05
> **JBAlaska said:**
> Just boils down to who's looking for you, if it's anyone but N$A you can prolly spoof them...But N$A doesn't lease Cray time..They own 2 of them..

Instant HD wipe:
Powerful Degausser mounted on top of your HD (On a UPS in case they cut your power), when the MAN kicks in your door, you flip a switch and ZAP!

Anonymous interweb surfing:
Combo of proxy tunneling and...Wait a sec, figure this stuff out for yourself LOL's

I can't say what I want to you, because my post would be deleted...<sigh>

Degaussing is not related to anonymity on a network, the topic of this thread.

No, a "combo of proxy tunneling and..." will not provide true, mathematical anonymity.


> **c2006 said:**
> Only 99.999% effective. Physical destruction of the drive is the *only* way to be sure. Mount it in a hot-swap bay, remove it, throw it from 20 stories up... It'll die.

The only way to be truly secure and have any semblance of anonymity is to have nothing plugged in. Including any monitors, as these can be scanned from outside.

Again, not related to anonymity. (and dropping a disk 20 stories is not going to come close to the destruction of data that degaussing would provide)

---

### Post by tjwoosta on 2009-11-05
Aquire a new laptop that you've never used casually before.
If you buy it from a store pay with cash wear sunglasses and don't give identity.
Zero the HD, format and encrypt, install linux.
Don't ever use it to connect to your home network, only coffee shops and such, and mix it up as in don't keep connecting from the same locations.
Always spoof mac using different address each time.
Always wear sunglasses or a hood or otherwise disguise yourself from cameras and observers, try to mix it up so you don't always look the same.
Don't cover the laptop in stickers, they shout "IM SUSPICIOUS LOOK AT ME", also they can be recognized.
Use SELinux.
Be careful what you install because some things phone home with stats and such, privacy risk or not its just better to remove variables like that.
Also better to use only open source and examine the code yourself.
Setup really strict iptables firewall.
Never put any personal information on this machine, and never access any personal information with this machine, i.e. email, IM, anything!
Tor, or other privacy proxies, are only good for slowing them down and they are insecure since it can easily be sniffed by the exit nodes, so keep that in mind.
Don't keep logs of anything.
Use noscript and only allow things that are explictly required.
Clear cache, cookies, history, everything, every time you close the browser.
If you need to transfer data to or from this machine use either a cd/dvd or USB, don't connect.
Also you could zero the HD, reformat reencrypt, and reinstall every month or so just for good measure.

Its probably still possible for the truly determined to track this computer but how could they ever trace it back to you, and how would they know where you will be next. Be quick with doing what your doing and move on to a new location.


This is all theoretical of course. ;)

---

### Post by edin9 on 2009-11-05
> **tjwoosta said:**
> Aquire a new laptop that you've never used casually before.
If you buy it from a store pay with cash wear sunglasses and don't give identity.
Zero the HD, format and encrypt, install linux.
Don't ever use it to connect to your home network, only coffee shops and such, and mix it up as in don't keep connecting from the same locations.
Always spoof mac using different address each time.
Always wear sunglasses or a hood or otherwise disguise yourself from cameras and observers, try to mix it up so you don't always look the same.
Don't cover the laptop in stickers, they shout &quot;IM SUSPICIOUS LOOK AT ME&quot;, also they can be recognized.
Use SELinux.
Be careful what you install because some things phone home with stats and such, privacy risk or not its just better to remove variables like that.
Also better to use only open source and examine the code yourself.
Setup really strict iptables firewall.
Never put any personal information on this machine, and never access any personal information with this machine, i.e. email, IM, anything!
Tor, or other privacy proxies, are only good for slowing them down and they are insecure since it can easily be sniffed by the exit nodes, so keep that in mind.
Don't keep logs of anything.
Use noscript and only allow things that are explictly required.
Clear cache, cookies, history, everything, every time you close the browser.
If you need to transfer data to or from this machine use either a cd/dvd or USB, don't connect.
Also you could zero the HD, reformat reencrypt, and reinstall every month or so just for good measure.

Its probably still possible for the truly determined to track this computer but how could they ever trace it back to you, and how would they know where you will be next. Be quick with doing what your doing and move on to a new location.


This is all theoretical of course. ;)

Depending on what method you use:~ Switch screen resolution every alternate session, use a random user agent generator, run from a livecd if using linux, use different system languages, different keyboard layouts, switch ip addresses repeatedly in the same session, disconnect from a wireless network at least 3 times a session, etc......

---

### Post by hobo14 on 2009-11-05
> **edin9 said:**
> 
[QUOTE=tjwoosta;8254078]Aquire a new laptop that you've never used casually before.
If you buy it from a store pay with cash wear sunglasses and don't give identity.
Zero the HD, format and encrypt, install linux.
Don't ever use it to connect to your home network, only coffee shops and such, and mix it up as in don't keep connecting from the same locations.
Always spoof mac using different address each time.
Always wear sunglasses or a hood or otherwise disguise yourself from cameras and observers, try to mix it up so you don't always look the same.
Don't cover the laptop in stickers, they shout "IM SUSPICIOUS LOOK AT ME", also they can be recognized.
Use SELinux.
Be careful what you install because some things phone home with stats and such, privacy risk or not its just better to remove variables like that.
Also better to use only open source and examine the code yourself.
Setup really strict iptables firewall.
Never put any personal information on this machine, and never access any personal information with this machine, i.e. email, IM, anything!
Tor, or other privacy proxies, are only good for slowing them down and they are insecure since it can easily be sniffed by the exit nodes, so keep that in mind.
Don't keep logs of anything.
Use noscript and only allow things that are explictly required.
Clear cache, cookies, history, everything, every time you close the browser.
If you need to transfer data to or from this machine use either a cd/dvd or USB, don't connect.
Also you could zero the HD, reformat reencrypt, and reinstall every month or so just for good measure.

Its probably still possible for the truly determined to track this computer but how could they ever trace it back to you, and how would they know where you will be next. Be quick with doing what your doing and move on to a new location.


This is all theoretical of course. ;)Depending on what method you use:~ Switch screen resolution every alternate session, use a random user agent generator, run from a livecd if using linux, use different system languages, different keyboard layouts, switch ip addresses repeatedly in the same session, disconnect from a wireless network at least 3 times a session, etc......[/QUOTE]

This thread has descended into silliness. 
Most of this stuff is not related to maintaining anonymity online, it's about preventing a conviction after you are identified, and will do nothing to prevent your real IP being matched to the IP at the pointy end, or your real IP being matched to your name.

Some are unspeakably absurd, eg: "wear sunglasses", "don't put stickers on your laptop", "switch screen resolutions", "disconnect 3 times"....?! 
Surely UF makes exceptions to their rules for circumstances like this, and allows abusive name calling?

---

### Post by edin9 on 2009-11-05
> **hobo14 said:**
> This thread has descended into silliness. 
Most of this stuff is not related to maintaining anonymity online, it's about preventing a conviction after you are identified, and will do nothing to prevent your real IP being matched to the IP at the pointy end, or your real IP being matched to your name.

Some are unspeakably absurd: &quot;wear sunglasses&quot;, &quot;don't put stickers on your laptop&quot;, &quot;switch screen resolutions&quot;, &quot;disconnect 3 times&quot;....?! 
Surely UF makes exceptions to their rules for circumstances like this, and allows abusive name calling?

Conviction? Whose breaking the law? Someone asked a question and was given answers.

---

### Post by kevdog on 2009-11-06
Seriously anyone who doesn't pick option #1 in this poll is such a novice!

---

### Post by chris.willis on 2009-11-06
Easy. Do what you want on the internet and, by use of a time machine, go back to the moment before you first accessed it and stop yourself from using it. You will never get traced if you never use the internet, ergo, 100% untraceable, but it has its flaws.

---

### Post by tjwoosta on 2009-11-06
> **hobo14 said:**
> This thread has descended into silliness. 
Most of this stuff is not related to maintaining anonymity online, it's about preventing a conviction after you are identified, and will do nothing to prevent your real IP being matched to the IP at the pointy end, or your real IP being matched to your name.

Your using random wireless hotspots so whoever tracks you will get the hotspots IP. Individual IPs are not unique and can easily be changed, and will probably be different every time you connect anyway if your using dhcp and spoofing your mac. Mac addresses are the unique identifier of every machine but as mentioned before yours is spoofed. Even if they could somehow track your machine how would anyone know which name to match with it, remember you never gave away any identification when obtaining the machine? Hence the sunglasses and disguise. Someone traces the hotspots ip, contacts the maintainer and figures out which individual ip it was and what the mac was, they could possibly figure out where you were sitting, and even check the cameras but if you were disguised good enough you were annonymous. By the time they finish the trace you are long gone and on another random network with another spoofed mac and another disguise. All they have at this point is a fake mac address and a video of someone in a disguise.

If your using a proxy it will take even longer for anybody to trace you because they would first get the exit nodes ip. After contacting the proxy service they could possibly get a list of all the ip's that were using the proxy at that time. If they somehow figure it out which ip it was from the list they still only have the hotspots ip that you were at.

[QUOTE=hobo14]
Some are unspeakably absurd, eg: "wear sunglasses", "don't put stickers on your laptop", "switch screen resolutions", "disconnect 3 times"....?! 
Surely UF makes exceptions to their rules for circumstances like this, and allows abusive name calling?[/QUOTE]

Well we are talking complete anonymity. Wearing sunglasses is so nobody sees your face, walking around in a city you would be surprised how many times your recorded through out the day. Stickers on laptop are easily identifiable, as well as a "hacker" tell. Switching screen resolutions I assume is because information like that is easily obtained by websites, but I wouldn't go that far because identical resolutions are common especially in wifi hotspots.

[quote=edin9]use different system languages, different keyboard layouts, switch ip addresses repeatedly in the same session, disconnect from a wireless network at least 3 times a session, etc......[/quote]

That all seems a bit unnecessary to me if you are on a random network anyway. Who cares about language and keyboard layout because everybody around you will probably be using the same.


lol, You could always steal a new laptop every week, use a random live cd, and crack random personal wireless networks to access the net.

---

### Post by OffHand on 2009-11-06
> **postaldude said:**
> 100% anonymous? Not a chance. Whatever you do to encrypt or divert your traffic, your ip address is still a necessary component of the packet, which has to be unencrypted, to get the data back to your machine. You can go through as many proxies as you like, but the data, as far as your isp is concerned, is still there. If someone really wanted to, and had the time, they could trace your activity on the net, get the ip, and the isp could tell them who it was.
Thankfully, mostly, they don't seem to, unless there's a court order (at least the ones i've heard of), so the chances are fairly low. But it's still possible.

vpn?

---

