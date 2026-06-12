---
title: "spyware non-deleter"
date: 2008-04-22
forum: Security
---

### Post by legolas on 2008-04-22
I was surfing the web a couple of months ago, and I downloaded a questionable 10 second movie from a questionable site.  -yeah, I know, but I always push it to the limit because I am very interested in how tough my ubuntu set-up really is after I brag to all my friends about how I can surf the dangerous waters of the net, without fear of contracting a virus or worse.  Well, the movie I downloaded was not very good, so I erased it- so I thought.  But about a week later it popped back up on my desktop.  I erase it again.  About a week later it is back so I erase it using the command line.  A week later, yes, back again.  This reminds me of a windows non-deleter problem that I had a couple years ago, except this movie does actually delete, for a while at least.  Any Ideas?

---

### Post by BorisK on 2008-04-23
Use **shred** command to delete file. Maybe it'll help, but I doubt it. One thing is for sure - the file will get shredded. Perhaps it won't pop up again.

---

### Post by Patsoe on 2008-04-23
I would say: don't delete it - if it's really a "non-deleter" like you think (had never heard of such a thing), then a lot of people will be interested in forensic studies on it. Get some security guys to look at the file.

(actually, more likely something else is going on... do you have more details on the file?)

---

### Post by arsenic23 on 2008-04-23
Here's something interesting to try.  First find the inode number of the file by using:
```
ls -i
```
in the directory, in this case your desktop, that contains the file.  And then search and see if there are any other hardlinks to that file.
```
find -inum ****
```
**** is going to be the inode number you see by the file when you used the ls command.

---

### Post by legolas on 2008-04-23
Thanks for the ideas guys.  I just deleted the last one before I started the thread so I have to wait a week or so for it to come back.  It may be linked to visiting the same site, or sites that got me into trouble in the first place.  Sounds like a cookie from hell.

---

### Post by legolas on 2008-05-04
Ok, it is back.  I didn't even visit any questionable sites either!
Here is what I got.

me@puter:~/Desktop$ ls -i clip-4.wmv
2781594 clip-4.wmv
me@puter:~/Desktop$ find -inum 2781594
./clip-4.wmv

Must be spyware but I use Firefox and I went to Tools> Clear Private Data,
and I would think that would have done it but, its ba~ck!

---

### Post by Patsoe on 2008-05-05
Only thing I can think of: do you also mount your /home partition in another OS, say Windows? I had an issue once where I had hibernated Windows, accessed the same partition from Linux, then later accessed it from the resumed Windows session, and somehow the directory contents got set to what they had been in the Windows session before hibernation...

---

### Post by legolas on 2008-05-05
Thats interesting!  I just so happened to sign over to windows and then it appeared again! I share a hard disk with windows and Ubuntu data.  Maybe it is some spyware on windows and just re-appears when I play with windows.  Only thing is that my Ubuntu system is on a different disk though, and the file that keeps re-appearing, appears on the Gutsy Desktop.  I am going to experiment with my windows and see what I see.  I'll get back with you guys soon.

---

### Post by mikewhatever on 2008-05-06
> **legolas said:**
> I was surfing the web a couple of months ago, and I downloaded a questionable 10 second movie from a questionable site.  -yeah, I know, but I always push it to the limit because I am very interested in how tough my ubuntu set-up really is after I brag to all my friends about how I can surf the dangerous waters of the net, without fear of contracting a virus or worse.  Well, the movie I downloaded was not very good, so I erased it- so I thought.  But about a week later it popped back up on my desktop.  I erase it again.  About a week later it is back so I erase it using the command line.  A week later, yes, back again.  This reminds me of a windows non-deleter problem that I had a couple years ago, except this movie does actually delete, for a while at least.  Any Ideas?

Right, so you've infected your OS on purpose and now come here and ask for help. Why do you want help? I suspect it is to keep bragging and trying to get infected again. What's wrong with you?!

---

