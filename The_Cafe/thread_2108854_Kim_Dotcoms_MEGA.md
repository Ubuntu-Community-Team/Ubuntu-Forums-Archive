---
title: "Kim Dotcoms MEGA?"
date: 2013-01-25
forum: The Cafe
---

### Post by candtalan on 2013-01-25
I have been trying out MEGA using Ubuntu 12.04, it really expects Chrome browser, so I have been using the repository Chromium and also Google Chrome. In many ways it works surprisingly well. However, the test I was mostly using was upload of a folder containing a total of approximately 650 small-ish files. In several tests over a couple of days now, I found that the browser crashed after some time. Inconveneint because the upload set then is not recoverable, and it seems not possible to collate, compare, whatever, the then partial upload.
I then tried first compressing the files into a single archive file, and this uploaded fast without problem (65MB or so).
I conclude so far that, for me, whatever is happening in the browser for multiple files, is not yet stable.

Anyone any experiences?

Edit: Just tried again, it crashed after approximately 150 files uploaded.  The (Edit) memory used had increased  from initial 20% to 50% (of 4GB) FWIW.

---

### Post by Double.J on 2013-01-25
Yes I've read quite a bit about mega running into server and bandwidth issues regarding it's popularity. A lot of press was given to it's launch. Note that's just tech writers, I've never tried it, I've been using adrive for quite a while now and have a lot uploaded there, so changing clouds seems a bit of effort!

Have you had a chance to try any larger files? Hopefully any initial launch bugs in the service will be short lived :)

---

### Post by sffvba[e0rt on 2013-01-25
It is early days, I signed up... used it once or twice, worked for what I was using.  Anyway, 50GB for free, yes please :)


404

---

### Post by pqwoerituytrueiwoq on 2013-01-25
> **not found said:**
> It is early days, I signed up... used it once or twice, worked for what I was using.  Anyway, 50GB for free, yes please :)


404
eagerly awaiting linux client for syncing (not filling my ubuntu one with my music)
i have a bandwidth limit (100gb) over my head so i will wait for the 31st to upload my stuff
edit: *does math* make that the 30th (not spending 7hrs uploading in one day)

---

### Post by candtalan on 2013-01-26
I am now trying a large single file, but after a few hours so far looking good, I notice that the (edit) memory is steadily getting eaten, steadily rising. this doe not bode well, but we will see

Edit: typo for 'swap' read 'memory'. Now changed to read correctly

---

### Post by candtalan on 2013-01-26
20 minutes later, another screenshot of the situation. Note (edit) memory use change and time

Edit typo correction 'memory' now has replaced the incorrect 'swap'

---

### Post by pqwoerituytrueiwoq on 2013-01-26
no change in swap, but your ram usage went up 200MB
edit:
you just edited your post to fix that

---

### Post by sffvba[e0rt on 2013-01-26
> **candtalan said:**
> 20 minutes later, another screenshot of the situation. Note swap use change and time


correction for swap read 'memory'

I don't see any change in swap... 88kb?!


404

---

### Post by jabulmer12 on 2013-01-26
for any one interested I am working on a ubuntu client in my free time, got auth working but there's limited info for developers so a lot of tile and errors

---

### Post by Lars Noodén on 2013-01-26
> **not found said:**
> It is early days, I signed up... used it once or twice, worked for what I was using.  Anyway, 50GB for free, yes please :)


I looked at the free option, but I couldn't find where the signup form said what I would be signing up for.  It also didn't seem to say which would be the username or login.  When you signed up, did you find any info like that?  Can you post a link?  50GB for free is nothing to turn down if there aren't any hidden gotchas.

---

### Post by candtalan on 2013-01-26
> **Lars Noodén said:**
> I looked at the free option, but I couldn't find where the signup form said what I would be signing up for.  It also didn't seem to say which would be the username or login.  When you signed up, did you find any info like that?  Can you post a link?  50GB for free is nothing to turn down if there aren't any hidden gotchas.

use https
[https://www.mega.co.nz/](https://www.mega.co.nz/)
register new a/c

I think login is necesarily your email addr. (dont use a hotmail they are getting 'lost')
Note that at present I think you cannot change the password later (unless you do something like nuke the data too) and your password is somehow integrated into the encryption too, as is entropy from mouse cursor when creating your encryption key (I am novice in this), so take it for the longterm.

Firefox works it seems, at least subsequent to registration, but chrome is required for the stuff like upload folder (not just files) etc  etc.

Mega is a fast and furious at present. The FAQ might help, or just internet search. Kim has given a number of interviews. Enjoy :-)

