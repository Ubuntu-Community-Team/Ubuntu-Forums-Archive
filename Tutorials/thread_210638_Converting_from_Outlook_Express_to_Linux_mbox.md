---
title: "Converting from Outlook Express to Linux mbox"
date: 2006-07-07
forum: Tutorials
---

### Post by airjunman on 2006-07-07
Now this is a real pain in the a$$, was at least.. I didn't find any place that told it clearly, so just put together what worked for me.. OE and MS Outlook store their mailboxes as .dbx files, one file for each mail folder(eg.:Inbox.dbx,Sent.dbx,etc.). Generally the path for those files on the Windows box is C:/Documents and Settings/***uid***/Local Settings/Application Data/Identities/{1C46C658-5362-5463-8708-F215FD67238}/Microsoft/Outlook Express
where ***uid*** is your windows logon user id, and, the numbers are changed 

On Linux you need to have KMail installed with a plugin called KMail CVT which lets you import OE mailboxes and convert them to the standard linux mbox files. Both can be got from the repositories by doing the following:

> $ sudo apt-get install kmail
$ sudo apt-get install kmailcvt

You now need to import the necessary files:
Open KMail
File>Import Messages
This opens a dialog box which asks you to choose the program from which you want to import the mail
Click on the dropdown menu and choose "Import Outlook Express Emails"
Click "Next" and then choose the files
(You may have transferred the dbx to some place on your linux partition or else hopefully you'd have the drive containing it mounted so you can access it, in my case I just have my NTFS/Windows partitions mounted, which the latest Ubuntu does automatically.. Anyways you'd have to do one or the other) If it is mounted it could be at /media/hda6 which is to just give an example of how mine is. Also as an example the folder in Windows where the files generally are is:  *C:/Documents and Settings/uid/Local Settings/Application Data/Identities/{1C46C658-5362-5463-8708-F215FD67238}/Microsoft/Outlook Express*

Once you've chosen the folder, KMail downloads the mailbox and organises the folder structure as 
Local Folder > OE Import > "foldername"(say Inbox)

Now all you do is go to each folder. Select all the mails in it by <Ctrl+A> and then click on File>Save as
This opens a box to choose where to save the file, choose the path and the filename. You can name the file anything(say example.mbox), unlike what I earlier assumed that you'd have to name it *.mbox, you can leave it without any extension.

Anyways you're done. If you want to use KMail as your mail client that is. I dont like it much, I prefer Opera Mail cos it has everything you want and not much more and the important functions have easy shortcuts. So, like me, if you use another mail client, you have one step more.

Open any program you want: Evolution or Opera Mail or Thunderbird or anything else that you use. Choose to import files of "generic mbox type" and choose the file you saved earlier(in our case example.mbox). You're good to go.

Let me know if I made any mistake cos I'm only a newbie anyways. Just trying to give back a lill. Hope it works n helps someone out there trying to make the transition from Windows to Linux/Ubuntu

---

### Post by airjunman on 2006-07-18
Noone interested?

---

### Post by PingunZ on 2006-07-19
very nice howto :KS 

Grtz PingunZ

---

### Post by airjunman on 2006-07-19
Thanks PingunZ :)... Whats ur email client of choice in Linux though... I have a feeling Opera may be slowing my system down...

---

### Post by skirkpatrick on 2006-07-19
Sorry, I used Thunderbird installed on Windows to import my OE data then copied the files over to my Linux Thunderbird.

---

### Post by airjunman on 2006-07-19
Anything that works rite :)

---

### Post by mrdav1e on 2007-02-05
I had a customer's OE data and she is converting to Ubuntu, imagine a 70+ year old converting!
Anyway, I had a hell of a time finding a way to convert.
This was a sweet method, couldn't have done it w/o you.
The only 'challenge' I had was finding the kmail program, it didn't install to the applications folder so I had to go to the filesystem/usr/bin and d-click on kmail.   Not a big deal.
I went from oe to kmail to thunderbird with this method.
Sincerely,
Dave

---

### Post by airjunman on 2007-02-05
Glad to be of help .. The forums in general do a great job of helping out.. cheers!

---

### Post by Roelski on 2007-04-04
Great post!  Finally found what I've been looking for for some time now.

1 addition: if you tend to import into Evolution, you'll have to choose the destination email folder (say "tree-level").  That means you'll have to prepare the tree manually BEFORE importing as it cannot be done while you're running the import wizzard.  

One trick is in correctly naming the folders when you export them, e.g. 1-B-c-mailfoldername would mean "third level under second level under first level" under Inbox, a folder named "mailfoldername".  This is pretty time-consuming if you have a lot of subfolder though it helps you structure your mailbox.

For the Gnome-adepts: I ran Kmail under Gnome without any probs.

Besides this, it works like a charm.

Roelski

---

