---
title: "A better newsgroup reader/ binary downloader"
date: 2009-03-27
forum: The Cafe
---

### Post by GuiGuy on 2009-03-27
I was going to post this in a software related group. But it finished up a rant so I thought it better to annoy the girls and boys in the Cafe with it :)

This issue is really bugging  me, so bear with me;

Why haven't we got a decent newsreader that provides a decent interface for binaries AND  performs as it should in what we like to call the true multitasking OS?

Yes, I know about hellanzb. I use it almost daily and it's great. Well behaved, stable, does what it should. 

But not everything is nzb. Occasionally we need to look into the groups. And here's where the problem starts, from my perspective and assessment at least:

Thunderbird's newsreader is totally inadequate. Downloading a group of files is just too frustrating.

Knode- life's too short. Give it the task of updating a couple of newsgroups with more than a dozen new posts and you may as well go out and have a dinner at the local pub as it takes over the PC and totally consumes all of the CPU. For me it's been so unresponsive that scrolling through a long list of headers  is impossible 

PAN; ahhh, the wanna be. A bit like the Big Mac really- promises so much but delivers so little. Initially it seems great. Responsive,fast, well structured etc, Then, after a few weeks, as more and more headers are gathered up, bang, there's the brick wall. Now I dare not even start it up. Almost immediately it starts thrashing the hard disk ( I haven't a clue what it's doing, but suspect it's indexing headers (?)) and making the PC so un-responsive  that it is unusable. Out of interest I let it run... three hours later it was still thrashing about. I've learnt to leave a shell open so I can kill PAN when it goes stupid. 

There's gotta be a newsreader out there that works!?

---

### Post by MellonCollie on 2009-03-27
I haven't found anything better (for me) than running Newsleecher inside an XP VM.

---

### Post by GuiGuy on 2009-03-27
> **MellonCollie said:**
> I haven't found anything better (for me) than running Newsleecher inside an XP VM.

Yea, I've resorted to that. Running client software out of a XP Virtual Box.  :(

---

### Post by Sealbhach on 2009-03-27
Liferea?


.

---

### Post by GuiGuy on 2009-03-27
> **Sealbhach said:**
> Liferea?
.

Thanks, I'll try it.

---

### Post by northwestuntu on 2009-03-27
newsbin pro runs great with wine

---

### Post by GuiGuy on 2009-03-27
> **northwestuntu said:**
> newsbin pro runs great with wine

Thanks. But that was the point of my post. There are many choices when we run Windows. But not Linux. Yet we argue that Linux  is far more "netcentric" than Windows.

Cheers

---

### Post by Sealbhach on 2009-03-27
In Linux Format magazine, they recommended Pan as the best usenet reader:

