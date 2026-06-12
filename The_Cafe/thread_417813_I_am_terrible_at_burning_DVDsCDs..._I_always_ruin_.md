---
title: "I am terrible at burning DVDs/CDs... I always ruin them.."
date: 2007-04-21
forum: The Cafe
---

### Post by billdotson on 2007-04-21
A couple days ago I just got a spindle of 25 Sony DVD+RW's so that I could burn the parts of my Windows backup image.

I was in Windows ( I use Roxio Easy Media Creator 7 in there).  I had the parts of the image on a FAT32 shared partition and I then commenced the burning process with Roxio.  The first DVD I put in there halfway through the burn it errored out and said "seek, sync, ATIP or mechanical positioning error"  I was just like ok then I guess the disc is bad.  Then I burned 3 more and they seemed to got fine and finish and all.  Then I tried the 5th one I got the same error.  I was using an LG super multi burner (model H22N) burner, firmware 1.01.  I assumed the discs were bad so I put them aside.  Then I went looking for that error on google I realized that it was either a media problem or my drive.  I put a new DVD in and told Roxio to verify data after the burn was done.. and it failed.. said it could not access "file aaa" the first file.  So I assumed the drive was bad due to that.  Then I put the DVDs that failed in my other burners.. the NEC and the Lite-On (which is SATA).  The burns went fine on those so I assumed that my issue lied with that LG burner.  I think that is only the beginning of the problem..

I booted into Linux and tried burning a DVD with Brasero using the verify file data before and after options and the burn and everything went fine (or so I thought) but when it was done it showed the DVD as having 5.5GiB of max space with 3.1GB being used (the data I burned to it)  

Then I tried burning another one and Brasero exited out randomly and I looked at the debugging information and it pretty much just said.. this is an unknown error. 

I do not know if this is related, but if I try to blank a cd-rw with gnomebaker the drive just locks up and won't unmount until I reboot. 

Anyway, after I tried Brasero I put in a DVD and tried it with K3B (version 0.12 from the edgy repositories).  I told it to verify before and after but after it burned the verification failed (I am not using the LG at this point, I stopped using it after I stopped using Roxio) Then I tried another and it finally worked.    

Then I tried another DVD and guess what.. that one didn't work.  

I had started my download of Feisty last night so I booted into the LiveCD and tried the 1.0 version of K3b.  When I try to format or blank anything in there it says it cannot mount the media.  Sometimes it will format it but then it will say it cannot eject it after it is done.

**I think there might be some issues w/ my fstab in Edgy AND Feisty because DVD burning in them seems like it returns a ridiculous amount of errors.  I don't even know if Roxio is doing any good.  In Ubuntu sometimes blank DVDs won't mount and if I try to force formatting them (not quick, full) it will finish in like 2 seconds and just say successful.  Now I remember why I quit burning things a few years ago.. I could never get any of the stuff to work.    **

It seems especially bad in Ubuntu, like a problem communicating with ym drives or something.. anyway it is incredibly annoying.  Maybe my fstab entires are all messed up for my drives.  With the fesity livecd it sees them as scsi devices even though 2 of them are IDE and the other is SATA.  Maybe I have to run the burning app as sudo, I do not know but I am getting tired of ruining freaking DVD+RWs, if I keep burning I might as well have just taken $30 and lit a flame to it.

This is so frustrating.  Now when I am going into advanced settings to try and fix things I see all these different formats like ISO9660, Joilet, Rock Ridge UDF and all this other stuff I do not understand.  I am so confused.. it seems like I will never get where I can do a burn and not have to go through an hour checking to see why it didn't burn or didn't burn correctly.

---

### Post by rmemm on 2007-04-21
A couple of comments -- fstab only has to do with mounting not burning as far as I know so burn errors should not be caused by fstab config.  One thing I did though was turn off auto mounting as I don't like the idea of the system mounting stuff while I'm burning.  You can then do manual mounting by adding one of the panel applets to the gnome UI.

As for UDF -- I think you want ISO images -- so not that -- you want ISO9660 or whatever.  Regarding Rockridge and Joliet -- I never can remember what they do other than add basically modern file system meta data -- so I use both all the time at the moment.

As far as the Linux burning software -- I don't have much experience with that other than I've used k3b some without much problem.

Other thing -- if it your problem shows up under windows and linux and multiple media lots -- sounds like a hardware issue of some sort -- maybe the drive needs cleaning?

Rob

---

### Post by billdotson on 2007-04-21
it seems that if I burn discs, even the ones that Ubuntu wouldn't mount or a Linux burning app wouldn't format read or burn to with my SATA Lite-On drive or my NEC ND-2100-AD using Roxio is Windows.  I just did a test one on one that K3B gave me an error message with.  The file verification in Roxio passed, but I have yet to use an md5sum to check with the source files.  Speaking of, the problems I am having in Linux, I think anyway is that my SATA burner isn't being read or isn't communicating with Linux quite right.  I am almost certain my LG bruner is bad and I am going to RMA it Monday.  I know for a fact one DVD I burnt using K3B in Linux worked and that was the one I burned using my NEC CD-RW/DVD+RW OEM burner (came in my HP that I got a couple years ago, took it out when the PSU killed the motherboard.. all the other parts were fine AFAIK.. I rebuilt it and gave it to a friend)

I know my drives aren't dirty or anything.. I usually keep my PC blown out pretty often and the Lite-On and LG burners are only 3 months old.  I guess the LG is defective.. I have never really tried burning anything before now.. :-\ 

Someone was telling me that in kernel 2.6.20 there is a PATA/SATA issue that might be causing problems but I don't think I have that kernel unless Edgy auto-upgraded to it or Feisty uses it.

I am going to run a few more tests from within Roxio where I know all my drives are being seen correctly and then try and move to diagnose Linux problems.  Problems like this are what really frustrate me w/ Linux.. :(

Thanks.

---

### Post by rmemm on 2007-04-22
SATA -- interesting -- maybe there are more bugs or unresolved issues with it since it's newer.  I think my laptop burner is IDE and it works fine under linux.  

Do you have SATA hard drives?  I ask because I was thinking of upgrading my motherboard and maybe moving to SATA hard drives.  Was wondering of you had them and if they work OK for you?

You mentioned fstab previously -- just for reference the file systems part of my fstab for the burner I have is ext2,udf,iso9660 and that works for me.  I think the original was udf,iso9660 which probably worked also.  ext2 is only there because I've been playing with ro and rw mounted DVD+RWs.

Rob

---

### Post by LookTJ on 2007-04-22
What app did you use in Ubuntu?

I use Brasero.

---