---

### Post by candtalan on 2013-01-26
Subsequent comments:
(Apologies for my wrongly typing swap rather than memory)
I let the single large file upload continue and took a few screenshots as time passed. The upload speed was very good, only limited by my broadband.
The browser (google chrome) again crashed at a time when the memory was over 50%, not sure of the exact point.

---

### Post by sffvba[e0rt on 2013-01-26
> **Lars Noodén said:**
> I looked at the free option, but I couldn't find where the signup form said what I would be signing up for.  It also didn't seem to say which would be the username or login.  When you signed up, did you find any info like that?  Can you post a link?  50GB for free is nothing to turn down if there aren't any hidden gotchas.

I read about the 50GB from this article ([http://news.yahoo.com/everything-know-kim-dotcoms-mega-174018641.html](http://news.yahoo.com/everything-know-kim-dotcoms-mega-174018641.html)) I was unable to find any info on the site itself however...


404

---

### Post by pqwoerituytrueiwoq on 2013-01-26
here are screenshots showing the pricing, i have not found a bandwidth limit for the free account yet

---

### Post by sffvba[e0rt on 2013-01-26
[s]> **pqwoerituytrueiwoq said:**
> here are screenshots showing the pricing, i have not found a bandwidth limit for the free account yet

:) lol, have a look at the second picture... 0GB of 50GB used :p[/s] Never mind, I read wrong...


404

---

### Post by candtalan on 2013-01-27
I later tried using firefox (not google chrome), which allows upload of a file, in my test here I use a single large file. All seemed to go well initially. Good upload speed, and as far as I could see, the memory use remained low, and there was no sign that it increased with time at least in the first 30 minutes or so. I left it overnight, to test the predicted 7 hours period suggested for the upload. 
in the morning the progress bar was indicating only 8%, the upload speed was a consitent high value. However, the system monitor indicated 'Total Sent' as 6.9GB and I recall it was around 3GB last night. I conclude that in this test, upload may have got almost completed yet the file somehow did not get fully taken at the server end (? novice talking here). Anyway I was not watching at the time. :-)

I will do some more tests when I can.
MEGA does seem though to work well, and fast for smaller files and bunches of files.

---

### Post by sffvba[e0rt on 2013-01-27
They need work on the client side, I am sure in time it will improve drastically...


404

---

### Post by sdowney717 on 2013-01-27
adrive gives 50gb free

---

### Post by sdowney717 on 2013-01-27
I signed up for MEGA, but got no email so cant confirm account.
How long does it take?

---

### Post by candtalan on 2013-01-27
> **sdowney717 said:**
> I signed up for MEGA, but got no email so cant confirm account.
How long does it take?

For me it was quick, minutes, in a lull during the initial gold rush panic. Since then they have re balanced. They are now aware that some email srevices dump the return emails from  looking  too much like spam, so worth double check on that.

---

### Post by candtalan on 2013-01-27
> **sdowney717 said:**
> adrive gives 50gb free
Nice I will look. I use SpiderOak (and U1) an dnow MEGA too. In principle I prefer encryption by default. (Adrive?)

---

### Post by candtalan on 2013-01-27
> **sdowney717 said:**
> adrive gives 50gb free
It seems a nice service, although does not appear to be encrypted by default, which in principle, I am uncomfortable about.

---

### Post by sdowney717 on 2013-01-27
> **candtalan said:**
> For me it was quick, minutes, in a lull during the initial gold rush panic. Since then they have re balanced. They are now aware that some email srevices dump the return emails from  looking  too much like spam, so worth double check on that.

Its not in junk folder.
I sent them a support question saying I did not get an email.

This is a hotmail service, which sometimes fails to get email from certain places, why I do not know.

Can you sign up for another account with gmail?

---

### Post by candtalan on 2013-01-27
> **sdowney717 said:**
> Its not in junk folder.
I sent them a support question saying I did not get an email.
This is a hotmail service, which sometimes fails to get email from certain places, why I do not know.
Can you sign up for another account with gmail?
Hotmail  is *known* to be getting lost! (yesterday tweet from kim d)

I would expect that you can use gmail.....

---

### Post by candtalan on 2013-01-27
Re my upload and memory issue - I have just noticed that the rise in memory use is broadly speaking the same as the rise in upload transfer progress. Does that mean something to anyone?

---

### Post by sdowney717 on 2013-01-27
I read that GoAruna is unlimited space.
Plus they have a linux client
I dont know how big a single file can be, one review said 100mb.

