---
title: "Uploading Directories While Avoiding FTP?"
date: 2007-04-17
forum: Server Platforms
---

### Post by Remi Rokosa on 2007-04-17
Is there a way to upload a directory using http whether it be a form or etc?

I recently put together a Ubuntu box that's dedicated storage for my friends and I to back up our music onto, unfortunately they're not techsavy (FTP isn't simple enough right?!... Yeah I know...) so I've grown kind of tired explaining how to use it so I was looking at a simple alternative. Sadly the only answers I've found so far were based on active server pages... which last time I checked is Microsoft based and I really don't want to sink to the level of using Server '03 again... 


Any suggestions?


                                                                                                                         -Thanks

---

### Post by mlentink on 2007-04-17
Why not use Samba? If they're win#$% users that's probably easiest for them..
Or are you not on the same network?

---

### Post by Remi Rokosa on 2007-04-19
No, they're not lan users. :-/ Thanks for the suggestion with samba though, anything else I could try?

---

### Post by Rinzwind on 2007-04-19
Apache can create a directorylisting. Then it's just rightclick and save. 
It would require you to open your system to the web.

You can also do it with hardware: 
At home I use a NAS ( [http://www.lacie.com/nl/products/product.htm?pid=10842](http://www.lacie.com/nl/products/product.htm?pid=10842) also in 320 en 500 Gb). Mine's 500 Gb plus has another 500 Gb USB disc linked to it. That LaCie one uses Yellow Dog Linux :)

---

### Post by Remi Rokosa on 2007-04-19
> **Rinzwind said:**
> Apache can create a directorylisting. Then it's just rightclick and save. 
It would require you to open your system to the web.

You can also do it with hardware: 
At home I use a NAS ( [http://www.lacie.com/nl/products/product.htm?pid=10842](http://www.lacie.com/nl/products/product.htm?pid=10842) also in 320 en 500 Gb). Mine's 500 Gb plus has another 500 Gb USB disc linked to it. That LaCie one uses Yellow Dog Linux :)

**Uploading**

I know how to make it so directories can be downloaded, I just don't know how they can be uploaded using something other then FTP... and something that's simple...


Thanks

---

### Post by tturrisi on 2007-04-19
ssh can do it, remote users can connect using a ssh client from linux or windows.

---

### Post by MJN on 2007-04-19
What about a graphical FTP/SFTP client? Presumably most of them can drag-and-drop directories? I can't imagine anything easier, or at least anything more similar to what they're probably already used to on their own PCs.
 
Mathew

---

### Post by Remi Rokosa on 2007-04-19
> **tturrisi said:**
> ssh can do it, remote users can connect using a ssh client from linux or windows.


I'm sorry for being such a nag, but what seems simple for you and me isn't for the average user. If they can't use FTP what makes you think they'll be able to SSH tunnel?

---

### Post by Remi Rokosa on 2007-04-19
> **MJN said:**
> What about a graphical FTP/SFTP client? Presumably most of them can drag-and-drop directories? I can't imagine anything easier, or at least anything more similar to what they're probably already used to on their own PCs.
 
Mathew

That sounds good, any recommendations?

---

### Post by bastiegast on 2007-04-19
If they can' use ftp, is there anything easier? Just tell them to open internet explorer, go to [ftp://username:Password@ip-address](ftp://username:Password@ip-address) and let them add the link to their favorites, If they open a ftp server in IE they can just drag and drop files as if it was a local directory, shouldn't be too hard to explain.

---

### Post by Remi Rokosa on 2007-04-19
Most of them use IE7 which doesn't let you just 'Drag & Drop' :-/

---

### Post by tturrisi on 2007-04-19
Users should not be expected to use commandline ftp or ssh.  If they can't use browser ftp or gui ftp-ssh clients then they should not be permitted to ever connect & upload, yet alone make directories and move files about!

---

### Post by MJN on 2007-04-19
Indeed. Command-line FTP is not much fun for the most technically savvy so I wouldn't even consider it for 'friends and family' when their goal is managing music and not managing the underlying technology.
 
FTP with Internet Explorer was always a bit naff in my opinion but then it was never really designed as an FTP client from the outset..
 
If your friends are Windows users I'd recommend WinSCP - free, fully functional, and pretty easy to use - they can happily ignore all the advanced stuff and I believe it can also be incorporated into Windows Explorer as an entry on the right-click context menu (e.g. Send To > Remote Music Store). You'll have to walk them through setting up their 'account' details (server, username, password) and a quick run-through on how it works (there're two windows as you'd expect - local computer and remote). It supports SFTP/SCP hence all you need to do is open up SSH access to your machine, given them system accounts (or perhaps shaing a single login depending on how you're running it?) and you're away.
 
My Dad uses it to upload photos to my server and if he can use it then believe me that's a thumbs up to its ease of use! ;) (Sorry Dad if you're reading this!)
 
Mathew

---

### Post by Remi Rokosa on 2007-04-19
Alright chip, thanks for the criticism.

A.) Browser FTP doesn't allow for drag and drop support.

B.) I don't want to have them downloading and configuring programs just to upload an album.

Wow, I'm really starting to think putting 2003 and using ASP would be better.

Can you just tell me how to ***upload*** directories via HTTP rather then telling me to do this other stuff?

---

### Post by Remi Rokosa on 2007-04-19
> **MJN said:**
> Indeed. Command-line FTP is not much fun for the most technically savvy so I wouldn't even consider it for 'friends and family' when their goal is managing music and not managing the underlying technology.
 
FTP with Internet Explorer was always a bit naff in my opinion but then it was never really designed as an FTP client from the outset..
 
If your friends are Windows users I'd recommend WinSCP - free, fully functional, and pretty easy to use - they can happily ignore all the advanced stuff and I believe it can also be incorporated into Windows Explorer as an entry on the right-click context menu (e.g. Send To > Remote Music Store). You'll have to walk them through setting up their 'account' details (server, username, password) and a quick run-through on how it works (there're two windows as you'd expect - local computer and remote). It supports SFTP/SCP hence all you need to do is open up SSH access to your machine, given them system accounts (or perhaps shaing a single login depending on how you're running it?) and you're away.
 
My Dad uses it to upload photos to my server and if he can use it then believe me that's a thumbs up to its ease of use! ;) (Sorry Dad if you're reading this!)
 
Mathew


WOW, Thank you. Finally someone that doesn't act like Simon Cowell.
Any quick run downs of WinSCP like guides or tutorials?

---

### Post by MJN on 2007-04-19
<damn - we're typing at the same time - I thought you were having a go at me hence have deleted my defence!>
 
As for guides/HowTo's I don't know - I'd just recommend downloading into (onto a Windows machine of course) and giving it a try - probably the best way as you'll experience first hand what your 'users' will go through!
 
I've probably made it sound more complicated than it is. Install an SSH server on your server then login with WinSCP as yourself - you'll soon see what sort of things it can do.
 
Mathew

---

### Post by Remi Rokosa on 2007-04-19
Alright, seriously thanks so much.

Do you have an instant messenger screen name?

---

### Post by MJN on 2007-04-19
'Fraid not...
 
Give WinSCP (or whatever) a go and post back - I'm sure there'll be many more wanting to do a similar thing as you so something more for the archives would be useful.
 
Mathew

---

