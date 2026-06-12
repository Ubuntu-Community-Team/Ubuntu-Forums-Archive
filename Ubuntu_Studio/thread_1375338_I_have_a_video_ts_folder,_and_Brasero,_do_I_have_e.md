---
title: "I have a video_ts folder, and Brasero, do I have everything I need?"
date: 2010-01-07
forum: Ubuntu Studio
---

### Post by Hazelip on 2010-01-07
I'm coming from a Windows world where I just used Nero and that was that.

Now, I've got a video_ts directory and I want to make a kid-safe disc that I won't get too bent over it being apparently used for skim boarding the driveway...

Anyway, I can't seem to find a tut on using Brasero to burn a DVD-player-friendly DVD.

Do I just burn a data disc and burn the video_ts folder over, or do I use the painfully slow create a video project option in Brasero?

I have used Brasero to burn a DVD from an ISO, and it worked great, but I don't even know how to make an ISO from a disc in Ubuntu.  I'm searching for help, but I'm not using the right keywords or something.  Starting to drive me mad.

Anyway, if you can help me out, or point me to a tutorial, I would greatly appreciate it.

Thank you so much,
Jake

---

### Post by howefield on 2010-01-07
> **Hazelip said:**
> ..but I don't even know how to make an ISO from a disc in Ubuntu.

All you would normally do is right click on the disk icon once it is mounted, and select Copy Disc, then select image in the drop down field "Select a disc to which to write".

Don't know if that will work for copying a dvd successfully or not.

What I do is rip the kids DVDs to the hard drive using Handbrake, then make a DVD iso with Devede which can then be burnt to disk with Brasero.

Handbrake can be gotten from handbrake.fr and Devede can be installed with Synaptic Package Manger.

Benefit is that I keep a copy on the hard drive that can be accessed via any computer or tv, and also it is easy to make another copy when the first gets ruined. :)

---

### Post by Hazelip on 2010-01-07
Okay, that sounds a bit like what I'm currently trying to do.  I used mkisofs to make an ISO of the VIDEO_TS directory and files, and I'm using Brasero to burn the image to a DVD.

Sound about right?

I figure for making an ISO from a disc, I'd just use DVD::rip, right?

---

### Post by Hazelip on 2010-01-07
Well, that didn't work.  "could not open location, you may not have permissions to the file."

Damn.

---

### Post by Hazelip on 2010-01-07
This is terribly frustrating.  I'm trying to use Devede to make an ISO, but it's filling a folder full of mpg files when I want it to make an ISO...

---

### Post by Hazelip on 2010-01-08
I've made an ISO of the video_ts directory twice using three tools, mkisofs, devede, and iso master.  Each time, when I mount the ISO, or burn it to a DVD, I get the same permissions error in movie player.

Can anyone help me out here?

Oh, I should have said this earlier, but I'm on 9.04, using the Super OS distro.

---

### Post by Hazelip on 2010-01-08
I'm sorry to be a pest like this, but is there anyone who might be able to shed some light on as to why I'm getting this permissions error when I appear to be successfully burning a proper DVD video image?

---

### Post by airplus on 2010-05-12
Well, I have the same problem, downloaded a DVD and have a nice VIDEO_TS folder ready to go.

I open Brasero and "Add files" and get that silly message.

My solution?

Copy the Video_TS folder to my XP partition, shut down Ubuntu, log in XP, fire up old trusty Nero and voila!  Job done.

I take the oportunity to install all the Windows security updates, antivirus, etc.etc. :)

---

### Post by cchhrriiss121212 on 2010-05-12
To anyone else with this problem, you should try Xfburn. Just start a new data composition then drag the video_ts to it and burn away.

---

### Post by Michael Schmidt on 2010-07-28
According to this link, you would start a data project and pass it the video_ts directory.  Brasero is supposed to automatically create the Video disk.  There is mention of libdvdcss if one wants to copy the disk.

[http://www.gnomefiles.org/app.php/Brasero](http://www.gnomefiles.org/app.php/Brasero)

---

### Post by wkulecz on 2010-07-30
CD/DVD burning is broke for me in 10.04 :(

I need to use Windows or 8.04 to burn a disk :(

---

### Post by mango42 on 2010-08-02
> **wkulecz said:**
> Your commitment to Freedom is measured by your tolerence for others doing things you disapprove.

Like banksters stealing your pension? Like killing your neighbours? Sorry, couldn't resist, post Gaza Freedom flotilla... :(

---

