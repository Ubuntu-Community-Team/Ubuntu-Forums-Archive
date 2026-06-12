---
title: "Help Request - rootkit suspected"
date: 2009-11-04
forum: Security
---

### Post by shiv.brahmi on 2009-11-04
"*I apologize if this has already been posted or if this is in the wrong area*"

Hi,

I had a set of servers crash yesterday and they have asterisk installed on them one serving as a back bone and the other as a standby both are running cent os (I personally use Ubuntu on my machine) I had rkhunter and chkrootkit already installed on my machine and suggested to my Tech manager to do the following:

[LIST]
[*]Remove the machines from the server
[*]Remove the hard disk
[*]Boot with the ram present and no hard disk through the CD rom drive using the Ubuntu Live CD
[*]Use "*s[COLOR=Navy]udo passwd su[/COLOR]*" and create a new password for "[COLOR=Navy]*su*[/COLOR]" and refresh "[COLOR=Navy]*mem*[/COLOR]" (sorry I know that the administrators will not like this but this was an emergency and Ubuntu does not give permission to execute a refresh command for "[COLOR=Navy]*mem*[/COLOR]" unless signed in as "[COLOR=Navy]*su*[/COLOR]")
[*]Then use a new hdd and do a fresh ubuntu install and then *add the **old **hdd* as a slave and run rkhunter and chkrootkit ([COLOR=Navy]i did not know how to run these remotely by connecting to the machines through mine - [COLOR=Green]*Please do let me know if this is even possible and how to go about this*[/COLOR][/COLOR])
[/LIST]
But all this work did not give any results and we do not even have a log file indicating what actually went wrong and why the "*mysql"* tables crashed to begin with.

Request every one to please help me with what we should actually have done in this scenario and how to safeguard against these in the future. 

Both these servers were running with a total of 15 people logged in at the time and are dual core machines with 2 gigs of memory each

Thank you

---

### Post by __p1n__ on 2009-11-04
There isn't enough information in your post to even begin to offer suggestions.  Check the recent files in /var/log to see if there's any clue.

One thing though, repeating your installation process will simply get you back to the previous point of potential vulnerability (presuming that malware is actually involved) so all you've done is restore service.

---

### Post by shiv.brahmi on 2009-11-04
Thank you for your reply .. actually we used a new hdd to install Ubuntu afresh and then attached the old hdd and ran rkhunter and chkrootkit with the old hdd as a slave .. sorry for the confusion there ... we have checked that file */var/log* last night and it did not have any information on the crash or anything remotely suggesting a crash for both the machines ..

---

### Post by cdenley on 2009-11-04
There is no "su" user, so that command will fail. If you are trying to use chkrootkit to check a mounted filesystem other that "/", then make sure you use use mount point as the root directory.
```

sudo chkrootkit -r /media/disk

```
Why do you assume you have a root kit? There are other ways an attacker could crash your server.

---

### Post by shiv.brahmi on 2009-11-04
"***Why do you assume you have a root kit? There are other ways an attacker could crash your server.***"
Other ways .. I am unaware of anything as such sorry not very literate in cracking .. request you to please advise.

---

### Post by cdenley on 2009-11-04
> **shiv.brahmi said:**
> "***Why do you assume you have a root kit? There are other ways an attacker could crash your server.***"
Other ways .. I am unaware of anything as such sorry not very literate in cracking .. request you to please advise.

[http://www.ubuntu.com/usn/USN-852-1](http://www.ubuntu.com/usn/USN-852-1)
I'm not a cracker, either, but I think it would be easier to crash a system than install a root kit. Perhaps there was a vulnerability in asterisk that got exploited.

---

### Post by shiv.brahmi on 2009-11-04
> **cdenley said:**
> [http://www.ubuntu.com/usn/USN-852-1](http://www.ubuntu.com/usn/USN-852-1)
I'm not a cracker, either, but I think it would be easier to crash a system than install a root kit. Perhaps there was a vulnerability in asterisk that got exploited.

Well this definitely does point fingers elsewhere but how do I determine where to look for the cause. And more so how to prevent it in the future .. don't have the resources to cover this from a security point of view in depth ..

---

### Post by cdenley on 2009-11-04
> **shiv.brahmi said:**
> Well this definitely does point fingers elsewhere but how do I determine where to look for the cause. And more so how to prevent it in the future .. don't have the resources to cover this from a security point of view in depth ..

Well, assuming it is a security issue, you should check your logs. It couldn't hurt to check to check for root kits as well. If they crashed your system by simply doing a buffer overflow and corrupting your memory, then you probably won't be able to track down exactly how it happened. For all I know, a power problem could have caused your servers to crash.

---

### Post by shiv.brahmi on 2009-11-04
> **cdenley said:**
> Well, assuming it is a security issue, you should check your logs. It couldn't hurt to check to check for root kits as well. If they crashed your system by simply doing a buffer overflow and corrupting your memory, then you probably won't be able to track down exactly how it happened. For all I know, a power problem could have caused your servers to crash.

Buffer overflow is a definite possibility .. the SWAP size is 1 gb .. guess too small?

---

### Post by shiv.brahmi on 2009-11-10
it turns out that it was not a buffer overflow .. we found something in the hash sums will keep you posted

---

### Post by Roasted on 2009-11-10
Yeah - post back here then. I'm curious on the results. :popcorn:

---

### Post by shiv.brahmi on 2009-11-13
> **Roasted said:**
> Yeah - post back here then. I'm curious on the results. :popcorn:
Will. do .. just busy with a samba + ldap setup .. by the way could you point to a good resource for that?

---

### Post by wojox on 2009-11-13
[Samba Wiki]("http://wiki.samba.org/index.php/Samba_&_LDAP")

---

