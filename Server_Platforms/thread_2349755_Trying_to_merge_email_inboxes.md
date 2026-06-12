---
title: "Trying to merge email inboxes"
date: 2017-01-17
forum: Server Platforms
---

### Post by Robert_Boutin on 2017-01-17
Hi, I rebuilt my email server which included installing a larger HDD.  Now I am trying to move my emails from my old HDD to the new.  I copied all the files into the inbox on the new HDD and I can see all of the emails when I open Roundcube.  However, Roundcube won't let me mark the emails as "Read", it gives me an error saying "Server Error: TheMailbox is Read Only" and even if I open it and read it, it remains marked as unread.  If I import a message into Roundcube, it behaves properly.  However, Roundcube won't let me import several thousand emails, even if I stay under the 8MB limit.  Any thoughts on this?  I'm hoping it's maybe just a matter of changing the permissions on the files in the old inbox but I have no idea where to even begin.  I am using Ubuntu 16.04 Server.  Roundcube says it is 1.2 Beta.

Thanks as always

---

### Post by darkod on 2017-01-18
Compare the permissions of the copied messages to the ones of the new messages that arrived on the new server. That's a good point to start. If there is difference change first only few of the old messages then check how they behave. Then change the rest.

---

### Post by SeijiSensei on 2017-01-18
Are you using mbox, where the folders are files?  

All the files and folders should be owned by your username with 700 or 600 permissions depending on whether the item is a directory or a file.

---

### Post by Robert_Boutin on 2017-01-18
I used ls -l <filename> to check file permissions.

Permission for the new files on the new HDD is -rw-------

Permission for the files that I copied into my new folder are -rw-rw-r--

So I ran chmod -R 600 on the folder with the old emails.  Now the permissions show as -rw------- so all seemed good.  But after I copied them into my email folder at /var/vmail/example.com/user/Maildir/cur/, I log into Roundcube and get an error when I click on my Inbox:  "An Error Occurred   Server Error: STATUS: Internal error occurred. Refer to server log for more information. [2017-01-18 23:09:41] (0.000 + 0.000 secs)."  So I assumed not all the files are owned by my username as you suggested.  I navigated to /var/vmail/example.com/user/Maildir/ and then tried chown user: cur but I got the same error in Roundcube.  I think you have me on the right path though.  Can you see anything obvious?  Thanks

---

### Post by Robert_Boutin on 2017-01-18
Ok, so I think I'm getting closer.  All my new email have user:group as vmail:vmail whereas all my old emails have user:group as rboutin:rboutin.

I tried to change the owner of all files to vmail:vmail by typing #chown vmail:vmail /var/vmail/example.com/username/Maildir/cur but it didn't seem to change ownership of the files.  The old ones remained rboutin:rboutin and didn't change to vmail:vmail

EDIT

And yet a little more progress.  I ran chown -R vmail:vmail . on the directory and now all files show up with vmail:vmail

example:
-rw------- 1 vmail vmail    82432 Jan 17 21:24 1484706248.M553466P10622.mail.example.com,S=82432,W=83968:2,S
 
So now I'm not getting an error in Roundcube, but... It says my inbox has 4006 messages with 2657 unread.  But when I scroll to page ~19, all my old emails are suddenly blank, no subject, etc, just nothing.  But Roundcube sees that they exist.

I'm certain the solution is simple, but this isn't a strength of mine.

---

### Post by darkod on 2017-01-19
When you say you executed chmod -R 600 be very careful because if there are subfolders, they will lose the execute/search bit and a folder needs that. In other words folders need to be 700 but files need to be 600. That is why using chmod -R is often difficult when removing permissions.

For removing permissions I prefer chmod -rw because that leaves the execute/search bit alone. For example to remove RW to group and to others, you would run:
```
sudo chmod -R g-rw
sudo chmod -R o-rw
```

Of course you need to add the name of the folder at the end but you get the point.

---

### Post by Robert_Boutin on 2017-01-19
Thanks to both of you.  As I suspected, it was an easy fix after reading your comments.  I neglected to execute chmod -R 700 /var/vmail/example.com/rboutin/Maildir/cur on the folder after moving old emails into the new directory.  It's working fine now.

Thanks again!

---

### Post by darkod on 2017-01-20
No problem, glad it's all fixed now. Please mark the thread as Solved if you don't need further help, you can do that in Thread Tools above the first post.

---