### Post by legolas on 2008-05-10
Heres an interesting development.  A new one has emerged.  A copy of the problem file has found itself on my Desktop.  I guess is has been just about a week since the last one appeared.  Now I have clip-4.wmv and clip-4(2).wmv on my Desktop.  I am thinking it tried to write itself on my Desktop again, found itself there already, so it gave itself the (2) in its name.  I haven't switched over to Windoze this time but it came back anyway, so this might not be Windoze related- especially since it is writing itself on my Ubuntu Desktop partition.

---

### Post by taggartromkey on 2008-05-10
I know this is slightly off topic but i just downloaded and installed a rootkit detecting program in terminal and this is what it gave me 
Setting up rkhunter (1.3.0-3) ...
Updating the file properties database:
[ Rootkit Hunter version 1.3.0 ]
File created: searched for 150 files, found 122

should i be concerned?

---

### Post by HunterThomson on 2008-05-10
> **mikewhatever said:**
> Right, so you've infected your OS on purpose and now come here and ask for help. Why do you want help? I suspect it is to keep bragging and trying to get infected again. What's wrong with you?!

What is with this guy? Someone out there looking for malware that can attack Ubuntu is a vary cool and a good thing, better him then me. For one, once it is found it can be defended against. Also, everyone dose say that you can't get infected with out like running a infected program as root. Finding out what is going on is also a fun challenge for the Ubuntu community.

Just my two cents. 

I am no help in finding out about the reappearing move. But, my guess is that it is really infecting window$ and because it is a shared drive you can see it in Ubuntu also. Just a newbie thought... have you looked at your log files for any weird entry's and run rootkit finding programs?
Edit- well maybe not on window$... I find this vary interesting though. What web site did you download the file from?

---

### Post by HunterThomson on 2008-05-11
> **taggartromkey said:**
> I know this is slightly off topic but i just downloaded and installed a rootkit detecting program in terminal and this is what it gave me 
Setting up rkhunter (1.3.0-3) ...
Updating the file properties database:
[ Rootkit Hunter version 1.3.0 ]
File created: searched for 150 files, found 122

should i be concerned?

If I remember correctly when I run the rkhunter I tells me no files are found.... Have you looked at the file? If you do get a definitive answer form someone that knows what they are doing (i.e. not me) you would want to reinstall the OS and format all partitions.

---

### Post by legolas on 2008-05-12
> **HunterThomson said:**
> What is with this guy? Someone out there looking for malware that can attack Ubuntu is a vary cool and a good thing, better him then me. For one, once it is found it can be defended against. Also, everyone dose say that you can't get infected with out like running a infected program as root. Finding out what is going on is also a fun challenge for the Ubuntu community.


Some people just need drama.

---

### Post by legolas on 2008-05-14
I noticed something.  I see every time Firefox crashes, or I shutdown my puter without  closing the web browser window, when I restart the web browser, it asks if I want to start a new session, or continue from where I left off.  If I choose to continue, the downloads window opens up and starts downloading the "evil" file.  I think if I can figure out how to empty the cache of the downloader, I might be rid of this file once and for all.
Ideas?  Like Hunter, I too find this very interesting!  Kind of a caper!

---

### Post by jakon on 2008-05-14
If it's firefox which is downloading the file, turn off automatic saving of files to the desktop. Edit -> Settings -> General -> Download -> Ask where to save file (or something like that, non-englisch Ubuntu here)

---

### Post by legolas on 2008-05-14
That wouldn't really be fixing the problem though.  There has to be a cache or list that I can modify so it doesn't try to download that specific file everytime.  I tried using the clear button on the downloads window, which looks like it erased the downloading history, and I tried erasing my cookies so, let's see how that does.

---

### Post by legolas on 2008-05-14
Ok, after doing the above, I killed my Firefox rather unceremoniously (kill button from the system monitor applet - I love that applet! )  and then I brought up the web browser again knowing it would ask if I wanted to start a new session or not.  I chose to continuw with the last session and this time the download window did not come up, so the file was not copied again.  It seems to be fixed.  Thanks for all your help everyone!
P.S.  Does anyone elses Firefox occasionally run up to 100% processor use for about 30 seconds or so and then go back to normal?  It may do this only in conjuction with Azureus, can't be sure...

---

