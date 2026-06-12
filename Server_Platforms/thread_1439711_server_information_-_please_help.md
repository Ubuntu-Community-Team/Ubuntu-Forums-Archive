---
title: "server information - please help"
date: 2010-03-26
forum: Server Platforms
---

### Post by adgators89 on 2010-03-26
I am looking to start a server in my classroom so that I can install either thin clients or zero clients that access tthe server for a virtual workstation.  What equipment would I need to do this?

could I set up a standard LAMP server and then install Xen?  I really have no clue how do do this, but it would really help me out if I could do this so I can get rid of windows here and have a full Ubuntu lab.

my other thought was to have 4 stations run off of one computer, but if I can have all 28 or 30 do it off of a server that I set up than that would be even better.  Would I need switches to connect them through ethernet?

any help here would be appreciated.  I am in a budget crisis and looking to provide more stations for the students.  I guess the server is where the operating system would be and that it would send a virtual desktop to each user that logs in - anyway that's what I would be aiming for.

please help a newbie :)

---

### Post by jrssystemsnet on 2010-03-26
I'm by no means certain you can get thin clients cheaper than you can get cheap computers.  Wal-Mart sells netbooks and notebooks in the $300 range; I don't think you can get new thin-clients for less than $800-ish apiece.

Which is not to say you couldn't set up a server to push desktops out to clients... just that you'd want other reasons to do it than "save money", because the cheapest possible client is almost certainly going to end up being a full netbook or notebook computer.

---

### Post by llawwehttam on 2010-03-26
I have seen 30 thin-clients run off one server in the past but it was a dual quad-core xeon server.

If you plan using standard computers as your servers I would not have more than 10 clients running from each and even then you would have to be using decent machines.

What country are you in?

I am in the UK and here you can get cheapish thinclients at about £160 a piece. I think you can get them for $200 in the US from HP.

---

### Post by gordintoronto on 2010-03-26
A LAMP server is irrelevant to what you are trying to do. LAMP is for running a web site.

---

### Post by jrssystemsnet on 2010-03-26
> **llawwehttam said:**
> I am in the UK and here you can get cheapish thinclients at about £160 a piece. I think you can get them for $200 in the US from HP.Interesting... got a link?

BTW, for reference's sake, I've got Windows Server 2003 Terminal Servers servicing 20-ish RDP clients with 8GB of RAM and a single dual-core CPU pretty well; the apps are CPA stuff - Quickbooks, Acrobat, various niche tax software products, etc.

I don't have a whole lot of experience pushing multiple graphical desktops from Linux, but I would certainly think an Ubuntu box ought to be able to handle at least as many RDP sessions as a Windows server on comparable hardware... especially since you'd be running the Ubuntu server 64-bit, instead of having to use 32-bit and PAE like you do on the Windows side. :)

---

### Post by adgators89 on 2010-03-26
as I said I don't have much experience doing this, but I do like the posts and appreciate your responses.

I could possibly set up my classroom with teh good pc's I have now - 3ghz  -- 2gb ram (will put 2gb more ram in them)  and use each pc to maintain 4 - 8 computers(that is what I originally intended to do.  If you have advice on doing that I would appreciate that as well.  I have looked into ncomputing and their usb device ($90 each) can do this, but I was looking for a more cost effective way by using what I already have to increase the number of workstations virtually.  

My lab has 28 computers computers and I have them set in 7 rows of 4.  I have 8 solid good pc's all with the specs above, plus they have ati radeon cards in their that supports dual monitors.  so if I could use each of the pc's to run each row then that would work as well.  just not sure how to set the main host pc up to display virtual desktops and how the other computers would hook up to that host computer.  Would I use ethernet to hook up with a switch or does anyone have any other suggestions on how to set up the host computer and get the clients connected to them?

zero clients are around 80 - 300 here in the US and thin clients start around 150 I believe.  I thought netbooks didn't have the productivity that was necesary, but maybe I am mistaken - I have never worked with them, only desktops and notebooks

I thought I could do just this by using 1 server, but maybe that is not possible.

---

### Post by stlsaint on 2010-03-27
[LTSP]("https://help.ubuntu.com/community/UbuntuLTSP")

---

