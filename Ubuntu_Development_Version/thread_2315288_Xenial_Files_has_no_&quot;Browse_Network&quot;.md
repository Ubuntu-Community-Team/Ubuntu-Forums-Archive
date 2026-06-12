---
title: "Xenial Files has no &quot;Browse Network&quot;"
date: 2016-02-27
forum: Ubuntu Development Version
---

### Post by jerrylamos on 2016-02-27
Xenial "Files" has no "Browse Network" choice only "Connect to Server".  14.04 LTS has both "Browse Network" and "Connect to server" both.

How to Browse Network with Xenial  "Files"?

Local wired network has Ubuntu, Windows 10, and Windows XP pc's.

I couldn't find anything useful to me on Ask Ubuntu about this Xenial problem.

Thanks.

---

### Post by Hreinsi on 2016-02-27
I was looking also. Ended up with installing Nemo

---

### Post by MikeMecanic on 2016-02-27
I got a similar issue last week (no network icon) and I created a standard user account and things went back to normal in the second account only.  Give it a try....

---

### Post by jerrylamos on 2016-02-28
Nemo works with networked Win XP.  When I boot Win 10 on the same network Nemo can't browse any more.  I'm looking at Win 10 settings...

Thanks for the hint.

---

### Post by mc4man on 2016-02-29
Don't use so don't really know  - 
In 3.18 remember seeing such in the Locations > Other,  in 3.14 nothing apparent (assuming Connect to Server isn't what you want?
What if you open nautilus > ctrl+l and go to  network:///
If that's what you want then bookmark that location

---

### Post by motang on 2016-02-29
Yeah I am also experiencing this. Hope it will get fixed soon.

---

### Post by jerrylamos on 2016-03-01
Nemo to the rescue.  "Files" (Nautilus?) has lost Browse Network function.
Sudo apt-get install nemo
Works fine for home network browse.

BTW, with Google search, finally fixed problem with Win 10 Workgroup password.  Control Panel, Network, Advanced something or other, finally got down to sharing files and printers.  Usual window after window after window after....

Can now print from Xenial to the Epson printer on the Win 10.

Nemo access Win 10 fine, Nautilus on Xenial cannot.  "Deprovement" compared to 14.04 LTS. Obviously I have 14.04 in another partition for what doesn't work or is omitted on Xenial. .

---

### Post by jerrylamos on 2016-03-04
Wrote a bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1551003](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1551003)

See last comments on bug below.  BTW, What is a "bot"?

Brad Figg (brad-figg) wrote on 2016-02-28: Status changed to Confirmed	#2
This change was made by a bot.
Changed in linux (Ubuntu):
status:	New &#8594; Confirmed

Alberto Salvia Novella (es20490446e) on 2016-03-03
Changed in linux (Ubuntu):
importance:	Undecided &#8594; High

---

### Post by sammiev on 2016-03-04
Bot = Web crawler or Web spider, a computer program that does automated tasks.

Found [here]("https://en.wikipedia.org/wiki/Bot").

---

### Post by mc4man on 2016-03-05
> **jerrylamos said:**
> Wrote a bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1551003](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1551003)

See last comments on bug below.  BTW, What is a "bot"?

Brad Figg (brad-figg) wrote on 2016-02-28: Status changed to Confirmed	#2
This change was made by a bot.
Changed in linux (Ubuntu):
status:	New &#8594; Confirmed

Alberto Salvia Novella (es20490446e) on 2016-03-03
Changed in linux (Ubuntu):
importance:	Undecided &#8594; High
Most bugs filed against the kernel will 1st get a brad figg auto response. Fail to see why you filed a bug in nautilus against linux kernel??

---

### Post by P-I H on 2016-03-05
I have this problem, but I suppose it is a bug in Nautilus.
The Network item is missing in the side panel. I am using linux kernel 4.5 rc6.
With ctrl+l and the command  network:///, I get the 2:nd picture.

---

### Post by motang on 2016-03-06
I also marked the said bug as affecting me.

---

### Post by PaulW2U on 2016-03-06
> **mc4man said:**
> 1Fail to see why you filed a bug in nautilus against linux kernel??
Agreed, it's either a nautilus bug or a bug against a protocol that nautilus uses to explore networks.
I see that the bug report has been updated to include nautilus. I've me too'd it.

---

### Post by mc4man on 2016-03-06
> **PaulW2U said:**
> Agreed, it's either a nautilus bug or a bug against a protocol that nautilus uses to explore networks.
I see that the bug report has been updated to include nautilus. I've me too'd it.

Yeah, I added nautilus yesterday to report, we'll see.
Out of curiosity did anyone who uses this see what they wanted when nautilus 3.18 was being used? (via the +Other Location in sidebar

---

### Post by P-I H on 2016-03-06
Yes, if I remember correctly that was the case.

---

### Post by motang on 2016-03-07
> **P-I H said:**
> I have this problem, but I suppose it is a bug in Nautilus.
The Network item is missing in the side panel. I am using linux kernel 4.5 rc6.
With ctrl+l and the command  network:///, I get the 2:nd picture.

Not sure if this will stick, funny thing is after pressing ctrl + l I typed in network:/// and was able to see the network shares like you mentioned. Then I pressed ctrl + d to bookmark it and now I have it on the side pane.  Rebooted and looks like it stuck.

So now I can browse my network shares.

---

### Post by jerrylamos on 2016-03-07
Hmmm.  Today, Ctrl-l network:/// didn't work, some complaint about network shares list, but I can still print from Xenial to the Win 10's printer.

---

### Post by howefield on 2016-03-07
> **jerrylamos said:**
> Hmmm.  Today, Ctrl-l network:/// didn't work, some complaint about network shares list, but I can still print from Xenial to the Win 10's printer.

Probably won't make any difference, but try network:/// from the "Connect to Server" option.

Worked for me so far.

---

### Post by motang on 2016-03-07
If you bookmarked *network:///* then you don't need to press *ctrl+l* and type it in as it is available in the left pane. :)

---

### Post by Hreinsi on 2016-03-12
One way is to install dconf editor   Nautilus and make network icon wisable on desktop. Or with unity tweak tool.

---

### Post by howefield on 2016-03-18
Fixed..

> 
Message: 1
Date: Fri, 18 Mar 2016 08:44:16 -0000
From: Sebastien Bacher <xxxxx@ubuntu.com>
To: [email]xenial-changes@lists.ubuntu.com[/email]
Subject: [ubuntu/xenial-proposed] nautilus 1:3.18.4.is.3.14.3-0ubuntu3
        (Accepted)
Message-ID: <20160318084416.20554.97395.launchpad@pepo.canonical.com>
Content-Type: text/plain; charset="utf-8"

nautilus (1:3.18.4.is.3.14.3-0ubuntu3) xenial; urgency=medium

  * debian/patches/git_desktop_grid.patch:
    - use the correct grid point when moving icons on the desktop view,
      (lp: #1462267)
  * debian/patches/ubuntu_new_gtksidebar.patch:
    - GtkPlacesSidebar changed in GTK 3.18, update to the new version, that
      restores special items on context menus (eject, format, etc) and the
      sidebar item to browse remote locations (lp: #1548977)

---