### Post by JamesD-2007 on 2007-07-02
Thanks, just what the Dr ordered.  Recovered all of mother in laws 'Important Stuff' with this.

---

### Post by tracer2009 on 2007-08-21
thanks just what i needed

---

### Post by yowshi on 2008-03-27
grrr it doesnt actually seem to be saving them anywhere for me.

---

### Post by carloslosgrande on 2008-04-04
[FONT="Comic Sans MS"]Thanks! Worked just fine for me[/FONT]

---

### Post by trondhuso on 2008-05-06
Looks great and promissing. I'll try it when I get the time. One suggestion though. Maybe it is more than enough to run the Kbuntu Live CD to do this If you don't want to install KDE-packages in your Gnome enviornment that is.

Trond

---

### Post by gordonh on 2008-05-13
> **mrdav1e said:**
> I had a customer's OE data and she is converting to Ubuntu, imagine a 70+ year old converting!
Anyway, I had a hell of a time finding a way to convert.
This was a sweet method, couldn't have done it w/o you.
The only 'challenge' I had was finding the kmail program, it didn't install to the applications folder so I had to go to the filesystem/usr/bin and d-click on kmail.   Not a big deal.
I went from oe to kmail to thunderbird with this method.
Sincerely,
Dave

I've been looking for a way to do this for weeks!
My wife's windows machines semi-crash meant I had to back up data including outlook mails before a complete re-install of windows (what a nightmare).

anyway, my exported .dbx files wouldn't re-load to outlook.  How can that make sense.  I have all the folders in Kmail now, so at worst I can re-send them to the hotmail account.

Why did I quote the above post?  After the two sudo apt-get install commands I typed kmail in the terminal and was taken straight into the setup procedure for Kmail.

Nice succinct howto.  thanks.

---

### Post by gordonh on 2008-05-13
> **yowshi said:**
> grrr it doesnt actually seem to be saving them anywhere for me.

did you remember to select "import outlook ..." from the dropdown menu?

I didn't the first time I tried.

The favourites folders pane was too small to see anything by default.  When I dragged it to the right everything became visible

---

### Post by Lucretia1 on 2008-12-16
This worked slicker than snail snot!  Absolutely perfect! My husband's windows machine finally died, so we're going windows-free and needed a way to convert all his old email.  THANKS!

---

### Post by cet77 on 2009-01-12
Thanks. :) works like a charm.. :)

-c-

---

### Post by cjv8888 on 2009-02-21
Worked really well.
Thank you.:D

---

### Post by alanbrodbeck on 2009-10-08
Worked great for rescuing a crashed windows pc (now running Ubuntu)!  I see it's been quite a while since this was written.
I only needed to run the first command:

$ sudo apt-get install kmail
kmailcvt was then present in /usr/bin/

Perhaps kmailcvt is now packaged with kmail proper.(?)
Thanks for writing this up!!

---

### Post by kevinguillorytraining on 2009-10-09
Thanks for nice howto. My choice in linux always Thunderbird

---

### Post by Godofgrunts on 2010-01-22
An easier way to do this is to use Wine and dbxconv

Instructions are on [my blog]("http://linuxnthings.blogspot.com/2010/01/convert-outlook-express-dbx-to-mbx-for.html")

As well as the [Wine Database entry]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=18935") (maintained by me, so if you have issues let me know).

---

### Post by martymcc on 2010-09-21
> **mrdav1e said:**
> I had a customer's OE data and she is converting to Ubuntu, imagine a 70+ year old converting!
Anyway, I had a hell of a time finding a way to convert.
This was a sweet method, couldn't have done it w/o you.
The only 'challenge' I had was finding the kmail program, it didn't install to the applications folder so I had to go to the filesystem/usr/bin and d-click on kmail.   Not a big deal.
I went from oe to kmail to thunderbird with this method.
Sincerely,
Dave
That comment about 70+ year olds might be objectionable age stereotyping. I'm 78 and converting from Windows to Mac OS X and Ubuntu at the same time, and I'm doing it myself, not as anyone's customer. My main computer runs Windows XP Home, with mail in Pegasus Mail, and I'm already sending and receiving mail on the Mac and I've migrated some, but not yet all, of my mailboxes. I use an old ThinkPad running Windows 98 SE to produce a newsletter for a chapter of The Mended Hearts, with mail in Outlook Express, and I haven't even decided which Linux mail client to migrate to, but this thread looks as though it would be very helpful.

---

### Post by the_warrior on 2011-07-18
*Thank you* for your very [I]useful information....
And thank you for sharing your knowledge...........
[/I]

---

### Post by pembertonq on 2012-01-18
I just tried yesterday, and kmail now natively has the ability to read Outlook Express. However, I couldn't find the method to save to mbox.

---

### Post by oldfred on 2012-08-17
Thread Closed.

---