[http://goaruna.com/pages/app/goaruna-online-file-manager](http://goaruna.com/pages/app/goaruna-online-file-manager)

small review
[http://www.ilovefreesoftware.com/24/webware/online-storage/goaruna-free-unlimited-online-storage-and-backup-space.html](http://www.ilovefreesoftware.com/24/webware/online-storage/goaruna-free-unlimited-online-storage-and-backup-space.html)

Which looks to have become only 2GB??
[http://goaruna.com/pages/plans](http://goaruna.com/pages/plans)

---

### Post by pqwoerituytrueiwoq on 2013-01-27
> **sdowney717 said:**
> I signed up for MEGA, but got no email so cant confirm account.
How long does it take?
instantaneous for me, i registered on the 20th
i used a gmail account

---

### Post by sffvba[e0rt on 2013-01-27
> **pqwoerituytrueiwoq said:**
> instantaneous for me, i registered on the 20th
i used a gmail account

+1 for using Gmail...


404

---

### Post by candtalan on 2013-01-27
This afternoon I succesfully uploaded a 950MB file with no problem - although I could see that the memory being used was  - as  before - steadily creeping up. It is a 4GB ram machine, and the memory taken during the upload was apparently approximately 1GB. My guess is that this is a memory usage issue rather than a file size issue....

---

### Post by jabulmer12 on 2013-01-27
Kim Dotcom posted on twitter that hotmail was blocking emails from Mega for any one having issues registering

---

### Post by sdowney717 on 2013-01-28
Signed up using gmail.
However everytime I goto upload a folder, after a few files, I get a crash.
Now twice in a row.
Google Chrome browser, any ideas?

---

### Post by sdowney717 on 2013-01-28
Now trying to do multiple files no folders, while it does not show the crash page, the page goes totally white after uploading a few files.

Personally so far this has proven to be not very good.

---

### Post by candtalan on 2013-01-28
> **sdowney717 said:**
> Now trying to do multiple files no folders, while it does not show the crash page, the page goes totally white after uploading a few files.
Personally so far this has proven to be not very good.
I had similar trouble for folders containig lots (hundreds) of small files, and also for large single files (posts here earlier). I am using a machine with 4GB RAM, and, at least for the single file upload, I could see a lot of ram use and increasing memory and then a crash. I was repeated. I have concluded so far, that just now, the folder upload is unstable at least for google chrome (and chromium in Ubuntu repos) with ubuntu 12.04, and that single file upload is good and fast, albeit that the (I guess..) the machine ram might inadvertently limit file size from some memory leak bug. More RAM = bigger file ok, just guessing.

A bunch of small files uploads fast and with no problem. Again, this might be ram size related??
hth

---

### Post by sdowney717 on 2013-01-28
I dont know, there was maybe 15 files in the folder and I have 8gb ram.
I just tried using firefox 18 and it worked, Mega though told me I was using a browser that was not good, and to use Chrome.

As far as security, read this
>  "A few people have asked what the correct approach would've been here," he said. "The straightforward choice would've been to use SHA1, though MD5 or SHA256 -- for the more paranoid -- would also have worked well."

Thanks to using CBC-MAC, however, the Mega service is vulnerable to having uploaded files intercepted. **"If you were hosting one of Mega's CDN [content delivery network] nodes (or you were a government official of the CDN hoster's jurisdiction), you could now take over Mega and steal users' encryption keys,"** Marcan said. "While Mega's sales pitch is impressive, and their ideas are interesting, the implementation suffers from fatal flaws. This casts serious doubts over their entire operation and the competence of those behind it." 
[http://www.informationweek.com/security/encryption/mega-insecure-kim-dotcom-defends-reboote/240146801](http://www.informationweek.com/security/encryption/mega-insecure-kim-dotcom-defends-reboote/240146801)

SO, maybe the encryption idea is not done good. If they can intercept and see what you have done and you dont want them to see...

My attitude is anythiog you do online might and likely could be cracked, viewed, observed, tracked and used against you.

---

### Post by sdowney717 on 2013-01-29
Just tried Mega again, still wont work for me.
Does it work for any of you?

Went to upload a folder, it starts uploading, very slow, then it crashes in 2 minutes.

First pic shows it working, second CRASH.

Also tried Firefox and you can not upload a folder, just individual files maybe one by one even.
In fact when I selected one, nothing happened, no upload, nothing.
Could someone be causing this to happen in the USA, perhaps an ISP or who knows what. Hotmail run by MS is blocking email signups, so I dont doubt could be true.

---

### Post by candtalan on 2013-02-01
I sent a support request email briefly talking of these problems seen here, with a link to this forums thread too. I have received a (fairly quick) reply this morning just now:
============================
Hi Alan,
Thank you for your feedback. We have changed the upload/download algorithms last night, and the runaway memory consumption of Chrome
during up- and downloads, seems to have improved. 
Weirdly, during uploading, occasionally pressing F12 seems to trigger a garbage
collector and reduces memory consumption significantly.

Memory is not the only issue why Chrome crashes with MEGA, however.

We are looking into producing some test cases to submit to the Chromium team for fixing.

Please let us know if you see any improvement with that F12 trick.

Thank you!
============================
I was impressed by this quick response. I will continue  testing my stuff when I can, along with the f12 thing

---

### Post by candtalan on 2013-02-01
Blog from MEGA re some issues including memory use and linux:
[https://mega.co.nz/#blog_5](https://mega.co.nz/#blog_5)

---

### Post by Lars Noodén on 2013-02-01
I find most web interfaces awkward and difficult.  Have they added an SSH, rsync or similar interface yet?

---

### Post by candtalan on 2013-02-01
> **candtalan said:**
> Blog from MEGA re some issues including memory use and linux:
[https://mega.co.nz/#blog_5](https://mega.co.nz/#blog_5)
Wow. Much improved. Not perfect, but wow.
First I tried a bunch of files in file upload - total of 45 files (total 4MB) - all went ok (previously crashed).
I then used my fave test folder which contains 665 files some in two further levels of subfolder, totalling 77MB.
It worked :-)

However, I actively used the F12 gambit.....
Memory began less than 20% (of my 4GB machine) and I used F12 whenever it edged over 20% or say 22%. F12 is a toggle, and at the revert, the memory always reduced, even also sometimes for a repeated F12. On one occasion I decided to allow the memory use to increase further before I chickend out with a use of F12. I allowed it to rise to 30%. On this occasion, the only time, once it was above say 25% it seemed to rise a bit faster, anyway, F12 (at 30%) resulted in a crash. Rats. However, I did not close chrome, I used the curley Refresh page icon and regained the view of my Cloud Drive, albeit with the list of awaiting upload stuff gone. Rats. However I again used the Folder Upload facility to choose the same fave folder, and - to my delight - the uploads continued from where they had left off! My recollection is that when I had tried previously to recover from the crashes, I could not get the interrupted uploads to continue from where they had stopped. Maybe  on those ocasions I had used a different technique. Anyway, the test folder continued  at a good rate and completed uploading! I was watching constantly, and I used F12 if the memory use went above 21%, but in the later stages of the whole process, the memory stayed near to 20%, looking good.
I am delighted, it looks much better for the future I think. :-)

---

### Post by MadCow108 on 2013-02-02
for those interested in serious encrypted redundant storage should look into tahoe-lafs
its a similar concept to what mega is doing now just done by people who actually know what they are doing.

---

### Post by wollac on 2013-04-04
> **jabulmer12 said:**
> for any one interested I am working on a ubuntu client in my free time, got auth working but there's limited info for developers so a lot of tile and errors

This would be great! I have been eagerly waiting for an Ubuntu client for Mega since the products launch and have yet to find anything so far.

---

### Post by vandamme on 2013-04-05
Copy.com just started a Dropbox-clone that has a nice Linux client (like Dropbox). You can get an extra 5 GB by referrals from a member (member gets 5 GB too). 
Mine is [https://copy.com?r=Zv8zHi](https://copy.com?r=Zv8zHi)  so you get 10 GB just by clicking on that.

---

### Post by candtalan on 2013-04-07
> **vandamme said:**
> Copy.com just started a Dropbox-clone that has a nice Linux client (like Dropbox). You can get an extra 5 GB by referrals from a member (member gets 5 GB too). 
Mine is [https://copy.com?r=Zv8zHi](https://copy.com?r=Zv8zHi)  so you get 10 GB just by clicking on that.
Interesting, although it does not appear to offer encryption by default.

---

### Post by candtalan on 2013-04-07
> **jabulmer12 said:**
> for any one interested I am working on a ubuntu client in my free time, got auth working but there's limited info for developers so a lot of tile and errors

Any progress in your project I wonder? More power to your elbow! I am most interested because the Chrome client (with Ubuntu) is not stable for folders containing multiple subfolders, nor for large files (3GB ish). I heard Kim was going to release the api or toolkit whatever, soon, has that happened?
tia

---

