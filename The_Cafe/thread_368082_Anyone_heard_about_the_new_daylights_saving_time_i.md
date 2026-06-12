---
title: "Anyone heard about the new daylights saving time issue w/ computers??"
date: 2007-02-22
forum: The Cafe
---

### Post by billdotson on 2007-02-22
I read in an IT magazine that daylight savings time is different this year than it usually is and most computers won't be able to adapt to the change or something of that nature.

Is this really going to be an issue for normal people?

---

### Post by zeroblitzt on 2007-02-22
I don't see why people are getting their pants in a bunch here. Yes, its coming earlier, but its a simple fix if people just pay attention and don't let the issue slip by. 

The way I see it, [http://time.gov](http://time.gov) will always have the correct time, so servers could just fetch the time from there. Then it would just trickle down.

---

### Post by chickengirl on 2007-02-22
My local paper actually said that this Daylight Savings Time thing would be a "mini Y2K". :rolleyes:

---

### Post by RandomJoe on 2007-02-22
Daylight savings will start two weeks earlier and end one week later in the US.  For older OSes (up to Win2K, for Windows) there aren't any auto-updates to fix that.  A few of them have fixes that can be manually applied.

For the vast majority of users, though, all it means is the clock will be an hour off for a couple of weeks.  While that might be a problem for me since I use the computer's clock to know when to do something, that's about the most critical thing to it for most people.

Some time-sensitive business functions could be a problem, though.  The big one I hear on the news is things like reservation systems - your flight time might be off, you could miss your plane!  (Not sure how seriously I'd believe that...)  The systems I work with - building automation - will (unless the users update them) be starting/stopping the equipment an hour off during that time.  These are dedicated / embedded systems so no auto-updates there either.

I think on the whole it's more the media looking for another Y2K, in addition to it being a good chance to get another jab in at the President politically...

---

### Post by saulgoode on 2007-02-22
There was some discussion about this that some might find helpful (though it concerns Slackware packages) on [linuxpackages.net](http://www.linuxpackages.net/forum/viewtopic.php?p=91127&sid=38e8f678e0bbbf4d5b97f285ded14c63).

---

### Post by billdotson on 2007-02-22
I mean couldn't you just manually set your time to the right time? oh and by the way when do I need to change my time so I am not behind/ahead whatever it is

---

### Post by RandomJoe on 2007-02-23
The US will start DST at midnight of 10-11 March, then end it midnight of 3-4 November.

Yes, you can just set the time but then the OS will auto-adjust when it hits the old change time so you will have to readjust it then.

For those running newer OSes with updates enabled (or making sure they run the updates manually) it's a non-issue.  I just looked, and the zoneinfo files on my Ubuntu system have a datestamp of 22 Jan 07 so I guess it's been updated already - I was looking for the update, but never noticed it...  (Now I just need to remember to go run the updates on all my unattended machines...!)

---

### Post by corstar on 2007-02-23
There has been a minor issue in Perth.
We are trialling DST for the first time here, so the normal setting for ubuntu is an hour behind.
I have a work around for it though... just set to Japanese Standard Time. I just hope they don't have DST or my pc will be out of sync again..

---

### Post by billdotson on 2007-02-23
so am I moving the time forward or ahead? and when will I have to move it back??  

I have Ubuntu Edgy Eft and Windows XP SP2.. will these OSes automatically update the time correctly?  It sounds kindof like there are certain programs in businesses that are synced to servers or something and don't run off of the PC time like say a TV tuner scheduling program would.   Is this correct?

---

### Post by dtruesdale on 2007-02-23
I thought the update was already in the pipe for most linux distros on this. It's a simple conf file. Linux unlike windows doesn't hide this. Plus if you are using ntp your system should adjust it's time to correct it self even if it does jump it will set it back.

---

### Post by PrinceArithon on 2007-02-23
I wish they would do away with Daylight Savings Time...especially for spring time because I hate losing an hour sleep.

---

### Post by beercz on 2007-02-23
I wish we didn't have to change the clocks twice a year too!

I waste an hour every time the clocks go forwards/backwards by having to adjust all the clocks, video recorder, central heating, security lights, car clocks, cooker, microwaves, phones, mobile phones , alarm clocks, clock radios, watches etc etc.

I really don't care what time we have, just as long as we don't have to change it twice a year!!!!

Just seems such a futile and time wasting activity!  Drives me mad!!  Aaaaaaarrrrrrggggggghhhhhhh!!!!!! ](*,)

---

### Post by prizrak on 2007-02-23
Updating is the pain in the butt in the production environment but not that much issue. I got NTP working anyway so I don't depend on local DST calendar.

---

### Post by manmower on 2007-02-23
Precisely, just use ntp.

---

### Post by SuperMike on 2007-02-23
What? There's a USA DST issue coming up??? OMG.

Just kidding. Actually this has been in the PIA we've been muddling through in our office. You have two routes for updating systems. If they're Ubuntu, you probably already have the update and a zdump command like below will show you the result:

# zdump -v EST5EDT | grep 2007

The output should look exactly like this:

EST5EDT Sun Mar 11 06:59:59 2007 UTC = Sun Mar 11 01:59:59 2007 EST isdst=0 gmtoff=-18000
EST5EDT Sun Mar 11 07:00:00 2007 UTC = Sun Mar 11 03:00:00 2007 EDT isdst=1 gmtoff=-14400
EST5EDT Sun Nov 4 05:59:59 2007 UTC = Sun Nov 4 01:59:59 2007 EDT isdst=1 gmtoff=-14400
EST5EDT Sun Nov 4 06:00:00 2007 UTC = Sun Nov 4 01:00:00 2007 EST isdst=0 gmtoff=-18000

If that's not the case, then do an 'apt-get update; apt-get upgrade' and then run the command again. If that didn't fix your issue, then there's the NIH.gov technique:

1. su

2. cd /root

3. ftp elsie.nci.nih.gov
user: anonymous
pass: [email]you@you.com[/email]

4. cd pub

5. ls

6. use 'get' to get the latest tzdata file like so:

get tzdata2007a.tar.gz

7. quit

8. mkdir tzdata

9. mv tzdata*.gz tzdata/.

10. cd tzdata

11. tar xzvf *.gz

12. cp /etc/localtime /etc/localtime.LAST

13. rm /etc/localtime

14. zic northamerica

15. ln -s /usr/share/zoneinfo/EST5EDT /etc/localtime

16. zdump -v /etc/localtime | grep 2007

It should show Mar 11 and Nov 4 as the new times, in my case. My example above is only for the east coast of USA. If that's not you, then modify for your timezone. Sorry I don't know about other timezones.

Next, you then have to update PHP, Java, Python, and any other non-C/C++ programming language, in some cases -- check with the maintainers of those languages for updates about this.

---

### Post by billdotson on 2007-02-23
so does Windows XP SP2 have this setup to do automatically?

---

### Post by jhenager on 2007-03-02
> **PrinceArithon said:**
> I wish they would do away with Daylight Savings Time...especially for spring time because I hate losing an hour sleep.

I remember a quote from a Native American that said DST was like cutting off one end of a blanket and sewing it on the other.

For those of you using XP - if you have Automatic Updates enabled, and you accept them, you should be fine.

Anyone still running W2K will have to apply a patch manually.
[http://support.microsoft.com/gp/dst_topissues](http://support.microsoft.com/gp/dst_topissues)
This reads like a short story, btw. Pack a lunch before you launch this page.


Edit: More information from another enthusiast -
I did some MORE web surfing and found a place from where the Windows98 version of TZEDIT.EXE may be downloaded from Microsoft, along with instructions for its use (in case you don't want to rely on an "unofficial" program but want to get the Microsoft utility and do the patch on your own). The URL to that discussion is: [http://groups.google.com/group/micro...821d260?hl=en&](http://groups.google.com/group/micro...821d260?hl=en&)

The actual Microsoft location from which the Windows 98 versions of TZEDIT.EXE, TZEDIT.HLP, and TZEDIT.CNT can be obtained via anonymous FTP is: [ftp://ftp.microsoft.com/services/tec...Reskit/CONFIG/](ftp://ftp.microsoft.com/services/tec...Reskit/CONFIG/)
[http://www.pcguide.com/vb/showthread.php?t=54164](http://www.pcguide.com/vb/showthread.php?t=54164)

---

### Post by Sunflower1970 on 2007-03-02
I always hate these switches. I would think most of the population does too. I wish they'd pick one, either DST or standard time and not switch. Ever. At least for a week or so afterwards I drag until I get used to the time change.

/rant

Looks Ubuntu's good for the time change for me on all my computers, I think I'll have to manually switch my PDA though...

---

### Post by Crashmaxx on 2007-03-02
I hate this stuff too. Its not a big deal. But I like summer time or DST. I don't see why in winter I would want to have standard time or whatever. Then it gets dark even earlier, I want the extra hour in the evening, not at the crack of dawn.

But either would be fine really, just the switching is a pain for no good reason. We don't need to conserve candles, and everyone stays up all night anyway. Just leave the time alone and don't make time zones any more confusing.

---

### Post by OrangeCrate on 2007-03-02
> **billdotson said:**
> so am I moving the time forward or ahead? and when will I have to move it back??  


Spring "ahead", Fall "back".

---

### Post by muguwmp67 on 2007-03-02
Lets see, VCR's have been DST compatible for 10 years or so now.  Software needs to be tested and possibly patched.  Pre Windows XP OS's will need special attention by thier users.

I know its not that big a deal (it usually takes me a week to get around to changing all my clocks anyway)  But this seems to be a bill created for no other reason than to give electronics, hardware and software manufacturers a reason to sell replacements for 'obsolete' products.  Gotta love the lobbyists.

What a pointless waste of time.

---

### Post by Sentinel83 on 2007-03-02
I work for a very large company (30K ppl) and the DST thing really is a huge undertaking.  All thousands of machines must be patched (most win2k) along with all of the millions of outlook meetings get updated with the new time, etc.  That's not mentioned all the applications that need to sync with time outside of outlook, domain controller time, NTP, etc.  And of course none of this goes smootly so far.  It is not as simple as everyone will make you believe.  If you have a smaller number of machines and users then maybe it is very manageable, but for large corporations its a complete pain in the neck, and costly. 

I do believe the Linux community is in better shape due to the quick turnaround with patches, etc.  We are spending a lot of money and time planning patch rollouts and specialized patches for our environment.

---

### Post by Nythain on 2007-03-02
So from what i gather, the "mini catastrophe" in this lies more in businessess and government stuff... not your home pc... its not like a wrong clock is gonna cause your monitor to explode.

But a lot of businesses either dont know about the change, or didnt pay attention to it till really late, and are havening to hual balls to get caught up. Think about airports, hospitals, banks, any business with mainframes not connected to the internet, businesses responsible for the running of our every day life. I've heard mention of stock market issues if not adressed quickly.

Im personally not to worried about anything, as recent media hype and hundreds of faxes and memo's have pretty much brought attention of this issue to the ENTIRE world let alone my local Bank of America.

My own personall computer... well thats no biggie... hell windows even has an option to automatically adjust time for DST... turn it off, manually set clock, and turn back on after DST, or just wait for an update...

---

### Post by hellmet on 2007-03-02
> **jhenager said:**
> 

Anyone still running W2K will have to apply a patch manually.
[http://support.microsoft.com/gp/dst_topissues](http://support.microsoft.com/gp/dst_topissues)
This reads like a short story, btw. Pack a lunch before you launch this page.



Why is that W2K  page looking awkward to me? Its like the page is aligning
towards the *right* ??

---