[http://pan.rebelbase.com/](http://pan.rebelbase.com/)


EDIT: Sorry, you tried it.

.

---

### Post by GuiGuy on 2009-03-27
> **Sealbhach said:**
> 

[http://pan.rebelbase.com/](http://pan.rebelbase.com/)

EDIT: Sorry, you tried it.

.

IMO & experience if that's the best we can do, Linux is in trouble ;)

It seems to me that Pan has trouble indexing very large groups of headers or its storage mechanism becomes corrupted. Couple that with the usual lack of documentation to help troubleshoot and it all becomes rather disappointing...

Cheers

---

### Post by Sealbhach on 2009-03-27
Here's the article syndicated from the magazine:

[http://www.techradar.com/news/software/applications/reviewed-and-rated-the-best-linux-newsreaders-583539?artc_pg=1](http://www.techradar.com/news/software/applications/reviewed-and-rated-the-best-linux-newsreaders-583539?artc_pg=1)


.

---

### Post by oldos2er on 2009-03-27
I prefer slrn, or, in a pinch, nn.

---

### Post by fifth on 2009-03-28
I've been using [KLibido]("http://klibido.sourceforge.net") for a few years.

Only feature it doesnt have, which i use, is ssl support. But I use Stunnel as a work-a-round.

---

### Post by GuiGuy on 2009-03-28
> **Sealbhach said:**
> Liferea?


.

News aggregation, not Newsgroup reading AFAICT.

---

### Post by GuiGuy on 2009-03-28
> **fifth said:**
> I've been using [KLibido]("http://klibido.sourceforge.net") for a few years.

Only feature it doesnt have, which i use, is ssl support. But I use Stunnel as a work-a-round.

I looked at it a while back but couldn't get my head around setting up stunnel so left it alone. 

Thanks

---

### Post by fifth on 2009-03-30
> **GuiGuy said:**
> I looked at it a while back but couldn't get my head around setting up stunnel so left it alone. 

Thanks

Stunnel is pretty easy to use, just install from the repos. I use a short (basically one command) script to start it;

```

#!/bin/sh
# Command to start stunnelfor my Giganews accout

echo "Starting Stunnel for Giganews SSL:"
[COLOR="Red"]sudo stunnel -c -d nntp -r news-europe.giganews.com:443[/COLOR]
echo "Complete."

```

Obviously replace "news-europe-giganews.com:443" with the address of the server and port you connect to.

Then on Klibido (or whatever reader) your server address is your own pc, ie "127.0.0.1" or "localhost" and port is 119. Put in the username and password as normal for your provider.

You could append the command to start your newsreader to the script and use it as a launcher to simplify things.

---

### Post by northwestuntu on 2009-03-31
> **GuiGuy said:**
> Thanks. But that was the point of my post. There are many choices when we run Windows. But not Linux. Yet we argue that Linux  is far more "netcentric" than Windows.

Cheers

well in most areas i am able to find a linux program that can replace a windows program, but this case i was not able to find anything that could match newsbin pro.  it's the only windows program i run on my computer.  mostly because it runs so perfect through wine i don't even bother trying to find a linux replacement.

---

### Post by wrtpeeps on 2009-03-31
Newsleecher* is the best newsreader in existance. Supersearch was sent by god. 

I had it running under Wine before, it runs fine except for the initial license entry (when you enter your key and hit submit, the program freezes).

There is a way around this by exporting your license data from the registry on a Windows machine, and running the .reg file on your Wine registry, but I found this to be really temperamental.

But once you get it registered to your license, you're fine.


*You have to buy a yearly subscription for Newsleecher, but it's definitely worth it! Super Search alone is worth the money (you pay extra for Super Search access.

---

### Post by northwestuntu on 2009-03-31
newsbin gives you free upgrades after you purchase it.  there are tons of web sites that will give you free searches.

---

### Post by wrtpeeps on 2009-03-31
> **northwestuntu said:**
> newsbin gives you free upgrades after you purchase it.  there are tons of web sites that will give you free searches.

I've yet to find anything CLOSE to Super Search.

---

### Post by mrfargoreed on 2009-04-02
I'm having exactly the same problem.  I tried Ubuntu about ten days ago and fell in love with it.  I want to move away from the Dark Side and use Ubuntu only, yet the ONE thing that is stopping me making the switch is a decent binary newsreader that downloads not just NZB files, but actually fetches headers, too.

I've tried PAN, but I preferred Klibido.  I just couldn't get either to work through SSL - followed instructions for stunnel4 (not the ones on this thread, I must add) and couldn't work it out.  

I did try Newsleecher on Wine, but it just hung and nothing happened - I didn't wait long enough to get to the registration screen.  Perhaps I needed to give it more time.

---

### Post by mister_p_1998 on 2009-04-02
I used Forte Agent in Windows since win3.1 days, and nothing on Linux touches it, pan's the nearest, but nowhere near as good.

Steve

---

### Post by northwestuntu on 2009-04-02
> **wrtpeeps said:**
> I've yet to find anything CLOSE to Super Search.

i've used super search and they all seem the same to me? newsbin also has a built in search.

---

### Post by mrfargoreed on 2009-04-03
Hey GuiGuy

I managed to get Klibido working with Stunnel with this thread:

[http://ubuntuforums.org/showthread.php?t=653246]("http://ubuntuforums.org/showthread.php?t=653246")

It seemed to be the best of a bad bunch of binary newsreaders, but at least it fetched headers and had a clean interface.  It's not Newsleecher, but it's the best I've tried so far.  

Hope this helps a little.

---

### Post by GuiGuy on 2009-04-03
> **mrfargoreed said:**
> I'm having exactly the same problem.  I tried Ubuntu about ten days ago and fell in love with it.  I want to move away from the Dark Side and use Ubuntu only, yet the ONE thing that is stopping me making the switch is a decent binary newsreader that downloads not just NZB files, but actually fetches headers, too.

I think for nzbs we're well provided for. I use Lottanzb/hellanzb and they work a treat. 

Cheers

> **mrfargoreed said:**
> Hey GuiGuy

I managed to get Klibido working with Stunnel with this thread:

[http://ubuntuforums.org/showthread.php?t=653246]("http://ubuntuforums.org/showthread.php?t=653246")

.

My head starts to spin when I'm confronted with lines and lines of settings to sort out, Inevitable it never works for fools like me the firts time so then I need to spend hours trying to sort it. 

Easier to install a windows app in Virtualbox ;)

BTW, I am having with PAN may be something else. I'll post separately on this thread.

> **GuiGuy said:**
> 
PAN; Almost immediately it starts thrashing the hard disk ( I haven't a clue what it's doing, but suspect it's indexing headers (?)) and making the PC so un-responsive  that it is unusable. Out of interest I let it run... three hours later it was still thrashing about. I've learnt to leave a shell open so I can kill PAN when it goes stupid. 


I may have to eat humble pie here. Last weekend I had to transfer a lot of files between eSATA and SATA devices on my ubuntu box. After a while I realised that the transfer was dreadfully slow. A few experiments and a bit of googling confirmed that there seems to be a major drama with SATA and UBUNTU. It seems that most, like me, only become aware of this problem when some high (SATA) disk transfer activity takes place. 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119730](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119730)

It may explain, in part and in my case at least, why PAN struggles when it encounters a huge number of headers.

Hopefully they'll be able to sort this bug out, especially as ATA/IDE devices are getting harder to find. And who'd want to go back anyway?

Cheers

---

### Post by mrfargoreed on 2009-04-04
> **GuiGuy said:**
> Easier to install a windows app in Virtualbox ;)

BTW, I am having with PAN may be something else. I'll post separately on this thread.

I was considering installing Virtualbox myself, but part of me just wants to be totally free from Windows.  Each day or two I'm finding solutions to things that I thought I could bot live without (Roboform, Newsleecher, etc) and I'm managing to find a way, and enjoy them.

I look forward to your PAN thread - I'm still undecided on PAN and Klibido, although I think Klibido looks better and is easier to use.

---

### Post by northwestuntu on 2009-04-04
> **GuiGuy said:**
> I think for nzbs we're well provided for. I use Lottanzb/hellanzb and they work a treat. 

Cheers

never heard of those before.  i'll give them a shot.

---

### Post by GuiGuy on 2009-04-04
> **northwestuntu said:**
> never heard of those before.  i'll give them a shot.

hellanzb is in the repository. 

lottanzb is a GUI for hellanzb. 
[http://www.lottanzb.org/](http://www.lottanzb.org/)
[http://www.lottanzb.org/downloads/ubuntu/](http://www.lottanzb.org/downloads/ubuntu/)

lottanzb makes configuration a doddle. Highly recommended if using nzbs.

---

### Post by LuisAugusto on 2009-04-12
What about KNode?

---

### Post by rukna on 2009-04-23
I'm in the same boat as most of you. Love everything else about Ubuntu, except be able to use a good binary newsgroup reader (another issue being able to use a good exchange client besides evolution, but that's some rant I'll save for another post). 

I have been using GrabIt in Windows. Works pretty nicely, including the search feature. I'll try newsleecher when I fire up my windows box next.

---

### Post by Colt725 on 2009-04-26
I went to the   [http://www.slyck.com/Newsgroups_Guide_Ubuntu_Linux_Guide](http://www.slyck.com/Newsgroups_Guide_Ubuntu_Linux_Guide) and followed the instructions. I am not new to newsgroup readers but using one in Linux is a nice challenge for me.   I am not quite ready to let go of XP but using KLibido to do my binary downloads, well Linux is sweet and I am running out of reasons to hold on to XP.   :popcorn:

I run Ubuntu Hardy on my laptop but I still had XP on my PC and I wasn't using Linux enough to get any benefit. I just installed jaunty jackalope on my PC with XP yesterday.

---

### Post by GuiGuy on 2009-04-26
> **Colt725 said:**
> 
I run Ubuntu Hardy on my laptop but I still had XP on my PC and I wasn't using Linux enough to get any benefit. I just installed jaunty jackalope on my PC with XP yesterday.

klibido crashes on my 9.04 kubuntu. Have raised the problem elsewhere. No response as yet.

---

### Post by Colt725 on 2009-04-27
I am sure you uninstalled it, logged out, and reinstalled KLibido

---

### Post by northwestuntu on 2009-05-11
> **GuiGuy said:**
> hellanzb is in the repository. 

lottanzb is a GUI for hellanzb. 
[http://www.lottanzb.org/](http://www.lottanzb.org/)
[http://www.lottanzb.org/downloads/ubuntu/](http://www.lottanzb.org/downloads/ubuntu/)

lottanzb makes configuration a doddle. Highly recommended if using nzbs.

been using lottanzb for a month now and i love it.  thanks for the links :P

---

### Post by ItchyNet on 2009-05-16
I'm proud to say I went Cold Turkey over to Ubuntu in 2006 when Vista was imminent.  The one and only windows hold-over program that I still run (using wine) is my beloved Usenet Explorer.  

Ninan is my favorite for NZB's which is sort-of linux-native (java) but there is SOO much more available on Usenet that is not covered by NZB sites.

I've seen some very promising linux offerings (i like klibido) but it, like all others, falls short in one way or another. 

I'm sure it's only a matter of time however.  I've not tried recent versions of pan but plan on giving it a looksee because i'm hearing good things recently.

---

### Post by northwestuntu on 2009-05-16
yes im afraid linux still lags behind when it comes to newsgroups.  lottanzb is great if you just want to use nzb files, but you can't use it to download headers. i still use newsbin pro.

---

### Post by GuiGuy on 2009-05-16
> **northwestuntu said:**
> yes im afraid linux still lags behind when it comes to newsgroups.  lottanzb is great if you just want to use nzb files, but you can't use it to download headers. i still use newsbin pro.

Since the OP in this thread I looked into a PAN a bit more. Its major problem, like so many linux applications, is that its programmers don't seem to know about multitasking and threads. I presume these concepts do exist in linux(?)

Second, its database management also seems to leave a lot to be desired. 

So, when you take this into account and are in the habit of downloading and retaining a lot of headers, PAN eventually gets bogged down. And there are no automated housekeeping functions built in, AFAICS, to speed things up again.

However, if you take the time to delete old messages, ie 
[LIST]
[*]RIGHT BUTTON CLICK ON NEWSGROUP
[*]DELETE SELECTED GROUPS' ARTICLES
[/LIST]

Performance returns to something resembling normality. 

Unfortunately Pan still doesn't do SSL and, I am sorry to say, I cannot get my head around Tor. It is another one of those obfuscated pieces of nonsense that the True Linux Believers seem to relish. I'll leave it to them.

All in all, Pan does seem to be the best of a poor lot. 

Cheers

---

### Post by thecoogster on 2009-05-20
Thanks for the input everyone, been using pan but it was fluctuating wildly and no SSL, gonna make the switch to one of the other programs.

Oh and first post   ):P

---

### Post by sdavmor on 2009-05-21
I've been running Newsbin Pro in a VirtualBox XP VM on top of Ubuntu for the last couple of years after running it on XP for about 5 years.  Before that I used Agent.  I tried Pan for a while but it was like stepping back to an old version of Agent. This weekend I think I'll give Newsbin Pro a try under WINE (on Jaunty) to see if I like that any better than the vBox approach. An equivalent functionality native-to*nix newsreader (supporting built-in header compression, multiple servers and all the other Newsbin bells and whistles) would be brilliant.

Cheers,
SDM in SoCal (Systems Theory)
[http://systemstheory.net](http://systemstheory.net)
:guitar:

---

### Post by yester64 on 2009-10-25
> **northwestuntu said:**
> newsbin pro runs great with wine

to be honest, that defeats the purpose of running linux if you have to run windows programs.
I actually have a key for newsbin, but newsbin has its own problems.
Klibido is ok, but crashes if you load more than 100k posts. Pan is nice if you want to read messages, but not very good for grabbing binaries.
and i am not in the boat for nzb downloads.

This is really one area that is bad supported. Of cource i can say this, i am not a programmer. I wish i can develop things.

---

### Post by Bachstelze on 2009-10-25
> **yester64 said:**
> to be honest, that defeats the purpose of running linux if you have to run windows programs.

Windows programs != Windows

---

### Post by xavier74 on 2009-10-28
Hello,

Klibido works pretty well to browse usenet group headers and download binary.

Grabbit works also pretty well but you have to use wine :-/

Otherwise with .nzb files there is also kwooty which is good for binary download as it also repair and extract files.

Bye

---

### Post by bayvista on 2009-11-05
I tried Pan with Jaunty. It downloads all the groups, but will not download headers. No Log message. Just nothing. So I'll try Liferea.

---

### Post by yester64 on 2009-11-05
> **bayvista said:**
> I tried Pan with Jaunty. It downloads all the groups, but will not download headers. No Log message. Just nothing. So I'll try Liferea.

Not sure if that helps, but everything is stored in /home/.pan2
There you have 2 folders a) article-cache and b) groups

I did a standart installation with the Softwaremanager and it worked right away. But i have 9.04 not sure if that matters.

---

### Post by Waddle on 2009-11-05
Just downloaded and running LottaNZB. Totally impressed! It downloads .par files only if needed (saves on major bandwidth), repairs broken files automatically,  supports SSL encryption (this was the selling point for me) and extracts .rar file automatically too . This is the best tool I've ever come across for binaries.   Amazing find and thanks to the OP who pointed it out to me here.

---

### Post by northwestuntu on 2009-11-05
> **yester64 said:**
> to be honest, that defeats the purpose of running linux if you have to run windows programs.
I actually have a key for newsbin, but newsbin has its own problems.
.

trust me on this one.  the features on newsbin pro blow away anything on linux.  sorry to say.  not to mention it works almost perfect through wine.  if they would come out with something better in linux i would use it, but until they do newsbin pro is the best :D

---

### Post by northwestuntu on 2009-11-05
> **Waddle said:**
> Just downloaded and running LottaNZB. Totally impressed! It downloads .par files only if needed (saves on major bandwidth), repairs broken files automatically,  supports SSL encryption (this was the selling point for me) and extracts .rar file automatically too . This is the best tool I've ever come across for binaries.   Amazing find and thanks to the OP who pointed it out to me here.

agreed! lottanzb is pretty good for handling nzb files.  i use it quite a bit, but if you want to download headers newsbin pro is the way to go.

---

### Post by Waddle on 2009-11-05
> **northwestuntu said:**
> agreed! lottanzb is pretty good for handling nzb files.  i use it quite a bit, but if you want to download headers newsbin pro is the way to go.

Yes I used Newsbin Pro for many years. I'm just tired of sorting through thousands of headers to find what I want. And although I may miss some good stuff every once in a while, I find using NZB search engines just as effective. Also with tools such as LottaNZB it just takes all the tedious work out of it for me. With a very small footprint. Not to mention the fact that I only use Windows for gaming these days. Nice to see a Linux binary client that supports SSL encrytion with out all the hassle of setting up Stunnel.

---

### Post by Davidmcoop on 2009-11-27
> **Sealbhach said:**
> Here's the article syndicated from the magazine:

[http://www.techradar.com/news/software/applications/reviewed-and-rated-the-best-linux-newsreaders-583539?artc_pg=1](http://www.techradar.com/news/software/applications/reviewed-and-rated-the-best-linux-newsreaders-583539?artc_pg=1)


.

I wonder what they must have been reviewing when they wrote this. None of the apps "do news". Not in the way that nntp is. They all crash

---

### Post by BbUiDgZ on 2010-01-04
i have to add to this thread that i'm using klibido and it works fine on 9.10
just as good as grabit imo :guitar:

---

### Post by tlcstat on 2010-01-06
Greetings, I am using altbinz which works perfect under wine. The free .25 version is all you need. I have to have a scheduler built in since Hughesnet only gives my unlimited downloads between 2AM and 7AM. The linux apps don't have a scheduler and as such are 
useless. Binsearch.net is a very good search engine and its free. I will keep trying the suggested linux apps but so far altbinz is the only thing that I can find that has everything.
tlcstat

---

### Post by GuiGuy on 2010-01-07
> **tlcstat said:**
> The linux apps don't have a scheduler and as such are useless. 
tlcstat

If you're using/ creating nzb files for your downloads then sabnzdbplus and lottanzb do scheduling. They're in the repository.

PS: you need to set up a CRON job for lottanzb, so maybe sabnzbd is the better option

---

### Post by aktiwers on 2010-01-07
No one mentioned sabnzbd yet?
Edit: woops didnt look on page 2

---

### Post by GuiGuy on 2010-01-07
> **aktiwers said:**
> No one mentioned sabnzbd yet?
Edit: woops didnt look on page 2

;)
However, not everything is suited for nzb so I agree that a decent newsreader that does SSL out of the box is something sadly missing from Linux. I have tried all the readers I could find and all have major failings IMO. Most failings relate to performance when their 'database' starts to grow.

---

### Post by futz on 2010-01-07
> **GuiGuy said:**
> PAN; ahhh, the wanna be. A bit like the Big Mac really- promises so much but delivers so little. Initially it seems great. Responsive,fast, well structured etc, Then, after a few weeks, as more and more headers are gathered up, bang, there's the brick wall. Now I dare not even start it up. Almost immediately it starts thrashing the hard disk ( I haven't a clue what it's doing, but suspect it's indexing headers (?)) and making the PC so un-responsive  that it is unusable. Out of interest I let it run... three hours later it was still thrashing about. I've learnt to leave a shell open so I can kill PAN when it goes stupid.
How much RAM do you have? 2GB is not enough for a serious Pan user. You WILL run out of memory constantly. Pan is greedy. You need 4GB or better. Of course if you have more than 4GB then you need to be running 64-bit Ubuntu. What version of Pan? 

I use Pan every day and have no such problems. It's certainly not perfect, but I love it. I download HUGE groups' headers (3 billion plus) routinely without problems. I run v0.133. I have 4GB of RAM. Was running Ubuntu 8.10 32-bit until yesterday - just switched to 9.10 64-bit.

The one time I saw Pan act like you describe was after I accidentally enabled Assistive Technologies. It was a terrible week! :D Here's a [link to the thread]("http://ubuntuforums.org/showthread.php?t=1123986").

I own Agent and run it in Windoze sometimes. It's great, but the best is probably Newsleecher (SuperSearch **RULES!**), tho that won't run in Wine (at least not for me, and not without a fight).

BTW: [Quickpar]("http://www.quickpar.org.uk/") runs great in Wine.

---

### Post by GuiGuy on 2010-01-07
> **futz said:**
> How much RAM do you have? 2GB is not enough for a serious Pan user. You WILL run out of memory constantly. Pan is greedy. You need 4GB or better. Of course if you have more than 4GB then you need to be running 64-bit Ubuntu. What version of Pan? 

Running a quadcore Phenom, 8G RAM, really smart underpinnings. I use Virtualbox a lot to run Windows. 

> 
I use Pan every day and have no such problems.


I haven't looked at Pan for awhile now. Using a client in Windows instead for newsgroup browsing. 

My other criticism of Pan is that it doesn't do SSL. Yea, I know there ways by yet again stuffing around with something else, but I'm just getting too old and tired for that. 

> 
The one time I saw Pan act like you describe was after I accidentally enabled Assistive Technologies. It was a terrible week! :D Here's a [link to the thread]("http://ubuntuforums.org/showthread.php?t=1123986").


Thanks for that. Good tip.


> 
BTW: [Quickpar]("http://www.quickpar.org.uk/") runs great in Wine.

Yes, agreed. 

I have a little netbook that I try to keep all linux. I use gpar on it. Seems to do the job. 

Cheers

---

### Post by jasondean on 2010-03-03
> **wrtpeeps said:**
> I've yet to find anything CLOSE to Super Search.

I find Easynews the best Usenet solution imo. and it OS agnostic since everything can be done from the website.

---

### Post by jasondean on 2010-03-03
> **GuiGuy said:**
> Running a quadcore Phenom, 8G RAM, really smart underpinnings. I use Virtualbox a lot to run Windows. 



I haven't looked at Pan for awhile now. Using a client in Windows instead for newsgroup browsing. 

My other criticism of Pan is that it doesn't do SSL. Yea, I know there ways by yet again stuffing around with something else, but I'm just getting too old and tired for that. 



Thanks for that. Good tip.




Yes, agreed. 

I have a little netbook that I try to keep all linux. I use gpar on it. Seems to do the job. 

Cheers

When I do use Pan(Easynews web *only* has 240 days retention, nttp OTH has 400 days)I think it's on of the better Usenet readers. SSL isn't difficult to setup and when I install new versions of Ubuntu with fresh installs I just copy the conf files to the new installation.

---

### Post by Ultra Cronic on 2012-07-31
> **MellonCollie said:**
> I haven't found anything better (for me) than running Newsleecher inside an XP VM.

I second that motion I just posted a vent-off on the linux communities ignorance to the void of a good news group down AND up-loader/ Reader witch means internal code written to manage yEnc splitfiles PAR's nzb and Nfo as well as Body text wrapped up in one GUI like NewsBin Pro. 
Seems as though these complaaints have been around for a long time and no Comeupance is the result.  I love linux, but after 22 years of people begging for the NewsBin-like software enouph is enouph, VM for linux and break out the WinXP pro install :(
Setup NewsBin pro = Problem solved but slower speed:( and Microsoft in the head CRASHES!!! Seriously Linux is totally inept with the oldest form of Internet communication the usenet since the late 60's [sad] the original internet, remember Kermit? 
I responded to this old post to make a point, it's nothing new linux usenet usage has gone to the sharts.

---

