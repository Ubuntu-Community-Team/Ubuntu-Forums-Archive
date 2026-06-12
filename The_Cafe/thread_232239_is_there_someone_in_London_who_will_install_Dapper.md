---
title: "is there someone in London who will install Dapper for me?"
date: 2006-08-08
forum: The Cafe
---

### Post by ice60 on 2006-08-08
hi, i got a new computer and Dapper won't install on it because of the Serial ATA RAID 0 Stripe. there are some ways to get it installed but i can't do it. plus i don't really know where to start because i don't know what the exact problem is.

can i just disable the RAID and use 1 HDD? or does anyone know where i can go in london to get help? thanks.

---

### Post by Tomosaur on 2006-08-08
I should imagine if you walk into a respectable college or university, the IT staff may be able to help you sort your problem, but they may request a fee for their time, and that all depends on the individual. I doubt a computer repair shop would help you out - many just hire non-trained staff who consult manuals in the back room to get things done.

---

### Post by moma on 2006-08-08
Contact a local LUG (Linux User Group).

I just read the latest Linux Format mag (a mag from the UK), and it has a list of LUGs in  England. 
See [http://www.lug.org.uk/]("http://www.lug.org.uk/")

London area LUGs are:
[http://www.lug.org.uk/lugs/london.php]("http://www.lug.org.uk/lugs/london.php")

Visit them ;-)

---

### Post by mips on 2006-08-08
If I was in london I would help you.

You should be able to disable raid and simply install to a single drive.

If you have a second pc connected to the internet I would be willing to assist via a chat client or VoIP.

---

### Post by ice60 on 2006-08-08
thanks, everyone. i did manage to install suse but i broke x because i didn't know what i was doing with the PM and couldn't find help so just guessed which nvidia package to install #-o i only really like Ubuntu anyway :D 

Tomosaur i might go back to my old IT teacher and ask him

moma, i read that too, i'll have a look thanks

mips i have got another computer but it's in pieces atm.

i'm sure there must be a setting in the BIOS to disable the RAID :confused: the reason i hadn't thought of it before is i've read afew people talking about it and no one has mentioned disabling RAID. i'll have a look.

---

### Post by ice60 on 2006-08-08
this is the computer i have.  
[http://forums.us.dell.com/supportforums/board/message?board.id=dim_harddrive&message.id=113017&c=us&l=en&cs=19&s=dhs](http://forums.us.dell.com/supportforums/board/message?board.id=dim_harddrive&message.id=113017&c=us&l=en&cs=19&s=dhs)

very reassuring, i wonder what he did :confused:

---

### Post by John.Michael.Kane on 2006-08-08
ice60 what raid controller chip is in that machine? in all fairness if the raid chip is not supported even disabling the raid,and installing with one hdd,and reconnecting the other drive later would still cause issues.

---

### Post by Brunellus on 2006-08-08
> **Tomosaur said:**
> I should imagine if you walk into a respectable college or university, the IT staff may be able to help you sort your problem, but they may request a fee for their time, and that all depends on the individual. I doubt a computer repair shop would help you out - many just hire non-trained staff who consult manuals in the back room to get things done.
bwahahahaah ahahahaha ha.

*regains composure*.

My uni in London was a Microsoft shop...lock, stock, & barrel, from the desktops all the way up to the mail servers (exchange) and web servers (IIS).  I'd be shocked if they ever let any non-microsoft software touch their network on purpose.

---

### Post by Tomosaur on 2006-08-08
Really? In uni here (Liverpool), they use both linux and windows, and also support both. Maybe we're just BETTER :P

---

### Post by ice60 on 2006-08-08
> **SD-Plissken said:**
> ice60 what raid controller chip is in that machine? in all fairness if the raid chip is not supported even disabling the raid,and installing with one hdd,and reconnecting the other drive later would still cause issues.
can i attach this to a post from the livecd?
```
sudo lshw
```
it doesn't give any personal information does it?

---

### Post by ice60 on 2006-08-08
i think i need BIOS help now if RAID can be disabled there. so it shouldn't matter what OS i have. anyway, i don't even have a working HDD OS on here anyway :rolleyes:

---

### Post by John.Michael.Kane on 2006-08-08
ice60 you should be fine posting. that command does show ones ip at the bottom of the list. if you want to can edit it out.


Sidenote if you want to do like was sugested,and just run the machine san's raid you will have to figure out where raid is in the bios.

---

### Post by ice60 on 2006-08-08
> **SD-Plissken said:**
> ice60 you should be fine posting. that command does show ones ip at the bottom of the list. if you want to can edit it out.


Sidenote if you want to do like was sugested,and just run the machine san's raid you will have to figure out where raid is in the bios.

OK, thanks. here's the attachment. my IP's this anyway 192.168.0.2 :D 

i just found this which mentions stuff about the BIOS settings under - Drives. it mentions sata
[http://support.dell.com/support/edocs/systems/dim9100/en/SM/syssetup.htm#wp1043338](http://support.dell.com/support/edocs/systems/dim9100/en/SM/syssetup.htm#wp1043338)
i'm still having a look through dell support too.

---

### Post by ice60 on 2006-08-08
i'm not sure there is a setting to disable RAID in the BIOS. i think these are the options -

RAID Autodetect/ AHCI
RAID Autodetect/ ATA
RAID On
Combination 

the default is RAID Autodetect/ AHCI but i already changed it to Combination, but Ubuntu can't see the drives with Combination either. that was the option i used so i could install SUSE. i'll have to have another look.

---

### Post by Tomosaur on 2006-08-08
> **ice60 said:**
> OK, thanks. here's the attachment. my IP's this anyway 192.168.0.2 :D 


Just FYI, that's not your actual IP. That's just the IP your router has assigned to your particular computer.

---

### Post by John.Michael.Kane on 2006-08-08
ice60 now i'm stumped most everything listed is intel it even looks like the sata controller is intel based. ok after futher searhing the way dell has it set up is with fake RAID through the bios. 

edit From everything i have read there does not seem to be a way to disable the raid from inside the bios.

---

### Post by ice60 on 2006-08-08
> **Tomosaur said:**
> Just FYI, that's not your actual IP. That's just the IP your router has assigned to your particular computer.

thanks, that's why i said that was my IP lol, i wouldn't have given it if it showed my router IP, not that it really matters. there really isn't anything on my computer unless someone wants to fix my SUSE install :D 

[QUOTE=Tomosaur]ice60 now i'm stumped most everything listed is intel it even looks like the sata controller is intel based. ok after futher searhing the way dell has it set up is with fake RAID through the bios.

edit From everything i have read there does not seem to be a way to disable the raid from inside the bios.[/QUOTE]
OMG :shock: i'm never going to be able to use Dapper. i'll have to do something else then :( maybe slackware or the GCC screensaver - Gentoo :razz:

---

### Post by mips on 2006-08-09
ice60,

Look at this thread by yozef, [http://www.ubuntuforums.org/showthread.php?t=230361](http://www.ubuntuforums.org/showthread.php?t=230361)

The 'Combination' option should/might disable raid. There must be a way to disable raid as not all the Dell's come with two drives and the manual explains how to enable raid at a later stage incase you want to do so.

Maybe it can help you.

I would suggest completely wiping the drive(s), especially the install drive.

Here are more results from Dell forums on RAID:
[http://forums.us.dell.com/supportforums/search?board_id=dim_harddrive&submitted=true&q=RAID+Dimension+9150&x=13&y=10](http://forums.us.dell.com/supportforums/search?board_id=dim_harddrive&submitted=true&q=RAID+Dimension+9150&x=13&y=10)
Also google for **Ubuntu Dimension 9150**  looks like other people had some success.
[http://www.howtoforge.com/linux_software_raid](http://www.howtoforge.com/linux_software_raid)
[http://blog.dataloss.nl/perma/ubuntu-510-breezy-on-dell-dimension-9150/](http://blog.dataloss.nl/perma/ubuntu-510-breezy-on-dell-dimension-9150/)
[http://www.graffagnino.net/blog_archive/2006_06_01_archive.php](http://www.graffagnino.net/blog_archive/2006_06_01_archive.php)
[http://www.goodells.net/dellrestore/](http://www.goodells.net/dellrestore/)   Do you still have the restore partition ?
[http://markus.dresch.com/index.php?m=200604](http://markus.dresch.com/index.php?m=200604)
[http://support.dell.com/support/edocs/systems/dim9150/en/om/WD722A03.pdf](http://support.dell.com/support/edocs/systems/dim9150/en/om/WD722A03.pdf)

---

### Post by ice60 on 2006-08-10
> **mips said:**
> ice60,

Look at this thread by yozef, [http://www.ubuntuforums.org/showthread.php?t=230361](http://www.ubuntuforums.org/showthread.php?t=230361)

The 'Combination' option should/might disable raid. There must be a way to disable raid as not all the Dell's come with two drives and the manual explains how to enable raid at a later stage incase you want to do so.

Maybe it can help you.

I would suggest completely wiping the drive(s), especially the install drive.

Here are more results from Dell forums on RAID:
[http://forums.us.dell.com/supportforums/search?board_id=dim_harddrive&submitted=true&q=RAID+Dimension+9150&x=13&y=10](http://forums.us.dell.com/supportforums/search?board_id=dim_harddrive&submitted=true&q=RAID+Dimension+9150&x=13&y=10)
Also google for **Ubuntu Dimension 9150**  looks like other people had some success.
[http://www.howtoforge.com/linux_software_raid](http://www.howtoforge.com/linux_software_raid)
[http://blog.dataloss.nl/perma/ubuntu-510-breezy-on-dell-dimension-9150/](http://blog.dataloss.nl/perma/ubuntu-510-breezy-on-dell-dimension-9150/)
[http://www.graffagnino.net/blog_archive/2006_06_01_archive.php](http://www.graffagnino.net/blog_archive/2006_06_01_archive.php)
[http://www.goodells.net/dellrestore/](http://www.goodells.net/dellrestore/)   Do you still have the restore partition ?
[http://markus.dresch.com/index.php?m=200604](http://markus.dresch.com/index.php?m=200604)
[http://support.dell.com/support/edocs/systems/dim9150/en/om/WD722A03.pdf](http://support.dell.com/support/edocs/systems/dim9150/en/om/WD722A03.pdf)
oh, WOW. thanks for all the help, mips. i'll go through it all and make an effort to find a fix. i'd stopped looking because i didn't realise how much i'd like SUSE 10.1 (with smart PM :D)

i'll have to find a way to image SUSE before i do anything else now because i have spent two whole days setting everything up.

i'm really glad you posted because i was going to leave it and just use SUSE, but i really should find a way to fix this so i can multi-boot.

---

