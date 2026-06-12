---
title: "So now that we are 1 day till release i have a major issue"
date: 2013-04-24
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2013-04-24
i have manged to boot the current live cd 2/4 times today
i got it to install once
now i got it installed again and i get this, sorry for crappy picture battery to too low for second try
[[IMG]http://i.imgur.com/EG6zyWQs.jpg[/IMG]]("http://i.imgur.com/EG6zyWQ.jpg")

this is the 1st time i have ever seen anything like this, and i have been using ubuntu a couple years now at least
edit, this was on the installed hdd, it booted on the second try

---

### Post by screaminj3sus on 2013-04-25
I've been having the same issue since the latest kernel update. I've only seen it a few times (most times it boots fine), it seems to happen at complete random and only during boot The 3.8 kernel works fine for me in other distros (right now I'm using 3.8.8 on arch), its only ubuntu that does this to me. this is literally the first time I've ever had linux kernel panic on me. the latest kernel has also given me random pulseaudio issues: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1171181](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1171181)

Its a shame because besides some annoying compiz and ubuntu-online-accounts issues raring had been very solid for me, and then very close to release it seems we got a "bad kernel". :(

I saw both problems on two different laptops

---

### Post by WorLord on 2013-04-25
Yup.  Reported it as a bug.  Apparently, it wasn't hot enough to push back a release.  

Anyone with a nVidia proprietary drivers and a VERY common soundcard (intel HDMI driver) can't boot on the -18 and 19 kernels.  

Use the 3.9 rc8, working for me, until the fix comes out.  :-(

---

### Post by pqwoerituytrueiwoq on 2013-04-25
I will probably just stick with the 3.9 kernel, unless one breaks virtualbox, by then hopefully there will be a fix out

---

### Post by screaminj3sus on 2013-04-25
> **WorLord said:**
> Yup.  Reported it as a bug.  Apparently, it wasn't hot enough to push back a release.  

Anyone with a nVidia proprietary drivers and a VERY common soundcard (intel HDMI driver) can't boot on the -18 and 19 kernels.  

Use the 3.9 rc8, working for me, until the fix comes out.  :-(

I don't have nvidia, but both the laptops do have intel HDMI (different chipsets though, one ibexpeak one pantherpoint). For me the kernel panic is pretty rare, but enough to make me not want to run 13.04 until its fixed. I will try the 3.9 kernel though.

---

### Post by pqwoerituytrueiwoq on 2013-04-25
@[**[COLOR=#000000]screaminj3sus[/COLOR]**]("http://ubuntuforums.org/member.php?u=296445")
[http://ubuntuforums.org/showthread.php?t=2137026](http://ubuntuforums.org/showthread.php?t=2137026)
i made a mainline kernel update checker/installer here

---

### Post by WorLord on 2013-04-25
> **screaminj3sus said:**
> I don't have nvidia, but both the laptops do have intel HDMI (different chipsets though, one ibexpeak one pantherpoint). For me the kernel panic is pretty rare, but enough to make me not want to run 13.04 until its fixed. I will try the 3.9 kernel though.

I have been told (but cannot personally verify) that 3.9 breaks VirtualBox, unless you grab VirtualBox from their repos instead of Ubuntu's.  I would run the 3.8.8 mainline kernel, if I were you -- pqwoerituytrueiwoq's script should work just fine.  :-)

---

### Post by pqwoerituytrueiwoq on 2013-04-25
i can confirm 3.9rc8 works with the stock virtualbox on raring

---

### Post by Nick Scratch on 2013-04-26
Is this what is breaking my Virtualbox? I updated to Ringtail around the same time I updated to Nvidia drivers, now Virtualbox boots me to Ubuntu login screen the second I try to do something (e.g. open preferences).

Any help would be appreciated.

---

### Post by cariboo on 2013-04-26
@Nick Scratch, it may be best to ask your question about Vbox in General Help, or Virtualization, as the majority of us have already moved to Saucy, and/or are using other than the default kernel.

Just ignore the Raring RIngtail in the title of this sub-forum, as it will go away when the poll closes on Tuesday.

---

