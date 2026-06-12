---
title: "Torrents"
date: 2010-10-11
forum: Security
---

### Post by pizza-is-good on 2010-10-11
When downloading Maverick today and the download time was more than an hour, I remembered that a long time ago, Canonical asked that advanced users download iso using torrents. So I clicked on the link to the torrent, and Transmission opened up. It got done fast, so I was happy.

I haven't used P2P for a very long time, so sorry if my questions seem stupid.

Being 'new' to torrents, I have some questions.
Is it safe? I mean, is my computer at all compromised because I am connected to someone else's computer?
In the preferences I did select 'require encryption'. Does that help with anything?

Other thing, when the iso finished downloading, it started 'seeding'. I imagine it is sending it to other peers, but a clarification would be nice. While seeding, only those files are being shared, right? I mean, not every file in my computer is being shared, right?
What is the seeding ratio? Is it the percentage of the file I've shared with others?

Now, since I was downloading from other peers, is it 'nice' or in the spirit of Ubuntu to keep seeding the iso for a long time so everyone that goes for it can download from me? Is there any risk from having Transmission on all day long so that there is one more peer to get data from?

And just general questions. What settings are the safest to use? And just general settings gidelines would be appreicated, like max amount of peers, max speeds, limits on speeds, etc.

Thanks,

~pizza

---

### Post by FuturePilot on 2010-10-11
> Is it safe? I mean, is my computer at all compromised because I am connected to someone else's computer?

Yes it is safe.

> In the preferences I did select 'require encryption'. Does that help with anything?
That will prevent anyone from sniffing the data you are downloading/uploading.

> Other thing, when the iso finished downloading, it started 'seeding'. I imagine it is sending it to other peers, but a clarification would be nice.

Yes, it means you're done downloading it and you are now only uploading to other peers.

> While seeding, only those files are being shared, right? I mean, not every file in my computer is being shared, right?

Yes. Only the file(s) that are part of the torrent are seeded.

> What is the seeding ratio? Is it the percentage of the file I've shared with others?

Basically yes. When you've uploaded as much as you've downloaded you reach a 1:1 ratio and it keeps increasing from there.

> Now, since I was downloading from other peers, is it 'nice' or in the spirit of Ubuntu to keep seeding the iso for a long time so everyone that goes for it can download from me?

It's usually considered proper torrent etiquette to seed at least until you reach a 1:1 ratio. If you seed longer, that's even more awesome. 

> Is there any risk from having Transmission on all day long so that there is one more peer to get data from?
No

> And just general questions. What settings are the safest to use? And just general settings gidelines would be appreicated, like max amount of peers, max speeds, limits on speeds, etc.

That all depends on your connection. Some routers have a hard time handling large amounts of connections. Others handle it fine. It also depends on your bandwidth as well.

---

### Post by rookcifer on 2010-10-11
The main thing to be concerned about when it comes to downloading torrent .iso's is to check the MD5/SHA1 hashes of the file and make sure they match.

---

### Post by Simian Man on 2010-10-11
> **rookcifer said:**
> The main thing to be concerned about when it comes to downloading torrent .iso's is to check the MD5/SHA1 hashes of the file and make sure they match.

Actually using torrents is the one time you generally *don't* have to do checksumming, because the torrent client generally already does that.

---

### Post by _outlawed_ on 2010-10-11
> Yes it is safe.

Legal software through torrents is safe, illegal isn't so safe as government agencies usually have bots running in p2p networks that upload garbage data and log your IP address the second you connect to them.


> That will prevent anyone from sniffing the data you are downloading/uploading.

Wrong. The only thing protocol encryption does is to bypass ISP throttling of the torrent protocol.

---

### Post by FuturePilot on 2010-10-11
> **_outlawed_ said:**
> Legal software through torrents is safe, illegal isn't so safe as government agencies usually have bots running in p2p networks that upload garbage data and log your IP address the second you connect to them.
I was talking from a security perspective. Legal/illegal issues is a whole separate discussion.

> Wrong. The only thing protocol encryption does is to bypass ISP throttling of the torrent protocol.

You're right. I stand corrected.

---

### Post by _outlawed_ on 2010-10-11
> **FuturePilot said:**
> I was talking from a security perspective.

So was I. If you were familiar with Kazaa, government agencies were filling the network with a TON of malicious software from viruses, to loggers, adware, malware and the sorts.

While torrents do provide a safer environment from it, nontrusted uploaders have a bad tendency to push the same crap through their torrents (like keygens and the sorts).

But Ubuntu torrents are 100% safe, so no need to worry at all. :)

---

### Post by JC Cheloven on 2010-10-11
> **pizza-is-good said:**
> And just general questions. What settings are the safest to use? And just general settings gidelines would be appreicated, like max amount of peers, max speeds, limits on speeds, etc.

If you allow it to upload at unlimited (or too high) speed, and you want to use your connection for something else (browsing the web...) at the same time, you may not be able to do so because there is no available upload bandwith for the other app to comunicate with the world. Otherwise, there is no problem in setting both download and upload speed to unlimited.

Tip: there is a turtle icon at the bottom of the window. This is for setting temporary speed limits in a quick way. The applied limits are set in edit-preferences-speed. You can set this to, say, at a 60% of the efective speeds of your connection, and press it when you eventually want to use your connection for something else at the same time.

