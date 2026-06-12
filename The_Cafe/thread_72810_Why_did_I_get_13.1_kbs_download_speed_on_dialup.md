---
title: "Why did I get 13.1 kb/s download speed on dialup?"
date: 2005-10-07
forum: The Cafe
---

### Post by dieselpower on 2005-10-07
I am running linux and was downloading an ISO image this morning, and for the first half hour got about 13,1 kb/s download speed. How can this happen? How can I make it do that all the time? I called my ISP and they could not help, and I really want to figure this out! I caught it doing that for about four minuts again and got a screenshot just as it quit, so you can see for yourself. Here it is. [http://www.ubuntuforums.org/attachment.php?attachmentid=2751&stc=1&d=1128699468](http://www.ubuntuforums.org/attachment.php?attachmentid=2751&stc=1&d=1128699468)
 NOTE; It is now running at 5.9 but just before the screenshot it was running at 13.1 kb/s. It took me too long to figure out how to do a screenshot!

---

### Post by KLineD on 2005-10-07
Normally I get 50ks+ out of my connection but when I start a download (particularly with mozilla firefox) the download box says 180ks+ or something along that dl speed. 

I believe its due to the fact that the browser starts downloading the file the second you click on the link so by the time you click on the confirmation dialog for the download and select a location it already has a good chunk of the file downloaded and thus the reported dl speed.

Anyway, you say you got that speed for half an hour and normally it happens to me but for a minute or so before it stabilize.

---

### Post by dieselpower on 2005-10-07
Yes but this is different, from the time I clicked the link to the time I confirmed was maybe 10 or 15 seconds. And in about ten minuts I had 4 or 5 megs downloaded. Look at that 3 minute blast in the kppp dialog box. that was maybe an hour after I started, and that was about 13 kb/s again!

---

### Post by Sirin on 2005-10-07
[QUOTE=dieselpower]Yes but this is different, from the time I clicked the link to the time I confirmed was maybe 10 or 15 seconds. And in about ten minuts I had 4 or 5 megs downloaded. Look at that 3 minute blast in the kppp dialog box. that was maybe an hour after I started, and that was about 13 kb/s again![/QUOTE]
Is the image still downloading? :D

When I had dialup, the highest my connection would go would be 6kb/s. I would be lucky to even get 8kb/s for just a half-second. Now, I'm running broadband, and I normally can download at 650kb/s, and sometimes I download at 2mb/s. :cool:

---

### Post by SGC on 2005-10-07
Downloading an ISO file using konqueror is a bad idea specially you are on dialup. I suggest to use kget (kde download manager) so that you can resume the download if you get dissconnected.
sudo apt-get install kget

---

### Post by mcduck on 2005-10-07
Now that's funny, as in the screenshot the download window says that the speed is 5,1KB/s, but the kppp statistics window shows 4,4Kb/s (and max 15Kb/s)

5,1KB/s is 40,8Kb/s.. Now there must be something wrong with either kppp or Konqueror :D

edit: if the download window said that the speed was 13,1KB/s, there is a silly bug in Konqueror. That would be 104,8Kb/s, way more than modem line's maximum speed of 56Kb/s..

---

### Post by poptones on 2005-10-07
The modems compress the data (that's how they get to 56K/sec). But this "56K number" is really just a general estimate. If the data is highly compressible, then you will (momentarily) go well above that. Since you are downloading an iso, there will be parts of the file that are more readily compressed.

Example: when I download headers from a news server I typically get download speeds of 20K-45K over dialup. When downloading a uue encoded file that same connection may get 7kbps, and when downloading yenc it will get about the expected 5.5kbps.

---

### Post by blastus on 2005-10-07
I'm on dialup and the exact same thing has happened to me a couple of times. This is not an anomaly. This is a consistently unobtainable (like 10-15 kb/s) download rate on dialup over a period of 10 to 30 minutes. It is readily verifiable by observing the size of the file you are downloading. 

I've had this happen with ISOs and even a large ZIP file. Compression was the first thing that popped into my mind as an explanation but how does one explain downloading a large ZIP file on dialup at 10kb/s for the first 10 minutes or so?

It's nice when it happens but I've found it to be an extremely rare occurrence.

---

### Post by zenwhen on 2005-10-07
It is IMPOSSIBLE to actually be able to download over 56k with a dial up connection. It isn't an anomaly. It is an incorrect measurement.

---

### Post by dieselpower on 2005-10-07
No, its not an incorrect measurement. The megabytes were pouring in *very* fast. I think I had 5 megs in the first ten minuts. Normaly it's about 12 megs an hour. look at the graph, it is a on/off type of thing, either it's about 5.9 or it's 13. very strange. And I may have gotten my KBps and Kbps mixed up. I forgot which one is bytes and bits;) 

BTW, Konqueror does resume, that is why I use it.

---

### Post by poptones on 2005-10-07
*It is IMPOSSIBLE to actually be able to download over 56k with a dial up connection.*

Riiiiiight.....

Do you want proxy server logs as well?

*BTW, Konqueror does resume, that is why I use it*

But HOW does it "resume?" An ISO is very large. Many browsers "resume" from cache. If you don't have your browser cache set to something ridiculous like 2GB or so, the file will never be able to resume because the browser will delete it as soon as it sweeps the cache. 

It's just too easy to use wget and not have such silly problems. I've had "resumable" file downloaders screw up on me; it sucks to spend 20 hours on dialup and then have the program delete the partial file on restart because it **thought** there was some sort of error.

---

### Post by zenwhen on 2005-10-08
You are either getting an abnormally high reading because of compression or inaccurate measuring. 56k modems conform to a standard (V.90, ITU '98 ) which says the maximum download rate you can get is 56,000bps. Converting this to KB/s which is what you're using it's 6KB/s, that is the absolute maximum limit which the specification allows. Not only that, but the limit is 56k because that is basically the highest frequency d>a communication you can get with a POTS line. If you are in America, the FCC limits the possible speed to 53k/s so it seems unlikely you are somehow not only breaking the laws of physics and the FCC but you are also  breaking specifications your modem and ISP adhere to (somewhat loosely). In short, no you are not getting  that, you never did get that, and please stop defending your position.

---

### Post by poptones on 2005-10-08
*You are either getting an abnormally high reading because of compression or inaccurate measuring. 56k modems conform to a standard (V.90, ITU '98 ) which says the maximum download rate you can get is 56,000bps... **blah, blah, blah, blah...***

I explained this a page back. There is nothing "abnormal" about high data rates when using v.9x modems. Text data (like newsgroup headers and portions of ISO files) has a [high symbol repetition rate]("http://www.ee.unb.ca/cgi-bin/tervo/mnp5.pl?message=joe98877666555+joker99877764983+joe99777674377+joe886787999+joker9778937783+joker7732984+joke+jokester+jack+joe232343242+joe3232344+joe32423432") which lends itself to symbol compression (which the modem handles itself). You are making the very common **newbie** mistake of [confusing a bit with a baud.]("http://support.intel.com/support/faxmodem/sb/cs-011466.htm")

*In short, no you are not getting that, you never did get that, and please stop defending your position.*

if you are allowed to make pompous challenges like this, please show ME the respect of not EDITING MY COMMENTS when I point out your utter **cluelessness**.

Does his forum have ANY MODERATORS that are not children?

---

### Post by zenwhen on 2005-10-08
You are creating an argument where it does not exist. No one said compression didn't improve what you get on the other end. Your bandwidth is till never any more than 53k. 

When you can download a nice fat binary package at over 53k sustained, and timed, you are proving that the extra bandwidth is there. If we aren't measuring uncompressed data here, we are arguing over nothing.

I have edited out the little jab you made at the end of your post. Do try and be a little more civilized.

---

### Post by zenwhen on 2005-10-08
You are creating an argument where it does not exist. No one said compression didn't improve what you get on the other end. Your bandwidth is till never any more than 53k. 

When you can download a binary package at over 53k sustained, and timed, you are proving that the extra bandwidth is there. If we aren't measuring uncompressed data here, we are arguing over nothing.

I have edited out the little jab you made at the end of your post. Do try and be a little more civilized.

---

### Post by zenwhen on 2005-10-08
You are creating an argument where it does not exist. No one said compression didn't improve what you get on the other end. Your bandwidth is still never any more than 53k. 

When you can download a binary package at over 53k sustained and timed, you are proving that the extra bandwidth is there. If we aren't measuring uncompressed data here, we are arguing over nothing.

I have edited your post to make it more pertinent to the topic.

---

### Post by poptones on 2005-10-08
*You are creating an argument where it does not exist.*

I am not the one making assinine statements like "you did not do this. It is IMPOSSIBLE. Stop defending your position..."

*No one said compression didn't improve what you get on the other end.*

Wrong. You said it. and you continue to say it BECAUSE YOU REFUSE TO SPEAK IN SPECIFIC TERMS.

*Your bandwidth is still never any more than 53k.*

53k WHAT? 53k BIT PER SECOND? You are dead wrong and I have posted graphic proof of it. 53k BITS PER SECOND IS NOT THE LIMIT. 

53k BAUD IS NOT 53K BITS. Read the links I provided and stop talking long enough to LEARN. 

*When you can download a binary package at over 53k sustained and timed, you are proving that the extra bandwidth is there.*

Those newsgroup headers ain't analog, chum. They are a "package of data" and the data transfer rate of >20 kbps is SUSTAINED. it does it every time.

What is the title of this thread? Does it not ask "why do I get over 13.1**kb/s** download speed? Kb/s... that's KILOBITS. I explained WHY it happens, all you did was deny it was possible. Who's "starting the argument" here?

*If we aren't measuring uncompressed data here, we are arguing over nothing.*

Wrong. We are arguning because you refuse to learn and repeatedly demonstrate an ignorance to the technical issues raiesed by the OP WHILE insisting you know what you are talking about. 

And if we are discussing "uncompressed data" then you are still dead wrong, because the channel [never goes over 2400baud!]("http://www.linuxports.com/howto/intro_to_networking/c4095.htm") The data is quadrature amplitude modulated into a 64 pont constellation so each *baud* sent over the channel represents up to 8 bits of data *before* any **other** compression!

---

### Post by zenwhen on 2005-10-08
Once again, I edited the personal attack out of your post. :) Please don't make a habit of this. 

Not everything can be compressed, sir. Being able to make use of compression to wind up with more at your end of the pipe is nice, but that doesn't make the pipe any bigger. If you are downloading already compressed data, your limit is apparent. You aren't getting more than 5.6K. I have read your links. They aren't anything I am ignorant of. In fact, they are pretty much common knowledge. What the OP claimed is not sustainable with many more things than parts of ISO's, web pages, and newsgroup headers. 

To end this up, let me quote your own link.

[http://support.intel.com/support/faxmodem/sb/cs-011466.htm](http://support.intel.com/support/faxmodem/sb/cs-011466.htm)

> Data compression allows modems to increase throughput **without increasing the baud rate** (transmission speed). With data compression, the sending modem compresses the data into a compact form. The receiving modem decompresses the data back to its original form. You save time and money because your information is transmitted much more quickly.

V.42bis is a data compression standard for high-speed modems. It compresses data by as much as 4:1 **(depending on the type of file you send).** Thus, a 9600 baud modem can transmit your data at up to 38,400bps (bits per second) using V.42bis. A 14.4K modem can transmit up to 57,600bps.

As I said earlier, not everything can be compressed. Your own link implies a limit on the speeds at which you can obtain uncompress-able data. Being able to get an "effectively" faster connection for surfing websites and grabbing news headers doesn't mean you can suck down more uncompressed data, which is the question here. Your limit there is your limit. Everything else is compression.

Since you cannot have this conversation in a civilized manner, it is going to be closed now. Feel free to discuss this with me in private or to post another thread when you have proof that you sustained 13K a second on a compressed binary.

---

### Post by zenwhen on 2005-10-08
Once again, I edited the personal attack out of your post. :) Please don't make a habit of this. 

Not everything can be compressed, sir. Being able to make use of compression to wind up with more at your end of the pipe is nice, but that doesn't make the pipe any bigger. If you are downloading already compressed data, your limit is apparent. You aren't getting more than 5.6K. I have read your links. They aren't anything I am ignorant of. In fact, they are pretty much common knowledge. What the OP claimed is not sustainable with many more things than parts of ISO's, web pages, and newsgroup headers. 

To end this up, let me quote your own link.

[http://support.intel.com/support/faxmodem/sb/cs-011466.htm](http://support.intel.com/support/faxmodem/sb/cs-011466.htm)

> Data compression allows modems to increase throughput **without increasing the baud rate** (transmission speed). With data compression, the sending modem compresses the data into a compact form. The receiving modem decompresses the data back to its original form. You save time and money because your information is transmitted much more quickly.

V.42bis is a data compression standard for high-speed modems. It compresses data by as much as 4:1 **(depending on the type of file you send).** Thus, a 9600 baud modem can transmit your data at up to 38,400bps (bits per second) using V.42bis. A 14.4K modem can transmit up to 57,600bps.

As I said earlier, not everything can be compressed. Your own link implies a limit on the speeds at which you can obtain uncompress-able data. Being able to get an "effectively" faster connection for surfing websites and grabbing news headers doesn't mean you can suck down more compressed data, which is the question here. Your limit there is your limit. Everything else is compression.

Since you cannot have this conversation in a civilized manner, it is going to be closed now. Feel free to discuss this with me in private or to post another thread when you have proof that you sustained 13K a second on a compressed binary.

---