EDIT: my current ratio = 2.86 and raising. I'm a good boy :rolleyes:

---

### Post by pizza-is-good on 2010-10-12
Thanks everyone for the replies. They have made it very clear.

> **FuturePilot said:**
> Yes it is safe.
That will prevent anyone from sniffing the data you are downloading/uploading.
Yes, it means you're done downloading it and you are now only uploading to other peers.
Yes. Only the file(s) that are part of the torrent are seeded.
Basically yes. When you've uploaded as much as you've downloaded you reach a 1:1 ratio and it keeps increasing from there.
It's usually considered proper torrent etiquette to seed at least until you reach a 1:1 ratio. If you seed longer, that's even more awesome. 
No
That all depends on your connection. Some routers have a hard time handling large amounts of connections. Others handle it fine. It also depends on your bandwidth as well.

Thanks for the very detailed explanation.

> **_outlawed_ said:**
> Legal software through torrents is safe, illegal isn't so safe as government agencies usually have bots running in p2p networks that upload garbage data and log your IP address the second you connect to them.

Glad to hear that. I only plan on using it for downloading ISOs.

> **_outlawed_ said:**
> So was I. If you were familiar with Kazaa, government agencies were filling the network with a TON of malicious software from viruses, to loggers, adware, malware and the sorts.

While torrents do provide a safer environment from it, nontrusted uploaders have a bad tendency to push the same crap through their torrents (like keygens and the sorts).

But Ubuntu torrents are 100% safe, so no need to worry at all. :)
That's good to know.

> **JC Cheloven said:**
> If you allow it to upload at unlimited (or too high) speed, and you want to use your connection for something else (browsing the web...) at the same time, you may not be able to do so because there is no available upload bandwith for the other app to comunicate with the world. Otherwise, there is no problem in setting both download and upload speed to unlimited.

Tip: there is a turtle icon at the bottom of the window. This is for setting temporary speed limits in a quick way. The applied limits are set in edit-preferences-speed. You can set this to, say, at a 60% of the efective speeds of your connection, and press it when you eventually want to use your connection for something else at the same time.

EDIT: my current ratio = 2.86 and raising. I'm a good boy :rolleyes:
Thanks for the tip there. I did notice browsing was slow. Very useful to know about the temporary limits.

I have both the 32 and 64 bit ISOs in Transmission, as I downloaded them both. They are at about 0.30 ratio... I'm sure that's bad, so I'll try to keep it on for a bit.
Since we are talking about being good boys, would it be good to download all the versions (netbook, server, alternate, etc) so that all can be seeded?

---

### Post by _outlawed_ on 2010-10-12
Good settings for your torrenting download/upload speeds would be something like this:

80%-90% of your total download speed
50-60% of your total upload speed

This way you won't throttle yourself and can still do other stuff. Here's an example of my current settings in Transmission:

**Last Result:**
Download Speed: **16511** kbps (2063.9 KB/sec transfer rate)
Upload Speed: **1817** kbps (227.1 KB/sec transfer rate)


Download cap: 1300 KB/s
Upload cap: 125 KB/s

---

### Post by pizza-is-good on 2010-10-13
> **_outlawed_ said:**
> Good settings for your torrenting download/upload speeds would be something like this:

80%-90% of your total download speed
50-60% of your total upload speed

This way you won't throttle yourself and can still do other stuff. Here's an example of my current settings in Transmission:

**Last Result:**
Download Speed: **16511** kbps (2063.9 KB/sec transfer rate)
Upload Speed: **1817** kbps (227.1 KB/sec transfer rate)


Download cap: 1300 KB/s
Upload cap: 125 KB/s

Now, I may really sound stupid, but how do I find my max download and upload speeds?

---

### Post by CharlesA on 2010-10-13
> **pizza-is-good said:**
> Now, I may really sound stupid, but how do I find my max download and upload speeds?

[http://www.speedtest.net](http://www.speedtest.net)

---

### Post by pizza-is-good on 2010-10-13
> **CharlesA said:**
> [http://www.speedtest.net](http://www.speedtest.net)

Thanks... I didn't think it'd be that easy.

OK, no more questions from me, I think.

---

### Post by JC Cheloven on 2010-10-13
> **pizza-is-good said:**
> Since we are talking about being good boys, would it be good to download all the versions (netbook, server, alternate, etc) so that all can be seeded?
Sure, I do that myself. More precisely, I download the flavours with a possibility, be it tiny, of being used for me at a later time (ie, I'll probably not use kubuntu, or the Ub. netbook remix, but I download them just in case), mainly for the purpose of seeding them for a couple of days. 

Torrent seeding helps to lower the load at ubuntu main servers. I consider this a way of giving back a small portion of what I received. 

Cheers
JC

---

### Post by pizza-is-good on 2010-10-14
> **JC Cheloven said:**
> Sure, I do that myself. More precisely, I download the flavours with a possibility, be it tiny, of being used for me at a later time (ie, I'll probably not use kubuntu, or the Ub. netbook remix, but I download them just in case), mainly for the purpose of seeding them for a couple of days. 

Torrent seeding helps to lower the load at ubuntu main servers. I consider this a way of giving back a small portion of what I received. 

Cheers
JC

I agree. I got all the 10.10 and 10.04 versions available(server, alternate, and desktop. 64 and 32 bit). Didn't find the netbook torrent though. Definitely feels good to give back, good idea, thanks!

---

